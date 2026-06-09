# Linux Kernel

## What is Linux Kernel?

The Linux Kernel is the core component of the Linux Operating System.

It acts as a bridge between:

```text
Applications
     ↓
Linux Kernel
     ↓
Hardware
```

Applications cannot directly access hardware.

All requests must pass through the Kernel.

---

## Linux Architecture

```text
User
 ↓
Applications
 ↓
Shell (bash)
 ↓
System Calls
 ↓
Linux Kernel
 ↓
Hardware
```

Examples of Hardware:

* CPU
* RAM
* Disk
* Network Interface Card (NIC)
* USB Devices

Everything eventually reaches the Linux Kernel.

---

## Why is Kernel Needed?

Without Kernel:

* CPU cannot be managed
* Memory cannot be allocated
* Files cannot be stored
* Network communication cannot happen
* Applications cannot execute

Linux cannot function without the Kernel.

---

## Real Life Example

Think of a company:

```text
CEO = Kernel

Employees = Applications

Resources = CPU, RAM, Disk, Network
```

Employees cannot directly take resources.

The CEO allocates resources.

Similarly, the Kernel manages all system resources.

---

## Major Responsibilities of the Kernel

### 1. CPU Management

Question:

Who gets CPU time?

Examples:

* Chrome
* VS Code
* Docker
* SSH

The Kernel Scheduler allocates CPU time.

```text
Process A → 10ms
Process B → 10ms
Process C → 10ms
```

---

### 2. Memory Management

Question:

Who gets RAM?

Examples:

* Docker Containers
* Kubernetes Pods
* Nginx
* PostgreSQL

The Kernel allocates and manages memory.

---

### 3. Storage Management

Question:

Where should files be stored?

Example:

```bash
touch test.txt
```

The Kernel:

* Allocates storage blocks
* Updates filesystem metadata
* Writes data to disk

---

### 4. Network Management

Question:

How does a packet reach another server?

The Kernel manages:

* TCP/IP
* UDP
* ARP
* Routing
* DNS Requests

Example:

```bash
ping google.com
```

---

### 5. Process Management

Question:

Which process should run?

Examples:

* systemd
* sshd
* dockerd
* containerd
* bash

The Kernel schedules and manages all processes.

---

## Kernel Components

### Scheduler

Responsible for:

* CPU Allocation
* Process Scheduling

Command:

```bash
top
```

---

### Memory Manager

Responsible for:

* RAM Allocation
* Swap
* Buffers
* Cache

Commands:

```bash
free -h
cat /proc/meminfo
```

---

### Filesystem Manager

Responsible for:

* Reading Files
* Writing Files
* Mounting Filesystems

Commands:

```bash
df -h
mount
```

---

### Network Stack

Responsible for:

* TCP
* UDP
* IP
* ARP

Commands:

```bash
ip a
ip route
```

---

### Device Drivers

Responsible for:

* Keyboard
* Mouse
* Disk
* NIC
* USB Devices

Command:

```bash
dmesg
```

---

## User Space vs Kernel Space

### User Space

Applications run here.

Examples:

* VS Code
* Chrome
* kubectl
* Docker CLI
* bash

Users interact with User Space.

---

### Kernel Space

Core operating system functions run here.

Examples:

* Scheduler
* Memory Manager
* Filesystem Manager
* Network Stack
* Device Drivers

Users cannot directly access Kernel Space.

---

## System Calls

Applications communicate with the Kernel through System Calls.

Example:

```bash
ls
```

Flow:

```text
ls
 ↓
System Call
 ↓
Kernel
 ↓
Filesystem
 ↓
Output
```

---

## Important Commands

### Kernel Version

```bash
uname -r
```

Example:

```text
6.8.0-124-generic
```

---

### Detailed Kernel Information

```bash
cat /proc/version
```

Source:

```text
/proc/version
```

---

### Kernel Messages

```bash
dmesg
```

Source:

```text
Kernel Ring Buffer
```

---

### Kernel Logs

```bash
journalctl -k
```

---

