---
title: "【应用代数】本原元和极小多项式"
layout: post
categories: 做笔记
tags:
  - Math
  - Algorithm
---

上一篇笔记中整理了域和欧式环的相关概念，并重点介绍了后者的性质和从欧式环构造域的方法。为了构造有限域，并证明特定元素数目的有限域的存在性和唯一性，我们需要一些基本概念和性质作为支撑。这些概念主要围绕本原元和极小多项式展开。

这份笔记涵盖了第5节至第8节课的核心内容，重在理清这些概念之间的关系和思路，严格的数学证明和推导过程请参考领域专业文献。

<!-- more -->

## 本原元

* 域的特征$p$：设域中加法单位元为$e$，$p$个$e$相加（记作$p·e$）为零的最小正整数$p$即为域的特征。（必为素数）

### 1. 有限域元素个数$q$

$q=p^m$.

* 元素的阶(order)：设$ord(\alpha)=t$，则$\alpha^t=1$.

### 2. 阶与元素个数的关系

$t \mid (q-1)$ .

> 去除的元素为零元，用到了拉格朗日定理。

### 3. 域上多项式解的个数

系数在$F$中的$m$次多项式最多有$m$个$F$上的解.

> 数学归纳法

### 4. $\alpha$与$\alpha ^i$阶的关系

* 引理：$\beta^s=1 \Leftrightarrow ord(\beta) \mid s$.

若$ord(\alpha)=t$，则$ord(\alpha^i)=t/gcd(i,t)$.

> 等式两边互推整除关系

### 5. 阶为$t$的元素个数

* 欧拉函数$\phi(t)$: 指$\{0,1,...,t-1\}$中与$t$互素的元素个数。

域中要么没有元素阶为$t$，要么恰有$\phi(t)$个.

> 由「3」能够推出：任何阶为$t$的元素一定在集合$\{1,\alpha,...\alpha^{t-1}\}$内，因为方程$x^t-1=0$至多有$t$个解，而$\{1,\alpha,...,\alpha^{t-1}\}$中元素各不相同。进而由「4」得知阶为$t$的元素恰好有$\phi(t)$个（或0个）。

### 6. 欧拉函数的性质

正整数$n$的所有因子的欧拉函数之和为$n$，即：

$\sum_{d \mid n} \phi(d)=n$.

> 证明思路：通过构造有理数的分数集，并划分为可约分和不可约分的集合，将可约分集约分为最简形式，证得有理数分数集的元素个数$n$与不可约分集合元素个数$\phi(d)$相等。

### 7. 阶为t的元素个数(plus)

（1）若$t\nmid (q-1)$，则不存在这样的元素；

（2）若$t \mid (q-1)$，则恰有$\phi(t)$个这样的元素。

> （1）可由「2」直接得出，（2）可由「5」、「6」联合推出。

* 推论：阶为$(q-1)$的元素共有$\phi(q-1)$个，因此任何域中的非零元乘法都是循环的。

* **本原元(Primitive root)**：阶为$(q-1)$的元素，可通过自乘运算得到整个域中的所有非零元素。

> 寻找本原元：高斯算法
>
> （1）设$i=1$，从域中任意取非零元$\alpha_i$，求出$ord(\alpha_1)=t_1$；
>
> （2）若$t_i=q-1$，执行（5）；
>
> （3）在域中选任意不为$\alpha$幂次的非零元$\beta$，求出$ord(\beta)=s$。若$s=q-1$，则$i$自增1，并令$\alpha_i=\beta$，执行（5）；
>
> （4）找到两个互素且乘积为$t_i$和$s$的最小公倍数的元素$d,e$，即$gcd(d,e)=1$且$d·e=lcm(t_i,s)$，同时满足$d\mid t_i,e\mid s$。令$\alpha_{i+1}=\alpha_i^{t_i/d}·\beta^{s/e}, t_{i+1}=lcm(t_i,s)$，$i$自增1，执行（2）。
>
> （5）输出$\alpha_i$，结束。

### 8. 阶的性质

若$ord(\alpha)=m$，$ord(\beta)=n$，且$gcd(m,n)=1$，则$ord(\alpha · \beta)=m·n$.

