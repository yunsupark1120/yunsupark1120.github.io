---
title: Linked List
date: 2024-02-12 23:23
categories: [Programming, Data Structure]
tags: [algorithm, datastructure, programming, python, list] # TAG names should always be lowercase
math: true
image: assets/img/DataStructure/Background.jpg
---

**This is a second post in Data Structure series.**

## Introduction

A linked list is a linear data structure where each element is a separate object.
A linked list, like an array, can store, add, remove, and search for data. However, an element in a linked list is not stored continuously in memory and does not have an index.

A linked list stores data in _node_. Each node consist of two parts: data and a reference to the next node in the sequence.
The first node is called the _head_ and the last node is called the _tail_. The tail node is the node that has a reference to `None`.

A linked list is a dynamic data structure, which means that the size of the list can change during the execution of the program. Also, the size and the type of the data can be vary in a linked list.

## Types of Linked List

- **Singly linked list**: Each node contains a data and a reference to the next node.
- **Doubly linked list**: Each node contains a data and two references to the next and previous node.
- **Circular linked list**: Last node contains a reference to the first node as the next node and the first node has a reference to the last node as the previous node.

## Performance of a Linked List

![Performance Chart](assets/img/DataStructure/DataStructurePerformance.jpg)

- A linked list, unlike an array, does not have to push every single element to a new memory for inserting a new element. It only needs to change the reference of the previous node to the new node.

- Since a linked list does not have an index, searching for an element in a linked list is slower than an array. To find an element in a linked list, the program has to traverse the list from the head to the tail.

- A linked list must contain a reference to the next node, so it uses more memory than an array.

## Linked List Class

below is a Python implementation of a singly linked list.

### Implementation

```python
class Node:
    def __init__(self, data, next=None):
        self.data = data # data
        self.next = next # reference to the next node (this is a pointer)

class LinkedList:
    def __init__(self):
        self.head = None

    def __str__(self):
        node = self.head
        while node is not None:
            print(node.data)
            node = node.next
        return ""

    def append(self, data):
        if self.head is None:
            self.head = Node(data)
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = Node(data)

    def search(self, data):
        current = self.head
        posistion = 0
        while current is not None:
            if current.data == data:
                return posistion
            posistion += 1
            current = current.next

        return -1

    def remove(self, target):
        if self.head.data == target:
            self.head = self.head.next
            return
        current = self.head
        prev = None
        while current is not None:
            if current.data == target:
                prev.next = current.next
                return
            prev = current
            current = current.next
        raise ValueError("Value not found in the list")

    def insert(self, target, data):
        new_node = Node(data)
        if self.head.data == target:
            new_node.next = self.head.next
            self.head.next = new_node
            return
        current = self.head
        while current:
            if current.data == target:
                new_node.next = current.next
                current.next = new_node
                return
            current = current.next
        raise ValueError("Value not found in the list")

    def update(self, old, new):
        if self.head.data == old:
            self.head.data = new
            return
        current = self.head
        while current:
            if current.data == old:
                current.data = new
                return
            current = current.next
        raise ValueError("Value not found in the list")

    def len(self):
        current = self.head
        count = 0
        while current:
            count += 1
            current = current.next
        return count

    def reverse(self):
        current = self.head
        prev = None
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        self.head = prev

```

### Methods Explained

1. Node Class

   The `Node` class is a blueprint for a node in a linked list. It contains two parts: data and a reference to the next node.

   ```Python
   class Node:
       def __init__(self, data, next=None):
           self.data = data # data
           self.next = next # reference to the next node (this is a pointer)
   ```

2. Constructor

   The constructor initializes the head of the linked list.

   ```Python
   def __init__(self):
       self.head = None
   ```

   By default, the head is `None` because the linked list is empty.

3. **str** Method

   The `__str__` method is called when `print()` is called on an object. This method returns a string representation of the linked list.

   ```Python
   def __str__(self):
       node = self.head
       while node is not None:
           print(node.data)
           node = node.next
       return ""
   ```

   ```Python
   while node is not None:
   ```

   If the `node` has not reached the end of the linked list, `print(node.data)` prints the data of the current node and updates the `node` to the next node.

4. append Method

   The `append` method adds a new node to the end of the linked list.

   ```Python
   def append(self, data):
       new_node = Node(data)
       if self.head is None:
           self.head = new_node
           return
       last_node = self.head
       while last_node.next:
           last_node = last_node.next
       last_node.next = new_node
   ```

   ```Python
   new_node = Node(data)
   ```

   Creates a new node with the given data.

   ```Python
   if self.head is None:
       self.head = new_node
       return
   ```

   If the linked list is empty, the new node becomes the head of the linked list.

   ```Python
   last_node = self.head
   while last_node.next:
       last_node = last_node.next
   ```

   If the linked list is not empty, the program traverses the linked list to find the last node.
   While the next node is not `None`, the program updates the `last_node` to the next node.

   ```Python
   last_node.next = new_node
   ```

   When the last node is found, the next node of the last node is updated to the new node.

5. search method

   The `search` method searches for a node with the given data in the linked list and returns the position of the node.

   ```Python
   def search(self, data):
       current = self.head
       posistion = 0
       while current is not None:
           if current.data == data:
               return posistion
           posistion += 1
           current = current.next

       return -1
   ```

   ```Python
   current = self.head
   posistion = 0
   ```

   Initially, the `current` is the head of the linked list and the `posistion` is 0.

   ```Python
   while current is not None:
       if current.data == data:
           return posistion
   ```

   While the `current` is not `None`, the program checks if the data of the current node is equal to the target data.
   If the data is found, the method returns the position of the node.

   ```Python
   posistion += 1
   current = current.next
   ```

   If the data does not match the target data, the position is incremented by 1 and the `current` is updated to the next node.

   ```Python
   return -1
   ```

   If the target data is not found in the linked list, the method returns -1.

