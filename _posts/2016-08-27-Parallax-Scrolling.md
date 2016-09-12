## 视差滚动
### 1.定义
视差滚动（Parallax Scrolling）指网页滚动过程中，多层次的元素进行不同程度的移动，视觉上形成立体运动效果的网页展示技术。

### 2.特性

视差滚动效果酷炫，适合于个性展示的场合。

视差滚动徐徐展开，适合于娓娓道来，讲故事的场合。

视差滚动容易迷航，需要具备较强的导航功能。

### 3.原理
传统的网页的文字、图片、背景都是一起按照相同方向相同速度滚动的，而视差滚动则是在滚动的时候，内容和多层次的背景实现或不同速度，或不同方向的运动。

有的时候也可以加上一些透明度、大小的动画来优化显示。

### 4.实现
4.1 原理一

利用background-attachment属性实现。

background-attachment: fixed || scroll || local
默认情况下，此属性取值scroll，页面滚动时，内容和背景一起运动，如果取值fixed，背景相对浏览器固定。

<pre><code>
<div>
<html lang="zh-CN"><head>
<meta charset="UTF-8">
<title>视差滚动原理一</title>
<style>
.article{
	width: 960px;
	margin: 0 auto;
	height: 800px;
	padding: 40px;
	font: 18px/1.5 'Microsoft YaHei';
	background-repeat: no-repeat;
	background-attachment: fixed;
	background-position: center center;
	background-size: cover;
}
.section1{
	background-image: url( http://www.alloyteam.com/wp-content/uploads/2014/01/section01.jpg);
}
.section2{
	background-image: url( http://www.alloyteam.com/wp-content/uploads/2014/01/section02.jpg);
}
.section3{
	background-image: url( http://www.alloyteam.com/wp-content/uploads/2014/01/section03.jpg);
}
.title{
	font: 32px/1.5 '微软雅黑';
	position: relative;
	top: 360px;
}
.content{
	position: relative;
	top: 380px;
	color: #777;
}
.section1 .title{
	color: white;
}
.section2 .title{
	color: #FF8500;
}
.section3 .title{
	color: #747474;
}
</style></head>

<body style="zoom: 1;">
<div class="article section1">
	<div class="title">
		章节·一  每当我加班凌晨，独自一人走在黑暗的回家路上
	</div>
	<div class="content">
		我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
	</div>
</div>
<div class="article section2">
	<div class="title">
		章节·二  我会想起那天夕阳下的奔跑
	</div>
	<div class="content">
		我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
	</div>
</div>
<div class="article section3">
	<div class="title">
		章节·三  那是我逝去的，青春
	</div>
	<div class="content">
		我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		我是内容我是内容我是内容我是内容我是内容我喜欢你我是内容我是内容
	</div>
</div>
</body></html>
</code></pre>

4.2 原理2

在scroll事件上添加一些动画事件。视差滚动的表现方式非常多，滚动到页面某个值后会触发一个CSS3动画，这也是众多视差滚动中常见的一种。


<pre><code>
<!DOCTYPE html>
<html lang="zh-CN"><head>
<meta charset="UTF-8">
<title>视差滚动原理儿</title>
<style>
.article{
	width: 960px;
	margin: 0 auto;
	height: 800px;
	padding: 40px;
	font: 18px/1.5 'Microsoft YaHei';
	overflow: hidden;
	background-repeat: no-repeat;
	background-attachment: fixed;
	background-position: center center;
	background-size: cover;
}
.section1{
	background-image: url( http://www.alloyteam.com/wp-content/uploads/2014/01/section01.jpg);
}
.section2{
	background-image: url( http://www.alloyteam.com/wp-content/uploads/2014/01/section02.jpg);
}
.section3{
	background-image: url( http://www.alloyteam.com/wp-content/uploads/2014/01/section03.jpg);
}
.title{
	font: 32px/1.5 '微软雅黑';
	position: relative;
	top: -100px;
}
.content{
	position: relative;
	top: 380px;
	left: 1024px;
	color: #777;
}
.section1 .title{
	color: white;
}
.section2 .title{
	color: #FF8500;
}
.section3 .title{
	opacity: 0;
	top: 360px;
	color: #747474;
}
.title-anim{
	top: 360px;
	-webkit-transition : all 3s;
	-moz-transition : all 3s;
	-ms-transition : all 3s;
	transition : all 3s;
}
.title-anim2{
	opacity: 1!important;
	/*opacity 属性设置元素的不透明级别*/
	-webkit-transition : all 2s;
	-moz-transition : all 2s;
	-ms-transition : all 2s;
	transition : all 2s;
}
.content-anim{
	left: 0px;
	-webkit-transition : all 3s;
	-moz-transition : all 3s;
	-ms-transition : all 3s;
	transition : all 3s;
}
</style></head>

<body style="zoom: 1;">
<div id="articles">
	<div id="article1" class="article section1">
		<div id="title1" class="title title-anim">
			章节·一  每当我加班凌晨，独自一人走在黑暗的回家路上
		</div>
		<div id="content1" class="content content-anim">
			我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
			我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
			我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		</div>
	</div>
	<div class="article section2">
		<div id="title2" class="title">
			章节·二  我会想起那天夕阳下的奔跑
		</div>
		<div id="content2" class="content">
			我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
			我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
			我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
		</div>
	</div>
	<div class="article section3">
		<div id="title3" class="title">
			章节·三  那是我逝去的，青春
		</div>
		<div id="content3" class="content">
			我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你
			我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你
			我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你我喜欢你
		</div>
	</div>
</div>

<script>
	var articleHeight = document.getElementById('article1').clientHeight;
	var title1 = document.getElementById('title1'),
		title2 = document.getElementById('title2'),
		title3 = document.getElementById('title3');
	var content1 = document.getElementById('content1'),
		content2 = document.getElementById('content2'),
		content3 = document.getElementById('content3');
	window.addEventListener('scroll',scrollHandler);

	function scrollHandler(e){
		var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
		if(scrollTop > 0 && scrollTop < articleHeight){
			title1.classList.add('title-anim');
			content1.classList.add('content-anim');
		}else if(scrollTop >= articleHeight && scrollTop < articleHeight*2){
			title2.classList.add('title-anim');
			content2.classList.add('content-anim');
		}else if(scrollTop >= articleHeight*2 && scrollTop < articleHeight*3){
			title3.classList.add('title-anim2');
			content3.classList.add('content-anim');
		}
	}
</script>


</body></html>
</code></pre>

4.3 原理3

视差滚动中最突出的内容就是立体的视差效果，最具有说明代表性的就是超级玛丽的游戏场景，当玩家操作马里奥移动时，水管和墙块更马里奥在同一水平层，移动速度最快。天上的白云为中层背景图，移动速度中等。而小山丘是最远的背景图，移动速度最慢。三个层次内容按不同速度移动，就会带来一种立体的视差效果。


<pre><code>
<!DOCTYPE html>
<html lang="zh-CN"><head>
<meta charset="UTF-8">
<title>视差滚动原理三</title>
<style>
body{
	height: 3000px;
	overflow-x: hidden; 
}
.scene{
	position: absolute;
	width: 100%;
	height: 100%;
}
img{
	position: absolute;

}
#scene_back{
}
#scene_center{
}
#scene_front{

}

#pokemon1{
	width: 150px;
	top: 200px;
	left: 50px;
}
#pokemon2{
	width: 300px;
	left: 800px;
	top: 450px;
}
#pokemon3{
	top: 600px;
	left: 150px;
}

