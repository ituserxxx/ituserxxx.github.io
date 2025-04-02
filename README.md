

golang


- 通道 channel

   - [1-什么是 CSP](./golang/channel/1-什么是%20CSP.md)

   - 1[2-channel 底层的数据结构是什么](./golang/channel/2-channel%20底层的数据结构是什么.md)

   - [3-向 channel 发送数据的过程是怎样的](./golang/channel/3-向%20channel%20发送数据的过程是怎样的.md)

   - [4-从 channel 接收数据的过程是怎样的](./golang/channel/4-从%20channel%20接收数据的过程是怎样的.md)

   - [5-关闭一个 channel 的过程是怎样的](./golang/channel/5-关闭一个%20channel%20的过程是怎样的.md)

   - [6-从一个关闭的 channel 仍然能读出数据吗](./golang/channel/6-从一个关闭的%20channel%20仍然能读出数据吗.md)

   - [7-操作 channel 的情况总结](./golang/channel/7-操作%20channel%20的情况总结.md)

   - [8-如何优雅地关闭 channel](./golang/channel/8-如何优雅地关闭%20channel.md)

   - [9-channel 发送和接收元素的本质是什么](./golang/channel/9-channel%20发送和接收元素的本质是什么.md)

   - [10-channel 在什么情况下会引起资源泄漏](./golang/channel/10-channel%20在什么情况下会引起资源泄漏.md)

   - [11-关于 channel 的 happened-before 有哪些](./golang/channel/11-关于%20channel%20的%20happened-before%20有哪些.md)

   - [12-channel 有哪些应用](./golang/channel/12-channel%20有哪些应用.md)


- 编译 compile

   - [1-逃逸分析是怎么进行的](./golang/compile/1-逃逸分析是怎么进行的.md)

   - [2-GoRoot 和 GoPath 有什么用](./golang/compile/2-GoRoot%20和%20GoPath%20有什么用.md)

   - [3-Go 编译链接过程概述](./golang/compile/3-Go%20编译链接过程概述.md)

   - [4-Go 编译相关的命令详解](./golang/compile/4-Go%20编译相关的命令详解.md)

   - [5-Go 程序启动过程是怎样的](./golang/compile/5-Go%20程序启动过程是怎样的.md)


- 接口 interface

  - [1-Go 语言与鸭子类型的关系](./golang/interface/1-Go%20语言与鸭子类型的关系.md)

  - [2-值接收者和指针接收者的区别](./golang/interface/2-值接收者和指针接收者的区别.md)

  - [3-iface 和 eface 的区别是什么](./golang/interface/3-iface%20和%20eface%20的区别是什么.md)

  - [4-接口的动态类型和动态值](./golang/interface/4-接口的动态类型和动态值.md)

  - [5-编译器自动检测类型是否实现接口](./golang/interface/5-编译器自动检测类型是否实现接口.md)

  - [6-接口的构造过程是怎样的](./golang/interface/6-接口的构造过程是怎样的.md)

  - [7-类型转换和断言的区别](./golang/interface/7-类型转换和断言的区别.md)

  - [8-接口转换的原理](./golang/interface/8-接口转换的原理.md)

  - [9-如何用 interface 实现多态](./golang/interface/9-如何用%20interface%20实现多态.md)

  - [10-Go 接口与 C++ 接口有何异同](./golang/interface/10-Go%20接口与%20C++%20接口有何异同.md)

- 哈希表 map
  
  - [1-map的底层实现原理是什么](./golang/map/1-map的底层实现原理是什么.md)

  - [2-如何实现两种 get 操作](./golang/map/2-如何实现两种%20get%20操作.md)

  - [3-map 的遍历过程是怎样的](./golang/map/3-map%20的遍历过程是怎样的.md)

  - [4-map 的赋值过程是怎样的](./golang/map/4-map%20的赋值过程是怎样的.md)

  - [5-map 的删除过程是怎样的](./golang/map/5-map%20的删除过程是怎样的.md)

  - [6-map 的扩容过程是怎样的](./golang/map/6-map%20的扩容过程是怎样的.md)

  - [7-map 中的 key 为什么是无序的](./golang/map/7-map%20中的%20key%20为什么是无序的.md)

  - [8-float 类型可以作为 map 的 key 吗](./golang/map/8-float%20类型可以作为%20map%20的%20key%20吗.md)

  - [9-可以边遍历边删除吗](./golang/map/9-可以边遍历边删除吗.md)

  - [10-可以对 map 的元素取地址吗](./golang/map/10-可以对%20map%20的元素取地址吗.md)

  - [11-如何比较两个 map 相等](./golang/map/11-如何比较两个%20map%20相等.md)

  - [12-map 是线程安全的吗](./golang/map/12-map%20是线程安全的吗.md)

