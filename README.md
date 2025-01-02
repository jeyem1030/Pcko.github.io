<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PCko</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(to right, #e0eafc, #cfdef3); 
            color: #000;
            margin: 0;
            padding: 0;
        }
        .header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 30px 20px;
            background-color: #333;
            color: #fff;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); 
        }
        .header .logo {
            font-size: 32px;
            font-weight: bold;
        }
        .header .search-bar {
            flex-grow: 1;
            max-width: 300px;
            margin-right: 20px;
        }
        .header .search-bar input {
            width: 100%;
            padding: 10px;
            border-radius: 5px; 
            border: 1px solid #ddd;
        }
        .nav {
            display: flex;
            justify-content: flex-end;
            align-items: center;
        }
        .nav a {
            margin-left: 20px;
            text-decoration: none;
            color: #fff;
            transition: color 0.3s; 
        }
        .nav a:hover {
            color: #ffeb3b; 
        }
        .content {
            padding: 20px;
        }
        .content h2 {
            text-align: center;
            color: #333; 
        }
        .pc-parts {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }
        .pc-parts .part {
            background-color: #fff;
            padding: 20px;
            text-align: center;
            width: 150px;
            border-radius: 10px; 
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); 
            transition: transform 0.3s; 
        }
        .pc-parts .part:hover {
            transform: scale(1.05); 
        }
        .pc-parts .part img {
            width: 100%;
            height: auto;
            border-radius: 5px; 
        }
        .chat-icon {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 60px;
            height: 60px;
            background-color: #6200ea;
            color: white;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 30px;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }
        .chat-container {
            display: none;
            position: fixed;
            bottom: 80px;
            right: 20px;
            width: 400px;
            height: 500px;
            background-color: #fff;
            border: 1px solid #ccc;
            border-radius: 10px;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }
        .chat-header {
            background-color: #6200ea;
            color: white;
            padding: 10px;
            text-align: center;
            font-size: 18px;
            font-weight: bold;
        }
        .chat-messages {
            flex: 1;
            padding: 10px;
            overflow-y: auto;
            background-color: #f9f9f9;
        }
        .message {
            margin: 5px 0;
            padding: 10px;
            border-radius: 8px;
        }
        .bot-message {
            background-color: #e0e0e0;
            align-self: flex-start;
        }
        .user-message {
            background-color: #6200ea;
            color: white;
            align-self: flex-end;
        }
        .chat-input {
            display: flex;
            padding: 10px;
            border-top: 1px solid #ccc;
            background-color: #fff;
        }
        .chat-input input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }
        .chat-input button {
            margin-left: 10px;
            padding: 10px 20px;
            background-color: #6200ea;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        .chat-input button:hover {
            background-color: #4b00b8;
        }
    </style>
</head>
<body>
    <div class="header">
        <div class="logo">PCko</div>
        <div class="search-bar">
            <input type="text" placeholder="Search">
        </div>
        <div class="nav">
            <a href="About.html">About</a>
            <a href="cart.html">Cart</a>
        </div>
    </div>
    <div class="content">
        <h2>PC parts</h2>
        <div class="pc-parts">
            <a href="monitor.html">
                <div class="part">Monitor
                    <img src="https://www.shutterstock.com/image-vector/monitor-pc-icon-computer-screen-600nw-380097874.jpg" alt="Monitor">
                </div>
            </a>
            <a href="index.html">
                <div class="part">Keyboard 
                    <img src="https://thumbs.dreamstime.com/b/keyboard-icon-vector-sign-symbol-isolated-white-background-logo-concept-your-web-mobile-app-design-134067880.jpg" alt="keyboard">
                </div>
            </a>
            <a href="mouse.html">
                <div class="part">Mouse 
                    <img src="https://pixsector.com/cache/2e1aab64/av496f7cb62169da6c8ef.jpg" alt="mouse">
                </div>
            </a>
            <a href="processor.html">
                <div class="part">Processor 
                    <img src="https://img.freepik.com/premium-vector/processor-logo-icon_617585-3379.jpg" alt="processor">
                </div>
            </a>
        </div>
    </div>
    <div class="chat-icon" onclick="toggleChat()">💬</div>
    <div class="chat-container" id="chatContainer">
        <div class="chat-header">Chatbot</div>
        <div class="chat-messages" id="chatMessages"></div>
        <div class="chat-input">
            <input type="text" id="userInput" placeholder="Type your message...">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>
    
    <script>
        function toggleChat() {
            const chatContainer = document.getElementById('chatContainer');
            chatContainer.style.display = chatContainer.style.display === 'none' || chatContainer.style.display === '' ? 'flex' : 'none';
        }
        const chatMessages = document.getElementById('chatMessages');
        function appendMessage(content, className) {
            const messageDiv = document.createElement('div');
            messageDiv.textContent = content;
            messageDiv.className = `message ${className}`;
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }
        function sendMessage() {
            const userInput = document.getElementById('userInput');
            const userMessage = userInput.value.trim();
            if (userMessage) {
                appendMessage(userMessage, 'user-message');
                userInput.value = '';
                botReply(userMessage);
            }
        }
        function botReply(message) {
            const lowerCaseMessage = message.toLowerCase();
            let botMessage;
            if (lowerCaseMessage.includes('hello')) {
                botMessage = 'Hi there! How can I help you today?';
            } else if (lowerCaseMessage.includes('how are you')) {
                botMessage = 'I am just a bot, but I am doing great! How about you?';
            } else if (lowerCaseMessage.includes('bye')) {
                botMessage = 'Goodbye! Have a great day!';
            } else {
                botMessage = "I'm not sure how to respond to that. Can you rephrase?";
            }
            appendMessage(botMessage, 'bot-message');
        }
    </script>
</body>
</html>
