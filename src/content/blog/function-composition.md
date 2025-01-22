---
author: Jobayer Hossain
pubDatetime: 2022-09-23T15:22:00Z
modDatetime: 2023-12-21T09:12:47.400Z
title: Function Composition in JavaScript - Functional Programming in JavaScript
slug: function-composition-in-java-script-functional-programming-in-java-script
featured: true
draft: false
tags:
  - Software Design
  - JavaScript
description:
    Function Composition are a core concept in functional programming. Learn what they are and how to use them in JavaScript.
---


In this article, we will learn about function composition in JavaScript. Starting with an example without function composition and then we will see how we can do the same thing using function composition. We will also learn why we should use function composition and how to use it in JavaScript.

![Function Composition in JavaScript](/content/function-composition.png)

## Why use Function Composition?

- Code reusability and modularity.
- Easier to test code.
- Flexibility to change the order of execution of functions.

## Without Function Composition

Let's start with a real world example where we will calculate the savings of a person. We will write a function that will calculate the savings of a person based on his income and expenses.

```js
const income = 1000;
const rent = 300;
const food = 200;
```

Here we have three variables. `income` is the income of a person, `rent` is the rent of his house and `food` is the cost of his food. Now we will write a functions which will be used to calculate the expenses of a person based on his income and expenses.

```js
const deductRent = (income) => income - rent;
const deductFood = (income) => income - food;
```

Here we have two functions. `deductRent` will deduct the rent from the income and `deductFood` will deduct the food cost from the income & return the left amount. Now we will write a function which will calculate the savings of a person based on his income and expenses.

```js
const afterRent = deductRent(income); // 700
const afterFood = deductFood(afterRent) // 500
```

Here we have two variables. `afterRent` will calculate the amount left after deducting the rent from the income and `afterFood` will calculate the amount left after deducting the food cost from the income. And this is how we can calculate the savings of a person based on his income and expenses normally.

Now let's see how we can do the same thing using function composition.

## With Function Composition

In the previous example, we saw how we can calculate the savings of a person based on his income and expenses normally. Now let's see how we can do the same thing using function composition. First we will start with the same variables and easier way to write the functions.

```js
const income = 1000;
const rent = 300;
const food = 200;
```

```js
const deductRent = (income) => income - rent;
const deductFood = (income) => income - food;
```

To get start with function composition we have multiple ways to achieve the same thing. First we will start with the most easiest way to write the function composition.

#### Using nested arguments in functions

In this method we will pass the nested functions as arguments to the variable. And it will return the value.

```js
const savings = deductFood(deductRent(income)); // 500
```

In the above example we first called the `deductRent` function with the `income` variable as argument and it returned the value. Then we passed the returned value to the `deductFood` function as argument and it returned the value. And finally we stored the returned value in the `savings` variable and it returns our expected result. which is most easiest way to write the function composition. But we can also write the same thing in a different way.

#### Using `compose` function

Compose function is a function which accepts multiple functions as arguments and returns a function. We can use this function to compose multiple functions together. So that we didn't have to pass nested functions as arguments to the `savings` function.

```js
const compose = (...fns) => {
    const inner = (arg) => {
      let  result = fns[0](arg)
        for(let i = 1; i < fns.length; i++) {
            result = fns[i](result)
        }
        return result
    }
    return inner
}
```

If you are not familiar with the `...` operator, it's called the spread operator. It's used to spread the elements of an array or object.

In the above example we have a function called `compose` which accepts multiple functions as arguments and returns a function. Inside the `compose` function we have another function called `inner` which accepts an argument and returns a value. Inside the `inner` function we have a variable called `result` which will store the result of the functions. Then we have a for loop which will loop through the functions and call them one by one. And finally we will return the `result` variable.

Now we can use the `compose` function to compose the `deductRent` and `deductFood` functions together as parameters.

```js
const savings = compose(deductFood, deductRent)

console.log(savings(income)) // 500
```

Here in savings function we passed the `deductFood` and `deductRent` functions as arguments to the `compose` function. And it returned a function which we stored in the `savings` variable. Then we called the `savings` function with the `income` variable as argument and it returned our desired result. In this `compose` function It will first call the `deductFood` function and then it will call the `deductRent` function with the result of the `deductFood` function as argument. Here we have an problem because in compose function by nature it should call the functions from right to left. But in our case it's calling the functions from left to right. So we need to fix this problem.

```js
const compose = (...fns) => {
    const inner = (arg) => {
      let  result = fns[fns.length - 1](arg)
        for(let i = fns.length - 2; i >= 0; i--) {
            result = fns[i](result)
        }
        return result
    }
    return inner
}
```

To fix this problem we modified the loop execution order inside `compose` function. Now it will call the functions from right to left.

##### Optimizing the `compose` function

We can also optimize the `compose` function by using the `reduceRight` method. It will reduce the array from right to left and return a single value. and we don't have to use the `for` loop anymore.

Here is the final code of the `compose` function using `reduceRight` method.

```js
    const compose = (...fns) => {
        const inner = (arg) => {
            return fns.reduceRight((acc, fn) => fn(acc), arg)
        }
        return inner
    }
```

reduceRight method is a method which accepts a callback function as argument and returns a single value. The callback function accepts two arguments. The first argument is the accumulator and the second argument is the current value. The callback function will be called for each element of the array and it will return a single value. and in our case we are calling the functions one by one and returning a single value.

So the code will be much cleaner and easier to read Here is the final code of the `compose` function using `reduceRight` method.

```js
const income = 1000;
const rent = 500;
const food = 200;

const deductRent = (income) => income - rent;
const deductFood = (income) => income - food;

const compose = (...fns) => {
  const inner = (arg) => {
    return fns.reduceRight((acc, fn) => fn(acc), arg);
  };
  return inner;
};

const savings = compose(deductFood, deductRent);
console.log(savings(income));
```

## Conclusion

Function composition is a core concept in functional programming. It's a way of combining multiple functions to create a new function. In this article, we learned what function composition is and how to use it in JavaScript. I hope you enjoyed this article. If you have any questions or feedback, feel free to reach out to me on [Twitter](https://twitter.com/jobayerdev).
