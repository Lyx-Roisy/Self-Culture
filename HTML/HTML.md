[学习体会](https://www.notion.so/f45a8e89e915423187aa9677db065989?pvs=21)

[关于表单](https://www.notion.so/e3ec7a9f32f1489d97c4dd75068706d8?pvs=21)

# 核心概念

- **_元素_**：开始标签、内容、结束标签三部分组成的整体
- **_属性_**：是写在一个元素的开始标签中的特殊词汇，它们用于控制这个元素的行为

## 基本结构

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <link rel="stylesheet" href="styles.css" />
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title> </title>
  </head>
  <body>
    <main>
      <section>
        <h1>
          <article>
            <p></p>
          </article>
        </h1>
      </section>
    </main>
  </body>
</html>
```

# 常用标签及属性

## “规范性“标签

### `<!DOCTYPE html>`

所有页面都应以其开头，被称为*声明*，确保浏览器尝试满足行业范围的规范

## “功能性”标签

### _`img`_

- 注意它是**自闭合**标签（无结束标签）
- 常用属性：`alt`（替代文本）、`src`

### _`a`_

**_锚点元素（超链接）_**，链接到另一个页面

- 常用属性：`href` 、
  - `target`  规定在何处打开链接
    - `_blank`  在新窗口中打开

### _`ul` & `ol`_

**_无序&有序列表_**

### _`li`_

**_列表项_**

### _`form`_

_表单_

- 常用属性：`action` （指示应将表单数据发送到哪里）
  - `method`  规定如何发送表单数据
    - 常用参数：
      - get：**将表单数据以名称/值对的形式附加到 URL 中**，对于用户希望将结果加为书签的表单提交很有用，**更适合非安全数据**
      - post：**在 HTTP 请求的正文中附加表单数据**（数据不会显示在 URL 中）**，适合敏感数据**

### _`input`_

- 注意它是**自闭合的、内联的**
- 常用属性：`placeholder` ，`required` （注意该属性无属性值，代表“必填”），`checked`（注意该属性无属性值，代表“使该复选框或单选按钮默认被选中”）
  - `type`  创建多种输入
    - text：文本，表单数据将为输入的内容
    - radio：单选，表单数据将为`name` / `value` 属性对
    - checkbox：复选框，表单数据将为`name` / `value` 属性对
  - `name`  指定输入数据的存放位置，或者说指明数据”属性“
    - 可以用于限制单选，通过**给每一个单选按钮添加相同的  `name`  属性以关联单选按钮**
  - `value`  设置 input 的数据值
    - 常在`type=radio`时使用
- 距离父级  `form`  元素最近的第一个  `type`  为  `submit`  的  `input`  元素会被当作提交按钮
  ```html
  <input type="submit" value="Submit" />
  ```

### _`label`_

帮助将  `input`  、`select`等元素的文本与元素本身关联起来，**默认是行内元素**

- 用法
  1. 套在`input`外面
  2. 套在`input`的文本外面，并添加与  `input` 的  `id` 具有相同值的  `for` 属性

### _`button`_

单击没有任何属性的表单按钮的默认行为会将数据提交到表单的  `action`  属性中指定的位置

- 注意它是**内联的**
- 常用属性：`type`

### _`select`_

给表单添加一个下拉列表

`select`  是包含一组  `option`  元素的容器，`option`  元素就是下拉列表的内容

### _`option`_

- 每一个  `option`  需要指定一个  `value`  属性。 如果没有指定，向服务器默认提交的是  `option`  内的文本

### _`textarea`_

- 和  `text`  类型的  `input`  类似，区别是 `textarea` 有一些额外的好处，比如可以方便地添加更多的文本以及设置默认显示的行数和列宽。

### `<span>`  与 `<div>`

- `<div>`是块级元素，而  `<span>`  是行内元素

## “美化性”标签

- _`main`  正文_
- _`footer`  页脚_
- _`article` 信息内容_
- _`div`  用于设计布局_
  - 常用属性：`class`
- _`em`斜体_
- _`strong`  加粗_
- _`figure`独立引用内容_
  - _`figcaption`： 说明_
- _`fieldset`  块级元素_（划分内容）
  - _`legend` ：`fieldset`_ 元素中内容的*标题*
- _`hr`  分隔符_
  - 注意是**自闭合标签**
