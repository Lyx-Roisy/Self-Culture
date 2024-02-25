[学习体会](https://www.notion.so/4b337fed53fc4d16b494da657f61ef18?pvs=4)

# 基础

## 基础语法

- `#` id选择器
- `.` class 选择器
- `[]` 属性选择器
    
    ```css
    input[name="password"]
    ```
    
    上面选择了 `name` 属性值为 `password` 的 `input` 元素。
    

## 常设参数

### margin相关

- *`auto`*  自适应，一般居中
- 0 重置一些浏览器的默认设置，从而去掉水平滚动条

```css
/* 居中对齐 2个值-前一个值代表上下,后一个值代表左右 4个值-上右下左*/
margin: 1em auto;
margin: 0 auto;
```

### display相关

- *`block`* 设置为换行元素
- *`inline-block`* 设置为行内元素

### overflow相关

设置元素溢出时所需的行为

- `visible` 内容不能被裁减并且可能渲染到边距盒（padding）的外部
- `hidden` 如果需要，内容将被裁减以适应边距（padding）盒
- `scroll`

## 常用单位

- *`rem`* ：与 `html` 元素的字体大小有关，常在`margin`中用到
- *`vh`*：常在height中使用，

# 核心

## *盒子模型*

每个 HTML 元素都是一个盒子，它拥有着自己的间距和边框，这叫作“盒子模型”，一般用<div class=” “>划分盒子，再在CSS文件中通过类选择器设计样式

### *弹性盒子*

***Flexbox*** 是一种一维 CSS 布局方法，侧重于**内容的流动**。 它提供了控制容器在容器中的间隔和对齐方式的能力。

- 将元素变成一个 *flex 容器：*`display` 属性设置为 `flex`
- 常设属性
    - 主轴：*`flex-direction`*
    - 是否允许换行：*`flex-wrap`*
    - 相对主轴对齐方式：*`justify-content`*
    - 相对交叉轴对齐方式：*`align-items`*
    - 图像适应方式：*`object-fit`*
    - 间距：*`gap`*

# 实操注意

- 为了更好地可视化元素的大小，添加边框可能会有所帮助

## 关于盒子模型默认设置的更改

### *box-sizing*

在盒子模型的默认定义里，所设置的 width 与 height 只会应用到这个元素的内容区。如果这个元素有任何的 border 或 padding ，绘制到屏幕上时的**盒子宽度、高度会加上设置的边框和内边距值**。

box-sizing 属性可以用来调整这一默认定义

- **border-box** ：**设置的边框和内边距的值是包含在 width 内的**。大多数情况下，这使得我们更容易地设定一个元素的宽高。

```css
* {
  box-sizing: border-box;
}
```

## 零散常用操作

### 改块元素为内联元素

```css
.class p {
  display: inline-block;
}
```

- 在HTML文件里就把几个p元素写在一行，之间不要有间隔
    
    ```html
    <p class="flavor">French Vanilla</p><p class="price">3.00</p>
    ```
    
    ```css
    .flavor {
      text-align: left;
      width: 50%;
    }
    
    .price {
      text-align: right;
      width: 50%;
    }
    ```
    

### 超链接不同状态颜色设置

```css
/* 未访问 */
a:link {
  color: black;
}
/* 已访问 */
a:visited {
  color: black;
}
/* 悬停 */
a:hover {
  color: brown;
}
/* 点击 */
a:active {
  color: brown;
}
```

### 选择/创建特定类型的最后一个元素

使用 `last-of-type` CSS 伪类

```css
p:last-of-type { }
```

`::after` 用来创建一个伪元素，作为已选中元素的最后一个子元素。 可以用它在最后一个图像后添加一个空元素