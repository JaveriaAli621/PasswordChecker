<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Password Strength Checker</title>
  <div class="made-by">Made by Javeria Ali, email: javeriaali055@gmail.com</div>
  
<style>
  .footer {
    position: fixed;
    bottom: 10px;
    right: 10px;
    background: rgba(255,255,255,0.95);
    padding: 10px 14px;
    border-radius: 10px;
    box-shadow: 0 2px 6px rgba(0,0,0,0,0.2);

</style>

  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #0e086c, #f49404);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    

    .made-by {
      position: fixed;      
      top: 10px;          
      left: 10px;           
      font-size: 14px;
      color: #aab30b;
      background: rgba(34, 0, 225, 0.8);
      padding: 6px 10px;
      border-radius: 6px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.2);
      font-family: 'Poppins', sans-serif;
    }
    .footer {
    position: fixed;
    bottom: 10px;
    right: 10px;
    background: rgba(255,255,255,0.9);
    padding: 10px 14px;
    border-radius: 8px;
    font-size: 14px;
    color: #333;
    box-shadow: 0 2px 6px rgba(0,0,0,0.2);
    text-align: right;
    }
    .socials a {
    margin-left: 8px;
    text-decoration: none;
    color: #667eea;
    font-weight: 500;
    transition: color 0.3s;
    }

    .socials a:hover {
    color: #764ba2;
    }
    .footer p {
    margin: 0 0 6px;
    font-weight: 600;
    }

    .container {
      background: #ffffffe1;
      border-radius: 12px;
      padding: 30px;
      width: 400px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.2);
      text-align: center;
      animation: fadeIn 1s ease;
    }
    h1 {
      margin-bottom: 20px;
      color: #000000;
    }
    input {
      width: 100%;
      padding: 12px;
      border-radius: 8px;
      border: 1px solid #ccc;
      margin-bottom: 15px;
      font-size: 16px;
      transition: border-color 0.3s;
    }
    input:focus {
      border-color: #7587d6;
      outline: none;
    }
    .strength-bar {
      height: 12px;
      border-radius: 6px;
      background: #eee;
      overflow: hidden;
      margin-bottom: 10px;
    }
    .strength-fill {
      height: 100%;
      width: 0%;
      background: red;
      transition: width 0.4s ease, background 0.4s ease;
    }
    .feedback {
      font-weight: 600;
      margin-top: 10px;
      color: #444;
    }
    .tips {
      margin-top: 15px;
      font-size: 14px;
      color: #666;
      background: #f9f9f9;
      padding: 10px;
      border-radius: 8px;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Password Strength Checker 🔒</h1>
    <input type="password" id="password" placeholder="Enter your password..." />
    <div class="strength-bar">
      <div class="strength-fill" id="strengthFill"></div>
    </div>
    <div class="feedback" id="feedback">Start typing to check strength...</div>
    <div class="tips" id="tips">Tip: Use at least 12 characters, mix letters, numbers & symbols.</div>
  </div>

  <script>
    const passwordInput = document.getElementById('password');
    const strengthFill = document.getElementById('strengthFill');
    const feedback = document.getElementById('feedback');
    const tips = document.getElementById('tips');

    passwordInput.addEventListener('input', () => {
      const val = passwordInput.value;
      let score = 0;

      if (val.length >= 12) score += 30;
      if (/[A-Z]/.test(val)) score += 20;
      if (/[a-z]/.test(val)) score += 20;
      if (/[0-9]/.test(val)) score += 15;
      if (/[^A-Za-z0-9]/.test(val)) score += 15;

      let strength = 'Very Weak';
      let color = 'red';

      if (score >= 80) { strength = 'Strong'; color = 'green'; }
      else if (score >= 60) { strength = 'Good'; color = 'orange'; }
      else if (score >= 40) { strength = 'Weak'; color = 'orangered'; }

      strengthFill.style.width = score + '%';
      strengthFill.style.background = color;
      feedback.textContent = `Strength: ${strength}`;

      if (strength === 'Strong') {
        tips.textContent = 'Great! Your password looks secure.';
      } else {
        tips.textContent = 'Tip: Add more length, mix symbols, numbers & uppercase letters.';
      }
    });
  </script>
</body>
</html>
