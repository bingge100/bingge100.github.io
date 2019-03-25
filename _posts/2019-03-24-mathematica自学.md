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

## 基本技巧

* 程序运行：shift+enter
* 终止运行：alt+空格 或者 alt+
* 帮助：？+函数名（开头大写）
* 变量的批量赋值
* 命令序列可以自动调用 %n
* 退出：alt+F4
* ;号在末尾表示不输出结果

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

## 编程技巧

+ 自定义函数

$$
f\left[x_{-}\right] :=\operatorname{Exp}[x] *(\sin [x]+1)+\log \left[x^{\wedge} 2\right]
$$

+ 条件结构
  + $Ihs : $=x$ hs 1$/$ ;test$   当 test 为真时使用定义 rsh
  + $If [test, then, else]$  如test为真计算then，反之计算else
  + $Which [test1, valuel, test2, value2,\cdots]$  依次计算 testi，给出对应的值 vaulei
  + $Switch [expr, forml, valuel, form2, value2,\cdots]$  expr 与每一个 formi 相比较，给出相匹配的值 valuei

eg:定义分段函数$$ 
f(x)=\left\{\begin{array}{cc}{x^{2}+1} & {x>0} \\ {-x^{2}-1} & {x<0} \\ {0} & {x=0}\end{array}\right.
$$
方法一：$$ 
\begin{array}{l}{f[x] :=x^{\wedge} 2+1 / ; x>0} \\ {f\left[x_{-}\right] :=-x^{\wedge} 2-1 / ; x<0} \\ {f\left[x_{-}\right] :=0 / ; x==0}\end{array}
$$

方法二：$$ 
f\left[x_{-}\right] :=I f\left[x>0, x^{\wedge} 2+1, I f\left[x<0,-x^{\wedge} 2-1,0\right]\right]
 $$

方法三：$$ 
f\left[x_{-}\right] :=\text { Which }\left[x>0, x^{\wedge} 2+1, x<0,-x^{\wedge} 2-1, x==0,0\right]
 ​$$

## 循环结构

+ Do 结构、For 与 While 结构
  + $Do[expr,{i,imin,imax,di}] $ 循环计算 expr，步长为 di，i从 imin 增加 imax(步长缺省则默认为 1，imin 缺省也默认为 1)
  + $Do[expr,{n}] $ 循环计算 expr 共 n 次
  + $Do[expr,{i,imin,imax,di},{j,jmin,jmax,dj}] ​$循环计算 expr，i 从 imin 到 imax 循环，对于每个 i，j 从jmin 到 jmax 循环（即多重循环）

+ For
  + $For[start,test,incr,body] $以 start 为起始值，重复计算执行主体 body 和执行表达式incr 改变循环变量的值，直到 test 为假 
+ while结构
  + $While[test,body] ​$只要 test 为真，则重复计算执行主体 body

tips:防止死循环,break[]函数

## 绘图

+ 平面曲线表示法
  + 直角坐标显式(简称显式)，直接输入$y=e^{-x} \sin x, \quad y=4+2 x-x^{3}$
  + 直角坐标隐式(简称隐式)$F(x, y)=0  ,x^2+y^2=0$
  + 参数式$z = x(t)，y = y(t)$
  + 极坐标式$\rho=\rho(\theta),\rho=\frac{1}{3} e^{2 \theta}$
  + 列表式(又称数据形式，或称离散点形式
  + 图形式(画出曲线的图形)
+ 空间曲线表示法
  + 参数形式$x = x(t)，y = y(t)，z = z(t)$
  + 交截形式
  + 

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

  



