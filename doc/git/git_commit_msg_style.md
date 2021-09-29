# Git Commit Message Style (completely personal opinion)

Add 1-2 of these symbols with a space to the beginning of each line in commit message
This should make the log easier to read / scan & filter
- `+` for method/class/file addition
- `-` for method/class/file removal
- `*` for changes (feature or behaviour related only, not code refactor)
- `!` for bug fixes
- `^` for external dependency update (Ruby gems, JS libraries), product releases
- `v` for external dependency downgrade (e.g. new version got issue requiring rollback to an older version)
- `$` for code refactor (`$` means time == money)
- `~` for comment/style/whitespaces/doc change only
