# 🚀 Git and GitHub Learning Guide

Welcome to the **Git and GitHub Learning Repository**!

This repository is created for beginners and learners who want to understand Git and GitHub from basic concepts to important commands used in real projects and interviews.

---

## 📚 Topics Covered

This repository covers:

* Git and GitHub Basics
* Version Control Systems
* Centralized vs Distributed Version Control
* Git vs GitHub
* Creating a GitHub Repository
* Clone and Fork
* Git Lifecycle
* Working Directory, Staging Area, Local Repository, and Remote Repository
* Git Branching
* Feature and Release Branches
* Git Reset
* Git Commit Amend
* Git Cherry-Pick
* Git Rebase Interactive
* Git Bisect
* Important Git Commands
* Interview Questions and Answers

---

# 1️⃣ What is Version Control?

A **Version Control System (VCS)** helps developers:

* Track changes in code
* Manage different versions of a project
* Collaborate with other developers
* Restore previous versions when required

### Examples

* Git
* Subversion (SVN)

---

# 2️⃣ Centralized vs Distributed Version Control

## Centralized Version Control

In a centralized version control system, there is one central repository where developers store and manage their code.

Example:

```text
Developer 1 ──┐
Developer 2 ──┼──> Central Repository
Developer 3 ──┘
```

Example: **SVN**

## Distributed Version Control

In a distributed version control system, every developer has a complete copy of the repository and its history.

Example:

```text
Developer 1 → Local Repository
Developer 2 → Local Repository
Developer 3 → Local Repository

        ↓ Push / Pull

    Remote Repository
        (GitHub)
```

Example: **Git**

---

# 3️⃣ Difference Between Git and GitHub

| Git                             | GitHub                                  |
| ------------------------------- | --------------------------------------- |
| Git is a version control system | GitHub is a cloud-based platform        |
| Tracks code changes             | Hosts Git repositories                  |
| Works locally                   | Supports remote collaboration           |
| Used for version control        | Supports pull requests and code reviews |

---

# 4️⃣ Create a GitHub Repository

### Step 1: Create a GitHub Account

Create an account and log in to GitHub.

### Step 2: Create a Repository

1. Click **New Repository**
2. Enter the repository name
3. Choose **Public** or **Private**
4. Click **Create Repository**

Example repository name:

```text
git-github-learning
```

---

# 5️⃣ Clone a Repository

Copy the HTTPS repository URL and run:

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/username/git-github-learning.git
```

This downloads the repository from GitHub to your local system.

Check the downloaded project:

```bash
ls -lrt
```

---

# 6️⃣ Git Lifecycle

The Git lifecycle contains four main stages:

```text
Working Directory
       ↓
   git add
       ↓
Staging Area
       ↓
  git commit
       ↓
Local Repository
       ↓
   git push
       ↓
Remote Repository (GitHub)
```

### Commands

```bash
git status
git add .
git commit -m "message"
git push
```

---

# 7️⃣ Check File Status

Use:

```bash
git status
```

This shows:

* Untracked files
* Modified files
* Staged files

Example:

```text
modified: README.md
```

---

# 8️⃣ Add Files to Staging Area

Add all files:

```bash
git add .
```

Add a specific file:

```bash
git add README.md
```

---

# 9️⃣ Commit Changes

Commit the staged changes:

```bash
git commit -m "feat: updated README file"
```

Check commit history:

```bash
git log
```

Short commit history:

```bash
git log --oneline
```

Example:

```text
a12bc34 feat: updated README file
b45de67 Initial commit
```

---

# 🔟 Push Changes to GitHub

Push changes:

```bash
git push origin main
```

Where:

```text
origin → Remote repository
main   → Branch name
```

For the first push:

```bash
git push -u origin main
```

---

# 1️⃣1️⃣ Important Git Commands

| Command                   | Description                        |
| ------------------------- | ---------------------------------- |
| `git init`                | Initialize a Git repository        |
| `git status`              | Check repository status            |
| `git add .`               | Add all changes to staging         |
| `git add <file>`          | Add a specific file                |
| `git commit -m "message"` | Create a commit                    |
| `git log`                 | Show commit history                |
| `git log --oneline`       | Show short commit history          |
| `git diff`                | Show file changes                  |
| `git clone <url>`         | Clone a repository                 |
| `git push`                | Push changes to remote             |
| `git fetch`               | Download latest remote information |
| `git branch -a`           | Show local and remote branches     |

---

# 1️⃣2️⃣ Git Branching

A branch allows developers to work independently without directly affecting the main branch.

Common branches:

```text
main/master
     │
     ├── feature branch
     │
     └── release branch
