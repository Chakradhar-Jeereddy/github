- Squash merge will combine the changes from feature branch by combining all commits into a single commit 
  which will be applied on main.
- With this option your history is linear, but you lose the commit history. This might be importan while debugging later.
- The better option then is to do a rebase in private/local branches, your commits from feature branch are sequentially reapplied on the main branch.
- Git does this internally using a process called "git cherry-pick asw123", allows to move to specific commits between branches.

