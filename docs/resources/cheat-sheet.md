---
layout: default
title: Git Cheat Sheet
parent: Resources
nav_order: 3
---

# Git Cheat Sheet
{: .no_toc }

Quick reference for essential Git commands.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Setup and Configuration

```bash
# Set user name and email
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# View configuration
git config --list

# Set default editor
git config --global core.editor "code --wait"

# Set default branch name
git config --global init.defaultBranch main

# Enable color output
git config --global color.ui auto
```

## Creating Repositories

```bash
# Initialize a new repository
git init

# Clone an existing repository
git clone <url>

# Clone to specific directory
git clone <url> <directory>

# Clone specific branch
git clone -b <branch> <url>
```

## Basic Snapshotting

```bash
# Check status
git status

# Short status
git status -s

# Stage specific file
git add <file>

# Stage all changes
git add .

# Stage all files of type
git add *.js

# Remove file from staging
git reset <file>

# Commit staged changes
git commit -m "message"

# Stage and commit in one command
git commit -am "message"

# Amend last commit
git commit --amend

# Remove file from working tree and index
git rm <file>

# Remove file from index only
git rm --cached <file>

# Move/rename file
git mv <old> <new>
```

## Branching and Merging

```bash
# List branches
git branch

# List all branches (including remote)
git branch -a

# Create new branch
git branch <branch-name>

# Switch to branch
git checkout <branch-name>

# Create and switch to new branch
git checkout -b <branch-name>

# Switch to branch (newer syntax)
git switch <branch-name>

# Create and switch (newer syntax)
git switch -c <branch-name>

# Merge branch into current branch
git merge <branch-name>

# Delete branch
git branch -d <branch-name>

# Force delete branch
git branch -D <branch-name>

# Rename current branch
git branch -m <new-name>
```

## Inspection and Comparison

```bash
# View commit history
git log

# View compact log
git log --oneline

# View log with graph
git log --graph --oneline --all

# View log for specific file
git log <file>

# View changes
git diff

# View staged changes
git diff --staged

# View changes between branches
git diff <branch1>..<branch2>

# View changes in specific file
git diff <file>

# Show commit details
git show <commit-hash>

# Show file at specific commit
git show <commit-hash>:<file>
```

## Sharing and Updating

```bash
# List remotes
git remote -v

# Add remote
git remote add <name> <url>

# Remove remote
git remote remove <name>

# Rename remote
git remote rename <old> <new>

# Fetch changes from remote
git fetch <remote>

# Fetch from all remotes
git fetch --all

# Pull changes (fetch + merge)
git pull <remote> <branch>

# Pull with rebase
git pull --rebase <remote> <branch>

# Push to remote
git push <remote> <branch>

# Push and set upstream
git push -u <remote> <branch>

# Push all branches
git push --all

# Push tags
git push --tags

# Force push (use with caution!)
git push --force

# Delete remote branch
git push <remote> --delete <branch>
```

## Undoing Changes

```bash
# Discard changes in file
git checkout -- <file>

# Discard all changes
git checkout -- .

# Restore file from specific commit
git checkout <commit> <file>

# Unstage file
git reset HEAD <file>

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Revert commit (create new commit)
git revert <commit>

# Clean untracked files (preview)
git clean -n

# Clean untracked files (execute)
git clean -f

# Clean untracked files and directories
git clean -fd
```

## Stashing

```bash
# Stash changes
git stash

# Stash with message
git stash save "message"

# List stashes
git stash list

# Apply latest stash
git stash apply

# Apply specific stash
git stash apply stash@{n}

# Apply and remove stash
git stash pop

# Drop stash
git stash drop stash@{n}

# Clear all stashes
git stash clear

# Show stash contents
git stash show -p stash@{n}
```

## Tagging

