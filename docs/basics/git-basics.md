---
layout: default
title: Git Basics
parent: Basic Concepts
nav_order: 1
---

# Git Basics
{: .no_toc }

Learn the fundamental concepts of Git version control.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What is Git?

Git is a distributed version control system that tracks changes in your code over time. It allows multiple developers to work on the same project simultaneously without overwriting each other's work.

### Key Benefits

- **Version History** - Track every change made to your code
- **Collaboration** - Work with teams efficiently
- **Branching** - Experiment safely without affecting the main codebase
- **Backup** - Distributed nature provides built-in backups

## Core Concepts

### Repository

A repository (or "repo") is a directory that contains your project files and the entire revision history.

```bash
# Initialize a new repository
git init

# Clone an existing repository
git clone https://github.com/username/repository.git
```

### Commits

A commit is a snapshot of your repository at a specific point in time.

```bash
# Stage files for commit
git add filename.txt
git add .  # Stage all changes

# Create a commit
git commit -m "Add new feature"
```

### Branches

Branches allow you to work on different versions of your code simultaneously.

```bash
# Create a new branch
git branch feature-branch

# Switch to a branch
git checkout feature-branch

# Create and switch in one command
git checkout -b feature-branch

# List all branches
git branch -a
```

### Working Directory, Staging Area, and Repository

Understanding the three states of Git:

1. **Working Directory** - Where you modify files
2. **Staging Area (Index)** - Where you prepare commits
3. **Repository** - Where commits are stored

```
Working Directory → (git add) → Staging Area → (git commit) → Repository
```

## Basic Workflow

### 1. Check Status

```bash
git status
```

Shows which files have been modified, staged, or are untracked.

### 2. Stage Changes

```bash
# Stage specific file
git add README.md

# Stage all changes
git add .

# Stage specific pattern
git add *.js
```

### 3. Commit Changes

```bash
git commit -m "Descriptive commit message"
```

### 4. View History

```bash
# View commit history
git log

# Compact view
git log --oneline

# With graph
git log --graph --oneline --all
```

## Common Commands Reference

| Command | Description |
|---------|-------------|
| `git init` | Initialize a new repository |
| `git clone <url>` | Clone a repository |
| `git status` | Check working tree status |
| `git add <file>` | Stage changes |
| `git commit -m "message"` | Commit staged changes |
| `git log` | View commit history |
| `git diff` | Show changes between commits |
| `git branch` | List, create, or delete branches |
| `git checkout <branch>` | Switch branches |
| `git merge <branch>` | Merge branches |

## Best Practices

1. **Commit Often** - Make small, logical commits
2. **Write Clear Messages** - Describe what and why, not how
3. **Use Branches** - Keep main branch stable
4. **Pull Before Push** - Stay synchronized with remote
5. **Review Before Commit** - Use `git diff` to review changes

## Next Steps

- Learn about [GitHub Basics](../github/github-basics.html)
- Practice with [Your First Repository Tutorial](../tutorials/first-repository.html)
- Explore [Branching Strategies](../advanced/branching-strategies.html)

---

## Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Git Cheat Sheet](../resources/cheat-sheet.html)
- [Interactive Git Tutorial](https://try.github.io/)
