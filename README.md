<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Replace Shop Name</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@900&family=Mr+Dafoe&display=swap');

        :root {
            --neon-pink: #ff00ff;
            --neon-blue: #00ffff;
            --sun-orange: #ff8c00;
            --sun-red: #ff0055;
            --bg-dark: #050110;
        }

        body {
            margin: 0;
            padding: 0;
            background-color: var(--bg-dark);
            font-family: 'Orbitron', sans-serif;
            color: white;
            overflow-x: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        /* CRT Scanline Overlay */
        body::before {
            content: " ";
            display: block;
            position: fixed;
            top: 0; left: 0; bottom: 0; right: 0;
            background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.15) 50%);
            z-index: 100;
            background-size: 100% 4px;
            pointer-events: none;
        }

        /* The Synthwave Sun */
        .sun {
            position: fixed;
            top: 10%;
            left: 50%;
            transform: translateX(-50%);
            width: 350px;
            height: 350px;
            border-radius: 50%;
            background: linear-gradient(var(--sun-orange) 0%, var(--sun-red) 50%, var(--bg-dark) 100%);
            box-shadow: 0 0 60px var(--sun-red);
            z-index: -3;
            -webkit-mask-image: linear-gradient(to bottom, 
                black 0%, black 60%, 
                transparent 60%, transparent 65%, 
                black 65%, black 75%, 
                transparent 75%, transparent 82%, 
                black 82%, black 90%, 
                transparent 90%, transparent 97%, 
                black 97%, black 100%);
        }

        /* Parallax Mountains */
        .mountain {
            position: fixed;
            bottom: 35%;
            width: 100%;
            height: 300px;
            z-index: -2;
        }

        .mtn-back {
            background: #240b36;
            clip-path: polygon(0% 100%, 15% 40%, 35% 80%, 50% 20%, 65% 70%, 85% 30%, 100% 100%);
            opacity: 0.5;
        }

        .mtn-front {
            background: linear-gradient(to bottom, #4e035a, var(--bg-dark));
            clip-path: polygon(0% 100%, 10% 70%, 25% 40%, 45% 90%, 60% 50%, 75% 80%, 90% 60%, 100% 100%);
            border-top: 2px solid var(--neon-pink);
        }

        /* Moving Grid Floor */
        .grid-floor {
            position: fixed;
            bottom: 0;
            width: 200%;
            height: 50vh;
            background-image: 
                linear-gradient(transparent 0%, var(--neon-blue) 100%),
                linear-gradient(90deg, var(--neon-pink) 1px, transparent 0),
                linear-gradient(var(--neon-pink) 1px, transparent 0);
            background-size: 100% 100%, 60px 60px, 60px 60px;
            transform: perspective(400px) rotateX(70deg);
            transform-origin: bottom;
            z-index: -1;
            opacity: 0.7;
        }

        header {
            margin: 80px 0 40px 0;
            text-align: center;
            z-index: 10;
        }

        h1 {
            font-family: 'Mr Dafoe', cursive;
            font-size: clamp(3rem, 10vw, 6rem);
            color: #fff;
            text-shadow: 0 0 10px #fff, 0 0 20px var(--neon-pink), 0 0 40px var(--neon-pink);
            transform: rotate(-5deg);
        }

        .shop-container {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 30px;
            max-width: 900px;
            padding: 20px;
            z-index: 10;
        }

        .product-card {
            background: rgba(5, 1, 16, 0.95);
            border: 2px solid var(--neon-blue);
            padding: 20px;
            text-align: center;
            box-shadow: 0 0 15px var(--neon-blue);
            transition: 0.3s;
        }

        .product-card:hover {
            border-color: var(--neon-pink);
            box-shadow: 0 0 25px var(--neon-pink);
            transform: scale(1.02);
        }

        .product-card img {
            width: 100%;
            border: 1px solid #333;
            margin: 15px 0;
        }

        .price {
            display: block;
            font-size: 2rem;
            color: #ffff00;
            margin-bottom: 10px;
        }

        .description {
            font-size: 0.7rem;
            color: var(--neon-blue);
            text-transform: uppercase;
        }

        footer {
            margin: 100px 0;
            background: #000;
            padding: 30px;
            border: 2px solid var(--neon-pink);
            text-align: center;
            z-index: 10;
            width: 280px;
        }

        footer h3 { color: var(--neon-pink); margin-top: 0; }
        footer p { color: var(--neon-blue); font-family: monospace; font-size: 0.9rem; }

        @media (max-width: 700px) {
            .shop-container { grid-template-columns: 1fr; }
            .sun { width: 200px; height: 200px; }
        }
    </style>
</head>
<body>

    <div class="sun"></div>
    <div class="mountain mtn-back" id="mtn-back"></div>
    <div class="mountain mtn-front" id="mtn-front"></div>
    <div class="grid-floor" id="grid"></div>

    <header>
        <h1>Replace Shop Name</h1>
    </header>

    <div class="shop-container">
        <div class="product-card">
            <h2>x replace item name</h2>
            <img src="https://picsum.photos/400/300?random=10" alt="item">
            <span class="price">100 EUR</span>
            <p class="description">sample description please replace</p>
        </div>
        <div class="product-card">
            <h2>x replace item name</h2>
            <img src="https://picsum.photos/400/300?random=11" alt="item">
            <span class="price">100 EUR</span>
            <p class="description">sample description please replace</p>
        </div>
        <div class="product-card">
            <h2>x replace item name</h2>
            <img src="https://picsum.photos/400/300?random=12" alt="item">
            <span class="price">100 EUR</span>
            <p class="description">sample description please replace</p>
        </div>
        <div class="product-card">
            <h2>x replace item name</h2>
            <img src="https://picsum.photos/400/300?random=13" alt="item">
            <span class="price">100 EUR</span>
            <p class="description">sample description please replace</p>
        </div>
    </div>

    <footer>
        <h3>CONTACT</h3>
        <p>example@email.com</p>
    </footer>

    <script>
        window.addEventListener('scroll', () => {
            const scroll = window.pageYOffset;
            
            // Grid moves fast
            document.getElementById('grid').style.backgroundPositionY = (scroll * 0.6) + 'px';
            
            // Front mountains move medium speed
            document.getElementById('mtn-front').style.transform = `translateY(${scroll * 0.15}px)`;
            
            // Back mountains move slow (Parallax)
            document.getElementById('mtn-back').style.transform = `translateY(${scroll * 0.05}px)`;
        });
    </script>
</body>
</html>
