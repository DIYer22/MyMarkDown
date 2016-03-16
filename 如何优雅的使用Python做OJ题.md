# 如何优雅地使用Python做OJ题



>作者：`UCE 小磊`

>时间：`2016/03/12`

>邮箱：`ylxx@live.com`

>标签：`oj` `python` `OnlineJudge`



## 一. Python与C++的简单对比：

### 例题
以[Problem 1023](http://coder.buct.edu.cn:8088/JudgeOnline/problem.php?id=1023)(ps:北化校内OJ,外网进不去)为例：

　题目描述
> 对10个整数从小到大排序。



　样例输入
> 4 85  3 234 45 345 345 122 30 12

　样例输出
> 3
4
12
30
45
85
122
234
345
345

### C++版
```C
#include <iostream>
#include <cstdio>
#include <cstdlib>
#include <algorithm> 

using namespace std; 

int main()  //C程序结构所必需的代码 
{
    int a[10];  //输入阶段 
    int i;
    for(i=0;i<10;i++) 
        cin>>a[i];
    sort(a, a+10);  //调用stl 
    for(i=0;i<10;i++)  //输出 
    	cout<<a[i]<<endl;
	return 1; 
}
/*  运行信息：
    Problem: 1023
    Language: C++
    Time:0 ms
    Memory:1292 kb
    代码长度：318B 18行
*/
```

### Python版本
```python
listt = map(lambda x:int(x), raw_input().split()) # 万能的输入语句，下文会详细解释其意义
listt.sort()  # 调用标准库
for i in listt :
    print i  # 输出
    
/*  运行信息：
    Problem: 1023
    Language: Python
    Time:100 ms
    Memory:7180 kb
    代码长度：92B 4行
*/
```
由于：
> 1. 代码简短，也更为人性化，让人摆脱繁琐的语言细节，平均代码量为C 的一半
1. 极其方便的字符串，列表操作
1. Python具有函数式编程的特性
1. 动态，交互式语言，带来DEBUG的便携

所以，用Python不仅能节省了大量coding，及调试时间
也让人在编程时更注重 逻辑思考，印证了那句
> Programming not coding


当然，缺点也十分明显
损失了大量的时间和内存性能
因此，复杂的题可能会引起时间或内存超限
所以Python适合完成一些对性能要求不高的题


## 二. 输入部分
输入部分根据输入行数，分两种情况
### 1. 只需输入一行
上面例子中的样例输入为
> 4 85  3 234 45 345 345 122 30 12

我们的输入函数为
**`listt = map(lambda x:int(x), raw_input().split())`**

我们先来看**右边**：

其中`raw_input()`是接受一排完整的输入`4 85  3 234 45 345 345 122 30 12\n`，并转换为字符串：
`"4 85  3 234 45 345 345 122 30 12"`

将此字符串施以`.split()`方法，将以空格:`' '`分开，便返回了一个字符串组成的列表:
`['4', '85', '3', '234', '45', '345', '345', '122', '30', '12']`

所以整个右边`raw_input().split()`返回的是字符串组成的列表

字符串列表中的每个元素在`map()`中，匿名函数`lambda`的作用下转换成了`int`型，并付给变量`listt`       
(不了解`map`函数，和匿名函数`lambda`的用法，看[廖雪峰老师的imooc Python进阶教程](http://www.imooc.com/view/317))

最后，变量listt 为`int`型列表
```
>>> listt
[4, 85, 3, 234, 45, 345, 345, 122, 30, 12]
```
### 2. 要输入N行
例：
以[Problem 1050](http://coder.buct.edu.cn:8088/JudgeOnline/problem.php?id=1050)(ps:北化校内OJ,外网进不去)为例：

　输入
> 学生数量N占一行, 每个学生的学号、姓名、三科成绩占一行，空格分开。成绩是正整数

　输出

> 各门课的平均成绩 最高分的学生的数据（包括学号、姓名、3门课成绩），平均成绩用整数表示

　样例输入
> 2
1 blue 90 80 70
b clan 80 70 60

　样例输出

> 85 75 65
1 blue 90 80 70


Python代码
```python
n = input()
def f(x):
    if ord(x[0]) < 90:  # 判断是数字还是字幕
        return int(x)
    return x
    
a = [map(f, raw_input().split()) for i in range(n)]
print sum([x[2] for x in a])/n, sum([x[3] for x in a])/n, sum([x[4] for x in a])/n  # 打印平均数
listt=[sum(x[2:]) for x in a]
maxx=max(listt)
for i in range(n):  # 找到最大值的索引
    if listt[i] ==maxx:
        break
print str(a[i]).replace(', ',' ').replace('\'','')[1:-1]+' '  #列表一排万能输出，但输出得不好看，不用在意
```

输入部分：
先输入`n`获得行数

接着输入n行
**`a = [map(f, raw_input().split()) for i in range(n)]`**

这段代码意思是将`map(f, raw_input().split())`运行n次，并将每次返还的结果(一个一维列表)，组成一个新的列表赋值给变量`a`，此时`a`为二维列表,共有n行。

　样例输入
> 2
1 blue 90 80 70
b clan 80 70 60

则变量`a`为：
```python
>>> a
[[1, 'blue', 90, 80, 70], ['b', 'clan', 80, 70, 60]]
```

## 三. 输出部分
一般输出部分较为简单
#### 1. 关于`print`注意以下几点
> 1. `print a, b`中，`,`会被替换为一个空格
1. 若打印两个变量不想要中间的空格，则换为`print str(a)+str(b)`
1. `print` 函数会自动在行尾添加一个`'\n'`
1. 若不想在行尾换行，可在`print `语句的最后面添加一个`,`（但有空格）
1. 在`for`循环中的`print`，既不想换行也不想要空格，在迭代中无法使用`str(a)+str(b)`，则使用`创建空字符串法`：

```python
strr = ''  # 创建一个空字符串
for i in listt:
    strr += i  # 依次添加 i，若是数字，记得换为str(i)
print strr  # 完美打印
```

#### 2. 不清楚的格式错误
有时候，仍会遇到不清楚的格式错误
便可以用上面的`创建空字符串法`输出

　例：
> 要求输出列表`listt`中的每一个数字，每个数字间有一个空格，但末尾不能有空格

　解：
```python
strr = ''  # 创建一个空字符串
for i in listt:
    strr += str(i)+' '  # 数字后面加了一个空格
print strr[:-1]  # 使用切片，去掉了最后一个空格
```


#### 3. 对于列表标准输出，懒人专用的`一行代码版`
`print str(a[i]).replace(', ',' ').replace('\'','')[1:-1]+' '`
（同时适用于字符串和数字列表）

一般将输入，输出的`一行代码版`注释在程序开头，方便复制调用。

## 四. 总结
### Python刷OJ，适合人群：
> * Python初学者，想熟悉Python
> * 遇到了迷之错误，想换一种语言试一下
> * 非专业ACMer[^footnote]，想方便做题
> * 想刷OJ刷出新感觉
> * 想了解Python的一些输入输出特性

### 关联阅读:
1. 让你的Python代码更加pythonic：[http://wuzhiwei.net/be_pythonic/](http://wuzhiwei.net/be_pythonic/)
2. Python零基础入门：[http://pan.baidu.com/s/1qWXEjwg](http://pan.baidu.com/s/1qWXEjwg)
[^footnote]:虽然有些ACM比赛提供Python环境，但亚洲区预选赛语言只包括C++、C和Java。
