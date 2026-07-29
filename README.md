<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For You 🌷</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&family=Dancing+Script:wght@700&display=swap" rel="stylesheet">

<link rel="stylesheet" href="style.css">
</head>

<body>

<div id="petals"></div>

<!-- Loading -->
<section id="loading" class="page active">
    <div class="card">
        <h1>🌷</h1>
        <h2>One small page...</h2>
        <p>made just for you.</p>
    </div>
</section>

<!-- Landing -->
<section id="landing" class="page">
    <div class="card">
        <h1>Hi. 🌷</h1>

        <p>
            I know this is a little unexpected.
        </p>

        <p>
            I wanted to ask you something in a way that's
            a little different.
        </p>

        <button onclick="showLetter()">
            Continue →
        </button>
    </div>
</section>

<!-- Letter -->
<section id="letter" class="page">

<div class="card">

<h1>Before I ask...</h1>

<p id="typing"></p>

<button id="continueBtn" onclick="showQuestion()">
One more thing 💗
</button>

</div>

</section>

<!-- Question -->

<section id="question" class="page">

<div class="card">

<h1>📸</h1>

<h2>
May I steal you
for a photobooth?
</h2>

<p>
Nothing too fancy.

Just you,
me,
a tiny booth,
a couple of goofy poses,
and a memory I'd love to keep.
</p>

<div class="buttons">

<button id="yesBtn" onclick="yesAnswer()">
Yes 💗
</button>

<button id="maybeBtn" onclick="maybeAnswer()">
Maybe
</button>

</div>

</div>

</section>

<!-- Ending -->

<section id="ending" class="page">

<div class="card">

<h1>🌷</h1>

<h2>
You just made my day.
</h2>

<p>
Thank you for saying yes.

I'm looking forward
to making our first little
photobooth memory together.
🤍
</p>

<div class="polaroid">

<div class="photo">
📸
</div>

<p>
Reserved for our first
photobooth picture.
</p>

</div>

</div>

</section>

<script src="script.js"></script>

</body>
</html>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Poppins',sans-serif;
}

html,body{
width:100%;
min-height:100%;
overflow-x:hidden;
background:#ffeef5;
}

body{
background:linear-gradient(180deg,#ffd9e8,#fff8fb);
color:#444;
}

.page{
display:none;
min-height:100vh;
padding:30px 20px;
justify-content:center;
align-items:center;
}

.page.active{
display:flex;
animation:fade .7s ease;
}

.card{
width:100%;
max-width:380px;
background:rgba(255,255,255,.8);
backdrop-filter:blur(12px);
border-radius:30px;
padding:28px;
text-align:center;
box-shadow:0 15px 40px rgba(255,105,180,.18);
position:relative;
overflow:hidden;
}

.card::before{
content:"🌷";
position:absolute;
top:15px;
right:18px;
font-size:22px;
opacity:.3;
}

h1{
font-family:'Dancing Script',cursive;
font-size:48px;
color:#ff5c99;
margin-bottom:10px;
}

h2{
font-size:28px;
margin-bottom:18px;
color:#555;
}

p{
font-size:15px;
line-height:1.8;
margin-bottom:14px;
}

button{
border:none;
outline:none;
cursor:pointer;
padding:14px 28px;
border-radius:999px;
font-size:16px;
font-weight:600;
transition:.35s;
}

button:hover{
transform:translateY(-2px);
}

#continueBtn,
button:first-child{
background:#ff6ea8;
color:white;
box-shadow:0 10px 20px rgba(255,110,168,.3);
}

#continueBtn:hover,
button:first-child:hover{
background:#ff5b99;
}

#maybeBtn{
background:#fff;
border:2px solid #ffc6dc;
color:#ff5b99;
}

.buttons{
display:flex;
justify-content:center;
gap:15px;
margin-top:25px;
flex-wrap:wrap;
}

.polaroid{
margin:25px auto 0;
width:180px;
background:white;
padding:10px;
border-radius:8px;
box-shadow:0 10px 20px rgba(0,0,0,.12);
}

.photo{
height:145px;
background:#ffe3ee;
display:flex;
align-items:center;
justify-content:center;
font-size:55px;
border-radius:4px;
}

