<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Free Fire Challenge 🔥</title>

  <style>
    body {
      height: 100vh;
      margin: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      background: radial-gradient(circle, #1a0000, #000);
      color: white;
      font-family: Arial, sans-serif;
      overflow: hidden;
    }

    .box {
      text-align: center;
      z-index: 2;
    }

    h1 {
      font-size: 2.2rem;
      text-shadow: 0 0 15px red;
    }

    button {
      padding: 14px 30px;
      font-size: 18px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      margin: 12px;
      transition: all 0.2s ease;
    }

    #yes {
      background: linear-gradient(45deg, #00ff88, #00cc66);
      box-shadow: 0 0 15px #00ff88;
    }

    #no {
      background: linear-gradient(45deg, #ff3333, #cc0000);
      position: absolute;
      box-shadow: 0 0 15px red;
      transition: left 0.15s, top 0.15s;
    }

    /* Fire animation */
    .fire {
      position: absolute;
      bottom: -20px;
      width: 100%;
      height: 200px;
      background: radial-gradient(circle at center, orange, red, transparent);
      animation: fireMove 2s infinite alternate;
      opacity: 0.5;
    }

    @keyframes fireMove {
      from { transform: scaleY(1); }
      to { transform: scaleY(1.2); }
    }
  </style>
</head>

<body>
  <div class="fire"></div>

  <div class="box">
    <h1>Khelega Free Fire? 🔥🎮</h1>
    <button id="yes" onclick="yesClick()">YES</button>
    <button id="no">NO</button>
  </div>

  <!-- Sound -->
  <audio id="clickSound">
    <source src="https://www.soundjay.com/buttons/sounds/button-09.mp3">
  </audio>

  <script>
    const noBtn = document.getElementById("no");
    const yesBtn = document.getElementById("yes");
    const sound = document.getElementById("clickSound");
    let yesSize = 18;

    function moveNo(x, y) {
      const rect = noBtn.getBoundingClientRect();
      const noX = rect.left + rect.width / 2;
      const noY = rect.top + rect.height / 2;

      const dx = noX - x;
      const dy = noY - y;
      const dist = Math.hypot(dx, dy);

      if (dist < 120) {
        let moveX = (dx / dist) * 160;
        let moveY = (dy / dist) * 160;

        let newX = rect.left + moveX;
        let newY = rect.top + moveY;

        newX = Math.max(0, Math.min(window.innerWidth - rect.width, newX));
        newY = Math.max(0, Math.min(window.innerHeight - rect.height, newY));

        noBtn.style.left = newX + "px";
        noBtn.style.top = newY + "px";

        yesSize += 1.4;
        yesBtn.style.fontSize = yesSize + "px";
      }
    }

    // PC
    document.addEventListener("mousemove", (e) => {
      moveNo(e.clientX, e.clientY);
    });

    // Mobile
    document.addEventListener("touchmove", (e) => {
      const t = e.touches[0];
      moveNo(t.clientX, t.clientY);
    });

    function yesClick() {
      sound.play();
      alert("Aja noobde 😎🔥 1v1 custom mein!");
    }
  </script>
</body>
</html>
