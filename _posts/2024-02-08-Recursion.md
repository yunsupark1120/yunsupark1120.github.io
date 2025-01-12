---
title: Recursion
date: 2024-02-08 00:23
categories: [Programming, Algorithm]
tags: [algorithm, programming, python, recursion] # TAG names should always be lowercase
image: assets/img/algorithm/Background.jpg
---

**This is a first post in Algorithm series.**

Recursion in algorithms is a method where a problem is solved by breaking it down into smaller instances of the same problem. This approach involves a function calling itself with a smaller input until it reaches a condition known as the base case, which is simple enough to be solved directly. Once the base case is reached, the solution to that base case is used to solve the other instances of the problem, building up to the solution of the original problem.

1. The base case is the condition to stop the recursion
2. The recursive case is the part where the function calls on itself.

## print 1 to 10 using recursive function

without recursion, the code would look like this:

```python
for i in range(11):
    print(i)
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10

same task done with recursion:

```python

def printNum(n = 1):
    if n > 10: #This is a base case
        return
    else: # This is a recursive case
        print(n)
        printNum(n + 1)

printNum()
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10

## Factorial

factorial is a function that multiplies a number by every number below it till 1

without recursion:

```python
n = 6
num = 1
for i in range(n):
    num *= n
    n -= 1
print(num)
```

    720

with recursion:

```python

def Factorial(n):
    num = 1
    if n < 0: # This is a Boundary Case
        raise ValueError("The input must be a non-negative integer")
    elif n <= 1: # This is a base case
        return 1
    else: # This is a recursive case
        return n * Factorial(n - 1)

print(Factorial(6))

```

    720

## Fibonacci

Fibonacci sequence is a sequence in which each number is the sum of the two preceding ones.

without recursion:

```python


n = 6
a_1 = 0
a_2 = 1
for i in range(n - 1):
    a_1, a_2 = a_2, a_1 + a_2
print(a_2)

```

    8

```python

def Fibonacci(n):
    if n == 0: # This is a base case
        return 0
    elif n == 1: # This is another base case
        return 1
    elif n > 1: # This is a recursive case
        return Fibonacci(n - 1) + Fibonacci(n - 2)
    else: # This is a boundary case
        raise ValueError("Negative integer is invalid")

print(Fibonacci(6))

```

_"To understand recursion, one must first understand recursion."_

_-Stephen Hawking-_
