---
Todo: 整合他人素材，完成这个讲义。
Requires: 先写点自己的理解和做题的感悟，有人提交时就整合，并审稿，特别是例题，需要自己做
aliases:
  - Integrate
---
%%用两个百分号扩在一起的是MarkDown注释，保存时不会展现。如无必要，无需删去。
也可以用这种方法标注内容%%
# Section 1  积分基础
>[!bug] 待补充
# Section 2  积分方法
## 预处理
拿到一个积分，最忌讳的是直接被那一团复杂的被积函数吓倒。先尝试着逐步拆解简化这个积分，然后进行求解。
常见的预处理方式：
1. 对定积分：在积分上下限互为相反数时靠奇函数来消项；通过拆分上下限来简化可能性
2. 对有理式：有理式的拆解
对有理式的拆解，集中在对分式 $\displaystyle\frac{M(x)}{N(x)} = \frac{a_0x^n+a_1x^{n-1}+\dots+a_{n-1}x+a_n}{b_0x^m+b_1x^{m-1}+\dots+b_{m-1}x+b_m}$ 的拆解中。
##### 第一步：拆成一个整式+真分式
$\displaystyle\frac{M(x)}{N(x)}=S(x)+\frac{P(x)}{Q(x)}$，其中 $S(x)$ 为整式，$\displaystyle\frac{P(x)}{Q(x)}$ 为真分式
整式可以直接分离，单独求积分；
对于真分式 $\displaystyle\frac{P(x)}{Q(x)} = \frac{a_0x^p+a_1x^{p-1}+\dots+a_{p-1}x+a_p}{b_0x^q+b_1x^{q-1}+\dots+b_{q-1}x+b_q},\quad p<q$
将分母进行因式分解 $Q(x)=b_0(x-a)^\alpha\cdots(x-b)^\beta(x^2+px+q)^\lambda\cdots(x^2+rx+s)^\mu$
通常这种一般的因式分解都会比较容易，出题人不会太难为人。
分母若出现 $(x^2+px+q)^\lambda$ 这种不可约二次式的幂的形式，需要该二次式的判别式 $\Delta = p^2 - 4q < 0$（即在实数范围内不可约）。如果 $\Delta \geq 0$，则它应当继续分解为一次式的乘积 $(x-a)(x-b)$ 或 $(x-a)^2$ ，而不会保留为这种二次形式。

这样，我们就能把 $\frac{P(x)}{Q(x)}$ 写成： $$\begin{align*}
\frac{P(x)}{Q(x)} &= \frac{A_1}{x-a} + \frac{A_2}{(x-a)^2} + \dots + \frac{A_\alpha}{(x-a)^\alpha} + \dots + \frac{B_1}{x-b} + \frac{B_2}{(x-b)^2} + \dots + \frac{B_\beta}{(x-b)^\beta} \\
&\quad + \frac{M_1x+N_1}{x^2+px+q} + \frac{M_2x+N_2}{(x^2+px+q)^2} + \dots + \frac{M_\lambda x+N_\lambda}{(x^2+px+q)^\lambda} \\
&\quad + \dots + \frac{R_1x+S_1}{x^2+rx+s} + \frac{R_2x+S_2}{(x^2+rx+s)^2} + \dots + \frac{R_\mu x+S_\mu}{(x^2+rx+s)^\mu}
\end{align*}$$
>[!warning] 注意！
>1. 若有 $\alpha$ 个重根，即某一因式为 $\alpha$ 次方，那么这个项就拆成分母从1次方加到 $\alpha$ 次方。
>2. 对于分母为 $\Delta>0$ 的二次函数，那么其分子就是一次函数，并且依旧要符合规则1。

接下来就能用待定系数法求出那些待定的系数 $A,B,M,N$ 等等。一般来说，这个过程不会太复杂，大可不必拿出考完的线代。

>[!summary] 任务
>尝试用待定系数法推出 $\displaystyle\frac{1}{(1+2x)(1+x^2)} = \frac{1}{5}\left[\frac{4}{1+2x} - \frac{2x}{1+x^2} + \frac{1}{1+x^2}\right]$

当然，并不是所有时候都要用待定系数法，如果你的注意力惊人。
也不是一定要给它拆成这种细碎的样子，因题目而异。如果不拆分有更快的做法，那就没必要拆。
3. 对根式：欧拉代换（可选）
>[!danger] 警告
>欧拉代换法是你最后的防线，而非你的第一个想法。
>当普通的代换能解决问题，如 $\sqrt{x^2+2x+2}=\sqrt{(x+1)^2+1}$，那么最好不用欧拉代换法。
>如果实在想不出来怎么做，可以用欧拉替代法硬算，将其作为最后的手段。

