## What is a branch?
If you don't use version control, a common workflow is to create different subdirectories to hold different versions of your project in different states, for example development and final. Of course, then you always end up with final-updated and final-updated-revised as well. The problem with this is that it becomes difficult to work out if you have the right version of each file in the right subdirectory, and you risk losing work.

One of the reasons Git is popular is its support for creating branches, which allows you to have multiple versions of your work, and lets you track each version systematically.

Each branch is like a parallel universe: changes you make in one branch do not affect other branches (until you merge them back together).

## How can I see what branches my repository has?
By default, every Git repository has a branch called master (which is why you have been seeing that word in Git's output in previous lessons). To list all of the branches in a repository, you can run the command ```git branch```. The branch you are currently in will be shown with a ```*``` beside its name.

## How can I view the differences between branches?
Branches and revisions are closely connected, and commands that work on the latter usually work on the former. For example, just as ```git diff revision-1..revision-2``` shows the difference between two versions of a repository, ```git diff branch-1..branch-2``` shows the difference between two branches.

## How can I switch from one branch to another?
You previously used git checkout with a commit hash to switch the repository state to that hash. You can also use git checkout with the name of a branch to switch to that branch.

Two notes:

When you run git branch, it puts a * beside the name of the branch you are currently in.
Git will only let you do this if all of your changes have been committed. You can get around this, but it is outside the scope of this course.

In this exercise, you'll also make use of git rm. This removes the file (just like the shell command rm) then stages the removal of that file with git add, all in one step.

e.g. 
```git checkout branch2
git rm file1
ls
git checkout master
ls
```
-- still there in master branch.

## How can I create a branch?
You might expect that you would use git branch to create a branch, and indeed this is possible. However, the most common thing you want to do is to create a branch then switch to that branch.

In the previous exercise, you used git checkout branch-name to switch to a branch. To create a branch then switch to it in one step, you add a -b flag, calling``` git checkout -b branch-name```,

The contents of the new branch are initially identical to the contents of the original. Once you start making changes, they only affect the new branch.

## How do I merge two branches?
Branching lets you create parallel universes; merging is how you bring them back together. When you merge one branch (call it the source) into another (call it the destination), Git incorporates the changes made to the source branch into the destination branch. If those changes don't overlap, the result is a new commit in the destination branch that includes everything from the source branch (the next exercises describe what happens if there are conflicts).

To merge two branches, you run ```git merge source destination``` (without .. between the two branch names). Git automatically opens an editor so that you can write a log message for the merge; you can either keep its default message or fill in something more informative.

```
You are in the master branch of the dental repository. Merge the changes from the summary-statistics branch (the source) into the master branch (the destination) with the message "Merging summary statistics."
```
e.g. ```git merge summary-statistics master```

## What are conflicts?
Sometimes the changes in two branches will conflict with each other: for example, bug fixes might touch the same lines of code, or analyses in two different branches may both append new (and different) records to a summary data file. In this case, Git relies on you to reconcile the conflicting changes.

The file todo.txt initially contains these two lines:
```
A) Write report.
B) Submit report.
```
You create a branch called update and modify the file to be:
```
A) Write report.
B) Submit final version.
C) Submit expenses.
```
You then switch back to the master branch and delete the first line, so that the file contains:

```B) Submit report.```
When you try to merge update and master, what conflicts does Git report? You can use ```git diff master..update``` to view the difference between the two branches.

## How can I merge two branches with conflicts?
When there is a conflict during a merge, Git tells you that there's a problem, and running git status after the merge reminds you which files have conflicts that you need to resolve by printing both modified: beside the files' names.

Inside the file, Git leaves markers that look like this to tell you where the conflicts occurred:

 ```
 <<<<<<< destination-branch-name
 ...changes from the destination branch...
 =======
 ...changes from the source branch...
 >>>>>>> source-branch-name
 ```
In many cases, the destination branch name will be ```HEAD``` because you will be merging into the current branch. To resolve the conflict, edit the file to remove the markers and make whatever other changes are needed to reconcile the changes, then commit those changes.

e.g. 
    ```
    It turns out that report.txt has some conflicts. Use nano report.txt to open it and remove some lines so that only the second title is kept. Save your work with Ctrl+O and Enter, and then leave the editor with Ctrl+X. You can easily remove entire lines with Ctrl+K.
    ```
