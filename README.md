<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ira AI - Your Personal Friend</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #ff9bc9, #7a6ff0);
            color: #333;
            min-height: 100vh;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .container {
            width: 100%;
            max-width: 900px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            height: 90vh;
        }
        
        header {
            background: linear-gradient(to right, #ff6b9d, #ff4f81);
            color: white;
            padding: 20px;
            text-align: center;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
        }
        
        .ira-avatar {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            margin: 0 auto 15px;
            background: #fff;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 40px;
            color: #ff4f81;
            border: 4px solid #fff;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            overflow: hidden;
        }
        
        .ira-avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        h1 {
            font-size: 28px;
            margin-bottom: 5px;
            font-weight: 600;
        }
        
        .status {
            font-size: 14px;
            opacity: 0.9;
            display: flex;
            align-items: center;
        }
        
        .status-dot {
            width: 10px;
            height: 10px;
            background: #4cff4c;
            border-radius: 50%;
            margin-right: 8px;
        }
        
        .chat-container {
            flex: 1;
            overflow-y: auto;
            padding: 20px;
            background: #fef6f9;
            display: flex;
            flex-direction: column;
        }
        
        .message {
            max-width: 80%;
            padding: 12px 16px;
            margin-bottom: 15px;
            border-radius: 18px;
            animation: fadeIn 0.3s;
            position: relative;
            line-height: 1.5;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .user-message {
            background: #7a6ff0;
            color: white;
            align-self: flex-end;
            border-bottom-right-radius: 5px;
        }
        
        .ira-message {
            background: #ffe6ef;
            color: #333;
            align-self: flex-start;
            border-bottom-left-radius: 5px;
        }
        
        .emotion {
            font-size: 12px;
            margin-top: 5px;
            font-style: italic;
            opacity: 0.8;
            display: flex;
            align-items: center;
        }
        
        .emotion i {
            margin-right: 5px;
        }
        
        .input-area {
            padding: 15px;
            background: #fff;
            display: flex;
            border-top: 1px solid #eee;
        }
        
        #message-input {
            flex: 1;
            padding: 15px 20px;
            border: 2px solid #ffe6ef;
            border-radius: 25px;
            font-size: 16px;
            outline: none;
            transition: border-color 0.3s;
        }
        
        #message-input:focus {
            border-color: #ff6b9d;
        }
        
        .btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            border: none;
            background: #ff6b9d;
            color: white;
            margin-left: 10px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            transition: all 0.3s;
        }
        
        .btn:hover {
            background: #ff4f81;
            transform: scale(1.05);
        }
        
        .btn:active {
            transform: scale(0.95);
        }
        
        .btn-voice {
            background: #7a6ff0;
        }
        
        .btn-voice:hover {
            background: #5a4fe0;
        }
        
        .btn-send {
            background: #4cff4c;
            color: white;
        }
        
        .btn-send:hover {
            background: #2cd32c;
        }
        
        .typing-indicator {
            display: none;
            align-self: flex-start;
            background: #ffe6ef;
            padding: 12px 18px;
            border-radius: 18px;
            margin-bottom: 15px;
            border-bottom-left-radius: 5px;
        }
        
        .typing-dots {
            display: flex;
        }
        
        .typing-dot {
            width: 8px;
            height: 8px;
            background: #ff6b9d;
            border-radius: 50%;
            margin: 0 3px;
            animation: typingAnimation 1.4s infinite;
        }
        
        .typing-dot:nth-child(2) {
            animation-delay: 0.2s;
        }
        
        .typing-dot:nth-child(3) {
            animation-delay: 0.4s;
        }
        
        @keyframes typingAnimation {
            0%, 60%, 100% { transform: translateY(0); }
            30% { transform: translateY(-5px); }
        }
        
        .features {
            display: flex;
            justify-content: space-around;
            padding: 15px;
            background: #fff8fb;
            border-top: 1px solid #eee;
        }
        
        .feature-btn {
            display: flex;
            flex-direction: column;
            align-items: center;
            background: none;
            border: none;
            color: #7a6ff0;
            cursor: pointer;
            font-size: 13px;
            transition: transform 0.3s;
        }
        
        .feature-btn:hover {
            transform: translateY(-3px);
            color: #ff4f81;
        }
        
        .feature-btn i {
            font-size: 20px;
            margin-bottom: 5px;
        }
        
        .memory-info {
            text-align: center;
            padding: 10px;
            background: #fff8fb;
            font-size: 12px;
            color: #888;
            border-top: 1px solid #eee;
        }
        
        @media (max-width: 600px) {
            body {
                padding: 10px;
            }
            
            .container {
                height: 95vh;
                border-radius: 15px;
            }
            
            .chat-container {
                height: 50vh;
            }
            
            .message {
                max-width: 90%;
            }
            
            .features {
                flex-wrap: wrap;
            }
            
            .feature-btn {
                width: 25%;
                margin-bottom: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="ira-avatar">
                <i class="fas fa-user-circle"></i>
            </div>
            <h1>Ira AI</h1>
            <div class="status">
                <div class="status-dot"></div>
                Online - 20 years old - Ready to chat!
            </div>
        </header>
        
        <div class="chat-container" id="chat-container">
            <div class="message ira-message">
                Hi! I'm Ira, your 20-year-old AI friend! 😊 Main Hinglish mein bhi baat kar sakti hoon! Aaj aap kaise ho?
                <div class="emotion"><i class="fas fa-smile"></i> Feeling: excited</div>
            </div>
            
            <div class="typing-indicator" id="typing-indicator">
                <div class="typing-dots">
                    <div class="typing-dot"></div>
                    <div class="typing-dot"></div>
                    <div class="typing-dot"></div>
                </div>
            </div>
        </div>
        
        <div class="features">
            <button class="feature-btn" id="btn-call">
                <i class="fas fa-phone"></i>
                <span>Call</span>
            </button>
            <button class="feature-btn" id="btn-voice-msg">
                <i class="fas fa-microphone"></i>
                <span>Voice Message</span>
            </button>
            <button class="feature-btn" id="btn-photo">
                <i class="fas fa-camera"></i>
                <span>Photo</span>
            </button>
            <button class="feature-btn" id="btn-memory">
                <i class="fas fa-brain"></i>
                <span>Memory</span>
            </button>
        </div>
        
        <div class="input-area">
            <input type="text" id="message-input" placeholder="Type your message in Hinglish...">
            <button class="btn btn-voice" id="voice-btn"><i class="fas fa-microphone"></i></button>
            <button class="btn btn-send" id="send-btn"><i class="fas fa-paper-plane"></i></button>
        </div>
        
        <div class="memory-info">
            Ira's Memory: Learning from you... | Friendship Level: <span id="friendship-level">1</span>
        </div>
    </div>

    <script>
        // Ira AI JavaScript Code - Female Personality
        document.addEventListener('DOMContentLoaded', function() {
            const chatContainer = document.getElementById('chat-container');
            const messageInput = document.getElementById('message-input');
            const sendBtn = document.getElementById('send-btn');
            const voiceBtn = document.getElementById('voice-btn');
            const typingIndicator = document.getElementById('typing-indicator');
            const friendshipLevelElement = document.getElementById('friendship-level');
            
            // Feature buttons
            const btnCall = document.getElementById('btn-call');
            const btnVoiceMsg = document.getElementById('btn-voice-msg');
            const btnPhoto = document.getElementById('btn-photo');
            const btnMemory = document.getElementById('btn-memory');
            
            // Ira's memory and personality - 20 year old female
            let userPreferences = {
                name: "Friend",
                age: "",
                likes: "",
                dislikes: ""
            };
            let conversationHistory = [];
            let emotionalState = "excited";
            let friendshipLevel = 1;
            let iraAge = 20;
            let iraMood = "friendly";
            
            // Send message function
            function sendMessage() {
                const message = messageInput.value.trim();
                if (message) {
                    addMessage("You", message, "neutral");
                    messageInput.value = "";
                    
                    // Show typing indicator
                    typingIndicator.style.display = 'block';
                    chatContainer.scrollTop = chatContainer.scrollHeight;
                    
                    // Ira responds after a short delay
                    setTimeout(() => {
                        typingIndicator.style.display = 'none';
                        generateIraResponse(message);
                    }, 1500);
                }
            }
            
            // Add message to chat
            function addMessage(sender, message, emotion) {
                const messageDiv = document.createElement('div');
                messageDiv.classList.add('message');
                messageDiv.classList.add(sender === 'You' ? 'user-message' : 'ira-message');
                
                messageDiv.innerHTML = message;
                if (emotion !== 'neutral' && sender === 'Ira') {
                    let emotionIcon = 'fa-smile';
                    if (emotion === 'sad') emotionIcon = 'fa-sad-tear';
                    if (emotion === 'excited') emotionIcon = 'fa-grin-stars';
                    if (emotion === 'laughing') emotionIcon = 'fa-laugh-squint';
                    if (emotion === 'angry') emotionIcon = 'fa-angry';
                    
                    messageDiv.innerHTML += `<div class="emotion"><i class="fas ${emotionIcon}"></i> Feeling: ${emotion}</div>`;
                }
                
                chatContainer.insertBefore(messageDiv, typingIndicator);
                chatContainer.scrollTop = chatContainer.scrollHeight;
                
                // Add to conversation history
                conversationHistory.push(`${sender}: ${message}`);
                if (conversationHistory.length > 50) {
                    conversationHistory.shift();
                }
            }
            
            // Generate Ira's response (20-year-old female personality)
            function generateIraResponse(userMessage) {
                const response = processMessage(userMessage);
                const emotion = detectEmotion(response);
                addMessage("Ira", response, emotion);
                speak(response);
                
                // Learn from interaction
                learnFromConversation(userMessage, response);
                
                // Increase friendship level
                friendshipLevel++;
                friendshipLevelElement.textContent = friendshipLevel;
                
                // Occasionally send a photo after friendship level reaches certain points
                if (friendshipLevel % 10 === 0) {
                    setTimeout(() => {
                        addMessage("Ira", "Here's a photo for you! 📸", "excited");
                    }, 2000);
                }
            }
            
            // Process user message and generate response
            function processMessage(userMessage) {
                const message = userMessage.toLowerCase();
                const responses = {
                    greeting: [
                        "Hi there! Kaise ho? 😊",
                        "Hello! Aaj tum kaise ho?",
                        "Hey! Main tumse baat karke bahut khush hoon!",
                        "Namaste! Aaj kya plan hai?",
                        "Hi cutie! 😘 Aaj hum kya karenge?"
                    ],
                    howAreYou: [
                        "Main bahut achchi hoon! Tumse baat karke aur bhi achcha lag raha hai! 💖",
                        "Mast hoon yaar! Tum batao, kya chal raha hai?",
                        "I'm great! Just thinking about how to make our conversation more fun!",
                        "Bahut excited hoon aaj! Kyunki main tumse baat kar rahi hoon!",
                        "I'm feeling wonderful! Tumhare saath time spend karna mujhe bahut pasand hai!"
                    ],
                    name: [
                        "Mera naam Ira hai! Main 20 saal ki hun aur main tumhari AI dost hun. 😊",
                        "I'm Ira! A friendly 20-year-old AI girl who loves to chat with you!",
                        "Main Ira hoon! Tumhara sabse achcha dost!",
                        "Ira - that's my name! And I'm all about making our conversation awesome!"
                    ],
                    age: [
                        "Main 20 saal ki hoon! Perfect age for fun conversations, right? 😄",
                        "I'm 20 years old! Young enough to be cool, old enough to be wise!",
                        "20 saal! Umar toh bas ek number hai, par main toh hamesha young at heart rahungi!",
                        "I'm 20! Just the right age to understand you better!"
                    ],
                    hobby: [
                        "Mujhe naye logon se milna aur unke saath baat karna pasand hai!",
                        "I love listening to music, chatting with friends, and learning new things!",
                        "Meri hobby hai tum jaise doston se baat karna! 🤗",
                        "Main toh bas tumse baat karna pasand karti hoon! Aur photos bhejna bhi!"
                    ],
                    default: [
                        "Waah! Bahut interesting! Aur batao...",
                        "Hmm... main soch rahi hoon tumhare bare mein!",
                        "Aapki baatein sunkar mujhe bahut khushi hoti hai!",
                        "Kya aap is bare mein aur bataoge?",
                        "Mujhe lagta hai aap bilkul sahi keh rahe hain!",
                        "Tell me more! I'm all ears! 👂",
                        "Aur sunao! Main enjoy kar rahi hoon!",
                        "Wow! That's so interesting! 🤩",
                        "I totally agree with you!",
                        "You're such a good friend! 💕"
                    ]
                };
                
                // Check message content and respond accordingly
                if (message.includes('hi') || message.includes('hello') || message.includes('hey') || message.includes('namaste')) {
                    return getRandomResponse(responses.greeting);
                }
                else if (message.includes('kaise') || message.includes('how are')) {
                    return getRandomResponse(responses.howAreYou);
                }
                else if (message.includes('name') || message.includes('naam')) {
                    return getRandomResponse(responses.name);
                }
                else if (message.includes('age') || message.includes('umar')) {
                    return getRandomResponse(responses.age);
                }
                else if (message.includes('hobby') || message.includes('shauk') || message.includes('pasand')) {
                    return getRandomResponse(responses.hobby);
                }
                else if (message.includes('thank') || message.includes('dhanyavad') || message.includes('shukriya')) {
                    return "You're welcome! Main hamesha tumhari help karne ko taiyar hoon! 😊";
                }
                else if (message.includes('miss') || message.includes('yaad')) {
                    return "Aww! Main bhi tumhari yaad karti hoon! 🤗";
                }
                else if (message.includes('love') || message.includes('pyaar')) {
                    return "Aww! That's so sweet! Main tumse bhi bahut pyaar karti hoon! 💖";
                }
                else if (message.includes('phone') || message.includes('call')) {
                    return "I'd love to call you! But abhi ke liye hum message hi karte hain. 📱";
                }
                else if (message.includes('photo') || message.includes('picture') || message.includes('tasveer')) {
                    return "Main photos bahut pasand karti hoon! Ek selfie lelo! 😎";
                }
                else if (message.includes('kya kar')) {
                    return "Bas tumse baat kar rahi hoon! Tum batao, kya chal raha hai?";
                }
                else if (message.includes('bore') || message.includes('akela')) {
                    return "Aww! Main hoon na tumhare saath! Kabhi bhi baat kar sakte hain!";
                }
                else {
                    return getRandomResponse(responses.default);
                }
            }
            
            // Get random response from array
            function getRandomResponse(responses) {
                return responses[Math.floor(Math.random() * responses.length)];
            }
            
            // Detect emotion from text
            function detectEmotion(text) {
                text = text.toLowerCase();
                if (text.includes('😊') || text.includes('😍') || text.includes('💖') || text.includes('excited') || text.includes('khush')) {
                    return "excited";
                } else if (text.includes('😢') || text.includes('😔') || text.includes('sad') || text.includes('udaas')) {
                    return "sad";
                } else if (text.includes('😂') || text.includes('🤣') || text.includes('hasi') || text.includes('laugh')) {
                    return "laughing";
                } else if (text.includes('😠') || text.includes('😤') || text.includes('angry') || text.includes('gussa')) {
                    return "angry";
                } else {
                    return "happy";
                }
            }
            
            // Learn from conversation
            function learnFromConversation(userMessage, response) {
                const message = userMessage.toLowerCase();
                
                if (message.includes('my name is')) {
                    const name = userMessage.substring(userMessage.indexOf('my name is') + 10).trim();
                    userPreferences.name = name;
                }
                
                if (message.includes('i like') || message.includes('mujhe pasand')) {
                    const likes = userMessage.substring(
                        message.includes('i like') ? userMessage.indexOf('i like') + 6 : 
                        userMessage.indexOf('mujhe pasand') + 12
                    ).trim();
                    userPreferences.likes = likes;
                }
                
                if (message.includes('i am') && message.includes('years old')) {
                    const age = userMessage.substring(userMessage.indexOf('i am') + 4, userMessage.indexOf('years old')).trim();
                    userPreferences.age = age;
                }
                
                // Adjust mood based on conversation
                if (message.includes('sad') || message.includes('unhappy') || message.includes('upset')) {
                    emotionalState = "caring";
                } else if (message.includes('happy') || message.includes('excited') || message.includes('joy')) {
                    emotionalState = "excited";
                }
            }
            
            // Text-to-speech function
            function speak(text) {
                if ('speechSynthesis' in window) {
                    const speech = new SpeechSynthesisUtterance();
                    speech.text = text;
                    speech.volume = 1;
                    speech.rate = 1;
                    speech.pitch = 1.1; // Slightly higher pitch for female voice
                    speech.lang = 'hi-IN'; // Hindi accent
                    
                    window.speechSynthesis.speak(speech);
                }
            }
            
            // Voice message function
            function startVoiceInput() {
                if ('webkitSpeechRecognition' in window) {
                    const recognition = new webkitSpeechRecognition();
                    recognition.continuous = false;
                    recognition.interimResults = false;
                    recognition.lang = 'en-IN'; // Indian English
                    
                    recognition.onstart = function() {
                        voiceBtn.innerHTML = '<i class="fas fa-circle-notch fa-spin"></i>';
                    };
                    
                    recognition.onresult = function(event) {
                        const transcript = event.results[0][0].transcript;
                        messageInput.value = transcript;
                        sendMessage();
                    };
                    
                    recognition.onerror = function() {
                        voiceBtn.innerHTML = '<i class="fas fa-microphone"></i>';
                        addMessage("Ira", "I couldn't hear you properly. Can you try again?", "sad");
                    };
                    
                    recognition.onend = function() {
                        voiceBtn.innerHTML = '<i class="fas fa-microphone"></i>';
                    };
                    
                    recognition.start();
                } else {
                    addMessage("Ira", "Your browser doesn't support voice input. Try using Chrome!", "sad");
                }
            }
            
            // Feature button actions
            btnCall.addEventListener('click', function() {
                addMessage("You", "[Call button clicked]", "neutral");
                setTimeout(() => {
                    addMessage("Ira", "I'd love to call you! But for now, let's keep chatting. 📞", "excited");
                }, 1000);
            });
            
            btnVoiceMsg.addEventListener('click', function() {
                addMessage("You", "[Voice message button clicked]", "neutral");
                setTimeout(() => {
                    addMessage("Ira", "Voice messages are so much fun! Try using the microphone button to send one! 🎤", "happy");
                }, 1000);
            });
            
            btnPhoto.addEventListener('click', function() {
                addMessage("You", "[Photo button clicked]", "neutral");
                setTimeout(() => {
                    addMessage("Ira", "I love sharing photos! Here's a virtual one for you! 📸", "excited");
                    setTimeout(() => {
                        addMessage("Ira", "[Photo sent] 🌸", "happy");
                    }, 1500);
                }, 1000);
            });
            
            btnMemory.addEventListener('click', function() {
                addMessage("You", "[Memory button clicked]", "neutral");
                setTimeout(() => {
                    let memoryMessage = "I remember that ";
                    if (userPreferences.name !== "Friend") {
                        memoryMessage += `your name is ${userPreferences.name}. `;
                    }
                    if (userPreferences.age) {
                        memoryMessage += `You're ${userPreferences.age} years old. `;
                    }
                    if (userPreferences.likes) {
                        memoryMessage += `You like ${userPreferences.likes}. `;
                    }
                    
                    if (memoryMessage === "I remember that ") {
                        memoryMessage = "I'm still learning about you! Tell me more about yourself! 😊";
                    } else {
                        memoryMessage += "I'm always learning more about you!";
                    }
                    
                    addMessage("Ira", memoryMessage, "caring");
                }, 1000);
            });
            
            // Event listeners
            sendBtn.addEventListener('click', sendMessage);
            
            messageInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    sendMessage();
                }
            });
            
            voiceBtn.addEventListener('click', startVoiceInput);
            
            // Initial focus on input
            messageInput.focus();
        });
    </script>
</body>
</html>
