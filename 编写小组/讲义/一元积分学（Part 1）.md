---
Todo: 整合他人素材，完成这个讲义。
Requires: 先写点自己的理解和做题的感悟，有人提交时就整合，并审稿，特别是例题，需要自己做
aliases:
  - Integrate
---
# Section 1  积分基础
（%%TODO：积分基础%%）
（%%积分的定义！%%）
# Section 2  积分方法
## 预处理
拿到一个积分，最忌讳的是直接被那一团复杂的被积函数吓倒。先尝试着逐步拆解简化这个积分，然后进行求解。
常见的预处理方式：
1. （对定积分：）靠奇函数来消项；通过拆分上下限来简化可能性(?)
2. （对有理式：）有理式的拆解
## 换元积分法
#### 常见特征：被积函数有三角函数、 $x^2\pm a^2$ 等元素
使用换元积分法非常考验你对被积函数的敏感程度，也就是“题感”，方法本身是特别容易理解的，因此我们必须熟练记忆一些初等函数求导公式以及额外补充的一些推出来的求导公式。
>[!example] 开胃菜
>求不定积分 $\int\cos^2x\sin x\mathrm dx$.
>>解：令 $u=\cos x$；两边求微：$\mathrm du=-\sin x\mathrm dx$，
>>$\int\cos^2x\sin x\mathrm dx=-\int u^2\mathrm du=-\dfrac{u^3}{3}+C=-\dfrac{\cos^3 x}{3}+C$
>>如果你对整个过程很熟练，可以写成 $\int\cos^2x\sin x\mathrm dx=\int\cos^2x\mathrm d(\cos x)=-\dfrac{\cos^3 x}{3}+C$

换元法有下列几种情况：
#### 1. 三角形式
>[!example] 例2.1
>求不定积分 $\int \sin^2 x \cos^5 x dx$.

>[!tip] 提示
>利用 $\cos x$ 来凑微分而不是 $\sin x$，这样你就能得到偶数次方的三角函数——如果最后剩下奇数次方的 $\sin x,\cos x$，那么可能还要多花一点心思去做换元或用别的技巧，但是偶数次方的可操作性强很多，你可以用 $\sin^2x+\cos^2x=1$ 来升降次，用诸如 $\cos^2x=\dfrac{1+\cos^2x}{2}$ 来换角，比奇数次更加便捷。
>这也是万能代换 $x=\tan\frac{t}{2}$ 背后的逻辑。 

>[!note] 解析
>$\begin{align}\text{原式}&= \int \sin^2 x \cos^4 x (\cos x) dx \\&= \int \sin^2 x \cos^4 x d\sin x \\&= \int \sin^2 x (1-\sin^2 x)^2 d\sin x \\&= \int \sin^2 x (\sin^4 x - 2\sin^2 x + 1) d\sin x \\&= \int (\sin^6 x - 2\sin^4 x + \sin^2 x) d\sin x \\&= \frac{1}{7}\sin^7 x - \frac{2}{5}\sin^5 x + \frac{1}{3}\sin^3 x + C\end{align}$
#### 2. 高次幂
>[!example] 例2.2
>求不定积分 $\int\dfrac{x\mathrm dx}{(x-1)^{100}}$.

>[!note] 解析
>$\begin{align}\text{原式}&=\int\frac{(x-1)+1}{(x-1)^{100}}\mathrm d(x-1)\\&=\int\frac{\mathrm d(x-1)}{(x-1)^{99}}+\int\frac{\mathrm d(x-1)}{(x-1)^{100}}\\&=-\frac{1}{98(x-1)^{98}} - \frac{1}{99(x-1)^{99}} + C\end{align}$

>[!error] 待决策
>### 3. 高次幂多项式与三角函数的转化
>$$\int \frac{\sqrt{\arctan x}}{1+x^2} dx$$
>原式
>$$\begin{align*}
&= \int \sqrt{\arctan x} d(\arctan x) \\
&= \frac{2}{3}(\arctan x)^{\frac{3}{2}} + C
\end{align*}$$
##  分部积分法


#### 常见特征：

#### 反对幂指三

# Section 3  特殊积分
### 1. 依靠循环式求解的积分
### 2. 依靠递推式求解的积分
# Section 4  变限积分

# Section 5  与积分相关的不等式证明
# Extra. 常用积分公式速记
