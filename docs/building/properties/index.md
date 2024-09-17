# Subtitle Properties

!!! warning "Stub"
    This page is a [stub][wikipedia-stubs].
    You can help by [expanding it][contributing].

    ??? question "How can I help?"
        You can help by updating this page with examples,
        and better splitting up the sections.

The `sub.properties` file is used to configure the build script.
This file contains various settings that control how the subtitles are processed
and how the final output is generated.

## Basic Structure

The `sub.properties` file is structured as an INI-like configuration file,
with key-value pairs separated by an equals sign (`=`).
Comments can be added using the hash symbol (`#`).

## Key Sections

### Release Information

=== "Description"

    !!! info ""

        - Basic Information: Details about the release group, show title, and shorthand names.
        - Codec Information: Specifies video format, video codec, and audio codec.
        - Track Names: Defines names for individual tracks (video, audio, subtitles).

=== "Example"

    !!! example ""

        ```ini
        # Basic information
        group=Kaleido-subs
        jp_title=Some random show
        shorthand=${jp_title}
        shorthand_pmx=${shorthand}

        # Codec information
        format=BD 1080p
        vcodec=HEVC x265 10-bit
        acodec=Opus 2.0
        codec_info=${format} ${vcodec} ${acodec}

        # Track names
        vtrack=x265
        atrack=Opus 2.0 @ 192 kb/s
        strack_reg=Full Subtitles [${group}]
        strack_hono=Honorifics [${group}]
        ```

### File Configuration

=== "Description"

    !!! info ""

        - Output Files: Naming conventions for muxed files and creditless versions.
        - Episode Configuration: Specifies episode range and chapter generation settings.
        - Script Components: File paths for subtitle components (dialogue, typesetting, inserts, warnings).

=== "Example"

    !!! example ""

        ```ini
        # Output files
        title=[${group}] ${jp_title} - ${tvdb} - (${codec_info})
        muxdir=[${group}] ${jp_title} S${season} (${codec_info})
        muxout=${muxdir}/$title [$mux.crc].mkv
        ncmuxout=${muxdir}/Creditless/${muxout}

        # Episode configuration
        episodes={01..24}
        chapters=${dialogue}

        # Script components
        dialogue=${episode}/${shorthand} ${episode} - Dialogue.ass
        extra=${episode}/${shorthand} ${episode} - Extra.ass
        TS=${episode}/${shorthand} ${episode} - TS*.ass
        INS=${episode}/${shorthand} ${episode} - INS*.ass
        notes=${episode}/${shorthand} ${episode} - Notes.ass
        render_warning=common/warning.ass
        ```

### Font Settings

=== "Description"

    !!! info ""

        - Font Directories: Locations of episode-specific and common fonts.

=== "Example"

    !!! example ""

        ```ini
        fonts=${episode}/fonts
        common_fonts=common/fonts
        ```

### OP/ED Settings

=== "Description"

    !!! info ""

        - OP/ED Configuration: Configures opening and ending credit sequences, including episode usage and font locations.
        - Creditless Videos: Settings for NCOPs/NCEDs (creditless openings and endings).

=== "Example"

    !!! example ""

        ```ini
        OP1=${OP1}/${shorthand} - OP1.ass
        ED1=${ED1}/${shorthand} - ED1.ass

        NCOP1=${OP1}/${shorthand} - NCOP1 (Premux).mkv
        NCED1=${ED1}/${shorthand} - NCED1 (Premux).mkv
        ```

### Episode Metadata

=== "Description"

    !!! info ""

        - Episode Numbering: Configures numbering scheme to match TVDB, including special episodes and absolute numbers.

=== "Example"

    !!! example ""

        ```ini
        tvdb=S${season}E${episode}
        epabs=${episode}
        ```

## Example Configuration

Below is an example of a typical `sub.properties` file:

