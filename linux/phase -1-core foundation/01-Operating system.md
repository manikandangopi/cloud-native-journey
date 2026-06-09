# Operating System

## What is an Operating System?

An Operating System (OS) is software that acts as a bridge between users, applications, and hardware.

```text
User
 ↓
Application
 ↓
Operating System
 ↓
Hardware
```

The Operating System manages hardware resources and provides services to applications.

---

## Without an Operating System

Without an OS:

- CPU cannot be managed
- Memory cannot be allocated
- Files cannot be stored
- Network cannot communicate
- Applications cannot execute

---

## Architecture Flow

```text
User
 ↓
Application
 ↓
Operating System
 ↓
Kernel
 ↓
Hardware

CPU
RAM
Disk
NIC
```

Everything eventually reaches the Kernel.

---

## Real Production Example

```text
Developer
 ↓
Docker
 ↓
Linux
 ↓
CPU
RAM
Disk
NIC
```

A developer runs a Docker container.

Docker requests resources from Linux.

Linux uses the Kernel to communicate with hardware.

---

## Why is an Operating System Needed?

Hardware understands only:

- Electrical Signals
- Binary Data

Humans use:

- Commands
- Applications
- GUI

The Operating System converts human requests into machine operations.

Example:

```bash
mkdir project
```

The OS converts this request into filesystem operations and creates the directory.

---

## Major Responsibilities of an Operating System

### 1. CPU Management

Question:

Who gets CPU time?

Examples:

- Chrome
- VS Code
- Docker
- SSH

The Operating System schedules CPU usage.

---

### 2. Memory Management

Question:

Who gets RAM?

Examples:

- Docker Container
- Nginx
- VS Code

The Operating System allocates memory to processes.

---

### 3. Storage Management

Question:

Where should files be stored?

Example:

```bash
touch note.txt
```

The Operating System allocates storage blocks and manages filesystems.

---

### 4. Network Management

Question:

How should packets travel?

Example:

```bash
ping google.com
```

The Operating System manages:

- Routing
- DNS
- TCP/IP
- ARP

---

### 5. Security Management

The Operating System manages:

- Users
- Groups
- Permissions
- Authentication
- Authorization

Example:

```bash
sudo apt update
```

---

## Types of Operating Systems

| Desktop | Server |
|----------|----------|
| Windows | Ubuntu Server |
| macOS | Rocky Linux |
| Ubuntu Desktop | RHEL |

---

## Linux Distribution

A Linux Distribution is a complete operating system built around the Linux Kernel.

### Ubuntu Contains

- Linux Kernel
- GNU Tools
- Package Manager
- Applications

### Rocky Linux Contains

- Linux Kernel
- Enterprise Packages
- Enterprise Tools

---

## Important Files

| Information | File |
|------------|------|
| OS Information | /etc/os-release |
| Hostname | /etc/hostname |
| Kernel Information | /proc/version |

---

## Verification Commands

### Check Operating System

```bash
cat /etc/os-release
```

### Check Hostname

```bash
hostnamectl
```

### Check Kernel Information

```bash
uname -a
```

### Check Distribution

```bash
lsb_release -a
```

---

## Actual Verification Output

### OS Verification

```bash
cat /etc/os-release
```

Output:

```text
PRETTY_NAME="Ubuntu 24.04.4 LTS"
VERSION_ID="24.04"
VERSION_CODENAME=noble
```

Source File:

```text
/etc/os-release
```

Status:

```text
PASS
```

---

### Hostname Verification

```bash
hostnamectl
```

Output:

```text
Static hostname: dev-k8s-ubuntulinux-01
Operating System: Ubuntu 24.04.4 LTS
Kernel: Linux 6.8.0-124-generic
Architecture: x86_64
Virtualization: Oracle VirtualBox
```

Source File:

```text
/etc/hostname
```

Status:

```text
PASS
```

---

### Kernel Verification

```bash
uname -a
```

Output:

```text
Linux dev-k8s-ubuntulinux-01 6.8.0-124-generic
```

Source File:

```text
/proc/version
```

Status:

```text
PASS
```

---

### Distribution Verification

```bash
lsb_release -a
```

Output:

```text
Distributor ID: Ubuntu
Description: Ubuntu 24.04.4 LTS
Release: 24.04
Codename: noble
```

Source File:

```text
/etc/os-release
```

Status:

```text
PASS
```

---

## Production Incident Example

### Incident

Docker Installation Failed

### Investigation

```bash
cat /etc/os-release
```

### Finding

Unsupported Linux Distribution

### Root Cause

Docker package not available for the current OS version.

### Resolution

Install a supported Linux distribution and version.

---

## Kubernetes Relevance

Every Kubernetes Node is a Linux Server.

```text
Worker Node
 └─ Linux
     └─ Container Runtime

Master Node
 └─ Linux
     └─ Kubernetes Control Plane
```

---

## What Files Provide This Information?

| Information | Source File |
|------------|-------------|
| OS Version | /etc/os-release |
| Hostname | /etc/hostname |
| Kernel Version | /proc/version |

---

## Why Production Cares?

- Docker requires supported Operating Systems
- Kubernetes requires supported Operating Systems
- Security updates depend on OS support
- Monitoring depends on proper hostname configuration
- Enterprise applications require certified OS versions

---

## What Happens If This Is Wrong?

### Wrong OS Version

- Docker Installation Failure
- Kubernetes Installation Failure
- Security Risks
- Missing Updates

### Wrong Hostname

- Monitoring Confusion
- Logging Confusion
- Inventory Issues
- Kubernetes Node Identification Problems

### Unsupported Kernel

- Docker Issues
- Networking Problems
- Container Runtime Failures
- Security Vulnerabilities

---

## Quick Revision

```text
Operating System = Foundation of Linux

Purpose:
Manage Hardware Resources

Architecture:

User
 ↓
Application
 ↓
Operating System
 ↓
Hardware

Responsibilities:

1. CPU Management
2. Memory Management
3. Storage Management
4. Network Management
5. Security Management

Important Files:

/etc/os-release
/etc/hostname
/proc/version

Important Commands:

cat /etc/os-release
hostnamectl
uname -a
lsb_release -a

Production Importance:

Docker
Kubernetes
Helm
Terraform

depend on OS compatibility.
```

---

## Interview Questions

1. What is an Operating System?
2. What are the major responsibilities of an Operating System?
3. What is a Linux Distribution?
4. What is the difference between Ubuntu and Linux?
5. Which file stores OS information?
6. How do you verify OS version in Linux?

---

## Lessons Learned

1. Operating System is the foundation of Linux.

2. Ubuntu is a Linux Distribution.

3. Docker and Kubernetes require supported Operating Systems.

4. OS manages CPU, Memory, Storage, Networking and Security.

5. Always verify OS version before software installation.

6. Production servers depend on OS stability and support.