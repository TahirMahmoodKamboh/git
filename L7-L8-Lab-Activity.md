# Lab Activity: Git Basics, Branches, and Releases

**Lectures:** L7 and L8  
**Level:** Beginner  
**Suggested time:** 60–90 minutes

## Lab goals

By the end of this activity, you should be able to:

- Create a Git repository and save changes as commits
- Explain the working tree, staging area, and repository
- Create a branch, make a change, and merge it
- Resolve a simple merge conflict
- Rebase a local branch onto an updated main branch
- Add a tag to mark a version

## What you need

- Git installed on your computer
- A text editor, such as Visual Studio Code
- A terminal (VS Code's built-in terminal is fine)

> **Safety:** Use a new practice folder for this lab. Do not run these commands in an existing project or a folder containing important files. Create and edit the text files in your editor when instructed.

## Part 1 — Configure Git (skip if already configured)

Git uses your name and email to identify the author of commits. Replace the example values with your own:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Check the saved values:

```bash
git config --global --list
```

## Part 2 — Create a repository and make your first commit

1. Open a terminal in the location where you want to create the lab folder, then run:

   ```bash
   mkdir student-task-tracker
   cd student-task-tracker
   ```

   If you already created the folder, open a terminal in that folder instead.
2. Start a Git repository:

   ```bash
   git init
   ```

3. Set the branch name to `main`:

   ```bash
   git branch -M main
   ```

4. In your text editor, create a file named `README.md` with this content:

   ```text
   # Student Task Tracker

   A small project for practicing Git.
   ```

5. Check the status:

   ```bash
   git status
   ```

   **Checkpoint:** Git should show `README.md` as an untracked file. An untracked file is not yet included in Git history.

6. Stage the file and check the status again:

   ```bash
   git add README.md
   git status
   ```

   **Checkpoint:** The file should now be listed as a change ready to be committed.

7. Create your first commit:

   ```bash
   git commit -m "Add project README"
   ```

8. View the commit:

   ```bash
   git log --oneline
   ```

   **Checkpoint:** The history should show one commit with your message.

### Record your observations

- Before `git add`, what status did Git show for `README.md`?
- What changed after `git add`?
- Which command saved the snapshot in the repository history?

## Part 3 — Edit, compare, stage, and commit

1. Open `README.md` in your text editor and add this line to the bottom:

   ```text
   Current goal: learn branches.
   ```

2. See what changed:

   ```bash
   git status
   git diff
   ```

   `git diff` shows changes that have not been staged yet.

3. Stage the edit, then inspect the staged change:

   ```bash
   git add README.md
   git diff --staged
   ```

4. Commit the change:

   ```bash
   git commit -m "Add project goal"
   ```

5. Confirm the working tree is clean:

   ```bash
   git status
   ```

   **Checkpoint:** Git should report that there is nothing to commit and the working tree is clean.

## Part 4 — Create a feature branch and merge it

1. Create a branch named `feature/tasks` and check it out:

   ```bash
   git checkout -b feature/tasks
   ```

2. In your text editor, create a file named `tasks.txt` with these lines:

   ```text
   Review Git commands
   Practice making commits
   ```

3. Stage and commit the new file:

   ```bash
   git add tasks.txt
   git commit -m "Add starter task list"
   ```

4. Return to `main` and check the files:

   ```bash
   git checkout main
   ```

   In your editor, notice that `tasks.txt` is not on `main` yet.

5. Merge the feature branch into `main`:

   ```bash
   git merge feature/tasks
   ```

6. Check the status and history:

   ```bash
   git status
   git log --oneline
   ```

   **Checkpoint:** `tasks.txt` should now be present on `main`, and its commit should appear in the history.

### Reflect

Why was the task-list change made on a separate branch before being merged into `main`?

## Part 5 — Rebase a local branch

This section creates a simple situation where `main` advances while a feature branch is in progress.

1. Create a new branch from `main` and check it out:

   ```bash
   git checkout -b feature/reminders
   ```

2. Open `README.md` in your text editor and add this line:

   ```text
   Reminder: review the task list every day.
   ```

3. Stage and commit the change:

   ```bash
   git add README.md
   git commit -m "Add task reminder"
   ```

4. Check out the `main` branch:

   ```bash
   git checkout main
   ```

   Open `tasks.txt` in your text editor and add a separate line, for example:

   ```text
   Organize tasks by priority
   ```

5. Stage and commit the update on `main`:

   ```bash
   git add tasks.txt
   git commit -m "Add task priority step"
   ```

6. Check out the feature branch and rebase it onto the updated `main`:

   ```bash
   git checkout feature/reminders
   git rebase main
   ```

   Git replays the feature branch's commit on top of the latest `main` commit. These edits are in different files, so a conflict is not expected. If Git does report a conflict, use `git status` to find the conflicted file, edit it to the content you want, and remove any conflict markers. Then stage the resolved file and continue:

   ```bash
   git add <conflicted-file>
   git rebase --continue
   ```

7. Inspect the history:

   ```bash
   git log --oneline
   ```

   **Checkpoint:** The reminder change should still exist, and the feature commit should now be based on the newer `main` history.

> **Important:** Rebase can rewrite commit history. Practice it on your own local branch; avoid rebasing shared commits that other people may already use.

## Part 6 — Create and resolve a merge conflict

This exercise intentionally edits the same line on two branches. First, make sure you have completed Part 5 and that no rebase is still in progress.

1. Check out `main`:

   ```bash
   git checkout main
   ```

   In your text editor, create `greeting.txt` with this single line:

   ```text
   Welcome to the task tracker.
   ```

2. Stage and commit it:

   ```bash
   git add greeting.txt
   git commit -m "Add greeting"
   ```

3. Create and check out a branch named `feature/greeting`:

   ```bash
   git checkout -b feature/greeting
   ```

4. Open `greeting.txt` in your text editor and change the line to:

   ```text
   Welcome to our improved task tracker.
   ```

   Stage and commit the change:

   ```bash
   git add greeting.txt
   git commit -m "Improve feature greeting"
   ```

5. Check out `main`:

   ```bash
   git checkout main
   ```

   Open `greeting.txt` in your text editor and change the same line to:

   ```text
   Welcome to the student task tracker.
   ```

   Stage and commit this different change:

   ```bash
   git add greeting.txt
   git commit -m "Personalize main greeting"
   ```

6. Merge the feature branch into `main`:

   ```bash
   git merge feature/greeting
   ```

   Git should report a conflict because both branches changed the same line.

7. Open `greeting.txt`. It will contain markers similar to these:

   ```text
   <<<<<<< HEAD
   Welcome to the student task tracker.
   =======
   Welcome to our improved task tracker.
   >>>>>>> feature/greeting
   ```

8. Choose a final greeting. You can keep either version or write a new one. Delete all three conflict-marker lines, save the file, then stage and commit the resolution:

   ```bash
   git add greeting.txt
   git commit -m "Resolve greeting conflict"
   ```

9. Check that the conflict is resolved:

   ```bash
   git status
   ```

   **Checkpoint:** The working tree should be clean and no conflict markers should remain in `greeting.txt`.

### Reflect

- Why could Git not decide which greeting to keep?
- What did you choose as the final greeting?
- Why must the conflict markers be removed before committing?

## Part 7 — Mark a version with a tag

After checking that the project files are in a good state, create a tag for this practice version:

```bash
git tag v1.0
git tag
```

**Checkpoint:** The tag list should include `v1.0`. The tag labels the current commit as a version milestone.

## Part 8 — Final review

Run these commands:

```bash
git status
git branch
git log --oneline
git tag
```

Complete the checklist:

- [ ] I created a repository with `git init`.
- [ ] I checked status and inspected file changes.
- [ ] I staged files and made commits with clear messages.
- [ ] I created a feature branch and merged it into `main`.
- [ ] I rebased my local feature branch onto an updated `main`.
- [ ] I resolved a merge conflict and removed its markers.
- [ ] I created and listed a version tag.

## Submission

Show your instructor:

1. The `git log --oneline` output
2. The final contents of `greeting.txt`
3. The output of `git branch` and `git tag`
4. A clean `git status`

## Key command reminder

| Goal | Command |
|---|---|
| Start a repository | `git init` |
| Check files and changes | `git status` |
| Stage a file | `git add filename` |
| Save a commit | `git commit -m "message"` |
| View changes not yet staged | `git diff` |
| Create and check out a branch | `git checkout -b branch-name` |
| Check out an existing branch | `git checkout branch-name` |
| Merge a branch into the current branch | `git merge branch-name` |
| Rebase current branch onto another branch | `git rebase branch-name` |
| List tags | `git tag` |
