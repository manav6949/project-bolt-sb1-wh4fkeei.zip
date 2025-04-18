# project-bolt-sb1-wh4fkeei.zip
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday</title>
    <style>
        body {
            margin: 0;
            font-family: 'Arial', sans-serif;
            background: pink;
            color: #333;
            text-align: center;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            display: none;
            padding: 20px;
            margin: auto;
            max-width: 500px;
            background: #ffe6f0;
            border-radius: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .question-container {
            display: flex;
            flex-direction: column;
            gap: 15px;
            justify-content: center;
            align-items: center;
        }
        .question {
            font-size: 1.8em;
            font-weight: bold;
            margin-bottom: 20px;
        }
        .option {
            padding: 10px 20px;
            background: #ff99cc;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1.2em;
            transition: background 0.3s;
        }
        .option:hover {
            background: #ff66b2;
        }
        .fireworks-container {
            display: none;
            position: relative;
            width: 100vw;
            height: 100vh;
            background: black;
            overflow: hidden;
        }
        .final-message {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-family: 'Brush Script MT', cursive;
            font-size: 5em;
            color: white;
            text-align: center;
        }
        .from-message {
            position: absolute;
            bottom: 10%;
            left: 50%;
            transform: translateX(-50%);
            font-size: 2em;
            font-weight: bold;
            color: white;
        }
        canvas {
            display: block;
        }
    </style>
</head>
<body>
    <div id="question-page" class="container">
        <div id="question-container" class="question-container">
            <div id="question" class="question">Welcome! Are you ready to start?</div>
            <button class="option" onclick="nextQuestion()">Yes, let's go!</button>
            <button class="option" onclick="nextQuestion()">Of course!</button>
        </div>
    </div>
    <div id="fireworks-page" class="fireworks-container">
        <canvas id="fireworksCanvas"></canvas>
        <h1 class="final-message">Happy Birthday!</h1>
        <div class="from-message">From Manav</div>
    </div>
    <script>
        const questions = [
            {
                question: "What is your favorite memory with me?",
                options: ["The trips we took", "Our deep talks", "Laughing together", "All of them!"]
            },
            {
                question: "Which is your favorite birthday gift?",
                options: ["A heartfelt card", "A surprise party", "Something handmade", "All of the above"]
            },
            {
                question: "What's your favorite thing about birthdays?",
                options: ["The cake", "The friends", "The celebration", "Everything!"]
            },
            {
                question: "If you could go anywhere on your birthday, where would it be?",
                options: ["Beach", "Mountains", "City adventures", "Anywhere with friends"]
            },
            {
                question: "What makes a birthday unforgettable?",
                options: ["The people", "The surprises", "The memories", "All of it"]
            }
        ];
        let currentQuestion = 0;
        function nextQuestion() {
            const questionContainer = document.getElementById("question-container");
            if (currentQuestion >= questions.length) {
                showFireworksPage();
                return;
            }
            const question = questions[currentQuestion];
            questionContainer.innerHTML = `
                <div class="question">${question.question}</div>
                ${question.options
                    .map(option => `<button class="option" onclick="nextQuestion()">${option}</button>`)
                    .join("")}
            `;
            currentQuestion++;
        }
        function showFireworksPage() {
            document.getElementById("question-page").style.display = "none";
            document.getElementById("fireworks-page").style.display = "block";
            startFireworks();
        }
        const canvas = document.getElementById('fireworksCanvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        const particles = [];
        class Particle {
            constructor(x, y, color) {
                this.x = x;
                this.y = y;
                this.color = color;
                this.size = Math.random() * 2 + 1;
                this.speed = Math.random() * 6 + 3;
                this.angle = Math.random() * Math.PI * 2;
                this.alpha = 1;
                this.fadeRate = 0.03;
            }
            update() {
                this.x += Math.cos(this.angle) * this.speed;
                this.y += Math.sin(this.angle) * this.speed;
                this.alpha -= this.fadeRate;
                if (this.alpha <= 0) {
                    this.alpha = 0;
                }
            }
            draw() {
                ctx.save();
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
                ctx.restore();
            }
        }
        function startFireworks() {
            function animate() {
                ctx.fillStyle = 'rgba(0, 0, 0, 0.2)';
                ctx.fillRect(0, 0, canvas.width, canvas.height);
                if (Math.random() < 0.1) {
                    for (let i = 0; i < 50; i++) {
                        const x = Math.random() * canvas.width;
                        const y = Math.random() * canvas.height / 2;
                        const color = `hsl(${Math.random() * 360}, 100%, 60%)`;
                        particles.push(new Particle(x, y, color));
                    }
                }
                particles.forEach((particle, index) => {
                    particle.update();
                    particle.draw();
                    if (particle.alpha <= 0) {
                        particles.splice(index, 1);
                    }
                });
                requestAnimationFrame(animate);
            }
            animate();
        }
        document.getElementById("question-page").style.display = "block";
    </script>
</body>
</html>
Navigation Menu
manav6949
project-bolt-sb1-wh4fkeei.zip

Type / to search
Code
Issues
Pull requests
Actions
Projects
Wiki
Security
Insights
Settings
Commit ddd5da9
manav6949
manav6949
authored
1 minute ago
·
·
Verified
Add files via upload
main
1 parent 
b233c70
 commit 
ddd5da9
File tree
Filter files…
untitled.html
1 file changed
+227
-0
lines changed
Search within code
 
Diff for:‎untitled.html
+227
Original file line number	Diff line number	Diff line change
@@ -0,0 +1,227 @@
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday</title>
    <style>
        body {
            margin: 0;
            font-family: 'Arial', sans-serif;
            background: pink;
            color: #333;
            text-align: center;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            display: none;
            padding: 20px;
            margin: auto;
            max-width: 500px;
            background: #ffe6f0;
            border-radius: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .question-container {
            display: flex;
            flex-direction: column;
            gap: 15px;
            justify-content: center;
            align-items: center;
        }
        .question {
            font-size: 1.8em;
            font-weight: bold;
            margin-bottom: 20px;
        }
        .option {
            padding: 10px 20px;
            background: #ff99cc;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1.2em;
            transition: background 0.3s;
        }
        .option:hover {
            background: #ff66b2;
        }
        .fireworks-container {
            display: none;
            position: relative;
            width: 100vw;
            height: 100vh;
            background: black;
            overflow: hidden;
        }
        .final-message {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-family: 'Brush Script MT', cursive;
            font-size: 5em;
            color: white;
            text-align: center;
        }
        .from-message {
            position: absolute;
            bottom: 10%;
            left: 50%;
            transform: translateX(-50%);
            font-size: 2em;
            font-weight: bold;
            color: white;
        }
        canvas {
            display: block;
        }
    </style>
</head>
<body>
    <div id="question-page" class="container">
        <div id="question-container" class="question-container">
            <div id="question" class="question">Welcome! Are you ready to start?</div>
            <button class="option" onclick="nextQuestion()">Yes, let's go!</button>
            <button class="option" onclick="nextQuestion()">Of course!</button>
        </div>
    </div>
    <div id="fireworks-page" class="fireworks-container">
        <canvas id="fireworksCanvas"></canvas>
        <h1 class="final-message">Happy Birthday!</h1>
        <div class="from-message">From Manav</div>
    </div>
    <script>
        const questions = [
            {
                question: "What is your favorite memory with me?",
                options: ["The trips we took", "Our deep talks", "Laughing together", "All of them!"]
            },
            {
                question: "Which is your favorite birthday gift?",
                options: ["A heartfelt card", "A surprise party", "Something handmade", "All of the above"]
            },
            {
                question: "What's your favorite thing about birthdays?",
                options: ["The cake", "The friends", "The celebration", "Everything!"]
            },
            {
                question: "If you could go anywhere on your birthday, where would it be?",
                options: ["Beach", "Mountains", "City adventures", "Anywhere with friends"]
            },
            {
                question: "What makes a birthday unforgettable?",
                options: ["The people", "The surprises", "The memories", "All of it"]
            }
        ];
        let currentQuestion = 0;
        function nextQuestion() {
            const questionContainer = document.getElementById("question-container");
            if (currentQuestion >= questions.length) {
                showFireworksPage();
                return;
            }
            const question = questions[currentQuestion];
            questionContainer.innerHTML = `
                <div class="question">${question.question}</div>
                ${question.options
                    .map(option => `<button class="option" onclick="nextQuestion()">${option}</button>`)
                    .join("")}
            `;
            currentQuestion++;
        }
        function showFireworksPage() {
            document.getElementById("question-page").style.display = "none";
            document.getElementById("fireworks-page").style.display = "block";
            startFireworks();
        }
        const canvas = document.getElementById('fireworksCanvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        const particles = [];
        class Particle {
            constructor(x, y, color) {
                this.x = x;
                this.y = y;
                this.color = color;
                this.size = Math.random() * 2 + 1;
                this.speed = Math.random() * 6 + 3;
                this.angle = Math.random() * Math.PI * 2;
                this.alpha = 1;
                this.fadeRate = 0.03;
            }
            update() {
                this.x += Math.cos(this.angle) * this.speed;
                this.y += Math.sin(this.angle) * this.speed;
                this.alpha -= this.fadeRate;
                if (this.alpha <= 0) {
                    this.alpha = 0;
                }
            }
            draw() {
                ctx.save();
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
                ctx.restore();
            }
        }
        function startFireworks() {
            function animate() {
                ctx.fillStyle = 'rgba(0, 0, 0, 0.2)';
                ctx.fillRect(0, 0, canvas.width, canvas.height);
                if (Math.random() < 0.1) {
                    for (let i = 0; i < 50; i++) {
                        const x = Math.random() * canvas.width;
                        const y = Math.random() * canvas.height / 2;
                        const color = `hsl(${Math.random() * 360}, 100%, 60%)`;
                        particles.push(new Particle(x, y, color));
                    }
                }
                particles.forEach((particle, index) => {
                    particle.update();
                    particle.draw();
                    if (particle.alpha <= 0) {
                        particles.splice(index, 1);
                    }
                });
                requestAnimationFrame(animate);
            }
            animate();
        }
        document.getElementById("question-page").style.display = "block";
    </script>
</body>
</html>
