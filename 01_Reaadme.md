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
Main flow GIT
======
repo creation
add the files to staging area
commit to local repo
push to central repo

init the repo
set the main branch 
add origin
add fles to staging, commit to local, push to central

clone
pull the changes

prod code points to -> main branch

we don't develop directly in main branches

create new branch, do the development here, test it, finally send to main branch

branches
pull request
merge
rebase
conflicts
branching strategy

create a branch
do the development there
	run cicd
if success then raise a PR to main branch

git checkout -b <branch-name>

Merge commit
============

merge commit is a special commit that is extra commit created, it will have 2 parents
merge commit preserves the history

Merge vs Rabase
===============
1. Merge create extra commit called merge commit, that has 2 parents so it preserves history
2. Rebase does not not create extra commit, it rewrites the history by changing the commit IDS. It has linear history

If you are working on shared branches go with merge, if you are working on private branches or local branches go with rebase

How do we get conflicts?How to resolve them?
=======
2 persons started egg-dosa.

if Git finds diff code in the same line, it can't understand which one to keep, so it creates conflicts. so the persons who coded to conflicts should sit together and decide which one to keep and which one to discard.

Branching Strategy
==================
git model
github model
trunk based

main develop release bugs feature hotfix -> git model
main and feature -> github/feature branching model
main -> trunk based

long lived branches
short lived branches

main develop
feature hotfix bugfix release

main

develop
========
source: main
all development are reflected here...

short-lived
========
feature

source: develop
target: develop through PR

deploy into DEV environment, everything is working as expected in DEV environment

release
======
source: develop
QA, UAT -> bugs
you can create a simple bug fix branches. do the changes and raise PR to release branch

all bugs are fixed

you can go for PROD from here...

target: main -> PROD and develop tag them

hotfix
=======
source: main

hotfix/bug-1234R -> do the development changes deploy to DEV
merge back to main and release into PROD

target: main and development

this is suitable waterfall model kind of development, if your software has multiple versions supported and multiple devices

GitHub/feature branching Model
============
main and feature

a branch is handled by only one person.

a feature is created from main branch, do the development. CI pipeline will run
	clone build scans unit testing
merge to main branch -> develop, uat, sit, prod

same code goes to all environments -> whatever is tested in DEV should go all the way to PROD. only configuration changes

dev uat qa prod -> dont create branches for environments

Git Reset
==========
Changes undone

1. soft -> changes will  come to staging environment
2. mixed
3. hard




