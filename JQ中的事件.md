# JQ中的事件

@(JQ知识)

### on绑定事件
>1.给多个事件行为绑定同一个函数
```
 $("#box").on("click",function (e) {
            //e是事件对象  原生的对象
            //this：点击的元素 原生的对象
        });
function fn(e){
   e:是事件对象 原生的对象
   this：当前触发事件的那个元素 原生的对象
   e.type：事件类型 “click” “mouseover”
}
$("#box").on("click mouseover",fn)
```
>2.on中有个参数是用来筛选的（后代筛选）
```
  $("#box").on("click","p.p",function (e) {
            //从#box的后代元素找到class名为“p”的p标签，给他绑定事件
            console.log(e.target);//p
            console.log(this);//p
```
>3.on中还有个参数是用用来给事件对象绑定数据的
-    objData：事件对象绑定的数据
-   e.data=objData

```
 var objData={name:"a",fn:function(){console.log(this)}};
        $("#box").on("click",objData,function (e) {
            //e.data ：事件类型数据，本身自带的属性，会把那个对象放在里面
            console.log(e.data);//objData
            console.log(e.data.fn);//this-->objData
        })
```
>4.事件命名空间 给事件类型后面加一个点和名字：“click.box”
>off移除事件
```
 $("#box").on("click.box",function (e) {
            console.log(e.type);
        }).on("click",function (e) {
            console.log("onclick");
        }).on("mouseover",function (e) {
            console.log(e.type);
        });
  $("#box").off();//把所有的事件都移除了
  $("#box").off("click");//把所有的click事件都移除了
  $("#box").off("click.box");//把所有的click.box事件都移除了
```
#### on事件写法
on("事件类型type"，“筛选器",{事件对象绑定的数据data},function(e){},false/true)
```
  $("#box").on("click.box","p:eq(2)",{name:"a"},function (e) {
            //this p.eq(2)
            //e.data.name="aa"
        })
```
#### 预留事件
>解决未来要添加的元素绑定事件的问题
>预留事件的第一种方式：
```
 $("#box p").on("click",function (e) {
            console.log(e.target);
        });
用上面的方法，如果再给box添加p标签，p标签不会绑定上事件
  $("#box").on("click","p",function (e) {
            console.log(e.target);
        })
用这种写法，如果再给box添加p标签，p标签会绑定上事件
```
>预留事件的第二种方式：
```
$("#box").delegate("p","click",function (e) {
            console.log(this);
        })
```
#### 预留事件的移除
>undelegate 
```
  $("#box").undelegate("click");
  //移除$("#box")预留的click事件
   $("#box").undelegate();
  //移除$("#box")预留的所有事件
```

### bind绑定事件
>绑定
```
$("#box").bind("type","筛选器"，{事件对象数据}，function(){}）
```
>移除
```
unbind("type")跟off一样用
```