# git advance topics
- branching strategy
- pull request
- conflict resolution 
- commit message best practices

# git client setup
- `brew uninstall git-flow` (if ver 1.4. gitflow installed)
- `brew install git-flow-avh`, 1.12.3 (AVH Edition)
- `git config --global user.email "name@mail.com"`: setup email
- `git config --global user.email`: check setup email

# github repo setup
- create github repo in organization
- `gh repo clone waxctech/waxctech.github.io` in $home/Repo
- `git remote`: if repo has been created in local, add reference link to remote repo to local repo
- add member to access repo
- enable github page -> in github > setting > pages > enable github pages, source = /docs
- create github project with automated review workflow

# gitflow setup
- on gitflow plugin, select `gitflow init`: create gitflow structure, local/develop
- push local/develop to remote/develop: due to missing in gitflow4idea plugin @TODO to fix

# gitflow branching: procedure for each new task
- *first thing first: fetch remote and update local*
- on codestream plugin, create new issue (label: feature, bug, release, hotfix)
- open gh ticket, assign project
- on gitflow, `Start Feature`: use `name of issue ticket_#ticket number` in github, e.g. "issue_#1"
- commit changes to local/feature branch, **do NOT push local/feature**
- *when work done, always check conflict before PR:*
  - fetch all `remote`
  - update all `local`
- if conflicted, rebase:  
  - checkout `local/develop`
  - rebase `local/main` on `local/develop`
  - checkout `local feature/issue_#1`
  - rebase `local/feature/issue_#1` onto `local/develop`
  - on gitflow, `Publish Feature`: push changes from local/feature to remote/feature
- on codestream, create Pull Request
  - use branch name as PR name
  - change base from `main` to `develop`
  - assign PR to project
- perform code review by reviewer
- use `squash and merged` to merge changes from remote/feature to remote/develop
- update remote/develop to local/develop
- on gitflow, `Finish Feature`: delete feature branch, auto push from local/develop to remote/develop
- resolved gh issue would be moved to done column by automation
> for `Start Release`, repeat the same flow for `release-v0.1.0` but only hotfix is allowed for merging changes from develop should be blocked

# commit message best practice
- do not use force push
- only commit changes on the same topic
- commit message:
```
  subject = issue ticket name and #number
  <empty line> 
  Body = detail explanation, diff than before, reason for changes, anything to watch out for?
  resolves: #ticket_number
```

# branching strategies: gitflow vs github flow
- use gitflow for multi teams, complex workflow before go-live
- using github flow for few branches small commits but required high quality QA test automation
- long running branch (main or dev) vs short lived branches (e.g. feature)

# .ignore vs .git/info/exclude
- files/ignore rules that have to be universally ignored should go in .gitignore
- otherwise files that you want to ignore only on your local clone should go into .git/info/exclude

# conflict resolution in github flow
- github flow w/ local merge (remote main > local feature > local main > github flow)
- if remote is blocked, do local merge first to keep local main with the latest changes
- `git checkout feature`
- `git diff main`
- `git merge main`

# undo a conflict and start over
- `git merge --abort` or  `git rebase --abort`

# temp storage for changes instead of commit
- `git stash`

# undo changes
- `git revert` (preferred) append commit applies inverse changes
- `gloga` // git log with graph decorator

# folk vs clone
- git folk is to create a copy of repo from one github account into your github account
- clone is from your repo to local.

# fetch vs pull
- fetch: only check and retrieve meta data from remote (without code merged)
- pull: copy change from remote (with code merged)
- update: intellij feature which combines fetch + pull

# github flow (deprecated by gitflow)
- workflow: remote main > local feature > remote feature > remote main > local main 
- `git branch`: check the current branch
- `git checkout -b feature-PLAT-1`: - b create a new branch
- `feature`-`<jira project key>`-`<jira ticket number>`: branch naming convention
- `git checkout feature-PLAT-1`: switch to existing feature branch
- write code for feature platform ticket
- `git status`: list all changes since last commit. alias: `gst`
- `git add .`: if newly created, stage changes in local. alias: `gaa`
- `git commit -am "resolved #PLAT-1"`: commit changes in local using comment convention [^2]. alias: `gcam`
- `git diff main`: compare difference between feature and main. alias: `gd`
- clean up your code with an interactive rebase before submitting your pull request.
- `git push -u origin feature-PLAT-1` // push changes to remote; origin refers to remote/feature repo
- create Pull Request on github by author
- perform quality metrics and change review on github by reviewer
- merge pull request from remote/feature to remote/main by approver
- `git checkout main` // switch back to main branch
- `git pull main` // sync changes from remote/main to local/main
- `git branch -d feature-PLAT-1` // delete local feature branch

# Reference
[interactive git cheat sheet](https://ndpsoftware.com/git-cheatsheet.html#loc=workspace)
[basic git video by freecodecamp](https://www.youtube.com/watch?v=RGOj5yH7evk)
[advanced git video by freecodecamp](https://www.youtube.com/watch?v=Uszj_k0DGsg)
[git tutorial by gitkraken](https://www.gitkraken.com/learn/git)
[merge vs rebase](https://www.gitkraken.com/learn/git/problems/git-rebase-vs-merge)
[how to gitflow:](https://github.com/petervanderdoes/gitflow-avh)
[git tutorial by altlassian](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)
[gitflow tutorial](https://git.logikum.hu/flow/init)
[gitflow4idea plugin](https://plugins.jetbrains.com/plugin/18320-git-flow-integration-plus)
[good commit message](https://www.freecodecamp.org/news/writing-good-commit-messages-a-practical-guide/)