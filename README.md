<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Te Amo Jimena 💖</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
            overflow: hidden;
            font-family: 'Poppins', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            transition: background 2s;
        }

        .container {
            text-align: center;
            z-index: 2;
            opacity: 0;
            animation: fadeIn 3s ease forwards 3s;
        }

        h1 {
            color: #ffffff;
            text-shadow: 0 0 10px #00ffe7, 0 0 20px #00ffe7, 0 0 40px #00ffe7;
            font-size: 4em;
            animation: latido 1s infinite;
            margin: 0;
        }

        @keyframes latido {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        @keyframes fadeIn {
            to { opacity: 1; }
        }

        .poema {
            margin-top: 40px;
            font-size: 1.6em;
            color: #ffffff;
            background: rgba(0,0,0,0.5);
            padding: 30px;
            border: 2px solid #00ffe7;
            border-radius: 20px;
            box-shadow: 0 0 20px #00ffe7;
            width: 60%;
            margin-left: auto;
            margin-right: auto;
            opacity: 0;
            animation: fadeIn 3s ease forwards 6s;
            backdrop-filter: blur(8px);
        }

        .heart, .particle {
            position: absolute;
            z-index: 0;
        }

        .heart {
            width: 20px;
            height: 20px;
            background: red;
            transform: rotate(45deg);
            animation: float 10s linear infinite;
            opacity: 0.7;
        }

        .heart::before, .heart::after {
            content: "";
            position: absolute;
            width: 20px;
            height: 20px;
            background: red;
            border-radius: 50%;
        }

        .heart::before { top: -10px; left: 0; }
        .heart::after { top: 0; left: -10px; }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(45deg); opacity: 0; }
            50% { opacity: 0.9; }
            100% { transform: translateY(-10vh) rotate(45deg); opacity: 0; }
        }

        .particle {
            border-radius: 50%;
            background: white;
            opacity: 0.5;
            animation: sparkle 8s linear infinite;
        }

        @keyframes sparkle {
            0% { transform: translateY(100vh) scale(0); opacity: 0; }
            50% { opacity: 0.7; }
            100% { transform: translateY(-10vh) scale(1.5); opacity: 0; }
        }

        canvas {
            position: absolute;
            top: 0; left: 0;
            z-index: 1;
        }
    </style>
</head>
<body>

<canvas id="fireworks"></canvas>

<div class="container">
    <h1>💖 Te Amo Jimena 💖</h1>
    <div class="poema">
        Eres mi sol, mi luna, mi estrella,<br>
        En tu sonrisa encuentro mi hogar,<br>
        Cada latido mío lleva tu nombre,<br>
        Te amo Jimena, por siempre sin final.
    </div>
</div>

<audio autoplay loop>
    <source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3" type="audio/mp3">
</audio>

<script>
// Corazones flotantes
function crearCorazon() {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.style.left = Math.random() * window.innerWidth + "px";
    heart.style.animationDuration = 5 + Math.random() * 5 + "s";
    heart.style.background = `hsl(${Math.random()*360}, 70%, 60%)`;
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 10000);
}
setInterval(crearCorazon, 300);

// Partículas brillantes
function crearParticula() {
    const particle = document.createElement("div");
    particle.className = "particle";
    particle.style.left = Math.random() * window.innerWidth + "px";
    particle.style.width = particle.style.height = Math.random() * 5 + 3 + "px";
    particle.style.animationDuration = 5 + Math.random() * 5 + "s";
    document.body.appendChild(particle);
    setTimeout(() => particle.remove(), 10000);
}
setInterval(crearParticula, 200);

// Fuegos artificiales
const canvas = document.getElementById("fireworks");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

function firework() {
    const x = Math.random() * canvas.width;
    const y = Math.random() * canvas.height/2;
    const colors = ["#00ffe7", "#00bcd4", "#4dd0e1", "#26c6da", "#ffffff"];
    for (let i = 0; i < 50; i++) {
        let angle = Math.random() * 2 * Math.PI;
        let radius = Math.random() * 100;
        let fx = x + radius * Math.cos(angle);
        let fy = y + radius * Math.sin(angle);
        ctx.beginPath();
        ctx.arc(fx, fy, 2, 0, 2 * Math.PI);
        ctx.fillStyle = colors[Math.floor(Math.random()*colors.length)];
        ctx.fill();
    }
}
setInterval(firework, 1500);

window.addEventListener("resize", () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
});
</script>

</body>
</html>
