---
layout: post
title: "Pre-processor Instructions"
date: 2015-10-15
---
`#` signals the prepocessor to do stuff

# `#define`

Acts as a find and replace

```c
#define FOO 33
```

# `#ifndef`

If not defined

```c
#ifndef FOO
#define FOO
// ALL THE CODE
#endif
```

This way everything gets run only once.

> **Convention:** make the constant the name of your file, like `LIST_H`
