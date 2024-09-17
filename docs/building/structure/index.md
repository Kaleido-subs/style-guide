# Project structure

By default,
it assumes the following directory structure:

!!! example "Project Directory"
    ```tree
    Project Directory                                       # Root directory of the project
    ├── 01                                                  # Directory for episode 1
    │   ├── NewShow - S01E01 (Premux) [ABCD1234].mkv        # Raw video file for episode 1
    │   ├── NewShow 01 - Dialogue.ass                       # Main dialogue subtitle file for episode 1
    │   ├── NewShow 01 - OP.ass                             # Opening song subtitle file for episode 1
    │   ├── NewShow 01 - TS (Actor 1).ass                   # Typesetting subtitle file for Actor 1 in episode 1
    │   ├── NewShow 01 - TS (Actor 2).ass                   # Typesetting subtitle file for Actor 2 in episode 1
    │   ├── NewShow 01 - TS (Actor 3).ass                   # Typesetting subtitle file for Actor 3 in episode 1
    │   └── fonts                                           # Directory for episode-specific fonts
    │       └── ...
    ├── 02                                                  # Directory for episode 2
    │   ├── NewShow - S01E02 (Premux) [ABCD1234].mkv        # Raw video file for episode 2
    │   ├── NewShow 02 - Dialogue.ass                       # Main dialogue subtitle file for episode 2
    │   ├── NewShow 02 - TS.ass                             # Typesetting subtitle file for episode 2
    │   └── fonts                                           # Directory for episode-specific fonts
    │       └── ...
    ├── ED1                                                 # Directory for ending 1
    │   ├── NewShow - ED1 (Premux) [ABCD1234].mkv           # Raw video file for ending 1
    │   ├── NewShow - ED1.ass                               # Subtitle file for ending 1 (includes both lyrics and typesetting)
    │   └── fonts                                           # Directory for ending-specific fonts
    │       └── ...
    ├── OP1                                                 # Directory for opening 1
    │   ├── NewShow - OP1 (Premux) [ABCD1234].mkv           # Raw video file for opening 1
    │   ├── NewShow - OP1.ass                               # Subtitle file for opening 1 (includes both lyrics and typesetting)
    │   └── fonts                                           # Directory for opening-specific fonts
    │       └── ...
    ├── common                                              # Directory for common files
    │   ├── fonts                                           # Directory for fonts used across multiple episodes
    │   │   ├── LinotypeFinnegan Medium.ttf                 # Default dialogue font
    │   │   └── LinotypeFinnegan MediumItalic.ttf           # Default dialogue font
    │   └── warning.ass                                     # Subtitle file containing a warning about rendering issues
    ├── gradle                                              # Directory for Gradle build tool files
    │   └── wrapper                                         # Gradle wrapper directory
    │       ├── gradle-wrapper.jar                          # Gradle wrapper JAR file
    │       └── gradle-wrapper.properties                   # Gradle wrapper properties file
    ├── README.md                                           # Project README file
    ├── build.gradle.kts                                    # Gradle build script
    ├── gradle.properties                                   # Gradle properties file
    ├── gradlew                                             # Gradle wrapper script for Unix-like systems
    ├── gradlew.bat                                         # Gradle wrapper script for Windows
    ├── settings.gradle.kts                                 # Gradle settings file
    └── sub.properties                                      # Subtitle properties file
    ```

