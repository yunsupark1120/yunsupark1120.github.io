---
title: Searching Algorithms
date: 2024-02-14 10:39
categories: [Programming, Algorithm]
tags: [algorithm, programming, python, c++, recursion] # TAG names should always be lowercase
math: true
image: assets/img/algorithm/Background.jpg
---

**This is a third post in Algorithm series.**

In this post, we\'ll discuss the algorithms for searching an element in
an array. There are many searching algorithms, but in this post, I will
introduce the two most popular algorithms:

1.  Linear Search
2.  Binary Search

## Introduction

Searching is the process of finding a particular element from a
collection of data. Thanks to the built in functions in most programming
languages like Python, programmers rarely need to implement the
searching algorithms on their own. However, understanding these
algorithms is a first step to understanding sophisticated algorithms and
move further.

## Linear Search

Linear search is the simplest searching algorithm that searches for an
element in a list in sequential order. It is also known as a sequential
search. It is a brute-force algorithm that checks each element of the
list until a match is found or the whole list has been searched.

### Performance

The time complexity of the linear search algorithm is ${O(n)}$.

This is because in the worst case, the algorithm will have to repeat the
searching process n times, where n is the number of elements in the
list.

- pros:
  - It is simple and easy to implement.
  - It is effective for small datasets.
  - The list does not need to be sorted.
- cons:
  - It is not the most efficient algorithm.
  - It may take a long time for large datasets.

### Pseudocode

The pseudocode for the linear search algorithm is as follows:

    function linear_search(list, target):
        for each element in the list:
            if the element is equal to the target:
                return the index of the element
        return -1

### Implementation

Here is a simple implementation of the linear search algorithm in
Python:

```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
```

Here is a simple implementation of the linear search algorithm in C++:

```cpp
int linear_search(int arr[], int target){
    int n = sizeof(arr)/sizeof(arr[0]);

    for(int i = 0; i < n; i++){
        if(arr[i] == target){
            return i;
        }
    } return -1;
}
```

### Example

Let\'s consider an example to understand the linear search algorithm.
Suppose we have a list of numbers:

    arr = [5, 3, 8, 6, 2, 7, 1, 4]

We want to search for the number 7 in the list. The linear search
algorithm will search for the number 7 in the list and return the index
of the number if it is found. If the number is not found, the algorithm
will return -1.

```python
arr = [5, 3, 8, 6, 2, 7, 1, 4]
target = 7
print(linear_search(arr, target)) # Output: 5
```

The algorithm starts to compare the target with each element of the
list. When it finds the number 7 at index 5, it returns the index 5.

## Binary Search

Binary search is a fast searching algorithm with a time complexity of
${O(\log n)}$. It is a divide and conquer algorithm that works on a
sorted array. It repeatedly divides the search interval in half and
compares the target value to the middle element of the array. If the
middle element is equal to the target, then the search is successful. If
the middle element is greater than the target, then the search continues
in the left half of the array. If the middle element is less than the
target, then the search continues in the right half of the array.

### Performance {#performance}

The time complexity of the binary search algorithm is ${O(\log n)}$.

This is because the algorithm divides the list in half at each
iteration, which reduces the search interval by half at each step.

- pros:
  - It is efficient for large datasets.
  - It is faster than linear search.
- cons:
  - The list must be sorted.
  - It is not effective for small datasets.

### Pseudocode {#pseudocode}

The pseudocode for the binary search algorithm is as follows:

    function binary_search(arr, target):
        left = 0
        right = length of arr - 1
        while left <= right:
            mid = (left + right) // 2
            if arr[mid] == target:
                return mid
            elif arr[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return -1

### Implementation {#implementation}

Here is a simple implementation of the binary search algorithm in
Python:

```python
def binary_search(arr, target):
    left = 0
    right = len(arr) - 1

    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1
```

Here is a simple implementation of the binary search algorithm in C++:

```cpp
int binary_search(int arr[], int target){
    int n = sizeof(arr)/sizeof(arr[0]);

    int left = 0;
    int right = n - 1;

    while(left <= right){
        int mid = (left + right) / 2;
        if(arr[mid] == target){
            return mid;
        } else if(arr[mid] < target){
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    } return -1;
}
```

### Example {#example}

Let\'s consider an example to understand the binary search algorithm.
Suppose we have a sorted list of numbers:

```python
arr = [1, 2, 3, 4, 5, 6, 7, 8]
```

We want to search for the number 6 in the list. The binary search
algorithm will compare the target with the middle element of the list
and drop the unnecessary half of the list. This process will continue
until the target is found or the list is empty. If the number is found,
the algorithm will return the index of the number. If the number is not
found, the algorithm will return -1.

```python
left = 0
right = len(arr) - 1 # length of the input list - 1 = 7

# in the first iteration:
mid = (left + right) // 2 # (0 + 7) // 2 = 3
arr[mid] = 4 # arr[3] = 4
arr[mid] < target # 4 < 6
```

Because the middle element is less than the target, there is no need to
investigate the left half. The algorithm will continue to search in the
right half of the list.

```python
left = mid + 1 # 3 + 1 = 4
right = 7

# in the second iteration:
mid = (left + right) // 2 # (4 + 7) // 2 = 5
arr[mid] = 6 # arr[5] = 6
arr[mid] == target # 6 == 6
```

### Recursive Binary Search

As the example above implies, the binary search algorithm is a
repetition of the same process. This makes it a good candidate for a
recursive implementation. Here is a simple implementation of the binary
search algorithm using recursion:

```python
def binary_search(arr, target, left = 0, right = None):
    if right is None:
        right = len(arr) - 1

    if left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            return binary_search(arr, target, mid + 1, right) # search in the right half
        else:
            return binary_search(arr, target, left, mid - 1) # search in the left half

    return -1
```

```cpp
int binary_search(int arr[], int target, int left = 0, int right = -1){
    int n = sizeof(arr)/sizeof(arr[0]);

    if(right == -1){
        right = n - 1;
    }

    if(left <= right){
        int mid = (left + right) / 2;
        if(arr[mid] == target){
            return mid;
        } else if(arr[mid] < target){
            return binary_search(arr, target, mid + 1, right);
        } else {
            return binary_search(arr, target, left, mid - 1);
        }
    } return -1;
}
```
