# index. html   
  
<!DOCTYPE html>  
<html lang="en">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width, initial-scale=1.0">  
  
<title>Ines' Birthday Dinner</title>  
  
<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">  
  
<style>  
*{  
    margin:0;  
    padding:0;  
    box-sizing:border-box;  
}  
  
body{  
    height:100vh;  
    overflow:hidden;  
    background:linear-gradient(135deg,#ff5fa2,#ff89c2,#ffc0db);  
    display:flex;  
    justify-content:center;  
    align-items:center;  
    position:relative;  
    font-family:'Poppins',sans-serif;  
}  
  
/* Floating Hearts */  
  
.hearts{  
    position:absolute;  
    width:100%;  
    height:100%;  
    overflow:hidden;  
    z-index:1;  
}  
  
.heart{  
    position:absolute;  
    color:rgba(255,255,255,0.35);  
    font-size:25px;  
    animation:floatUp linear infinite;  
}  
  
@keyframes floatUp{  
    from{  
        transform:translateY(100vh) scale(0.5);  
    }  
    to{  
        transform:translateY(-120px) scale(1.4);  
    }  
}  
  
/* Invitation Card */  
  
.card{  
    position:relative;  
    z-index:5;  
    background:rgba(255,255,255,0.12);  
    backdrop-filter:blur(12px);  
    border:2px solid rgba(255,255,255,0.25);  
    padding:50px;  
    border-radius:35px;  
    text-align:center;  
    color:white;  
    max-width:700px;  
    width:90%;  
    box-shadow:0 15px 50px rgba(0,0,0,0.15);  
    animation:appear 1.8s ease forwards;  
    opacity:0;  
}  
  
@keyframes appear{  
    from{  
        opacity:0;  
        transform:translateY(50px) scale(.9);  
    }  
    to{  
        opacity:1;  
        transform:translateY(0) scale(1);  
    }  
}  
  
.title{  
    font-family:'Great Vibes',cursive;  
    font-size:4rem;  
    margin-bottom:20px;  
    text-shadow:0 0 20px rgba(255,255,255,.7);  
}  
  
.subtitle{  
    font-size:1.3rem;  
    line-height:1.8;  
    font-weight:600;  
}  
  
/* Confetti */  
  
.confetti{  
    position:absolute;  
    width:12px;  
    height:12px;  
    top:-20px;  
    z-index:20;  
}  
  
@keyframes confettiFall{  
    to{  
        transform:  
        translate(var(--x), 110vh)  
        rotate(1080deg);  
        opacity:0;  
    }  
}  
  
/* Sparkles */  
  
.sparkle{  
    position:absolute;  
    color:white;  
    animation:twinkle 2s infinite;  
    opacity:.6;  
}  
  
@keyframes twinkle{  
    50%{  
        opacity:1;  
        transform:scale(1.5);  
    }  
}  
</style>  
</head>  
  
<body>  
  
<div class="hearts" id="hearts"></div>  
  
<div class="card">  
    <div class="title">  
        🎉 You've Been Invited to<br>  
        Ines' Birthday Dinner 🎉  
    </div>  
  
    <div class="subtitle">  
        📅 Date: 20th June<br><br>  
        📍 Venue: Dario Event Center  
    </div>  
</div>  
  
<script>  
  
/* Floating Hearts */  
  
const heartsContainer = document.getElementById("hearts");  
  
for(let i=0;i<35;i++){  
  
    let heart=document.createElement("div");  
    heart.className="heart";  
    heart.innerHTML="💖";  
  
    heart.style.left=Math.random()*100+"vw";  
    heart.style.fontSize=(15+Math.random()*30)+"px";  
    heart.style.animationDuration=(8+Math.random()*10)+"s";  
    heart.style.animationDelay=Math.random()*5+"s";  
  
    heartsContainer.appendChild(heart);  
}  
  
/* Sparkles */  
  
for(let i=0;i<25;i++){  
  
    let sparkle=document.createElement("div");  
  
    sparkle.className="sparkle";  
    sparkle.innerHTML="✨";  
  
    sparkle.style.left=Math.random()*100+"vw";  
    sparkle.style.top=Math.random()*100+"vh";  
    sparkle.style.fontSize=(10+Math.random()*20)+"px";  
    sparkle.style.animationDelay=Math.random()*2+"s";  
  
    document.body.appendChild(sparkle);  
}  
  
/* CONFETTI BURST */  
  
function launchConfetti(){  
  
const colors=[  
"#ffffff",  
"#ffd700",  
"#ff1493",  
"#ff69b4",  
"#87cefa",  
"#98fb98"  
];  
  
for(let i=0;i<250;i++){  
  
let confetti=document.createElement("div");  
confetti.className="confetti";  
  
confetti.style.background=  
colors[Math.floor(Math.random()*colors.length)];  
  
confetti.style.left="50vw";  
  
confetti.style.setProperty(  
"--x",  
(Math.random()*1000-500)+"px"  
);  
  
confetti.style.animation=  
`confettiFall ${3+Math.random()*3}s ease-out forwards`;  
  
document.body.appendChild(confetti);  
  
setTimeout(()=>{  
confetti.remove();  
},7000);  
}  
}  
  
window.onload=()=>{  
setTimeout(launchConfetti,300);  
};  
</script>  
  
</body>  
</html>  
