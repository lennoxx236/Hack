# Hack
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Alyssa 💘</title>

<style>
body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg, #ffd1dc, #f8c8dc);
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: -apple-system, BlinkMacSystemFont, Arial, sans-serif;
  overflow: hidden;
}

.card {
  background: white;
  padding: 28px 20px;
  border-radius: 26px;
  text-align: center;
  width: 90%;
  max-width: 330px;
  box-shadow: 0 12px 35px rgba(0,0,0,0.15);
  position: relative;
  z-index: 2;
}

h2 {
  margin-bottom: 20px;
}

.buttons {
  position: relative;
  height: 120px;
}

button {
  padding: 14px 28px;
  border: none;
  border-radius: 30px;
  font-size: 17px;
  cursor: pointer;
}

#yes {
  background: #ff4d6d;
  color: white;
  font-weight: bold;
}

#no {
  position: absolute;
  background: #e0e0e0;
  left: 50%;
  transform: translateX(-50%);
  bottom: 10px;
}

/* 😡 Image énervée */
.angry {
  position: absolute;
  top: -120px;
  left: 50%;
  transform: translateX(-50%) scale(0);
  width: 120px;
  transition: transform 0.2s ease;
}

.angry.show {
  transform: translateX(-50%) scale(1);
}

.success {
  position: absolute;
  inset: 0;
  background: white;
  display: none;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  animation: fadeIn 0.6s ease;
  z-index: 3;
}

.success img {
  width: 150px;
  margin-bottom: 15px;
  animation: pop 0.6s ease;
}

@keyframes pop {
  0% { transform: scale(0); }
  80% { transform: scale(1.1); }
  100% { transform: scale(1); }
}

.heart {
  font-size: 65px;
  animation: pulse 1s infinite;
}

@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.25); }
  100% { transform: scale(1); }
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

/* 💖 Coeurs qui tombent */
.falling-heart {
  position: fixed;
  top: -40px;
  color: #ff4d6d;
  font-size: 14px;
  pointer-events: none;
  animation: fall linear forwards;
  z-index: 1;
  text-align: center;
}

@keyframes fall {
  to {
    transform: translateY(110vh);
    opacity: 0;
  }
}
</style>
</head>

<body>

<div class="card">
  <h2>Alyssa, will you be my Valentine? 💘</h2>

  <!-- 😡 Image qui s’énerve -->
  <img
    src="https://i.imgur.com/5qH6zYF.png"
    alt="Angry cute"
    class="angry"
    id="angryImg"
  />

  <div class="buttons">
    <button id="yes">Yes 💖</button>
    <button id="no">No</button>
  </div>

  <div class="success" id="success">
    <!-- 🧸 Image mignonne -->
    <img src="https://i.imgur.com/8Km9tLL.png" alt="Cute bear" />

    <div class="heart">❤️</div>
    <h2>Yay Alyssa! 💕</h2>
    <p>See you on Valentine’s Day 😌</p>
  </div>
</div>

<!-- 🎶 Musique douce -->
<audio id="music" preload="auto">
  <source src="https://www.bensound.com/bensound-music/bensound-love.mp3" type="audio/mpeg">
</audio>

<script>
const noBtn = document.getElementById("no");
const yesBtn = document.getElementById("yes");
const success = document.getElementById("success");
const music = document.getElementById("music");
const angryImg = document.getElementById("angryImg");

function moveNo() {
  // image énervée
  angryImg.classList.add("show");
  setTimeout(() => angryImg.classList.remove("show"), 800);

  // bouton qui fuit
  const x = Math.random() * 200 - 100;
  const y = Math.random() * 80 - 40;
  noBtn.style.transform = translate(${x}px, ${y}px);
}

noBtn.addEventListener("mouseover", moveNo);
noBtn.addEventListener("touchstart", moveNo);

function createHeart() {
  const heart = document.createElement("div");
  heart.className = "falling-heart";
  heart.innerHTML = ❤️<br>Alyssa;
  heart.style.left = Math.random() * 100 + "vw";
  heart.style.animationDuration = (3 + Math.random() * 3) + "s";
  document.body.appendChild(heart);
  setTimeout(() => heart.remove(), 6000);
}

yesBtn.addEventListener("click", () => {
  success.style.display = "flex";
  music.play();
  setInterval(createHeart, 300);
});
</script>

</body>
</html>
