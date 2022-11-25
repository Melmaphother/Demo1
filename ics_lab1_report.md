## ICS_Lab1_Report

#### 姓名：王道宇

#### 学号：PB21030794

#### 时间：2022/11/5

### Purpose

> 本实验的内容为，给定数据$A$和$B$，其中$A,B$的范围如下：
> 
> $$
> \begin{aligned}
0x0001<A<0x7FFF\\
0x0001<B<0x000F
\end{aligned}
> $$
> 
> 需要编写程序得出$A$中从最低位（即第0位）到第$B$位中1的个数。

### Principle

> 由于只需要考虑A的最低的$B$位有多少个一，我们只需要用$0x0001, \space0x0002, \space 0x0004\dots$直到$0x0001$ 左移B位的结果和A做与操作，结果是1时计一次数，为0时不计数即可。为了实现左移这一操作，可以在循环中给出一条指令让某个变量一直乘2即可。

### Procedure

> 所设指令的伪代码依次为
> 
> 1. 起始地址为$x3000$
> 
> 2. $R_0 = M[x3001+x00FF] = M[x3100] = A$
> 
> 3. $R_1 = M[x3002+x00FF] = M[x3101] = B$
> 
> 4. $R_2 = 0$，作为计数器，最终输出1的个数
> 
> 5. $R_3 = 0$，作为循环变量
> 
> 6. $R_4 = R_3 + 1$   $R_4$作为左移$B$位的变量一直与和$R_0$相与
> 
> 7. $R_5 = R_0R_4$ ，其中$R_0$就是$A$
> 
> 8. $(R_5 = 0) \space ?\space jump\space to \space 10 \space :\space jump\space to \space9$
> 
> 9. $R_2 = R_2 + 1$   计数
> 
> 10. $R_4 = R_4 + R_4$   左移
> 
> 11. $R_3 = R_3 + xFFFF = R_3 - 1$ 循环变量递减
> 
> 12. $R_6 = R_1 + R_3$ 循环变量与$B$相加做判断
> 
> 13. $(R_6 > 0) \space ?\space jump\space to \space 7 \space :\space jump\space to \space14$
> 
> 14. $R_3 = 0$  将循环变量清零
> 
> 15. $M[x300E + x00F4] = M[x3102] = R_2$ 将$R_2$中的内容储存到对应的内存中

### Result

> 测试参数为：$A = 13, B = 3$

<img src="file:///C:/Users/Melmaphother/Desktop/网课期间作业/ics_lab1_图片/QQ图片20221106085818.png" title="" alt="" width="680">

> 测试参数为：$A = 167,B = 6$

![](C:\Users\Melmaphother\Desktop\网课期间作业\ics_lab1_图片\167.jpg)

> 测试参数为：$A = 32767,B = 15$

![](C:\Users\Melmaphother\Desktop\网课期间作业\ics_lab1_图片\32767.jpg)
