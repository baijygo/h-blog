# callback 回调

- 回调是解决异步问题比较老的一种方式, 也是使用很多的一种方式.我们大致从一些维度认识一下回调

- 回调是一种处理特定问题的模式, 伴随着函数式编程而生. 函数式编程最主要的技术之一就是回调函数
- 函数作为一等功民的[函数式编程](/programming-paradigm/index.md)中, 函数可以作为参数进行传递(回调), 也可以作为返回值提供给外部(函数生成器: thunk, currying).
- 当一个函数作为主调函数的参数时, 它往往会在特定的时间和场景(上下文)执行.
- 执行过程中,回调函数选择性接收函数内部的数据, 或者状态(内存), 经过处理选择性返回,或者改变状态.
- 回调函数不是由该函数实现方来直接调用，而是在特定的时间或者在特定的条件下由另外一方调用的，对某一事件或条件进行响应。
- 这个机制很类似 hook, 我们称之为回调.
- In computer programming, a callback is a reference to a piece of executable code that is passed as an argument to other code. --维基百科


---


<!-- ## 语法通式

```javascript
function call (args, cb) {
    // ...
    const re = cb(args, ...);
    // ...
}
``` -->
---



---

## chat shell
> '浮于表层的闲谈'.  选看.一直找不到比较合适的词汇.看官见谅

- 你觉得回调很 low ,可能是因为: 实现回调函数就像传递一般的参数变量一样简单.由于函数式编程极好的支持,以至于这项技术使用基本没有障碍.
- 没有使用障碍导致回调的滥用, 大部分问题都用了简单的回调堆叠来解决. 实际上我们有很多基于回调的模式可以避免这些问题.比如: cps, cps 进一步转化为 thunk.等等.

- C++, C 中的回调: 回调函数就是一个通过函数指针调用的函数。如果把函数的指针作为函数参数传递给另一个函数，当这个函数指针作为调用者而指向某个函数时，这就是回调函数。
- 回调和异步没关系. 回调能处理多种场景,异步是其中之一.
- 当我们遇到回调无底洞的时候，无需惊慌,其实这根本不是什么问题: 因为同样有协程和 monad 无底洞。因为如果你把任何一个抽象使用地足够频繁的话，都同样会创造一个无底洞。

> 说了这么多,回调到底有没有问题呢? 答案是有, 而且很大.

- 使用回调处理异步往往意味着,你舍弃了返回值,而使用回调接收异步操作结果. 而这正是用回调风格来编程会很困难的根本原因: 回调风格不返回任何值，所以难以组合[函数式编程中函数有良好的输入和输出是函数可以组合的根本]。
- 一个没有返回值的函数执行的效果其实是利用它的副作用
- 一个没有返回值和利用副作用的函数其实就是一个黑洞。
- 所以，使用回调风格来编程无法避免会是指令式的，它实际上是通过把一系列严重依赖于副作用的操作安排好执行顺序，而不是通过函数的调用来把输入输出值对应好。
- 如果你是通过人手组织程序执行流程, 而不是靠理顺值的关系来解决问题的, 是很难编写出正确的并行程序

- 回调难于调试,回调的执行,你想要的结果数据以及你的代码书写逻辑存在时间上的'中断', 你的逻辑难免随着这种中断而出现断层

> 为什么出现新的方案解决异步

- 以往的异步处理方案, 大多是回调的变种, 或者干脆使用一些发布订阅之类的模式.但是 promise 不同
- 基于 promise 的函数总是让你把函数返回值作为一个不依赖于时间的值来考虑的。当你调用一个回调风格的函数时，在你的函数调用和它的回调函数被调用之间，在程序里面我们没办法找到一个最终结果的表现形式.

- 一种新的方案的出现,并被推为主流, 往往不是因为他有绝对的优势, 而是因为原来的方案存在不可调和的问题.


> 回调的优化方案

## 引用&参考

- [http://blog.csdn.net/luozhonghua2014/article/details/45651659](http://blog.csdn.net/luozhonghua2014/article/details/45651659)
-[大神博客https://segmentfault.com/a/1190000000356347](https://segmentfault.com/a/1190000000356347)
