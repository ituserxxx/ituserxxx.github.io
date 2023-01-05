---
layout: post
title:  node 调用c 动态库
date:   2023-01-02 01:05:55 +0300
image:  /assets/images/33do.jpg
author: ituserxxx
tags:   Node C
---


环境

- apt install node
- apt install npm
- npm install ffi-napi --save

目录

demo
——a.c
——a.js

a.c文件内容

```c
#include <stdio.h>
#include <stdint.h>
#include <string.h>
#include <unistd.h>

int add(int a,int b) {
    return a+b;
}
```

编译动态库

```shell
gcc -shared -fPIC  -o a.so a.c -lm
```

a.js文件调用

```nodejs
var ffi = require('ffi-napi');
//serial_name, int baudrate, int bits, char parity, int stop, char flow
var g = ffi.Library('./a.so',{'add':['int',[ "int", "int" ]]});
var a1  = g.add(1,11)
```