6. remove method

   The `remove` method removes the data from the linked list.

   ```Python
   def remove(self, target):
       if self.head.data == target:
           self.head = self.head.next
           return
       current = self.head
       prev = None
       while current is not None:
           if current.data == target:
               prev.next = current.next
               return
           prev = current
           current = current.next
       raise ValueError("Value not found in the list")
   ```

   ```Python
   if self.head.data == target:
       self.head = self.head.next
       return
   ```

   If the first data is the target data, the head of the list is updated to the next node.

   ```Python
   current = self.head
   prev = None
   ```

   If the first data is not the target data, the `current` is the head of the linked list and the `prev` is `None`.

   ```Python
   while current is not None:
       if current.data == target:
           prev.next = current.next
           return
       prev = current
       current = current.next
   ```

   While the list has not reached the end, the program checks if the data of the current node is equal to the target data.
   If the target data is found, the previous node updates its pointer so that it skips the target node and points to the next node.
   If current data does not match the target data, the previous node and the current node moves one step forward.

   ```Python
   raise ValueError("Value not found in the list")
   ```

   If the target data is not found in the linked list, the method raises a ValueError.

7. insert method

   The `insert` method receives two parameters `target` and `data`. The method inserts a new node with the given data after the node with the target data.

   ```Python
   def insert(self, target, data):
       new_node = Node(data)
       if self.head.data == target:
           new_node.next = self.head.next
           self.head.next = new_node
           return
       current = self.head
       while current:
           if current.data == target:
               new_node.next = current.next
               current.next = new_node
               return
           current = current.next
       raise ValueError("Value not found in the list")
   ```

   The insertion works by updating the pointers of the existing nodes.
   The pointer of the target node is updated to reference the new node, and the pointer of the new node is the original pointer of the target node, before the insertion.

   ```Python
   new_node.next = self.head.next
   self.head.next = new_node
   return

   new_node.next = current.next
   current.next = new_node
   return
   ```

   These codes perform the updating process.

   ```Python
   new_node = Node(data)
   ```

   The method starts by creating a new nmode with the given data.

   ```Python
   if self.head.data == target:
       new_node.next = self.head.next
       self.head.next = new_node
       return
   ```

   If the target data is the first data, the new node is inserted after the head of the linked list.

   ```Python
   while current:
       if current.data == target:
           new_node.next = current.next
           current.next = new_node
           return
       current = current.next
   ```

   If the first data is not the target data, it traverses the linked list by updating the `current` to the next node.
   When the target data is found, the insertion is performed.

   ```Python
   raise ValueError("Value not found in the list")
   ```

   If the target data is not found in the linked list, the method raises a ValueError.

8. update method

   The `update` method receives two parameters `target` and `data`. The method updates the data of the node with the target data to the new data.

   ```Python
   def update(self, old, new):
       if self.head.data == old:
           self.head.data = new
           return
       current = self.head
       while current:
           if current.data == old:
               current.data = new
               return
           current = current.next
       raise ValueError("Value not found in the list")
   ```

   ```Python
   if self.head.data == old:
       self.head.data = new
       return
   ```

   If the first data is the target data, the data of the head node is updated to the new data.

   ```Python
   while current:
       if current.data == old:
           current.data = new
           return
       current = current.next
   ```

   If the first data is not the target data, the program traverses the linked list by updating the `current` to the next node.
   When the target data is found, the data of the node is updated to the new data.

   ```Python
   raise ValueError("Value not found in the list")
   ```

   If the target data is not found in the linked list, the method raises a ValueError.

9. len method

   The `len` method returns the length of the linked list.

   ```Python
   def __len__(self):
       current = self.head
       count = 0
       while current:
           count += 1
           current = current.next
       return count
   ```

   ```Python
   current = self.head
   count = 0
   ```

   Initially, the `current` is the head of the linked list and the `count` is 0.

   ```Python
   while current:
       count += 1
       current = current.next
   ```

   While the list has not reached the end, the program increments the `count` by 1 and updates the `current` to the next node.

   ```Python
   return count
   ```

   When the end of the linked list is reached, the method returns the `count`.

10. reverse method

    The `reverse` method reverses the order of the linked list.

    ```Python
    def reverse(self):
        current = self.head
        prev = None
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        self.head = prev
    ```

    ```Python
    current = self.head
    prev = None
    ```

    Initially, the `current` is the head of the linked list and the `prev` is `None`.

    ```Python
    while current:
        next = current.next
        current.next = prev
        prev = current
        current = next
    ```

    While the list has not reached the end, the program reverses the order of the linked list by updating the pointers of the nodes.
    For example, lets say we have the following linked list:

    ```
    1 -> 2 -> 3 -> 4 -> 5
    ```

    The reverse method works as follows: 0. `current = 1` and `prev = None`

    1. `next = current.next` The next node is saved in the `next` variable
       `next` = 2
    2. `current.next = prev` The next node is replaced with the previous node
       `2` -> `None`
    3. `prev = current` The `prev` variable is updated to the current node
       `prev` = `1`
    4. `current = next` The `current` variable is updated to the next node
       `current` = `2`
    5. The process is repeated until the end of the linked list is reached.

       ```
       1 -> None
       2 -> 1 -> None
       3 -> 2 -> 1 -> None
       4 -> 3 -> 2 -> 1 -> None
       5 -> 4 -> 3 -> 2 -> 1 -> None
       ```
