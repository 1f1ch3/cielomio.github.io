# <!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mira cielo te llego una Carta ♥</title>
<style>
/* ——— TODO TU CÓDIGO ORIGINAL SIN CAMBIOS ——— */
@import url('https://fonts.googleapis.com/css2?family=Permanent+Marker&family=Patrick+Hand&display=swap');
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Patrick Hand',cursive;background:#ffe0f0;min-height:100vh;display:flex;justify-content:center;align-items:center;overflow-x:hidden;overflow-y:auto;position:relative;padding:20px 0;}
.fondo-corazones{position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:0;}
.corazon-flotante{position:absolute;font-size:20px;animation:flotarSubir 8s linear infinite;opacity:0;}
@keyframes flotarSubir{0%{opacity:0;transform:translateY(100vh) rotate(0deg);}10%{opacity:.7;}90%{opacity:.7;}100%{opacity:0;transform:translateY(-100px) rotate(360deg);}}
.container{position:relative;z-index:1;width:100%;max-width:700px;padding:20px;}
.titulo{font-family:'Permanent Marker',cursive;text-align:center;font-size:clamp(2em,5vw,3.5em);color:#2c2c2c;margin-bottom:10px;transform:rotate(-2deg);text-shadow:4px 4px 0px #ff69b4;animation:tituloWiggle 3s ease-in-out infinite;}
@keyframes tituloWiggle{0%,100%{transform:rotate(-2deg);}50%{transform:rotate(2deg);}}
.corazones-titulo{position:absolute;font-size:clamp(1.5em,4vw,2.5em);animation:latido 1.5s ease-in-out infinite;}
.ct1{top:5%;left:5%;color:#ff1744;animation-delay:0s;}
.ct2{top:8%;right:8%;color:#ff4081;animation-delay:.3s;}
.ct3{top:15%;left:12%;color:#ff6090;animation-delay:.6s;}
.ct4{top:12%;right:15%;color:#ff1744;animation-delay:.9s;}
.ct5{top:20%;left:18%;color:#ff4081;animation-delay:1.2s;}
.ct6{top:18%;right:20%;color:#ff6090;animation-delay:1.5s;}
@media(max-width:768px){.ct3,.ct5{display:none;}}
@keyframes latido{0%,100%{transform:scale(1);}25%{transform:scale(1.3);}50%{transform:scale(1);}}
.sobre-escena{position:relative;width:100%;max-width:450px;height:350px;margin:40px auto;perspective:1000px;}
.sobre-container{position:absolute;width:100%;height:100%;cursor:pointer;transition:transform .3s ease;transform-style:preserve-3d;}
.sobre-container:hover:not(.abierto){transform:translateY(-10px);filter:brightness(1.1);}
.sombra{position:absolute;bottom:-20px;left:50%;transform:translateX(-50%);width:90%;height:20px;background:radial-gradient(ellipse,rgba(0,0,0,.3),transparent);transition:all .3s ease;}
.sobre-container:hover:not(.abierto) .sombra{width:80%;opacity:.5;}
.sobre-cuerpo{position:absolute;bottom:0;left:50%;transform:translateX(-50%);width:min(380px,90vw);height:min(240px,35vh);background:linear-gradient(135deg,#ffb3d9 0%,#ff91c7 50%,#ffb3d9 100%);border:5px solid #2c2c2c;border-radius:15px;box-shadow:8px 8px 0px rgba(0,0,0,.3);z-index:2;}
.sobre-cuerpo::before{content:'';position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:90%;height:2px;background:repeating-linear-gradient(90deg,#ff1744 0px,#ff1744 10px,transparent 10px,transparent 20px);}
.solapa-trasera{position:absolute;bottom:0;left:50%;transform:translateX(-50%);width:min(380px,90vw);height:min(130px,18vh);background:linear-gradient(135deg,#ffc9e3 0%,#ffb3d9 100%);border:5px solid #2c2c2c;border-top:none;clip-path:polygon(0 100%,50% 0,100% 100%);z-index:1;}
.solapa-frontal{position:absolute;top:46%;left:50%;transform:translateX(-50%);transform-origin:top center;width:min(380px,90vw);height:min(200px,28vh);background:linear-gradient(180deg,#ff91c7 0%,#ff91c7 100%);border:5px solid #2c2c2c;border-bottom:none;clip-path:polygon(0 0,50% 100%,100% 0);z-index:3;transition:transform 1s cubic-bezier(0.68,-0.55,0.265,1.55),z-index 0s linear .5;}
.sobre-container.abierto .solapa-frontal{transform:translateX(-50%) rotateX(-180deg);z-index:1;}
.corazon-sello{position:absolute;top:70%;left:48%;transform:translateX(-50%) rotate(0deg);width:60px;height:60px;z-index:4;transition:all 1s ease;filter:drop-shadow(3px 3px 0px rgba(0,0,0,.3));}
.corazon-sello::before{content:'❤️';position:absolute;font-size:60px;animation:corazonPulso 1.5s ease-in-out infinite;}
@keyframes corazonPulso{0%,100%{transform:scale(1);}50%{transform:scale(1.15);}}
.sobre-container.abierto .corazon-sello{transform:translateX(-50%) translateY(-150px) rotate(360deg) scale(0);opacity:0;}
.carta{position:absolute;bottom:50px;left:50%;transform:translateX(-50%);width:min(340px,85vw);height:0;background:#fff;border:5px solid #2c2c2c;border-radius:10px;padding:0;box-shadow:6px 6px 0px rgba(0,0,0,.3);overflow:hidden;transition:all 1.2s cubic-bezier(0.68,-0.55,0.265,1.55);z-index:2;}
.sobre-container.abierto .carta{height:min(500px,60vh);bottom:50%;transform:translate(-50%,50%);padding:35px 30px;}
.carta::before{content:'';position:absolute;top:0;left:0;right:0;height:20px;background:repeating-linear-gradient(45deg,#ff69b4,#ff69b4 10px,#ff1744 10px,#ff1744 20px);}
.carta-contenido{opacity:0;transition:opacity .8s ease 1s;line-height:2;color:#2c2c2c;font-size:clamp(1.2em,3vw,1.5em);height:100%;overflow-y:auto;}
.sobre-container.abierto .carta-contenido{opacity:1;}
.carta h2{font-family:'Permanent Marker',cursive;color:#ff1744;margin-bottom:20px;font-size:clamp(1.8em,4vw,2.2em);text-align:center;transform:rotate(-1deg);}
.carta p{margin-bottom:18px;}
.firma{text-align:right;margin-top:30px;font-size:1.4em;color:#ff1744;font-family:'Permanent Marker',cursive;transform:rotate(-2deg);}
.brillo{position:absolute;width:30px;height:30px;animation:brillar 2s ease-in-out infinite;}
.brillo::before,.brillo::after{content:'✨';position:absolute;font-size:20px;}
.brillo1{top:10%;left:15%;animation-delay:0s;}
.brillo2{top:15%;right:10%;animation-delay:.5s;}
.brillo3{bottom:20%;left:10%;animation-delay:1s;}
.brillo4{bottom:15%;right:15%;animation-delay:1.5s;}
@keyframes brillar{0%,100%{opacity:.3;transform:scale(1) rotate(0deg);}50%{opacity:1;transform:scale(1.5) rotate(180deg);}}
.instruccion{text-align:center;margin-top:20px;font-size:clamp(1.3em,3vw,1.8em);color:#ff1744;font-family:'Permanent Marker',cursive;animation:rebote 1s ease-in-out infinite;}
@keyframes rebote{0%,100%{transform:translateY(0);}50%{transform:translateY(-10px);}}
.sobre-container.abierto~.instruccion{display:none;}
.confeti{position:fixed;width:10px;height:10px;background:#ff69b4;opacity:0;z-index:999;}
.confeti.activo{animation:caerConfeti 3s ease-out forwards;}
@keyframes caerConfeti{0%{opacity:1;transform:translateY(-100px) rotate(0deg);}100%{opacity:0;transform:translateY(100vh) rotate(720deg);}}
.boton-cerrar{position:fixed;bottom:20px;left:50%;transform:translateX(-50%);padding:12px 30px;background:#ff1744;color:white;border:4px solid #2c2c2c;border-radius:50px;font-family:'Permanent Marker',cursive;font-size:clamp(1.1em,2.5vw,1.3em);cursor:pointer;box-shadow:5px 5px 0px rgba(0,0,0,.3);opacity:0;pointer-events:none;transition:all .3s ease;z-index:1000;}
.boton-cerrar:hover{transform:translateX(-50%) scale(1.1);background:#ff4081;}
.sobre-container.abierto~.boton-cerrar{opacity:1;pointer-events:all;transition-delay:1.5s;}
</style>
</head>
<body>
<div class="fondo-corazones" id="fondoCorazones"></div>
<div class="container">
<div class="corazones-titulo ct1">♥</div><div class="corazones-titulo ct2">♥</div><div class="corazones-titulo ct3">♥</div><div class="corazones-titulo ct4">♥</div><div class="corazones-titulo ct5">♥</div><div class="corazones-titulo ct6">♥</div>
<h1 class="titulo">Mira cielito te llegó una Carta ♥</h1>
<div class="sobre-escena">
<div class="brillo brillo1"></div><div class="brillo brillo2"></div><div class="brillo brillo3"></div><div class="brillo brillo4"></div>
<div class="sobre-container" id="sobre">
<div class="sombra"></div><div class="solapa-trasera"></div><div class="sobre-cuerpo"></div>
<div class="carta"><div class="carta-contenido"><h2>Para ti ♥</h2><p>Holi amorcito</p><p>Esta carta es para recordarte lo increíblemente especial que eres para mi magnificamente divina mega duper hiper irrealista para miiiiii</p><p>Eres la niña mas linda, hermosaaa, divina, apesar que ya casi no hablamos o no quieras hablar conmigo o incluso ya no quieras estar conmigo, nada ni nadie me hara o me obligara a dejar de sentir lo que siento por ti amorcito</p><p>Se que a lo mejor no estamos en buen momento o peleamos mucho pero quiero que sepas que te amo demasiado amorcito, eres miprincesa y miniñachiquitaaaaa, el amor de todas mis vidas, la mama de mis futuros hijos, y mi futura esposaaaa</p><p class="firma">De tu noviecito<br>Tiamo</p></div></div>
<div class="solapa-frontal"></div><div class="corazon-sello"></div>
</div>
</div>
<button class="boton-cerrar" id="btnCerrar">Cerrar Carta</button>
<p class="instruccion">Dale clic en el sobre</p>

<!-- 💖 NUEVO BOTÓN AÑADIDO PARA iPhone -->
<div style="text-align:center;margin-top:20px;">
  <button id="btnAbrirExtra" style="padding:12px 30px;background:#ff4081;color:white;border:4px solid #2c2c2c;border-radius:50px;font-family:'Permanent Marker',cursive;font-size:1.2em;cursor:pointer;box-shadow:5px 5px 0 rgba(0,0,0,0.3);">
    Abrir Carta 💌
  </button>
</div>

</div>

<script>
const sobre=document.getElementById('sobre');
const btnCerrar=document.getElementById('btnCerrar');
const fondoCorazones=document.getElementById('fondoCorazones');

// Corazones flotantes
function crearCorazonFondo(){
const corazon=document.createElement('div');
corazon.className='corazon-flotante';
corazon.textContent='♥';
corazon.style.left=Math.random()*100+'%';
corazon.style.fontSize=(Math.random()*20+15)+'px';
corazon.style.color=['#ff1744','#ff4081','#ff69b4'][Math.floor(Math.random()*3)];
corazon.style.animationDuration=(Math.random()*5+5)+'s';
corazon.style.animationDelay=Math.random()*3+'s';
fondoCorazones.appendChild(corazon);
setTimeout(()=>{corazon.remove();},8000);}
setInterval(crearCorazonFondo,500);

// Confeti
function crearConfeti(){
const colores=['#ff1744','#ff4081','#ff69b4','#ffb3d9','#ffd700','#00bcd4'];
for(let i=0;i<50;i++){
setTimeout(()=>{
const confeti=document.createElement('div');
confeti.className='confeti activo';
confeti.style.left=Math.random()*100+'%';
confeti.style.background=colores[Math.floor(Math.random()*colores.length)];
confeti.style.width=(Math.random()*8+5)+'px';
confeti.style.height=(Math.random()*8+5)+'px';
confeti.style.animationDelay=Math.random()*0.5+'s';
document.body.appendChild(confeti);
setTimeout(()=>{confeti.remove();},3000);
},i*30);
}}
sobre.addEventListener('click',function(){if(!this.classList.contains('abierto')){this.classList.add('abierto');crearConfeti();if(navigator.vibrate){navigator.vibrate([50,100,50]);}}});
btnCerrar.addEventListener('click',function(e){e.stopPropagation();sobre.classList.remove('abierto');});

// 💡 BOTÓN EXTRA COMPATIBLE CON IPHONE
const btnAbrirExtra=document.getElementById('btnAbrirExtra');
btnAbrirExtra.addEventListener('click',abrirCarta);
btnAbrirExtra.addEventListener('touchstart',abrirCarta);
function abrirCarta(e){
  e.preventDefault();
  if(!sobre.classList.contains('abierto')){
    sobre.classList.add('abierto');
    crearConfeti();
  }
}
</script>
</body>
</html>
