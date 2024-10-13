# My-3D-Website
This a 3d design website
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ammar 3D Home Design</title>
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #4CAF50;
            color: white;
            padding: 15px;
            text-align: center;
        }
        .logo {
            font-size: 30px;
            font-weight: bold;
        }
        nav {
            text-align: center;
            margin-top: 10px;
        }
        nav a {
            text-decoration: none;
            color: white;
            background-color: #333;
            padding: 10px 20px;
            margin: 5px;
            display: inline-block;
        }
        .container {
            max-width: 1200px;
            margin: 20px auto;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .form-group {
            margin-bottom: 15px;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
        }
        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        .button:hover {
            background-color: #45a049;
        }
        footer {
            text-align: center;
            padding: 10px;
            background-color: #333;
            color: white;
            position: fixed;
            bottom: 0;
            width: 100%;
            display: none; /* Hide footer by default */
        }
        .chatbox {
            position: fixed;
            bottom: 10px;
            right: 10px;
            background-color: #4CAF50;
            color: white;
            padding: 15px;
            border-radius: 10px;
            cursor: pointer;
            display: none; /* Hide chatbox by default */
        }
        .chat-container {
            position: fixed;
            bottom: 70px;
            right: 10px;
            width: 300px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background: white;
            display: none; /* Hide chat window by default */
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
        }
        .chat-header {
            background-color: #4CAF50;
            color: white;
            padding: 10px;
            text-align: center;
            border-radius: 5px 5px 0 0;
        }
        .chat-messages {
            height: 200px;
            overflow-y: auto;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 0 0 5px 5px;
        }
        .chat-input {
            display: flex;
        }
        .chat-input input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px 0 0 5px;
        }
        .chat-input button {
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 0 5px 5px 0;
            cursor: pointer;
        }
        .chat-input button:hover {
            background-color: #45a049;
        }
        .eye-icon {
            position: relative;
        }
        .eye-icon i {
            position: absolute;
            top: 50%;
            right: 10px;
            transform: translateY(-50%);
            cursor: pointer;
        }
        .toggle-footer-icon {
            cursor: pointer;
            margin-left: 10px;
            color: white;
        }
        .message {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }
        .delete-icon {
            cursor: pointer;
            color: red;
        }
    </style>
