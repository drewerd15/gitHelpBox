Welcome to the wonderful world of Git. I'll start with an explanation of what this guide is, and what it isn't. There are many many wonderful guides out there to help you understand and better work with git. This is not one of them. This guide is here to help you when things go wrong. Please also checkout the wonderful resource dangit git https://dangitgit.com/en (available in spicier versions for those who want it). A grate resource for common git issues.

## Git Is Broken: please send help

### Cloning:

Lets start from square one. We have a repo on github, lets grab those files. On your local machine navigate to a where you would like you shiny new repo to live.
`cd ./projects`
Now lets clone the repo: click the green Code button and copy the location for the github repo. To clone this repo
`git clone https://github.com/drewerd15/gitHelpBox.git`
That will make a local copy on your machine.

### Branching:

Branching make a copy of the current code that lets us commit and push it to the remote while we are working on it but doesn't interfere with anything else. Mostly you will use this to create a feature, then you will merge this back into the main branch. To make a new branch use:
`git checkout -b MyNewBranch`
This will create a new branch and switch you to it.
To see all branches use:
`git branch`

Main vs Master
You may notice a lot of repos using either terms. Modern usage has moved away from Master as the default name for the main branch. New repos will generally default to Main as the root branch. In vscode, you can easily tell what branch you are on by looking in the lower left hand corner where the name is displayed.

### Pulling:

Ok so we have git
Lets start with the basics committing

Practically a commit comes in three parts and we can think of them like shipping a box:
staging `git add` We put our changed files in a box and add any new ones.
committing `git commit` We tape up the box and write what's inside.
pushing `git push` We ship the box to our main repository.

Here's what a solid workflow looks like:

### Staging:

---

`git add ./myFile.js` - You can add specific files
`git add .` - You can add all new files that aren't on your ignore list

---

**Gotcha**: Help I staged(added) something I didn't want to!
No worries, maybe it's a dumb file, or it has secrets in it, or you added your npm folder.
`git reset`
`git reset --<./file-I-Don't-Want-Here>`
[More details here](https://devconnected.com/how-to-unstage-files-on-git/)

**IMPORTANT** If you committed a secret file, like an api key or a password. The very first thing you do is tell someone on your team, then change the key or password immediately. There are ways to remove a commit but It's not something to be done lightly, and carries significant risk.

### Commiting:

---

`git commit`

- Puts all staged files into a commit and brings up the text editor vi, see the section 'Help I'm Stuck in Vi/Nano'

`git commit -m 'My useful commit message here'`

- Much quicker, lets you skip nano or vi
  \*\*\* add stuff about editing commits, amending, changing messages

---

### Push:

push is where we send our committed and changed code to github or server to be stored and for others to see.

`git push origin main`

- This will be your standard push. It pushes your code to the remote server. Normally when you clone a repo the place where you cloned it from is called `origin`. The second part is what branch you want to push to.

`git push origin newFeatures`

- This pushes to a remote branch called `newFeatures`

---

### Mergeing and Conflicts

Once you have your features ready on your branch and you are ready to add them to to main branch it's time to merge!
There are many different ways to merge but I recommend this workflow. Assuming I'm starting on the branch FeatureA. I will pull from the main branch to get the latest code, I will merge those changes with vsCode. Then I will commit and either push to main or make a pull request to have my changes approved to be merged with the main branch. So here is what this would look like:
`git checkout FeatureA`
`git pull origin main` or `git merge main`
`pull` will download the latest commit from your remote and let you merge things in. `merge` will pull in the changes from your local branch. You can use either as the situation requires. You may end up in a situation where you want to merge two local branches say featureA and featureB, merge will let you combine the two.

Check through everything that conflicts and choose my version, the updated version of the conflicting code, or tweak things to merge the two.

`git push FeatureA` - This will push to the remote branch then I'll make a pull request

When you push or pull a change that conflicts with your branch there will be merge conflicts. Sometimes you have resolve those yourself sometimes git can do it for you. You can also do this on github at times but I don't recommend it. It is best merge in vscode since it is easier to make the necessary edits.

### Help I'm Stuck in Vi/Nano

---

Step one don't panic.
First look on the bottom if you see a bunch of commands that look like "^G Get Help" and you see Nano in a corner, Congratulations you are in Nano, a terminal based text editor. Type your commit message on a line that doesn't start with #. Then press **ctrl (command for macs) + o** to Write Out or save your message. Press enter, then **ctrl (command) + x** to quit, press n to not save your commit message.

If you don't see those things you are in vi.
Press **esc** to ensure you are in navigation mode, then press **i** to go to edit mode. Use the arrow keys to navigate and write your message.
Press **esc** to leave edit mode then type ":wq" then **enter** to save and quit.
