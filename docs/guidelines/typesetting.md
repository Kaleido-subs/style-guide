# Typesetting guidelines

We won't go much in-depth about typesetting here,
but we will provide some basic things to be wary of.

## Faux bold/italics and different weights

Try to avoid faux bold and faux italics.
This happens when a line is set in bold or italics,
but there is no supported font for it.

Different weights of the same font introduce a similar problem.
If the font you include doesn't support the weight you've selected,
it will fall back to a similar weight font.
However, if the user has it installed,
the text will not display as intended.

Different weights and italic fonts become a huge problem
when you're using a common font.
Try to avoid using common fonts where reasonable,
and instead try to use a font that looks similar
and has the weight/italics you need.

This will be particularly difficult to avoid for the following types of signs[^common-fonts]:

| Usage                                   | Font Name       |
|---------------------------------------- |-----------------|
| Phone - Android                         | Roboto          |
| Phone - iOS                             | San Francisco   |
| Computer - Mac OS X                     | Helvetica Neue  |
| Computer - Windows                      | Segoe UI        |
| Computer - Ubuntu                       | Ubuntu          |
| Command Line - Unix                     | Ubuntu Mono     |
| Command Line - Windows                  | Lucida Console  |
| Google Search                           | Arial           |
| Google Products (YouTube, Gmail, etc)   | Roboto          |
| Blog Titles - Sans Serif                | Oswald          |
| Blog Titles - Serif                     | Playfair        |

[^common-fonts]: Table courtesy of [Sara Linsley's lettering tutorial](https://github.com/saraoswald/lettering-tutorials/wiki/Signs-and-Labels#choosing-a-label-font)

But there are still some workarounds:

1. Set the exact expected weight in the tags.
   This can be done using \b400, for example.
2. Use \fax to mimic the appearance of italics.
   This must be a negative value,
   and you generally shouldn't go lower than \fax-1.
3. Use the shad trick with \bord to change the appearance of the font weight.

## Masking

Generally speaking,
Kaleido will mask most signs where possible.
This is for a couple reasons:

1. The original sign often doesn't leave a lot of space for additional translated text.
   This makes typesetting very obvious, very distracting, and often more difficult to read.
2. It greatly simplifies the process of typesetting.
   Once a mask is in place, you're free to approach the typesetting however you prefer
   without having to worry about the original sign too much.
   This includes the original blurriness, fonts, and in some extreme cases even colours and shape.

Masking is particularly useful for signs like
papers, texts, webpages, and other particularly dense signs.

However, be careful not to abuse masking either.
It often takes longer, performs worse,
and can easily become a crutch
if you're not careful.

## Illustrator

Illustrator is a powerful tool,
and can be very useful for typesetting,
especially alongside Content Aware Fill from Photoshop.
However, it often suffers from the same problems as masking,
but typically worse.
