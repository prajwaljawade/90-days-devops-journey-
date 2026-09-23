


---

When I started learning DevOps, one name kept coming up everywhere: **Docker**. Everyone talked about "containers", "images", and how Docker apparently solved one of the most annoying problems in software development. So I decided to sit down, go through the fundamentals properly, and write it all up the way I understood it — partly to help myself remember, and partly for anyone else who's just getting started.

Here's what I learned.

## The Problem Docker Solves

Before jumping into definitions, it helps to understand *why* Docker exists in the first place.

Every developer has heard (or said) this sentence at least once: **"But it works on my machine!"** A particular piece of code runs perfectly fine on the developer's system, but the moment it reaches the user or a different environment, it breaks. Different OS versions, missing dependencies, mismatched configurations — the list of things that can go wrong is endless.

Docker was built to fix exactly this. Instead of worrying about whether an app will behave the same way everywhere, Docker packages the application along with everything it needs to run — dependencies, configs, libraries — into one consistent unit. That unit runs the same way, everywhere.

## What Exactly Is Docker?

Docker is an **open-source platform** designed to create, deploy, and run applications easily using containers.

A few basics that helped it click for me:

- Docker was first released in **March 2013**, created by **Solomon Hykes**.
- It's written in the **Go** language.
- Docker performs **OS-level virtualization** — commonly called **containerization**.
- Unlike a full virtual machine, Docker containers share the **host OS's Linux kernel** instead of creating a whole separate virtual OS. This is what makes containers so much lighter than VMs.
- You can install Docker on any OS, but the **Docker engine runs natively on Linux**.

## Why Everyone Recommends Docker

Once I understood the "why," the advantages made a lot more sense:

- No need to pre-allocate RAM.
- Improves **CI efficiency** — you build one container image and reuse the same image across every stage of deployment (dev → test → prod).
- Cost-effective and lightweight.
- Runs on physical hardware, virtual hardware, or the cloud — it doesn't care.
- Images are reusable, and containers are created very quickly.

## But It's Not Perfect

Learning the trade-offs is just as important as learning the benefits:

- Not ideal for applications that need a **rich GUI**.
- Managing a **large number of containers** can get complicated fast.
- **No cross-platform compatibility** — an app containerized on Windows won't just run on Linux, and vice versa.
- Best suited when the **development and testing OS are the same**. If they differ, a VM is a better fit.
- Docker doesn't offer a built-in solution for **data recovery and backup**.

One line from my notes that really helped clear my confusion between images and containers:

> **When an image is running, we call it a container. When a container is stopped/not runnable, we call it an image.**

## The Architecture — Client, Host, Registry

Docker's architecture is made up of three main pieces working together:

1. **Client** — where you run commands like `docker build`, `docker pull`, `docker run`.
2. **Docker Host** — where the actual **Docker daemon** lives, along with containers and images.
3. **Registry** — where Docker images are stored (like Docker Hub, or a private registry).

Breaking down the components further:

- **Docker Daemon** — runs on the host OS, manages containers and services, and can even communicate with other daemons.
- **Docker Client** — how users interact with the daemon, using commands and REST APIs.
- **Docker Host** — provides the environment to actually run everything: daemon, images, containers, networks, and storage.
- **Docker Hub / Registry** — manages and stores images. There are two types:
  - **Public Registry** (Docker Hub)
  - **Private Registry** (used to share images within an organization)
- **Docker Images** — read-only binary templates used to create containers. Think of an image as a single file containing all the dependencies and configuration needed to run a program.
- **Docker Container** — a running instance created from an image. If the image is the template, the container is a live copy of it.

There are three ways to create an image:
1. Pull an existing image from Docker Hub.
2. Build one from a Dockerfile.
3. Create one from an existing container.

## Getting Hands-On: Installation & Core Commands

Once the theory made sense, I moved to the practical side — spinning up a machine (I used an AWS instance with Docker pre-installed) and running through the essential commands.

**Install Docker (if not already installed):**
```bash
yum install docker
```

**See all images available locally:**
```bash
docker images
```

**Search for an image on Docker Hub:**
```bash
docker search <image_name>
```

**Pull an image from Docker Hub:**
```bash
docker pull <image_name>
```

**Create and run a named container:**
```bash
docker run -it --name <container_name> <image_name> /bin/bash
```
The `-it` flag puts you in interactive mode and drops you straight into the container's terminal.

**Check if the Docker service is running:**
```bash
service docker status
```

**Start the Docker service:**
```bash
service docker start
```

**Start / stop a container:**
```bash
docker start <container_name>
docker stop <container_name>
```

**Attach to a running container:**
```bash
docker attach <container_name>
```

**List all containers (running + stopped):**
```bash
docker ps -a
```

**List only running containers:**
```bash
docker ps
```

**Remove a container:**
```bash
docker rm <container_name>
```

**Exit a container:**
```bash
exit
```

**Remove an image:**
```bash
docker image rm <image_name>
```

## Building an Image the Manual Way

Before diving into Dockerfiles, I tried creating an image manually — just to understand what's actually happening under the hood.

