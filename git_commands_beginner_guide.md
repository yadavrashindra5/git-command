# Git Commands Cheat Sheet for Beginners

This document explains important Git commands with:
- Simple description
- Command syntax
- Real-world example
- Clear explanation of the example

---

# 1. git init

## Description
Creates a new Git repository in your current project folder.

Use this when:
- starting a brand-new project

## Command

```bash
git init
```

## Example

```bash
mkdir my-project
cd my-project
git init
```

## Explanation

- `mkdir my-project` → creates a project folder
- `cd my-project` → enters the folder
- `git init` → turns the folder into a Git repository

Git now starts tracking changes inside this project.

---

# 2. git clone

## Description
Downloads an existing repository from GitHub or another remote server.

## Command

```bash
git clone <repository-url>
```

## Example

```bash
git clone https://github.com/user/project.git
```

## Explanation

- Git downloads the project
- Creates a folder named `project`
- Copies all code and commit history to your computer

You use this when working on an existing project.

---

# 3. git status

## Description
Shows the current state of your repository.

This is the MOST USED Git command.

## Command

```bash
git status
```

## Example

```bash
git status
```

## Explanation

Git will show:
- modified files
- untracked files
- staged files
- current branch

Example output:

```bash
modified: app.js
untracked: style.css
```

Meaning:
- `app.js` was changed
- `style.css` is new and not tracked yet

---

# 4. git add

## Description
Moves files into the staging area before committing.

## Command

```bash
git add <file-name>
```

## Example

```bash
git add app.js
```

## Explanation

Suppose you changed `app.js`.

Running:

```bash
git add app.js
```

tells Git:

> "I want to include this file in the next commit."

---

## Add all files

```bash
git add .
```

## Explanation

Adds ALL changed files to staging.

Use carefully.

---

# 5. git commit

## Description
Creates a snapshot of your staged changes.

## Command

```bash
git commit -m "message"
```

## Example

```bash
git commit -m "Add login page"
```

## Explanation

- `-m` means message
- `"Add login page"` explains what changes were made

Git saves a permanent snapshot of your work.

Think of commits like save points in a game.

---

# 6. git log

## Description
Shows commit history.

## Command

```bash
git log
```

## Example

```bash
git log --oneline
```

## Explanation

`--oneline` shows commits in short format.

Example output:

```bash
a1b2c3 Add login page
d4e5f6 Fix navbar bug
```

Each line is a commit.

---

## Graph View

```bash
git log --oneline --graph --all
```

## Explanation

Shows:
- branches
- merges
- commit structure

Very useful for understanding project history.

---

# 7. git diff

## Description
Shows changes between files and commits.

## Command

```bash
git diff
```

## Example

```bash
git diff
```

## Explanation

Suppose you changed:

```js
const name = "John"
```

to:

```js
const name = "Rashindra"
```

`git diff` shows exactly what changed.

Useful before committing.

---

## Staged Changes

```bash
git diff --staged
```

## Explanation

Shows changes already added with `git add`.

---

# 8. git branch

## Description
Creates or lists branches.

## Command

```bash
git branch
```

## Example

```bash
git branch feature-login
```

## Explanation

Creates a new branch named:

```bash
feature-login
```

Branches help you work on features independently.

---

# 9. git switch

## Description
Switches between branches.

## Command

```bash
git switch <branch-name>
```

## Example

```bash
git switch feature-login
```

## Explanation

Moves you from current branch to:

```bash
feature-login
```

Now your work happens inside that branch.

---

## Create and Switch Together

```bash
git switch -c feature-login
```

## Explanation

- creates branch
- immediately switches to it

Very commonly used.

---

# 10. git merge

## Description
Combines another branch into the current branch.

## Command

```bash
git merge <branch-name>
```

## Example

```bash
git merge feature-login
```

## Explanation

Suppose:
- login feature was built in `feature-login`
- you are currently on `main`

Running:

```bash
git merge feature-login
```

brings login feature into main branch.

---

# 11. git rebase

## Description
Moves commits to another base commit.

Creates cleaner history.

## Command

```bash
git rebase main
```

## Example

```bash
git switch feature-login
git rebase main
```

## Explanation

Suppose:
- main branch received new commits
- your branch is outdated

Rebase moves your feature commits on top of latest main branch.

This keeps history cleaner than merge sometimes.

---

# 12. git remote add

