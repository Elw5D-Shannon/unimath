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
1. （对定积分：）靠奇函数来消项；通过拆分上下限来简化可能性(?)
2. （对有理式：）有理式的拆解
>[!Bug] 待补充
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

>[!done] 你应当结合 $\sin^2x+\cos^2x=1$ 和 $\tan^2x+1=\sec^2x$ 来辅助记忆，并强化运用能力

>[!example] 例题2.
>求不定积分 $\displaystyle\int\frac{\mathrm dx}{\sqrt{x^2+a^2}} \quad (a>0)$

>[!note] 解析
>令 $x = a\tan t$ ，则$\mathrm dx = a\sec^2 t\mathrm dt$，$t \in \left(-\frac{\pi}{2},\frac{\pi}{2}\right)$，则
$\sqrt{x^2+a^2} = \sqrt{a^2\tan^2 t + a^2} = a\sec t$
>$\begin{align}\int \frac{dx}{\sqrt{x^2+a^2}} &= \int \frac{a\sec^2 t dt}{a\sec t} \\&= \int \sec t dt \\&= \ln|\sec t + \tan t| + C_1 \\&= \ln\left|\frac{\sqrt{x^2+a^2}}{a} + \frac{x}{a}\right| + C_1 \\&= \ln\left|x + \sqrt{x^2+a^2}\right| + C\end{align}$
#### 3. 有理式
>[!example] 例2.
>求不定积分 $\displaystyle\int\dfrac{x\mathrm dx}{(x-1)^{100}}$.

>[!note] 解析
>$\begin{align}\text{原式}&=\int\frac{(x-1)+1}{(x-1)^{100}}\mathrm d(x-1)\\&=\int\frac{\mathrm d(x-1)}{(x-1)^{99}}+\int\frac{\mathrm d(x-1)}{(x-1)^{100}}\\&=-\frac{1}{98(x-1)^{98}} - \frac{1}{99(x-1)^{99}} + C\end{align}$

>[!tip] !!!
>（等待添加，有什么想法吗？）

>[!example] 例2.
>求不定积分 $\displaystyle\int \frac{\mathrm{d}x}{\sqrt[6]{x+1} - \sqrt[3]{x+1}}$

>[!hint] 提示
>对于含有多个次数不同的根式时，换元时要换元为根指数的最小公倍数。
>若被积函数中含有 $\sqrt[n_1]{ax+b}$,$\sqrt[n_2]{ax+b}$,$\dots$,$\sqrt[n_k]{ax+b}$，可考虑代换 $t = \sqrt[n]{ax+b}$（n 为 $n_1$,$n_2$,$\dots,n_k$ 的最小公倍数）
>若被积函数中含有 $\sqrt[n_1]{\frac{ax+b}{cx+d}}$,$\sqrt[n_2]{\frac{ax+b}{cx+d}}$,$\dots$,$\sqrt[n_k]{\frac{ax+b}{cx+d}}$，可考虑代换 $t = \sqrt[n]{\frac{ax+b}{cx+d}}$（n 为 $n_1$,$n_2$,$\dots$,$n_k$ 的最小公倍数）

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
令 $x=\frac1t,\mathrm dx=-\frac{1}{t^2}\mathrm dt$
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


#### 4. 连续分部积分（选学？）
>[!bug] 需要斟酌该内容是否重要。

分部积分法的推广公式就是重复使用分部积分法法则。
假设函数 $u,v$ 有 $n+1$ 阶连续导数，则：$\int u v^{(n+1)}\mathrm dx = \int u\mathrm d v^{(n)} = u v^{(n)} - \int v^{(n)}\mathrm du = u v^{(n)} - \int u' v^{(n)}\mathrm dx$
我们还可以继续把 $\int u' v^{(n)}\mathrm dx$ 撕开：$\int u v^{(n+1)} dx = u v^{(n)} - u' v^{(n-1)} + u'' v^{(n-2)} - \dots + (-1)^n u^{(n)} v + (-1)^{n+1} \int u^{(n+1)} v dx$
如果被积函数的因式之一是多项式，且次数较高的时候，这个公式特别方便。通常来说，取 $u$ 为该多项式。
>[!todo] 示例
>$\int (2x^3 + 3x^2 + 4x + 5)\mathrm e^x\mathrm dx$
>我们可以令 $u=2x^3 + 3x^2 + 4x + 5$，$v=\mathrm e^x$
>$u' = 6x^2 + 6x + 4,\quad u'' = 12x + 6,\quad u''' = 12$
>于是$\begin{align*}\int (2x^3 + 3x^2 + 4x + 5) e^x dx &= (2x^3 + 3x^2 + 4x + 5)e^x - (6x^2 + 6x + 4)e^x + (12x + 6)e^x - 12e^x + C \\&= (2x^3 - 3x^2 + 10x - 5)e^x + C\end{align*}$
>
# Section 4  变限积分

# Section 5  与积分相关的不等式证明
# Extra. 常用积分公式速记
### 一、基本初等函数积分
$\int 0 \, \mathrm dx =C$
 $\int k \, \mathrm dx = kx + C$ （ k  为常数）
 $\int x^\mu \, \mathrm {d}x = \frac{x^{\mu+1}}{\mu+1} + C$ （ $\mu \neq -1$ ）
 $\int \sqrt{x} \mathrm {d}x = \frac{2}{3}x^{\frac{3}{2}} + C$
 $\int \frac{1}{x} \, \mathrm {d}x = \ln|x| + C$ 
