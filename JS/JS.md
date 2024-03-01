# 实操注意

- 尽量少使用内联 JS，而是统一写到单独的.js 文件中。内联 JS 会污染 HTML，而且效率低下

# 概述

- JavaScript 的一个非常常见的用途是**通过[文档对象模型 API](https://www.notion.so/b396d9cfd337430db8f422932af8187e?pvs=21) ，动态修改 HTML 和 CSS**
  - 因此需要注意代码顺序，如果 JavaScript 先于要修改的 HTML 和 CSS 加载和运行，则可能发生错误 （结合[脚本调用](https://www.notion.so/JS-7a107338dcf64c6d8989a7561113958b?pvs=21)部分理解）
- JavaScript 中一切都是对象。对象是存储在单个分组中的相关功能的集合

## 内部与外部 JS

- 内部：在`<head>`元素中添加`<script>`元素，在`<script>`元素中编写 JS 代码
- 外部：在`<head>`元素中添加
  ```html
  <script src="script.js" defer></script>
  ```
  在同目录 script.js 文件中编写 JS 代码

## 脚本调用

![async-defer.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/b40ddca8-1c99-440a-b5eb-1d9a452cb058/45bdedb1-7c36-4433-ac4f-886ef4fdff67/async-defer.jpg)

- `async`  和  `defer`  都指示浏览器在一个**单独的线程**中下载脚本，而页面的其他部分（DOM 等）正在下载，因此在获取过程中页面加载不会被阻塞。
- 如果脚本**无需等待页面解析，且无依赖独立运行**，那么应使用  `async`。
- 如果脚本**需要等待页面解析，且依赖于其他脚本**，调用这些脚本时应使用  `defer`，将关联的脚本按所需顺序置于 HTML 的相应  `<script>`  元素中。

# 基础语法

## 数据表示

- 创建变量 `let`
  - JS 是“动态类型语言”，不需要指定变量的数据类型，它可以是变化的
- 创建常量 `const`
- 例
  ```jsx
  let randomNumber = Math.floor(Math.random() * 100) + 1;
  const guesses = document.querySelector(".guesses");
  ```

## 函数

- 创建函数 `function`

## 字符串

- `replace()` 替换子字符串 注意如果要修改原变量，还要进行赋值操作
  - 例
    ```jsx
    newStory = newStory.replace(":insertx:", xItem);
    ```

### 模板字面量

使用反引号声明的字符串

- 属性
  - 可以嵌入 JS
  - 可以为多行
- 用法
  - 串联：可以在  `${ }`  中包装 JavaScript **变量或表达式**，其结果将被包含在字符串中
  - 例
    ```jsx
    const name = "克里斯";
    const greeting = `你好，${name}`;
    console.log(greeting); // "你好，克里斯"
    ```

## 运算与条件判断

- `===` 相等`!==` 不相等 注意和其他语言区别，是三个等号！！
  - `==`和`!=`也是运算符，但只能测试值是否相同，数据类型可能不同
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b40ddca8-1c99-440a-b5eb-1d9a452cb058/dca03b31-1982-4135-b827-4b783e16849e/Untitled.png)

## 数组

- 增删元素 `push()` `pop()` (作用于数组结尾) 、`unshift()` `shift()` (作用于数组开头)
- 取数组中随机元素`randomValueFromArray()`

## 事件

- 检查元素的属性 `getAttribute(name)`
- 设置元素的属性`setAttribute(name, value)`
  - 文本属性`textContent` 直接赋值就可

### 添加监听器 `EventTarget.addEventListener()`

- 常用的参数列表为`(type, listener)`
  - `type`事件类型：`"click"、"mouseover"、"keydown"`等等
  - `listener` ：一个实现了  `EventListener`  接口的对象，或者是一个函数
- 移除监听器 `removeEventListener`

### 事件对象

表示为`event`、`evt`  或  `e` ，被自动传递给事件处理函数，以提供额外的功能和信息

- 大多数事件对象有**与该特定类型的事件相关的额外属性**（具体使用时查询），如事件对象  `e`  的  `target`  属性始终是事件刚刚发生的元素的引用

### 事件冒泡

事件从**最内层元素起**冒泡而出（子元素 → 父元素）

- `stopPropagation()` 防止事件向任何其他元素传递
- 例
  ```jsx
  video.addEventListener("click", (event) => {
    **event.stopPropagation();**
    video.play();
  });

  box.addEventListener("click", () => box.classList.add("hidden"));
  ```

### 事件捕获

事件从**最外层元素起**直到达到目标（父元素 → 子元素）

- 默认是禁用的，需要在  `addEventListener()`  的  `capture`  选项中启用

### 事件委托

当想在用户与子元素中的任一个互动时运行一些代码时，我们在它们的父元素上设置事件监听器，**让发生在子元素身上的事件冒泡到它们的父元素上**，而不必在每个子元素上单独设置事件监听器

- 关键：使用  `event.target`  来获取事件的目标元素（也就是子元素，获取父元素使用`event.currentTarget`）

## 循环

### `for...in` VS `for...of`

`for...in`  循环遍历的结果是数组元素的下标，而  `for...of`  遍历的结果是元素的值

```jsx
let arr = [3, 5, 7];
arr.foo = "hello";

for (let i in arr) {
  console.log(i); // 输出 "0", "1", "2", "foo"
}

for (let i of arr) {
  console.log(i); // 输出 "3", "5", "7"
}

// 注意 for...of 的输出没有出现 "hello"
```

### 定时循环

- 指定周期调用 `setInterval`
  ```jsx
  var span = document.getElementsByTagName("span")[0];
  //会返回一个值，可以用来关闭此循环
  var int = setInterval(function () {
    var date = new Date();
    span.innerText = date.toLocaleTimeString();
  }, 1000);
  ```
  - **`clearInterval(参数)`** 关闭定时循环
- 指定时间调用
  ```jsx
  setTimeout(function () {
    var img = document.getElementsByTagName("img")[0];
    img.src = "img/1.jpg";
  }, 3000);
  ```

# 调试

- `console.log()`  把值打印到控制台
