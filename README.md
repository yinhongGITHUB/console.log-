# 学习笔记：有趣的 console.log 打印问题

问：在使用 console.log 输出 foo1 时，改变输出数据（即：将对象 foo1 的 bar 从 1 改成 2），再次使用 console.log 输出对象 foo1，两次输出是什么？

答：既有可能是 2 也有可能是 1，想不到吧！！！不管回答 1，2 都不准确哦

# 1.代码重现

```js
eg:
      let foo1 = {
        bar: 1,
      };
      console.log(foo1);// foo1.bar是1呢?，还是2呢?
      foo1.bar++;
      console.log(foo1);// foo1.bar是1呢?，还是2呢?
```

# 2.步骤分析

2.1 当默认浏览器打开时,如下图：

![image](https://github.com/yinhongGITHUB/console.log-/blob/main/imgs/first.png)

2.2 点击展开对象，如下图：

![image](https://github.com/yinhongGITHUB/console.log-/blob/main/imgs/second.png)

2.3 这里可以看到，先打印的 foo1 里面的 bar 居然也变了，神奇之旅就此开始。此时刷新页面。

![image](https://github.com/yinhongGITHUB/console.log-/blob/main/imgs/thirdly.png)

怎么回事？居然又恢复正常了，第一个 console 打印 foo1 的 bar 确实应该为 1。

# 技术总结

在第一次默认浏览器打开页面的时候（即步骤 2.1），chrome 会对 log 的对象求一次值，打印出来是 Object ，可以继续展开的。但当你展开控制台中的 Object 的时候（即步骤 2.2），chrome 又会对它求一次值，
这一次是显示它的属性。所以才会有前后打印的东西不一样的情况发生，因为对象引用的实体的值改变了.

# 个人总结

实在很难想到，当你看到未展开的对象时，它是你想要的值，但是当你真正想去看他的时候，浏览器却再作了一次求值操作。导致出现了意料之外的情况。也不要单纯的认为 console 就是打印最终值哦，所以说控制台还是不可信，毕竟浏览器的“花花肠子太多了”。
