<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ChatGPT風チャット画面</title>
<style>
    body {
        font-family: 'Arial', sans-serif;
        background-color: #f5f5f5;
        margin: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }
    .chat-container {
        width: 400px;
        height: 600px;
        border-radius: 10px;
        box-shadow: 0 4px 12px rgba(0,0,0,0.15);
        display: flex;
        flex-direction: column;
        background-color: #ffffff;
        overflow: hidden;
    }
    .chat-header {
        background-color: #10a37f;
        color: white;
        padding: 15px;
        font-weight: bold;
        text-align: center;
    }
    .chat-messages {
        flex: 1;
        padding: 15px;
        overflow-y: auto;
        display: flex;
        flex-direction: column;
        gap: 10px;
    }
    .message {
        padding: 10px 15px;
        border-radius: 20px;
        max-width: 70%;
    }
    .user-message {
        background-color: #dcf8c6;
        align-self: flex-end;
    }
    .bot-message {
        background-color: #eaeaea;
        align-self: flex-start;
    }
    .chat-input {
        display: flex;
        border-top: 1px solid #ddd;
    }
    .chat-input input {
        flex: 1;
        padding: 10px 15px;
        border: none;
        border-radius: 0;
        outline: none;
        font-size: 16px;
    }
    .chat-input button {
        padding: 10px 20px;
        border: none;
        background-color: #10a37f;
        color: white;
        cursor: pointer;
        font-size: 16px;
    }
</style>
</head>
<body>
<div class="chat-container">
    <div class="chat-header">ChatGPT風チャット</div>
    <div class="chat-messages" id="chatMessages"></div>
    <div class="chat-input">
        <input type="text" id="userInput" placeholder="メッセージを入力...">
        <button onclick="sendMessage()">送信</button>
    </div>
</div>

<script>
function sendMessage() {
    const input = document.getElementById('userInput');
    const messages = document.getElementById('chatMessages');
    if(input.value.trim() === '') return;

    // ユーザーメッセージ表示
    const userMsg = document.createElement('div');
    userMsg.classList.add('message', 'user-message');
    userMsg.textContent = input.value;
    messages.appendChild(userMsg);

    // Botの返信（簡易）
    const botMsg = document.createElement('div');
    botMsg.classList.add('message', 'bot-message');
    botMsg.textContent = 'これはBotの自動返信です: ' + input.value;
    messages.appendChild(botMsg);

    messages.scrollTop = messages.scrollHeight;
    input.value = '';
}
</script>
</body>
</html>
