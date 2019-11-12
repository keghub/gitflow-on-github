# Git flow on GitHub
Testing how to work on GitHub with git flow while taking advantage of all the perks of forks and pull requests

## Setting up your environment
Normally Git flows are based on a single shared repository. In this example, we are going to use GitHub features like forks.

To set up your environment, follow the following steps:
1. Fork this repo into your account (e.g. https://github.com/Kralizek/gitflow-on-github)
2. Clone your fork locally using the default moniker for the remote (`origin`)
```powershell
git clone https://github.com/Kralizek/gitflow-on-github
```
3. Add a source pointing at this repo using the `upstream` moniker
```powershell
git remote add upstream https://github.com/emgdev/gitflow-on-github
```
4. (Optional) Enable support for git flow in your tool(s) of choice

## Refreshing your local repository and fork
Keeping your fork and your local copy as updated as possible is always suggested.

The following steps are best to be performed before starting working on something new.
1. Fetch all updates from all your remotes
```powershell
git fetch --all --prune
```
2. Refresh your local copy of `master` and push updates to your fork
```powershell
git checkout master
git pull upstream master
git push origin master
```
3. Refresh your local copy of `develop` and push updates to your fork
```powershell
git checkout develop
git pull upstream develop
git push origin develop
```

## Hotfixes
According to Git flow, hotfix branches should be started from `master` and merged into it when done. Then, they should also be merged into `develop`.

Follow these steps when working on a hotfix

1. Refresh your local repository and fork as shown above
2. Make sure you are on the `master` branch
```powershell
git checkout master
```
3. Create a hotfix branch
```powershell
git branch -b hotfix/an-urgent-fix
```
4. Implement your hotfix. When done, commit your changes
```powershell
# squashing bugs...
# squashing bugs...
# squashing bugs...
# squashing bugs...
# squashing bugs...
git commit -am "This is a very important fix"
```
5. Push your changes to a remote branch of your fork
```powershell
git push origin hotfix/an-urgent-fix
```
6. In GitHub, create a pull request from your fork to the source repo, having care of selecting `upstream/master` as your target branch
7. Have your hotfix reviewed and merged into `master`
8. In GitHub, create a pull request from the `master` branch of the repo into the `develop` one of the same repo
9. In GitHub, in your fork page remove, the remote branch `hotfix/an-urgent-fix` for the hotfix

## Features
According to Git flow guidelines, feature branches should be started from `develop` and merged into it when done. When finished, they should be merged into the `develop` branch.

Follow these steps when working on a new feature

1. Refresh your local repository and fork as shown above
2. Make sure you are on the `develop` branch
```powershell
git checkout develop
```
3. Create a feature branch 
```powershell
git checkout feature/a-really-good-feature
```
4. Implement your feature. When done, commit your changes
```powershell
# hacking like hell...
# hacking like hell...
git commit -am "This is a major breakthrough"
```
5. Push your changes to a remote branch of your fork
```powershell
git push origin feature/a-really-good-feature
```
6. In GitHub, create a pull request from your fork to the source repo, having care of selecting `upstream/develop` as your target branch
7. Have your amazing feature reviewed and merged into the `develop` branch

