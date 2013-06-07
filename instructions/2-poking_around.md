## POKING AROUND 

At this point, you should have a clone of the repository on your local machine.  This file walks through some instructions to peruse that repo.  It goes over basic commands for using git locally.


### Branches

Git repositories are organized into branches that store different versions of the code.  Take a look at what branches you have

    $ git branch
      develop
      instructions
    * master
      problem_branch

There should be an asterisk next to "master," indicating that you're currently on the master branch.  Let's switch over to the develop branch, and ignore the others for now.

    git checkout develop

This is the branch you'll typically be starting your work from (more on that later).  Run `git branch` to verify that you're on develop.  Let's go ahead and make a new branch called myfeature, so you can make changes without affecting "develop".

    git branch myfeature

Run `git branch` again, and you'll see that the new branch has been created, but you're still on develop, so let's switch over to myfeature.

    git checkout myfeature

As you can imagine, it's quite common to make a new branch, and then immediately check it out.  Git provides a way to do this in one step.  Before we try this out, delete the branch you just made (but first you have to switch back over to develop).

    $ git checkout develop
    $ git branch -d myfeature
    $ git branch
    * develop
      instructions
      master
      problem_branch

Now to make and checkout a branch in one step:

    $ git checkout -b myfeature

The -b flag tells git to make a new branch whose name is the argument you pass.  You can also include the name of an existing branch afterwards if you'd like this new branch to be a clone of something other than the current branch.  To make a new branch off of master, for instance, you'd run:

    git checkout -b myfeature master

That's the basics of creating and deleting branches.


### Making changes

You should now be on a branch where it's appropriate to make some changes.  If you run `ls` it should show a file called "first_file.txt".  Go ahead and make some changes to it.

After saving the changes, have git tell you what's changed locally

    $ git status
    # On branch myfeature
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    #      modified:   first_file.txt
    #
    no changes added to commit (use "git add" and/or "git commit -a")

To incorporate changes, you need to stage them and then commit the staged changes.

    git add .
    # the dot means "everything in this current directory"
    git commit -m "I made some additions to first_file.txt"
    # the "-m" flag tells git that you're going to add a commit message
    # this message should briefly describe the changes you made

You may get a message from git about configuring your name and email address.  Follow those instructions if necessary.  





