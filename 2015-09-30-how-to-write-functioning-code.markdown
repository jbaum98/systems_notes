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

# declaring Strings
because strings are arrays of `char`s and arrays are pointers, strings are actually pointers to the first character and end at a `null`.

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

   > This is different from **#3** because a pointer is _mutable_ and an array is _immutable_

# functions
functions are declared pretty much like Java.

> **Caveat**
> functions cannot be used until they are declared. You can declare a header at the top.

## Function Headers

```c
<return type> <name> (<parameters>)
```

## Passing Values

all C functions are _pass by value_
: a paramter is a copy of the variable passed into the function. The original varialbe is not touched

```c
int foo(char *s, int i) {
    i++;
    s[0]++;
}
char * w = "cool";
int x = 5;
foo(w, x);
```

if we mutate `i` within `foo`, `x` is not mutated because `i` is copy of `x`, and is at a different memory location.
similarly, if we modify the value of `s`, that is the memory location at which it points, `w` is unchanged. However, if we modify the **value at the memory location** that `s` refers to, then the value at which `w` points will also be modified because they point to the same memory location.

> you cannot mutate the value of the variables you have passed in, but you can mutate the value stored at memory locations whose pointers are passed in.

## Calling Other Functions

1. Define the function before you use it.
2. Declare the header before you use it.
3. Create a seperate header file and include it.
   
   ```c
   //stringy.h

   int len(char *s);
   ```

   ```c
   //stringy.c, or compiled stringy binary
   int len(char *s) {
       int i = 0;
       while (s[i] != 0) { // or s[i] because 0 is false
           i++;
       }
       return i;
   }
   ```

   ```c
   //other_file.c
   #import <stdio.h>
   #import "stringy.h"

   int main() {
       char *s = "This is my string!";
       int l = len(s);
       printf("length of *%s*: %d\n", s, l);
   
       return 0;
   }
   ```

# standard Library String Functions
stored in `string.h`.
all functions rely on _null-terminated strings_.

- `strlen`
- `srtcmp`
- `strcopy`
- `strcat`

Many have `strn*` version that take an extra parameter that sets a limit to the number of bytes it will look at it in string
