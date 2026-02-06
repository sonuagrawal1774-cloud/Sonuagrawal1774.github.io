<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Be My Valentine 💖</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- Cute Google Font -->
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">

  <style>
    body {
      margin: 0;
      height: 100vh;
      background-color: #ff7f7f; /* coral pink */
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
      font-family: 'Pacifico', cursive;
    }

    .container {
      text-align: center;
      z-index: 2;
    }

    h1 {
      font-size: 2.8rem;
      color: white;
      margin-bottom: 40px;
      font-weight: bold;
    }

    button {
      font-size: 1.2rem;
      padding: 12px 28px;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      position: relative;
    }

    #yesBtn {
      background-color: #ff2e63;
      color: white;
      margin-right: 20px;
    }

    #noBtn {
      background-color: white;
      color: #ff2e63;
      position: absolute;
    }

    /* Floating hearts */
    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background: rgba(255, 255, 255, 0.4);
      transform: rotate(45deg);
      animation: floatUp linear infinite;
    }

    .heart::before,
    .heart::after {
      content: "";
      width: 20px;
      height: 20px;
      background: rgba(255, 255, 255, 0.4);
      border-radius: 50%;
      position: absolute;
    }

    .heart::before {
      top: -10px;
      left: 0;
    }

    .heart::after {
      left: -10px;
      top: 0;
    }

    @keyframes floatUp {
      from {
        transform: translateY(100vh) rotate(45deg);
        opacity: 0;
      }
      to {
        transform: translateY(-10vh) rotate(45deg);
        opacity: 1;
      }
    }

    /* Confetti */
    .confetti {
      position: fixed;
      width: 10px;
      height: 10px;
      background-color: red;
      animation: fall 3s linear forwards;
    }

    @keyframes fall {
      to {
        transform: translateY(100vh) rotate(720deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>
      Adityaaaa, my baby,<br>
      will you be my valentine? 💕
    </h1>
    <button id="yesBtn">Yes 💖</button>
    <button id="noBtn">No 🙈</button>
  </div>

  <script>
    const noBtn = document.getElementById("noBtn");
    const yesBtn = document.getElementById("yesBtn");

    // Move "No" button randomly
    noBtn.addEventListener("mouseover", () => {
      const x = Math.random() * (window.innerWidth - 100);
      const y = Math.random() * (window.innerHeight - 100);
      noBtn.style.left = x + "px";
      noBtn.style.top = y + "px";
    });

    // Confetti on yes
    yesBtn.addEventListener("click", () => {
      for (let i = 0; i < 150; i++) {
        const confetti = document.createElement("div");
        confetti.classList.add("confetti");
        confetti.style.left = Math.random() * window.innerWidth + "px";
        confetti.style.backgroundColor =
          `hsl(${Math.random() * 360}, 100%, 70%)`;
        confetti.style.animationDuration = (Math.random() * 2 + 2) + "s";
        document.body.appendChild(confetti);

        setTimeout(() => confetti.remove(), 3000);
      }
      alert("YAY!!! 💘 Valentine accepted 💘");
    });

    // Create floating hearts
    function createHeart() {
      const heart = document.createElement("div");
      heart.classList.add("heart");
      heart.style.left = Math.random() * window.innerWidth + "px";
      heart.style.animationDuration = (Math.random() * 5 + 5) + "s";
      document.body.appendChild(heart);

      setTimeout(() => heart.remove(), 10000);
    }

    setInterval(createHeart, 300);
  </script>

</body>
</html>
