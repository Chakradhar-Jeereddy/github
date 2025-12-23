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

If you are working on shared branches go with merge, if you are working on private branches or local branches go with rebase (all commits come on my name).

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

* merge
* rebase
* branching strategy
* PR

Reset -> commits will be deleted, it is only suitable for private branches or local commits.
=====
soft, mixed, hard
```
Never use in shared branches as you will lose the commit ids, it deletes the commit id.
git reset --soft <commit id>    # Undo changes from local repo and keeps it in staging area
git reset --hard <commit id>    # Undo changes from local repo, staging area and workspace.
git reset <commit id>           # Default is mixed mode which undo changes from local repo and staging area.
```
commit -> it is like promise

revert -> will not delete any commit, we can correct the changes using revert commit, old commits still will be there. Useful for shared/remote branches
======
```
git revert <commit id>
As to make changes in files and commit. It creates a new commit with new corrections and preseve the previous commits.
```

git squash/interactive rebase
===========
100 commits -> squash them into single commit
```
git rebase -i <where-to-pick>
# The file opens.
select the commit id to pick
pick 69afbb1b3981428b2da8547856ad08b036eafad7 (and save the file)

Sqash

git rebase -i 543e0f5
pick 378b745 # add oil
squash f4254c7 # add batter
s e3a12d8 # reverted
s 543e0f5 # picked cherry
=> save
git rebase --continue
Resove merge conflicts in the file, save
git add .
put commit message and save
```
git stash
=========
while we are working on some branch, suddenly an emergency defect came in production, so we need to move and create hotfix branch. we can stash uncommited changes changes complete hotfix, comeback to our branch and pop the changes
```
git stash
git checkout hotfix
git checkout feature
git merge hotfix
git stash # Brings back the uncommmited changes
```
git cherry-pick
============
if you are developing some feature, but a part of it already developed earlier instead of doing everything from the scratch you can cherry pick the changes from previous commits
```
git log main
commit c5fbb8ba61772bfbf3691dae28b178194a25d065
Author: chakradhar06 <chakradhar06@gmail.com>
Date:   Mon Dec 22 16:41:51 2025 -0500

    commbined commits

commit 0e08b3feb0d23ed6f613b2ada1a926404061638b (origin/master, origin/HEAD)
Author: chakradhar06 <chakradhar06@gmail.com>
Date:   Mon Dec 22 16:12:15 2025 -0500

git checkout feature
git cherry-pick c5fbb8ba61772bfbf3691dae28b178194a25d065
1 file changed, 2 insertions(+)
git log  # only the changes picked will come from main and a new commit id is created.
```

Check details of a commit
=======================
git show <commit id>

# Restore deleted commit
=====================
approach 1
=========
```
git reset --hard <commit> # This will delete commit, changes from workspace/staging/local repo.
git reflog    #it will show the deleted commits as well.
git show <commit id>   # Shows details of the commit, so we can pick the right commit

git checkout -b restore-branch <commit id>
git checkout freature-branch
git merge restore-branch
git checkout -d restore branch.
```
approach 2
==========
```
git reset --hard <commit> # This will delete commit, changes from workspace/staging/local repo.
git reflog    #it will show the deleted commits as well.
git show <commit id>   # Shows details of the commit, so we can pick the right commit

git checkout feature-branch
git reset --hard <deleted commit id> (Make sure you don't use this appoach in shared remote/local branches
```

Conflicts 
==========
2 persons working on same branch
git finds conflict if both persions updated the same line in the code.
And it can't decide which one to remove or keep. It has to be resolved through human intervention.
Edit the files and remove the conflicts, save and commit.

Git tagging
===========
 git tag v0 c5fbb8ba61772bfbf3691dae28b178194a25d065  # adds tag to the commit id
 git tag v2                                           # adds tag to the current commid id.
 git tag v1 0e08b3feb0d23ed6f613b2ada1a926404061638b
 git reset --hard v0    #rollback changes to tag v0
 git show v0  # shows the details of commit id attached to the tag.


