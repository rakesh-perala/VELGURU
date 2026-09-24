1 What Is Linux?
Linux is an open-source operating system kernel.

In everyday conversation, people commonly use the term "Linux" to refer to a complete operating system distribution built around the Linux kernel.

Examples:

Ubuntu
Debian
Red Hat Enterprise Linux
Rocky Linux
AlmaLinux
Amazon Linux
SUSE Linux Enterprise
Linux is heavily used in enterprise infrastructure because it provides:

Stability
Automation capabilities
Strong networking support
Security controls
Process management
Flexible configuration
Excellent command-line tooling
Strong cloud support

# 4. Linux Command Categories

| Category             | Main Commands                        |
| -------------------- | ------------------------------------ |
| Directory creation   | `mkdir`, `mkdir -p`                  |
| Directory navigation | `pwd`, `cd`, `ls`                    |
| Move and rename      | `mv`                                 |
| Copy                 | `cp`, `cp -r`, `cp -a`               |
| Permissions          | `chmod`, `umask`, `stat`             |
| Users                | `useradd`, `adduser`, `passwd`, `id` |
| Groups               | `groupadd`, `usermod`, `gpasswd`     |
| Ownership            | `chown`, `chgrp`                     |
| File content         | `cat`, `less`, `head`, `tail`, `nl`  |
| Filtering            | `grep`, `cut`, `sort`, `uniq`, `awk` |
| Search               | `find`, `locate`, `grep -r`          |
| Tar archives         | `tar`                                |
| Zip archives         | `zip`, `unzip`                       |
| Validation           | `ls -l`, `stat`, `file`, `du`, `id`  |

---

# 2. Linux Introduction

## 2.1 What is Linux?

Linux is an open-source operating system kernel.

A Linux distribution combines:

```text
Linux Kernel
     +
System Utilities
     +
Package Manager
     +
Libraries
     +
Applications
```

Examples:

* Ubuntu
* Debian
* Red Hat Enterprise Linux
* Rocky Linux
* AlmaLinux
* Amazon Linux

---

## 2.2 Why DevOps Engineers Need Linux

Most DevOps infrastructure uses Linux extensively:

```text
Developer
   ↓
Git
   ↓
Jenkins
   ↓
Docker
   ↓
Kubernetes
   ↓
AWS EC2 / EKS
   ↓
Linux Infrastructure
```

A DevOps engineer should be comfortable with:

* Files
* Permissions
* Processes
* Networking
* Services
* Logs
* Storage
* Users
* SSH
* Shell scripting
* Troubleshooting

---

# 3. Linux Architecture

```text
+----------------------------------+
|          Applications            |
+----------------------------------+
|       Shell / Utilities          |
+----------------------------------+
|          System Libraries        |
+----------------------------------+
|          Linux Kernel            |
+----------------------------------+
|             Hardware             |
+----------------------------------+
```

## 3.1 Kernel

The kernel communicates with hardware.

It manages:

* CPU
* Memory
* Processes
* Storage
* Networking
* Devices

---

## 3.2 Shell

The shell allows us to interact with Linux.

Example:

```bash
bash
```

Common shells:

```text
bash
zsh
sh
fish
```

---

# 4. Linux Installation and Lab Setup

For training, use an Ubuntu-based environment.

Recommended environments:

```text
Laptop
  ↓
WSL / Virtual Machine
  ↓
Ubuntu
```

or:

```text
Local Machine
      ↓
AWS EC2
      ↓
Ubuntu / Amazon Linux
```

## Basic verification

```bash
cat /etc/os-release
uname -a
hostname
whoami
pwd
```

---

# 5. Linux Terminal Fundamentals

Before learning commands, students must understand:

```text
Command
Option
Argument
Path
Output
Exit Status
```

Example:

```bash
ls -lah /var/log
```

Breakdown:

```text
ls       → command
-l       → option
-a       → option
-h       → option
/var/log → argument
```

---

# 6. Linux File System

Linux uses a hierarchical filesystem.

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

## Important directories

