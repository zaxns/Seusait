<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulário de Cadastro</title>
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
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 300px;
        }
        .container h2 {
            margin-bottom: 20px;
            font-size: 24px;
            text-align: center;
        }
        .form-group {
            margin-bottom: 15px;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        .form-group input {
            width: 100%;
            padding: 8px;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        .password-strength {
            margin-top: 5px;
            font-size: 12px;
        }
        .password-strength span {
            font-weight: bold;
        }
        .submit-btn {
            width: 100%;
            padding: 10px;
            background-color: #28a745;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        .submit-btn:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Cadastro</h2>
    <form id="registrationForm">
        <div class="form-group">
            <label for="name">Nome:</label>
            <input type="text" id="name" name="name" required>
        </div>
        <div class="form-group">
            <label for="email">E-mail:</label>
            <input type="email" id="email" name="email" required>
        </div>
        <div class="form-group">
            <label for="password">Senha:</label>
            <input type="password" id="password" name="password" required oninput="checkPasswordStrength()">
            <div class="password-strength">
                Força da senha: <span id="strength">Muito Fraca</span>
            </div>
        </div>
        <div class="form-group">
            <label for="confirmPassword">Confirme a Senha:</label>
            <input type="password" id="confirmPassword" name="confirmPassword" required oninput="checkPasswordMatch()">
            <div id="passwordMatch" class="password-strength"></div>
        </div>
        <button type="submit" class="submit-btn">Cadastrar</button>
    </form>
</div>

<script>
    function checkPasswordStrength() {
        const password = document.getElementById('password').value;
        const strengthText = document.getElementById('strength');
        let strength = 0;

        if (password.length >= 8) strength++;
        if (password.match(/[a-z]/)) strength++;
        if (password.match(/[A-Z]/)) strength++;
        if (password.match(/[0-9]/)) strength++;
        if (password.match(/[^a-zA-Z0-9]/)) strength++;

        const strengthLevels = ['Muito Fraca', 'Fraca', 'Moderada', 'Forte', 'Muito Forte', 'Excelente'];
        strengthText.textContent = strengthLevels[strength];
        strengthText.style.color = ['red', 'orange', 'yellow', 'green', 'darkgreen', 'blue'][strength];
    }

    function checkPasswordMatch() {
        const password = document.getElementById('password').value;
        const confirmPassword = document.getElementById('confirmPassword').value;
        const matchText = document.getElementById('passwordMatch');

        if (password === confirmPassword) {
            matchText.textContent = 'Senhas coincidem';
            matchText.style.color = 'green';
        } else {
            matchText.textContent = 'Senhas não coincidem';
            matchText.style.color = 'red';
        }
    }

    document.getElementById('registrationForm').addEventListener('submit', function(event) {
        const password = document.getElementById('password').value;
        const confirmPassword = document.getElementById('confirmPassword').value;

        if (password !== confirmPassword) {
            alert('As senhas não coincidem!');
            event.preventDefault();
        }
    });
</script>

</body>
</html># Seusait
