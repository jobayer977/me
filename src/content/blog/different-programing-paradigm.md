---
author: Jobayer Hossain
pubDatetime: 2022-09-23T15:22:00Z
modDatetime: 2023-09-07T09:12:47.400Z
title: Different Programing Paradigm
slug: different-programing-paradigm
featured: true
draft: false
tags:
  - Software Design
description:
    An explanation of the different programming paradigms.
---


In this article, We will learn about different programming paradigms.And it's use cases.

![Different Programing Paradigm](/content/different-programing-paradigm.png)

## The Concept of Programming Paradigm

Programming paradigm is the style or approach used in writing computer programs. It defines the structure and organization of code. It also defines the how the program will execute. There are many different programming paradigms. Some of them are:

- Imperative programming
- Functional programming
- Object-oriented programming
- Logic programming
- Declarative programming

## Do we need to know about it ?

Knowing about different programming paradigms isn't a must, but it's good general knowledge for every programmer. It helps you understand various programming languages and their pros and cons.

Let's start with the Imperative programming.

## Imperative Programming

Imagin you are writing a program to calculate the sum of the first 10 natural numbers. In imperative programming, approach would be to write every single step to do the task. Let's see how we can solve the problem in imperative programming:

```js
let sum = 0;
let i = 1;

while (i <= 10) {
  sum += i;
  i++;
}

console.log(sum);
```

Here we will create a variable called `sum` and initialize it with 0. Then we will create another variable called `i` and initialize it with 1. Then we will create a `while` loop and we will check if `i` is less than or equal to 10. If it is, then we will add `i` to `sum` and increment `i` by 1. We will repeat this process until `i` is greater than 10. Then we will print the `sum` variable. So overall, we specified every single step to do the task.

Now let's see how we can solve the same problem without following the imperative programming approach:

```js
const sum = 10 * (10 + 1) / 2;
console.log(sum);
```

In this approach, Create a variable called `sum` and then multiply 10 with 10 + 1 and then divide it by 2. This is an simple math formula to calculate the sum of the first 10 natural numbers. So overall, we didn't specify every single step to do the task. This is the difference between imperative programming and other programming paradigms.

## Functional Programming

Now let's see how we can solve the same problem using functional programming. In functional programming, we don't specify the steps to do the task. Instead, we specify what we want to do. In functional programming, we use functions to do the task. Let's see how we can solve the same problem:

```js
const numbersArray = Array.from({ length: 10 }, (_, index) => index + 1);

const sum = numbersArray.reduce((acc, num) => acc + num);

console.log(sum);

```

Here we created an array of 10 numbers using the `Array.from` function. Then we used the `reduce` function to calculate the sum of the array. So overall, we didn't specify the steps to do the task. Instead, we specified what we want to do.

Let's move on to the next Object-oriented programming approach.

## Object-oriented Programming

Object-oriented programming is a bit different from the other programming paradigms. In object-oriented programming, we create objects and we use those objects to do the task. Now let's see how we can solve the same problem using object-oriented programming:

```js
class Sum {
  constructor() {
    this.sum = 0;
  }

  add(num) {
    this.sum += num;
  }

  getSum() {
    return this.sum;
  }
}

const sum = new Sum();

for (let i = 1; i <= 10; i++) {
  sum.add(i);
}

console.log(sum.getSum());
```

In object-oriented programming, everything is handled using objects and classes, where objects have properties and methods to solve problems.

Here we created a class called `Sum`. The class has a property called `sum` which is initialized with 0. The class also has two methods called `add` and `getSum`. The `add` method adds the given number to the `sum` property. The `getSum` method returns the `sum` property.

## Logic Programming

In logic programming, we specify the rules and facts. Then we ask the computer to find the solution. Let's see how we can solve the same problem using logic programming:

```js
const sum = (n) => {
  if (n === 1) {
    return 1;
  }

  return n + sum(n - 1);
};

console.log(sum(10));
```

Here we first create a function called `sum`. The function takes a number as an argument. If the number is 1, then we return 1. Otherwise, we return the number plus the sum of the number minus 1. So overall, we specified the rules and facts. Then we asked the computer to find the solution. it's an recursive function. So it will call itself until the number is 1.

## Declarative Programming

It is a style of programming where the programmer specifies what the program should accomplish by describing the problem, rather than describing how the program should accomplish the task. like functional programming, we don't specify the steps to do the task. Instead, we specify what we want to do.

Let's see how we can solve the same problem using declarative programming:

```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const sum = numbers.reduce((accumulator, currentNumber) => accumulator + currentNumber, 0);
console.log(sum);

```

We will create an array of 10 numbers. Then we will use the `reduce` function to calculate the sum of the array. So overall, we didn't specify the steps to do the task. Instead, we specified what we want to do.

## Conclusion

So basically, they all are different approaches to solve a problem. They all have their pros and cons. Some programming languages support multiple programming paradigms. For example, JavaScript supports imperative, functional, object-oriented, and declarative programming. Some programming languages only support one programming paradigm. For example, Prolog only supports logic programming. So it's up to you to choose the right programming paradigm for your project.
