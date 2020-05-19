---
title: 前端学习笔记1--W3school制作
date: 2019-12-1 17:22:45
tags:
categories: 前端
---

# 前言

这篇文章整理了我在制作一个w3school的静态网页时遇到的种种问题，主要是各种对齐问题以及flex布局的各种用法。

# 成果图



  <img src="C:/Program Files/hexo/source/_posts/前端学习笔记1—w3school制作/w3.gif"  >  

# 遇到的一些问题

## 建议以后每次写css前都设置

```css
.container {

 max-width: 1180px;

 margin: 0 auto;
}
```

## flex问题

* 自己制作的时候只要参考了 https://css-tricks.com/snippets/css/a-guide-to-flexbox/ A Complete Guide to Flexbox这个网页，里面把各个样式的布局都有介绍，虽然自己还不太会用。

* 自己做下来的时候主要用到的还是display-direction来控制主轴的方向以及justify-content: space-between来实现一些基础的布局。例如w3school正文部分的分三栏就是通过justify-content: space-between来实现的。不得不说比之前第一次写网页用position来绝对定位一点一点调强多了。

## 对齐问题

### 上下不同元素对齐问题

* 同一行元素想对齐只要设置横向的flex布局就可以实现
* 对于不同行元素的对齐，例如导航栏和正文要实现对齐，其实只要把两个元素的布局均设置成justify-content: space-between就可以实现了
* 如果只是上下行文本的对齐，其实可以div两个文本设置成 text-align: left ，然后用padding或margin慢慢调整至你想要的位置
* 关于正文中middle的图片在左，文字紧挨图片在右的布局实现
  1. div图片以及所有文字设置成横向flex布局
  2. div文字设置成竖向flex布局
  3. 调节文字的padding或margin使图片紧贴文字

## 居中问题

```
.parent {
  display: flex;
  height: 300px; /* Or whatever */
}
.child {
  width: 100px;  /* Or whatever */
  height: 100px; /* Or whatever */
  margin: auto;  /* Magic! */
}
```

 这取决于在flex容器中设置为“ auto”的边距会吸收额外空间的事实。因此，将垂直边距设置为`auto`会使项目在两个轴上完美居中。 

## 页面缩放隐藏一些元素的实现

这里要涉及到css3的媒体查询功能，下面直接上格式。

```css
@media not|only mediatype and (expressions) {
    CSS 代码...;
}
```

例如要实现本次的页面缩小隐藏左右两栏的效果（在页面小于1500px就会实现）

```css
@media screen and (max-width:1500px){
  .right{display:none; }
  }
```

# 后记

这是笔者第一篇前端笔记，也是第一次真正意义上自己写的blog，希望能坚持学习前端，并坚持写笔记下去吧。

明天要考高数了，赶快复习去吧。（逃）

还有下个星期的acm集训队新生选拔，冲冲冲！

