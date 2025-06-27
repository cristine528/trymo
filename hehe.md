**<!DOCTYPE html>**

**<html lang="en">**

**<head>**

    **<meta charset="UTF-8">**

    **<meta name="viewport" content="width=device-width, initial-scale=1.0">**

    **<title>Secret Message</title>**

    **<style>**

        **body {**

            **margin: 0;**

            **padding: 0;**

            **background-color: #000;**

            **width: 100vw;**

            **height: 100vh;**

            **display: flex;**

            **justify-content: center;**

            **align-items: center;**

            **color: transparent;**

            **font-family: 'Arial', sans-serif;**

            **cursor: default;**

            **user-select: none;**

            **overflow: hidden;**

            **transition: color 1.5s ease-in-out;**

        **}**



        **#secret-message {**

            **font-size: 2rem;**

            **text-align: center;**

            **opacity: 0;**

            **transition: opacity 2s ease-in-out;**

            **position: absolute;**

        **}**



        **.tap-counter {**

            **position: fixed;**

            **bottom: 20px;**

            **left: 20px;**

            **color: #333;**

            **font-size: 0.8rem;**

            **z-index: 100;**

        **}**



        **.instructions {**

            **position: fixed;**

            **top: 50%;**

            **left: 50%;**

            **transform: translate(-50%, -50%);**

            **color: #222;**

            **text-align: center;**

            **font-size: 0.9rem;**

            **transition: opacity 0.5s ease;**

        **}**



        **body.show-message #secret-message {**

            **opacity: 1;**

            **color: #ff69b4;**

            **text-shadow: 0 0 10px rgba(255,105,180,0.8);**

            **font-size: 2.5rem;**

            **font-style: italic;**

        **}**



        **body.show-message .instructions {**

            **opacity: 0;**

        **}**



        **.glow {**

            **animation: glow 2s infinite alternate;**

        **}**



        **@keyframes glow {**

            **0% {**

                **text-shadow: 0 0 5px rgba(255,255,255,0.5);**

            **}**

            **100% {**

                **text-shadow: 0 0 30px rgba(255,105,180,1);**

            **}**

        **}**

    **</style>**

**</head>**

**<body>**

    **<div class="instructions">**

        **Tap anywhere 3 times<br>**

        **<span style="font-size: 0.7rem;">(this message will disappear)</span>**

    **</div>**

    **<div id="secret-message">**

        **iloveyou baby, pakiss na**

    **</div>**

    **<div class="tap-counter" id="tap-counter">**

        **Taps: 0/3**

    **</div>**



    **<script>**

        **let tapCount = 0;**

        **const secretMessage = document.getElementById('secret-message');**

        **const tapCounter = document.getElementById('tap-counter');**

        **const body = document.body;**



        **// Initialize with empty click handler**

        **body.addEventListener('click', function handleTap() {**

            **tapCount++;**

            **tapCounter.textContent = `Taps: ${tapCount}/3`;**



            **if (tapCount === 3) {**

                **body.classList.add('show-message');**

                **secretMessage.classList.add('glow');**

                **tapCounter.style.color = '#fff';**



                **// Change the handler to do nothing after 3 taps**

                **body.removeEventListener('click', handleTap);**

                **body.addEventListener('click', function() {});**

            **}**

        **});**



        **// Hide instructions after first tap**

        **setTimeout(() => {**

            **document.querySelector('.instructions').style.opacity = 0.4;**

        **}, 3000);**

    **</script>**

**</body>**

**</html>**





