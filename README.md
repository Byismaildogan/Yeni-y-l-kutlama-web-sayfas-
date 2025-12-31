<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>Mutlu Yıllar 2026 🎆</title>
<!-- ...Bu projede sadece arkadaşlarımla otururken eğlence amacı güdülmüştür.Kodlamalar ai,
 düzenlemeler tarafımdan yapılmıştır... -->

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    height:100vh;
    background: radial-gradient(circle at top, #1b1b4b, #000);
    overflow:hidden;
    font-family:'Segoe UI', sans-serif;
    color:white;
    display:flex;
    justify-content:center;
    align-items:center;
}

/* ORTA ALAN */
.center{
    position:relative;
    display:flex;
    flex-direction:column;
    align-items:center;
    gap:30px; /* 👈 GERİ SAYIM & YIL ARASI MESAFE */
    z-index:5;
}

/* Geri sayım */
.countdown{
    font-size:clamp(60px, 10vw, 120px);
    font-weight:bold;
    height:1em;
}

/* Yıl */
.year{
    display:flex;
    font-size:clamp(80px, 12vw, 140px);
    font-weight:800;
    opacity:0;
    transition:opacity 1s ease;
    text-shadow:0 0 25px rgba(255,255,255,.8);
}

.digit{
    width:0.8em;
    text-align:center;
    position:relative;
}

.five{
    animation: up 2s forwards;
    animation-delay:7s;
}

.six{
    position:absolute;
    bottom:-150%;
    opacity:0;
    animation: in 2s forwards;
    animation-delay:8.2s;
}

@keyframes up{
    to{
        transform:translateY(-200%);
        opacity:0;
    }
}

@keyframes in{
    to{
        transform:translateY(-150%);
        opacity:1;
    }
}

/* Alt yazı */
.text{
    position:absolute;
    bottom:12%;
    font-size:clamp(18px, 4vw, 32px);
    opacity:0;
    animation:fade 2s forwards;
    animation-delay:9.5s;
    letter-spacing:2px;
}

@keyframes fade{
    to{opacity:1}
}

/* Konfeti */
.confetti{
    position:absolute;
    width:8px;
    height:14px;
    animation:fall linear infinite;
}

@keyframes fall{
    to{
        transform:translateY(110vh) rotate(720deg);
    }
}

/* Havai fişek */
.firework{
    position:absolute;
    width:6px;
    height:6px;
    border-radius:50%;
    animation:explode 1.5s ease-out forwards;
}

@keyframes explode{
    from{transform:scale(0);opacity:1}
    to{transform:scale(8);opacity:0}
}
</style>
</head>

<body>

<div class="center">
    <div class="countdown" id="count">10</div>

    <div class="year" id="year">
        <div class="digit">2</div>
        <div class="digit">0</div>
        <div class="digit">2</div>
        <div class="digit">
            <span class="five">5</span>
            <span class="six">6</span>
        </div>
    </div>
</div>

<div class="text">🎆 Mutlu Yıllar — 2026 🎆</div>

<audio id="boom" src="https://cdn.pixabay.com/audio/2022/03/15/audio_5c06c84e8a.mp3"></audio>

<script>
/* Geri sayım */
let count = 10;
const countEl = document.getElementById("count");
const yearEl = document.getElementById("year");

const timer = setInterval(()=>{
    countEl.textContent = count;
    count--;
    if(count < 0){
        clearInterval(timer);
        countEl.textContent = "";
        yearEl.style.opacity = 1;
    }
},600);

/* Konfeti */
const colors = ["#ff4d4d","#ffd93d","#4dff4d","#4dd2ff","#ff4dff"];
for(let i=0;i<160;i++){
    const c=document.createElement("div");
    c.className="confetti";
    c.style.left=Math.random()*100+"vw";
    c.style.background=colors[Math.floor(Math.random()*colors.length)];
    c.style.animationDuration=Math.random()*3+3+"s";
    document.body.appendChild(c);
}

/* Havai fişek */
function firework(){
    const f=document.createElement("div");
    f.className="firework";
    f.style.left=Math.random()*100+"vw";
    f.style.top=Math.random()*60+"vh";
    f.style.background=colors[Math.floor(Math.random()*colors.length)];
    document.body.appendChild(f);
    setTimeout(()=>f.remove(),1500);
}

setTimeout(()=>{
    document.getElementById("boom").play();
    setInterval(firework,300);
},8500);
</script>

</body>
</html>
