---
title: 关于go语言中panic/defer/recover
date: 2019-08-31 15:20:38
tags:
---
## defer的作用
类似其他语言的finally{}，可以非常方便地在获得资源之后直接defer释放资源，保证资源释放，或者其他的一些处理工作
## defer的执行时机
在函数体执行完成之后，回到调用点之前。这意味这你可以在defer中修改return的值
## 函数中出现了错误（panic）defer中能够执行到么
大部分情况下都可以。极端情况如内存耗尽这样的会直接结束程序。
## recover之后的函数返回值是什么？
这个问题是我最疑惑的，我们来使用一段代码实验一下：

```go
package main

import (
	"fmt"
)

func biggest(nums ...int) int {
	defer func(){
		if p := recover(); p != nil {
			fmt.Println("执行了recover", p)
		}
	}()
	result := 100
	for _, val := range nums {
		fmt.Println("handle:", val, result)
		if val == 3 {
			panic("不会数3")
		}
		if val > result {
			result = val
		}
	}
	return result
}

func main(){
	largest := biggest(1,2,3,4)
	fmt.Println("largest:", largest)
}
```
结果每次输出的最大值都是0。结论很明显：**panic之后的函数recover之后会返回返回类型的0值**，可以改变一下返回的类型试试
## 什么时候使用panic
**无法预期的** 错误，可预期的错误一般使用error返回值
## 什么时候使用recover
无法紧要的任务出错了，不想因此奔溃程序，可以使用recover仅仅记录一条日志
