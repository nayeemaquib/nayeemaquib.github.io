---
layout: post
title:  "Git Tricks"
date:   2018-09-21
categories: Github
---

_September 21, 2018_



<h2>How to rename a local git branch?</h2>
  
If in current branch, type:  
`$ git branch -m <newname>`  
So to change a branch name from `feature-v0.1` to `feature-v0.2` while in `feature-v0.1`, type:  
`$ git branch -m feature-v0.2`  
  
If in another branch, type:  
`$ git branch -m <oldname> <newname>`  
So to change a branch name from `feature-v0.1` to `feature-v0.2` while in any other branch, say `master`, type:  
`$ git branch -m feature-v0.1 feature-v0.2`  
<br />

<h2>How to delete a git branch?</h2>
  
To delete a local branch there are two options:  
`$ git branch -d <branchname>`  
`$ git branch -D <branchname>`  
Here, `-d` is an alias for `--delete` and `-D` is an alias for `--delete --force`. `-d` deletes the branch 
if it has already been fully merged in its upstream branch. `-D` deletes the branch irrespective of its 
merged status, which makes it same as:  
`$ git branch -df <branchname>`  
So to delete a branch named `feature-v0.1`, type:  
`$ git branch -d feature-v0.1`  
  
To delete a remote branch there are two identical options:  
`$ git push <remotename> -d <branchname>`  
`$ git push <remotename> :<branchname>`  
So to delete a remote branch named `feature-v0.2` assuming remote name is `origin`, type:  
`$ git push origin -d feature-v0.2`  
<br />

<h2>How to properly merge a git branch to master?</h2>

If in current branch, type:  
`$ git checkout master`  
`$ git pull origin master`   
`$ git merge <branch-name>`  
`$ git push origin master`

To brush up about rebasing, check out this [page](https://git-scm.com/book/en/v2/Git-Branching-Rebasing).

<br />

<h2>How to compare two branches of git?</h2>

Given that both of them are locally available, to see the difference at the tip:  
`$ git diff branch1/hash1..branch2/hash2`  
To see the difference from their common ancestor:  
`$ git diff branch1/hash1...branch2/hash2`  

To find the tag use:
`$ git log`  
For a compact version of the log use:
`$ git log --oneline`  
For a compact tree of the log use:
`git log --graph --all --oneline --decorate`  

If they are not locally available, then either get them by using:  
`$ git checkout branch_name`  
Or specify the remotes path:
`$ git diff remotes/origin/branch1..remotes/origin/branch2`  

<h2>How to reset remote to a certain commit?</h2>

To make the remote match a commit that is locally available use:  
`$ git push --force origin <hash>:<remote_branch_name>`  
e.g:  
`$ git push --force origin 91ace7351:master`  
If it is the current commit, that you want to match then just use:  
`$ git push -f origin master`  

