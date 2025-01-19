Git status show which branch you're in and tracked(staged) and untracked files in working directory

```
[root@replica project]# echo "hello" > index.js
[root@replica project]# git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       index.js
nothing added to commit but untracked files present (use "git add" to track)
```

After adding the files to be commited, git status will show the files under tracked files.
```
[root@replica project]# git add index.js
[root@replica project]# git status
# On branch master
#
# Initial commit
#
# Changes to be committed:
#   (use "git rm --cached <file>..." to unstage)
#
#       new file:   index.js
#
```
To remove the file from staging or cache use "rm --cached
```
[root@replica project]# git rm --cached index.js
rm 'index.js'
[root@replica project]# git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       index.js
```
To remove file from directory use -f (force)
```
[root@replica project]# git rm index.js -f
rm 'index.js'
[root@replica project]# git status
# On branch master
#
# Initial commit
#
nothing to commit (create/copy files and use "git add" to track)
```

