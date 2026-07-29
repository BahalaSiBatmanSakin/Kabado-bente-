<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For You 🌷</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&family=Dancing+Script:wght@700&display=swap" rel="stylesheet">

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Poppins',sans-serif;
}

body{
background:linear-gradient(180deg,#ffd8e8,#fff3f8);
overflow:hidden;
height:100vh;
display:flex;
justify-content:center;
align-items:center;
color:#444;
}

.page{
position:absolute;
width:100%;
height:100%;
display:flex;
justify-content:center;
align-items:center;
padding:25px;
transition:.6s;
}

.hidden{
opacity:0;
pointer-events:none;
transform:translateY(30px);
}

.card{
width:100%;
max-width:380px;
background:rgba(255,255,255,.75);
backdrop-filter:blur(14px);
border-radius:28px;
padding:30px;
text-align:center;
box-shadow:0 15px 35px rgba(255,105,180,.15);
animation:fade .8s;
}

@keyframes fade{
from{
opacity:0;
transform:translateY(25px);
}
to{
opacity:1;
transform:translateY(0);
}
}

h1{
font-family:'Dancing Script',cursive;
font-size:46px;
color:#ff5d97;
margin-bottom:10px;
}

h2{
font-size:28px;
margin:15px 0;
color:#555;
}

p{
line-height:1.8;
font-size:15px;
margin-top:15px;
}

button{
margin-top:28px;
padding:14px 32px;
border:none;
border-radius:40px;
font-size:16px;
cursor:pointer;
transition:.3s;
}

.primary{
background:#ff6ea7;
color:white;
box-shadow:0 8px 20px rgba(255,110,167,.35);
}

.primary:hover{
transform:scale(1.05);
}

.secondary{
background:white;
color:#ff5d97;
border:2px solid #ffc3d8;
}

.tulip{
position:absolute;
font-size:26px;
opacity:.25;
animation:float linear infinite;
}

@keyframes float{
0%{
transform:translateY(120vh) rotate(0deg);
}
100%{
transform:translateY(-120px) rotate(360deg);
}
}

.loadingText{
font-size:20px;
font-weight:500;
animation:pulse 1.5s infinite;
}

@keyframes pulse{
50%{
opacity:.5;
}
}
</style>
</head>

<body>

<div id="flowers"></div>

<!-- Loading -->

<div class="page" id="loading">

<div class="card">

<h1>🌷</h1>

<div class="loadingText">
One small page,<br>
made just for you.
</div>

</div>

</div>

<!-- Landing -->

<div class="page hidden" id="landing">

<div class="card">

<h1>Hi. 🌷</h1>

<p>
I know this is a little unexpected.
</p>

<p>
I wanted to ask you something in a way that's a bit different.
Not because I had to...
I just thought you'd deserve something a little more thoughtful.
</p>

<button class="primary" onclick="openLetter()">
Continue →
</button>

</div>

</div>

<!-- Letter -->

<div class="page hidden" id="letter">

<div class="card">

<h1>Before I ask...</h1>

<p id="typeText"></p>

<button class="primary" id="nextBtn" style="display:none;" onclick="openQuestion()">
One more thing... 💗
</button>

</div>

</div>

<script>

const message=`I just wanted to say thank you.

Thank you for being someone who's genuinely easy to appreciate.

Whether it's the little things you do or simply the kind of person you are, you've made more moments brighter than you probably realize.

I'm really glad I got the chance to know you.

So... there's one small thing I'd like to ask.`;

function show(id){
document.querySelectorAll(".page").forEach(p=>p.classList.add("hidden"));
document.getElementById(id).classList.remove("hidden");
}

setTimeout(()=>{
show("landing");
},2500);

function openLetter(){
show("letter");

let i=0;

const target=document.getElementById("typeText");

const timer=setInterval(()=>{

target.innerHTML+=message.charAt(i);

i++;

if(i>=message.length){

clearInterval(timer);

document.getElementById("nextBtn").style.display="inline-block";

}

},28);

}

function flower(){

const f=document.createElement("div");

f.className="tulip";

f.innerHTML=Math.random()>.5?"🌷":"🌸";

f.style.left=Math.random()*100+"vw";

f.style.animationDuration=(8+Math.random()*6)+"s";

f.style.fontSize=(20+Math.random()*18)+"px";

document.body.appendChild(f);

setTimeout(()=>{

f.remove();

},15000);

}

setInterval(flower,700);

function openQuestion(){

show("question");

}

</script>

<!-- Question -->

<div class="page hidden" id="question">

<div class="card">

<h1>🌷</h1>

<h2>May I steal you for a photobooth?</h2>

<p>
Nothing too fancy.

Just you, me, a tiny booth, a couple of goofy poses,
and a memory I'd love to keep.
</p>

<div style="display:flex;justify-content:center;gap:15px;margin-top:30px;">

<button id="yesBtn" class="primary" onclick="yesClicked()">
Yes 💗
</button>

<button id="maybeBtn" class="secondary" onclick="maybeClicked()">
Maybe
</button>

</div>

</div>

</div>

<!-- Ending -->

<div class="page hidden" id="ending">

<div class="card">

<h1>🌷</h1>

<h2>You just made my day.</h2>

<p>
Thank you for saying yes.

I'm looking forward to making
our first little photobooth memory together.

I hope it's something we'll both smile about whenever we look back at it.
🤍
</p>

<div style="
margin:25px auto;
width:170px;
background:white;
padding:10px;
border-radius:8px;
box-shadow:0 8px 20px rgba(0,0,0,.15);
">

<div style="
height:140px;
background:#ffe5ef;
display:flex;
align-items:center;
justify-content:center;
font-size:48px;
">
📸
</div>

<p style="font-size:13px;margin-top:10px;">
Reserved for our first photobooth picture.
</p>

</div>

</div>

</div>

<script>

let maybeCount=0;

function maybeClicked(){

maybeCount++;

const yes=document.getElementById("yesBtn");
const maybe=document.getElementById("maybeBtn");

yes.style.transform=`scale(${1+maybeCount*0.18})`;

maybe.style.transform=`scale(${1-maybeCount*0.18})`;

maybe.style.opacity=1-(maybeCount*0.25);

if(maybeCount>=4){

maybe.style.transition=".5s";

maybe.style.opacity="0";

setTimeout(()=>{

maybe.style.display="none";

},500);

}

}

function yesClicked(){

show("ending");

confetti();

}

function confetti(){

for(let i=0;i<120;i++){

const c=document.createElement("div");

c.innerHTML=Math.random()>.5?"🌸":"🌷";

c.style.position="fixed";
c.style.left=Math.random()*100+"vw";
c.style.top="-20px";
c.style.fontSize=(16+Math.random()*18)+"px";
c.style.transition="4s linear";

document.body.appendChild(c);

setTimeout(()=>{

c.style.transform=`translateY(${window.innerHeight+150}px) rotate(${Math.random()*720}deg)`;

},50);

setTimeout(()=>{

c.remove();

},4000);

}

}

</script>

</body>
</html>

}

</script>
