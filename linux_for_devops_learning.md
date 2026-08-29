# 🐧 Linux for DevOps — My Learning Journey



## Introduction

As I started learning **DevOps**, one thing became very clear to me:

**Linux is one of the most important foundations of DevOps.**

DevOps engineers work with servers, applications, logs, users, permissions, networking, automation, and deployment tools. Most of these activities are performed on Linux systems.

So, instead of only memorizing commands, I am trying to understand **what each command does, why we use it, and where it can be useful in real DevOps work.**

These are my learning notes from my Linux session.

---

# 1. 🐧 What is Linux?

Linux is a **free and open-source operating system** that originated from the Unix family.

Linux was developed by **Linus Torvalds in 1991**. The first Linux code was released in September 1991, followed by the first official version, Linux 0.02, in October 1991.

Today, Linux is widely used in:

* Servers
* Cloud platforms
* DevOps
* Containers
* Networking
* Cybersecurity
* Supercomputers

### Why is Linux important for DevOps?

Because many DevOps environments run on Linux servers.

For example:

```text
Developer
    ↓
Git
    ↓
CI/CD Pipeline
    ↓
Linux Server
    ↓
Docker
    ↓
Kubernetes
    ↓
Application
```

Understanding Linux makes it much easier to understand the tools used later in a DevOps journey.

---

# 2. 📂 Linux File System Hierarchy

One of the first things I learned was the **Linux File System Hierarchy**.

Unlike Windows, Linux has a single root starting point represented by:

```bash
/
```

Linux uses a tree-like structure, where directories originate from the root directory.

A simplified structure looks like this:

```text
/
├── bin
├── sbin
├── dev
├── etc
├── home
├── boot
├── opt
├── tmp
├── usr
├── var
└── root
```

## Important directories

### `/`

The root directory. It is the starting point of the Linux filesystem.

### `/home`

Contains home directories of normal users.

### `/root`

Home directory of the root/superuser.

### `/etc`

Contains important configuration files used by the operating system and applications.

### `/var`

Contains variable data such as logs and other files that can grow over time.

One important location is:

```bash
/var/log
```

This is especially important for DevOps because application and system logs are commonly investigated when troubleshooting.

### `/tmp`

Used for temporary files.

### `/boot`

Contains files required during the boot process, including Linux kernel and boot-loader related files.

### `/dev`

Contains device files representing hardware and devices.

### `/usr`

Contains applications and files used by users.

### `/opt`

Often used for optional or third-party application software.

### `/mnt`

Used for temporarily mounting filesystems.

### `/media`

Used for removable media devices.

The notes describe these directories and their purposes in the Linux filesystem hierarchy.

---

# 3. ⌨️ Basic Linux Commands

Before working with servers, I need to become comfortable with basic Linux commands.

## `pwd`

Shows the current working directory.

```bash
pwd
```

Example:

```text
/home/prajwal
```

---

## `ls`

Shows files and directories in the current directory.

```bash
ls
```

---

## `cd`

Used to change directories.

```bash
cd /home
```

---

## `whoami`

Shows the currently logged-in user.

```bash
whoami
```

---

## `uname`

Displays information about the system/kernel.

```bash
uname
```

To check the kernel version:

```bash
uname -r
```

---

## `clear`

Clears the terminal screen.

```bash
clear
```

---

## `history`

Displays previously executed commands.

```bash
history
```

---

## `date`

Displays the current date and time.

```bash
date
```

These commands are among the basic Linux commands covered in my notes.

---

# 4. 📄 Creating and Managing Files

Linux provides simple commands for creating and managing files and directories.

## `touch`

`touch` can be used to create an empty file.

```bash
touch file1.txt
```

Multiple files can also be created:

```bash
touch file1.txt file2.txt file3.txt
```

My key learning:

> `touch` creates an empty file; it is not a text editor.

The notes specifically point out that `touch` is used for creating empty files.

---

# 5. 📋 Copying Files with `cp`

The `cp` command is used to copy files or directories.

Basic syntax:

```bash
cp <source> <destination>
```

Example:

```bash
cp file1.txt backup.txt
```

Common options from my notes:

```text
-r  → recursive
-v  → verbose
-f  → force
```

For example:

```bash
cp -r project/ backup/
```

The `-r` option is useful when copying directories and their contents.

---

# 6. 🗑️ Remove, Move and Rename

Linux also provides commands for removing, moving and renaming files/directories.

The important concepts I practiced were:

```text
Remove
Move
Rename
```

The `mv` command can be used for both moving and renaming.

Example:

```bash
mv oldname.txt newname.txt
```

This helped me understand that many Linux commands can perform more than one practical task depending on how they are used.

---

# 7. 👤 Linux User Management

In a server environment, multiple users may need access to the system.

Linux provides commands for:

