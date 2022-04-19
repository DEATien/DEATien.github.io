# Deatool模型介绍

:(fas fa-bolt):  本文将带您快速了解不同模型的形式

### CCR模型
$$
\begin{aligned}
\min & \theta_0\\\\
s.t. & \sum_{j=1}^{n} \lambda_{j} x_{i j} \leq \theta x_{i 0} \\\\
& \sum_{j=1}^{n} \lambda_{j} y_{r j} \geq y_{r 0} \\\\
& \lambda_j \geq 0 \\\\
& i=1,2 \ldots, m ; r=1,2 \ldots, q ; j=1,2 \ldots, n
\end{aligned}
$$

### BCC模型
$$
\begin{aligned}
\min & \theta_0 \\\\
s.t. & \sum_{j=1}^{n} \lambda_{j} x_{i j} \leq \theta x_{i 0} \\\\
& \sum_{j=1}^{n} \lambda_{j} y_{r j} \geq y_{r 0} \\\\
& \sum_{j=1}^{n} \lambda_{j} = 1 \\\\
& \lambda_j \geq 0 \\\\
& i=1,2 \ldots, m ; r=1,2 \ldots, q ; j=1,2 \ldots, n
\end{aligned}
$$

### SBM模型
$$
\begin{aligned}
\min & \rho=\frac{1-\frac{1}{m} \sum_{i=1}^{m} s_{i}^{-} / x_{i 0}}{1+\frac{1}{q} \sum_{r=1}^{q} s_{r}^{+} / y_{r 0}} \\\\
s.t. & \sum_{j=1}^{n} \lambda_{j} x_{i j} + s_{i}^{-} = x_{i0} \\\\
& \sum_{j=1}^{n} \lambda_{j} y_{r j} - s_{i}^{+} = y_{r0} \\\\
&\lambda, s^{-}, s^{+} \geq 0
\end{aligned}
$$
:(fas fa-book):  注：VRS假设下需要加入$\sum_{j=1}^{n} \lambda_{j} = 1$的约束条件

### undesirable-SBM模型
$$
\begin{aligned}
\min & \rho=\frac{1-\frac{1}{m} \sum_{i=1}^{m} s_{i}^{-} / x_{i 0}}{1+\frac{1}{q_{1}+q_{2}}\left(\sum_{r=1}^{q_{1}} s_{r}^{+} / y_{r 0}+\sum_{t=1}^{q_{2}} s_{t}^{u-} / u_{t 0}\right)} \\\\
s.t. & \sum_{j=1}^{n} \lambda_{j} x_{i j} + s_{i}^{-} = x_{i0} \\\\
& \sum_{j=1}^{n} \lambda_{j} y_{r j} - s_{i}^{+} = y_{r0} \\\\
& \sum_{j=1}^{n} \lambda_{j} u_{t j} + s_{u-}^{+} = u_{t0} \\\\
&\lambda, s^{-},s^{u-},s^{+} \geqslant 0
\end{aligned}
$$
:(fas fa-book):  注：VRS假设下需要加入$\sum_{j=1}^{n} \lambda_{j} = 1$的约束条件

### DDF模型
#### $(-x,y,-b)$弱可处置性$=$
$$
\begin{aligned}
\max \beta \\\\
s.t. & \sum_{j=1}^{n} \lambda_{j} x_{i j} \leq(1-\beta) x_{i0}\\\\
& \sum_{j=1}^{n} \lambda_{j} y_{r j} \geq(1+\beta) x_{r0}\\\\
& \sum_{j=1}^{n} \lambda_{j} u_{t j} =(1-\beta) u_{t0}\\\\
&\lambda \geq 0
\end{aligned}
$$
#### $(-x,y,-b)$强可处置性$\geq$
$$
\begin{aligned}
\max \beta \\\\
s.t. & \sum_{j=1}^{n} \lambda_{j} x_{i j} \leq(1-\beta) x_{i0}\\\\
& \sum_{j=1}^{n} \lambda_{j} y_{r j} \geq(1+\beta) x_{r0}\\\\
& \sum_{j=1}^{n} \lambda_{j} u_{t j} \geq(1-\beta) u_{t0}\\\\
&\lambda \geq 0
\end{aligned}
$$
#### $(-x,y,-b)$强可处置性$\leq$
$$
\begin{aligned}
\max \beta \\\\
s.t. & \sum_{j=1}^{n} \lambda_{j} x_{i j} \leq(1-\beta) x_{i0}\\\\
& \sum_{j=1}^{n} \lambda_{j} y_{r j} \geq(1+\beta) x_{r0}\\\\
& \sum_{j=1}^{n} \lambda_{j} u_{t j} \leq(1-\beta) u_{t0}\\\\
&\lambda \geq 0
\end{aligned}
$$

:(fas fa-book):  注：VRS假设下需要加入$\sum_{j=1}^{n} \lambda_{j} = 1$的约束条件

### Support or Contact
:(fas fa-comments): Wechat：:(fas fa-address-card): yomamalielie
