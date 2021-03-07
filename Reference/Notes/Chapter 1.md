# Chapter 1 Computer Abstractions and Technology

## 1.8 The Power Wall 

##### I. Trend

+ <img src="D:\STU\2021-Spring\Core Course\⭐⭐⭐Computer Arch III\Reference\Notes\Image\Fig1.16.png" alt="Fig1.16" style="zoom:50%;" />.

+ Both clock rate and power increased rapidly for  decades and then flattened off recently

+ the reason for their recent slowing is that we have run into the  practical power limit for cooling commodity microprocessors.

  

##### II. CMOS

+ The dominant technology for integrated circuits is called CMOS (complementary  metal oxide semiconductor).
+ For CMOS, the primary source of energy consumption  is so-called dynamic energy—that is, energy that is consumed when transistors  switch states **from 0 to 1** and vice versa.
+ The dynamic energy depends on the  capacitive loading of each transistor and the voltage applied:
  + Energy ∝ Capacitive load * Voltage^2

##### III. Leakage

+ With regard to Figure 1.16, how could `clock rates` grow by a factor of 1000 while  `power` increased by only a factor of 30? 
  + which means clock rate increased rate is 33.33 times than power, good efficiency.
+ Energy and thus power can be reduced by  **lowering the voltage**, which occurred with each new generation of technology, and  power is a function of the voltage squared.
+  In 20 years, voltages have gone from 5V to 1V, which is why  the increase in power is only 30 times.
+ The modern problem is that further lowering of the voltage appears to make the  transistors too **leaky**, like water faucets that cannot be completely shut off.
  + Thus we can't lower the voltage infinitely.
+ In servers, leakage is typically responsible for 40% of the energy  consumption. 
  + Leakage is a big problem in power and energy