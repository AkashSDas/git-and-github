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
  
  ## Shortcuts

To add every change to the staging area and commit them at once with a `message`.
```bash
git add . && git commit -m "message"
```