* Creating users
* Checking user properties
* Setting passwords
* Checking password properties
* Switching users
* Logging out
* Deleting users

The user-management section of my notes focuses on these administrative tasks.

### Why is this important in DevOps?

Imagine a company server where:

```text
Developer
Tester
DevOps Engineer
Administrator
```

all need different levels of access.

User management helps control who can access the system and what they can do.

---

# 8. 👥 Linux Group Management

A **group** is a collection of user accounts.

Groups are useful because administrators can manage permissions for multiple users together.

For example:

```text
DevOps-Team
   ├── Prajwal
   ├── Rahul
   └── Amit
```

Instead of configuring permissions individually for every user, permissions can be assigned to the group.

This becomes especially useful in organizations with many users.

---

# 9. 🔐 Linux File Permissions

One of the most important Linux topics for me was **file permissions**.

Linux permissions control who can access files and directories.

The three main permission categories are:

```text
u → User/Owner
g → Group
o → Others
```

The basic permissions are:

```text
r → Read
w → Write
x → Execute
```

The notes cover basic permissions, special permissions and ACL permissions.

---

# 10. 🔢 Numeric Permissions

Linux permissions can also be represented using numbers.

```text
Read    = 4
Write   = 2
Execute = 1
```

So:

```text
rwx = 4 + 2 + 1 = 7
rw- = 4 + 2     = 6
r-x = 4 + 1     = 5
```

For example:

```bash
chmod 755 script.sh
```

Conceptually:

```text
Owner  → 7 → rwx
Group  → 5 → r-x
Others → 5 → r-x
```

This is something I definitely want to practice more because permissions are extremely important when working with Linux servers.

The numeric permission values are included in my notes.

---

# 11. 🔑 Changing Permissions and Ownership

Linux provides commands to change:

* File permissions
* File ownership
* Group ownership

For example:

```bash
chmod
```

is used to change permissions.

And ownership can be managed using ownership-related commands.

The notes specifically cover changing permissions, changing ownership and changing group ownership.

---

# 12. 🛡️ ACL — Access Control List

ACL was one of the interesting topics for me.

Normally, Linux permissions work with:

```text
Owner
Group
Others
```

But what if I want to give **one specific user** access to a file without making that user a member of the group?

That's where **ACL** becomes useful.

ACL provides an additional and more flexible permission mechanism for files and directories.

For example:

```text
project.txt

Owner  → read/write
Group  → read
Others → no access

Specific user Rahul → read/write
```

Rahul does not necessarily need to become part of the group just to receive that additional access.

---

# 13. 🔎 grep and Regular Expressions

When working with servers, I will often need to search through logs.

This is where `grep` becomes very useful.

`grep` searches files for a particular pattern and displays matching lines.

Example:

```bash
grep "error" app.log
```

I can use it to:

* Search for a word
* Search across multiple files
* Perform case-insensitive searches
* Search recursively
* Invert matches
* Display line numbers
* Display matching filenames

For example:

```bash
grep -i "error" app.log
```

### DevOps use case

Suppose an application is failing.

Instead of manually reading thousands of log lines:

```bash
grep "ERROR" app.log
```

can quickly help me find relevant entries.

This is one of the commands I expect to use frequently while working with Linux servers.

---

# 14. 🔍 find Command

Another important Linux command is:

```bash
find
```

The `find` command searches for files and directories based on conditions.

It can search based on:

* File name
* File type
* User
* Group
* Permissions
* Size
* Date

For example:

```bash
find /home -type f
```

I can also use conditions to search for files based on their size or permissions.

### DevOps use case

Suppose a server is running out of disk space.

Finding large files becomes useful:

```bash
find /var -type f
```

From there, I can investigate which files are consuming storage.

---

# 15. 📊 wc — Word Count

The `wc` command can be used to count lines and words.

Examples:

```bash
wc -l file.txt
```

Counts lines.

```bash
wc -w file.txt
```

Counts words.

The notes introduce `wc` as a command for counting words and lines.

---

# 16. ⬆️ head and tail

These two commands are very useful when working with logs.

### `head`

Displays the beginning of a file.

```bash
head file.txt
```

By default, it displays the top portion of the file.

### `tail`

Displays the end of a file.

```bash
tail file.txt
```

The notes cover both `head` and `tail` for displaying the beginning and end of files.

### Why is `tail` important for DevOps?

Application logs continuously grow.

Instead of opening a huge log file, I can inspect the latest entries with:

```bash
tail app.log
```

---

# 17. 📦 Archive Files with tar

The `tar` command is used to create and extract archives.

It is commonly used for:

* Backups
* Packaging files
* Archiving directories
* Compression workflows

The notes explain that `tar` can work with compression algorithms such as gzip, bzip2 and xz.

Basic syntax:

```bash
tar <options> <files>
```

Important options:

