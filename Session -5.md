# Linux Directory Management – Complete Structured Study Notes (RHEL 8)

**Session 5: Working with Directories in Linux**
Based on the Linux Administration Training Session by Nehra Classes. The session focuses on navigating, creating, managing, listing, and deleting directories in Linux. 

---

# Learning Objectives

After completing this topic, you should be able to:

* Understand Linux directory structure
* Navigate between directories
* Display current working directory
* Use absolute and relative paths
* Create directories
* Create nested directory structures
* Delete directories safely
* Work with hidden directories
* Understand parent and current directories

---

# Introduction to Directories in Linux

A directory in Linux is similar to a folder in Windows.

Directories are used to:

* Organize files
* Store data systematically
* Create hierarchical structures
* Manage users and applications efficiently

Linux follows a tree-like filesystem structure where everything starts from the Root Directory (`/`).

---

# Important Directory Navigation Commands

## 1. pwd Command

### Purpose

Displays the current working directory.

### Syntax

```bash
pwd
```

### Example

```bash
pwd
```

### Output

```bash
/home/user
```

### Use Case

Whenever you are unsure about your current location in the filesystem, use:

```bash
pwd
```

This command helps identify where you are working. 

---

# 2. cd Command (Change Directory)

### Purpose

Used to move between directories.

### Syntax

```bash
cd directory_name
```

---

## Move to a Specific Directory

```bash
cd /var/log
```

---

## Move to Home Directory

```bash
cd
```

or

```bash
cd ~
```

If no directory is specified after `cd`, Linux automatically takes you to your home directory. 

---

## Move to Root Directory

```bash
cd /
```

Root (`/`) is the topmost directory in Linux. 

---

# Understanding Hidden Directory Entries

Using:

```bash
ls -a
```

shows hidden entries.

Example:

```text
.
..
```

---

## Meaning of "."

```text
.
```

Represents:

### Current Directory

Example:

```bash
cd .
```

You remain in the same directory.

---

## Meaning of ".."

```text
..
```

Represents:

### Parent Directory

Example:

```bash
cd ..
```

Moves one level up in the directory hierarchy. 

---

# Practical Examples

Assume:

```text
/home/user/docs
```

Current location:

```bash
pwd
```

Output:

```text
/home/user/docs
```

---

### Move to Parent Directory

```bash
cd ..
```

Result:

```text
/home/user
```

---

### Move Back into docs

```bash
cd docs
```

Result:

```text
/home/user/docs
```

---

# Absolute Path vs Relative Path

One of the most important Linux concepts.

---

# Absolute Path

An absolute path starts from root (`/`).

### Example

```bash
cd /home/user/documents
```

Characteristics:

* Starts with `/`
* Complete path specified
* Works from anywhere

---

# Relative Path

A relative path starts from the current location.

### Example

Suppose current directory:

```text
/home/user
```

Then:

```bash
cd documents
```

works because `documents` exists inside current directory.

No complete path is required. 

---

# Listing Directory Contents

## ls Command

### Syntax

```bash
ls
```

Displays:

* Files
* Directories

---

## Show Hidden Files

```bash
ls -a
```

Displays:

```text
.
..
.hidden_file
```

---

## Long Listing Format

```bash
ls -l
```

Shows:

* Permissions
* Owner
* Group
* Size
* Date
* Filename

---

## Human Readable Format

```bash
ls -lh
```

Displays sizes in:

* KB
* MB
* GB

instead of bytes. 

---

# Creating Directories

## mkdir Command

### Meaning

```text
mkdir = Make Directory
```

Used to create new directories. 

---

## Syntax

```bash
mkdir directory_name
```

---

## Example

```bash
mkdir links
```

Creates:

```text
links/
```

directory. 

---

# Creating Directory Using Full Path

```bash
mkdir /tmp/links
```

Creates directory at a specific location.

---

# Creating Nested Directories

Suppose you want:

```text
tmp/
└── links/
    └── units/
```

If parent directories already exist:

```bash
mkdir /tmp/links/units
```

will work. 

---

# Problem with Nested Directories

Suppose you execute:

```bash
mkdir /tmp/links/unix1/batch1
```

but:

```text
unix1
```

