# Git Notes: Commit, Reset, and Revert

## Introduction

Before learning these commands, understand Git's three areas:

Working Tree (Your actual files)
↓
Staging Area (Index)
↓
Repository (Commits)

Think of Git like a game with save points:
- Working Tree = Current game progress
- Staging Area = Things you want to save
- Commit = Saved checkpoint

---

# 1. Git Commit

## What is a Commit?

A commit is a snapshot of your project at a specific point in time.

Think of it as: Save Game

Whenever you complete a meaningful piece of work, you create a commit.

## Why Do We Use Commit?

Imagine you are building an e-commerce website.

Day 1: Login Page
Day 2: Product Listing Page
Day 3: Shopping Cart

Each day you create a commit. If Day 3 breaks everything, you can return to Day 2.

### Basic Workflow

git add .
git commit -m "Add login page"

Git creates a snapshot of the staged changes.

### Good Commit Messages

Bad:
- fix
- update
- done

Good:
- Add login validation
- Fix payment calculation bug
- Update dashboard UI

Rule:
Verb + What Changed

### Important

git commit only saves locally.

To upload to GitHub:

git push

---

# 2. Git Reset

## What is Reset?

Reset moves your branch backward in history.

Example:

A → B → C (HEAD)

### Understanding HEAD~1

HEAD = C
HEAD~1 = B
HEAD~2 = A

Meaning:
Go backward from the current commit.

## Soft Reset

git reset --soft HEAD~1

What Happens?
- HEAD moves backward
- Staging area remains unchanged
- Working files remain unchanged

Changes from removed commit remain staged.

Use Case:
Wrong commit message or forgot some files.

## Mixed Reset

git reset HEAD~1

What Happens?
- HEAD moves backward
- Staging area reset
- Working files remain unchanged

Changes become unstaged but still exist.

## Hard Reset

git reset --hard HEAD~1

What Happens?
- HEAD moves backward
- Staging area reset
- Working files reset

Everything from the removed commit disappears.

Warning:
Can permanently remove work.

## Reset Summary

soft  = reset HEAD only
mixed = reset HEAD + staging
hard  = reset HEAD + staging + files

---

# 3. Git Revert

## What is Revert?

Revert creates a NEW commit that undoes an older commit.

It does not remove history.

Example:

Before:
A → B → C

Run:
git revert HEAD

After:
A → B → C → D

Where D reverses C.

## Why Not Use Reset?

If commit C has already been pushed, other developers may already have it.

Using reset and force push rewrites history.

Revert is safer because it preserves history.

## Revert Latest Commit

git revert HEAD

Undo the latest commit.

## Revert Previous Commit

git revert HEAD~1

Undo the commit before HEAD.

## Common Error

git revert HEAD~1

Error:
Your local changes would be overwritten.

Reason:
You have uncommitted changes.

Fix:

git stash
git revert HEAD~1
git stash pop

---

# Reset vs Revert

Reset:
- Removes commit
- Rewrites history
- Best for local commits

Revert:
- Creates new commit
- Preserves history
- Best for pushed/shared commits

---

# Golden Rule

Local commit not shared yet:
git reset

Commit already pushed/shared:
git revert

---

# Final Mental Model

Commit = Create checkpoint

Reset = Pretend commit never happened

Revert = Create new commit that cancels a previous commit
