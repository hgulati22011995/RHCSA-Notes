# Linux Fundamentals, RHEL Installation, Boot Process & Filesystem

---

# 📖 Module 1: History of UNIX and Linux

## UNIX Developers

Dennis Ritchie and Ken Thompson developed UNIX at Bell Labs in 1968.

### Key Milestones

| Year  | Event                                                  |
| ----- | ------------------------------------------------------ |
| 1968  | UNIX developed at Bell Labs                            |
| 1971  | Linux concept evolved from UNIX principles             |
| Later | Linux became an open-source UNIX-like operating system |

---

# 🐧 What is Linux?

Linux is an:

✅ Open Source Operating System

✅ Multi-user Operating System

✅ Multi-tasking Operating System

✅ Secure & Stable Platform

✅ Hardware Independent

### Why Linux is Popular?

* Free to use
* Highly customizable
* Better performance
* Strong security
* Supports multiple file systems
* Excellent process management

---

# UNIX vs Linux

| UNIX                   | Linux                      |
| ---------------------- | -------------------------- |
| Proprietary            | Open Source                |
| Expensive              | Free                       |
| Vendor controlled      | Community controlled       |
| Limited customization  | Highly customizable        |
| Older operating system | UNIX-like operating system |

### GNU Meaning

**GNU = GNU's Not UNIX**

GNU provides tools and utilities that work with the Linux Kernel.

---

# Linux Distributions

## Debian-Based Distributions

* Ubuntu
* Debian
* Linux Mint

## Red Hat-Based Distributions

* RHEL (Red Hat Enterprise Linux)
* CentOS
* Fedora
* Rocky Linux
* AlmaLinux

---

# 🌎 Where Linux is Used?

Linux is everywhere:

* Servers
* Cloud Platforms
* Smartphones (Android)
* Smart Watches
* Super Computers
* Gaming Consoles
* NASA Systems
* Embedded Devices
* Laptops & Desktops

---

# 🧠 Linux Architecture

```text
+----------------+
|     User       |
+----------------+
        |
        v
+----------------+
|     Shell      |
+----------------+
        |
        v
+----------------+
|    Kernel      |
+----------------+
        |
        v
+----------------+
|   Hardware     |
+----------------+
```

---

## Kernel

Kernel is the heart of Linux.

### Responsibilities

* Memory Management
* Process Management
* Device Management
* File System Management
* CPU Scheduling

Kernel acts as a bridge between user and hardware.

---

## Shell

Shell is the command interpreter.

Examples:

* Bash
* Ksh
* Zsh
* Sh

Windows equivalent:

* Command Prompt (CMD)
* PowerShell

---

# 🔐 Linux Login

To access a Linux machine:

You need:

* Username
* Password

Login can be:

### Local Login

Directly from server console.

### Remote Login

Using:

* SSH
* PuTTY
* MobaXterm

---

# ⚡ Linux Booting Process

## Definition

Booting is the process of loading operating system files from disk into RAM.

---

## Step 1: POST

### POST = Power On Self Test

When system starts:

* Motherboard checks hardware
* RAM verification
* CPU verification
* Peripheral verification

If successful → control goes to BIOS/UEFI

---

## Step 2: BIOS / UEFI

### BIOS

Basic Input Output System

Responsibilities:

* Detect hardware
* Select boot device
* Start operating system loading process

### UEFI

Modern replacement for BIOS.

Advantages:

* Faster boot
* Mouse support
* Better security
* GPT support

---

## Step 3: CMOS

Stores:

* Date
* Time
* BIOS settings
* Hardware configuration

Powered by CMOS battery.

---

## Step 4: MBR

### Master Boot Record

Located:

```text
First Sector of Disk
```

Size:

```text
512 Bytes
```

Responsibilities:

* Partition information
* Boot loader location

---

## Step 5: GRUB

### GRUB

Grand Unified Boot Loader

Functions:

* Loads Linux Kernel
* Provides boot menu
* Allows rescue mode

Older bootloader:

```text
LILO
(Linux Loader)
```

---

## Step 6: Initramfs

Temporary file system loaded into RAM.

Purpose:

* Locate root filesystem
* Load necessary drivers
* Prepare system startup

---

## Step 7: Kernel Loading

Kernel loads:

* Memory management
* Device drivers
* Hardware modules

---

## Step 8: System Initialization

System services start.

Examples:

* SSH
* Network
* Firewall
* Logging services

---

# Linux Run Levels / Targets

| Run Level | Purpose                      |
| --------- | ---------------------------- |
| 0         | Shutdown                     |
| 1         | Single User Mode             |
| 2         | Multi User (without network) |
| 3         | Multi User (with network)    |
| 4         | Custom                       |
| 5         | GUI Mode                     |
| 6         | Reboot                       |

---

# 📁 Linux File System Structure

Root Directory:

```text
/
```

Known as:

* Root Directory
* Parent of all Directories

---

