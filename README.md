# Ayan-
Sign Fruit Game 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Fruit Slash — $SIGN Edition</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: linear-gradient(to bottom, #ffa64d, #ff8533);
      font-family: Arial, sans-serif;
    }
    #gameCanvas {
      display: block;
      margin: 0 auto;
      background: #fff3e0;
      border: 4px solid #ff6600;
      border-radius: 15px;
    }
    #score {
      position: absolute;
      top: 15px;
      left: 15px;
      font-size: 24px;
      font-weight: bold;
      color: #d35400;
    }
    #title {
      position: absolute;
      top: 15px;
      right: 15px;
      font-size: 20px;
      color: #e74c3c;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div id="score">Score: 0</div>
  <div id="title">$SIGN Airdrop Game</div>
  <canvas id="gameCanvas" width="600" height="600"></canvas>

  <script>
    const canvas = document.getElementById("gameCanvas");
    const ctx = canvas.getContext("2d");
    let fruits = [];
    let score = 0;

    const fruitImages = [
      "https://upload.wikimedia.org/wikipedia/commons/1/15/Red_Apple.jpg",
      "https://upload.wikimedia.org/wikipedia/commons/c/c4/Orange-Fruit-Pieces.jpg",
      "https://upload.wikimedia.org/wikipedia/commons/2/2f/Cut_Mango.jpg",
      "https://cryptologos.cc/logos/ethsign-sign-logo.png" // $SIGN Logo
    ];

    class Fruit {
      constructor(x, y, imgSrc) {
        this.x = x;
        this.y = y;
        this.vx = (Math.random() - 0.5) * 8;
        this.vy = -Math.random() * 10 - 8;
        this.img = new Image();
        this.img.src = imgSrc;
        this.radius = 40;
        this.cut = false;
      }
      draw() {
        if (!this.cut) {
          ctx.drawImage(this.img, this.x - this.radius, this.y - this.radius, this.radius*2, this.radius*2);
        }
      }
      update() {
        this.x += this.vx;
        this.y += this.vy;
        this.vy += 0.4; // gravity
        this.draw();
      }
    }

    function spawnFruit() {
      let x = Math.random() * canvas.width;
      let y =
