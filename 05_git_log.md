```
We can switch back in time using the commit hash, each commit is associated with a unique has which allows us to go back in time to see older version of the file.
[root@replica project]# git log --oneline
commit 1279e42cbcd1ac00f2a22c77d80e1f8d19c88564
Author: chakradhar <mymailbox.yodlee@gmail.com>
Date:   Sun Jan 19 18:48:12 2025 -0500

    d

commit 7c8ff5b49896060c05124b5ad51ab84ef6a1b6f9
Author: chakradhar <mymailbox.yodlee@gmail.com>
Date:   Sun Jan 19 18:47:29 2025 -0500

    d
[root@replica project]# git status
# On branch master
nothing to commit, working directory clean
[root@replica project]# git checkout 7c8ff5b49896060c05124b5ad51ab84ef6a1b6f9
Note: checking out '7c8ff5b49896060c05124b5ad51ab84ef6a1b6f9'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at 7c8ff5b... d
[root@replica project]# git checkout 1279e42cbcd1ac00f2a22c77d80e1f8d19c88564
Previous HEAD position was 7c8ff5b... d
HEAD is now at 1279e42... d
```

```
Example of switching between the versions
[root@replica project]# cat sample
hello brother
[root@replica project]# git checkout 4e35dda
Warning: you are leaving 1 commit behind, not connected to
any of your branches:

  2933948 version2

If you want to keep them by creating a new branch, this may be a good time
to do so with:

 git branch new_branch_name 2933948

HEAD is now at 4e35dda... version1
[root@replica project]# cat sample
hello sir
[root@replica project]#
```
