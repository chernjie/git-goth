<img src="https://raw.github.com/mig33/git-goth/master/goth_day_smiley.png" alt="Goth Day Smiley" style="float:right;" width="200" />

git-goth
========

GIT-SVN Extension, several convenience functions to help with release/merges/feature management etc.

Usage
=====
```
Usage: git goth -h|help|?
Usage: git goth edit|-e|eclipse                 # edit this script
Usage: git goth branch                          # Show upstream/downstream stats
Usage: git goth branch last [<limit>]           # list SVN branches sorted by last updated
Usage: git goth scp|stage <remote> [ref|file..] # scp and stage your files to specified remote
Usage: git goth remote                          # show remote status relative to HEAD
Usage: git goth upstream|up [<ref>]             # find upstream branch
Usage: git goth scp|stage <remote> [<ref>]      # show diff relative to <ref> and upload unstaged files to <remote>
Usage: git goth show [-dhj]                     # -d:unpushed -h:hash-only -j:jira-only
Usage: git goth rebase --all                    # stash + svn fetch + rebase all branches
Usage: git goth cherry-pick|cp [<ref>..]        # customized cherry-pick for SVN
Usage: git goth trac|tracf [<ref>..]            # generate Trac link

Usage: git qa info [-limit]                      # list last RC tags or maintenance branch
Usage: git qa graph [-limit]                     # show QA graph
Usage: git qa unmerged [JIRA#..]                 # release jira tracking, whether a jira has been merged or release
Usage: git qa merge <branchname> <JIRA#> [message]
Usage: git qa blame                              # run a different variation of git log --merge

Deprecated commands:
Usage: git goth log [branch]                    # log of current SVN branch
Usage: git qa rc [new [QAT]]                     # Create new SVN branch
Usage: git qa build                              # Run ant build
Usage: git qa tag [REL_8.XX]                     # Generate create new SVN tag command
Usage: git qa rebase                             # Run git qa merge to rebase from RC

```

Installation
============

The simplest way is to [download this file](https://raw.github.com/mig33/git-goth/master/git-goth) and place it somewhere your `PATH` recognise.

OR

```
curl -sk https://raw.github.com/mig33/git-goth/master/git-goth > ~/bin/git-goth
chmod +x ~/bin/git-goth
```

Documentation
=============

git goth scp|stage
------------------
```
Usage: git goth scp|stage <remote> [ref|file..] # show diff relative to <ref> and upload unstaged files to specified remote
```
This is wrapper around the following tasks:
```
- git diff <files>
- scp <files> <remote>:<files>
- git add <files>
- # delete any files in remote repo if files are deleted in local repo.
```
