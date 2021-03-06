# 常见面试题汇总

主要来源:
- 网上看到的面经, 在此自己尝试作答
- 日常开发和学习中遇到的问题, 自问自答
- 身边同学的亲身经历

统一收集在此, 作为自学的一种方式.

| [Java 核心概念](#核心概念) | [集合](#集合) | [并发](#并发) | [JVM](#jvm) | [框架](#框架) | [中间件](#中间件) | [数据库](#数据库) | [操作系统](#操作系统) | [网络](#网络) | [数据结构/算法](#数据结构/算法) | [分布式系统](#分布式系统) | [架构设计](#架构设计) | [面向对象](#面向对象设计) | [常用工具](#常用工具) | [大数据](#大数据)
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

## <span id="core">核心概念</span>
- [Class.forName() 和 ClassLoader 的区别](https://github.com/DestinyWang/interview/blob/master/blogs/core/the-difference-between-forName-and-ClassLoader.md)
- [对象逃逸分析](https://github.com/DestinyWang/interview/blob/master/blogs/core/escape-analysis.md)
- [谈谈对强软弱虚四种引用的理解](https://github.com/DestinyWang/interview/blob/master/blogs/core/strong-soft-weak-virtual-reference.md)
- [String, StringBuffer, StringBuilder 的区别](https://github.com/DestinyWang/interview/blob/master/blogs/core/string-stringbuilder-stringbuffer.md)
- [Java 中文件的复制方式](https://github.com/DestinyWang/interview/blob/master/blogs/core/file-copy.md)
- [如何解释内部匿名类使用外部变量要加final](https://github.com/DestinyWang/interview/blob/master/blogs/core/why-add-final-to-internal-anonymous-classes-using-external-variables.md)

## <span id="collections">集合</span>

## <span id="concurrent">并发</span>
- [AtomicInteger 底层原理与 CAS](https://github.com/DestinyWang/interview/blob/master/blogs/concurrent/atomic-integer.md)
- [Java 并发包提供的工具](https://github.com/DestinyWang/interview/blob/master/blogs/concurrent/java-concurrent-util.md)
- [线程安全的单例模式](https://github.com/DestinyWang/interview/blob/master/blogs/concurrent/thread-safe-singleton.md)
- [AQS 源码分析](https://github.com/DestinyWang/interview/blob/master/blogs/concurrent/abstract-queue-synchronized.md)
- [synchronized 简介](https://github.com/DestinyWang/interview/blob/master/blogs/concurrent/synchronized.md)

## <span id="jvm">JVM</span>
- [JVM 内存划分以及 OOM 的理解](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/memory-partitioning-of-jvm.md)
- [Java 常见的垃圾收集器](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/garbage-collector.md)
- [CMS GC](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/cms-gc.md)
- [G1 GC](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/g1-gc.md)
- [GC 调优](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/the-gc-tuning.md)
- [谈谈线上 JVM 的启动参数](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/jvm-startup-parameters.md)
- [谈谈对 OOM 的理解](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/out-of-memory-error.md)
- [如何定位执行慢的问题](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/how-do-you-locate-slow-thread.md)
- [谈谈对 JIT 的理解](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/jit.md)
- [JVM 逃逸分析](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/escape-analysis.md)
- [当一个线程抛出了 OOM, 同进程的其他线程是否可以正常执行](https://github.com/DestinyWang/interview/blob/master/blogs/jvm/one-thread-oom-other-threads-behavior.md)

## <span id="framework">框架</span>
- [Spring Bean 的生命周期和作用域](https://github.com/DestinyWang/interview/blob/master/blogs/framework/the-life-cycle-and-scope-of-Spring-beans.md)
- [Netty 核心概念](https://github.com/DestinyWang/interview/blob/master/blogs/framework/Netty.md)
- [Netty 如何解决空轮询](https://github.com/DestinyWang/interview/blob/master/blogs/framework/how-netty-solves-the-empty-wheel-training.md)

## <span id="middleware">中间件</span>
- [ZAB 协议的基本概念](https://github.com/DestinyWang/interview/blob/master/blogs/middleware/zab.md)

## <span id="db">数据库</span>
- [InnoDB 如何实现高并发](https://github.com/DestinyWang/interview/blob/master/blogs/db/innodb-transaction-model.md)
- [InnoDB 如何实现事务的隔离级别](https://github.com/DestinyWang/interview/blob/master/blogs/db/how-does-innodb-implements-transaction-isolation.md)
- [详解 InnoDB 锁机制](https://github.com/DestinyWang/interview/blob/master/blogs/db/the-locks-in-innodb.md)

## <span id="os">操作系统</span>
- [从打开电源到出现显示桌面, 计算机都干了些什么事情](https://github.com/DestinyWang/interview/blob/master/blogs/os/what-does-the-computer-do-from-turning-on-the-power-to-the-display-desktop.md)
- [Linux 启动时遇到错误应该如何处理](https://github.com/DestinyWang/interview/blob/master/blogs/os/how-to-troubleshoot-a-linux-boot-failure.md)
- [深入理解同步/异步/阻塞/非阻塞的区别](https://github.com/DestinyWang/interview/blob/master/blogs/os/synchronous-asynchronous-blocking-non-blocking.md)
- [如何解释 select, poll, epoll 之间的区别](https://github.com/DestinyWang/interview/blob/master/blogs/os/select-poll-epoll.md)

## <span id="network">网络</span>
- [从浏览器输入 URL 到呈现页面会经过哪些步骤](https://github.com/DestinyWang/interview/blob/master/blogs/network/what-happens-from-the-input-URL-to-display-page.md)
- [TCP 拥塞控制](https://github.com/DestinyWang/interview/blob/master/blogs/network/tcp-congestion-control.md)
- [ping 命令是如何工作的](https://github.com/DestinyWang/interview/blob/master/blogs/network/how-does-ping-cmd-works.md)
- [TCP 中的 TIME_WAIT 功能](https://github.com/DestinyWang/interview/blob/master/blogs/network/too-much-timewait-on-tcp-connection.md)

## <span id="algorithm">数据结构/算法</span>
- [三角形最小路径和](https://github.com/DestinyWang/interview/blob/master/blogs/algorithm/Triangle.md)
- [找到所有数组中消失的数字](https://github.com/DestinyWang/interview/blob/master/blogs/algorithm/Find-All-Numbers-Disappeared-in-an-Array.md)
- [海量数据查询的问题汇总](https://github.com/DestinyWang/interview/blob/master/blogs/algorithm/find-repeats-most.md)
- [实现一个简单的 LRU 算法](https://github.com/DestinyWang/interview/blob/master/src/main/java/org/destiny/byteddance/lru/Solution.java)
- [两数之和II-输入有序数组](https://github.com/DestinyWang/interview/blob/master/blogs/algorithm/Two-Sum-II-Input-array-is-sorted.md)
- [leetcode-2-两数相加(字节跳动面试题)](https://github.com/DestinyWang/interview/blob/master/src/main/java/org/destiny/bytedance/add_two_numbers/Solution.java)
- [leetcode-75-颜色分类](https://github.com/DestinyWang/interview/blob/master/blogs/algorithm/merge-sorted-arrays.md)
- [leetcode-88-合并两个有序数组](https://github.com/DestinyWang/interview/blob/master/blogs/algorithm/sort-color.md)
- [leetcode-209-长度最小的子数组](https://github.com/DestinyWang/interview/blob/master/blogs/algorithm/minimum-size-subarray-sum.md)
- [leetcode-283-移动0](https://github.com/DestinyWang/interview/blob/master/blogs/algorithm/move-zeros.md)
- [leetcode-448-找到所有数组中消失的数字](https://github.com/DestinyWang/interview/blob/master/blogs/algorithm/Find-All-Numbers-Disappeared-in-an-Array.md)

## <span id="distributed">分布式系统</span>
- [CAP 理论简介](https://github.com/DestinyWang/interview/blob/master/blogs/distributed/CAP.md)
- [分布式事务](https://github.com/DestinyWang/interview/blob/master/blogs/distributed/distributed-transaction.md)

## <span id="architect">架构设计</span>
- [系统如何在不重启的情况下接收新的请求类型并转换成统一的内部模型](https://github.com/DestinyWang/interview/blob/master/blogs/architect/how-does-the-system-receive-new-request-types-without-a-reboot-and-switch-to-a-unified-internal-model.md)
- [如何实现分布式锁](https://github.com/DestinyWang/interview/blob/master/blogs/architect/distributed-lock.md)

## <span id="OOD">面向对象设计</span>
- [贫血模型, 充血模型, 胀血模型, 领域驱动设计](https://github.com/DestinyWang/interview/blob/master/blogs/ood/domain-driven-design.md)

## <span id="util">常用工具</span>
- [Apache Bench 和 JMeter](https://github.com/DestinyWang/interview/blob/master/blogs/util/apache-bench-and-jmeter.md)
- [单元测试](https://github.com/DestinyWang/interview/blob/master/blogs/util/unit-test.md)

## <span id="bigdata">大数据</span>
- [Hadoop 简介](https://github.com/DestinyWang/interview/blob/master/blogs/bigdata/hadoop.md)