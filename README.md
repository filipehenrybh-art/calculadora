<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Planejador de Caminhada | Alcance Seu Peso Ideal</title>
    <meta name="description" content="Calcule quanto você precisa caminhar diariamente para chegar ao peso ideal. Método científico e personalizado.">
    <style>
        :root {
            --primary: #4CAF50;
            --primary-dark: #388E3C;
            --primary-light: #C8E6C9;
            --secondary: #FF9800;
            --secondary-dark: #F57C00;
            --light: #f8f9fa;
            --dark: #2E3A47;
            --gray: #6C757D;
            --success: #28A745;
            --warning: #FFC107;
            --danger: #DC3545;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            color: var(--dark);
            line-height: 1.6;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            padding: 40px 20px;
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: white;
            border-radius: 15px;
            margin-bottom: 30px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            position: relative;
            overflow: hidden;
        }
        
        header:before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320"><path fill="%23ffffff" fill-opacity="0.1" d="M0,96L48,112C96,128,192,160,288,186.7C384,213,480,235,576,213.3C672,192,768,128,864,128C960,128,1056,192,1152,192C1248,192,1344,128,1392,96L1440,64L1440,320L1392,320C1344,320,1248,320,1152,320C1056,320,960,320,864,320C768,320,672,320,576,320C480,320,384,320,288,320C192,320,96,320,48,320L0,320Z"></path></svg>');
            background-size: cover;
            background-position: center;
        }
        
        .header-content {
            position: relative;
            z-index: 1;
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 15px;
            font-weight: 700;
        }
        
        .subtitle {
            font-size: 1.3rem;
            opacity: 0.9;
            max-width: 600px;
            margin: 0 auto;
        }
        
        .progress-container {
            display: flex;
            justify-content: center;
            margin: 30px 0;
        }
        
        .progress-step {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin: 0 20px;
            position: relative;
        }
        
        .step-number {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: var(--light);
            color: var(--dark);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            margin-bottom: 10px;
            z-index: 2;
            box-shadow: 0 3px 5px rgba(0,0,0,0.1);
        }
        
        .step-active .step-number {
            background-color: var(--secondary);
            color: white;
        }
        
        .step-completed .step-number {
            background-color: var(--success);
            color: white;
        }
        
        .step-text {
            font-size: 0.9rem;
            text-align: center;
            color: white;
        }
        
        .card {
            background-color: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            margin-bottom: 30px;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }
        
        .form-container {
            display: block;
        }
        
        .form-group {
            margin-bottom: 25px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--dark);
        }
        
        .input-group {
            position: relative;
        }
        
        input, select {
            width: 100%;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: border 0.3s, box-shadow 0.3s;
        }
        
        input:focus, select:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px var(--primary-light);
            outline: none;
        }
        
        .unit {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--gray);
        }
        
        .btn {
            display: inline-block;
            background: linear-gradient(to right, var(--primary), var(--primary-dark));
            color: white;
            padding: 16px 32px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
            width: 100%;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 7px 10px rgba(0,0,0,0.15);
        }
        
        .btn-secondary {
            background: linear-gradient(to right, var(--secondary), var(--secondary-dark));
        }
        
        .btn-outline {
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
        }
        
        .result-container {
            text-align: center;
            display: none;
        }
        
        .result-title {
            color: var(--primary);
            margin-bottom: 20px;
            font-size: 1.8rem;
        }
        
        .result-card {
            background: linear-gradient(135deg, #e3f2fd, #f3e5f5);
            padding: 30px;
            border-radius: 15px;
            margin: 20px 0;
            border-left: 5px solid var(--primary);
        }
        
        .result-value {
            font-size: 3rem;
            font-weight: 700;
            color: var(--primary);
            margin: 20px 0;
        }
        
        .result-description {
            margin-bottom: 20px;
            color: var(--gray);
            font-size: 1.1rem;
        }
        
        .checkout-container {
            text-align: center;
            display: none;
        }
        
        .ebook-image {
            max-width: 250px;
            margin: 0 auto 20px;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }
        
        .ebook-image img {
            width: 100%;
            height: auto;
            display: block;
        }
        
        .ebook-title {
            font-size: 2rem;
            margin-bottom: 15px;
            color: var(--primary);
        }
        
        .ebook-description {
            margin-bottom: 20px;
            color: var(--gray);
            font-size: 1.1rem;
        }
        
        .benefits {
            text-align: left;
            margin: 25px 0;
            padding-left: 0;
            list-style: none;
        }
        
        .benefits li {
            margin-bottom: 15px;
            position: relative;
            padding-left: 35px;
        }
        
        .benefits li:before {
            content: "✓";
            color: var(--success);
            font-weight: bold;
            position: absolute;
            left: 0;
            top: 0;
            width: 25px;
            height: 25px;
            background-color: var(--primary-light);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .price {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--primary);
            margin: 20px 0;
        }
        
        .original-price {
            text-decoration: line-through;
            color: var(--gray);
            font-size: 1.5rem;
            margin-right: 10px;
        }
        
        .discount {
            background-color: var(--secondary);
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 1rem;
            display: inline-block;
            margin-left: 10px;
        }
        
        .guarantee {
            margin: 20px 0;
            font-style: italic;
            color: var(--gray);
            padding: 15px;
            background-color: var(--light);
            border-radius: 8px;
        }
        
        .testimonials {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin: 30px 0;
        }
        
        .testimonial {
            flex: 1;
            min-width: 250px;
            background-color: var(--light);
            padding: 20px;
            border-radius: 10px;
            text-align: left;
        }
        
        .testimonial-text {
            font-style: italic;
            margin-bottom: 15px;
        }
        
        .testimonial-author {
            font-weight: bold;
            color: var(--primary);
        }
        
        footer {
            text-align: center;
            padding: 30px 0;
            color: var(--gray);
            font-size: 0.9rem;
            border-top: 1px solid #eee;
            margin-top: 30px;
        }
        
        .faq {
            text-align: left;
            margin: 30px 0;
        }
        
        .faq-item {
            margin-bottom: 15px;
            border-bottom: 1px solid #eee;
            padding-bottom: 15px;
        }
        
        .faq-question {
            font-weight: bold;
            margin-bottom: 10px;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .faq-answer {
            display: none;
            color: var(--gray);
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }
            
            h1 {
                font-size: 2.2rem;
            }
            
            .progress-step {
                margin: 0 10px;
            }
            
            .step-text {
                font-size: 0.8rem;
            }
            
            .card {
                padding: 20px;
            }
            
            .result-value {
                font-size: 2.5rem;
            }
            
            .testimonials {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="header-content">
                <h1>Alcance Seu Peso Ideal</h1>
                <p class="subtitle">Descubra quanto você precisa caminhar diariamente para chegar ao seu peso ideal com nosso método científico</p>
                
                <div class="progress-container">
                    <div class="progress-step step-active">
                        <div class="step-number">1</div>
                        <div class="step-text">Seus Dados</div>
                    </div>
                    <div class="progress-step">
                        <div class="step-number">2</div>
                        <div class="step-text">Resultado</div>
                    </div>
                    <div class="progress-step">
                        <div class="step-number">3</div>
                        <div class="step-text">Ebook</div>
                    </div>
                </div>
            </div>
        </header>
        
        <div class="card form-container" id="form-container">
            <form id="calculator-form">
                <div class="form-group">
                    <label for="gender">Gênero</label>
                    <select id="gender" required>
                        <option value="">Selecione seu gênero</option>
                        <option value="male">Masculino</option>
                        <option value="female">Feminino</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="age">Idade</label>
                    <div class="input-group">
                        <input type="number" id="age" min="18" max="100" required placeholder="Sua idade em anos">
                        <span class="unit">anos</span>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="height">Altura</label>
                    <div class="input-group">
                        <input type="number" id="height" min="100" max="250" required placeholder="Sua altura em centímetros">
                        <span class="unit">cm</span>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="weight">Peso Atual</label>
                    <div class="input-group">
                        <input type="number" id="weight" min="30" max="300" step="0.1" required placeholder="Seu peso atual em quilogramas">
                        <span class="unit">kg</span>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="activity">Nível de Atividade Física</label>
                    <select id="activity" required>
                        <option value="">Selecione seu nível de atividade</option>
                        <option value="1.2">Sedentário (pouco ou nenhum exercício)</option>
                        <option value="1.375">Levemente ativo (exercício leve 1-3 dias/semana)</option>
                        <option value="1.55">Moderadamente ativo (exercício moderado 3-5 dias/semana)</option>
                        <option value="1.725">Muito ativo (exercício intenso 6-7 dias/semana)</option>
                        <option value="1.9">Extremamente ativo (exercício muito intenso e trabalho físico)</option>
                    </select>
                </div>
                
                <button type="submit" class="btn">Calcular Minha Caminhada Diária</button>
            </form>
        </div>
        
        <div class="card result-container" id="result-container">
            <h2 class="result-title">Sua Caminhada Diária Recomendada</h2>
            
            <div class="result-card">
                <div class="result-value" id="walking-result">0 minutos</div>
                <p class="result-description" id="result-description">
                    Com base nas suas informações, esta é a quantidade de caminhada diária necessária para alcançar seu peso ideal de forma saudável.
                </p>
            </div>
            
            <p class="result-description">
                <strong>Importante:</strong> A alimentação é responsável por 70% do sucesso no emagrecimento. A caminhada potencializa os resultados!
            </p>
            
            <button class="btn btn-secondary" id="show-ebook">Quero Aprender a Me Alimentar Melhor</button>
            <button class="btn btn-outline" id="back-to-form">Recalcular</button>
        </div>
        
        <div class="card checkout-container" id="checkout-container">
            <div class="ebook-image">
                <div style="width:100%;height:300px;background:linear-gradient(135deg, #4CAF50, #388E3C);display:flex;align-items:center;justify-content:center;color:white;font-size:24px;font-weight:bold;">EBOOK SAUDÁVEL</div>
            </div>
            
            <h2 class="ebook-title">Guia Completo da Alimentação Saudável</h2>
            <p class="ebook-description">
                Aprenda a se alimentar corretamente para potencializar seus resultados e alcançar seu peso ideal com saúde e sem passar fome.
            </p>
            
            <ul class="benefits">
                <li>Plano alimentar personalizado para seu perfil</li>
                <li>+50 receitas saudáveis e saborosas</li>
                <li>Dicas para manter a motivação</li>
                <li>Como lidar com deslizes sem culpa</li>
                <li>Lista de compras saudáveis</li>
                <li>Estratégias para manter o peso após o emagrecimento</li>
                <li>Cardápios para todas as refeições</li>
                <li>Guia de substituições inteligentes</li>
            </ul>
            
            <div class="testimonials">
                <div class="testimonial">
                    <p class="testimonial-text">"Perdi 12kg em 3 meses seguindo o método do ebook. Aprendi a me alimentar corretamente sem dietas malucas!"</p>
                    <p class="testimonial-author">- Maria S., 34 anos</p>
                </div>
                <div class="testimonial">
                    <p class="testimonial-text">"Finalmente entendi como a alimentação funciona. Não estou mais preso ao efeito sanfona!"</p>
                    <p class="testimonial-author">- João P., 42 anos</p>
                </div>
            </div>
            
            <div class="price">
                <span class="original-price">R$ 97,00</span> R$ 47,00
                <span class="discount">52% OFF</span>
            </div>
            
            <p class="guarantee">Garantia incondicional de 7 dias! Se não gostar, devolvemos seu dinheiro.</p>
            
            <button class="btn" id="buy-now">Comprar Agora - R$ 47,00</button>
            <button class="btn btn-outline" id="back-to-result">Voltar ao Resultado</button>
            
            <div class="faq">
                <h3>Perguntas Frequentes</h3>
                <div class="faq-item">
                    <div class="faq-question">Como receberei o ebook? <span>+</span></div>
                    <div class="faq-answer">Você receberá o ebook em formato PDF por email imediatamente após a confirmação do pagamento.</div>
                </div>
                <div class="faq-item">
                    <div class="faq-question">O ebook serve para vegetarianos? <span>+</span></div>
                    <div class="faq-answer">Sim, o ebook inclui opções vegetarianas e veganas para todas as refeições.</div>
                </div>
                <div class="faq-item">
                    <div class="faq-question">Posso usar o ebook se tenho restrições alimentares? <span>+</span></div>
                    <div class="faq-answer">Sim, o ebook oferece alternativas para as principais restrições alimentares como lactose, glúten e açúcar.</div>
                </div>
            </div>
        </div>
        
        <footer>
            <p>© 2023 Planejador de Caminhada para Peso Ideal. Todos os direitos reservados.</p>
            <p>Este site não substitui orientação médica profissional. Consulte um médico antes de iniciar qualquer programa de exercícios.</p>
        </footer>
    </div>

    <script>
        // Atualizar progresso
        function updateProgress(step) {
            const steps = document.querySelectorAll('.progress-step');
            steps.forEach((s, index) => {
                if (index < step) {
                    s.classList.add('step-completed');
                    s.classList.remove('step-active');
                } else if (index === step) {
                    s.classList.add('step-active');
                    s.classList.remove('step-completed');
                } else {
                    s.classList.remove('step-active', 'step-completed');
                }
            });
        }
        
        // Calcular caminhada
        document.getElementById('calculator-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Coletar dados do formulário
            const gender = document.getElementById('gender').value;
            const age = parseInt(document.getElementById('age').value);
            const height = parseInt(document.getElementById('height').value);
            const weight = parseFloat(document.getElementById('weight').value);
            const activity = parseFloat(document.getElementById('activity').value);
            
            // Calcular IMC atual
            const heightInMeters = height / 100;
            const currentBMI = weight / (heightInMeters * heightInMeters);
            
            // Definir peso ideal (IMC entre 18.5 e 24.9)
            const idealWeightMin = 18.5 * (heightInMeters * heightInMeters);
            const idealWeightMax = 24.9 * (heightInMeters * heightInMeters);
            
            // Calcular peso ideal médio
            const idealWeight = (idealWeightMin + idealWeightMax) / 2;
            
            // Calcular diferença de peso
            const weightDifference = weight - idealWeight;
            
            // Calcular calorias necessárias para perder o peso
            // 1kg de gordura = aproximadamente 7700 calorias
            const totalCaloriesToLose = weightDifference * 7700;
            
            // Calcular calorias queimadas por minuto de caminhada
            // Uma pessoa de 70kg queima aproximadamente 4 calorias por minuto caminhando
            const caloriesPerMinuteWalking = (weight / 70) * 4;
            
            // Calcular minutos de caminhada necessários
            let walkingMinutes = Math.round(totalCaloriesToLose / caloriesPerMinuteWalking);
            
            // Considerar o tempo para perder o peso de forma saudável (0.5-1kg por semana)
            const weeksToLose = weightDifference / 0.5; // Considerando perda de 0.5kg por semana
            const daysToLose = weeksToLose * 7;
            
            // Ajustar minutos diários de caminhada
            walkingMinutes = Math.round(walkingMinutes / daysToLose);
            
            // Garantir um valor mínimo e máximo razoável
            walkingMinutes = Math.max(20, Math.min(walkingMinutes, 120));
            
            // Exibir resultado
            document.getElementById('walking-result').textContent = walkingMinutes + ' minutos';
            document.getElementById('result-description').textContent = 
                `Para alcançar seu peso ideal de ${idealWeight.toFixed(1)}kg de forma saudável, ` +
                `recomendamos caminhar ${walkingMinutes} minutos por dia. ` +
                `Este plano considera uma perda de peso gradual de aproximadamente 0.5kg por semana.`;
            
            // Mostrar resultado e esconder formulário
            document.getElementById('form-container').style.display = 'none';
            document.getElementById('result-container').style.display = 'block';
            updateProgress(1);
        });
        
        // Mostrar ebook
        document.getElementById('show-ebook').addEventListener('click', function() {
            document.getElementById('result-container').style.display = 'none';
            document.getElementById('checkout-container').style.display = 'block';
            updateProgress(2);
        });
        
        // Voltar ao formulário
        document.getElementById('back-to-form').addEventListener('click', function() {
            document.getElementById('result-container').style.display = 'none';
            document.getElementById('form-container').style.display = 'block';
            updateProgress(0);
        });
        
        // Voltar ao resultado
        document.getElementById('back-to-result').addEventListener('click', function() {
            document.getElementById('checkout-container').style.display = 'none';
            document.getElementById('result-container').style.display = 'block';
            updateProgress(1);
        });
        
        // Comprar agora
        document.getElementById('buy-now').addEventListener('click', function() {
            alert('Obrigado pelo seu interesse! Em uma implementação real, você seria redirecionado para uma página de checkout segura.');
            // Em um site real, aqui seria o redirecionamento para o checkout
            // window.location.href = 'https://exemplo.com/checkout';
        });
        
        // FAQ
        document.querySelectorAll('.faq-question').forEach(question => {
            question.addEventListener('click', () => {
                const answer = question.nextElementSibling;
                const isVisible = answer.style.display === 'block';
                
                // Fechar todas as respostas
                document.querySelectorAll('.faq-answer').forEach(ans => {
                    ans.style.display = 'none';
                });
                
                // Abrir/fechar a resposta clicada
                answer.style.display = isVisible ? 'none' : 'block';
                
                // Atualizar ícones
                document.querySelectorAll('.faq-question span').forEach(span => {
                    span.textContent = '+';
                });
                
                if (!isVisible) {
                    question.querySelector('span').textContent = '-';
                }
            });
        });
    </script>
</body>
</html>
