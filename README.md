<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>between last year and this afternoon</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;600;700&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">

  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>

  <style>
    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
    }

    body{
      overflow-x:hidden;
      background:#7cc9ff;
      font-family:'Inter',sans-serif;
      color:white;
      height:100vh;
      cursor:default;
    }

    .hero{
      position:relative;
      width:100%;
      height:100vh;
      overflow:hidden;
      background:
        radial-gradient(circle at top,#9be0ff 0%,#6bbfff 40%,#58aee5 100%);
    }

    /* atmospheric blur */
    .hero::before{
      content:'';
      position:absolute;
      inset:0;
      background:
        radial-gradient(circle at center, rgba(255,255,255,0.15), transparent 60%);
      filter:blur(80px);
      pointer-events:none;
    }

    /* clouds */

    .cloud{
      position:absolute;
      background:white;
      border-radius:100px;
      opacity:0.9;
      filter:blur(1px);
    }

    .cloud1{
      width:200px;
      height:70px;
      top:90px;
      left:80px;
      animation:floatCloud 18s ease-in-out infinite;
    }

    .cloud2{
      width:140px;
      height:55px;
      top:130px;
      right:180px;
      animation:floatCloud 22s ease-in-out infinite;
    }

    @keyframes floatCloud{
      0%,100%{
        transform:translateX(0px);
      }
      50%{
        transform:translateX(25px);
      }
    }

    /* title */

    .title{
      position:absolute;
      top:70px;
      left:8%;
      z-index:20;
      mix-blend-mode:screen;
    }

    .title h1{
      font-family:'Cormorant Garamond',serif;
      font-size:7vw;
      line-height:0.85;
      font-weight:600;
      letter-spacing:-2px;
      text-shadow:
        0 5px 30px rgba(0,0,0,0.15);
    }

    .title p{
      margin-top:15px;
      font-size:14px;
      letter-spacing:3px;
      opacity:0.8;
    }

    /* main scene */

    .scene{
      position:absolute;
      width:100%;
      height:100%;
      inset:0;
      perspective:1200px;
    }

    .layer{
      position:absolute;
      transition:transform .15s linear;
      will-change:transform;
    }

    /* grass foreground */

    .grass{
      position:absolute;
      bottom:-40px;
      width:120%;
      left:-10%;
      z-index:2;
      filter:blur(1px);
    }

    /* floating notes */

    .note{
      position:absolute;
      font-size:35px;
      animation:floatNote 5s ease-in-out infinite;
      opacity:0.8;
    }

    .note:nth-child(1){
      left:20%;
      top:40%;
      animation-delay:0s;
    }

    .note:nth-child(2){
      left:70%;
      top:38%;
      animation-delay:1s;
    }

    .note:nth-child(3){
      left:55%;
      top:30%;
      animation-delay:2s;
    }

    @keyframes floatNote{
      0%,100%{
        transform:translateY(0px) rotate(0deg);
      }

      50%{
        transform:translateY(-25px) rotate(10deg);
      }
    }

    /* image */

    .main-image{
      position:absolute;
      bottom:-2%;
      left:50%;
      transform:translateX(-50%);
      width:75vw;
      max-width:1200px;
      z-index:10;

      filter:
        drop-shadow(0 40px 50px rgba(0,0,0,0.3))
        saturate(1.05);
    }

    .main-image img{
      width:100%;
      display:block;
      object-fit:contain;
      pointer-events:none;
      user-select:none;
    }

    /* glow */

    .glow{
      position:absolute;
      width:500px;
      height:500px;
      background:radial-gradient(circle,
      rgba(255,204,120,0.3),
      transparent 70%);
      bottom:10%;
      left:50%;
      transform:translateX(-50%);
      filter:blur(80px);
      z-index:1;
    }

    /* buttons */

    .bottom-ui{
      position:absolute;
      bottom:40px;
      left:50%;
      transform:translateX(-50%);
      display:flex;
      gap:18px;
      z-index:50;
    }

    .btn{
      padding:14px 26px;
      border-radius:999px;
      background:rgba(255,255,255,0.15);
      backdrop-filter:blur(10px);
      border:1px solid rgba(255,255,255,0.2);
      color:white;
      text-decoration:none;
      font-size:13px;
      letter-spacing:1px;
      transition:0.3s;
    }

    .btn:hover{
      transform:translateY(-4px);
      background:rgba(255,255,255,0.22);
    }

    /* vignette */

    .vignette{
      position:absolute;
      inset:0;
      background:
      radial-gradient(circle at center,
      transparent 45%,
      rgba(0,0,0,0.25));
      pointer-events:none;
      z-index:100;
    }

    /* grain */

    .grain{
      position:absolute;
      inset:0;
      background-image:url("https://www.transparenttextures.com/patterns/noise.png");
      opacity:0.08;
      mix-blend-mode:overlay;
      pointer-events:none;
      z-index:99;
    }

    /* responsive */

    @media(max-width:900px){

      .title h1{
        font-size:15vw;
      }

      .main-image{
        width:120vw;
        bottom:5%;
      }

      .bottom-ui{
        flex-direction:column;
      }

    }

  </style>
</head>

<body>

  <section class="hero">

    <div class="cloud cloud1"></div>
    <div class="cloud cloud2"></div>

    <div class="title">
      <h1>
        between<br>
        last year<br>
        and this afternoon
      </h1>

      <p>2025 — 2026 ✦ a music diary</p>
    </div>

    <div class="scene" id="scene">

      <div class="glow"></div>

      <div class="note">♪</div>
      <div class="note">♫</div>
      <div class="note">♩</div>

      <div class="layer main-image" data-speed="0.05">
        <img src="anchit-web.png" alt="">
      </div>

    </div>

    <div class="bottom-ui">
      <a href="#" class="btn">SPOTIFY</a>
      <a href="#" class="btn">INSTAGRAM</a>
      <a href="#" class="btn">AMBIENT SOUND</a>
    </div>

    <div class="grain"></div>
    <div class="vignette"></div>

  </section>

  <script>

    const scene = document.getElementById('scene');
    const layers = document.querySelectorAll('.layer');

    window.addEventListener('mousemove', (e)=>{

      const x = (window.innerWidth / 2 - e.pageX) / 40;
      const y = (window.innerHeight / 2 - e.pageY) / 40;

      layers.forEach(layer=>{

        const speed = layer.getAttribute('data-speed');

        layer.style.transform =
          `translateX(calc(-50% + ${x * speed}px))
           translateY(${y * speed}px)
           scale(1.02)`;

      });

    });

    gsap.from(".title h1",{
      y:80,
      opacity:0,
      duration:1.5,
      ease:"power4.out"
    });

    gsap.from(".title p",{
      y:30,
      opacity:0,
      delay:0.3,
      duration:1.2,
      ease:"power3.out"
    });

    gsap.from(".main-image",{
      y:120,
      opacity:0,
      duration:2,
      ease:"power4.out"
    });

    gsap.from(".btn",{
      y:40,
      opacity:0,
      stagger:0.1,
      delay:0.8,
      duration:1,
      ease:"power3.out"
    });

  </script>

</body>
</html>
