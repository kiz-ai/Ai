<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Noirfox Bible Quiz</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body {
      background: linear-gradient(to bottom, #1e3c72, #2a5298);
      text-align: center;
      color: white;
      font-family: 'Poppins', sans-serif;
    }
    .quiz-container {
      background: white;
      color: black;
      padding: 20px;
      margin: 30px auto;
      width: 90%;
      max-width: 700px;
      border-radius: 15px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
    }
    button {
      padding: 15px;
      margin: 10px;
      width: 100%;
      border: none;
      cursor: pointer;
      border-radius: 10px;
      transition: background 0.3s;
    }
    button:hover {
      background: #0d6efd;
      color: white;
    }
    .timer {
      font-size: 24px;
      color: red;
      margin-bottom: 15px;
    }
    footer {
      background: #0d1b40;
      padding: 10px;
      color: white;
    }
    .spin-btn {
      background: #ffcc00;
      padding: 10px;
      margin: 20px;
      cursor: pointer;
    }
  </style>
</head>
<body>
<header>Noirfox Bible Quiz</header>

<div class="quiz-container">
  <h2 id="question">Loading Question...</h2>
  <div class="timer" id="timer">25</div>
  <button onclick="checkAnswer(0)" class="answer">A.</button>
  <button onclick="checkAnswer(1)" class="answer">B.</button>
  <button onclick="checkAnswer(2)" class="answer">C.</button>
</div>

<button class="spin-btn" onclick="window.open('https://www.effectiveratecpm.com/u73v8s5gfz?key=7458abc62788b44a577055c4531c86b9')">
  🔄 Spin to Get More Quiz
</button>

<footer>© 2025 Noirfox Bible Quiz | Privacy Policy</footer>

<audio id="correctSound" src="https://www.soundjay.com/button/beep-07.wav"></audio>
<audio id="wrongSound" src="https://www.soundjay.com/button/beep-10.wav"></audio>

<script>
  const questions = [
    { question: "Who was the first man?", answers: ["A. Cain", "B. Adam", "C. Seth"], correct: 1 },
    { question: "Where was Jesus born?", answers: ["A. Jerusalem", "B. Bethlehem", "C. Nazareth"], correct: 1 }
  ];
  let current = 0, timer, timeLeft = 25;

  function loadQuestion() {
    document.getElementById("question").innerText = questions[current].question;
    document.querySelectorAll(".answer").forEach((btn, i) => {
      btn.innerText = questions[current].answers[i];
      btn.classList.remove("correct", "wrong");
    });
    timeLeft = 25;
    document.getElementById("timer").innerText = timeLeft;
    clearInterval(timer);
    timer = setInterval(() => {
      if (--timeLeft === 0) nextQuestion();
      document.getElementById("timer").innerText = timeLeft;
    }, 1000);
  }

  function checkAnswer(index) {
    clearInterval(timer);
    const btns = document.querySelectorAll(".answer");
    btns[index].classList.add(index === questions[current].correct ? "correct" : "wrong");
    document.getElementById(index === questions[current].correct ? "correctSound" : "wrongSound").play();
    setTimeout(nextQuestion, 1000);
  }

  function nextQuestion() {
    current = (current + 1) % questions.length;
    loadQuestion();
  }

  window.onload = loadQuestion;
</script>
</body>
</html>