# Appendix B Graphics and  Computing GPUs

## B.2 GPU System Architectures

+ discuss system configurations, GPU functions and services, standard programming  interfaces, and a basic GPU internal architecture.

### Heterogeneous CPU–GPU System Architecture

+ A heterogeneous computer system architecture using a GPU and a CPU can be  described at a high level by two primary characteristics
  + how many functional  subsystems and/or chips are used and what are their interconnection technologies  and topology (拓扑结构)
  + what memory subsystems are available to these  functional subsystems

#### The Historical PC (circa 1990)

##### I. configurations

+ The north  bridge (see Chapter 6) contains high-bandwidth interfaces, connecting the CPU,  memory, and PCI bus.
  + north bridge contains memory control unit, connect with CPU and Memory
+ The south bridge contains legacy interfaces and devices:  ISA bus (audio, LAN), interrupt controller; DMA controller; time/counter.
  + <img src="D:\STU\2021-Spring\Core Course\⭐⭐⭐Computer Arch III\Reference\Notes\Image\Fig B.2.1.png" alt="Fig B.2.1" style="zoom:50%;" />.
  + Graphics  subsystems with built-in processing elements (GPUs) did not exist in the PC  landscape of 1990.
+ configurations in common use today
  + Intel
    + <img src="D:\STU\2021-Spring\Core Course\⭐⭐⭐Computer Arch III\Reference\Notes\Image\Fig B 2.2a.png" alt="Fig B 2.2a" style="zoom:50%;" />
  + AMD
    + <img src="D:\STU\2021-Spring\Core Course\⭐⭐⭐Computer Arch III\Reference\Notes\Image\Fig B2.2b.png" alt="Fig B2.2b" style="zoom:50%;" />
  + In both cases, the GPUs and CPUs may access each other’s memory, albeit with less  available bandwidth than their access to the more directly attached memories.
  + In  the case of the AMD system, the north bridge or memory controller is integrated  into the same die as the CPU.
    + north bridge into die

##### II. memory

+ unified memory architecture (UMA)
  + Def: A system architecture in  which the CPU and GPU  share a common system  memory.
  + These systems have relatively low-performance GPUs
  + dedicated GPU memory (专用GPU内存, like GDDR) provides high  bandwidth and low latency.
+ Chapter 5 explains how caches maintain coherence in a shared address space
  + Cache coherence

#### Game Consoles

+ Console systems such as the Sony PlayStation 3 and the Microsoft Xbox 360  resemble the PC system architectures previously described.
  + PS, Xbox
+ Console systems do not need  to have their subsystems expanded and upgraded the way PC systems do, so the  major internal system buses tend to be customized rather than standardized.