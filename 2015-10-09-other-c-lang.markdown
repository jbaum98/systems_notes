---
layout: post
title: "Other C Language Stuff"
date: 2015-10-09
---

# Typedef

```c
// typedef <real type> <new name>;
typdef float bubbles;

bubbles b = 12.34;
float f = 12.34;
assert( f == b );
```

# Structs

```c
struct { int a; char c;} s;
struct { int a; char c;} t; // <= need to rewrite the whole struct type

typedef struct {int a; char c} myStruct;

myStruct s;
myStruct t; // :)

s.a = 38;
s.c = '*';
```

## Prototyping

```c
struct foo { int a; char c; } t;

struct foo s;
struct foo t;
```

## Creating structs

```c
typdef struct { int a; charc; } foo;

foo *t;
t = (foo*)malloc( sizeof(foo) );

(*t).a = 87;
t-> c = 'f';
```
