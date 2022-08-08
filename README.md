# git-and-github

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

## git merge

Difficult way to merge remote and local repos. Fetch the remote repo and merge the two branches.

- git fetch - to fetch the remote repo

This will create a `remote/main` branch in the local repo. Merging the `remote/main` branch into the `main` branch will result in syncing local repo with remote repo.

- git merge <branch-name> - to merge a branch into the current branch

There are different strategies of merging two branches. The simplest is the `Fast Forward` strategy.

## git pull

Simpler way of mergin remote and local repos.

- git pull - to pull the changes from the remote repository (if you have used the `-u` flag which pushing)
- git pull <remote-name> <branch-name> - to pull the changes from the remote repository (if you have not used the `-u` flag which pushing)

If you have any uncommitted changes in your current working directory and you are trying to pull down from remote then the operation will fail. It's not going overwrite your local changes first. To solve this either commit your local changes first OR use a technique called `stash`.

If your local code is modified in the same line of code as the code in the remote repository then you will get a merge conflict.

## git clone

- git clone <url> - to clone a remote repository
- git clone <url> <directory> - to clone a remote repository in a different directory
- git clone <url> <directory> -b <branch-name> - to clone a remote repository in a different directory with a branch name

## git branch

- git branch - to see the list of branches in the repo
- git branch -M <branch-name> - to rename a branch
- git branch <branch-name> - to create a new branch
- git branch -d <branch-name> - to delete a branch, safer option. Will delete only if it is not merged in the main branch
- git branch -D <branch-name> - to delete a branch, danger option. Will delete no matter what is the status of the branch

## git checkout

- git checkout - to switch to the main branch
- git checkout <branch-name> - to switch to a branch
- git checkout -b <branch-name> - to create a new branch and switch to it
- git checkout - - to checkout the previous branch

## Merge Conflicts

A conflict occurs when you are merging 2 different branches which modifies the same line. In this case Git doesn't know which one is the correct one thus creating a conflict.

You can use different ways to solve this problem:

- Accept current changes - from the main branch
- Accept incoming changes - from the other branch
- Accept both changes
- Compare changes and decide what to do

You can use `git diff` to see the changes in the conflict.

If you don't know which option to select then use the `git merge --abort`. It will take you to the origin state before the merge was started. But if you are ok with other options then you have to make an extra commit and the conflict is resolved. This is called a `merge commit` and it is required since the two branches had conflict. This is different from using the `Fast Forward` technique where you don't require an additional commit.

Merge Conflict aren't that big of a deal. When it happens do the following:

- Find the files which are in conflict
- Choose the correct one, merge it and move on

## Codespaces

An intresting feature of Github to know about.

## Fork (Github)

If you want to work on the same repo with other developers but want host it yourself and do things in isolation, you can fork the repo in Github and it will copy that repo to your account. This allows you make changes without affecting the original repo. At time same time it maintain a link with original repo from which can fetch updates. The original repo is the source of truth and is known as `upstream` repo.

A common thing devs do is they will work on feature in this forked repo and then make a pull request to the original repo. The author of the original repo will review your changes and can decide whether to merge or not.

Tip to be in sync with the `upstream`:

- git remote add upstream <url> - to add the upstream repo
- git fetch upstream - to fetch the updates from the upstream repo
- git rebase upstream/master - to add the changes from the upstream repo onto the current branch

## git reset

Techniques to fix screw ups in your repo. When your project gets to state that's not ideal, Git provides several techniques to get it to an acceptable state.

There are 3 different file areas in Git:

- Working dir - the files which are currently being worked on
- Staging area - the files which are staged for commit
- Commit history - the files which are committed

### Removing a file from the staging area

- git reset - to remove all the files from the staging area
- git reset HEAD <file-name> - to remove a file from the staging area

### Bad commit and go back to previous commit

Get the SHA id of the previous commit to which you want to go back.

- git reset <SHA-id> - to go back to the commit with the SHA id

By default Git reset will run in `mixed mode`. Which means it will take us to previous commit but won't delete the files that we're working on. Those files will be left in the staging area.

Using the `--hard` flag will take you to the previous commit but would also delete the files and this is irreversible.

- git reset --hard <SHA-id> - to go back to the commit with the SHA id and delete the files.

## Remember

Don't do a rest when the commit is already been pushed to a remote repo on Github. Since there are other developers who rely on you commit and if you remove it then it can be very hard to reconcile the changes.

