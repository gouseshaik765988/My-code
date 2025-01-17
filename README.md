<!DOCTYPE html>
<html>
<head>
    <title>Move Ball Continuously</title>
</head>
<body>
    <div class="container">
        <div class="ball" id="ball"></div>
    </div>

    <div class="controls">
        <button onclick="startMove('right')">Move Right</button>
        <button onclick="startMove('left')">Move Left</button><br>  
        <button onclick="startMove('down')">Move Down</button>
        <button onclick="startMove('up')">Move Up</button>
        <button onclick="stopMove()">Stop</button>
    </div>

    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: rgb(195, 146, 241);
        }
        .container {
            width: 600px;
            height: 400px;
            border: solid black;
            position: relative;
        }
        .ball {
            position: absolute;
            left: 0px;
            bottom: 0px;
            width: 50px;
            height: 50px;
            background-color: brown;
            border-radius: 50%;
            border: solid black;
        }
    </style>

    <script>
        const ball = document.getElementById('ball');
        let left = 0; 
        let bottom = 0;
        let moveInterval; // To store the interval ID for continuous movement

        function startMove(direction) {
            // Clear any existing movement interval before starting a new one
            clearInterval(moveInterval);
            
            // Start moving the ball continuously in the given direction
            moveInterval = setInterval(() => {
                if (direction === 'right' && left < 550) {
                    left += 10;
                    ball.style.left = left + 'px';
                }
                if (direction === 'left' && left > 0) {
                    left -= 10;
                    ball.style.left = left + 'px';
                }
                if (direction === 'down' && bottom > 0) {
                    bottom -= 10;
                    ball.style.bottom = bottom + 'px';
                }
                if (direction === 'up' && bottom < 350) {
                    bottom += 10;
                    ball.style.bottom = bottom + 'px';
                }
            }, 100); // Moves the ball every 100ms
        }

        function stopMove() {
            // Stop the ball's movement
            clearInterval(moveInterval);
        }
    </script>
</body>
</html>
