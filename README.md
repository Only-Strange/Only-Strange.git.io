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
  
  export default [
    {
    question: "segundo a histologia, qual é o grau de lesão do LSIL?",
    answers: [
        { option: "NIC 1", correct: true },
        { option: "NIC 2/3", correct: false },
        { option: "Carcinoma invasivo", correct: false },

    ],
},

{
    question: "Quais células da ectocérvice são predominantes no LSIL?",
    answers: [
      { option: "Velhas", correct: false },
      { option: "Maduras", correct: true },
      { option: "Imaturas", correct: false },
    ],
  },


{
        question: "Como está a relação núcleo citoplásmatica no LSIL?",
        answers: [
          { option: "RNC alto", correct: true },
          { option: "RNC normal", correct: false },
          { option: "RNC baixo", correct: false },
        ],
      },

{
    question: "A lesão que o HPV causa no grau do LSIL é",
    answers: [
      { option: "Irreverssível", correct: false },
      { option: "Reverssível", correct: true },
      { option: "Impossível de determinar", correct: false },
    ],
  },
{
    question: "Quais são os tipos de HPV mais frequente no LSIL?",
    answers: [
      { option: "Tipo 16 e 18", correct: false },
      { option: "Tipo 31, 45 e 51", correct: false },
      { option: "Tipo 61 e 70", correct: false },
      { option: "Tipo 6 e 11", correct: true },
    ],
  },
];
  
  @import url('https://fonts.googleapis.com/css2?family=Verdana, Geneva, Tahoma:wght@400;500;600&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family:Verdana, Geneva, Tahoma, sans-serif
}

body {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 5px;
  background: linear-gradient(90deg, rgba(0,191,255) 0%, rgba(0,0,139) 100%);
}

body h1 {
    color: springgreen
}

body h2 {
  color: aqua;
}

main {
  background-color: whitesmoke;
  padding: 10px;
  border-radius: 10px;
  width: 100%;
  max-width: 300px;
  min-height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.content {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 10px;
}

.spnQtd {
  text-align: end;
}

.answers {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

button {
  width: 100%;
  text-align: start;
  padding: 5px;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  background-color: #9400D3;
  color: wellow;
}

.finish {
  display: none;
  flex-direction: column;
  gap: 10px;
}

.finish button {
  text-align: center;
}