- 垃圾回收器 memgc

  - [1-垃圾回收的认识](./golang/memgc/1-垃圾回收的认识.md)

  - [2-垃圾回收机制的实现](./golang/memgc/2-垃圾回收机制的实现.md)

  - [3-垃圾回收的优化问题](./golang/memgc/3-垃圾回收的优化问题.md)

  - [4-历史及演进](./golang/memgc/4-历史及演进.md)

  - [5-总结](./golang/memgc/5-总结.md)

- 调度器 sched

   - [1-goroutine和线程的区别](./golang/sched/1-goroutine和线程的区别.md)

   - [2-什么是 go scheduler](./golang/sched/2-什么是%20go%20scheduler.md)

   - [3-goroutine 调度时机有哪些](./golang/sched/3-goroutine%20调度时机有哪些.md)

   - [4-什么是M_N模型](./golang/sched/4-什么是M_N模型.md)

   - [5-什么是workstealing](./golang/sched/5-什么是workstealing.md)

   - [6-GPM 是什么](./golang/sched/6-GPM%20是什么.md)

   - [7-描述 scheduler 的初始化过程](./golang/sched/7-描述%20scheduler%20的初始化过程.md)

   - [8-main goroutine 如何创建](./golang/sched/8-main%20goroutine%20如何创建.md)

   - [9-g0 栈何用户栈如何切换](./golang/sched/9-g0%20栈何用户栈如何切换.md)

   - [10-schedule 循环如何启动](./golang/sched/10-schedule%20循环如何启动.md)

   - [11-goroutine 如何退出](./golang/sched/11-goroutine%20如何退出.md)

   - [12-schedule 循环如何运转](./golang/sched/12-schedule%20循环如何运转.md)

   - [13-M 如何找工作](./golang/sched/13-M%20如何找工作.md)

   - [14-sysmon 后台监控线程做了什么](./golang/sched/14-sysmon%20后台监控线程做了什么.md)

   - [15-一个调度相关的陷阱](./golang/sched/15-一个调度相关的陷阱.md)

- 数组与切片 slice
  
  - [1-数组和切片有什么异同](./golang/slice/1-数组和切片有什么异同.md)

  - [2-切片的容量是怎样增长的](./golang/slice/2-切片的容量是怎样增长的.md)

  - [3-切片作为函数参数](./golang/slice/3-切片作为函数参数.md)



- 标准库 stdlib

   - [context](./golang/stdlib/context/README.md)

   - [reflect](./golang/stdlib/reflect/README.md)

   - [unsafe](./golang/stdlib/unsafe/README.md)

 


redis

- **面试篇** 
   - [Redis 常见面试题](/redis/base/redis_interview.md)
- **数据类型篇** 
   - [Redis 数据类型和应用场景](/redis/data_struct/command.md)
   - [图解 Redis 数据结构](/redis/data_struct/data_struct.md)
- **持久化篇** 
	- [AOF 持久化是怎么实现的？](/redis/storage/aof.md) 	
	- [RDB 快照是怎么实现的？](/redis/storage/rdb.md) 
	- [Redis 大 Key 对持久化有什么影响？](/redis/storage/bigkey_aof_rdb.md) 
- **功能篇**
   - [Redis 过期删除策略和内存淘汰策略有什么区别？](/redis/module/strategy.md) 
- **高可用篇** 
   - [主从复制是怎么实现的？](/redis/cluster/master_slave_replication.md) 	
   - [为什么要有哨兵？](/redis/cluster/sentinel.html)
- **缓存篇** 
   - [什么是缓存雪崩、击穿、穿透？](/redis/cluster/cache_problem.md) 	
   - [数据库和缓存如何保证一致性？](/redis/architecture/mysql_redis_consistency.md) 	
