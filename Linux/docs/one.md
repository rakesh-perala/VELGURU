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
