```
Squash merge will combine the changes from feature branch by combining all commits into a single commit which will be applied on main.
With this option your history is linear, but you lose the commit history. This might be importan while debugging later.

The better option then is to do a rebase, your commits from feature branch are sequentially reapplied on the main branch.
Git doesn this internally using a process called "git cherry-pic asw123" It allows to move specific commits between branches.
```
