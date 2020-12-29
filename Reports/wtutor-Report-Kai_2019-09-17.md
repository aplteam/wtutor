# Beautifying WTUTOR and WTUTOR95


## Overview

Goal was to bring both workspaces up to date for modern PCs and modern (usually quite big) screens.

For checking the result load either wtutor.dws or wtutor95.dws.

For development load development.dws; this workspace provides detailed information via `⎕LX`. The workspaces wtutor.dws and wtutor95.dws are assembled from the development workspace. See the `⍙Info` function in development.dws.

The topics and their associated table of contents are saved in the two component files wtutor.dcf and wtutor95.dcf.

## Detailed Report

In the process I have performed the following actions:

* The main GUI (the box presenting the different topcis) is now readable on screens of any size.

  * I also fixed the problem that after returning from a lesson the first {CursorUp}/{CursorDown} was ignored.

* The sub GUI (showing the lessons) is now big enough to display the lessons properly.

* I have deleted quite a range of functions all aiming to give the user the option to edit all lessons of a specific topic in a single variable.

* I have cleaned the WS from all variables that are created on the fly while watching the lessions.

* All objects with names using (originally) underlined characters have been renamed to uppercase ones.

* In some important functions GoTos were replaced by control structures.

* I have added a function `⍙Info` with detailed documentation.

* The lesson regarding Visual Basic was removed because it was never displayed due to a typo anyway and it's oudated stuff.

* All references to Motif and Linux removed: this is a Windows-only application.

* A function `∆Reset`...
  * deletes all superfluous variables
  * sets `⎕LX←#.LX`
  * Sets a couple of system variables: `⎕IO`, `⎕ML`, `⎕DIV` and `⎕WX`.

* Note that all global variables and all "public" functions were renamed so that they start with a `∆` character. Nothing else does.

* The caption of the main window shows the number of tutorials now.

* The list carries numbers now for easier identification.

* The "Lesson" GUI now also shows the total number of lessons for the current topic.

* Function `QUIT_IF_VERSION7` was deleted.

* The automatic state change of the session to full-screen mode was removed.

* The topics are saved in component files in order to make assembling the workspaces easy.

  There is a set of functions available for both, read and write:

  `⍙ReadWTUTOR`, `⍙ReadWTUTOR95`, `⍙WriteWTUTOR` and `⍙WriteWTUTOR95`.

### More changes (2018-12-14)

* All lessons checked for whether they do what they are supposed to do.

  As a side effect bugs 1581, 1582, 1583, 1584 and 1585 reported.

  This requiered quite a number of changes: missing icons, missing DLLs, replacing calls to (now) non-existent programs and more.

* `⍙EditBooks` now injects the topic number into the header of each topic.

* True global variable renamed from `ORIG` to `∆ORIG` to make the workspaces manageable.

* Missing functions added (deleted by accident earlier on).

### More changes (2018-12-18)

* The two workspaces are now united into a single one: just wtutor.dws

* Because of this change the function `⍙ReadWTUTOR95` and `⍙WriteWTUTOR95` have been removed.

* The main GUI has now an edit field "Filter" in order to make is easier for the user to find a certain topic. This seemed appropriate because there are now 55 topics!

* `⍙EditBooks` now writes `∆TOPICS`, `∆BOOKS` and all other global variables to a component file after prompting the user.