### 主题：ics第一次作业
### 时间：10月3日
### 学号：PB21030794
### 姓名：王道宇

## T1
a. $ax+b$   
![a选项](F:\markdown\picture_1_a.jpg)  
b. The average of the four input numbers w, x, y, and z  
![b选项](F:\markdown\picture_1_b.jpg)  
c. $x^2-y^2$  
![c选项](F:\markdown\picture_1_c.jpg)  
d. $a^6$  
![d选项](F:\markdown\picture_1_d.jpg)

## T2  
(1)Convert these decimal numbers to eight-bit 2's complement binary numbers.  
a. 98  
答：$(98)_D=(01100010)_B$ ,其为正数，补码仍然为$(01100010)_B$   
b. -105  
答：$(-105)_D=(11101001)_B$ ,其为负数，补码为其取反加一$(10010111)_B$  
  
(2) Convert the following eight-bit 2's complement binary numbers to decimal.  
注：首先，补码的补码为其本身  
c. 01000010  
答：该数为正数，原码就是补码，故该数为$(01000010)_B=(66)_D$  
d. 11101111  
答：该数为负数，原码为补码的补码，故该数的原码为$(10010001)_B=(-17)_D$

## T3
a. $01+110011$  
答：原式$=00000001+11110011=11110100$ ,原码为$10001100$ ,换为十进制为$-12$  
b. $111+0100110$  
答：原式$=11111111+00100110=00100101$,其中结果的最高位前一位有一个$1$为溢出位，可不计，原码为其本身，换为十进制为$37$  
c. $1010+1101$  
答：直接相加会溢出，考虑8位二进制数，则：原式$=11111010+11111101=11110111$ ，其中结果的最高位前一位有一个$1$为溢出位，可不计，原码为$10001001$ ,换为十进制为$-9$  
d. $0001+1110$  
答：直接相加不会溢出，故原式$=0001+1110=1111$ ，原码为$1001$ ,换为十进制为$-1$

## T4
正数补0，负数补1  
a. $101011->11101011$  
b. $011110->00011110$  
c. $11111111110000->11110000$  
d. $00001->00000001$  

## T5
$(4.3)_D=(100.01001100110011...)_B$  
IEEE floating point representation：  
取32位单精度：  
$sign=0$  
$fraction=00010011001100110011001$  
$exponent=00000010$  
表示了$(4.3)_D=(-1)^{sign}\times(1+fraction)^{exponent}$,其中各变量如上。  
C语言代码：  
```c
  #include <stdio.h>

    union my_union {
        int   a;
        float b;
    };

    int main() {
        union my_union t;
        t.b = 4.3;
        t.a=(int)t.b
        for (int loop = 31; loop >= 0; loop--) {
            putchar((t.a&(1<<loop))) == 0 ? '0' : '1');
        }
        return 0;
    }

```
如果指数位全为1，当$fraction=0,s=0$时表示正无穷$+\infty$ ;当$fraction=0,s=1$时表示负无穷$-\infty$;当$fraction\neq0$时表示$not\; a\;number$

## T6
$0\;10001001\;11111001101001000000000$中  
$Bias=127,$  
$sign=0,$  
$exponent=(10001001)_D=(127+9)_D，E=exp-bias=(9)_D,$  
$fraction=0.97509765625$  
故该数为$1.97509765625$ 

## T7
(1)  
a. $10100101\;AND\; 11010101 = 10000101$  
b. $10001110\;OR\;11110101=11111111$  
c. $NOT(11110001)\;OR\;NOT(01011010)=NOT(11110001\;AND\;01011010)=10101111$  
(2)  
d.$(x1234\;AND\;X5678) \;OR \;(xABCD\;AND\;X99EF)=x1230\;OR\;x89CD=
x9BFD$  
e.$x6A12\;XOR\;x3A15=x5007$  

## T8
$Q1 = (A \;AND \;B) OR \;NOT(C)$  
| A | B | C | Q1 |   | A | B | C | Q1 |
|---|---|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 1 |   | 1 | 0 | 0 | 1 |
| 0 | 0 | 1 | 0 |   | 1 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |   | 1 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 |   | 1 | 1 | 1 | 1 |

$Q2 = NOT(NOT(A)\;OR\;NOT(B)) AND\;C=A\;AND\;B\;AND\;C$  
| A | B | C | Q2 |   | A | B | C | Q2 |
|---|---|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 |   | 1 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |   | 1 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 |   | 1 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |   | 1 | 1 | 1 | 1 |

## T9
(1). Convert ASCII string "\t\n\r" to base64  
   "\t\n\r"转换为二进制为：0000,1001,0000,1010,0000,1101 ,对应了base64为：000010，010000，101000，001101=CQoN  
(2). 对base64的设想：  
Base64 is widely used for sending e-mail attachments. This is required because SMTP – in its original form – was designed to transport 7-bit ASCII characters only. This encoding causes an overhead of 33–37% (33% by the encoding itself; up to 4% more by the inserted line breaks).  
摘自:wikipidia

## T10
What is the largest positive number that can be represented by an IEEE floating point number (Normalized Form)?  
$sign=0,exponent=11111110,fraction=111,1111,1111,1111,1111,1111$  
相当于：$\sum_{i=254}^{231}2^i=2^{255}-2^{231}$

## T11
//感觉不用select box也行？是不是哪里写错了？
(1)浮点乘法运算
```c
//Subtract(a,b)=Add(a,Multiple(b,-1));//减法定义
    int main(){
        frac_A=A[0:23];
        M_A={1,frac_A};
        frac_B=B[0:23];
        M_B={1,frac_B};
        exp_A=A[23:31];
        exp_B=B[23:31];
        M_C=Mutiple(M_A,M_B);//得到一个48位的二进制数
        i=47;
        while(!M_C[i]){
            i=Subtract(i,1);
        }
        M_C=M_C[i:i-23];//选择第一个1后的23位
        exp_C=i//第一个1的位置即为指数
    }
```  

(2)浮点加法运算
```c
    //伪代码
    //select定义为：select(sel,a,b);
    int main(){
        output=1;
        frac_A=A[0:23];
        M_A={1,frac_A};
        frac_B=B[0:23];
        M_B={1,frac_B};
        exp_A=A[23:31];
        exp_B=B[23:31];
        while(output){
            output=select(exp_A>exp_B,0,1);
            if(output){
                exp_B=Add(exp_B,1)
                Shift_Right(M_B,1);
            }
        }
        M_A={0,M_A}；
        M_B={0,M_B};//防止进位影响
        M_C=Add(M_A,M_B);//此时会得到一个25位的二进制数
        if(M_C[24]==1)Shift_Right(M_C,1);//出现进位需要丢弃尾数
        frac_C=M_C[0:23];
        exp_C=exp_A;
        C={0,exp_C,frac_C};
    }
```