| Directory  | Purpose                        |
| ---------- | ------------------------------ |
| `/`        | Root of filesystem             |
| `/home`    | Normal users' home directories |
| `/root`    | Root user's home               |
| `/etc`     | Configuration                  |
| `/var`     | Variable data and logs         |
| `/var/log` | Logs                           |
| `/tmp`     | Temporary files                |
| `/opt`     | Optional/application software  |
| `/usr`     | User-space programs/libraries  |
| `/bin`     | Essential commands             |
| `/sbin`    | System administration commands |
| `/dev`     | Device files                   |
| `/proc`    | Process/kernel information     |
| `/sys`     | Kernel/device information      |
| `/boot`    | Boot-related files             |

---

# 7. Essential File and Directory Commands

> **Rule:** Every important command below has **5 labs**.

---

# 7.1 `pwd`

## What is `pwd`?

`pwd` means:

```text
Print Working Directory
```

It tells us where we currently are.

### Syntax

```bash
pwd
```
---

## Lab 1 — Check Current Directory

```bash
pwd
```

### Objective

Understand the current working directory.

---

## Lab 2 — Navigate and Verify

```bash
cd /tmp
pwd
```

---

## Lab 3 — Home Directory

```bash
cd ~
pwd
```

---

## Lab 4 — Parent Directory

```bash
cd ..
pwd
```

---

## Lab 5 — Production Directory Verification

```bash
cd /var/log
pwd
ls
```

### Interview Questions

1. What does `pwd` do?
2. Difference between absolute and relative paths?
3. What does `~` represent?

---

# 7.2 `ls`

## What is `ls`?

Lists files and directories.

### Basic syntax

```bash
ls
```

### Important options

```bash
ls -l
ls -a
ls -h
ls -lh
ls -la
ls -ltr
```

---

## Understanding `ls -l`

Example:

```text
-rw-r--r-- 1 ubuntu ubuntu 2456 Sep 24 10:30 app.conf
```

Breakdown:

```text
-              → File type
rw-r--r--      → Permissions
1              → Link count
ubuntu         → Owner
ubuntu         → Group
2456           → Size
Sep 24 10:30   → Modification time
app.conf       → Filename
```

---

## Lab 1 — Basic Listing

```bash
ls
```

---

## Lab 2 — Detailed Listing

```bash
ls -l
```

---

## Lab 3 — Hidden Files

```bash
ls -la
```

---

## Lab 4 — Human-Readable Sizes

```bash
ls -lh
```

---

## Lab 5 — Production Log Investigation

```bash
cd /var/log
ls -ltr
```

### Why `-ltr`?

```text
-l → detailed
-t → time sorted
-r → reverse
```

This is useful for identifying recently modified files.

---

# 7.3 `cd`

## Purpose

Change directory.

```bash
cd /var/log
```

---

## Lab 1

```bash
cd /tmp
pwd
```

## Lab 2

```bash
cd ..
pwd
```

## Lab 3

```bash
cd ~
pwd
```

## Lab 4

```bash
cd -
pwd
```

## Lab 5

Navigate:

```text
/opt
/opt/app
/opt/app/config
/opt/app/logs
```

using only `cd`.

---

# 7.4 `mkdir`

## Purpose

Create directories.

```bash
mkdir devops
```

### Important option

```bash
mkdir -p
```

`-p` creates parent directories when required.

---

## Lab 1

```bash
mkdir project
ls
```

## Lab 2

```bash
mkdir app logs config
ls
```

## Lab 3

```bash
mkdir -p project/application/config
```

## Lab 4 — Application Structure

```bash
mkdir -p shopsphere/{app,config,logs,backup}
```

Verify:

```bash
ls -R shopsphere
```

## Lab 5 — Production Directory

Create:

```text
/opt/company/app/
├── config
├── logs
├── releases
└── backup
```

Command:

```bash
sudo mkdir -p /opt/company/app/{config,logs,releases,backup}
```

---

# 7.5 `touch`

## Purpose

Create an empty file or update timestamps.

```bash
touch app.log
```

---

## Lab 1

```bash
touch file1.txt
```

## Lab 2

```bash
touch app.log error.log access.log
```

## Lab 3

```bash
mkdir logs
touch logs/application.log
```

## Lab 4

Create configuration files:

```bash
mkdir config
touch config/app.conf config/db.conf config/cache.conf
```

