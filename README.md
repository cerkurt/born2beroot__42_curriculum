This project has been created as part of the 42 curriculum by **cerkurt**.

---

## Description

**Born2beRoot** is a system administration project focused on **virtualization
Linux system configuration and security fundamentals**.

The goal of this project is to create a **secure virtual server** using
**VirtualBox** and a minimal Linux distribution
(**Debian** or **Rocky Linux**), while following strict rules regarding:

- system security
- user and permission management
- disk partitioning with LVM
- firewall configuration
- automated system monitoring

Unlike coding projects, Born2beRoot focuses on
**understanding how a Linux system works internally**.

---

## Project Objectives

By completing this project, I learned how to:

- Create and manage a **virtual machine**
- Install and configure a **minimal Linux server**
- Use **LVM (Logical Volume Manager)** with encrypted partitions
- Configure **SSH**, **UFW**, and system security rules
- Implement a **strong password policy**
- Manage users, groups, and sudo permissions
- Write a **Bash monitoring script**
- Understand core Linux concepts (TTY, AppArmor, LVM, MAC, etc.)

---

## Operating System Choice

### Debian (Stable)

I chose **Debian** for this project.

**Pros**
- Very stable and lightweight
- Simple package management with `apt`
- Uses **AppArmor**, which is easier to understand and manage
- Recommended for beginners in system administration

**Cons**
- Conservative software versions
- Less enterprise-oriented compared to Rocky Linux

---

## Security Configuration Overview

### Mandatory Security Measures

- No graphical interface (CLI only)
- SSH enabled on **port 4242**
- Root login via SSH **disabled**
- Firewall (**UFW**) enabled at startup
- Only port **4242** open
- **AppArmor** enabled at startup

---

## Password Policy

The system enforces a strong password policy:

- Password expires every **30 days**
- Minimum length: **10 characters**
- Must contain:
  - at least one uppercase letter
  - at least one lowercase letter
  - at least one number
- No more than 3 consecutive identical characters
- Username must not be part of the password
- Root password follows the same policy

---

## User & Sudo Configuration

- Root user exists by default
- A user with my **42 login** is created
- The user belongs to:
  - `user42`
  - `sudo`

### Sudo Rules

- Maximum **3 authentication attempts**
- Custom error message on incorrect password
- All sudo actions (input/output) are logged in `/var/log/sudo/`
- TTY mode enabled
- Restricted executable paths

---

## Disk Partitioning & LVM

The system uses **encrypted LVM partitions**.

### Why LVM?

- Logical volumes can be resized without reinstalling
- Storage can be extended or reorganized easily
- Commonly used in real production servers

Example logical volumes:
- `/`
- `/home`
- `/var`
- `/tmp`
- `/srv`
- `swap`

---

## Monitoring Script (`monitoring.sh`)

A Bash script runs **every 10 minutes** at startup and broadcasts system
information using `wall`.

Displayed information:
- OS architecture and kernel version
- Number of physical CPUs
- Number of virtual CPUs
- RAM usage and percentage
- Disk usage and percentage
- CPU load
- Last reboot date
- LVM status
- Active TCP connections
- Logged-in users
- IP and MAC address
- Number of sudo commands executed

---

## Repository Content

```text
.
├── README.md
└── b2br_testsheet
