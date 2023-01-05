---
layout: post
title:  golang 获取系统信息(cpu 内存 磁盘 网络)
date:   2023-01-05 11:05:55 +0300
image:  /assets/images/33do.jpg
author: ituserxxx
tags:   Golang
---


```go
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