.polaroid p{
font-size:13px;
margin-top:10px;
}

#typing{
min-height:170px;
text-align:left;
white-space:pre-line;
}

#petals{
position:fixed;
inset:0;
pointer-events:none;
overflow:hidden;
z-index:-1;
}

.petal{
position:absolute;
font-size:22px;
animation:fall linear forwards;
opacity:.35;
}

@keyframes fall{
0%{
transform:translateY(-10vh) rotate(0deg);
}
100%{
transform:translateY(110vh) rotate(360deg);
}
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

@media(max-width:400px){

.card{
padding:22px;
}

h1{
font-size:42px;
}

h2{
font-size:24px;
}

p{
font-size:14px;
}

button{
width:100%;
}

.buttons{
flex-direction:column;
}

}
// ===== Pages =====
const pages = document.querySelectorAll(".page");

function showPage(id){
    pages.forEach(page => page.classList.remove("active"));
    document.getElementById(id).classList.add("active");
}

// ===== Loading =====
setTimeout(()=>{
    showPage("landing");
},2200);

// ===== Letter =====
const letter = `I just wanted to say thank you.

Thank you for being someone who's genuinely easy to appreciate.

Whether it's your kindness, the little things you do, or simply the way you are, you've made more moments brighter than you probably realize.

I'm really glad I got the chance to know you.

So... there's one small thing I'd like to ask. 🌷`;

function showLetter(){

    showPage("letter");

    const typing=document.getElementById("typing");
    const btn=document.getElementById("continueBtn");

    typing.innerHTML="";
    btn.style.display="none";

    let i=0;

    const speed=28;

    const timer=setInterval(()=>{

        typing.innerHTML+=letter.charAt(i);

        i++;

        if(i>=letter.length){

            clearInterval(timer);

            btn.style.display="inline-block";

        }

    },speed);

}

function showQuestion(){
    showPage("question");
}

// ===== Maybe Button =====

let clicks=0;

function maybeAnswer(){

    clicks++;

    const yes=document.getElementById("yesBtn");
    const maybe=document.getElementById("maybeBtn");

    // Yes grows
    yes.style.transform=`scale(${1+(clicks*0.18)})`;

    // Maybe shrinks
    maybe.style.transform=`scale(${1-(clicks*0.18)})`;

    // Maybe fades
    maybe.style.opacity=1-(clicks*0.25);

    // Cute messages
    const msgs=[
        "Hmm? 🤨",
        "Are you sure? 🌷",
        "Pretty please?",
        "I'll take that as a maybe. 💗"
    ];

    if(clicks<=msgs.length){
        maybe.innerText=msgs[clicks-1];
    }

    if(clicks>=4){

        maybe.style.transition=".5s";
        maybe.style.opacity="0";

        setTimeout(()=>{
            maybe.style.display="none";
        },500);

    }

}

// ===== Yes =====

function yesAnswer(){

    showPage("ending");

    confetti();

}

// ===== Tulip Confetti =====

function confetti(){

    for(let i=0;i<120;i++){

        const petal=document.createElement("div");

        petal.innerHTML=Math.random()>.5?"🌷":"🌸";

        petal.style.position="fixed";
        petal.style.left=Math.random()*100+"vw";
        petal.style.top="-30px";
        petal.style.fontSize=(18+Math.random()*18)+"px";
        petal.style.transition="4s linear";

        document.body.appendChild(petal);

        setTimeout(()=>{

            petal.style.transform=
            `translateY(${window.innerHeight+100}px)
            rotate(${Math.random()*720}deg)`;

        },50);

        setTimeout(()=>{

            petal.remove();

        },4000);

    }

}

// ===== Floating Background Tulips =====

function floatingPetal(){

    const petal=document.createElement("div");

    petal.className="petal";

    petal.innerHTML=Math.random()>.5?"🌷":"🌸";

    petal.style.left=Math.random()*100+"vw";

    petal.style.animationDuration=
    (8+Math.random()*5)+"s";

    petal.style.fontSize=
    (18+Math.random()*18)+"px";

    document.getElementById("petals")
    .appendChild(petal);

    setTimeout(()=>{
        petal.remove();
    },13000);

}

setInterval(floatingPetal,700);
