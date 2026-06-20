# Session 9: Shell Expansion in Linux & Control Operators

## Complete Structured Notes (Nehra Classes)

---

# 1. Introduction

In Linux Shell, **Control Operators** are special symbols used to control the execution flow of commands.

They help us:

* Execute multiple commands together
* Run commands conditionally
* Run commands in the background
* Check command execution status
* Ignore special characters
* Write readable shell scripts

---

# 2. What are Control Operators?

Control operators are special symbols that determine:

* How commands execute
* When commands execute
* Whether commands execute sequentially or conditionally

### Common Linux Control Operators

| Operator         | Purpose                 |
| ---------------- | ----------------------- |
| ;                | Sequential Execution    |
| &                | Background Execution    |
| $?               | Previous Command Status |
| &&               | Logical AND             |
| ||               | Logical OR              |
| && ||            | If-Else Style Logic     |
| #                | Comment                 |
| \                | Escape Character        |
| \ at End of Line | Line Continuation       |

---

# 3. Semicolon ( ; ) Operator

## Purpose

Executes multiple commands **one after another**.

### Syntax

```bash
command1 ; command2 ; command3
```

---

## Example

```bash
date ; pwd ; cal
```

### Execution Flow

1. date executes
2. pwd executes
3. cal executes

Output appears sequentially.

---

## Important Point

Even if one command fails, remaining commands still execute.

### Example

```bash
abcd ; pwd ; cal
```

Output:

```bash
bash: abcd: command not found
/home/user
calendar output
```

Even though first command failed:

* pwd executed
* cal executed

---

## Example

```bash
echo Hello ; echo World
```

Output:

```bash
Hello
World
```

---

# 4. Ampersand ( & ) Operator

## Purpose

Runs a command in the background.

### Syntax

```bash
command &
```

---

## Example

```bash
sleep 30 &
```

Output:

```bash
[1] 12345
```

The command starts in background and terminal becomes free immediately.

---

## Example

```bash
date & pwd
```

Both commands begin execution simultaneously.

---

## Difference Between ; and &

### Semicolon

```bash
sleep 20 ; date
```

Execution:

```text
Wait 20 seconds
Then run date
```

---

### Ampersand

```bash
sleep 20 & date
```

Execution:

```text
sleep runs in background
date executes immediately
```

---

## Comparison Table

| Operator | Behavior            |
| -------- | ------------------- |
| ;        | Sequential          |
| &        | Parallel/Background |

---

# 5. Sleep Command

## Purpose

Pauses execution for specified seconds.

### Syntax

```bash
sleep seconds
```

---

## Example

```bash
sleep 10
```

Terminal waits for 10 seconds.

---

## Example

```bash
sleep 30
```

Terminal remains busy for 30 seconds.

---

# 6. Exit Status Variable ($?)

## Purpose

Stores the status code of the previously executed command.

### Syntax

```bash
echo $?
```

---

# Meaning of Values

## Successful Execution

```bash
0
```

Means:

```text
Command executed successfully
```

---

## Failed Execution

Any non-zero value.

Commonly:

```bash
127
```

Means:

```text
Command not found
```

---

## Example 1

```bash
pwd
echo $?
```

Output:

```bash
/home/user
0
```

---

## Example 2

```bash
abcd
echo $?
```

Output:

```bash
127
```

Meaning:

```text
Previous command failed.
```

---

## Why Important?

Useful in:

* Shell scripting
* Error handling
* Automation
* Monitoring command execution

---

# 7. Logical AND Operator ( && )

## Purpose

Execute next command ONLY if previous command succeeds.

### Syntax

```bash
command1 && command2
```

---

## Example

```bash
echo First && echo Second
```

Output:

```bash
First
Second
```

---

## Example

```bash
abcd && echo Success
```

Output:

```bash
bash: abcd: command not found
```

Second command will NOT execute.

---

## Logic

| Command1 | Command2 Executes? |
| -------- | ------------------ |
| Success  | Yes                |
| Failure  | No                 |

---

# 8. Logical OR Operator ( || )

## Purpose

Execute second command only when first command fails.

### Syntax

```bash
command1 || command2
```

---

## Example

```bash
echo First || echo Second
```

Output:

```bash
First
```

Second command skipped.

---

## Example

```bash
abcd || echo Failed
```

Output:

```bash
bash: abcd: command not found
Failed
```

---

## Logic

