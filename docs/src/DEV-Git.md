# Key Area
- comment best practices
- branching strategy
- pull request
- conflict resolution 

# git client setup
- brew uninstall git-flow (if ver 1.4. gitflow installed)
- brew install git-flow-avh
- git config --global user.email "name@mail.com" // setup email
- git config --global user.email // check setup email
- install gitlens plugin for VS


# setup
1. create github repo (public)
   in github > setting > pages > enable github pages, source = /docs
- in project repo directory

- create github project

> mdBook init docs
> "n" do not add docs in .gitignore
> cd docs
> mdBook build


2. in the repo -> create github project -> create issue #1

- gitflow init
- in git panel -> show hash
- in local develop repo, push to remote develop
- gitflow start feature branch "issue #1" (i.e., issue ticket no.)
- commit message with "resolved #1"
- when done > *Note*"fetch all remote"  and update any new changes
- if conflict, "rebase feature/issue#1" onto "develop"
- for conflict before publish feature
- create PR with codestream
- change base from main to develop
- PR title "Use branch name" with resolved #1 in comment
- code review
- squash and (merged) feature to remote and then local develop
- start release, publish, update main, finish release
- back push local develop to remote develop



# Diagrams as code
[cloud arh](https://diagrams.mingrammer.com/)
https://github.com/plantuml-stdlib/C4-PlantUML
[plantuml](https://plantuml.com/en/)

- brew install graphviz
  [asciidoc](https://docs.asciidoctor.org/diagram-extension/latest/#meme)
  https://asciidoc.org/
  https://vega.github.io/vega/
  https://vega.github.io/vega-lite/


In general, files/ignore rules that have to be universally ignored should go in .gitignore, and otherwise files that you want to ignore only on your local clone should go into .git/info/exclude



# git repo setup
- create a repo in github under organisation
- add member to access repo
- `gh repo clone man-chi/plaftform` in $home/Repo
- `git remote` // if repo has been created local, add reference lin0k to remote repo to local repo

# github flow (remote main > local feature > remote feature > remote main > local main)
- `git branch` // check the current branch
- `git checkout -b feature-PLAT-1` // - b create a new branch
- > use branch naming convention: `feature`-`<jira project key>`-`<jira ticket number>` or `fix`
- `git checkout feature-PLAT-1` // switch to existing feature branch
- write code for feature platform ticket
- `git status` // list all changes since last commit. alias: `gst`
- `git add .` // if newly created, stage changes in local. alias: `gaa`
- `git commit -am "resolved #PLAT-1"` // commit changes in local using comment convention [^2]. alias: `gcam`
- `git diff main` //  compare difference between feature and main. alias: `gd`
- clean up your code with an interactive rebase before submitting your pull request.
- `git push -u origin feature-PLAT-1` // push changes to remote; origin refers to remote/feature repo
- create Pull Request on github by author
- perform quality metrics and change review on github by reviewer
- merge pull request from remote/feature to remote/main by approver
- `git checkout main` // switch back to main branch
- `git pull main` // rebase main
- `git branch -d feature-PLAT-1` // delete local feature branch

# github flow w/ local merge (remote main > local feature > local master > github flow)
- if remote is blocked, do local merge first to keep local main with latest changes
- `git checkout feature`
- `git diff main`
- `git merge main`

# undo a conflict and start over
- `git merge --abort` or  `git rebase --abort`

# temp storage for changes instead of commit_
- `git stash` 

# undo changes
- `git revert` (preferred) append commit applies inverse changes
- `gloga` // git log with graph decorator

# folk vs clone
- git folk is to create a copy of repo from one github account into your github account, whereas clone is from your repo to local [^3].

# commit message - best practices
- only commit changes on the same topic
- using staging
- `git add -p filename` _patch mode_ selective for line of changes in specific file
- commit message:
  subject = concise summary of what happened
  `empty line` 
  Body = detail explanation, diff than before, reason for changes, anything to watch out for?
- do not use force push

# branching strategies
- using github flow (instead of gitflow)
- few branches
- small commits
- high quality QA test automation
- long running branch (main or dev) vs short lived branches (e.g. feature)

# git flow branching
1. create ticket in JIRA, mapping to gitflow short-lived branch  (TASK=FEATURE, sub-task=BUGFIX, epic=RELEASE-0.1.0, bug=HOTFIX)
2. copy branch name from JIRA ticket, e.g. `PLAT-9-research-on-git-flow-avh`
3. gitflow action > "Start Feature" branch, e.g. `PLAT-9-research-on-git-flow-avh`
4. work on changes
5. cmd+0 checkbox changes, message changes, commit changes to the local feature branch starting with "PLAT-9 ..." (DON'T use git push)
6. gitflow action > "Publish Feature" branch (DON'T finish branch), changes will be committed to remote feature branch
7. create pull request with title `PLAT-9-research-on-git-flow-avh`, set marge target to develop <- feature
8. perform code review and approve merge code to develop
9. update local develop
10. gitflow `finish feature branch`, remove feature branch
11. if bug is found on develop branch, start bugfix git flow branch using jira sub-task (continue step 1)
12. if multiple features are merged to develop, ready for release, branch release with ver numbering (v0.1.0)

# Reference:
[basic git by freecodecamp](https://www.youtube.com/watch?v=RGOj5yH7evk)
[advanced git by freecodecamp](https://www.youtube.com/watch?v=Uszj_k0DGsg)
[commit convention by git journal](https://github.com/saschagrunert/git-journal/)
[git fork](https://www.toolsqa.com/git/difference-between-git-clone-and-git-fork/)
[MERGE vs REBASE](https://www.gitkraken.com/learn/git/problems/git-rebase-vs-merge)
[how to gitflow:](https://github.com/petervanderdoes/gitflow-avh)
[git cheat sheet - interactive](https://ndpsoftware.com/git-cheatsheet.html#loc=workspace)
[git altlassian](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)
[gitflow tutorial](https://git.logikum.hu/flow/init)