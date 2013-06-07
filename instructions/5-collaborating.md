## COLLABORATING 

So you followed the instructions in "Getting Started", and you're comfortable using git locally.  Now it's time to manage other repositories.

### Monitor remote repositories

When you cloned this repo from your GitHub account, git automatically set up your GitHub repo as a remote repository called "origin".  Tell git to show your remote repositories.

    git remote

To display more information about your remote repositories, try

    git remote -v

Right now it should only be tracking one remote repository: the one you cloned from, sensibly called origin.  Go ahead and add this one.  It's somewhat typical to call the parent repository "upstream", but you can use any easy-to-remember name you like.

    git remote add upstream git://github.com/esoergel/gitplayground.git

You've added a code-name for that repo, now "fetch" the latest version of the repo so your computer knows what's going on over there.

    git fetch upstream

If you run `git remote -v` again, you should see "upstream" there.  Now that you've fetched, you can use the `-r` flag to see what branches there are on the remote repositories (the r stands for remote).

    git branch -r

Use `git branch -rv` to display the last commit message for each branch.

If you're working with a group, you can also add any other forks of the project as remote repos.  Let's say you're working closely with your friend Graham Chapman on this project, and you want to see what his changes look like without him pushing to the central "definitive" repository.  Add his repo as another remote. (This repo doesn't actually exist as far as I know, so don't bother running the commands).

    git remote add graham git://github.com/gchapman/gitplayground.git
    git fetch graham

Now you should have multiple remote branches, run `git remote` to verify.  
For more detailed information on a specific remote repository, run

     git remote show upstream


### Making changes

Now it's time to submit changes. You can run `git branch` to see what branches you have.  Checkout the branch you're going to be working off of.

    git checkout develop 

Pull any updates from the appropriate branch of the master remote repo, branch "develop" on "upstream" in this case.
`git pull` is actually just a shortcut for `git fetch` and `git merge`.  When you pull from a remote repository, you *are* performing a merge, so the behavior is identical to merging locally.

    git pull upstream develop 

This should say up-to-date or add changes with no problem.  You haven't been working directly on "develop" have you?  Get on a feature branch!  You can make a new branch with `git branch branchname`, but in this case, you can make a branch and checkout said branch in one step.  Let's call it feature/yourname

    git checkout -b feature/ethan

Go ahead and edit "names.txt".  Add your name to the end.  On a real project you can now make whatever changes you like.  Take a look at the changes you made with `git status`.  Stage and commit your changes

    git add .
    git commit -m "I added my name to names.txt"

If you want someone to merge your changes, the first step is to make sure you have the latest changes from that repo and branch.  To submit to this repo's develop branch, make sure your feature branch is up to date with upstream/develop.

    git pull upstream develop

A `pull` command is a shortcut for `git fetch` and `git merge`.  As with any merge command, there is the possibility of a merge conflict.  Resolve that if necessary, and commit the changes (covered elsewhere).

Okay, you've fixed that horrific bug, and you've incorporated the latest changes from everyone else, now how do you show the world?  Firstly, get it out there on your github repo so other people can see your changes.  Push this branch to origin.

    git push origin feature/ethan

If you've already pushed this branch once, or if you cloned it from origin, it may be tracking the corresponding branch on GitHub, and you can get away with just `git push`, which will push updates on all changed branches which have remote counterparts.

At some point, you may want to push from one branch to another, so to push to your GitHub repo (origin), from your local "feature/ethan" branch to your GitHub "develop" branch, run

    git push origin feature/ethan:develop


### Github pull request

Now your changes are available for all to see on GitHub.  Next up is to submit a pull request to whatever repo you'd like your changes to appear in.  This is a GitHub-specific thing, you're basically telling the owner of the repo "hey, I made some changes, will you merge them in?"


1. Go to your github repo: https://github.com/[YOUR_ACCOUNT_HERE]/gitplayground/
1. Click Pull Request at the top
1. For example, to send "feature/yourname" from "youraccount/gitplayground/" to "develop" on "esoergel/gitplayground," your boxes should be filled out like the example below.

    Pull Request format:
    
        base repo: esoergel/gitplayground       head repo: youraccount/gitplayground 
        base branch: develop                    head branch: feature/yourname

1. Write a message explaining what changes you're trying to get pulled in.

Then sit back and wait for your request to get approved.  Congratulations, you've just contributed to an open source project!!


### Additional collaborative tasks

#### Checking out a remote branch

If you want to work on a copy of a remote branch, or just inspect a friend's branch to test out her latest changes, you'll need to checkout the branch. First, run `git branch -r` to see a list of the remote branches.  Let's look at upstream/playground. You've got a couple options here.

 1. Checkout the remote branch just to inspect it first.

        git checkout upstream/playground
    Now if you run `git branch`, it'll tell you that you're on (no branch).  You can play around with the code, and if you do want to save it to a local branch called myplayground, run the following

        git checkout -b myplayground

 1. Or you can directly make a new local branch that's a copy of the remote branch.

        git checkout -b myplayground upstream/playground


Your branches don't necessarily have to correspond to the remote branches, you can push from any branch to any other branch (although it might be simpler if they do).

