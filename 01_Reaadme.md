```
1) Working directory - Where we actively edit files locally.

2) The staging area: It is a temporary holding spot for changes before committing.
 - Example: git add mycode.txt

3) Local repository - This is where we store committed changes locally.
 - Example: get commit -m "message"

4) Remote repository - Server like githhub for sharing and backing up code.

```
Most git commands move files between these four locations

```
With the repo cloned locally lets look at where the code lives.

A) When you start working on a file, you're in the working directory, called a local development environment.
B) When you are ready to commit your changes, use "git add" to stage a snapshot of those files in the staging Area.
C) Think of this as checkpoint, where your changes are gathered up and ready to be finalized.
D) Git commit, it takes a snapshot of the staging area and saves it to your local repository. It locks those staged changes has permanent record.
E) When you're ready to share your progress with the team or backup your work, use "git push" to commit changes to remote repository.
F) Which will be shared server where your team can collaborate, like github or bitbucket.

Collaboration in Git is a two-way exchange.
To integrate your teammates work, use "git pull", which fetches changes from the remote repository and merges them into your local repository.
```
```
git pull = git fetch + git merge

git fetch -It grabs latest update into local repository.
git merge - It merge the changes with files in working directory.

git checkout - It alows to switch between different branches.

Git branching - Allows you to diverge from the main codebase to develop a new feature withot impacting the main code. 

```







