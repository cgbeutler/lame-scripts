![Bach](http://www.jsbach.net/bass/elements/bass-hanewinckel-title.jpg)

TODO: make a picture of bach with tools... instead of a bass

# ToolBachs
Scripts to help make life less lame!

### br.sh
Useful for when you need a visual break on the command line.
(Better than hitting enter a bunch of times...)

Usage:

    br [-f fg_color] [-b bg_color] [a label for the bar]

With no args, it creates a line of `=` signs accross the screen with a red backround.

-f [color] sets the foreground color for the break

-b [color] sets the background color for the break

any non-arg things will be turned into a label for the break. This makes it easy to search back through the command terminal for stuff.

Other Possible Usages:

    br; run-some-long-output-thang; br command 1 complete; run-some-other-long-thing; br command 2 complete

### gits.py
Quick python script that lists all of the git repos in the current directory

The plan is to later expand this to provide more information. If this doesn't get more useful... it may get cut.

### qsync.sh
Sets up quick sync stuff that uses `rsync` to keep two directories synced.

This is designed for people who like to work on their own computer with all their setup files. This does not mess with the target folders, just the one this script run from.

`qsync.sh setup` places a `.qsync` file in the current directory. Ignored files and targets are loaded from this file.

`qsync.sh pull [target]` can be used in directories with a `.qsync` file to sync the directory with the targets changes.

`qsync.sh lpull [target]` do a dry run of `pull` without changes being applied. (uses -n on rsync)

`qsync.sh push [target]` can be used in directories with a `.qsync` file to sync the directory's changes with the target.

`qsync.sh lpush [target]` do a dry run of `push` without changes being applied. (uses -n on rsync)


###### Example of use:
    qsync.sh setup
    [edit the .qsync file how you want it]
    qsync.sh pull work-files
    [edit the work files]
    qsync.sh push work-files

##### Issues to be aware of
Keep in mind that qsync just uses rsync. This means that moving and deleting files will not be applied. This also means that you cannot make changes in both the target and host without one of them being wiped out! I would recommend using rsync for a while first so you get the idea of how it works. If you need more power, use git or something. This is not meant to be a full on rpm. This is just a quick and dirty wrapper for rsync.
