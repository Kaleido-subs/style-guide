# Release Description Template

This document outlines the structure and content of a typical anime release description.

It's designed to provide comprehensive information about the release,
including technical details, staff credits, usage guidelines, and social media links.

## Cover Art and Basic Information

The description typically starts with a cover image of the anime,
followed by a table containing basic information about the series:

- Title: The official title of the anime
    - This will typically be the romanized title
- TVDB ID: The identifier for the series on TheTVDB
- AniDB ID: The identifier for the series on AniDB
- Season: The season number and ordering information
    - The order is obtained from [TVDB][tvdb]

!!! example "Basic Information Table"
    ```
    | Anime Information |                                 |
    | ----------------- | ------------------------------- |
    | **Title**         | Anime Name                      |
    | **TVDB ID**       | [TVDB ID][tvdb]                 |
    | **AniDB ID**      | [AniDB ID][anidb]               |
    | **Season**        | Season Number (Watch Order)     |
    ```

## Staff Credits

Two tables are usually included to credit the staff involved in the release:

1. Episode Staff
      - Lists roles such as Translation, Editing, Encoding, Timing, Typesetting, and Quality Control,
   along with the contributors for each role.
2. Song Staff
      - Credits for Opening and Ending themes and insert songs,
        including Translation, Editing, (Karaoke) Timing, Typesetting, and Song Styling.

If the song list is too large,
it can be split off into a separate table.

!!! example "Example"
    === "Combined"
        ```
        | Episode Staff         |                    |     | Song Staff            | Opening        | Ending         |
        | --------------------- | ------------------ | --- | --------------------- | -------------- | -------------- |
        | **Translation**       | Translator A       |     | **Translation**       | Translater I   | Translater I   |
        | **Translation Check** | Checker B          |     | **Translation Check** | Checker J      | Checker J      |
        |                       | Checker C          |     | **Editing**           | Editor K       | Editor K       |
        | **Editing**           | Editor D           |     | **Timing**            | Timer M        | Timer M        |
        | **Encode**            | Editor D           |     | **Typesetting**       | Timer M        | Typesetter N   |
        | **Timing**            | Timer E            |     |                       | Typesetter O   |                |
        | **Typesetting**       | Editor D           |     | **Song Styling**      | Timer M        | Timer M        |
        ```
    === "Split off"
        ```
        | Episode Staff         |              |
        | --------------------- | ------------ |
        | **Translation**       | Translator A |
        | **Translation Check** | Checker B    |
        | **Editing**           | Editor C     |
        | **Encode**            | Encoder D    |
        | **Timing**            | Timer E      |
        | **Typesetting**       | Typesetter F |
        | **Quality Control**   | QC G         |
        |                       | QC H         |

        | Song Staff  | Translation  | Editing  | (Karaoke) Timing | Song Styling | Typesetting  |
        | ----------- | ------------ | -------- | ---------------- | ------------ | ------------ |
        | OP          | Translator I | Editor K | Timer M          | Styler Q     | Typesetter O |
        | ED (S01E01) | Translator J | Editor L | Timer N          | Styler R     | Typesetter O |
        | ED (S01E02) | Translator J | Editor L | Timer N          | Styler R     | Typesetter O |
        | ED (S01E03) | Translator J | Editor K | Timer N          | Styler R     | Typesetter O |
        | ED (S01E04) | Translator J | Editor L | Timer N          | Styler R     | Typesetter O |
        | ED (S01E05) | Translator J | Editor K | Timer N          | Styler R     | Typesetter O |
        ...
        ```

## Technical Information

### Video

Provides details about the video source and specifications:

- Sources: Origin of the video (e.g., Blu-ray)
- Resolution: Video resolution (e.g., 1920x1080p)
- Codec: Video codec used (e.g., H.265 10-bit)
- Aspect Ratio: The aspect ratio of the video
- Extra: Links to video comparisons and media info

!!! example "Video Table"
    ```
    |                  |                                 |                        |
    | ---------------- | ------------------------------- | ---------------------- |
    | **Sources**      | [Blu-ray (company)][source-url] |                        |
    | **Resolution**   | 1920x1080p                      |                        |
    | **Codec**        | H.265 (x265) 10-bit             |                        |
    | **Aspect Ratio** | 16:9                            |                        |
    | **Extra**        | [Video Comparison][slowpics]    | [MediaInfo][mediainfo] |
    ```

### Audio

A table describing the audio track(s):

- Track language
- Codec
- Channel configuration
- Bitrate
- Source
- Default and forced flags

!!! example "Audio Table"
    === "Mono Audio"
        ```
        | Track        | Codec | Channels | Bitrate  | Source                          | Default | Forced |
        | ------------ | ----- | -------- | -------- | ------------------------------- | ------- | ------ |
        | **Japanese** | Opus  | 2.0      | 192 kbps | [Blu-ray (company)][source-url] | Yes     | No     |
        ```
    === "Dual Audio"
        ```
        | Track        | Codec | Channels | Bitrate  | Source                          | Default | Forced |
        | ------------ | ----- | -------- | -------- | ------------------------------- | ------- | ------ |
        | **Japanese** | Opus  | 2.0      | 192 kbps | [Blu-ray (company)][source-url] | Yes     | No     |
        | **English**  | AAC   | 2.0      | 192 kbps | [Blu-ray (company)][source-url] | Yes     | No     |
        ```

### Subtitles

A table listing available subtitle tracks:

- Track description
- Language
- Language code
- Format (e.g., ASS, SRT)
- Default and forced status

!!! example "Subtitle Table"
    === "Regular Tracks"
        ```
        | Track                             | Language | Language Code | Format | Default | Forced |
        | --------------------------------- | -------- | ------------- | ------ | ------- | ------ |
        | **Full Subtitles**                | English  | eng           | ASS    | Yes     | No     |
        | **Full Subtitles (Honorifics)**   | English  | enm           | ASS    | Yes     | No     |
        ```
    === "Dual Audio"
        ```
        | Track                             | Language | Language Code | Format | Default | Forced |
        | --------------------------------- | -------- | ------------- | ------ | ------- | ------ |
        | **Full Subtitles**                | English  | eng           | ASS    | Yes     | No     |
        | **Full Subtitles (Honorifics)**   | English  | enm           | ASS    | Yes     | No     |
        | **Signs & Songs**                 | English  | sng           | ASS    | No      | Yes    |
        ```
    === "Extra Tracks"
        ```
        | Track                             | Language | Language Code | Format | Default | Forced |
        | --------------------------------- | -------- | ------------- | ------ | ------- | ------ |
        | **Full Subtitles**                | English  | eng           | ASS    | Yes     | No     |
        | **Full Subtitles (Honorifics)**   | English  | enm           | ASS    | Yes     | No     |
        | **Full Subtitles (Trivia Notes)** | English  | eng           | ASS    | No      | No     |
        ```

## Additional Information

- Special features of the release (e.g., alternative subtitle tracks)
- Contact information (e.g., Discord server link)
- Social media links (e.g., Twitter)
- Supported media players
- Usage and redistribution guidelines
- Offers for additional resources (e.g., song styling for other groups)

[tvdb]: https://www.thetvdb.com/