#pokemon4{
	width: 200px;
	left: 800px;
	top: 400px;
}
#pokemon5{
	width: 300px;
	left: 500px;
	top: 500px;
}
#pokemon6{
	top: 1200px;
}

#pokemon7{
	width: 150px;
	left: 250px;
	top: 550px;
}
#pokemon8{
	width: 300px;
	left: 100px;
	top: 900px;
}
#pokemon9{
	top: 1400px;
	left: 400px;
}

 
</style></head>

<body style="zoom: 1;"><!--zoom:1;属性是IE浏览器的专有属性，Firefox等其它浏览器不支持。它可以设置或检索对象的缩放比例。除此之外，它还有其他一些小作用，比如触发ie的hasLayout属性，清除浮动、清除margin的重叠等。
但很遗憾的是，它通不过W3C验证-->

<div id="scene_back" class="scene" style="top: 0px;">
	<img id="pokemon1" src="http://www.alloyteam.com/wp-content/uploads/2014/01/001.png">
	<img id="pokemon4" src="http://www.alloyteam.com/wp-content/uploads/2014/01/004.png">
	<img id="pokemon7" src="http://www.alloyteam.com/wp-content/uploads/2014/01/007.png">
</div>
<div id="scene_center" class="scene" style="top: 200px;">
	<img id="pokemon2" src="http://www.alloyteam.com/wp-content/uploads/2014/01/002.png">
	<img id="pokemon5" src="http://www.alloyteam.com/wp-content/uploads/2014/01/005.png">
	<img id="pokemon8" src="http://www.alloyteam.com/wp-content/uploads/2014/01/008.png">
