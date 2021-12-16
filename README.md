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

当默认浏览器打开时,如下图
![image](https://github.com/yinhongGITHUB/console.log-/blob/main/imgs/first.png)
