## POKING AROUND 

At this point, you should have a clone of the repository on your local machine.  This file walks through some instructions to peruse that repo.  It goes over basic commands for using git locally.


### Branches

Git repositories are organized into branches that store different versions of the code.  Take a look at what branches you have

    $ git branch
      develop
      instructions
    * master

There should be an asterisk next to "master," indicating that you're currently on the master branch.  Let's switch over to the develop branch.

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

Now to make and checkout a branch in one step:

    $ git checkout -b myfeature

The -b flag tells git to make a new branch whose name is the argument you pass.  You can also include the name of an existing branch afterwards if you'd like this new branch to be a clone of something other than the current branch.  To make a new branch off of master, for instance, you'd run:

    git checkout -b myfeature master

That's the basics of creating and deleting branches.


### Making changes

You should now be on a branch where it's appropriate to make some changes.  












