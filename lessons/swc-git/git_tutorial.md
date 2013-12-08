---
layout: lesson
root: ../..
title: Version Control with Git Tutorial
---

1. Git Inroduction ([slides](http://mollygibson.github.io/2014-01-08-iastate/lessons/swc-git/slides/01-Introduction/01-GitIntroduction.pdf))
   * [Exercise 1: Download and Install Git](#install) 
   * [Exercise 2: Configure Git and Initialize Repository](#configure-git-and-initialize-repository)
2. Working Locally (slides)
   * [Exercise 3: Local Git Workflow](#local-git-workflow)
3. Working with Github (slides)
   * [Exercise 4: Collaborate on Github Project](#collaborate-on-github)
4. Branching and Merging (slides) 
   * [Exercise 5: Branch and Merge](#branch-merge)

### <a name="install"></a>Exercise 1: Download and Install Git
#### Windows
Install [Git Bash](http://msysgit.github.io/). This give you Bash as well as Git.
#### MacOSX
Download the graphical Git installer from the [Google Code page](http://code.google.com/p/git-osx-installer).
#### Unix
If you are on a Debian-based distribution like Ubuntu, try apt-get:

```
$ apt-get install git
```

If you're on Fedora, you can use yum:

```
$ yum install git-core
```

---
### <a name="configure-git-and-initialize-repository"></a>Exercise 2: Configure Git and Initialize Repository

#### Configure Git
The first time we use Git on a new machine, we need to configure a few things:

```
$ git config --global user.name "Your name goes here"
$ git config --global user.email you@yourdomain.com
$ git config --global core.editor vim
$ git config color.ui auto
```

Git commands are written `git verb`,
where `verb` is what we actually want it to do.
In this case,
we're telling Git:

*   our name and email address,
*   what our favorite text editor is,
*   to colorize output, and
*   that we want to use these settings globally (i.e., for every project),

The four commands above only need to be run once:
Git will remember the settings until we change them.
Once Git is configured,
we can start using Git.

Check your configuration with:

```
$ git config --list
```

#### Initialize a Git Repository

Create a folder called git_tutorial and initialize an empty git repository:

```
$ mkdir git_tutorial
$ cd git_tutorial
$ git init
```

if we use `ls -a` to see hidden files, we can see the git has created a hidden directory called `.git`:

```
$ ls -a
.  ..  .git
```

This directory stores information about our project in this directory. If you ever delete it, you will lose the history of your project. 

---
### <a name="local-git-workflow"></a> Exercise 3: Local Git Workflow 


Remember the git file workflow:

![lifecycle](imgs/git_workflow.png)


1. Create an AUTHORS file, a TODO file, and a README file in the `git_tutorial` repository you created in the last exercise.
2. Inside it, initialize an empty git repository (`git init`)
3. Create an AUTHORS file, a TODO file and a README file.
4. Add the AUTHORS file to the staging area. (`git add`)
5. Check the status of the repository (`git status`)
6. Add the two other files to the staging area (`git add`)
7. Commit your changes (`git commit`).
8. Now rename the AUTHORS file to CONTRIBUTORS (`git mv`) and commit.
9. Add your name to the CONTRIBUTORS file.
10. Cancel the changes you've made to this file. Tips: look at what git status tells you to do.
11. Create a src directory, and add a python script that prints the first 10 integers of the Fibonacci suite. Add and commit this script.
12. Remove this file using git rm (but don't commit it).
13. Try cancelling those changes. What's happening?

---
### <a name="collaborate-on-github"></a> Exercise 4: Collaborate on Github

1. Go to github.com and create an account. 


---
### <a name="branch-merge"></a> Exercise 5: Branch and Merge








