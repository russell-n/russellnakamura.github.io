.. title: Fixing a 'hasDotGit' Error Converting hg to git
.. slug: fixing-a-hasdotgit-error-converting-hg-to-git
.. date: 2016-03-29 12:53:31 UTC-07:00
.. tags: git hg errors
.. category: howto
.. link: 
.. description: How to fix 'hasDotGit' when converting a repository from mercurial to git.
.. type: text

The Problem
-----------

I was converting one of my repositories from a `mercurial <https://www.mercurial-scm.org/>`_ repository to a `git <https://git-scm.com/>`_ repository using `hg-fast-convert <https://github.com/frej/fast-export>`_ when I ran into a strange error. Although the `hg-fast-convert` command seemed to work, when I tried to push the repository to *github* I got a *hasDotGit* error, telling me that my repository had a .git folder in it. The output from the failed push didn't really tell me enough to fix the problem, and googling didn't get me anything that I could use so I decided to try re-converting the repository using the `hg-git` extension instead.

.. code:: bash

   cd mercurial_repository
   hg push ../new_git_repository

This gave me a slightly more useful error message.

.. code:: bash
          
   abort: Refusing to export likely-dangerous path 'tuna/_themes/.git/hooks/commit-msg.sample'

`tuna` was my sub-folder and apparently I at some point committed a `.git` folder to the (now non-existent)  `_themes` folder. To get it to be convertible, I would need to remove this folder from the repository history. As it turns out, this was easier than I thought it would be.

Removing .git
-------------

I found the solution on the `JitBit <https://www.jitbit.com/alexblog/232-removing-files-from-mercurial-history/>`_ blog, so reading that will tell you all that you need to know, but I'm going to document the whole process in case I need to do it again (and to remind me of how to fix the `hasDotGit` error.

The Convert Extension
~~~~~~~~~~~~~~~~~~~~~

The `convert` extension comes with mercurial but isn't enabled by default. To add it edit the `.hgrc` file so that it's in the extensions.

.. code:: ini

   [extensions]
   hgext.convert =

Cleaning the Repository
~~~~~~~~~~~~~~~~~~~~~~~

What the `convert` extension is going to do is convert the mercurial repository to a mercurial repository, excluding the `.git` folder in the process. To tell it what to exclude I created a file called `exclude.txt` that had the following in it.

.. code:: 

  exclude "tuna/_themes/.git/"

Then, at the command line I converted the `mercurial_repository` to the `cleaned_repository`.

.. code:: bash

   hg convert --filemap exclude.txt mercurial_repository/ cleaned_repository/

This created a clone of the `mercurial_repository` with the `.git` folder removed.

Converting to Git
~~~~~~~~~~~~~~~~~

Now that I had the cleaned-repository I could use *hg-fast-export* to convert it to a git repository.

.. code:: bash

   git init git_repository
   cd git_repository
   hg-fast-export -r ../cleaned_repository
   git checkout HEAD
   git remote add origin git@github.com:russellnakamura/git_repository
   git push -u origin master

Which now worked. 
