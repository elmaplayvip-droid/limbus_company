<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Конструктор договоров | DocConstructor</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            --secondary-gradient: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            --success-gradient: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
            --card-shadow: 0 10px 40px rgba(0,0,0,0.1);
            --card-hover: 0 20px 60px rgba(0,0,0,0.15);
            --border-radius: 16px;
            --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
            line-height: 1.6;
        }

        /* Header */
        header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 20px rgba(0,0,0,0.1);
        }

        .header-content {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1.5rem;
            font-weight: 700;
            color: #667eea;
            text-decoration: none;
        }

        .logo-icon {
            font-size: 2rem;
        }

        /* Hero Section */
        .hero {
            text-align: center;
            padding: 60px 20px 40px;
            color: white;
        }

        .hero h1 {
            font-size: 3rem;
            font-weight: 800;
            margin-bottom: 16px;
            text-shadow: 0 2px 10px rgba(0,0,0,0.2);
        }

        .hero p {
            font-size: 1.25rem;
            opacity: 0.95;
            max-width: 600px;
            margin: 0 auto;
        }

        /* Stats Grid */
        .stats-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px 40px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .stat-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 24px;
            text-align: center;
            box-shadow: var(--card-shadow);
            transition: var(--transition);
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--card-hover);
        }

        .stat-icon {
            font-size: 2.5rem;
            margin-bottom: 12px;
        }

        .stat-value {
            font-size: 2.5rem;
            font-weight: 800;
            background: var(--primary-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .stat-label {
            color: #666;
            font-size: 0.9rem;
            font-weight: 500;
            margin-top: 8px;
        }

        /* Features Section */
        .features {
            max-width: 1200px;
            margin: 0 auto 40px;
            padding: 0 20px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .feature-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: var(--border-radius);
            padding: 24px;
            display: flex;
            align-items: flex-start;
            gap: 16px;
            box-shadow: var(--card-shadow);
            transition: var(--transition);
        }

        .feature-card:hover {
            transform: translateY(-3px);
            box-shadow: var(--card-hover);
        }

        .feature-icon {
            font-size: 2rem;
            flex-shrink: 0;
        }

        .feature-content h3 {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 8px;
            color: #333;
        }

        .feature-content p {
            font-size: 0.9rem;
            color: #666;
        }

        /* Main Content */
        .main-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px 60px;
        }

        .content-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
        }

        @media (max-width: 1024px) {
            .content-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Form Section */
        .form-card, .preview-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 40px;
            box-shadow: var(--card-shadow);
            transition: var(--transition);
        }

        .section-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 3px solid #667eea;
        }

        .section-header h2 {
            font-size: 1.5rem;
            font-weight: 700;
            color: #333;
        }

        .section-icon {
            font-size: 1.8rem;
        }

        .form-group {
            margin-bottom: 24px;
        }

        .form-group label {
            display: block;
            margin-bottom: 10px;
            color: #555;
            font-weight: 600;
            font-size: 0.95rem;
        }

        .required::after {
            content: " *";
            color: #e74c3c;
        }

        input[type="text"],
        input[type="number"],
        input[type="date"],
        select,
        textarea {
            width: 100%;
            padding: 14px 18px;
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            font-size: 1rem;
            transition: var(--transition);
            font-family: inherit;
            background: #fafafa;
        }

        input:focus,
        select:focus,
        textarea:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 4px rgba(102, 126, 234, 0.15);
            background: white;
        }

        textarea {
            resize: vertical;
            min-height: 100px;
        }

        /* Role Selector */
        .role-selector {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 12px;
            margin-bottom: 15px;
        }

        .role-option {
            padding: 16px;
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            text-align: center;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 500;
            background: #fafafa;
        }

        .role-option:hover {
            border-color: #667eea;
            background: #f0f3ff;
            transform: translateY(-2px);
        }

        .role-option.active {
            border-color: #667eea;
            background: var(--primary-gradient);
            color: white;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
        }

        /* Contract Info */
        .contract-type-info {
            background: linear-gradient(135deg, #e8f4f8 0%, #f0e8f8 100%);
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 24px;
            border-left: 4px solid #667eea;
            animation: slideIn 0.3s ease;
        }

        .contract-type-info h3 {
            color: #667eea;
            margin-bottom: 8px;
            font-size: 1.1rem;
        }

        .contract-type-info p {
            color: #666;
            font-size: 0.9rem;
        }

        /* Checkboxes */
        .checkbox-group {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-top: 16px;
            padding: 12px;
            background: #f8f9fa;
            border-radius: 10px;
        }

        .checkbox-group input[type="checkbox"] {
            width: 22px;
            height: 22px;
            cursor: pointer;
            accent-color: #667eea;
        }

        .checkbox-group label {
            margin: 0;
            cursor: pointer;
            font-weight: 500;
            color: #555;
        }

        /* Buttons */
        .button-group {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin-top: 28px;
        }

        button {
            padding: 14px 28px;
            border: none;
            border-radius: 12px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            display: inline-flex;
            align-items: center;
            gap: 10px;
            font-family: inherit;
        }

        .btn-primary {
            background: var(--primary-gradient);
            color: white;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.5);
        }

        .btn-success {
            background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);
            color: white;
            box-shadow: 0 4px 15px rgba(17, 153, 142, 0.4);
        }

        .btn-success:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(17, 153, 142, 0.5);
        }

        .btn-warning {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            box-shadow: 0 4px 15px rgba(245, 87, 108, 0.4);
        }

        .btn-warning:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(245, 87, 108, 0.5);
        }

        .btn-secondary {
            background: linear-gradient(135deg, #bdc3c7 0%, #2c3e50 100%);
            color: white;
            box-shadow: 0 4px 15px rgba(44, 62, 80, 0.3);
        }

        .btn-secondary:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(44, 62, 80, 0.4);
        }

        /* Preview Box */
        .preview-box {
            background: linear-gradient(135deg, #f8f9fa 0%, #ffffff 100%);
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            padding: 30px;
            min-height: 500px;
            white-space: pre-wrap;
            font-family: 'Times New Roman', Times, serif;
            font-size: 1.1em;
            line-height: 1.8;
            color: #333;
            overflow-y: auto;
            max-height: 700px;
            transition: var(--transition);
        }

        .preview-box:hover {
            border-color: #667eea;
        }

        .preview-box.empty {
            color: #999;
            font-style: italic;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            font-family: 'Inter', sans-serif;
            font-size: 1rem;
        }

        /* Success Message */
        .success-message {
            background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);
            color: white;
            padding: 16px 24px;
            border-radius: 12px;
            margin-bottom: 24px;
            display: none;
            animation: slideIn 0.3s ease;
            font-weight: 500;
        }

        .success-message.show {
            display: block;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Error States */
        .error-message {
            color: #e74c3c;
            font-size: 0.85rem;
            margin-top: 8px;
            display: none;
            font-weight: 500;
        }

        .error-message.show {
            display: block;
        }

        .input-error {
            border-color: #e74c3c !important;
            background: #fef5f5 !important;
        }

        /* Footer */
        footer {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 30px 20px;
            text-align: center;
            color: #666;
            font-size: 0.9rem;
        }

        footer a {
            color: #667eea;
            text-decoration: none;
            font-weight: 600;
        }

        footer a:hover {
            text-decoration: underline;
        }

        /* Print Styles */
        @media print {
            body {
                background: white !important;
                padding: 0 !important;
            }

            header, 
            .hero, 
            .stats-container, 
            .features, 
            .form-card, 
            .button-group, 
            footer {
                display: none !important;
            }

            .main-container {
                max-width: 100% !important;
                padding: 0 !important;
                margin: 0 !important;
            }

            .content-grid {
                display: block !important;
            }

            .preview-card {
                box-shadow: none !important;
                padding: 0 !important;
                margin: 0 !important;
                background: none !important;
            }

            .preview-box {
                border: none !important;
                max-height: none !important;
                overflow: visible !important;
                padding: 0 !important;
                margin: 0 !important;
                background: none !important;
            }

            .section-header {
                display: none !important;
            }

            .success-message {
                display: none !important;
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2rem;
            }

            .hero p {
                font-size: 1rem;
            }

            .form-card, .preview-card {
                padding: 24px;
            }

            .button-group {
                flex-direction: column;
            }

            button {
                width: 100%;
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="header-content">
            <a href="#" class="logo">
                <span class="logo-icon">📄</span>
                <span>DocConstructor</span>
            </a>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <h1>Создайте юридически грамотный договор за 2 минуты</h1>
        <p>Профессиональный конструктор договоров для бизнеса и частных лиц</p>
    </section>

    <!-- Stats -->
    <div class="stats-container">
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-icon">📊</div>
                <div class="stat-value" id="contractCount">0</div>
                <div class="stat-label">Создано договоров</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">📝</div>
                <div class="stat-value" id="wordCount">0</div>
                <div class="stat-label">Слов в договоре</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">🔤</div>
                <div class="stat-value" id="charCount">0</div>
                <div class="stat-label">Символов</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">⚡</div>
                <div class="stat-value">4</div>
                <div class="stat-label">Типа договоров</div>
            </div>
        </div>
    </div>

    <!-- Features -->
    <div class="features">
        <div class="feature-card">
            <div class="feature-icon">🚀</div>
            <div class="feature-content">
                <h3>Быстро</h3>
                <p>Заполните форму и получите готовый договор за пару минут</p>
            </div>
        </div>
        <div class="feature-card">
            <div class="feature-icon">🛡️</div>
            <div class="feature-content">
                <h3>Надёжно</h3>
                <p>Шаблоны соответствуют законодательству РФ</p>
            </div>
        </div>
        <div class="feature-card">
            <div class="feature-icon">💾</div>
            <div class="feature-content">
                <h3>Удобно</h3>
                <p>Экспорт в TXT, копирование и печать в один клик</p>
            </div>
        </div>
        <div class="feature-card">
            <div class="feature-icon">🔄</div>
            <div class="feature-content">
                <h3>Автосохранение</h3>
                <p>Данные формы сохраняются автоматически</p>
            </div>
        </div>
    </div>

    <!-- Main Content -->
    <div class="main-container">
        <div class="content-grid">
            <!-- Form Section -->
            <div class="form-card">
                <div class="section-header">
                    <span class="section-icon">📝</span>
                    <h2>Параметры договора</h2>
                </div>

                <div class="success-message" id="successMessage">
                    ✅ Текст договора скопирован в буфер обмена!
                </div>

                <div class="form-group">
                    <label for="contractType" class="required">Тип договора</label>
                    <select id="contractType" required>
                        <option value="">Выберите тип договора...</option>
                        <option value="service">Договор оказания услуг</option>
                        <option value="sale">Договор купли-продажи</option>
                        <option value="rent">Договор аренды</option>
                        <option value="contract">Договор подряда</option>
                    </select>
                    <div class="error-message" id="contractTypeError">Выберите тип договора</div>
                </div>

                <div class="contract-type-info" id="contractTypeInfo" style="display: none;">
                    <h3 id="infoTitle"></h3>
                    <p id="infoText"></p>
                </div>

                <div class="form-group">
                    <label>Роли сторон</label>
                    <div class="role-selector">
                        <div class="role-option active" data-party1="Исполнитель" data-party2="Заказчик" onclick="selectRole(this)">
                            🤝 Исполнитель / Заказчик
                        </div>
                        <div class="role-option" data-party1="Продавец" data-party2="Покупатель" onclick="selectRole(this)">
                            🛒 Продавец / Покупатель
                        </div>
                        <div class="role-option" data-party1="Арендодатель" data-party2="Арендатор" onclick="selectRole(this)">
                            🏠 Арендодатель / Арендатор
                        </div>
                        <div class="role-option" data-party1="Подрядчик" data-party2="Заказчик" onclick="selectRole(this)">
                            🔨 Подрядчик / Заказчик
                        </div>
                    </div>
                </div>

                <div class="form-group">
                    <label for="party1" class="required">Сторона 1 (<span id="role1Label">Исполнитель</span>)</label>
                    <input type="text" id="party1" placeholder="Например: Иванов Иван Иванович или ООО «Компания»" required>
                    <div class="error-message" id="party1Error">Введите данные первой стороны</div>
                </div>

                <div class="form-group">
                    <label for="party2" class="required">Сторона 2 (<span id="role2Label">Заказчик</span>)</label>
                    <input type="text" id="party2" placeholder="Например: Петров Петр Петрович или ООО «Партнер»" required>
                    <div class="error-message" id="party2Error">Введите данные второй стороны</div>
                </div>

                <div class="form-group">
                    <label for="subject" class="required">Предмет договора</label>
                    <textarea id="subject" placeholder="Опишите предмет договора (например: выполнение консультационных услуг, передача товара и т.д.)" required></textarea>
                    <div class="error-message" id="subjectError">Опишите предмет договора</div>
                </div>

                <div class="form-group">
                    <label for="amount" class="required">Сумма договора (руб.)</label>
                    <input type="number" id="amount" placeholder="Например: 100000" min="0" step="0.01" required>
                    <div class="error-message" id="amountError">Введите сумму договора</div>
                </div>

                <div class="form-group">
                    <label for="date" class="required">Дата заключения</label>
                    <input type="date" id="date" required>
                    <div class="error-message" id="dateError">Выберите дату заключения</div>
                </div>

                <div class="form-group">
                    <label for="period" class="required">Срок исполнения</label>
                    <input type="text" id="period" placeholder="Например: 30 календарных дней" required>
                    <div class="error-message" id="periodError">Укажите срок исполнения</div>
                </div>

                <div class="form-group">
                    <label for="city" class="required">Город заключения</label>
                    <input type="text" id="city" placeholder="Например: Москва" required>
                    <div class="error-message" id="cityError">Укажите город заключения</div>
                </div>

                <div class="checkbox-group">
                    <input type="checkbox" id="includePayment" checked>
                    <label for="includePayment">📌 Включить раздел об оплате</label>
                </div>

                <div class="checkbox-group">
                    <input type="checkbox" id="includeResponsibility" checked>
                    <label for="includeResponsibility">⚖️ Включить раздел об ответственности</label>
                </div>

                <div class="button-group">
                    <button class="btn-primary" onclick="generateContract()">
                        <span>📄</span> Сгенерировать договор
                    </button>
                    <button class="btn-success" onclick="copyText()">
                        <span>📋</span> Скопировать текст
                    </button>
                    <button class="btn-warning" onclick="exportToTxt()">
                        <span>💾</span> Экспорт в .txt
                    </button>
                    <button class="btn-secondary" onclick="printContract()">
                        <span>🖨️</span> Печать
                    </button>
                    <button class="btn-secondary" onclick="clearForm()">
                        <span>🗑️</span> Очистить форму
                    </button>
                </div>
            </div>

            <!-- Preview Section -->
            <div class="preview-card">
                <div class="section-header">
                    <span class="section-icon">👁️</span>
                    <h2>Предпросмотр договора</h2>
                </div>
                <div class="preview-box empty" id="previewBox">
                    Заполните форму слева и нажмите кнопку<br>«Сгенерировать договор» для просмотра текста
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <p>© 2024 DocConstructor. Все права защищены.</p>
        <p>Создавайте договоры быстро и профессионально</p>
    </footer>

    <script>
        // Templates for different contract types
        const contractTemplates = {
            service: {
                title: 'ДОГОВОР ОКАЗАНИЯ УСЛУГ',
                description: 'Регулирует отношения между исполнителем и заказчиком по оказанию услуг',
                body: (data) => `
г. ${data.city}
${formatDate(data.date)}

${data.party1}, именуем${getEnding(data.party1, 'ый', 'ая')} в дальнейшем «${data.role1}», и
${data.party2}, именуем${getEnding(data.party2, 'ый', 'ая')} в дальнейшем «${data.role2}»,
вместе именуемые «Стороны», заключили настоящий договор о нижеследующем:

1. ПРЕДМЕТ ДОГОВОРА

1.1. ${data.role1} обязуется оказать ${data.subject}, а ${data.role2} обязуется принять и оплатить эти услуги.

1.2. Срок оказания услуг: ${data.period}.

2. СТОИМОСТЬ УСЛУГ И ПОРЯДОК ОПЛАТЫ

2.1. Стоимость услуг по настоящему договору составляет ${formatNumber(data.amount)} ( ${numberToWords(data.amount)} ) рублей.

2.2. Оплата производится ${data.role2} в течение 5 (пяти) банковских дней с момента подписания настоящего договора.

2.3. Оплата производится путем перечисления денежных средств на расчетный счет ${data.role1}.

${data.includeResponsibility ? `
3. ОТВЕТСТВЕННОСТЬ СТОРОН

3.1. За неисполнение или ненадлежащее исполнение обязательств по настоящему договору Стороны несут ответственность в соответствии с действующим законодательством Российской Федерации.

3.2. ${data.role1} несет ответственность за качество оказываемых услуг.

3.3. ${data.role2} несет ответственность за своевременную оплату услуг.
` : ''}

4. ЗАКЛЮЧИТЕЛЬНЫЕ ПОЛОЖЕНИЯ

4.1. Настоящий договор вступает в силу с момента его подписания и действует до полного исполнения Сторонами своих обязательств.

4.2. Все изменения и дополнения к настоящему договору действительны только в письменной форме и должны быть подписаны обеими Сторонами.

4.3. Настоящий договор составлен в двух экземплярах, имеющих одинаковую юридическую силу, по одному для каждой из Сторон.

5. АДРЕСА, РЕКВИЗИТЫ И ПОДПИСИ СТОРОН

${data.role1}:
${data.party1}

${data.role2}:
${data.party2}
`
            },
            sale: {
                title: 'ДОГОВОР КУПЛИ-ПРОДАЖИ',
                description: 'Регулирует отношения по продаже и покупке товара',
                body: (data) => `
г. ${data.city}
${formatDate(data.date)}

${data.party1}, именуем${getEnding(data.party1, 'ый', 'ая')} в дальнейшем «${data.role1}», и
${data.party2}, именуем${getEnding(data.party2, 'ый', 'ая')} в дальнейшем «${data.role2}»,
вместе именуемые «Стороны», заключили настоящий договор о нижеследующем:

1. ПРЕДМЕТ ДОГОВОРА

1.1. ${data.role1} обязуется передать в собственность ${data.subject}, а ${data.role2} обязуется принять этот товар и оплатить его.

1.2. Срок передачи товара: ${data.period}.

2. ЦЕНА ДОГОВОРА И ПОРЯДОК РАСЧЕТОВ

2.1. Цена товара по настоящему договору составляет ${formatNumber(data.amount)} ( ${numberToWords(data.amount)} ) рублей.

2.2. Оплата производится ${data.role2} в течение 5 (пяти) банковских дней с момента передачи товара.

2.3. Право собственности на товар переходит к ${data.role2} с момента полной оплаты.

${data.includeResponsibility ? `
3. ОТВЕТСТВЕННОСТЬ СТОРОН

3.1. За неисполнение или ненадлежащее исполнение обязательств по настоящему договору Стороны несут ответственность в соответствии с действующим законодательством Российской Федерации.

3.2. ${data.role1} несет ответственность за качество передаваемого товара.

3.3. ${data.role2} несет ответственность за своевременную оплату товара.
` : ''}

4. ЗАКЛЮЧИТЕЛЬНЫЕ ПОЛОЖЕНИЯ

4.1. Настоящий договор вступает в силу с момента его подписания и действует до полного исполнения Сторонами своих обязательств.

4.2. Все изменения и дополнения к настоящему договору действительны только в письменной форме.

4.3. Настоящий договор составлен в двух экземплярах, имеющих одинаковую юридическую силу.

5. АДРЕСА, РЕКВИЗИТЫ И ПОДПИСИ СТОРОН

${data.role1}:
${data.party1}

${data.role2}:
${data.party2}
`
            },
            rent: {
                title: 'ДОГОВОР АРЕНДЫ',
                description: 'Регулирует отношения по аренде имущества',
                body: (data) => `
г. ${data.city}
${formatDate(data.date)}

${data.party1}, именуем${getEnding(data.party1, 'ый', 'ая')} в дальнейшем «${data.role1}», и
${data.party2}, именуем${getEnding(data.party2, 'ый', 'ая')} в дальнейшем «${data.role2}»,
вместе именуемые «Стороны», заключили настоящий договор о нижеследующем:

1. ПРЕДМЕТ ДОГОВОРА

1.1. ${data.role1} передает во временное владение и пользование ${data.subject}, а ${data.role2} принимает это имущество и обязуется вносить арендную плату.

1.2. Срок аренды: ${data.period}.

2. АРЕНДНАЯ ПЛАТА И ПОРЯДОК РАСЧЕТОВ

2.1. Размер арендной платы составляет ${formatNumber(data.amount)} ( ${numberToWords(data.amount)} ) рублей.

2.2. Арендная плата вносится ${data.role2} ежемесячно не позднее 5-го числа текущего месяца.

2.3. Оплата производится путем перечисления денежных средств на расчетный счет ${data.role1}.

${data.includeResponsibility ? `
3. ОТВЕТСТВЕННОСТЬ СТОРОН

3.1. За неисполнение или ненадлежащее исполнение обязательств по настоящему договору Стороны несут ответственность в соответствии с действующим законодательством Российской Федерации.

3.2. ${data.role1} несет ответственность за передачу имущества в надлежащем состоянии.

3.3. ${data.role2} несет ответственность за сохранность арендованного имущества и своевременную оплату.
` : ''}

4. ЗАКЛЮЧИТЕЛЬНЫЕ ПОЛОЖЕНИЯ

4.1. Настоящий договор вступает в силу с момента его подписания.

4.2. ${data.role2} имеет преимущественное право на заключение договора аренды на новый срок.

4.3. Настоящий договор составлен в двух экземплярах.

5. АДРЕСА, РЕКВИЗИТЫ И ПОДПИСИ СТОРОН

${data.role1}:
${data.party1}

${data.role2}:
${data.party2}
`
            },
            contract: {
                title: 'ДОГОВОР ПОДРЯДА',
                description: 'Регулирует отношения по выполнению подрядных работ',
                body: (data) => `
г. ${data.city}
${formatDate(data.date)}

${data.party1}, именуем${getEnding(data.party1, 'ый', 'ая')} в дальнейшем «${data.role1}», и
${data.party2}, именуем${getEnding(data.party2, 'ый', 'ая')} в дальнейшем «${data.role2}»,
вместе именуемые «Стороны», заключили настоящий договор о нижеследующем:

1. ПРЕДМЕТ ДОГОВОРА

1.1. ${data.role1} обязуется выполнить ${data.subject}, а ${data.role2} обязуется принять результат работы и оплатить его.

1.2. Срок выполнения работ: ${data.period}.

2. ЦЕНА РАБОТ И ПОРЯДОК РАСЧЕТОВ

2.1. Цена работ по настоящему договору составляет ${formatNumber(data.amount)} ( ${numberToWords(data.amount)} ) рублей.

2.2. Оплата производится ${data.role2} в течение 5 (пяти) банковских дней с момента подписания акта сдачи-приемки работ.

2.3. Оплата производится путем перечисления денежных средств на расчетный счет ${data.role1}.

${data.includeResponsibility ? `
3. ОТВЕТСТВЕННОСТЬ СТОРОН

3.1. За неисполнение или ненадлежащее исполнение обязательств по настоящему договору Стороны несут ответственность в соответствии с действующим законодательством Российской Федерации.

3.2. ${data.role1} несет ответственность за качество выполняемых работ и соблюдение сроков.

3.3. ${data.role2} несет ответственность за своевременную оплату выполненных работ.
` : ''}

4. ЗАКЛЮЧИТЕЛЬНЫЕ ПОЛОЖЕНИЯ

4.1. Настоящий договор вступает в силу с момента его подписания и действует до полного исполнения Сторонами своих обязательств.

4.2. Все изменения и дополнения к настоящему договору действительны только в письменной форме.

4.3. Настоящий договор составлен в двух экземплярах, имеющих одинаковую юридическую силу.

5. АДРЕСА, РЕКВИЗИТЫ И ПОДПИСИ СТОРОН

${data.role1}:
${data.party1}

${data.role2}:
${data.party2}
`
            }
        };

        let currentRole1 = 'Исполнитель';
        let currentRole2 = 'Заказчик';
        let contractsCreated = 0;

        // Initialize date with today
        document.getElementById('date').valueAsDate = new Date();

        function selectRole(element) {
            document.querySelectorAll('.role-option').forEach(opt => opt.classList.remove('active'));
            element.classList.add('active');
            currentRole1 = element.dataset.party1;
            currentRole2 = element.dataset.party2;
            document.getElementById('role1Label').textContent = currentRole1;
            document.getElementById('role2Label').textContent = currentRole2;
        }

        function getEnding(party, male, female) {
            if (party.match(/(а$|я$)/i) && !party.match(/(ООО|АО|ИП)/i)) {
                return female;
            }
            return male;
        }

        function formatDate(dateString) {
            const date = new Date(dateString);
            const options = { day: 'numeric', month: 'long', year: 'numeric' };
            return date.toLocaleDateString('ru-RU', options);
        }

        function formatNumber(num) {
            return parseFloat(num).toLocaleString('ru-RU');
        }

        function numberToWords(num) {
            const n = parseFloat(num);
            if (isNaN(n)) return 'ноль';

            const ones = ['', 'один', 'два', 'три', 'четыре', 'пять', 'шесть', 'семь', 'восемь', 'девять'];
            const teens = ['десять', 'одиннадцать', 'двенадцать', 'тринадцать', 'четырнадцать', 'пятнадцать', 'шестнадцать', 'семнадцать', 'восемнадцать', 'девятнадцать'];
            const tens = ['', '', 'двадцать', 'тридцать', 'сорок', 'пятьдесят', 'шестьдесят', 'семьдесят', 'восемьдесят', 'девяносто'];
            const hundreds = ['', 'сто', 'двести', 'триста', 'четыреста', 'пятьсот', 'шестьсот', 'семьсот', 'восемьсот', 'девятьсот'];

            if (n === 0) return 'ноль';

            let words = '';
            let number = Math.floor(n);

            if (number >= 1000000) {
                words += hundreds[Math.floor(number / 100000) % 10] + ' ';
            }

            if (number >= 1000) {
                words += Math.floor(number / 1000) + ' тысяч ';
                number %= 1000;
            }

            if (number >= 100) {
                words += hundreds[Math.floor(number / 100)] + ' ';
                number %= 100;
            }

            if (number >= 20) {
                words += tens[Math.floor(number / 10)] + ' ';
                number %= 10;
            } else if (number >= 10) {
                words += teens[number - 10] + ' ';
                number = 0;
            }

            if (number > 0) {
                words += ones[number] + ' ';
            }

            return words.trim() + ' рублей';
        }

        function validateForm() {
            let isValid = true;
            const fields = ['contractType', 'party1', 'party2', 'subject', 'amount', 'date', 'period', 'city'];

            fields.forEach(field => {
                const element = document.getElementById(field);
                const errorElement = document.getElementById(field + 'Error');

                if (!element.value.trim()) {
                    element.classList.add('input-error');
                    if (errorElement) errorElement.classList.add('show');
                    isValid = false;
                } else {
                    element.classList.remove('input-error');
                    if (errorElement) errorElement.classList.remove('show');
                }
            });

            return isValid;
        }

        function generateContract() {
            if (!validateForm()) {
                alert('Пожалуйста, заполните все обязательные поля!');
                return;
            }

            const contractType = document.getElementById('contractType').value;
            const template = contractTemplates[contractType];

            const data = {
                party1: document.getElementById('party1').value,
                party2: document.getElementById('party2').value,
                subject: document.getElementById('subject').value,
                amount: document.getElementById('amount').value,
                date: document.getElementById('date').value,
                period: document.getElementById('period').value,
                city: document.getElementById('city').value,
                role1: currentRole1,
                role2: currentRole2,
                includePayment: document.getElementById('includePayment').checked,
                includeResponsibility: document.getElementById('includeResponsibility').checked
            };

            const contractText = `${template.title}\n\n${template.body(data)}`;

            const previewBox = document.getElementById('previewBox');
            previewBox.textContent = contractText;
            previewBox.classList.remove('empty');

            contractsCreated++;
            document.getElementById('contractCount').textContent = contractsCreated;
            updateStats(contractText);

            const infoDiv = document.getElementById('contractTypeInfo');
            document.getElementById('infoTitle').textContent = template.title;
            document.getElementById('infoText').textContent = template.description;
            infoDiv.style.display = 'block';

            previewBox.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
        }

        function updateStats(text) {
            const words = text.trim().split(/\s+/).length;
            const chars = text.length;

            document.getElementById('wordCount').textContent = words;
            document.getElementById('charCount').textContent = chars;
        }

        function copyText() {
            const previewBox = document.getElementById('previewBox');
            if (previewBox.classList.contains('empty')) {
                alert('Сначала сгенерируйте договор!');
                return;
            }

            navigator.clipboard.writeText(previewBox.textContent).then(() => {
                const successMsg = document.getElementById('successMessage');
                successMsg.classList.add('show');
                setTimeout(() => {
                    successMsg.classList.remove('show');
                }, 3000);
            }).catch(err => {
                const textArea = document.createElement('textarea');
                textArea.value = previewBox.textContent;
                document.body.appendChild(textArea);
                textArea.select();
                document.execCommand('copy');
                document.body.removeChild(textArea);

                const successMsg = document.getElementById('successMessage');
                successMsg.classList.add('show');
                setTimeout(() => {
                    successMsg.classList.remove('show');
                }, 3000);
            });
        }

        function exportToTxt() {
            const previewBox = document.getElementById('previewBox');
            if (previewBox.classList.contains('empty')) {
                alert('Сначала сгенерируйте договор!');
                return;
            }

            const text = previewBox.textContent;
            const blob = new Blob([text], { type: 'text/plain;charset=utf-8' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `Договор_${new Date().toISOString().split('T')[0]}.txt`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
        }

        function printContract() {
            const previewBox = document.getElementById('previewBox');
            if (previewBox.classList.contains('empty')) {
                alert('Сначала сгенерируйте договор!');
                return;
            }
            window.print();
        }

        function clearForm() {
            if (confirm('Вы уверены, что хотите очистить форму?')) {
                document.querySelectorAll('input[type="text"], input[type="number"], input[type="date"], textarea').forEach(input => {
                    input.value = '';
                });
                document.getElementById('date').valueAsDate = new Date();
                document.getElementById('previewBox').textContent = 'Заполните форму слева и нажмите кнопку\n«Сгенерировать договор» для просмотра текста';
                document.getElementById('previewBox').classList.add('empty');
                document.getElementById('contractTypeInfo').style.display = 'none';
                document.querySelectorAll('.input-error').forEach(el => el.classList.remove('input-error'));
                document.querySelectorAll('.error-message.show').forEach(el => el.classList.remove('show'));
            }
        }

        window.addEventListener('beforeunload', () => {
            const formData = {
                contractType: document.getElementById('contractType').value,
                party1: document.getElementById('party1').value,
                party2: document.getElementById('party2').value,
                subject: document.getElementById('subject').value,
                amount: document.getElementById('amount').value,
                date: document.getElementById('date').value,
                period: document.getElementById('period').value,
                city: document.getElementById('city').value
            };
            localStorage.setItem('contractFormData', JSON.stringify(formData));
        });

        window.addEventListener('load', () => {
            const saved = localStorage.getItem('contractFormData');
            if (saved) {
                const formData = JSON.parse(saved);
                Object.keys(formData).forEach(key => {
                    const element = document.getElementById(key);
                    if (element && formData[key]) {
                        element.value = formData[key];
                    }
                });
            }
        });

        document.querySelectorAll('input, select, textarea').forEach(input => {
            input.addEventListener('input', function() {
                if (this.value.trim()) {
                    this.classList.remove('input-error');
                    const errorEl = document.getElementById(this.id + 'Error');
                    if (errorEl) errorEl.classList.remove('show');
                }
            });
        });
    </script>
</body>
</html>


