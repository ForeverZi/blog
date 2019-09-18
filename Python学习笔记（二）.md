# Python学习笔记（二）

[TOC]
## 分支与循环
### 条件表达式
　和其他语言相同，Python支持条件表达式，它的两个布尔值常量为True和False。支持的布尔运算为：not、and、or、==和！=，布尔短路逻辑也无特殊之处，在此略过不表。
###if语句
如下所示，其中elif和else都是可选的：

```python
age = int(input('enter your age:'))
if age<10:
    print('you are a child')
elif age>=10 and age<18:
    print('you are a juvenile')
else:
    print('you are a adult')
print('you age is ' + str(age))
```
Python还提供了一种类似?:三元运算符的条件表达式：
```python
sex= input("what's you sex:")
clothes = 'trousers' if sex == 'man' else 'skirt'
```
***
*注意1：关键字if、条件和结尾的：必须位于同一行*
*注意2：和其他语言不同，Python使用缩进来指示语句所属的代码块，在同一个代码块中，所有语句的缩进量必须相同*
***
### 循环

* for循环
```python
#print 0~9
for i in range(10):
    print(i)
```
* while循环
```python
#pritn 0~9
i = 0
while i < 10:
    print(i)
    i = i + 1
```
* break与continue，break可以跳出当前循环块，continue将跳转到循环条件，略过本次循环的剩余语句

## 函数
### 定义
　如下所示，Python中的函数分为两个部分：函数头和函数体。函数头总是以关键字def开始，接着一个空格，后面是函数名以及参数列表，最后和if、循环语句一样以冒号：结束。函数体开始是可选的文档字符串，一般是以三引号包围的多行字符串（单行字符串也可以），第一行是函数的简介，接下来是详情和示例，我们可以使用help函数或者打印函数的\_\_doc\_\_变量看到他们。函数体包含一个*缩进*的代码块，注意*缩进*

```python
import math
def area(radius):
    ```求对应半径的圆形的面积
    示例：
    >>>area(1)
    3.1415926
```
    return math.pi*radius*radius
### 变量的作用域

```python
name = 'jack'
def changName1(newName):
    #创建了一个值为newName的局部变量，全局变量name不变
    name = newName

def changeName2(newName):
    #修改了全局变量name
    global name
    name = newName
```

### 函数的参数

　函数的参数按引用传递，而不是拷贝，也就是说实参和形参指向同一个值。但基本类型无法修改，因此只能修改引用的非基本类型。
　函数的参数可以设置默认值，但带默认值的参数不能位于没有默认值的参数的前面。默认值仅在def语句执行时计算，如果是对象或者其他非基本类型，则无论调用多少次其默认值都指向同一对象，此时存在副作用。
### 模块与名称空间
　模块其实就是一个包含了一系列功能函数的集合的Python源文件，它不含有执行的方法（main函数）。模块的命名空间就是源文件的文件名（不含后缀）。在模块的开始可以添加文件描述（一个字符串）。







  