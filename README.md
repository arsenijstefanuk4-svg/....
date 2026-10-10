<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Миньон и Серверная Хатка</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Fredoka+One&family=Montserrat:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Montserrat', sans-serif;
            overflow: hidden;
            background: #1a1a2e;
            user-select: none;
        }
        .title-font {
            font-family: 'Fredoka One', cursive;
        }
        @keyframes shake {
            0% { transform: translate(1px, 1px) rotate(0deg); }
            20% { transform: translate(-3px, 0px) rotate(1deg); }
            40% { transform: translate(1px, -1px) rotate(-1deg); }
            60% { transform: translate(-3px, 1px) rotate(0deg); }
            80% { transform: translate(2px, -2px) rotate(1deg); }
            100% { transform: translate(1px, -2px) rotate(-1deg); }
        }
        .shake-screen {
            animation: shake 0.5s cubic-bezier(.36,.07,.19,.97) both;
        }
        @keyframes pulse-glow {
            0%, 100% { box-shadow: 0 0 15px rgba(239, 68, 68, 0.6); }
            50% { box-shadow: 0 0 30px rgba(239, 68, 68, 0.9), 0 0 50px rgba(220, 38, 38, 0.5); }
        }
        .btn-launch {
            animation: pulse-glow 2s infinite;
        }
    </style>
