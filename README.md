---
description: 'http://nil.csail.mit.edu/6.824/2020/schedule.html'
---

# 课程零：课程简介

## 分布式系统是什么?

* 多个电脑协作
* 大型网站站点的存储、MapReduce、对等分享（p2p）等
* 许多关键的基础设施都是分布式的

## 人们为什么要构建分布式系统?

* 通过并行来增加容量
* 通过复制/复本来增加容错能力
* 使计算在物理上靠近外部实体（？）
* 通过隔离来提升安全

## 但是：

* 许多并发部分，复杂的交互
* 必须应对部分失败（partial）
* 难以发挥性能潜力

## 为什么要上这门课？

* 非常有趣：困难的问题，功能强大的解决方案
* 正被真正的系统所使用：由大型网站的兴起所驱动
* 是一个活跃的研究领域：未解决的重要问题
* 可动手实操：你将在实验室中构建真实的系统

### 课程结构

{% embed url="http://pdos.csail.mit.edu/6.824" %}

#### 课程助理：

pass:这个对我没用

#### 课程组成：

* 讲义
* 论文
* 考试（额，这个对我也没啥用）
* 实验
* 期末项目（可选）

#### 讲义：

构想，论文讨论和实验将被录像，可在线获得（额，我就是这么获得的）

#### 论文：

* 研究论文，一些是经典的，一些是新的（问题，点子，实现细节、评估）
* 学习课程之前一定要读完论文

#### 考试：

pass

#### 实验：

**目标**:对一些重要技术有更深刻的理解。每周一次

* 实验一：MapReduce
* 实验二：使用Raft进行容错复制
* 实验三：容错K-V存储
* 实验四：分片K-V存储

### 课程关注的话题

这是一门关于应用程序基础设施的课程：

* 存储
* 通信
* 计算

目标：隐藏分布复杂性的抽象。在我们的研究中会反复出现几个主题。

* 话题—实现：RPC ，线程，并发控制
* 话题二性能：可扩展的吞吐量（只需水平添加硬件资源，而不用重新进行系统设计）。随着机器数量的增加，有些问题会变得困难（负载不平衡、出现掉队的、延迟增加、无法并行的代码：初始化、交互，资源瓶颈：网络）。随着扩展有些问题不是那么容易解决的：单个用户请求的快速响应，所有用户希望更新相同的数据。这些都需要更好的设计，而不是仅仅增加机器资源就能解决的。
* 话题三容错：1000太服务器，很大的网络-&gt;总是会出现部分异常坏掉的情况。我们想从应用程序中隐藏掉这些失败。我们经常想可用（尽管失败，应用仍可以正常处理）、自愈（当失败被解决掉的时候能够自我恢复）。好主意：复制服务器（一个服务器崩溃，仍有其他的可以进行处理）
* 话题四一致性：General-purpose infrastructure needs well-defined behavior.

      E.g. "Get\(k\) yields the value from the most recent Put\(k,v\)."

    Achieving good behavior is hard!

      "Replica" servers are hard to keep identical.

      Clients may crash midway through multi-step update.

      Servers may crash, e.g. after executing but before replying.

      Network partition may make live servers look dead; risk of "split brain".

    Consistency and performance are enemies.

      Strong consistency requires communication,

        e.g. Get\(\) must check for a recent Put\(\).

      Many designs provide only weak consistency, to gain speed.

        e.g. Get\(\) does \*not\* yield the latest Put\(\)!

        Painful for application programmers but may be a good trade-off.

    Many design points are possible in the consistency/performance spectrum!





#### 



