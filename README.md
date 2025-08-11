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

### 🧩 Exercise

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
```bash
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

---

## 🧩 Exercise

**Task:**  
Create an `if-else` condition in the `for` loop that checks if the variable named `var` contains the contents of the variable named `value`.  
Additionally, the variable `var` must contain **more than 113,450 characters**.  
If these conditions are met, the script must then print the **last 20 characters** of the variable `var`.  
Submit these last 20 characters as the answer.

**Exercise Script (starter code):**
```bash
#!/bin/bash

var="8dm7KsjU28B7v621Jls"
value="ERmFRMVZ0U2paTlJYTkxDZz09Cg"

for i in {1..40}
do
    var=$(echo "$var" | base64)
		
    # <---- If condition here:
done
```
✅ Answer

Terminal: 
> $ nano exercise.sh
> 
> $ ./exercise.sh                (#try running the "exercise.sh")
> 
> #Permission denied
> 
> $ chmod +x exercise.sh         (#chmod (grant permissions) +x (to execute) exercise.sh (bash))
> 
> $ ./exercise.sh                (#run/execute)
> 
> U2paTlJYTkxDZz09Cg==


```bash
#!/bin/bash/exercise.sh

# The line above (shebang) specifies that the script should be executed with the Bash interpreter.

# Variable declaration and initialization.
var="8dm7KsjU28B7v621Jls"
value="ERmFRMVZ0U2paTlJYTkxDZz09Cg"

# Starts a loop that will execute 40 times.
for i in {1..40}
do
    # In each iteration, the content of the 'var' variable is Base64 encoded,
    # and the new encoded value replaces the old one.
    var=$(echo "$var" | base64)

    # Beginning of the 'if' conditional structure.
    # The entire condition will only be true if both checks (joined by '&&') succeed.

    # 1st Check: Verifies if the string in 'var' contains the exact string stored in 'value'.
    # 2nd Check: Verifies if the number of characters in 'var' is greater than 113,450.
    #    - 'echo -n "$var"' prints the content of 'var' without a trailing newline.
    #    - '| wc -c' counts the number of bytes (characters) from that output.
    #    - '[ ... -gt ... ]' performs the numerical comparison ("greater than").
    if [[ "$var" == *"$value"* ]] && [ "$(echo -n "$var" | wc -c)" -gt 113450 ]; then
        # This block is only executed if BOTH of the above conditions are true.
        # Prints the last 20 characters of the current content of 'var'.
        # 'echo -n' ensures that only the variable's content is sent to 'tail'.
        echo -n "$var" | tail -c 20
    fi # End of the conditional structure.

done # End of the loop.
```
Output: U2paTlJYTkxDZz09Cg==        #wrong
Hint: -1 char.

Final answer: 2paTlJYTkxDZz09Cg==  

- Comparison Operators
- Arithmetic

### 3. Script Control
- Input and Output Control
- Flow Controls - Loops
- Flow Control - Branches

### 4. Execution Flow
- Functions
- Debugging

