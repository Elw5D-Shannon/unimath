
矩阵打印方式

$\begin{pmatrix} 1+x_1 & 1+x_1^2 & ... &1+x_1^n \\ 1+x_2 & 1+x_2^2 & ... &1+x_2^n \\ ... \\ 1+x_n & 1+x_n^2 & ... &1+x_n^n \end{pmatrix}$

然而，我们教材上是使用的方括号矩阵，要将pmatrix换成bmatrix：

$\begin{bmatrix} 1+x_1 & 1+x_1^2 & ... &1+x_1^n \\ 1+x_2 & 1+x_2^2 & ... &1+x_2^n \\ ... \\ 1+x_n & 1+x_n^2 & ... &1+x_n^n \end{bmatrix}$

行列式的输入方法如下：(vmatrix)

$\begin{vmatrix} 1+x_1 & 1+x_1^2 & ... &1+x_1^n \\ 1+x_2 & 1+x_2^2 & ... &1+x_2^n \\ ... \\ 1+x_n & 1+x_n^2 & ... &1+x_n^n \end{vmatrix}$

求和、求积的上下记号可以使用limits套：
（小公式如此，大公式不必管）
$\sum\limits_{i=2}^{n}a_i, \prod\limits_{i=1}^{n}a_i$

积分符号的上下标，按照原本的上下标来处理：

$\int_1^5 x\mathrm{d}x$

如果像让积分符号更加好看，就在前面加上\displaystyle，如

$\displaystyle\int_1^5f(x)\text{d}x$

积分符号的上下记号，用limits套，注意高数大物教材区别：

$\displaystyle\int\limits_{L}(x+y)\mathrm{d}s$
闭曲线积分：$\oint_L\boldsymbol F\mathrm d\boldsymbol r$
$\displaystyle\oint_L\boldsymbol F\mathrm d\boldsymbol r$

二重积分： $\iint xy\mathrm dS$
从A到B的向量 $\overrightarrow{AB}$，坐标轴向量 $\hat i,\hat j,\hat k$ 或者 $\vec i,\vec j,\vec k$
你说什么？向量的0次方？ $\vec{r}^0$
~~（哦，这其实是一种上标）~~

物理量对时间的导数一般这样写（或者说牛顿的导数记法）： $\dot{\boldsymbol{r}}$ 
如果是二阶导的话就是这样的： $\ddot{\boldsymbol r}$
最高到四阶：$\ddddot{\boldsymbol r}$

梯度算子（~~那不拉算子~~）（不是拉普拉斯算子）
$$\nabla=\left(\frac{\partial}{\partial x},\frac{\partial}{\partial y},\frac{\partial}{\partial z}\right)$$
拉普拉斯算子
$$\Delta=\nabla\cdot\nabla=\frac{\partial^2}{\partial x^2}+\frac{\partial^2}{\partial y^2}+\frac{\partial^2}{\partial z^2}$$

>[!quote] Cym10x
>$\nabla\cdot\nabla$ 是不是很可爱？（逃）

下划线输入可以这样 $\underline{\qquad}$.

**颜色文字:**
$\color{red} x^2 + \color{blue} y^2 = 1$
```text
只要查一下颜色的编号放进去就可以（虽然应该用不到这么奇怪的表示方式）
$\color{red} x^2 + \color{blue} y^2 = 1$
```

常用的希腊字母
$\alpha, \beta, \gamma, \delta, \epsilon(\varepsilon),\phi(\varphi), \psi, \nu, \mu, \theta, \upsilon$
`$\alpha, \beta, \gamma, \delta, \epsilon(\varepsilon),\phi(\varphi), \psi, \nu, \mu, \theta, \upsilon$`
大写只要把首字母大写就能得到了

在括号前面加上\left 和 \right 以获得更加美观的括号（尤其在分数两边）
$(\dfrac{1}{2})$ v.s. $\left(\dfrac{1}{2}\right)$ 
`$(\dfrac{1}{2})$ v.s. $\left(\dfrac{1}{2}\right)$`

LaTeX 并不原生支持闭合曲面积分的输入，只能另想法子：
$\displaystyle\bigcirc\kern-11.5pt{\int}\kern-6.5pt{\int}$