---
Todo: 整合他人素材，完成这个讲义。
Requires: 先写点自己的理解和做题的感悟，有人提交时就整合，并审稿，特别是例题，需要自己做
aliases:
  - Integrate
---
%%用两个百分号扩在一起的是MarkDown注释，保存时不会展现。如无必要，无需删去。
也可以用这种方法标注内容
所有“待审查”是标注待审查标签上面的内容
%%
# Section 1  积分基础

数学是对抽象概念的演绎，有概念我们就得讲定义。所以先上不定积分与定积分的定义。

>[!info] 定义$\qquad$原函数与不定积分
>对一个定义在区间 $I$ 上的函数 $f(x)$，如果存在一个可导函数 $F(x)$，使得$$F'(x)=f(x),$$则称 $F(x)$ 是 $f(x)$ 的一个原函数。 $f(x)$ 的原函数全体称为其不定积分，记作$$\int f(x)\text dx=F(x)+C,$$其中 $C$ 是常数。

按照这个定义，$f(x)$ 后面的 $\text dx$ 似乎是不必要的——但显然实际上不是。大家有兴趣可以自己去查资料，我们的时间都比较有限，就不展开了。自己有好奇心去探索才是学习的一个最大动力……

言归正传，接下来是定积分的定义。
>[!info] 定义$\qquad$定积分
>设 $f(x)$ 在区间 $[a,b]$ 上有定义，取一列数 $x_i(i=0,1,\cdots,n)$，满足 $a=x_0\lt x_1\lt x_2 \lt \cdots\lt x_n=b$，记 $\lambda=\min\limits_{0\leqslant i\lt n}(x_{i+1}-x_i),$ 如果对任意$\xi_i\in[x_i,x_{i+1}],0\leqslant i\lt n$，极限 $\displaystyle\lim_{\lambda\to0}\sum_{i=0}^{n-1}f(\xi_i)(x_{i+1}-x_i)$ 存在，则称函数 $f(x)$ 在区间 $[a,b]$ 上可积，记为$$\int_a^bf(x)\text dx=\lim_{\lambda\to0}\sum_{i=0}^{n-1}f(\xi_i)(x_{i+1}-x_i),$$
>其结果称为定积分。
<br>

然后是连接不定积分与定积分桥梁：牛顿-莱布尼兹公式

>[!info] 牛顿-莱布尼兹公式
>设 $f(x)$ 在区间 $[a,b]$ 上可积，且有一个原函数 $F(x)$ ，则$$\int_a^bf(x)\text dx=F(b)-F(a).$$

使用这个定理是有条件的。因为 $F(x)$ 是 $f(x)$ 的一个原函数，所以它必须可导，从而必须<span class="emphasize">连续</span>。
有了这个定理，我们就可以比较方便地计算定积分了——至少比用定义方便。并且，这也让我们有了求不定积分的动力。根据不定积分的定义，我们可以将基本求导公式反推，得到下面的常用的基本不定积分公式（更详尽的在最下面）：

$\displaystyle\int 0\mathrm dx =C$，<span class="emphasize">补药漏写常数 C 口牙！</span>
$\displaystyle\int k\mathrm dx = kx + C$ （ $k$  为常数）
$\displaystyle\int x^\mu\mathrm dx = \frac{x^{\mu+1}}{\mu+1} + C$ （ $\mu \neq -1$ ）
$\displaystyle\int \frac{1}{x}\mathrm dx = \ln|x| + C$ 
$\displaystyle\int a^x\mathrm dx = \frac{a^x}{\ln a} + C$ （ $a>0,a\neq1$ ）
$\displaystyle\int e^x\mathrm dx = e^x + C$ 
$\displaystyle\int \sin x\mathrm dx = -\cos x + C$ 
$\displaystyle\int \cos x\mathrm dx = \sin x + C$ 
 $\displaystyle\int \sec^2 x\mathrm dx = \tan x + C$ 
 $\displaystyle\int \csc^2 x\mathrm dx = -\cot x + C$ 
 $\displaystyle\int \sec x \tan x\mathrm dx = \sec x + C$ 
 $\displaystyle\int \csc x \cot x\mathrm dx = -\csc x + C$ 
以下公式不是基本不定积分公式，但是也很常见，必须熟记：
$\displaystyle\int \tan x\mathrm dx = -\ln|\cos x| + C$
$\displaystyle\int \cot x\mathrm dx = \ln|\sin x| + C$
$\displaystyle\int \sec x\mathrm dx = \ln|\sec x + \tan x| + C$ 
$\displaystyle\int \csc x\mathrm dx = \ln|\csc x - \cot x| + C$ 
（这一列撬棍是不是特别喜感哈哈哈哈）
# Section 2  积分方法
## 预处理
拿到一个积分，最忌讳的是直接被那一团复杂的被积函数吓倒。先尝试着逐步拆解简化这个积分，然后进行求解。
常见的预处理方式：
### 1. 对定积分：在积分上下限互为相反数时靠奇函数来消项；通过拆分上下限来简化可能性
### 2. 对有理式：有理式的拆解
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
>2. 对于分母为二次函数，那么其分子就是一次函数，并且依旧要符合规则1。

接下来就能用待定系数法求出那些待定的系数 $A,B,M,N$ 等等。一般来说，这个过程不会太复杂，大可不必拿出考完的线代。下面这个都还算是难的。

>[!summary] 任务
>尝试用待定系数法推出 $\displaystyle\frac{1}{(1+2x)(1+x^2)} = \frac{1}{5}\left(\frac{4}{1+2x}+\frac{-2x+1}{1+x^2}\right)$

>[!solution] 解析
>$\displaystyle\frac{1}{(1+2x)(1+x^2)}$ 本身就是真分式。
>我们可以将其拆分为 $$\frac A{1+2x} - \frac{Bx+C}{1+x^2}$$
>合并得 $$\dfrac{(A+2B)x^2+(B+2C)x+(A+C)}{(1+2x)(1+x^2)}$$
>然后列方程组 $$\begin{cases}A+2B=0\\B+2C=0\\A+C=1\end{cases}$$
>解得 $$\begin{cases}A=\frac45\\B=\frac{-2}5\\C=\frac15\end{cases}$$
>代入得 $\displaystyle\frac {\frac45}{1+2x}+\frac{\frac{-2}5x+\frac15}{1+x^2}$
>化简，即得 $\displaystyle\frac{1}{(1+2x)(1+x^2)} = \frac{1}{5}\left(\frac{4}{1+2x}+\frac{-2x+1}{1+x^2}\right)$

当然，并不是所有时候都要用待定系数法，如果你的注意力惊人。
比如说对于 $\displaystyle\int\frac{2\mathrm dx}{x^2-1}$，$\displaystyle\frac{2}{x^2-1}=\frac{1}{x-1}-\frac{1}{x+1}$
也不是一定要给它拆成这种细碎的样子，因题目而异。如果不拆分有更快的做法，那就没必要拆。
### 对根式：欧拉代换（可选）
>[!danger] 警告
>欧拉代换法是你最后的防线，而非你的第一个想法。
>当普通的代换能解决问题，如 $\sqrt{x^2+2x+2}=\sqrt{(x+1)^2+1}$，那么最好不用欧拉代换法。
>如果实在想不出来怎么做，可以用欧拉替代法硬算，将其作为最后的手段。