## Lab 5

Create a production-style structure:

```bash
mkdir -p application/{config,logs}
touch application/config/application.conf
touch application/logs/application.log
```

---

# 7.6 `cp`

## Purpose

Copy files/directories.

```bash
cp source destination
```

Important options:

```bash
-r
-p
-i
```

---

## Lab 1 — Copy File

```bash
touch app.conf
cp app.conf app.conf.backup
```

---

## Lab 2 — Copy Multiple Files

```bash
touch a.txt b.txt c.txt
mkdir backup
cp a.txt b.txt c.txt backup/
```

---

## Lab 3 — Copy Directory

```bash
mkdir -p application/config
touch application/config/app.conf

cp -r application application-backup
```

---

## Lab 4 — Preserve Attributes

```bash
cp -p app.conf app.conf.backup
```

---

## Lab 5 — Production Configuration Backup

Before modifying:

```bash
sudo cp /etc/nginx/nginx.conf \
/etc/nginx/nginx.conf.backup
```

### Team Lead Rule

> Never modify an important production configuration without knowing
> how you will recover it.

---

# 7.7 `mv`

## Purpose

Move or rename files/directories.

---

## Lab 1 — Rename

```bash
mv old.txt new.txt
```

## Lab 2 — Move File

```bash
mv app.log logs/
```

## Lab 3 — Move Directory

```bash
mv application /opt/
```

## Lab 4 — Rename Configuration

```bash
mv app.conf app.conf.old
```

## Lab 5 — Release Deployment

```text
releases/
├── app-1.0.0
├── app-1.1.0
└── current
```

Practice switching:

```bash
mv current current-old
mv app-1.1.0 current
```

Discuss why this pattern can support controlled deployments and why atomic deployment mechanisms are preferable in production.

---

# 7.8 `rm`

## Purpose

Remove files/directories.

```bash
rm file.txt
```

Important:

```bash
rm -r directory
rm -i file
```

### WARNING

```bash
rm -rf
```

is dangerous.

### Trainer Rule

> Never run `rm -rf` blindly in production.

---

## Lab 1

```bash
touch test.txt
rm test.txt
```

## Lab 2

```bash
touch a b c
rm a b c
```

## Lab 3

```bash
mkdir testdir
touch testdir/file
rm -r testdir
```

## Lab 4

```bash
touch important.txt
rm -i important.txt
```

## Lab 5 — Safe Cleanup

Find files first:

```bash
find /tmp -type f -name "*.log"
```

Then decide what can safely be removed.

---

# 7.9 `rmdir`

Removes empty directories.

```bash
rmdir directory
```

## 5 Labs

```bash
mkdir test
rmdir test
```

```bash
mkdir empty1 empty2
rmdir empty1 empty2
```

Create a file and observe:

```bash
mkdir test
touch test/file
rmdir test
```

Why does it fail?

Because the directory isn't empty.

---

# 7.10 `tree`

Displays directory structure.

```bash
tree
```

Example:

```text
project
├── app
├── config
│   └── application.conf
├── logs
│   └── application.log
└── backup
```

### 5 Labs

Practice:

```bash
tree project
tree -L 2 project
tree -a project
tree -d project
tree /etc 2>/dev/null | head
```

---

# 8. File Viewing Commands

---

# 8.1 `cat`

Displays file contents.

```bash
cat file.txt
```

## Lab 1

```bash
echo "Hello Linux" > file.txt
cat file.txt
```

## Lab 2

```bash
cat /etc/hostname
```

## Lab 3

```bash
cat file1 file2
```

## Lab 4

```bash
cat -n file.txt
```

## Lab 5

Create an application configuration and inspect it:

```bash
cat application.conf
```

### Trainer Note

For very large files, don't blindly use `cat`.

Use:

```bash
less
```

---

# 8.2 `less`

Useful for reading large files.

```bash
less application.log
```

Useful keys:

```text
Space → Next page
b     → Previous page
/word → Search
n     → Next match
q     → Quit
```

### 5 Labs

```bash
less /var/log/syslog
```

Search:

```text
/error
```

Next:

```text
n
```

Practice with:

* application logs
* access logs
* system logs
* configuration files
* large text files

---

