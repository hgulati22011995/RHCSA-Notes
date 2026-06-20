# Session 10: Shell Variables in Linux – Detailed & Structured Notes

## Overview

In this session, the focus is on **Shell Variables** in Linux. Variables are used to store data that can be referenced and manipulated by the shell. Understanding variables is essential for:

* Shell scripting
* Automation
* System administration
* Environment customization
* Command-line productivity

---

# 1. What is a Variable?

A **Variable** is a named storage location that holds a value.

### Characteristics

* Stores data temporarily or permanently.
* Value can change during execution.
* Used by the shell and scripts.
* Makes scripts dynamic and reusable.

### Example

```bash
MYVAR=100
```

Here:

* Variable Name = `MYVAR`
* Value = `100`

---

# 2. Types of Variables in Linux

Linux Shell Variables are mainly divided into two categories:

## A. System Defined Variables

These variables are already created by Linux.

Examples:

| Variable | Purpose                   |
| -------- | ------------------------- |
| HOME     | User home directory       |
| USER     | Current username          |
| SHELL    | Current shell             |
| HOSTNAME | System hostname           |
| PWD      | Present working directory |
| PATH     | Search path for commands  |
| PS1      | Shell prompt format       |

### Example

```bash
echo $USER
```

Output:

```bash
root
```

or

```bash
vikas
```

depending on logged-in user.

---

## B. User Defined Variables

Variables created by users according to their requirements.

Example:

```bash
CITY=Delhi
```

Access value:

```bash
echo $CITY
```

Output:

```bash
Delhi
```

---

# 3. Viewing Variable Values

Use `$` before the variable name.

### Syntax

```bash
echo $VARIABLE_NAME
```

### Examples

#### Current User

```bash
echo $USER
```

#### Current Shell

```bash
echo $SHELL
```

Output:

```bash
/bin/bash
```

#### Current Directory

```bash
echo $PWD
```

Output:

```bash
/root
```

#### Hostname

```bash
echo $HOSTNAME
```

Output:

```bash
server01
```

---

# 4. Why Variable Values Change?

Variables are dynamic.

Example:

### Root User

```bash
echo $USER
```

Output:

```bash
root
```

### Normal User

```bash
echo $USER
```

Output:

```bash
vikas
```

Reason:

* Variable stores current login information.
* Value depends on the active session.

---

# 5. Linux is Case Sensitive

Linux treats uppercase and lowercase differently.

### Example

```bash
echo $USER
```

Output:

```bash
root
```

But:

```bash
echo $user
```

Output:

```bash
(blank)
```

Because:

```bash
USER ≠ user
```

These are treated as different variables.

---

# 6. Creating User Defined Variables

### Syntax

```bash
VARIABLE_NAME=value
```

### Example

```bash
MYVAR=5
```

Check value:

```bash
echo $MYVAR
```

Output:

```bash
5
```

---

## Another Example

```bash
AGE=100
```

```bash
echo $AGE
```

Output:

```bash
100
```

---

# 7. Rules for Naming Variables

## Valid Rules

### Rule 1

Must start with a letter or underscore.

Valid:

```bash
MYVAR=10
```

```bash
myvar=10
```

```bash
_var=10
```

---

### Rule 2

Numbers can appear after the first character.

Valid:

```bash
VAR1=10
```

```bash
USER123=test
```

---

## Invalid Rules

### Cannot Start with a Number

Invalid:

```bash
1VAR=10
```

Error:

```bash
command not found
```

---

### Avoid Special Characters

Invalid:

```bash
MY-VAR=10
```

```bash
MY@VAR=10
```

```bash
MY#VAR=10
```

---

# 8. Modifying Variable Values

Variables can be overwritten.

### Initial Value

```bash
MYVAR=555
```

```bash
echo $MYVAR
```

Output:

```bash
555
```

---

### Change Value

```bash
MYVAR=666
```

```bash
echo $MYVAR
```

Output:

```bash
666
```

Old value is replaced.

---

# 9. Quotes and Variables

Understanding quotes is very important.

---

## Double Quotes

Variable expansion occurs.

Example:

```bash
MYVAR=666
echo "$MYVAR"
```

Output:

```bash
666
```

---

## Single Quotes

Variable expansion does NOT occur.

Example:

```bash
echo '$MYVAR'
```

Output:

```bash
$MYVAR
```

The text is printed literally.

---

## Comparison

| Command         | Output |
| --------------- | ------ |
| `echo "$MYVAR"` | 666    |
| `echo '$MYVAR'` | $MYVAR |

---

# 10. Using Variables Inside Sentences

Example:

```bash
CITY=Delhi
```

```bash
echo "I live in $CITY"
```

Output:

```bash
I live in Delhi
```

---

# 11. Displaying All Variables

Use:

```bash
set
```

This command displays:

* System variables
* User variables
* Shell functions

Example:

```bash
set
```

Shows a long list of variables currently available.

---

# 12. Removing Variables

Use:

```bash
unset VARIABLE_NAME
```

### Example

```bash
unset MYVAR
```

Check:

```bash
echo $MYVAR
```

Output:

```bash
(blank)
```

Variable has been removed.

---

# 13. Temporary vs Permanent Variables

## Temporary Variable

Created directly:

```bash
MYVAR=100
```

Exists only during current session.

After logout:

```bash
Variable disappears.
```

---

## Permanent Variable

Store variable in profile files.

Common files:

```bash
~/.bashrc
```

```bash
~/.bash_profile
```

```bash
~/.profile
```

System-wide:

```bash
/etc/profile
```

---

# 14. Making Variables Permanent

Edit:

```bash
vim ~/.bashrc
```

