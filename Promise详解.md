# Promise详解
[TOC]
## 简介
Promise是新标准引入的一个特性，我们在之前的笔记中看到javascript都是以同步的方式执行，有着严格的先后顺序。Promise是Javascript提供的一种简单的异步执行方式。先让我们看一下标准的Promise使用的方式：
```js
var promise = new Promise(function(resolve, reject){
    var rr = Math.random();
    if(rr>0.5){
        resolve("god knows");
    }else{
        reject("unhappy without reason");
        throw "reject"
    }
});
promise.then(function(msg){
    console.log("pass msg:", msg);
}, function(msg){
    console.log("reject reason:", msg);
});
```
## Promise的状态

 > 引用自MDN

Promise拥有三种状态pending、resolved和rejected（对应未完成、已完成和执行失败），初始状态是pending。根据Promise初始化的参数函数的执行情况来转换Promise状态，如果函数抛出异常或者调用了reject方法则Promise转为rejected状态，如果函数调用了resolve方法则Promise转为resolved状态，否则Promise会一直处于pending状态。

## Promise的方法（非原型方法）
* Promise.all(iterator)
   这个方法返回一个新的promise对象，该promise对象在iterable里所有的promise对象都成功的时候才会触发成功，一旦有任何一个iterable里面的promise对象失败则立即触发该promise对象的失败。这个新的promise对象在触发成功状态以后，会把一个包含iterable里所有promise返回值的数组作为成功回调的返回值，顺序跟iterable的顺序保持一致；如果这个新的promise对象触发了失败状态，它会把iterable里第一个触发失败的promise对象的错误信息作为它的失败错误信息。Promise.all方法常被用于处理多个promise对象的状态集合。
* Promise.race(iterable)
   当iterable参数里的任意一个子promise被成功或失败后，父promise马上也会用子promise的成功返回值或失败详情作为参数调用父promise绑定的相应句柄，并返回该promise对象。

## Promise的原型方法
* Promise.prototype.catch(onRejected)
   添加一个否定(rejection) 回调到当前 promise, 返回一个新的promise。如果这个回调被调用，新 promise 将以它的返回值来resolve，否则如果当前promise 进入fulfilled状态，则以当前promise的肯定结果作为新promise的肯定结果.
* Promise.prototype.then(onFulfilled, onRejected)
   添加肯定和否定回调到当前 promise, 返回一个新的 promise, 将以回调的返回值 来resolve.

## Promise的用途和优点
在浏览器页面执行js永远是单线程的，如果需要执行一些耗时的操作容易造成网页卡顿，使用Promise可以很好地解决这个问题。因为Promise能够阻止异常的传递，在执行一些高风险的方法时（尤其是涉及到资源请求、操作数据等）能够比trycatch更优雅地解决问题，使得逻辑更加清晰简单。

## 名词表
* 同步：可以简单理解为代码以固定的顺序执行
* 异步：和同步不一样，代码的执行顺序不固定
* 回调：因为触发了某个条件（节点），某个事先注册好的函数被调用了

[参考文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)