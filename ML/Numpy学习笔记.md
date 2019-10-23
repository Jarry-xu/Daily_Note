---
typora-root-url: assets\
---



## Numpy学习笔记

[TOC]

### 数组特性：

#### 1.数组生成

一般从列表生成（手工生成的话），要么就是从其他类型转为nparray类型

##### 初始值设置 fill函数

##### 生成函数

##### 	arange产生从[start，stop]，以step为间隔的数组

##### 	linspace产生从[start，stop]的N个等间隔数组

##### 	meshgrid用来生成二网网格

##### 	ones or zeros生成全0或1数组

##### 	empty`_`like, ones`_`like, zeros`_`like 产生一个跟 `a` 大小一样，类型一样的对应数组

##### 	identity 生成单位矩阵

#### 2.数组操作

##### 数学运算

可以直接对数组进行数学运算，包括但不限于加减乘除，乘方开方

数组之间也可以进行类似的运算，包括点乘

##### 切片与索引

需要记住的是切片在内存中使用的是引用机制

###### 花式索引：get everywhere

第一种方式：指定特定位置

```
a = arange(0, 80, 10)
indices = [1, 2, -3]
y = a[indices]
print y
```

第二种：使用布尔数组mask来进行花式索引

```
y=a[a>0]
```

##### 使用where语句 返回找到满足条件的位置元组

#### 3.数据类型转换

使用astype或者asarray进行

####  3.1 数组与字符串的转换

```
a = np.array([[1,2],
           [3,4]], 
          dtype = np.uint8)
#转换为字符串
str=a.tostring()
#字符串转换为数组
a = np.fromstring(s, 
                  dtype=np.uint8)
#返回一维数组，需要自己去还原维度
```

#### 3.2 数组与列表的转换 tolist()

#### 4.数组方法

####     1.求和 sum

1. 一维求和
2. 多维数组按指定维度求和 使用axis 

####     2.求积 prod 参照求和

####     3.最大最小

- 局部最大最小 指定维度
- 全局最大最小  a.max()or min()
- 最大最小的位置 argmin or argmax

####     4.均值 mean

#### 	5.标准差std 方差var

#### 	6.数值限制 clip方法   

```
a.clip(3,5)
小于3的变成3 大于5的变成5
```

#### 	7.近似方法round 

```
a.round(decimals=1)近似到一位小数
```

#### 	8.排序方法sort和argsort 会改变数组本身

需要注意的是对于多维数组排序默认按照最后一维进行，就二维数组来说，0代表列，1代表行

#### 5.数组排序

#### sort函数 返回排序好的数组

#### argsort函数 返回从小到大的排列在数组中的索引位置

searchsorted函数 在已经排序好的数组中插入新的值

```
sorted_array = linspace(0,1,5)
values = array([.1,.8,.3,.12,.5,.25])
searchsorted(sorted_array, values)
```

#### 6.数组形状改变

1. reshape函数不改变自身 
2. 直接修改数组的shape属性
3. 使用newaxis增加数组维数

```python
y=a[newaxis,:]
```

4. 使用squeeze方法去除多余的长度为1的维度轴

#### 7.数组之间的连接 

1. concatenate函数将两个或者多个数组按照指定维度进行拼接  

2. flatten方法或者ravel将多维数组变为1维数组，flatten返回的是数组的复制,ravel返回的是引用

​    但是如果ravel的对象本身是一个view，那么在此基础上的修改就不会改变原数组的值

3. atleast_xd 函数 用来保证数组至少有x维，主要用途是进行数据的规范化，保证输入满足一定的条件

### ufunc对象

每个ufunc对象的op函数都有以下方法：

reduce方法 将op沿着某个轴应用，默认第一维

accumulate方法 保存每一步的结果形成的数组

reduceat方法 运用到指定下标，返回与indices大小相同的数组

outer方法

```
a = np.array([0,1])
b = np.array([1,2,3])
np.add.outer(a, b)
#注意顺序
前面的按元素分别加到后面的数组中
```

### Trick:

#### 使用select函数

**参数一，**condlist=【条件一，条件二，条件三，，，，】

**参数二，**choicelist=【操作一，操作二，操作三，，，，，】

只有每个条件中，对应为true的才会执行相对应的操作，最终所有条件都不满足的元素，则执行默认值default。

#### 使用choose函数实现条件筛选与替换

参考

[choose用法]: https://nbviewer.jupyter.org/github/lijin-THU/notes-python/blob/master/03-numpy/03.17-choose.ipynb

需要注意的是它是将原数组按照不同的条件进行替换

### 绘图基础

使用matplotlib 可以绘制图像

#### 二维图

一般使用plot()，格式如下：

```
plot(y)
plot(x, y)
plot(x, y, format_string)
自己查字符参数
#默认多次plot会在同一个图中叠加
plt.axis([xmin, xmax, ymin, ymax]) 标定x y 轴的最大显示范围
```

PS：只给定 `y` 值，默认以下标为 `x` 轴

#### 散点图

```
scatter(x, y)
scatter(x, y, size)
scatter(x, y, size, color)
```

#### 画多个图

使用figure可以产生新的图像

使用subplot可以在一幅图中画多幅子图

```
subplot(1, 2, 1)
plot(x)
subplot(1, 2, 2)
plot(y)
```

#### 为数据添加标签：

在Plot函数中指定label=‘something’，然后加入Legend()来显示图例

```
plot(x, label='sin')
plot(y, label='cos')
legend()
#或者直接在lengend中加入Label
legend(['sin', 'cos'])
使用annotate在指定位置添加注释
plt.annotate('local max', xy=(2, 1), xytext=(3, 1.5),
            arrowprops=dict(facecolor='black', shrink=0.05),
            )
```

#### 文本处理 

参考[链接](https://nbviewer.jupyter.org/github/lijin-THU/notes-python/blob/master/06-matplotlib/06.03-working-with-text---basic.ipynb)

```
plot(x, sin(x))
xlabel('radians')
# 可以设置字体大小
ylabel('amplitude', fontsize='large')
Axes对象方法： Axes对象是Figure对象中的子图
title('Sin(x)')
text()在 Axes对象任意位置添加文字
Figure对象方法：
figtext()
suptitle()
grid()#显示网格
```

#### 关闭和清除图像

清除已有的图像使用：

```
clf()
```

关闭当前图像：

```
close()
```

关闭所有图像：

```
close('all')
```

#### 绘图实例

[绘图实例链接](https://nbviewer.jupyter.org/github/lijin-THU/notes-python/blob/master/06-matplotlib/06.10-different-plots.ipynb)

