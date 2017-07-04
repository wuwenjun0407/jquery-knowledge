# JQ简单学习（选择器）

@(JQ知识)

### 选择器
>用JQ选择器选则出来的是JQ对象，他只能用JQ中提供的方法，不能用原生的方法和属性
#### 如何把一个JQ对象变成原生对象？
>1.$("#box")[0]
>
>2.$("#box").get(0)
#### 如何把一个原生对象变成JQ对象？
> $(原生对象)  
> 
> $(box)
#### 1.基本选择器
>
-   ID 选择器 获取一个元素
```
$("#box")
```
-  类选择器 获取出来的是一组JQ元素集合
```
$(".box")
```
-  标签选择器 获取出来的是一组JQ元素集合
```
$("div")
```  	
-  通配符选择器 获取出来的是一组JQ元素集合
```
$("*")
```
-   集合选择器  获取出来的是一组JQ元素集合
```
$("div,p,.box")
```
#### 2.层级选择器
>
-   后代选择器 获取出来的是一组JQ元素集合
```
$("#box p")
```
-  子代选择器 获取出来的是一组JQ元素集合
```
$("#box>p")
```
-  下一个弟弟选择器（+后面只能加标签名或者不加） 获取出来的是一组JQ元素集合
```
$("#box+")
$("#box+div")
```
	-   所有的弟弟选择器 获取出来的是一组JQ元素集合
```
$("#box~div") **常用**获取后面你指定的一个的一个
$("#box~") 只要是弟弟都获取出来，包括script
```
#### 基本过滤选择器   
>
-  :frist  只能选择一个
```
$("div :first") //所有的div中第一个div中第一个孩子元素（如果第一个没有，继续向下寻找）
$("div:first") //所有div中第一个div
```
- ：last 
```
$("div :last") //所有的div中最后一个div中第一个孩子元素（如果最后一个没有，继续向上寻找）
$("div:first") //所有div中最后一个div
```
-   :not  获取出来的是一组JQ元素集合
```
$("div:not(.box)") //所有class名不是box的div
```
-  :odd 奇数 获取出来的是一组JQ元素集合
```
#("div:odd") //索引是奇数的div
```
- :even 偶数 获取出来的是一组JQ元素集合
```	
#("div:even") //索引是偶数的div
```
- :eq(索引)
```
$("div:eq(1)") //选取索引为1的div
$("div :eq(1)") //选取div后代索引为1的元素
```
- :gt(索引)
```
$("div:gt(2)") //选取索引大于2的div
```
- :lt(索引)
```
$("div:lt(2)") //选取索引小于2的div
```
- :header  //选取所有的H标签（h1-h6）获取出来的是一组JQ元素集合
```
$(":header") //获取整个页面下所有的h标签
$(".box :header") //指定容器下的必须加空格
```
- :animated //选取所有进行动画的标签（必须是JS动画，css动画获取不到）

#### 内容过滤选择器
>
-  :contains("内容")  获取出来的是一组JQ元素集合
```
$("div:contains('我')") //所有div中含有内容是”我“的标签
```
-  :has()  获取出来的是一组JQ元素集合
```
$("div:has(p)") //所有包含p标签的div
```
-  :empty  //空元素 获取出来的是一组JQ元素集合
-  :parent  //非空元素 获取出来的是一组JQ元素集合

#### 可见性过滤选择器
>
- :hidden  //隐藏元素 获取出来的是一组JQ元素集合
- :visible  //可见元素 获取出来的是一组JQ元素集合

#### 属性过滤选择器（获取出来的是一组JQ元素集合）

```
$("div[id]") //所有有ID的div   [] 里面写属性名
```
```
$("div[class=box]") //所有class=box的div
```
```
$("div[class!=box]") //所有class!=box（class名不是box）的div
```
```
div("div[class^=box]") //所有class以box开头的div
```
```
div("div[class$=box]") //所有class以box结尾的div
```
```
div("div[class*=box]") //所有class含有box结尾的div
```
```
$("div[class|=box]") //所有class=box或者是以box-作为前缀的div
```
```
$("div[class~=box]") //所有class以空格分开后的class名中含有box的div
```

#### 子元素过滤选择器
>
-  :nth-child(1)  //第一个孩子  获取出来的是一组JQ元素集合
```
$("div p:nth-child(1)")
```
-  :nth-child(odd) //第奇数的孩子  获取出来的是一组JQ元素集合
```
$("div span:nth-child(odd)")
```
-  :nth-child(even) //第偶数的孩子  获取出来的是一组JQ元素集合
```
$("div span:nth-child(even)")
```
-  :nth-child(3n) //n从n开始 是3的倍数个孩子  获取出来的是一组JQ元素集合
```
$("div span:nth-child(3n)")
```
- :first-child  //第一个孩子
```
$("div p:first-child")  //div后面第一个叫p的孩子
```
- :last-child  //最后一个孩子
```
$("div p:last-child")  //div后面最后一个叫p的孩子
```
