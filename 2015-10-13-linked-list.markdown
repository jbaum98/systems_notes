---
layout: post
title: "Linked List"
date: 2015-10-13
---
### DN: What's wrong with this?

```c
node * insert_front( node * n, int i ) {
    node new;
    new.i = i;
    new.next = n;

    return &new;
}
```
The memory is allocated, but is allocated on the stack.
That means it is popped off at the end of the function, and we can't use it.

> **Dynamic allocation is for persisting values across function calls.**
