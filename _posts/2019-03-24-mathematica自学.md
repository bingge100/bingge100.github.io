---
layout:     post
title:      mathematica自学教程
subtitle:    Markdown tutorial
date:       2019-03-24
author:     大兵哥
header-img: img/tag-bg-o.jpg
catalog: true
tags:
    - 知识管理
    - 软件学习
comments: true
---


# mathematica自学

## mathematica功能

+ 数值计算，数值精算程序都尽量精确 ,由N（）函数控制

+ 符号计算

+ 绘图功能

+ 编程功能

## 笔记本

+ 自由格式语言输入
+ 使用样式表进行格式的调整
+ 输入技巧：alt+],自动匹配成[]

## 基本技巧

* 程序运行：shift+enter

* 终止运行：alt+空格 或者 alt+

* 帮助：？+函数名（开头大写）

* 变量的批量赋值，并且都用小写开头

* 清除变量clear[]

* 命令序列可以自动调用 %n

* 退出：alt+F4

* ;号在末尾表示不输出结果

* 查询程序包：$Packages

  

比如：

第一个程序：

![图片](/../img2/1553439310559.png)

从这个图片可以看出：

* 可以直接进行数值运算的输入
* 计算得到的结果系统尽可能用精确值表示（区别）
* 字体大小可以进行调整
* 文档结构清晰
* 随时随处插入各种对像
* 系统会自动记录输入的指令的顺序和输出结果



## 数据转换

+ $N[ ]$函数
  + N[x] 将x转换为实数形式
  + N[x，n] 将x转换为最多具n个数字精度的近似实数
  + Rationalize[x] 给出x的近似有理数
  + Rationalize[x，dx] 给出误差在dx内x的近似有理数
  + Rationalize[%]
    + % 表示上一次输出的结果
       %% 表示倒数第2次输出的结果
       %%…%(共n个) 表示倒数第n次输出的结果
       %n 表示以n为序号的那次输出结果
  + ScientificForm[表达式] 以科学记数形式输出表达式

+ 变量控制
  + 赋值：p=3
  + 擦除：clear[变量名]，或者p=.
  + 变量替换:
    + p3 = 5 - 4 y + 3 y^2 + y^3
      p3/.y -> t+1            
      p3/.y ->2 ![](/../img2/Snipaste_2019-03-25_11-41-56.png)

    + f = x^2 + x y + y^2

      f/.{x->u+1, y->v-1}

      ![](/../img2/Snipaste_2019-03-25_11-44-30.png)

+ 表（list）

  + 当表中的元素较少时，可以采用直接输入的形式：
    表变量名 = {元素1，元素2，…}​
    来生成表，即在给出表名的同时又给出了表中的元素，但在更多的时候是要利用建表函数Table、Range和Array来生成
  + 表的元素又称为表的分量，表中分量的一般表示如下：
    t[[n]]或Part[t，n] 表示表t中的第n个元素
    t[[-n]]或Part[t，-n] 表示表t中的倒数第n个元素
    First[t] 表示表t中的第一个元素
    Last[t] 表示表t中的最后一个元素
    t[{n1，n2，…}]
    或
    Part[t，n1，n2…]] 表示由表t中第n1，n2,…元素组成的表
    t[[i，j]] 表示表t中的第i个子表的第j个元素
  + 表的集合运算
    + Union[t1，t2，…]若干表之“并”，由表t1，t2，…中所有不同元素组成
    + Intersection[t1，t2，…]若干表的“交”，由表t1，t2，…中公共元素组成
    + Complement[t1，t2]表t1与表t2的“补”
      。由t1中有而t2中没有的元素

+ 局部变量和全局变量

  原因是调用f[a]后，全局变量a的值已经变为10了。使用模
  块函数可以解决这个问题，因为模块函数内定义的变量均为
  局部变量。

  模块函数的定义格式为：
  Module[{x,y...},模块体]
  Module[{x=x0,y=y0...},模块体]
  Module[{x,y...},表达式/;条件]

## 编程技巧

+ 输入/出数据文件
  (1) 输出到文件：
  Export["文件名",表]
  (2) 输入文件：
  Import["文件名"]
  (3) 显示文件内容：
  !!"文件名"
  (4) 读数据文件：
  ReadList["文件名",Number]
  ReadList["文件名",Number,RecordLists True]
  注：无Number，以"
  ，
  "作间隔；有Number以空格作间隔
