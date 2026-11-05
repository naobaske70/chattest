<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>チャットの練習</title>

  <style>
    body {
      font-family: sans-serif;
      background: #e8eef3;
      margin: 0;
    }

    .container {
      max-width: 500px;
      margin: 20px auto;
      padding: 15px;
    }

    button {
      padding: 10px 15px;
      border: none;
      border-radius: 6px;
      background: #06c755;
      color: white;
      cursor: pointer;
    }

    .close {
      background: #d9534f;
    }

    input {
      box-sizing: border-box;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 6px;
    }

    #messages {
      height: 300px;
      overflow-y: auto;
      background: #b2c7d9;
      padding: 15px;
      margin: 15px 0;
      border-radius: 6px;
    }

    .message {
      background: white;
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 10px;
      overflow-wrap: anywhere;
    }
  </style>
</head>

<body>
  <div class="container">
    <h1>主催者メニュー</h1>

    <button id="createButton">＋ ルームを作成</button>

    <section id="room" hidden>
      <h2>みんなの部屋</h2>

      <input id="name" placeholder="名前を入力">
      <button id="closeButton" class="close">ルームを閉じる</button>

      <div id="messages"></div>

      <input id="message" placeholder="メッセージを入力">
      <button id="sendButton">送信</button>
    </section>
  </div>

  <script>
    const room = document.getElementById("room");
    const messages = document.getElementById("messages");
    const nameInput = document.getElementById("name");
    const messageInput = document.getElementById("message");

    document.getElementById("createButton").onclick = function () {
      room.hidden = false;
    };

    document.getElementById("sendButton").onclick = function () {
      const name = nameInput.value.trim();
      const message = messageInput.value.trim();

      if (!name || !message) {
        alert("名前とメッセージを入力してください。");
        return;
      }

      const item = document.createElement("div");
      item.className = "message";
      item.textContent = name + "： " + message;
      messages.appendChild(item);
      messageInput.value = "";
      messages.scrollTop = messages.scrollHeight;
    };

    document.getElementById("closeButton").onclick = function () {
      const ok = confirm(
        "ルームを閉じますか？ メッセージは消えます。"
      );

      if (ok) {
        messages.textContent = "";
        nameInput.value = "";
        messageInput.value = "";
        room.hidden = true;
      }
    };
  </script>
</body>
</html>
