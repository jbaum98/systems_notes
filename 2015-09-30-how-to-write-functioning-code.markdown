---
layout: post
title:  "How To Write Functioning Code"
date:   2015-09-30
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

## Declaring Strings
Because strings are arrays of `char`s and arrays are pointers,
strings are actually pointers to the first character and end at a `null`.

1. Declare  a normal `char[]` with size

   ```c
   char s[256];
   ```
   Allocates 256 bytes, setting nothing automatically

2. Declare `char[]` with size and a literal

   ```c
   char s[256] = "Imagine";
   ```
   Allocates 256 bytes, setting the first 7 bytes to `"Imagine"`
   and the 8th byte to `null`

3. Declare `char[]` with a literal and no size

   ```c
   char s[] = "Tuesday";
   ```
   Allocates 8 bytes (what it needs), setting the first 7 bytes to `"Tuesday"`
   and the 8th byte to `null`

4. Declare a `*char` with a literal

   ```c
   char *s = "Mankind"
   ```
   Allocates 8 bytes (what it needs), setting the first 7 bytes to `"Tuesday"`
   and the 8th byte to `null`.

   > This is different from **#3** because a pointer is _mutable_
   and an array is _immutable_

## Functions
Functions are declared pretty much like Java.

> **Functions cannot be used until they are declared.
> You can declare a header at the top.**

### Function Headers

```c
int is_even(int i)
=== ======= =====
 |     |      |
 |     |      ----------------
 |     ------------           |
 -----             |          |
      |            |          |
// <return type> <name> (<parameters>)
```

### Passing Values

All C functions are _pass by value_


pass by value
: a paramter is a copy of the variable passed into the function.
The original variable is not touched

```c
int foo(char *s, int i) {
    i++;
    s[0]++;
}
char * w = "cool";
int x = 5;
foo(w, x);
```

If we mutate `i` within `foo`, `x` is not mutated,
because `i` is copy of `x`, and is at a different memory location.
Similarly, if we modify the value of `s`, that is the memory location
at which it points, `w` is unchanged. However, if we modify
the **value at the memory location** that `s` refers to,
then the value at which `w` points will also be modified
because they point to the same memory location.

> You cannot mutate the value of the variables you have passed in,
> but you can mutate the value stored at memory locations whose pointers
> are passed in.

### Calling Other Functions

1. Define the function before you use it.
2. Declare the header before you use it.
3. Create a seperate header file and include it.

   ```c
   //<stringy.h>

   int len(char *s);
   ```

   ```c
   //<stringy.c>

   #import <stdio.h>
   #import "stringy.h"

   int main() {
       char *s = "This is my string!";
       int l = len(s);
       printf("length of *%s*: %d\n", s, l);

       return 0;
   }

   int len(char *s) {
       int i = 0;
       while (s[i] != 0) { // or s[i] because 0 is false
           i++;
       }
       return i;
   }
   ```

## Standard Library String Functions
Many useful string functions are stored in `string.h`. They all rely on the strings being _null-terminated_.

All the functions assume that the parameter strings are always null-terminated.


### `strlen`

```c
int strlen( char *s )
```

Returns the number of characters from the start of `s` up to but not including the terminating null

### `strcmp`

```c
int strcmp( char *s1, char *s2 )
```

Returns 0 if `s1` and `s2` are identical up to the terminating null.
Returns a positive number if `s1` is greater than `s2` (lexicographically)
Returns a negative number if `s1` is less than `s2`

### `strcpy`

```c
char * strcpy( char *dest, char *source )
```

Copies all the chars up to and including the terminating null from `source` into `dest`.
Returns `dest`

### `strcat`

```c
char * strcat( char *s1, char *s2 )
```

Appends all the characters up to and including the terminating null in `s2` to the end of `s1`.
Returns `s1`

> **Many string functions have a `strn` version, these take an extra parameter
> that sets a limit to the number of bytes you will look at in a string.**

#### `strncat`

```c
strncat( char *s1, char *s2, int n )
```

Appends at most n chars from `s2` into `s1`.
It will stop if it hits a terminating null in `s2` before `n` bytes
It will add a terminating null to s1

### `strchr`

```c
char * strchr( char *s, char c )
```

Returns a pointer to the first occurance of c in s.
If c is not in s, returns null (0)

### `strstr`

```c
char * strstr( char *s, char *key )
```

Returns a pointer to the start of the first occurance of key in s
If key is not in s, returns null
