[TOC] 

# 一、0的故事——无即是有
数字的表示方法不是突然就形成的，阿拉伯数字（印度）**10进制计数法**深入人心，但这一过程经历了上千年历史。现在依旧还存在着**罗马数字**这种非按位计数法数字（1998：```MCMXCVIII```）。
> 日常生活的0  
没有计划的计划  
没有药效的药  
指数表示法——着眼于0的个数的计数法。例如`$10^{12}$`和`$10^{13}$`的比较用指数表示会更好一些。

## 1.按位计数法
基数N：N进制数
N进制中，4位数`$a_3a_2a_1a_0 $`为
```math
a_3*N^3+a_2*N^2+a_1*N^1+a_0*N^0
```
这里的数字0不代表没有，只代表该数位上没有，但++0起到的占位作用++不能忽略。
## 2.指数法则
当我们将指数理解成“`$10^n$`是n个10相乘”，会自然而然想到1,2,3,4，当`$10^0$`如何解释呢？++0个10相乘？++  
| `$10^3$` |`$1000$`|
|:-: | :-: |
|`$10^2$`|100|
|`$10^1$`|10|
|`$10^0$`|1|
|`$10^{-1}$`|0.1|
|`$10^{-2}$`|0.01|
**注意指数向下减一,数则变成其10分之1**

---
# 二、逻辑——真与假的二元世界
> 能判断对错的陈述句叫做**命题**。

## 1.完整性和排他性
在考虑规则时，确认有没有"**遗漏**"和"**重复**"。  
没有“遗漏”，即具备**完整性**，由此明确该规则无论在什么情况下都能使用。  
没有“重复”，即具备**排他性**，由此明确该规则不存在矛盾之处。

## 2.复合型逻辑表达式

||数学符号|c/c++语法|含义|真|比较|
|:-|:-:|:-:|:-|:-|:-|:-:|
|**逻辑非**| -A|!|不是|只有A=false时，`-A`为true||
|**逻辑与**|A`$\bigwedge$`B |&&|并且|只有A=true，B=true，**A`$\bigwedge$`B**为true|
|**逻辑或**|A`$\bigvee$`B| \|\| |或者|仅当A和B都为false时,**A`$\bigvee$`B**才为false|
|**异或**|A`$\bigoplus$`B|xor(^)|异或|A或B为true( 但AB不能同时为true ),**A`$\bigoplus$`B**为true|**异或的否定**`-（A xor B）`**是**`A=B`|
|**相等**|A=B|==|相等|A和B的真假相等时，**`A=B`**为真|**同上，**`(-(A xor B))`**=**`(A=B)`|
|**蕴涵**|A`$\Rightarrow$`B|**if(A)**<br>**B=true;**|若A，则B|A=true，B=false时，**A`$\Rightarrow$`B**才为false，其余为true|**B`$\Rightarrow$`A 不为真（逆命题和原命题无联系）**|
|---|---|---|---|只要A为false，不论B的真假，**A`$\Rightarrow$`B**恒为真|**(-B)`$\Rightarrow$`(-A)为真（逆否命题同真同假）**|
|---|---|---|---|若A为true，B也为true，**A`$\Rightarrow$`B**为true||
## 3.双命题逻辑运算——真值表
||命题|同真|A真B假|A假B真|同假|十进制数|二进制数|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
||A|true|true|false|false|
||B|true|false|true|false|
|||||||
||恒为false|false|false|false|false|0|0000
||A`$\bigwedge$`B|true|false|false|false|1|0001
||A`$\bigwedge$`(-B)|false|true|false|false|2|0010
||A|true|true|false|false|3|0011
||(-A)`$\bigvee$`|false|false|true|false|4|0100
||B|true|false|true|false|5|0101
|A`$\bigoplus$`B|-(A=B)|false|true|true|false|6|0110
||A`$\bigvee$`B|true|true|true|false|7|0111
||-(A`$\bigvee$`B)|false|false|false|true|8|1000
||A=B|true|false|false|true|9|1001
||-B|false|true|false|true|10|1010
||A`$\bigvee$`(-B)|true|true|false|true|11|1011
||-A|false|false|true|true|12|1100
|A`$\Rightarrow$`B|(-A)`$\bigvee$`B|true|false|true|true|13|1101
||-(A`$\bigwedge$`B)|false|true|true|true|14|1110
||恒为true|true|true|true|true|15|1111
## 4.德·摩根定律
> (-A)`$\bigvee$`(-B)=-(A`$\bigwedge$`B)  
(-A)`$\bigwedge$`(-B)=-(A`$\bigvee$`B)

