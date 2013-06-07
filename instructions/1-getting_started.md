## GETTING STARTED

To start off, you need a copy of this repository on your local machine.  This file walks you through how to do that.  Later instructions will go more in-depth on collaboration and dealing with remote repos, so don't worry if you're not totally sure what you're doing right now.

### Fork the repository
You don't have permission to write to the main github repo for this project, so the first thing to do is create a fork on your github account.  That way you can update your fork and show off changes without getting permission from the owner of this repository.  It also makes it easier to submit changes later on.

 1. Log in to your github account (or make one and log in if necessary).
 2. Click "Fork" in the top right.  This makes a copy of the repository that you own.

### Get a local copy of your fork
You should now be looking at github.com/yourusername/gitplayground.  Right under the description at the top is a line with some buttons - ZIP, HTTP, SSH, and Git Read-Only.  The url in the box there is the location of this repository on GitHub's servers.  Because you own your fork of this repo, HTTP is selected, and you have Read+Write access to the repository.  If you look at the same location on this repo, Git Read-Only is selected.  If you tried to push changes via the HTTP url, you'd get a permission-denied error.  Anyways, clone the repo on to your local machine:

 1. `cd` to the directory where you'd like to store the project (it'll automatically make a gitplayground directory inside there).
 2. run the clone command:
        git clone https://github.com/yourusername/gitplayground.git
 3. `cd` into the directory and look around.
        cd gitplayground
        ls

That's it for now, this is the procedure to get a copy of any code from GitHub that you'd like to contribute to.
Next up, [poking around](2-poking_around.md).
