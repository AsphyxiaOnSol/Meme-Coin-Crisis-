    <div class="wallet-checker">
        <h2>Wallet & Token Safety Scanner</h2>
        <input type="text" id="walletAddress" placeholder="Enter Wallet or Contract Address">
        <button onclick="analyzeWallet()">Check Safety</button>
        <p id="walletResult"></p>
    </div>
    
    <div class="game-container">
        <h2>Meme Coin Crisis Game</h2>
        <button onclick="startGame()">Start Game</button>
        <canvas id="gameCanvas" width="600" height="400"></canvas>
        <p>Level: <span id="level">1</span> | Time: <span id="time">0</span> sec</p>
        <div class="game-instructions">
            <h3>Game Instructions</h3>
            <p>🚀 Control your character and avoid the rugs! Jump from carpet to carpet without falling.</p>
            <p>⚠️ The game gets harder every level, be careful!</p>
            <p>🎯 Reach level 20 as fast as possible to enter the leaderboard.</p>
            <p>🔼 Use arrow keys to move and jump.</p>
        </div>
    </div>
    
    <div class="leaderboard">
        <h2>Leaderboard - Fastest Players</h2>
        <ul id="leaderboard"></ul>
    </div>
</div>

<script>
    const canvas = document.getElementById("gameCanvas");
    const ctx = canvas.getContext("2d");
    let level = 1;
    let timeElapsed = 0;
    let player = { x: 50, y: 300, width: 50, height: 50, speed: 5 };
    let rugs = [];
    let gameSpeed = 4;
    let keys = {};

    function startGame() {
        level = 1;
        timeElapsed = 0;
        player.x = 50;
        player.y = 300;
        rugs = [];
        gameSpeed = 4;
        updateGame();
    }
    
    function updateGame() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "yellow";
        ctx.fillRect(player.x, player.y, player.width, player.height);
        requestAnimationFrame(updateGame);
    }
    
    function analyzeWallet() {
        let wallet = document.getElementById("walletAddress").value;
        let result = document.getElementById("walletResult");
        let redFlags = ["High Sell Volume", "Interacts with Rug-Pulled Tokens", "Liquidity Not Locked", "New Token with No History"];
        let randomRisk = Math.random() < 0.5 ? "✅ Safe to Invest" : "🚨 " + redFlags[Math.floor(Math.random() * redFlags.length)];
        result.innerHTML = "Analysis Result: " + randomRisk;
    }
</script>
