---
layout: post
title: "File IO"
date: 2015-10-19
---
# File Descriptor Table

The file descriptor table is a list of the files currently in use.
It is usually limited to 256. Each file has an index starting at 0,
which is called the _file descriptor_

```c
int getdtablesize();
```

## Files in File Descriptor Table by Default

0. `stdin`
1. `stdout`
2. `stderr`

# `open`

Located in `<fctl.h>`
Returns the file descriptor if successful.
Returns `-1` and sets `errno` if unsuccessful.

```c
int open(const char* path, int o_flags);
int open(const char* path, int o_flags, mode_t mode);
```

## Errors
In `errno.h` there is defined a variable `int errno`.
It is common practice to set `errno` to an integer signifying
the cause of an error.
You can use `strerror(errno)` to obtain a string description of the error.

## Mode

Only used when creating a file.
Set's the new files permissions using a 3-digit octal number.

In C, octal number literals have a leading 0:

```c
int x = 0777; // 511 in decimal or  111111111 in binary
int y = 777;  // 777 in decimal or 1100001001 in binary
int z = 0b111100100 // you can use binary too
//        rwxrwxrwx
```

## Open Flags

name     | desc
:---------|:------
`O_RDONLY`| read only
`O_WRONLY`| write only
`O_RDWR`  | read and write
`O_TRUNC` | truncate
`O_CREAT` | create
`O_EXCL`  | exclusive. used in conjunction with create, will fail if file already exists


### Bitwise Operators

symbol | operation
------ | ---------
`&`    | and
`|`    | or
`~`    | not
`^`    | xor

>**Bitwise not vs not**
>
>```c
>int x = 13; // 00001101
>!x          // 0
>~x          // 11110010 => -14
>```

We can use bitwise or to combine multiple open flags,
because they are powers of 2

```c
O_WRONLY = 1        // 00000001
O_APPEND = 8        // 00001001
O_WRONLY | O_APPEND // 00001001
```

# `close`

Located in `unistd.h`
Returns `0` if succesful.
Returns `-1` and sets `errno` if unsuccessful.

```c
int close( int file_desc );
```

# `read`

Located in `unistd.h`
Reads `n` bytes from the file specified by `file_desc` into the buffer `buf`.
Returns number of bytes read.
Returns `-1` and sets `errno` if unsuccessful.

```c
int read( int file_desc, void *buf, int n );
```

# `write`

Located in `unistd.h`
Writes `n` bytes from the buffer `buf` into the file specified by `file_desc`.
Returns number of bytes written.
Returns `-1` and sets `errno` if unsuccessful.

```c
int write( int file_desc, void *buf, int n );
```
