<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Battery</title>
</head>
<style>
    .battery-top{
        width: 30px;
        height: 10px;
        background: black;
        margin: auto;
        border: 3px solid silver;
        border-top-right-radius: 8px;
        border-top-left-radius: 8px;
    }
    .battery-content{
        width: 150px;
        height: 250px;
        background: black;
        position: relative;
        margin:  auto;
        border: 3px solid silver;
        border-radius: 18px;
    }
    .charge{
        width: 100%;
        position: absolute;
        bottom: 0;
        border-radius: 3px;
        border-bottom-left-radius: 12px;
        border-bottom-right-radius: 12px;
        
        animation: battery 15s linear infinite;
    }
    .percentage {
        position: absolute;
        width: 100%;
        text-align: center;
        font-size: 24px;
        font-weight: bold;
        color: white;
        bottom: 10px;
    }
    @keyframes battery {
        0%{
            height: 0%;
            background: red;
        }
        25%{
            height: 25%;
            background: orange;
        }
        50%{
            height: 50%;
            background: yellow;
        }
        75%{
            height: 75%;
            background: #d7fc83;
        }
        100%{
            height: 100%;
            background: rgb(0, 255, 0);
        }
    }
</style>
<body>
    <div class="main">
        <div class="battery-top"></div>
        <div class="battery-content">
            <div class="charge"></div>
            <div class="percentage"></div>
        </div>
    </div>
    <script>
        const percentageDiv = document.querySelector('.percentage');
        const chargeDiv = document.querySelector('.charge');
        const batteryContent = document.querySelector('.battery-content');

        function updatePercentage() {
            const height = chargeDiv.offsetHeight;
            const percentage = Math.round((height / batteryContent.clientHeight) * 100);
            percentageDiv.textContent = percentage + '%';

            if (percentage === 100) {
                percentageDiv.textContent = "Zaryad to'ldi";
                chargeDiv.style.animationPlayState = 'paused';
                setTimeout(() => {
                    chargeDiv.style.animationPlayState = 'running';
                }, 45000);
            }
        }

        setInterval(updatePercentage, 100);
    </script>
</body>
</html>