|A||B||(-A)`$\bigvee$`(-B)|-(A`$\bigwedge$`B)||(-A)`$\bigwedge$`(-B)|-(A`$\bigvee$`B)|
|:-:|:-:|:-:|:-:|-:|:-|:-:|-:|:-|
|true||true||false|false||false|false|
|true||false||true|true||false|false|
|false||true||true|true||false|false|
|false||false||true|true||true|true|
|||||↑_|_↑||↑_|_↑|


### 逻辑表达式的对偶性
> 在逻辑表达式中**分别将true和false、A和-A、`$\bigvee$`和`$\bigwedge$`进行互换，就能够得到该逻辑表达式的否定式。**

|true|\<\-->|false|转换后，新、旧表达式互为否定式|
|:-:|:-:|:-:|:-:|
|A|\<\-->|-A||
|`$\bigvee$`|\<\-->|`$\bigwedge$`||
## 5.包含未定义的逻辑
> 实际上，在程序中由于某些错误导致**无法得到true或者false中的任何一个值。**  
undefined意为“未定义”假设计算机遇到这种情况不进行任何处理。

### 带条件的逻辑与(&&)
带条件的逻辑与——**根据条件A判断是否需要看B。**  
注意，这里的 A&&B 已经不是A`$\bigwedge$`B了。
```c++
if(A){
    if(B){
        ...
    }
}
```
A&&B并不等于B&&A
```c++
//这里的check()函数起到了检查的可否执行execute的作用。
if(check() && execute(){
    ...
}
```

A&&B如果不包含undefined时，A&&B和A`$\bigwedge$`B相等，下表仅列出值带undefined的情况：
|A|B||A&&B||
|-|-|-|-|-|
true|undefined||undefined|
false|undefined||false|A为false，A&&B恒为false|
undefined|true||undefined|
undefined|false||undefined|
undefined|undefined||undefined|


### 带条件的逻辑或(||)
同样，带条件的逻辑或——**根据条件A判断是否需要看B。**  
注意，这里的 A&&B 已经不是A`$\bigvee$`B了。
```c++
if(A||B){
    ...
}
```
等同于
```c++
if(A){
    ...
}else if(B){
    ...
}

```
A||B如果不包含undefined时，A||B和A`$\bigvee$`B相等，下表仅列出值带undefined的情况：
|A|B||A\|\|B||
|-|-|-|-|-|
true|undefined||true|A为true，A&&B恒为true|
false|undefined||undefined|
undefined|true||undefined|
undefined|false||undefined|
undefined|undefined||undefined|

### 三值逻辑的否定(!)
注意，这里的!A已经不是-A了。  
不包含undefined时，!A和-A相等。
|A|!A|
|-|-|
|undefined|undefined|
### 三值逻辑的德·摩根定律
在有undefined的参与下，以下式子(德·摩根定律)还成立吗？  
① (!A || !B) \=\= !(A && B)  
② (!A)&&(!B) \=\= !(A || B)  

编程中常用的到逻辑符号，真值表如下，**三值逻辑下的德·摩根定律依旧成立。**
|A|B||!A|!B|(!A)&&(!B) | (!A)\|\|(!B)|A&&B|!(A&&B)|A\|\|B|!(A\|\|B)|
|:-:|:-:|-|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
true|true||false|false|false|false|true|false|true|false|
true|false||false|true|false|true|false|true|true|false|
true|U||false|U|false|U|U|U|true|false|
false|true||true|false|false|true|false|true|true|false|
false|false||true|true|true|true|false|true|false|true|
false|U||true|U|U|true|false|true|U|U|
U|true||U|false|U|U|U|U|U|U|
U|false||U|true|U|U|U|U|U|U|
U|U| |U|U|U|U|U|U|U|U|
 | | | | | |②|①| |①| |②
```c++
if((x>=0)&&(y>=0){
    ...
}//等同于
if(!(x<0||y<0)){
    ...
}
```

三、余数——周期性和分组
======
## 1.余数的力量——将大数字除一次就能分组
> 一亿天之后是星期几？  
`$10^{100}$`天之后是星期几？  
`$1234567^{987654321}$`的个位数是多少 

