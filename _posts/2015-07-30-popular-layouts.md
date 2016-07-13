---
title: 几种常见布局
category: CSS3相关
---
这篇文章主要是对几种常见的网页布局进行了一个总结，以前在进行CSS布局的时候总是遇到哪个布局，
才去想怎么去实现，没有系统的总结过，导致
踩了很多坑，浪费了很多时间。所以最近抽空将自己能想到的几种常见的布局进行了一个总结，
可能还有很多没有考虑到得，以后想起了，或者在项目中
遇到再补充...



###几种常见的布局

####1、两列布局(一般是menu和content)
html
{% highlight html linenos %}
<div class="container clearfix">
    <div class="menu">menu</div>
    <div class="content">content</div>
<div>
{% endhighlight %}

{% highlight css linenos %}
.clearfix:after{
  content:".";
  display:block;
  height:0;
  clear:both;
  visibility:hidden
}
{% endhighlight %}

####(1)menu固定宽度，content自适应

{% highlight css linenos %}
.container{
  /留出左边固定的宽度/
  margin-left: 100px;
  height: auto;
}


.menu{
  width: 100px;
  float:left;
  /设置margin-left为负的左侧宽度/
  margin-left: -100px;
}



.content{
  width: 100%;
}
{% endhighlight %}

说明：使用该方法时menu和content两个div要么是浮动的，要么是inline-block；当为inline-block时，
他们的container容器的font-size必须为0，这是因为默认的两个inline-block之间有一定的间隙，这个间隙可以
通过font-size=0去掉

####(2)menu和content都自适应

{% highlight css linenos %}
.container{
  width:100%;
  height: auto;
}


.menu{
  width: 20%;
  float:left;
}



.content{
  width: 80%;
  float:right;
}
{% endhighlight %}

####2、三列布局
html
{% highlight html linenos %}
<div class="container clearfix">
    <div class="leftmenu">menu</div>
    <div class="content">content</div>
    <div class="rightmenu">menu</div>
<div>
{% endhighlight %}
{% highlight css linenos %}
.clearfix:after{
  content:".";
  display:block;
  height:0;
  clear:both;
  visibility:hidden
}
{% endhighlight %}

####(1)1列自适应（一般为content自适应，leftmenu和rightmenu固定）

{% highlight css linenos %}
.container{
  /留出左边固定的宽度/
  margin:0px 100px;
  height: auto;
  font-size:0px;
}
.content{
  width:100%;
  height:100px;
  //可以替换为float:left/right;
  display:inline-block;
  background-color:grey;
}
.leftmenu{
  width:100px;
  float:left;
  margin-left:-100px;
}
.rightmenu{
  width:100px;
  float:right;
  margin-right:-100px;
}
{% endhighlight %}
注意：如果三列中有一列为display:inline-block；则container的font-size:0px;
不然会因为inline-block的间隙问题而导致不能在同一行

####(2)两列自适应，一列固定宽度

这种布局一般可以归结为两列布局，其中一列固宽，一列自适应，DOM结构变为

{% highlight html linenos %}
<div class="container clearfix">
    <div class="leftmenu">menu</div>
    <div class="content">
        <div class="leftcontent">menu</div>
        <div class="rightcontent">menu</div>
    </div>
<div>
{% endhighlight %}
其中content里面的内容又可以两列都自适应宽度的布局。自此，这种布局就被分解为两列布局的嵌套形式

####(3)三列都是自适应宽度

{% highlight css linenos %}
.container{
  height: auto;
}
.leftmenu{
  width:30%;
  float:left;
}
.rightmenu{
  width:10%;
  float:right;
.content{
  width:60%;
  display:inline-block;
}
{% endhighlight %}
这种布局只需要为每列设置所需的百分比就可以了，但有一个地方必须注意：三个div必须要么是浮动，要么是
行内元素

####3、一列布局

{% highlight html linenos %}
<div class="container clearfix">
    <div class="content">
    </div>
<div>
{% endhighlight %}
这种布局一般是内容部分固定宽度，一把为960px，页面居中显示，css实现为
{% highlight css linenos %}
   .container{
      width:100%;
    }
    .content{
        width:960px;
        margin:0px auto;
    }
{% endhighlight %}
注意：此时的content容器必须是块元素，不呢改为行内元素，否则无法居中，当然，也可以在container上使用
text-align:center来居中



