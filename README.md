<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Rose Day My Love</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <style>
        body {
            background-color: #fff5f5;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            font-family: 'Georgia', serif;
            text-align: center;
            overflow: hidden;
        }

        .container {
            padding: 20px;
            max-width: 90%;
            z-index: 2;
        }

        h1 {
            color: #d63384;
            font-size: 2.2rem;
            margin-bottom: 15px;
        }

        p {
            color: #4a4a4a;
            font-size: 1.1rem;
            line-height: 1.6;
            margin-bottom: 30px;
        }

        /* The Emoji Styling */
        #rose-emoji {
            display: none;
            font-size: 8rem; /* Makes the emoji large */
            margin: 20px 0;
            animation: popIn 1s cubic-bezier(0.17, 0.67, 0.83, 0.67);
        }

        .btn {
            background-color: #ff4d4d;
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 1.2rem;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(255, 77, 77, 0.4);
            transition: all 0.3s ease;
        }

        .btn:hover {
            transform: scale(1.05);
            background-color: #e60000;
        }

        @keyframes popIn {
            0% { opacity: 0; transform: scale(0.5); }
            100% { opacity: 1; transform: scale(1); }
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Happy Rose Day! 🌹</h1>
        <p>Even though we are miles apart, you are the most beautiful, <br> 
           fragrant rose in the garden of my heart. ✨</p>
        
        <div id="rose-emoji">🌹</div>

        <br>
        <button id="mainButton" class="btn" onclick="celebrate()">Click Here</button>
    </div>

    <audio id="romantic-music" loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
    </audio>

    <script>
        function celebrate() {
            // 1. Play Music
            const music = document.getElementById('romantic-music');
            music.play().catch(e => console.log("Audio requires user interaction first"));

            // 2. Show Emoji & Hide Button
            document.getElementById('rose-emoji').style.display = 'block';
            document.getElementById('mainButton').style.display = 'none';

            // 3. Burst Confetti
            const duration = 5 * 1000;
            const animationEnd = Date.now() + duration;

            (function frame() {
              const timeLeft = animationEnd - Date.now();

              if (timeLeft <= 0) return;

              const particleCount = 40;
              
              // Confetti from left
              confetti({
                particleCount,
                angle: 60,
                spread: 55,
                origin: { x: 0 },
                colors: ['#ff4d4d', '#ff0000', '#d63384']
              });
              
              // Confetti from right
              confetti({
                particleCount,
                angle: 120,
                spread: 55,
                origin: { x: 1 },
                colors: ['#ff4d4d', '#ff0000', '#d63384']
              });

              requestAnimationFrame(frame);
            }());
        }
    </script>
</body>
</html>
