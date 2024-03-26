
var svg =`

<svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
	 viewBox="0 0 512 512" style="enable-background:new 0 0 512 512;" xml:space="preserve">
<g transform="translate(1 1)">
	<g>
		<g>
			<path d="M192.707,163.693c-3.413-3.413-8.533-3.413-11.947,0l-85.333,85.333c-2.56,2.56-3.413,5.973-1.707,9.387
				c0.853,1.707,1.707,2.56,2.56,3.413l84.48,84.48c1.707,1.707,3.413,2.56,5.973,2.56s4.267-0.853,5.973-2.56
				c3.413-3.413,3.413-8.533,0-11.947L113.347,255l79.36-79.36C196.12,172.227,196.12,167.107,192.707,163.693z" class="brainPath"/>
			<path d="M413.72,248.173l-84.48-84.48c-3.413-3.413-8.533-3.413-11.947,0s-3.413,8.533,0,11.947l79.36,79.36l-79.36,79.36
				c-3.413,3.413-3.413,8.533,0,11.947c1.707,1.707,3.413,2.56,5.973,2.56s5.12-0.853,5.973-2.56l85.333-85.333
				c2.56-2.56,3.413-5.973,1.707-9.387C415.427,249.88,414.573,249.027,413.72,248.173z" class="brainPath"/>
			<path d="M282.307,161.987c-4.267-0.853-8.533,1.707-10.24,5.973l-51.2,170.667c-0.853,4.267,1.707,8.533,5.973,10.24
				c0.853,0,1.707,0,2.56,0c3.413,0,6.827-2.56,7.68-5.973l51.2-170.667C289.133,167.96,286.573,163.693,282.307,161.987z" class="brainPath"/>
			<path d="M400.067-1H109.933C48.493-1-1,48.493-1,109.933v290.133C-1,461.507,48.493,511,109.933,511h290.133
				C461.507,511,511,461.507,511,400.067V109.933C511,48.493,461.507-1,400.067-1z M493.933,400.067
				c0,52.053-41.813,93.867-93.867,93.867H109.933c-52.053,0-93.867-41.813-93.867-93.867V109.933
				c0-52.053,41.813-93.867,93.867-93.867h290.133c52.053,0,93.867,41.813,93.867,93.867V400.067z" class="brainPath"/>
		</g>
	</g>
</g>
</svg>


`

/*Helper functions*/
/******************/
function complimentary(x){
return 255 - Math.abs((x - 127.5));
}
function complimentary2(x){
return 255 - Math.abs((x - 63.75));
}
function complimentary3(x){
return 255 - Math.abs((x - 191.25));
}

//correct for numbers over 255 and under 0
function corrected(x){
var val = (x*1);
if(val > 255){
  return 255;
} else if (val < 0){
  return 0;
} else {
  return Math.round(val);
}
}

function addClass(query, theClass) {
var x = document.querySelectorAll(query);
for (var i = 0; i < x.length; i++) {
  x[i].classList.add(theClass);
}
}

//random number generator
function randNum(from, to) {
return Math.floor(Math.random() * (to - from + 1) + from);
}
/******************/
/*Helper functions*/

function setColors(param){
var r,g,b;
//get new random color
//lighter if "light" is passed
//or if it's day vs. night

//get hours
var d = new Date();
var hh = d.getHours();

/*param == "light"*/
if( hh > 5 && hh < 19 ){
  r = randNum(200,255);
  g = randNum(200,255);
  b = randNum(200,255);
//darker if "dark" is passed
/*param == "dark"*/
} else if ( hh < 6 || hh > 18  ){
  r = randNum(0,50);
  g = randNum(0,50);
  b = randNum(0,50);
  //or else use default lime and black styling
} else {
  return;
}
//set background color
var bgColor = "rgb(" + r + "," + g + "," + b + ")";

//get a complimentary color 1
var r1 = corrected(Math.round(complimentary(r)));
var g1 = corrected(Math.round(complimentary(g)));
var b1 = corrected(Math.round(complimentary(b)));
var brainColor ="#111";
//get a complimentary color 2
var r2 = corrected(Math.round(complimentary2(r)));
var g2 = corrected(Math.round(complimentary2(g)));
var b2 = corrected(Math.round(complimentary2(b)));
var brainColor2 ="#fff";
//get a complimentary color 3
var r3 = corrected(Math.round(complimentary3(r)));
var g3 = corrected(Math.round(complimentary3(g)));
var b3 = corrected(Math.round(complimentary3(b)));
var brainColor3 = "#fff";

var bp = document.getElementsByClassName("brainPath");
for (var i=0; i<bp.length; i++){
  bp[i].style.stroke = brainColor;
}
var br = document.getElementsByClassName("brainRect");
for (var i=0; i<br.length; i++){
  br[i].style.stroke = brainColor;
  br[i].style.fill = brainColor;
}
var bc = document.getElementsByClassName("brainCircle");
for (var i=0; i<bc.length; i++){
  bc[i].style.stroke = brainColor2;
  bc[i].style.fill = brainColor2;
}
var bc = document.getElementsByClassName("brainEllipse");
for (var i=0; i<bc.length; i++){
  bc[i].style.stroke = brainColor3;
  bc[i].style.fill = brainColor3;
}

}

//gets the current line length of the svg
function animateSVGs() {
var allPaths = document.querySelectorAll("path");
for (var i = 0; i < allPaths.length; i++) {
  var lineLength = allPaths[i].getTotalLength();
  allPaths[i].style.strokeDasharray = lineLength;
  allPaths[i].style.strokeDashoffset = lineLength;
  //neg animation times start the animation midway
  allPaths[i].style.animationDelay = randNum(-50, 50) / 10 + "s";
}
var allRects = document.querySelectorAll("rect");
for (var i = 0; i < allRects.length; i++) {
  allRects[i].style.animationDelay = randNum(-50, 50) / 10 + "s";
}
var allCircles = document.querySelectorAll("circle");
for (var i = 0; i < allCircles.length; i++) {
  allCircles[i].style.animationDelay = randNum(-50, 50) / 10 + "s";
}
var allEllipses = document.querySelectorAll("ellipse");
for (var i = 0; i < allEllipses.length; i++) {
  allEllipses[i].style.animationDelay = randNum(-50, 50) / 10 + "s";
}
}

function neuralize() {
document.querySelector(".aiContainer").innerHTML = "";
document.querySelector(".aiContainer").innerHTML = svg;
animateSVGs();
addClass("path", "animatePaths");
addClass("rect", "animateRects");
addClass("circle", "animateCircles");
addClass("ellipse", "animateCircles");
}

document.querySelector(".aiContainer").addEventListener("click", function(){setColors("dark")});

neuralize();
setColors("dark");
















