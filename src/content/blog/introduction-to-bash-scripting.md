---
author: Jobayer Hossain
pubDatetime: 2022-09-23T15:22:00Z
modDatetime: 2023-12-21T09:12:47.400Z
title: Introduction to Bash Scripting
slug: introduction-to-bash-scripting
featured: true
draft: false
tags:
  - DevOps
  - bash
description:
    An introduction to Bash Scripting. Learn how to create simple scripts for task automation and system administration.
---


![Introduction to Bash Scripting](/content/introduction-to-bash-scripting.png)

Bash (Bourne Again SHell) is a scripting language for automating tasks, processing commands, and managing systems, commonly used in Unix and Linux.

This article covers the basics of Bash scripting and how to create simple scripts for task automation and system administration.

To start we have to create an empty file with the `.sh` extension. For example, `script.sh`. here `sh` stands for shell script.

And then we have to add the following line at the top of the file to tell the system that this is a bash script.

```bash
#!/bin/bash
```

this is called a shebang line. It tells the system that this script should be executed using the bash shell. there are other shells like `sh`, `zsh`, `ksh`, etc. it is manly used for compatibility reasons. but bash is the most popular shell and it is available in almost all Unix and Linux systems.

Now let's write a simple script that prints "Hello, World!" to the terminal.

```bash
#!/bin/bash

echo "Hello, World!"
```

To run the script, we have to make it executable permission. we can do that by running the following command `chmod +x script.sh`. this command gives the script executable permission. after that, we can run the script by running `./script.sh`.

it will print `Hello, World!` to the terminal.

Here `chmod +x` is a command to change the file permission. `+x` means executable permission. `./script.sh` is a command to run the script.

## Variables

Variables are used to store data in a script. we can use variables to store strings, numbers, and other data types.

To declare a variable, we have to write the variable name followed by an equal sign and the value of the variable. for example, `name="Jon Doe"`.

```bash
#!/bin/bash
name="Jon Doe"
```

To access the value of a variable, we have to use the dollar sign `$` followed by the variable name. for example, `$name`.

```bash
#!/bin/bash
name="Jon Doe"
echo "Hello, $name"
```

this script will print `Hello, Jon Doe` to the terminal.

The `echo` command prints text to the terminal. For variables, use double quotes (`"`) instead of single quotes (`'`), and ensure no spaces around the equal sign (`=`).

in variables, we can store numbers as well.

```bash
#!/bin/bash
age=30
echo "I am $age years old"
```

this script will print `I am 30 years old` to the terminal.

In variables, we can store arrays as well.

```bash
#!/bin/bash
fruits=("Apple" "Banana" "Orange")
echo "I like ${fruits[0]}"
```

this script will print `I like Apple` to the terminal. as we can see we have to use `${fruits[0]}` to access the first element of the array.

## User Input

In some cases, we need to take input from the user. we can use the `read` command to take input from the user. let's say we want to take the user's name as input. to take the user's name as input bash use the `read` command followed by the variable name.

```bash
#!/bin/bash
echo "Enter your name:"
read name
echo "Hello, $name"
```

When a value is entered, it is stored in the variable `name`. The `read` command waits for the user to enter a value and press Enter. So the user can enter their name and press Enter, and the script will print `Hello, <name>` to the terminal.

## Conditional Statements

Conditional statements are used to make decisions in a script. it allows us to execute different code blocks based on certain conditions. i.e if a condition is true then execute a block of code otherwise execute another block of code. Let's say an example.

```bash
#!/bin/bash
isRaining=true

if [ $isRaining = true ]; then
  echo "Take an umbrella"
fi
```

Here we have a variable `isRaining` with a value of `true`. we are checking if the value of `isRaining` is `true` then print `Take an umbrella` to the terminal. the `if` statement is followed by the condition in square brackets `[ ]` and then the `then` keyword. the code block inside the `if` statement is executed if the condition is true. and to end the `if` statement we have to use the `fi` keyword which is `if` in reverse.

we can also use the `else` keyword to execute a block of code if the condition is false.

```bash
#!/bin/bash
isRaining=false

if [ $isRaining = true ]; then
  echo "Take an umbrella"
else
  echo "Enjoy the weather"
fi
```

Here we have a variable `isRaining` with a value of `false`. we are checking if the value of `isRaining` is `true` then print `Take an umbrella` to the terminal. otherwise print `Enjoy the weather` to the terminal.

