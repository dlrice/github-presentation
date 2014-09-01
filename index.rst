======================
An introduction to Git
======================

.. Sell Git, why it's useful. Perform some simple tasks.

Overview
========
* Sell Git to you
* Show you how to clone other people's repositories.
* Show you how to make your own repository.
* Show you how to share this repository.


What is Git?
============
**Git**
    A distributed version control system.

**Version Control System**
    A system that records changes made to a file or set of files over time so that you can recall specific versions later on. (Chacon 2009)

**Distributed**
    All versions of code in a version control system are contained on a clients machine. 

.. Basically we're saving a history of our work and we can conveniently revisit any older version. It can be any file: source code, dissertations, websites.

Centralized VCS
===============

.. image:: /_static/central.png
   :align: center

(Chacon 2009)

Distributed VCS
===============

.. image:: /_static/distributed.png
   :align: center

(Chacon 2009)

Painful VCS
===========
* some-program.py
* some-program-2.py
* some-program-2-OOP.py
* some-program-3-OOP.py
* some-program-3-OOPfixed.py
* some-program-3a-OOPfixed.py
* some-program-3b-OOPfixed.py
* some-program-4-OOPmultiple-surfaces-BROKEN-more accurate finite differences.py
* some-program-4-OOPmultiple-surfaces-BROKEN-NOW-FIXED-more accurate finite differences-version 2.py

.. Hard to know what exactly is going on, especially if someone else was to come along on and pick it up.

What is GitHub?
===============
An online hosting service for Git repositories.

* Git
    * Command line interface.
    * Can be used completely locally if desired.
* GitHub
    * Graphical web interface.
    * Shares your code with the rest of the world.


Git(Hub) is a helpful tool when you want to...
==============================================
* use somebody else's code.
* write a software project and you want to keep track of its evolution.
* share some software that will make other people's lives easier.
* introduce experimental changes to some software but be able to revert back if it doesn't work at all.
* collaborate with others on a software project.

.. Make a demonstration of cloning a samtools repo.
.. The structure of code can change quite a lot, especially in the early stages, so being able to 
.. You may have written a script that others could use as well and so would save them the task of having to rewrite it. Avoid dupclicating effort within the group, institute, world by sharing with GitHub.
.. This applies to small project with just two people, maybe in the same room, or to a massive open source project such as linux.


Use somebody else's code
========================
#. Find a software project on GitHub.
#. Copy the clone URL.
#. Within terminal, go to local location for the project.
#. Enter::
   
    git clone [copied url]

The .git directory
==================
Could have downloaded a zip but this doesn't give us the:

**.git directory** 
    * Contains all versions (compressed).
    * View the author's work over time.
    * Revert to a previous version.
    * Make changes to the software yourself.

.. The new software version doesn't work with your scripts, so you can now have a look at the previous changes to quickly figure out why or revert to a previous version.
.. You can make changes to the software yourself, comfortable in the fact that you can quickly revert back to the original.
.. Make a demonstration of this.

..   * Revert to a previous version.
..    * Make changes to the software yourself.

Contains all versions
=====================
Git works by taking snapshots:

.. image:: /_static/snapshots.png
    :align: center

(Chacon 2009)

* Each snapshot/commit is given a unique ID known as a checksum (SHA-1).
* Hexadecimal, 40 digits long

View the author's work over time
================================
* To view a log of previous commits::
    
    git log
    git log --oneline
    git log --pretty=fuller

View the author's work over time
================================
Assume last commit by the authors prevented the software from interfacing with your own scripts. What exact changes were made::

    git log -p

Time travel
===========
Let's go back in time::
    
    git checkout HEAD~1 [filenames]

Let's go forwards in time::

    git checkout HEAD [filenames]

Make changes to the software yourself
=====================================
We can build on top of any commit.

* Extend the functionality.
* Fix a bug.

Initial setup
=============
Before we make our repos we need to tell git who we are::

    git config --global user.name "Your Name"
    git config --global user.email "you@somewhere.com"


Track our own software
======================
Two ways to do this:

* Make a repository from scratch::

    git init [repo name]


* Initialise a repository in an existing project::

    cd project directory
    git init 

* After doing this we get a directory and a .git subdirectory.

.. Talked about tracking the evolution of our own software project.

Ignore files
============
* Need to let git know which files we want to track.
* Not all files need to be tracked:
    * Compiled files
    * Data files
    * Temporary files
* Definitely want:
    * Source files
    * Documentation
* To make sure we don't accidentally track inapproriate files we create .gitignore.
* Sits in the working directory.
* Every line specifies (with glob patterns) sets of files to keep out.
    * file types
    * directories

.. Create a directory and subdirectory to ignore. Create an ignore file.

Add files
=========

To add files to be tracked::

    git add [files]

Commit
======
Once all our files have been added. We are ready to commit::

    git commit -a -m "Message"

``-a`` : add all our tracked files to this commit
``-m`` : use this message for the log

Status
======
At any point we can inquire on the state of the repo with::

    git status

Renaming and removing
=====================
To stop tracking a file::
    
    git rm [filename]

To rename a file::

    git mv [current filename] [new filename]


Branches
========
* If we want to try something out while not impacting the current code base we can create a branch::

    git branch [branch name]

* Useful if you have an idea to try out but don't want to affect the master.
* To view all branches::

    git branch

Merging
=======
If you are happy with your experiment we can merge it back to the master. To do this::
    
    git merge [experiment branch]


Sharing your work
=================
The repo so far is local. We can share it by adding a remote.

#. Log in to GitHub.
#. Create a repo.
#. Back on the local machine::

    git remote add origin [repo url]
    git push origin master

Read more
=========
Pro Git by Scott Chacon - a good (and free) book referenced throughout this talk as (Chacon, 2009):
    http://git-scm.com/book
Ignore files
    http://git-scm.com/docs/gitignore
Git introduction in a IPython notebook
    https://github.com/jakevdp/2013_fall_ASTR599
Software carpentry - software for scientists introduction to git
    http://software-carpentry.org/v5/novice/git/index.html
Git Immersion - a web-based guided tour
    http://gitimmersion.com/
