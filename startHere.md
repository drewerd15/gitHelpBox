Welcome to the wonderful world of Git. I'll start with an expanation of what this guide is, and what it isn't. There are many many wonderful guides out there to help you undertand and better work with git. This is not one of them. This guide is here to help you when things go wrong.

## Git Is Broken: please send help

Lets start with the basics commiting

Practically a comit comes in three parts and we can think of them like shipping a box:
stageing `git add` We put our changed files in a box and add any new ones.
commiting `git commit` We tape up the box and write what's inside.
pushing `git push` We ship the box to our main repository.

Here's what a solid workflow looks like:

### Stageing:

---

`git add ./myFile.js` - You can add specific files
`git add .` - You can add all new files that aren't on your ignore list

---

\*\*\*add stuff about unstaging `git reset` https://devconnected.com/how-to-unstage-files-on-git/

### Commiting:

---

`git commit`

- Puts all staged files into a commit and brings up the text editor vi, see the section 'Help I'm Stuck in Vi/Nano'

`git commit -m 'My useful commit message here'`

- Much quicker, lets you skip nano or vi
  \*\*\* add stuff about editing commits, ammending, changing messages

---

### Push:

push is where we send our commited and changed code to github or server to be stored and for others to see.

`git push origin main`

- This will be your standard push. It pushes your code to the remote server. Normally when you clone a repo the place where you cloned it from is called `origin`. The second part is what branch you want to push to.

`git push origin newFeatures`

- This pushes to a remote branch called `newFeatures`

---

### Merge Conflicts

When you push or pull a change that confits with your branch ther will be merge conficlts. Sometimes you have resolve those yourself sometimes git can do it for you. You can also do this on github at times but I don't reccomend it. It is best merge in vscode since it is easier to make the necessary edits.

`git
Help I'm Stuck in Vi/Nano
Step one don't panic.
First look on the bottom if you see a buch of commands that look like "^G Get Help" and you see Nano in a corner, Congratulations you are in Nano, a terminal based text editor. Type your commit message on a line that doesn't start with #. Then press ctrl (command for macs) + o to Write Out or save your message. Press enter, then ctrl (command) + x to quit, press n to not save your commit message.

If you don't see those things you are in vi.
Press esc to ensure you are in navigation mode, then press i to go to edit mode. Use the arrow keys to navigate and write your message.
Press esc to leave edit mode then press :wq save and quit.
