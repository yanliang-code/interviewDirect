##### 一、问题

- ```javascript
  <script>
      // 优先执行同步任务，异步任务的优先级低
      // 同步任务
      console.log(1);
      // 异步任务（先挂起）
      setTimeout(function () {
          console.log(2);
      }, 0); // 浏览器小于指定秒数的，比如：指定秒数为4，小于4的都按照4秒延时
      // 同步任务
  	console.log(3);	
  </script>
  ```

- ```javascript
  	// 只打印A，由于下方的都是同步任务，所以一直在执行循环
    	//   console.log('A');
      //   while (true) {}
      //   console.log('B');
  ```

- ```javascript
  // 循环是同步任务，setTimeout会先放入浏览器的time模块中，等到执行指定延时时间到了
  // 再将其放入异步队列，等待事件循环来调用
  // 运行栈、任务队列、异步队列、time模块
  for (var i = 0; i < 100000; i++) {
      setTimeout(function () {
          console.log(i);
      }, 1000);
  }
  ```

- 如何理解JS的单线程（一个时间只能干一件事）

- 什么是任务队列（同步任务、异步任务）

- 什么是Event Loop

- 什么情况下会开启异步任务以及加入异步任务的时机



##### 二、解答

- 执行结果 1 3 2

  - 涉及知识点
    - js运行机制
    - 任务队列
      - 同步任务
      - 异步任务
        - 放入时间
        - 执行时间

- 什么是Event Loop

  1. <img src="D:\video\@@亮工学习资料\L140 - 前端跳槽面试必备技巧 面试官全流程指导（缺缺缺） - 266元\project\b1j6wg\pic\2020-10-18_090445.png" alt="2020-10-18_090445" style="zoom: 33%;" />

- 什么情况下会开启异步任务

  - setTImeout 和 setInterval
  - DOM 事件 （addEventListener，通过GUI线程来知道用户执行了什么操作）
    - 有的时候页面卡是，页面有同步任务在执行，这时你触发点击事件，
    - 浏览器还会继续执行同步任务，等待同步任务执行完，在去看异步队列中是否有待执行的，再去执行
  - ES6 的 Promise

  

  

