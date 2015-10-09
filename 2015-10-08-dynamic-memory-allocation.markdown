---
layout: post
title: "Dynamic Memory Allocation"
date: 2015-10-8
---

# `malloc`

```c
void * malloc(int x);
```

Allocates `x` bytes of memory from the heap, returning the address at the beginning of the allocation.

Make sure to typecast the `void *` to the type you want.

# `calloc`

```c
void * calloc(int n, int x);
```

Like malloc but zeroes it out for ya. Also allocates `n * x` bytes. Because Brian Kernigan said so.

# `realloc`

```c
void realloc(void *p, int x);
```

Changes the amount of memory allocated to a given block to `x` bytes.

`p` must be a pointer to the beginning of an alllocated block of memory that was `malloc`ed or `calloc`ed, but doesn't need to be original pointer.

# `free`

```c
void free(void *p);
```

Releases dynamically allocated memory.

Every single call to `malloc`/`calloc` should have a corresponding call to `free`.
