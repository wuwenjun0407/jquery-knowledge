# JQ请求方法

@(JQ知识)

### 第一种
>load("请求地址"，传给服务器的参数，回调函数)
>
第一个参数必填，后两个可选

>传给服务器的参数：不传的话表示的事get请求，穿了就表示post请求
>
回调函数：不管你请求成功没有都会执行
>默认给他传了三个参数：
  -    responseText：返回的数据
  -  taxtStatus：请求状态信息
  -  XHR：请求对象
```
 $("#get").click(function (e) {
        $("#box").load("get/11.html",function (responseText,textStatus,XHR) {
            console.log(responseText);//返回整个html
            console.log(textStatus);//一个对象
            console.log(XHR);
            var str=responseText.split("<ul>")[1].split("</ul>")[0];
            $(this).html("<ul>"+str+"</ul>");
        })
    })
```
### 第二种
>$.get(url,传给后台的数据，回调函数)
>回调函数：只有在请求成功之后才会执行
>回调函数参数：
>function(data(返回的数据)，status（状态信息）)
```
 $("#get1").click(function (e) {
        $.get("get/data.txt",{name:"aa"},function (data,status) {
            data="JSON" in window?JSON.parse(data):eval("("+data+")");
            $.each(data,function (index,item) {
                
            })
        })
    })
```
### 第三种
>$.post()跟get方法一样用，只不过必须给后台传参数
>将其请求回来的数据变为json对象