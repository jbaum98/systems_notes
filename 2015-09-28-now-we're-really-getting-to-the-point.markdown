---
layout: post
title:  "Ok, Now We're Really Getting to the Point"
date:   2015-09-28
---
# What is a pointer?
Pointers are variables that store a memory address which refers to the location of some other value. They are declared like this:

```c
int *p;
// also this is okay
int * p;
```

# Pointer Arithmetic
As seen above, pointers are declared with a specific type in mind that will be stored at the memory location specified by the pointer. However, because all pointers contain memory addresses, they are all the same size, so the only real difference between two pointers of different types is when it comes to pointer arithmetic.

```c
int    * ip = 100; // an int pointer to memory location 100 which we probably don't have access to
double * dp = 100; // a double pointer to the same memory location

printf("ip + 1: %lu\n", ip + 1); //=> 104
printf("dp + 1: %lu\n", dp + 1); //=> 108
```

C adds the number of bytes necessary to store an entire value of the type of the pointer. So for an int it adds 4 bytes, but for a double it adds 8 bytes. If you don't care about the type of the pointer, use the void * type:

```c
void * p = 100;
printf("p + 1: %lu", p + 1); //=> 101
```

# Operators Used With Pointers
To access the memory location of a given variable, use the & operator. To access the value at a given memory location (dereference), use the * operator.

```c
int i = 100;
int * ip = &ip;                                                      // now ip contains the memory location of i
printf("i is located at: %lu\n", &i);                                // some memory address idk where
printf("the value of ip is: %lu\n", ip);                             // should be the same as above
printf("the value of i is: %d\n", i);                                //=> 100
printf("the value at the memory location stored in ip is: %d", *ip); //=> 100
```

# Arrays
What is an array, really? In C, it is simply a pointer to its first element.

```c
int ar[5];
printf("ar: %lu\n", ar);
printf("ar: %lu\n", &(ar[0])); // should be the same as previous line
```

This means that when you access the nth element of an array ar, you are really just dereferencing ar + n. Which also means that array notation is another way to specify dereferencing, but you should be sure to use the notation that makes sense for what you're doing. Which means never doing any of the following:
```c
5[ar] // same as ar[5]
ip[0] // same as *ip
0[ip] // same as *ip
```

> **Note:** The one difference between arrays and pointers is that arrays are immutable, so while you can change the value of pointer variables, you cannot change the values of arrays.
