# JQ简单学习（常用的动画方法）

@(JQ知识)

```
 (function () {})();//原生中的自执行函数
 $(function () {});//JQ中的自执行函数
```
### 动画方法
>在JQ中加动画之前先执行一下stop（），因为先要停止上一个动画取开启下一个动画。
```
    $(function () {
        //在JQ中的事件都没有on
        //click(function(){})
        var $box=$(".box");
        $("submitBtn").click(function () {
            //这里的this给谁绑定的就是谁
            
        })
    })()
```
>1.隐藏 hide()
           
             $box.stop().hide();
             $box.stop().hide("fast");
             $box.stop().hide("slow");
             $box.stop().hide(2000);
>2.显示 show()
            
             $box.stop().show();
             $box.stop().show("fast");
             $box.stop().show("slow");
             $box.stop().show(2000);
 >3.slideUp() 收起来
          
             $box.stop().slideUp();
             $box.stop().slideUp("fast");
             $box.stop().slideUp("slow");
             $box.stop().slideUp(2000);
> 4.slideDown()展开
            
             $box.stop().slideDown();
             $box.stop().slideDown("fast");
             $box.stop().slideDown("slow");
             $box.stop().slideDown(2000);

>5.slideToggle() 自动收放
            
             $box.stop().slideToggle();
             $box.stop().slideToggle("fast");
             $box.stop().slideToggle("slow");
             $box.stop().slideToggle(3000);

> 6  fadeIn()Out() 淡入淡出
            
             /In
             $box.stop().fadeIn();
             $box.stop().fadeIn("fast");
             $box.stop().fadeIn("slow");
             $box.stop().fadeIn(2000);
             /Out
             $box.stop().fadeOut();
             $box.stop().fadeOut("fast");
             $box.stop().fadeOut("slow");
             $box.stop().fadeOut(2000);
>Toggle()自动淡入淡出

>delay(时间) 延迟动画 对这俩hide(),show()没有效果
            
             $box.stop().delay(3000).slideDown();
             $box.stop().delay(3000).show();
             $box.stop().delay(3000).show(2000);

>animate({目标值},duration,回调函数function)
```
 $box.stop().animate({top:600,height:100},2000,function(){
             //this当前执行动画的元素
             //this.innerHTML="哈哈哈"
             $(this).css("backgroundColor","red");
             $(this).delay(3000).animate({top:80,height:50},1000,function(){
             $(this).css("backgroundColor","yellowgreen");
             })
             })
```

### JQ 获取出来的一组集合 在绑定事件的时候，默认是一个一个的绑定