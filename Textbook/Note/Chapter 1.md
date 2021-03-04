# High Performance Computing

+ 像高性能计算这样复杂的学科是有挑战性的，因为几乎所有的东西都是根据其他东西来定义的，并且与其他东西相关联。
+ 第一章简要介绍了高性能计算的基本要素

## Chapter 1 Introduction

### 1.1 HIGH PERFORMANCE COMPUTING DISCIPLINES

+ 高性能计算实际上是多个相关学科的集合，每个学科都提供了整个领域的一个重要方面。

#### 1.1.1 Definition

+ HPC is a field of endeavor that relates to all facets of technology, methodology, and application
  associated with achieving the greatest computing capability possible at any point in time and technology.
  + 高性能计算是一个努力的领域，涉及技术、方法和应用的所有方面，与提高最佳计算能力相关联。

#### 1.1.2 APPLICATION PROGRAMS

+ 高性能计算的目的是通过经验主义、理论，甚至是广泛可用或可访问的商用计算机(如企业服务器)，得出无法单独解决的问题的答案。

#### 1.1.3 PERFORMANCE AND METRICS

##### I. Metrics

+ There is no single measure of performance that fully reflects all aspects of the quality of computer operation.
  + 即需要多角度去评判`performance`
  + These two fundamental measures are
    +  “time”
    +  “number of operations”
+ For HPC the most widely used metric is “floating-point operations per second” or “flops”.
  + 对于高性能计算，最广泛使用的指标是“每秒浮点运算”或“浮点运算”。
  + 使用希腊前缀kilo、mega、giga、tera和peta分别表示1000、100万、10亿、1万亿和1千万亿。

##### II. Benchmark

+  HPC community selects specific problems around which to standardize. Such standardized application programs are “benchmarks”.
+ 高性能计算社区选择具体问题进行标准化。这样的标准化应用程序就是“基准”。
+ Ex
  + One particularly widely used supercomputer benchmark is “Linpack”, or more precisely the “highly parallel Linpack” (HPL), which solves a set of linear equations in dense matrix form.
  + 一个特别广泛使用的超级计算机基准是“Linpack”，或者更准确地说是“高度并行的Linpack”(HPL)，它以密集矩阵的形式求解一组线性方程

#### 1.1.4 HIGH PERFORMANCE COMPUTING SYSTEMS ####

##### I. Intro

+ 今天，这些机器呈现为一排排的机架，占据了数千平方英尺的空间，潜在地消耗了数兆瓦的电力。
+ 高性能计算系统的核心是其无数组件的结构和组织，以及它们操作和执行提供给它们的用户应用程序的语义或规则。
+ 高性能计算系统不仅仅是硬件，它还是一系列控制物理组件层次结构和管理用户工作负载的软件组件。

##### II. Feature

+ HPC System 和laptop以及desk-side workstation or departmental enterprise server有许多**共同之处**
  + has a software structure that serves many of the same purposes of interface, control, and functionality, including but not limited to the following.
  + 具有服务于许多相同的接口、控制和功能目的的软件结构，包括但不限于以下内容。
    + 管理机器及其操作的所有方面的操作系统。 HPC S 也有 OS
    + 还有一些和传统computer类似的功能，具体在书中有列出
+ 与传统计算机区别
  + <img src="D:\STU\2021-Spring\Core Course\⭐⭐⭐Computer Arch III\Note\Image\1614480838(1).png" alt="1614480838(1)" style="zoom:50%;" />.
  + 高性能计算系统与传统计算机的区别在于这里所示的许多组件资源的组织、互连性和规模。
  + “节点”包含计算所需的所有功能元素，并且高度复制以实现大规模。
  + 理解为高度的并行性，每个Node都是一台独立的计算机

#### 1.1.5 SUPERCOMPUTING PROBLEMS

##### I. Background

+ 超级计算的起源在于模拟由核物理驱动的问题，所以许多超级计算问题都是在跟踪由不同物种组成的大型粒子系统的背景下提出的，这些粒子系统可能相互作用，并且不平衡。
+ 这种非平衡问题通常很难分析计算，实验探索的成本也很高。
+ ex
  + 例如，很大一部分超级计算时间花在求解流体流动的纳维尔-斯托克斯方程上，因为它们与许多工程问题相关。
  + 第二个例子是，LIGO科学合作组织在2015年直接检测到重力辐射的天体物理源，这得到了数百万小时的超级计算资源的支持，这些资源用于求解爱因斯坦场方程，以模拟双星黑洞的合并。

