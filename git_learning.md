# Git & GitHub: What I Learned as a DevOps Beginner 🚀

As I started learning DevOps, one of the first tools I came across was **Git**.

At first, Git looked a little confusing because there were many commands like `git add`, `git commit`, `git push`, `git pull`, branches, merge, stash, rebase, etc.

But after learning the concepts step by step, I understood that Git is basically a way to **track changes in code and work safely with other developers**.

In this blog, I am sharing what I learned about Git and GitHub in my own simple words.

---

## 1. What is Source Code Management?

Before understanding Git, I learned about **Source Code Management (SCM)**.

SCM is used to manage and track changes made to source code.

There are mainly two types:

* **CVCS – Centralized Version Control System**
* **DVCS – Distributed Version Control System**

### CVCS – Centralized Version Control System

In a centralized system, the main code is stored on a central server.

The developer generally needs to be connected to the network to perform operations.

One major problem is that if the central server fails, the complete data can be affected.

### DVCS – Distributed Version Control System

Git follows the distributed approach.

In DVCS, every contributor can have a **local copy (clone)** of the main repository.

This local repository contains the files and the required metadata.

So, developers can work on their local repositories and later synchronize their changes with the remote repository.

---

# 2. Why is Git Important for DevOps?

While learning DevOps, I understood that Git is very important because modern DevOps workflows depend heavily on source code management.

For example, in a **CI/CD pipeline**, the pipeline needs the latest version of the application code.

The pipeline can take the latest code, build it, test it and then deploy it to the required environment.

So, Git becomes an important part of the DevOps workflow.

---

# 3. Git Three-Stage Architecture

One concept that helped me understand Git better was its three-stage architecture.

It can be understood through:

**Working Directory → Repository → Remote Repository**

### Working Directory

This is where we actually work on our files.

We create files, modify code and make changes here.

### Repository

The repository stores our project and its Git information.

It keeps track of changes and contains metadata related to the project.

### Remote Repository

A remote repository is generally hosted on a server such as GitHub.

It allows developers to store and share their project with others.

---

# 4. What is a Commit?

A **commit** is basically a saved version of our changes in Git.

Whenever I make some changes and commit them, Git creates a unique identifier for that commit.

The commit ID is based on a hash.

One interesting thing I learned is that even a very small change, such as changing a single dot, can result in a different commit ID.

So commits help us identify different versions of our project.

Think of it like:

**Code change → Commit → Version of the project**

---

# 5. What is a Git Tag?

A tag is used to give a meaningful name to a particular version of the repository.

For example, instead of remembering a commit ID, we can create a tag like:

```bash
v1.0
```

This can represent a particular release or version of the project.

Once a tag points to a particular commit, creating another commit does not automatically move that tag.

---

# 6. Push and Pull

Two commands that I use frequently while learning Git are:

### Git Push

`git push` sends our local changes to the remote repository.

For example:

```bash
git push origin main
```

This is useful when I want to upload my local commits to the remote repository.

### Git Pull

`git pull` brings changes from the remote repository to the local repository.

For example:

```bash
git pull origin main
```

I can think of it simply as:

**Push → Local → Remote**

**Pull → Remote → Local**

---

# 7. Understanding Git Branches 🌿

Branches were one of the most important concepts I learned in Git.

Imagine a project where multiple developers are working on different tasks.

Instead of directly changing the main code, we can create separate branches.

For example:

```text
main
 ├── login-feature
 ├── payment-feature
 └── bug-fix
```

Each task can have its own branch.

The developers can work independently and later merge their changes into the main branch.

This makes **parallel development** easier.

---

# 8. Why Do We Use Branches?

Suppose I am working on a new login feature.

If I directly modify the main branch and something goes wrong, the main project can be affected.

Instead, I can create a new branch:

```bash
git checkout -b login-feature
```

Then I can work on the feature separately.

After completing the work, the branch can be merged with the main branch.

So the basic flow becomes:

```text
Create Branch
      ↓
Write Code
      ↓
Add Changes
      ↓
Commit
      ↓
Merge
      ↓
Main Branch
```

---

# 9. Git Merge Conflict 😵

While learning branches, I also came across **merge conflicts**.

A conflict can happen when different branches contain different changes in the same file or same part of a file.

For example:

```text
Branch A → changed the same line
Branch B → also changed the same line
                    ↓
               Merge Conflict
```

Git cannot automatically decide which change should be kept.