> 证两者互相整除

## 极小多项式

有限域$F_{p^m}[x]$.

* 极小多项式概念的推导过程：$m+1$个向量在$m$维空间上必线性相关 -> 取$F_{p^m}$上的任意一个元素$\alpha$，则方程$A_0+A_1\alpha+...+A_m\alpha^m=0$有解 -> 设解集为$S(\alpha)=\{f(x)\in F_p(x):f(\alpha)=0\}$，由上一步知此解集非空 -> 找出$S(\alpha)$中幂次最小的首一(monic)多项式$p(x)$ -> 证明这样的多项式唯一（若存在多个，则相减后幂次会更低，因此唯一） -> 证其整除$S(\alpha)$中其他所有元素（用类似欧式环的方法） -> 称$p(x)$为关于$\alpha$的$F_p$上的极小多项式。

### 9. 极小多项式的性质

（1）$p(\alpha) = 0$；（2）$deg(p)\leqslant m$；

（3）若$f(x)$为$F_p[x]$上的其他满足$f(\alpha)=0$的元素，则$p(x)\mid f(x)$.

* 本原多项式：若$\alpha$为本原元，则称$p(\alpha)$为本原多项式。通常用「$mod\ p(\alpha)$」来表示一个域（后面的章节会证明这个域与其他元素数目相同的域同构）

> 为了更快速地求出极小多项式，需要引入「共轭元」的概念，在介绍「共轭元」之前，给出引理10-12。

### 引理10. 域和子域元素的关系

给出$F_{q^n}$的子域$F_q$，且$\beta \in F_{q^n}$，则：

$\beta \in F_q \Leftrightarrow \beta^q=\beta$ .

且$F_q$中任意元素$x$满足$x^q-x=0$.

> 由「2」易证

### 引理11. 二项式系数性质

若p为素数，则二项式系数$C_p^k$能够被$p$整除（$1\leqslant k\leqslant p-1$）。

### 引理12. 素数次幂的多项展开式

设$\alpha_1,\alpha_2,...,\alpha_t$为域$F_{p^m}$中的元素，则：

$(\alpha_1+\alpha_2+...+\alpha_t)^{p^k}=\alpha_1^{p^k}+\alpha_2^{p^k}+...+\alpha_t^{p^k}\quad(k=1,2,...)$ 

> 证明用到了「引理11」，并结合数学归纳法

### 13. 共轭元性质

* 共轭元（Conjugates）的由来：

  多项式$p(\alpha)=0\Rightarrow p(\alpha^q)=0$（综合引理10-12）

  进一步：$p(\alpha^{q^2})=0, p(\alpha^{q^3})=0,...$

  由于域中元素有限，因此存在循环，记$\alpha^{q^d}=\alpha$.

  则$d$就是$\alpha$共轭元的数目，称$\alpha,\alpha^q,\alpha^{q^2},...,\alpha^{q^{d-1}}$互为共轭元。

元素$\alpha$的共轭元数目$d$是$n$的因子（$d\mid n$），$d$是满足$q^d\equiv 1(mod\ t)$的最小正整数。

> 符号说明：
>
> 拥有$q^n$个元素的有限域。
>
> $d$也被称为$\alpha$的**度（degree of $\alpha$）**，$t$是$\alpha$的阶（$ord(\alpha)=t$）。
>
> $q^d\equiv 1$ 也可视作$\alpha^{q^d}=\alpha$，即共轭元的定义。

### 14. 由共轭元确定极小多项式

设$F$是拥有$q^n$个元素的有限域，$k$是含$q$个元素的子域，若$\alpha\in F$，则$\alpha$在$k$上的极小多项式为：

$f_\alpha(x)=(x-\alpha)(x-\alpha^q)...(x-\alpha^{q^{d-1}})$.

> 在$k$上是指系数属于子域$k$。
>
> $\alpha$的极小多项式次数=$\alpha$的共轭元个数=$d$

---

以上所有性质和概念的相关联系如下图所示：

![](https://github.com/HusterHope/blogimage/raw/master/20181121-1.png)
