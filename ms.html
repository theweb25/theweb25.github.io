<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Modern Minesweeper</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&display=swap');

        body {
            font-family: 'JetBrains Mono', monospace;
            touch-action: manipulation; /* Improves touch response */
        }

        /* Prevent highlighting text when spam clicking */
        .no-select {
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
        }

        /* Custom scrollbar for the board container */
        .board-scroll::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        .board-scroll::-webkit-scrollbar-track {
            background: #1f2937;
        }
        .board-scroll::-webkit-scrollbar-thumb {
            background: #4b5563;
            border-radius: 4px;
        }

        /* Grid Cell Animations */
        .cell {
            transition: background-color 0.1s ease, transform 0.1s ease;
        }
        .cell:active {
            transform: scale(0.95);
        }
        .cell.revealed {
            animation: popIn 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        @keyframes popIn {
            0% { transform: scale(0.5); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        /* Number Colors */
        .num-1 { color: #60a5fa; } /* Blue */
        .num-2 { color: #4ade80; } /* Green */
        .num-3 { color: #f87171; } /* Red */
        .num-4 { color: #a78bfa; } /* Purple */
        .num-5 { color: #facc15; } /* Yellow */
        .num-6 { color: #2dd4bf; } /* Teal */
        .num-7 { color: #e879f9; } /* Pink */
        .num-8 { color: #9ca3af; } /* Gray */

        /* Flag Mode Toggle Switch */
        .toggle-checkbox:checked {
            right: 0;
            border-color: #ef4444;
        }
        .toggle-checkbox:checked + .toggle-label {
            background-color: #ef4444;
        }
    </style>
</head>
<body class="bg-gray-900 text-gray-100 min-h-screen flex flex-col items-center justify-center p-4">

    <!-- Header / Stats -->
    <div class="w-full max-w-2xl mb-4 flex flex-col gap-4">
        <div class="flex justify-between items-center bg-gray-800 p-4 rounded-xl shadow-lg border border-gray-700">
            <!-- Mines Left -->
            <div class="flex items-center gap-2">
                <div class="text-red-400">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 21v-8a2 2 0 012-2h14a2 2 0 012 2v8M12 3v18M12 3a9 9 0 00-9 9m9-9a9 9 0 009 9" />
                    </svg>
                </div>
                <span id="mine-count" class="text-2xl font-bold font-mono">010</span>
            </div>

            <!-- Face / Reset -->
            <button onclick="initGame()" id="reset-btn" class="text-3xl hover:scale-110 transition-transform active:scale-95 focus:outline-none">
                🙂
            </button>

            <!-- Timer -->
            <div class="flex items-center gap-2">
                <div class="text-blue-400">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                    </svg>
                </div>
                <span id="timer" class="text-2xl font-bold font-mono">000</span>
            </div>
        </div>

        <!-- Controls -->
        <div class="flex flex-wrap justify-between gap-2">
            <!-- Difficulty -->
            <div class="flex bg-gray-800 rounded-lg p-1 border border-gray-700">
                <button onclick="setDifficulty('easy')" class="px-3 py-1 rounded hover:bg-gray-700 text-sm transition-colors diff-btn active" id="btn-easy">Easy</button>
                <button onclick="setDifficulty('medium')" class="px-3 py-1 rounded hover:bg-gray-700 text-sm transition-colors diff-btn" id="btn-medium">Med</button>
                <button onclick="setDifficulty('hard')" class="px-3 py-1 rounded hover:bg-gray-700 text-sm transition-colors diff-btn" id="btn-hard">Hard</button>
            </div>

            <!-- Mobile Flag Toggle -->
            <button id="mode-toggle" class="flex items-center gap-2 bg-gray-800 border border-gray-700 px-4 py-1 rounded-lg hover:bg-gray-750 transition-colors md:hidden" onclick="toggleMode()">
                <span class="text-sm">Tap to:</span>
                <span id="mode-icon" class="text-blue-400 font-bold">DIG ⛏️</span>
            </button>
        </div>
    </div>

    <!-- Game Board -->
    <div class="bg-gray-800 p-2 md:p-4 rounded-xl shadow-2xl border border-gray-700 overflow-auto max-w-[95vw] max-h-[70vh] board-scroll relative">
        <div id="game-grid" class="grid gap-1 mx-auto no-select">
            <!-- Grid generated by JS -->
        </div>
        
        <!-- Game Over Overlay -->
        <div id="overlay" class="hidden absolute inset-0 bg-black/60 backdrop-blur-sm flex flex-col items-center justify-center z-10 rounded-xl">
            <h2 id="overlay-title" class="text-4xl font-bold mb-4 text-white drop-shadow-lg">Game Over</h2>
            <p id="overlay-msg" class="text-gray-300 mb-6">Better luck next time!</p>
            <button onclick="initGame()" class="bg-blue-600 hover:bg-blue-500 text-white font-bold py-2 px-6 rounded-full shadow-lg transform transition hover:scale-105">
                Play Again
            </button>
        </div>
    </div>

    <!-- Instructions -->
    <div class="mt-6 text-gray-500 text-xs text-center">
        <p class="hidden md:block">Left Click: Reveal • Right Click: Flag</p>
        <p class="md:hidden">Tap: Reveal/Flag (Toggle above) • Long Press: Flag</p>
    </div>

    <script>
        // --- Game Config & State ---
        const difficulties = {
            easy: { rows: 9, cols: 9, mines: 10 },
            medium: { rows: 16, cols: 16, mines: 40 },
            hard: { rows: 16, cols: 30, mines: 99 }
        };

        let currentDiff = 'easy';
        let grid = [];
        let gameActive = false;
        let flags = 0;
        let time = 0;
        let timerInterval = null;
        let isFirstClick = true;
        let touchMode = 'dig'; // 'dig' or 'flag'
        let longPressTimer;

        // --- DOM Elements ---
        const gridEl = document.getElementById('game-grid');
        const mineCountEl = document.getElementById('mine-count');
        const timerEl = document.getElementById('timer');
        const resetBtn = document.getElementById('reset-btn');
        const overlay = document.getElementById('overlay');
        const overlayTitle = document.getElementById('overlay-title');
        const overlayMsg = document.getElementById('overlay-msg');
        const modeToggleBtn = document.getElementById('mode-toggle');
        const modeIcon = document.getElementById('mode-icon');

        // --- Init ---
        function setDifficulty(diff) {
            currentDiff = diff;
            // Update UI buttons
            document.querySelectorAll('.diff-btn').forEach(b => {
                b.classList.remove('bg-gray-600', 'text-white');
                b.classList.add('text-gray-400');
            });
            const activeBtn = document.getElementById(`btn-${diff}`);
            activeBtn.classList.add('bg-gray-600', 'text-white');
            activeBtn.classList.remove('text-gray-400');
            
            initGame();
        }

        function initGame() {
            // Reset State
            gameActive = true;
            isFirstClick = true;
            flags = 0;
            time = 0;
            grid = [];
            clearInterval(timerInterval);
            timerInterval = null;
            
            // Reset UI
            timerEl.innerText = "000";
            resetBtn.innerText = "🙂";
            overlay.classList.add('hidden');
            
            const config = difficulties[currentDiff];
            mineCountEl.innerText = String(config.mines).padStart(3, '0');

            // Setup Grid Style
            gridEl.style.gridTemplateColumns = `repeat(${config.cols}, minmax(0, 1fr))`;
            
            // Render Board
            renderBoard(config.rows, config.cols);
        }

        function renderBoard(rows, cols) {
            gridEl.innerHTML = '';
            
            // Calculate responsive cell size
            // Default (Easy): Large cells
            let cellSizeClass = "w-8 h-8 md:w-10 md:h-10 text-lg";

            if (currentDiff === 'medium') {
                // Medium: Slightly smaller
                cellSizeClass = "w-6 h-6 md:w-8 md:h-8 text-base";
            } else if (currentDiff === 'hard') {
                // Hard: Smallest to fit more on screen
                cellSizeClass = "w-5 h-5 md:w-6 md:h-6 text-xs md:text-sm";
            }

            for (let r = 0; r < rows; r++) {
                const row = [];
                for (let c = 0; c < cols; c++) {
                    const cellData = {
                        r, c,
                        isMine: false,
                        isRevealed: false,
                        isFlagged: false,
                        neighborCount: 0
                    };
                    row.push(cellData);

                    const cellEl = document.createElement('div');
                    cellEl.className = `${cellSizeClass} bg-gray-600 rounded cursor-pointer flex items-center justify-center font-bold shadow-sm cell hover:bg-gray-500 transition-colors`;
                    cellEl.dataset.r = r;
                    cellEl.dataset.c = c;
                    
                    // Event Listeners
                    cellEl.addEventListener('click', () => handleClick(r, c));
                    cellEl.addEventListener('contextmenu', (e) => {
                        e.preventDefault();
                        toggleFlag(r, c);
                    });

                    // Mobile Long Press Support
                    cellEl.addEventListener('touchstart', (e) => {
                        longPressTimer = setTimeout(() => {
                            if(navigator.vibrate) navigator.vibrate(50);
                            toggleFlag(r, c);
                        }, 500); 
                    }, {passive: true});

                    cellEl.addEventListener('touchend', () => {
                        clearTimeout(longPressTimer);
                    });
                    
                    cellEl.addEventListener('touchmove', () => {
                        clearTimeout(longPressTimer);
                    });

                    gridEl.appendChild(cellEl);
                    cellData.element = cellEl;
                }
                grid.push(row);
            }
        }

        // --- Core Logic ---

        function toggleMode() {
            touchMode = touchMode === 'dig' ? 'flag' : 'dig';
            if (touchMode === 'flag') {
                modeIcon.innerText = "FLAG 🚩";
                modeIcon.className = "text-red-400 font-bold";
                modeToggleBtn.classList.add('border-red-500');
            } else {
                modeIcon.innerText = "DIG ⛏️";
                modeIcon.className = "text-blue-400 font-bold";
                modeToggleBtn.classList.remove('border-red-500');
            }
        }

        function handleClick(r, c) {
            if (!gameActive) return;

            // Handle Mobile Flag Mode
            if (touchMode === 'flag') {
                toggleFlag(r, c);
                return;
            }

            const cell = grid[r][c];
            if (cell.isFlagged) return; // Can't click flagged cells
            
            // First Click Logic (Safe Start)
            if (isFirstClick) {
                startTimer();
                generateMines(r, c);
                isFirstClick = false;
            }

            revealCell(r, c);
        }

        function toggleFlag(r, c) {
            if (!gameActive || isFirstClick) return; // Don't flag before starting or if game over
            const cell = grid[r][c];
            if (cell.isRevealed) return;

            cell.isFlagged = !cell.isFlagged;
            
            // Update UI
            if (cell.isFlagged) {
                cell.element.innerHTML = `<span class="text-red-500 text-sm md:text-base">🚩</span>`;
                flags++;
            } else {
                cell.element.innerHTML = '';
                flags--;
            }

            const config = difficulties[currentDiff];
            mineCountEl.innerText = String(Math.max(0, config.mines - flags)).padStart(3, '0');
        }

        function generateMines(safeR, safeC) {
            const config = difficulties[currentDiff];
            let minesPlaced = 0;
            
            while (minesPlaced < config.mines) {
                const r = Math.floor(Math.random() * config.rows);
                const c = Math.floor(Math.random() * config.cols);

                // Prevent mine on safe spot and its neighbors
                if (Math.abs(r - safeR) <= 1 && Math.abs(c - safeC) <= 1) continue;
                
                if (!grid[r][c].isMine) {
                    grid[r][c].isMine = true;
                    minesPlaced++;
                }
            }

            // Calculate numbers
            for (let r = 0; r < config.rows; r++) {
                for (let c = 0; c < config.cols; c++) {
                    if (!grid[r][c].isMine) {
                        grid[r][c].neighborCount = countNeighbors(r, c);
                    }
                }
            }
        }

        function countNeighbors(r, c) {
            let count = 0;
            const config = difficulties[currentDiff];
            for (let i = -1; i <= 1; i++) {
                for (let j = -1; j <= 1; j++) {
                    const nr = r + i;
                    const nc = c + j;
                    if (nr >= 0 && nr < config.rows && nc >= 0 && nc < config.cols) {
                        if (grid[nr][nc].isMine) count++;
                    }
                }
            }
            return count;
        }

        function revealCell(r, c) {
            const config = difficulties[currentDiff];
            // Bounds check
            if (r < 0 || r >= config.rows || c < 0 || c >= config.cols) return;
            
            const cell = grid[r][c];
            if (cell.isRevealed || cell.isFlagged) return;

            cell.isRevealed = true;
            cell.element.classList.add('revealed');
            cell.element.classList.remove('bg-gray-600', 'hover:bg-gray-500', 'cursor-pointer', 'shadow-sm');
            cell.element.classList.add('bg-gray-800', 'border', 'border-gray-700', 'cursor-default');

            if (cell.isMine) {
                gameOver(false);
                cell.element.classList.add('bg-red-500'); // Highlight the killer mine
                cell.element.innerHTML = "💣";
                return;
            }

            if (cell.neighborCount > 0) {
                cell.element.innerHTML = cell.neighborCount;
                cell.element.classList.add(`num-${cell.neighborCount}`);
            } else {
                // Flood Fill
                for (let i = -1; i <= 1; i++) {
                    for (let j = -1; j <= 1; j++) {
                        revealCell(r + i, c + j);
                    }
                }
            }

            checkWin();
        }

        function revealAllMines(won) {
            const config = difficulties[currentDiff];
            for (let r = 0; r < config.rows; r++) {
                for (let c = 0; c < config.cols; c++) {
                    const cell = grid[r][c];
                    if (cell.isMine) {
                        if (won) {
                            cell.element.innerHTML = "🚩";
                            cell.element.classList.add('text-green-500');
                        } else if (!cell.isRevealed) {
                            // Don't overwrite the red killer mine
                            cell.element.innerHTML = "💣";
                        }
                    } else if (cell.isFlagged && !cell.isMine) {
                        // Wrong flag
                        cell.element.innerHTML = "❌";
                    }
                }
            }
        }

        function checkWin() {
            const config = difficulties[currentDiff];
            let revealedCount = 0;
            
            for (let r = 0; r < config.rows; r++) {
                for (let c = 0; c < config.cols; c++) {
                    if (grid[r][c].isRevealed) revealedCount++;
                }
            }

            const totalCells = config.rows * config.cols;
            if (revealedCount === totalCells - config.mines) {
                gameOver(true);
            }
        }

        function gameOver(won) {
            gameActive = false;
            clearInterval(timerInterval);
            
            if (won) {
                resetBtn.innerText = "😎";
                overlayTitle.innerText = "You Won!";
                overlayTitle.className = "text-4xl font-bold mb-4 text-green-400 drop-shadow-lg";
                overlayMsg.innerText = `Time: ${time}s`;
                revealAllMines(true);
            } else {
                resetBtn.innerText = "😵";
                overlayTitle.innerText = "Game Over";
                overlayTitle.className = "text-4xl font-bold mb-4 text-red-400 drop-shadow-lg";
                overlayMsg.innerText = "Don't give up!";
                revealAllMines(false);
            }
            
            // Show overlay with a slight delay so user sees what happened
            setTimeout(() => {
                overlay.classList.remove('hidden');
            }, 1000);
        }

        function startTimer() {
            timerInterval = setInterval(() => {
                time++;
                timerEl.innerText = String(time).padStart(3, '0');
            }, 1000);
        }

        // Initialize default
        setDifficulty('easy');

    </script>
</body>
</html>


