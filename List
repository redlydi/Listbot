<!DOCTYPE html><html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Листбот</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(180deg, #146b3a, #1c8c4c);
      font-family: 'Segoe UI', sans-serif;
      color: #fff;
      overflow: hidden;
    }.top-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 20px;
}

.profile-btn, .leaf-counter-box {
  background: rgba(255, 255, 255, 0.1);
  padding: 10px 15px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.leaf-counter-box img {
  width: 24px;
  height: 24px;
}

.main-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: calc(100vh - 120px);
}

#main-leaf {
  width: 160px;
  height: 160px;
  background-image: url('clean_leaf.png');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  cursor: pointer;
  transition: transform 0.1s ease;
}

#main-leaf:active {
  transform: scale(0.9);
}

.status-text {
  margin-top: 20px;
  font-size: 20px;
  font-weight: 500;
}

.buttons {
  display: flex;
  gap: 15px;
  margin-top: 30px;
}

.btn {
  background: rgba(255, 255, 255, 0.1);
  padding: 10px 20px;
  border-radius: 12px;
  font-size: 16px;
  color: #fff;
  cursor: pointer;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.bottom-nav {
  position: absolute;
  bottom: 0;
  width: 100%;
  display: flex;
  justify-content: space-around;
  background: rgba(0, 0, 0, 0.1);
  padding: 10px 0;
  backdrop-filter: blur(5px);
}

.bottom-nav div {
  text-align: center;
  font-size: 14px;
  color: #fff;
}

  </style>
</head>
<body>
  <div class="top-bar">
    <div class="profile-btn">Профиль &raquo;</div>
    <div class="leaf-counter-box">
      <img src="clean_leaf.png" alt="leaf" />
      <div id="leaf-count">0</div>
    </div>
  </div>  <div class="main-content">
    <div id="main-leaf" onclick="tapLeaf()"></div>
    <div class="status-text">Вы здоровы</div>
    <div class="buttons">
      <div class="btn">ЗАДАНИЯ &raquo;</div>
      <div class="btn">ЛИДЕРЫ &raquo;</div>
    </div>
  </div>  <div class="bottom-nav">
    <div>Главная</div>
    <div>Задания</div>
    <div>Рулетка</div>
    <div>Магазин</div>
    <div>История</div>
  </div>  <script>
    let count = 0;

    function tapLeaf() {
      count++;
      document.getElementById("leaf-count").innerText = count.toLocaleString('ru-RU');
    }
  </script></body>
</html>