??? example "Example of a real project structure"
    ```tree
    Blue-Archive
    |-- 01
    |   |-- Blue Archive The Animation - S01E01 (Premux) [A4B6D23B].mkv
    |   |-- BlueArchive 01 - Dialogue.ass
    |   |-- BlueArchive 01 - OP.ass
    |   |-- BlueArchive 01 - TS (Gry).ass
    |   |-- BlueArchive 01 - TS (Light).ass
    |   |-- BlueArchive 01 - TS (MSO).ass
    |   |-- BlueArchive 01 - TS (Period).ass
    |   |-- BlueArchive 01 - TS (petzku).ass
    |   `-- fonts
    |       |-- ...
    |-- 02
    |   |-- Blue Archive The Animation - S01E02 (Premux) [DCFED1AB].mkv
    |   |-- BlueArchive 02 - Dialogue.ass
    |   |-- BlueArchive 02 - TS (Light).ass
    |   |-- BlueArchive 02 - TS (MSO).ass
    |   `-- fonts
    |       |-- ...
    |-- 03
    |   |-- Blue Archive The Animation - S01E03 (Premux) [38000900].mkv
    |   |-- BlueArchive 03 - Dialogue.ass
    |   |-- BlueArchive 03 - TS (Light).ass
    |   `-- fonts
    |       |-- ...
    |-- 04
    |   |-- Blue Archive The Animation - S01E04 (Premux) [3AA19D61].mkv
    |   |-- BlueArchive 04 - Dialogue.ass
    |   |-- BlueArchive 04 - Extra.ass
    |   |-- BlueArchive 04 - TS (Light).ass
    |   |-- BlueArchive 04 - TS (petzku).ass
    |   `-- fonts
    |       |-- ...
    |-- 05
    |   |-- Blue Archive The Animation - S01E05 (Premux) [83434195].mkv
    |   |-- BlueArchive 05 - Dialogue.ass
    |   |-- BlueArchive 05 - TS (Light).ass
    |   `-- fonts
    |       |-- ...
    |-- 06
    |   |-- Blue Archive The Animation - S01E06 (Premux) [4F14C2AE].mkv
    |   |-- BlueArchive 06 - Dialogue.ass
    |   |-- BlueArchive 06 - Extra.ass
    |   |-- BlueArchive 06 - TS (Light).ass
    |   |-- BlueArchive 06 - TS (petzku).ass
    |   `-- fonts
    |       |-- ...
    |-- 07
    |   |-- Blue Archive The Animation - S01E07 (Premux) [3B0015AF].mkv
    |   |-- BlueArchive 07 - Dialogue.ass
    |   |-- BlueArchive 07 - TS (Light).ass
    |   `-- fonts
    |       |-- ...
    |-- 08
    |   |-- Blue Archive The Animation - S01E08 (Premux) [A5674D39].mkv
    |   |-- BlueArchive 08 - Dialogue.ass
    |   |-- BlueArchive 08 - TS (Light).ass
    |   |-- BlueArchive 08 - TS (petzku).ass
    |   `-- fonts
    |       |-- ...
    |-- 09
    |   |-- Blue Archive The Animation - S01E09 (Premux) [C6C9D1E0].mkv
    |   |-- BlueArchive 09 - Dialogue.ass
    |   |-- BlueArchive 09 - TS (Light).ass
    |   |-- Whiteboard.ass
    |   `-- fonts
    |       |-- ...
    |-- 10
    |   |-- Blue Archive The Animation - S01E10 (Premux) [C077087E].mkv
    |   |-- BlueArchive 10 - Dialogue.ass
    |   |-- BlueArchive 10 - TS (Light).ass
    |   `-- fonts
    |       |-- ...
    |-- 11
    |   |-- Blue Archive The Animation - S01E11 (Premux) [DC03E7BE].mkv
    |   |-- BlueArchive 11 - Dialogue.ass
    |   |-- BlueArchive 11 - TS (Light).ass
    |   `-- fonts
    |       |-- ...
    |-- 12
    |   |-- Blue Archive The Animation - S01E12 (Premux) [1ADD8F6D].mkv
    |   |-- BlueArchive 12 - Dialogue.ass
    |   |-- BlueArchive 12 - INS.ass
    |   |-- BlueArchive 12 - TS (Light).ass
    |   |-- BlueArchive 12 - TS (petzku).ass
    |   `-- fonts
    |       |-- ...
    |-- NCED1
    |   |-- Blue Archive The Animation - NCED1 (Premux) [8C8AD616].mkv
    |   |-- BlueArchive NCED1.ass
    |   `-- fonts
    |       |-- ...
    |-- NCOP1
    |   |-- Blue Archive The Animation - NCOP1 (Premux) [BE45148E].mkv
    |   |-- BlueArchive NCOP1.ass
    |   `-- fonts
    |       |-- ...
    |-- README.md
    |-- build.gradle.kts
    |-- common
    |   |-- fonts
    |   |   |-- LinotypeFinnegan Medium.ttf
    |   |   |-- LinotypeFinnegan MediumItalic.ttf
    |   |   `-- RoGSanSrfStd-UB.otf
    |   `-- warning.ass
    |-- gradle
    |   `-- wrapper
    |       |-- gradle-wrapper.jar
    |       `-- gradle-wrapper.properties
    |-- gradle.properties
    |-- gradlew
    |-- gradlew.bat
    |-- settings.gradle.kts
    `-- sub.properties
    ```