## Important Directories

### /bin

Essential user commands.

Examples:

```bash
ls
cp
mv
cat
```

---

### /etc

Configuration files.

Examples:

```bash
/etc/passwd
/etc/hosts
/etc/fstab
```

---

### /sbin

Administrative commands.

Examples:

```bash
fdisk
shutdown
reboot
```

---

### /usr

Read-only user applications.

Contains:

```text
/usr/bin
/usr/sbin
/usr/lib
```

---

### /dev

Device files.

Examples:

```text
/dev/sda
/dev/sdb
/dev/null
```

---

### /home

User home directories.

Example:

```text
/home/himanshu
```

---

### /lib

System libraries.

Kernel modules are stored here.

---

### /tmp

Temporary files.

Automatically cleaned.

---

### /opt

Optional software installations.

Example:

```text
Oracle
VMware
```

---

### /proc

Virtual filesystem.

Contains:

* Process information
* Kernel information

---

### /root

Home directory of root user.

```text
/root
```

---

# Virtualization

## What is Virtualization?

Running multiple operating systems on one physical machine.

Benefits:

* Cost Saving
* Resource Optimization
* Testing Environment
* Easy Management

---

## Popular Virtualization Software

### VMware Workstation

VMware Workstation

### Oracle VirtualBox

Oracle VM VirtualBox

---

# RHEL Installation Prerequisites

## Minimum Requirements

### CPU

* 1 Core Minimum
* 2 Cores Recommended

### RAM

* 2 GB Minimum
* 4 GB Recommended

### Disk

* 30 GB Recommended

---

# RHEL Virtual Machine Creation Steps

## Step 1

Create New Virtual Machine

```text
File → New Virtual Machine
```

---

## Step 2

Choose:

```text
Custom Installation
```

---

## Step 3

Attach RHEL ISO

```text
RHEL ISO File
```

---

## Step 4

Select Operating System

```text
Linux
Red Hat Enterprise Linux
```

---

## Step 5

Configure Hardware

| Resource | Recommended |
| -------- | ----------- |
| CPU      | 2 Cores     |
| RAM      | 4 GB        |
| Disk     | 30 GB       |

---

## Step 6

Power On VM

Choose:

```text
Install Red Hat Enterprise Linux
```

---

# RHEL Installation Configuration

### Language

```text
English (India)
```

### Keyboard

```text
English (India)
```

### Time Zone

```text
Asia/Kolkata
```

### Network

Enable Network

### Root Password

Set Administrator Password

### User Creation

Create Normal User

---

# Disk Partitioning

## Required Partitions

### /boot

Stores boot files.

Size:

```text
1 GB
```

---

### swap

Used when RAM is exhausted.

Size:

```text
2 GB or RAM Size
```

---

### /

Root filesystem.

Stores entire operating system.

Remaining Disk Space

---

## Recommended Layout

| Partition | Size            |
| --------- | --------------- |
| /boot     | 1 GB            |
| swap      | 2 GB            |
| /         | Remaining Space |

---

# Remote Login

## Check IP Address

```bash
ip addr
```

---

## Ping Test

```bash
ping <IP_ADDRESS>
```

---

## SSH Login

```bash
ssh root@192.168.x.x
```

---

# Tools for Remote Access

### PuTTY

PuTTY

### MobaXterm

MobaXterm

---

# Three Meanings of "Root" in Linux

| Term  | Meaning                  |
| ----- | ------------------------ |
| /     | Root Directory           |
| root  | Root User                |
| /root | Root User Home Directory |

---

# Important Interview Questions

### Q1. What is Linux?

An open-source UNIX-like operating system.

### Q2. What is Kernel?

Core component of Linux that interacts with hardware.

### Q3. What is GRUB?

Linux boot loader responsible for loading the kernel.

### Q4. What is MBR?

Master Boot Record located in first sector of disk.

### Q5. Difference between BIOS and UEFI?

UEFI is modern, faster, and supports GPT.

### Q6. What is Swap?

Disk space used as virtual memory when RAM becomes full.

### Q7. What is SSH?

Secure Shell protocol used for remote login.

### Q8. What are mandatory Linux partitions?

* /boot
* /
* swap

---

# Quick Revision Sheet

```text
UNIX → Developed by Dennis Ritchie & Ken Thompson

Linux → Open Source UNIX-like OS

Kernel → Heart of Linux

Shell → Command Interpreter

POST → Hardware Testing

BIOS/UEFI → Boot Device Selection

MBR → 512 Bytes

GRUB → Boot Loader

Run Level 0 → Shutdown

Run Level 1 → Single User

Run Level 5 → GUI

Run Level 6 → Reboot

/boot → Boot Files

swap → Virtual Memory

/ → Root Filesystem

SSH → Remote Login
```

🎯 These notes convert the transcript into structured training material suitable for Linux Administration, RHCSA/RHEL learning, interviews, classroom study, and professional documentation.
