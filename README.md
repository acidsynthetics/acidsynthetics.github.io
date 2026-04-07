<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>Synthetics</title>
 <style>
 @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@900&family=Mr+Dafoe&display=swap');

 :root {
 --neon-pink: #ff00ff;
 --neon-blue: #00ffff;
 --neon-purple: #9d00ff;
 --sun-orange: #ff8c00;
 --sun-red: #ff0055;
 --bg-dark: #030008;
 --bg-glow: #1a0033;
 }

 body {
 margin: 0;
 padding: 0;
 background: radial-gradient(circle at 50% 40%, var(--bg-glow) 0%, var(--bg-dark) 80%);
 background-color: var(--bg-dark);
 font-family: 'Orbitron', sans-serif;
 color: white;
 overflow-x: hidden;
 display: flex;
 flex-direction: column;
 align-items: center;
 min-height: 100vh;
 width: 100%; /* Ensure body spans full width */
 }

 /* CRT Scanline Overlay */
 body::before {
 content: " ";
 display: block;
 position: fixed;
 top: 0; left: 0; bottom: 0; right: 0;
 background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.2) 50%);
 z-index: 100;
 background-size: 100% 3px;
 pointer-events: none;
 opacity: 0.6;
 }

 .star {
 position: fixed;
 background-color: #fff;
 border-radius: 50%;
 z-index: -4;
 animation: twinkle 2s infinite ease-in-out;
 }

 @keyframes twinkle {
 0%, 100% { opacity: 0.3; transform: scale(1); }
 50% { opacity: 1; transform: scale(1.4); box-shadow: 0 0 10px #fff; }
 }

 .sun {
 position: fixed;
 top: 12%;
 left: 50%;
 transform: translateX(-50%); /* Keeps it perfectly centered */
 width: 280px;
 height: 280px;
 border-radius: 50%;
 background: linear-gradient(var(--sun-orange) 0%, var(--sun-red) 40%, var(--bg-dark) 90%);
 box-shadow: 0 0 40px var(--sun-red), 0 0 80px var(--sun-orange), 0 0 120px rgba(255, 0, 255, 0.3);
 z-index: -3;
 -webkit-mask-image: linear-gradient(to bottom, 
 black 0%, black 60%, 
 transparent 62%, transparent 64%, 
 black 66%, black 74%, 
 transparent 76%, transparent 78%, 
 black 80%, black 88%, 
 transparent 90%, transparent 92%, 
 black 94%, black 100%);
 }

 .mountain {
 position: fixed;
 bottom: 30%;
 width: 100vw; /* Use viewport width to prevent cutoff */
 left: 0;
 height: 350px;
 z-index: -2;
 }

 .mtn-back {
 background: #1a0033;
 clip-path: polygon(0% 100%, 10% 40%, 30% 85%, 42% 50%, 45% 100%, 55% 100%, 58% 50%, 70% 85%, 90% 40%, 100% 100%);
 opacity: 0.4;
 filter: blur(2px);
 }

 .mtn-front {
 background: linear-gradient(to bottom, #300066, var(--bg-dark));
 clip-path: polygon(0% 100%, 15% 50%, 35% 90%, 45% 60%, 48% 100%, 52% 100%, 55% 60%, 65% 90%, 85% 50%, 100% 100%);
 border-top: 3px solid var(--neon-pink);
 filter: drop-shadow(0 0 15px var(--neon-pink));
 }

 .grid-container {
 position: fixed;
 bottom: 0;
 left: 0;
 width: 100%;
 height: 50vh;
 z-index: -1;
 perspective: 200px;
 perspective-origin: 50% 0%; 
 overflow: hidden;
 }

 .grid-floor {
 position: absolute;
 top: 0;
 left: -100%; /* Wider floor to prevent side gaps on large screens */
 width: 300%; 
 height: 100%;
 background-image: 
 linear-gradient(var(--bg-dark) 0%, transparent 20%, rgba(0, 255, 255, 0.1) 100%),
 linear-gradient(90deg, var(--neon-blue) 1px, transparent 1px),
 linear-gradient(var(--neon-pink) 1px, transparent 1px);
 background-size: 100% 100%, 60px 60px, 60px 60px;
 transform: rotateX(75deg);
 transform-origin: top;
 animation: roadMove 2s linear infinite;
 mask-image: linear-gradient(to bottom, transparent 0%, black 15%);
 }

 @keyframes roadMove {
 from { background-position: 0 0; }
 to { background-position: 0 60px; }
 }

 header {
 margin: 80px 0 50px 0;
 text-align: center;
 z-index: 10;
 width: 100%;
 }

 h1 {
 font-family: 'Mr Dafoe', cursive;
 font-size: clamp(3.5rem, 12vw, 7rem);
 color: #fff;
 text-shadow: 3px 0px var(--neon-blue), -3px 0px var(--neon-pink), 0 0 20px rgba(255, 255, 255, 0.5), 0 0 40px var(--neon-pink);
 transform: rotate(-5deg);
 margin: 0;
 }

 .shop-container {
 display: grid;
 grid-template-columns: repeat(2, 1fr);
 gap: 40px;
 max-width: 1000px;
 width: 90%;
 padding: 20px;
 z-index: 10;
 }

 .product-card {
 background: linear-gradient(135deg, rgba(255, 255, 255, 0.08) 0%, rgba(0, 0, 0, 0.3) 100%);
 border-radius: 4px;
 padding: 25px;
 text-align: center;
 position: relative;
 border: 1px solid var(--neon-blue);
 box-shadow: 0 0 15px rgba(0, 255, 255, 0.3), inset 0 0 10px rgba(0, 255, 255, 0.1);
 transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
 overflow: hidden;
 }

 .product-card::before {
 content: "";
 position: absolute;
 top: 0; left: 0; right: 0;
 height: 1px;
 background: #fff;
 box-shadow: 0 0 10px #fff, 0 0 20px var(--neon-blue);
 opacity: 0.8;
 }

 .product-card:hover {
 transform: translateY(-10px) scale(1.03);
 border-color: var(--neon-pink);
 box-shadow: 0 0 40px rgba(255, 0, 255, 0.6), inset 0 0 20px rgba(255, 0, 255, 0.2);
 }

 .product-card img {
 width: 100%;
 border: 1px solid rgba(255, 255, 255, 0.1);
 margin: 15px 0;
 filter: contrast(1.2) brightness(1.1);
 }

 .price {
 display: block;
 font-size: 2.2rem;
 color: #ffff00;
 margin-bottom: 10px;
 font-weight: 900;
 text-shadow: 0 0 15px rgba(255, 255, 0, 0.5);
 }

 .description {
 font-size: 0.75rem;
 color: var(--neon-blue);
 text-transform: uppercase;
 letter-spacing: 2px;
 }

 footer {
 margin: 100px 0;
 background: rgba(0, 0, 0, 0.9);
 padding: 40px;
 border: 2px solid var(--neon-pink);
 box-shadow: 0 0 30px var(--neon-pink);
 text-align: center;
 z-index: 10;
 width: fit-content;
 min-width: 320px;
 }

 footer h3 { color: var(--neon-pink); margin-top: 0; }
 
 .email-box {
 display: flex;
 align-items: center;
 justify-content: center;
 gap: 15px;
 margin-top: 10px;
 }

 #email-text { 
 color: var(--neon-blue); 
 font-family: monospace; 
 font-size: 1rem; 
 text-shadow: 0 0 5px var(--neon-blue); 
 }

 .copy-btn {
 background: transparent;
 border: 1px solid var(--neon-blue);
 color: var(--neon-blue);
 font-family: 'Orbitron', sans-serif;
 font-size: 0.7rem;
 padding: 5px 10px;
 cursor: pointer;
 transition: all 0.3s;
 text-transform: uppercase;
 box-shadow: 0 0 5px var(--neon-blue);
 }

 .copy-btn:hover {
 background: var(--neon-blue);
 color: #000;
 box-shadow: 0 0 15px var(--neon-blue);
 }

 .copy-btn:active {
 transform: scale(0.95);
 }

 @media (max-width: 700px) {
 .shop-container { grid-template-columns: 1fr; }
 .sun { width: 200px; height: 200px; }
 .email-box { flex-direction: column; }
 }
 </style>
</head>
<body>

 <div id="starfield"></div>

 <div class="sun"></div>
 <div class="mountain mtn-back"></div>
 <div class="mountain mtn-front"></div>
 
 <div class="grid-container">
 <div class="grid-floor"></div>
 </div>

 <header>
 <h1>Synthetics</h1>
 </header>

 <div class="shop-container">
 <div class="product-card">
 <h2>100 PCS replace</h2>
 <img src="https://picsum.photos/400/300?random=10" alt="item">
 <span class="price">300 EUR</span>
 <p class="description"> replace <br> 10x10 matrix
 </p>
 </div>
 <div class="product-card">
 <h2>759 PCS x</h2>
 <img src="https://picsum.photos/400/300?random=11" alt="item">
 <span class="price">1518 EUR</span>
 <p class="description">x<br> custom print available </p>
 </div>
 <div class="product-card">
 <h2>1000 Drops of replace</h2>
 <img src="https://picsum.photos/400/300?random=12" alt="item">
 <span class="price">2000 EUR</span>
 <p class="description">x</p>
 </div>
 <div class="product-card">
 <h2>1unit replace</h2>
 <img src="https://picsum.photos/400/300?random=13" alt="item">
 <span class="price">15.000 EUR</span>
 <p class="description">product desc replace</p>
 </div>
 </div>

 <footer>
 <h3>CONTACT</h3>
 <div class="email-box">
 <span id="email-text">example@email.com</span>
 <button class="copy-btn" onclick="copyEmail()">Copy</button>
 </div>
 </footer>

 <script>
 const starfield = document.getElementById('starfield');
 const colors = ['#ff00ff', '#00ffff', '#ffffff', '#ffff00', '#9d00ff'];
 
 for (let i = 0; i < 80; i++) {
 const star = document.createElement('div');
 star.className = 'star';
 const size = Math.random() * 3 + 1 + 'px';
 star.style.width = size;
 star.style.height = size;
 star.style.top = Math.random() * 60 + '%';
 star.style.left = Math.random() * 100 + '%';
 star.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
 star.style.boxShadow = `0 0 8px ${star.style.backgroundColor}`;
 star.style.animationDelay = Math.random() * 2 + 's';
 starfield.appendChild(star);
 }

 window.addEventListener('scroll', () => {
 const scroll = window.pageYOffset;
 const mtnFront = document.querySelector('.mtn-front');
 const mtnBack = document.querySelector('.mtn-back');
 if(mtnFront) mtnFront.style.transform = `translateY(${scroll * 0.1}px)`;
 if(mtnBack) mtnBack.style.transform = `translateY(${scroll * 0.03}px)`;
 });

 function copyEmail() {
 const email = document.getElementById('email-text').innerText;
 const btn = document.querySelector('.copy-btn');
 
 navigator.clipboard.writeText(email).then(() => {
 const originalText = btn.innerText;
 btn.innerText = 'Copied!';
 btn.style.borderColor = 'var(--neon-pink)';
 btn.style.color = 'var(--neon-pink)';
 btn.style.boxShadow = '0 0 15px var(--neon-pink)';
 
 setTimeout(() => {
 btn.innerText = originalText;
 btn.style.borderColor = 'var(--neon-blue)';
 btn.style.color = 'var(--neon-blue)';
 btn.style.boxShadow = '0 0 5px var(--neon-blue)';
 }, 1500);
 });
 }
 </script>
</body>
</html>
