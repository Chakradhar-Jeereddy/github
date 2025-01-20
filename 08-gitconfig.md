## The git config command is a convenience function that is used to set Git configuration values on a global or local project level. These configuration levels correspond to .gitconfig text files. Executing git config will modify a configuration text file.
* common configuration settings like email, username, and editor.

Local - updates in .gitconfig file and applied at local level (It is default)

Global  - Applies at system user level at user's home directory

System  - Applies at system wide at /etc/ directory


Updating at global level
```
git config --global user.email 'chakra@gmail.com'

[root@replica project]# cat ~/.gitconfig
[user]
        name = chakradhar
        email = chakra@gmail.com
```

Updating at local level (--local is optional)
```
[root@replica project]# git config  user.email 'chakrareddt@gmail.com'
[root@replica project]# cat .git/config
[core]
        repositoryformatversion = 0
        filemode = true
        bare = false
        logallrefupdates = true
[user]
        name = chakra
        email = chakrareddt@gmail.com
```

Git config editor
```
git config [--local|--global] --edit
git config [--local|--global] -e
[user]
        name = chakradhar
        email = chakrareddt@gmail.com
[credential]
        helper = cache
```

Creating git alias

```
[root@replica project]# git config alias.st status
[root@replica project]# git st
# HEAD detached at 4e35dda
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#       modified:   sample
#
no changes added to commit (use "git add" and/or "git commit -a")
```

Git config get option and unset option
```
[root@replica project]# git config --unset user.name
[root@replica project]# git config --unset user.email

[root@replica project]# git config -l --local
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
alias.st=status

           <command> [<args>]
# git config --global user.name
chakradhar
# git config --global user.email
chakrareddt@gmail.com
```





