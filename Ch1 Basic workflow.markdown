## Status of repository

```git status```

Git has a staging area in which it stores files with changes you want to save that haven't been saved yet.
Putting files in the staging area is like putting things in a box, 
while committing those changes is like putting that box in the mail: 
you can add more things to the box or take things out as often as you want, but once you put it in the mail, you can't make further changes.

git status shows you which files are in this staging area, and which files have changes that haven't yet been put there.
In order to compare the file as it currently is to what you last saved, you can use git diff filename. 
git diff without any filenames will show you all the changes in your repository, while git diff directory will show you the changes to the files in some directory.



## What is in a diff?
```git diff```
A diff is a formatted display of the differences between two sets of files. Git displays diffs like this:

```
diff --git a/report.txt b/report.txt
index e713b17..4c0742a 100644
--- a/report.txt
+++ b/report.txt
@@ -1,4 +1,5 @@
-# Seasonal Dental Surgeries 2017-18
+# Seasonal Dental Surgeries (2017) 2017-18
+# TODO: write new summary
```

This shows:

The command used to produce the output (in this case, diff --git). In it, a and b are placeholders meaning "the first version" and "the second version".
An index line showing keys into Git's internal database of changes. We will explore these in the next chapter.
--- a/report.txt and +++ b/report.txt, wherein lines being removed are prefixed with - and lines being added are prefixed with +.
A line starting with @@ that tells where the changes are being made. The pairs of numbers are start line and number of lines (in that section of the file where changes occurred). This diff output indicates changes starting at line 1, with 5 lines where there were once 4.
A line-by-line listing of the changes with - showing deletions and + showing additions (we have also configured Git to show deletions in red and additions in green). Lines that haven't changed are sometimes shown before and after the ones that have in order to give context; when they appear, they don't have either + or - in front of them.
Desktop programming tools like RStudio can turn diffs like this into a more readable side-by-side display of changes; you can also use standalone tools like DiffMerge or WinMerge.

## What's the first step in saving changes?
```git add filename```
add all changes to the staging area
```git add .```

## How can I tell what's going to be committed?
compare with the latest commit
```git diff -r HEAD```

## How do I commit changes?
To save the changes in the staging area, you use the command git commit. It always saves everything that is in the staging area as one unit: as you will see later, when you want to undo changes to a project, you undo all of a commit or none of it.

When you commit changes, Git requires you to enter a log message. This serves the same purpose as a comment in a program: it tells the next person to examine the repository why you made a change.

By default, Git launches a text editor to let you write this message. To keep things simple, you can use -m "some message in quotes" on the command line to enter a single-line message like this:

## How can I view a repository's history?
The command git log is used to view the log of the project's history. Log entries are shown most recent first, and look like this:

```
commit 0430705487381195993bac9c21512ccfb511056d
Author: Rep Loop <repl@datacamp.com>
Date:   Wed Sep 20 13:42:26 2017 +0000

    Added year to report title.
 ```

The ```commit``` line displays a unique ID for the commit called a hash; we will explore these further in the next chapter. The other lines tell you who made the change, when, and what log message they wrote for the change.

When you run ```git log```, Git automatically uses a pager to show one screen of output at a time. Press the space bar to go down a page or the 'q' key to quit.

You are in the directory dental, which is a Git repository. Use a single Git command to view the repository's history. What is the message on the very first entry in the log (which is displayed last)?

## How can I view a specific file's history?
A project's entire log can be overwhelming, so it's often useful to inspect only the changes to particular files or directories. You can do this using ```git log path```, where path is the path to a specific file or directory. The log for a file shows changes made to that file; the log for a directory shows when files were added or deleted in that directory, rather than when the contents of the directory's files were changed.

e.g. ```git log data/southern.csv```

## How do I write a better log message
Writing a one-line log message with git commit -m "message"is good enough for very small changes, but your collaborators (including your future self) will appreciate more information. If you run git commit without -m "message", Git launches a text editor with a template like this:
```
 # Please enter the commit message for your changes. Lines starting with '#' will be ignored, and an empty message aborts the commit.
 # On branch master
 # Your branch is up-to-date with 'origin/master'.
 #
 # Changes to be committed:
 #       modified:   skynet.R
```
The lines starting with # are comments, and won't be saved. (They are there to remind you what you are supposed to do and what files you have changed.) Your message should go at the top, and may be as long and as detailed as you want.

Use git commit without -m to commit the changes. The Nano editor will open up. Write a meaningful message and use Ctrl+O and Enter to save, and then Ctrl+X to leave the editor.