对于不定积分 $\int R\left(x,\sqrt{ax^2+bx+c}\right)dx \quad (a\neq0)$，可以从如下角度作代换：
- 欧拉第一代换：如果 $a>0$，令 $\sqrt{ax^2+bx+c}=t-\sqrt{a}x$，或令 $\sqrt{ax^2+bx+c}=\sqrt{a}x+t$。
- 欧拉第二代换：如果 $c>0$，令 $\sqrt{ax^2+bx+c}=tx-\sqrt{c}$，或令 $\sqrt{ax^2+bx+c}=tx+\sqrt{c}$。
- 欧拉第三代换：如果 $ax^2+bx+c=a(x-\alpha)(x-\beta)$，则可以令 $\sqrt{ax^2+bx+c}=t(x-\alpha)$
对于任意一种换元，换元后等式两边平方，此时 $x^2$ 这一项将会被抵消，因此用含 $t$ 的多项式将 $x$ 表示出来。
>[!todo] 示例
>求不定积分$\displaystyle\int \frac{dx}{(x^2+a^2)\sqrt{a^2-x^2}}$
>解：令 $\sqrt{a^2-x^2}=t(a-x)$，则
>$$\displaystyle t^2=\frac{a+x}{a-x},\quad x=a\frac{t^2-1}{t^2+1},\quad\mathrm dx=\frac{4at}{(t^2+1)^2}\mathrm dt$$
>$$\displaystyle x^2+a^2=\frac{2a^2(t^4+1)}{(t^2+1)^2}$$
>于是
>$$\begin{align}\int \frac{\mathrm dx}{(x^2+a^2)\sqrt{a^2-x^2}} &= \int \frac{\frac{4at}{(t^2+1)^2}\mathrm dt}{\frac{2a^2(t^4+1)}{(t^2+1)^2}\cdot\frac{2at}{t^2+1}} \\&= \frac{1}{2a^2}\int \frac{2t^2+2}{t^4+1}\mathrm dt\end{align}$$
>之后可以按照有理式的方法继续积分下去。
### 对奇数次三角函数：万能代换
>[!danger] 警告
>万能代换法同样是你最后的防线，计算量很大，只有在万不得已的时候才会考虑。

对于由三角函数和常数经过有限次四则运算构成的函数，即三角函数有理式的积分，我们常常利用到三角函数中的万能代换：$$t=\tan\frac x2$$
我们做题中，令  $\displaystyle t = \tan \frac{x}{2}$ ，则 $\displaystyle\mathrm dx = \frac{2}{1 + t^2}\mathrm dt$。

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
>利用 $\cos x$ 来凑微分而不是 $\sin x$，这样你就能得到偶数次方的三角函数——如果最后剩下奇数次方的 $\sin x,\cos x$，那么可能还要多花一点心思去做换元或用别的技巧，但是偶数次方的可操作性强很多，你可以用 $\sin^2x+\cos^2x=1$ 来升降次，用诸如 $\cos^2x=\dfrac{1+\cos 2x}{2}$ 来换角，比奇数次更加便捷。
>“化偶数次”也是万能代换 $x=\tan\frac{t}{2}$ 背后的逻辑。

>[!solution] 解析
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

>[!solution] 解析
>令 $x = a\tan t$ ，则$\mathrm dx = a\sec^2 t\mathrm dt$，$t \in \left(-\frac{\pi}{2},\frac{\pi}{2}\right)$，则
$\sqrt{x^2+a^2} = \sqrt{a^2\tan^2 t + a^2} = a\sec t$
>$\begin{align}\int \frac{dx}{\sqrt{x^2+a^2}} &= \int \frac{a\sec^2 t dt}{a\sec t} \\&= \int \sec t dt \\&= \ln|\sec t + \tan t| + C_1 \\&= \ln\left|\frac{\sqrt{x^2+a^2}}{a} + \frac{x}{a}\right| + C_1 \\&= \ln\left|x + \sqrt{x^2+a^2}\right| + C\end{align}$

>[!hint] 对于反三角函数，我们可以用第一类换元法，尝试构造 $u$ 等于该反三角函数：
>$$\begin{align*}
\int \frac{\sqrt{\arctan x}}{1+x^2}\mathrm dx
&= \int \sqrt{\arctan x}\mathrm d(\arctan x) \\
&= \frac{2}{3}(\arctan x)^{\frac{3}{2}} + C
\end{align*}$$
#### 3. 有理式
>[!example] 例2.3
>求不定积分 $\displaystyle\int\dfrac{x\mathrm dx}{(x-1)^{100}}$.

>[!solution] 解析
>$\begin{align}\text{原式}&=\int\frac{(x-1)+1}{(x-1)^{100}}\mathrm d(x-1)\\&=\int\frac{\mathrm d(x-1)}{(x-1)^{99}}+\int\frac{\mathrm d(x-1)}{(x-1)^{100}}\\&=-\frac{1}{98(x-1)^{98}} - \frac{1}{99(x-1)^{99}} + C\end{align}$

>[!example] 例2.4
>设 $\displaystyle a_n=\int_0^1x(1-x)^n\text dx,n=1,2,\cdots$.
>（1）求级数 $\displaystyle\sum_{n=1}^\infty a_n$；
>（2）设常数 $\lambda\gt0$，试讨论级数 $\displaystyle\sum_{n=1}^\infty \lambda^na_n$ 的敛散性.

>[!solution] 解析
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
a_n &= \int_0^1 x (1-x)^n\mathrm dx = \int_0^1 (1-t) t^n\mathrm dt \\
&= \int_0^1 (t^n - t^{n+1})\mathrm dt = \left[ \frac{t^{n+1}}{n+1} - \frac{t^{n+2}}{n+2} \right]_0^1 \\
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
>为什么用这种换元可以简化计算呢？观察一下特征：一个相对复杂的式子上有一个 $n$ 次方，变得更加复杂，而简单的式子 $x$ 是一次的，更加简单。为了<span class="emphasize">“调和”</span>两个式子的复杂度，我们把复杂式子代换掉，这样就能更加方便地进行积分了。

>[!example] 例2.
>求不定积分 $\displaystyle\int \frac{\mathrm{d}x}{\sqrt[6]{x+1} - \sqrt[3]{x+1}}$

>[!hint] 提示
>对于含有多个次数不同的根式时，换元时要换元为根指数的最小公倍数。
>若被积函数中含有 $\sqrt[n_1]{ax+b}$,$\sqrt[n_2]{ax+b}$,$\dots$,$\sqrt[n_k]{ax+b}$，可考虑代换 $t = \sqrt[n]{ax+b}$（$n$ 为 $n_1$,$n_2$,$\dots,n_k$ 的最小公倍数）
>若被积函数中含有 $\displaystyle\sqrt[n_1]{\frac{ax+b}{cx+d}},\sqrt[n_2]{\frac{ax+b}{cx+d}},\dots,\sqrt[n_k]{\frac{ax+b}{cx+d}}$，可考虑代换 $\displaystyle t = \sqrt[n]{\frac{ax+b}{cx+d}}$（$n$ 为 $n_1$,$n_2$,$\dots$,$n_k$ 的最小公倍数）