## git revert

Never reset a commit that's already been pushed to a remote repo, but there's still a way you can undo a commit without creating issues for others who are working on a repo.

To do this, get the SHA id of the commit you want to revert and then use the `git revert` command.

- git revert <SHA-id> - to revert the commit with the SHA id

This will remove the files just like `git reset` command but the bad commit won't be lost, it will still be a part of the commit history. But we'll have a new commit with the reverted changes. This can be pushed.

Generally:

- git reset - when working alone
- git revert - when working with other devs

## git ammend

If you make a minor issue in Git (typo in commit message OR forgot to stage a file with `git add`) then you can use the `git amend` command to amend the commit without having to `reset` OR `revert`. This works only on a couple of issue but whenever possible use `git ammend`.

To update the commit message:

- git commit --ammend -m "message" - to change the commit message

To commit files you forgot to stage:

- git add . - to stage all the files that you forgot to commit
- git commit --ammend --no-edit - to amend the commit without changing the commit message

## git stash

Save your work for later without commiting it. This is very useful when you working on something experimental that's not ready to be commited yet but you want to work on it later on, but for now you want to go back to the normal state of the repo to work on something else.

- git stash - to stash your work
- git stats save <name> - to stash your work with a name
- git stash pop - to pop the stash and bring back your work
- git stash list - to see the list of stashes
- git stash clear - to clear all the stashes

Be careful because you could end with merge conflicts when updating same lines of code in different stashes.

## git rebase

While working in a team, a lot of devs prefer using `rebase` instead of `merge`. In `merge` you have a dev who creates a branch, make some commits to it and then merges it back to the main branch. When you have a large team with multiple people working on multiple features, it would lead to a very complex commit history. This makes it harder to roll back to a previous state if bugs are introduced.

So instead of `merge` we can use `rebase`. This will take a feature branch and rewrite history to make it look like you've just started working on the feature branch with the latest updates from the main branch (OR maybe someother branch that you've rebased).

This should only be done when you are working on you own private feature branch. It a destructive action as it rewrites history. So if you have an active public branch that bunch of people are working on the you would not want to rebase it because then everybody will be working on a different history.

Another way to think about this that `rebase` keeps your feature branch up to date with the main branch.

Tip - If you are not sure whether to use rebase OR not:

- Create an extra branch from your current feature branch
- Rebase on that branch to make sure everything is working fine
- If it is then delete the temporary branch and use rebase on the feauture branch

### Squash

When you have a large number of commits you can squash them into one commit. This is useful when you have a large number of commits and you want to keep a smaller number of commits.

- git rebase --no-interactive - to squash the commits

An editor will open (maybe Vim) where you can change the from `pick` to `squash` the commits which you want to squash and then save the file. Once that is done, an another file will open to customize the commit message (you can quite it to use the default). This will rebase with the squashed commits replacing the commit you've squashed.

This is the last thing you do before you submit a pull request OR merge your feature to the main branch.

The `fixup` also works similar to `squash` but it discards the commit message from the commit you are squashing.

## Tips and Tricks

### Add and Committing

```bash
# 💩

git add .
git commit -m "message"

OR

git add . && git commit -m "message"
```

```bash
# ✅
git commit -am "message"
```

OR even better create aliases for you Git work.

```bash
# 🔥
git config --global alias.ac "commit -am"
git ac "pro way"
```

### Amend

Do this only when you've not pushed your code to a remote repo.

```bash
# update the latest commit
git commit --amend -m "updated message"

# add new files to the latest commit
git add .
git commit --amend --no-edit
```

### Force

Overwrite commit history of remote. If there are commits in remote repo which the local repo doesn't have then you'll loose them.

```bash
# ⚠️
git push origin main --force
```

### Bisect

It allows you to point at the last working commit. Then it will run a binary search to find the commit where the bug is and then you can fix it. If the commit looks good then mark it as something (good) and then move on till you find the bad one.

```bash
git bisect start
git bisect bad
git bisect good <SHA-id>
git bisect bad
```

### Fixup and Squash

```bash
# fixup
git commit --fixup <SHA-id>

# squash
git commit --squash <SHA-id>
```

The above commands tells Git in advance that you're going to squash them. So when you do rebase with `--autosquash` flag then it will squash the commits.

```bash
git rebase -i --autosquash
```

### Hooks

This is useful when you want to run some commands before you commit and after you commit.