## Description
Connects local repository to remote repository.

## Command

```bash
git remote add origin <url>
```

## Example

```bash
git remote add origin https://github.com/user/project.git
```

## Explanation

- `origin` is remote name
- URL points to GitHub repository

Now your local project is connected to GitHub.

---

# 13. git push

## Description
Uploads commits to remote repository.

## Command

```bash
git push origin main
```

## Example

```bash
git push origin main
```

## Explanation

- `origin` → remote repository
- `main` → branch name

Your local commits are uploaded to GitHub.

---

# 14. git pull

## Description
Downloads latest changes and merges them.

## Command

```bash
git pull
```

## Example

```bash
git pull origin main
```

## Explanation

Downloads latest commits from GitHub and updates your local branch.

Use before starting work daily.

---

# 15. git fetch

## Description
Downloads remote changes WITHOUT merging.

## Command

```bash
git fetch
```

## Example

```bash
git fetch origin
```

## Explanation

Git downloads latest updates but does not modify your files.

Safer than pull when checking updates.

---

# 16. git restore

## Description
Discards local changes.

## Command

```bash
git restore <file>
```

## Example

```bash
git restore app.js
```

## Explanation

Suppose you accidentally changed `app.js`.

This command removes local changes and restores previous version.

WARNING:
You lose uncommitted changes.

---

# 17. git restore --staged

## Description
Removes file from staging area.

## Command

```bash
git restore --staged <file>
```

## Example

```bash
git restore --staged app.js
```

## Explanation

Suppose you accidentally used:

```bash
git add app.js
```

This command unstages the file.

Your changes remain in the file.

---

# 18. git reset

## Description
Moves HEAD and optionally removes commits or changes.

Powerful but dangerous.

---

## Soft Reset

```bash
git reset --soft HEAD~1
```

## Explanation

Removes latest commit but keeps changes staged.

Useful when:
- commit message was wrong
- forgot to add files

---

## Hard Reset

```bash
git reset --hard HEAD~1
```

## Explanation

Deletes:
- latest commit
- all related changes

WARNING:
Changes are permanently lost.

---

# 19. git stash

## Description
Temporarily saves unfinished work.

## Command

```bash
git stash
```

## Example

```bash
git stash
```

## Explanation

Suppose:
- you are working
- suddenly need to switch branches

But your work is incomplete.

`git stash` hides your current changes safely.

---

# 20. git stash pop

## Description
Restores stashed changes.

## Command

```bash
git stash pop
```

## Example

```bash
git stash pop
```

## Explanation

Brings back previously stashed work.

---

# 21. git remote -v

## Description
Shows connected remote repositories.

## Command

```bash
git remote -v
```

## Example

```bash
git remote -v
```

## Explanation

Example output:

```bash
origin https://github.com/user/project.git
```

Shows where your repository pushes and pulls code.

---

# 22. git show

## Description
Displays detailed commit information.

## Command

```bash
git show
```

## Example

```bash
git show
```

## Explanation

Shows:
- latest commit
- author
- date
- changed lines

Useful for inspecting commits.

---

# 23. git blame

## Description
Shows who changed each line in a file.

## Command

```bash
git blame <file>
```

## Example

```bash
git blame app.js
```

## Explanation

Shows:
- who modified each line
- commit id
- modification date

Very useful for debugging.

---

# Daily Real-World Workflow

## Example Workflow

```bash
git pull
git switch -c feature-login
git add .
git commit -m "Add login feature"
git push origin feature-login
```

## Step-by-Step Explanation

### 1. Pull latest changes

```bash
git pull
```

Gets latest project updates.

---

### 2. Create feature branch

```bash
git switch -c feature-login
```

Creates separate branch for login feature.

---

### 3. Add changes

```bash
git add .
```

Stages all changed files.

---

### 4. Commit changes

```bash
git commit -m "Add login feature"
```

Creates snapshot of work.

---

### 5. Push branch

```bash
git push origin feature-login
```

Uploads feature branch to GitHub.

---

# Important Beginner Advice

Before running unfamiliar commands:

```bash
git <command> --help
```

Examples:

```bash
git reset --help
git rebase --help
```

This helps avoid dangerous mistakes.

---

# Best Commands to Practice Daily

```bash
git status
git log --oneline --graph --all
git diff
```

These help you understand:
- repository state
- commit history
- file changes

Master these first.
