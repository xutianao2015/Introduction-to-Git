# status of repository

```git status```

Git has a staging area in which it stores files with changes you want to save that haven't been saved yet.
Putting files in the staging area is like putting things in a box, 
while committing those changes is like putting that box in the mail: 
you can add more things to the box or take things out as often as you want, but once you put it in the mail, you can't make further changes.

git status shows you which files are in this staging area, and which files have changes that haven't yet been put there.
In order to compare the file as it currently is to what you last saved, you can use git diff filename. 
git diff without any filenames will show you all the changes in your repository, while git diff directory will show you the changes to the files in some directory.



# What is in a diff?
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

# What's the first step in saving changes?
```git add filename```
add all changes to the staging area
```git add .```

# How can I tell what's going to be committed?
compare with the latest commit
```git diff -r HEAD```