对于不定积分 $\int R\left(x,\sqrt{ax^2+bx+c}\right)dx \quad (a\neq0)$，可以从如下角度作代换：
- 欧拉第一代换：如果 $a>0$，令 $\sqrt{ax^2+bx+c}=t-\sqrt{a}x$，或令 $\sqrt{ax^2+bx+c}=\sqrt{a}x+t$。
- 欧拉第二代换：如果 $c>0$，令 $\sqrt{ax^2+bx+c}=tx-\sqrt{c}$，或令 $\sqrt{ax^2+bx+c}=tx+\sqrt{c}$。
- 欧拉第三代换：如果 $ax^2+bx+c=a(x-\alpha)(x-\beta)$，则可以令 $\sqrt{ax^2+bx+c}=t(x-\alpha)$
对于任意一种换元，换元后等式两边平方，此时 x^2 这一项将会被抵消，因此用含 t 的多项式将 x 表示出来。
>[!todo] 示例
>求不定积分$\displaystyle\int \frac{dx}{(x^2+a^2)\sqrt{a^2-x^2}}$
>解：令 $\sqrt{a^2-x^2}=t(a-x)$，则
>$\displaystyle t^2=\frac{a+x}{a-x},\quad x=a\frac{t^2-1}{t^2+1},\quad dx=\frac{4at}{(t^2+1)^2}dt$
>$\displaystyle x^2+a^2=\frac{2a^2(t^4+1)}{(t^2+1)^2}$
>于是
>$\begin{align}\int \frac{dx}{(x^2+a^2)\sqrt{a^2-x^2}} &= \int \frac{\frac{4at}{(t^2+1)^2}dt}{\frac{2a^2(t^4+1)}{(t^2+1)^2}\cdot\frac{2at}{t^2+1}} \\&= \frac{1}{2a^2}\int \frac{2t^2+2}{t^4+1}dt\end{align}$
>之后可以按照有理式的方法继续积分下去

