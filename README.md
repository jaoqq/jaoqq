bem vindo auxílio de mira jao!

<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Painel FOV Simples</title>
  <style>
    body {
      font-family: Arial;
      background: #111;
      color: white;
      padding: 20px;
    }

    .box {
      background: #222;
      padding: 15px;
      border-radius: 10px;
      width: 300px;
    }

    input[type=range] {
      width: 100%;
    }

    .value {
      margin-top: 10px;
      font-size: 18px;
      color: #00ff99;
    }

    button {
      margin-top: 10px;
      padding: 10px;
      width: 100%;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
    }

    .save {
      background: #00ff99;
    }

    .reset {
      background: #ff4444;
      color: white;
    }
  </style>
</head>
<body>

  <div class="box">
    <h3>Controle FOV</h3>

    <input type="range" min="1" max="120" value="70" id="fov">

    <div class="value">
      FOV: <span id="valor">70</span>%
    </div>

    <button class="save" onclick="salvar()">Salvar configurações</button>
    <button class="reset" onclick="reset()">Resetar</button>
  </div>

  <script>
    const slider = document.getElementById("fov");
    const valor = document.getElementById("valor");

    // carregar salvo
    window.onload = function () {
      const salvo = localStorage.getItem("fov");
      if (salvo) {
        slider.value = salvo;
        valor.textContent = salvo;
      }
    }

    slider.oninput = function () {
      valor.textContent = this.value;
    }

    function salvar() {
      localStorage.setItem("fov", slider.value);
      alert("Configurações salvas!");
    }

    function reset() {
      slider.value = 70;
      valor.textContent = 70;
      localStorage.removeItem("fov");
    }
  </script>

</body>
</html>
