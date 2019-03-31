> 一些常用的基础知识

## 结构伪类选择器
```css
/* 第一个子元素 */
:first-child{}

/* 最后一个子元素 */
:last-child{}

/* 前三个子元素 */
:nth-child(-n+3){}

/* 奇数子元素 */
:nth-child(odd){}

/* 偶数子元素 */
:nth-child(even){}
``

## 目标伪类选择器
```css
/* 当锚链接触发是生效 */
:target:{
  color:red;
}
```

## 伪元素选择器
```css
/* 元素之后 */
::after{}
/* 元素之前 */
::before{}
```

## 伪类选择器
```css
/* a标签的样式，低版本ie不兼容 */
a:link{}
/* a标签访问后 */
a:visited{}
/* a激活 */
a:active{}
/* 鼠标悬停样式 */
div:hover{}
/* 获取焦点样式 */
input:focus{}
```

## 属性选择器
```css
/* 类名位nav的元素 */
[class="nav"]{}
/* 类名位nav并且id为true的元素 */
[class="nav"][id="true"]{}
/* 类名以a开头的元素 */
[class^="a"]{}
/* 类名以z结尾的元素 */
[class$="z"]{}
/* 类名包含n的元素 */
[class="n"]{}
```