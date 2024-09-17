# Group Roles

Subtitling groups are often made up of multiple people,
and each member has a specific role.

This document outlines the most common roles and their responsibilities.
This is done on a per-project basis,
and the roles may be shared or rotated between members,
or a single person may take on multiple roles.

Everyone on the team should be trusted to do their job to the best of their ability,
and be given enough leeway to do so.
If you can't trust someone to do their job to a satisfactory degree,
then they shouldn't be on the team in the first place.

## Project Leader

One of the primary responsibilities of the project leader is to set up the necessary infrastructure.
This ranges from preparing a logical folder structure,
to setting up version control,
and coordinating file sharing so members can access the files they need.

Beyond the technical setup,
the project leader is also responsible for project management.
They gather the staff and assign roles,
and track and update the progress of the project.
If the project is starting to drag,
they are responsible for taking appropriate action,
such as assigning new staff or replacing existing ones,
and in some cases stepping up to the plate themselves to help get the project back on track.

The project leader is often also the person checking the final release candidate to ensure everything looks good and remaining errors are dealt with,
as well as the person releasing the finished project.

In a subtitling project,
the project leader gets the final say on most matters.
If the translator and editor have differing opinions and can't come to an agreement,
the project leader is the one who gets to call the final shot.

## Translator

The translator is responsible for translating the script,
as well as signage.
How much control they have over the final product varies by group,
but they are a vital component of the team whose opinion should be respected.

The base script has a profound impact on the final quality,
so it's paramount that the translator has a firm grasp of both the source language _and_ the target language.
In case they struggle to convey the intended meaning or are afraid their translation may be misunderstood,
they leave comments for the editor to work with.

Ideally,
the translator should understand the source material well enough to be able to make informed decisions on how to best translate certain elements of the script.
This is especially important for things such as terminology.

!!! tip "Optional Role"
     This role is technically optional,
     as there are translations available for most modern titles.
     However, as mentioned previously,
     the base translation heavily influences the final quality,
     so it's almost always best to have a translator in the team.

## Editor

The editor is responsible for how the final script reads.
Their job is to ensure the translation reads well and flows naturally,
while also fixing any mistakes the translator made (or discussing alternative translations with them).

They are expected to have a good understanding of grammar and syntax,
as well as the ability to recognize when something doesn't sound quite right.
They get to draw the line on how adaptive the translation should be.
Ideally, they are brave enough to make changes to better capture the nuance of the source text,
even if it means rewriting large portions of the script.

The editor is also responsible for making sure the text is formatted correctly,
and is easily readable for viewers.
This includes things like line breaks,
slimming down lines if they are too long,
and splitting and joining lines as necessary.

In Kaleido, the editor is king.
They get to decide the direction of the script,
and typically can only be overruled by the project leader.
The tough choices fall on them,
and they are the ones who should address script comments made by the QC.
However, they should still make an effort to discuss changes with the translator,
and take their suggestions into consideration.

No matter how good the translator is,
they almost always benefit from having an editor look over their work.

## Translation Checker

The translation checker is responsible for ensuring the translation is accurate.
They typically work after the editor has made their changes,
and they check whether the translation captures the correct nuances.

Translation checkers can often be viewed as editors who know the source language,
without being burdened by the need to make changes to the script.
This allows them to focus more on the greater picture,
which the editor may miss if they become too caught up on individual lines.

!!! tip "Optional Role"
     This role is _technically_ optional,
     and is sometimes filled by the original translator.
     With a sufficiently experienced translator-editor pair,
     there isn't always a need for a separate translation checker.
     However, it's still a good idea to have an additional pair of eyes to catch anything the editor might have missed.

## Timer

The timer is responsible for timing the translation.
For original translations,
they are often the first person to get to work.
If there is already a timed script available,
they may perform a timing pass at a later date,
but ideally still before editing,
as the timing can influence how the editor may handle certain lines.

The timer may also be responsible for karaoke timing
if the song styler wants to include that.

## Encoder

The encoder is responsible for the video quality of the final release.
They should ensure the best video sources are used,
and that they are filtered to remove artefacting if possible.

They get to call the final shot on all aspects of the video,
and should strive to improve upon the source video
and make an encode that beats out other options,
even at the cost of increased file sizes.

They, along with the project leader,
may also decide whether they want to include additional files,
such as specials or dubbed audio.

## Typesetter(s)

The typesetter is responsible for setting translations for the signage of the show.
This is among the most technically challenging roles,
and often the task that takes the longest to complete.

They should ensure that the typeset text is readable,
performant, and (relatively) consistent across instances.

## Song Styler

The person responsible for styling the songs.
They make sure the lyrics fit with the song's style or visual's aesthetic,
and that they are styled in a way that is pleasing to the eye while remaining readable.
They get to decide how the lyrics should be styled,
including whether karaoke should be included.

This role is often picked up by another member of the team,
but there can also be a or multiple dedicated song stylists.
If none are found,
the project leader or typesetter may create some simple song styling.

## Quality Control/Assurance

The QC is responsible for ensuring the final product meets a baseline level of quality.
This is a multi-faceted role,
and possibly the most difficult to take on.
The QC is expected to be familiar with the tools and software used,
and have a good grasp of the principles of subtitling.
They are also expected to be familiar with common techniques used by all roles of the team,
as well as to make up for any shortcomings during their pass.

The QC is not one who gets to make direct changes to the script,
short of simple things like correcting typos or fixing inconsistencies.
They should leave notes on things that need to be fixed,
and if possible offer suggestions on things the script can be improved on.

!!! danger "Difficult Role"
     Quality Control is not a trivial role,
     and should not be an afterthought.
     They should be experienced enough to catch mistakes that others may miss,
     and this role should not be left in the hands of newbies.

In Kaleido, the QC often creates a pull request with notes and suggestions.
The project leader ensures that all notes are addressed by the appropriate members,
and once the QC is satisfied,
they approve the pull request.

## Other roles

There may be other, highly specialised roles in a group that are not listed here.
These are often advisors who provide advice on specific aspects of the project.
Examples include git masters,
translators who have worked on the source material and can give feedback and advice,
and so on.

These may also be dedicated song translators and editors.
Writing songs is a very specialised skill,
and one that not many translators and editors possess,
so it's not uncommon to outsource these roles to specialists.