```

### Create and switch to a new branch

```bash
git checkout -b feature-branch
```

### View all branches

```bash
git branch -a
```

### Switch to a branch

```bash
git checkout branch-name
```

### Fetch latest branch information

```bash
git fetch
```

---

# 1️⃣3️⃣ Git Reset

Git reset is used to move the `HEAD` to a previous commit.

There are three main types:

## 1. Soft Reset

```bash
git reset --soft <commit-id>
```

* Commit is removed from local commit history
* Changes remain in the staging area
* Files are ready to commit again

## 2. Mixed Reset

```bash
git reset --mixed <commit-id>
```

* Commit is removed
* Changes remain in the working directory
* Changes are unstaged

## 3. Hard Reset

```bash
git reset --hard <commit-id>
```

* Commit is removed
* Staged changes are removed
* Working directory changes are removed

⚠️ **Warning:** `git reset --hard` can permanently delete uncommitted changes.

---

# 1️⃣4️⃣ Git Commit Amend

Use:

```bash
git commit --amend
```

This can be used to modify the latest commit.

For example, to change the latest commit message:

```bash
git commit --amend -m "new commit message"
```

---

# 1️⃣5️⃣ Git Cherry-Pick

`git cherry-pick` is used to copy a specific commit from one branch and apply it to another branch.

Example:

```bash
git cherry-pick <commit-id>
```

Example scenario:

```text
branch1:
file1.txt
file2.txt
file4.txt

branch2:
file3.txt
file5.txt
```

If you want the changes from the commit containing `file3.txt` to be applied to `branch1`:

```bash
git cherry-pick 2884557
```

---

# 1️⃣6️⃣ Git Interactive Rebase

Use:

```bash
git rebase -i <commit-id>
```

Interactive rebase can be used to:

* Squash commits
* Reword commit messages
* Reorder commits
* Drop commits
* Execute commands between commits

## Squash Commits

Squashing combines multiple commits into one commit.

```bash
git rebase -i <commit-id>
```

Change:

```text
pick commit1
pick commit2
```

To:

```text
pick commit1
squash commit2
```

---

# 1️⃣7️⃣ Drop a Commit

Using interactive rebase:

```bash
git rebase -i <commit-id>
```

Change:

```text
pick <commit-id>
```

To:

```text
drop <commit-id>
```

This removes the selected commit from the rebased history.

---

# 1️⃣8️⃣ Reword a Commit

Run:

```bash
git rebase -i <commit-id>
```

Change:

```text
pick
```

To:

```text
reword
```

Save the file and update the commit message when Git opens the editor.

---

# 1️⃣9️⃣ Git Bisect

`git bisect` helps identify the commit that introduced a bug.

Start:

```bash
git bisect start
```

Mark the current commit as bad:

```bash
git bisect bad
```

Mark a known working commit as good:

```bash
git bisect good <commit-id>
```

Git then performs a binary search through the commit history to help identify the problematic commit.

After completing the process:

```bash
git bisect reset
```

---

# 2️⃣0️⃣ Clone vs Fork

| Clone                                       | Fork                                                      |
| ------------------------------------------- | --------------------------------------------------------- |
| Downloads a repository to your local system | Creates a copy of a repository in your GitHub account     |
| Used to work locally                        | Often used to contribute without direct repository access |
| Repository remains on your computer         | Creates a separate remote repository                      |

### Example

If you have access to a team repository:

```text
Clone the repository → Work locally → Push changes
```

For an open-source repository where you don't have direct write access:

```text
Fork → Clone your fork → Make changes → Push → Create Pull Request
```

---

# 2️⃣1️⃣ Create a Repository from the Command Line

```bash
mkdir project
cd project
git init
git add .
git commit -m "Initial commit"
git remote add origin <repository-url>
git push -u origin main
```

---

# 🎯 Common Interview Questions

### Q1: What is Git?

Git is a distributed version control system used to track and manage changes in source code.

### Q2: What is GitHub?

GitHub is a cloud-based platform used to host Git repositories and support collaboration.

### Q3: What is the Git lifecycle?

```text
Working Directory → Staging Area → Local Repository → Remote Repository
```

### Q4: What is the difference between Clone and Fork?

Clone copies a repository to your local machine, while Fork creates a copy of another repository under your GitHub account.

### Q5: What is Cherry-Pick?

Cherry-pick copies a specific commit from one branch and applies it to another branch.

### Q6: What is Git Bisect?

Git Bisect is used to identify the commit that introduced a bug.

### Q7: What is the difference between Git and GitHub?

Git is a version control system, while GitHub is a platform for hosting Git repositories and collaboration.

---

# 🛠 Practice Commands

Try these commands in your own test repository:

```bash
git init
git status
git add .
git commit -m "Initial commit"
git branch
git checkout -b feature-branch
git add .
git commit -m "Added new feature"
git log --oneline
git checkout main
git merge feature-branch
git push
```

---

# 📌 Learning Tips

1. Don't just memorize commands.
2. Create a test repository and practice every command.
3. Understand the Git lifecycle before learning advanced commands.
4. Learn branching and merging properly.
5. Be careful with commands like:

```bash
git reset --hard
git push --force
```

These commands can rewrite history or remove changes.

---

# 🤝 Contributions

If you are learning Git and GitHub and want to improve these notes:

1. Fork this repository
2. Create a new branch
3. Make your changes
4. Commit your changes
5. Push your branch
6. Create a Pull Request

---

# ⭐ Support

If this repository helps you learn Git and GitHub, consider giving it a **Star ⭐**.

Happy Learning! 🚀
