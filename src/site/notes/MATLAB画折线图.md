---
{"dg-publish":true,"permalink":"/MATLAB画折线图/","dgPassFrontmatter":true}
---

```matlab
figure;
loglog(x,y,'d-','linewidth',2); hold on;
plot(x,y,'s-','linewidth',2); hold on;
plot(x,y,'o-','linewidth',2); hold on;
```
这是双对数坐标轴
### **为什么不用 `loglog` 画所有线？**

实际上可以全部用 `loglog`，但代码作者选择：

- 用 `loglog` 画第一条线（建立双对数坐标）
    
- 用 `plot` 画后续的线（在已建立的双对数坐标上）
    

**两种方法效果相同**，因为坐标轴类型一旦设置就会影响所有后续绘图。
dg-publish: true