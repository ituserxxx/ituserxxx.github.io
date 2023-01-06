---
layout: post
title:  golang jsonrpc demo
date:   2022-10-01 09:05:55 +0300
image:  /assets/images/33do.jpg
author: ituserxxx
tags:   [Golang,Rpc]
---

server.go

```
package main

import (
	"context"
	"net/http"

	"github.com/echovl/jsonrpc"
)
type Comm struct {
	Code int `json:"code"`
	Msg string `json:"msg"`
	Data interface{} `json:"data"`
}

func ping(ctx context.Context, in interface{}) (*Comm, error) {
	return &Comm{
		Data: in,
	}, nil
}
func pong(ctx context.Context, in interface{}) (*Comm, error) {
	return &Comm{
		Data: in,
	}, nil
}
func main() {
	server := jsonrpc.NewServer()
	_ = server.HandleFunc("ping", ping)
	_ = server.HandleFunc("pong", pong)

	http.Handle("/jsonrpc", server)
	err := http.ListenAndServe(":9090", nil)
	if err != nil {
		return
	}
}
```

client.go

```
package main

import (
	"context"
	"data_collect/rpc/server/req"
	"fmt"
	"github.com/echovl/jsonrpc"
)
type comm struct {
	Code int `json:"code"`
	Msg string `json:"msg"`
	Data interface{} `json:"data"`
}

// test func
func main() {
	client := jsonrpc.NewClient("http://127.0.0.1:9090/jsonrpc")
	var result *comm
	resp, err := client.Call(context.Background(),"ping",req.Abc{})
	if err != nil {
		panic(err)
	}
	if err := resp.Decode(&result); err != nil {
		panic(err)
	}
	fmt.Println("result: ", result)
}
```

curl 方式

```
curl 127.0.0.1:9096/jsonrpc -X POST --data '{"method":"HelloService.Hello","params":["request params"],"id":0}'

```
