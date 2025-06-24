<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <title>🌍 Explorateur de la Démocratie</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f8ff;
      text-align: center;
      padding: 20px;
    }

    h1 {
      color: #2c3e50;
    }

    .section {
      margin: 20px auto;
      padding: 20px;
      background: white;
      border-radius: 12px;
      max-width: 600px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    button {
      margin: 10px;
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      background: #3498db;
      color: white;
      border-radius: 8px;
      cursor: pointer;
    }

    button:hover {
      background: #2980b9;
    }

    img {
      max-width: 100%;
      border-radius: 8px;
    }
  </style>
</head>
<body>

  <h1>🌍 Explorateur de la Démocratie</h1>
  
  <div class="section">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Flag_of_France.svg/640px-Flag_of_France.svg.png" alt="Drapeau de la France" />
  </div>

  <div class="section">
    <h2>📘 Qu’est-ce que la démocratie ?</h2>
    <p>La démocratie est un système politique où les citoyens élisent leurs représentants.<br>
    Elle repose sur la liberté, l’égalité et la participation de tous.</p>
  </div>

  <div class="section">
    <h2>🧠 Quiz rapide</h2>
    <p id="question">Clique sur le bouton ci-dessous pour commencer.</p>
    <div id="reponses"></div>
    <button onclick="lancerQuiz()">▶️ Commencer le quiz</button>
    <p id="score"></p>
  </div>

  <script>
    const questions = [
      {
        question: "Qui détient le pouvoir en démocratie ?",
        choix: ["Un roi", "Le peuple", "L’armée"],
        bonne: 1
      },
      {
        question: "Quel droit est fondamental en démocratie ?",
        choix: ["Le droit de vote", "Le droit de voler", "Le droit de tricher"],
        bonne: 0
      },
      {
        question: "Quelle valeur est essentielle en démocratie ?",
        choix: ["La liberté d'expression", "Le silence forcé", "La peur"],
        bonne: 0
      }
    ];

    let index = 0;
    let score = 0;

    function lancerQuiz() {
      if (index < questions.length) {
        const q = questions[index];
        document.getElementById("question").innerText = q.question;
        const div = document.getElementById("reponses");
        div.innerHTML = "";
        q.choix.forEach((c, i) => {
          const btn = document.createElement("button");
          btn.textContent = c;
          btn.onclick = () => verifier(i);
          div.appendChild(btn);
        });
      } else {
        document.getElementById("question").innerText = "🎉 Fin du quiz !";
        document.getElementById("reponses").innerHTML = "";
        document.getElementById("score").innerText = `Tu as obtenu ${score}/${questions.length} bonnes réponses.`;
      }
    }

    function verifier(choix) {
      if (choix === questions[index].bonne) {
        alert("✅ Bonne réponse !");
        score++;
      } else {
        alert("❌ Mauvaise réponse.");
      }
      index++;
      lancerQuiz();
    }
  </script>

</body>
</html>
