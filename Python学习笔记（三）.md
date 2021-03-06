# Python学习笔记（三）
[TOC]
## 字符串处理
### 1、访问字符
　和c/c++相同，我们可以使用和数组索引一样的形式来访问字符串中的某个字符。除了常见0到len(str)-1索引，Python还提供了负数索引，负数索引i指向的字符和正索引len(str)+i相同。
```python
s = 'hello'
s[0] #'h'
s[-1] #'o'
s[-3]==s[2] #'l' 
```
> hello

| 正索引 | 负索引 | 字符 |
| :----: | :----: | :--: |
|   0    |   -5   |  h   |
|   1    |   -4   |  e   |
|   2    |   -3   |  l   |
|   3    |   -2   |  l   |
|   4    |   -1   |  o   |
　我们还可以使用for循环访问字符串中的每个字符：
```python
s = 'python'
#方法一
for i in range(len(s)):
    print(s[i])
#方法二
for c in s:
    print(c)
```
### 2、字符编码与解码
　字符串由字符组成，字符是可见或者不可见的标识，计算机无法直接处理原始的字符，我们使用一套编号来表示这些字符，最常见的就是Unicode字符编码集。每个Unicode码表示一个字符，为了方便传输、存储，我们又对Unicode码又进行编码，如utf-8。
　现在我们言归正传，在Python中我们可以获取某个字符的Unicode码，也可以给定Unicode码获取相应的字符：
```python
ord('a')    #97
chr(98)   #'b'
```
### 3、截取字符串
　很多时候我们只需要字符串中的一部分，而非全部，这时候我们就需要对字符串进行截取。在Python中，我们使用`s[begin:end]`这种形式对字符串进行截取，它返回从索引begin到end-1的子串。其中begin与end可以为空，它们的默认值分别是0与`len(s)`。字符串截取也支持负数索引，但如果你无法使用负数索引截取到最后一个字符，此时你可以选择使用默认值，如`s[-2:]`，它截取了最后两个字符。
### 4、标准字符串函数
　Python提供了一些内置的字符处理函数，主要包含字符串测试函数，字符串搜索函数，字符串拆分函数等等，在此不表，详情请参看Python文档。

## 正则表达式
[1]待我以后用到了再来填坑
