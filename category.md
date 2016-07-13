---
layout: page
title: 分类页面
---
{% for category in site.categories %}
<div  class="m_arclist">
<h2 class="title">{{ category | first }}</h2>
<span class="count">共有{{ category | last | size }}篇文章</span>
<ul class="arclist">
    {% for post in category.last %}
        <li><a class="archref" href="{{ post.url|prepend: site.baseurl }}">{{ post.title }}</a><span class="date">{{ post.date | date:"%Y-%m-%d"}}</span></li>
    {% endfor %}
</ul>
</div>
{% endfor %}