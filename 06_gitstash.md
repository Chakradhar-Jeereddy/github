Stash is a 5th stage where we can save uncommited transactions so your working tree is clean.
Command is "git stash save"
When you don't want to commit those transactions.
To bring back those uncommited changes to working tree use "git stash pop"

```
[root@replica project]# vi sample
[root@replica project]# git stash save
Saved working directory and index state WIP on (no branch): 4e35dda version1
HEAD is now at 4e35dda version1
[root@replica project]# cat sample
hello sir
[root@replica project]# git stash pop
# HEAD detached at 4e35dda
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#       modified:   sample
#
no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (fee555a790f5f9ebecdbbd3651e8619a73ce2a54)
[root@replica project]# cat sample
ello sir
[root@replica project]#
```

```
Git fetch will bring code from remote repository to  local repository but will not merge with files in working directory.
Git merge will merge local repo files with working directory files.
git pull does both fetch and merge.
```
