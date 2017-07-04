# JQ中的AJAX请求

@(JQ知识)

```
 $.ajax({
        type:"get",//请求方式
        url:"get/data.txt",//请求地址，都是后台给你的
        async:false,//是否异步，false：同步 true：异步
        timeout:300,//请求时间，自己规定的，如果超时就算失败
        data:{"name":"aa"},//传给后台数据，如果你用get方式请求，可以直接把数据拼接到URL上，或者是写在这里，（也会自动给你加在URL上）
        dataType:"json",//你规定返回给你数据的格式，如果返回给你的不是你想要的，他会自己转成你想要的。（比如：返回的是字符串，而你写的是json，他会自动转成json）
        beforeSend:function (xhr) {
            //xhr：请求对象 Ajax对象
            //请求发出去之前执行的函数，如果你想拦截请求就在这里拦截
        },
        complete:function (xhr,textStatus) {
            //请求发送之后执行，不管成不成功都会执行
            //xhr:请求对象 Ajax对象
            //textStatus:请求状态信息
        },
        success:function (data,textStatus) {
            //请求成功后执行
            //data:返回的数据
            //textStatus:请求状态信息
        },
        error:function (xhr,textStatus,errorThrown) {
            //xhr:请求对象 Ajax对象
            //textStatus:请求状态信息
            //errorThrown:错误信息
        },
        global:false,//是否会触发全局请求
        //比如你把这次请求加在一个事件里面，只有触发这个事件的时候才会请求，如果你加上global：true，不用你触发事件，打开页面就会先请求一次
    })
```
### url解析,跳转,表单提交
>原生的方法
```
var url=window.location.href;
    url=window.decodeURI(url);
    url="http://localhost:63342/第五周/第三天/1.html?user=啊啊啊&passWord=11&box=on&sel=2"
    var s1=url.split("?")[1].replace(/=/g,":'");
    s1=s1.replace(/&/g,"',");
    var obj=eval("({" + s1 + "'})");
    var str2="";
    for(var key in obj){
        str2+="<span>"+key+"</span> <span>"+obj[key]+"</span><br>"
    }
    document.body.innerHTML+=str2;

```
>JQ的方法带着数据跳转到另一个地址
```
$("#sub").click(function (e) {
        var url=$("form").serialize();
        window.open("地址"+"?"+url);
    })
```