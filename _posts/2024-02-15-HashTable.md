---
title: Hash Table
date: 2024-02-15 12:03
categories: [Programming, Data Structure]
tags: [algorithm, datastructure, programming, python, dictionary] # TAG names should always be lowercase
math: true
image: assets/img/DataStructure/Background.jpg
---

**This is a fifth post in Data Structure series.**

## Introduction

Associate Array is an abstract data type that stores a value with a key associated with it. In a simpler term, it is a collection of **Key-Value Pairs**. The key is used to access the elements in the collection. The key is mapped to a value, and the value can be retrieved by providing the key. The key is unique, and it is used to identify the value. The value can be anything, such as a string, integer, or even a complex data structure.
A dictionary in Python is an example of an associate array.

A **hash table** is a linear data structure that implements an associative array abstract data type, a structure that can map keys to values. A _hash table_ uses a **hash function** to compute an index into an array of buckets or slots, from which the desired value can be found. Python dictionaries are implemented using hash tables.

A _hash function_ receives a key as a parameter and returns a **has value**, the index of the array where the value is stored in.

```
hash_function(key) -> hash_value -> index -> array[index] = value
```

## Hash Function

A _hash function_ is a function that takes an input (or 'key') and returns a fixed-size string of bytes. The output is typically a fixed-size string of bytes or a fixed-size integer. The output is called the _hash value_.

For example, a simple hash function can be defined as follows:

```python
def hash_function(key, arr):
    return key % len(arr)
```

The above hash function returns the remainder of the key divided by the length of the array, where the values will be stored.

Imagine we have an array of size 7, and have the following keys to store: 21, 29, 86, 38, 39, 40, 90

```
21 % 7 = 0
29 % 7 = 1
86 % 7 = 2
38 % 7 = 3
39 % 7 = 4
40 % 7 = 5
90 % 7 = 6

arr = [21, 29, 86, 38, 39, 40, 90]
```

## Collision

So far, the example array `arr = [21, 29, 86, 38, 39, 40, 90]` has no problem. However, consider the case we receive more keys: 30, 23, 2, 6.

    ```
    30 % 7 = 2
    23 % 7 = 2
    2 % 7 = 2
    6 % 7 = 6
    ```

The returned index are already filled with other values. This is called a **collision**.
To solve this problem, we can use a technique called **chaining**.
_Chaining_ is a technique that allows multiple items to be stored in the same slot of the hash table. Each slot contains a linked list of items. When a collision occurs, the item is added to the linked list at the slot.

```
arr = [21, 29, [86, 30, 23, 2], 38, 39, 40, [90, 6]]

arr[0] = 21
arr[1] = 29
arr[2] = [86, 30, 23, 2]
arr[3] = 38
arr[4] = 39
arr[5] = 40
arr[6] = [90, 6]
```

To find the value of the key 23, we can use the hash function to find the index of the array, and then search the inside list to find the value.

## Performance

![Performance Chart](assets/img/DataStructure/DataStructurePerformance.jpg)

- Unlike other data structures, the operations search, insert, and delete have a time complexity of $O(1)$ on average.
- Hash Table is the most efficient data structure for searching, inserting, and deleting elements, especially for large datasets.
- Accessing _n_ th element is not possible in a hash table.

Implementing a hash table is the most efficient way for searching, and no other searching algorithms can be faster than $O(1)$.
Hash tables are used widely all accross the developing sectors.

For example, the JSON (JavaScript Object Notation) data format is a widely used data interchange format. It is used to store and transmit data between a server and a web application. Using API, JSON can be easily converted to a dictionary in Python.

The key-value DBMS (Database Management System) is another example of a hash table. It is used to store and retrieve data in a database.

The version control system Git also uses a hash table to store the content of the files.

If there is a large dataset, and we need to search, insert, or delete elements, the hash table is the best data structure to use.

If we need to manipulate data in order or have to access the _n_ th element, then we should use other data structures such as an array, or linked list.

## Implementation

To implement a practical hash table data structure, we can use multiple arrays, where one array stores the keys at the index calculated by the hash function, and the other array stores the associated values at the same index.

There is no need to implement a hash table from scratch in Python, as Python already has a built-in dictionary data structure.

```python

hash_table = {}
hash_table['one'] = 1
hash_table['two'] = 2
hash_table['three'] = 3

for key in hash_table:
    print(f"{key}: {hash_table[key]}")

```

## Problem Solving

### Characters in a String

_Given a string, write a function to count the number of times each character appears in the string._

We can solve this problem using a dictionary in Python. We can use the character as the key and the count as the value.

```python
def countChar(word: str) -> dict:
    char_count = {}
    for char in word:
        if char in char_count:
            char_count[char] += 1 # if there is corresponding key, increase the value by 1
        else:
            char_count[char] = 1 # if there is no corresponding key, create a new key and associate a value of 1
    return char_count
```

### Sum of Two Numbers

_Given an array of integers, and a target number, write a function to return the indices of the two numbers that add up to the target number. We can assume that there is only one solution, and the same element cannot be used twice._

For example

```
input = [-1, 2, 3, 4, 7]
target = 5

input[1] + input[2] = 2 + 3 = 5

output = [1, 2]
```

There are multiple ways to solve this problem.

1. Brute Force

```python
def findSum(nums: list, target: int) -> list:
    for i in range(len(nums)):
        for j in range(len(nums)):
            if i != j and nums[i] + nums[j] == target:
                return [i, j]
    return []
```

This solution has a time complexity of $O(n^2)$, and it is not efficient.

We can approach this problem using a hash table data structure.

```python
def twoSum(nums: list, target: int) -> list:
    num_dict = {}
    for index, n in enumerate(nums):
        rem = target - n
        if rem in num_dict:
            return [num_dict[rem], index]
        else:
            num_dict[n] = index
```

```python
num_dict = {}
```

First, we create an empty dictionary to keep track of the index of the elements in the input list.
Later in this dictionary, the key will be the elements of the input list, and the value will be the index of the elements.

```python
for index, n in enumerate(nums):
    rem = target - n
```

Using the `enumerate` function, we can iterate through the list and get the _index_ and the _value_ of the element. After that, we assign the value of `target - n` to the variable `rem`.

```python
if rem in num_dict:
    return [num_dict[rem], index]
```

If the value of `rem` is already in the dictionary, we return the index of the value of `rem` and the current index.
This is because `rem = target - n`, thus `target = rem + n`. If the `rem` value is already in the dictionary, we can access the value associated with the `rem` key (which is the index from the input list), and the current index to get the indices of the two numbers that add up to the target number.

```python
else:
    num_dict[n] = index
```

If the value of `rem` is not in the dictionary, we add the current value `n` to the dictionary with the index as the value, and move on to the next iteration.
