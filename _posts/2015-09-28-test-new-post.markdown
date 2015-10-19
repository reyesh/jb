---
layout: post
title:  "git notes"
date:   2015-10-18 17:56:47
categories: git notes udacity school
comments: true
---
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


Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
