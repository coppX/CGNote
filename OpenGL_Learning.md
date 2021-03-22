## 实现直线算法

![image-20210322173348545](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210322173348545.png)

​		假想屏幕就是个二维n个单元格组成的

​		如图6.6所示一样任意一条直线，都有决策参数P，由图6.7中的dlower - dupper获得，负数则代表渲染的是是yk单元格，反之则是渲染yk+1的单元格。当直线斜率绝对值小于1的适合以x轴作为延伸进行单元格的分析渲染，当斜率绝对值大于1的时候则以y轴进行。

## 实现圆的算法

![image-20210322181429314](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210322181429314.png)

![image-20210322181039992](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210322181039992.png)

​		圆的算法实现是计算在圆弧斜率在0到-1之间1/8圆，然后通过对称获得整个圆。

​		类似直线的决策参数，圆也有自己的决策参数P=(xk+1)²+(yk-1/2)² - r²，yk-1/2就是图6.14中的中点，通过判断中点是否在圆内来决定是渲染yk-1还是yk，该方法的前提就是圆弧斜率在0到-1之间，只有在这区间内可以沿x轴进行分析渲染。至于为什么是沿x轴分析是因为在该区间内△x的值大于△y，误差会比较小。

## 实现椭圆的算法

![image-20210322184322534](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210322184322534.png)![image-20210322184337627](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210322184337627.png)

![image-20210322182406947](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210322182406947.png)

​		实现椭圆的算法和实现圆的算法大致相同，区别在于在第一象限不能直接对称获得，所以在第一象限内需要对圆弧进行两部分的计算渲染。在第一象限计算完之后进行对称来获取完整的椭圆。

​		第一部分的计算就和圆一样是取圆弧斜率在0到-1之间，首先Rx为短半轴，Ry为长半轴，根据椭圆的公式可以知道椭圆的决策参数P=Ry²（xk+1）²+Rx²（Yk-1/2）² - Rx²Ry²，决策参数P就如图6.21中的中点，P在圆内就是则渲染Yk否则渲染Yk-1。

​		第二部分的计算则是圆弧斜率在-1到无穷小之间如图6.22，这时△y大于△x，所以这部分对y轴进行延伸分析，根据决策参数P是否大于0来决定是渲染Xk还是Xk+1。