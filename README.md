# common git commands

- git init - to create a git repo
- git add - to add files to the staging area
- git commit - to commit the changes
- git status - to see the status of the repo
- git log - to see the history of the repo
- git diff - to see the changes between the current and previous commit
- git branch - to see the branches in the repo
- git branch <branch-name> - to create a new branch
- git checkout <branch-name> - to switch to a branch
- git merge <branch-name> - to merge a branch into the current branch

## git config

In order to collaborate with other developers, you need to identify your git identity. You can do this by adding your `name` and `email` to the git config.

- git config --global user.name "Your Name" - to set your name
- git config --global user.email "Your Email" - this is the email that will be used when you commit
- git config --list - to see the config

## git init

This is the first step in creating a git repo. You can create a git repo in another directory by passing the directory as an argument to the git init command.

- git init - creates a new git repo in the current directory
- git init <directory> - to create a git repo in another directory

## git add

In order to take a snapshot/commit of the current state of the repo, you need to add all the files you want to commit to the staging area. This is done via the git add command.

- git add . - adds all files to the staging area
- git add <file> - adds a single file to the staging area
- git reset . - to remove all files from the staging area
- git reset <file> - to remove a file from the staging area

## git status

It's useful to know the current status of your repo.

- git status - to see the status of the repo

## .gitignore

This is a file that tells git which files to ignore. It's useful for ignoring temporary files and other files that you don't want to commit.

## git commit

To commit files i.e. moving them from the staging area to the repo, you need to use the git commit command. Every commit has an unique id which is used to identify the commit and compare the changes with other commits.

- git commit - to commit the changes
- git commit -m "message" - to commit with a message
- git commit --amend - to amend the last commit
- git commit --amend -m "message" - to amend the last commit with a message

To omit using the `git add` command to add files to the staging area use the `-a` flag in `git commit` to directly add files to the staging area.

- git commit -a - to commit all files to the staging area
- git commit -a -m "message" - to commit all files to the staging area with a message

## Remote repositories

Git is popular option to collaborate with other developers. Popular services are Github, Bitbucket and Gitlab.

- git remote - to see the list of remote repositories you have access to
- git remote add <remote-name> <url> - to add a remote repository. Common <remote-name> value is `origin`
- git remote -v - to see the list of remote repositories urls you have access to
- git remote show <remote-name> - to see more details of a remote repository

## git push

To push the changes to the remote repository, you need to use the git push command.

- git push - to push the changes to the remote repository
- git push <remote-name> - to push the changes to the remote repository
- git push <remote-name> <branch-name> - to push the changes to the remote repository with a branch name
- git push <remote-name> <branch-name> -u - `u` flag to set origin repo to the upstream remote in the git config file. This allows us to use git pull command to pull from the remote repository without requiring additional arguments. You want to use the `-u` flag when remote repo is final source of truth
  
## Shortcuts

To add every change to the staging area and commit them at once with a `message`.
```bash
git add . && git commit -m "message"
```