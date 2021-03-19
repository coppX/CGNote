Bidirectional Reflectance Distribution Function/双向反射分布函数  
BRDF是计算机图形学中最核心的概念之一，他描述的是物体表面将光能从任何一个入射放心反射到任何一个视点方向的反射特性，即入射光线经过某个表面反射后如何在各个出射方向上分布。BRDF模型是绝大多数图形算法中描述光反射现象的基本模型
## 数学基础
### 1.1球面坐标Spherical Coordinate
![](./1.1.png)
其中:
- r表示向量的长度
- $\theta$表示向量和Z轴的夹角
- $\psi$表示向量在x-y平面上的投影和x轴的逆时针夹角。
### 2.2立体角Solid Angle
![](./1.2.jpeg)
我们知道弧度是度量二维角度的量，等于角度在单元圆上对应的弧长，单位圆的周长是2π，所以整个圆对应的弧度也就是2π。立体角则是三维角度的度量，用符合Ω表示，单位为立体弧度(也叫球面度，Steradian，简写为sr)，等于立体角在单位球面上对应的区域的面积(实际上也就是在任意半径的球上除以半径的平方ω=s/(r^2))，单位球的表面积是4π，所以整个球面的立体角也是4π  
![](./1.3.jpeg)  
立体角ω有如下微分形式:  
$d\omega=\frac{dA}{r^2}$  
其中dA为面积片元。而面积微元dA在球面坐标系下可以写成:  
$dA=(rd\theta)(rsin\theta d\psi)=r^2sin\theta d\theta d\psi$  
因此:  
$d\omega=\frac{dA}{r^2}=sin\theta d\theta d\psi$

### 2.3投影面积Foreshortened Area
投影面积描述了一个屋里表面的微小区域在某个视线上的可见面积。  
对于面积微元A，则沿着与法线夹角为$\theta$方向的A的可见面积为:  
$Area=Acos\theta$  
![](./1.4.jpeg)
