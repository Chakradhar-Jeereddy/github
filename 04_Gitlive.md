```
To initialize git repository (It creates an empty local repository)
git init
Reinitialized existing Git repository in /root/project/.git/
```



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

To create a new branch
```
[root@replica project]# git checkout -b chakra
Switched to a new branch 'chakra'

[root@replica project]# git status
# On branch chakra
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       index.js
nothing added to commit but untracked files present (use "git add" to track)

To switch to master

[root@replica project]# git checkout  -b master
Switched to a new branch 'master'
[root@replica project]# git checkout  -b chakra1
Switched to a new branch 'chakra1'
[root@replica project]# git checkout  -b chakra
Switched to a new branch 'chakra'
[root@replica project]# git checkout  -b chakr2
Switched to a new branch 'chakr2'
[root@replica project]# git checkout  -b chakra2
Switched to a new branch 'chakra2'

```

To delete branch (at least there should be one commit in the branch)
```
[root@replica project]# git checkout -b chakra
A       base
Switched to a new branch 'chakra'
[root@replica project]# git branch -D chakra1
Deleted branch chakra1 (was 1279e42).
```

To create branch, to create file, add file to stage,remove file from staging, readd file and commit file to local repository and delete branch.
```
[root@replica project]# git branch
* master
[root@replica project]# git checkout -b chakra
A       base
Switched to a new branch 'chakra'
[root@replica project]# touch sample.txt
[root@replica project]# git status
# On branch chakra
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       new file:   base
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       sample.txt
[root@replica project]# git add sample.txt
[root@replica project]# git status
# On branch chakra
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       new file:   base
#       new file:   sample.txt
#
[root@replica project]# git rm --cached sample.txt
rm 'sample.txt'
[root@replica project]# git status
# On branch chakra
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       new file:   base
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       sample.txt
[root@replica project]# l
bash: l: command not found...
[root@replica project]# ls
base  index.js  sample  sample.txt
[root@replica project]# git add sample.txt
[root@replica project]# git status
# On branch chakra
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       new file:   base
#       new file:   sample.txt
#
[root@replica project]# git commit -m 'updates'
[chakra f863a08] updates
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 base
 create mode 100644 sample.txt
[root@replica project]# git status
# On branch chakra
nothing to commit, working directory clean
[root@replica project]# git log
commit f863a08b977766af38ad40641c7d0d8aa9c921ec
Author: chakradhar <mymailbox.yodlee@gmail.com>
Date:   Sun Jan 19 19:29:18 2025 -0500

    updates

commit 1279e42cbcd1ac00f2a22c77d80e1f8d19c88564
Author: chakradhar <mymailbox.yodlee@gmail.com>
Date:   Sun Jan 19 18:48:12 2025 -0500

    d

commit 7c8ff5b49896060c05124b5ad51ab84ef6a1b6f9
Author: chakradhar <mymailbox.yodlee@gmail.com>
Date:   Sun Jan 19 18:47:29 2025 -0500

    d
[root@replica project]# git branch
* chakra
  master
[root@replica project]# git checkout master
Switched to branch 'master'
[root@replica project]# git branch
  chakra
* master
[root@replica project]# git branch -d chakra
error: The branch 'chakra' is not fully merged.
If you are sure you want to delete it, run 'git branch -D chakra'.
[root@replica project]# git branch -D chakra
Deleted branch chakra (was f863a08).
[root@replica project]# git branch
* master
[root@replica project]#
```












