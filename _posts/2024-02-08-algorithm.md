---
title: Recursion
date: 2024-02-08 00:23
categories: [Studies, Algorithm]
tags: [algorithm] # TAG names should always be lowercase
---

Recursion is a method where the solution to a problem depends on solutions to smaller instances of the same problem.

Recursion requires a base case.
Without the base case, the fuction will iterate without stopping.

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
    if n > 10:
        return
    else:
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
    if n < 0:
        raise ValueError("The input must be a non-negative integer")
    elif n <= 1:
        return 1
    else:
        return n * Factorial(n - 1)

print(Factorial(6))

```

    720

## Fibonacci

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
    if n == 0:
        return 0
    elif n == 1:
        return 1
    elif n > 1:
        return Fibonacci(n - 1) + Fibonacci(n - 2)
    else:
        raise ValueError("Negative integer is invalid")

print(Fibonacci(6))

```
