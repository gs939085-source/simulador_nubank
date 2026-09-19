# simulador_nubank
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simulador Nubank</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: #f0f1f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .phone-container {
            width: 100%;
            max-width: 400px;
            height: 100%;
            max-height: 800px;
            background-color: #820ad1;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }

        @media (min-width: 401px) {
            .phone-container {
                border-radius: 40px;
                height: 85vh;
            }
        }

        /* Header */
        header {
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: white;
        }

        .profile-icon {
            width: 40px;
            height: 40px;
            background-color: #9c27b0;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            cursor: pointer;
        }

        .header-icons span {
            margin-left: 15px;
            cursor: pointer;
            font-size: 20px;
        }

        /* Content Area */
        .content {
            background-color: #ffffff;
            flex: 1;
            border-top-left-radius: 24px;
            border-top-right-radius: 24px;
            padding: 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 24px;
        }

        .account-section h3 {
            font-size: 16px;
            color: #333;
            font-weight: 500;
        }

        .account-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }

        .balance {
            font-size: 22px;
            font-weight: bold;
            color: #333;
        }

        /* Shortcuts Menu */
        .shortcuts-container {
            display: flex;
            gap: 12px;
            overflow-x: auto;
            padding-bottom: 5px;
        }

        .shortcuts-container::-webkit-scrollbar {
            display: none;
        }

        .shortcut-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            min-width: 76px;
            cursor: pointer;
        }

        .shortcut-icon {
            width: 64px;
            height: 64px;
            background-color: #f0f1f5;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 8px;
            font-size: 20px;
        }

        .shortcut-label {
            font-size: 12px;
            color: #333;
            text-align: center;
            font-weight: 500;
        }

        /* Cards / Banners */
        .card-banner {
            background-color: #f0f1f5;
            padding: 16px;
            border-radius: 16px;
            cursor: pointer;
        }

        .card-banner h4 {
            font-size: 14px;
            color: #333;
            margin-bottom: 4px;
        }

        .card-banner p {
            font-size: 14px;
            color: #820ad1;
            font-weight: 500;
        }
    </style>
</head>
<body>

    <div class="phone-container">
        <!-- Topo Roxo -->
        <header>
            <div class="profile-icon">S</div>
            <div class="header-icons">
                <span id="eye-btn" onclick="toggleBalance()">👁️</span>
                <span>❓</span>
                <span>✉️</span>
            </div>
        </header>

        <!-- Corpo Branco -->
        <div class="content">
            <!-- Seção de Saldo -->
            <div class="account-section">
                <div class="account-header">
                    <h3>Conta</h3>
                    <span>&gt;</span>
                </div>
                <div class="balance" id="balance-display">R$ 1.482,50</div>
            </div>

            <!-- Atalhos Rápidos -->
            <div class="shortcuts-container">
                <div class="shortcut-item" onclick="alert('Área Pix aberta!')">
                    <div class="shortcut-icon">🔄</div>
                    <div class="shortcut-label">Área Pix</div>
                </div>
                <div class="shortcut-item" onclick="alert('Função Pagar aberta!')">
                    <div class="shortcut-icon">📄</div>
                    <div class="shortcut-label">Pagar</div>
                </div>
                <div class="shortcut-item" onclick="alert('Função Transferir aberta!')">
                    <div class="shortcut-icon">↗️</div>
                    <div class="shortcut-label">Transferir</div>
                </div>
                <div class="shortcut-item" onclick="alert('Depositar via Pix ou boleto!')">
                    <div class="shortcut-icon">📥</div>
                    <div class="shortcut-label">Depositar</div>
                </div>
                <div class="shortcut-item" onclick="alert('Recarga de celular indisponível no momento.')">
                    <div class="shortcut-icon">📱</div>
                    <div class="shortcut-label">Recarga</div>
                </div>
            </div>

            <!-- Cartão de Crédito -->
            <div class="card-banner" onclick="alert('Abrindo fatura do cartão...')">
                <h4>Cartão de Crédito</h4>
                <p>Fatura atual: R$ 349,90</p>
            </div>

            <!-- Empréstimo -->
            <div class="card-banner" onclick="alert('Simulação de empréstimo selecionada.')">
                <h4>Empréstimo</h4>
                <p>Valor disponível de até R$ 5.000,00</p>
            </div>
        </div>
    </div>

    <script>
        let isBalanceVisible = true;

        function toggleBalance() {
            const balanceDisplay = document.getElementById('balance-display');
            const eyeBtn = document.getElementById('eye-btn');

            if (isBalanceVisible) {
                balanceDisplay.textContent = '••••••••';
                eyeBtn.textContent = '🙈';
                isBalanceVisible = false;
            } else {
                balanceDisplay.textContent = 'R$ 1.482,50';
                eyeBtn.textContent = '👁️';
                isBalanceVisible = true;
            }
        }
    </script>
</body>
</html>


