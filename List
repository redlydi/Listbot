<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LeafCoin Clicker</title>
    <style>
        /* Общие стили */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(to bottom, #1A3C34, #4CAF50);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: Arial, sans-serif;
            color: white;
            overflow: hidden;
        }

        #game {
            width: 375px;
            height: 667px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 20px;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            position: relative;
        }

        /* Шапка с монетами */
        #header {
            padding: 15px;
            text-align: center;
            background: rgba(0, 0, 0, 0.5);
        }

        #coin-counter {
            font-size: 28px;
            font-weight: bold;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }

        /* Контент вкладок */
        #tab-content {
            flex: 1;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        /* Кликер */
        #tab-clicker {
            text-align: center;
        }

        #leaf {
            width: 200px;
            height: 200px;
            cursor: pointer;
            transition: transform 0.1s ease;
        }

        #leaf.clicked {
            transform: scale(1.1) rotate(5deg);
        }

        #clicker-text {
            margin-top: 20px;
            font-size: 24px;
            font-weight: bold;
        }

        #clicker-subtext {
            font-size: 16px;
            margin-top: 5px;
            opacity: 0.9;
        }

        /* Магазин */
        #tab-shop {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100%;
        }

        .shop-button {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: none;
            padding: 15px 30px;
            margin: 10px 0;
            border-radius: 10px;
            font-size: 16px;
            cursor: pointer;
            transition: background 0.3s, transform 0.1s;
            width: 80%;
            text-align: left;
        }

        .shop-button:hover:not(:disabled) {
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.02);
        }

        .shop-button:disabled {
            background: rgba(255, 255, 255, 0.1);
            cursor: not-allowed;
            opacity: 0.6;
        }

        /* Рулетка */
        #tab-roulette {
            text-align: center;
        }

        #roulette-message {
            font-size: 18px;
            margin-bottom: 20px;
        }

        #spin-button {
            background: #FFD700;
            color: #1A3C34;
            border: none;
            padding: 15px 40px;
            border-radius: 10px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s, background 0.3s;
        }

        #spin-button:hover:not(:disabled) {
            background: #ffeb3b;
            transform: scale(1.05);
        }

        #spin-button:disabled {
            background: #666;
            color: #999;
            cursor: not-allowed;
        }

        #spin-result {
            margin-top: 20px;
            font-size: 20px;
            font-weight: bold;
            min-height: 60px;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Инвентарь */
        #tab-inventory {
            text-align: center;
        }

        #inventory-items img {
            width: 150px;
            height: 150px;
            margin-top: 20px;
            border: 3px solid #FFD700;
            border-radius: 10px;
        }

        #inventory-items p {
            font-size: 18px;
            margin-top: 20px;
        }

        /* Вкладки */
        #tabs {
            display: flex;
            justify-content: space-around;
            background: rgba(0, 0, 0, 0.7);
            padding: 10px 0;
        }

        .tab {
            flex: 1;
            text-align: center;
            padding: 10px;
            cursor: pointer;
            font-size: 14px;
            position: relative;
            transition: background 0.3s;
        }

        .tab:hover {
            background: rgba(255, 255, 255, 0.1);
        }

        .tab.active {
            background: rgba(255, 255, 255, 0.2);
        }

        .tab.active::before {
            content: '';
            position: absolute;
            top: -5px;
            left: 50%;
            transform: translateX(-50%);
            width: 8px;
            height: 8px;
            background-color: #4CAF50;
            border-radius: 50%;
        }
    </style>
