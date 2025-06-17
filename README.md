<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <title>BienVita - Login</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://www.gstatic.com/firebasejs/10.12.0/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/10.12.0/firebase-auth-compat.js"></script>
  <style>
    body {
      background-color: #fffdd0;
      font-family: 'Segoe UI', sans-serif;
    }
  </style>
</head>
<body class="min-h-screen flex items-center justify-center px-4">

  <div class="bg-white p-10 rounded-3xl shadow-lg w-full max-w-md text-center border border-green-100">
    <h2 class="text-3xl font-semibold text-green-800 mb-2">Bem-vinde ao BienVita</h2>
    <p class="text-green-600 text-sm mb-6">Respira fundo e faça teu login 🌿</p>

    <input id="email" type="email" placeholder="Email"
      class="w-full mb-4 px-4 py-3 border border-green-300 rounded-xl focus:outline-none focus:ring-2 focus:ring-green-400" />

    <input id="senha" type="password" placeholder="Senha"
      class="w-full mb-6 px-4 py-3 border border-green-300 rounded-xl focus:outline-none focus:ring-2 focus:ring-green-400" />

    <button onclick="loginFirebase()"
      class="w-full bg-green-500 hover:bg-green-600 text-white font-bold py-3 px-4 rounded-xl transition duration-300">
      Entrar
    </button>

    <p id="mensagem" class="mt-4 text-sm"></p>
    <p class="mt-4 text-sm text-green-700">
      Ainda não tem uma conta? <a href="cadastro.html" class="text-green-600 font-semibold hover:underline">Criar conta</a>
    </p>
  </div>

  <script>
    const firebaseConfig = {
      apiKey: "AIzaSyBK1GJbt4y07tm-1cinyc94PCuD7GNV8gA",
      authDomain: "bien-vita-ae438.firebaseapp.com",
      projectId: "bien-vita-ae438",
    };

    firebase.initializeApp(firebaseConfig);
    const auth = firebase.auth();

    function loginFirebase() {
      const email = document.getElementById("email").value.trim();
      const senha = document.getElementById("senha").value.trim();
      const msg = document.getElementById("mensagem");

      auth.signInWithEmailAndPassword(email, senha)
        .then(() => {
          msg.textContent = "Login feito com sucesso 🌞 Seja bem-vinde!";
          msg.className = "text-green-600 mt-4";
          setTimeout(() => {
            window.location.href = "inicio.html";
          }, 1500);
        })
        .catch((error) => {
          msg.textContent = "Erro: " + error.message;
          msg.className = "text-red-500 mt-4";
        });
    }
  </script>
</body>
</html>
