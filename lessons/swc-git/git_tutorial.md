---
layout: lesson
root: ../..
title: ISU Bootcamp Git Tutorial
---
## <a name="top"></a>Outline

1. Git Inroduction and Working Locally ([slides](http://mollygibson.github.io/2014-01-08-iastate/lessons/swc-git/slides/01-Introduction/01-GitIntroduction.pdf))
   * [Exercise 1: Download and Install Git](#install) 
   * [Exercise 2: Configure Git and Initialize Repository](#configure-git-and-initialize-repository)
   * [Exercise 3: Local Git Workflow](#local-git-workflow)
3. Working with Github ([slides](http://mollygibson.github.io/2014-01-08-iastate/lessons/swc-git/slides/02-Github/02-Github.pdf))
   * [Exercise 4: Collaborate on Github Project](#collaborate-on-github)     
4. Branching and Merging ([slides](http://mollygibson.github.io/2014-01-08-iastate/lessons/swc-git/slides/03-Branching/03-Branching.pdf)) 
   * [Exercise 5: Branch and Merge](#branch-merge)
5. Extras
   * [Resources](#resources)
  
---   
   
### <a name="install"></a><font color='red'>Exercise 1: Download and Install Git</font>

Please download and install Git before the tutorial today. 

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
[top](#top)

---
### <a name="configure-git-and-initialize-repository"></a><font color='red'>Exercise 2: Configure Git and Initialize Repository</font>

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
$ mkdir swc_git_tutorial
$ cd swc_git_tutorial
$ git init
```

if we use `ls -a` to see hidden files, we can see the git has created a hidden directory called `.git`:

```
$ ls -a
.  ..  .git
```

This directory stores information about our project in this directory. If you ever delete it, you will lose the history of your project. 

[top](#top)

---
### <a name="local-git-workflow"></a> <font color='red'>Exercise 3: Working Locally with Git</font>


This is a great interactive [Git cheatsheet](http://ndpsoftware.com/git-cheatsheet.html) to figure out what commands to use for what you want. <b>It will be overwhelming right now! Stick to the <i>workspace</i>, <i>index</i>, and <i>local repository</i> (we will talk about the upstream repository soon)!</b> 


1. Create an AUTHORS file, a TODO file, and a README file in the `swc_git_tutorial` directory you created in the last exercise.
2. Add your name to the AUTHORS file and add it to the staging area.
3. Check the status of the repository.
   * Notice that there are 'untracked' files in the directory. Remember, this means Git has not been told to keep track of them. 
3. Commit your changes to the repository. Make sure to use an informative commit message!
4. Add your email to the AUTHORS file. 
5. Add the AUTHORS, TODO, and README files to the staging area. 
6. Check the status of the repository.
   * Notice that it specifies that files are new or modified from a previous version.
6. Commit your changes to the repository. 
7. Change the name of the AUTHORS file to CONTRIBUTORS.
8. Check the status of the repository.
   * Git thinks you deleted AUTHORS and let's you know there is a new untracked file.
   * In order to make sure Git keeps track of the changes to this file, we should rename the file in git using `git mv`. This works just like the `mv` command in the shell, but it also let's Git keep track of the move.
9. Rename the AUTHORS file to CONTRIBUTORS using `git mv` command.
   * Note: You will have to first rename the CONTRIBUTORS file back to AUTHORS in your working directory. 
10. Add your changes to the staging area and commit them to the repository.
11. Add "1. Learn Git" to the TODO file. 
12. Add the TODO file to the staging area and commit it.
13. Add "2. Forget Git" to the TODO file.
    * You realize you didn't actually want to change this file and want to revert it back to the last committed file. You can do this with the `git checkout` command.
14. Use Git to discard your latest changes to the TODO file. 
    * Hint: The status message will tell you how to discard your changes.
11. Look at the change history in your repository using `git log`.
12. How would you view the last change made to the TODO file? 


[top](#top)

---
### <a name="collaborate-on-github"></a> <font color='red'>Exercise 4: Work with a Remote Repository</font>

1. Go to github.com and create an account.
2. Make a new repository on Github a title it `swc_git_tutorial`.
   * Don't add a README, LICENSE or .gitignore file this time - we are going to push our exisiting repository.
3. Add the repository you just made as a remote called `origin` to your local repository we made in the previous exercise.
4. Push your local repository to Github.
   * Note: Github tells you how to do this after making your repository. 
5. Look at the files you pushed to Github. 
   * Notice all of the commit history from your local repository is maintained. 
6. Edit the TODO file on Github. Add "2. Learn Github".
7. Commit the file to the repository.
8. Fetch the changes you made on the remote repository and merge them into your local repository. 
9. Check the status of the repository. 
10. Inspect the TODO file and view the changes.

[top](#top)

---
### <a name="branch-merge"></a> <font color='red'>Exercise 5: Collaborate on Github</font>

For this exercise we will work in groups of four. 

1. <i>One</i> person in the group create a remote repository on Github called "swc_ex5".
   * This time you can let Github make the README, LICENSE, and .gitignore files.
2. All other members of the group FORK that repository on Github.
3. Everyone CLONE a copy of either the original or forked repos onto their local machines. 
4. What remote repositories have already been set up for each of you?
   * Hint: `git remote -v`
5. Everyone add a file to the repository titled with their first name and a short sentence about themselves. 
6. Add and commit the file to your repository.
7. Push your file to your remote repository.
8. Everyone that forked the original repository send pull requests.
9. The member who made the original repository should merge all pull requests into the original repository.
10. Everyone fetch all of the changes from the original repository and merge them into their local repository. 
       * Note: You can also do a `git pull upstream master`. This will fetch and merge in one command. 
11. 



[top](#top)


---

###<a name="resources"></a><font color='blue'>Resources for Learning Git</font>

1. Git 
   * [Interactive Git Cheatsheet](http://ndpsoftware.com/git-cheatsheet.html)
   * [Git Documentation](http://git-scm.com/doc)
1. Branching
   * [An interactive demo for learning branching with Git](http://pcottle.github.io/learnGitBranching/)
2. SSH Keys
   * [A Github tutorial for setting up SSH Keys](https://help.github.com/articles/generating-ssh-keys)

[top](#top)

---

