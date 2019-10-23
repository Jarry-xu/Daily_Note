# vim常用操作

## 翻页操作

向上翻页 ctrl+b  (b=back)

向下翻页 ctrl+f (f=front)

## 单行操作

home 移到行头

end 移动到行尾

n + space 移动n个字符

dd  删除一行     ndd   删除n行

d0 从光标到行头   d$从光标到行尾

yy 复制一行    nyy 复制n行

y0 从光标到行头   y$从光标到行尾

p 行后复制  P行前复制

## 行间操作

、+ 找到下一个非空格的行开头 

、-          上一个非空格行

gg 回到第一行

G  回到最后一行

N + enter   向下移动N行

J 合并两行

## 查找与替换

/word  

n 查找下一个  N查找上一个 

查找并替换 

1. :n1,n2 /word1/word2/g   指定行替换

2. :1,$s/word1/word2/gc     



### 块选择   同时选择一片区域

按V    行选择

ctrl +v 块选择   

选择完之后按y复制  

按d删除



### 多窗口编辑

：sp  同文件分屏

：sp filename  不同文件分屏

光标切换

ctrl +w +j(向下)/k向上