>[!solution] 解析
>令 $t=\sqrt[6]{x+1}$，则 $x=t^6-1$，$\mathrm dx=6t^5\mathrm dt$，则 
>$\begin{align}\int \frac{dx}{\sqrt[6]{x+1} - \sqrt[3]{x+1}} &= \int \frac{6t^5 dt}{t - t^2} \\&= 6\int \frac{t^4}{1-t} dt \\&= 6\int \left(-t^3 - t^2 - t - 1 + \frac{1}{1-t}\right) dt \\&= 6\left(-\frac{t^4}{4} - \frac{t^3}{3} - \frac{t^2}{2} - t - \ln|1-t|\right) + C \\&= -\frac{3}{2}\sqrt[3]{(x+1)^2} - 2\sqrt{x+1} - 3\sqrt[3]{x+1} - 6\sqrt[6]{x+1} -\\ 6\ln|\sqrt[6]{x+1} -1| + C\end{align}$
#### 4. 倒代换
在拆解有理式之后，对于 $\dfrac{1}{ax+b},\dfrac{1}{ax^2+bx+c}$ 等一次、二次分式，我们可以从容应对；但是如果次数再高一点，就很难办了。
然而，对于一些较为简单的高次幂函数，我们可以使用**倒代换**：把 $x$ 倒过来！
令 $\displaystyle x=\frac1t,\mathrm dx=-\frac{1}{t^2}\mathrm dt.$

>[!example] 例题
>求不定积分 $\displaystyle\int\frac{1}{x(x^7+2)}\mathrm dx$

>[!solution] 解析
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
<br>

>[!todo] 示例
>求不定积分 $\int x\cos x\mathrm dx$

%%像这种示例，就不用挖掉解答了：
建议以后不挖去解答的用“示例”标签，可以用info或者todo样式%%
>[!done] 正确示例
>解：按照顺序，匹配到“**幂**”，那么我们取 $u=x$，$\mathrm dv=\cos x\mathrm dx=\mathrm d\sin x$
>$\int x \cos x\mathrm dx = \int x\mathrm d\sin x = x \sin x - \int \sin x\mathrm dx = x \sin x + \cos x + C$

>[!fail] 错误示例
>解：我们尝试取 $u=\cos x$，$\mathrm dv=x\mathrm dx=\frac{1}{2}\mathrm dx^2$，
>$\displaystyle\int x\cos x\mathrm dx=\frac{1}{2}\int\cos x\mathrm dx^2=\frac 12\left(x^2\cos x+\int x^2\sin x\mathrm dx\right)$    ……
>你还愿意继续积下去吗？我是不愿意了。
### 常见情况：
#### 1. 幂函数与其他函数乘积
>[!example] 例题
>求不定积分 $\int x^3 \ln x\mathrm dx$

>[!solution] 解析
>最先匹配的是“**对**”（对数函数 $\ln x$），取 $u=\ln x,\mathrm dv=x^3\mathrm dx$，则：
>$\begin{align}\int x^3 \ln x\mathrm dx&= \int \ln x \mathrm d\left(\frac{x^4}{4}\right) \\&= \frac{1}{4}x^4 \ln x - \frac{1}{4}\int x^3\mathrm dx \\&= \frac{1}{4}x^4 \ln x - \frac{1}{16}x^4 + C\end{align}$

>[!example] 例题
>求不定积分 $\displaystyle\int\mathrm e^{\sqrt{x}}\mathrm dx$

>[!solution] 解析
>我们可以提前代换变量，将根式消去。
>令 $t=\sqrt{x}$，则 $t^2=x,\ 2t\mathrm dt=\mathrm dx$，这样就能将根式化为整式。
>$\begin{align}\text{原式}&=2\int t\mathrm e^t\mathrm dt\\&=2\int t\mathrm d\mathrm e^t\\&=2t\mathrm e^t-2\int\mathrm e^t\mathrm dt\\&=2t\mathrm e^t-2\mathrm e^t+C\\&=2\mathrm e^\sqrt x(\sqrt x-1)+C\end{align}$

>[!example] 例题
>求不定积分 $\displaystyle \int x \tan^2 x\mathrm dx = \underline{\qquad}.$

>[!hint] 提示
>这道题取 $u=x$ 没错，不过如何处理 $\mathrm dv$？这需要一定的三角代换。

>[!solution] 解析
>$$\begin{aligned}
>\int x\tan^2x\text dx
>&=\int x(\sec^2x-1)\text dx\\
>&=\int x\text d(\tan x)-\int x\text dx\\
>&=x\tan x-(-\ln|\cos x|)-\frac{x^2}{2}+C\\
>&=x \tan x + \ln |\cos x| - \dfrac{x^2}{2} + C
>\end{aligned}$$

<br>
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

>[!hint] 提示
>在进行循环式时，一般要多次求分部积分。如果你分部积了一次拿不准的话，再分部积一次，也许会有意外收获。

>[!example] 例题
>求 $\displaystyle I=\int\dfrac{\text e^{\arctan x}}{(1+x^2)^{3/2}}\text dx.$

>[!solution] 解析
>令 $u=\arctan x$, 则 $\text dx=\sec^2u\text du.$ 则 $$\begin{aligned}
>\displaystyle I&=\int \text e^u\cos u\text du\\
>&=\int \text e^u\text d\sin u\\
>&=\text e^u\sin u-\int\text e^u\sin u\text du\\
>&=\text e^u\sin u+\int \text e^u\text d\cos u\\
>&=\text e^u\sin u+(\text e^u\cos u-\int\text e^u\cos u\text du)\\
>&=\text e^u\sin u+\text e^u\cos u-I
>\end{aligned},$$于是 $\displaystyle I=\dfrac{1}{2}\text e^u(\sin u+\cos u)=\dfrac{(x+1)\text e^{\arctan x}}{2\sqrt{x^2+1}}+C.$

>[!tip] 小技巧
>如何通过 $u$ 算出 $\sin x$ 和 $\cos x$？只要画一个三角形就看可以很直观地看出来了。
><img src="三角形.png" width="200" height="200"/>

