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
`$ git pull`  
`$ git checkout <branch-name>`  
`$ git pull`  
`$ git rebase -i master`  
`$ git checkout master`  
`$ git merge <branch-name>`  

To brush up about rebasing, check out this [page](https://git-scm.com/book/en/v2/Git-Branching-Rebasing).

<br />