##### II. Linear Algebra and Graphic problem

+ 许多类别的高性能计算问题是围绕超级计算机解决线性代数问题的能力设计的。
+ 目前用来衡量超级计算机最高性能的主要基准是一个密集的线性代数问题。
+ 虽然许多高性能计算问题源于数学模型，但今天一些最重要的超级计算问题源于图形问题 (Graphic Problem) 。
  + Graph problems often come from problems arising in knowledge 
    + management, 
    + machine intelligence, 
    + linguistics, 
    + networks, 
    + biology, 
    + dynamical systems, and 
    + collections of pair-wise systems.

#### 1.1.6 APPLICATION PROGRAMMING

##### I. HPC programming characteristics

+ 但是对于高性能计算来说，传统采用的编程接口数量相对较少，大约为几十个，尽管有更多的实验或研究模型。
+ 超级计算领域的编程有额外的要求和特点。
  + 性能是高性能计算编程区别于其他领域的驱动要求。仅次于正确性和可重复性
  + 对计算并行性的表示和利用的需求最能代表性能
  + 高性能计算编程的第二个方面是控制数据和任务分配与并行和分布式系统 (distributed systems) 的物理资源之间的关系。

##### II. Programming Models

+ 根据并行系统体系结构类别的性质，采用不同的编程模型。
+ 多线程共享内存系统编程接口，如OpenMP和Cilk，强调细粒度并行。
+ 中到粗粒度的并行性，如高度规模的大规模并行处理器(MPPs)和集群所反映的，主要由通信顺序进程表示，如消息传递接口(MPI)及其许多变体。

### 1.2 IMPACT OF SUPERCOMPUTING ON SCIENCE, SOCIETY, AND SECURITY

+ 高性能计算代表着增长最快的市场之一，主要由各种应用领域的最终用户需求驱动，包括金融服务、石油和天然气、制造、地球科学、生命科学、国家实验室和政府情报。
+ PS：这部分内容作为一个科普介绍，了解即可

#### 1.2.1 CATALYZING FRAUD DETECTION AND MARKET DATA ANALYTICS 催化欺诈检测和市场数据分析

+ 越来越多的金融服务公司，如自营交易公司、投资银行和支付处理公司，正在部署超级计算来解决回测、风险管理和欺诈检测等核心业务问题。
+ 营交易和投资管理公司经常部署高性能计算系统(Tflops的w100s)来开发准确的交易策略和预测市场表现，使他们能够打包高利润的金融工具。

#### 1.2.2 DISCOVERING, MANAGING, AND DISTRIBUTING OIL AND GAS

+ 石油和天然气公司是超级计算技术的最大商业用户，包括所有公开引用的商业petascale系统。
+ 在勘探中，超级计算机被用于通过地下成像识别油藏的高分辨率地震处理

#### 1.2.3 ACCELERATING INNOVATION IN MANUFACTURING

+ 航空航天、汽车、消费品、重工业、轮胎制造商和电子/半导体制造商，这些不同行业的共同点是将计算机辅助工程应用程序用于产品设计和制造过程。

#### 1.2.4 PERSONALIZED MEDICINE AND DRUG DISCOVERY

+ 生命科学是另一个主要的垂直领域，在各种应用领域依赖高性能计算技术。
+ 级计算被研究人员和企业用于基因组测序和药物发现。制药公司通常使用各种分子动力学模拟方法部署超级计算机来加速药物发现过程。

#### 1.2.5 PREDICTING NATURAL DISASTERS AND UNDERSTANDING CLIMATE CHANGE

+ 超级计算经常被用来研究气候变化及其影响。
+ 高性能计算模型用于预测自然灾害的各个方面，如地震的强度和影响、飓风的路径和强度、海啸的方向和影响等

### 1.3 ANATOMY OF A SUPERCOMPUTER

##### I. Intro

