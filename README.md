<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Comentários Públicos</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      padding: 0;
    }
    #comments {
      margin-top: 20px;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      max-width: 500px;
    }
    .comment {
      border-bottom: 1px solid #ddd;
      padding: 10px 0;
    }
    .comment:last-child {
      border-bottom: none;
    }
    form {
      margin-top: 20px;
    }
    input, button, textarea {
      width: 100%;
      margin: 10px 0;
      padding: 8px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      background-color: #007BFF;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
  </style>
</head>
<body>
  <h1>Comentários Públicos</h1>
  <div id="comments">
    <p id="no-comments">Nenhum comentário ainda. Seja o primeiro!</p>
  </div>

  <form id="comment-form">
    <textarea id="comment-text" rows="4" placeholder="Escreva seu comentário aqui..."></textarea>
    <input type="password" id="comment-password" placeholder="Digite a senha para comentar">
    <button type="submit">Enviar Comentário</button>
  </form>

  <script>
    const password = "dd3f33";
    const commentsDiv = document.getElementById("comments");
    const form = document.getElementById("comment-form");
    const noCommentsText = document.getElementById("no-comments");

    form.addEventListener("submit", function (event) {
      event.preventDefault();

      const commentText = document.getElementById("comment-text").value.trim();
      const commentPassword = document.getElementById("comment-password").value;

      if (commentPassword !== password) {
        alert("Senha incorreta! Não foi possível adicionar o comentário.");
        return;
      }

      if (commentText === "") {
        alert("Por favor, escreva algo antes de enviar.");
        return;
      }

      // Adiciona o comentário à lista
      const commentElement = document.createElement("div");
      commentElement.classList.add("comment");
      commentElement.textContent = commentText;
      commentsDiv.appendChild(commentElement);

      // Remove o texto "Nenhum comentário ainda"
      noCommentsText.style.display = "none";

      // Limpa o formulário
      document.getElementById("comment-text").value = "";
      document.getElementById("comment-password").value = "";
    });
  </script>
</body>
</html>
