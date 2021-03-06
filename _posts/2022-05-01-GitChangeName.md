---
layout: post
title:  "Fixing details of committer on Git"
date: 2022-05-01 04:21:00 +0530
tags: git commit authorship
blurb: A small hack using filter-branch to fix committer/author details on git
---

## Issue

Problem with wrong names for committer or author on git for a number of commits? This can be fixed either by git rebase or by git filter-branch.

## Fix

*Note of caution: This script will change SHA1s for all previous commits.*

Create a shell script with +x permissions

```
#!/bin/sh
 
git filter-branch -f --env-filter '
 
an="$GIT_AUTHOR_NAME"
am="$GIT_AUTHOR_EMAIL"
cn="$GIT_COMMITTER_NAME"
cm="$GIT_COMMITTER_EMAIL"
 
if [ "$GIT_COMMITTER_EMAIL" = "your@email.to.match" ]
then
cn="Your New Committer Name"
cm="Your New Committer Email"
fi
if [ "$GIT_AUTHOR_EMAIL" = "your@email.to.match" ]
then
an="Your New Author Name"
am="Your New Author Email"
fi
 
export GIT_AUTHOR_NAME=$an
export GIT_AUTHOR_EMAIL=$am
export GIT_COMMITTER_NAME=$cn
export GIT_COMMITTER_EMAIL=$cm
'
```

Once done, run the push command to update origin. Please note that this will override SHA1s irrevocably at origin

```
git push origin +main
```

Source(s): 
[1](https://gist.github.com/ecentinela/199670/7fdb39cbfc2890820c8e8ef64e1184716a24f1cc)
[2](https://stackoverflow.com/questions/2919878/git-rewrite-previous-commit-usernames-and-emails)
[3](https://stackoverflow.com/questions/68384486/how-do-i-properly-change-the-author-of-a-commit-for-the-past-few-commits-in-gith)