```text
c → create
x → extract
v → verbose
f → file
t → test/list
z → gzip
j → bzip2
J → xz
C → specific destination
```

These options are summarized in my notes.

Example:

```bash
tar -cvf backup.tar project/
```

Extract:

```bash
tar -xvf backup.tar
```

For gzip:

```bash
tar -czvf backup.tar.gz project/
```

---

# 18. ⚙️ Linux Job Automation

One of the most important DevOps concepts I learned in this session is **automation**.

Linux allows us to schedule jobs so that tasks can execute automatically.

The notes introduce two important mechanisms:

```text
at
crontab
```

### `at`

Used when I want to execute a job **one time**.

### `crontab`

Used when I want to execute jobs **repeatedly according to a schedule**.

The notes describe job automation as a way to perform operating-system tasks automatically, including daily administrative work.

This is directly connected to the DevOps mindset:

> **If a task is repetitive, try to automate it.**

---

# 19. 🔐 sudo

The `sudo` command allows an authorized user to execute commands with another user's privileges, commonly administrative/root privileges.

Linux checks the `/etc/sudoers` configuration to determine what privileges are allowed.

Example:

```bash
sudo command
```

The notes also cover:

* Giving sudo privileges to users
* Giving sudo privileges to groups
* The wheel group
* Passwordless sudo configuration

For example, the notes show the wheel group being used for sudo privileges.

### Important lesson

Administrative privileges should be given carefully.

A small permission mistake on a production server can cause serious problems.

---

# 20. 🌐 Linux Networking

A DevOps engineer also needs to understand Linux networking.

The notes cover networking management using:

```bash
nmcli
```

`nmcli` is used to manage network settings through NetworkManager.

I learned that networking tasks include:

* Checking IP addresses
* Managing connections
* Checking active connections
* Checking device status
* Creating connections
* Configuring IP addresses
* Configuring gateways
* Configuring DNS
* Activating/deactivating connections
* Setting hostnames

Example commands from my notes include:

```bash
nmcli con show --active
```

and:

```bash
nmcli con show citynet
```

The notes also demonstrate modifying an example connection called `citynet`.

---

# 21. 🖥️ nmtui

Another way to configure networking is:

```bash
nmtui
```

It provides a text-based interface for NetworkManager configuration.

My notes also mention that connections created using `nmcli` and `nmtui` are stored in connection configuration files.

---

# 🧠 What I Learned From This Linux Session

Before this session, Linux commands looked like a collection of random commands.

Now I'm starting to see the bigger picture.

```text
Linux
 │
 ├── Filesystem
 │
 ├── Commands
 │
 ├── Users & Groups
 │
 ├── Permissions
 │
 ├── ACL
 │
 ├── Log Searching
 │      ├── grep
 │      ├── find
 │      ├── head
 │      └── tail
 │
 ├── Archives
 │      └── tar
 │
 ├── Automation
 │      ├── at
 │      └── crontab
 │
 ├── Privileges
 │      └── sudo
 │
 └── Networking
        ├── nmcli
        └── nmtui
```

These aren't isolated topics.

They work together when managing real servers.

---

# 🧪 My Next Step: Hands-on Practice

Reading Linux notes is not enough.

My next goal is to practice these commands on a Linux machine.

### Practice checklist

* [ ] Navigate the Linux filesystem
* [ ] Create files and directories
* [ ] Copy, move and delete files
* [ ] Create users
* [ ] Create groups
* [ ] Change permissions
* [ ] Change ownership
* [ ] Practice ACL
* [ ] Search logs using `grep`
* [ ] Search files using `find`
* [ ] Practice `head` and `tail`
* [ ] Create and extract `tar` archives
* [ ] Schedule jobs using `at`
* [ ] Schedule recurring jobs using `crontab`
* [ ] Practice `sudo`
* [ ] Check and configure networking with `nmcli`

---

# 🚀 Why This Matters for My DevOps Journey

Linux is not just another topic that I need to finish.

It is a **foundation for the DevOps tools I will learn next**.

My learning path is gradually moving toward:

```text
Linux
  ↓
Git & GitHub
  ↓
Networking
  ↓
Shell Scripting
  ↓
AWS / Cloud
  ↓
Docker
  ↓
Jenkins / CI-CD
  ↓
Kubernetes
  ↓
Terraform
  ↓
Monitoring
```

I am learning these concepts step by step rather than trying to learn everything at once.

---

# 💡 My Key Takeaway

The biggest lesson from this Linux session was:

> **Don't just memorize commands. Understand what problem each command solves.**

As a beginner in DevOps, my goal is not to become perfect in Linux in one day.

My goal is to **practice every day, make mistakes, understand those mistakes, and gradually become comfortable working with Linux servers.**

This is one more step in my **DevOps learning journey.** 🚀🐧

---