+ 泰坦，它是世界上最快的计算机之一。
+ Titan is a Cray XK7 architecture: a heterogeneous architecture reflecting an important trend in HPC
  + 异构，在HPC领域很重要的概念和趋势
  + 也是GPU架构研究必须关注和了解的概念

##### II. Layer

+ <img src="D:\STU\2021-Spring\Core Course\⭐⭐⭐Computer Arch III\Note\Image\1614483221(1).png" alt="1614483221(1)" style="zoom:50%;" />.
  + 通用超级计算机的系统堆栈由一个系统硬件层和几个软件层组成。
  + 第一个软件层是操作系统，包括资源管理和访问输入/输出(I/O)通道的中间件。
    + OS的下层就是hardware
  + 更高的软件层包括运行时系统和工作流管理。
+ 整个工作管理层涉及几个支持功能，包括
  + **编程语言**(如Fortran、C、C语言)、
  + 通常用于并行的**附加库**(如MPI、OpenMP)以及
  + 为处理器内核提供机器可读代码并根据用户代码进行翻译和优化的**编译器**。
+ 超级计算机系统的最后一层是运行时系统软件。

### 1.4 COMPUTER PERFORMANCE

+ 如何度量computer performance?

#### 1.4.1 PERFORMANCE

+ 有必要以一种或多种有用的方式定义performance，并建立用于衡量绩效的量化指标。
  + 即1. 多维度的benchmark
  + 2. 量化

#### 1.4.2 PEAK PERFORMANCE

##### I. Definition

+ the maximum rate at which operations can be accomplished theoretically by the hardware resources of a supercomputer.
  + 理论上超级计算机的硬件资源可以完成操作的最大速率。

##### II. History

+ 峰值性能由设备技术提供的时钟速率和计算机体系结构确定的硬件并行度的组合决定。两者都是器件密度的函数
+ 在过去的40年中，器件密度呈现出显著的增长速度。戈登·摩尔捕捉到了这一趋势，他预测设备密度将每两年增加两倍。
  + 也就是摩尔定律
+ Thus peak performance in terms of operations per second is determined by clock rate and architecture.
  + 就每秒操作数而言，峰值性能取决于时钟速率和架构。

#### 1.4.3 SUSTAINED PERFORMANCE

+ 持续性能是超级计算机系统在运行应用程序时实现的实际或真实性能。
+ 与指定的峰值性能相比，持续性能被认为是超级计算机真正价值的更好指标。

#### 1.4.4 SCALING

+ a simple and widely used measure (to quantify the size of a system) is 
  + the number of processor cores employed
+ weak scaling ?
  + the size of data and the size of system成比例增长
  + 系统规模增加，给定core所做的工作量也保持不变
  + 但是实际情况是由于成本，per core的内存量在下降,  limiting the opportunity for weak scaling
  + 曾经有人认为there would be about 1 byte of main memory per 1 flops of performance.。
    + 目前只能达到90%
    + 太湖之光可以达到99%（比起理想情况下降了1%）

#### 1.4.5 PERFORMANCE DEGRADATION

This formalization of performance degradation is referred to through the acronym SLOW, which identifies the sources as 

+ starvation, 	
  + Starvation directly relates to a critical source of performance, parallelism
  + 即无法达到最理想的情况，所有硬件资源都busy。可能有一些空闲，而有一些过于busy
+ latency, 
  + locality to reduce latency
  + 以及经常提到的  "hide long latency"，例如pipeline, GPU
+ overhead, and 
  + Definition:  the amount of **additional work** beyond that **actually required** to perform the computation (such as on a pure sequential processor)
+ waiting for contention
  + easy to see，资源竞争，例如ALU等硬件资源竞争
  + Typical examples include bank conflicts for main memory and insufficient bandwidth for communication networks.

#### 1.4.6 PERFORMANCE IMPROVEMENT

+ 高性能计算用户可以找到许多方法来提高交付的性能，有时称为“性能调试” (performance debugging) 。
+ Method
  +  hardware scaling, 
  + parallel algorithms, 
  + performance monitoring, 
  + work and data distribution, 
  + task granularity control

### 1.5 A BRIEF HISTORY OF SUPERCOMPUTING

+ 可以划分为7个时代，了解即可

