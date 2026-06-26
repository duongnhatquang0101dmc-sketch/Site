<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bot treo console - Dashboard</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body class="bg-slate-900 text-slate-100 font-sans min-h-screen">

    <nav class="bg-slate-800 border-b border-slate-700 px-6 py-4 flex justify-between items-center">
        <div class="flex items-center space-x-3">
            <i class="fa-solid fa-robot text-cyan-400 text-2xl"></i>
            <span class="text-xl font-bold tracking-wider text-white">BOT CONTROL PANEL</span>
        </div>
        <div class="flex items-center space-x-4">
            <span class="flex h-3 w-3 relative">
                <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400 opacity-75"></span>
                <span class="relative inline-flex rounded-full h-3 w-3 bg-green-500"></span>
            </span>
            <span class="text-sm text-slate-400">Hệ thống: Ổn định</span>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto p-6 grid grid-cols-1 lg:grid-cols-3 gap-6">
        
        <section class="lg:col-span-2 space-y-6">
            <h2 class="text-xl font-semibold text-slate-200 flex items-center gap-2">
                <i class="fa-solid fa-list-check text-cyan-400"></i> Danh Sách Bot Đang Treo
            </h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4" id="bot-list">
                
                <div class="bg-slate-800 p-5 rounded-xl border border-slate-700 hover:border-slate-600 transition" id="bot-card-1">
                    <div class="flex justify-between items-start mb-4">
                        <div>
                            <h3 class="text-lg font-bold text-white">Bot Facebook Messenger</h3>
                            <p class="text-xs text-slate-400">ID: fb_bot_01</p>
                        </div>
                        <span id="status-1" class="px-2.5 py-1 text-xs font-medium bg-green-500/10 text-green-400 border border-green-500/20 rounded-full">
                            Online
                        </span>
                    </div>
                    <div class="space-y-2 text-sm text-slate-300 mb-5">
                        <div class="flex justify-between"><span>Thời gian chạy:</span> <span class="font-mono text-cyan-400">24h 15m</span></div>
                        <div class="flex justify-between"><span>RAM tiêu thụ:</span> <span class="font-mono text-cyan-400">120MB</span></div>
                    </div>
                    <div class="flex gap-2">
                        <button onclick="toggleBot(1)" id="btn-toggle-1" class="flex-1 bg-red-600/20 hover:bg-red-600 text-red-400 hover:text-white border border-red-500/30 font-medium py-2 px-3 rounded-lg text-sm transition flex items-center justify-center gap-2">
                            <i class="fa-solid fa-power-off"></i> Dừng Bot
                        </button>
                        <button onclick="viewLog('Bot Facebook Messenger')" class="bg-slate-700 hover:bg-slate-600 text-slate-200 font-medium py-2 px-3 rounded-lg text-sm transition">
                            <i class="fa-solid fa-terminal"></i> Log
                        </button>
                    </div>
                </div>

                <div class="bg-slate-800 p-5 rounded-xl border border-slate-700 hover:border-slate-600 transition" id="bot-card-2">
                    <div class="flex justify-between items-start mb-4">
                        <div>
                            <h3 class="text-lg font-bold text-white">Bot Discord Music</h3>
                            <p class="text-xs text-slate-400">ID: dc_bot_02</p>
                        </div>
                        <span id="status-2" class="px-2.5 py-1 text-xs font-medium bg-amber-500/10 text-amber-400 border border-amber-500/20 rounded-full">
                            Offline
                        </span>
                    </div>
                    <div class="space-y-2 text-sm text-slate-300 mb-5">
                        <div class="flex justify-between"><span>Thời gian chạy:</span> <span class="font-mono text-cyan-400">00h 00m</span></div>
                        <div class="flex justify-between"><span>RAM tiêu thụ:</span> <span class="font-mono text-cyan-400">0MB</span></div>
                    </div>
                    <div class="flex gap-2">
                        <button onclick="toggleBot(2)" id="btn-toggle-2" class="flex-1 bg-green-600/20 hover:bg-green-600 text-green-400 hover:text-white border border-green-500/30 font-medium py-2 px-3 rounded-lg text-sm transition flex items-center justify-center gap-2">
                            <i class="fa-solid fa-play"></i> Chạy Bot
                        </button>
                        <button onclick="viewLog('Bot Discord Music')" class="bg-slate-700 hover:bg-slate-600 text-slate-200 font-medium py-2 px-3 rounded-lg text-sm transition">
                            <i class="fa-solid fa-terminal"></i> Log
                        </button>
                    </div>
                </div>

            </div>
        </section>

        <section class="space-y-6">
            <h2 class="text-xl font-semibold text-slate-200 flex items-center gap-2">
                <i class="fa-solid fa-terminal text-cyan-400"></i> Live Console Output
            </h2>
            
            <div class="bg-black rounded-xl p-4 font-mono text-xs border border-slate-800 h-[350px] overflow-y-auto flex flex-col justify-between">
                <div id="console-output" class="space-y-1 text-emerald-400">
                    <p class="text-slate-500">[2026-06-27 01:00:00] Khởi động hệ thống dashboard...</p>
                    <p class="text-green-400">[OK] Kết nối cơ sở dữ liệu thành công.</p>
                    <p class="text-cyan-400">[INFO] Bot Facebook Messenger đang hoạt động tốt.</p>
                    <p class="text-amber-400">[WARN] Bot Discord Music hiện đang tắt.</p>
                </div>
                <div class="mt-4 pt-2 border-t border-slate-900 flex gap-2">
                    <input type="text" placeholder="Nhập lệnh command..." class="bg-slate-900 border border-slate-700 rounded px-2 py-1 text-white flex-1 focus:outline-none focus:border-cyan-500">
                    <button class="bg-cyan-600 hover:bg-cyan-500 text-white px-3 py-1 rounded text-xs transition">Gửi</button>
                </div>
            </div>

            <div class="bg-slate-800 p-5 rounded-xl border border-slate-700">
                <h3 class="text-md font-bold text-white mb-2 flex items-center gap-2">
                    <i class="fa-regular fa-sticky-note text-yellow-400"></i> Ghi chú nhanh (Note)
                </h3>
                <textarea class="w-full bg-slate-900 text-slate-200 text-sm p-3 rounded-lg border border-slate-700 focus:outline-none focus:border-cyan-500 resize-none h-24" placeholder="Lưu lại token, lệnh cần nhớ ở đây..."></textarea>
            </div>
        </section>

    </main>

    <script>
        function toggleBot(botId) {
            const btn = document.getElementById(`btn-toggle-${botId}`);
            const status = document.getElementById(`status-${botId}`);
            const consoleBox = document.getElementById('console-output');
            const time = new Date().toLocaleTimeString();

            if (status.innerText.trim() === "Online") {
                // Tắt bot
                status.innerText = "Offline";
                status.className = "px-2.5 py-1 text-xs font-medium bg-amber-500/10 text-amber-400 border border-amber-500/20 rounded-full";
                
                btn.className = "flex-1 bg-green-600/20 hover:bg-green-600 text-green-400 hover:text-white border border-green-500/30 font-medium py-2 px-3 rounded-lg text-sm transition flex items-center justify-center gap-2";
                btn.innerHTML = `<i class="fa-solid fa-play"></i> Chạy Bot`;
                
                consoleBox.innerHTML += `<p class="text-red-400">[${time}] Người dùng đã dừng Bot ID: ${botId}</p>`;
            } else {
                // Bật bot
                status.innerText = "Online";
                status.className = "px-2.5 py-1 text-xs font-medium bg-green-500/10 text-green-400 border border-green-500/20 rounded-full";
                
                btn.className = "flex-1 bg-red-600/20 hover:bg-red-600 text-red-400 hover:text-white border border-red-500/30 font-medium py-2 px-3 rounded-lg text-sm transition flex items-center justify-center gap-2";
                btn.innerHTML = `<i class="fa-solid fa-power-off"></i> Dừng Bot`;
                
                consoleBox.innerHTML += `<p class="text-green-400">[${time}] Khởi chạy thành công Bot ID: ${botId}...</p>`;
            }
            // Tự động cuộn console xuống cuối
            consoleBox.parentElement.scrollTop = consoleBox.parentElement.scrollHeight;
        }

        function viewLog(botName) {
            const consoleBox = document.getElementById('console-output');
            const time = new Date().toLocaleTimeString();
            consoleBox.innerHTML += `<p class="text-slate-400">[${time}] Đang kiểm tra log file của: ${botName}...</p>`;
            consoleBox.parentElement.scrollTop = consoleBox.parentElement.scrollHeight;
        }
    </script>
</body>
</html>
