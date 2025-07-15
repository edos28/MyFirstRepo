<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ph.D. in Mathematics Ad</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #f4f4f9;
            color: #2c3e50;
            font-family: 'Georgia', serif;
        }
        canvas {
            display: block;
        }
        .overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            z-index: 10;
        }
        h1 {
            font-size: 3rem;
            font-weight: bold;
            margin-bottom: 20px;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
        }
        p {
            font-size: 1.5rem;
            margin-bottom: 30px;
            line-height: 1.6;
            max-width: 600px;
        }
        a {
            padding: 15px 30px;
            font-size: 1.2rem;
            color: #fff;
            background-color: #2c3e50;
            border-radius: 5px;
            text-decoration: none;
            transition: background-color 0.3s ease;
        }
        a:hover {
            background-color: #1a252f;
        }
        .math-equation {
            position: absolute;
            font-family: 'Courier New', monospace;
            font-size: 1.2rem;
            color: #34495e;
            opacity: 0.8;
            pointer-events: none;
            animation: float 10s linear infinite;
        }
        @keyframes float {
            0% {
                transform: translateY(0) translateX(0);
            }
            50% {
                transform: translateY(-20px) translateX(10px);
            }
            100% {
                transform: translateY(0) translateX(0);
            }
        }
    </style>
</head>
<body>
    <canvas id="academicCanvas"></canvas>
    <div class="overlay">
        <h1>Advance the Frontiers of Mathematics</h1>
        <p>Pursue groundbreaking research in PDEs, machine learning, and biological modeling. Join a community of scholars shaping the future.</p>
        <a href="#">Apply Now</a>
    </div>

    <script>
        const canvas = document.getElementById('academicCanvas');
        const ctx = canvas.getContext('2d');

        // Set canvas dimensions to fill the window
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        // Handle window resizing
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });

        // Floating mathematical equations
        const equations = [
            "∂u/∂t = D∇²u + f(u)",
            "y = mx + b",
            "P(A|B) = P(B|A)P(A)/P(B)",
            "∫_a^b f(x) dx",
            "det(A - λI) = 0",
            "xₙ₊₁ = rxₙ(1 - xₙ)",
            "∇ × E = -∂B/∂t"
        ];

        // Equation class
        class Equation {
            constructor(x, y, text) {
                this.x = x;
                this.y = y;
                this.text = text;
                this.opacity = Math.random() * 0.5 + 0.3;
                this.speed = Math.random() * 0.5 + 0.2;
            }

            draw() {
                ctx.font = 'italic 18px Georgia';
                ctx.fillStyle = `rgba(44, 62, 80, ${this.opacity})`;
                ctx.fillText(this.text, this.x, this.y);
            }

            update() {
                this.y -= this.speed;
                if (this.y < 0) {
                    this.y = canvas.height + Math.random() * 100;
                    this.x = Math.random() * canvas.width;
                }
                this.draw();
            }
        }

        // Create floating equations
        const equationObjects = [];
        for (let i = 0; i < 50; i++) {
            const x = Math.random() * canvas.width;
            const y = Math.random() * canvas.height;
            const text = equations[Math.floor(Math.random() * equations.length)];
            equationObjects.push(new Equation(x, y, text));
        }

        // Animation loop
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            equationObjects.forEach(equation => {
                equation.update();
            });

            requestAnimationFrame(animate);
        }

        animate();
    </script>
</body>
</html>
