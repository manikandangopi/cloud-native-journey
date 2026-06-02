# Linux Mastery Document

## Day 1 - Linux Server Provisioning (Production Level Understanding)

### Objective

The objective of Day 1 was to build a Linux Server Lab environment and understand the fundamental components required for operating a Linux system in a production environment.

### Tasks Performed

* Setting up virtualization
* Installing Linux operating systems
* Configuring network connectivity
* Configuring system hostname
* Synchronizing system time
* Enabling secure remote access using SSH for VS Code
* Managing servers remotely through development tools

---

# Linux Fundamentals

## 1. What is Linux?

Linux is an open-source, Unix-like operating system family based on the Linux Kernel.

### Simple Definition

Linux = Heart of the Operating System (Kernel)

### Facts

* Creator: Linus Benedict Torvalds
* First Release: 1991

---

## 2. What is an Operating System (OS)?

An Operating System (OS) is system software that manages computer hardware and allows applications to run.

### Responsibilities

* CPU Management
* Memory Management (RAM)
* Disk and File System Management
* Device Management
* User and Security Management

### Examples

* Linux
* Windows
* macOS
* Unix

---

## 3. What is the Kernel?

The Kernel is the core component of an operating system.

### Responsibilities

* CPU Management
* Memory Management
* Disk Management
* Network Management
* Device Management

### What Kernel Does Not Provide

* ls command
* cp command
* Bash shell
* GUI

These are userspace tools.

---

## 4. Linux Kernel Responsibilities

| Area     | Kernel Role             |
| -------- | ----------------------- |
| CPU      | Process Scheduling      |
| Memory   | RAM Management & Paging |
| Disk     | Block Device Management |
| Network  | TCP/IP Stack            |
| Devices  | Driver Management       |
| Security | System Calls            |

---

## 5. Kernel Features Used by Containers

| Feature       | Purpose              |
| ------------- | -------------------- |
| Namespaces    | Container Isolation  |
| Cgroups       | CPU & Memory Control |
| OverlayFS     | Container Filesystem |
| Network Stack | Container Networking |

---

## 6. Commands for Kernel Inspection

```bash
uname -r
uname -a
lsmod
dmesg
cat /proc/version
cat /proc/cpuinfo
cat /proc/meminfo
cat /proc/modules
```

---

## 7. GNU Project

GNU stands for:

GNU's Not Unix

Started by Richard Stallman in 1983.

### GNU Provides

* Bash Shell
* ls
* cp
* mv
* grep
* awk
* sed
* gcc compiler
* glibc libraries
* Core utilities

Without GNU tools, the Linux Kernel alone is not a complete operating system.

---

## 8. GNU + Linux = GNU/Linux

| Component | Provided By |
| --------- | ----------- |
| Kernel    | Linux       |
| Shell     | GNU         |
| Commands  | GNU         |
| Libraries | GNU         |
| License   | GPL         |

---

## 9. Linux Boot Process

### Boot Flow

1. Power On
2. BIOS / UEFI
3. GRUB Bootloader
4. Linux Kernel
5. Initramfs
6. systemd
7. System Services
8. Login Shell

### Simple Flow

BIOS → GRUB → Kernel → Initramfs → systemd → Services → User Login

---

## 10. Bash and Linux CLI

Bash stands for:

Bourne Again Shell

### Workflow

User → Bash → System Call → Kernel → Hardware

Example:

```bash
ls
```

* Bash parses command
* Kernel accesses filesystem
* Output displayed to user

---

## 11. Linux Distributions

A Linux Distribution consists of:

* Linux Kernel
* GNU Tools
* Package Manager
* Configuration Files
* Additional Software

### Simple Definition

Linux Kernel alone is not a complete OS.

Distribution = Complete Usable Operating System

---

## 12. Linux Distribution Components

1. Linux Kernel
2. GNU Tools
3. Package Manager
4. Init System (systemd)
5. Configuration Files
6. Networking & Security Tools

---

## 13. Major Linux Distribution Families

### Red Hat Family

Examples:

* RHEL
* Rocky Linux
* AlmaLinux
* CentOS Stream

Package Managers:

```bash
dnf
rpm
```

Use Cases:

* Enterprise Servers
* Production Datacenters
* Banking
* Telecom

---

### Debian Family

Examples:

* Debian
* Ubuntu
* Linux Mint

Package Managers:

```bash
apt
dpkg
```

Use Cases:

* Cloud Computing
* DevOps
* Containers
* Automation

---

### Arch Family

Examples:

* Arch Linux
* Manjaro

Package Manager:

```bash
pacman
```

Use Cases:

* Advanced Users
* Custom Linux Environments
