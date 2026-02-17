---
layout: default
title: GitHub Basics
parent: GitHub Features
nav_order: 1
---

# GitHub Basics
{: .no_toc }

Understanding GitHub's core features and workflows.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## What is GitHub?

GitHub is a web-based platform built on top of Git that provides hosting for software development and version control. It adds collaboration features, project management tools, and a social coding environment.

## Key Features

### Repositories

Repositories on GitHub are remote storage locations for your Git projects.

- **Public Repositories** - Open to everyone
- **Private Repositories** - Restricted access
- **README** - Project introduction and documentation
- **License** - Define usage rights

### Issues

Issues are GitHub's way of tracking tasks, enhancements, and bugs.

```markdown
# Creating an Issue
1. Navigate to the repository
2. Click "Issues" tab
3. Click "New Issue"
4. Add title and description
5. Assign labels, assignees, and milestones
```

**Best Practices:**
- Use descriptive titles
- Provide detailed descriptions
- Add relevant labels
- Reference related issues with #number

### Pull Requests

Pull requests let you tell others about changes you've pushed to a branch in a repository.

#### Creating a Pull Request

1. **Fork or create a branch**
   ```bash
   git checkout -b feature-branch
   ```

2. **Make and commit changes**
   ```bash
   git add .
   git commit -m "Add new feature"
   ```

3. **Push to GitHub**
   ```bash
   git push origin feature-branch
   ```

4. **Open Pull Request on GitHub**
   - Navigate to repository
   - Click "Pull requests" → "New pull request"
   - Select branches to compare
   - Add description and reviewers
   - Click "Create pull request"

#### Pull Request Review Process

1. **Code Review** - Team members review changes
2. **Discussion** - Comment on specific lines
3. **Request Changes** - Ask for modifications
4. **Approval** - Approve the changes
5. **Merge** - Integrate changes into main branch

### Collaboration Features

#### Forking

Create a personal copy of someone else's repository.

```bash
# After forking on GitHub, clone your fork
git clone https://github.com/your-username/forked-repo.git

# Add upstream remote
git remote add upstream https://github.com/original-owner/repo.git
```

#### Stars and Watching

- **Star** - Bookmark repositories you like
- **Watch** - Get notifications about repository activity

#### Organizations

Create organizations for team collaboration:
- Shared repositories
- Team permissions
- Unified billing

## GitHub Workflow

### 1. Clone Repository

```bash
git clone https://github.com/username/repository.git
cd repository
```

### 2. Create Branch

```bash
git checkout -b feature-name
```

### 3. Make Changes

Edit files, add features, fix bugs...

### 4. Commit Changes

```bash
git add .
git commit -m "Descriptive message"
```

### 5. Push to GitHub

```bash
git push origin feature-name
```

### 6. Create Pull Request

Open PR on GitHub for review and merging.

## Remote Operations

### Managing Remotes

```bash
# View remotes
git remote -v

# Add remote
git remote add origin https://github.com/username/repo.git

# Remove remote
git remote remove origin

# Rename remote
git remote rename old-name new-name
```

### Syncing with Remote

```bash
# Fetch changes
git fetch origin

# Pull changes (fetch + merge)
git pull origin main

# Push changes
git push origin branch-name
```

## GitHub CLI

GitHub's official command-line interface.

```bash
# Install gh CLI (varies by OS)
# Then authenticate
gh auth login

# Create repository
gh repo create

# Create pull request
gh pr create

# View pull requests
gh pr list

# Clone repository
gh repo clone username/repository
```

## Best Practices

1. **Meaningful Commits** - Write clear commit messages
2. **Small Pull Requests** - Easier to review
3. **Update README** - Keep documentation current
4. **Use Issues** - Track work systematically
5. **Add .gitignore** - Exclude unnecessary files
6. **Protect Main Branch** - Require reviews before merging
7. **Use Templates** - Standardize PRs and issues

## Repository Settings

### Branch Protection

Protect important branches from force pushes and deletion:
- Require pull request reviews
- Require status checks
- Enforce restrictions

### Collaborators

Add team members with different permission levels:
- **Read** - View and clone
- **Triage** - Manage issues and PRs
- **Write** - Push to repository
- **Maintain** - Manage without sensitive actions
- **Admin** - Full access

## Next Steps

- Learn about [GitHub Actions](./github-actions.html)
- Explore [Code Review Best Practices](../collaboration/code-review.html)
- Try [Your First Pull Request Tutorial](../tutorials/first-pull-request.html)

---

## Additional Resources

- [GitHub Guides](https://guides.github.com/)
- [GitHub Documentation](https://docs.github.com/)
- [GitHub Learning Lab](https://lab.github.com/)
