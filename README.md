<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>

<title>Between Last Year And This Afternoon</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;500;600;700&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">

<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>

<style>

*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

html,body{
  width:100%;
  height:100%;
  overflow:hidden;
  background:#75c6ff;
  font-family:'Inter',sans-serif;
}

/* =========================
MAIN SCENE
========================= */

.scene{
  position:relative;
  width:100vw;
  height:100vh;
  overflow:hidden;

  background:
  radial-gradient(circle at top,
  #a6e3ff 0%,
  #74c4ff 45%,
  #4da5e5 100%);
}

/* =========================
ATMOSPHERIC LIGHT
========================= */

.sun-glow{
  position:absolute;
  width:800px;
  height:800px;
  border-radius:50%;

  background:
  radial-gradient(circle,
  rgba(255,255,255,0.35),
  rgba(255,255,255,0));

  top:-250px;
  right:-100px;

  filter:blur(50px);

  z-index:1;
}

.vignette{
  position:absolute;
  inset:0;

  background:
  radial-gradient(circle at center,
  transparent 55%,
  rgba(0,0,0,0.22));

  z-index:999;
  pointer-events:none;
}

.grain{
  position:absolute;
  inset:0;

  background-image:
  url("https://www.transparenttextures.com/patterns/noise.png");

  opacity:0.08;
  mix-blend-mode:overlay;

  z-index:998;
  pointer-events:none;
}

/* =========================
TITLE
========================= */

.title-wrap{
  position:absolute;

  top:7vh;
  left:6vw;

  z-index:100;
}

.hero-title{
  font-family:'Cormorant Garamond',serif;
  font-size:7vw;
  line-height:0.83;
  font-weight:600;

  color:#fff8ef;

  letter-spacing:-3px;

  text-shadow:
  0 10px 30px rgba(0,0,0,0.15);
}

.subtitle{
  margin-top:20px;

  font-size:13px;
  letter-spacing:4px;

  color:white;
  opacity:0.75;
}

/* =========================
PARALLAX SYSTEM
========================= */

.parallax{
  position:absolute;
  will-change:transform;
}

/* =========================
CLOUDS
========================= */

.cloud{
  position:absolute;
  background:white;
  border-radius:999px;
  opacity:0.9;
  filter:blur(1px);
}

.cloud::before,
.cloud::after{
  content:'';
  position:absolute;
  background:white;
  border-radius:50%;
}

.cloud1{
  width:180px;
  height:60px;
  top:90px;
  left:80px;
}

.cloud1::before{
  width:80px;
  height:80px;
  top:-35px;
  left:15px;
}

.cloud1::after{
  width:100px;
  height:100px;
  top:-50px;
  right:20px;
}

.cloud2{
  width:160px;
  height:55px;
  top:150px;
  right:140px;
}

.cloud2::before{
  width:70px;
  height:70px;
  top:-25px;
  left:20px;
}

.cloud2::after{
  width:90px;
  height:90px;
  top:-40px;
  right:15px;
}

/* =========================
FLOATING NOTES
========================= */

.note{
  position:absolute;

  font-size:40px;

  opacity:0.8;

  animation:floatNote 5s ease-in-out infinite;
}

.note1{
  top:30%;
  left:22%;
}

.note2{
  top:32%;
  right:18%;
  animation-delay:1s;
}

.note3{
  top:42%;
  right:38%;
  animation-delay:2s;
}

@keyframes floatNote{

  0%,100%{
    transform:translateY(0px) rotate(0deg);
  }

  50%{
    transform:translateY(-20px) rotate(10deg);
  }

}

/* =========================
MAIN IMAGE
========================= */

.scene-image{
  position:absolute;

  bottom:-2vh;
  left:50%;

  width:78vw;
  max-width:1300px;

  transform:
  translateX(-50%);

  z-index:20;
}

.scene-image img{

  width:100%;

  display:block;

  object-fit:contain;

  pointer-events:none;
  user-select:none;

  filter:
  drop-shadow(0 40px 50px rgba(0,0,0,0.28));

  animation:
  sceneFloat 6s ease-in-out infinite;
}

@keyframes sceneFloat{

  0%,100%{
    transform:
    translateY(0px);
  }

  50%{
    transform:
    translateY(-8px);
  }

}

/* =========================
FOREGROUND ATMOSPHERE
========================= */

.foreground{
  position:absolute;

  bottom:-100px;
  left:-10%;

  width:120%;
  height:260px;

  background:
  radial-gradient(circle at center,
  rgba(117,203,97,0.85),
  rgba(71,143,57,0.95));

  filter:blur(40px);

  z-index:15;
}

/* =========================
BUTTONS
========================= */

.ui{
  position:absolute;

  bottom:40px;
  left:50%;

  transform:
  translateX(-50%);

  display:flex;
  gap:18px;

  z-index:200;
}

.btn{
  text-decoration:none;

  color:white;

  padding:14px 24px;

  border-radius:999px;

  background:
  rgba(255,255,255,0.12);

  border:
  1px solid rgba(255,255,255,0.18);

  backdrop-filter:blur(14px);

  font-size:13px;

  letter-spacing:2px;

  transition:0.3s ease;
}

.btn:hover{

  transform:
  translateY(-4px)
  scale(1.03);

  background:
  rgba(255,255,255,0.18);

}

/* =========================
PARTICLES
========================= */

.particle{
  position:absolute;

  width:4px;
  height:4px;

  border-radius:50%;

  background:white;

  opacity:0.4;

  animation:
  particleFloat linear infinite;
}

@keyframes particleFloat{

  from{
    transform:translateY(100vh);
  }

  to{
    transform:translateY(-120vh);
  }

}

/* =========================
RESPONSIVE
========================= */

@media(max-width:900px){

  .hero-title{
    font-size:14vw;
  }

  .scene-image{
    width:130vw;
    bottom:5vh;
  }

  .ui{
    flex-direction:column;
  }

}

</style>
</head>

<body>

<div class="scene" id="scene">

  <div class="sun-glow"></div>

  <!-- CLOUDS -->

  <div class="cloud cloud1 parallax" data-speed="0.02"></div>
  <div class="cloud cloud2 parallax" data-speed="0.03"></div>

  <!-- TITLE -->

  <div class="title-wrap parallax" data-speed="0.01">

    <h1 class="hero-title">
      between<br>
      last year<br>
      and this afternoon
    </h1>

    <div class="subtitle">
      2025 — 2026 ✦ a music diary
    </div>

  </div>

  <!-- NOTES -->

  <div class="note note1 parallax" data-speed="0.05">♫</div>
  <div class="note note2 parallax" data-speed="0.07">♪</div>
  <div class="note note3 parallax" data-speed="0.06">♩</div>

  <!-- MAIN IMAGE -->

  <div class="scene-image parallax" data-speed="0.09">

    <!-- IMPORTANT:
    Rename your image EXACTLY to:
    scene.png
    -->

    <img src="./scene.png" alt="scene">

  </div>

  <!-- FOREGROUND -->

  <div class="foreground"></div>

  <!-- BUTTONS -->

  <div class="ui">

    <a href="#" class="btn">
      SPOTIFY
    </a>

    <a href="#" class="btn">
      INSTAGRAM
    </a>

    <a href="#" class="btn">
      AMBIENT MODE
    </a>

  </div>

  <!-- GRAIN -->

  <div class="grain"></div>

  <!-- VIGNETTE -->

  <div class="vignette"></div>

</div>

<script>

/* =========================
PARALLAX
========================= */

const scene =
document.getElementById('scene');

const layers =
document.querySelectorAll('.parallax');

window.addEventListener('mousemove',(e)=>{

  const x =
  (window.innerWidth / 2 - e.clientX) / 40;

  const y =
  (window.innerHeight / 2 - e.clientY) / 40;

  layers.forEach(layer=>{

    const speed =
    layer.getAttribute('data-speed');

    const moveX =
    x * speed * 100;

    const moveY =
    y * speed * 100;

    layer.style.transform =
    `translate(${moveX}px, ${moveY}px)`;

  });

});

/* =========================
GSAP ENTRANCE
========================= */

gsap.from(".hero-title",{

  y:120,
  opacity:0,
  duration:1.8,
  ease:"power4.out"

});

gsap.from(".subtitle",{

  y:40,
  opacity:0,
  delay:0.4,
  duration:1.2,
  ease:"power3.out"

});

gsap.from(".scene-image",{

  y:180,
  opacity:0,
  duration:2,
  ease:"power4.out"

});

gsap.from(".btn",{

  y:30,
  opacity:0,
  stagger:0.1,
  delay:0.8,
  duration:1,
  ease:"power3.out"

});

/* =========================
PARTICLES
========================= */

for(let i=0;i<40;i++){

  const particle =
  document.createElement('div');

  particle.classList.add('particle');

  particle.style.left =
  Math.random() * 100 + 'vw';

  particle.style.animationDuration =
  (8 + Math.random() * 12) + 's';

  particle.style.animationDelay =
  Math.random() * 5 + 's';

  document.querySelector('.scene')
  .appendChild(particle);

}

</script>

</body>
</html>
