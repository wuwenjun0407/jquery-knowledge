# JQ简单学习（常用的属性方法）

@(JQ知识)

#### 只有原生中才有this，不管this代表的是谁，肯定是个原生对象
### 回调函数集合
```
  
    function f1(a){console.log("f1:"+a)}
    function f2(a,b){console.log("f2:"+a+b)}
    //f1(1,2,3,4);
    //f2(1,1);
    var $call=$.Callbacks();//回调函数集合
    console.log($call);
//    $call.add(f1);
//    $call.add(f2);
    $call.add(f1,f2);//add向回调函数集合中增加方法名
    $call.fire(1,2);//fire去依次执行里面的函数,可以传参数,函数执行的时候会自动获取想要的参数
    $call.fire(1);
    $call.remove(f1);//remove删除回调函数集合中的方法
    console.log($call.has(f1));//false
    //has判断回调函数集合中有没有这个函数
    $call.empty();//empty清空里面的函数

  
```
### 属性
```
 
    //attr(),获取/设置属性 一般都是自定义属性,会显示在HTML标签上
    //一个参数是获取
    //二个参数:设置,
    // 批量设置:参数是个对象
    console.log($("#box").attr("photo"));
    $("#box").attr("p","p");
    $("#box").attr({a:"a",b:"b"});

    //removeAttr():移除属性
    $("#box").removeAttr("a");
    $("#box").removeAttr("a b");
    //批量删除

    //prop 获取/设置属性(一般都是天生自带的 内置属性)
    //如果设置的是内置属性就会显示在HTML结构上,如果是自定义属性不会显示

    //class
    toggleClass(该元素上有了该属性就删除，没有就添加)
    //addClass/removeClass/toggleClass
    $("#box").addClass("box1 box2    box");

```
### JQ遍历的方法
```

    //each()遍历JQ集合的(数组中forEach很像)
    //如果想遍历一个非JQ对象，比如一个数组[]一个对象{}，就用$.each().
    //如果想遍历一个JQ对象就用 JQ对象.each()
    //参数是个函数,这个函数默认执行的时候给他传了2个参数,第一个参数是索引,第二参数是当前的那一项而且是个原生对象
    $("#oUl>li").each(function(index,item){
        //this==item
        console.log(this);
	        //item 原生对象
        //给每个li增加一个class名"JQ"
//        $(item).addClass("JQ");
        $(this).addClass("JQ");
//        item.innerHTML++;
        this.innerHTML++;
        //item.className+=" JQ";
    });
    //map 跟each一样只是他有返回值

    var $map=$("#oUl>li").map(function(index,item){
    });
    console.log($map.length);//0
```
### JQ设置样式
>css()样式,获取/设置,批量设置
```
 console.log($("#box").css("color"));
    $("#box").css("color","red");
    $("#box").css({"color":"yellow","fontSize":"40px"});
```
>offset()   当前元素距离body 的偏移量
```    
    $("#box").offset().left;
    $("#box").offset().top;
```    
>scrollTop()/scrollLeft() 不穿参数是获取,传参数是修改 没有单位
```
    console.log($("body").scrollTop());
    $("body").scrollTop(1000);
    console.log($("body").scrollTop());
```
>width()/height()
```
    
    console.log($("#oUl>li").height());
    $("#oUl>li").height(50);
```

>   innerWidth()/innerHeight() 这个跟 原生的clientWidth/clientHeight系列一样
   
> 不穿参数是获取,传参数是修改(没有单位)  修改的时候padding不变改变宽高

 >   outerWidth()/outerHeight() 相当于offsetWidth/offsetHeight系列
 
>不穿参数是获取,传参数是修改(没有单位) 修改的时候padding+border不变改变宽高

>注意 outerWidth(true)/outerHeight(true),是获取并且加上margin


#### JQ中强大的好处:链式写法
```
JQ 中的方法都有返回值返回的是个JQ对象
    $(".box1").css({width: 100, height: 100, backgroundColor: "red"}).width(200).addClass("box2").height();
```
#### 文档处理
```   
    //加在父级元素的后面
    //父级.append(新元素可以是原生的也可以给是JQ对象)
    var oDiv=document.createElement("div");
    $(".box1").append(oDiv);
    $(".box1").append($("#p1"));

    //新元素.appendTo(父级)
    $("#p1").appendTo($(".box"));

    //prepend/prependTo  加在父级元素的前面
    $("ul").prepend($("#p1"));

    //after/before 加在当前元素的后面/前面
    $(".box1").after($("#p1"));
    $(".box1").before($("#p1"));

    // JQ选择出来的元素.insertBefore(指定元素)
    //将JQ选择出来的元素添加到指定元素的前面
    // JQ选择出来的元素.insertAfter (指定元素)
    //将JQ选择出来的元素添加到指定元素的后面

    //replaceAll(选择器)
    $(".box1").replaceAll("#p1");//将#p1替换成.box1

    var p=document.createElement("p");
    $(p).replaceAll("li");

    //remove() 删除
    //$(".box1").remove();

    $("div").remove(".box");//把所有div中类名是box删掉
    //$(".box1 div").remove();
    $("span").remove(".span1");
    把所有的span中class名是span1的删掉
```
#### 筛选
>eq()，first()，last()
```
var $li=$("ul>li")
$li[0]//得到的是原生对象（元素）
$li.eq(0)//得到的是JQ对象
$li.last()
$li.first()
```
>同级过滤 filter
```
$("ul>li").filter(".li1")//先获取所有的ul下的li,在所有的li找类名是li1的li元素
```
>子级过滤 children
```
$("ul").children(".li1")//在ul下找类名是li1的孩子
```
>后代过滤 find
```
$("ul").find(".li1")///在ul下找类名是li1的后代（子子孙孙）
```

### DOM
>parent
```
$(".box1").parent（）//找他的一个父级元素
$(".box1").parents（）//找他的所有父级元素（父亲，父亲的父亲。。。HTML）
```
>next()     下一个弟弟
>prev()     上一个哥哥
>nextAll()   所有的弟弟
>prevAll ()    所有的哥哥
>sibLings()   所有的兄弟

```
  $(document).ready(function () {
      //只要页面上所有的DOM结构(包括图片)加载完成后才开始执行  
    })
     jQuery(function ($) {
        
    });
    $(function () {
        
    })
```


