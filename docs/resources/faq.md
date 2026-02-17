---
layout: default
title: FAQ
parent: Resources
nav_order: 1
---

# Frequently Asked Questions
{: .no_toc }

Common questions and answers about Git and GitHub.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## General Questions

### What's the difference between Git and GitHub?

**Git** is a version control system that tracks changes in your code. It runs locally on your computer.

**GitHub** is a cloud-based hosting service for Git repositories. It adds collaboration features, web interface, and remote storage.

Think of it this way:
- Git = the tool
- GitHub = the service that uses the tool

### Do I need to know Git to use GitHub?

Yes, basic Git knowledge is essential for effective GitHub use. However, GitHub provides a web interface for many common operations, making it more accessible to beginners.

### Is GitHub free?

Yes! GitHub offers:
- **Free accounts** with unlimited public and private repositories
- **GitHub Free** for individuals
- **GitHub Pro** for professional developers ($4/month)
- **GitHub Team** for organizations ($4/user/month)
- **GitHub Enterprise** for large organizations

### Can I use GitHub for private projects?

Absolutely! All GitHub accounts can create unlimited private repositories. Private repos are only visible to you and people you explicitly share them with.

## Repository Questions

### How do I delete a repository?

On GitHub:
1. Go to repository Settings
2. Scroll to bottom → "Danger Zone"
3. Click "Delete this repository"
4. Type repository name to confirm
5. Click "I understand the consequences, delete this repository"

**Warning:** This is permanent and cannot be undone!

### How do I rename a repository?

1. Go to repository Settings
2. Under "Repository name", enter new name
3. Click "Rename"

**Note:** GitHub automatically redirects from the old URL, but update your local remotes:

```bash
git remote set-url origin https://github.com/username/new-name.git
```

### What's the difference between forking and cloning?

- **Forking** creates a copy of a repository under your GitHub account. You can make changes and submit pull requests to the original.
- **Cloning** downloads a repository to your local machine. It doesn't create a new repository on GitHub.

```bash
# Fork on GitHub (using the Fork button), then clone your fork
git clone https://github.com/your-username/forked-repo.git
```

### How large can my repository be?

- Repository size: No hard limit, but 5GB is recommended
- Individual file size: 100 MB maximum (hard limit)
- Repository with over 1GB: You'll receive a warning
- Large files: Use Git LFS (Large File Storage) for files over 50MB

## Commit and Branch Questions

### How do I undo the last commit?

**Keep changes, undo commit:**
```bash
git reset --soft HEAD~1
```

**Discard changes and undo commit:**
```bash
git reset --hard HEAD~1
```

**Create a new commit that undoes changes:**
```bash
git revert HEAD
```

### How do I write a good commit message?

Follow these guidelines:

```bash
# Good commit messages
git commit -m "Add user authentication feature"
git commit -m "Fix navigation menu overflow on mobile"
git commit -m "Update dependencies to latest versions"

# Bad commit messages
git commit -m "Fixed stuff"
git commit -m "Update"
git commit -m "asdfgh"
```

**Best practices:**
- Use imperative mood: "Add feature" not "Added feature"
- First line under 50 characters
- Capitalize first letter
- No period at the end
- If needed, add details after blank line

### How do I delete a branch?

**Delete local branch:**
```bash
git branch -d branch-name  # Safe delete (only if merged)
git branch -D branch-name  # Force delete
```

**Delete remote branch:**
```bash
git push origin --delete branch-name
```

### Can I recover a deleted branch?

Yes, if you know the commit hash:

```bash
# Find the commit
git reflog

# Recreate the branch
git checkout -b recovered-branch commit-hash
```

## Collaboration Questions

### How do I contribute to an open source project?

1. **Fork** the repository
2. **Clone** your fork
3. **Create a branch** for your changes
4. **Make and commit** your changes
5. **Push** to your fork
6. **Open a pull request** to the original repository