does not exist.

Linux returns:

```text
No such file or directory
```

because parent directory is missing. 

---

# mkdir -p Option

## Purpose

Automatically creates:

* Parent directories
* Child directories

in a single command.

### Syntax

```bash
mkdir -p path
```

---

### Example

```bash
mkdir -p /tmp/links/unix1/batch1
```

Creates:

```text
tmp
└── links
    └── unix1
        └── batch1
```

even if none of the directories previously existed. 

---

# Directory Structure Creation Example

```bash
mkdir -p /tmp/A/B/C
```

Result:

```text
A
└── B
    └── C
```

Created automatically. 

---

# Creating Files Inside Directories

Example:

```bash
cal > calendar.txt
```

Creates a file containing calendar output.

A file can then be stored inside nested directories. 

---

# Removing Directories

## rmdir Command

### Purpose

Deletes empty directories.

### Syntax

```bash
rmdir directory_name
```

---

### Example

```bash
rmdir links
```

Works only if directory is empty.

---

# Limitation of rmdir

If directory contains:

* Files
* Subdirectories

then:

```bash
rmdir
```

fails.

---

# rm -r Command

### Purpose

Deletes directory recursively.

### Syntax

```bash
rm -r directory_name
```

Deletes:

* Directory
* Subdirectories
* Files

all together. 

---

## Example

```bash
rm -r links
```

Removes:

```text
links
└── units
    └── files
```

completely.

---

# Directory Deletion Hierarchy

Without recursive deletion:

You must delete:

1. Child directory
2. Parent directory
3. Grandparent directory

one by one.

Using:

```bash
rm -r
```

everything is removed in one command. 

---

# Linux Directory Tree Concept

Example structure:

```text
/
├── home
│   └── user
│       └── docs
├── etc
├── var
└── tmp
```

Everything in Linux exists under the root filesystem.

---

# Best Practices

### Always Check Current Location

```bash
pwd
```

before creating or deleting directories.

---

### Verify Directory Contents

```bash
ls -la
```

before deletion.

---

### Use mkdir -p

for creating large directory structures.

---

### Use rm -r Carefully

A wrong recursive delete can remove important files permanently.

---

# Frequently Used Directory Commands

| Command  | Purpose                      |
| -------- | ---------------------------- |
| pwd      | Show current directory       |
| cd       | Change directory             |
| cd ..    | Go to parent directory       |
| cd ~     | Go to home directory         |
| cd /     | Go to root directory         |
| ls       | List contents                |
| ls -a    | Show hidden files            |
| ls -l    | Long listing                 |
| ls -lh   | Human-readable sizes         |
| mkdir    | Create directory             |
| mkdir -p | Create nested directories    |
| rmdir    | Remove empty directory       |
| rm -r    | Remove directory recursively |

---

# Interview Questions

### Q1. What is the difference between Absolute Path and Relative Path?

**Answer:**

| Absolute Path          | Relative Path                 |
| ---------------------- | ----------------------------- |
| Starts from root (`/`) | Starts from current directory |
| Complete path          | Partial path                  |
| Works from anywhere    | Depends on current location   |

---

### Q2. What does "." represent?

**Answer:** Current Directory.

---

### Q3. What does ".." represent?

**Answer:** Parent Directory.

---

### Q4. Which command creates directories?

```bash
mkdir
```

---

### Q5. What is the purpose of `mkdir -p`?

**Answer:** Creates parent and child directories automatically.

---

### Q6. Difference between `rmdir` and `rm -r`?

| rmdir                        | rm -r                           |
| ---------------------------- | ------------------------------- |
| Deletes empty directory only | Deletes directory with contents |
| Safer                        | More powerful                   |

---

# Key Takeaways

✅ Linux directories are organized in a tree structure.

✅ Use `pwd` to identify your current location.

✅ Use `cd` for navigation.

✅ `.` means current directory and `..` means parent directory.

✅ Use `mkdir` to create directories.

✅ Use `mkdir -p` to create nested directory structures.

✅ Use `rmdir` for empty directories.

✅ Use `rm -r` for recursive directory deletion.

✅ Understand Absolute and Relative paths thoroughly, as they are heavily used in Linux administration and interviews.
