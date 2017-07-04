# JQ简单学习（小技巧）

@(JQ知识)


#### 鼠标右键禁用
```
$(document).contextmenu(function () {
			return false;//阻止事件默认行为的方法
        })
$("a")[0].onclick=function () {
		    //组织a标签的默认跳转行为
			return false;
        }
```
#### 鼠标的键值
```
  $("#box").mousedown(function (e) {
			//e 表示的是事件对象
            console.log(e.which);
            //左键：3 右键：1 中间：2
        })
```
#### 自定义选择器
```
var select="widthMore50px";//选择宽度大于50的元素
		//$  就是JQ
		$.expr[":"][select]=function (a) {
		    //return 后面的是条件
			return $(a).width()>50;
        };
        $("div:widthMore50px")
```
#### 关闭动画
```
 jQuery.fx.off=false;//页面上动画有效果
        jQuery.fx.off=true;//关掉页面上的动画
      
      $("#box").click(function () {
          $(".box2").stop().slideToggle();
      });
      $("#close").click(function () {
		  jQuery.fx.off=true;
      });
        $("#open").click(function () {
            jQuery.fx.off=false;
        })
```
#### 改变this
```
$.proxy(函数，要改变的this)
		var a=0;
		function f1() {
			console.log(this.a)
        }
        f1();//0
		var obj={a:"a",f1:"f1"};
		obj.f1();//"a"
		$.proxy(f1,obj)();//"a"
```
#### 去除首尾空格
```
var str=" aa  ";
	str=$.trim(str);
        console.log(str.length);//2
```
#### 去重
```
var ary=[1,2,3,4,51,2,3];
        console.log($.unique(ary));//[1, 2, 3, 4, 51]
```
#### 判断是不是一个对象
```
var obj={};
	var obj1={1:1};
        console.log($.isEmptyObject(obj));//true
        console.log($.isEmptyObject(obj));//true
        console.log($.isEmptyObject(obj1));//false
        console.log($.isEmptyObject(obj1));//false

```