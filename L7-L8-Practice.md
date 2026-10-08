# Git Practice Worksheet: Lectures 7 and 8

These exercises help you practice the ideas and commands from L7 and L8. Try each activity before checking the answer key.

> **Safety tip:** Do the command-line activities in a new, empty practice folder. Do not use a folder that contains important work.

## Part A — Check Your Understanding

Answer in your own words.

1. What problem does version control help solve?
2. What is a Git repository?
3. What is the difference between the working tree and the staging area?
4. What does a commit represent?
5. Which command shows the current status of your files?
6. What does `git add` do? Does it create a commit?
7. Why would a developer create a branch?
8. What is a merge conflict, and why might one happen?
9. What is one difference between merge and rebase?
10. What is a Git tag commonly used to mark?
11. Which workflow gives each feature its own branch?
12. Which workflow uses short-lived branches and merges changes frequently?

## Part B — Put the Commands in Order

Arrange these commands into the right order for saving a new file in Git:

```text
git commit -m "Add project notes"
git status
git init
git add notes.txt
```

Then answer: At which step does Git save a permanent snapshot in the repository history?

## Part C — Hands-On: Your First Repository (L7)

1. Create and open a new, empty folder named `git-practice`.
2. Initialize a Git repository.
3. Check the repository status.
4. Create a text file named `README.txt` and write `My Git practice project` inside it.
5. Check the status again. Notice that the file is untracked.
6. Stage only `README.txt`.
7. Check the status again. Notice that the file is staged.
8. Commit it with the message `Add practice README`.
9. View the commit history in short form.
10. Change the text in `README.txt`, then inspect the unstaged change.
11. Stage and commit the change with a meaningful message.

**Record your results**

- What did `git status` report before staging?
- What changed in the status after staging?
- Which command displayed the change you made to the file?
- How many commits do you see after completing the activity?

## Part D — Hands-On: Branch and Merge (L8)

Continue in your `git-practice` repository.

1. From `main`, rename the current branch to `main` if needed:

   ```bash
   git branch -M main
   ```

   (You should already have a commit from Part C.)
2. Create a branch named `feature/profile`.
3. Switch to `feature/profile`.
4. Create a file named `profile.txt` with a short profile description.
5. Stage and commit the new file.
6. Switch back to `main` and check the status.
7. Merge `feature/profile` into `main`.
8. Check the commit history and confirm that `profile.txt` is now part of the main branch.

**Think about it:** Why is the profile work kept separate until you merge it?

## Part E — Hands-On: Create and Resolve a Merge Conflict

This exercise deliberately creates a conflict. Make sure you are in your practice repository and have a clean working tree first.

1. On `main`, create `greeting.txt` containing this single line:

   ```text
   Hello from the main branch
   ```

2. Stage and commit the file.
3. Create and switch to a branch named `feature/greeting`.
4. Change the line in `greeting.txt` to `Hello from the feature branch`, then stage and commit it.
5. Switch back to `main`.
6. Change the same line to `Hello from the updated main branch`, then stage and commit it.
7. Try to merge `feature/greeting` into `main`. Git should report a conflict.
8. Open `greeting.txt`. Choose the final wording you want to keep, and remove all conflict marker lines (`<<<<<<<`, `=======`, and `>>>>>>>`).
9. Save the file, stage it, and commit the conflict resolution.
10. Run `git status` and check that there are no unresolved conflicts.

**Check your understanding**

- What do the conflict markers show?
- Why could Git not merge the two edits automatically?
- What must you do to the conflict markers before committing?

## Part F — Rebase, Tags, and Workflow Choices (L8)

### Rebase

In your practice repository, create a new branch named `practice/rebase` from `main`. Add and commit a small change on that branch. Then run:

```bash
git rebase main
```

Since the branch was created from the current `main` and no new commit was added to `main`, there may be nothing for Git to replay. This still lets you practice the command. In your own words, explain what rebase does when the base branch has advanced.

> Rebase can rewrite commit history. For this beginner exercise, only rebase your local practice branch; do not rebase shared commits that teammates may already have based work on.

### Tag

Create a version tag for a stable commit, then list the tags:

```bash
git tag v1.0
git tag
```

What milestone does the tag identify in your project?

### Choose a workflow

Choose the most suitable workflow for each situation and give one reason.

1. A small team wants the simplest process and works directly with one shared main branch.
2. Developers want to isolate and review each feature before it reaches the main branch.
3. A team wants a highly structured process with separate development, release, and hotfix branches.
4. A CI/CD team prefers short-lived branches and integrating changes frequently.

Options: **Central workflow**, **Feature branch workflow**, **Git Flow**, **Trunk-based development**.

## Part G — Quick Command Challenge

Write the Git command that would:

1. Start tracking the current folder as a repository.
2. Show modified, staged, and untracked files.
3. Stage one file named `app.txt`.
4. Save staged changes with the message `Fix navigation`.
5. Show a concise commit history.
6. Create a branch named `bugfix/header`.
7. Switch to that branch.
8. Merge `bugfix/header` into the currently checked-out branch.
9. Create a tag named `v1.1`.

## Answer Key

### Part A

Answers will vary. Key points:

1. It records changes and helps compare or restore versions.
2. A project folder whose files and history Git tracks.
3. The working tree is where files are edited; the staging area holds selected changes for the next commit.
4. A saved snapshot or milestone in project history.
5. `git status`
6. It stages selected changes; it does not create a commit.
7. To work on a change separately without disrupting the main line of development.
8. It occurs when Git cannot automatically combine competing changes, often edits to the same lines.
9. Merge combines histories and may create a merge commit; rebase replays commits on a new base and can make history linear.
10. To label an important commit, often a release version.
11. Feature branch workflow.
12. Trunk-based development.

### Part B

```text
git init
git status
git add notes.txt
git commit -m "Add project notes"
```

The commit command saves the snapshot in the repository history.

### Part G

1. `git init`
2. `git status`
3. `git add app.txt`
4. `git commit -m "Fix navigation"`
5. `git log --oneline`
6. `git branch bugfix/header`
7. `git switch bugfix/header`
8. `git merge bugfix/header`
9. `git tag v1.1`

For the workflow choices in Part F, a good match is: 1) Central workflow, 2) Feature branch workflow, 3) Git Flow, and 4) Trunk-based development.

---

Based on the L7 and L8 topics in `Contents.md` and the matching lecture notes.
