---
layout: default
title: Creating Your First Repository
parent: Tutorials
nav_order: 1
---

# Creating Your First Repository
{: .no_toc }

Step-by-step guide to create and manage your first Git repository.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Prerequisites

Before starting this tutorial, ensure you have:
- Git installed on your computer ([Download Git](https://git-scm.com/downloads))
- A GitHub account ([Sign up](https://github.com/join))
- A text editor (VS Code, Sublime Text, etc.)

## Step 1: Create a Local Repository

### Initialize Git

Open your terminal and create a new project directory:

```bash
# Create a new directory
mkdir my-first-repo
cd my-first-repo

# Initialize Git repository
git init
```

You should see: `Initialized empty Git repository in /path/to/my-first-repo/.git/`

### Create Files

Create a README file:

```bash
# Create README.md
echo "# My First Repository" > README.md
echo "This is my first Git repository!" >> README.md
```

Or create it manually with your text editor:

```markdown
# My First Repository

This is my first Git repository!

## About

Learning Git and GitHub fundamentals.
```

### Make Your First Commit

```bash
# Check status
git status

# Stage the README file
git add README.md

# Commit the changes
git commit -m "Initial commit: Add README"
```

## Step 2: Create a GitHub Repository

### On GitHub

1. Go to [GitHub](https://github.com)
2. Click the **+** icon in the top-right corner
3. Select **New repository**
4. Fill in the details:
   - **Repository name**: `my-first-repo`
   - **Description**: "My first GitHub repository"
   - **Visibility**: Public (or Private)
   - **Do NOT** initialize with README (we already have one)
5. Click **Create repository**

## Step 3: Connect Local and Remote

After creating the repository, GitHub shows setup instructions. Use the "push an existing repository" section:

```bash
# Add GitHub repository as remote
git remote add origin https://github.com/YOUR-USERNAME/my-first-repo.git

# Rename branch to main (if needed)
git branch -M main

# Push your code to GitHub
git push -u origin main
```

Replace `YOUR-USERNAME` with your actual GitHub username.

### Verify the Connection

```bash
# Check remote repository
git remote -v
```

You should see:
```
origin  https://github.com/YOUR-USERNAME/my-first-repo.git (fetch)
origin  https://github.com/YOUR-USERNAME/my-first-repo.git (push)
```

## Step 4: Make Additional Changes

### Add More Content

Create a new file:

```bash
# Create a source code file
echo 'console.log("Hello, GitHub!");' > hello.js
```

Or create `hello.js` with your editor:

```javascript
// My first JavaScript file
console.log("Hello, GitHub!");
console.log("Learning version control!");
```

### Commit and Push

```bash
# Check what changed
git status

# Stage the new file
git add hello.js

# Commit
git commit -m "Add hello.js with greeting message"

# Push to GitHub
git push origin main
```

## Step 5: View on GitHub

1. Go to your repository on GitHub: `https://github.com/YOUR-USERNAME/my-first-repo`
2. You should see:
   - README.md displayed on the main page
   - hello.js in the file list
   - Your commit history

## Step 6: Create a .gitignore File

Let's add a `.gitignore` file to exclude unwanted files:

```bash
# Create .gitignore
cat > .gitignore << EOF
# OS files
.DS_Store
Thumbs.db

# Editor files
.vscode/
.idea/
*.swp

# Dependencies
node_modules/
EOF
```

Commit and push:

```bash
git add .gitignore
git commit -m "Add .gitignore file"
git push origin main
```

## Common Workflows

### Check Repository Status

```bash
git status
```

### View Commit History

```bash
# Detailed view
git log

# Compact view
git log --oneline

# With graph
git log --graph --oneline --all
```

### See What Changed

```bash
# Show unstaged changes
git diff

# Show staged changes
git diff --staged

# Show changes in specific file
git diff README.md
```

### Undo Changes

```bash
# Discard changes in working directory
git checkout -- filename

# Unstage a file
git reset HEAD filename

# Amend last commit
git commit --amend -m "New commit message"
```

## Best Practices

1. **Write Good Commit Messages**
   - Use present tense: "Add feature" not "Added feature"
   - Be descriptive but concise
   - First line should be under 50 characters

2. **Commit Frequently**
   - Make small, logical commits
   - Each commit should represent one change

3. **Keep README Updated**
   - Document what your project does
   - Include setup instructions
   - Add usage examples

4. **Use .gitignore**
   - Exclude generated files
   - Don't commit sensitive data
   - Ignore OS-specific files

## Troubleshooting

### Authentication Issues

If you encounter authentication errors, you may need to use a Personal Access Token (PAT):

1. Go to GitHub Settings → Developer settings → Personal access tokens
2. Generate a new token with `repo` scope
3. Use the token as your password when pushing

Or set up SSH authentication (recommended).

### Push Rejected

If push is rejected:

```bash
# Pull latest changes first
git pull origin main

# Then push again
git push origin main
```

## Next Steps

Congratulations! You've created your first repository. Next, try:

- [Working with Branches](./working-with-branches.html)
- [Creating Your First Pull Request](./first-pull-request.html)
- [Collaborating with Others](../collaboration/team-workflow.html)

---

## Summary

You've learned to:
- ✅ Initialize a local Git repository
- ✅ Create a GitHub repository
- ✅ Connect local and remote repositories
- ✅ Make commits and push changes
- ✅ Use `.gitignore` effectively

Keep practicing these fundamentals—they're the foundation of all Git workflows!
