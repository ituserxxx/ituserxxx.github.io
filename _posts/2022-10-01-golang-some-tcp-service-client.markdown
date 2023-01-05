---
layout: post
title:  go 实现Tcp 多线程服务端
date:   2022-10-01 09:05:55 +0300
image:  /assets/images/33do.jpg
author: ituserxxx
tags:   Golang
---



package tcp

import (
	"collect/level_db"
	"collect/server/resp"
	"collect/tools"
	"collect/tools/ylog"
	"fmt"
	"github.com/gogf/gf/util/gconv"
	"net"
	"sync"
	"time"
)

const maxFifoLen int = 1024
const listenTcpPort string = ":8089"

// tcp/client/main.go

type tcpPlatfrom struct {
	con      net.Conn
	IpPort   string
	IsCon    bool
	SendChan chan interface{}
	IsClose  bool
	*level_db.TcpPlatfromModel
	IsAuth bool
	HearCount int
}

var TcpPlatfromList = make([]*tcpPlatfrom, 0)
var tpListLock sync.RWMutex

// NewTcpClient 客户端
func NewTcpClient(in *level_db.TcpPlatfromModel) {
	var tc = &tcpPlatfrom{
		con:              nil,
		IpPort:           "",
		IsClose:          false,
		IsCon:            false,
		SendChan:         make(chan interface{},100),
		TcpPlatfromModel: in,
		IsAuth: false,
		HearCount:10,
	}
	addr := fmt.Sprintf("%s:%s", in.Ip, in.Port)
	tc.IpPort = addr

	conn, err := net.Dial("tcp", addr)
	if err != nil {
		tools.DebugErr(err.Error())
		return
	}
	tc.con = conn
	tc.IsCon = true
	go tc.healthHeart()
	go tc.send()
	tpListLock.RLock()
	TcpPlatfromList = append(TcpPlatfromList, tc)
	tpListLock.RUnlock()
	defer func() {
		_ = conn.Close() // 关闭连接
		tpListLock.RLock()
		for i, platfrom := range TcpPlatfromList {
			if platfrom.IpPort == tc.IpPort{
				TcpPlatfromList = append(TcpPlatfromList[:i],TcpPlatfromList[i+1:]...)
				break
			}
		}
		tpListLock.RUnlock()
	}()
	go tc.headleRecv()
	tc.checkHearCount()
}
func (tc *tcpPlatfrom) headleRecv() {
	for {
		if tc.IsClose  {
			println("close headleRecv")
			return
		}
		buf := make([]byte,maxFifoLen)
		n, err := tc.con.Read(buf[:])
		if err != nil {
			tools.DebugErr(err.Error())
			return
		}
		msg := string(buf[:n])
		var rece = &resp.ReceData{}
		var res = &resp.ReportData{}
		if err := gconv.Structs(msg, rece); err != nil {
			res.Code = resp.RespCodeParamsErr
			res.Msg = err.Error()
			tc.SendChan<-res
			continue
		}
		//fmt.Println("recv-client->" + msg+tc.PlatformName)
		if rece.Data == "pong" {
			tc.IsCon = true
			tc.IsClose = false
			tc.HearCount =10
			continue
		}
		if msg == tc.RegisterContent {
			tc.IsAuth = true
			continue
		}
		if tc.IsAuth {
			tc.SendChan<-tools.PlatformInterfaceHandle(rece,res)
			continue
		}
		//if {
		//	res.Code = resp.RespCodeNotAuth
		//	res.Msg = "illegal operation,please go auth"
		//	tc.SendChan<-res
		//	continue
		//}
	}
}
func (tc *tcpPlatfrom) healthHeart() {
	for {
		if tc.IsClose{
			tools.DebugInfo("tcp close healthHeart")
			return
		}
		time.Sleep(time.Duration(gconv.Int(tc.HeartbeatTime)) * time.Millisecond)
		ylog.Loger.Info("tcp healthHeart addr :"+tc.IpPort)
		_, _ = tc.con.Write([]byte(tc.HeartbeatContent))
		tc.HearCount--
	}
}
func (tc *tcpPlatfrom) reconnect() {
	//for {
	//	time.Sleep(1 * time.Minute)
	//}
}
func (tc *tcpPlatfrom) checkHearCount() {
	for {
		if tc.IsClose{
			tools.DebugInfo("tcp close checkHearCount")
			return
		}
		if tc.HearCount < 0{
			Close(tc.Ip,gconv.Int64(tc.Port))
			return
		}
		time.Sleep(time.Duration(gconv.Int(tc.HeartbeatTime)) * time.Millisecond)
	}
}
func (tc *tcpPlatfrom) send() {
	for {
		if tc.IsClose{
			tools.DebugInfo("tcp close send")
			return
		}
		select {
		case msg, ok := <-tc.SendChan:
			if ok {
				_, _ = tc.con.Write([]byte(gconv.String(msg)))
			}
		default:
			time.Sleep(time.Second)
		}
	}
}
func AllPlatfromReport(msg string) {
	for _, platfrom := range TcpPlatfromList {
		platfrom.SendChan <- msg
	}
}
func GetStatus(ip string, port int64) bool {
	addr := fmt.Sprintf("%s:%d", ip, port)
	for _, platfrom := range TcpPlatfromList {
		if platfrom.IpPort == addr && platfrom.IsCon == true {
			return true
		}
	}
	return false
}
func Close(ip string, port int64)  {
	addr := fmt.Sprintf("%s:%d", ip, port)
	for i, platfrom := range TcpPlatfromList {
		if platfrom.IpPort == addr {
			TcpPlatfromList[i].IsClose = true
		}
	}
}
