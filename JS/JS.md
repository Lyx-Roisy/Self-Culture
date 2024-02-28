# 实操注意

- 尽量少使用内联JS，而是统一写到单独的.js文件中。内联 JS 会污染 HTML，而且效率低下

# 概述

- JavaScript 的一个非常常见的用途是**通过[文档对象模型 API](https://www.notion.so/DOM-b396d9cfd337430db8f422932af8187e?pvs=21) ，动态修改 HTML 和 CSS**
    - 因此需要注意代码顺序，如果 JavaScript 先于要修改的 HTML 和 CSS 加载和运行，则可能发生错误 （结合[脚本调用](https://www.notion.so/JS-7a107338dcf64c6d8989a7561113958b?pvs=21)部分理解）
- JavaScript 中一切都是对象。对象是存储在单个分组中的相关功能的集合

## 内部与外部JS

- 内部：在`<head>`元素中添加`<script>`元素，在`<script>`元素中编写JS代码
- 外部：在`<head>`元素中添加
    
    ```html
    <script src="script.js" defer></script>
    ```
    
    在同目录script.js文件中编写JS代码
    

## 脚本调用

![async-defer.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/b40ddca8-1c99-440a-b5eb-1d9a452cb058/45bdedb1-7c36-4433-ac4f-886ef4fdff67/async-defer.jpg)

- `async` 和 `defer` 都指示浏览器在一个**单独的线程**中下载脚本，而页面的其他部分（DOM 等）正在下载，因此在获取过程中页面加载不会被阻塞。
- 如果脚本**无需等待页面解析，且无依赖独立运行**，那么应使用 `async`。
- 如果脚本**需要等待页面解析，且依赖于其他脚本**，调用这些脚本时应使用 `defer`，将关联的脚本按所需顺序置于 HTML 的相应 `<script>` 元素中。

# 基础语法

## 数据表示

- 创建变量 `let`
    - JS是“动态类型语言”，不需要指定变量的数据类型，它可以是变化的
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
        newStory = newStory.replace(':insertx:', xItem);
        ```
        

### 模板字面量

使用反引号声明的字符串

- 属性
    - 可以嵌入JS
    - 可以为多行
- 用法
    - 串联：可以在 `${ }` 中包装 JavaScript **变量或表达式**，其结果将被包含在字符串中
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

- 增删元素 `push()` `pop()` (作用于数组结尾)  、`unshift()` `shift()` (作用于数组开头)
- 取数组中随机元素`randomValueFromArray()`

# 调试

- `console.log()` 把值打印到控制台