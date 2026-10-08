# Lecture 8: Git & Version Control (Advanced Basics)

## 1) Branching and Merging

A branch is a separate line of development inside the same repository.

Why use branches?

- Work on new features without disturbing the main project
- Let multiple developers work independently
- Test changes before merging them into the main code

### Example

```bash
git branch feature-login
git switch feature-login
```

This creates a new branch and moves you to it.

### Merge
When the feature is finished, you merge it into the main branch.

```bash
git switch main
git merge feature-login
```

A merge combines the work from one branch into another.

## 2) Merge Conflicts

A merge conflict happens when Git cannot automatically decide how to combine changes from two branches.

Example:

- Branch A changed a line in a file
- Branch B also changed the same line
- Git needs help to decide the final result

### Conflict Example

```bash
<<<<<<< HEAD
print("Old code")
=======
print("New code")
>>>>>>> feature-login
```

This means:

- `<<<<<<< HEAD` = current branch version
- `=======` = incoming branch version
- `>>>>>>> feature-login` = branch being merged in

## 3) Conflict Resolution

To resolve a conflict:

1. Open the conflicted file
2. Read both versions
3. Decide the correct final content
4. Remove conflict markers
5. Save the file
6. Stage the resolved file
7. Commit the result

```bash
git add file_name
git commit -m "Resolve merge conflict"
```

## 4) Git Rebase

Rebase is another way to integrate changes from one branch into another.

Instead of merging, rebase moves your branch commits on top of another branch.

### Example

```bash
git switch feature-login
git rebase main
```

### Rebase vs Merge

- Merge keeps branch history and creates a merge commit
- Rebase creates a cleaner linear history

Rebase can be useful, but it may be confusing for beginners and can rewrite commit history.

## 5) Tags

A tag marks an important point in the project, like a release version.

Example:

```bash
git tag v1.0
git tag
```

Tags are useful for marking:

- Release versions
- Stable checkpoints
- Production milestones

## 6) Releases

A release is a version of software that is ready for users or customers.

### Common release steps

- Finish a stable version
- Test it
- Tag it with a version number
- Publish it
- Share changelog notes

Examples of release tags:

- `v1.0.0`
- `v2.1.0`
- `v3.0-beta`

## 7) Git Workflow Strategies

Different teams use different Git strategies depending on the size and needs of the project.

### 1. Central Workflow
A single main branch is used.

- Simple
- Good for small teams
- Less flexible

### 2. Feature Branch Workflow
Each feature is developed in its own branch.

- Safer for bigger projects
- Easier to review
- Good for teamwork

### 3. Git Flow
A more structured workflow with branches like:

- `main`
- `develop`
- `feature/*`
- `release/*`
- `hotfix/*`

This is useful for larger and more organized projects.

### 4. Trunk-Based Development
Developers work on short-lived branches and merge often.

- Fast
- Keeps branches small
- Good for modern CI/CD teams

## 8) Summary of Key Git Concepts

The main ideas in Lecture 8 are:

- Branching helps separate work
- Merging combines completed work
- Conflicts need manual resolution
- Rebase restructures commit history
- Tags mark releases or important checkpoints
- Releases are official project versions
- Workflow strategies guide collaboration

## 9) Common Commands Review

```bash
git branch
git switch main
git switch feature-login
git merge feature-login
git rebase main
git tag v1.0
git log --oneline
git status
```

## 10) Beginner-Friendly Example

```bash
git init
git branch feature-login
git switch feature-login

echo "New feature code" >> app.txt
git add app.txt
git commit -m "Add login page"

git switch main
git merge feature-login
```

This shows the basic process of creating a branch, making a change, and merging it back into the main branch.

## 11) Best Practices

- Use descriptive branch names such as `feature-login` or `bugfix-header`
- Commit often with clear messages
- Do not ignore merge conflicts
- Test code before merging
- Use tags for important releases
- Keep branch changes small and focused

## 12) Practice Questions

1. What is a branch?
2. Why do merge conflicts happen?
3. What is the purpose of a tag?
4. What is the difference between merging and rebasing?
5. Why are workflow strategies important in team projects?

---

This note is based on the course topic: Git & Version Control (L8).
