---
title: CSS3过渡-Dock
category: CSS3相关
---
事实上，这样会触发多次提交。这种交互，对于客户和开发人员都是不友好的，为了进一步增进用户体验，我们决定为按钮添加实时的反馈，以减少多次提交
这就涉及到了等待动画（当然，也可以用非动画），在强大的CSS3面前，这些已经是小菜一碟。以下是三种实现方法(有的是参考别人的):...
<div class="dock-wrapper">
	<div class="content">
		<h1>CSS Dock</h1>
		<div class="dock">
			<ul>
				<li id="mail">
					<a href="#mail">
						<em><span>Mail</span></em>
						<img src="{{ "assets/img/01.png" | prepend: site.baseurl }}"/>
					</a>
				</li>
				<li id="ical">
					<a href="#ical">
						<em><span>cal</span></em>
						<img src="{{ "assets/img/02.png" | prepend: site.baseurl }}"/>
					</a>
				</li>
				<li id="idisk">
					<a href="#idisk">
						<em><span>idisk</span></em>
						<img src="{{ "assets/img/03.png" | prepend: site.baseurl }}"/>
					</a>
				</li>
				<li id="iphoto">
					<a href="#iphoto">
						<em><span>iphoto</span></em>
						<img src="{{ "assets/img/04.png" | prepend: site.baseurl }}"/>
					</a>
				</li>
			</ul>
		</div>
		<div class="dock-stage">
			<div class="dock-container">
				<div class="dock-panel"></div>
			</div>
		</div>
	</div>
</div>