1. Create and enter a container:
   ```bash
   docker run -it --name <container_name> <image_name> /bin/bash
   cd /tmp
   ```
2. Create a file inside it:
   ```bash
   touch myfile
   ```
3. Check what changed compared to the base image:
   ```bash
   docker diff <old_container_name>
   ```
   (`D` = deletion, `C` = change, `A` = addition)
4. Commit the container as a new image:
   ```bash
   docker commit <container_name> <container_image_name>
   docker images
   ```
5. Run a new container from this updated image — and the file you created earlier will still be there.

This exercise made it very clear: **an image is basically a frozen snapshot of a container's filesystem state.**

## The Real Deal: Dockerfiles

Doing everything manually is fine for learning, but in the real world, you automate image creation using a **Dockerfile** — a plain text file containing a set of build instructions.

Here are the instructions I learned, one by one:

| Instruction | What it does |
|---|---|
| `FROM` | Defines the base image. Must be the first line in the Dockerfile. |
| `RUN` | Executes a command and creates a new layer in the image. |
| `MAINTAINER` | Notes the author/owner/description of the image. |
| `COPY` | Copies files from the local system into the image. Can't fetch from the internet or remote repos. |
| `ADD` | Like `COPY`, but can also download files from the internet and extract archives. |
| `EXPOSE` | Declares the port the container will use (e.g., 8080 for Tomcat, 80 for Nginx). |
| `WORKDIR` | Sets the working directory for the container. |
| `CMD` | Runs a command when the container is created — can be overridden at runtime. |
| `ENTRYPOINT` | Similar to `CMD` but takes priority — the command specified here always runs first. |
| `ENV` | Sets environment variables. |
| `ARG` | Defines a build-time parameter with a default value. Unlike `ENV`, values set with `ARG` are **not** accessible once the container is running. |

**Steps to build and run from a Dockerfile:**

1. Create a file named `Dockerfile`.
2. Add your instructions.
3. Build the image:
   ```bash
   docker build -t <image_name> .
   ```
   (`-t` sets the tag/name, and `.` tells Docker to look in the current directory for the Dockerfile.)
4. Run a container from the new image:
   ```bash
   docker run -it --name <container_name> <image_name> /bin/bash
   ```

The best part? Once your Dockerfile exists, you don't need to recreate it for every change — just edit it and rebuild the image.

## Understanding Docker Volumes

This is the part that took me the longest to really understand, so I'm writing it out in detail.

A **volume** is simply a directory inside a container that's used for persistent storage. A few key rules:

- You must declare a directory as a volume **at the time the container is created** — you can't add one to an existing container.
- Even if the container stops, the data in the volume is still accessible.
- One volume can be shared across multiple containers.
- Volumes are **not** included when you update an image.

Volumes can be mapped in two ways:
1. **Container ↔ Container**
2. **Host ↔ Container**

### Creating a Volume via Dockerfile

```dockerfile
FROM ubuntu
VOLUME ["/myvolume1"]
```

Build and run it:
```bash
docker build -t <image_name> .
docker run -it --name <container_name> <image_name> /bin/bash
```

Now sharing that volume with a second container:
```bash
docker run -it --name <container_name> --privileged=true \
  --volumes-from <container_name> <os_image_name> /bin/bash
```

Any changes made in one container's volume instantly show up in the other.

### Creating a Volume via Command Line

```bash
docker run -it --name <container_name> -v /<volume_name> <os_name> /bin/bash
```

And to share it with another container:
```bash
docker run -it --name <container_name> --privileged=true \
  --volumes-from <container_name> <os_name> /bin/bash
```

### Mapping Host ↔ Container

```bash
docker run -it --name <container_name> -v /home/ec2-user:/<volume_name> \
  --privileged=true <os_name> /bin/bash
```

Once inside, anything you `touch` in that volume will also show up on the host machine — a genuinely satisfying moment when you see it work for the first time.

### Other Useful Volume Commands

```bash
docker volume ls                       # list all volumes
docker volume create <volume_name>     # create a volume
docker volume rm <volume_name>         # delete a volume
docker volume prune                    # remove all unused volumes
docker volume inspect <volume_name>    # get volume details
docker container inspect <container_name>  # get container details
```

## A Few Concepts That Finally Clicked

**`docker attach` vs `docker exec`**
- `docker exec` creates a **new process** inside the container's environment.
- `docker attach` simply connects your terminal's standard I/O to the container's **already running main process**.
- In short: use `exec` when you want to run something new inside an already-running container.

**`EXPOSE` vs `-p` (publish)**

This one confused me for a while, so here's the breakdown:

| Setup | Result |
|---|---|
| Neither `EXPOSE` nor `-p` | The service is only accessible from *inside* the container itself. |
| Only `EXPOSE` | Accessible from other Docker containers, but not from outside Docker. Good for inter-container communication. |
| Both `EXPOSE` and `-p` | Accessible from anywhere — even outside Docker entirely. |

**Note:** if you use `-p` without `EXPOSE`, Docker does an *implicit* expose — because if a port is open to the public, it's automatically open to other containers too.

## Wrapping Up

