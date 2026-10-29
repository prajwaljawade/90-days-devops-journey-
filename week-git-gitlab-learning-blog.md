# Learning Git and GitLab for DevOps 🚀

As part of my DevOps learning journey, I revised Git and GitLab commands and learned how they help us manage code and work with repositories.

## 1. Repository Basics

A repository stores our project files and their history. I practised the purpose of commands such as:

- `git init` — initialize a new repository
- `git clone <repository>` — copy a remote repository to my local machine
- `git status` — check the current changes
- `git log` — view commit history
- `git push` — send local commits to a remote repository
- `git pull` — bring changes from a remote repository into my local working branch

These commands are useful when starting a project and keeping local and remote code in sync.

## 2. Branches and Commits

Branches help us work on features or fixes separately from the main code. I learned commands like `git branch`, `git checkout`, and `git merge`.

I also revised the basic commit workflow:

```bash
git status
git add <file>
git commit -m "Add a meaningful message"
git push
```

A clear commit message makes it easier to understand what changed later. Before committing, I should check which files have been modified.

## 3. Working with Changes

Sometimes I need to check differences or temporarily save unfinished work. These commands are helpful:

- `git diff` — view changes
- `git diff --staged` — view staged changes
- `git stash` — temporarily save changes
- `git stash pop` — apply the latest stash and remove it from the stash list
- `git blame <file>` — see who last changed each line

I also learned that commands such as `git reset --hard` can discard local changes, so I need to use them carefully.

## 4. Tags, Remotes, and Merge Workflows

Tags can mark a particular point in a project's history, such as a release. Remote commands help me check or update the connection to a hosted repository.

I also revised concepts such as merging, rebasing, and cherry-picking. These are useful when bringing work from one branch into another, although each works differently and should be used with care.

## 5. GitLab and CI/CD

One important part of the cheatsheet was CI/CD. GitLab CI/CD uses a `.gitlab-ci.yml` file to define pipeline stages and jobs.

A simple pipeline can have three stages:

```yaml
stages:
  - build
  - test
  - deploy

build:
  stage: build
  script:
    - echo "Building the application..."

unit_test:
  stage: test
  script:
    - echo "Running unit tests..."

deploy:
  stage: deploy
  script:
    - echo "Deploying the application..."
```

This example shows the basic structure of a pipeline. The commands shown only print messages; a real project would need actual build, test, and deployment commands. GitLab Runner is used to execute CI/CD jobs.

## 6. Git Configuration and Best Practices

I revised how to configure my Git name and email:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Some good practices I want to follow are:

- Use meaningful branch names, such as `feature/login` or `bugfix/payment-issue`.
- Write short and clear commit messages.
- Pull recent changes regularly to reduce merge conflicts.
- Use `.gitignore` to avoid tracking files that should not be committed.
- Use CI/CD pipelines to automate testing and deployment.
- Keep authentication secure and give team members only the access they need.

## 7. Common Problems

I also revised a few common Git problems:

- **Authentication errors:** check that the correct SSH key or access token is configured.
- **Merge conflicts:** inspect the conflicting files, resolve the conflicts, then stage and commit the resolution.
- **Detached HEAD:** switch back to the branch you want to continue working on.

## My Learning

This revision helped me connect Git commands with the way developers collaborate on projects. Git helps track changes and branches, while GitLab adds repository collaboration and CI/CD features.

I am still learning, so my next step is to practise these commands in a test repository and create a simple GitLab pipeline.

**Learning → Practising → Building → Sharing** 🚀
