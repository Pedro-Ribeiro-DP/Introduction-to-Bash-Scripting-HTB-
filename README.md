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

🧩 Exercise

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
> $ chmod +x exercise.sh         (#chmod (grant permissions) +x (to execute) exercise.sh (name))
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

  🧩 Exercise

**Task:**  
Create a `For` loop that encodes the variable `var` 28 times in `base64`. The number of characters in the 28th hash is the value that must be assigned to the `salt` variable.


**Exercise Script (starter code):**
```bash
#!/bin/bash

# Decrypt function
function decrypt {
	MzSaas7k=$(echo $hash | sed 's/988sn1/83unasa/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/4d298d/9999/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/3i8dqos82/873h4d/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/4n9Ls/20X/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/912oijs01/i7gg/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/k32jx0aa/n391s/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/nI72n/YzF1/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/82ns71n/2d49/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/JGcms1a/zIm12/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/MS9/4SIs/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/Ymxj00Ims/Uso18/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/sSi8Lm/Mit/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/9su2n/43n92ka/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/ggf3iunds/dn3i8/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/uBz/TT0K/g')

	flag=$(echo $MzSaas7k | base64 -d | openssl enc -aes-128-cbc -a -d -salt -pass pass:$salt)
}

# Variables
var="9M"
salt=""
hash="VTJGc2RHVmtYMTl2ZnYyNTdUeERVRnBtQWVGNmFWWVUySG1wTXNmRi9rQT0K"

# Base64 Encoding Example:
#        $ echo "Some Text" | base64

# <- For-Loop here

# Check if $salt is empty
if [[ ! -z "$salt" ]]
then
	decrypt
	echo $flag
else
	exit 1
fi
```
✅ Answer

Terminal: 
> $ nano decode.sh
> 
> $ ./decode.sh                (#try running the "exercise.sh")
> 
> #Permission denied
> 
> $ chmod +x decode.sh         (#chmod (grant permissions) +x (to execute) exercise.sh (name))
> 
> $ ./decode.sh                (#run/execute)
> 
> *** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
HTBL00p5r0x



```bash
#!/bin/bash
# The line above (shebang) specifies that the script should be executed with the Bash interpreter.

# Defines the decryption function that will be called later.
function decrypt {
    # The following chain of 'sed' commands modifies the input hash. This is a form of obfuscation
    # that alters the hash string before it's passed to OpenSSL.
	MzSaas7k=$(echo $hash | sed 's/988sn1/83unasa/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/4d298d/9999/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/3i8dqos82/873h4d/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/4n9Ls/20X/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/912oijs01/i7gg/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/k32jx0aa/n391s/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/nI72n/YzF1/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/82ns71n/2d49/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/JGcms1a/zIm12/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/MS9/4SIs/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/Ymxj00Ims/Uso18/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/sSi8Lm/Mit/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/9su2n/43n92ka/g')
	Mzns7293sk=$(echo $MzSaas7k | sed 's/ggf3iunds/dn3i8/g')
	MzSaas7k=$(echo $Mzns7293sk | sed 's/uBz/TT0K/g')

    # Finally, it attempts to decrypt the modified hash using AES-128-CBC.
    # The password for decryption is composed of the string 'pass:' followed by the calculated $salt.
	flag=$(echo $MzSaas7k | base64 -d | openssl enc -aes-128-cbc -a -d -salt -pass pass:$salt)
}

# Variable declaration and initialization.
var="9M"
salt=""
hash="VTJGc2RHVmtYMTl2ZnYyNTdUeERVRnBtQWVGNmFWWVUySG1wTXNmRi9rQT0K"

# Starts a loop that will execute 28 times.
for i in {1..28}
do
    # In each iteration, the content of 'var' is Base64 encoded.
    # Crucially, 'echo' without '-n' adds a newline character ('\n') to the output,
    # which gets included in the Base64 encoding at every step. This behavior is key to the solution.
	var=$(echo $var | base64)
done # End of the loop.

# After the loop, the salt is calculated.
# 'echo $var | wc -c' counts all characters in the final hash PLUS the trailing newline from 'echo'.
# This results in a salt value of (length of var + 1).
salt=$(echo $var | wc -c)

# Beginning of the final conditional check.
# It verifies if the 'salt' variable is not empty ('! -z').
if [[ ! -z "$salt" ]]
then
    # If 'salt' has a value, the decrypt function is called.
	decrypt
    # The resulting flag from the decryption is printed to the screen.
	echo $flag
else
    # If, for some reason, 'salt' is empty, the script exits with an error status code.
	exit 1
fi # End of the conditional structure.
```
Final answer: HTBL00p5r0x

- Flow Control - Branches

### 4. Execution Flow
- Functions
- Debugging