</head>
<body>

    <!-- Header Section -->
    <header>
        <div class="logo">Ammar 3D Home Design</div>
        <p>Bringing Your Dream Home to Life in 3D!</p>
        <nav>
            <a href="#home">Home</a>
            <a href="#upload">Upload Design</a>
            <a href="#contact">Contact</a>
        </nav>
    </header>

    <!-- Login Section -->
    <div class="container" id="login">
        <h2>Login</h2>
        <form id="loginForm">
            <div class="form-group">
                <label for="username">Username:</label>
                <input type="text" id="username" name="username" required>
            </div>
            <div class="form-group eye-icon">
                <label for="password">Password:</label>
                <input type="password" id="password" name="password" required>
                <i onclick="togglePasswordVisibility()">👁️</i>
            </div>
            <button type="submit" class="button">Login</button>
        </form>
        <p id="loginMessage" style="color: red; display: none;">Invalid login credentials. Please try again.</p>
    </div>

    <!-- Main Container (Visible after login) -->
    <div class="container" id="home" style="display: none;">
        <h1>Welcome to Ammar 3D Home Design</h1>
        <p>Design and upload your custom home projects. Choose the number of rooms, floors, and special features like a garage, pool, or lounge.</p>

        <!-- File Upload Form -->
        <h2>Upload Your Design</h2>
        <form action="/submit_project" method="POST" enctype="multipart/form-data">
            <div class="form-group">
                <label for="file">Upload Design File (STL, OBJ, etc.):</label>
                <input type="file" id="file" name="file" required>
            </div>

            <div class="form-group">
                <label for="title">Project Title:</label>
                <input type="text" id="title" name="title" placeholder="Enter your project title" required>
            </div>

            <div class="form-group">
                <label for="price">Project Price:</label>
                <input type="text" id="price" name="price" placeholder="Enter the price for your project">
            </div>

            <div class="form-group">
                <label for="notes">Notes:</label>
                <textarea id="notes" name="notes" rows="4" placeholder="Add any notes or specifications here"></textarea>
            </div>

            <div class="form-group">
                <label for="rooms">Number of Rooms:</label>
                <select id="rooms" name="rooms">
                    <option value="1">1 Room</option>
                    <option value="2">2 Rooms</option>
                    <option value="3">3 Rooms</option>
                    <option value="4">4 Rooms</option>
                    <option value="5">5+ Rooms</option>
                </select>
            </div>

            <div class="form-group">
                <label for="floors">Number of Floors:</label>
                <select id="floors" name="floors">
                    <option value="1">1 Floor</option>
                    <option value="2">2 Floors</option>
                    <option value="3">3 Floors</option>
                    <option value="4">4+ Floors</option>
                </select>
            </div>

            <!-- Home Parts (Garage, Pool, Lounge, etc.) -->
            <div class="form-group">
                <label for="garage">Include Garage:</label>
                <input type="checkbox" id="garage" name="garage">
            </div>

            <div class="form-group">
                <label for="pool">Include Swimming Pool:</label>
                <input type="checkbox" id="pool" name="pool">
            </div>

            <div class="form-group">
                <label for="lounge">Include Lounge:</label>
                <input type="checkbox" id="lounge" name="lounge">
            </div>

            <div class="form-group">
                <label for="kitchen">Include Kitchen:</label>
                <input type="checkbox" id="kitchen" name="kitchen">
            </div>

            <button type="submit" class="button">Submit Design</button>
        </form>
    </div>

    <!-- Contact Section -->
    <div class="container" id="contact">
        <h2>Contact Us</h2>
        <p>If you have any questions or need assistance, feel free to reach out to us via email:</p>
        <p>Email: <a href="mailto:syedammarali294@gmail.com">syedammarali294@gmail.com</a></p>
    </div>

    <!-- Chat Button -->
    <div class="chatbox" id="chatbox" onclick="toggleChat()">
        Chat with us
    </div>

    <!-- Chat Window -->
    <div class="chat-container" id="chat-container">
        <div class="chat-header">
            <h3>Chat Support</h3>
            <button onclick="toggleChat()">✖</button>
        </div>
        <div class="chat-messages" id="chat-messages"></div>
        <div class="chat-input">
            <input type="text" id="chat-input" placeholder="Type your message..." />
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <!-- Footer -->
    <footer id="footer">
        <span id="copyright">© 2024 Ammar 3D Home Design. All rights reserved.</span>
        <span class="toggle-footer-icon" onclick="toggleCopyright()">👁️</span>
    </footer>

    <script>
        function togglePasswordVisibility() {
            const passwordField = document.getElementById("password");
            if (passwordField.type === "password") {
                passwordField.type = "text";
            } else {
                passwordField.type = "password";
            }
        }

        // Simple login validation
        document.getElementById("loginForm").onsubmit = function(event) {
            event.preventDefault();
            const username = document.getElementById("username").value;
            // Users can log in without needing a password
            if (username === "syedammarali294@gmail.com") {
                document.getElementById("login").style.display = "none";
                document.getElementById("home").style.display = "block";
                document.getElementById("chatbox").style.display = "block"; // Show chatbox after login
            } else {
                document.getElementById("loginMessage").style.display = "block";
            }
        };

        // Chat functionalities
        function toggleChat() {
            const chatContainer = document.getElementById("chat-container");
            chatContainer.style.display = chatContainer.style.display === "block" ? "none" : "block";
        }

        function sendMessage() {
            const input = document.getElementById("chat-input");
            const messageText = input.value.trim();
            if (messageText) {
                const messageContainer = document.createElement("div");
                messageContainer.className = "message";
                messageContainer.innerHTML = `
                    <span>${messageText}</span>
                    <span class="delete-icon" onclick="deleteMessage(this)">🗑️</span>
                `;
                document.getElementById("chat-messages").appendChild(messageContainer);
                input.value = ""; // Clear input after sending
            }
        }

        function deleteMessage(element) {
            const messageContainer = element.parentElement;
            messageContainer.remove();
        }

        // Toggle copyright visibility
        function toggleCopyright() {
            const copyrightText = document.getElementById("copyright");
            if (copyrightText.style.display === "none") {
                copyrightText.style.display = "block";
            } else {
                copyrightText.style.display = "none";
            }
        }

        // Show footer when the user clicks on the toggle icon
        document.querySelector('.toggle-footer-icon').onclick = function() {
            const footer = document.getElementById('footer');
            if (footer.style.display === "none") {
                footer.style.display = "block";
            } else {
                footer.style.display = "none";
            }
        };
    </script>

</body>
</html>
