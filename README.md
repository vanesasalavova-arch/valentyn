<!DOCTYPE html>
<html lang="cs">
<head>
<meta charset="UTF-8">
<title>Valentýn ❤️</title>

<style>
body {
  background: #ffe6f0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  font-family: Arial, sans-serif;
  margin: 0;
  overflow: hidden;
}

.card {
  background: white;
  padding: 50px;
  border-radius: 20px;
  text-align: center;
  box-shadow: 0 15px 35px rgba(0,0,0,0.15);
  position: relative;
}

h1 {
  color: #d6336c;
  margin-bottom: 40px;
}

.buttons {
  display: flex;
  justify-content: center;
  gap: 20px;
}

button {
  border: none;
  padding: 12px 30px;
  font-size: 18px;
  border-radius: 10px;
  cursor: pointer;
  transition: 0.2s;
  position: relative;
}

#ano {
  background: #28a745;
  color: white;
}

#ne {
  background: #dc3545;
  color: white;
  position: absolute;
}
.heart {
  position: fixed;
  top: -10px;
  font-size: 24px;
  animation: fall 3s linear forwards;
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
  <h1>Budeš můj Valentýn? ❤️</h1>
  <div class="buttons">
    <button id="ano">ANO</button>
    <button id="ne">NE</button>
  </div>
</div>

<script>
let size = 18;
const neBtn = document.getElementById("ne");
const anoBtn = document.getElementById("ano");

// Náhodná pozice pro NE
function moveButton() {
  const x = Math.random() * (window.innerWidth - 100);
  const y = Math.random() * (window.innerHeight - 50);
  neBtn.style.left = x + "px";
  neBtn.style.top = y + "px";
}

// Zmenšování + uhýbání
neBtn.addEventListener("mouseover", () => {
  size -= 2;
  if (size > 6) {
    neBtn.style.fontSize = size + "px";
    neBtn.style.padding = "6px " + size + "px";
  } else {
    neBtn.style.display = "none";
  }
  moveButton();
});

// Kliknutí ANO
anoBtn.addEventListener("click", () => {
  document.body.innerHTML = `
    <div style="
      display:flex;
      justify-content:center;
      align-items:center;
      height:100vh;
      background:#ffe6f0;
      flex-direction:column;
      font-family:Arial;
    ">
      <h1 style="color:#d6336c;">Věděl jsem to 😎❤️</h1>
      <p>Teď už spolu oficiálně chodíme.</p>
    </div>
  `;

  // Padající srdíčka
  setInterval(() => {
    const heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML = "❤️";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = Math.random() * 20 + 20 + "px";
    document.body.appendChild(heart);

    setTimeout(() => {
      heart.remove();
    }, 3000);
  }, 200);
});
</script>

</body>
</html>
