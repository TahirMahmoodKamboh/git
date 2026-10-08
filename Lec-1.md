# Lecture 7: Git & Version Control

## 1) What is Version Control?

Version control is a system that keeps track of changes made to files over time. It helps you:

- Go back to an earlier version of your project
- Compare changes made by different people
- Work safely without overwriting someone else's work
- Keep a history of your project development

Think of it like a camera that saves snapshots of your project at different points in time.

## 2) Why Git?

Git is a distributed version control system. It is widely used in software development because it is:

- Fast
- Flexible
- Good for team work
- Free and open-source
- Supported by platforms like GitHub and GitLab

## 3) Git Architecture

Git is built around a few important parts:

### Repository
A repository (repo) is a project folder that Git tracks. It contains all project files and Git history.

### Working Tree
The working tree is your current project folder on your computer. This is where you edit files.

### Staging Area
The staging area is like a waiting room for changes before they are saved in Git.

- You edit files
- You add them to the staging area using `git add`
- Then you save them permanently with `git commit`

### Commit
A commit is a saved version of your project. Each commit has:

- A message describing the change
- A unique ID (hash)
- A timestamp

This creates a timeline of project progress.

## 4) Basic Git Workflow

A common beginner workflow is:

1. Create or open a project
2. Edit files
3. Check status
4. Stage files
5. Commit changes
6. Repeat

## 5) Git Configuration

Before using Git properly, you should configure your identity:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

These details are added to each commit so others know who made the change.

## 6) Basic Git Commands

### `git init`
Creates a new Git repository in the current folder.

```bash
git init
```

### `git status`
Shows which files are modified, staged, or untracked.

```bash
git status
```

### `git add`
Adds files to the staging area.

```bash
git add filename.txt
git add .
```

- `git add filename.txt` adds a specific file
- `git add .` adds all changed files in the current folder

### `git commit`
Saves the staged changes as a new commit.

```bash
git commit -m "Add homepage design"
```

The commit message should be short and meaningful.

### `git log`
Shows the history of commits.

```bash
git log
```

### `git diff`
Shows the difference between versions.

```bash
git diff
```

### `git checkout` / `git switch`
Used to move between different states or branches of the project.

```bash
git switch main
```

## 7) Important Terms

### Repository
The project folder being tracked by Git.

### Working Directory
Where you work on files.

### Staging Area
Where files wait before being committed.

### Commit
A saved milestone in the project history.

### Branch
A separate line of development (discussed more in L8).

## 8) Simple Example

```bash
mkdir myproject
cd myproject
git init

echo "Hello world" > intro.txt
git status
git add intro.txt
git commit -m "Initial commit"
```

This creates a Git repository, tracks a file, stages it, and saves it as a commit.

## 9) Beginner Tips

- Commit often, but only after meaningful work
- Write clear commit messages
- Check `git status` before committing
- Do not stage everything unless you are sure
- Keep backups and use branches for risky changes

## 10) Summary

In Lecture 7, we learned the basic idea of version control and how Git tracks project changes. The important concepts are:

- Repository
- Working tree
- Staging area
- Commit
- Configuration
- Basic Git commands

These are the foundations of using Git in real-world development.

## 11) Practice Questions

1. What is version control?
2. Why is Git useful?
3. What is the difference between working tree and staging area?
4. What command is used to save changes permanently?
5. What is a commit?

---

This note is based on the course topic: Git & Version Control (L7).
