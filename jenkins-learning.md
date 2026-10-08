# Week 4 — Learning Jenkins & CI/CD 🚀

This week, I started learning **Jenkins** as part of my DevOps journey.

Before learning Jenkins, I had heard about CI/CD many times, but I wanted to understand how it actually helps in a real development process.

## 🔹 What is Jenkins?

Jenkins is an **open-source automation server** used to automate different parts of the software development process.

It can help automate tasks like:

* Building applications
* Running tests
* Checking code
* Creating artifacts
* Deploying applications

For me, the main idea was simple:

**Instead of doing the same steps manually again and again, Jenkins can automate them.**

## 🔹 Understanding CI/CD

I also learned the basic concept of **CI/CD**.

**CI – Continuous Integration**

Developers regularly integrate their code into a shared repository. The code can then be automatically built and tested.

**CD – Continuous Delivery**

After the code passes the required checks, it can be kept ready for release or deployment.

A simple flow I understood was:

**Developer → Git → Jenkins → Build → Test → Deploy**

This helped me understand where Jenkins fits into the DevOps process.

## 🔹 Jenkins Pipeline

One of the important things I learned was **Jenkins Pipeline**.

A pipeline represents the different steps that code goes through before reaching production.

For example:

```text
Git
 ↓
Build
 ↓
Test
 ↓
Code Analysis
 ↓
Create Artifact
 ↓
Deploy
```

Instead of manually performing every step, we can define these steps in a Jenkins pipeline.

## 🔹 Declarative Pipeline

I also learned about **Declarative Pipeline**.

It provides a structured way to write Jenkins pipelines and makes them easier to understand and maintain.

A basic pipeline contains things like:

```text
pipeline
   ↓
agent
   ↓
stages
   ↓
steps
```

Each stage can perform a particular task such as building, testing, or deploying an application.

## 🔹 Jenkins Steps

I learned that Jenkins provides different steps for performing different tasks.

For example:

* `git` → checkout code
* `sh` → run shell commands
* `npm` → run npm-related tasks
* `docker` → work with Docker
* JUnit → handle test results
* Archive → store build artifacts

This showed me how Jenkins can connect different DevOps tools together.

## 🔹 Jenkins Logs & Troubleshooting

Another important thing I learned was checking **Jenkins logs**.

When a pipeline fails, the console output helps us understand what went wrong.

So troubleshooting is also an important part of working with Jenkins.

Instead of just seeing that a build failed, I need to read the logs and find the actual error.

## 🔹 What I Learned This Week

This week helped me understand that Jenkins is not just a tool for running builds.

It can become an important part of the **CI/CD process** by connecting source code, builds, testing, and deployment.

My basic understanding now looks like:

```text
Linux
  ↓
Git & GitHub
  ↓
Jenkins
  ↓
CI/CD
  ↓
Docker
  ↓
Cloud
```

I am still learning and practicing these concepts step by step. My goal is not just to remember the commands, but to understand **why and where we use them in real DevOps workflows.**


