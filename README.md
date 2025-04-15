<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Gerador de Senhas</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #1e1e2f;
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }

    .container {
      background: #2d2d44;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.3);
      text-align: center;
    }

    h1 {
      margin-bottom: 20px;
    }

    .password-display {
      font-size: 1.4em;
      padding: 10px;
      background: #444;
      border-radius: 5px;
      margin-bottom: 15px;
      word-break: break-all;
    }

    input[type="range"] {
      width: 100%;
    }

    button {
      padding: 10px 20px;
      font-size: 1em;
      background: #4caf50;
      border: none;
      border-radius: 5px;
      color: white;
      cursor: pointer;
      transition:  0.3s;
      margin-top: 10px;
    }

    button:hover {
      background: #45a049;
    }

    .length-label {
      margin: 10px 0;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Gerador de Senhas</h1>
    <div class="password-display" id="password">Sua senha aparecerá aqui</div>

    <label class="length-label">Tamanho: <span id="lengthValue">12</span></label><br/>
    <input type="range" min="4" max="24" value="12" id="lengthRange"/>

    <button onclick="generatePassword()">Gerar Senha</button>
    <button onclick="copyPassword()">Copiar</button>
  </div>

  <script>
    const passwordDisplay = document.getElementById("password");
    const lengthRange = document.getElementById("lengthRange");
    const lengthValue = document.getElementById("lengthValue");

    lengthRange.addEventListener("input", () => {
      lengthValue.textContent = lengthRange.value;
    });

    function generatePassword() {
      const length = lengthRange.value;
      const chars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_+";
      let password = "";

      for (let i = 0; i < length; i++) {
        const randomIndex = Math.floor(Math.random() * chars.length);
        password += chars[randomIndex];
      }

      passwordDisplay.textContent = password;
    }

    function copyPassword() {
      const textArea = document.createElement("textarea");
      textArea.value = passwordDisplay.textContent;
      document.body.appendChild(textArea);
      textArea.select();
      document.execCommand("copy");
      document.body.removeChild(textArea);
      alert("Senha copiada!");
    }
  </script>
</body>
</html>