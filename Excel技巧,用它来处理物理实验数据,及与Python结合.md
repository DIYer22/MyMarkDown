# 一. Excel技巧及用它来处理物理实验数据

标签（空格分隔）： Excel

---
[点击下载DataNitro，课堂示例xls，7个实验的模板](http://pan.baidu.com/s/1o7v1ZRk)

[Python下载 及Python教程](http://pan.baidu.com/s/1qWXEjwg)

---

[TOC]

## 1. Excel公式基础
在空格里加等于号之后直接书写公式即可

例如求第一列三个数的平均值：
> =(A1+A2+A3)/3

用求和函数来做：
> =SUM(A1:A3)/3

统计A1，A2....，A10中非空单元格的个数：
> =COUNTA(A1:A10)

IF语句：
> =IF(条件，条件为TURE时返回值，条件为FALSE时返回值）


## 2. 处理物理实验数据

建议的应用：
1. 写一个包含不确定度计算器，完善的线性回归折线图模板 的xls 发给手机 配合WPS ，极大的方便计算与画图
2. 每做一个实验，写一套完整的数据处理，帮宿舍所有人处理数据，作为互帮互助 让他们轮流帮你抄实验报告和预习报告 让自己成为脑力劳动者　(•̀ᴗ•́)و✧


不确定度公式：
![](http://7xs2rt.com1.z0.glb.clouddn.com/excel_for_phyimage002.png)
人肉版：
![](http://7xs2rt.com1.z0.glb.clouddn.com/excel_for_phyimage004.jpg)






## 3. 作图
![](http://mmbiz.qpic.cn/mmbiz/rPmGjYCZYeyzTFIj0BiameStibSWicic7LVpstpjDOhCQH0430Ogu3trneSU2Q34QCF7IQjW5hiblK1iah1gjVvWVyCQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)

> 1. 选中数据后直接有快捷创建图表的按钮
2. 创建折线图
3. 可操作的区域有，坐标轴，网格，数据曲线，趋势线（即线性回归线），线上的数据点，标题，图表的边框
4. 操作的方式有： 1.右边侧栏的设置菜单及其N个子菜单   2.鼠标右键菜单（可调控的东西太多太多了，大家回去都试一下吧）
5. 线性回归在数据曲线上右键->添加趋势线即可，建议将趋势线换一种颜色，并在菜单里面寻找"显示公式"选项，并勾选它
6. 调整大小，使网格为方形，并添加数据点图标，数据点标注可以很方便的手工作图（不用尺子或数格子）


## 4. 其它常用Excel函数
VLOOKUP 函数用法：
![](http://7xs2rt.com1.z0.glb.clouddn.com/excel_for_phyQQ%E5%9B%BE%E7%89%8720160323182713.png)
扩展阅读：
> [Excel常用函数大全](http://blog.sciencenet.cn/blog-587114-814315.html)



## 5. 调用Python

可以先阅读：
　　[Excel与Python结合的各种方式](http://www.gocalf.com/blog/python-read-write-excel.html)

[Python下载 及Python教程](http://pan.baidu.com/s/1qWXEjwg)

我举的例子是
DataNitroTrial.exe　->　[点击下载](http://pan.baidu.com/s/1bnPuiAz)

以及[DataNitro 基础教程](http://jingyan.baidu.com/article/656db91886146be380249c72.html)

Ps:
> 1. 调用的.py文件，及xls文件本身 存放的路径都不能有中文 演示失败是因为 xls文件放在中文路径下的原因
2. 直接在Excel中调用Pyhton函数写的公式好像不行，我在两台电脑上试了，很遗憾，都失败了，如果谁的电脑成功了，请联系一下我 ^_^



## 6. Excel+Python的优缺点
同类技术
> 数据库，VBA+Excel

相对于数据库
> Excel直观的图形化界面带来的便捷
高精度，高易用性的数据精细操作
近乎零成本的数据可视化

相对于VBA+Excel
> 不用再去学习VBA （VB近年来屡被评为最受讨厌语言）
Python相对于VB语言的其他优势


Excel+Python适用于：
> 1. 数据量小而杂，且原始数据为Excel
2. 需要高精度的数据操作
3. 希望数据可视化方便


# 二. 社团事物
1. 大概统计一下各方向的人数
2. 征集有趣 or 有用 or 有助于技能成长 互相学习 的项目
2. 每隔两周要写一篇学习记录和未来两周的规划(大家直接执行吧)
2. 想找两个同学帮忙申请教室(彭翼和陈琛)

