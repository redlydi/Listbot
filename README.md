<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>🌿 Листок Tap</title>
  <style>
    body {
      margin: 0;
      background: radial-gradient(ellipse at center, #0a0a0a 0%, #050505 100%);
      font-family: 'Segoe UI', sans-serif;
      overflow: hidden;
    }

    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      position: relative;
    }

    #main-leaf {
      width: 160px;
      height: 160px;
      background-image: url('https://i.pinimg.com/originals/09/d0/f9/09d0f9d02df7681950a6ce98e9794910.jpg');
      background-size: cover;
      background-position: center;
      border-radius: 50%;
      box-shadow: 0 0 40px #44cc44;
      cursor: pointer;
      transition: transform 0.1s ease;
    }

    #main-leaf:active {
      transform: scale(0.93);
    }

    #leaf-counter {
      position: absolute;
      top: 20px;
      right: 20px;
      display: flex;
      flex-wrap: wrap;
      width: 120px;
      min-height: 40px;
      gap: 6px;
    }

    .small-leaf {
      width: 20px;
      height: 20px;
      background-image: url('https://i.pinimg.com/originals/09/d0/f9/09d0f9d02df7681950a6ce98e9794910.jpg');
      background-size: cover;
      background-position: center;
      border-radius: 5px;
      animation: fadeIn 0.3s ease;
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: scale(0.7);
      }
      to {
        opacity: 1;
        transform: scale(1);
      }
    }

    h1 {
      color: #55ff55;
      text-shadow: 0 0 15px #33aa33;
      margin-bottom: 40px;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>🌿 Нажми на лист</h1>

    <div id="main-leaf" onclick="tapLeaf()"></div>

    <div id="leaf-counter"></div>
  </div>

  <script>
    function tapLeaf() {
      const leafCounter = document.getElementById("leaf-counter");
      const smallLeaf = document.createElement("div");
      smallLeaf.classList.add("small-leaf");
      leafCounter.appendChild(smallLeaf);
    }
  </script>

