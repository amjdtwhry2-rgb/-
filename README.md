# -
بث المباشر <!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة ريسبكت | Respect Live</title>
    <style>
        :root {
            --bg-color: #0b0712;
            --card-surface: #151021;
            --primary-accent: #8A2BE2;
            --secondary-accent: #FF007F;
            --text-primary: #FFFFFF;
            --text-secondary: #A09AAB;
            --border-color: #2D1E4E;
            --admin-badge: #FFD700;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-primary);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        header {
            background: rgba(21, 16, 33, 0.95);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--border-color);
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo-area {
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }

        .brand-name {
            font-size: 1.75rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--primary-accent), var(--secondary-accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: -0.5px;
        }

        .status-badge {
            background-color: #00E676;
            color: #000;
            font-size: 0.75rem;
            font-weight: 700;
            padding: 0.25rem 0.75rem;
            border-radius: 50px;
            text-transform: uppercase;
        }

        .admin-controls {
            background: #2a1b4e;
            padding: 0.5rem 1rem;
            border-radius: 8px;
            font-size: 0.85rem;
            border: 1px solid var(--primary-accent);
        }

        .main-layout {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
            width: 100%;
            display: grid;
            grid-template-columns: 1fr 380px;
            gap: 2rem;
            flex: 1;
        }

        @media (max-width: 1024px) {
            .main-layout {
                grid-template-columns: 1fr;
            }
        }

        .broadcast-section {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .player-card {
            background-color: var(--card-surface);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(138, 43, 226, 0.15);
        }

        .video-ratio {
            width: 100%;
            aspect-ratio: 16 / 9;
            background-color: #050505;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
        }

        .live-overlay {
            position: absolute;
            top: 1rem;
            left: 1rem;
            background: rgba(0,0,0,0.6);
            padding: 0.5rem 1rem;
            border-radius: 8px;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            backdrop-filter: blur(4px);
        }

        .pulse-dot {
            width: 12px;
            height: 12px;
            background-color: var(--secondary-accent);
            border-radius: 50%;
            box-shadow: 0 0 8px var(--secondary-accent);
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(255, 0, 127, 0.7); }
            70% { transform: scale(1); box-shadow: 0 0 0 10px rgba(255, 0, 127, 0); }
            100% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(255, 0, 127, 0); }
        }

        .broadcast-info {
            padding: 1.5rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .streamer-profile {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .avatar-placeholder {
            width: 56px;
            height: 56px;
            border-radius: 50%;
            background: linear-gradient(45deg, var(--primary-accent), var(--secondary-accent));
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            font-size: 1.25rem;
        }

        .streamer-details h1 {
            font-size: 1.25rem;
            margin-bottom: 0.25rem;
        }

        .streamer-details p {
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        .security-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            background: #102a1b;
            color: #4CAF50;
            padding: 0.5rem 1rem;
            border-radius: 50px;
            font-weight: 600;
            font-size: 0.85rem;
        }

        .sidebar {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .panel-card {
            background-color: var(--card-surface);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            height: 500px;
        }

        .panel-header {
            padding: 1.25rem;
            border-bottom: 1px solid var(--border-color);
            font-weight: 700;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .chat-messages {
            flex: 1;
            padding: 1.25rem;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .message {
            background: rgba(255,255,255,0.03);
            padding: 0.75rem 1rem;
            border-radius: 12px;
            font-size: 0.95rem;
            line-height: 1.4;
        }

        .message.admin {
            border-right: 3px solid var(--admin-badge);
            background: rgba(255, 215, 0, 0.05);
        }

        .message .username {
            font-weight: 700;
            margin-left: 0.5rem;
        }

        .message.admin .username {
            color: var(--admin-badge);
        }

        .chat-input-area {
            padding: 1rem;
            background: rgba(11, 7, 18, 0.6);
            border-top: 1px solid var(--border-color);
            display: flex;
            gap: 0.5rem;
        }

        .chat-input-area input {
            flex: 1;
            background: var(--card-surface);
            border: 1px solid var(--border-color);
            border-radius: 10px;
            padding: 0.75rem 1rem;
            color: white;
            outline: none;
            transition: border-color 0.2s;
        }

        .chat-input-area input:focus {
            border-color: var(--primary-accent);
        }

        .send-btn {
            background: linear-gradient(135deg, var(--primary-accent), var(--secondary-accent));
            color: white;
            border: none;
            border-radius: 10px;
            padding: 0 1.5rem;
            font-weight: 600;
            cursor: pointer;
            transition: opacity 0.2s;
        }

        .send-btn:hover {
            opacity: 0.9;
        }

        .schedule-list {
            padding: 1.25rem;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .schedule-item {
            background: rgba(255,255,255,0.02);
            padding: 1rem;
            border-radius: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .schedule-time {
            font-family: monospace;
            color: var(--secondary-accent);
            font-weight: bold;
        }

        .authorized-streamers {
            padding: 1.25rem;
        }

        .streamer-chips {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-top: 0.75rem;
        }

        .chip {
            background: #231936;
            color: #E0D8F0;
            padding: 0.5rem 1rem;
            border-radius: 50px;
            font-size: 0.85rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .chip.verified::after {
            content: '✓';
            color: #00E676;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <header>
        <div class="logo-area">
            <span class="brand-name">ريسبكت | Respect Live</span>
        </div>
        <div class="admin-controls">
            صلاحيات المالك: <span style="color: var(--admin-badge);">مُفعّلة</span>
        </div>
    </header>

    <main class="main-layout">
        <div class="broadcast-section">
            <div class="player-card">
                <div class="video-ratio">
                    <div class="live-overlay">
                        <div class="pulse-dot"></div>
                        <span>بث مباشر مؤمن</span>
                    </div>
                    <div style="text-align: center; color: var(--text-secondary);">
                        <svg width="64" height="64" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M23 12a10 10 0 1 1-20 0 10 10 0 0 1 20 0z"/><path d="m9 9 6 3-6 3V9z"/></svg>
                        <p style="margin-top: 1rem;">البث المباشر الخاص بمجتمع ريسبكت</p>
                    </div>
                </div>
                <div class="broadcast-info">
                    <div class="streamer-profile">
                        <div class="avatar-placeholder">ر</div>
                        <div class="streamer-details">
                            <h1>سهرة تفاعلية مع شباب ريسبكت</h1>
                            <p>بواسطة: الإدارة العليا</p>
                        </div>
                    </div>
                    <div class="security-badge">
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="11" width="18" height="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
                        محصن بالكامل
                    </div>
                </div>
            </div>
        </div>

        <div class="sidebar">
            <div class="panel-card">
                <div class="panel-header">
                    <span>دردشة المجتمع الحية</span>
                    <span style="font-size: 0.8rem; color: #4CAF50;">● محمي</span>
                </div>
                <div class="chat-messages" id="chatContainer">
                    <div class="message admin">
                        <span class="username">الرئيس (دربح):</span>
                        أهلاً بالجميع في منصة ريسبكت الرسمية. القوانين صارمة والكل مرحب به.
                    </div>
                    <div class="message">
                        <span class="username">مشرف (مصعب):</span>
                        البث سيبدأ بعد قليل، جهزوا أسئلتكم يا شباب.
                    </div>
                    <div class="message">
                        <span class="username">متابع:</span>
                        يعطيكم العافية، بانتظاركم!
                    </div>
                </div>
                <div class="chat-input-area">
                    <input type="text" id="chatInput" placeholder="اكتب رسالتك...">
                    <button class="send-btn" onclick="sendMsg()">إرسال</button>
                </div>
            </div>

            <div class="panel-card" style="height: auto;">
                <div class="panel-header">📅 جدول البثوث القادمة</div>
                <div class="schedule-list">
                    <div class="schedule-item">
                        <div>
                            <div style="font-weight: 600;">بث التحديات العام</div>
                            <div style="font-size: 0.85rem; color: var(--text-secondary);">تقديم: مصعب الحارثي</div>
                        </div>
                        <div class="schedule-time">10:00 م</div>
                    </div>
                    <div class="schedule-item">
                        <div>
                            <div style="font-weight: 600;">سوالف وسيناريوهات</div>
                            <div style="font-size: 0.85rem; color: var(--text-secondary);">تقديم: درعاء</div>
                        </div>
                        <div class="schedule-time">السبت - 09:00 م</div>
                    </div>
                </div>
            </div>

            <div class="panel-card" style="height: auto;">
                <div class="panel-header">🛡️ قائمة البث المصرح لهم</div>
                <div class="authorized-streamers">
                    <p style="font-size: 0.85rem; color: var(--text-secondary);">فقط الأسماء المعتمدة يمكنها الظهور هنا:</p>
                    <div class="streamer-chips">
                        <div class="chip verified">دربح</div>
                        <div class="chip verified">مصعب الحارثي</div>
                        <div class="chip verified">درعاء</div>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <script>
        function sendMsg() {
            const input = document.getElementById('chatInput');
            const container = document.getElementById('chatContainer');
            if(input.value.trim() !== '') {
                const msg = document.createElement('div');
                msg.className = 'message';
                msg.innerHTML = `<span class="username">أنت:</span> ${input.value}`;
                container.appendChild(msg);
                input.value = '';
                container.scrollTop = container.scrollHeight;
            }
        }
    </script>
</body>
</html>

