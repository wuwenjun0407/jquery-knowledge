# JQ简单学习（表单对象属性过滤选择器）

@(JQ知识)

	$("#form1 :enabled");//选取form1下面的所有可用元素
			$("#form1 :disabled");//选取form1下面的所有可用元素
			$("#form1 :checked");//选出form1下所有被选中的元素
			$("#form1 select option:selected");//下拉选项被选中的元素
			$("#form1 :input");//input textarea select button
			$(":text");//所有的单行文本框
			$(":password");//所有的密码框
			$(":radio");//所有的单选框
			$(":checkbox");//所有的复选框
			$(":submit");//所有的提交按钮
			$(":image");//所有的图片按钮
			$(":button");//所有的按钮
			$(":reset");//所有的重置按钮
			$(":file");//所有的上传域
			$(":hidden");//所有隐藏元素

### 表单的选取
>全选
```
		$("#all").click(function () {
			$("[name=items]").prop("checked",true);
        });
```        
>全不选
```
        $("#no").click(function () {
            $("[name=items]").prop("checked",false);
        });
```        
>反选
```
		$("#rev").click(function () {
			$("[name=items]").each(function (index,item) {
				$(this).prop("checked",!$(this).prop("checked"))
            })
        });
```
>提交
```
		$("#send").click(function () {
			var str="你喜欢的女明星是： \n";
			$("[name=items]:checked").each(function (index,item) {
				str+=$(this).val()+"\n";
            });
			alert(str);
        })
```
#### 全选和不全选的框和要选择的框在一行的时候，选择全选和全不选的方法
>第一种方法：
```
		$("#all").click(function () {
			if($("[name=items]:checked").length===$("[name=items]").length){
                $("[name=items]").prop("checked",false)
			}else {
                $("[name=items]").prop("checked",true)
			}
        });

        $("[name=items]").click(function () {
           /* if($("[name=items]").length===$("[name=items]:checked").length){
			 $("#all").prop("checked",true)
			 }else {
			 $("#all").prop("checked",false)
			 }*/
            $("#all").prop("checked",$("[name=items]").length===$("[name=items]:checked").length);
        });
```

>第二种方法：
```
		$("#all").click(function () {
			$("[name=items]").prop("checked",this.checked);
        });
```