</head>
<body>
    <div id="game">
        <div id="header">
            <div id="coin-counter">0 LeafCoins</div>
        </div>
        <div id="tab-content">
            <!-- Кликер -->
            <div id="tab-clicker">
                <img id="leaf" src="leaf.png" alt="Leaf">
                <div id="clicker-text">Ваше дерево растёт!</div>
                <div id="clicker-subtext">Кликни лист, чтобы заработать LeafCoins</div>
            </div>
            <!-- Магазин -->
            <div id="tab-shop" style="display: none;">
                <button id="buy-auto-clicker" class="shop-button">Автокликер (1,000,000 LeafCoins)</button>
                <button id="buy-booster" class="shop-button">Усилитель клика (2,000,000 LeafCoins)</button>
            </div>
            <!-- Рулетка -->
            <div id="tab-roulette" style="display: none;">
                <div id="roulette-message">Проверь удачу!</div>
                <button id="spin-button">Крутить</button>
                <div id="spin-result"></div>
            </div>
            <!-- Инвентарь -->
            <div id="tab-inventory" style="display: none;">
                <div id="inventory-items"></div>
            </div>
        </div>
        <div id="tabs">
            <div class="tab active" data-tab="clicker">Главная</div>
            <div class="tab" data-tab="shop">Магазин</div>
            <div class="tab" data-tab="roulette">Рулетка</div>
            <div class="tab" data-tab="inventory">Инвентарь</div>
        </div>
    </div>

    <script>
        // Состояние игры
        let coins = 0;
        let multiplier = 1;
        let autoClickRate = 0;
        let hasGoldenPepe = false;
        let lastFreeSpinTime = 0;

        // Элементы DOM
        const coinCounter = document.getElementById('coin-counter');
        const leaf = document.getElementById('leaf');
        const buyAutoClickerBtn = document.getElementById('buy-auto-clicker');
        const buyBoosterBtn = document.getElementById('buy-booster');
        const spinButton = document.getElementById('spin-button');
        const rouletteMessage = document.getElementById('roulette-message');
        const spinResult = document.getElementById('spin-result');
        const inventoryItems = document.getElementById('inventory-items');

        // Загрузка состояния из localStorage
        function loadState() {
            const savedState = JSON.parse(localStorage.getItem('leafCoinClickerState'));
            if (savedState) {
                coins = savedState.coins || 0;
                multiplier = savedState.multiplier || 1;
                autoClickRate = savedState.autoClickRate || 0;
                hasGoldenPepe = savedState.hasGoldenPepe || false;
                lastFreeSpinTime = savedState.lastFreeSpinTime || 0;
            }
            updateUI();
        }

        // Сохранение состояния в localStorage
        function saveState() {
            const state = {
                coins,
                multiplier,
                autoClickRate,
                hasGoldenPepe,
                lastFreeSpinTime
            };
            localStorage.setItem('leafCoinClickerState', JSON.stringify(state));
        }

        // Обновление интерфейса
        function updateUI() {
            coinCounter.textContent = `${Math.floor(coins)} LeafCoins`;
            buyAutoClickerBtn.disabled = autoClickRate > 0 || coins < 1000000;
            buyBoosterBtn.disabled = multiplier > 1 || coins < 2000000;
            if (autoClickRate > 0) buyAutoClickerBtn.textContent = 'Автокликер куплен';
            if (multiplier > 1) buyBoosterBtn.textContent = 'Усилитель куплен';
            updateRoulette();
            updateInventory();
        }

        // Клик по листу
        leaf.addEventListener('click', () => {
            coins += 1 * multiplier;
            leaf.classList.add('clicked');
            setTimeout(() => leaf.classList.remove('clicked'), 100);
            updateUI();
            saveState();
        });

        // Автокликер
        setInterval(() => {
            if (autoClickRate > 0) {
                coins += autoClickRate * multiplier;
                updateUI();
                saveState();
            }
        }, 1000);

        // Переключение вкладок
        document.querySelectorAll('.tab').forEach(tab => {
            tab.addEventListener('click', () => {
                document.querySelectorAll('#tab-content > div').forEach(content => {
                    content.style.display = 'none';
                });
                document.getElementById(`tab-${tab.dataset.tab}`).style.display = 'flex';
                document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
                tab.classList.add('active');
                updateUI();
            });
        });

        // Покупка автокликера
        buyAutoClickerBtn.addEventListener('click', () => {
            if (coins >= 1000000 && autoClickRate === 0) {
                coins -= 1000000;
                autoClickRate = 1;
                updateUI();
                saveState();
            }
        });

        // Покупка усилителя
        buyBoosterBtn.addEventListener('click', () => {
            if (coins >= 2000000 && multiplier === 1) {
                coins -= 2000000;
                multiplier = 4;
                updateUI();
                saveState();
            }
        });

        // Проверка бесплатного спина
        function canSpinForFree() {
            const now = Date.now();
            return now - lastFreeSpinTime >= 24 * 60 * 60 * 1000;
        }

        // Обновление рулетки
        function updateRoulette() {
            if (canSpinForFree()) {
                rouletteMessage.textContent = 'Бесплатный спин доступен!';
                spinButton.disabled = false;
            } else {
                const timeLeft = 24 * 60 * 60 * 1000 - (Date.now() - lastFreeSpinTime);
                const hours = Math.floor(timeLeft / (60 * 60 * 1000));
                const minutes = Math.floor((timeLeft % (60 * 60 * 1000)) / (60 * 1000));
                rouletteMessage.textContent = `Следующий бесплатный спин через ${hours}ч ${minutes}м`;
                spinButton.disabled = coins < 100000;
            }
            if (!canSpinForFree()) {
                spinButton.textContent = 'Крутить (100,000 LeafCoins)';
            } else {
                spinButton.textContent = 'Крутить бесплатно';
            }
        }

        // Логика спина
        spinButton.addEventListener('click', () => {
            if (canSpinForFree() || coins >= 100000) {
                if (!canSpinForFree()) {
                    coins -= 100000;
                } else {
                    lastFreeSpinTime = Date.now();
                }

                spinButton.disabled = true;
                spinResult.textContent = 'Крутим...';
                let spins = 0;
                const spinAnimation = setInterval(() => {
                    spins++;
                    spinResult.textContent = `Крутим... (${spins})`;
                    if (spins >= 10) {
                        clearInterval(spinAnimation);
                        spin();
                    }
                }, 200);
            }
        });

        function spin() {
            const random = Math.floor(Math.random() * 1000000000);
            let reward;
            if (random < 104997000) {
                reward = 0; // Ничего
            } else if (random < 504997000) {
                reward = 10000;
            } else if (random < 754997000) {
                reward = 100000;
            } else if (random < 869997000) {
                reward = 2000;
            } else if (random < 999997000) {
                reward = 500000;
            } else {
                if (!hasGoldenPepe) {
                    hasGoldenPepe = true;
                    reward = 'Золотой Пепе';
                } else {
                    reward = 1000000;
                }
            }

            if (typeof reward === 'number') {
                coins += reward;
                spinResult.textContent = reward === 0 ? 'Увы, ничего!' : `Вы выиграли ${reward} LeafCoins!`;
            } else {
                spinResult.textContent = 'Поздравляем! Вы выиграли Золотого Пепе!';
            }
            updateUI();
            saveState();
            setTimeout(() => spinButton.disabled = false, 1000);
        }

        // Обновление инвентаря
        function updateInventory() {
            if (hasGoldenPepe) {
                inventoryItems.innerHTML = '<img src="golden_pepe.png" alt="Золотой Пепе"><p>Золотой Пепе</p>';
            } else {
                inventoryItems.innerHTML = '<p>Инвентарь пуст</p>';
            }
        }

        // Инициализация
        loadState();
        updateUI();
        setInterval(updateRoulette, 60000); // Обновление таймера каждую минуту
    </script>
</body>
</html>
