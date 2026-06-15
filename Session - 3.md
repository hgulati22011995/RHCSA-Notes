## Topic: Linux File System Hierarchy (FHS) & Basic Linux Administration

---

# 1. Session Overview

This session focused on:

* Linux File System Hierarchy (FHS)
* Understanding important Linux directories
* Difference between Root User and Normal User
* Remote Login using SSH
* Virtual Machine Cloning/Templates
* Basic Linux Commands
* Real-world Linux Administration concepts

---

# 2. Linux Administration Best Practices

### Key Takeaways

✅ Always practice commands yourself.

✅ Linux administration is mostly performed using:

* Command Line Interface (CLI)
* SSH Remote Login

✅ GUI may not always be available on production servers.

✅ Learn to work completely from terminal.

---

# 3. Creating a Linux VM Template

## Why Create Templates?

Instead of installing Linux repeatedly:

1. Create one clean machine.
2. Configure it properly.
3. Save it as a template.
4. Clone whenever needed.

### Benefits

* Saves time
* Industry standard practice
* Faster deployment
* Consistent environments

### Clone Workflow

```
Virtual Machine
   ↓
Right Click
   ↓
Clone
   ↓
Current State
   ↓
Full Clone
   ↓
Create
```

Result:

A new machine is created within seconds.

---

# 4. Accessing Linux Remotely

## Common Industry Practice

Administrators usually connect remotely using:

### SSH (Secure Shell)

```
ssh root@IP_ADDRESS
```

Example:

```bash
ssh root@192.168.1.128
```

After entering the password:

```bash
[root@server ~]#
```

You are logged into the Linux server.

---

# 5. Understanding the Linux Prompt

Example:

```bash
[root@server ~]#
```

### Breakdown

| Part   | Meaning        |
| ------ | -------------- |
| root   | Logged-in user |
| server | Hostname       |
| ~      | Home directory |
| #      | Root user      |

---

## Root User vs Normal User

### Root User

Prompt:

```bash
#
```

Meaning:

* Super User
* Full access
* Can modify anything

---

### Normal User

Prompt:

```bash
$
```

Meaning:

* Limited privileges
* Cannot perform administrative tasks

Example:

```bash
[user@server ~]$
```

---

# 6. Linux File System Hierarchy

Unlike Windows:

### Windows

```text
C:\
D:\
E:\
```

Linux uses a single hierarchy:

```text
/
```

The forward slash (`/`) is called:

### Root Directory

All directories originate from this location.

---

# 7. Important Linux Commands

## Change Directory

```bash
cd /
```

Moves to root directory.

---

## List Files

```bash
ls
```

Lists files and directories.

---

## Long Listing

```bash
ls -l
```

Displays:

* Permissions
* Owner
* Group
* Size
* Date
* Filename

---

## Display Current Location

```bash
pwd
```

Output:

```bash
/root
```

---

# 8. Linux Directory Structure Explained

---

## 1. /bin

### Meaning

Binary Programs

Contains essential executable commands.

Examples:

```bash
ls
cp
mv
cat
pwd
```

Purpose:

Stores command binaries required by all users.

---

## 2. /sbin

### Meaning

System Binary

Contains administrative commands.

Examples:

```bash
fdisk
reboot
shutdown
```

Used mainly by:

* Root User
* System Administrators

---

## 3. /boot

### Purpose

Contains files required for system booting.

Important Files:

### Kernel

```text
vmlinuz
```

### Initramfs

```text
initramfs
```

### GRUB Bootloader Files

```text
/boot/grub2
```

Without these files:

❌ System will not boot.

---

## 4. /dev

### Device Files

Everything in Linux is treated as a file.

Examples:

```text
/dev/sda
/dev/sdb
/dev/cdrom
/dev/tty
```

Represents:

* Hard disks
* USB devices
* CD/DVD
* Terminals

---

## 5. /etc

### Configuration Directory

Stores configuration files.

Examples:

```text
/etc/passwd
/etc/shadow
/etc/hosts
/etc/fstab
```

Used for:

* User settings
* Network settings
* Service configuration

---

## 6. /home

### User Home Directories

Example:

```text
/home/user1
/home/user2
```

