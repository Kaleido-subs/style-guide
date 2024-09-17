# Getting Started

## Prerequisites

To begin using this template for your subtitling project,
you'll need to ensure you have the necessary dependencies installed.

- [SubKt](https://github.com/Myaamori/SubKt) for subtitle processing
- [mkvmerge](https://mkvtoolnix.download/downloads.html) for video muxing
- A compatible version of the Java Development Kit (JDK)

!!! warning "JDK version"
    Currently, JDK versions 14, 15, and 16 are supported,
    with versions 14 and 15 working out-of-the-box with SubKt.
    Later versions _may_ work.
    If you encounter any issues,
    make sure Gradle is using the correct JDK version.

## Setting up your project

Navigate to the [project-template](https://github.com/Kaleido-subs/project-template) GitHub page,
then click the "Use this template" button in the top-right corner of the page
to create a new repository based on this template.

!["Use this template" button](./img/use-this-template.png)

Next, configure your project files.
Generally speaking,
you'll only need to configure the following files:

- `build.gradle.kts`
- `sub.properties`

For more details on how to configure these files,
see their respective documentation:

- [build.gradle.kts](./build-script/index.md)
- [sub.properties](./properties/index.md)

## Building your project subtitles

You can build your project using the Gradle wrapper.

!!! example "Calling the Gradle wrapper"
    === ":fontawesome-brands-windows: Windows"
        ```sh
        gradlew.bat mux.01
        ```

    === ":fontawesome-brands-linux: Unix"
        ```sh
        ./gradlew mux.01
        ```

!!! tip "Using other commands"
     You can replace `mux` with other commands like `chapters`, `merge`, `cleanmerge`, or `swap`
     depending on your needs.
     The output of these commands (except for `mux`) can be found in the `build/` directory.

The output of the `mux` command is a single `.mkv` file
with the subtitle embedded in it
and any other associated files attached to it.

By default,
the output directory is `[${group}] ${jp_title} (${codec_info})`.
This directory will contain the final muxed `.mkv` files,
named according to the `muxout` pattern:
`[${group}] ${jp_title} - ${tvdb} - (${codec_info}) [$mux.crc].mkv`

!!! tip "Changing the output directory"
    You can change the output directory and filename pattern
    by editing the `muxout` and `title` properties in the `sub.properties` file!
    See the [properties documentation](./properties/index.md) for more information.
