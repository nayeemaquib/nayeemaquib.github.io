---
layout: post
title:  "Git Tricks"
date:   2018-09-21
categories: Github
---

_September 21, 2018_

<strong>How to rename a local git branch?</strong>

If in current branch:
`$ git branch -m <newname>`
So to change a branch name from `feature-v0.1` to `feature-v0.2` while in `feature-v0.1` type:
`$ git branch -m feature-v0.2`
If in another branch:
`$ git branch -m <oldname> <newname>`
So to change a branch name from `feature-v0.1` to `feature-v0.2` while in any other branch, say `master` type:
`$ git branch -m feature-v0.1 feature-v0.2`

