# valentine-nata
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Nata 💘</title>

<!-- Cute Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600&family=Pacifico&display=swap" rel="stylesheet">

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Fredoka',cursive;
}

body{
overflow:hidden;
background:linear-gradient(135deg,#ff9bb3,#ff6f91,#ffc3a0);
color:#fff;
}

.slide{
width:100vw;
height:100vh;
display:none;
flex-direction:column;
justify-content:center;
align-items:center;
text-align:center;
padding:20px;
animation:fade .6s ease;
}

.active{display:flex;}

@keyframes fade{
from{opacity:0;transform:scale(.95)}
to{opacity:1;transform:scale(1)}
}

h1{
font-family:'Pacifico',cursive;
margin-bottom:20px;
}

button{
border:none;
padding:15px 25px;
margin:10px;
border-radius:30px;
font-size:18px;
cursor:pointer;
background:#ff4f7b;
color:white;
box-shadow:0 6px 15px rgba(0,0,0,.2);
transition:.25s;
}

button:active{
transform:scale(.9);
}

.bigBtn{
font-size:22px;
padding:18px 30px;
background:linear-gradient(45deg,#ff4f7b,#ff9bb3);
}

/* popup */
.popup{
position:fixed;
top:50%;
left:50%;
transform:translate(-50%,-50%) scale(0);
background:linear-gradient(135deg,#ff7aa2,#ffb3c6);
padding:25px;
border-radius:20px;
text-align:center;
z-index:10;
width:85%;
max-width:320px;
transition:.4s;
}

.popup.show{
transform:translate(-50%,-50%) scale(1);
}

.overlay{
position:fixed;
inset:0;
background:rgba(0,0,0,.4);
display:none;
}

.overlay.show{display:block}

/* confetti hearts */
.heart{
position:absolute;
font-size:20px;
animation:fall 4s linear infinite;
}

@keyframes fall{
0%{transform:translateY(-10vh)}
100%{transform:translateY(110vh)}
}

input{
padding:12px;
border-radius:20px;
border:none;
width:80%;
margin-top:10px;
text-align:center;
}

.letter{
background:#ffe0ea;
color:#a3003c;
padding:20px;
border-radius:20px;
max-width:320px;
}

</style>
</head>

<body>

<div class="overlay" id="overlay"></div>

<!-- SLIDE 1 -->
<div class="slide active" id="s1">
<h1>Will you be my Valentine, Nata? 💘</h1>
<button class="bigBtn" onclick="yes()">YES</button>
<button id="noBtn" onclick="no()">NO</button>
</div>

<!-- SAD SLIDE -->
<div class="slide" id="sad">
<h1>bubi udah ga sayang aku 😠</h1>
<button onclick="show('s1')">back</button>
</div>

<!-- SLIDE 2 -->
<div class="slide" id="s2">
<div class="letter">
makasi ya bubu for being my valentine once again.<br><br>
i honestly feel so lucky to have u.<br>
you make my days softer, my heart warmer,
and my world brighter.<br><br>
i love you more than words could ever explain.
and i hope this little surprise makes u smile.<br><br>
i always choosing u, forever.<br>
— Chica
</div>
<br>
<button onclick="show('s3')">NEXT</button>
</div>

<!-- SLIDE 3 -->
<div class="slide" id="s3">
<h1>Pick Your Gift 🎀</h1>

<button class="bigBtn" onclick="gift1()">FIRST GIFT</button>
<button class="bigBtn" onclick="gift2()">SECOND GIFT</button>
<button class="bigBtn" onclick="gift3()">LAST GIFT</button>
</div>

<!-- SLIDE 4 -->
<div class="slide" id="s4">
<h1>YAYYY U DID IT BUBI ‼️</h1>
<p>
i’m so proud of you, i hope this little games makes your day,
giving u some butterfly and don’t forget you have me
on this valentine (hihihi) 💖
</p>
<br>
<button onclick="show('s5')">NEXT</button>
</div>

<!-- FINAL -->
<div class="slide" id="s5">
<h1>Can I hug u now? 🫂💗</h1>
</div>

<!-- POPUP -->
<div class="popup" id="popup"></div>

<script>

let noCount=0;

function show(id){
document.querySelectorAll('.slide').forEach(s=>s.classList.remove('active'));
document.getElementById(id).classList.add('active');
}

function yes(){
confetti();
show('s2');
}

function no(){
let btn=document.getElementById("noBtn");
btn.style.position="absolute";
btn.style.left=Math.random()*70+"%";
btn.style.top=Math.random()*70+"%";
noCount++;
if(noCount>=3){
show('sad');
}
}

function popup(text){
document.getElementById("popup").innerHTML=text;
document.getElementById("popup").classList.add("show");
document.getElementById("overlay").classList.add("show");

document.getElementById("overlay").onclick=closePopup;
}

function closePopup(){
document.getElementById("popup").classList.remove("show");
document.getElementById("overlay").classList.remove("show");
}

function gift1(){
popup("FREE CHOCOLATE 🍫<br><br>Screenshot for redeem");
}

function gift2(){
popup("FREE HUG AND KISSES UNLIMITED 🥰<br>(nanti pas ketemu yaa sayang)");
}

function gift3(){
popup(`
ketik passwordnya yaa<br>
<small>clue : lagu fav ku yang ngingetin aku tentang kita awal awal kenal hihi</small>
<br><input id="pw" placeholder="type here">
<br><br>
<button onclick="check()">submit</button>
`);
}

function check(){
let v=document.getElementById("pw").value.toLowerCase();
if(v.includes("die") && v.includes("smile")){
closePopup();
confetti();
show('s4');
}else{
alert("hmm masih salah 😝");
}
}

function confetti(){
for(let i=0;i<20;i++){
let h=document.createElement("div");
h.className="heart";
h.innerHTML="💖";
h.style.left=Math.random()*100+"vw";
h.style.animationDuration=(3+Math.random()*3)+"s";
document.body.appendChild(h);
setTimeout(()=>h.remove(),4000);
}
}

</script>

</body>
</html>