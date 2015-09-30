---
layout: post
title:  "What's the Point"
date:   2015-09-22 19:56:24
---

# Memory Management

Memory allocation either happens at compile time or at run time (dynamic)

## Compiler Allocated Memory

Packaged with the binary of the program

There is no standard default value

Variables and arrays are allocated here

## Arrays in C

- Arrays are not dynamic
- Must have fixed size
  - this means you can't pass a variable into a an array initializer
- There is no length function
- There is no boundary checking