Add:

```bash
MYVAR=599
```

Save file.

Apply changes:

```bash
source ~/.bashrc
```

Check:

```bash
echo $MYVAR
```

Output:

```bash
599
```

Variable remains available after login.

---

# 15. Source Command

Used to reload configuration files without logout.

### Syntax

```bash
source filename
```

Example:

```bash
source ~/.bashrc
```

or

```bash
. ~/.bashrc
```

Both are equivalent.

---

# 16. PS1 Variable (Shell Prompt)

PS1 controls terminal prompt appearance.

Check current prompt configuration:

```bash
echo $PS1
```

Example Output:

```bash
[\u@\h \W]\$
```

---

## Common PS1 Symbols

| Symbol | Meaning                |
| ------ | ---------------------- |
| \u     | Username               |
| \h     | Hostname               |
| \w     | Current path           |
| \W     | Current directory      |
| $      | $ for user, # for root |

---

## Change Prompt

Example:

```bash
PS1="TechMint > "
```

Prompt becomes:

```bash
TechMint >
```

Temporary until logout.

---

# 17. PATH Variable

One of the most important system variables.

View PATH:

```bash
echo $PATH
```

Example:

```bash
/usr/local/bin:/usr/bin:/bin
```

---

## Purpose of PATH

When you run:

```bash
ls
```

Linux searches directories listed in PATH.

Search sequence:

```text
Directory 1
Directory 2
Directory 3
...
```

If command found:

```bash
Command executes
```

Otherwise:

```bash
command not found
```

---

# 18. Exported Variables

Some variables are inherited by child shells.

Check exported variables:

```bash
export
```

or

```bash
export -p
```

---

# 19. Creating Exported Variables

Example:

```bash
VAR1=3
VAR2=4
```

Export:

```bash
export VAR2
```

---

### Child Shell Test

Start child shell:

```bash
bash
```

Check:

```bash
echo $VAR1
```

Output:

```bash
(blank)
```

Not exported.

---

```bash
echo $VAR2
```

Output:

```bash
4
```

Exported successfully.

---

# 20. Shell Levels (SHLVL)

Displays shell nesting level.

Check:

```bash
echo $SHLVL
```

Output:

```bash
1
```

---

Start new shell:

```bash
bash
```

Check again:

```bash
echo $SHLVL
```

Output:

```bash
2
```

---

Start another shell:

```bash
bash
```

Output:

```bash
3
```

Each shell creates a child shell.

---

Exit shell:

```bash
exit
```

or

```bash
Ctrl+D
```

Shell level decreases.

---

# 21. Environment Variables Only

Start shell without inherited environment:

```bash
env -i bash
```

Purpose:

* Clears environment variables.
* Starts clean shell.

Useful for troubleshooting and testing.

---

# 22. Using Curly Braces with Variables

Problem:

```bash
PREFIX=super
```

```bash
echo "$PREFIXman"
```

Shell interprets:

```bash
PREFIXman
```

as one variable.

Output:

```bash
(blank)
```

---

## Correct Method

```bash
echo "${PREFIX}man"
```

Output:

```bash
superman
```

---

Another Example

```bash
echo "${PREFIX}girl"
```

Output:

```bash
supergirl
```

---

# 23. Detecting Undefined Variables

Normally:

```bash
echo $UNKNOWN
```

Output:

```bash
(blank)
```

---

Enable strict checking:

```bash
set -u
```

Now:

```bash
echo $UNKNOWN
```

Output:

```bash
bash: UNKNOWN: unbound variable
```

---

Disable feature:

```bash
set +u
```

Returns to normal behavior.

---

# Important Commands Summary

| Command       | Purpose                             |
| ------------- | ----------------------------------- |
| `echo $VAR`   | Display variable                    |
| `VAR=value`   | Create variable                     |
| `unset VAR`   | Delete variable                     |
| `set`         | Show all variables                  |
| `export VAR`  | Export variable                     |
| `export -p`   | Show exported variables             |
| `source file` | Reload configuration                |
| `echo $PATH`  | View command search path            |
| `echo $PS1`   | View prompt format                  |
| `echo $SHLVL` | View shell level                    |
| `set -u`      | Detect undefined variables          |
| `set +u`      | Disable undefined-variable checking |

---

# Interview Questions

### Q1. What is a Shell Variable?

A shell variable is a named storage location used to store data in the shell environment.

---

### Q2. What are the two types of variables in Linux?

1. System Defined Variables
2. User Defined Variables

---

### Q3. How do you display a variable value?

```bash
echo $VARIABLE
```

---

### Q4. How do you remove a variable?

```bash
unset VARIABLE
```

---

### Q5. What is the difference between single and double quotes?

* Double Quotes → Variable expansion occurs.
* Single Quotes → Literal text is displayed.

---

### Q6. What is the purpose of PATH?

PATH tells Linux where to search for executable commands.

---

### Q7. What does PS1 control?

PS1 controls the appearance of the shell prompt.

---

### Q8. What does export do?

It makes a variable available to child shells and subprocesses.

---

# Key Takeaways

* Variables store dynamic values.
* Linux variables are case-sensitive.
* Use `$` to access variable values.
* `unset` removes variables.
* `export` shares variables with child shells.
* `PATH` controls command lookup.
* `PS1` controls shell prompt appearance.
* `source` reloads configuration files.
* `${VAR}` helps safely concatenate variables with text.
* `set -u` helps detect undefined variables.
* Permanent variables should be stored in `.bashrc`, `.bash_profile`, or `/etc/profile`.

These concepts form the foundation for **Shell Scripting**, **Linux Administration**, **DevOps Automation**, and advanced command-line operations.