| Command1 | Command2 Executes? |
| -------- | ------------------ |
| Success  | No                 |
| Failure  | Yes                |

---

# 9. Combining AND and OR ( && || )

Used to create simple If-Else style logic.

---

## Structure

```bash
command1 && command2 || command3
```

Meaning:

```text
If command1 succeeds
    Execute command2
Else
    Execute command3
```

---

# Example

Create a file:

```bash
touch file1
```

---

Now execute:

```bash
rm file1 && echo "It Works" || echo "It Failed"
```

Output:

```bash
It Works
```

Because:

```text
file1 existed
rm succeeded
```

---

Run again:

```bash
rm file1 && echo "It Works" || echo "It Failed"
```

Output:

```bash
rm: cannot remove file1
It Failed
```

Because:

```text
file no longer exists
rm failed
```

---

## Flow Diagram

```text
Command Success
      |
      v
Execute Right Side of &&
      |
      v
Skip ||
```

```text
Command Failure
      |
      v
Skip &&
      |
      v
Execute Right Side of ||
```

---

# 10. Comment Operator ( # )

## Purpose

Anything written after # is ignored by shell.

---

## Example

```bash
echo Hello # This is a comment
```

Output:

```bash
Hello
```

---

Everything after:

```bash
#
```

is ignored.

---

## Example in Script

```bash
#!/bin/bash

# Display welcome message

echo "Welcome"
```

---

## Benefits

Used for:

* Documentation
* Explanations
* Notes
* Readability

---

# 11. Escape Character ( \ )

## Purpose

Makes the next special character lose its special meaning.

---

## Example 1

Without Escape

```bash
echo Hello;World
```

Shell interprets:

```text
echo Hello
World
```

Result:

```bash
Hello
bash: World: command not found
```

---

## Example 2

With Escape

```bash
echo Hello\;World
```

Output:

```bash
Hello;World
```

Semicolon becomes normal text.

---

# 12. Escaping Spaces

## Example

```bash
echo Hello\ World
```

Output:

```bash
Hello World
```

Space treated as part of same string.

---

# 13. End-of-Line Backslash (Line Continuation)

Used when command is too long.

---

## Example

```bash
echo This command \
is split \
into three \
parts
```

Output:

```bash
This command is split into three parts
```

---

## How It Works

When backslash appears at end of line:

```bash
\
```

Shell waits for next line.

Command executes only after final line without backslash.

---

# 14. Practical Examples

## Multiple Commands

```bash
date ; pwd ; whoami
```

---

## Background Process

```bash
sleep 60 &
```

---

## Success Check

```bash
mkdir test
echo $?
```

---

## Conditional Execution

```bash
mkdir test && echo "Created"
```

---

## Error Handling

```bash
mkdir test || echo "Failed"
```

---

## If-Else Style

```bash
mkdir test && echo Success || echo Failure
```

---

# Interview Questions

### Q1. What is a Control Operator?

A special symbol used to control command execution flow.

---

### Q2. Difference between ; and & ?

| ;                          | &                    |
| -------------------------- | -------------------- |
| Sequential Execution       | Background Execution |
| Waits for previous command | Doesn't wait         |

---

### Q3. What does `$?` store?

Exit status of previously executed command.

---

### Q4. What does exit code 0 mean?

Successful execution.

---

### Q5. What does exit code 127 mean?

Command not found.

---

### Q6. When is `&&` used?

When next command should execute only if previous command succeeds.

---

### Q7. When is `||` used?

When next command should execute only if previous command fails.

---

### Q8. What is the purpose of `#`?

Creates comments.

---

### Q9. What is an escape character?

Backslash (`\`) used to suppress special meaning of next character.

---

### Q10. Why use line continuation (`\`)?

To split long commands into multiple lines for better readability.

---

# Session Summary

In this session, we learned:

✅ Semicolon Operator (`;`)
✅ Background Operator (`&`)
✅ Sleep Command
✅ Exit Status Variable (`$?`)
✅ Logical AND (`&&`)
✅ Logical OR (`||`)
✅ IF-ELSE Style Command Chaining (`&& ||`)
✅ Comment Operator (`#`)
✅ Escape Character (`\`)
✅ Line Continuation Using Backslash

### Key Takeaway

Control operators are fundamental building blocks of Linux shell scripting and command-line automation. Mastering them allows you to create efficient command chains, automate tasks, perform conditional execution, and write professional shell scripts.
