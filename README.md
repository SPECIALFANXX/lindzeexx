<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fan Club Website</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .page {
      display: none;
      background-color: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      width: 300px;
      text-align: center;
    }
    .page.active {
      display: block;
    }
    h2 {
      margin-bottom: 20px;
      color: #333;
    }
    input, select {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    button {
      width: 100%;
      padding: 10px;
      background-color: #007bff;
      color: #fff;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
    .error-message {
      color: red;
      font-size: 14px;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <!-- Signup Page -->
  <div id="signupPage" class="page active">
    <h2>Sign Up</h2>
    <form id="signupForm">
      <input type="text" id="signupName" placeholder="Full Name" required>
      <input type="email" id="signupEmail" placeholder="Email Address" required>
      <input type="password" id="signupPassword" placeholder="Password" required>
      <input type="tel" id="signupPhone" placeholder="Phone Number" required>
      <button type="submit">Sign Up</button>
    </form>
    <p>Already have an account? <a href="#" onclick="showPage('loginPage')">Login here</a></p>
  </div>

  <!-- Login Page -->
  <div id="loginPage" class="page">
    <h2>Login</h2>
    <form id="loginForm">
      <input type="email" id="loginEmail" placeholder="Email Address" required>
      <input type="password" id="loginPassword" placeholder="Password" required>
      <button type="submit">Login</button>
    </form>
    <p>Don't have an account? <a href="#" onclick="showPage('signupPage')">Sign up here</a></p>
    <div id="loginErrorMessage" class="error-message"></div>
  </div>

  <!-- Welcome Page -->
  <div id="welcomePage" class="page">
    <h1>Welcome to the Fan Club!</h1>
    <p>Thank you for joining us. We're excited to have you as part of our community.</p>
    <button onclick="showPage('formPage')">Proceed to Form</button>
  </div>

  <!-- Form Page -->
  <div id="formPage" class="page">
    <h2>Fill in Your Information</h2>
    <form id="infoForm">
      <input type="text" id="fullName" placeholder="Full Name" required>
      <input type="number" id="age" placeholder="Age" required>
      <input type="date" id="dob" placeholder="Date of Birth" required>
      <input type="email" id="email" placeholder="Email Address" required>
      <input type="tel" id="phone" placeholder="Phone Number" required>
      <select id="country" required>
        <option value="">Select Country</option>
        <option value="USA">United States</option>
        <option value="Canada">Canada</option>
        <option value="UK">United Kingdom</option>
        <option value="India">India</option>
      </select>
      <input type="text" id="state" placeholder="State" required>
      <input type="text" id="city" placeholder="City" required>
      <input type="text" id="zipCode" placeholder="Zip Code" required>
      <button type="submit">Next</button>
    </form>
  </div>

  <!-- Fan Access Page -->
  <div id="fanAccessPage" class="page">
    <h2>Fan Access</h2>
    <form id="fanAccessForm">
      <input type="text" id="fanCode" placeholder="Fan Code" required>
      <input type="text" id="fanId" placeholder="Fan ID Number" required>
      <button type="submit">Submit</button>
    </form>
    <div id="fanAccessErrorMessage" class="error-message"></div>
  </div>

  <script>
    // Simulated user data (from signup)
    let savedUser = {
      email: "",
      password: ""
    };

    // Show a specific page and hide others
    function showPage(pageId) {
      document.querySelectorAll('.page').forEach(page => {
        page.classList.remove('active');
      });
      document.getElementById(pageId).classList.add('active');
    }

    // Signup Form Submission
    document.getElementById('signupForm').addEventListener('submit', function (event) {
      event.preventDefault();
      savedUser.email = document.getElementById('signupEmail').value;
      savedUser.password = document.getElementById('signupPassword').value;
      alert('Signup successful! Please login.');
      showPage('loginPage');
    });

    // Login Form Submission
    document.getElementById('loginForm').addEventListener('submit', function (event) {
      event.preventDefault();
      const email = document.getElementById('loginEmail').value;
      const password = document.getElementById('loginPassword').value;

      if (email === savedUser.email && password === savedUser.password) {
        showPage('welcomePage');
      } else {
        document.getElementById('loginErrorMessage').textContent = 'Incorrect email or password.';
      }
    });

    // Form Page Submission
    document.getElementById('infoForm').addEventListener('submit', function (event) {
      event.preventDefault();
      showPage('fanAccessPage');
    });

    // Fan Access Form Submission
    document.getElementById('fanAccessForm').addEventListener('submit', function (event) {
      event.preventDefault();
      const fanCode = document.getElementById('fanCode').value;
      const fanId = document.getElementById('fanId').value;

      if (fanCode === 'Damien' && fanId === 'XX519FT') {
        alert('Access granted! Welcome to the fan club.');
      } else {
        document.getElementById('fanAccessErrorMessage').textContent = 'Invalid Fan Code or ID Number.';
      }
    });
  </script>
</body>
</html>
