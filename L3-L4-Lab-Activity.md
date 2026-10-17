# Lab Activity: GitHub/GitLab Collaboration and Continuous Integration

## Course: Git and Version Control
## Topics Covered: Lecture 3 and Lecture 4

## Title
Collaborative Git Workflow and Continuous Integration Practice

## Introduction
This lab activity is designed to help students understand how software teams use Git platforms such as GitHub and GitLab to collaborate, review code, and automate testing. The exercise also introduces Continuous Integration (CI), a major concept in modern software development and DevOps.

This activity is written in a simple and beginner-friendly format while keeping a formal academic structure suitable for university assignments.

## Learning Objectives
By the end of this lab, students will be able to:

- Create or clone a remote Git repository
- Understand the purpose of `git fetch`, `git pull`, and `git push`
- Work with branches for team-based development
- Create a pull request or merge request
- Participate in basic code review practices
- Explain the workflow of Continuous Integration
- Identify how CI improves software quality and team productivity

## Tools and Requirements
- Git installed on the computer
- GitHub or GitLab account
- Internet connection
- Code editor or IDE
- Optional: Python or another language for CI demonstration

## Scenario
A small software team is developing a project named `student-project`. The team needs to:

1. Share a central repository online
2. Work on separate branches
3. Merge code safely
4. Review each other’s work
5. Run automated tests using CI

## Task 1: Set Up the Remote Repository

### Step 1: Create a repository on GitHub or GitLab
If you do not already have a repository, create a new one on GitHub or GitLab.

### Step 2: Initialize or clone the project
If you are starting from scratch:

```bash
git init
```

If you are joining an existing project:

```bash
git clone https://github.com/your-username/student-project.git
cd student-project
```

### Step 3: Connect the local project to the remote repository

```bash
git remote add origin https://github.com/your-username/student-project.git
```

### Deliverable
- A working Git repository connected to a remote repository

## Task 2: Create and Use a Branch

Create a new branch for a feature or task.

```bash
git checkout -b feature/login-page
```

Or:

```bash
git switch -c feature/login-page
```

Create or edit a file, such as `README.md` or `index.html`, and then save the changes.

```bash
git add .
git commit -m "Add login page feature"
```

Push the branch to the remote repository:

```bash
git push origin feature/login-page
```

### Questions
1. Why do teams use branches instead of working only on the main branch?
2. What is the benefit of creating a separate feature branch?

## Task 3: Pull Request / Merge Request

Open a pull request (GitHub) or merge request (GitLab) for your branch.

### Instructions
- Open the repository in GitHub or GitLab
- Compare your branch with the main branch
- Add a title and short description
- Request a teammate to review the changes

### Deliverable
- A pull request or merge request link

## Task 4: Remote Repository Commands Practice

Run the following commands and record the output:

```bash
git status
git remote -v
git fetch origin
git pull origin main
git log
```

### Short answer questions
1. What is the difference between `git fetch` and `git pull`?
2. Why should a developer pull the latest changes before starting work?
3. Why is `git push` important in team-based development?

## Task 5: Code Review Activity

Each student or team member must review at least one teammate’s pull request or merge request.

### Review checklist
- [ ] The code is correct and works as expected
- [ ] The code is easy to understand
- [ ] There are no obvious mistakes or bugs
- [ ] The naming of variables/files is clear
- [ ] The change is safe to merge

### Write a short review comment
Example:

> The change is clear and easy to follow. However, I suggest adding a short description to explain the purpose of the file. Please update the documentation before merging.

### Deliverable
- A short code review summary

## Task 6: Understand Continuous Integration (CI)

Continuous Integration is the practice of automatically testing and validating code whenever developers make changes.

A basic CI workflow is:

Source code → Build → Test → Quality Gate → Feedback

### Explain the meaning of each stage
1. Source code: the project files are gathered from the repository
2. Build: the application is prepared or compiled
3. Test: automated tests run to check correctness
4. Quality Gate: rules are applied to ensure quality and standards
5. Feedback: developers receive results quickly

## Task 7: Simple CI Example

Create a simple Python project for testing.

### Step 1: Create a file named `hello.py`

```python
print("Hello CI")
```

### Step 2: Create a test file

```python
def test_hello():
    assert "Hello" in "Hello CI"
```

### Step 3: Run the test locally

```bash
pytest
```

### Explanation
If the test passes, the code is considered valid. In CI, this test would run automatically whenever code is pushed to the repository.

## Task 8: Basic GitHub Actions Example

Add a workflow file named `.github/workflows/ci.yml`.

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Install dependencies
        run: python -m pip install pytest

      - name: Run tests
        run: pytest
```

### Task
Push the workflow to the repository and observe whether the CI pipeline runs.

### Questions
1. Why is automation important in CI?
2. How does CI help detect problems early?
3. What happens if tests fail in CI?

## Deliverables for Submission
Each student or group must submit the following:

1. Repository URL or remote repository link
2. Screenshot or proof of branch creation and commit
3. Pull request or merge request link
4. Summary of the code review comments
5. Screenshot or output of CI results
6. Short reflection report (minimum 150 words)

## Reflection Questions
Answer the following questions briefly:

1. Why is version control important in a team project?
2. How does GitHub or GitLab support collaborative software development?
3. What is the importance of pull requests or merge requests?
4. Why is code review necessary before merging changes?
5. How does Continuous Integration improve software quality?

## Conclusion
This lab demonstrates the practical workflow used in software development teams. Students learn how remote repositories, branch-based development, collaborative review, and automated CI checks work together to maintain reliable and high-quality software projects.

---

This activity is based on the concepts from Lecture 3 and Lecture 4: GitHub/GitLab collaboration and Continuous Integration.
