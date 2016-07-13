---
title: 按钮等待动画
category: CSS3相关
---
最近项目中遇到了这样一个问题：用户填写完成后点击提交按钮时，在点击和服务器返回数据之间的这一段时间，由于按钮没有任何反馈，用户以为没有触发点击事件，导致点击多次，事实上，这样会触发多次提交。这种交互，对于客户和开发人员都是不友好的，为了进一步增进用户体验，我们决定为按钮添加实时的反馈，以减少多次提交
这就涉及到了等待动画（当然，也可以用非动画），在强大的CSS3面前，这些已经是小菜一碟。以下是三种实现方法(有的是参考别人的):...

###CSS3实现的提交等待动画：三种
html
{% highlight html linenos %}
<button class="dotBtn">处理中<span class="dotting"></span></button>
{% endhighlight %}
####1、box-shadow实现
这种方法的原理是：利用阴影叠加，横向分别设置一个，两个，三个阴影。

css
{% highlight css linenos %}
.dotting{
	display:inline-block;
	width:2px;
	height:2px;
	-webkit-animation:dots1 2s infinite step-start;
	animation:dots 2s infinite step-start;
	
}
@keyframes dots{
	25%{box-shadow:2px 0 white;}
	50%{box-shadow:2px 0 white,6px 0 white;}
	75%{box-shadow:2px 0 white,6px 0 white,10px 0 white;}
}
@-webkit-keyframes dots{
	25%{box-shadow:2px 0 white;}
	50%{box-shadow:2px 0 white,6px 0 white;}
	75%{box-shadow:2px 0 white,6px 0 white,10px 0 white;}
}
{% endhighlight %}
<button class="dotBtn">处理中<span class="dotting-1"></span></button>


####2、border-background实现
这种方法的原理是：利用左右边框+背景色，注意，该方法必须要设置background-clip: content-box;不然背景色会填充包括padding在内的所有区域。

css
{% highlight css linenos%}
.dotting{
	display:inline-block;
	width:10px;
	height:2px;
	padding-left:2px;
	padding-right:2px;
	background-color:currentColor;
	background-clip: content-box;
	border:2px solid currentColor;
	border-top:none;
	border-bottom:none;	
	-webkit-animation:dots 2s infinite step-start;
	animation:dots 2s infinite step-start;
}
@keyframes dots{
	25%{background-color:transparent;border-right:transparent;border-left:transparent;}
	50%{background-color:transparent;border-right:transparent;}
	75%{border-right:transparent;}
}
@-webkit-keyframes dots{
	25%{background-color:transparent;border-right:transparent;border-left:transparent;}
	50%{background-color:transparent;border-right:transparent;}
	75%{border-right:transparent;}
}
{% endhighlight %}
<button class="dotBtn">处理中<span class="dotting-2"></span></button>

####3、width实现
这种方法的原理是：在不同时间改变元素的宽度，让溢出部分隐藏。

html
{% highlight html linenos %}
<button class="dotBtn">处理中<span class="dotting">...</span></button>
{% endhighlight %}
css
{% highlight css linenos %}
.dotting{
	position:absolute;
	display:inline-block;
	-webkit-animation:dots 2s infinite step-start;
	animation:dots 2s infinite step-start;
	overflow:hidden;
	vertical-align: bottom;
}
@keyframes dots{
	0%{width:0px;}
	25%{width:4px;}
	50%{width:10px;}
	75%{width:14px;}
	100%{width:0px;}
}
@-webkit-keyframes dots{
	0%{width:0px;}
	25%{width:4px;}
	50%{width:10px;}
	75%{width:14px;}
	100%{width:0px;}
}
{% endhighlight %}
<button class="dotBtn">处理中<span class="dotting-3">...</span></button>