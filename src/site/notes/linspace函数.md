---
{"dg-publish":true,"permalink":"/linspace函数/","dgPassFrontmatter":true}
---

[[MATLAB\|MATLAB]]
本文详细介绍了Matlab中linspace函数的使用方法、功能及示例应用，帮助读者理解如何在Matlab环境下生成指定范围内的等间距点数组。

功能：linspace是Matlab中的一个指令，用于产生x1,x2之间的N点行矢量。其中x1、x2、N分别为起始值、中止值、元素个数。若缺省N，默认点数为100。在matlab的命令窗口下输入help linspace或者doc linspace可以获得该函数的帮助信息。

　　将产生从1到20步长为1的数组。类似于在命令窗口中输入：

>>  X=linspace(1,20)  
  
结果

X =  
  
  
  列 1 至 20
  
  
     1     2     3     4     5     6     7     8     9    10    11    12    13    14    15    16    17    18    19    20  

>>  

```c
X=linspace(0,2*pi,12) 
```

结果
  
X =  
  
  
  列 1 至 12
  
  
      0    0.5712    1.1424    1.7136    2.2848    2.8560    3.4272    3.9984    4.5696    5.1408    5.7120    6.2832  
dg-publish: true