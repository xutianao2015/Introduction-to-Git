## How can I create a brand new repository?
If you want to create a repository for a new project in the current working directory, you can simply say ```git init project-name```, where "project-name" is the name you want the new repository's root directory to have.

One thing you should not do is create one Git repository inside another. While Git does allow this, updating nested repositories becomes very complicated very quickly, since you need to tell Git which of the two .git directories the update is to be stored in.

## How can I turn an existing project into a Git repository?
you will often want to convert existing projects into repositories. Doing so is simple, just run:

```git init```in the project's root directory, or:

```git init /path/to/project```
from anywhere else on your computer.

## How can I create a copy of an existing repository?
In each case, you will clone an existing repository instead of creating a new one. Cloning a repository does exactly what the name suggests: it creates a copy of an existing repository (including all of its history) in a new directory.

To clone a repository, use the command ```git clone URL```, where URL identifies the repository you want to clone. This will normally be something like
```https://github.com/datacamp/project.git```

but for this lesson, we will use a repository on the local file system, so you can just use a path to that directory. When you clone a repository, Git uses the name of the existing repository as the name of the clone's root directory, for example:

```git clone /existing/project```

will create a new directory called project inside your home directory. If you want to call the clone something else, add the directory name you want to the command:

```git clone /existing/project newprojectname```

## How can I find out where a cloned repository originated?
When you a clone a repository, Git remembers where the original repository was. It does this by storing a ```remote``` in the new repository's configuration. A remote is like a browser bookmark with a name and a URL.

If you use an online git repository hosting service like GitHub or Bitbucket, a common task would be that you clone a repository from that site to work locally on your computer. Then the copy on the website is the remote.

If you are in a repository, you can list the names of its remotes using git remote.

If you want more information, you can use git remote -v (for "verbose"), which shows the remote's URLs. Note that "URLs" is plural: it's possible for a remote to have several URLs associated with it for different purposes, though in practice each remote is almost always paired with just one URL.