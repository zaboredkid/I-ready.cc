<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Project K.I.W.I. | Interactive Gold Matrix</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Courier New', Courier, monospace;
        }

        body, html {
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000000;
            color: #d4af37;
        }

        /* Matrix Background */
        #matrix-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        /* Interactive Interface Overlay */
        .ui-container {
            position: relative;
            z-index: 2;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(2px);
            text-align: center;
            padding: 20px;
        }

        .kiwi-card {
            border: 2px solid #d4af37;
            background: rgba(15, 15, 15, 0.85);
            padding: 40px;
            border-radius: 4px;
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.2);
            max-width: 500px;
            transition: all 0.3s ease;
        }

        .kiwi-card:hover {
            box-shadow: 0 0 50px rgba(212, 175, 55, 0.5);
            transform: scale(1.02);
            background: rgba(25, 25, 25, 0.95);
        }

        h1 {
            font-size: 2.5rem;
            letter-spacing: 4px;
            margin-bottom: 15px;
            text-transform: uppercase;
            text-shadow: 0 0 10px rgba(212, 175, 55, 0.6);
        }

        .tagline {
            font-size: 1rem;
            color: #f3e5ab;
            margin-bottom: 30px;
            line-height: 1.6;
        }

        .btn-interactive {
            display: inline-block;
            background: transparent;
            color: #d4af37;
            border: 1px solid #d4af37;
            padding: 12px 30px;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            cursor: pointer;
            text-decoration: none;
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
        }

        .btn-interactive:hover {
            background: #d4af37;
            color: #000;
            box-shadow: 0 0 15px #d4af37;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <canvas id="matrix-canvas"></canvas>

    <div class="ui-container">
        <div class="kiwi-card">
            <h1>🥝 KIWI.sys</h1>
            <p class="tagline">An interactive, high-performance web interface rendering neural network telemetry inside an executive gold and obsidian matrix wrapper.</p>
            <a href="#" class="btn-interactive" onclick="triggerOverload()">Initialize Deck</a>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('matrix-canvas');
        const ctx = canvas.getContext('2d');

        // Set dimensions
        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);

        // Matrix character array (mix of katakana, numbers, and latin code markers)
        const alphabet = "🥝0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZシステム";
        const fontSize = 16;
        let columns = canvas.width / fontSize;

        const rainDrops = [];
        for (let x = 0; x < columns; x++) {
            rainDrops[x] = 1;
        }

        // Color Spectrum definitions for Gold
        const goldShades = ["#d4af37", "#f3e5ab", "#aa7c11", "#ffdf00", "#b59410"];

        function drawMatrix() {
            // Slight transparency trail creates the digital rain motion decay
            ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            for (let i = 0; i < rainDrops.length; i++) {
                const text = alphabet.charAt(Math.floor(Math.random() * alphabet.length));
                
                // Randomly alternate gold shades to give depth/shimmer
                ctx.fillStyle = goldShades[Math.floor(Math.random() * goldShades.length)];
                ctx.font = fontSize + 'px monospace';
                
                // First characters in columns occasionally glow pure white
                if(Math.random() > 0.98) {
                    ctx.fillStyle = "#ffffff";
                }

                ctx.fillText(text, i * fontSize, rainDrops[i] * fontSize);

                if (rainDrops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                    rainDrops[i] = 0;
                }
                rainDrops[i]++;
            }
        }

        // Interactive speed boost function when clicking the interface button
        function triggerOverload() {
            clearInterval(matrixInterval);
            // Speed up rendering temporarily
            matrixInterval = setInterval(drawMatrix, 15);
            setTimeout(() => {
                clearInterval(matrixInterval);
                matrixInterval = setInterval(drawMatrix, 33);
            }, 2000);
        }

        // Loop execution (roughly 30 FPS base speed)
        let matrixInterval = setInterval(drawMatrix, 33);
    </script>
</body>
</html>
