<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For My Love ❤️</title>
<style>
    body {
        font-family: 'Poppins', sans-serif;
        background: linear-gradient(135deg, #ff9a9e, #fad0c4);
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
        overflow: hidden;
    }
    .container {
        background: white;
        padding: 25px;
        border-radius: 20px;
        box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        width: 360px;
        text-align: center;
        position: relative;
    }
    h1 {
        color: #ff4d6d;
    }
    .question {
        font-size: 18px;
        margin: 15px 0;
    }
    button {
        display: block;
        width: 100%;
        margin: 8px 0;
        padding: 10px;
        border: none;
        border-radius: 10px;
        background: #ff4d6d;
        color: white;
        font-size: 16px;
        cursor: pointer;
        transition: 0.3s;
    }
    button:hover {
        background: #e63950;
    }
    #timer {
        font-weight: bold;
        color: #333;
    }
    .heart {
        position: absolute;
        color: pink;
        animation: float 4s linear infinite;
    }
    @keyframes float {
        0% {transform: translateY(0); opacity:1;}
        100% {transform: translateY(-200px); opacity:0;}
    }
</style>
</head>
<body>
<div class="container">
    <h1>❤️ For You ❤️</h1>
    <div id="timer">Time: 60s</div>
    <div id="quiz"></div>
</div>

<script>
let questions = [
    {
        question: "The Malvaceae family is characterized by which feature?",
        options: [
            "Actinomorphic flowers, monadelphous stamens",
            "Zygomorphic flowers, diadelphous stamens",
            "Unisexual flowers, tetradynamous stamens",
            "Inferior ovary, epipetalous stamens"
        ],
        answer: "Actinomorphic flowers, monadelphous stamens"
    },
    {
        question: "The efferent process of neuron is known as",
        options: ["Dendron", "Axon", "Cyton", "Dendrite"],
        answer: "Axon"
    },
    {
        question: "The heart in cockroach is longitudinal beaded and there are",
        options: [
            "2 chambers in thorax and 11 in abdomen",
            "3 chambers in thorax and 10 in abdomen",
            "2 chambers in thorax and 10 in abdomen",
            "3 chambers in thorax and 9 in abdomen"
        ],
        answer: "3 chambers in thorax and 10 in abdomen"
    },
    {
        question: "Open circulatory system is not a hindrance in cockroach because",
        options: [
            "Heart is simple but chambered",
            "Blood is colorless",
            "Excretion occurs through Malpighian tubules",
            "Circulatory and respiratory systems are not connected"
        ],
        answer: "Circulatory and respiratory systems are not connected"
    },
    {
        question: "Which statement is true for Pheretima?",
        options: [
            "It is dioecious with sexual dimorphism",
            "Copulation occurs at night in burrow during rainy season",
            "It can copulate throughout the year whenever it rains",
            "It cannot move backwards and forwards"
        ],
        answer: "Copulation occurs at night in burrow during rainy season"
    },
    {
        question: "Pharyngeal nephridia of earthworm occur in segments",
        options: ["3,4 and 5", "4,5 and 6", "5,6 and 7", "6,7 and 8"],
        answer: "4,5 and 6"
    },
    {
        question: "If two vectors are parallel, what is the value?",
        options: ["0", "2", "3", "4"],
        answer: "2"
    },
    {
        question: "A particle moves under force (3i+j+4k). Work done is?",
        options: ["70 J", "75 J", "72 J", "80 J"],
        answer: "75 J"
    },
    {
        question: "Which statement is false?",
        options: [
            "Mass, speed and energy are scalars",
            "Momentum, force and torque are vectors",
            "Distance is scalar, displacement is vector",
            "Vector has only magnitude while scalar has both"
        ],
        answer: "Vector has only magnitude while scalar has both"
    },
    {
        question: "Assertion & Reason question",
        options: [
            "Both true and reason explains assertion",
            "Both true but reason not explanation",
            "Assertion true, reason false",
            "Both false"
        ],
        answer: "Both false"
    }
];

let currentQuestion = 0;
let score = 0;
let timeLeft = 60;

function startTimer() {
    let timer = setInterval(() => {
        timeLeft--;
        document.getElementById("timer").innerText = "Time: " + timeLeft + "s";
        if (timeLeft <= 0) {
            clearInterval(timer);
            showResult();
        }
    }, 1000);
}

function loadQuestion() {
    if (currentQuestion >= questions.length) {
        showResult();
        return;
    }

    let q = questions[currentQuestion];
    let quizDiv = document.getElementById("quiz");

    quizDiv.innerHTML = `
        <div class="question">${q.question}</div>
        ${q.options.map(opt => `<button onclick="checkAnswer('${opt}')">${opt}</button>`).join('')}
    `;
}

function checkAnswer(selected) {
    if (selected === questions[currentQuestion].answer) {
        score++;
    }
    currentQuestion++;
    loadQuestion();
}

function showResult() {
    let percentage = (score / questions.length) * 100;
    let message = "";

    if (percentage === 100) {
        message = "Perfect! You know everything about me ❤️ I love you sooo much! 💕";
        launchConfetti();
    } else if (percentage >= 70) {
        message = "So close! You really know me well 😘 Keep loving me like this 💖";
    } else if (percentage >= 40) {
        message = "Not bad, but we need more cute moments together 😜❤️";
    } else {
        message = "Hmm... looks like I need more of your attention 😏❤️";
    }

    document.getElementById("quiz").innerHTML = `
        <h2>Your Score: ${score}/${questions.length}</h2>
        <h3>${percentage.toFixed(0)}%</h3>
        <p>${message}</p>
    `;
}

function launchConfetti() {
    for (let i = 0; i < 30; i++) {
        let heart = document.createElement("div");
        heart.className = "heart";
        heart.innerText = "❤️";
        heart.style.left = Math.random() * 100 + "%";
        heart.style.top = "80%";
        document.body.appendChild(heart);

        setTimeout(() => heart.remove(), 4000);
    }
}

startTimer();
loadQuestion();
</script>
</body>
</html>