See our [Contributing Guide](./contributing.html) for details.

### What's a pull request?

A pull request (PR) is a way to propose changes to a repository. It allows:
- Code review before merging
- Discussion about the changes
- Automated testing
- Tracking of what's being added

### How do I resolve merge conflicts?

1. **Identify conflicts:**
   ```bash
   git status
   ```

2. **Open conflicted files** and look for:
   ```
   <<<<<<< HEAD
   Your changes
   =======
   Their changes
   >>>>>>> branch-name
   ```

3. **Edit the file** to resolve conflicts

4. **Stage and commit:**
   ```bash
   git add conflicted-file.txt
   git commit -m "Resolve merge conflict"
   ```

### How do I keep my fork synchronized?

```bash
# Add upstream remote (one time)
git remote add upstream https://github.com/original-owner/repo.git

# Fetch upstream changes
git fetch upstream

# Merge into your main branch
git checkout main
git merge upstream/main

# Push to your fork
git push origin main
```

## GitHub Features Questions

### What are GitHub Actions?

GitHub Actions is a CI/CD platform that allows you to automate workflows. Common uses:
- Running tests automatically
- Building and deploying applications
- Publishing packages
- Automating routine tasks

### What's a GitHub Gist?

A Gist is a simple way to share code snippets, notes, or small files. Features:
- Can be public or secret
- Support for multiple files
- Version history
- Can be embedded in websites
- Supports markdown

Create at: [gist.github.com](https://gist.github.com)

### What are GitHub Pages?

GitHub Pages is a free static site hosting service. Perfect for:
- Project documentation
- Personal websites
- Portfolio sites
- Blog (with Jekyll)

Enable in repository Settings → Pages.

### What's the difference between Issues and Discussions?

- **Issues**: Track tasks, bugs, and feature requests. Meant to be closed when resolved.
- **Discussions**: Community conversations, Q&A, and announcements. Open-ended.

## Security Questions

### How do I remove sensitive data from my repository?

If you accidentally committed sensitive data:

1. **Remove from latest commit:**
   ```bash
   git rm --cached sensitive-file.txt
   git commit --amend
   git push --force
   ```

2. **Remove from history:**
   Use BFG Repo-Cleaner or `git filter-branch`

3. **Consider the data compromised** and rotate credentials

**Prevention:** Use `.gitignore` and never commit:
- Passwords or API keys
- Environment files (`.env`)
- Private keys
- Database credentials

### Should I use HTTPS or SSH?

Both are secure. Choose based on preference:

**HTTPS:**
- Easier to set up
- Works everywhere (even behind firewalls)
- Requires credential helper or PAT

**SSH:**
- No need to enter password each time
- More secure (key-based)
- Requires SSH key setup

## Troubleshooting Questions

### Why is my push rejected?

Common reasons:

1. **Remote has changes you don't have:**
   ```bash
   git pull origin main
   git push origin main
   ```

2. **Force push was used (and you're behind):**
   ```bash
   git fetch origin
   git reset --hard origin/main  # WARNING: Discards local changes
   ```

3. **Branch is protected:**
   Use a pull request instead of direct push

### Why can't I see my changes on GitHub?

Check:
1. Did you commit? (`git status`)
2. Did you push? (`git push origin branch-name`)
3. Are you looking at the right branch on GitHub?
4. Did the push succeed? (check terminal output)

### Git is asking for credentials every time

Set up credential helper:

```bash
# macOS
git config --global credential.helper osxkeychain

# Windows
git config --global credential.helper wincred

# Linux
git config --global credential.helper cache
```

Or set up SSH authentication.

---

## Still Have Questions?

- Check [GitHub Documentation](https://docs.github.com/)
- Visit [GitHub Community](https://github.community/)
- Review our [Troubleshooting Guide](./troubleshooting.html)
- Open an [issue](https://github.com/galaxiya2/github-training/issues) in this repository