# 8.3 `head`

Displays beginning of a file.

```bash
head file.txt
```

Options:

```bash
head -n 5 file.txt
```

### 5 Labs

```bash
head /var/log/syslog
head -n 5 /var/log/syslog
head -n 20 application.log
head -n 1 file.txt
head -n 50 access.log
```

---

# 8.4 `tail`

Displays the end of a file.

```bash
tail application.log
```

Important:

```bash
tail -f application.log
```

`-f` follows a changing file.

### Production Scenario

Application is running:

```text
User
 ↓
Load Balancer
 ↓
Application
 ↓
application.log
```

Trainer:

> "The user reports HTTP 500. Show me what the application is logging right now."

```bash
tail -f application.log
```

### 5 Labs

```bash
tail file.txt
tail -n 20 file.txt
tail -f application.log
tail -F application.log
tail -n 100 access.log
```

---

# 9. Searching Files and Data

---

# 9.1 `find`

One of the most important DevOps Linux commands.

Syntax:

```bash
find <path> <conditions>
```

---

## Lab 1 — Find by Name

```bash
find /tmp -name "*.log"
```

## Lab 2 — Find Files

```bash
find . -type f
```

## Lab 3 — Find Directories

```bash
find . -type d
```

## Lab 4 — Find Large Files

```bash
find /var -type f -size +100M 2>/dev/null
```

## Lab 5 — Production Log Search

```bash
find /var/log -type f -name "*.log" -mtime -1
```

Discuss:

```text
What files?
Where?
How old?
Why?
Can they be deleted?
```

---

# 9.2 `grep`

Search text.

```bash
grep "ERROR" application.log
```

Important options:

```bash
-i
-n
-r
-v
-c
```

---

## Lab 1

```bash
grep "ERROR" application.log
```

## Lab 2

```bash
grep -i "error" application.log
```

## Lab 3

```bash
grep -n "ERROR" application.log
```

## Lab 4

```bash
grep -r "database" /opt/app/
```

## Lab 5 — Incident Investigation

```bash
grep -i "error\|exception\|failed" application.log
```

Then:

```bash
grep -i "timeout" application.log
```

---

# 9.3 `wc`

Count lines, words and bytes.

```bash
wc file.txt
```

Examples:

```bash
wc -l application.log
wc -w file.txt
wc -c file.txt
```

### 5 Labs

Count:

* log lines
* configuration lines
* users
* errors
* HTTP requests

Example:

```bash
grep -i "ERROR" application.log | wc -l
```

---

# 9.4 `sort`

Sort text.

```bash
sort file.txt
```

Labs:

```bash
sort names.txt
sort -r names.txt
sort -n numbers.txt
sort -k2 data.txt
sort access.log
```

---

# 9.5 `uniq`

Remove/count adjacent duplicate lines.

```bash
sort names.txt | uniq
```

Count:

```bash
sort names.txt | uniq -c
```

Labs:

```bash
sort names.txt | uniq
sort names.txt | uniq -c
sort access.log | uniq -c
sort errors.log | uniq -c
sort users.txt | uniq -c
```

---

# 10. Redirection and Pipes

This is a **must-know DevOps concept**.

---

# 10.1 Standard Streams

```text
stdin  → 0
stdout → 1
stderr → 2
```

---

# 10.2 `>`

Overwrite output.

```bash
echo "hello" > file.txt
```

---

# 10.3 `>>`

Append output.

```bash
echo "new line" >> file.txt
```

---

# 10.4 `2>`

Redirect errors.

```bash
command 2> error.log
```

---

# 10.5 `|`

Pipe output from one command into another.

```bash
ps aux | grep nginx
```

---

## 5 Practical Labs

### Lab 1

```bash
ls > files.txt
cat files.txt
```

### Lab 2

```bash
echo "deployment successful" >> deployment.log
```

### Lab 3

```bash
find /root -name "*.log" 2>errors.log
```

### Lab 4

```bash
ps aux | grep java
```

### Lab 5 — Production Log Analysis

```bash
grep -i "ERROR" application.log | \
sort | \
uniq -c | \
sort -nr
```

Trainer asks:

> "What happened to the data after each pipe?"

Students must explain every stage.

---
