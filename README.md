<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Cadastro</title>
  <style>
    body {
      font-family: 'Segoe UI', Arial, sans-serif;
      background: #bcc1fa;
      color: #000;
      margin: 0;
      padding: 70px 20px 40px;
      max-width: 500px;
      margin-left: auto;
      margin-right: auto;
      position: relative;
    }

    /* ===== Título principal ===== */
    h1 {
      text-align: center;
      color: #0078d7;
      margin-bottom: 25px;
      font-weight: 700;
      font-size: 1.5rem;
    }

    /* ===== Botão Refazer ===== */
    #refazerCadastro {
      display: block;
      margin: 0 auto 25px auto;
      padding: 8px 14px;
      border: none;
      border-radius: 8px;
      background-color: #000;
      color: #0078d7;
      cursor: pointer;
      transition: all 0.3s ease;
      font-size: 0.9rem;
    }

    #refazerCadastro:hover {
      background-color: #1a1a1a;
      transform: translateY(-2px);
    }

    /* ===== Formulário ===== */
    form {
      background-color: #545151;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
    }

    label {
      display: block;
      margin-top: 12px;
      font-weight: 600;
      color: #0078d7;
      font-size: 0.95rem;
    }

    input {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      background-color: #f8f3f3;
      border: 1px solid #ccc;
      border-radius: 6px;
      color: #000;
      box-sizing: border-box;
      transition: border-color 0.3s ease, background-color 0.3s ease;
      font-size: 0.95rem;
    }

    input:focus {
      outline: none;
      border-color: #0078d7;
      background-color: #f0f8ff;
    }

    /* ===== Mensagens ===== */


    #msg.error {
      color: #d32f2f;
      background-color: #fff0f0;
      border: 1px solid #f0bcbc;
    }

    #msg.success {
      color: #0078d7;
      background-color: #e7f3ff;
      border: 1px solid #b5d9ff;
    }

    /* ===== Botão Enviar ===== */
    button[type="submit"] {
      margin-top: 16px;
      padding: 10px;
      width: 100%;
      background-color: #000;
      color: #0078d7;
      border: none;
      border-radius: 8px;
      font-weight: 600;
      cursor: pointer;
      transition: background-color 0.3s, transform 0.2s;
      font-size: 1rem;
    }

    button[type="submit"]:hover {
      background-color: #1a1a1a;
      transform: translateY(-2px);
    }

    button[type="submit"]:active {
      transform: translateY(0);
    }
  </style>
</head>
<body>


  <!-- ===== CONTEÚDO ===== -->
  <h1>Cadastre-se</h1>

  <button id="refazerCadastro">Refazer cadastro</button>

  <form id="myForm">
    <label for="name">Nome</label>
    <input id="name" name="name" type="text" placeholder="Seu nome completo" required />

    <label for="phone">Telefone</label>
    <input id="phone" name="phone" type="tel" placeholder="(99) 99999-9999" required />

    <label for="email">E-mail</label>
    <input id="email" name="email" type="email" placeholder="exemplo@email.com" required />

    <div id="msg" class="error" role="alert" aria-live="polite"></div>

    <button type="submit">Enviar</button>
  </form>

  <script>
    const form = document.getElementById('myForm');
    const msg = document.getElementById('msg');

    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      msg.className = 'error';
      msg.textContent = '';

      const name = document.getElementById('name').value.trim();
      const phone = document.getElementById('phone').value.trim();
      const email = document.getElementById('email').value.trim();

      const phoneRegex = /^[\d\s()+-]{6,}$/;
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

      if (!name || !phoneRegex.test(phone) || !emailRegex.test(email)) {
        msg.textContent = 'Telefone ou e-mail não válidos, tente novamente';
        return;
      }

      try {
        form.reset();
        msg.className = 'success';
        msg.textContent = 'Enviado com sucesso — obrigado!';
      } catch (err) {
        msg.className = 'error';
        msg.textContent = 'Erro de rede. Verifique sua conexão.';
        console.error(err);
      }
    });
  </script>
</body>
</html>
