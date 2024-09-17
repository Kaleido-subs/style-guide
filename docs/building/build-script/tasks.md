# Build Script tasks

!!! warning "Stub"
    This page is a [stub][wikipedia-stubs].
    You can help by [expanding it][contributing].

    ??? question "How can I help?"
        You can help by updating this page with examples.

This is a list of all the tasks
automatically included in our build script.

## Tasks

### merge

=== "Description"
    !!! info ""
        The `merge` task combines multiple subtitle files into a single ASS file.
        It's used to merge the main dialogue file with other components like OP/ED, extras, inserts, and typesetting.

        Key features:
        - Includes the main dialogue file
        - Optionally includes OP/ED files with sync line matching
        - Includes extra files if present
        - Sets script info like title, border/shadow scaling, and layout resolution

=== "Example"
    !!! example ""
        ```kotlin
        // Example code for merge task
        ```

### cleanmerge

=== "Description"
    !!! info ""
        The `cleanmerge` task processes the merged subtitle file to remove unnecessary lines:
        - Removes blank lines
        - (Optionally) Removes karaoke template lines

=== "Example"
    !!! example ""
        ```kotlin
        // Example code for cleanmerge task
        ```

### chapters

=== "Description"
    !!! info ""
        Generates chapter markers from the dialogue file:
        - Uses "chapter" as the chapter marker
        - Creates a chapters file for muxing

=== "Example"
    !!! example ""
        ```kotlin
        // Example code for chapters task
        ```

### swap

=== "Description"
    !!! info ""
        Applies text swapping for honorifics and other predefined replacements:
        - Operates on specified styles (e.g., "Main", "Default", "Alt")
        - Creates an alternative subtitle track with swapped text

=== "Example"
    !!! example ""
        ```kotlin
        // Example code for swap task
        ```

### mux

=== "Description"
    !!! info ""
        The `mux` task combines video, audio, and subtitle files into a single MKV container:
        - Sets title and track metadata
        - Includes video and audio from the premux
        - Adds regular and honorific subtitle tracks
        - Attaches fonts and chapters
        - Applies compression to subtitle tracks
        - Skips unused fonts
        - Outputs the final muxed file

=== "Example"
    !!! example ""
        ```kotlin
        // Example code for mux task
        ```

## NC Tasks

For NCOP/NCED (creditless openings/endings):

### merge
=== "Description"
    !!! info ""
        - Combines NC-specific subtitle files

=== "Example"
    !!! example ""
        ```kotlin
        // Example code for NC merge task
        ```

### cleanncmerge
=== "Description"
    !!! info ""
        - Removes unnecessary lines from NC subtitles

=== "Example"
    !!! example ""
        ```kotlin
        // Example code for NC cleanncmerge task
        ```

### chapters
=== "Description"
    !!! info ""
        - Generates NC-specific chapters

=== "Example"
    !!! example ""
        ```kotlin
        // Example code for NC chapters task
        ```

### mux
=== "Description"
    !!! info ""
        - Creates a separate muxed file for NC videos with appropriate metadata and attachments

=== "Example"
    !!! example ""
        ```kotlin
        // Example code for NC mux task
        ```

[//]: # (stubs)
[contributing]: https://github.com/Kaleido-subs/style-guide/pulls
[wikipedia-stubs]: https://en.wikipedia.org/wiki/Wikipedia:Stubs
