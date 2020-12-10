## BRANCHING AND COLLABORATION: CONCEPTS

This file doesn't contain any code, it's a general look at the ideas behind branching models and the decentralized nature of git.


### Decentralization

#### Distributed nature

Git is proudly heralded as a "distributed revision control system."  This means that there's no imperative for a central repository (unlike most previous revision control systems).  When working on a project with a group, it's helpful to treat one specific repository as the definitive one, that way everyone always knows where to go to get the latest changes.  The beauty of decentralization is that this status is in name only; if the guy who runs that repo isn't here today, you can make sure another repo is in line with that one, and then have everyone send changes to that repo, making it the definitive one for the day.  Then at the end of the day, send one pull request back to the main repo, and it'll get updated with all the changes on that branch.

#### Pushing and pulling 

With one central repository, who has access to make changes?  Anyone can read open source projects, but the owner decides who can make changes.  There is a clear distinction between read and write access.  With git, you can `push` code to a remote repository if and only if you have write access.  For small projects, granting push access to everyone can work, but this quickly becomes untenable with more contributors, and it's sensible to have someone in charge of making sure the repository stays clean.

By contrast, anyone can `pull` changes from a remote repo to their own, as this only requires them being permitted to read that repository (`git pull` is a shortcut for `git fetch` and `git merge`).  In this scenario, the owner of the repo is the one making the changes, not the remote party.  This is also how you can get and/or inspect changes other people made that haven't been approved as submissions to the main repository.

This provides a great way for the maintainer of a repository to get changes from other contributors without needing to grant them write access (which would allow them to `pull`).  The contributer can issue a "pull-request" on github, telling the maintainer that they've made some changes that are worth merging in to the main repository.  The maintainer can then look over those changes, test the code, and `pull` the changes into the codebase.

#### Trust

With this system, each contributor can choose what code to allow into their repositories.  Let's say your beginner friend "Bob" makes some changes to a big project.  With only a central repository, Bob might have a difficult time getting his code approved, and he might not be confident enough in his changes to submit it in the first place.

Instead, he can send you a pull request, and you can look over the changes, test them, and make sure everything works.  Once you're sure it's work you'd vouch for, you can submit a pull request to the central repository.  This way the central maintainer doesn't need to inspect code from Bob - some beginner she doesn't know.  She can see that's it's coming from you and because she knows you know what you're doing, she can be more confident that the changes are valid. 


~~~~~~~~~~~~~~~~~

### Branching on large projects

Branches are free and merging is easy.  You're not branching enough.  You should rarely be working directly on the same branch as other people.  There are better and more detailed descriptions of branching models ([like this one](http://nvie.com/posts/a-successful-git-branching-model/)), but here's a brief overview:

 * Master - never, ever, work on master.  Master represents the last "stable" release of your code.  Once a new release is fully tested and ready to go, it's pushed to master.
 * Staging - this is where you store fully developed code that is still being tested before it gets released to master.
 * Develop - this acts as the center of all development, the latest and greatest code gets pushed here.
 * Feature branches - Are you working on develop?  What feature?  Get on a feature branch.  Let's say your project is a set of lists of the best Swedish pop music.  You and two others are compiling a list of the best ABBA songs.  You should all work on a branch called feature/ABBA (the slash doesn't really mean anything special, it's just notation). 
 * other branches - There are three of you working on feature/ABBA, so maybe you should make your own branch for your portion, say feature/ABBA/Eurovision_era.
 * bugfixes - If a bug is discovered, create a helpfully labeled bugfix branch off of the relevant branch (if the bug is in production, branch off of master, never work directly in master).  Test the fix, and merge it back in to the parent branch.

Long-lived feature branches can regularly pull updates from develop as other features and bugfixes get merged in to stay up to date.  Once a branch is ready, it should be merged into its parent branch, and then the parent branch should be merged up (and so on).  Work on a feature branch shouldn't be pulled directly into staging or master, for example.

#### Merge conflicts

Most of the time, merges will Just Work.  If two changes are made in the same place, and they're not one after the other, git might not be able to tell what to do, and you'll get a merge conflict.  Git will complain, so you go to the relevant section of code, resolve the conflict, and commit the resolution.  The fewer people working on a branch, the less likely this is to happen, that's one reason you should branch and branch again.

Next up, commands you need for [collaborating](5-collaborating.md)
