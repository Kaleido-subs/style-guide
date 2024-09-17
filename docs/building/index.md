# Building our subtitles

This document covers a high-level overview of SubKt,
our build script template,
and how to use and modify it depending on the project.

## What is SubKt?

SubKt is a build script template for subtitles.
It is designed to be a starting point for any project,
and can be modified to fit the needs of said project.
It also includes in-depth [documentation](https://github.com/TypesettingTools/SubKt/blob/master/docs/subkt/index.md).

If includes a lot of useful features
for building a subtitle file
using individual components,
allowing subtitlers to work with individual files
without having to worry about touching files
that other subtitlers are working in.

It also comes with muxing functionality,
adding stuff like font checking,
CRC32 hashing,
batching,
distributing,
and more.


## Kaleido project template

Kaleido uses SubKt to build subtitle files and mux files.

The [Kaleido project template][project-template]
is a Github repository that can be used as a template
for new projects.
It includes a pre-configured build setup,
as well as a basic project structure.

!!! warning "Project-dependent settings"
    Our template is designed to be a starting point for any new project,
    which means you **must** modify the template to fit the needs of your project
    every time you start a new one!

For a quickstart guide,
see the [getting started](./getting-started.md) document.

For information on how to modify the template,
see the following documents:

- [Project structure](./structure/index.md)
- [Subtitle Properties](./properties/index.md)
- [Build Script](./build-script/index.md)

For running the build script,
see the [building your project subtitles](./getting-started.md/#building-your-project-subtitles) section.

[//]: # (TODO: add links to the other documents)
[project-template]: https://github.com/Kaleido-subs/project-template
