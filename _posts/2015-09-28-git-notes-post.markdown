---
layout: post
title:  "Git Notes"
date:   2015-10-18 17:56:47
categories: git notes udacity school
comments: true
---
Since you did not `git add <file>` to staging, it should be under unstaged files (or untracked if file was created). You can confirm that with:
```
git status
```

At this point there are 3 options to undo the local changes you have:

Discard all local changes, but save them for possible re-use later:
```
git stash
```
Discarding local changes (permanently) to a file:
```
git checkout -- <file>
```
Discard all local changes to all files permanently:
```
git reset --hard
```

```
git log --graph --online master coins
```

on detached HEAD, to create a new branch for reachablity
```
git checkout -b new_branch_name
```

```
git branch new_branch_name
```
```
git checkout new_branch_name
```

list branches
```
git branch
```

merges coins into master
```
git merge master coins
``` 

compares the commit to its parent, useful when you merge
```
git show commit1
``` 

deletes the label
```git branch -d coins``` 

`git checkout -b new_branch_name`

same as these two commands:

`git branch new_branch name; git checkout new_branch_name`

(used to start a new branch name from a previous commit, otherwise you’ll be on detach head state


`git remote add origin <https://github.com/username/rep.git>` (standard to name origin)

`git remote -v` (shows where URL where i would push and pull data from)

send changes to the remote

`git push <remote> <local_branch>`

`git push origin master`

sync your updated github repo with your local repo

`git pull <remote> <local_branch>`

`git pull origin master`

`git remote` (list remotes)

`git remote add origin git@github.com:casdf/file.git`

`git remote -v` (verbose)

`git push origin master` (to push all changes to current branch to github )

`git fetch origin` (updates origin/master on local with the latest master on github)

`git pull origin master`

the same as

`git fetch origin`

`git merge master origin/master`

`git push origin different-branch-not-master` publish a different branch on github

you can delete a remote branch using
`git push origin --delete <branchName>`

push an existing repository from the command line

`git remote add origin https://github.com/reyesh/Ask-a-flowchart-which-new-new-media-service-is-right-for-me-.git`
`git push -u origin master`



Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
