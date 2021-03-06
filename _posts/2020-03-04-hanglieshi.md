---
layout:     post                    # 使用的布局（不需要改）
title:      "线性代数（行列式篇）"               # 标题 
subtitle:   "I love study" #副标题
date:       2020-03-05              # 时间
author:     "Nice_try"                      # 作者
header-img: "img/blog04.jpg"    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - blog
    - 线性代数
---

## 行列式

**易错点**  

 - 对角线法则仅适用于二阶，三阶行列式  
 - 行列式任一行（列）的元素与另一行（列）的对应元素的 代数余子式乘积之和等于零   

**知识点**   
*余子式：* Mij表示划掉aij所在的第i行和第j列之后所形成的低一阶行列式  

*代数余子式：* Aij=(-1)^(i+j)*Mij  

*转置：* 行列式转置后值不变-->行列式中行和列式对称的 对行成立的性质对列也成立  

*换行(列)：* 行列式的两行（列）交换位置后 值变号--->若行列式中有相同的两行(列)，则行列式的值为0  

*数乘：* 用数k乘行列式某一行中的所有元素等于用k乘此行列式-->可以提取某一行(列)的公因子到行列式外  

*加取：* 行列式某一行(列)元素加上另一行(列)对应元素的k倍，行列式的值不变  

*拆分：* 若行列式某一行(列)的元素式两个数之和，则行列式可拆成两个行列式的和----->若行列式某一行(列)的元素都是m个元素的和，则行列式可以写成m个行列式的和------>**尽量不要尝试一次拆分多行(列)**

*展开：* 行列式等于它的任一行（列）的各元素 与其对应的代数余子式乘积之和------>行列式任一行（列）的元素与另一行（列）的对应元素的 代数余子式乘积之和等于零
![展开](https://img-blog.csdnimg.cn/20200303215008833.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303215031197.png)

**技巧**

 - 将行列式按行（列）展开时优先展开含0较多的行（列）减小计算量
 - ![对角行列式](https://img-blog.csdnimg.cn/20200303212155352.png)对角行列式的值为a11*a22*……*ann
 - ![下三角行列式](https://img-blog.csdnimg.cn/20200303212337205.png)下（上）三角行列式的值为a11*a22*……*ann
 - ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303212454943.png)斜三角行列式的值为![行列式的值](https://img-blog.csdnimg.cn/20200303212606219.png)
 - ![在这里插入图片描述](https://img-blog.csdnimg.cn/202003032128298.png)其转置行列式为![转置](https://img-blog.csdnimg.cn/20200303212858895.png)
 - ![模板题目](https://img-blog.csdnimg.cn/20200303214202396.png)各行(列)元素和相等的行列式![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303220645112.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303214308451.png)形如这样格式的行列式值为：![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303214352517.png)
 - 反对称行列式，就是主对角线两侧元素关于主对角线反对称，且主对角线元素为0。![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303215437541.png)对于奇数阶反对称行列式，其值为0。需要提醒一点的是，对称行列式的主对角线元素不需要一定为0！
 - 分块处理![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303215647749.png)
 - 箭形行列式![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303220138406.png)
 - 两三角行列式![在这里插入图片描述](https://img-blog.csdnimg.cn/2020030322021761.png)
 - 两条线行行列式![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303220441451.png)
 - 三对角行列式![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303220601396.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pSTkFfXw==,size_16,color_FFFFFF,t_70)
 - 相邻两行(列)对应元素相差1的行列式![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303220855760.png)
 - 范德蒙德行列式![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303220938501.png)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303221008663.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pSTkFfXw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303221018666.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pSTkFfXw==,size_16,color_FFFFFF,t_70)
 - ![List item](https://img-blog.csdnimg.cn/20200303221321706.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pSTkFfXw==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200303221333161.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pSTkFfXw==,size_16,color_FFFFFF,t_70)

