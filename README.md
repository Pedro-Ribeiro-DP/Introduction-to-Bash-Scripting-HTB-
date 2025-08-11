# Introduction to Bash Scripting (HTB)

## 📌 Description
This repository contains notes, practical examples, and solved exercises from the **Introduction to Bash Scripting** module by Hack The Box (HTB).  
It covers everything from the fundamental concepts of the language to script execution control, providing a solid foundation for automating tasks and understanding execution flow in Linux.

### Includes:
- Basic concepts of the shell and Bash.
- Essential components for writing efficient scripts.
- Control structures and loops.
- Execution flow management.
- Practical exercises to reinforce learning.

---

## 📂 Table of Contents

### 1. Introduction
- Bourne Again Shell

### 2. Working Components
- Conditional Execution

---

## 🧩 Exercise

**Task:**  
Create an `if-else` condition in the `for` loop of the **Exercise Script** that prints the number of characters of the 35th generated value of the variable `var`. Submit the number as the answer.

**Exercise Script (starter code):**
```bash
#!/bin/bash
# Count number of characters in a variable:
#     echo $variable | wc -c

# Variable to encode
var="nef892na9s1p9asn2aJs71nIsm"

for counter in {1..40}
do
    var=$(echo $var | base64)
done
```

✅ Answer
```
#!/bin/bash

# Variable to encode
var="nef892na9s1p9asn2aJs71nIsm"

for counter in {1..40}; do
    var=$(echo "$var" | base64)

    # Check if the loop is at the 35th iteration
    if [ "$counter" -eq 35 ]; then
        # Print the number of characters in the variable
        echo "$var" | wc -c
    fi
done
```

Output: 684824


- Arguments, Variables, and Arrays
- Comparison Operators
- Arithmetic

### 3. Script Control
- Input and Output Control
- Flow Controls - Loops
- Flow Control - Branches

### 4. Execution Flow
- Functions
- Debugging

