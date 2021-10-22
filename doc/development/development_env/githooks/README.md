
# Git Hooks
Git hooks are scripts that Git executes before or after events such as: commit, push, and receive.  
Git hooks are a built-in feature - no need to download anything. Git hooks are run locally.  
(From https://githooks.com)


## How to Enable Git Hooks

```sh
brew install lefthook
```
Done.

For SourceTree users you might need to run
```sh
sudo launchctl config user path `echo $PATH`
```
Ref:
- https://community.atlassian.com/t5/Bitbucket-questions/SourceTree-Hook-failing-because-paths-don-t-seem-to-be-set/qaq-p/274792#M33050
- https://apple.stackexchange.com/questions/51677/how-to-set-path-for-finder-launched-applications/198282#198282

We use [lefthook](https://github.com/Arkweid/lefthook) as git hooks manager.  
All the git hooks config are version controlled. See `lefthook.yml`  

If you use `asdf` + `asdf-ruby` + `SourceTree`
You might need to check-in and modify your git hook script
https://dev.to/pikachuexe/how-to-use-sourcetree-with-git-hook-via-lefthook-running-bundle-exec-with-asdf-managing-ruby-versions-2j4k
