# Game-For-Child
It is a game based web page for children

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Adventure Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f8ff;
        }
        .scene {
            margin: 20px;
            padding: 20px;
            border: 2px solid #ccc;
            border-radius: 10px;
            background-color: #fff;
        }
        .choices button {
            margin: 10px;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            background-color: #00aaff;
            color: #fff;
            font-size: 16px;
            cursor: pointer;
        }
        .choices button:hover {
            background-color: #007acc;
        }
    </style>
</head>
<body>
    <h1>Adventure Game</h1>
    <div id="game" class="scene">
        <p id="scene-description">Once upon a time, in a magical forest...</p>
        <div class="choices">
            <button onclick="chooseOption(1)">Explore the forest</button>
            <button onclick="chooseOption(2)">Talk to the animals</button>
            <button onclick="chooseOption(3)">Follow the stream</button>
        </div>
    </div>
    <script>
        const scenes = {
            1: {
                description: "You find a hidden path that leads to a secret garden filled with colorful flowers.",
                choices: [
                    { text: "Smell the flowers", nextScene: 4 },
                    { text: "Pick a flower", nextScene: 5 },
                    { text: "Continue exploring", nextScene: 6 }
                ]
            },
            2: {
                description: "The animals are friendly and invite you to their picnic.",
                choices: [
                    { text: "Join the picnic", nextScene: 7 },
                    { text: "Play games with them", nextScene: 8 },
                    { text: "Tell them a story", nextScene: 9 }
                ]
            },
            3: {
                description: "The stream leads you to a sparkling waterfall.",
                choices: [
                    { text: "Swim in the waterfall", nextScene: 10 },
                    { text: "Look for fish", nextScene: 11 },
                    { text: "Relax by the water", nextScene: 12 }
                ]
            },
            4: { description: "The flowers smell amazing and make you feel happy.", choices: [] },
            5: { description: "You pick a beautiful flower and keep it as a souvenir.", choices: [] },
            6: { description: "You find more hidden treasures as you explore the garden.", choices: [] },
            7: { description: "You enjoy delicious food at the picnic.", choices: [] },
            8: { description: "You have fun playing games with the animals.", choices: [] },
            9: { description: "The animals love your story and applaud.", choices: [] },
            10: { description: "Swimming in the waterfall is refreshing and fun.", choices: [] },
            11: { description: "You spot colorful fish swimming in the stream.", choices: [] },
            12: { description: "You relax by the water and feel at peace.", choices: [] },
        };

        function chooseOption(option) {
            const scene = scenes[option];
            document.getElementById("scene-description").innerText = scene.description;
            const choicesDiv = document.querySelector(".choices");
            choicesDiv.innerHTML = "";
            scene.choices.forEach((choice, index) => {
                const button = document.createElement("button");
                button.innerText = choice.text;
                button.onclick = () => chooseOption(choice.nextScene);
                choicesDiv.appendChild(button);
            });
        }
    </script>
</body>
</html>
