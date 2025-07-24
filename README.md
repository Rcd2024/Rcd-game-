<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>RCD Games - Robô Aviator</title>
  <style>
    body {
      background-color: #000;
      color: #f00;
      font-family: 'Arial', sans-serif;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
    }h1 {
  margin-top: 30px;
  font-size: 2.5rem;
  text-shadow: 0 0 10px #f00;
}

.container {
  margin-top: 30px;
  width: 90%;
  max-width: 600px;
  background-color: #111;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px #900;
}

.results span {
  margin-right: 10px;
  font-weight: bold;
}

button {
  margin-top: 20px;
  padding: 10px 20px;
  background-color: #f00;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.3s;
}

button:hover {
  background-color: #c00;
}

input {
  width: 60px;
  margin-right: 5px;
  padding: 5px;
  background-color: #222;
  color: #f00;
  border: 1px solid #f00;
  border-radius: 5px;
  text-align: center;
}

  </style>
</head>
<body>
  <h1>RCD GAMES - ROBÔ AVIATOR</h1>  <div class="container">
    <h2>Digite os Últimos Resultados (em x):</h2>
    <div id="inputs"></div>
    <button onclick="analisar()">Analisar</button>
    <h3>Previsão:</h3>
    <p id="resultado">Preencha os resultados acima e clique em Analisar.</p>
  </div>  <script>
    const inputsDiv = document.getElementById('inputs');
    const totalInputs = 10;

    for (let i = 0; i < totalInputs; i++) {
      const input = document.createElement('input');
      input.type = 'number';
      input.step = '0.01';
      input.placeholder = `${i + 1}`;
      inputsDiv.appendChild(input);
    }

    function analisar() {
      const valores = Array.from(document.querySelectorAll('#inputs input'))
        .map(i => parseFloat(i.value))
        .filter(n => !isNaN(n));

      if (valores.length < 5) {
        document.getElementById('resultado').innerText = 'Por favor, preencha pelo menos 5 valores.';
        return;
      }

      const ultimos = valores.slice(-5);
      const baixos = ultimos.filter(v => v < 2).length;

      let mensagem = 'Situação neutra. Use cautela.';
      if (baixos >= 3) {
        mensagem = '🔺 Alta chance de rodada alta agora!';
      } else if (ultimos[0] > 10) {
        mensagem = '🔻 Possível queda nas próximas jogadas.';
      }

      document.getElementById('resultado').innerText = mensagem;
    }
  </script></body>
</html>
