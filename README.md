<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Эржанчик | C++ System Engineer</title>
    <style>
        /* ===== RESET & BASE ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0e14;
            font-family: 'Fira Code', 'Consolas', 'Courier New', monospace;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
            color: #c0d0e0;
        }

        /* ===== MAIN BOARD ===== */
        .board {
            max-width: 1100px;
            width: 100%;
            background: linear-gradient(145deg, #11181f, #0b1016);
            border: 1px solid #1e2c3a;
            border-radius: 28px;
            padding: 40px 45px 50px;
            box-shadow: 
                0 20px 50px rgba(0, 0, 0, 0.8),
                inset 0 0 80px rgba(0, 180, 255, 0.03);
            backdrop-filter: blur(2px);
            transition: all 0.2s ease;
        }

        /* ===== HEADER ===== */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            flex-wrap: wrap;
            margin-bottom: 28px;
            border-bottom: 1px solid #1f2e3c;
            padding-bottom: 22px;
        }

        .title-group h1 {
            font-size: 2.6rem;
            font-weight: 600;
            letter-spacing: -0.5px;
            background: linear-gradient(135deg, #8abfff, #4af0b0);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 6px;
        }

        .title-group .sub {
            font-size: 0.9rem;
            color: #6a8ba0;
            letter-spacing: 2px;
            text-transform: uppercase;
            font-weight: 300;
        }

        .badge-group {
            display: flex;
            gap: 14px;
            flex-wrap: wrap;
            margin-top: 6px;
        }

        .badge {
            background: #14222e;
            padding: 8px 18px;
            border-radius: 40px;
            font-size: 0.75rem;
            font-weight: 500;
            border: 1px solid #2a4050;
            color: #b0d0e8;
            letter-spacing: 0.3px;
            box-shadow: inset 0 1px 0 rgba(255,255,255,0.04);
        }

        .badge .highlight {
            color: #6ef0b0;
        }

        /* ===== TYPING LINE ===== */
        .typing-line {
            font-size: 1.1rem;
            color: #6ef0b0;
            padding: 14px 0 18px 0;
            border-bottom: 1px dashed #1e2e3c;
            margin-bottom: 30px;
            display: flex;
            align-items: center;
            gap: 10px;
            flex-wrap: wrap;
        }

        .typing-line .cursor {
            display: inline-block;
            width: 12px;
            height: 22px;
            background: #6ef0b0;
            animation: blink 1s step-end infinite;
            border-radius: 2px;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }

        .typing-line .prompt {
            color: #4a7a9a;
            font-weight: 300;
        }

        /* ===== GRID: 2 колонки ===== */
        .grid-2 {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 32px 40px;
            margin-top: 12px;
        }

        /* ===== СЕКЦИИ ===== */
        .section {
            margin-bottom: 8px;
        }

        .section-title {
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 2.5px;
            color: #4a7a9a;
            font-weight: 500;
            margin-bottom: 18px;
            border-left: 3px solid #3a8ab0;
            padding-left: 14px;
        }

        .section-title .icon {
            margin-right: 8px;
            opacity: 0.7;
        }

        /* ===== C++ / C СПИСОК ===== */
        .lang-list {
            display: flex;
            flex-direction: column;
            gap: 14px;
        }

        .lang-item {
            background: #0f181f;
            border-radius: 14px;
            padding: 16px 20px;
            border: 1px solid #1e2e3a;
            transition: 0.2s;
            box-shadow: inset 0 1px 0 rgba(255,255,255,0.02);
        }

        .lang-item:hover {
            border-color: #3a6a8a;
            background: #121d26;
        }

        .lang-item .head {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }

        .lang-item .name {
            font-size: 1.2rem;
            font-weight: 600;
            color: #d0e8f8;
        }

        .lang-item .name .cpp { color: #5f9fd0; }
        .lang-item .name .c { color: #6a8fc0; }

        .lang-item .version {
            font-size: 0.7rem;
            background: #1a2a36;
            padding: 4px 14px;
            border-radius: 30px;
            color: #8ab0c8;
            border: 1px solid #2a4052;
        }

        .lang-item .desc {
            font-size: 0.9rem;
            color: #90aab8;
            line-height: 1.5;
            margin-top: 4px;
        }

        .lang-item .tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 12px;
        }

        .lang-item .tags span {
            background: #14222e;
            padding: 3px 14px;
            border-radius: 30px;
            font-size: 0.65rem;
            color: #7aaac0;
            border: 1px solid #233645;
            letter-spacing: 0.3px;
        }

        .lang-item .tags span.strong {
            color: #6ef0b0;
            border-color: #2a6a5a;
        }

        /* ===== ОСОБЕННОСТИ C++ ===== */
        .feature-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
            margin-top: 6px;
        }

        .feature-card {
            background: #0f181f;
            border-radius: 12px;
            padding: 14px 16px;
            border: 1px solid #1a2a34;
            transition: 0.2s;
        }

        .feature-card:hover {
            border-color: #2a5a70;
        }

        .feature-card .num {
            font-size: 1.6rem;
            font-weight: 600;
            color: #3a8ab0;
            opacity: 0.6;
            line-height: 1;
        }

        .feature-card .label {
            font-size: 0.75rem;
            color: #80a8b8;
            margin-top: 4px;
            letter-spacing: 0.2px;
        }

        /* ===== СТАТИСТИКА ===== */
        .stats-mini {
            display: flex;
            justify-content: space-between;
            gap: 12px;
            margin-top: 18px;
            flex-wrap: wrap;
        }

        .stat-block {
            background: #0f181f;
            border-radius: 14px;
            padding: 14px 20px;
            flex: 1;
            min-width: 80px;
            border: 1px solid #1a2a34;
            text-align: center;
        }

        .stat-block .val {
            font-size: 1.6rem;
            font-weight: 600;
            color: #8ac8e8;
        }

        .stat-block .lbl {
            font-size: 0.65rem;
            text-transform: uppercase;
            color: #5a7a8a;
            letter-spacing: 0.5px;
        }

        /* ===== ФУТЕР ===== */
        .footer {
            margin-top: 38px;
            padding-top: 24px;
            border-top: 1px solid #1a2a34;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 16px;
        }

        .footer .quote {
            font-size: 0.85rem;
            color: #4a7a8a;
            font-style: italic;
        }

        .footer .quote strong {
            color: #7ab8d0;
            font-style: normal;
        }

        .footer .social a {
            color: #5a8aaa;
            text-decoration: none;
            border: 1px solid #1e2e3c;
            padding: 6px 18px;
            border-radius: 40px;
            font-size: 0.8rem;
            transition: 0.2s;
            display: inline-block;
        }

        .footer .social a:hover {
            border-color: #4a8ab0;
            color: #8ac8f0;
            background: #0f1a22;
        }

        /* ===== RESPONSIVE ===== */
        @media (max-width: 820px) {
            .board { padding: 28px 22px 35px; }
            .grid-2 { grid-template-columns: 1fr; gap: 24px; }
            .title-group h1 { font-size: 2rem; }
            .feature-grid { grid-template-columns: 1fr 1fr; }
        }

        @media (max-width: 500px) {
            .header { flex-direction: column; }
            .badge-group { margin-top: 12px; }
            .feature-grid { grid-template-columns: 1fr; }
            .stats-mini { flex-direction: column; }
            .typing-line { font-size: 0.9rem; }
        }

        /* ===== ДОПОЛНИТЕЛЬНЫЙ СТИЛЬ ДЛЯ C++/C ===== */
        .cpp-icon { color: #5f9fd0; }
        .c-icon { color: #6a8fc0; }
        .accent-text { color: #6ef0b0; }

        .divider-light {
            height: 1px;
            background: linear-gradient(90deg, transparent, #1e3240, transparent);
            margin: 22px 0 18px 0;
        }
    </style>
</head>
<body>

<div class="board">

    <!-- ===== HEADER ===== -->
    <div class="header">
        <div class="title-group">
            <h1>Эржанчик</h1>
            <div class="sub">Systems Engineer · C++ / C · Security</div>
        </div>
        <div class="badge-group">
            <span class="badge">⚡ <span class="highlight">C++20</span></span>
            <span class="badge">🔧 <span class="highlight">C11</span></span>
            <span class="badge">🛡️ CMake</span>
            <span class="badge">🧩 Win32 · JNI</span>
        </div>
    </div>

    <!-- ===== TYPING LINE ===== -->
    <div class="typing-line">
        <span class="prompt">$></span>
        <span>Systems Engineer · C++ / C · Low‑level · Security</span>
        <span class="cursor"></span>
    </div>

    <!-- ===== ОСНОВНАЯ СЕТКА ===== -->
    <div class="grid-2">

        <!-- ======= ЛЕВАЯ КОЛОНКА ======= -->
        <div class="col">

            <!-- C++ -->
            <div class="section">
                <div class="section-title"><span class="icon">▸</span> C++</div>
                <div class="lang-list">
                    <div class="lang-item">
                        <div class="head">
                            <span class="name"><span class="cpp">C++</span> / 20</span>
                            <span class="version">std::ranges · constexpr</span>
                        </div>
                        <div class="desc">
                            Высокопроизводительные системы, сетевые сервера (Winsock2, WebSocket), 
                            многопоточность, RAII, умные указатели.
                        </div>
                        <div class="tags">
                            <span>Boost</span>
                            <span>Qt</span>
                            <span>OpenCV</span>
                            <span class="strong">CMake</span>
                            <span>BCrypt</span>
                            <span>SQLite3</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- C -->
            <div class="section" style="margin-top: 8px;">
                <div class="section-title"><span class="icon">▸</span> C</div>
                <div class="lang-list">
                    <div class="lang-item">
                        <div class="head">
                            <span class="name"><span class="c">C</span> / 11</span>
                            <span class="version">ANSI · POSIX</span>
                        </div>
                        <div class="desc">
                            Системное программирование, работа с памятью, Win32 API, 
                            взаимодействие с железом, эмбедded‑подходы.
                        </div>
                        <div class="tags">
                            <span>Win32 API</span>
                            <span>JNI</span>
                            <span>libcurl</span>
                            <span>miniz</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Доп. фичи C++ / C -->
            <div class="section" style="margin-top: 18px;">
                <div class="section-title"><span class="icon">▸</span> ключевые возможности</div>
                <div class="feature-grid">
                    <div class="feature-card">
                        <div class="num">⚡</div>
                        <div class="label">Низкоуровневая оптимизация</div>
                    </div>
                    <div class="feature-card">
                        <div class="num">🧠</div>
                        <div class="label">In‑memory выполнение</div>
                    </div>
                    <div class="feature-card">
                        <div class="num">🔐</div>
                        <div class="label">AES‑256 · SHA‑256 · PBKDF2</div>
                    </div>
                    <div class="feature-card">
                        <div class="num">🛡️</div>
                        <div class="label">Анти‑отладка · Anti‑VM</div>
                    </div>
                </div>
            </div>

        </div>

        <!-- ======= ПРАВАЯ КОЛОНКА ======= -->
        <div class="col">

            <!-- Обо мне (кратко) -->
            <div class="section">
                <div class="section-title"><span class="icon">▸</span> обо мне</div>
                <div style="background: #0f181f; border-radius: 14px; padding: 18px 20px; border: 1px solid #1a2a34;">
                    <p style="line-height: 1.7; color: #90aab8; font-size: 0.95rem;">
                        Системный инженер с фокусом на <strong style="color: #6ef0b0;">C++</strong> и <strong style="color: #6a8fc0;">C</strong>. 
                        Разрабатываю высокопроизводительные сетевые сервера, защищённые загрузчики, 
                        PWA‑приложения и бэкенд на FastAPI.
                    </p>
                    <p style="line-height: 1.7; color: #90aab8; font-size: 0.95rem; margin-top: 10px;">
                        🧩 Работаю с <strong style="color: #8ac8e8;">Win32 API</strong>, <strong style="color: #8ac8e8;">JNI</strong>, 
                        <strong style="color: #8ac8e8;">CMake</strong>, <strong style="color: #8ac8e8;">BCrypt</strong>. 
                        Постоянно изучаю системное программирование и безопасность.
                    </p>
                </div>
            </div>

            <!-- Статистика (мини) -->
            <div class="section" style="margin-top: 18px;">
                <div class="section-title"><span class="icon">▸</span> активность</div>
                <div class="stats-mini">
                    <div class="stat-block">
                        <div class="val">C++</div>
                        <div class="lbl">основной</div>
                    </div>
                    <div class="stat-block">
                        <div class="val">C</div>
                        <div class="lbl">системный</div>
                    </div>
                    <div class="stat-block">
                        <div class="val">CMake</div>
                        <div class="lbl">сборка</div>
                    </div>
                </div>
            </div>

            <!-- Стек (коротко) -->
            <div class="section" style="margin-top: 8px;">
                <div class="section-title"><span class="icon">▸</span> технологии</div>
                <div style="display: flex; flex-wrap: wrap; gap: 10px; background: #0f181f; border-radius: 14px; padding: 16px 18px; border: 1px solid #1a2a34;">
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645;">C++20</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645;">C11</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645;">Python</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645;">TypeScript</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645;">React</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645;">FastAPI</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645;">SQLite</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645;">OpenSSL</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645;">JWT</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645;">WebSocket</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645; color: #6ef0b0; border-color: #2a5a4a;">Win32 API</span>
                    <span style="background: #14222e; padding: 4px 16px; border-radius: 30px; font-size: 0.75rem; border: 1px solid #233645; color: #6ef0b0; border-color: #2a5a4a;">JNI</span>
                </div>
            </div>

        </div>
        <!-- ===== КОНЕЦ КОЛОНОК ===== -->

    </div>

    <!-- ===== ФУТЕР ===== -->
    <div class="footer">
        <div class="quote">
            «<strong>C++</strong> даёт контроль, <strong>C</strong> даёт свободу.»
        </div>
        <div class="social">
            <a href="https://t.me/Cocojambossss" target="_blank">✈ Telegram</a>
        </div>
    </div>

</div>
<!-- ===== КОНЕЦ BOARD ===== -->

</body>
</html>