>待填入：[高等数学：欧拉替换法在求解不定积分时的应用 - 知乎](https://zhuanlan.zhihu.com/p/348304254)

>[!Bug] 待补充
>而且，我们还得穿插定积分内容
## 换元积分法
常见特征：被积函数有三角函数、 $x^2\pm a^2$ 等元素
使用换元积分法非常考验你对被积函数的敏感程度，也就是“题感”，方法本身是特别容易理解的，因此我们必须熟练记忆一些初等函数求导公式以及额外补充的一些推出来的求导公式。
>[!todo] 开胃菜
>求不定积分 $\int\cos^2x\sin x\mathrm dx$.
>>解：令 $u=\cos x$；两边求微：$\mathrm du=-\sin x\mathrm dx$，
>>$\int\cos^2x\sin x\mathrm dx=-\int u^2\mathrm du=-\dfrac{u^3}{3}+C=-\dfrac{\cos^3 x}{3}+C$
>>如果你对整个过程很熟练，可以写成 $\int\cos^2x\sin x\mathrm dx=\int\cos^2x\mathrm d(\cos x)=-\dfrac{\cos^3 x}{3}+C$

除此之外还有第二类换元法
>[!bug] TODO: 待补充

换元法有下列几种情况：
#### 1. 三角函数式
>[!example] 例2.1
>求不定积分 $\int \sin^2 x \cos^5 x\mathrm dx$.

>[!tip] 提示
>利用 $\cos x$ 来凑微分而不是 $\sin x$，这样你就能得到偶数次方的三角函数——如果最后剩下奇数次方的 $\sin x,\cos x$，那么可能还要多花一点心思去做换元或用别的技巧，但是偶数次方的可操作性强很多，你可以用 $\sin^2x+\cos^2x=1$ 来升降次，用诸如 $\cos^2x=\dfrac{1+\cos^2x}{2}$ 来换角，比奇数次更加便捷。
>“化偶数次”也是万能代换 $x=\tan\frac{t}{2}$ 背后的逻辑。

>[!note] 解析
>$\begin{align}\text{原式}&= \int \sin^2 x \cos^4 x (\cos x)\mathrm dx \\&= \int \sin^2 x \cos^4 x\mathrm d\sin x \\&= \int \sin^2 x (1-\sin^2 x)^2\mathrm d\sin x \\&= \int \sin^2 x (\sin^4 x - 2\sin^2 x + 1)\mathrm d\sin x \\&= \int (\sin^6 x - 2\sin^4 x + \sin^2 x) \mathrm d\sin x \\&= \frac{1}{7}\sin^7 x - \frac{2}{5}\sin^5 x + \frac{1}{3}\sin^3 x + C\end{align}$
#### 2. 三角代换式
三角代换并不是绝对的，需要根据被积函数的情况来定。然而，当出现类似 $x^2\pm a^2$ 的结构，尤其是在根号内的时候，可以根据 $\sin^2x+\cos^2x=1$ 和 $\tan^2x+1=\sec^2x$ 适当选择代换式
一般规律如下：当被积函数中含有
${\sqrt{a^2 - x^2}}$ 可令 $x = a\sin t$
${\sqrt{a^2 + x^2}}$ 可令 $x = a\tan t$
${\sqrt{x^2 - a^2}}$ 可令 $x = a\sec t$

>[!fail] 不应当死记硬背上面的代换，这样很容易记错

>[!done] 你可以结合 $\sin^2x+\cos^2x=1$ 和 $\tan^2x+1=\sec^2x$ 来辅助记忆，并强化运用能力

>[!example] 例题2.2
>求不定积分 $\displaystyle\int\frac{\mathrm dx}{\sqrt{x^2+a^2}} \quad (a>0)$

>[!note] 解析
>令 $x = a\tan t$ ，则$\mathrm dx = a\sec^2 t\mathrm dt$，$t \in \left(-\frac{\pi}{2},\frac{\pi}{2}\right)$，则
$\sqrt{x^2+a^2} = \sqrt{a^2\tan^2 t + a^2} = a\sec t$
>$\begin{align}\int \frac{dx}{\sqrt{x^2+a^2}} &= \int \frac{a\sec^2 t dt}{a\sec t} \\&= \int \sec t dt \\&= \ln|\sec t + \tan t| + C_1 \\&= \ln\left|\frac{\sqrt{x^2+a^2}}{a} + \frac{x}{a}\right| + C_1 \\&= \ln\left|x + \sqrt{x^2+a^2}\right| + C\end{align}$
#### 3. 有理式
>[!example] 例2.3
>求不定积分 $\displaystyle\int\dfrac{x\mathrm dx}{(x-1)^{100}}$.

>[!note] 解析
>$\begin{align}\text{原式}&=\int\frac{(x-1)+1}{(x-1)^{100}}\mathrm d(x-1)\\&=\int\frac{\mathrm d(x-1)}{(x-1)^{99}}+\int\frac{\mathrm d(x-1)}{(x-1)^{100}}\\&=-\frac{1}{98(x-1)^{98}} - \frac{1}{99(x-1)^{99}} + C\end{align}$

>[!example] 例2.4
>设 $\displaystyle a_n=\int_0^1x(1-x)^n\text dx,n=1,2,\cdots$.
>（1）求级数 $\displaystyle\sum_{n=1}^\infty a_n$；
>（2）设常数 $\lambda\gt0$，试讨论级数 $\displaystyle\sum_{n=1}^\infty \lambda^na_n$ 的敛散性.

>[!note] 解析
>（1）**解1：**$$\begin{aligned}
>a_n&=-\int_0^1x(1-x)^n\text d(1-x)\\
>&=-\frac{1}{n+1}\int_0^1x\text d(1-x)^{n+1}\\
>&=-\frac{1}{n+1}\left([x(1-x)^{n+1}]_0^1-\int_0^1(1-x)^{n+1}\text dx\right)\\
>&=-\frac{1}{n+1}\int_0^1(1-x)^{n+1}\text d(1-x)\\
>&=-\frac{1}{n+1}\left[\frac{(1-x)^{n+2}}{n+2}\right]_0^1\\
>&=\frac{1}{(n+1)(n+2)}\\
>&=\frac{1}{n+1}-\frac{1}{n+2}.
>\end{aligned}$$
>于是$$\sum_{k=1}^n a_k = \sum_{k=1}^n \left( \frac{1}{k+1} - \frac{1}{k+2} \right) = \frac{1}{2} - \frac{1}{n+2}.$$
>因此$$\sum_{n=1}^\infty a_n = \lim_{n \to \infty} \left( \frac{1}{2} - \frac{1}{n+2} \right) = \frac{1}{2}.$$
>**解2：** 令 $t=1-x$，则
>$$\begin{aligned}
a_n &= \int_0^1 x (1-x)^n \, dx = \int_0^1 (1-t) t^n \, dt \\
&= \int_0^1 (t^n - t^{n+1}) \, dt = \left[ \frac{t^{n+1}}{n+1} - \frac{t^{n+2}}{n+2} \right]_0^1 \\
&= \frac{1}{n+1} - \frac{1}{n+2}.
>\end{aligned}$$
>后同解1
>（2）设 $\displaystyle b_n = \lambda^n a_n = \lambda^n \left( \frac{1}{n+1} - \frac{1}{n+2} \right)$。考虑比值判别法：$$\lim_{n \to \infty} \frac{b_{n+1}}{b_n} = \lim_{n \to \infty} \frac{\lambda^{n+1} \left( \frac{1}{n+2} - \frac{1}{n+3} \right)}{\lambda^n \left( \frac{1}{n+1} - \frac{1}{n+2} \right)} = \lambda \lim_{n \to \infty} \frac{ \frac{1}{(n+2)(n+3)} }{ \frac{1}{(n+1)(n+2)} } = \lambda \lim_{n \to \infty} \frac{n+1}{n+3} = \lambda.$$
>故当 $0 < \lambda < 1$ 时，级数收敛；当 $\lambda > 1$ 时，级数发散。
当 $\lambda = 1$ 时，$\displaystyle b_n = \frac{1}{n+1} - \frac{1}{n+2}$，由 (1) 知级数收敛。
综上，当 $0 < \lambda \le 1$ 时，级数 $\displaystyle \sum_{n=1}^\infty \lambda^n a_n$ 收敛；当 $\lambda > 1$ 时，级数发散.

>[!summary] 题后总结
>以上两题很像，就放在一起总结了。
>2.4第一问解1是利用凑微分法和分部积分法，比较常规，也相对容易想到；解2利用第二类换元法，2.3在微分中凑出一个较为复杂的表达式，可以理解为令 $t=x-1$ 的换元，都大大简化了计算。
>为什么用这种换元可以简化计算呢？观察一下特征：一个相对复杂的式子上有一个 $n$ 次方，变得更加复杂，而简单的式子 $x$ 是一次的，更加简单。为了<span style='color: #ff7700; font-weight: bold'>“调和”</span>两个式子的复杂度，我们把复杂式子代换掉，这样就能更加方便地进行积分了。

>[!example] 例2.
>求不定积分 $\displaystyle\int \frac{\mathrm{d}x}{\sqrt[6]{x+1} - \sqrt[3]{x+1}}$

>[!hint] 提示
>对于含有多个次数不同的根式时，换元时要换元为根指数的最小公倍数。
>若被积函数中含有 $\sqrt[n_1]{ax+b}$,$\sqrt[n_2]{ax+b}$,$\dots$,$\sqrt[n_k]{ax+b}$，可考虑代换 $t = \sqrt[n]{ax+b}$（$n$ 为 $n_1$,$n_2$,$\dots,n_k$ 的最小公倍数）
>若被积函数中含有 $\sqrt[n_1]{\frac{ax+b}{cx+d}}$,$\sqrt[n_2]{\frac{ax+b}{cx+d}}$,$\dots$,$\sqrt[n_k]{\frac{ax+b}{cx+d}}$，可考虑代换 $t = \sqrt[n]{\frac{ax+b}{cx+d}}$（$n$ 为 $n_1$,$n_2$,$\dots$,$n_k$ 的最小公倍数）

>[!note] 解析
>令 $t=\sqrt[6]{x+1}$，则 $x=t^6-1$，$\mathrm dx=6t^5\mathrm dt$，则 
>$\begin{align}\int \frac{dx}{\sqrt[6]{x+1} - \sqrt[3]{x+1}} &= \int \frac{6t^5 dt}{t - t^2} \\&= 6\int \frac{t^4}{1-t} dt \\&= 6\int \left(-t^3 - t^2 - t - 1 + \frac{1}{1-t}\right) dt \\&= 6\left(-\frac{t^4}{4} - \frac{t^3}{3} - \frac{t^2}{2} - t - \ln|1-t|\right) + C \\&= -\frac{3}{2}\sqrt[3]{(x+1)^2} - 2\sqrt{x+1} - 3\sqrt[3]{x+1} - 6\sqrt[6]{x+1} -\\ 6\ln|\sqrt[6]{x+1} -1| + C\end{align}$

>[!error] 待决策
>##### 高次幂多项式与三角函数的转化
>$$\int \frac{\sqrt{\arctan x}}{1+x^2}\mathrm dx$$
>原式
>$$\begin{align*}
&= \int \sqrt{\arctan x}\mathrm d(\arctan x) \\
&= \frac{2}{3}(\arctan x)^{\frac{3}{2}} + C
\end{align*}$$
#### 4. 倒代换
在拆解有理式的时候，对于 $\dfrac{1}{ax+b},\dfrac{1}{ax^2+bx+c}$ 等一次、二次分式，我们可以从容应对；但是如果次数再高一点，就很难办了。
然而，对于一些较为简单的高次幂函数，我们可以使用**倒代换**：把 $x$ 倒过来！
令 $\displaystyle x=\frac1t,\mathrm dx=-\frac{1}{t^2}\mathrm dt.$

>[!example] 例题
>求不定积分 $\displaystyle\int\frac{1}{x(x^7+2)}\mathrm dx$

>[!note] 解析
>令 $x=\frac{1}{t}$，
>$\begin{align}\int\frac{1}{x(x^7+2)}\mathrm dx&=\int\frac{t\mathrm dt}{(t^{-7}+2)(-t^2)}\\&=-\int\frac{t^6\mathrm dt}{1+2t^7}\\&=-\frac{1}{14}\ln|1+2t^7|+C\\&=-\frac{1}{14}\ln|2+x^7|+\frac{1}{2}\ln|x|+C\end{align}$
##  分部积分法
分部积分法的基本公式：$\int u\mathrm dv=uv-\int v\mathrm du$
分部积分法的要点是通过合理选择 $u,\mathrm dv$ 使得 $\int v\mathrm du$ 比 $\int u\mathrm dv$ 更容易求。那么如何选择呢？按照教员上课提到的“<span style="color:#ff7700;font-weight:bold;">反对幂指三</span>”，我们这样选择 $u$，十有八九能成功（实在不行再调换顺序）：
1. **反**：反三角函数家族 $\arcsin,\arccos,\arctan,...$ 
2. **对**：对数函数，通常特指 $\ln x$ 
3. **幂**：幂函数，$x,x^2,x^3,...$ 
4. **指**：指数函数，通常特指 $\mathrm e^x$ 
5. **三**：三角函数家族 $\sin,\cos,\tan,\cot,\sec,\csc$ 
>[!todo] 示例
>求不定积分 $\int x\cos x\mathrm dx$

%%像这种示例，就不用挖掉解答了：
建议以后不挖去解答的用“示例”标签，可以用info或者todo样式%%
>[!done] 正确示例
>解：按照顺序，匹配到“**幂**”，那么我们取 $u=x$，$\mathrm dv=\cos x\mathrm dx=\mathrm d\sin x$
>$\int x \cos x\mathrm dx = \int x\mathrm d\sin x = x \sin x - \int \sin x\mathrm dx = x \sin x + \cos x + C$

>[!fail] 错误示例
>解：我们尝试取 $u=\cos x$，$\mathrm dv=x\mathrm dx=\frac{1}{2}\mathrm dx^2$，
>$\displaystyle\int x\cos x\mathrm dx=\frac{1}{2}\int\cos x\mathrm dx^2=x^2\cos x+\int x^2\sin x\mathrm dx$    ……
>你还愿意继续积下去吗？我是不愿意了。
### 常见情况：
#### 1. 幂对乘积或幂反乘积或幂指乘积
>[!example] 例题
>求不定积分 $\int x^3 \ln x\mathrm dx$

>[!note] 解析
>最先匹配的是“**对**”（对数函数 $\ln x$），取 $u=\ln x,\mathrm dv=x^3\mathrm dx$，则：
>$\begin{align}\int x^3 \ln x\mathrm dx&= \int \ln x d\left(\frac{x^4}{4}\right) \\&= \frac{1}{4}x^4 \ln x - \frac{1}{4}\int x^3\mathrm dx \\&= \frac{1}{4}x^4 \ln x - \frac{1}{16}x^4 + C\end{align}$

>[!example] 例题
>求不定积分 $\int\mathrm e^{\sqrt{x}}\mathrm dx$

>[!note] 解析
>我们可以提前代换变量，将根式消去。
>令 $t=\sqrt{x}$，则 $t^2=x,\ 2t\mathrm dt=\mathrm dx$，这样就能将根式化为整式。
>$\displaystyle\int\mathrm e^\sqrt{x}\mathrm dx=2\int t\mathrm e^t\mathrm dt$
>取 $u=x$：
>$\begin{align}\text{原式}&=2\int t\mathrm d\mathrm e^t\\&=2t\mathrm e^t-2\int\mathrm e^t\mathrm dt\\&=2t\mathrm e^t-2\mathrm e^t+C\\&=2\mathrm e^\sqrt x(\sqrt x-1)+C\end{align}$

>[!bug] TODO: 待补充 种类

然而，不少积分不能直接积出来。对于部分情况，需要用到**循环式**和**递推式**求解。
#### 2. 依靠循环式求解的积分
**循环式**是指在进行分部积分的时候，多次循环会出现**同一积分式**：
>[!todo] 示例
>求不定积分 $\int\mathrm e^x \sin x\mathrm dx$
>
>>解：
>>$\begin{align}\int\mathrm e^x \sin x\mathrm dx &= \int \sin x\mathrm d\mathrm e^x \\&=\mathrm e^x \sin x - \int\mathrm e^x\mathrm d(\sin x) \\&=\mathrm e^x \sin x - \int\mathrm e^x \cos x\mathrm dx \\&=\mathrm e^x \sin x - \int \cos x\mathrm d\mathrm e^x \\&=\mathrm e^x \sin x - \left(\mathrm e^x \cos x - \int\mathrm e^x\mathrm d(\cos x)\right) \\&=\mathrm e^x \sin x -\mathrm e^x \cos x - \int\mathrm e^x \sin x\mathrm dx\end{align}$
>
>可以看到，经过两次分部积分之后，$\int\mathrm e^x \sin x\mathrm dx$ 又一次出现了。
>果断将它移到等式左边，直接同时除以 $2$：
>$\int\mathrm e^x \sin x\mathrm dx=\mathrm e^x \sin x -\mathrm e^x \cos x - \int\mathrm e^x \sin x\mathrm dx\Rightarrow2\int\mathrm e^x \sin x\mathrm dx=\mathrm e^x \sin x -\mathrm e^x \cos x$
>因此 $\displaystyle\int\mathrm e^x \sin x\mathrm dx=\frac{\mathrm e^x \sin x -\mathrm e^x \cos x}{2}$

>[!bug] TODO:等待补充难题

%%参考：[Math is Fun - Integration by Parts](https://www.mathsisfun.com/calculus/integration-by-parts.html)
仅供娱乐，切勿当真%%

#### 3. 依靠递推式求解的积分
与循环式类似，递推式会在使用分部积分时出现和原式类似，但是比原式“**低一级**”的积分式。这种结构一般在积分式含有正整数 $n$ 的时候出现（e.g. $(x^2+a^2)^n$ ）例如：
>[!todo] 示例
>求不定积分 $\displaystyle I_n = \int \frac{\mathrm dx}{(x^2 + a^2)^n} \quad (a>0)$
>我们尝试一次分部积分：
>$$\begin{align*}I_{n-1} &= \int \frac{dx}{(x^2 + a^2)^{n-1}} = \frac{x}{(x^2 + a^2)^{n-1}} + 2(n-1)\int \frac{x^2}{(x^2 + a^2)^n} dx \\&= \frac{x}{(x^2 + a^2)^{n-1}} + 2(n-1)\int \frac{(x^2 + a^2) - a^2}{(x^2 + a^2)^n} dx \\&= \frac{x}{(x^2 + a^2)^{n-1}} + 2(n-1)(I_{n-1} - a^2 I_n)\end{align*}$$
>这样积了一遍之后，我们就会发现：这一次积分，我们打通了 $I_n$ 与 $I_{n-1}$ 的桥梁。
>这样，我们尝试用 $I_{n-1}$ 来表示 $I_n$：
>$$I_n = \frac{1}{2a^2(n-1)} \left[ \frac{x}{(x^2 + a^2)^{n-1}} + (2n-3)I_{n-1} \right]$$
>那么 $I_1$ 呢？
>$$\displaystyle I_1=\int\frac{dx}{x^2 + a^2}$$
>取 $x=a\tan t$：
>$$I_1=\int\frac{a\sec^2 t\mathrm dt}{a^2\sec^2 t}=\frac ta+C=\frac1a\arctan\frac xa+C$$
>TO BE CONTINUED

>[!bug] 这道题求通项似乎是一件很困难的事。

#### 4. 连续分部积分（选学？）
>[!bug] 需要斟酌该内容是否重要。

分部积分法的推广公式就是重复使用分部积分法法则。
假设函数 $u,v$ 有 $n+1$ 阶连续导数，则：$\int u v^{(n+1)}\mathrm dx = \int u\mathrm d v^{(n)} = u v^{(n)} - \int v^{(n)}\mathrm du = u v^{(n)} - \int u' v^{(n)}\mathrm dx$
我们还可以继续把 $\int u' v^{(n)}\mathrm dx$ 撕开：$\int u v^{(n+1)} dx = u v^{(n)} - u' v^{(n-1)} + u'' v^{(n-2)} - \dots + (-1)^n u^{(n)} v + (-1)^{n+1} \int u^{(n+1)} v dx$
如果被积函数的因式之一是多项式，且次数较高的时候，这个公式特别方便。通常来说，取 $u$ 为该多项式，然后逐步求 $v^{(n)},v^{(n-1)},\cdots,v$，再依次乘到一起（注意正负号！）
>[!todo] 示例
>$\int (2x^3 + 3x^2 + 4x + 5)\mathrm e^x\mathrm dx$
>我们可以令 $u=2x^3 + 3x^2 + 4x + 5$，$v=\mathrm e^x$
>$u' = 6x^2 + 6x + 4,\quad u'' = 12x + 6,\quad u''' = 12$
>于是$\begin{align*}\int (2x^3 + 3x^2 + 4x + 5) e^x dx &= (2x^3 + 3x^2 + 4x + 5)e^x - (6x^2 + 6x + 4)e^x + (12x + 6)e^x - 12e^x + C \\&= (2x^3 - 3x^2 + 10x - 5)e^x + C\end{align*}$

>[!example] 例题
>求不定积分 $\int \cos x (x^3 + 2x^2 + 3x + 4) dx$

>[!note] 解析
>解：TO BE CONTINUED
# Section 4  变限积分

# Section 5  与积分相关的不等式证明
## Extra. 常用积分公式速记
### 一、基本初等函数积分
 $\displaystyle\int 0 \, dx =C$
 $\displaystyle\int k \, dx = kx + C$ （ k  为常数）
 $\displaystyle\int x^\mu \, dx = \frac{x^{\mu+1}}{\mu+1} + C$ （ $\mu \neq -1$ ）
 $\displaystyle\int \frac{1}{x} \, dx = \ln|x| + C$ 
$\displaystyle\int a^x \, dx = \frac{a^x}{\ln a} + C$ （ $a>0,a\neq1$ ）
 $\displaystyle\int e^x \, dx = e^x + C$ 
### 二、三角函数积分
 $\displaystyle\int \sin x \, dx = -\cos x + C$ 
 $\displaystyle\int \cos x \, dx = \sin x + C$ 
 $\displaystyle\int \tan x \, dx = -\ln|\cos x| + C$
 $\displaystyle\int \cot x \, dx = \ln|\sin x| + C$
 $\displaystyle\int \sec x \, dx = \ln|\sec x + \tan x| + C$ 
 $\displaystyle\int \csc x \, dx = \ln|\csc x - \cot x| + C$ 
 $\displaystyle\int \sec^2 x \, dx = \tan x + C$ 
 $\displaystyle\int \csc^2 x \, dx = -\cot x + C$ 
 $\displaystyle\int \sec x \tan x \, dx = \sec x + C$ 
 $\displaystyle\int \csc x \cot x \, dx = -\csc x + C$ 
 $\displaystyle\int \sin^2 x \, dx = \frac{x}{2} - \frac{\sin 2x}{4} + C$ 
 $\displaystyle\int \cos^2 x \, dx = \frac{x}{2} + \frac{\sin 2x}{4} + C$ 
### 三、反三角函数积分
 $\displaystyle\int \arcsin x \, dx = x\arcsin x + \sqrt{1-x^2} + C$ 
 $\displaystyle\int \arccos x \, dx = x\arccos x - \sqrt{1-x^2} + C$ 
 $\displaystyle\int \arctan x \, dx = x\arctan x - \frac{1}{2}\ln(1+x^2) + C$ 
 $\displaystyle\int \text{arccot } x \, dx = x\text{arccot } x + \frac{1}{2}\ln(1+x^2) + C$ 
### 四、含根式的积分（ a>0 ）
 $\displaystyle\int \frac{1}{\sqrt{a^2 - x^2}} \, dx = \arcsin\frac{x}{a} + C$ 
 $\displaystyle\int \frac{1}{\sqrt{x^2 + a^2}} \, dx = \ln\left(x + \sqrt{x^2 + a^2}\right) + C$ 
 $\displaystyle\int \frac{1}{\sqrt{x^2 - a^2}} \, dx = \ln\left|x + \sqrt{x^2 - a^2}\right| + C$ 
 $\displaystyle\int \sqrt{a^2 - x^2} \, dx = \frac{x}{2}\sqrt{a^2 - x^2} + \frac{a^2}{2}\arcsin\frac{x}{a} + C$ 
 $\displaystyle\int \sqrt{x^2 + a^2} \, dx = \frac{x}{2}\sqrt{x^2 + a^2} + \frac{a^2}{2}\ln\left(x + \sqrt{x^2 + a^2}\right) + C$ 
 $\displaystyle\int \sqrt{x^2 - a^2} \, dx = \frac{x}{2}\sqrt{x^2 - a^2} - \frac{a^2}{2}\ln\left|x + \sqrt{x^2 - a^2}\right| + C$ 
### 五、含分式的积分（ $a\neq0$ ）
 $\displaystyle\int \frac{1}{x^2 + a^2} \, dx = \frac{1}{a}\arctan\frac{x}{a} + C$ 
 $\displaystyle\int \frac{1}{x^2 - a^2} \, dx = \frac{1}{2a}\ln\left|\frac{x - a}{x + a}\right| + C$ 
 $\displaystyle\int \frac{1}{ax + b} \, dx = \frac{1}{a}\ln|ax + b| + C$ 
### 六、指数与对数结合积分
 $\displaystyle\int x e^x \, dx = (x-1)e^x + C$ 
$\displaystyle\int x \ln x \, dx = \frac{x^2}{2}\ln x - \frac{x^2}{4} + C$ 
 $\displaystyle\int e^x \sin x \, dx = \frac{e^x}{2}(\sin x - \cos x) + C$ 
 $\displaystyle\int e^x \cos x \, dx = \frac{e^x}{2}(\sin x + \cos x) + C$ 
### 七、常用凑微分积分
 $\displaystyle\int \frac{1}{\sqrt{1 - x^2}} \, dx = \arcsin x + C = -\arccos x + C$ 
 $\displaystyle\int \frac{1}{1 + x^2} \, dx = \arctan x + C = -\text{arccot } x + C$ 
 $\displaystyle\int \frac{1}{x\ln x} \, dx = \ln|\ln x| + C$ 
 $\displaystyle\int \frac{e^{\sqrt{x}}}{\sqrt{x}} \, dx = 2e^{\sqrt{x}} + C$ 
 $\displaystyle\int \frac{\sin\sqrt{x}}{\sqrt{x}} \, dx = -2\cos\sqrt{x} + C$ 
>[!abstract] 练习
>尝试推导上述公式

Trivia: 魔法六边形
<svg xmlns="http://www.w3.org/2000/svg" width="177.5" height="133.1" version="1.1" style="font-family:Latin Modern Math; font-size:20px; fill:#ba00ff; stroke-width:0.32px;">
<defs>
	<marker style="overflow:visible;" orient="auto">
		<path transform="matrix(-0.4,0,0,-0.4,-4,0)" style="fill:#005c94; stroke:#005c94; stroke-width:1pt;" d="M 0,0 5,-5 -12.5,0 5,5 Z"/>
	</marker>
</defs>
<g transform="translate(225.063,490.564)">
	<path style="fill:#fefad7; stroke:#a40000; stroke-width:0.47;" d="m -105.7,-371.2 -57.7,0 -28.9,-50 28.9,-50 57.7,0 28.9,50 z"/>
	<path style="fill:none; stroke:black;" d="m -163.5,-471.1 57.5,99.5"/>
	<path style="fill:none; stroke:black;" d="M -192.2,-421.2 H -77.1"/>
	<path style="fill:none; stroke:black;" d="m -106,-471.1 -57.3,99.9"/>
	<text x="-179.5" y="-475.8" style="font-style:italic;">sin</text>
	<text x="-226.1" y="-416.1" style="font-style:italic;">tan</text>
	<text x="-116.9" y="-475.8" style="font-style:italic;">cos</text>
	<text x="-178.1" y="-357.8" style="font-style:italic;">sec</text>
	<text x="-74.9" y="-416.1" style="font-style:italic;">cot</text>
	<text x="-117.8" y="-357.8" style="font-style:italic;">csc</text>
	<text x="-147.3" y="-407.8" transform="scale(1.00188,0.998123)" style="font-family:Arial; font-size:42.7px; fill:black; stroke:white;">1</text>
</g>
</svg>
