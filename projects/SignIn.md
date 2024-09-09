---
layout: project
type: project
image: img/micromouse/micromouse-square.jpg
title: "Sign-in"
date: 2024
published: true
labels:
  - Front-end Development
  - HTML
  - CSS
summary: "A sign in page I created during the summer."
---

This web page features a sign-in form with a stylish background image of Oahu, Hawaii. Upon clicking the "Sign In" button, instead of submitting the form, a modal appears displaying a funny computer science joke. The modal, which overlays the page, includes a joke about programmers and provides a button to close the modal and return to the sign-in form.

Here is the code that I used to create this website:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sign In Page</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-image: url('https://images.unsplash.com/photo-1598135753163-6167c1a1ad65?q=80&w=2069&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'); /* Updated image URL */
            background-size: cover;
            background-position: center;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            color: #fff;
        }

        .signin-container {
            background-color: rgba(0, 0, 0, 0.7); /* semi-transparent black */
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            width: 100%;
            max-width: 400px;
            transition: transform 0.3s ease;
        }

        .signin-container:hover {
            transform: translateY(-10px);
        }

        .signin-container h2 {
            text-align: center;
            margin-bottom: 20px;
            font-size: 24px;
            color: #f1f1f1;
        }

        .signin-container input[type="email"],
        .signin-container input[type="password"] {
            width: 100%;
            padding: 12px;
            margin: 12px 0;
            border: none;
            border-radius: 5px;
            outline: none;
            background: #333;
            color: #fff;
            font-size: 16px;
            transition: all 0.3s ease;
        }

        .signin-container input[type="email"]:focus,
        .signin-container input[type="password"]:focus {
            background-color: #555;
            box-shadow: 0 0 5px #007BFF;
        }

        .signin-container input[type="submit"] {
            width: 100%;
            padding: 12px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 18px;
            transition: background-color 0.3s ease, box-shadow 0.3s ease;
        }

        .signin-container input[type="submit"]:hover {
            background-color: #0056b3;
            box-shadow: 0 8px 20px rgba(0, 123, 255, 0.5);
        }

        .signin-container .signup-link {
            text-align: center;
            margin-top: 15px;
            color: #bbb;
        }

        .signin-container .signup-link a {
            color: #00BFFF;
            text-decoration: none;
        }

        .signin-container .signup-link a:hover {
            text-decoration: underline;
        }

        /* Modal styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background: #fff;
            color: #000;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }

        .modal-content button {
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #007BFF;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }

        .modal-content button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>

    <div class="signin-container">
        <h2>Sign In</h2>
        <form id="signin-form">
            <input type="email" name="email" placeholder="Email" required>
            <input type="password" name="password" placeholder="Password" required>
            <input type="submit" value="Sign In">
        </form>
        <div class="signup-link">
            Don't have an account? <a href="/signup">Sign up here</a>
        </div>
    </div>

    <!-- Modal -->
    <div id="joke-modal" class="modal">
        <div class="modal-content">
            <p>Why do programmers prefer dark mode?</p>
            <p>Because light attracts bugs!</p>
            <button onclick="closeModal()">Close</button>
        </div>
    </div>

    <script>
        // Handle form submission
        document.getElementById('signin-form').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent actual form submission
            document.getElementById('joke-modal').style.display = 'flex'; // Show the modal
        });

        // Close the modal
        function closeModal() {
            document.getElementById('joke-modal').style.display = 'none';
        }
    </script>

</body>
</html>
```
