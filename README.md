<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Webpage</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 10px;
        }
        .error {
            color: red;
        }
        .success {
            color: green;
        }
    </style>
</head>
<body>

    <h1>Interactive Webpage with Form Validation</h1>

    <!-- Form for user input -->
    <form id="userForm">
        <label for="username">Username: </label>
        <input type="text" id="username" name="username" required>
        <br><br>

        <label for="email">Email: </label>
        <input type="email" id="email" name="email" required>
        <br><br>

        <label for="password">Password: </label>
        <input type="password" id="password" name="password" required>
        <br><br>

        <button type="submit" id="submitButton">Submit</button>
    </form>

    <div id="message"></div>

    <!-- Interactive Button -->
    <button id="changeTextButton">Change Text</button>
    <p id="dynamicText">This is some dynamic text!</p>

    <script>
        // Event listener for the form submission
        document.getElementById('userForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent form submission to server

            // Get input values
            const username = document.getElementById('username').value;
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;
            let message = document.getElementById('message');

            // Form validation
            if (username === '' || email === '' || password === '') {
                message.innerHTML = '<p class="error">All fields are required.</p>';
            } else if (!validateEmail(email)) {
                message.innerHTML = '<p class="error">Please enter a valid email address.</p>';
            } else {
                message.innerHTML = `<p class="success">Form submitted successfully! Username: ${username}</p>`;
            }
        });

        // Function to validate email format
        function validateEmail(email) {
            const emailPattern = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;
            return emailPattern.test(email);
        }

        // Event listener for the change text button
        document.getElementById('changeTextButton').addEventListener('click', function() {
            document.getElementById('dynamicText').innerText = 'The text has been changed!';
        });
    </script>

</body>
</html>
