/*
Title: slider
Description: slider
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setValue](#2)

[lock](#3)

[close](#4)

[show](#5)

[hide](#6)
</div>

#**概述**

slider封装了一个滑动器，开发者可自定义最大值、最小值、当前值以及拖动滑块时的气泡提示信息等各种滑动器用到的功能。原生代码比前端实现更加流畅稳定

![图片说明](/img/docImage/slider.jpg)

#**open**<div id="1"></div>

打开slider

open({params}, callback(ret, err))

##params

multiOpen：

- 类型：布尔
- 默认值：false
- 描述：同一个页面是否可以同时打开多个滑动器，可为空

alwaysShowBubble：

- 类型：布尔
- 默认值：true
- 描述：是否一直显示提示气泡，可为空

x：

- 类型：数字
- 默认值：30
- 描述：slider左边点的坐标，可为空

y：

- 类型：数字
- 默认值：104
- 描述：slider左边点的坐标，可为空

<del>width：</del>

- <del>类型：数字</del>
- <del>默认值：260</del>
- <del>描述：slider的宽，可为空</del>

w：

- 类型：数字
- 默认值：260
- 描述：slider的宽，可为空

height：

- 类型：数字
- 默认值：5
- 描述：slider的高，可为空

<del>h：</del>

- <del>类型：数字</del>
- <del>默认值：5</del>
- <del>描述：slider的高，可为空</del>

bgImg：

- 类型：字符串
- 默认值：无
- 描述：slider的背景图片，不可为空

selectedBgImg：

- 类型：字符串
- 默认值：无
- 描述：slider滑块左边划过的区域图片，不可为空

<del>barW：</del>

- <del>类型：数字</del>
- <del>默认值：30</del>
- <del>描述：slider滑块的宽，可为空</del>

<del>barH：</del>

- <del>类型：数字</del>
- <del>默认值：18</del>
- <del>描述：slider滑块的高，可为空</del>

<del>barImg：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：slider滑块背景图片，不可为空</del>

bar：

- 类型：json对象
- 默认值：见内部字段
- 描述：气泡设置，可为空,若为空则不显示滑块

内部字段：

```js
{
	barWidth：//滑块宽，数字，可为空，默认30
	barHeight： //滑块的高，数字，可为空，默认18
	barImg：//滑块背景，字符串，可为空，默认#4f94dc，支持rgb，rgba，#，img
}
```

<del>bubbleW：</del>

- <del>类型：数字</del>
- <del>默认值：60</del>
- <del>描述：slider滑动时弹出的气泡的宽，可为空</del>

<del>bubbleH：</del>

- <del>类型：数字</del>
- <del>默认值：40</del>
- <del>描述：slider滑动时弹出的气泡的高，可为空</del>

<del>bubbleImg：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：slider气泡的背景图片路径，不可为空</del>

<del>bubbleSuffix：</del>

- <del>类型：字符串</del>
- <del>默认值：℃</del>
- <del>描述：slider气泡上的文字后缀，可为空</del>

<del>bubbleColor：</del>

- <del>类型：字符串</del>
- <del>默认值：#FFFFFF</del>
- <del>描述：slider气泡上的文字颜色，可为空, 支持rgb，rgba，#</del>

bubble：

- 类型：json对象
- 默认值：无
- 描述：气泡设置，可为空

内部字段：

```js
{
	bubbleWidth：//数字类型，默认60，气泡的宽，可为空
	bubbleHeight：//数字类型，默认40，气泡的高，可为空
	bubbleImg：//字符串，默认#5cacee，气泡背景，可为空，支持rgb,rgba,#,img
	titleSuffix：//字符串，默认℃，气泡后缀，可为空
	titleColor：//字符串，默认#000000，可为空，支持rgb，rgba，#
}
```

minValue：

- 类型：数字
- 默认值：0
- 描述：slider最小值，可为空

maxValue：

- 类型：数字
- 默认值：100
- 描述：slider最大值，可为空

defValue：

- 类型：数字
- 默认值：0
- 描述：slider开启默认值，可为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：把模块视图添加到指定窗口的名字，可为空

step：

- 类型：数字
- 默认值：0.00001
- 描述：滑块滑动最小单位，可为空

fixed:
- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	id:               //滑动器的id
	touchCancel:      //是否是滑动结束事件
	value:				//滑动时返回滑动的值
}
```

##示例代码

```js
var obj = api.require('slider');
obj.open({
         x:30,
         y:104,
         width:260,
         height:6,
         bgImg:"widget://image/slider_bg.png",
         selectedBgImg:"widget://image/slider_selected.png",
         barW:30,
         barH:20,
         barImg:"widget://image/slider_bar.png",
         bubbleW:60,
         bubbleH:40,
         bubbleImg:"widget://image/slider_bubble.png",
         minValue:0,
         maxValue:100,
         defValue:30
},function(ret,err){
    if(ret.touchCancel){
        api.alert({msg:ret.value});
    }else{
        ret.value;
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setValue**<div id="2"></div>

设置slider的值

setValue({params})

##params

id：

- 类型：数字
- 默认值：打开的第一个菜单的id
- 描述：菜单id，可为空

value:

- 类型：数字
- 默认值：无
- 描述：要设置的滑块的值（在最大值和最小值直接的一个值），不可为空

minValue：

- 类型：数字
- 默认值：无
- 描述：slider最小值，可为空，为空时保持之前的值

maxValue：

- 类型：数字
- 默认值：无
- 描述：slider最大值，可为空，为空时保持之前的值

step：

- 类型：数字
- 默认值：0.00001
- 描述：滑块滑动最小单位，可为空

##示例代码

```js
var obj = api.require('slider');
obj.setValue({
    value:51
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**lock**<div id="3"></div>

锁定slider的值

lock({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作菜单id，若为空则关闭全部，可为空

lock:

- 类型：布尔
- 默认值：true
- 描述：是否锁定当前slider的值，可为空

##示例代码

```js
var obj = api.require('slider');
obj.lock({
	lock:true
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



##**close**<div id="4"></div>

关闭slider

close()

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作菜单id，若为空则关闭全部，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
   status:      //操作状态值，布尔值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:      //错误信息，字符串
}
```

##示例代码

```js
var obj = api.require('slider');
obj.close({
    value:51
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="5"></div>

显示滑动器

show(callBack(ret,err))

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作菜单id，若为空则关闭全部，可为空


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值，布尔值
}
```

err：

- 类型：JSON对象

内部字段：

```
{
	msg:“”	//错误描述，字符串
}
```

##示例代码

	var obj= api.require('slider');
	obj.show();

##补充说明
无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="6"></div>

隐藏滑动器

hide(callBack(ret,err))

##params

id：

- 类型：数字
- 默认值：无
- 描述：菜单id，若当前页面存在且仅存在一个滑块对象,则默认操作此对象.此时参数可为空


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```
{
	status:true           //操作成功状态值，布尔值
}
```

err：


- 类型：JSON对象

内部字段：

```js
{
	msg:“”	//错误描述，字符串
}
```

##示例代码

	var obj = api.require('slider');
	obj.hide();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