So, we have to manually open the conflicting file and resolve the changes.

After resolving the conflict:

```bash
git add .
git commit
```

The merge can then be completed.

Some commands that can help while dealing with conflicts are:

```bash
git diff
git log --merge
git reset
git merge --abort
```

`git merge --abort` can be useful when I want to stop the merge process and return to the state before the merge started.

---

# 10. Basic Git Commands I Learned

Here are some of the important commands from my notes:

### Configure username and email

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

### Initialize a repository

```bash
git init
```

### Clone an existing repository

```bash
git clone <repository-url>
```

### Check repository status

```bash
git status
```

### Add a file

```bash
git add filename
```

### Add all files

```bash
git add .
```

### Commit changes

```bash
git commit -m "message"
```

### Check branches

```bash
git branch
```

### Create a new branch

```bash
git checkout -b feature
```

### Switch to another branch

```bash
git checkout branch-name
```

### Delete a branch

```bash
git branch -d branch-name
```

### Push changes

```bash
git push
```

### Pull changes

```bash
git pull
```

### Check commit history

```bash
git log
```

---

# 11. What is Cherry-Pick?

Another interesting Git concept I learned was **cherry-pick**.

Cherry-picking means taking a particular commit from one branch and applying it to another branch.

For example, suppose I accidentally made an important fix in the wrong branch.

Instead of taking the complete branch, I can take only that particular commit and apply it to the correct branch.

The command is:

```bash
git cherry-pick <commit-id>
```

So, I understood cherry-pick as:

**Pick one useful commit → Apply it to another branch**

---

# 12. Git Stash

Sometimes we are working on a feature and suddenly we need to switch to another task.

But our current code is incomplete.

In that situation, committing incomplete code may not be a good idea, and deleting the changes is also not what we want.

This is where **Git Stash** becomes useful.

Git stash temporarily stores our uncommitted changes.

For example:

```bash
git stash
```

Now I can switch to another branch or work on something else.

Later, I can bring my changes back.

### See stash list

```bash
git stash list
```

### Apply stashed changes

```bash
git stash apply
```

### Apply and remove from stash

```bash
git stash pop
```

### Delete a stash

```bash
git stash drop
```

For me, the easiest way to remember stash is:

**Stash = Keep my unfinished work safely for later.**

---

# 13. What is Git Rebase?

Rebase was another concept I found interesting.

**Rebasing means moving or combining a sequence of commits onto a new base commit.**

One of the main reasons for using rebase is to maintain a more **linear project history**.

It is commonly discussed in feature-branch workflows.

The concept initially looked confusing to me, but I started understanding it as:

**Move my commits to a newer base → Keep the history cleaner and more linear.**

---

# 14. What is Git Squash?

Squashing means **combining multiple commits into one commit**.

Suppose I have:

```text
Commit 1
Commit 2
Commit 3
Commit 4
```

If these commits are small changes related to the same feature, they can sometimes be combined into one meaningful commit.

After squashing:

```text
Feature Completed
```

Git's **interactive rebase** can be used for this.

For example:

```bash
git rebase -i HEAD~4
```

This allows us to work with the recent commits and squash them together.

The main benefit I understood is that it can make the project history cleaner and easier to understand.

---

# 15. My Git Learning Flow

After learning all these concepts, I started seeing Git as a complete workflow rather than just a collection of commands.

My basic understanding is:

```text
Create / Clone Repository
          ↓
    Create Branch
          ↓
      Write Code
          ↓
       git add
          ↓
      git commit
          ↓
      git push
          ↓
    Remote Repository
          ↓
       CI/CD
          ↓
       Deployment
```

Of course, real projects can have more steps, but this flow helped me understand how Git fits into DevOps.

---

# 16. Final Thoughts 🚀

When I first started learning Git, I thought it was mainly about remembering commands.

But after going through concepts like **repositories, commits, branches, merge conflicts, stash, cherry-pick, rebase and squash**, I realized that Git is more about understanding how code changes are managed.

As someone learning DevOps, Git is one of those tools that I know I will use again and again.

I am still learning, but now when I see commands like:

```bash
git add
git commit
git push
git pull
git branch
git merge
git stash
git rebase
```

they don't feel like random commands anymore.

They represent different steps in managing and collaborating on code.

**This is what I learned about Git & GitHub as part of my DevOps journey. 🚀**

And this is just the beginning — next, I want to understand how Git and GitHub connect with **CI/CD pipelines and real DevOps projects.**
