<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Untuk Hafizah Arasya ❤️</title>

<style>
* {
    margin: 0;
    padding: 0;
}

body {
    background: black;
    overflow: hidden;
    font-family: 'Segoe UI', sans-serif;
}

/* Judul */
h1 {
    position: absolute;
    top: 15%;
    width: 100%;
    text-align: center;
    font-size: 50px;
    background: linear-gradient(to right, pink, violet);
    -webkit-background-clip: text;
    color: transparent;
    animation: fadeIn 3s ease-in-out;
}

/* Teks romantis */
#text {
    position: absolute;
    bottom: 80px;
    width: 100%;
    text-align: center;
    color: white;
    font-size: 18px;
    padding: 0 20px;
}

/* Animasi fade */
@keyframes fadeIn {
    from {opacity: 0;}
    to {opacity: 1;}
}

/* Love jatuh */
.heart {
    position: absolute;
    color: pink;
    font-size: 20px;
    animation: fall linear infinite;
}

@keyframes fall {
    from {
        transform: translateY(-10%);
    }
    to {
        transform: translateY(110vh);
    }
}
</style>
</head>

<body>

<h1>Selamat Ulang Tahun Hafizah Arasya ❤️</h1>

<div id="text"></div>

<!-- Musik -->
<iframe id="musicFrame" width="0" height="0"
src="https://www.youtube.com/embed/2Vv-BfVoq4g?autoplay=1&loop=1&playlist=2Vv-BfVoq4g"
frameborder="0"
allow="autoplay">
</iframe>

<canvas id="canvas"></canvas>

<script>
// trigger biar musik jalan di HP
document.body.addEventListener("click", function() {
    let iframe = document.getElementById("musicFrame");
    iframe.src = iframe.src;
});
</script>

<script>
// ================= TEXT TYPING =================
const message = `Untuk Hafizah Arasya,

Di hari istimewamu, aku cuma ingin kamu tahu…
bahwa kamu adalah alasan kenapa dunia terasa lebih indah.

Senyummu sederhana, tapi mampu mengubah hariku.
Hadirmu biasa, tapi rasanya luar biasa.

Selamat ulang tahun ya 
Semoga semua hal baik selalu menemukan jalannya ke kamu.
Dan semoga… aku tetap jadi bagian dari cerita indahmu.`;

let i = 0;
function typing() {
    if (i < message.length) {
        document.getElementById("text").innerHTML += message.charAt(i);
        i++;
        setTimeout(typing, 40);
    }
}
typing();

// ================= HEART EFFECT =================
function createHeart() {
    const heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML = "❤";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = (Math.random() * 3 + 2) + "s";
    document.body.appendChild(heart);

    setTimeout(() => {
        heart.remove();
    }, 5000);
}
setInterval(createHeart, 300);

// ================= FIREWORK =================
let canvas = document.getElementById("canvas");
let ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let fireworks = [];
let gravity = 0.2;

function random(n) {
    return Math.random() * n;
}

class Particle {
    constructor(x, y, color) {
        this.x = x;
        this.y = y;
        this.color = color;
        this.velX = random(6) - 3;
        this.velY = random(6) - 3;
        this.life = 100;
    }

    update() {
        this.x += this.velX;
        this.y += this.velY;
        this.velY += gravity;
        this.life--;
    }

    draw() {
        ctx.beginPath();
        ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
        ctx.fillStyle = this.color;
        ctx.shadowBlur = 10;
        ctx.shadowColor = this.color;
        ctx.fill();
    }
}

class Firework {
    constructor(x, y) {
        this.x = x;
        this.y = y;
        this.particles = [];
        this.color = `hsl(${random(360)},100%,50%)`;

        for (let i = 0; i < 80; i++) {
            this.particles.push(new Particle(x, y, this.color));
        }
    }

    update() {
        this.particles.forEach(p => p.update());
    }

    draw() {
        this.particles.forEach(p => p.draw());
    }
}

// klik untuk buat fireworks
canvas.addEventListener("click", (e) => {
    fireworks.push(new Firework(e.clientX, e.clientY));
});

// auto fireworks
setInterval(() => {
    fireworks.push(new Firework(random(canvas.width), random(canvas.height / 2)));
}, 1200);

// animasi
function animate() {
    ctx.fillStyle = "rgba(0,0,0,0.2)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    fireworks.forEach((f, i) => {
        f.update();
        f.draw();
        if (f.particles[0].life <= 0) {
            fireworks.splice(i, 1);
        }
    });

    requestAnimationFrame(animate);
}
animate();

// resize
window.addEventListener("resize", () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
});
</script>

</body>
</html>