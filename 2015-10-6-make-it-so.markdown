---
layout: post
title: "Make It So"
date: 2015-10-16
---
# Problems Declaring Strings

**Literal strings are immutable.**

```c
char *s1  = "Hello";
char *s2  = "Hello";
assert( s1 == s2 ); // only allocates once
*s2 = 'J'; // segfault
```

However, array notation results in a new allocation

```c
char s3[] = "Hello"; // allocates new memory
assert( s3 != s1 );
```
