##### 一、题目

- 基本概念：DOM 事件的级别
- DOM 事件模型（就是冒泡、捕获）
- DOM 事件流
- 描述 DOM 事件捕获的具体流程
- Event 对象的常见应用
- 自定义事件

##### 二、解答

- DOM 标准定义的级别（DOM1标准中不涉及事件方面更新，所以没有）
  - DOM0   element.onclick = function(){} // 只能定义一个事件，多事件会互相覆盖
  - DOM2   elemet.addEventListener('click', function(){}, false) // 第三个参数false是冒泡、true是捕获
  - DOM3   elemet.addEventListener('keyup', function(){}, false) // 增加了一些事件类型、多了自定义事件
  - 注：其中 IE 浏览器的 addEventListener函数对就是 attachEvent函数.
- DOM 事件模型
  - 捕获：从上到下，直到目标元素
  - 冒泡：从目标元素向上
- DOM 事件流
  - 浏览器在当前页面与用户做交互过程中，用户点击了左键，点击这个事件如何传递到页面中，此过程就是事件流
  - 事件通过捕获到达目标元素（目标阶段），从目标元素冒泡到 window 元素
  - 完整事件流有三个阶段
    - 捕获
    - 目标阶段
    - 冒泡
- 描述 DOM 事件捕获的具体流程（26行）
  - 事件捕获的具体过程:
    - window对象接收事件 - document - html（document.documentElement） - body - 按照 html 结构向下传递 - 目标元素
  - 事件冒泡的具体过程:
    - 目标元素 - 根据 html 结构层层向上冒泡到 window
- Event 对象的常见应用
  - 用于获取用户的触发事件的相关信息
  - event.preventDefault()  阻止默认行为
  - event.stopPropagation()  阻止冒泡
  - event.stopImmediatePropation()  
    - 事件响应优先级  一个事件绑定两个函数a、b，想只触发a不触发b，在a函数内使用此函数即可
  - event.currentTarget  实际绑定触发事件的元素
    - 事件代理情况下，一般 currentTarget 为父级元素，target 为触发事件的子级元素（只有在代理事件的回调内能正常获取）
  - event.target 触发指定事件的目标元素
    - IE 中为 sourceElement
- 自定义事件（82行）
  - 必备条件
    - 创建事件对象  Event/CustomEvent（传入事件名称）
    - 监听指定dom的指定事件 addEventListener
    - 代码中有触发指定dom的指定事件的位置 dispatchEvent
  - 不可传参
    - Event
  - 可传参
    - CustomEvent