```bash
# List tags
git tag

# Create lightweight tag
git tag <tag-name>

# Create annotated tag
git tag -a <tag-name> -m "message"

# Tag specific commit
git tag <tag-name> <commit>

# Show tag information
git show <tag-name>

# Push tag to remote
git push origin <tag-name>

# Push all tags
git push --tags

# Delete local tag
git tag -d <tag-name>

# Delete remote tag
git push origin --delete <tag-name>

# Checkout tag
git checkout <tag-name>
```

## Advanced Operations

```bash
# Cherry-pick commit
git cherry-pick <commit>

# Rebase current branch
git rebase <branch>

# Interactive rebase
git rebase -i HEAD~n

# Continue rebase after resolving conflicts
git rebase --continue

# Abort rebase
git rebase --abort

# Squash last n commits
git rebase -i HEAD~n

# Find commits by message
git log --grep="pattern"

# Find commits by author
git log --author="name"

# Search in code
git grep "pattern"

# Show who changed each line
git blame <file>

# Show commit that introduced a bug (binary search)
git bisect start
git bisect bad
git bisect good <commit>
```

## Git Workflow Patterns

### Feature Branch Workflow

```bash
# Create feature branch
git checkout -b feature/new-feature

# Work on feature
# ... make changes ...
git add .
git commit -m "Add new feature"

# Update from main
git checkout main
git pull origin main
git checkout feature/new-feature
git merge main

# Push feature branch
git push -u origin feature/new-feature

# Create pull request on GitHub
# After merge, delete local branch
git checkout main
git branch -d feature/new-feature
```

### Hotfix Workflow

```bash
# Create hotfix branch from main
git checkout main
git pull origin main
git checkout -b hotfix/critical-bug

# Fix bug
git add .
git commit -m "Fix critical bug"

# Push and merge quickly
git push -u origin hotfix/critical-bug
# Create and merge PR
git checkout main
git pull origin main
git branch -d hotfix/critical-bug
```

## Aliases

Set up useful shortcuts:

```bash
# Status
git config --global alias.st status

# Checkout
git config --global alias.co checkout

# Commit
git config --global alias.ci commit

# Branch
git config --global alias.br branch

# Log with graph
git config --global alias.lg "log --graph --oneline --all"

# Last commit
git config --global alias.last "log -1 HEAD"

# Undo last commit
git config --global alias.undo "reset --soft HEAD~1"

# List aliases
git config --global alias.aliases "config --get-regexp ^alias\."
```

## .gitignore Patterns

```bash
# Ignore specific file
secret.txt

# Ignore all files with extension
*.log

# Ignore directory
node_modules/

# Ignore files in directory
build/*.js

# Ignore files in all subdirectories
**/temp

# Negate pattern (don't ignore)
!important.log

# Ignore files starting with
temp*

# Ignore files ending with
*~
```

## Common .gitignore Templates

### Node.js
```
node_modules/
npm-debug.log
.env
dist/
build/
```

### Python
```
__pycache__/
*.py[cod]
venv/
.env
*.egg-info/
dist/
```

### Java
```
*.class
*.jar
target/
.gradle/
build/
```

### General
```
.DS_Store
Thumbs.db
*.swp
.vscode/
.idea/
```

---

## Quick Reference Card

| Task | Command |
|------|---------|
| New repo | `git init` |
| Clone | `git clone <url>` |
| Status | `git status` |
| Stage | `git add <file>` |
| Commit | `git commit -m "msg"` |
| Push | `git push origin main` |
| Pull | `git pull origin main` |
| New branch | `git checkout -b <name>` |
| Switch branch | `git checkout <name>` |
| Merge | `git merge <branch>` |
| Log | `git log --oneline` |
| Diff | `git diff` |
| Stash | `git stash` |
| Undo changes | `git checkout -- <file>` |
| Undo commit | `git reset --soft HEAD~1` |

---

## Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Interactive Git Cheat Sheet](https://ndpsoftware.com/git-cheatsheet.html)
- [Visual Git Cheat Sheet](http://www.ndpsoftware.com/git-cheatsheet.html)
