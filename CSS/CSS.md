# CSS
- `#` id选择器
- `.` class 选择器

## 常设参数

### margin相关

- `auto`

## 常用操作

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