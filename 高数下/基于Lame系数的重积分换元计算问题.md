---
tags: [数学分析, 重积分, 拉梅系数, 坐标变换]
---

# 基于拉梅系数的重积分换元

## 正交曲线坐标与拉梅系数

设坐标变换 $\mathbf{r}(q_1,q_2,q_3) = \big(x(q_i), y(q_i), z(q_i)\big)$ 的坐标曲线两两正交，则定义 **拉梅系数**（尺度因子）为
$$
h_i = \left| \frac{\partial \mathbf{r}}{\partial q_i} \right|,
$$
此时体积元与面积元可直接写出：
$$
\mathrm{d}V = h_1 h_2 h_3 \, \mathrm{d}q_1\mathrm{d}q_2\mathrm{d}q_3, \qquad
\mathrm{d}A = h_1 h_2 \, \mathrm{d}q_1\mathrm{d}q_2 .
$$
重积分换元公式简化为
$$
\iiint_V f \, \mathrm{d}x\mathrm{d}y\mathrm{d}z
= \iiint_{V'} f\big(x(q_i)\big) \, h_1 h_2 h_3 \, \mathrm{d}q_1\mathrm{d}q_2\mathrm{d}q_3 .
$$

### 常用坐标系的拉梅系数

| 坐标系 | 坐标变量 | 拉梅系数 |
|--------|----------|----------|
| 直角坐标 | $(x,y,z)$ | $h_x=h_y=h_z=1$ |
| 柱坐标 | $(\rho,\varphi,z)$ | $h_\rho=1,\; h_\varphi=\rho,\; h_z=1$ |
| 球坐标 | $(r,\theta,\varphi)$ | $h_r=1,\; h_\theta=r,\; h_\varphi=r\sin\theta$ |
| 平面极坐标 | $(\rho,\varphi)$ | $h_\rho=1,\; h_\varphi=\rho$ |

---

## 典型换元问题

> [!question]- 问题1：球坐标换元计算三重积分
> 计算三重积分
> $$ I = \iiint_{\Omega} (x^2+y^2)\,\mathrm{d}V $$
> 其中 $\Omega$ 是单位球体 $x^2+y^2+z^2 \le 1$。

> [!success]- 解答1
> 引入球坐标 $(r,\theta,\varphi)$：
> $$ x = r\sin\theta\cos\varphi,\; y = r\sin\theta\sin\varphi,\; z = r\cos\theta $$
> 拉梅系数：$h_r=1,\; h_\theta=r,\; h_\varphi=r\sin\theta$，
> 体积元 $\mathrm{d}V = r^2\sin\theta\,\mathrm{d}r\mathrm{d}\theta\mathrm{d}\varphi$。
> 
> 被积函数 $x^2+y^2 = r^2\sin^2\theta$，积分区域为 $r\in[0,1]$，$\theta\in[0,\pi]$，$\varphi\in[0,2\pi]$。
> $$
> \begin{aligned}
> I &= \int_0^{2\pi}\mathrm{d}\varphi \int_0^\pi \sin\theta\,\mathrm{d}\theta \int_0^1 (r^2\sin^2\theta)\, r^2 \,\mathrm{d}r \\
>   &= \int_0^{2\pi}\mathrm{d}\varphi \int_0^\pi \sin^3\theta\,\mathrm{d}\theta \int_0^1 r^4\,\mathrm{d}r \\
>   &= 2\pi \cdot \frac{4}{3} \cdot \frac{1}{5} = \frac{8\pi}{15}.
> \end{aligned}
> $$

> [!question]- 问题2：极坐标换元计算二重积分
> 计算二重积分
> $$ J = \iint_{D} e^{x^2+y^2}\,\mathrm{d}x\mathrm{d}y $$
> 其中 $D$ 是圆盘 $x^2+y^2 \le a^2$。

> [!success]- 解答2
> 采用平面极坐标 $(\rho,\varphi)$：
> $$ x = \rho\cos\varphi,\; y = \rho\sin\varphi $$
> 拉梅系数：$h_\rho=1,\; h_\varphi=\rho$，
> 面积元 $\mathrm{d}A = \rho\,\mathrm{d}\rho\mathrm{d}\varphi$。
> 
> 被积函数 $e^{x^2+y^2}=e^{\rho^2}$，积分区域 $\rho\in[0,a],\,\varphi\in[0,2\pi]$。
> $$
> \begin{aligned}
> J &= \int_0^{2\pi}\mathrm{d}\varphi \int_0^a e^{\rho^2}\,\rho\,\mathrm{d}\rho \\
>   &= 2\pi \cdot \left[ \frac{1}{2} e^{\rho^2} \right]_0^a \\
>   &= \pi(e^{a^2}-1).
> \end{aligned}
> $$

> [!question]- 问题3：一般曲线坐标的拉梅系数与积分
> 已知曲线坐标 $(u,v)$ 与直角坐标的变换为
> $$ x = \frac{u^2-v^2}{2},\qquad y = u v. $$
> ** (1)** 计算拉梅系数 $h_u, h_v$ 并写出面积元 $\mathrm{d}A$。  
> ** (2)** 设区域 $D$ 由 $u\in[0,1],\, v\in[0,1]$ 所确定，计算积分
> $$ K = \iint_D y \,\mathrm{d}x\mathrm{d}y. $$

> [!success]- 解答3
> **(1) 拉梅系数与面积元**
> 位置向量 $\displaystyle \mathbf{r} = \left(\frac{u^2-v^2}{2},\; u v\right)$。
> $$
> \frac{\partial \mathbf{r}}{\partial u} = (u,\; v),\qquad
> \frac{\partial \mathbf{r}}{\partial v} = (-v,\; u).
> $$
> 二者内积为 $u(-v)+v u = 0$，故坐标正交。
> $$
> h_u = \sqrt{u^2+v^2},\qquad h_v = \sqrt{(-v)^2+u^2} = \sqrt{u^2+v^2}.
> $$
> 面积元
> $$ \mathrm{d}A = h_u h_v \,\mathrm{d}u\mathrm{d}v = (u^2+v^2)\,\mathrm{d}u\mathrm{d}v. $$
> 
> **(2) 计算积分**
> 被积函数 $y = uv$，积分区域为矩形 $[0,1]\times[0,1]$。
> $$
> \begin{aligned}
> K &= \int_0^1 \int_0^1 (u v) \cdot (u^2+v^2) \,\mathrm{d}u\mathrm{d}v \\
>   &= \int_0^1 \int_0^1 (u^3 v + u v^3) \,\mathrm{d}u\mathrm{d}v \\
>   &= \int_0^1 \left( \frac{v}{4} + \frac{v^3}{2} \right) \mathrm{d}v \\
>   &= \left[ \frac{v^2}{8} + \frac{v^4}{8} \right]_0^1 = \frac{1}{4}.
> \end{aligned}
> $$

---

## 小结
在正交曲线坐标系中，**拉梅系数** 给出了局部尺度伸缩的度量。重积分换元时，只需用 $h_1h_2h_3$ 替代雅可比行列式的绝对值，既直观又不易出错。

