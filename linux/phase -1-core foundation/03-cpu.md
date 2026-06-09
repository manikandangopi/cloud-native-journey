# CPU (Central Processing Unit)

## What is CPU?

CPU (Central Processing Unit) is the component responsible for executing instructions.

Think of CPU as:

```text
CPU = Worker of the Computer

Kernel = Manager
CPU = Worker
Process = Job
```

Every command eventually reaches the CPU.

Example:

```bash
ls
```

Flow:

```text
User
 ↓
Shell
 ↓
Kernel
 ↓
CPU
 ↓
Execute Instruction
 ↓
Output
```

---

# CPU Architecture

```text
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
CPU Scheduler
 ↓
CPU Core
 ↓
Instruction Execution
```

---

# Why CPU is Needed?

Without CPU:

* No Linux
* No Docker
* No Kubernetes
* No Applications
* No Command Execution

CPU performs actual work.

---

# Real Production Example

```text
Developer
 ↓
Docker Container
 ↓
Linux Kernel
 ↓
CPU
```

When a user accesses:

```text
https://company.com
```

Request reaches:

```text
Nginx
 ↓
Application
 ↓
Kernel
 ↓
CPU
```

CPU executes instructions and sends response.

---

# Major Responsibilities of CPU

## 1. Execute Instructions

Examples:

```bash
ls
pwd
mkdir project
```

CPU executes every instruction.

---

## 2. Run Processes

Examples:

* Chrome
* VS Code
* Docker
* SSH
* kubectl

CPU executes process instructions.

---

## 3. CPU Scheduling

Question:

Who gets CPU time?

Answer:

```text
Linux Kernel Scheduler
```

Example:

```text
Process A → 10 ms
Process B → 10 ms
Process C → 10 ms
```

This is called CPU Scheduling.

---

## 4. Context Switching

CPU rapidly switches between processes.

Example:

```text
VS Code
Docker
Chrome
Terminal
```

This creates the illusion that everything runs simultaneously.

---

# CPU Components

## CPU Core

Your Machine:

```text
Core(s) per socket: 2
```

Meaning:

```text
Core 1
Core 2
```

Each core executes instructions.

---

## CPU Thread

Your Machine:

```text
Thread(s) per core: 1
```

Thread = Execution path inside a CPU core.

---

## CPU Cache

Your Machine:

```text
L1 Cache
L2 Cache
L3 Cache
```

Think:

```text
RAM = Warehouse

L3 Cache = Room
L2 Cache = Desk
L1 Cache = Hand
```

Closer to CPU = Faster access.

---

# Actual Machine Verification

## CPU Overview

### Command

```bash
lscpu
```

### Output

```text
Architecture: x86_64
CPU(s): 2
Model name: Intel Core i7-10750H CPU @ 2.60GHz
Hypervisor vendor: KVM
Virtualization type: full
```

### Analysis

#### Architecture

```text
x86_64
```

Meaning:

```text
64-bit CPU Architecture
```

Production Importance:

* Docker Support
* Kubernetes Support
* Enterprise Software Compatibility

---

#### CPU Count

```text
2
```

Verification:

```bash
nproc
```

Output:

```text
2
```

Linux can schedule work on 2 CPUs.

---

#### CPU Model

```text
Intel Core i7-10750H
```

Provides:

* Virtualization Support
* Container Support
* Performance Optimization

---

# Important Commands

## CPU Overview

```bash
lscpu
```

---

## CPU Count

```bash
nproc
```

---

## Detailed CPU Information

```bash
cat /proc/cpuinfo
```

---

## Real-Time CPU Monitoring

```bash
top
```

---

## Load Average

```bash
uptime
```

---

# Important Source Files

| Information      | Source        |
| ---------------- | ------------- |
| CPU Information  | /proc/cpuinfo |
| CPU Statistics   | /proc/stat    |
| Load Information | /proc/loadavg |

---

# What Files Provide This Information?