!!! example "Default subtitle properties file"

    ```ini
    # Basic information.
    ### TODO: fill this in
    group=Kaleido-subs                                  # Name of the release group
    jp_title=                                           # Japanese title of the show (to be filled in)
    shorthand=${jp_title}                               # Shorthand name, using the Japanese title
    shorthand_pmx=${shorthand}                          # Shorthand name for premux files


    # Codec info
    format=BD 1080p                                     # Video format (Blu-ray, 1080p resolution)
    vcodec=HEVC x265 10-bit                             # Video codec (HEVC x265 with 10-bit color depth)
    acodec=Opus 2.0                                     # Audio codec (Opus 2.0 channel)
    codec_info=${format} ${vcodec} ${acodec}            # Combined codec information string


    # Specific names for individual tracks. Should match codec info.
    vtrack=x265                                         # Video track name
    atrack=Opus 2.0 @ 192 kb/s                          # Audio track name with bitrate
    strack_reg=Full Subtitles [${group}]                # Regular subtitle track name
    strack_hono=Honorifics [${group}]                   # Honorifics subtitle track name


    # Show-related (output) files
    title=[${group}] ${jp_title} - ${tvdb} - (${codec_info})  # Title format for regular episodes
    {SP*}.title=[${group}] ${jp_title} - ${epabs} (${episode}) - ${tvdb} - (${format} ${vcodec} ${acodec})  # Title format for special episodes
    premux=${episode}/*(Premux)*.mkv                    # Path pattern for premux files

    muxdir=[${group}] ${jp_title} (${codec_info})       # Directory name for muxed files
    muxout=${muxdir}/$title [$mux.crc].mkv              # Output filename for muxed files
    ncmuxout=${muxdir}/Creditless/${muxout}             # Output filename for creditless (NC) muxed files


    # Episodes and other basic features.
    episodes={01..24}|SP{1..2}                          # Episode range, including specials
    chapters=${dialogue}                                # Generate chapters from dialogue file


    # Individual script components
    dialogue=${episode}/${shorthand} ${episode} - Dialogue.ass  # Path for dialogue subtitle file
    extra=${episode}/${shorthand} ${episode} - Extra.ass        # Path for extra subtitle file
    TS=${episode}/${shorthand} ${episode} - TS*.ass             # Path pattern for typesetting files
    INS=${episode}/${shorthand} ${episode} - INS*.ass           # Path pattern for insert files
    render_warning=common/warning.ass                           # Path for rendering warning file


    ## Per-episode fonts, e.g. typesetting
    fonts=${episode}/fonts                              # Directory for episode-specific fonts
    ## Common fonts, e.g. dialogue and titles
    common_fonts=common/fonts                           # Directory for common fonts used across episodes


    # OP/ED scripts and episode numbers
    ## Common OP/EDs
    {02..12}.OP_name=NCOP1                              # Opening 1 used in episodes 2-12
    {13..24}.OP_name=NCOP2                              # Opening 2 used in episodes 13-24
    {01..12}.ED_name=NCED1                              # Ending 1 used in episodes 1-12
    {13..24}.ED_name=NCED2                              # Ending 2 used in episodes 13-24

    OP=${OP_name}/${shorthand} ${OP_name}.ass           # Path for opening subtitle file
    ED=${ED_name}/${shorthand} ${ED_name}.ass           # Path for ending subtitle file

    ## Fonts
    opfonts=${OP_name}/fonts                            # Directory for opening-specific fonts
    edfonts=${ED_name}/fonts                            # Directory for ending-specific fonts


    # Creditless
    ncs=NCOP{1..2}|NCED{1..2}                           # Creditless opening and ending patterns

    ncsubs=${episode}/${shorthand}_${episode}.ass       # Path for creditless subtitle file
    ncpremux=${episode}/${shorthand}_${episode} (Premux).mkv  # Path for creditless premux file
    ncfonts=${episode}/fonts                            # Directory for creditless-specific fonts


    ## Episode numbers following TVDB.
    ### Moved to the bottom because it's very spammy.
    tvdb=S${season}E${epnum}                            # TVDB episode numbering format

    season=01                                           # Default season number
    epnum=${episode}                                    # Episode number (same as episode variable)

    ### S00 episodes.
    {SP*}.season=00                                     # Set season to 00 for all special episodes
    SP1.epnum=01                                        # Episode number for Special 1
    SP2.epnum=02                                        # Episode number for Special 2
    SP3.epnum=03                                        # Episode number for Special 3

    ### S00 absolute-ish episode number, used for easier user readability.
    SP1.epabs=07.5                                      # Absolute episode number for Special 1
    SP2.epabs=12.5                                      # Absolute episode number for Special 2
    SP3.epabs=25                                        # Absolute episode number for Special 3
    ```

[//]: # (stubs)
[contributing]: https://github.com/Kaleido-subs/style-guide/pulls
[wikipedia-stubs]: https://en.wikipedia.org/wiki/Wikipedia:Stubs