%%上述在同济中亦有记载%%
%%参考：[Math is Fun - Integration by Parts](https://www.mathsisfun.com/calculus/integration-by-parts.html)
仅供娱乐，切勿当真%%
#### 3. 依靠递推式求解的积分
与循环式类似，递推式会在使用分部积分时出现和原式类似，但是比原式“**低一级**”的积分式，这会给人一种“我好像在求数列的递推式”。这个时候就可以把待求积分看作是数列。这种结构一般在积分式含有正整数 $n$ 的时候出现（e.g. $(x^2+a^2)^n$ ）例如：
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
>这样我们就能依次推出 $I_2,I_3,\cdots,I_n$

>[!bug] 这道题求通项似乎是一件很困难的事。
>一般来说不要求像数列一样求出通项。

>[!example] 例题
>证明 $\displaystyle I_n=\int\tan^nx\text{d}x=\dfrac{\tan^{n-1}x}{n-1}-I_{n-2}.$

>[!solution] 解析
>$\displaystyle \begin{align}I_n&=\int\tan^{n-2}x(\sec^2x-1)\text{d}x\\&=\int\tan^{n-2}x\text{d}(\tan x)-I_{n-2}\\&=\dfrac{\tan^{n-1}x}{n-1}-I_{n-2}\end{align}$

>[!example] 例题
>记 $\displaystyle I_n = \int_0^{\frac{\pi}{4}} \sec^n x \mathrm dx, \ (n=0,1,2,\cdots)$。
(1) 证明：当 $n \geq 2$ 时，$\displaystyle I_n = \frac{2^{\frac{n-2}{2}}}{n-1} + \frac{n-2}{n-1} I_{n-2}$；
(2) 计算 $I_3$ 的值。

>[!solution] 解析
>（1）证明：$$\begin{aligned}
I_n &= \int_0^{\frac{\pi}{4}} \sec^n x \mathrm dx = \int_0^{\frac{\pi}{4}} \sec^{n-2} x \cdot \sec^2 x \mathrm dx \\
&= \int_0^{\frac{\pi}{4}} \sec^{n-2} x \mathrm d(\tan x) \\
&= \left[ \tan x \sec^{n-2} x \right]_0^{\frac{\pi}{4}} - \int_0^{\frac{\pi}{4}} \tan x \cdot (n-2) \sec^{n-3} x \cdot \sec x \tan x \mathrm dx \\
&= 1 \cdot 2^{\frac{n-2}{2}} - (n-2) \int_0^{\frac{\pi}{4}} \tan^2 x \sec^{n-2} x \mathrm dx \\
&= 2^{\frac{n-2}{2}} - (n-2) \int_0^{\frac{\pi}{4}} (\sec^2 x - 1) \sec^{n-2} x \mathrm dx \\
&= 2^{\frac{n-2}{2}} - (n-2) \left( I_n - I_{n-2} \right),
\end{aligned}$$
>故$\displaystyle I_n = \frac{2^{\frac{n-2}{2}}}{n-1} + \frac{n-2}{n-1} I_{n-2}.$
>（2）$\displaystyle I_1=\int_0^\frac{\pi}{4}\sec x\text dx=[\ln|\sec x+\tan x|]_0^\frac{\pi}{4}=\ln(\sqrt2+1).$
>故$\displaystyle I_3=\frac{2^{\frac{3-2}{2}}}{3-1} + \frac{3-2}{3-1} I_{3-2} = \frac{\sqrt{2}}{2} + \frac{1}{2} I_1 = \frac{\sqrt{2}}{2} + \frac{1}{2} \ln(\sqrt{2} + 1).$

>[!summary] 题后总结
>因为要证明的式子中是 $I_n$ 和 $I_{n-2}$，中间隔了两项，所以在凑的时候也要凑一个 $\tan^2x$和$\sec^2x$ 出来；而且 $\tan^2x=\sec^2x-1,\text d(\tan x)=\sec^2x\text dx$，用平方也更好凑一点。

#### 4. 连续分部积分（选学？）
>[!bug] 需要斟酌该内容是否重要。

分部积分法的推广公式就是重复使用分部积分法法则。
假设函数 $u,v$ 有 $n+1$ 阶连续导数，则：$\int u v^{(n+1)}\mathrm dx = \int u\mathrm d v^{(n)} = u v^{(n)} - \int v^{(n)}\mathrm du = u v^{(n)} - \int u' v^{(n)}\mathrm dx$
我们还可以继续把 $\int u' v^{(n)}\mathrm dx$ 撕开：$$\int u v^{(n+1)} dx = u v^{(n)} - u' v^{(n-1)} + u'' v^{(n-2)} - \dots + (-1)^n u^{(n)} v + (-1)^{n+1} \int u^{(n+1)} v dx$$
如果被积函数的因式之一是多项式，且次数较高的时候，这个公式特别方便。通常来说，取 $u$ 为该多项式，然后逐步求 $v^{(n)},v^{(n-1)},\cdots,v$，再依次乘到一起（注意正负号！）
>[!todo] 示例
>$\int (2x^3 + 3x^2 + 4x + 5)\mathrm e^x\mathrm dx$

>[!solution] 解析
>我们可以令 $u=2x^3 + 3x^2 + 4x + 5$，$v=\mathrm e^x$
>$u' = 6x^2 + 6x + 4,\quad u'' = 12x + 6,\quad u''' = 12$
>于是$\begin{align*}\int (2x^3 + 3x^2 + 4x + 5) e^x dx &= (2x^3 + 3x^2 + 4x + 5)e^x - (6x^2 + 6x + 4)e^x + (12x + 6)e^x - 12e^x + C \\&= (2x^3 - 3x^2 + 10x - 5)e^x + C\end{align*}$

>[!example] 例题
>求不定积分 $\int \cos x (x^3 + 2x^2 + 3x + 4) dx$

>[!solution] 解析
>解：令 $u=x^3 + 2x^2 + 3x + 4$，$u'=3x^2+4x+3$，$u''=6x+4$，$u'''=6,u^{(4)}=0$
>$v^{(4)}=\cos x,v'''=\sin x,v''=-\cos x,v'=-\sin x,v=\cos x$
>于是
>$\begin{align}\int\cos x(x^3+2x^2+3x+4)\mathrm dx&=(x^3 + 2x^2 + 3x + 4)\sin x\\&\qquad+(3x^2+4x+3)\cos x-(6x+4)\sin x-6\cos x+C\\&=(x^3+2x^2-3x)\sin x+(3x^2+4x-3)\cos x+C\end{align}$

>[!bug] 待验证正确性

但是我们一般其实用不到这么高阶的，而低阶的不用这个公式也能比较自然地做出来，比如：

>[!example] 例题
>设 $f(x)$ 在 $[a, b]$ 上有连续的二阶导数，且 $f(a) = f(b) = 0$，试证
>$$\int_a^b f(x) \, dx = \frac{1}{2} \int_a^b (x - a)(x - b) f''(x) \, dx.$$

>[!solution] 解析
>$$\begin{aligned}\int_a^b(x-a)(x-b)f''(x)\text dx
>&=\int_a^b(x-a)(x-b)\text df'(x)\\
>&=(x-a)(x-b)f'(x)\bigg|_a^b-\int_a^b(2x-a-b)\text df(x)\\
>&=-(2x-a-b)f(x)\bigg|_a^b+\int_a^b f(x)\text d(2x)\\
>&=2\int_a^bf(x)\text dx.
>\end{aligned}$$

# Section 4  变限积分

变限积分的意思就是这个积分的上/下限是变量。它最重要的性质就是$$\frac{\text d}{\text dx}\left(\int_a^xf(t)\text dt\right)=f(x).$$
由此有一些推论：
1. $\displaystyle\frac{\text d}{\text dx}\left(\int^a_xf(t)\text dt\right)=-f(x);$
2. $\displaystyle\frac{\text d}{\text dx}\left(\int_a^{\varphi(x)}f(t)\text dt\right)=f(\varphi(x))\varphi'(x);$
3. $\displaystyle\frac{\text d}{\text dx}\left(\int_{\psi(x)}^{\varphi(x)}f(t)\text dt\right)=f(\varphi(x))\varphi'(x)-f(\psi(x))\psi'(x).$

利用牛顿-莱布尼兹公式和复合函数求导法则可以证明这三点。
变限积分的一个难点就是被积函数里出现 $x$ 时应该怎么处理。一般来说有两个处理办法：

1. 类似 $\displaystyle\int_a^x(t+g(t))f(t)\text dt$ 的形式，可以拆开处理，即 $\displaystyle\int_a^x(x+g(t))f(t)\text dt= x\int_a^xf(t)\text dt+\int_a^xg(t)f(t)\text dt;$
2. 类似 $\displaystyle\int_a^xf(x+t)\text dt$ 的形式，可以进行换元，令 $u=x+t$，则 $\text dt=\text du$，所以 $\displaystyle\int_a^xf(x+t)\text dt=\int_{x+a}^{2x}f(u)\text du.$

上面两种类型并没有穷尽所有的可能，只是抛砖引玉，实际可能的变形是有很多的。
<br>
先来两道简单的题目热热身。

>[!example] 例题
>计算极限  
>$$\lim_{x\to 0}\frac{x - \large\int_{0}^{x}\cos t^{2}\mathrm{d}t}{x^{3}\ln(1 + \tan^{2}x)}。$$

>[!hint] 提示
>观察一下上下的极限分别是多少

>[!solution] 解析：
>用等价无穷小代换和洛必达法则$$\begin{aligned}
>\text{原式}&=\lim_{x\to0}\frac{x-\large\int_0^x\cos t^2\text dt}{x^5}\\
>&\overset{\frac{0}{0}}{=}\lim_{x\to0}\frac{1-\cos x^2}{5x^4}\\
>&=\lim_{x\to0}\frac{\frac{1}{2}x^4}{5x^4}\\
>&=\frac{1}{10}.
>\end{aligned}$$

>[!example] 例题
>已知 
>$$\begin{cases} 
>x = \large\int_{0}^{t} \frac{\sin u}{u} \text du, \\ 
>y = \large\int_{0}^{t} \sin u^2 \text du, 
>\end{cases}$$ 
>求 $\dfrac{\text dy}{\text dx}$ 和 $\dfrac{\text d^2 y}{\text dx^2}$。 

>[!hint] 提示
>还记得参数方程的二阶导怎么求吗？
>$$\displaystyle\frac{\text d^2y}{\text dx^2}=\frac{\text d}{\text dx}\left(\frac{\text dy}{\text dx}\right)=\frac{\text d}{\text dt}\left(\frac{\text dy}{\text dx}\right)\bigg/\frac{\text dx}{\text dt}.$$

>[!solution] 解析
>$x$ 和 $y$ 分别对 $t$ 求导得$$\frac{\text dx}{\text dt}=\frac{\sin t}{t},\frac{\text dy}{\text dt}=\sin t^2.$$
>故 $$\frac{\text dy}{\text dx}=\frac{\text dy}{\text dt}\bigg/\frac{\text dx}{\text dt}=t\sin t.$$
>$$\frac{\text d^2y}{\text dx^2}=\frac{\text d}{\text dt}\left(\frac{\text dy}{\text dx}\right)\bigg/\frac{\text dx}{\text dt}=\frac{\sin t+t\cos t}{\sin t^2}.$$

积分的题目往往比较综合，会和其他的知识点一起考察，比如……级数。

>[!example] 例题
>已知函数 $$f_n(x)=\int_0^xt^2(1-t)\sin^{2n}t\text dt,\qquad x\in(-\infty,+\infty),$$其中 $n$ 为正整数。
>（1）证明：对任意正整数 $n$，函数 $f_n(x)$ 在 $x=1$ 处取得最大值；
>（2）记 $a_n=f_n(1),n=1,2,\cdots$，试判断级数 $\displaystyle\sum_{n=1}^\infty a_n$ 的敛散性。

>[!solution] 解析
>（1）$f'_n(x)=x^2(1-x)\sin^{2n}x$，令 $f'_n(x)=0$，得 $x=0,1,\pm n\pi(n=1,2,\cdots)$
>当 $x\lt1$ 时，$x^2\gt0$，$1-x\gt0$，$\sin^{2n}x\gt0$，故 $f'_n(x)\gt0$；当 $x\gt1$ 时，$x^2\gt0$，$1-x\lt0$，$\sin^{2n}x\gt0$，故 $f'_n(x)\lt0$。因此 $f_n(x)$ 在 $x=1$ 左侧递增，右侧递减，从而 $x=1$ 为 $f_n(x)$ 的极大值点，也是最大值点。
>
>（2）当 $t\in[0,1]$ 时，有 $0\leqslant\sin t\leqslant t$，故$$\begin{aligned}
>0\leqslant a_n
>&=\int_0^1t^2(1-t)\sin^{2n}t\text dt\\
>&\leqslant\int_0^1t^{2n+2}(1-t)\text dt\\
>&=\frac{t^{2n+3}}{2n+3}\bigg|_0^1-\frac{t^{2n+4}}{2n+4}\bigg|_0^1\\
>&=\frac{1}{(2n+3)(2n+4)}.
>\end{aligned}$$
>又$$\lim_{n\to\infty}\dfrac{(2n+3)(2n+4)}{n^2}=4,$$由比较判别法知 $\displaystyle\sum_{n=1}^\infty\frac{1}{(2n+3)(2n+4)}$ 收敛，故 $\displaystyle \sum_{n=1}^\infty a_n$ 收敛。

>[!example] 例题
>已知函数 $f(x)$ 在 $(-\infty, +\infty)$ 内连续，且
$$\int_0^x t f(x-t)\mathrm {d}t = x^3 - \int_0^x f(t) \mathrm{d}t.$$
(1) 验证：$f'(x) + f(x) = 6x$ 且 $f(0) = 0$；
(2) 计算定积分 $\displaystyle \int_0^1 \text e^x f(x) \mathrm{d}x$。

>[!solution] 解析
>（1）令 $u=x-t$，则$$\begin{aligned}
>-\int_x^0(x-u)f(u)\text du
>&=x\int_0^xf(u)\text du-\int_0^xuf(u)\text du\\
>&=x^3-\int_0^xf(t)\text dt\\
>&=x^3-\int_0^xf(u)\text du
>\end{aligned},$$
>两边求导得$$\int_0^xf(u)\text du+xf(x)-xf(x)=\int_0^xf(u)\text du=3x^2-f(x),\qquad(*)$$
>再求导得$f'(x) + f(x) = 6x.$ 在 $(*)$ 式中令 $x=0$ 得 $f(0)=0.$
>（2）
>**解1：** 考虑不定积分 $\displaystyle \int \text e^xf(x)\text dx.$ 用分部积分法得$$\begin{aligned}
>\int \text e^xf(x)\text dx
>&=\int f(x)\text d\text e^x\\
>&=\text e^xf(x)-\int f'(x)\text e^x\text dx\\
>&=\text e^xf(x)-\int (6x-f(x))\text e^x\text dx\\
>&=\text e^xf(x)-6(x-1)\text e^x+\int \text e^xf(x)\text dx
>\end{aligned},$$于是 $\text e^xf(x)=6(x+1)\text e^x+C.$ 由 $f(0)=0$ 知 $C=6,$ 故 $\text e^xf(x)=6(x+1)\text e^x+6.$
>从而 $\displaystyle \int_0^1\text e^xf(x)\text dx=6(x+2)\text e^x\big|_0^1+6x\big|_0^1=18\text e-6.$
>
>**解2：** 令 $g(x) = \text e^x f(x)$，则 $g(0)=0$，且$$g'(x) = \text e^x [f'(x)+f(x)] = 6x \text e^x.$$
积分得$$g(x) = \int 6x \text e^x\mathrm{d}x = 6(x-1)\text e^x + C.$$
代入 $g(0)=0$ 得 $0 = 6(0-1) + C$，即 $C=6$，所以$$g(x) = 6(x-1)\text e^x + 6.
$$于是$$\begin{aligned}
\int_0^1 \text e^x f(x)\mathrm {d}x 
&= \int_0^1 \left[ 6(x-1)\text e^x + 6 \right]\mathrm {d}x \\
&= \left[ 6(x-2)\text e^x + 6x \right]_0^1 \\
&= ( -6\text e + 6) - (-12) \\
&= 18 - 6\text e.
\end{aligned}$$

>[!summary] 题后总结
>第一问需要用到两个东西：（1）换元，把函数里的 $x$ 拿到函数外面来；（2）<span style='color: orange'>定积分的值与被积变量无关</span>。第二点很容易被忘记。
>第二问的两种解法都是有来头的。
>解法1源自分部积分法，如果你尝试对需要求的定积分进行分部积分法，然后再用第一问的结论带进去，就会发现 $\displaystyle\int_0^1\text e^xf(x)\text dx$ 这一项被消掉了，这时如果你相对敏锐一点就会想到——这一项在不定积分中也会被消掉！这样我们就可以直接求出 $f(x)$ 的表达式了，再求定积分自然不在话下。剩下要注意就是<span style='color: orange' >不要忘记积分常数</span>。
>解法2的思路类似于微分中值定理的题。我们看第一问的结论 $f'(x) + f(x) = 6x$，是不是很像微分中值定理中我们要凑的 $(\text e^xf(x))'$？这样就产生了第二种思路。后面的过程中仍然要注意<span class="emphasize">不要忘记积分常数</span>。

# Section 5  定积分

由于定积分确定了上下限，因此定积分在不定积分的基础上多了不少有趣的性质，比如之前提到的在 $[-a,a]$ 有定义的奇函数在 $[-a,a]$ 的定积分为 $0$ ；
除此之外还有很多性质，有些会为积分的化简提供便利，有些会给你挖个大坑。

1. **周期函数每个周期内的定积分相同**
简单来说，如果 $T$ 是 $f(x)$ 的周期，那么 $\displaystyle\int_a^{a+T}f(x)\mathrm dx=\int_{a+T}^{a+2T}f(x)\mathrm dx$.
>[!example] 例题
>定积分 $\int_{-2026}^{2026} (x-[x])\mathrm dx$（其中 $[x]$ 表示不超过 $x$ 的最大整数）的值为\_\_\_\_\_\_\_\_。

>[!solution] 解析
>$f(x)=x-[x]$ 是周期为 $1$ 的函数，那么 $\displaystyle\int_{-2026}^{2026} (x-[x])\mathrm dx=5052\int_0^1(x-[x])\mathrm dx=5052\int_0^1x\mathrm dx=5052 \left[\frac{x^2}{2} \right]_0^1=2026$

>[!example] 例题
>已知 $\displaystyle a_n = \int_0^{n\pi} |\cos x| \mathrm dx,\ n=1,2,\cdots$，则下列级数收敛的是（ ）。
(A) $\displaystyle \sum_{n=1}^\infty \frac{a_n}{n}$
(B) $\displaystyle \sum_{n=1}^\infty \frac{a_n}{n^2}$
(C) $\displaystyle \sum_{n=1}^\infty (-1)^n \frac{a_n}{n}$
(D) $\displaystyle \sum_{n=1}^\infty (-1)^n \frac{a_n}{n^2}$

>[!note] 解析
>由于函数 $|\cos x|$ 以 $\pi$ 为周期，所以$$a_n = \int_0^{n\pi} |\cos x| \mathrm dx = n \int_0^{\pi} |\cos x| \mathrm dx = n \cdot 2 \int_0^{\pi/2} \cos x \mathrm dx = 2n\sin x|_0^{\pi/2} = 2n.$$
>对于选项(A)，有 $\displaystyle\sum_{n=1}^{\infty}\frac{a_n}{n}=\sum_{n=1}^{\infty}2,$ 显然发散；
>对于选项(B)，有 $\displaystyle\sum_{n=1}^{\infty}\frac{a_n}{n^2}=\sum_{n=1}^{\infty}\frac{2}{n},$ 是调和级数的两倍，也发散；
>对于选项(C)，有 $\displaystyle\sum_{n=1}^\infty (-1)^n \frac{a_n}{n} = \sum_{n=1}^\infty (-1)^n \frac{2n}{n} = \sum_{n=1}^\infty (-1)^n 2,$ 通项不趋于 $0$，故发散；
>对于选项(D)，有 $\displaystyle\sum_{n=1}^\infty (-1)^n \frac{a_n}{n^2} = \sum_{n=1}^\infty (-1)^n \frac{2n}{n^2} = 2 \sum_{n=1}^\infty \frac{(-1)^n}{n}$，为交错级数，由莱布尼兹判别法易知其收敛.
>故选D.

>[!summary] 题后总结
>这道题的关键在于利用三角函数的<span style='color: blue'>周期性</span>，然后再利用对称性（第二个等号处）简化积分的计算。尤其要注意带绝对值的三角函数，它的定积分基本上只需要对 $\dfrac{\pi}{2}$ 的长度进行研究就可以了（见图）。

![[cosx的绝对值.png]]



2. 除此之外，还可以把定积分的上下限劈开：$\int_a^bf(x)\mathrm dx=\int_a^cf(x)\mathrm dx+\int_c^bf(x)\mathrm dx$，这在 $f(x)$ 是分段函数（如绝对值）的情况下特别有用：
>[!example] 例题
>已知函数 $\displaystyle f(x) = \begin{cases} \frac{1}{1 + \sqrt[3]{x}}, & x \geq 0, \\ \frac{\arctan x}{1 + x^2}, & x < 0, \end{cases}$ 计算定积分 $\displaystyle I = \int_{-1}^1 f(x)\mathrm dx$。

>[!solution] 解析
>我们可以按照 $f(x)$ 的分段形式对定积分进行拆分：
>$$\displaystyle I = \int_{-1}^1 f(x)  \mathrm dx = \int_{-1}^0 f(x)  \mathrm dx + \int_0^1 f(x)  \mathrm dx$$
> 对于第一部分：
>$$
  \int_{-1}^0 f(x)\mathrm dx = \int_{-1}^0 \frac{\arctan x}{1+x^2}\mathrm dx = \int_{-1}^0 \arctan x\mathrm d(\arctan x) = \frac{1}{2} (\arctan x)^2 \bigg|_{-1}^0 = -\frac{\pi^2}{32}.$$
>对于第二部分，令 $t = \sqrt[3]{x}$，则 $x = t^3,\ dx = 3t^2 dt$，且当 $x$ 从 $0$ 到 $1$ 时，$t$ 从 $0$ 到 $1$：
  >$$
  \begin{aligned}
  \int_0^1 f(x)\mathrm dx &= \int_0^1 \frac{1}{1+\sqrt[3]{x}}\mathrm dx = \int_0^1 \frac{1}{1+t} \cdot 3t^2\mathrm dt = 3 \int_0^1 \frac{t^2}{1+t}\mathrm dt \\
  &= 3 \int_0^1 \left( t - 1 + \frac{1}{1+t} \right)\mathrm dt = 3 \left[ \frac{1}{2} t^2 - t + \ln |1+t| \right]_0^1 \\
  &= 3 \left( \frac{1}{2} - 1 + \ln 2 \right) = 3 \ln 2 - \frac{3}{2}.
  \end{aligned}$$
>故$$I = \int_{-1}^1 f(x)\mathrm dx = \int_{-1}^0 f(x)\mathrm dx + \int_0^1 f(x)\mathrm dx = -\frac{\pi^2}{32} + 3 \ln 2 - \frac{3}{2}.$$



而且，有不少定积分的应用 <span class="emphasize"> 超乎你的想象</span>。

>[!example] 例题
>(1) 设 $\displaystyle a_n = 1 + \frac{1}{\sqrt{2}} + \frac{1}{\sqrt{3}} + \cdots + \frac{1}{\sqrt{n}} - 2\sqrt{n}$。证明：数列 $\{a_n\}$ 收敛；
>(2) 求极限 $\displaystyle \lim_{n \to \infty} \frac{1}{\sqrt{n}} \left( \frac{1}{\sqrt{n+1}} + \frac{1}{\sqrt{n+2}} + \cdots + \frac{1}{\sqrt{2n}} \right)$。

>[!solution] 解析
>（1）证明：
>考虑数列的单调性，有 $$a_{n+1}-a_n=\frac{1}{\sqrt{n+1}} - 2\sqrt{n+1} + 2\sqrt{n} = \frac{1}{\sqrt{n+1}} - 2(\sqrt{n+1} - \sqrt{n}),$$由于$\displaystyle\sqrt{n+1} - \sqrt{n} = \frac{1}{\sqrt{n+1} + \sqrt{n}}\gt\frac{1}{2\sqrt{n+1}},$ 所以$$a_{n+1} - a_n = \frac{1}{\sqrt{n+1}} - \frac{2}{\sqrt{n+1} + \sqrt{n}}\lt0,$$即数列 $\{a_n\}$ 单调递减。
>另一方面，利用定积分进行估计：$$2\sqrt n-2=\int_1^n \frac{1}{\sqrt{x}} \mathrm dx < \sum_{k=1}^n \frac{1}{\sqrt{k}} < 1 + \int_1^n \frac{1}{\sqrt{x}} \mathrm dx=2\sqrt n-1,$$
>所以 $-2\lt a_n\lt -1.$于是 $\{a_n\}$ 单调递减有下界，故数列收敛。
>（2）
>**解1：**
>$\displaystyle a_{2n}-a_n=\frac{1}{\sqrt{n+1}} + \frac{1}{\sqrt{n+2}} + \cdots + \frac{1}{\sqrt{2n}}+2(\sqrt{2n}-\sqrt n),$ 故 $$\frac{a_{2n}-a_n}{\sqrt n}=\frac{1}{\sqrt{n}} \left( \frac{1}{\sqrt{n+1}} + \frac{1}{\sqrt{n+2}} + \cdots + \frac{1}{\sqrt{2n}} \right)-2(\sqrt2-1).$$因为 $\{a_n\}$ 收敛，所以 $\displaystyle\lim_{n\to\infty}(a_{2n}-a_n)=0$，故$$\displaystyle \lim_{n \to \infty} \frac{1}{\sqrt{n}} \left( \frac{1}{\sqrt{n+1}} + \frac{1}{\sqrt{n+2}} + \cdots + \frac{1}{\sqrt{2n}} \right)=2(\sqrt2-1).$$
>**解2：**
>利用定积分的定义：
>$$\begin{aligned}
\lim_{n \to \infty} &\frac{1}{\sqrt{n}} \left( \frac{1}{\sqrt{n+1}} + \frac{1}{\sqrt{n+2}} + \cdots + \frac{1}{\sqrt{2n}} \right) \\
&= \lim_{n \to \infty} \frac{1}{n} \left( \frac{1}{\sqrt{1+\frac{1}{n}}} + \frac{1}{\sqrt{1+\frac{2}{n}}} + \cdots + \frac{1}{\sqrt{1+\frac{n}{n}}} \right)\\
&= \int_0^1 \frac{1}{\sqrt{1+x}} \mathrm dx \\
&= 2\sqrt{1+x} \bigg|_0^1 \\
&= 2\sqrt{2} - 2.
>\end{aligned}$$
>故所求极限为 $2\sqrt{2} - 2$。

>[!summary] 题后总结
>这道题相当地难！如果没有见过类似的题目，根本想不到第一问要用单调有界定理，第二问要用第一问的数列作差。当然为了呼应这次的标题，我们也提供了用定积分定义的解决方法。
>这道题的渊源是什么呢？这是一道工科数分的题，我怀疑工科数分和真正的数分用的教材是类似的，因为这道题和下面这道题很像，而下面的题是数分教材里的经典例题……
>>[!example] 补充例题
>>记 $\displaystyle b_n=1+\frac{1}{2}+\cdots+\frac{1}{n}-\ln n,$ 求证 $\{b_n\}$ 收敛。并利用这个结果证明 $\displaystyle\ln2=\lim_{n\to\infty}\left(\frac{1}{n+1}+\frac{1}{n+2}+\cdots+\frac{1}{2n}\right).$
>
>除了有界性，证明方法和上面如出一辙！所以第一问不要求大家完全掌握，了解为主；但第二问的解2需要掌握，这是利用定积分定义的经典题目。

%%不知道该放在哪的题
另外，此题解析等所有说明都不要删除，保留一种探索感%%

>[!example] 例题
>已知函数 $f(x), g(x)$ 在闭区间 $[a, b]$ 上连续，且 $f(x) > 0$，则极限 $\displaystyle \lim_{n \to \infty} \int_a^b g(x) \sqrt[n]{f(x)}\mathrm dx$ 的值为$\underline{\qquad}.$

>[!solution] 解析（？）
>由于 $f(x)$ 在 $[a,b]$ 上连续，由最值定理，存在 $m,M>0$，使得 $m\leqslant f(x)\leqslant M,$ 故$$\sqrt[n]{m} \int_a^b g(x)\mathrm dx \leqslant \int_a^b g(x) \sqrt[n]{f(x)}\mathrm dx \leqslant \sqrt[n]{M} \int_a^b g(x)\mathrm dx.$$又有 $\displaystyle \lim_{n \to \infty} \sqrt[n]{m} = \lim_{n \to \infty} \sqrt[n]{M} = 1$，所以由夹逼定理知$$\lim_{n \to \infty} \int_a^b g(x) \sqrt[n]{f(x)}\mathrm dx = \int_a^b g(x)\mathrm dx.$$

>[!summary] 题后反思
>这道题很妙，妙在想到用夹逼定理。但是这是怎么想到的呢？
>我们观察一下极限的形式：有一个开 $n$ 次根号。这会让我们想到这样一个极限：$$\lim_{n\to\infty}\sqrt[n]a=1,a\gt0.$$从而可以用放缩和夹逼定理做出这道题……吗？
>不对，我们再看一下这个不等式：$$\sqrt[n]{m} \int_a^b g(x)\mathrm dx \leqslant \int_a^b g(x) \sqrt[n]{f(x)}\mathrm dx \leqslant \sqrt[n]{M} \int_a^b g(x)\mathrm dx,$$它真的成立吗？并不，题中没有给出 $g(x)\gt0$ 的条件，甚至连 $g(x)$ 保持同号的条件都没有，所以并不成立。那么应该怎么做呢？下面给出一种思路。

>[!done] 正解 
>仍然利用 $f(x)$ 的最值和这个极限 $\lim\limits_{n\to\infty}\sqrt[n]a=1,a\gt0.$ 
>考虑差$\displaystyle\int_a^bg(x)\sqrt[n]{f(x)}\text dx-\int_a^bg(x)\text dx=\int_a^bg(x)(\sqrt[n]{f(x)}-1)\text dx.$
>由于我们不清楚 $g(x)$ 的符号，所以考虑绝对值 $$\int_a^b|g(x)(\sqrt[n]{f(x)}-1)|\text dx.$$由于 $g(x)$ 在 $[a,b]$ 上连续，所以它必定有界，即存在正数 $G\gt0$，使得 $|g(x)|\leqslant G,$ 故$$0\leqslant\int_a^b|g(x)(\sqrt[n]{f(x)}-1)|\text dx\leqslant G\int_a^b|\sqrt[n]{f(x)}-1|\text dx.$$由于 $\displaystyle\sqrt[n]m-1\leqslant \sqrt[n]{f(x)}-1\leqslant\sqrt[n]M-1,$ 所以 $\displaystyle\lim_{n\to\infty}\sqrt[n]{f(x)}-1=0,$ 从而 $\displaystyle\lim_{n\to\infty}|\sqrt[n]{f(x)}-1|=0,$ 故$$\displaystyle\lim_{n\to\infty}\int_a^bG|\sqrt[n]{f(x)}-1|=0\qquad(*),$$由夹逼定理知$$\int_a^b|g(x)(\sqrt[n]{f(x)}-1)|\text dx=0,$$故$$\lim_{n \to \infty} \int_a^b g(x) \sqrt[n]{f(x)}\mathrm dx = \int_a^b g(x)\mathrm dx.$$

>[!summary] 题后总结
>上述方法是怎么想到的呢？其实，我先用画图软件大致确定了答案应该是 $\displaystyle\int_a^bg(x)\text dx,$ 然后想：不知道符号的处理办法应该是加绝对值。但是加绝对值会有这样一个问题：$\displaystyle\lim f(x)=a\Rightarrow \lim |f(x)|=|a|,$ 但 $\displaystyle\lim |f(x)|=|a|\nRightarrow \lim f(x)=a$。但有一种特殊情况：<span style='color: blue'>如果</span> $\color{blue}a=0,$ <span style='color: blue'>那么反过来也是成立的</span>。所以可以考虑被积函数和结果式子的差，这样就可以让极限值为 $0$，从而可以得出结论了。
>其实上面的证明还有点小瑕疵，就是 $(*)$ 处。里面的极限等于零真的可以推出积分的极限等于零吗？确实是可以的，但这是有条件的。我们先给出这道题可以这么做的证明，再说条件是什么。
>>[!note] 补充证明
>>由于 $f(x)$ 是连续的，所以 $\sqrt[n]{f(x)}-1$ 也是连续的，从而由积分中值定理可知，存在 $\xi\in(a,b),$ 使得 $\displaystyle \int_a^b\sqrt[n]{f(x)}-1\text dx=\sqrt[n]{f(\xi)}-1\to0\,(n\to\infty).$ 
>
>实际上，只有函数“一致连续”才能得出极限和积分号可以互换的结论；就上面这道题而言，就是我们可以先求 $\lim\limits_{n\to\infty}(\sqrt[n]f(x)-1)$ 再求这个积分。有兴趣的可以自行去了解一致连续是什么意思。实际上，在闭区间上一致连续和连续是等价的，所以这里可以这样做。
>有趣的是，这道题的第一个解析是原卷的解析，也就是说，出卷老师也没有意识到这个地方不能用夹逼定理。大家不能忘记夹逼定理的方法，但是也要注意具体情形下到底能不能用夹逼定理，<span style='color: blue'>这个不等式究竟是否成立</span>。

定积分的大坑主要是换元时要换上下限。
>[!warning] 注意！
>单纯把 $f'(x)\mathrm dx$ 换成 $\mathrm df(x)$ 不需要改变上下限，因为后者也是在对 $x$ 求积分，此时上下限仍然针对 $x$；当你使用<span class="danger">全新的变量</span>，如令 $t=f(x)$，且你决定设置 $t$ 为新积分变量而非单纯的关于 $x$ 的函数时，你必须更换成新的上下限。
>即：上下限是根据变量设置的，而非仅仅根据微分算子后面的表达式

而不定积分的大坑就是换元之后要记得再还原。
>[!warning] 注意！
>不定积分和定积分的换元法是相当类似的，但也并非完全一样。定积分只要考虑积分上下限就可以了，因为定积分的结果和积分变量无关，只与函数本身和上下限有关；但不定积分最后得出的表达式<span class="danger">和积分变量是有关的</span>，不同的变量不定积分就是不一样。所以一定要记得把换过去的变量再换回来！


>[!bug] 请自行补充你自己容易犯错的点

<br><br><br><br><br><br><br><br><br><br><br>

# Extra. 常用积分公式速记
 
### 一、三角函数积分

 $\displaystyle\int \sin^2 x\mathrm dx = \frac{x}{2} - \frac{\sin 2x}{4} + C$ 
 $\displaystyle\int \cos^2 x\mathrm dx = \frac{x}{2} + \frac{\sin 2x}{4} + C$ 
### 二、反三角函数积分
 $\displaystyle\int \arcsin x\mathrm dx = x\arcsin x + \sqrt{1-x^2} + C$ 
 $\displaystyle\int \arccos x\mathrm dx = x\arccos x - \sqrt{1-x^2} + C$ 
 $\displaystyle\int \arctan x\mathrm dx = x\arctan x - \frac{1}{2}\ln(1+x^2) + C$ 
 $\displaystyle\int \text{arccot } x\mathrm dx = x\text{arccot } x + \frac{1}{2}\ln(1+x^2) + C$ 
### 三、含根式的积分（ a>0 ）
 $\displaystyle\int \frac{1}{\sqrt{a^2 - x^2}}\mathrm dx = \arcsin\frac{x}{a} + C$ 
 $\displaystyle\int \frac{1}{\sqrt{x^2 + a^2}}\mathrm dx = \ln\left(x + \sqrt{x^2 + a^2}\right) + C$ 
 $\displaystyle\int \frac{1}{\sqrt{x^2 - a^2}}\mathrm dx = \ln\left|x + \sqrt{x^2 - a^2}\right| + C$ 
 $\displaystyle\int \sqrt{a^2 - x^2}\mathrm dx = \frac{x}{2}\sqrt{a^2 - x^2} + \frac{a^2}{2}\arcsin\frac{x}{a} + C$ 
 $\displaystyle\int \sqrt{x^2 + a^2}\mathrm dx = \frac{x}{2}\sqrt{x^2 + a^2} + \frac{a^2}{2}\ln\left(x + \sqrt{x^2 + a^2}\right) + C$ 
 $\displaystyle\int \sqrt{x^2 - a^2}\mathrm dx = \frac{x}{2}\sqrt{x^2 - a^2} - \frac{a^2}{2}\ln\left|x + \sqrt{x^2 - a^2}\right| + C$ 
### 四、含分式的积分（ $a\neq0$ ）
 $\displaystyle\int \frac{1}{x^2 + a^2}\mathrm dx = \frac{1}{a}\arctan\frac{x}{a} + C$ 
 $\displaystyle\int \frac{1}{x^2 - a^2}\mathrm dx = \frac{1}{2a}\ln\left|\frac{x - a}{x + a}\right| + C$ 
 $\displaystyle\int \frac{1}{ax + b}\mathrm dx = \frac{1}{a}\ln|ax + b| + C$ 
### 五、指数与对数结合积分
 $\displaystyle\int x e^x\mathrm dx = (x-1)e^x + C$ 
$\displaystyle\int x \ln x\mathrm dx = \frac{x^2}{2}\ln x - \frac{x^2}{4} + C$ 
 $\displaystyle\int e^x \sin x\mathrm dx = \frac{e^x}{2}(\sin x - \cos x) + C$ 
 $\displaystyle\int e^x \cos x\mathrm dx = \frac{e^x}{2}(\sin x + \cos x) + C$ 
### 六、常用凑微分积分
 $\displaystyle\int \frac{1}{\sqrt{1 - x^2}}\mathrm dx = \arcsin x + C = -\arccos x + C$ 
 $\displaystyle\int \frac{1}{1 + x^2}\mathrm dx = \arctan x + C = -\text{arccot } x + C$ 
 $\displaystyle\int \frac{1}{x\ln x}\mathrm dx = \ln|\ln x| + C$ 
 $\displaystyle\int \frac{e^{\sqrt{x}}}{\sqrt{x}}\mathrm dx = 2e^{\sqrt{x}} + C$ 
 $\displaystyle\int \frac{\sin\sqrt{x}}{\sqrt{x}}\mathrm dx = -2\cos\sqrt{x} + C$ 
>[!abstract] 练习
>尝试推导上述公式

# Trivia
魔法六边形
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

![[谏学高数者十思疏]]