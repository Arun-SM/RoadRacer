<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
  "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
	<head>
<style type="text/css">
.outer_cover {
	height: 600px;
	width: 500px;
	background-color: #323255;
	margin: 0 auto;
}
.player {
	position: absolute;
	height: 125px;
	width: 100px;
	background-color: #BCBCBC;
	margin-top: 450px;
}
.top_design {
	position: absolute;
	height: 50px;
	width: 76px;
	background-color: #89899A;
	margin-top: 30px;
}
.player_decorator {
	position: absolute;
	height: 101px;
	width: 76px;
	background-color: #A9A9A9;
	margin-top: 12px;
	margin-left: 12px;
}
.devils {
	position: absolute;
	top: -110px;
	height: 125px;
	width: 100px;
	background-color: #787878;
	z-index: 100;
}
.devils_top_design {
	position: absolute;
	height: 75px;
	width: 100px;
	background-color: #A9EDED;
}
.road_divider1 {
	position: absolute;
	height: 80px;
	width: 20px;
	left: 0;
	right: 0;
	top: -70px;
	background-color: #FFFFFF;
	margin-left: auto;
	margin-right: auto;
}
.road_divider2 {
	position: absolute;
	height: 80px;
	width: 20px;
	left: 0;
	right: 0;
	top: 90px;
	background-color: #FFFFFF;
	margin-left: auto;
	margin-right: auto;
}
.road_divider3 {
	position: absolute;
	height: 80px;
	width: 20px;
	left: 0;
	right: 0;
	top: 250px;
	background-color: #FFFFFF;
	margin-left: auto;
	margin-right: auto;
}
.road_divider4 {
	position: absolute;
	height: 80px;
	width: 20px;
	left: 0;
	right: 0;
	top: 410px;
	background-color: #FFFFFF;
	margin-left: auto;
	margin-right: auto;
}
.game_over {
	position: absolute;
	height: 130px;
	width: 500px;
	top: 0;
	bottom: 0;
	background-color: #FFEEFF;
	border-width: 2px;
	margin-top: auto;
	margin-bottom: auto;
	visibility: hidden;
	font-family: Calibri;
	font-size: 20;
	text-align: center;
	vertical-align: center;
	z-index: 1000;
}
</style>
<script type="text/javascript">
//document.keydown = function_keypress;
var points = 0;
var e1 = 0, e2 = 0, e3 = 0, e4 = 0;
var timer_event = 0;
window.addEventListener("load", function_timer);
window.addEventListener("keydown", function_keypress);
function function_nothing() {
	return;
}
function checkForGameOver() {
	p = document.getElementById("player");
	if((e1 !== 0 &amp;&amp; 
		(((p.offsetLeft &lt;= (e1.offsetLeft + e1.offsetWidth) &amp;&amp; p.offsetLeft &gt;= e1.offsetLeft) ||
		((p.offsetLeft + p.offsetWidth) &gt;= e1.offsetLeft &amp;&amp; (p.offsetLeft + p.offsetWidth) &lt;= (e1.offsetLeft + e1.offsetWidth))) &amp;&amp;
		(p.offsetTop &lt;= (e1.offsetTop + e1.offsetHeight)))) ||
	(e2 !== 0 &amp;&amp; 
		(((p.offsetLeft &lt;= (e2.offsetLeft + e2.offsetWidth) &amp;&amp; p.offsetLeft &gt;= e2.offsetLeft) ||
		((p.offsetLeft + p.offsetWidth) &gt;= e2.offsetLeft &amp;&amp; (p.offsetLeft + p.offsetWidth) &lt;= (e2.offsetLeft + e2.offsetWidth))) &amp;&amp;
		(p.offsetTop &lt;= (e2.offsetTop + e2.offsetHeight)))) ||
	(e3 !== 0 &amp;&amp; 
		(((p.offsetLeft &lt;= (e3.offsetLeft + e3.offsetWidth) &amp;&amp; p.offsetLeft &gt;= e3.offsetLeft) ||
		((p.offsetLeft + p.offsetWidth) &gt;= e3.offsetLeft &amp;&amp; (p.offsetLeft + p.offsetWidth) &lt;= (e3.offsetLeft + e3.offsetWidth))) &amp;&amp;
		(p.offsetTop &lt;= (e3.offsetTop + e3.offsetHeight)))) ||
	(e4 !== 0 &amp;&amp; 
		(((p.offsetLeft &lt;= (e4.offsetLeft + e4.offsetWidth) &amp;&amp; p.offsetLeft &gt;= e4.offsetLeft) ||
		((p.offsetLeft + p.offsetWidth) &gt;= e4.offsetLeft &amp;&amp; (p.offsetLeft + p.offsetWidth) &lt;= (e4.offsetLeft + e4.offsetWidth))) &amp;&amp;
		(p.offsetTop &lt;= (e4.offsetTop + e4.offsetHeight))))) {

//		alert(e1 + " e1 " + e2 + " e2 " + e3 + " e3 " + e4 + " e4 " + p.offsetLeft + " " + e1.offsetLeft + " " + e1.offsetWidth + " " + p.offsetWidth + " " + p.offsetTop + " " + e1.offsetTop + " " + e1.offsetHeight);

		window.removeEventListener("keydown", function_nothing);
		window.clearInterval(timer_event);
		var go = document.getElementById("game_over");
		go.style.visibility = "visible";
		var score = document.getElementById("score");
		score.innerHTML = (points/10);
		var score_teaser = document.getElementById("score_teaser");
		score_teaser.innerHTML = (points/10) + 1;
	}
}
function function_timer(e) {
	timer_event = setInterval(function() { move_car() }, 200);
}
function move_car() {
	points = points + 10;
	rd1 = document.getElementById("road_divider1");
	rd2 = document.getElementById("road_divider2");
	rd3 = document.getElementById("road_divider3");
	rd4 = document.getElementById("road_divider4");
	if(rd1.offsetTop &gt;= 100) {
		rd1.style.top = "-70px";
		rd2.style.top = "90px";
		rd3.style.top = "250px";
		rd4.style.top = "410px";
	}
	else {
		rd1.style.top = rd1.offsetTop + 60 + "px";
		rd2.style.top = rd2.offsetTop + 60 + "px";
		rd3.style.top = rd3.offsetTop + 60 + "px";
		rd4.style.top = rd4.offsetTop + 60 + "px";
	}
	if(points % 150 == 0) {
		b = document.getElementById("outer_cover");
		p = document.getElementById("player");
		var new_devil = document.createElement("div");
		var new_devil_top = document.createElement("div");
		new_devil.className = "devils";
		new_devil_top.className = "devils_top_design";
		new_devil.appendChild(new_devil_top);
		var new_devil_left = Math.floor((Math.random() * 500));
		new_devil_left = new_devil_left + b.offsetLeft;
		if(new_devil_left &gt;= (b.offsetLeft + b.offsetWidth - p.offsetWidth)) {
			new_devil_left = b.offsetLeft + b.offsetWidth - p.offsetWidth;
		}
		new_devil.style.left = new_devil_left + "px";
		document.getElementById("outer_cover").appendChild(new_devil);
		if(e1 == 0) {
			e1 = new_devil;
		}
		else if(e2 == 0) {
			e2 = new_devil;
		}
		else if(e3 == 0) {
			e3 = new_devil;
		}
		else if(e4 == 0) {
			e4 = new_devil;
		}
	}
	b = document.getElementById("outer_cover");
	if(e1 !== 0 &amp;&amp; (e1.offsetTop &gt;= (b.offsetTop + b.offsetHeight - 60))) {
		b.removeChild(e1);
		e1 = 0;
	}
	else if(e1 !== 0) {
		e1.style.top = e1.offsetTop + 30 + "px";
	}
	if(e2 !== 0 &amp;&amp; (e2.offsetTop &gt;= (b.offsetTop + b.offsetHeight - 60))) {
		b.removeChild(e2);
		e2 = 0;
	}
	else if(e2 !== 0) {
		e2.style.top = e2.offsetTop + 30 + "px";
	}
	if(e3 !== 0 &amp;&amp; (e3.offsetTop &gt;= (b.offsetTop + b.offsetHeight - 60))) {
		b.removeChild(e3);
		e3 = 0;
	}
	else if(e3 !== 0) {
		e3.style.top = e3.offsetTop + 30 + "px";
	}
	if(e4 !== 0 &amp;&amp; (e4.offsetTop &gt;= (b.offsetTop + b.offsetHeight - 60))) {
		b.removeChild(e4);
		e4 = 0;
	}
	else if(e4 !== 0) {
		e4.style.top = e4.offsetTop + 30 + "px";
	}
	checkForGameOver();
}
function function_keypress(e) {
	//alert("key_pressed");
	p = document.getElementById("player");
	b = document.getElementById("outer_cover");
	//alert(e.keyCode);
	// consider moving only left or right
	if((e.keyCode != "37")&amp;&amp;(e.keyCode != "39")) {
		//alert("Coming in");
		return;
	}
	// Left pressed
	if(e.keyCode == 37) {
		//alert(p.offsetLeft + " Hello -- Saw ?" + b.offsetLeft);
		if(p.offsetLeft &lt;= b.offsetLeft) {
			// ignore key presee event here, left border
			return;
		}
		p.style.left = p.offsetLeft - 10 + "px";
	}
	// Right pressed
	p.offsetRight = p.offsetLeft + p.offsetWidth;
	b.offsetRight = b.offsetLeft + b.offsetWidth;
	if(e.keyCode == 39) {
		if(p.offsetRight &gt;= b.offsetRight) {
			// right border reacheeds
			return;
		}
		//alert("Right pressed " + p.offsetRight);
		p.style.left = p.offsetLeft + 10 + "px";
	}
	checkForGameOver();
}
</script>
		<title>
				Road-Racer GAME !!!
		</title>
	</head>
	<body>
<!-- Airplane -->
		<div class="outer_cover" id="outer_cover">
			<div class="road_divider1" id="road_divider1">
			</div>
			<div class="road_divider2" id="road_divider2">
			</div>
            <div class="road_divider3" id="road_divider3">
			</div>
			<div class="road_divider4" id="road_divider4">
			</div>
			<div class="player" id="player">
            	<div class="player_decorator" id="player_decorator">
            		<div class="top_design" id="top_design">
            		</div>
            	</div>
            </div>
            <div class="devil_space" id="devil_space">
            </div>
            <div class = "game_over" id="game_over">
            	Game Over and Score is <div id="score"></div><br/>
            	Next time try for <div id="score_teaser"></div>
            	<button onclick="location.reload()">TRY AGAIN</button>
            </div>
		</div>
	</body>
</html>
