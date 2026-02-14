<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Juansi Díaz</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

body{
  font-family: 'Courier New', monospace;
  color:#00ff99;
  overflow:hidden;
  text-align:center;
  background:black;
}

/* Video Fondo */
video{
  position:fixed;
  right:0;
  bottom:0;
  min-width:100%;
  min-height:100%;
  object-fit:cover;
  z-index:-2;
  filter:brightness(30%);
}

/* Matrix Canvas */
canvas{
  position:fixed;
  top:0;
  left:0;
  z-index:-1;
}

/* Contenido */
.container{
  position:relative;
  top:50%;
  transform:translateY(-50%);
}

h1{
  font-size:55px;
  letter-spacing:5px;
  margin-bottom:20px;
}

.typewriter{
  font-size:22px;
  margin-bottom:30px;
  height:30px;
}

.tech{
  font-size:20px;
  line-height:35px;
  margin-bottom:25px;
}

.contact{
  font-size:18px;
  opacity:0.8;
}
</style>
</head>

<body>

<!-- VIDEO FONDO -->
<video autoplay muted loop>
  <source src="anime.mp4" type="video/mp4">
</video>

<!-- MATRIX EFECTO -->
<canvas id="matrix"></canvas>

<div class="container">
  <h1>JUANSI DÍAZ</h1>

  <div class="typewriter" id="typing"></div>

  <div class="tech">
    Python 🐍<br>
    Kali Linux 💻<br>
    Visual Studio Code<br>
    GitHub
  </div>

  <div class="contact">
    Instagram: @iam.juansi<br>
    juansicastillo7@gmail.com
  </div>
</div>

<!-- AUDIO TECLADO -->
<audio id="sound" src="https://www.soundjay.com/mechanical/sounds/keyboard-1.mp3"></audio>

<script>
// EFECTO MATRIX
const canvas = document.getElementById("matrix");
const ctx = canvas.getContext("2d");

canvas.height = window.innerHeight;
canvas.width = window.innerWidth;

let letters = "01";
letters = letters.split("");

let fontSize = 14;
let columns = canvas.width/fontSize;
let drops = [];

for(let x=0; x<columns; x++)
  drops[x]=1;

function draw(){
  ctx.fillStyle="rgba(0,0,0,0.05)";
  ctx.fillRect(0,0,canvas.width,canvas.height);

  ctx.fillStyle="#00ff99";
  ctx.font=fontSize+"px monospace";

  for(let i=0; i<drops.length; i++){
    let text = letters[Math.floor(Math.random()*letters.length)];
    ctx.fillText(text,i*fontSize,drops[i]*fontSize);

    if(drops[i]*fontSize > canvas.height && Math.random()>0.975)
      drops[i]=0;

    drops[i]++;
  }
}

setInterval(draw,33);

// EFECTO MAQUINA DE ESCRIBIR
const text = "Ciberseguridad & Ethical Hacking";
let i = 0;
function typing(){
  if(i < text.length){
    document.getElementById("typing").innerHTML += text.charAt(i);
    document.getElementById("sound").play();
    i++;
    setTimeout(typing, 70);
  }
}
typing();
</script>

</body>
</html>