## CPU Information

```text
/proc/cpuinfo
```

Contains:

* CPU Model
* Vendor
* CPU MHz
* Core Count
* Cache Information

---

## CPU Statistics

```text
/proc/stat
```

Contains:

* CPU Usage
* User Time
* System Time
* Idle Time

---

# Load Average

## Command

```bash
uptime
```

Example:

```text
load average: 0.00 0.00 0.00
```

Meaning:

```text
1 Minute Load
5 Minute Load
15 Minute Load
```

Your CPU Count:

```text
2 CPUs
```

Healthy Examples:

```text
Load = 0.50
Load = 1.00
Load = 1.50
```

Warning:

```text
Load = 3.00
Load = 4.00
```

Critical:

```text
Load = 10.00+
```

---

# Healthy State

* CPU detected
* Architecture valid
* CPU utilization below 70%
* Load Average lower than CPU Count
* System responsive

---

# Unhealthy State

* CPU above 90%
* High Load Average
* Application Slow
* API Timeout
* Pod Timeout
* Container Performance Issues

---

# Production Relevance

CPU directly impacts:

* Docker Containers
* Kubernetes Pods
* Databases
* APIs
* Web Servers

Without CPU:

```text
No Work Gets Executed
```

---

# Docker Relevance

Docker Containers consume CPU resources.

```text
Container
 ↓
Docker
 ↓
Kernel
 ↓
CPU
```

High CPU causes:

* Slow Containers
* Application Latency
* Container Restart Issues

---

# Kubernetes Relevance

Every Pod requires CPU.

Example:

```yaml
resources:
  requests:
    cpu: "250m"
  limits:
    cpu: "500m"
```

Kubernetes Scheduler places Pods based on available CPU resources.

---

# Production Incident Example

## Incident

Application Response Time Increased.

### Investigation

```bash
top
```

### Finding

```text
CPU Usage = 98%
```

### Root Cause

```text
Runaway Process
Infinite Loop
```

### Resolution

```bash
ps -ef
kill -9 <PID>
```

---

# Troubleshooting Flow

## Step 1

```bash
lscpu
```

Verify CPU count and architecture.

---

## Step 2

```bash
nproc
```

Verify available processors.

---

## Step 3

```bash
top
```

Check CPU utilization.

---

## Step 4

```bash
uptime
```

Check load average.

---

## Step 5

```bash
cat /proc/cpuinfo
```

Verify detailed CPU information.

---

# Interview Questions

1. What is CPU?
2. What is CPU Scheduling?
3. Difference between Core and Thread?
4. What is Context Switching?
5. What is CPU Cache?
6. What command shows CPU information?
7. Which file stores CPU information?
8. What is Load Average?
9. What happens when CPU reaches 100%?
10. How does Linux allocate CPU to processes?

---

# Quick Revision

```text
CPU = Brain that executes instructions

Architecture:

User
 ↓
Application
 ↓
Kernel
 ↓
CPU

Source Files:

/proc/cpuinfo
/proc/stat
/proc/loadavg

Commands:

lscpu
nproc
cat /proc/cpuinfo
top
uptime

Responsibilities:

1. Execute Instructions
2. Run Processes
3. CPU Scheduling
4. Context Switching

Production Issues:

High CPU
Slow Applications
API Timeout
Pod Timeout

Healthy:

CPU < 70%
Load Average < CPU Count

Unhealthy:

CPU > 90%
Load Average > CPU Count
```

---

# Lessons Learned

1. CPU executes all instructions in Linux.
2. Every command eventually reaches the CPU.
3. Linux Kernel Scheduler allocates CPU time.
4. CPU Cores execute workloads.
5. CPU Cache improves performance.
6. Docker Containers consume CPU.
7. Kubernetes Pods consume CPU.
8. Load Average is a critical production metric.
9. High CPU causes latency and performance issues.
10. CPU is the execution engine of the Operating System.
