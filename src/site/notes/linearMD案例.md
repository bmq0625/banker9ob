---
{"dg-publish":true,"permalink":"/linearMD案例/","dgPassFrontmatter":true}
---

[[MATLAB\|MATLAB]] [[MDS案例\|MDS案例]]
```matlab
clear;close all;
time_0=[6.515,15.54,33.627,65.971,121.812,1335.68,7194.2];
time_1=[1.425,2.418,3.307,4.957,6.41,22.015,53.86];
time_2=[1.369,2.252,3.612,5.659,8.445,53.63,239.142];
N=[6:10,15,20].^3*4;
figure;
loglog(N,time_0,'d-','linewidth',2); hold on;
plot(N,time_2,'s-','linewidth',2); hold on;
plot(N,time_1,'o-','linewidth',2); hold on;
x=5e3:5e4;
plot(x,1e-6*x.^2,'--','linewidth',2);
plot(x,1e-3*x,':','linewidth',2);
xlabel('Number of atoms');
ylabel('Computation time for 1000 steps');
legend('No neighbor list','O(N^2) algorithm', 'O(N) algorithm)','~N^2','~N');
set(gca,'fontsize',15,'linewidth',1);
axis tight
```
我来逐行逐句详细解释这段MATLAB代码：
## 第1行：`clear;close all;`
- `clear`：清除工作区中的所有变量
- `close all`：关闭所有打开的图形窗口
- 作用：清理工作环境

## 第2-4行：定义时间数据数组
```matlab
time_0=[6.515,15.54,33.627,65.971,121.812,1335.68,7194.2];  % 无邻居列表的计算时间
time_1=[1.425,2.418,3.307,4.957,6.41,22.015,53.86];         % O(N)算法时间
time_2=[1.369,2.252,3.612,5.659,8.445,53.63,239.142];       % O(N²)算法时间
```
这些是不同算法在不同规模下的计算时间（单位可能是秒）

## 第5行：`N=[6:10,15,20].^3*4;`
- `[6:10,15,20]`：创建数组 [6,7,8,9,10,15,20]
- `.^3`：对每个元素求立方（逐元素运算）
- `*4`：乘以4
- 结果：计算原子数量，假设每个晶胞有4个原子
- N = [864, 1372, 2048, 2916, 4000, 13500, 32000]

## 第6行：`figure;`
- 创建新的图形窗口

## 第7-9行：绘制三条主要曲线
```matlab
loglog(N,time_0,'d-','linewidth',2); hold on;  % 双对数坐标，菱形标记，线宽2
plot(N,time_2,'s-','linewidth',2); hold on;    % 正方形标记
plot(N,time_1,'o-','linewidth',2); hold on;    % 圆形标记
```
- `loglog`：双对数坐标图（x轴和y轴都取对数）
- `'d-'`、`'s-'`、`'o-'`：标记样式（菱形、正方形、圆形）+实线
- `hold on`：保持图形，允许多次绘制

## 第10-12行：绘制理论参考线
```matlab
x=5e3:5e4;                    % 创建x坐标范围 [5000, 55000, ..., 50000]
plot(x,1e-6*x.^2,'--','linewidth',2);  % O(N²)理论线：y = 10⁻⁶ × x²
plot(x,1e-3*x,':','linewidth',2);      % O(N)理论线：y = 10⁻³ × x
```
- `x.^2`：逐元素平方
- `'--'`：虚线，`':'`：点线

## 第13-14行：设置坐标轴标签
```matlab
xlabel('Number of atoms');                          % x轴标签
ylabel('Computation time for 1000 steps');          % y轴标签
```

## 第15行：`legend(...)`
- 添加图例，对应前面绘制的5条线
- 注意：`'O(N) algorithm)'` 有个多余的右括号

## 第16行：`set(gca,'fontsize',15,'linewidth',1);`
- 设置坐标轴属性
- `'fontsize',15`：坐标轴字体大小设为15
- `'linewidth',1`：坐标轴线宽设为1

## 第17行：`axis tight`
- 自动调整坐标轴范围，使图形紧贴数据
![Pasted image 20251020215919.png](/img/user/Pasted%20image%2020251020215919.png)
## 代码目的分析
这段代码绘制了**分子动力学模拟中不同算法的计算复杂度比较**：
- 展示了三种算法随原子数量增加的时间增长趋势
- 在双对数坐标下，O(N)算法表现为斜率≈1的直线，O(N²)算法表现为斜率≈2的直线
- 通过理论参考线验证算法的实际复杂度

**关键理解**：在双对数坐标中，幂函数关系会表现为直线，斜率对应幂次：
- 斜率≈1 → O(N)
- 斜率≈2 → O(N²)
dg-publish: true