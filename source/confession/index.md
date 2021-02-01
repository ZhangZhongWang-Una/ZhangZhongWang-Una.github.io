---
title: 告白
comments: false
date: 2021-01-12 22:21:06
keywords:
description:
photos: /images/categories1.png
type: 
layout: false
---
{% raw %}
    <body>
        <!-- <div id="main">
            <div id="box"></div>
            <canvas id="tree" style="position: absolute;" ></canvas>
            <canvas id="flower" style="position: absolute;"></canvas>
        </div> -->
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        
        <script type="text/javascript" src="/lib/confession/jquery.min.js"></script>
        <script type="text/javascript" src="/lib/confession/jscex.min.js"></script>
		<script type="text/javascript" src="/lib/confession/jscex-parser.js"></script>
		<script type="text/javascript" src="/lib/confession/jscex-jit.js"></script>
		<script type="text/javascript" src="/lib/confession/jscex-builderbase.min.js"></script>
		<script type="text/javascript" src="/lib/confession/jscex-async.min.js"></script>
		<script type="text/javascript" src="/lib/confession/jscex-async-powerpack.min.js"></script>
		<script type="text/javascript" src="/lib/confession/functions.js" charset="utf-8"></script>
		<script type="text/javascript" src="/lib/confession/love.js" charset="utf-8"></script>
        
    <!-- <script type="text/javascript" src="/js/Blossoms.js"></script> -->
    <title>告白</title>
    <link type="text/css" rel="stylesheet" href="/lib/confession/default.css">
        <div id="main">
            <div id="error">本页面采用HTML5编辑，目前您的浏览器无法显示，请换成谷歌(<a href="http://www.google.cn/chrome/intl/zh-CN/landing_chrome.html?hl=zh-CN&brand=CHMI">Chrome</a>)或者火狐(<a href="http://firefox.com.cn/download/">Firefox</a>)浏览器，或者其他游览器的最新版本。</div>
            <div id="wrap">
                <div id="text">
			        <div id="code">
			        	<span class="say">* 致女某某： *</span><br>
						<span class="say"> </span><br>
			        	<span class="say">· 女某某，情人节快乐！</span><br>
						<span class="say"> </span><br>
                        <span class="say">· 不经意相识, 或许是缘分，或许是注定的。</span><br>
						<span class="say"> </span><br>
			        	<span class="say">· 虽然.....，但......！</span><br>
						<span class="say"> </span><br>
			        	<span class="say">· 虽然......，但.......！</span><br>
						<span class="say"> </span><br>
			        	<span class="say">· 虽然......，但......！</span><br>
						<span class="say"> </span><br>
			        	<span class="say">· 虽然......</span><br>
						<span class="say"> </span><br>
			        	<span class="say">· 无论如何，只要你我依旧喜欢对方，我会一直陪着你。</span><br>
                        <span class="say"> </span><br>
                        <span class="say">· You are my only girlfriend.</span><br>
						<span class="say"> </span><br>
						<span class="say">· I love you,×××!</span><br>
						<span class="say"> </span><br>
                        <span class="say"><span class="space"></span>--@author 男某某--</span>
			        </div>
                </div>
                <div id="clock-box">
                    <span class="STYLE1">现在是</span>男某某 <span class="STYLE1" style="color: red">❤</span> 女某某<span class="STYLE1" style="color: red">相恋</span>
                  <div id="clock"></div>
              </div>
                <canvas id="canvas" width="1100" height="680"></canvas>
            </div>
            
        </div>
    
    <script>
    </script>

    <script>
    (function(){
        var canvas = $('#canvas');
		
        if (!canvas[0].getContext) {
            $("#error").show();
            return false;
        }

        var width = canvas.width();
        var height = canvas.height();
        
        canvas.attr("width", width);
        canvas.attr("height", height);

        var opts = {
            seed: {
                x: width / 2 - 20,
                color: "rgb(190, 26, 37)",
                scale: 2
            },
            branch: [
                [535, 680, 570, 250, 500, 200, 30, 100, [
                    [540, 500, 455, 417, 340, 400, 13, 100, [
                        [450, 435, 434, 430, 394, 395, 2, 40]
                    ]],
                    [550, 445, 600, 356, 680, 345, 12, 100, [
                        [578, 400, 648, 409, 661, 426, 3, 80]
                    ]],
                    [539, 281, 537, 248, 534, 217, 3, 40],
                    [546, 397, 413, 247, 328, 244, 9, 80, [
                        [427, 286, 383, 253, 371, 205, 2, 40],
                        [498, 345, 435, 315, 395, 330, 4, 60]
                    ]],
                    [546, 357, 608, 252, 678, 221, 6, 100, [
                        [590, 293, 646, 277, 648, 271, 2, 80]
                    ]]
                ]] 
            ],
            bloom: {
                num: 700,
                width: 1080,
                height: 650,
            },
            footer: {
                width: 1200,
                height: 5,
                speed: 10,
            }
        }

        var tree = new Tree(canvas[0], width, height, opts);
        var seed = tree.seed;
        var foot = tree.footer;
        var hold = 1;

        canvas.click(function(e) {
            var offset = canvas.offset(), x, y;
            x = e.pageX - offset.left;
            y = e.pageY - offset.top;
            if (seed.hover(x, y)) {
                hold = 0; 
                canvas.unbind("click");
                canvas.unbind("mousemove");
                canvas.removeClass('hand');
            }
        }).mousemove(function(e){
            var offset = canvas.offset(), x, y;
            x = e.pageX - offset.left;
            y = e.pageY - offset.top;
            canvas.toggleClass('hand', seed.hover(x, y));
        });

        var seedAnimate = eval(Jscex.compile("async", function () {
            seed.draw();
            while (hold) {
                $await(Jscex.Async.sleep(10));
            }
            while (seed.canScale()) {
                seed.scale(0.95);
                $await(Jscex.Async.sleep(10));
            }
            while (seed.canMove()) {
                seed.move(0, 2);
                foot.draw();
                $await(Jscex.Async.sleep(10));
            }
        }));

        var growAnimate = eval(Jscex.compile("async", function () {
            do {
    	        tree.grow();
                $await(Jscex.Async.sleep(10));
            } while (tree.canGrow());
        }));

        var flowAnimate = eval(Jscex.compile("async", function () {
            do {
    	        tree.flower(2);
                $await(Jscex.Async.sleep(10));
            } while (tree.canFlower());
        }));

        var moveAnimate = eval(Jscex.compile("async", function () {
            tree.snapshot("p1", 240, 0, 610, 680);
            while (tree.move("p1", 500, 0)) {
                foot.draw();
                $await(Jscex.Async.sleep(10));
            }
            foot.draw();
            tree.snapshot("p2", 500, 0, 610, 680);


            canvas.parent().css("background", "url(" + tree.toDataURL('image/png') + ")");
            canvas.css("background", "#ffe");
            $await(Jscex.Async.sleep(300));
            canvas.css("background", "none");
        }));

        var jumpAnimate = eval(Jscex.compile("async", function () {
            var ctx = tree.ctx;
            while (true) {
                tree.ctx.clearRect(0, 0, width, height);
                tree.jump();
                foot.draw();
                $await(Jscex.Async.sleep(25));
            }
        }));
       //下面修改起始日期
        var textAnimate = eval(Jscex.compile("async", function () {
		    var together = new Date();
		    together.setFullYear(2020, 1, 2); 			//时间年月日 月份0~11
		    together.setHours(22);						//小时	
		    together.setMinutes(22);					//分钟
		    together.setSeconds(2);					//秒前一位
		    together.setMilliseconds(2);				//秒第二位

		    $("#code").show().typewriter();
            $("#clock-box").fadeIn(500);
            while (true) {
                timeElapse(together);
                $await(Jscex.Async.sleep(1000));
            }
        }));

        var runAsync = eval(Jscex.compile("async", function () {
            $await(seedAnimate());
            $await(growAnimate());
            $await(flowAnimate());
            $await(moveAnimate());

            textAnimate().start();

            $await(jumpAnimate());
        }));

        runAsync().start();
    })();
    </script>
    <!-- <script>
      (function($,win,dom,undef) {
	
	var bos_html = $('<div id="box" style="width:500px;height:350px;"><canvas id="tree"></canvas><canvas id="flower"></canvas></div>');
	bos_html.appendTo("body")
 
	//两个canvas
	var tree = dom.getElementById("tree");
	var box =$("#box");
	console.log(tree);
	tree.width = 500;//$("#box").width();
	tree.height = 350//$("#box").height() ;
	var tCxt = tree.getContext("2d");
	var flower = document.getElementById("flower");
	flower.width = 500;//$("#box").width();
	flower.height = 350;//$("#box").height();
	var cxt = flower.getContext("2d");
 
	var flowerList = [];//樱花列表
	var rootTop = 350 ;//树起点
	var flowerColor = "rgba(255,192,203,.3)" ;//花色
	var flowerColorDeep = "rgba(241,158,194,.5)" ;//花色深
	var treeColor2 = "rgba(255,192,203,.5)" ;//树枝颜色
	var treeColor = "#8B7355" ;//树干颜色
	var fallList = [];//飘落樱花列表
	var g = 0.01 ;//重力加速度
	var gWind = 0.005;//风力加速度
	var limitSpeedY = 1;//速度上限
	var limitSpeedX = 1 ;//速度上限
 
	cxt.shadowColor= "#FFF" ;
	cxt.shadowBlur = 10 ;
 
	function drawTree(x,y,deg,step,type){
		var deg1 = step%2 == 0 ? 0.1 : -0.1 ;
		var x1 = x + Math.cos(deg+deg1) * (step+4) * 0.8 ;//以步长来判断枝干长度 x轴偏移大一些
		var y1 = y + Math.sin(deg+deg1) * (step-1) * 0.8 ;//以步长来判断枝干长度 Y轴压缩一些
		tCxt.beginPath();
		tCxt.lineWidth = step/3;
		tCxt.moveTo(x,y);
		tCxt.lineTo(x1,y1);
		tCxt.strokeStyle = (step > 5 ) ? treeColor : treeColor2 ;//细纸条都换成花的颜色
		tCxt.stroke();
		if(step > 10){//树干相交的位置有间隙，以一个圆填充
			tCxt.fillStyle = treeColor ;
			tCxt.arc(x,y,step/6,0,Math.PI*2);
			tCxt.fill();
		}
		
		if( step < 3 || (step < 20 && Math.random() > 0.4)){
			//末梢位置 画花瓣
			var color = [flowerColorDeep,flowerColor,flowerColor][Math.round(Math.random()+0.2)] ;
			var r = 2+Math.random()*2
			tCxt.fillStyle = color ;
			tCxt.arc(x1+Math.random()*3,y1+Math.random()*3,r,0,Math.PI)
			tCxt.fill();
			flowerList.push({x:x,y:y,sx:(Math.random()-0.5),sy:0,color:color,r:r,deg:deg});//保存下画樱花的位置
		}
		
		step -- ;
		if(step > 0){
			drawTree(x1,y1,deg,step,type);
			if(step%3 == 1 && step > 0 && step < 30)
				drawTree(x1,y1,deg+0.2 + 0.3 * Math.random(),Math.round(step/1.13));//右分叉
			if(step%3 == 0 && step > 0 && step < 30)
				drawTree(x1,y1,deg-0.2 - 0.3 * Math.random(),Math.round(step/1.13));//左分叉
		}
	}
 
	drawTree(tree.width/2,rootTop,-Math.PI/2,30,1);//执行
 
	var len = flowerList.length ;
	function step(){
		if(Math.random() > 0.3)    fallList.push(flowerList[Math.floor(Math.random()*len)]);//随机取出一个，花瓣复制到飘落花瓣的列表中
 
		cxt.clearRect(0,0,tree.width,tree.height);
		for(var i = 0 ;i < fallList.length ; i ++){
			if(fallList[i].sy < limitSpeedY) fallList[i].sy += g ;
			fallList[i].sx += gWind ;
			fallList[i].x += fallList[i].sx ;
			fallList[i].y += fallList[i].sy ;
			if(fallList[i].y > rootTop){//飘到树根的花瓣移除
				fallList.splice(i,1);
				i -- ;
				continue ;
			}
			cxt.beginPath();
			cxt.fillStyle = fallList[i].color ;
			fallList[i].deg += fallList[i].sx*0.05 ;//跟速度相关的旋转花瓣
			cxt.arc(fallList[i].x,fallList[i].y,fallList[i].r,fallList[i].deg,fallList[i].deg+Math.PI*1.3);
			cxt.fill();
		}
		requestAnimationFrame(step);
	}
	requestAnimationFrame(step);
})(jQuery,window,document);  
    </script> -->

    
</body>




{% endraw %}