以上两个问题，只要着眼于不同的地方，  
运用余数推出数字的周期性，就能将大数字简化成小数字的问题。  
## 2.奇偶校验（分组）
奇偶校验位有**偶校验**和**奇校验**  
[奇偶校验——维基百科](https://zh.wikipedia.org/wiki/%E5%A5%87%E5%81%B6%E6%A0%A1%E9%AA%8C%E4%BD%8D)  
[奇偶校验——百度百科](https://baike.baidu.com/item/%E5%A5%87%E5%81%B6%E6%A0%A1%E9%AA%8C)
> 奇偶校验的例子：  
寻找恋人——奇数村和偶数村  
铺设草席——将每一块地分类  
哥尼斯堡七桥问题——奇点和偶点（思考的是出入度的奇偶性，而不是出入度本身）

# 四、数学归纳法
> 最简单和最常见的数学归纳法是证明当n等于任意一个自然数时某命题成立。(wiki百科)  

 证明分下面两步：  

- 1.**基底的证明**（推倒第一张多米诺骨牌）  
```math
证明当n=1时命题成立。  
```  

- 2.**归纳的证明**（让下一张多米诺骨牌倒下）  
```math
假设在n=k时命题成立，推导在n=k+1时命题也成立。  
```

> 这种方法的原理在于：首先证明在某个起点值时命题成立，然后证明从一个值到下一个值的过程有效。当这两点都已经证明，那么任意值都可以通过反复使用这个方法推导出来。 

> - **循环实现归纳过程**
>> 在编写循环时，找到让每次循环都成立的逻辑表达式很重要。这种逻辑表达式称为**循环不变式**。循环不变式相当于用数学归纳法证明的“断言”。

# 五、排列组合
**认清计数对象的性质**

## 1.置换
> 将n个事物按顺序进行排列称为**置换**。  
得到n!(n的阶乘)  
根据第2点，可以将置换理解为在n个事物中选n个进行排列，记做`$P^n_n$`

```math
n!=n\times(n-1)\times(n-2)\times....\times2\times1\ \ \ (共n项)
```

## 2.排列
> 将从n个事物中选k个按一定顺序排列称为**排列**，排列总数记做`$P^k_n$`  
P是`$permutation$`的缩写。  
"5张牌中选0张进行排列的总数"为`$P_5^0$`，而`$P_5^0$`=1，不等于0。  

```math
P^k_n=(n-0)\times(n-1)\times(n-2)\times....\times(n-k+1)\ \ \ \ （共k项）
```
用阶乘表示：
```math
P_n^k=\cfrac{n!}{(n-k)!}
```
举例：从5张牌中选3张出来进行排列，总共多少种情况？  
`$P_5^3$`=`$\cfrac{5\times4\times3\times2\times1}{2\times1}$`=`$5\times4\times3$`  （约分）

## 3.组合
从n个事物中取k个，**不考虑它们的顺序**，这种取分称为**组合(combination)**，组合总数记做`$C_n^k$`  
> 要计算n中取k的组合总数，只要这样考虑即可：
    > - 首先，和排列一样“考虑顺序”进行计数  
    > - 除以 重复计数的部分（重复度）  
    
```math
C_n^k=\cfrac{从n张里面取k张的排列总数}{k张的置换总数}=\cfrac{P_n^k}{P_k^k}
```
```math
=\cfrac{\cfrac{n!}{(n-k)!}}{k!}=\cfrac{n!}{(n-k)!}\times\cfrac{1}{k!}
```
```math
=\cfrac{n!}{(n-k)!\times k!}
```

## 4.置换、排列、组合的关系
> 从5张牌选3张进行排列。
>- 置换——“3张牌的交替排列方法”  
>- 组合——“3张牌的取法”  
>- 排列——“取出3张牌，进行交替排列”  

```math
“3张的置换”\times “从5张中取3张的组合”=“从5张中取3张的排列”
```
```math
P_3^3\times C_5^3=P_5^3
```
>- **重复组合**  
> 不需要排序，可以以固定顺序排好以模拟，使用“**隔板**”可以解决。   
>- 善用逻辑  
> (【1】+【2】-【3】)/重复度  
> 【1】左端是王牌的情况；【2】右端是王牌的情况；【3】两端是王牌的情况  
> 文氏图画逻辑：【所有】-【局部】
>>- 1.药品ABC三种，新药调剂规则：  
>>>- 从ABC这3中药品中，共取100粒进行调剂。
>>>- 调剂时，ABC这三种药品每种至少有1粒。
>>>- 不考虑药品调剂的顺序。
>>>- 同种药品每粒都相同。  
>>- 2.现在用5张扑克牌，王牌2张，JQK各一张。将这5张牌排成一排。规则：
>>>- 左端或者右端至少有一端是王牌的排法有多少钟？(不区分大小王牌)



# 六、递归

# 七、指数爆炸

# 八、不可解问题

---
# 名人列表
|名字|英文|名号|
|:-:|:-:|:-:|
|高斯|Karl Friedrich Gauss|数学家|
|德·摩根|De Morgan|逻辑学家|
|莱昂哈德·欧拉|Leonhard Euler|图论开山鼻祖|
|爱德华·卢卡斯|Edouard Lucas|发明"汉诺塔"|
|斐波那契|Lenoardo Fibonacci|斐波那契数列|
|约翰·奈皮尔|John Napire|发明对数|