$\int a^x \, \mathrm {d}x = \frac{a^x}{\ln a} + C$ （ $a>0,a\neq1$ ）
 $\int e^x \, \mathrm {d}x = e^x + C$ 
### 二、三角函数积分
 $\int \sin x \, \mathrm {d}x = -\cos x + C$ 
 $\int \cos x \, \mathrm {d}x = \sin x + C$ 
 $\int \tan x \, \mathrm {d}x = -\ln|\cos x| + C$
 $\int \cot x \, \mathrm {d}x = \ln|\sin x| + C$
 $\int \sec x \, \mathrm {d}x = \ln|\sec x + \tan x| + C$ 
 $\int \csc x \, \mathrm {d}x = \ln|\csc x - \cot x| + C$ 
 $\int \sec^2 x \, \mathrm {d}x = \tan x + C$ 
 $\int \csc^2 x \, \mathrm {d}x = -\cot x + C$ 
 $\int \sec x \tan x \, \mathrm {d}x = \sec x + C$ 
 $\int \csc x \cot x \, \mathrm {d}x = -\csc x + C$ 
 $\int \sin^2 x \, \mathrm {d}x = \frac{x}{2} - \frac{\sin 2x}{4} + C$ 
 $\int \cos^2 x \, \mathrm {d}x = \frac{x}{2} + \frac{\sin 2x}{4} + C$ 
### 三、反三角函数积分
 $\int \arcsin x \, \mathrm {d}x = x\arcsin x + \sqrt{1-x^2} + C$ 
 $\int \arccos x \, \mathrm {d}x = x\arccos x - \sqrt{1-x^2} + C$ 
 $\int \arctan x \, \mathrm {d}x = x\arctan x - \frac{1}{2}\ln(1+x^2) + C$ 
 $\int \text{arccot } x \, \mathrm {d}x = x\text{arccot } x + \frac{1}{2}\ln(1+x^2) + C$ 
### 四、含根式的积分（ $a>0$ ）
 $\int \frac{1}{\sqrt{a^2 - x^2}} \, \mathrm {d}x = \arcsin\frac{x}{a} + C$ 
 $\int \frac{1}{\sqrt{x^2 + a^2}} \, \mathrm {d}x = \ln\left(x + \sqrt{x^2 + a^2}\right) + C$ 
 $\int \frac{1}{\sqrt{x^2 - a^2}} \, \mathrm {d}x = \ln\left|x + \sqrt{x^2 - a^2}\right| + C$ 
 $\int \sqrt{a^2 - x^2} \, \mathrm {d}x = \frac{x}{2}\sqrt{a^2 - x^2} + \frac{a^2}{2}\arcsin\frac{x}{a} + C$ 
 $\int \sqrt{x^2 + a^2} \, \mathrm {d}x = \frac{x}{2}\sqrt{x^2 + a^2} + \frac{a^2}{2}\ln\left(x + \sqrt{x^2 + a^2}\right) + C$ 
 $\int \sqrt{x^2 - a^2} \, \mathrm {d}x = \frac{x}{2}\sqrt{x^2 - a^2} - \frac{a^2}{2}\ln\left|x + \sqrt{x^2 - a^2}\right| + C$ 
### 五、含分式的积分（ $a\neq0$ ）
 $\int \frac{1}{x^2 + a^2} \, \mathrm {d}x = \frac{1}{a}\arctan\frac{x}{a} + C$ 
 $\int \frac{1}{x^2 - a^2} \, \mathrm {d}x = \frac{1}{2a}\ln\left|\frac{x - a}{x + a}\right| + C$ 
 $\int \frac{1}{ax + b} \, \mathrm {d}x = \frac{1}{a}\ln|ax + b| + C$ 
### 六、指数与对数结合积分
 $\int x e^x \, \mathrm {d}x = (x-1)e^x + C$ 
$\int x \ln x \, \mathrm {d}x = \frac{x^2}{2}\ln x - \frac{x^2}{4} + C$ 
 $\int e^x \sin x \, \mathrm {d}x = \frac{e^x}{2}(\sin x - \cos x) + C$ 
 $\int e^x \cos x \, \mathrm {d}x = \frac{e^x}{2}(\sin x + \cos x) + C$ 
### 七、常用凑微分积分
 $\int \frac{1}{\sqrt{1 - x^2}} \, \mathrm {d}x = \arcsin x + C = -\arccos x + C$ 
 $\int \frac{1}{1 + x^2} \, \mathrm {d}x = \arctan x + C = -\text{arccot } x + C$ 
 $\int \frac{1}{x\ln x} \, \mathrm {d}x = \ln|\ln x| + C$ 
 $\int \frac{e^{\sqrt{x}}}{\sqrt{x}} \, \mathrm {d}x = 2e^{\sqrt{x}} + C$ 
 $\int \frac{\sin\sqrt{x}}{\sqrt{x}} \, \mathrm {d}x = -2\cos\sqrt{x} + C$ 
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
