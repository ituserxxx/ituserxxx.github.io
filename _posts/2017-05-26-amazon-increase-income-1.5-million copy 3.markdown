---
layout: post
title:  Amazon increase income 1.5 Million
date:   2017-05-26 14:05:55 +0300
image:  /assets/images/blog/post-2.jpg
author: uixgeek
tags:   UX design
---

**Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.**




 ```
package main

import (
	"fmt"
	"github.com/shirou/gopsutil/v3/cpu"
	"github.com/shirou/gopsutil/v3/disk"
	"github.com/shirou/gopsutil/v3/mem"
	"github.com/shirou/gopsutil/v3/net"
	"time"
)

func main() {
	v, _ := mem.VirtualMemory()
	fmt.Println(v.Total,v.UsedPercent,v.Used,v.Free)

	c1,_ := cpu.Percent(time.Duration(time.Second), false)
	fmt.Println(c1)

	d,_ := disk.Usage("/")
	fmt.Println(d.Total,d.Used,d.UsedPercent)

	info, _ := net.IOCounters(false)
	fmt.Println(info[0].BytesSent,info[0].BytesRecv,info[0])
}
```
