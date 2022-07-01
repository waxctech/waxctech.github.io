# VCode setup (if needed)

- rust analyzer, Darcula Theme, gitlens

# intellij community setup (default)

- in git panel -> show hash
- update keymap

# gitflow4idea plugin setup

- check `push on finish feature`
- check `push on finish release`

# popular intellij plugin

- material theme UI
- gitflow integration plus
- gittoolbox: auto fetch
- codestream: issue, code review, PR, feedback, codemark in IDE
- plantuml
- rust, toml, grcov, evcxr plugin: required for rust
- ignore
- CSV
- sonarlint
- docker
- aws
- ideola
- database navigation
- graphql
- terraform
- tabinine AI code
- turn off all unused intellij plugin


# codestream code collaboration  
- create jira project -> link to github (same name)
- in jira app, github configure -> connect github organization.
- if project is not shown codestream, reinstall codestream intellij plugin
- use codemarks instead of bookmark

# task management w/ Github flow on codestream
- create issue
- issue -> start work (move issue to in process & start feature branch)
- commit with jira ID, e.g. WAXC-1, comment with resolves WAXC-1
- create PR
- review and approve merge
- delete remote/feature branch
- mark issue as 'Done'

# create mdbook in repo

- `mdBook init docs`: initialized mdbook in docs
- `n`: do not add docs in .gitignore
- `cd docs`
- `mdBook build`: build mdbook in docs
  

