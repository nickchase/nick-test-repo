Working with the miraweb repository
===================================

This document explains the steps necessary for working with the Mirantis web site
*files* using Git.  Changes that are made through the admin control panel are handled
manually, as are any changes that are made directly to the database.  (Though any 
scripts used to alter the database should be stored in this repository.)

Workflow
--------

The general workflow looks like this:

1. User makes a change on dev.mirantis.com directly by editing files in their local working directory (explained below) and uploading them to the server using SFTP.
1. User checks the changes on the server.
1. If the user is happy, (or if needs to stop for a checkpoint) they can commit and push the changes to the miraweb repo's `development` branch.
1. When the user is ready to move the changes to staging, they merge them to the `staging` branch.
1. The Synthesis process automatically checks the `staging` branch every 5 minutes, and changes will be automatically propogated to the staging server.  No action needs to be taken to make this happen (other than merging changes with `staging`).
1. When the user is happy with the changes on `staging`, they can be merged into the `master` branch.
1. Twice a week, after review, Synthesis propogates the changes in the `master` branch to the production server.  No action needs to be taken to make this happen (other than merging changes with `master`). 


How to work with the miraweb repo
---------------------------------

Working with the miraweb repo to make changes to the development branch conists of the following steps:

1.  Create a github.com account, if you don't already have one, and contact an administrator to be added to the miraweb repo.
1.  Install git on your local machine.  This comes in various flavors, so you may have to ask Google for assistance here.
1.  Open a git bash window (if necessary).
1.  Decide what directory is going to be your "working directory" -- where you store your files -- and navigate to that folder in the git bash window, or in the command line window if you're simply using git from the command line.
1.  Type `https://github.com/Mirantis/miraweb.git` and press enter; enter any authentication information the server asks you for.
1.  Change to the miraweb directory.
1.  Change to the development branch by typing `git checkout development`.
1.  Make any necessary changes, add any new files, etc., to this directory on your local machine.
1.  Test your changes by uploading them to dev.mirantis.com using sFTP.
1.  Tell git that you want to add your changes to the repo by typing `git add *`.  (You can also add individual files by name, if you don't want to add all changes.)
1.  Commit changes by typing `git commit -m "A short message explaining what you changed."
1.  At this point the changes are committed locally, so you can go back if you want to, but they're not on the server yet.  To do that, type `git push origin development` to send the files to the development branch of the original server.

