---
layout: project
type: project
title: "Abstract Data Type: List"
date: 2020
published: True
labels:
  - C
  - Abstract Data Type
  - 
summary: "A program in C that creates an abstract Data Type: Singly Linked List."
---
In this coding project, I delve into abstract data types using C, focusing on linked lists. The project's goal is clear: gain a profound understanding of dynamic memory allocation while ensuring the release of every allocated byte.

The foundation is a crafted `node` struct representing each element in our linked list.

<img width="200px" src = "../img/struct.png" class="img-thumbnail" img>

We dynamically allocate memory for new nodes through the `add` function, gracefully handling situations where memory allocation may fail.

<img width="300px" src = "../img/add.png" class="img-thumbnail" img>

We traverse the list, print its contents, and ultimately free up the allocated memory in the `free_list` function.

<img width="300px" src = "../img/Print-free.png" class="img-thumbnail" img>

This project serves as a practical exploration of linked lists and a robust exercise in memory management within the confines of C. 
