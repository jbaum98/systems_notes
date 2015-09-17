---
layout: post
title:  "Always Read the Fine Print"
date:   2015-09-17 13:27:00
---
> ### DN: Write a basic "Hello World" program in Java
```java
public class Driver {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

# Data Types and Variables
Character literals are single characters inside `''`
```c
char x = 'a';
```

String literals exists, even though there is no String data type.
```c
char[] x = "hello";
```
Any variable type can be declared an "unsigned" variables
meaning that it will never be negative.
It has 0 as its lower bound, and an upper bound greater than the signed version.
```c
unsigned char x; // 0 <= x <= 255
```
> **WARNING**
> You cannot declare a variable inside a `for` loop
```c
// NO GOOD MR JAVA
for (int i = 0; i < 10; i++) {...}
// INSTEAD
int i;
for (i = 0; i < 10; i++)     {...}
```

# Hello Wolrd in C

## Minimal C Program
The `main` function is the one that runs. It's return type is `int`, and therefore must return
an `int` status code. `0` means everything is okay.
```c
int main() {
    return 0;
}
```

We compile with `gcc`
```sh
gcc minimal.c           # produces a.out
gcc minmal.c -o minimal # produces minimal
```
