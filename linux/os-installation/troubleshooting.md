# Troubleshooting Guide

## Objective

Document issues encountered during Linux server provisioning and record the solutions used to resolve them.

This knowledge base helps during future deployments and production troubleshooting.

---

# Issue 1: Virtual Disk Not Detected

## Problem

During VM startup, the operating system installer could not detect any storage device.

---

## Symptoms

* No disk available during installation
* Installation cannot continue
* Storage section appears empty

---

## Root Cause

Virtual disk was not attached to the VM.

---

## Solution

Open:

```text
VirtualBox
   →
Settings
   →
Storage
```

Verify:

```text
Virtual Hard Disk Attached
```

If missing:

```text
Add Existing Disk
```

or

```text
Create New Virtual Disk
```

---

## Verification

Boot VM again.

Installer should detect:

```text
50 GB Virtual Disk
```

---

# Issue 2: Same IP Address on Multiple VMs

## Problem

Both Ubuntu and Rocky Linux received similar NAT-based IP addresses.

Example:

```text
10.0.2.15
```

---

## Symptoms

* Difficult SSH access
* Communication issues
* Networking confusion

---

## Root Cause

VirtualBox NAT Networking.

NAT assigns addresses internally.

---

## Solution

Change adapter mode:

```text
VirtualBox
   →
Settings
   →
Network
   →
Bridged Adapter
```

---

## Result

Ubuntu:

```text
10.90.121.74
```

Rocky Linux:

```text
10.90.121.214
```

Each VM receives its own network identity.

---

# Issue 3: SSH Connection Failure

## Problem

Unable to connect using SSH.

---

## Symptoms

```text
Connection Refused
```

or

```text
Connection Timed Out
```

---

## Root Cause

Possible reasons:

* SSH service stopped
* Wrong IP address
* Incorrect SSH configuration
* Firewall blocking access

---

## Solution

Verify SSH service:

Ubuntu:

```bash
sudo systemctl status ssh
```

Rocky Linux:

```bash
sudo systemctl status sshd
```

Start service:

```bash
sudo systemctl start ssh
```

or

```bash
sudo systemctl start sshd
```

---

## Verify IP Address

```bash
ip a
```

---

## Test Connectivity

```bash
ping <server-ip>
```

---

# Issue 4: Rocky Linux Sleep Issue

## Problem

Rocky Linux VM entered sleep mode automatically.

---

## Symptoms

* SSH disconnected
* VM became inaccessible
* Background tasks stopped

---

## Root Cause

Power management targets enabled.

---

## Solution

Disable sleep targets:

```bash
sudo systemctl mask sleep.target
sudo systemctl mask suspend.target
sudo systemctl mask hibernate.target
sudo systemctl mask hybrid-sleep.target
```

---

## Verification

Check status:

```bash
systemctl status sleep.target
```

Expected:

```text
masked
```

---

# Issue 5: No Internet Access

## Symptoms

```bash
ping 8.8.8.8
```

fails.

---

## Checks

Verify IP:

```bash
ip a
```

Verify route:

```bash
ip route
```

Verify DNS:

```bash
cat /etc/resolv.conf
```

---

## Solution

Restart networking.

Ubuntu:

```bash
sudo netplan apply
```

Rocky Linux:

```bash
sudo systemctl restart NetworkManager
```

---

# Issue 6: Hostname Not Updated

## Symptoms

Hostname change not reflected.

---

## Verify

```bash
hostnamectl
```

---

## Solution

Re-login:

```bash
logout
```

or

```bash
sudo reboot
```

---

# Issue 7: Time Synchronization Not Working

## Symptoms

Incorrect system time.

---

## Verify

```bash
timedatectl
```

---

## Solution

Enable NTP:

```bash
sudo timedatectl set-ntp true
```

Restart service:

```bash
sudo systemctl restart systemd-timesyncd
```

---

# Troubleshooting Commands Cheat Sheet

## System Information

```bash
hostnamectl
uname -r
```

---

## Networking

```bash
ip a
ip route
ping 8.8.8.8
```

---

## Storage

```bash
lsblk
df -h
```

---

## Memory

```bash
free -h
```

---

## Services

```bash
systemctl status ssh
systemctl status sshd
```

---

## Time

```bash
timedatectl
```

---

# Lessons Learned

* Always verify storage before installation.
* Use Bridged Adapter for Linux labs.
* Ensure SSH is running before remote access.
* Disable sleep mode on lab servers.
* Verify networking before troubleshooting applications.
* Keep system time synchronized.

---

# Learning Outcome

Successfully identified and resolved common Linux server provisioning issues involving:

* Storage
* Networking
* SSH
* Power Management
* Hostname Configuration
* Time Synchronization

This troubleshooting knowledge forms the foundation for Linux Administration, Docker, Kubernetes, and DevOps operations.
