---
layout: post
title:  "How To Write Functioning Code"
date:   2015-09-30 13:56:24
---
> ### DN: Write a program the finds the length of a string
>
```c
int len( char *s ) {
    int i = 0;
    while (s[i] != 0) { // or s[i] because 0 is false
        i++;
    }
    return i;
}
```

# Declaring Strings
Because strings are arrays of `char`s and arrays are pointers, strings are actually pointers to the first character and end at a `null`.

1. Declare  a normal `char[]` with size
```c
char s[256];
```
Allocates 256 bytes, setting nothing automatically

2. Declare `char[]` with size and a literal
```c
char s[256] = "Imagine";
```
Allocates 256 bytes, setting the first 7 bytes to `"Imagine"` and the 8th byte to `null`

3. Declare `char[]` with a literal and no size
```c
char s[] = "Tuesday";
```
Allocates 8 bytes (what it needs), setting the first 7 bytes to `"Tuesday"` and the 8th byte to `null`

4. Declare a `*char` with a literal
```c
char *s = "Mankind"
```
Allocates 8 bytes (what it needs), setting the first 7 bytes to `"Tuesday"` and the 8th byte to `null`.
> This is different from *#3* because a pointer is _mutable_ and an array is _immutable_

# Functions
Functions are declared pretty much like Java.
> *Caveat*
> Functions cannot be used until they are declared. You can declare a header at the top.