## Important Source Files

| Information        | Source        |
| ------------------ | ------------- |
| Kernel Version     | /proc/version |
| CPU Information    | /proc/cpuinfo |
| Memory Information | /proc/meminfo |
| Mount Information  | /proc/mounts  |
| Kernel Logs        | journalctl -k |
| Driver Messages    | dmesg         |

---

## Healthy State

* Supported Kernel Version
* No Kernel Panic
* No Driver Errors
* No Hardware Errors
* Stable Performance

Example:

```text
6.8.0-124-generic
```

---

## Unhealthy State

* Kernel Panic
* Driver Failure
* Unsupported Kernel
* Hardware Errors
* Frequent Reboots

---

## Production Relevance

Docker depends heavily on Linux Kernel.

Kernel Features used by Docker:

* Namespaces
* Cgroups
* OverlayFS

Without these features:

```text
Containers cannot run.
```

---

## Docker Architecture

```text
Docker CLI
 ↓
Docker Daemon
 ↓
Linux Kernel
 ↓
Hardware
```

---

## Kubernetes Relevance

Every Kubernetes Node contains:

```text
Linux
+
Kernel
+
Container Runtime
+
Kubelet
```

Kubernetes depends on:

* Namespaces
* Cgroups
* Networking
* Storage

All provided by the Linux Kernel.

---

## Production Incident Example

### Incident

Container restarting continuously.

### Investigation

```bash
uname -r
dmesg
journalctl -k
```

### Finding

Kernel feature missing.

### Root Cause

Unsupported Kernel Version.

### Resolution

Upgrade Kernel.

---

## Troubleshooting Flow

### Step 1

```bash
uname -r
```

Check Kernel Version.

### Step 2

```bash
cat /proc/version
```

Check detailed Kernel information.

### Step 3

```bash
dmesg | tail -50
```

Check recent Kernel messages.

### Step 4

```bash
journalctl -k -n 50
```

Check Kernel logs.

### Step 5

```bash
dmesg | grep -i error
```

Check for Kernel-related errors.

---

## What Files Provide This Information?

| Information        | Source        |
| ------------------ | ------------- |
| Kernel Version     | /proc/version |
| CPU Details        | /proc/cpuinfo |
| Memory Details     | /proc/meminfo |
| Filesystem Details | /proc/mounts  |

---

## Why Production Cares?

* Docker depends on Kernel features.
* Kubernetes depends on Kernel features.
* Networking depends on Kernel networking stack.
* Storage depends on Kernel filesystem support.
* Security depends on Kernel security mechanisms.

---

## What Happens If This Is Wrong?

### Unsupported Kernel

* Docker failures
* Kubernetes failures
* Driver incompatibilities

### Kernel Panic

* Server outage
* Application downtime

### Driver Failure

* Hardware not detected
* Network issues
* Storage issues

---

## Quick Revision

```text
Kernel = Brain of Linux

Architecture:

User
 ↓
Application
 ↓
Shell
 ↓
System Call
 ↓
Kernel
 ↓
Hardware

Responsibilities:

1. CPU Management
2. Memory Management
3. Storage Management
4. Network Management
5. Process Management

Docker Uses:

Namespaces
Cgroups
OverlayFS

Containers share Host Kernel.

Important Commands:

uname -r
cat /proc/version
dmesg
journalctl -k
```

---

## Interview Questions

1. What is Kernel?
2. What are Kernel responsibilities?
3. What is User Space?
4. What is Kernel Space?
5. What is a System Call?
6. What command shows Kernel Version?
7. Which file stores Kernel information?
8. Why does Docker depend on Linux Kernel?
9. Do Containers have their own Kernel?
10. What is the difference between User Space and Kernel Space?

---

## Lessons Learned

1. Kernel is the brain of Linux.
2. Every command eventually reaches the Kernel.
3. Docker depends on Kernel features.
4. Kubernetes depends on Kernel features.
5. Containers share the Host Kernel.
6. Kernel manages CPU, Memory, Storage, Networking and Processes.