+ Input[] 输入数值表达式Input[提示字符串]InputString[] 输入字符串InputString[提示字符
+ 自定义函数

$$
f\left[x_{-}\right] :=\operatorname{Exp}[x] *(\sin [x]+1)+\log \left[x^{\wedge} 2\right]
$$

​     !!fil，查看自定义函数内容

​    Save[“文件名”，自定义函数名序列f，g，h，…]

​     <<file1
​     f[1] + g[1, 2]

+ 函数迭代

  ![](/../img2/Snipaste_2019-03-25_13-04-29.png)

+ 函数嵌套

  newton3[x_] := N[1/2( x + 3/x)]
  NestList[newton3, 5.0, 4]

+ 不动点

  FixedPoint[newton3, 5.0]

+ 迭代折叠函数

  f[x_, y_] := x + y^2FoldList[f, x, {a, b, c}]

  

+ 函数运算与算子

  ![](/../img2/Snipaste_2019-03-25_13-09-56.png)

  ![Snipaste_2019-03-25_13-10-15](/../img2/Snipaste_2019-03-25_13-10-15.png)

+ 条件结构

  + $Ihs : $=x$ hs 1$/$ ;test$   当 test 为真时使用定义 rsh
  + $If [test, then, else]$  如test为真计算then，反之计算else
  + $Which [test1, valuel, test2, value2,\cdots]$  依次计算 testi，给出对应的值 vaulei
  + $Switch [expr, forml, valuel, form2, value2,\cdots]$  expr 与每一个 formi 相比较，给出相匹配的值 valuei

eg:定义分段函数
$$
f(x)=\left\{\begin{array}{cc}{x^{2}+1} & {x>0} \\ {-x^{2}-1} & {x<0} \\ {0} & {x=0}\end{array}\right.
$$
方法一：
$$
\begin{array}{l}{f[x] :=x^{\wedge} 2+1 / ; x>0} \\ {f\left[x_{-}\right] :=-x^{\wedge} 2-1 / ; x<0} \\ {f\left[x_{-}\right] :=0 / ; x==0}\end{array}
$$




方法二：
$$
f\left[x_{-}\right] :=I f\left[x>0, x^{\wedge} 2+1, I f\left[x<0,-x^{\wedge} 2-1,0\right]\right]
$$
方法三：
$$
f\left[x_{-}\right] :=\text { Which }\left[x>0, x^{\wedge} 2+1, x<0,-x^{\wedge} 2-1, x==0,0\right]
$$

## 循环结构

+ Do 结构、For 与 While 结构
  + $Do[expr,{i,imin,imax,di}] $ 循环计算 expr，步长为 di，i从 imin 增加 imax(步长缺省则默认为 1，imin 缺省也默认为 1)
  + $Do[expr,{n}] $ 循环计算 expr 共 n 次
  + $Do[expr,{i,imin,imax,di},{j,jmin,jmax,dj}] $循环计算 expr，i 从 imin 到 imax 循环，对于每个 i，j 从jmin 到 jmax 循环（即多重循环）

+ For
  + $For[start,test,incr,body] $以 start 为起始值，重复计算执行主体 body 和执行表达式incr 改变循环变量的值，直到 test 为假 
+ while结构
  + $While[test,body] ​$只要 test 为真，则重复计算执行主体 body

tips:防止死循环,break[]函数

## 绘图

+ 平面曲线表示法
  + 直角坐标显式(简称显式)，直接输入$y=e^{-x} \sin x, \quad y=4+2 x-x^{3}$

    $$
    Plot[f(x)，{x，x1，x2}，可选项]
    Plot[{f1(x)，f2(x)，…}，{x，x1，x2}，可选项]
    $$

  + 直角坐标隐式(简称隐式)$F(x, y)=0  ,x^2+y^2=0$

    ImplicitPlot[F[x，y] == 0，{x，x1，x2}，可选项]

    << Graphics` 调入包
    ImplicitPlot[x^4 + y^4 – 18 (x^2 + y^2) + 14 ==0, {x, -6, 6}]

  + 参数式$z = x(t)，y = y(t)$

    ```
    ParametricPlot[{x(t), y(t)}, {t, t1, t2}, 可选项]
    ParametricPlot[{{x1(t)，yl(t)}，{x2(t)，y2(t)}，…}，{t，t1，t2}，可选项]
    ```
  + 极坐标式$\rho=\rho(\theta),\rho=\frac{1}{3} e^{2 \theta}​$
     $$
     PolarPlot [\rho(\theta),\{\theta, \theta 1, \theta 2\}]
     $$
    << Graphics`
    PolarPlot[1 – 2 Cos[t], {t, 0, 2 Pi}]

  + 列表式(又称数据形式，或称离散点形式
    $$
    ListPlot[\{x1，y1\}，\{x2，y2\}，…，\{xn，yn\}，可选项]
    $$

  + 图形式(画出曲线的图形)

+ 空间曲线表示

  + 显式：$z = x
    ^4 + y
    ^4 – 18(x^2 + y
    ^2
    )​$

    Plot3D[x^4+y^4 – 18 (x^2 + y^2), {x, -4, 4}, {y, -4, 4}]

  + 参数形式$x = x(t)，y = y(t)，z = z(t)$

  x = x(u，v)，y = y(u，v)，z = z(u，v)

  ParametricPlot3D[{x(u，v)，y(u，v)，z(u，v)}，{u，u1，u2}，{v，v1，
  v2}，可选项]

  + 数据形式

  Ta = {{0, 1, 4, 9, 16}, {1, 2, 5, 10, 17}, {2, 3, 6, 11, 18}, {3, 4, 7, 12,
  19}};
  ListPlot3D[Ta]

  + 交截形式
    $$
    \left\{\begin{array}{l}{f(x, y, z)=0} \\ {\varphi(x, y, z)=0}\end{array}\right.
    $$

  + 绘制函数函数ParametricPlot3D[{x(t)，y(t)，z(t)}，{t，t1，t2}，可选项]

  + 投影函数shadow[]，不是内置函数，<<Graphics'

+ 属性（可选项）

  ![](/../img2/Snipaste_2019-03-25_12-21-00.png)

  + 可选项名 - > 可选项值   PlotStyle->GrayLevel[i]

+ Show函数的功能之一是显示已经做好的图形

  + C1 = Plot[Sin[x], {x, 0, 2 Pi}, PlotStyle-> RGBColor[1, 0, 1]];
    C2 = Plot[Sin[x – 1], {x, 0, 2 Pi}, PlotStyle-> GrayLevel[0.6]];
    C3 = Plot[Sin[x + 1], {x, 0, 2 Pi}, PlotStyle-> Thickness[0.009]];
    C4 = Plot[Sin[2 x], {x, 0, 2 Pi}, PlotStyle-> Dashing[{0.01, 0.02,
    0.04}]];

    Show[C1, C2, C3, C4]

## 符号计算

+ 表达式的变换 

  ![](/../img2/Snipaste_2019-03-25_12-41-30.png)

+ 函数的极限 

Limit[f(x), x->a]与Limit[f(x)，x->Infinity

+ 导函数与偏导数 

D[f(x)，x]D[f(x)，{x，n}上面第一式是将f(x)对x求一阶导数，而第二式是将f(x)对x
求n阶导数，式中的D是求导符号。

D[f(x，y)，x，y] 将f(x，y)先对x求导，再对y求导。D[f(x，y)，{x，m}，{y，n}]将f(x，y)先对x求m阶导数，再对y求n阶

+ 不定积分与定积分 

Integrate[f(x)，Integrate[f(x)，{x, a, b}

+ 将函数展开为幂级数 

Series[f(x), {x, x0, n}]

+ 求和与求积 

Sum[un，{n，n1，n2}] 求和
Product[un，{n，nl，n2}] 求积
 式中un为通项，n为通项的项数，n1为起始项，n2为终止
项，n2可以取有限数，也可以取Infinity(即+∞)

+ 方程求根 

Solve[代数方程（或方程组），未知量]

+ 常微分方程求解 

DSolve[微分方程或方程组，未知函数，自变量] 求通解
DSolve[{微分方程，初始条件}，未知函数，自变量] 求特解

+ 偏微分方程

DSolve[偏微分方程，未知函数u(x，y)，自变量{x，上式中尚未涉及到定解条件，求得的解只含有任意函数的解析解

## 数值计算

+ 函数值与导数值的计算

  x = {-Pi/6, Pi/3, Pi/2};
  N[Sin[x] + Sin[2 x] + Sin[3 x]]

+ 定积分与重积分的数值计算

  Clear[x];

  f = Exp[-2*x] * Sinfx = D[f, x]

  N[fx /. { x->l }]

  fxx = D[f, {x, 2} ]

  N[fxx/. {x-> -1}]

  fxxx = D[f, {x, 3}]N[fxxx/. {x ->2

  NIntegrate[f(x)，{x，a，b}]

  NIntegrate[f(x，y)，{x，a，b}，{y，c，d}]

+ 方程的近似根

  FindRoot[f(x) = = 0，{x，x0}]

  在0≤x≤1与0≤y≤1的范围内很可能存在
  实根，故不妨取x0
  = Random[]，y0
  = Random[]，即有
  FindRoot[{x + y ==1, Sin[x] – Cos[y] == 0.1},
   {x, Random[]},{y, Random[]}]

+ 常微分方程数值解

  NDSolve[{微分方程，初始条件}，未知函数，{自变量范围}]NDSolve[{微分方程组，初始条件}，{未知函数1，未知函数2，…}， {自变量范围

+ 一元插值

  InterpolatingPolynomial[数据名(用data1)，自变量名]

+ 二元插值

+ 一元拟合

  Fit[data1，{1，x，x

  ，…}，

+ 二元拟合

## 迭代和分形

基本概念：

+ 生成元 

## 帮助

现代软件都十分庞大，功能纷繁复杂，有非常多的库调用，那么怎么样去从全局把控去掌握这些软件的操作技巧，把心力着力于问题的分析和解决呢，毕竟人脑可不是全部用来记忆的，那么这里有一些软件通用的技巧。

+ 使用$?$或$??$命令

  + 具体某一个对象的信息：$? name$
  + 显示有关name的详细信息：$??name​$
  + 通配符,显示相关所有的对象：$?Abc*$

+ Help功能

  + 窗口里面的help
  + 快捷键调出帮助界面：Shift + n

+ 名称完善功能：Ctrl+K ,输入命令或函数前几个字母得到一个名称列表

+ 公式输入可以用输入面板palttes![](/../img2/Snipaste_2019-03-25_11-24-34.png)

+ (\*…**)为Mathematica系统的注释符号，两个*号之间为注释内容，注释部分可以放在程序的任何位置

  

## 学习资源

官网

有点郁闷啊，为啥GitHub有些更新看不见了呢，shit!

