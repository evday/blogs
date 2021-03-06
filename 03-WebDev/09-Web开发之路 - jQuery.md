# Web开发之路 - jQuery
<!-- TOC -->

- [Web开发之路 - jQuery](#web开发之路---jquery)
    - [介绍  🍀](#介绍--🍀)
    - [$符号  🍀](#符号--🍀)
    - [jQuery查找  🍀](#jquery查找--🍀)
        - [选择器  🍀](#选择器--🍀)
        - [筛选器  🍀](#筛选器--🍀)
    - [jQuery操作  🍀](#jquery操作--🍀)
        - [属性  🍀](#属性--🍀)
        - [CSS  🍀](#css--🍀)
        - [文本操作  🍀](#文本操作--🍀)
        - [文档处理  🍀](#文档处理--🍀)
        - [事件  🍀](#事件--🍀)
        - [效果  🍀](#效果--🍀)
        - [扩展  🍀](#扩展--🍀)

<!-- /TOC -->
## 介绍  🍀

为了使写更少的代码完成更多的功能 , JavaScript (helper) 库应运而生 , 这些JavaScript库常被成为JavaScript框架

广受欢迎的JavaScript框架如下 : 

- jQuery
- Prototype
- MooTools

jQuery是目前最受欢迎的JavaScript框架 , jQuery库包含以下功能 : 

- HTML元素选取
- HTML元素操作
- CSS操作
- HTML事件函数
- JavaScript特效和动画
- HTML DOM 遍历和修改
- AJAX
- Utilities

除此之外 , jQuery还提供了大量的插件 , jQuery受欢迎与其**兼容性**是密不可分的

**下载jQuery**

```
http://jquery.com/download/
```

jQuery库是一个JavaScript文件 , 所以可以直接使用`<script>` 标签引用

```html
<script src="jquery-1.10.2.min.js"></script>
```

也可通过CDN (内容分发网络) 进行引用

```html
<!-- 菜鸟教程CDN -->
<script src="http://cdn.static.runoob.com/libs/jquery/1.10.2/jquery.min.js"></script>
<!-- 百度CDN -->
<script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
<!-- Google CDN -->
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js"></script>
<!-- Microsoft CDN -->
<script src="http://ajax.htmlnetcdn.com/ajax/jQuery/jquery-1.10.2.min.js"></script>
```

## $符号  🍀

`$`是jQuery符号  , jQuery把所有功能全部封装在一个全局变量`jQuery`中 , 而`$`也是一个合法的变量名 , 它是变量jQuery的别名

```javascript
window.jQuery; // jQuery(selector, context)
window.$;      // jQuery(selector, context)
$ === jQuery;  // true
typeof($);     // 'function'
```

`$`本质上就是一个函数 , 但是函数也是对象 , 于是`$`除了可以直接调用外 , 也可以有很多其他属性

**PS : 如果`$`变量被占用了 , 那么我们就只能使用`jQuery`这个变量了**

> **jQuery对象**

jQuery对象就是通过jQuery包装DOM对象后产生的对象 , jQuery对象是jQuery独有的 , 如果一个对象是jQuery对象 , 那么它就可以使用jQuery里面的方法 , 如 : `$("test").html();`

约定 : 如果获取的是jQuery对象 , 那么要在变量前面加上`$`

```javascript
var $variable = jQuery对象
var variable = DOM对象
```

**PS : 虽然jQuery对象是包含DOM对象后产生的 , 但是jQuery无法使用DOM对象的任何方法 , 同理DOM对象也不能使用jQuery里的方法** 

> **jQuery语法**

语法 : `$(selector).action()`

- 美元符号定义 jQuery
- 选择符(selector)"查询"和"查找" HTML 元素
- jQuery 的 action() 执行对元素的操作

## jQuery查找  🍀

### 选择器  🍀

1. **ID**

   ```javascript
   $('#test')  // id="test"
   ```

2. **Class**

   ```javascript
   $(".c1")  // class="c1"
   ```

3. **标签**

   ```javascript
   $('p')  // 所有p标签
   ```

4. **组合**

   ```javascript
   $('a')
   $('.c2')
   $('a,.c2,#i10')
   ```

5. **层级**

   ```javascript
   $(".outer div")  //后代,子子孙孙
   $(".outer>div")  //子元素
   $(".outer+div")  //相邻,同一父元素
   $(".outer~div")  //包含
   ```

6. **基本**

   ```javascript
   :first  //第一行
   :last  //最后一行
   :eq()  //匹配一个给定索引值的元素
   ```

7. **属性**

   ```javascript
   $('[Lyon]')       //具有Lyon属性的所有标签
   $('[Lyon="123"]') //Lyon属性等于123的标签
   ```

左侧菜单实例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>left_menu</title>

    <script src="js/jquery-2.2.3.js"></script>
    <script>
          function show(self){
              //console.log($(self).text())
              $(self).next().removeClass("hide")
              $(self).parent().siblings().children(".con").addClass("hide")
          }
    </script>
    <style>
          .menu{
              height: 500px;
              width: 30%;
              background-color: gainsboro;
              float: left;
          }
          .content{
              height: 500px;
              width: 70%;
              background-color: rebeccapurple;
              float: left;
          }
         .title{
             line-height: 50px;
             background-color: #425a66;
             color: forestgreen;}
         .hide{
             display: none;
         }
    </style>
</head>
<body>
    <div class="outer">
        <div class="menu">
            <div class="item">
                <div class="title" onclick="show(this);">菜单一</div>
                <div class="con">
                    <div>111</div>
                    <div>111</div>
                    <div>111</div>
                </div>
            </div>
            <div class="item">
                <div class="title" onclick="show(this);">菜单二</div>
                <div class="con hide">
                    <div>111</div>
                    <div>111</div>
                    <div>111</div>
                </div>
            </div>
            <div class="item">
                <div class="title" onclick="show(this);">菜单三</div>
                <div class="con hide">
                    <div>111</div>
                    <div>111</div>
                    <div>111</div>
                </div>
            </div>
        </div>
        <div class="content"></div>
    </div>
</body>
</html>
```

### 筛选器  🍀

```javascript
$('#i1').next()
$('#i1').nextAll()
$('#i1').nextUntil('#ii1')
$('#i1').prev()
$('#i1').prevAll()
$('#i1').prevUntil('#ii1')
$('#i1').parent()
$('#i1').parents()
$('#i1').parentsUntil()
$('#i1').children()
$('#i1').siblings()
$('#i1').find()
$('li:eq(1)')
$('li').eq(1)
first()
last()
hasClass(class)
```

## jQuery操作  🍀

### 属性  🍀

```javascript
// 专门用于做自定义属性
$(..).attr('n')
$(..).attr('n','v')
$(..).removeAttr('n')
// 专门用于chekbox,radio
$(..).prop('checked')
$(..).prop('checked', true)
```

### CSS  🍀

```javascript
$('t1').css('样式名称', '样式值')
//位置
$(window).scrollTop()  // 获取
$(window).scrollTop(0) // 设置
scrollLeft([val])
offset().left                 // 指定标签在html中的坐标
offset().top                  // 指定标签在html中的坐标
position() 	                  // 指定标签相对父标签(relative)标签的坐标
$('i1').height()           // 获取标签的高度 纯高度
$('i1').innerHeight()      // 获取边框 + 纯高度 + ？
$('i1').outerHeight()      // 获取边框 + 纯高度 + ？
$('i1').outerHeight(true)  // 获取边框 + 纯高度 + ？
```

### 文本操作  🍀

```javascript
$(..).text()           // 获取文本内容
$(..).text("<a>1</a>") // 设置文本内容
$(..).html()
$(..).html("<a>1</a>")
$(..).val()
$(..).val(..)
```

### 文档处理  🍀

```javascript
// 内部插入
$("#c1").append("<b>hello</b>")
$("p").appendTo("div")
prepend()
prependTo()
// 外部插入
before()
insertBefore()
after
insertAfter()
replaceWith()
remove()
empty()
clone()
```

### 事件  🍀

```javascript
jQuery：
$('.c1').click()
$('.c1').bind('click',function(){})
$('.c1').unbind('click',function(){})
$('.c').delegate('a', 'click', function(){})
$('.c').undelegate('a', 'click', function(){})
$('.c1').on('click', function(){})
$('.c1').off('click', function(){})
// 阻止事件发生
return false
// 当页面框架加载完成之后，自动执行
$(function(){
  $(...)
})
```

拖动面板实例

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
    <div style="border: 1px solid #ddd;width: 600px;position: absolute;">
        <div id="title" style="background-color: black;height: 40px;color: white;">
            标题
        </div>
        <div style="height: 300px;">
            内容
        </div>
    </div>
<script type="text/javascript" src="jquery-2.2.3.js"></script>
<script>
    $(function(){
        // 页面加载完成之后自动执行
        $('#title').mouseover(function(){
            $(this).css('cursor','move');
        }).mousedown(function(e){
            //console.log($(this).offset());
            var _event = e || window.event;
            // 原始鼠标横纵坐标位置
            var ord_x = _event.clientX;
            var ord_y = _event.clientY;
            var parent_left = $(this).parent().offset().left;
            var parent_top = $(this).parent().offset().top;
            $(this).bind('mousemove', function(e){
                var _new_event = e || window.event;
                var new_x = _new_event.clientX;
                var new_y = _new_event.clientY;
                var x = parent_left + (new_x - ord_x);
                var y = parent_top + (new_y - ord_y);
                $(this).parent().css('left',x+'px');
                $(this).parent().css('top',y+'px');
            })
        }).mouseup(function(){
            $(this).unbind('mousemove');
        });
    })
</script>
</body>
</html>
```

### 效果  🍀

```javascript
// 基本
show([s,[e],[fn]])
hide([s,[e],[fn]])
toggle([s],[e],[fn])
// 滑动
slideDown([s],[e],[fn])
slideUp([s,[e],[fn]])
slideToggle([s],[e],[fn])
// 淡入淡出
fadeIn([s],[e],[fn])
fadeOut([s],[e],[fn])
fadeTo([[s],o,[e],[fn]])
fadeToggle([s,[e],[fn]])
// 自定义
animate(p,[s],[e],[fn])1.8*
stop([c],[j])1.7*
delay(d,[q])
finish([queue])1.9+
// 设置
jQuery.fx.off
jQuery.fx.interval
```

回调函数实例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="js/jquery-2.2.3.js"></script>
    <script>
    $(document).ready(function(){
   $("button").click(function(){
       $("p").hide(1000,function(){
           alert('动画结束')
       })
//$("p").css('color','red').slideUp(1000).slideDown(2000)
   })
});
    </script>
</head>
<body>
  <button>隐藏</button>
  <p>helloworld helloworld helloworld</p>
</body>
</html>
```

### 扩展  🍀

- [jQuery.fn.extend(object)](http://jquery.cuishifeng.cn/jQuery.fn.extend.html)
- [jQuery.extend(object)](http://jquery.cuishifeng.cn/jQuery.extend_object.html)

更多详细内容  [jQuery API中文文档](http://jquery.cuishifeng.cn/)