there are another keyword `elif` which is used to check multiple conditions.

```bash
#!/bin/bash
isRaining=false
isSunny=true

if [ $isRaining = true ]; then
  echo "Take an umbrella"
elif [ $isSunny = true ]; then
  echo "Wear sunglasses"
else
  echo "Enjoy the weather"
fi
```

`elif` is short for `else if`. it is used to check multiple conditions. if the first condition is false then it checks the next condition. if all conditions are false then the `else` block is executed. in our example, if `isRaining` is true then print `Take an umbrella` to the terminal. if `isRaining` is false and `isSunny` is true then print `Wear sunglasses` to the terminal. otherwise print `Enjoy the weather` to the terminal.

## Comparison Operators

Comparison operators are used to compare values in conditional statements. So we can make decisions based on the comparison results. here are some comparison operators that are used in bash scripting.

- `-eq` - equal to (numeric) i.e `if [ 1 -eq 1 ]`
- `-ne` - not equal to (numeric) i.e `if [ 1 -ne 2 ]`
- `-gt` - greater than (numeric) i.e `if [ 2 -gt 1 ]`
- `-lt` - less than (numeric) i.e `if [ 1 -lt 2 ]`
- `-ge` - greater than or equal to (numeric) i.e `if [ 2 -ge 1 ]`
- `-le` - less than or equal to (numeric) i.e `if [ 1 -le 2 ]`
- `=` - equal to (string) i.e `if [ "hello" = "hello" ]`
- `!=` - not equal to (string) i.e `if [ "hello" != "world" ]`
- `-z` - empty string i.e `if [ -z "" ]`
- `-n` - not empty string i.e `if [ -n "hello" ]`

## Loops

Loops are used to repeat a block of code multiple times. Let's see two types of loops in bash scripting.

- `for` loop
- `while` loop

### For Loop

The `for` loop is used to iterate over a list of items. let's say we want to print numbers from 1 to 5.

```bash
#!/bin/bash

for number in 1 2 3 4 5; do
  echo $number
done
```

for loop starts with the `for` keyword followed by the variable name `number` and the list of items `1 2 3 4 5`. then the `do` keyword and the code block to execute. and to end the loop we have to use the `done` keyword. So here the loop start with the first item `1` and print it to the terminal. then the loop continues with the next item `2` and print it to the terminal. and so on until the last item `5`. inside code block we can run any command or code block and we can use the variable `number` to access the current item.

### While Loop

Compared to the `for` loop, the `while` loop is used to repeat a block of code until a condition is true. let's say we want to print numbers from 1 to 5 using the `while` loop.

```bash
#!/bin/bash

number=1

while [ $number -le 5 ]; do
  echo $number
  number=$((number + 1))
done
```

while loop starts with the `while` keyword and the condition in square brackets `[ ]`. then the `do` keyword and the code block to execute. and to end the loop we have to use the `done` keyword. So here the loop starts with the variable `number` with a value of `1`. then it checks if the value of `number` is less than or equal to `5`. if the condition is true then it prints the value of `number` to the terminal and increments the value of `number` by `1`. then it checks the condition again. if the condition is false then the loop ends. so the loop prints numbers from `1` to `5` to the terminal.

## Functions

Functions are used to group a block of code and execute it multiple times. it helps to organize the code and make it reusable. let's say we want to create a function that prints `Hello, World!` to the terminal.

```bash
#!/bin/bash

function sayHello() {
  echo "Hello, World!"
}

sayHello
```

In bash scripting, we can create a function using the `function` keyword followed by the function name `sayHello()` and then include the code block to execute within curly braces `{}`. Inside this code block, any desired command or code can be run when the function is called. Let's print `Hello, World!` to the terminal for now. To call the function, simply write its name - in this case, `sayHello`. This will print `Hello, World!` to the terminal.

A function can take arguments as well. let's say we want to create a function that takes a name as an argument and prints `Hello, <name>` to the terminal.

```bash
#!/bin/bash

function sayHello() {
  echo "Hello, $1"
}

sayHello "Jon Doe"
```

Here we have a function `sayHello` that takes an argument `$1`. the argument `$1` is the first argument passed to the function. so when we call the function `sayHello "Jon Doe"` it passes the value `Jon Doe` to the function. and the function prints `Hello, Jon Doe` to the terminal.
