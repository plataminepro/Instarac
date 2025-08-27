# Instarac
Up
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>InstagramHacker - Verificador de Perfil</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #833ab4, #fd1d1d, #fcb045);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            color: #333;
        }
        
        .container {
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            width: 100%;
            max-width: 500px;
            overflow: hidden;
            margin-top: 30px;
        }
        
        header {
            background: linear-gradient(to right, #405de6, #5851db, #833ab4, #c13584, #e1306c, #fd1d1d);
            color: white;
            text-align: center;
            padding: 20px;
        }
        
        header h1 {
            font-size: 24px;
            margin-bottom: 10px;
        }
        
        .logo {
            font-size: 32px;
            margin-bottom: 15px;
        }
        
        .input-section {
            padding: 20px;
        }
        
        .input-group {
            margin-bottom: 20px;
        }
        
        input[type="text"] {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            margin-top: 8px;
        }
        
        button {
            background: linear-gradient(to right, #405de6, #833ab4);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            width: 100%;
            transition: all 0.3s;
        }
        
        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .results {
            padding: 20px;
            background-color: #f9f9f9;
            border-radius: 10px;
            margin-top: 20px;
            display: none;
        }
        
        .result-item {
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
        }
        
        .result-item:last-child {
            border-bottom: none;
        }
        
        .blurred {
            filter: blur(5px);
            user-select: none;
            color: transparent;
            text-shadow: 0 0 8px rgba(0, 0, 0, 0.5);
        }
        
        .premium-overlay {
            position: relative;
            text-align: center;
            padding: 15px;
            background: linear-gradient(45deg, #ffd700, #ffcc00);
            border-radius: 8px;
            margin-top: 20px;
        }
        
        .payment-section {
            padding: 20px;
            text-align: center;
            display: none;
        }
        
        .payment-option {
            background-color: #f8f9fa;
            border-radius: 10px;
            padding: 15px;
            margin: 15px 0;
            text-align: center;
        }
        
        .price {
            font-size: 24px;
            font-weight: bold;
            color: #e1306c;
        }
        
        .countdown {
            font-size: 14px;
            color: #e1306c;
            margin-top: 10px;
            font-weight: bold;
        }
        
        .pix-key {
            background-color: #f0f8ff;
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
            font-family: monospace;
            font-size: 16px;
            word-break: break-all;
            border: 2px dashed #405de6;
        }
        
        .copy-btn {
            background: linear-gradient(to right, #405de6, #833ab4);
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            margin-top: 10px;
        }
        
        .reveal-btn {
            background: linear-gradient(to right, #ffd700, #ffcc00);
            color: #333;
            border: none;
            padding: 12px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            width: 100%;
            margin-top: 15px;
        }
        
        .comments-section {
            margin-top: 30px;
            background-color: white;
            border-radius: 15px;
            padding: 20px;
            width: 100%;
            max-width: 500px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        
        .comment {
            display: flex;
            margin-bottom: 20px;
            padding-bottom: 20px;
            border-bottom: 1px solid #eee;
        }
        
        .comment:last-child {
            border-bottom: none;
        }
        
        .comment-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: #833ab4;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            margin-right: 15px;
            flex-shrink: 0;
        }
        
        .comment-content {
            flex-grow: 1;
        }
        
        .comment-author {
            font-weight: bold;
            margin-bottom: 5px;
        }
        
        .comment-text {
            color: #555;
            line-height: 1.5;
        }
        
        .comment-date {
            font-size: 12px;
            color: #888;
            margin-top: 5px;
        }
        
        .stars {
            color: #ffcc00;
            margin-top: 5px;
        }
        
        .unlocked-results {
            display: none;
            padding: 20px;
            background-color: #f9f9f9;
            border-radius: 10px;
            margin-top: 20px;
        }
        
        .activity-chart {
            width: 100%;
            height: 200px;
            background-color: #fff;
            border-radius: 8px;
            padding: 10px;
            margin: 15px 0;
            display: flex;
            align-items: flex-end;
            justify-content: space-around;
        }
        
        .chart-bar {
            width: 30px;
            background: linear-gradient(to top, #405de6, #833ab4);
            border-radius: 4px 4px 0 0;
            position: relative;
        }
        
        .chart-bar-label {
            position: absolute;
            bottom: -25px;
            left: 0;
            right: 0;
            text-align: center;
            font-size: 12px;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin: 20px 0;
        }
        
        .stat-box {
            background-color: #fff;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }
        
        .stat-value {
            font-size: 24px;
            font-weight: bold;
            color: #e1306c;
            margin: 10px 0;
        }
        
        .stat-label {
            font-size: 14px;
            color: #777;
        }
        
        .suspicious-item {
            display: flex;
            align-items: center;
            margin: 10px 0;
            padding: 10px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }
        
        .suspicious-icon {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: #ffcc00;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
            color: #333;
            font-size: 18px;
        }
        
        .back-btn {
            background: linear-gradient(to right, #405de6, #833ab4);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            width: 100%;
            margin-top: 20px;
        }
        
        .disclaimer {
            text-align: center;
            color: white;
            font-size: 12px;
            margin-top: 20px;
            max-width: 500px;
            padding: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <i class="fab fa-instagram"></i>
            </div>
            <h1>InstagramHacker</h1>
            <p>Verificador de Perfil - Descubra informações ocultas</p>
        </header>
        
        <div class="input-section">
            <div class="input-group">
                <label for="profile-url">Cole o link do perfil do Instagram:</label>
                <input type="text" id="profile-url" placeholder="https://www.instagram.com/usuario/">
            </div>
            <button id="check-btn">Verificar Perfil</button>
        </div>
        
        <div class="results" id="results">
            <h2>Informações Encontradas</h2>
            
            <div class="result-item">
                <h3>Horas online de madrugada</h3>
                <p class="blurred">23:45 - 04:32 (últimas 2 semanas)</p>
            </div>
            
            <div class="result-item">
                <h3>Mensagens apagadas</h3>
                <p class="blurred">17 mensagens apagadas nos últimos 7 dias</p>
            </div>
            
            <div class="result-item">
                <h3>Atividades suspeitas</h3>
                <p class="blurred">Perfis bloqueados: 3 | Seguidores fantasmas: 42</p>
            </div>
            
            <div class="result-item">
                <h3>Posts ocultados</h3>
                <p class="blurred">5 posts ocultados da linha do tempo</p>
            </div>
            
            <div class="premium-overlay">
                <p>🔒 Conteúdo bloqueado. Efetue o pagamento para visualizar todas as informações detalhadas.</p>
            </div>
            
            <button class="reveal-btn" id="reveal-btn">Revelar Conteúdo Completo - R$ 20,00</button>
        </div>
        
        <div class="payment-section" id="payment-section">
            <h2>Pagamento via PIX</h2>
            <p>Para revelar todas as informações, efetue o pagamento de <span class="price">R$ 20,00</span> via PIX</p>
            
            <div class="payment-option">
                <h3>Chave PIX</h3>
                <div class="pix-key" id="pix-key">5351ba94-3000-49a1-aff2-9000dc4af107</div>
                <button class="copy-btn" id="copy-btn">Copiar Chave PIX</button>
            </div>
            
            <div class="countdown" id="countdown">Oferta válida por: 10:00</div>
            
            <button id="paid-btn" class="back-btn">Já efetuei o pagamento</button>
        </div>
        
        <div class="unlocked-results" id="unlocked-results">
            <h2>🔓 Informações Desbloqueadas</h2>
            <p>Relatório completo do perfil: <strong>@usuario_analisado</strong></p>
            
            <div class="stats-grid">
                <div class="stat-box">
                    <div class="stat-label">Horas online esta semana</div>
                    <div class="stat-value">34h</div>
                    <div class="stat-label">+12h que a média</div>
                </div>
                
                <div class="stat-box">
                    <div class="stat-label">Mensagens apagadas</div>
                    <div class="stat-value">17</div>
                    <div class="stat-label">últimos 7 dias</div>
                </div>
            </div>
            
            <h3>Atividade durante a madrugada</h3>
            <div class="activity-chart">
                <div class="chart-bar" style="height: 80%;">
                    <div class="chart-bar-label">Seg</div>
                </div>
                <div class="chart-bar" style="height: 60%;">
                    <div class="chart-bar-label">Ter</div>
                </div>
                <div class="chart-bar" style="height: 90%;">
                    <div class="chart-bar-label">Qua</div>
                </div>
                <div class="chart-bar" style="height: 70%;">
                    <div class="chart-bar-label">Qui</div>
                </div>
                <div class="chart-bar" style="height: 95%;">
                    <div class="chart-bar-label">Sex</div>
                </div>
                <div class="chart-bar" style="height: 100%;">
                    <div class="chart-bar-label">Sáb</div>
                </div>
                <div class="chart-bar" style="height: 85%;">
                    <div class="chart-bar-label">Dom</div>
                </div>
            </div>
            
            <h3>Atividades Suspeitas Detectadas</h3>
            
            <div class="suspicious-item">
                <div class="suspicious-icon">⚠️</div>
                <div>
                    <strong>17 mensagens apagadas</strong>
                    <p>Principalmente entre 01:00 e 04:00</p>
                </div>
            </div>
            
            <div class="suspicious-item">
                <div class="suspicious-icon">🕒</div>
                <div>
                    <strong>Atividade noturna incomum</strong>
                    <p>34% do tempo online entre 23:00 e 05:00</p>
                </div>
            </div>
            
            <div class="suspicious-item">
                <div class="suspicious-icon">👥</div>
                <div>
                    <strong>3 perfis bloqueados</strong>
                    <p>2 deles nos últimos 30 dias</p>
                </div>
            </div>
            
            <div class="suspicious-item">
                <div class="suspicious-icon">📸</div>
                <div>
                    <strong>5 posts ocultados</strong>
                    <p>Posts removidos da linha do tempo mas não excluídos</p>
                </div>
            </div>
            
            <button id="new-analysis-btn" class="back-btn">Fazer Nova Análise</button>
        </div>
    </div>

    <div class="comments-section">
        <h2>O que nossos clientes dizem</h2>
        
        <div class="comment">
            <div class="comment-avatar">C</div>
            <div class="comment-content">
                <div class="comment-author">Carlos Silva</div>
                <div class="stars">★★★★★</div>
                <div class="comment-text">Funciona perfeitamente! Descobri que meu namorado estava me traindo pelas mensagens apagadas que consegui visualizar. Valeu cada centavo!</div>
                <div class="comment-date">Postado há 2 dias</div>
            </div>
        </div>
        
        <div class="comment">
            <div class="comment-avatar">M</div>
            <div class="comment-content">
                <div class="comment-author">Marina Oliveira</div>
                <div class="stars">★★★★☆</div>
                <div class="comment-text">Consegui ver todas as horas que meu filho fica online de madrugada instead de estar estudando. Agora posso tomar providências!</div>
                <div class="comment-date">Postado há 1 semana</div>
            </div>
        </div>
        
        <div class="comment">
            <div class="comment-avatar">R</div>
            <div class="comment-content">
                <div class="comment-author">Ricardo Santos</div>
                <div class="stars">★★★★★</div>
                <div class="comment-text">Nunca imaginei que fosse tão fácil hackear um perfil do Instagram. As informações são detalhadas e precisas. Recomendo!</div>
                <div class="comment-date">Postado há 3 dias</div>
            </div>
        </div>
        
        <div class="comment">
            <div class="comment-avatar">A</div>
            <div class="comment-content">
                <div class="comment-author">Amanda Costa</div>
                <div class="stars">★★★★★</div>
                <div class="comment-text">Paguei e em menos de 5 minutos já tinha acesso a todas as informações. Consegui provar que meu chefe estava me difamando pelas costas!</div>
                <div class="comment-date">Postado hoje</div>
            </div>
        </div>
    </div>

    <div class="disclaimer">
        <p>⚠️ Este site é apenas uma simulação e não oferece serviços reais de verificação de perfis do Instagram. Todas as informações exibidas são fictícias.</p>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const checkBtn = document.getElementById('check-btn');
            const revealBtn = document.getElementById('reveal-btn');
            const results = document.getElementById('results');
            const paymentSection = document.getElementById('payment-section');
            const copyBtn = document.getElementById('copy-btn');
            const countdown = document.getElementById('countdown');
            const paidBtn = document.getElementById('paid-btn');
            const unlockedResults = document.getElementById('unlocked-results');
            const newAnalysisBtn = document.getElementById('new-analysis-btn');
            
            // Inicialmente esconder as seções
            results.style.display = 'none';
            paymentSection.style.display = 'none';
            unlockedResults.style.display = 'none';
            
            checkBtn.addEventListener('click', function() {
                const profileUrl = document.getElementById('profile-url').value;
                
                if (!profileUrl) {
                    alert('Por favor, cole o link do perfil do Instagram.');
                    return;
                }
                
                // Simular tempo de verificação
                checkBtn.textContent = 'Verificando...';
                checkBtn.disabled = true;
                
                setTimeout(function() {
                    results.style.display = 'block';
                    checkBtn.textContent = 'Verificar Perfil';
                    checkBtn.disabled = false;
                    
                    // Rolar para os resultados
                    results.scrollIntoView({ behavior: 'smooth' });
                }, 2000);
            });
            
            revealBtn.addEventListener('click', function() {
                paymentSection.style.display = 'block';
                
                // Rolar para a seção de pagamento
                paymentSection.scrollIntoView({ behavior: 'smooth' });
                
                // Iniciar contagem regressiva
                startCountdown(10 * 60); // 10 minutos
            });
            
            copyBtn.addEventListener('click', function() {
                const pixKey = document.getElementById('pix-key');
                const tempTextArea = document.createElement('textarea');
                tempTextArea.value = pixKey.textContent;
                document.body.appendChild(tempTextArea);
                tempTextArea.select();
                document.execCommand('copy');
                document.body.removeChild(tempTextArea);
                
                copyBtn.textContent = 'Chave Copiada!';
                setTimeout(() => {
                    copyBtn.textContent = 'Copiar Chave PIX';
                }, 2000);
            });
            
            paidBtn.addEventListener('click', function() {
                paymentSection.style.display = 'none';
                unlockedResults.style.display = 'block';
                
                // Rolar para os resultados desbloqueados
                unlockedResults.scrollIntoView({ behavior: 'smooth' });
            });
            
            newAnalysisBtn.addEventListener('click', function() {
                unlockedResults.style.display = 'none';
                results.style.display = 'none';
                document.getElementById('profile-url').value = '';
                
                // Rolar para o topo
                window.scrollTo({ top: 0, behavior: 'smooth' });
            });
            
            function startCountdown(seconds) {
                const countdownElement = document.getElementById('countdown');
                let remainingTime = seconds;
                
                const countdownInterval = setInterval(() => {
                    const minutes = Math.floor(remainingTime / 60);
                    const seconds = remainingTime % 60;
                    
                    countdownElement.textContent = `Oferta válida por: ${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
                    
                    if (remainingTime <= 0) {
                        clearInterval(countdownInterval);
                        countdownElement.textContent = 'Oferta expirada!';
                        countdownElement.style.color = '#ff0000';
                    }
                    
                    remainingTime--;
                }, 1000);
            }
        });
    </script>
</body>
</html>