</head>
<body class="w-screen h-screen flex flex-col justify-between relative bg-gradient-to-b from-slate-900 via-indigo-950 to-slate-900">

    <header class="w-full py-4 text-center z-20 bg-black/30 backdrop-blur-md border-b border-white/10">
        <h1 class="title-font text-3xl md:text-5xl text-amber-400 tracking-wider drop-shadow-[0_4px_4px_rgba(0,0,0,0.8)]">
            МИНИОН И СЕРВЕРНАЯ КАТАСТРОФА
        </h1>
        <p class="text-slate-300 text-sm md:text-base mt-1 font-medium">
            Он опять уронил онлайн сервера! Наказание неизбежно! 🚀🔥
        </p>
    </header>

    <main id="stage" class="relative flex-1 w-full h-full overflow-hidden flex items-center justify-center">
        
        <!-- Background Decor Grid & Lights -->
        <div class="absolute inset-0 opacity-25 bg-[radial-gradient(#4f46e5_1px,transparent_1px)] [background-size:24px_24px] pointer-events-none"></div>

        <!-- Canvas for animations (Missiles & Explosions) -->
        <canvas id="gameCanvas" class="absolute inset-0 w-full h-full pointer-events-none z-10"></canvas>

        <!-- Environment Container (Minion & Server Shack) -->
        <div id="sceneContainer" class="relative z-0 flex flex-col items-center justify-end h-[400px] w-[500px]">
            
            <!-- Server Shack (Хатка-Серверная) -->
            <div id="serverShack" class="relative w-64 h-72 bg-slate-800 border-4 border-slate-700 rounded-2xl shadow-2xl flex flex-col items-center p-4 transition-all duration-300">
                <!-- Roof -->
                <div class="absolute -top-12 w-72 h-16 bg-red-600 rounded-t-xl border-4 border-red-700 shadow-lg flex items-center justify-center">
                    <span class="text-xs font-bold text-white tracking-widest uppercase bg-black/40 px-3 py-1 rounded-full">Server Rack v2.0</span>
                </div>
                
                <!-- Server Lights & Blinkers -->
                <div class="mt-4 w-full flex-1 bg-slate-950 rounded-xl p-3 border-2 border-slate-700 flex flex-col justify-around">
                    <div class="flex items-center justify-between bg-slate-900 p-2 rounded border border-slate-800">
                        <span class="text-[10px] text-slate-400 font-mono">CORE_ONLINE</span>
                        <div class="w-3 h-3 rounded-full bg-emerald-500 animate-ping"></div>
                    </div>
                    <div class="flex items-center justify-between bg-slate-900 p-2 rounded border border-slate-800">
                        <span class="text-[10px] text-slate-400 font-mono">PLAYERS_LOAD</span>
                        <div class="w-3 h-3 rounded-full bg-amber-500"></div>
                    </div>
                    <div class="flex items-center justify-between bg-slate-900 p-2 rounded border border-slate-800">
                        <span class="text-[10px] text-slate-400 font-mono">PING_STATUS</span>
                        <div class="w-3 h-3 rounded-full bg-red-500"></div>
                    </div>
                </div>

                <!-- Door / Cable ports -->
                <div class="w-16 h-12 bg-slate-900 rounded-t-lg mt-2 border-t-2 border-slate-700"></div>
            </div>

            <!-- Minion (Миньон) -->
            <div id="minion" class="absolute bottom-2 -left-20 w-32 h-44 flex flex-col items-center transition-all duration-300">
                <!-- Minion Goggles & Face -->
                <div class="relative w-28 h-36 bg-yellow-400 rounded-full border-4 border-yellow-500 shadow-xl flex flex-col items-center pt-6">
                    <!-- Goggles -->
                    <div class="flex items-center justify-center space-x-1 bg-slate-300 p-1.5 rounded-full border-2 border-slate-400 shadow-inner">
                        <div class="w-9 h-9 bg-white rounded-full border-2 border-slate-600 flex items-center justify-center overflow-hidden">
                            <div class="w-3 h-3 bg-amber-800 rounded-full flex items-center justify-center">
                                <div class="w-1 h-1 bg-black rounded-full"></div>
                            </div>
                        </div>
                    </div>
                    <!-- Smile -->
                    <div class="mt-4 w-10 h-4 border-b-4 border-slate-900 rounded-full"></div>
                    <!-- Overalls logo -->
                    <div class="mt-3 w-8 h-6 bg-blue-600 rounded border border-blue-700 flex items-center justify-center">
                        <span class="text-[8px] font-bold text-white">M</span>
                    </div>
                </div>
                <!-- Minion Legs & Boots -->
                <div class="flex space-x-4 -mt-2">
                    <div class="w-4 h-6 bg-blue-600 rounded-b"></div>
                    <div class="w-4 h-6 bg-blue-600 rounded-b"></div>
                </div>
            </div>

        </div>

        <!-- Status / Message Overlay -->
        <div id="messageBox" class="absolute top-10 z-30 opacity-0 transform -translate-y-10 transition-all duration-500 pointer-events-none bg-red-600/90 border-4 border-yellow-400 text-white px-8 py-4 rounded-3xl shadow-2xl text-center">
            <h2 id="msgTitle" class="title-font text-2xl md:text-3xl tracking-wide text-yellow-300">БЭХ! СЕРВЕР УНИЧТОЖЕН!</h2>
            <p id="msgText" class="text-sm md:text-base font-semibold mt-1">Миньон сломал пинг на 9999ms! Онлайн упал до нуля!</p>
        </div>

    </main>

    <footer class="w-full py-6 z-20 bg-black/40 backdrop-blur-md border-t border-white/10 flex flex-col items-center justify-center">
        <button id="launchBtn" onclick="launchMissiles()" class="btn-launch group relative inline-flex items-center justify-center px-8 py-4 text-lg font-bold text-white transition-all bg-gradient-to-r from-red-600 via-orange-600 to-amber-600 rounded-2xl hover:scale-105 active:scale-95 shadow-xl border-2 border-yellow-400 cursor-pointer">
            <span class="absolute inset-0 w-full h-full rounded-2xl bg-white/20 opacity-0 group-hover:opacity-100 transition-opacity"></span>
            <svg class="w-6 h-6 mr-3 animate-bounce" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>
            <span>ОТПРАВИТЬ РАКЕТЫ!</span>
        </button>
        <p class="text-xs text-slate-400 mt-2">Нажмите кнопку, чтобы восстановить справедливость в дата-центре</p>
    </footer>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const stage = document.getElementById('stage');
        const messageBox = document.getElementById('messageBox');
        const msgTitle = document.getElementById('msgTitle');
        const msgText = document.getElementById('msgText');
        const serverShack = document.getElementById('serverShack');
        const minion = document.getElementById('minion');
        const launchBtn = document.getElementById('launchBtn');

        let width, height;
        function resizeCanvas() {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        let missiles = [];
        let particles = [];
        let isAnimating = false;

        const messages = [
            { title: "БАХ! СЕРВЕР УШЕЛ В КАТАКОМБЫ!", text: "Миньон случайно пролил сок на главный коммутатор!" },
            { title: "КАБУМ! ОНЛАЙН ОБНУЛЕН!", text: "Пинг подскочил до 9999ms, хостинг плачет!" },
            { title: "УУУПС! БАЗА ДАННЫХ УЛЕТЕЛА!", text: "Миньон нажал не ту кнопку и снес весь кластер!" },
            { title: "ЭПИЧЕСКИЙ БАХ!", text: "Серверная стойка превратилась в пепел от бананового взрыва!" }
        ];

        class Missile {
            constructor(startX, startY, targetX, targetY) {
                this.x = startX;
                this.y = startY;
                this.targetX = targetX;
                this.targetY = targetY;
                
                const angle = Math.atan2(targetY - startY, targetX - startX);
                const speed = 12;
                this.vx = Math.cos(angle) * speed;
                this.vy = Math.sin(angle) * speed;
                this.active = true;
            }

            update() {
                this.x += this.vx;
                this.y += this.vy;

                // Trail particles
                particles.push(new Particle(this.x, this.y, '#f97316', true));

                // Check collision with target area
                const dist = Math.hypot(this.targetX - this.x, this.targetY - this.y);
                if (dist < 15) {
                    this.active = false;
                    createExplosion(this.targetX, this.targetY);
                }
            }

            draw() {
                ctx.save();
                ctx.translate(this.x, this.y);
                ctx.rotate(Math.atan2(this.vy, this.vx) + Math.PI / 2);
                
                // Rocket body
                ctx.fillStyle = '#e2e8f0';
                ctx.beginPath();
                ctx.moveTo(0, -12);
                ctx.lineTo(-5, 8);
                ctx.lineTo(5, 8);
                ctx.closePath();
                ctx.fill();

                // Rocket tip
                ctx.fillStyle = '#ef4444';
                ctx.beginPath();
                ctx.moveTo(0, -16);
                ctx.lineTo(-5, -10);
                ctx.lineTo(5, -10);
                ctx.closePath();
                ctx.fill();

                ctx.restore();
            }
        }

        class Particle {
            constructor(x, y, color, isTrail = false) {
                this.x = x;
                this.y = y;
                this.color = color;
                this.isTrail = isTrail;
                
                if (isTrail) {
                    this.vx = (Math.random() - 0.5) * 2;
                    this.vy = (Math.random() - 0.5) * 2;
                    this.radius = Math.random() * 3 + 1;
                    this.life = 20;
                } else {
                    const angle = Math.random() * Math.PI * 2;
                    const speed = Math.random() * 8 + 2;
                    this.vx = Math.cos(angle) * speed;
                    this.vy = Math.sin(angle) * speed;
                    this.radius = Math.random() * 6 + 2;
                    this.life = 50;
                }
            }

            update() {
                this.x += this.vx;
                this.y += this.vy;
                this.life--;
            }

            draw() {
                ctx.save();
                ctx.globalAlpha = Math.max(0, this.life / 50);
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.fill();
                ctx.restore();
            }
        }

        function createExplosion(x, y) {
            // Spawn explosion particles
            const colors = ['#ef4444', '#f97316', '#eab308', '#ffffff'];
            for (let i = 0; i < 60; i++) {
                particles.push(new Particle(x, y, colors[Math.floor(Math.random() * colors.length)]));
            }

            // Screen shake effect
            stage.classList.add('shake-screen');
            setTimeout(() => {
                stage.classList.remove('shake-screen');
            }, 500);

            // Damage reaction on minion and shack
            serverShack.style.transform = `translate(${(Math.random()-0.5)*20}px, ${(Math.random()-0.5)*20}px) rotate(${(Math.random()-0.5)*10}deg)`;
            minion.style.transform = `translate(${(Math.random()-0.5)*30}px, ${(Math.random()-0.5)*30}px) rotate(${(Math.random()-0.5)*20}deg)`;

            setTimeout(() => {
                serverShack.style.transform = 'none';
                minion.style.transform = 'none';
            }, 600);

            // Show funny message
            showRandomMessage();
        }

        function showRandomMessage() {
            const msg = messages[Math.floor(Math.random() * messages.length)];
            msgTitle.innerText = msg.title;
            msgText.innerText = msg.text;

            messageBox.style.opacity = '1';
            messageBox.style.transform = 'translateY(0)';

            setTimeout(() => {
                messageBox.style.opacity = '0';
                messageBox.style.transform = 'translateY(-40px)';
            }, 3500);
        }

        function launchMissiles() {
            if (isAnimating) return;
            isAnimating = true;
            launchBtn.disabled = true;
            launchBtn.classList.add('opacity-50', 'cursor-not-allowed');

            const rect = serverShack.getBoundingClientRect();
            const targetX = rect.left + rect.width / 2;
            const targetY = rect.top + rect.height / 2;

            // Launch 3 missiles from bottom corners and center
            const startPositions = [
                { x: width * 0.2, y: height + 50 },
                { x: width * 0.5, y: height + 50 },
                { x: width * 0.8, y: height + 50 }
            ];

            startPositions.forEach((pos, index) => {
                setTimeout(() => {
                    missiles.push(new Missile(pos.x, pos.y, targetX + (index - 1) * 30, targetY + (index - 1) * 20));
                }, index * 250);
            });

            // Re-enable button after sequence completes
            setTimeout(() => {
                isAnimating = false;
                launchBtn.disabled = false;
                launchBtn.classList.remove('opacity-50', 'cursor-not-allowed');
            }, 2500);
        }

        // Main game animation loop
        function animate() {
            ctx.clearRect(0, 0, width, height);

            // Update and draw missiles
            missiles.forEach((m, index) => {
                m.update();
                m.draw();
                if (!m.active) {
                    missiles.splice(index, 1);
                }
            });

            // Update and draw particles
            particles.forEach((p, index) => {
                p.update();
                p.draw();
                if (p.life <= 0) {
                    particles.splice(index, 1);
                }
            });

            requestAnimationFrame(animate);
        }

        animate();
    </script>
</body>
</html>
