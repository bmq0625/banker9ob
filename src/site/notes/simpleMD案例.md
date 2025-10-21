---
{"dg-publish":true,"permalink":"/simpleMD案例/","dgPassFrontmatter":true}
---

[[MDS案例\|MDS案例]] [[MATLAB\|MATLAB]]
# plot_torus.m
```matlab
代码
clear; close all;
[theta,phi] = meshgrid(linspace(0,2*pi,50));
r = 2;
R = 5;
x = (R + r*cos(theta)).*cos(phi);
y = (R + r*cos(theta)).*sin(phi);
z = r*sin(theta);
figure;
surf(x,y,z);
shading interp
colormap summer
axis equal
set(gca,'xtick',[])
set(gca,'ytick',[])
set(gca,'ztick',[])
set(gca,'Visible','off')
print -dpng test_print
```
我来逐行逐句详细解释这段MATLAB代码：
## 第1行：`clear; close all;`
- `clear`：清除工作区中的所有变量
- `close all`：关闭所有打开的图形窗口
- 作用：清理环境，确保代码从干净的状态开始执行

## 第2行：`[theta,phi] = meshgrid(linspace(0,2*pi,50));`
- `linspace(0,2*pi,50)`：创建从0到2π的50个等间距点
- `meshgrid()`：生成网格坐标矩阵
- 结果：创建50×50的`theta`和`phi`矩阵，用于参数化曲面

## 第3-4行：定义半径
```matlab
r = 2;    % 小圆半径（环管的半径）
R = 5;    % 大圆半径（环的中心到圆管中心的距离）
```

## 第5-7行：计算环面坐标
```matlab
x = (R + r*cos(theta)).*cos(phi);  % x坐标：(大圆半径 + 小圆径向分量) × 大圆的cos分量
y = (R + r*cos(theta)).*sin(phi);  % y坐标：(大圆半径 + 小圆径向分量) × 大圆的sin分量 
z = r*sin(theta);                  % z坐标：小圆的垂直分量
```
这是**圆环面（torus）**的标准参数方程
第5-7行的 .* 能否替换成 * ？这俩有啥区别？
**绝对不能替换！** [[各种乘在 MATLAB 中的区别\|各种乘在 MATLAB 中的区别]]
## 第8行：`figure;`
- 创建一个新的图形窗口

## 第9行：`surf(x,y,z);`
- 绘制三维曲面图，使用计算出的x,y,z坐标

## 第10行：`shading interp`[[好像不对\|好像不对]]
- 设置着色方式为插值着色
- 使颜色在网格面之间平滑过渡
- 这里开始就没有分号了

## 第11行：`colormap summer`
- 设置颜色映射为"summer"配色方案
- 呈现从绿色到黄色的渐变

## 第12行：`axis equal`
- 设置坐标轴比例相等
- 确保图形在三个维度上比例正确，不扭曲

## 第13-15行：隐藏坐标轴刻度
```matlab
set(gca,'xtick',[])  % 隐藏x轴刻度
set(gca,'ytick',[])  % 隐藏y轴刻度  
set(gca,'ztick',[])  % 隐藏z轴刻度
```

## 第16行：`set(gca,'Visible','off')`
- 完全隐藏坐标轴及其边框
- `gca`获取当前坐标轴句柄

## 第17行：`print -dpng test_print`
- 将图形保存为PNG文件
- `-dpng`：指定输出格式为PNG
- `test_print`：输出文件名（实际保存为test_print.png）
![Pasted image 20251020215728.png](/img/user/Pasted%20image%2020251020215728.png)
**总结**：这段代码创建并渲染了一个圆环面的三维图形，设置了美观的视觉效果，隐藏了坐标轴，最后将结果保存为PNG图片文件。
dg-publish: true