
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Valentine?</title>
    <style>
        body { text-align: center; font-family: 'Arial', sans-serif; background-color: #fce4ec; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100vh; overflow: hidden; margin: 0; }
        h1 { color: #d81b60; margin-bottom: 20px; transition: 0.3s; min-height: 1.5em; }
        .gif-container img { width: 250px; border-radius: 15px; margin-bottom: 20px; transition: 0.3s; }
        .buttons-wrapper { display: flex; gap: 20px; align-items: center; justify-content: center; min-height: 150px; }
        button { padding: 15px 25px; font-size: 1.2rem; cursor: pointer; border: none; border-radius: 10px; transition: transform 0.2s ease; }
        #yesBtn { background-color: #4caf50; color: white; position: relative; z-index: 10; }
        #noBtn { background-color: #f44336; color: white; position: relative; transition: all 0.3s ease; }
    </style>
</head>
<body>

    <div id="mainContent">
        <h1 id="question">Will you be my Valentine? 💖</h1>
        
        <div class="gif-container">
            <img id="catGif" src="https://drive.google.com/thumbnail?id=1vk1HdmxSbEMTOZQkg1JforFEe7Ms75C2">
        </div>

        <div class="buttons-wrapper">
            <button id="yesBtn" onclick="celebrate()">YES!</button>
            <button id="noBtn" onclick="handleNoClick()">NO</button>
        </div>
    </div>

    <script>
        let clickCount = 0;

        const mainQuestions = [
            "Will you be my Valentine? 💖",
            "luh, wala man lang pagdadalawang isip? no talaga?",
            "pleaseeee?",
            "💔💔💔💔💔",
            "di mo na ako love💔💔💔",
            "iiyak na ako",
            "sure ka na??",
            "kabit mo siguro kasama mo sa 14"
            
        ];

        const mainGifs = [
            "https://drive.google.com/thumbnail?id=1_aBvUxQclKxKQ9KsVCPSesm0MX8VuQAq",
            "https://drive.google.com/thumbnail?id=1dolrn7aqN_fk2K2IlsNhlaiRGPHuz4Ev",
            "https://drive.google.com/thumbnail?id=1Z0v14uT6qkPe7U5egVKy_0NRe9fhNx12",
            "https://drive.google.com/thumbnail?id=1nIDjhdnnzYFtMX2L2JEG6qSzjOYt75ij",
            "https://drive.google.com/thumbnail?id=1IjirJtdqWcLQtI541Dd-E5poqO8gqERc",
            "https://drive.google.com/thumbnail?id=1MFS8-qXWwNbUnkw1nngHqaHhruob40iB",
            "https://drive.google.com/thumbnail?id=1V93t8yxe5qSwuU-rhDcvH6cDe0B2z8xq"
        ];

        function handleNoClick() {
            const noBtn = document.getElementById('noBtn');
            const yesBtn = document.getElementById('yesBtn');
            const questionText = document.getElementById('question');
            const catImg = document.getElementById('catGif');

            // 1. Move button
            noBtn.style.position = 'absolute';
            const maxX = window.innerWidth - noBtn.offsetWidth;
            const maxY = window.innerHeight - noBtn.offsetHeight;
            noBtn.style.left = Math.floor(Math.random() * maxX) + 'px';
            noBtn.style.top = Math.floor(Math.random() * maxY) + 'px';

            clickCount++;

            // 2. Shrink/Grow logic
            const noScale = Math.max(0.1, 1 - (clickCount * 0.15)); 
            const yesScale = 1 + (clickCount * 0.4); 
            noBtn.style.transform = `scale(${noScale})`;
            yesBtn.style.transform = `scale(${yesScale})`;

            // 3. Update Text - Fixed to prevent "undefined"
            let qIndex = Math.min(clickCount, mainQuestions.length - 1);
            questionText.innerHTML = mainQuestions[qIndex];

            // 4. Update GIF - Fixed to prevent 1x1 blank image
            // This logic ensures it stays on the last valid image in your list
            let gIndex = Math.min(clickCount - 1, mainGifs.length - 1);
            if(gIndex >= 0) {
                catImg.src = mainGifs[gIndex];
            }
        }

        function celebrate() {
            document.getElementById('question').innerHTML = "YAY! I LOVE YOU! 🥰❤️";
            document.getElementById('catGif').src = "https://drive.google.com/thumbnail?id=18Kjda9cJtEqVoW4WR9p3vadBERpdEEhh";
            document.getElementById('noBtn').style.display = 'none';
            document.getElementById('yesBtn').style.transform = "scale(1)";
            document.getElementById('yesBtn').innerHTML = "❤️❤️❤️❤️❤️";
        }
    </script>
</body>
</html>
