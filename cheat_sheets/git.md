# git

## Setting up ssh

* Open the terminal
* Run `ssh-keygen`
* Copy the contents of the file at `~/.ssh/id_rsa.pub` into your clipboard
* Log into to your Github account in your browser
* Go to https://github.com/settings/keys
* Add your SSH key

## Testing your SSH key

* Go to Github, and login
* Make a new repository
* Press the green `CODE`
* Press the `SSH` option
* Copy the `URL`
* In your command line, type the following
```
git clone <url>
```
* `cd <url>`
* `code .`
* Edit away
* `git add -A`
* `git commit -m "Some message"`
* `git push`

## Config

* `git config --global core.editor "code --wait"` - Use VS Code as default editor
* `git config --global --add --bool push.autoSetupRemote true` - Set upstream automatically (note this only works in very recent versions of `git`: you may come across older versions of `git` that don't support this)
* `git config --global user.name "Mona Lisa"` - Configure the username in `git`. Note, this is *NOT* the username you use to log into Github or Gitlab, merely the name of the user recorded in git logs
* `git config user.email "youremail@yourdomain.com"` - Configure the email in `git`. Note, this is *NOT* the email you use to log into Github or Gitlab, merely the email of the user recorded in git logs
  * Please note that in public repositories, this email will be exposed to the public, making it a potential victim of spambots and hackers. If you don't want to expose your email address to the public, then either set up a 'junk' email address, or set a random email address here.

## Workflow

* `git add -A` - Add all new changes to all new files to the staging area
* `git commit -m "<some_message>"` - Create a commit from all files in the staging area
* `git push` - 'Push' your changes to the git server (usually the repository in Github)
  * Usually, the first time you push a branch, `git` will ask you to set an upstream branch. Read the instructions that `git` spits out carefully. Alternatively, use config to auto-setup the upstream branch.
* `git pull` - 'Pull' changes on the server on the upstream branch and synchronize your local branch to it.
* `git fetch` - 'Fetch' all changes on the server that are not in your local clone. This does not change your local branches, but it updates your local copies of remote branches so that `git pull` has less to do
* `git checkout -b <new_branch>` - Create a new branch, and switch to it
* `git checkout <branch>` - Checkout an existing branch

## After remote trunk has changed

The following instructions assume that the remote trunk branch is called `main`. If it's not, then alter these instructions as appropriate.

1. Make sure that you're checked out on your working branch.
2. If you have any changes that are not staged, `git stash`. Alternatively, stage, commit and push all changes (typically with a git message of `WIP` = 'Work in progress')
3. Checkout the trunk branch `git checkout main`
4. Update your trunk branch with changes from the server `git pull`
5. Check out your working branch `git checkout <your_branch_name>`
6. Merge the trunk branch into your working branch `git merge main`
7. This might result in some merge conflicts. If that's the case
   1. Resolve the conflicts. VS Code and Pycharm both have pretty good interfaces for this
   2. `git add -A` your resolutions
   3. Continue with the merge `git merge --continue`
8. This will make a new commit on your working branch, which you will have to push to the server `git push`
9. If you stashed anything in 2., you can restore them by `git stash pop`