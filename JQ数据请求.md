# JQ数据请求

@(JQ知识)

### 获取方式
```
$.ajax({
   //请求方式
   type：“GET”，//“POST”
   //请求地址URL
   url:"data.txt?_="+Math.random(),
   //dataType 规定后台返回给你的数据格式，你可以直接规定返回给你的数据是JSON对象，这样你就不用自己转换了
   dataType:"json",//"html","text"
   //书否异步
   asyns:true,//false 同步， true 异步
   //缓存
   cache:true,
   //你传给后台的数据data
   data：null，
   //请求成功之后，执行的函数
   success：function（）{
          //data,后台给你返回的数据
          window.data=data；
      }
   //请求失败执行的函数
   error：function（）{
            console.log("请求失败")
        }
})
```