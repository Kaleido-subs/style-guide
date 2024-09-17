# Build script

The build script is the script
that reads all the subtitle properties
and uses them to merge subtitle files
and mux them into a single `.mkv` file.

The build script is located at `./build.gradle.kts`,
and can be called with the `gradlew` wrapper.

!!! example "Calling the build script"
    === ":fontawesome-brands-windows: Windows"
        ```sh
        gradlew mux.01
        ```

    === ":fontawesome-brands-linux: Unix"
        ```sh
        ./gradlew mux.01
        ```

This is what a default build script looks like,
with annotations added to explain each line.

!!! example "Default build script"
    ```kotlin
    import myaa.subkt.ass.*
    import myaa.subkt.tasks.*
    import myaa.subkt.tasks.Mux.*
    import myaa.subkt.tasks.Nyaa.*
    import java.awt.Color
    import java.time.*

    plugins {
        id("myaa.subkt")
    }

    // Retrieve the script's playRes values
    fun ASSFile.getPlayRes(): Pair<Int?, Int?> {
        return this.scriptInfo.playResX to this.scriptInfo.playResY
    }

    fun Provider<String>.getPlayRes(): Pair<Int?, Int?> {
        return ASSFile(File(this.get())).getPlayRes()
    }

    // Check whether a string contains parts of a ktemplate
    fun String.isKaraTemplate(): Boolean {
        return this.startsWith("code") || this.startsWith("template") || this.startsWith("mixin")
    }

    // Check whether a line is part of a ktemplate
    fun EventLine.isKaraTemplate(): Boolean {
        return this.effect.isKaraTemplate()
    }

    // Check if a line is entirely blank (no text, actor, or effect)
    fun EventLine.isBlank(): Boolean {
        return this.text.isEmpty() && this.actor.isEmpty() && this.effect.isEmpty()
    }

    subs {
        readProperties("sub.properties")  // Read properties from sub.properties file
        episodes(getList("episodes"))     // Get list of episodes from properties

        // Merge all the individual script components
        merge {
            from(get("dialogue"))  // Include the main dialogue file

            if (propertyExists("OP")) {
                from(get("OP")) {
                    syncSourceLine("sync")     // Specify the sync line in the OP file
                    syncTargetLine("opsync")   // Specify the target sync line in the main file
                }
            }

            if (propertyExists("ED")) {
                from(get("ED")) {
                    syncSourceLine("sync")     // Specify the sync line in the ED file
                    syncTargetLine("edsync")   // Specify the target sync line in the main file
                }
            }

            fromIfPresent(get("extra"), ignoreMissingFiles = true)  // Include extra file if present
            fromIfPresent(getList("INS"), ignoreMissingFiles = true)  // Include INS files if present
            fromIfPresent(getList("TS"), ignoreMissingFiles = true)   // Include TS files if present

            fromIfPresent(get("render_warning"), ignoreMissingFiles = true)  // Include render warning if present

            includeExtraData(false)        // Don't include extra data
            includeProjectGarbage(false)   // Don't include project garbage

            // Try to set the LayoutRes values from the playRes values of the dialogue file.
            // Falls back to 1920x1080 if not found
            val (resX, resY) = get("dialogue").getPlayRes()

            scriptInfo {
                title = get("group").get()
                scaledBorderAndShadow = true
                wrapStyle = WrapStyle.NO_WRAP
                values["LayoutResX"] = resX ?: 1920  // Set LayoutResX, default to 1920 if not found
                values["LayoutResY"] = resY ?: 1080  // Set LayoutResY, default to 1080 if not found
            }
        }

        // Remove ktemplate and empty lines from the final output
        val cleanmerge by task<ASS> {
            from(merge.item())
            // ass { events.lines.removeIf { it.isKaraTemplate() or it.isBlank() } }
            ass { events.lines.removeIf { it.isBlank() } }  // Remove blank lines
        }

        // Generate chapters from dialogue file
        chapters {
            from(get("chapters"))
            chapterMarker("chapter")  // Use "chapter" as the chapter marker
        }

        // Run swapper script for honorifics and other swaps
        swap {
            from(cleanmerge.item())

            styles(Regex("Main|Default|Alt"))  // Apply swaps to these styles
        }

        // Finally, mux following the conventions listed here: https://thewiki.moe/advanced/muxing/#correct-tagging
        mux {
            title(get("title"))  // Set the title of the muxed file

            // Optionally specify mkvmerge version to use
            if (propertyExists("mkvmerge")) {
                mkvmerge(get("mkvmerge"))
            }

            from(get("premux")) {
                tracks {
                    include(track.type == TrackType.VIDEO || track.type == TrackType.AUDIO)  // Include only video and audio tracks
                }

                video {
                    lang("und")              // Set video language to undefined
                    name(get("vtrack"))      // Set video track name
                    default(true)            // Set as default video track
                }

                audio {
                    lang("jpn")              // Set audio language to Japanese
                    name(get("atrack"))      // Set audio track name
                    default(true)            // Set as default audio track
                    forced(false)            // Not forced
                }

                includeChapters(false)       // Don't include chapters from premux
                attachments { include(false) }  // Don't include attachments from premux
            }

            from(cleanmerge.item()) {
                tracks {
                    lang("eng")                 // Set subtitle language to English
                    name(get("strack_reg"))     // Set subtitle track name
                    default(true)               // Set as default subtitle track
                    forced(false)               // Not forced
                    compression(CompressionType.ZLIB)  // Use ZLIB compression
                }
            }

            from(swap.item()) {
                subtitles {
                    lang("enm")                 // Set honorific subtitle language to Middle English
                    name(get("strack_hono"))    // Set honorific subtitle track name
                    default(true)               // Set as default subtitle track
                    forced(false)               // Not forced
                    compression(CompressionType.ZLIB)  // Use ZLIB compression
                }
            }

            chapters(chapters.item()) { lang("eng") }  // Include chapters with English language

            // Fonts handling
            skipUnusedFonts(true)  // Skip attaching unused fonts

            attach(get("common_fonts")) {
                includeExtensions("ttf", "otf")  // Attach common fonts
            }

            attach(get("fonts")) {
                includeExtensions("ttf", "otf")  // Attach episode-specific fonts
            }

            // Get OP/ED fonts if necessary
            if (propertyExists("OP")) {
                attach(get("opfonts")) {
                    includeExtensions("ttf", "otf")  // Attach OP fonts
                }
            }

            if (propertyExists("ED")) {
                attach(get("edfonts")) {
                    includeExtensions("ttf", "otf")  // Attach ED fonts
                }
            }

            out(get("muxout"))  // Set output file name and path
        }

        // =================================================================================================================
        // NCOP/EDs
        tasks(getList("ncs")) {
            merge {
                from(get("ncsubs"))  // Include NC subtitle file

                includeExtraData(false)
                includeProjectGarbage(false)

                scriptInfo {
                    title = get("group").get()
                    originalScript = get("group").get()
                    scaledBorderAndShadow = true
                }
            }

            val cleanncmerge by task<ASS> {
                from(merge.item())
                // ass { events.lines.removeIf { it.isKaraTemplate() or it.isBlank() } }
                ass { events.lines.removeIf { it.isBlank() } }  // Remove blank lines
            }

            chapters {
                from(cleanncmerge.item())
                chapterMarker("ncchapter")  // Use "ncchapter" as the chapter marker for NC
            }

            mux {
                title(get("title"))  // Set the title of the muxed NC file

                from(get("ncpremux")) {
                    tracks {
                        include(track.type == TrackType.VIDEO || track.type == TrackType.AUDIO)  // Include only video and audio tracks
                    }

                    video {
                        lang("jpn")              // Set video language to Japanese
                        name(get("vtrack"))      // Set video track name
                        default(true)            // Set as default video track
                    }
                    audio {
                        lang("jpn")              // Set audio language to Japanese
                        name(get("atrack"))      // Set audio track name
                        default(true)            // Set as default audio track
                    }
                    includeChapters(false)       // Don't include chapters from NC premux
                    attachments { include(false) }  // Don't include attachments from NC premux
                }

                from(cleanncmerge.item()) {
                    tracks {
                        lang("eng")                 // Set subtitle language to English
                        name(get("strack_reg"))     // Set subtitle track name
                        default(true)               // Set as default subtitle track
                        forced(false)               // Not forced
                        compression(CompressionType.ZLIB)  // Use ZLIB compression
                    }
                }

                chapters(chapters.item()) { lang("eng") }  // Include chapters with English language

                skipUnusedFonts(true)  // Skip attaching unused fonts

                attach(get("ncfonts")) {
                    includeExtensions("ttf", "otf")  // Attach NC-specific fonts
                }

                attach(get("common_fonts")) {
                    includeExtensions("ttf", "otf")  // Attach common fonts
                }

                out(get("ncmuxout"))  // Set output file name and path for NC
            }
        }
    }
    ```

For more information on individual tasks,
see the [tasks documentation](./tasks.md).
