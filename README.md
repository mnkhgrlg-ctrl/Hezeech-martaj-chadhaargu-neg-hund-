# Hezeech-martaj-chadhaargu-neg-hund
<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<title>For You ❤️</title>
<style>
*{box-sizing:border-box;}
body{
  margin:0;
  height:100vh;
  overflow:hidden;
  font-family:-apple-system,BlinkMacSystemFont,sans-serif;
  background:radial-gradient(circle at top,#1a0033,#000);
  color:white;
}

/* ===== STARS ===== */
.star{
  position:fixed;
  width:2px;
  height:2px;
  background:white;
  border-radius:50%;
  animation:twinkle linear infinite;
}
@keyframes twinkle{50%{opacity:.2}}

/* ===== CENTER ===== */
.center{
  position:absolute;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  text-align:center;
}

/* ===== LOCK ===== */
#lock{
  display:flex;
  flex-direction:column;
  gap:14px;
  align-items:center;
  animation:fadeIn 1.5s;
}
.hint{font-size:14px;color:#ff9ecf;opacity:.9;}
#lock input{
  padding:12px;font-size:20px;border:none;border-radius:10px;outline:none;
  text-align:center;background:#00000080;color:white;letter-spacing:3px;width:180px;
}
#lock button{
  padding:10px 26px;border:none;border-radius:12px;font-size:16px;
  cursor:pointer;background:linear-gradient(45deg,#ff0055,#ff5cab);
  color:white;box-shadow:0 0 20px #ff3b7f;transition:.3s;
}
#lock button:hover{transform:scale(1.05);}

/* ===== GIFT BOX ===== */
#gift{
  display:none;
  width:260px;height:170px;
  background:#c8002d;
  border-radius:16px;
  position:relative;
  cursor:pointer;
  box-shadow:0 25px 70px rgba(255,0,80,.7);
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
}
#lid{
  width:280px;height:55px;
  background:#ff0033;
  position:absolute;
  top:-55px;
  left:-10px;
  border-radius:12px;
  transition:1s cubic-bezier(.19,1,.22,1);
}
#giftText{
  color:#ffd1ea;
  font-size:28px;
  font-weight:900;
  text-shadow:0 0 20px hotpink;
}

/* ===== MAIN MESSAGE ===== */
#mainMsg{
  display:none;
  font-size:42px;
  font-weight:900;
  color:#ffd1ea;
  text-shadow:0 0 40px hotpink;
  margin-bottom:20px;
}

/* ===== LOVE WORDS ===== */
#loveBox{
  display:none;
  height:55vh;width:85vw;
  max-width:650px;
  overflow:hidden;
  font-size:22px;font-weight:700;
  color:#ffd1ea;text-shadow:0 0 20px pink;
}
.scroll{
  animation:scrollUp 28s linear infinite;
}
@keyframes scrollUp{
  from{transform:translateY(100%)}
  to{transform:translateY(-100%)}
}

/* ===== EFFECTS ===== */
@keyframes fadeIn{from{opacity:0;transform:translateY(20px)} to{opacity:1}}
@keyframes zoom{from{opacity:0;transform:scale(.4)} to{opacity:1;transform:scale(1)}}
.boom{
  position:fixed;font-size:28px;pointer-events:none;
  animation:blast 3s ease-out forwards;
}
@keyframes blast{
  to{transform:translate(calc(-300px + 600px * var(--x)), calc(-300px + 600px * var(--y))) scale(.2); opacity:0;}
}

/* ===== MOBILE ===== */
@media(max-width:600px){
  #mainMsg{font-size:30px}
  #loveBox{font-size:18px}
  #gift{width:210px;height:150px}
  #giftText{font-size:22px}
}
</style>
</head>
<body>
<div class="center">

<!-- PASSWORD -->
<div id="lock" class="glass">
  <div style="font-size:22px">🔐 Нууц үг оруул</div>
  <div class="hint">Hint: Tiim ❤️</div>
  <input id="code" placeholder="Энд бич">
  <button onclick="unlock()">Нээх 💖</button>
</div>

<!-- GIFT -->
<div id="gift">
  <div id="lid"></div>
  <div id="giftText">💗 Надтай үерхээч 💗</div>
</div>

<!-- MAIN LOVE MESSAGE -->
<div id="mainMsg">💖 Би чамд хайртай! 💖</div>

<!-- LOVE WORDS -->
<div id="loveBox">
  <div class="scroll" id="loveText"></div>
</div>

</div>

<script>
/* ===== STARS ===== */
for(let i=0;i<150;i++){
  let s=document.createElement("div");
  s.className="star";
  s.style.left=Math.random()*100+"vw";
  s.style.top=Math.random()*100+"vh";
  s.style.animationDuration=2+Math.random()*4+"s";
  document.body.appendChild(s);
}

/* ===== PASSWORD ===== */
function unlock(){
  if(code.value==="Tiim"){
    lock.style.display="none";
    gift.style.display="flex";
  } else {
    navigator.vibrate?.(200);
    alert("💔 Буруу нууц үг");
  }
}

/* ===== GIFT CLICK ===== */
let opened=false;
gift.onclick = ()=>{
  if(opened) return;
  opened=true;
  lid.style.transform = "rotateX(160deg) translateY(-110px)";
  setTimeout(()=>{ gift.style.display="none"; },1000);

  // FIREWORK
  for(let i=0;i<90;i++){ explode("❤️"); explode("✨"); }

  // SHOW MAIN MESSAGE
  setTimeout(()=>{ mainMsg.style.display="block"; },600);

  // SHOW LOVE WORDS
  setTimeout(()=>{ 
    loveBox.style.display="block"; 
  },2000);
}

/* ===== FIREWORK ===== */
function explode(t){
  const e=document.createElement("div");
  e.className="boom";
  e.innerHTML=t;
  e.style.left=innerWidth/2+"px";
  e.style.top=innerHeight/2+"px";
  e.style.setProperty("--x",Math.random());
  e.style.setProperty("--y",Math.random());
  document.body.appendChild(e);
  setTimeout(()=>e.remove(),3000);
}

/* ===== LOVE WORDS ===== */
const words=[
  "I love you ❤️","Je t'aime 💖","Te amo 💕","Ich liebe dich 💘",
  "Te quiero 😘","愛してる 💞","사랑해 💗","Я тебя люблю 💝",
  "Ik hou van jou 💖","Eu te amo 💕"
];
let textHTML="";
for(let i=0;i<50;i++){
  textHTML+=words[Math.floor(Math.random()*words.length)]+"<br><br>";
}
loveText.innerHTML=textHTML;
</script>
</body>
</html>
