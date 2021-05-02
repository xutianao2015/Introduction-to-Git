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

e.g. git checkout branch2
git rm file1
ls
git checkout master
ls
-- still there in master branch.

## How can I create a branch?
You might expect that you would use git branch to create a branch, and indeed this is possible. However, the most common thing you want to do is to create a branch then switch to that branch.

In the previous exercise, you used git checkout branch-name to switch to a branch. To create a branch then switch to it in one step, you add a -b flag, calling``` git checkout -b branch-name```,

The contents of the new branch are initially identical to the contents of the original. Once you start making changes, they only affect the new branch.

## How do I merge two branches?


