# 如何优雅的使用Python做OJ题



---
作者：`UCE 小磊`

时间：`2016/03/12`

**与C++的简单对比：**

以[Problem 1023](http://coder.buct.edu.cn:8088/JudgeOnline/problem.php?id=1023)(ps:北化校内OJ,外网进不去)为例：

　题目描述
> 用选择法对10个整数从小到大排序。



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

C++语言版
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

Python版本： 
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

Python代码十分简短
也更为人性化
可以让人摆脱繁琐的语言细节
正因此，节省了大量做题时间
用Python编程时更注重，逻辑思考，印证了那句
> Programming not coding


当然，缺点也十分明显
损失了大量的时间和内存性能
所以，也并非所有题都适合Python写

## 一. 基础部分
### 1. 以一行输入
上面例子中的样例输入为
> 4 85  3 234 45 345 345 122 30 12

我们的输入函数为
`listt = map(lambda x:int(x), raw_input().split())`

我们先来看右边：

其中`raw_input()`是接受一排完整的输入`4 85  3 234 45 345 345 122 30 12\n`，并转换为字符串：
`"4 85  3 234 45 345 345 122 30 12"`

将此字符串施以`.split()`方法，将以空格:`' '`分开，便返回了一个字符串组成的list:
`['4', '85', '3', '234', '45', '345', '345', '122', '30', '12']`

所以整个右边`raw_input().split()`返回的是字符串组成的list

字符串list中的每个元素在`map()`中，匿名函数`lambda`的作用下转换成了`int`型，并付给变量`listt`       
(不了解`map`函数，和匿名函数`lambda`的用法，看[廖雪峰老师的imooc Python进阶教程](http://www.imooc.com/view/317))

最后，变量listt 为`int`型`list`
```
>>> listt
[4, 85, 3, 234, 45, 345, 345, 122, 30, 12]
```
### 1. 以N行输入
例：

　输入
> 学生数量N占一行, 每个学生的学号、姓名、三科成绩占一行，空格分开。成绩是正整数

　输出

> 各门课的平均成绩 最高分的学生的数据（包括学号、姓名、3门课成绩），平均成绩用整数表示，舍弃小数

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
print sum([x[2] for x in a])/n, sum([x[3] for x in a])/n, sum([x[4] for x in a])/n
listt=[sum(x[2:]) for x in a]
maxx=max(listt)
for i in range(n):
    if listt[i] ==maxx:
        break
print str(a[i]).replace(', ',' ').replace('\'','')[1:-1]+' '  # 输出得不好看不用管它
```

输入部分：
`a = [map(f, raw_input().split()) for i in range(n)]`


## 二. 进阶部分