Stores:

* Documents
* Downloads
* User files

Each user gets a separate home directory.

---

## 7. /root

### Root User Home

```text
/root
```

Only for root user.

Equivalent of:

```text
/home/user
```

for regular users.

---

## 8. /lib

Contains:

### 32-bit Libraries

Used by:

* Programs
* Commands
* System services

---

## 9. /lib64

Contains:

### 64-bit Libraries

Required by modern Linux systems.

Many applications depend on these shared libraries.

---

## 10. /media

Used for automatically mounted devices.

Examples:

* USB Drives
* CD/DVD
* External Storage

Example:

```text
/media/usb
```

---

## 11. /mnt

### Temporary Mount Point

Used manually for:

* ISO Images
* Network Shares
* External Storage

Example:

```bash
mount /dev/cdrom /mnt
```

---

## 12. /opt

### Optional Software

Used for installing third-party applications.

Examples:

```text
/opt/google
/opt/application
```

---

## 13. /proc

### Process Information Directory

Virtual file system.

Contains:

* CPU information
* Memory information
* Running processes

Examples:

```bash
cat /proc/cpuinfo
```

```bash
cat /proc/meminfo
```

Very important for troubleshooting.

---

## 14. /run

Stores runtime information.

Contains:

* Process IDs
* Runtime sockets
* Temporary service data

---

## 15. /srv

Stores data related to services.

Examples:

* Web server data
* FTP server data

---

## 16. /tmp

### Temporary Files

Used for:

* Temporary storage
* Extraction
* Intermediate files

Important:

⚠ Files may be deleted automatically after reboot.

Never store critical data here.

---

## 17. /usr

Contains:

### User Applications

Subdirectories:

```text
/usr/bin
/usr/sbin
/usr/lib
/usr/share
```

Most software resides here.

---

## 18. /var

### Variable Data

Contains frequently changing files.

Examples:

```text
/var/log
/var/spool
/var/cache
```

---

# 9. Understanding Logs

Logs are usually stored in:

```text
/var/log
```

Examples:

```text
messages
secure
cron
maillog
```

Uses:

* Troubleshooting
* Monitoring
* Auditing

---

# 10. Understanding Mounting

Before accessing storage:

Linux must mount it.

Example:

```bash
mount /dev/cdrom /mnt
```

After mounting:

Files become accessible.

---

# 11. Working with Files

## Create a File

```bash
vi newfile.txt
```

Add content:

```text
Welcome to Linux Training
```

Save and exit.

---

## View File

```bash
cat newfile.txt
```

Output:

```text
Welcome to Linux Training
```

---

# 12. Linux Permissions Basics

Using:

```bash
ls -l
```

Example:

```bash
-rwxr-xr-x
```

Shows:

* Read
* Write
* Execute permissions

For:

* Owner
* Group
* Others

---

# 13. Important Linux Concepts Learned

### Root Directory

```text
/
```

Parent of all directories.

---

### Home Directory

```text
~
```

Current user's home location.

---

### Forward Slash

Linux path separator:

```text
/
```

Unlike Windows:

```text
\
```

---

# 14. Real Interview Questions

### Q1. Difference Between Root and Normal User?

**Root User**

* Full permissions
* Can execute administrative commands

**Normal User**

* Limited access
* Cannot perform privileged operations

---

### Q2. What is `/etc`?

Stores system configuration files.

---

### Q3. What is `/var/log`?

Stores system log files.

---

### Q4. What is `/tmp`?

Temporary storage location.

---

### Q5. What is `/proc`?

Virtual filesystem containing process and kernel information.

---

# 15. Practical Commands Covered

```bash
pwd
ls
ls -l
cd
cat
vi
mount
ssh
```

---

# Session Summary

By the end of this session, you should understand:

✅ Linux File System Hierarchy (FHS)

✅ Purpose of important directories

✅ Root vs Normal User

✅ SSH Remote Access

✅ Virtual Machine Cloning

✅ File Creation and Viewing

✅ Linux Boot-related Files

✅ Mounting Concepts

✅ Logs and Process Information

This session forms the foundation for Linux Administration, RHCSA, RHCE, DevOps, Cloud, and System Engineering roles.
