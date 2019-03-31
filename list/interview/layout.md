> 布局类题目

## 不固定宽高子元素在父元素内水平垂直居中的多种方法

```css
//first
.fa{		
	width:400px;
	height: 400px;
	background-color: skyblue;
	position: relative;
}
.son{
  position: absolute;
  top:50%;
  left:50%;
  transform: translate(-50%,-50%);
}
//second
.box{		
	width:400px;
	height: 400px;
	background-color: skyblue;
  position: relative;
}
.content{
  position: absolute;
  top:0;
  left:0;
  right:0;
  bottom: 0;
  width:50%;
  height:50%;
  margin: auto;
}
```

## 圣杯布局
```html
<!-- 结构代码 -->
<div class="container">
    <div class="middle">
        <h4>我是middle</h4>
        <p>我是内容部分我是内容部分我是内容部分我是内容部分我是内容部分我是内容部分我是内容部分我是内容部分</p>
    </div>
    <div class="left">
        <h4>我是left</h4>
        <p>我是left的内容</p>
    </div>
    <div class="right">
        <h4>我是right的内容</h4>
        <p>我是right的内容</p>
    </div>
</div>
```
```css
/* 样式代码 */
/* 浮动加定位 */
*{margin:0;padding:0;}
body{background-color: #cccc;text-align:center;}
header{height:50px;background-color: pink;line-height:50px;}
.container{padding:0 220px 0 200px;}
.middle,.left,.right{
    position:relative;
    float: left;
    min-height: 300px;
    }
.middle{background-color: red;width:100%;}
.left{width:200px;background-color: yellow;margin-left:-100%;left:-200px;}
.right{width:220px;background-color: blue;margin-left:-220px;right:-220px;}
/* 弹性布局 */
.container{
    display: flex;
    flex:1;/*简写，1,1，auto的意思*/
  }
  .middle{
    flex:1;
  }
  .left, .right{
    flex: 0 0 50px;/*默认为横向的，所以这里的50px相当于宽度*/
    background-color: red;
  }
  .left{
    order:-1;
  }
```