<!DOCTYPE html>

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Citologia LSIL</title>

  <link rel="stylesheet" href="style.css">
  <style src="style.css"></style>
  <script src="script.js"></script>
  <script src="source.js"></script>
</head>


<body>

  <h1>Quiz LSIL</h1>

  <h2>De acordo com o que foi apresentado, clique nas alternativas corretas em relação ao LSIL</h2>
  <main>
    <div class="content">
      <span class="spnQtd"></span>
      <span class="question"></span>
      <div class="answers"></div>
    </div>
    <div class="finish">
      <span></span>
      <button>Recomeçar</button>
    </div>
  </main>
  
  <script src="script.js" type="module"></script>
</body>
    <footer>
        <p style="color: crimson;" align "center"> Una Aimorés 2023/1</p>
        <p style="color:#00BFFF" align "left"> Análises Citológicas e Biotecnologia</p>
        <p style="color:goldenrod;" align "right"> criado por: Luan Victor</p>

    </html>

  const question = document.querySelector(".question");
const answers = document.querySelector(".answers");
const spnQtd = document.querySelector(".spnQtd");
const textFinish = document.querySelector(".finish span");
const content = document.querySelector(".content");
const contentFinish = document.querySelector(".finish");
const btnRestart = document.querySelector(".finish button");

import questions from "./source.js";

let currentIndex = 0;
let questionsCorrect = 0;

btnRestart.onclick = () => {
  content.style.display = "flex";
  contentFinish.style.display = "none";

  currentIndex = 0;
  questionsCorrect = 0;
  loadQuestion();
};

function nextQuestion(e) {
  if (e.target.getAttribute("data-correct") === "true") {
    questionsCorrect++;
  }

  if (currentIndex < questions.length - 1) {
    currentIndex++;
    loadQuestion();
  } else {
    finish();
  }
}

function finish() {
  textFinish.innerHTML = `você acertou ${questionsCorrect} de ${questions.length}`;
  content.style.display = "none";
  contentFinish.style.display = "flex";
}

function loadQuestion() {
  spnQtd.innerHTML = `${currentIndex + 1}/${questions.length}`;
  const item = questions[currentIndex];
  answers.innerHTML = "";
  question.innerHTML = item.question;

  item.answers.forEach((answer) => {
    const div = document.createElement("div");

    div.innerHTML = `
    <button class="answer" data-correct="${answer.correct}">
      ${answer.option}
    </button>
    `;

    answers.appendChild(div);
  });

  document.querySelectorAll(".answer").forEach((item) => {
    item.addEventListener("click", nextQuestion);
  });
}

loadQuestion();
