---
layout: post
title:  golang 在数组最前面添加值
date:   2023-01-01 09:05:55 +0300
image:  /assets/images/33do.jpg
author: ituserxxx
tags:   Golang
---


```
func Test_a(t *tesing.T){
    l := []string{"b"}
    a := "a"
    l = append([]string{a}, l...)
    println(l[0],l[1])
}
```