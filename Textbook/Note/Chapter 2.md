## Chapter 2 HPC ARCHITECTURE 1: SYSTEMS AND TECHNOLOGIES

### 2.1 Intro

##### I. HPC architecture

+ Definition:  the organization and functionality of its constituent components and the logical instruction set architecture (ISA) it presents to computer programs that run on supercomputers. 
+ 性能计算架构是其组成组件的组织和功能，以及它向运行在超级计算机上的程序呈现的逻辑指令集架构。

##### II. Goal

+ minimize time to solution
+ maximize throughput of operation
+ serve the class of computations associated with large, usually numeric-intensive, applications.
  + 数据密集型问题，big data or graph analytics

A unifying theme across HPC architectures is “parallelism”

跨高性能计算体系结构的一个统一主题是“并行性”

### 2.2 KEY PROPERTIES OF HPC ARCHITECTURE

+ P= e  * S * a(R) * μ(E)
+ P is average performance
+ S is scaling (the number of units that can operate at the same time)
+ a is availability,  which is the total fraction of time the system is capable of performing a computation
+ R is a function of reliability
+ μ is the instruction retirement rate (通常是时钟速率) of the processor core
+ E, Average performance 

#### 2.2.1 SPEED

Speed有很多方面的定义

+  clock rate
   +  Processor core clock rates may vary from slightly less than 1 GHz to approaching 3 GHz
   +  主频是否就是描述时钟周期的
+  cycle time of the main memory
+   the rate at which data can be transferred or communicated between any two points within the system
   +  系统内任意两点之间数据传输或通信的速率

#### 2.2.2 PARALLELISM

无论串行有多快，都无法满足所有要求，且单兵作战的能力有所限制（光速、原子粒度和玻尔兹曼常数限制了单个处理器内核执行指令流的速度）

+  both the data path and the control path are factors in how parallelism is exploited by an HPC architecture

#### 2.2.3 EFFICIENCY

+  For HPC, a common measure of efficiency is 
  + the ratio of the sustained floating-point performance to the theoretical peak floating-point performance
  + both measure in flops, floating-point operations per second
  + 对于高性能计算，一个常见的效率度量是持续浮点性能与理论峰值浮点性能的比率，两者都以每秒浮点运算次数来度量
  + 即需要衡量有多少比例达到了峰值性能

#### 2.2.4 POWER

+ 在新一代高性能计算机中，主动热控制变得越来越重要和普遍。

#### 2.2.5 RELIABILITY

+ 重启

#### 2.2.6 PROGRAMMABILITY

+ 许多公共代码库由专家开发，并针对各种高性能计算系统类型和规模进行了优化。
+ 代码重用对于管理应用程序开发的复杂性和难度至关重要。

### 2.3 PARALLEL ARCHITECTURE FAMILIES—FLYNN’S TAXONOMY

比较常见的四种分类，图片帮助理解

+ SISD, MISD, SIMD, MIMD
+ GPU基于SIMD架构，MISD几乎没有使用
+ <img src="D:\STU\2021-Spring\Core Course\⭐⭐⭐Computer Arch III\Note\Image\微信截图_20210304191254.png" alt="微信截图_20210304191254" style="zoom:50%;" />.

### 2.4 ENABLING TECHNOLOGY

#### 2.4.1 TECHNOLOGY EPOCHS

+ 从原始计数装置到如今的LSI、VLSI的发展，再到今天multicore heterogeneous with GPU的概述

#### 2.4.2 ROLES OF TECHNOLOGIES

三类主要技术在很大程度上定义了高性能计算体系结构如何发展以及它们能够实现的性能的设计空间。

+ digital logic
  +  makes possible the actual basic operations that perform the calculations comprising the end-user work
  + 使实际的基本操作成为可能，这些操作执行包括最终用户工作在内的计算。
+  memory
  + allows information to be stored temporarily (ephemeral) or permanently (persistent), to be accessed by logic elements, and to be modified (updated) as required
  + 它允许信息临时(短暂)或永久(持久)存储，由逻辑元素访问，并根据需要修改(更新)。
+ data communication
  + moves information from one part of the system architecture to another.
  + 它将信息从系统架构的一部分转移到另一部分。

#### 2.4.3 DIGITAL LOGIC

+ 简单来说，0和1。
+ PS: 各种电子元件、器件、晶体管组成逻辑门电路

#### 2.4.4 MEMORY TECHNOLOGIES

+ 信息是由比特集合来表示的，每一位是0或1(真或假)，它们通常被分组为8位字节或多字节字。
+ 信息被视为不同的类型并进行编码，例如布尔、字符、字符串、整数(不同长度)和浮点(32位或64位)等。
+ History
  + 第一代(1940年至1952年)见证了许多记忆技术的发明和应用，最早的是水银延迟线，它也被称为“一维存储器”。水银延迟线用于第一代计算机，如EDSAC [1]和IBM 704 [2]。
  + 二维存储器：它在真空管内部的磷屏幕上存储静电荷，非常像电视和示波器中的老式显像管。
  + 三维：核心内存是由一堆堆的内核组成的，被称为三维内存。磁存储。

##### 2.4.4.2 Modern Memory Technologies

现代计算机体系结构结合了超级计算中占主导地位的三种主要内存技术: DRAM, SRAM, and magnetic storage media, including hard-disk drives and tapes.

+ SRAM
  + SRAM provides the highest-speed semiconductor memory. 
  + 静态随机存取存储器提供最高速度的半导体存储器。
+ main memory
  + The main memory is the primary component for storing data within a computer and is composed almost entirely of DRAM technology.
  + 主存储器是计算机中存储数据的主要组件，几乎完全由DRAM技术组成。
  + 不幸的是，DRAMs是不稳定的。
  + 它们需要破坏性读取，访问DRAM unit会破坏其值，因此必须重写。
+ DRAM and SRAM
  + DRAM比SRAM密度大得多，每单位面积容纳的位数要多得多。
  + DRAM消耗的能量也比SRAM少得多，但速度要慢得多。