---
title:  经典摘录-Bayes' rule贝叶斯定律
mathjax: true
mathjax2: true
categories: 中文
tags: [probability, 概率论]
date: 2017-08-28 20:16:00
commets: true
top: true
toc: true
---

说明：全文摘自[Introduction to probability, 2nd Edition](http://www.athenasc.com/probbook.html) 

本文讨论条件概率定律的应用，首先引入一个计算事件概率的定理。

##  The law of total probability

设 $A_1, A_2, ... , A_n$ 是一组互不相容的事件，它形成样本空间的一个分割（每个试验结果必定使得其中一个事件发生！）。又假定对每个 $i, P(A_i) > 0$ 。则对任何事件 $B$ ，下列公式成立
$$
\begin{eqnarray}
P(B) &=& P(A_1\cap B )+\cdots+P(A_n\cap B) \\ 
&=& P(A_1)P(B|A_1)+\cdots+P(B)P(B|A_n)
\end{eqnarray}
$$
这是**总概率定律（或翻译为：全概率定律），**下面有图示和证明。直观上，将样本空间分割成若干事件 $A_i$ 的并（ $A_1, \cdots, A_n$ 形成样本空间的一个分割）然后任意事件 $B$ 的概率等于事件 $B$ 在 $A_i$ 发生的情况下的条件概率的加权平均，而权重刚好等于这些事件 $A_i$ 的无条件概率。这条定理的一个主要应用是计算事件 $B$ 的概率。直接计算事件 $B$ 的概率有点难度，但是若条件概率 $P(B|A_i)$ 是已知的或是很容易推导计算时，总概率定律定理就成为了计算 $P(B)$ 的有力工具。应用这条定理的关键是找到合适的分割 $A_1,\cdots, A_n$ ，而合适的分割又与问题的实际背景有关。

![Figure_1.13_visualization_and_verification_of_the_total_probability_theorem.png](http://img.blog.csdn.net/20180301153607785?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveW91MTMxNDUyMG1l/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

由于事件 $A_1, A_2, \cdots, A_n$ 形成一个样本空间的一个分割，事件 $B$ 可以分解成不想交的 $n$ 个事件的并，即：

$$
B=(A_!\cap B)\cup\cdots\cup(A_n\cap B) \quad (1)
$$
利用可加定理，得到：

$$
P(B) = P(A_1 \cap B)+\cdots+P(A_n \cap B) \quad (2)
$$
利用条件概率的定义，得到：

$$
P(A_i\cap B) = P(A_i)P(B|A_i) \quad (3)
$$
将 $(3)$ 式子代入 $(2)$ 式子中得到：

$$
P(B)=P(A_1)P(B|A_1)+\cdots+P(A_n)P(B|A_n)
$$
也可以用等价的序列树形图来说明总概率定律（如上右边图）：叶子 $A_i \cap B$ 的概率等于由叶子到根部上的概率的乘积 $P(A_i)P(B|A_i)$ 。而事件 $B$ 由图上显示的3个叶子组成，将它们的概率相加就得到 $P(B)$ 。

### 总概率定律的例子

例 1.13 你参加一个棋类比赛，其中 $50\%$ 是一类棋手，你赢他们的概率为 $0.3\%$ ； $25\%$ 是二类棋手，你赢他们的概率是 $0.4$ ；剩下的是三类棋手，你赢得他们的概率是 $0.5$ 。从他们中间随机地选一位棋手与你比赛，你胜算的概率有多大？

记 $A_i$ 表示与你下棋的棋手的类别。依题意

$$
P(A_1)=0.5,\quad P(A_2) =0.25, \quad P(A_3) = 0.25
$$
记 $B$ 为你赢得比赛的事件，那么得到：

$$
P(B|A_1)=0.3,\quad P(B|A_2)=0.4,\quad P(B|A_3)=0.5
$$
那么利用总概率定律，你在不比赛中胜出的概率为：
$$
\begin{eqnarray}
P(B) &=& P(A_1)P(B|A_1)+P(A_2)P(B|A_2)+P(A_3)P(B|A_3) \\
&=& 0.5 \cdot 0.3+ 0.25 \cdot 0.4 + 0.25 \cdot 0.5 \\
&=& 0.375
\end{eqnarray}
$$

## Inference and Bayes' Rule 推断与贝叶斯定律

总概率定律经常与著名的贝叶斯定律联系起来，**贝叶斯定律将形如 $P(A|B)$ 的条件概率与形如 $P(B|A)$ 的条件概率联系起来**。

### Bayes' Rule贝叶斯定律

设 $A_1,A_2,\ldots,A_n$ 是一组互斥的事件，它形成样本空间的一个分割（每个试验结果必定使得其中一个事件发生）。又假定对每一个 $i, P(A_i)>0$ ，则对于任何事件 $B$ ，只要它满足 $P(B)>0$ ，下列公式成立：
$$
\begin{eqnarray}
P(A_i|B) &=& \frac{P(A_i)P(B|A_i)}{P(B)}\\
&=&\frac{P(A_i)P(B|A_i)}{P(A_1)P(B|A_1)+\cdots+P(A_n)P(B|A_n)}
\end{eqnarray}
$$
为证明贝叶斯定律，只需注意到 $P(A_i)P(B|A_i)$ 与 $P(B)P(A_i|B)$ 是相等的，它们都等于 $P(A_i \cap B)$ ，这样得到了第一个等式，至于第二个等式，只需对 $P(B)$ 利用总概率定律即可。

贝叶斯定律还可以用来进行**因果推理**。有许多”原因“可以造成某一”结果“。现在设我们观察到某一结果，希望推断造成这个结果出现的”原因“。现在设事件 $A_1,\ldots, A_n​$ 是原因，而 $B​$ 代表由原因引起的结果。 $P(B|A_i)​$ 表示在因果模型中由”原因“ $A_i​$ 造成结果 $B​$ 的概率（见下图）。当观察到结果 $B​$ 的时候，希望反推结果 $B​$ 是由原因 $A_i​$  造成的概率 $P(A_i|B)​$ 。 $P(A_i|B)​$ 为由于代表新近得到的信息 $B​$ 之后 $A_i​$ 出现的概率，称之为 **posterior probability 后验概率**，而原来的 $P(A_i)​$ 就称为 **prior probability 先验概率**。

### 贝叶斯定律进行推断的例子

#### 医学

在某病人X光片中发现一个阴影，（用 $B$ 表示，代表”结果“）。希望对造成这种结果的3个原因进行分析。这3个原因互斥，并且造成这个结果的原因一定是三者之一：原因1（事件 $A_1$）是恶性肿瘤，原因2（事件 $A_2$）是良性肿瘤，原因3（事件 $A_3$）是肿瘤外的其他原因。假定已经知道 $P(A_i)$ 和 $P(B|A_i), i=1,2,3$  。现在已经发现了阴影（事件 $B$ 发生），利用贝叶斯公式，这些原因的条件概率为：

$$
P(A_i|B)=\frac{P(A_i)P(B|A_i)}{P(A_1)P(B|A_1)+P(A_2)P(B|A_2)+P(A_3)P(B|A_3)},i=1,2,3
$$
在右图给出序列树形图，可用序列树形图给出条件概率计算的另外一种等价的解释。图中第一个深灰的叶子表示恶性肿瘤并出现阴影，其概率为 $P(A_1\cap B)$ ，且所有深灰的叶子表示片子中出现阴影，其概率为 $P(B)$ ，而由恶性肿瘤造成阴影的条件概率 $P(A_1|B)$ 是两个概率相除的结果。

#### 比赛

继续使用例 1.13 你参加一个棋类比赛，其中 $50\%$ 是一类棋手，你赢他们的概率为 $0.3\%$ ； $25\%$ 是二类棋手，你赢他们的概率是 $0.4$ ；剩下的是三类棋手，你赢得他们的概率是 $0.5$ 。现在假定你已经得胜，问你的对手为一类棋手的概率有多大？
用 $A_i$ 表示你与 $i$ 类棋手相遇的事件。由例中给出的条件知道：
$$
P(A_1)=0.5,\quad P(A_2)=0.25,\quad P(A_3)=0.25
$$
记 $B$ 表示你赢的比赛的事件，你胜出的概率为：
$$
P(B|A_1)=0.3,\quad P(B|A_2)=0.4,\quad P(B|A_3)=0.5
$$
利用贝叶斯公式得：
$$
\begin{eqnarray}
P(A_1|B) &=& \frac{P(A_1)P(B|A_1)}{P(A_1)P(B|A_1)+P(A_2)P(B|A_2)+P(A_3)P(B|A_3)} \\
&=& \frac{0.5\cdot 0.3}{0.5\cdot 0.3+0.25\cdot 0.4+0.25\cdot 0.5} \\
&=& 0.4
\end{eqnarray}
$$

#### 假阳性之谜

 设对于某种少见的疾病的检出率为 $0.95$ ；如果一个被检查的病人有某种疾病，其检查结果为阳性的概率为 $0.95$ ；如果该人没有这种疾病，其检查结果为阴性的概率是 $0.95$ 。现在假定某一人群中患有这种病的概率为  $0.001$ ，并从这个总体中随机地抽取一个人进行检测，检查结果为阳性。现在问这个人患有这种病的概率有多大？

设 $A$ 为这个人有这种疾病， $B$ 为经检验这个人为阳性。利用贝叶斯公式：
$$
\begin{eqnarray}
P(A|B) &=& \frac{P(A)P(B|A)}{P(A)P(B|A)+P(A^c)P(B|A^c)} \\
&=& \frac{0.001\cdot 0.95}{0.001\cdot 0.95 + 0.999\cdot 0.05} \\
&=& 0.0187
\end{eqnarray}
$$
尽管检验方法非常精确，一个经检测为阳性的人仍然不大可能真正患有这种疾病（患有该疾病的概率小于 $2\%$ ）。根据《经济学人》杂志 $1999$ 年 $2$ 月 $20$ 日的报道，在一家著名的大医院中 $80\%$ 的受访者不知道这类问题的正确答案，而大部分人回答，这个经检测为阳性的人患病概率为 $0.95$ !

## 连续随机变量的贝叶斯定律

在许多情况下，我们会遇到一个没有观察到的对象。用随机变量 $X$ 代表这种未观察到的量，设其概率密度函数是 $ f_X(x)$ 。我们能够观察到的量是经过噪声干扰的量 $Y$ ，$Y$ 的分布函数是条件分布函数，其条件概率密度函数为： $f_{X|Y}(y|x)$ 。当 $Y$ 的值被观察到以后，它包含 $X$ 的多少信息呢？这类问题与离散随机变量的推断问题类似。现在唯一的不同之处在于处理的是连续随机变量。

![Figure_3.20_schematic_description_of_the_inference_problem.png](http://img.blog.csdn.net/20180301153651988?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveW91MTMxNDUyMG1l/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

上图是推断问题的框图，有一个未观察到的变量 $X$ ，其概率密度函数 $f_X$ 是已知的，同时得到一个观察到的随机变量 $Y$ ，其条件概率密度函数为 $f_{Y|X}(y|x)$ 。给定 $Y$ 的观察值 $y$ ，推断问题变成条件概率密度函数 $f_{X|Y}(x|y)$ 的计算问题。

注意到：当观察到事件 $Y=y$ 以后，所有的信息都包含在条件概率密度函数 $f_{X|Y}(x|y)$ 中，现在只需计算这个条件概率密度函数。利用公式 $f_Xf_{Y|X}=f_{X,Y}=f_Yf_{X|Y}$ 可以得到：

$$
f_{X|Y}(x|y)=\frac{f_X(x)f_{Y|X}(y|x)}{f_Y(y)}
$$
这个即所求的公式，与之等价的公式：

$$
f_{X|Y}(x|y)=\frac{f_X(x)f_{Y|X}(y|x)}{\int_{-\infty}^{+\infty}f_X(t)f_{Y|X}(y|t)dt}
$$

### 例子

通用照明公司生产一种灯泡，已知其使用寿命 $Y$ 为指数随机变量，其概率密度函数为 $\lambda e^{-\lambda y}, y>0$ ，按过往经验，在任意给定的一天参数 $\lambda$ 实际上是一个随机变量，其概率密度函数为区间 $[1, \frac{3}{2}]$ 上的均匀分布。现在随机地取已知灯泡进行试验，得到灯泡的寿命数据。得到数据以后，对于 $\lambda$ 的分布有什么新的认识？

将 $\lambda$ 看成一个随机变量 $\Lambda$ ，作为对 $\lambda$ 的初始认识，那么根据题意 $\Lambda$ 的概率密度函数是：

$$
f_{\Lambda(\lambda)}=2, 1\le \lambda \le \frac{3}{2}
$$
当得到数据 $y$ 以后，关于 $\Lambda$ 的信息包含于条件概率密度函数 $f_{\Lambda, y}(\lambda|y)$ 中，利用连续贝叶斯公式得到：

$$
f_{ \Lambda|y}(\lambda|y)=\frac{f_\Lambda(\lambda)f_{Y|\Lambda}(y|\lambda)}{\int_{+\infty}^{-\infty}f_{\Lambda}(t)f_{Y|\Lambda}(y|t)dt}=\frac{2\lambda e^{-\lambda y}}{\int_{1}^{\frac{3}{2}}2te^{-ty}dt}，1\le \lambda \le \frac{3}{2}
$$

## 关于连续随机变量的推断

在许多实际问题中，未观察到的随机变量可能是连续的随机变量。例如，在通信问题中传输的信号是一个二进制的信号，经过传输以后，混入的噪声是正态随机变量，这样，观测到的随机变量就是连续的随机变量；或者在医疗诊断中，观察到的量也是连续的测量值，例如：体温或血液样本中的指标。这种情况下需要将贝叶斯公式作适当改变。

现在研究一种特殊情况，未观察到的是一个事件$A$ 。不知道 $A$ 是否发生了。事件 $A$ 的概率 $P(A)$ 是已知的。设 $Y$ 是一个连续的随机变量，并且假定条件概率密度函数 $f_{Y|A}(y)$ 和 $f_{Y|A^c}(y)$ 是已知的。令人兴趣的是事件 $A$  的条件概率密度函数 $P(A|Y=y)$ 。这个量代表得到的观察值 $y$ 以后关于事件 $A$ 的信息。

由于事件 ${Y=y}$ 是一个零概率事件，转而去考虑事件 ${y \le Y \le y+\delta}$ ，其中 $\delta$ 是一个很小的正数，然后令 $\delta$ 趋于0 。利用贝叶斯公式，令 $f_{Y}(y)>0$ ，我们得到：
$$
\begin{eqnarray}
P(A|Y=y) &\approx& P(A|y\le Y \le y+\delta) \\
&=& \frac{P(A)P(y\le Y \le y+\delta|A)}{P(y\le Y \le y+\delta)} \\
&\approx&\frac{P(A)f_{Y|A}(y)\delta}{f_Y(y)\delta} \\
&=& \frac{P(A)f_{Y|A}(y)}{f_Y(y)}
\end{eqnarray}
$$
利用总概率定律，可将上式的分母写成：
$$
f_{Y}(y)=P(A)f_{Y|A}(y)+P(A^c)f_{Y|A^c}(y)
$$
这样得到：
$$
P(A|Y=y)=\frac{P(A)f_{Y|A}(y)}{P(A)f_{Y|A}(y)+P(A^c)f_{Y|A^c}(y)}
$$
现在令事件 $A$ 具有形式 $\{N=n\}$ ，其中 $N$ 是一个离散的随机变量，代表未观察到的随机变量。记 $p_N$ 为 $N$ 的分布函数。令 $Y$  为连续随机变量，对任意 $N$ 的取值 $n$，$Y$  具有条件概率密度函数 $f_{Y|N}(y|n)$ 。 这样上面的公式变成 ：
$$
P(N=n|Y=y)=\frac{p_N(n)f_{Y|N}(y|n)}{f_Y(y)}
$$
利用下面的总概率定律：
$$
f_Y(y)=\sum\limits_{i}p_N(i)f_{Y|N}(y|i)
$$
得到：
$$
P(N=n|Y=y)=\frac{p_N(n)f_{Y|N}(y|n)}{\sum\limits_{i}p_N(i)f_{Y|N}(y|i)}
$$

### 例子-信号检测

设 $S$ 是一个只取2个值的信号（signal）。记  $P(S=1)=p$ 和 $P(S=-1)=1-p$ 。在接收端，得到的信号为 $Y=N+S$ ，其中 $N$ 是一个正态分布的噪声（noise），期望为0，方差为1，并且与 $S$ 相互独立。当观察到的信号为 $y$ 的时候，$S=1$ 的概率是多少？

对于给定的 $S=s=1, Y$ 是一个正态随机变量，期望为 $s=1$ ，方差为 $1$ 。应用刚才得到的公式：
$$
P(S=1|Y=y)=\frac{p_S(1)f_{Y|S}(y|1)}{f_Y(y)}=\frac{\frac{p}{\sqrt{2\pi}}e^{-\frac{(y-1)^2}{2}}}{\frac{p}{\sqrt{2\pi}}e^{-\frac{(y-1)^2}{2}}+\frac{1-p}{\sqrt{2\pi}}e^{-\frac{(y+1)^2}{2}}}
$$
将上式化简得：
$$
P(S=1|Y=y)=\frac{pe^y}{pe^y+(1-p)e^{-y}}
$$
注意：当 $y\rightarrow -\infty, P(S=1|Y=y)\rightarrow 0$ ，当 $y\rightarrow \infty, P(S=1|Y=y)\rightarrow 1$ 。 $y$ 在实数轴上变化时， $P(S=1|Y=y)$ 是 $y$ 的严格上升函数，这符合直观的理解。

### 基于离散观察值的推断

在前文连续随机变量的贝叶斯定律中得到的：
$$
\begin{eqnarray}
P(A|Y=y) &\approx& P(A|y\le Y \le y+\delta) \\
&=& \frac{P(A)P(y\le Y \le y+\delta|A)}{P(y\le Y \le y+\delta)} \\
&\approx&\frac{P(A)f_{Y|A}(y)\delta}{f_Y(y)\delta} \\
&=& \frac{P(A)f_{Y|A}(y)}{f_Y(y)}
\end{eqnarray}
$$
反解得到：
$$
f_{Y|A}(y)=\frac{f_Y(y)P(A|Y=y)}{P(A)}
$$
根据归一性（$\int_{-\infty}^{+\infty}f_{Y|A}(y)dy=1$），那么得到一个等价的表达式：
$$
f_{Y|A}(y)=\frac{f_Y(y)P(A|Y=y)}{\int_{-\infty}^{+\infty}f_Y(t)P(A|Y=t)dt}
$$
这个公式可以用于当事件 $A$  被观测到时候，对随机变量 $Y$ 进行推断。对于事件 $A$ 是 $\{N=n\}$ 的形式，根据前文：
$$
P(N=n|Y=y)=\frac{p_N(n)f_{Y|N}(y|n)}{\sum\limits_{i}p_N(i)f_{Y|N}(y|i)}
$$
得到一个相似的公式对随机变量 $Y$ 进行推断：
$$
f_{Y|N}(y|n)=\frac{P(N=n|Y=y)\sum\limits_{i}p_N(i)f_{Y|N}(y|i)}{p_N(n)}
$$

## 总结

令 $Y$ 为连续随机变量。

1.  若 $X$ 为连续随机变量，则有：
    $$
    f_{X|Y}(x|y)f_Y(y)=f_X(x)f_{Y|X}(y|x)
    $$
    和
    $$
    f_{X|Y}(x|y)=\frac{f_X(x)f_{Y|X}(y|x)}{f_Y(y)}=\frac{f_X(x)f_{Y|X}(y|x)}{\int_{-\infty}^{+\infty}f_X(t)f_{Y|X}(y|t)dt}
    $$

2.  若 $N$ 为离散随机变量，则有：
    $$
    f_Y(y)P(N=n|Y=y)=p_N(n)f_{Y|N}(y|n)
    $$
    得到贝叶斯定律为：
    $$
    P(N=n|Y=y)=\frac{p_N(n)f_{Y|N}(y|n)}{f_Y(y)}=\frac{p_N(n)f_{Y|N}(y|n)}{\sum\limits_{i}p_N(i)f_{Y|N}(y|i)}
    $$
    和
    $$
    f_{Y|N}(y|n)=\frac{f_Y(y)P(N=n|Y=y)}{p_N(n)}=\frac{f_Y(y)P(N=n|Y=y)}{\int_{-\infty}^{+\infty}f_Y(t)P(N=n|Y=t)dt}
    $$

3.  对于事件 $A$ ，关于 $P(A|Y=y)$ 和 $f_{Y|A}(y)$ 具有类似的贝叶斯定律。