</div>
<div id="scene_front" class="scene" style="top: 700px;">
	<img id="pokemon3" src="http://www.alloyteam.com/wp-content/uploads/2014/01/003.png">
	<img id="pokemon6" src="http://www.alloyteam.com/wp-content/uploads/2014/01/006.png">
	<img id="pokemon9" src="http://www.alloyteam.com/wp-content/uploads/2014/01/009.png">
</div>

<script>
	var sceneBack = document.getElementById('scene_back'),
		sceneCenter = document.getElementById('scene_center'),
		sceneFront = document.getElementById('scene_front');
	var old_top1 = 0,
		old_top2 = 200,
		old_top3 = 700;

	addEvent(window,'scroll',onScroll);
	onScroll();

	function onScroll(e){
		var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
		sceneBack.style.top = old_top1+scrollTop*.9+'px';
		sceneCenter.style.top = old_top2+scrollTop*.7+'px';
		sceneFront.style.top = old_top3+scrollTop*.3+'px';	
	}

   	function addEvent(eventTarget, eventType, eventHandler) {
	/*兼容不同浏览器的绑定事件方法*/
	    if (eventTarget.addEventListener) {
	        eventTarget.addEventListener(eventType, eventHandler, false);
	    } else {
	        if (eventTarget.attachEvent) {
	            eventType = "on" + eventType;
	            eventTarget.attachEvent(eventType, eventHandler);
	        } else {
	            eventTarget["on" + eventType] = eventHandler;
	        }
	    }
    }

</script>


</body></html>
</code></pre>

4.4原理四

上下颠倒出现，这个跟原理三是一样的，唯独就是不是所有的元素都是往上升，而是一些元素上升，一些元素下沉。在计算top值的时候，不是“加上”，变成“减去”scrollTop就会有相应的效果。
<pre><code>
<!DOCTYPE html>
<html lang="zh-CN"><head>
<meta charset="UTF-8">
<title>视差滚动</title>
<style>
.container{
	position: absolute;
	width: 100%;
	height: 3000px;
}
img{
	position: absolute;
}
#ahri{
	left: 550px;
	
}
 
</style></head>


<body style="zoom: 1;">

<section class="container">
	<img id="sona" src="http://www.alloyteam.com/wp-content/uploads/2014/01/lol_sona.jpg" style="top: -1000px;">
	<img id="ahri" src="http://www.alloyteam.com/wp-content/uploads/2014/01/lol_ahri.jpg" style="top: 1000px;">
</section>

<script>

	var sona = document.getElementById('sona'),
		ahri = document.getElementById('ahri');
	var old_top1 = -1000,
		old_top2 = 1000;

	addEvent(window,'scroll',onScroll);
	onScroll();
	
	function onScroll(e){
		var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
		sona.style.top = old_top1+scrollTop*2+'px';
		ahri.style.top = old_top2-scrollTop*0+'px';
	}
	onScroll();

	function addEvent(eventTarget, eventType, eventHandler) {
	    if (eventTarget.addEventListener) {
	        eventTarget.addEventListener(eventType, eventHandler, false);
	    } else {
	        if (eventTarget.attachEvent) {
	            eventType = "on" + eventType;
	            eventTarget.attachEvent(eventType, eventHandler);
	        } else {
	            eventTarget["on" + eventType] = eventHandler;
	        }
	    }
    }

</script>


</body></html>
</pre></code>

原文：http://www.alloyteam.com/2014/01/parallax-scrolling-love-story/