## 1 常用坐标轴系以及变换（欧美）

### 1地面坐标系$S_g$

$O_g$：坐标原点，地面任意一点

$X_g$：水平面内任意方向

$Z_g$：垂直于地面，指向地心。

$Y_g$：右手定则，在水平面内垂直于X轴。

### 2机体坐标系$S_b$

$O_b$：坐标原点，位于飞机质心位置。

$X_b$：指向飞机机头方向

$Z_b$：飞机对称面内，垂直于X轴向下。

$Y_b$：右手定则，垂直于$X_bZ_b$指向飞机右侧，右机翼。

### 3气流坐标系$S_a$

$O_a$：坐标原点，飞机的质心位置。

$X_a$：与飞机的速度方向重合。

$Z_a$：在飞机的对称面内，垂直于X轴，指向下方。

$Y_a$：右手定则，垂直于XZ指向飞机右侧。

### 4 稳定坐标系$S_s$

$O_s$：坐标原点，飞机的质心位置。

$X_s$：与飞机速度V在飞机对称面的投影重合。

$Z_s$：在飞机对称面内，与X垂直，指向下方。与$Z_a$轴一致。

$Y_s$：与$Y_b$一致。（由于$X_s$和$Z_s$均在飞机对称面内，故$Y_s$必定和$Y_b$重合）

### 5航迹坐标系$S_k$

$O_k$：坐标原点，飞机的质心位置

$X_k$：与飞机的速度方向重合一致，即与$X_a$重合。

$Z_k$：在飞机速度方向的铅锤面内，与X轴垂直，指向下方。

$Y_k$：右手定则。垂直于$XZ$。

### 6计算坐标系$S_c$

CFD计算过程中使用的坐标轴系。

$O_c$：机身顶点（也可以调整到飞机质心位置）

$X_c$：沿机身轴线指向后方。

$Y_c$：垂直于飞机对称面，指向右方

$Z_c$：在飞机对称面内，垂直于X，指向上方。右手定则。

## 2坐标轴系之间的关系

### 1气流坐标系与机体坐标系(气流角/气动角)

侧滑角$\beta$：飞行速度方向与飞机对称面的夹角，速度方向如果在对称面右侧，则为正。$-90^\circ\leq\beta\leq90^\circ$。当时$\beta=0^\circ$，气流坐标系$S_a$和稳定坐标系$S_s$重合。

迎角$\alpha$：飞行速度方向在飞机对称面的投影与$OX_b$轴的夹角，速度方向如果在$OX_b$下方，则为正。$-\pi\leq\alpha\leq\pi$

### 2机体坐标系和地面坐标系(姿态角，通常所指的欧拉角)

机体坐标系相对与地面坐标系的方位，飞行器在空中的姿态，用三个欧拉角表示。

偏航角$\psi$$：$$OX_b$$在水平面$$OX_gY_g$$上的投影与$$OX_g$之间的夹角。飞机右偏航时形成的角度为正。$-\pi\leq\psi\leq\pi$

俯仰角$\theta$：机体轴$OX_b$与水平面$OX_gY_g$之间的夹角。飞机头部向上则为正。$-\pi/2\leq\theta\leq\pi/2$

滚转角（倾斜角）$\phi$:飞机对称面与包含$OX_b$轴的铅锤面之间的夹角。飞机右滚形成的角度为正。$-\pi\leq\phi\leq\pi$

### 3航迹坐标系和地面坐标系

航迹（轨迹）偏角，航向角：航迹轴$OX_k$在水平面$OX_gY_g$上的投影与$OX_g$的夹角，航迹向右偏转时为正。

航迹（轨迹）倾角，爬升角：航迹轴$OX_k$与水平面$OX_gY_g$之间的夹角，航迹向上倾斜时为正。

### 4航迹坐标系和气流坐标系==????==

航迹坐标系和气流坐标系之间的相互关系，在无风的情况下，$OX_k$和$OX_w$时同轴的，故只有一个角度。

速度滚转角：飞行器对称平面$OX_bZ_b$与含有速度矢量的铅锤面之间的夹角，绕速度矢量右滚转为正。

### 5地面坐标系和气流坐标系（航迹角）==????==

气流偏航角/航迹方位角：飞行速度xa在水平面的投影与xg之间的夹角，xa投影位于xg的右侧，则为正。

气流俯仰角/航迹倾斜角：飞行速度xa与水平面的夹角，当xa在水平面上时，则为正。

气流倾斜角/航迹滚转角$\mu$：za轴与通过速度xa的铅锤面间的夹角，飞机右滚转为正。

## 3坐标变换

### 1平面坐标系各轴之间的转换

假如有两个坐标系$Ox_py_p$和$Ox_qy_q$，当坐标系$Ox_py_p$顺时针转过$\alpha$角后，将与新坐标系$Ox_qy_q$重合。则某矢量**r**在坐标系中可分别表示为$(x_p,y_p)$和$(x_q,y_q)$，如果已知矢量的坐标$(x_p,y_p)$，则可以用下式计算新坐标系$(x_q,y_q)$。
$$
x_q=x_pcos(\alpha)+y_psin(\alpha)\\

y_q=-x_psin(\alpha)+y_pcos(\alpha)
$$
写成矩阵形式：
$$
\left[
\matrix{x_q \\y_q}\right]
=
\left[\matrix{cos\ \alpha\ \ \ \ sin\ \alpha \\-sin\ \alpha\ \ \ \ cos\ \alpha}\right]
\left[\matrix{x_p \\y_p}\right]
$$
另：
$$
L_{qp}
=
\left[\matrix{cos\ \alpha\ \ \ \ sin\ \alpha \\-sin\ \alpha\ \ \ \ cos\ \alpha}\right]
$$
则$\vec r_q=\vec L_{qp}\vec r_p$

$\vec L_{qp}$为p到q的转换矩阵。

### 2三维坐标轴之间的转换

绕$z$轴旋转：
$$
\left[
\matrix{x_q \\y_q\\z_q}\right]
=
\left[\matrix{cos\ \alpha & sin\ \alpha & 0 \\-sin\ \alpha & cos\ \alpha & 0\\0 & 0 & 1}\right]
\left[\matrix{x_p \\y_p\\z_p}\right]
$$
绕$y$轴旋转：
$$
\left[
\matrix{x_q \\y_q\\z_q}\right]
=
\left[\matrix{
cos\ \alpha & 0 & -sin\ \alpha\\
0 & 1 & 0\\
sin\ \alpha & 0 & cos\ \alpha
}\right]
\left[\matrix{x_p \\y_p\\z_p}\right]
$$
绕$x$轴旋转：
$$
\left[
\matrix{x_q \\y_q\\z_q}\right]
=
\left[\matrix{
1 & 0 & 0\\
0 & cos\ \alpha & sin\ \alpha \\
0 & -sin\ \alpha & cos\ \alpha
}\right]
\left[\matrix{x_p \\y_p\\z_p}\right]
$$
一般情况下


$$
\left[\matrix{x_q \\y_q\\z_q}\right]
=\vec L_x(\xi)\vec L_y(\eta)\vec L_z(\zeta)
\left[\matrix{x_p \\y_p\\z_p}\right]
$$














