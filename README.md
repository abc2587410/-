<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>正修科技大學 護理一甲 班級網頁 (CSU Nursing 1A)</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter & Noto Sans TC -->
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        royal: {
                            800: '#1e3a8a',
                            900: '#172554',
                            950: '#0f172a',
                            lightBg: '#1e293b',
                            card: '#ffffff',
                            cardAlt: '#f8fafc',
                            accent: '#38bdf8',
                            hover: '#0284c7'
                        }
                    },
                    fontFamily: {
                        sans: ['Noto Sans TC', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Noto Sans TC', sans-serif;
            background: linear-gradient(135deg, #0f172a 0%, #1e3a8a 50%, #172554 100%);
            background-attachment: fixed;
            color: #f8fafc;
        }
        .active-tab {
            background-color: #38bdf8 !important;
            color: #0f172a !important;
            font-weight: 700;
            box-shadow: 0 4px 12px rgba(56, 189, 248, 0.35);
        }
        .glass-header {
            background: rgba(15, 23, 42, 0.85);
            backdrop-filter: blur(12px);
        }
        .glass-modal {
            background: rgba(15, 23, 42, 0.92);
            backdrop-filter: blur(16px);
        }
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0f172a;
        }
        ::-webkit-scrollbar-thumb {
            background: #3b82f6;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #60a5fa;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col text-slate-100">

    <!-- Navigation Header -->
    <header class="sticky top-0 z-40 glass-header border-b border-blue-900/60 shadow-lg">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16 items-center">
                <!-- Logo & Brand Title (Clickable to Home) -->
                <div class="flex items-center space-x-3 cursor-pointer group" onclick="switchTab('home')">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-sky-400 to-blue-600 flex items-center justify-center text-slate-950 shadow-md group-hover:scale-105 transition-transform duration-200">
                        <i class="fa-solid font-bold text-xl fa-user-nurse"></i>
                    </div>
                    <div>
                        <h1 class="text-lg sm:text-xl font-extrabold text-white leading-tight group-hover:text-sky-300 transition-colors">
                            正修科技大學
                        </h1>
                        <p class="text-xs font-medium text-sky-300 tracking-wider">護理一甲 (CSU Nursing 1A)</p>
                    </div>
                </div>

                <!-- Desktop Navigation Buttons -->
                <nav class="hidden lg:flex space-x-1 xl:space-x-2 text-sm font-medium">
                    <button onclick="switchTab('home')" id="nav-home" class="nav-btn px-3 py-2 rounded-lg text-slate-200 hover:text-sky-300 hover:bg-white/10 transition"><i class="fa-solid fa-house mr-1.5"></i>首頁公告</button>
                    <button onclick="switchTab('reminders')" id="nav-reminders" class="nav-btn px-3 py-2 rounded-lg text-slate-200 hover:text-sky-300 hover:bg-white/10 transition"><i class="fa-solid fa-clock-rotate-left mr-1.5"></i>考試作業</button>
                    <button onclick="switchTab('schedule')" id="nav-schedule" class="nav-btn px-3 py-2 rounded-lg text-slate-200 hover:text-sky-300 hover:bg-white/10 transition"><i class="fa-solid fa-calendar-days mr-1.5"></i>班級課表</button>
                    <button onclick="switchTab('faculty')" id="nav-faculty" class="nav-btn px-3 py-2 rounded-lg text-slate-200 hover:text-sky-300 hover:bg-white/10 transition"><i class="fa-solid fa-chalkboard-user mr-1.5"></i>師長介紹</button>
                    <button onclick="switchTab('students')" id="nav-students" class="nav-btn px-3 py-2 rounded-lg text-slate-200 hover:text-sky-300 hover:bg-white/10 transition"><i class="fa-solid fa-users mr-1.5"></i>同學名冊</button>
                    <button onclick="switchTab('gallery')" id="nav-gallery" class="nav-btn px-3 py-2 rounded-lg text-slate-200 hover:text-sky-300 hover:bg-white/10 transition"><i class="fa-solid fa-images mr-1.5"></i>活動花絮</button>
                    <button onclick="switchTab('forum')" id="nav-forum" class="nav-btn px-3 py-2 rounded-lg text-slate-200 hover:text-sky-300 hover:bg-white/10 transition"><i class="fa-solid fa-comments mr-1.5"></i>討論區</button>
                    <button onclick="switchTab('polls')" id="nav-polls" class="nav-btn px-3 py-2 rounded-lg text-slate-200 hover:text-sky-300 hover:bg-white/10 transition"><i class="fa-solid fa-square-poll-vertical mr-1.5"></i>班務投票</button>
                </nav>

                <!-- Mobile Menu Button -->
                <div class="lg:hidden flex items-center">
                    <button id="mobile-menu-btn" onclick="toggleMobileMenu()" class="p-2 rounded-lg text-slate-200 hover:text-sky-300 hover:bg-white/10 focus:outline-none">
                        <i class="fa-solid fa-bars text-xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Navigation Menu -->
        <div id="mobile-menu" class="hidden lg:hidden border-t border-blue-900/50 bg-slate-900/95 px-4 pt-2 pb-4 space-y-1 shadow-2xl">
            <button onclick="switchTab('home')" class="mobile-nav-btn block w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-200 hover:bg-sky-500/20 hover:text-sky-300"><i class="fa-solid fa-house w-6"></i>首頁公告</button>
            <button onclick="switchTab('reminders')" class="mobile-nav-btn block w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-200 hover:bg-sky-500/20 hover:text-sky-300"><i class="fa-solid fa-clock-rotate-left w-6"></i>考試與作業</button>
            <button onclick="switchTab('schedule')" class="mobile-nav-btn block w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-200 hover:bg-sky-500/20 hover:text-sky-300"><i class="fa-solid fa-calendar-days w-6"></i>互動課表</button>
            <button onclick="switchTab('faculty')" class="mobile-nav-btn block w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-200 hover:bg-sky-500/20 hover:text-sky-300"><i class="fa-solid fa-chalkboard-user w-6"></i>導師與任課教師</button>
            <button onclick="switchTab('students')" class="mobile-nav-btn block w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-200 hover:bg-sky-500/20 hover:text-sky-300"><i class="fa-solid fa-users w-6"></i>幹部與同學名冊</button>
            <button onclick="switchTab('gallery')" class="mobile-nav-btn block w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-200 hover:bg-sky-500/20 hover:text-sky-300"><i class="fa-solid fa-images w-6"></i>班級活動花絮</button>
            <button onclick="switchTab('forum')" class="mobile-nav-btn block w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-200 hover:bg-sky-500/20 hover:text-sky-300"><i class="fa-solid fa-comments w-6"></i>班級討論區</button>
            <button onclick="switchTab('polls')" class="mobile-nav-btn block w-full text-left px-3 py-2 rounded-md text-base font-medium text-slate-200 hover:bg-sky-500/20 hover:text-sky-300"><i class="fa-solid fa-square-poll-vertical w-6"></i>即時投票區</button>
        </div>
    </header>

    <!-- Hero Banner -->
    <div class="bg-gradient-to-r from-blue-900/80 via-blue-800/80 to-slate-900/80 border-b border-blue-800/40 py-8 px-4 sm:px-6 lg:px-8 shadow-inner backdrop-blur-sm">
        <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-4">
            <div class="space-y-1 text-center md:text-left">
                <span class="inline-block px-3 py-1 rounded-full bg-sky-500/20 text-sky-300 text-xs font-bold border border-sky-400/30">113 學年度第一學期</span>
                <h2 class="text-2xl sm:text-3xl font-extrabold text-white tracking-tight">關懷生命 · 護理傳承</h2>
                <p class="text-sky-200 text-sm max-w-xl">正修科技大學 護理系一甲 官方班級網頁平台</p>
            </div>
            <div class="flex items-center gap-4 bg-slate-900/70 backdrop-blur-md px-6 py-3 rounded-2xl border border-sky-400/20 text-xs sm:text-sm shadow-md">
                <div class="text-center px-4 border-r border-slate-700">
                    <p class="text-slate-400 text-xs">班級人數</p>
                    <p class="text-xl font-black text-sky-300">26 人</p>
                </div>
                <div class="text-center px-4">
                    <p class="text-slate-400 text-xs">導師</p>
                    <p class="text-xl font-black text-white">楊惠如 老師</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Main Content Area -->
    <main class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">

        <!-- SECTION 1: Announcements / Home -->
        <section id="tab-home" class="tab-content space-y-6">
            <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 pb-4 border-b border-blue-800/50">
                <div>
                    <h3 class="text-xl font-bold text-white flex items-center gap-2">
                        <i class="fa-solid fa-bullhorn text-sky-400"></i> 最新班務公告
                    </h3>
                    <p class="text-xs text-sky-200/70">即時掌握護理一甲第一手重要教務與實習動態</p>
                </div>
                <div class="flex flex-wrap gap-2 w-full sm:w-auto">
                    <button onclick="filterAnnouncements('all')" class="ann-filter-btn px-3 py-1.5 text-xs font-bold rounded-full bg-sky-400 text-slate-950 shadow-sm hover:opacity-90">全部公告</button>
                    <button onclick="filterAnnouncements('緊急')" class="ann-filter-btn px-3 py-1.5 text-xs font-semibold rounded-full bg-rose-500/20 text-rose-300 border border-rose-500/30 hover:bg-rose-500/30">🚨 緊急</button>
                    <button onclick="filterAnnouncements('教務')" class="ann-filter-btn px-3 py-1.5 text-xs font-semibold rounded-full bg-sky-500/20 text-sky-300 border border-sky-500/30 hover:bg-sky-500/30">📚 教務</button>
                    <button onclick="filterAnnouncements('實習')" class="ann-filter-btn px-3 py-1.5 text-xs font-semibold rounded-full bg-emerald-500/20 text-emerald-300 border border-emerald-500/30 hover:bg-emerald-500/30">💉 實習</button>
                    <button onclick="filterAnnouncements('班務')" class="ann-filter-btn px-3 py-1.5 text-xs font-semibold rounded-full bg-amber-500/20 text-amber-300 border border-amber-500/30 hover:bg-amber-500/30">🏫 班務</button>
                    <button onclick="openModal('add-announcement-modal')" class="ml-auto sm:ml-2 px-3 py-1.5 text-xs font-bold rounded-xl bg-sky-400 text-slate-950 hover:bg-sky-300 shadow-sm flex items-center gap-1 transition">
                        <i class="fa-solid fa-plus"></i> 發布公告
                    </button>
                </div>
            </div>

            <div id="announcement-list" class="grid grid-cols-1 md:grid-cols-2 gap-5">
                <!-- Announcements rendered here -->
            </div>
        </section>

        <!-- SECTION 2: Homework & Exam Reminders -->
        <section id="tab-reminders" class="tab-content hidden space-y-6">
            <div class="flex justify-between items-center pb-4 border-b border-blue-800/50">
                <div>
                    <h3 class="text-xl font-bold text-white flex items-center gap-2">
                        <i class="fa-solid fa-clock-rotate-left text-sky-400"></i> 作業與考試倒數提醒
                    </h3>
                    <p class="text-xs text-sky-200/70">精確掌控護理系各科課業繳交與考試時程</p>
                </div>
                <button onclick="openModal('add-reminder-modal')" class="px-3 py-2 text-xs font-bold rounded-xl bg-sky-400 text-slate-950 hover:bg-sky-300 shadow-sm flex items-center gap-1 transition">
                    <i class="fa-solid fa-plus"></i> 新增提醒
                </button>
            </div>

            <div id="reminders-list" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
                <!-- Reminders rendered here -->
            </div>
        </section>

        <!-- SECTION 3: Interactive Timetable -->
        <section id="tab-schedule" class="tab-content hidden space-y-6">
            <div class="pb-4 border-b border-blue-800/50">
                <h3 class="text-xl font-bold text-white flex items-center gap-2">
                    <i class="fa-solid fa-calendar-days text-sky-400"></i> 護理一甲 第一學期課表
                </h3>
                <p class="text-xs text-sky-200/70">點擊課程卡片可查看課程大綱與授課教師資訊</p>
            </div>

            <!-- Timetable Table Container -->
            <div class="overflow-x-auto rounded-2xl border border-blue-800/60 bg-white/95 text-slate-800 shadow-xl">
                <table class="w-full text-sm text-center border-collapse min-w-[700px]">
                    <thead>
                        <tr class="bg-blue-900 text-white font-bold border-b border-blue-800">
                            <th class="p-3 w-16 border-r border-blue-800">節次</th>
                            <th class="p-3 w-24 border-r border-blue-800">時間</th>
                            <th class="p-3 border-r border-blue-800">星期一</th>
                            <th class="p-3 border-r border-blue-800">星期二</th>
                            <th class="p-3 border-r border-blue-800">星期三</th>
                            <th class="p-3 border-r border-blue-800">星期四</th>
                            <th class="p-3">星期五</th>
                        </tr>
                    </thead>
                    <tbody id="timetable-body" class="divide-y divide-slate-200">
                        <!-- Timetable content rendered here -->
                    </tbody>
                </table>
            </div>
        </section>

        <!-- SECTION 4: Faculty Intro -->
        <section id="tab-faculty" class="tab-content hidden space-y-6">
            <div class="pb-4 border-b border-blue-800/50">
                <h3 class="text-xl font-bold text-white flex items-center gap-2">
                    <i class="fa-solid fa-chalkboard-user text-sky-400"></i> 班導師與授課教師團隊
                </h3>
                <p class="text-xs text-sky-200/70">諮詢課業與生活輔導諮詢管道</p>
            </div>

            <div id="faculty-list" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Faculty cards rendered here -->
            </div>
        </section>

        <!-- SECTION 5: Students & Officers -->
        <section id="tab-students" class="tab-content hidden space-y-6">
            <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 pb-4 border-b border-blue-800/50">
                <div>
                    <h3 class="text-xl font-bold text-white flex items-center gap-2">
                        <i class="fa-solid fa-users text-sky-400"></i> 護一甲 同學與幹部通訊名冊
                    </h3>
                    <p class="text-xs text-sky-200/70">共計 26 位同學，互相扶持共創美好學習環境</p>
                </div>
                <div class="relative w-full sm:w-72">
                    <i class="fa-solid fa-magnifying-glass absolute left-3 top-2.5 text-slate-400 text-sm"></i>
                    <input type="text" id="student-search-input" oninput="renderStudents()" placeholder="搜尋姓名、幹部職務或興趣..." class="w-full pl-9 pr-3 py-1.5 text-sm rounded-xl bg-slate-900/80 border border-blue-700/60 text-white placeholder-slate-400 focus:ring-2 focus:ring-sky-400 focus:outline-none">
                </div>
            </div>

            <div id="students-grid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
                <!-- Students cards rendered here -->
            </div>
        </section>

        <!-- SECTION 6: Photo Gallery -->
        <section id="tab-gallery" class="tab-content hidden space-y-6">
            <div class="flex justify-between items-center pb-4 border-b border-blue-800/50">
                <div>
                    <h3 class="text-xl font-bold text-white flex items-center gap-2">
                        <i class="fa-solid fa-images text-sky-400"></i> 班級活動花絮
                    </h3>
                    <p class="text-xs text-sky-200/70">精彩記錄護理一甲豐富的大學生活</p>
                </div>
                <button onclick="openModal('add-photo-modal')" class="px-3 py-2 text-xs font-bold rounded-xl bg-sky-400 text-slate-950 hover:bg-sky-300 shadow-sm flex items-center gap-1 transition">
                    <i class="fa-solid fa-upload"></i> 上傳相片
                </button>
            </div>

            <div id="gallery-grid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-5">
                <!-- Gallery rendered here -->
            </div>
        </section>

        <!-- SECTION 7: Forum -->
        <section id="tab-forum" class="tab-content hidden space-y-6">
            <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 pb-4 border-b border-blue-800/50">
                <div>
                    <h3 class="text-xl font-bold text-white flex items-center gap-2">
                        <i class="fa-solid fa-comments text-sky-400"></i> 護一甲 班級討論區
                    </h3>
                    <p class="text-xs text-sky-200/70">課業研討、技術交流與生活點滴分享</p>
                </div>
                <button onclick="openModal('add-post-modal')" class="px-4 py-2 text-xs font-bold rounded-xl bg-sky-400 text-slate-950 hover:bg-sky-300 shadow-sm flex items-center gap-1.5 transition">
                    <i class="fa-solid fa-pen-to-square"></i> 發起討論
                </button>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                <!-- Left: Post List -->
                <div id="forum-posts" class="lg:col-span-2 space-y-4">
                    <!-- Posts rendered here -->
                </div>

                <!-- Right: Rules & Tags -->
                <div class="space-y-4">
                    <div class="bg-white/95 text-slate-800 p-5 rounded-2xl border border-blue-800/40 shadow-lg">
                        <h4 class="font-bold text-blue-900 text-sm mb-2 flex items-center gap-1.5">
                            <i class="fa-solid fa-shield-halved text-sky-600"></i> 討論區守則
                        </h4>
                        <ul class="text-xs text-slate-600 space-y-1.5 list-disc list-inside">
                            <li>請保持理性友善發言，相互尊重。</li>
                            <li>涉及臨床與實驗隱私內容請去識別化。</li>
                            <li>討論課業請註明科目與相關章節。</li>
                        </ul>
                    </div>

                    <div class="bg-slate-900/80 p-5 rounded-2xl border border-blue-700/50 shadow-lg">
                        <h4 class="font-bold text-sky-300 text-sm mb-2.5 flex items-center gap-1.5">
                            <i class="fa-solid fa-fire text-amber-400"></i> 熱門發問標籤
                        </h4>
                        <div class="flex flex-wrap gap-2 text-xs">
                            <span class="px-2.5 py-1 bg-blue-950/80 rounded-lg text-sky-300 border border-sky-500/30">#解剖學跑台</span>
                            <span class="px-2.5 py-1 bg-blue-950/80 rounded-lg text-emerald-300 border border-emerald-500/30">#基護無菌技術</span>
                            <span class="px-2.5 py-1 bg-blue-950/80 rounded-lg text-rose-300 border border-rose-500/30">#楊惠如導師時間</span>
                            <span class="px-2.5 py-1 bg-blue-950/80 rounded-lg text-amber-300 border border-amber-500/30">#正修美食考據</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- SECTION 8: Polls & Voting -->
        <section id="tab-polls" class="tab-content hidden space-y-6">
            <div class="flex justify-between items-center pb-4 border-b border-blue-800/50">
                <div>
                    <h3 class="text-xl font-bold text-white flex items-center gap-2">
                        <i class="fa-solid fa-square-poll-vertical text-sky-400"></i> 班務即時投票區
                    </h3>
                    <p class="text-xs text-sky-200/70">公開透明班級事務即時表決</p>
                </div>
                <button onclick="openModal('add-poll-modal')" class="px-3 py-2 text-xs font-bold rounded-xl bg-sky-400 text-slate-950 hover:bg-sky-300 shadow-sm flex items-center gap-1 transition">
                    <i class="fa-solid fa-plus"></i> 發起投票
                </button>
            </div>

            <div id="polls-container" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <!-- Polls rendered here -->
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-slate-950/90 text-slate-400 text-xs py-8 border-t border-blue-900/60 mt-12 backdrop-blur-md">
        <div class="max-w-7xl mx-auto px-4 text-center space-y-2">
            <div class="flex justify-center items-center space-x-2">
                <div class="w-6 h-6 rounded-lg bg-sky-400 flex items-center justify-center text-slate-950 font-black text-xs">護</div>
                <span class="text-slate-200 font-bold text-sm">正修科技大學 護理系一甲 (CSU Nursing 1A)</span>
            </div>
            <p>校址：83004 高雄市鳥松區澄清路840號</p>
            <p class="text-slate-500">© 2026 CSU Nursing 1A Class Website. All Rights Reserved.</p>
        </div>
    </footer>

    <!-- Image Lightbox Modal -->
    <div id="lightbox-modal" class="fixed inset-0 bg-black/90 z-50 hidden flex items-center justify-center p-4 backdrop-blur-md">
        <div class="relative max-w-4xl w-full bg-slate-900 rounded-2xl overflow-hidden shadow-2xl flex flex-col border border-blue-800">
            <button onclick="closeModal('lightbox-modal')" class="absolute top-4 right-4 z-10 w-9 h-9 bg-black/60 hover:bg-black text-white rounded-full flex items-center justify-center">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>
            <div class="p-2 flex items-center justify-center bg-black">
                <img id="lightbox-img" src="" alt="Enlarged view" class="max-h-[75vh] w-auto object-contain rounded-lg">
            </div>
            <div class="p-4 bg-slate-900 text-white">
                <h4 id="lightbox-title" class="font-bold text-base"></h4>
                <p id="lightbox-desc" class="text-xs text-slate-300 mt-1"></p>
            </div>
        </div>
    </div>

    <!-- Course Details Modal -->
    <div id="course-modal" class="fixed inset-0 bg-black/70 z-50 hidden flex items-center justify-center p-4 backdrop-blur-sm">
        <div class="bg-slate-900 rounded-2xl max-w-md w-full p-6 space-y-4 shadow-2xl border border-blue-700/60 relative text-slate-100">
            <button onclick="closeModal('course-modal')" class="absolute top-4 right-4 text-slate-400 hover:text-white">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-sky-400/20 text-sky-300 flex items-center justify-center text-lg font-bold border border-sky-400/30">
                    <i class="fa-solid fa-book-open"></i>
                </div>
                <div>
                    <h4 id="course-modal-title" class="text-lg font-bold text-white"></h4>
                    <span id="course-modal-code" class="text-xs text-sky-300"></span>
                </div>
            </div>
            <div class="space-y-2 text-xs text-slate-300 border-t border-slate-800 pt-3">
                <p><strong class="text-sky-200">授課老師：</strong> <span id="course-modal-teacher"></span></p>
                <p><strong class="text-sky-200">學分數：</strong> <span id="course-modal-credits"></span></p>
                <p><strong class="text-sky-200">課程簡介：</strong> <span id="course-modal-desc"></span></p>
            </div>
            <div class="pt-2 text-right">
                <button onclick="closeModal('course-modal')" class="px-4 py-1.5 bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-semibold rounded-xl">關閉</button>
            </div>
        </div>
    </div>

    <!-- Modal: Add Announcement -->
    <div id="add-announcement-modal" class="fixed inset-0 bg-black/70 z-50 hidden flex items-center justify-center p-4 backdrop-blur-sm">
        <div class="bg-slate-900 rounded-2xl max-w-md w-full p-6 space-y-4 shadow-2xl border border-blue-700/60 text-white">
            <div class="flex justify-between items-center">
                <h4 class="font-bold text-white text-base">發布班務公告</h4>
                <button onclick="closeModal('add-announcement-modal')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <form id="announcement-form" onsubmit="handleAddAnnouncement(event)" class="space-y-3 text-xs">
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">公告類別</label>
                    <select id="ann-category" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white focus:ring-2 focus:ring-sky-400">
                        <option value="教務">教務</option>
                        <option value="實習">實習</option>
                        <option value="班務">班務</option>
                        <option value="緊急">緊急</option>
                    </select>
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">標題</label>
                    <input type="text" id="ann-title" required placeholder="請輸入公告標題" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white focus:ring-2 focus:ring-sky-400">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">公告內容</label>
                    <textarea id="ann-content" rows="3" required placeholder="詳細說明..." class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white focus:ring-2 focus:ring-sky-400"></textarea>
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">發布者 / 幹部</label>
                    <input type="text" id="ann-author" required placeholder="例：班長 陳正修" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div class="flex justify-end gap-2 pt-2">
                    <button type="button" onclick="closeModal('add-announcement-modal')" class="px-3.5 py-2 bg-slate-800 rounded-xl text-slate-300">取消</button>
                    <button type="submit" class="px-4 py-2 bg-sky-400 text-slate-950 font-bold rounded-xl hover:bg-sky-300">確定發布</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Modal: Add Reminder -->
    <div id="add-reminder-modal" class="fixed inset-0 bg-black/70 z-50 hidden flex items-center justify-center p-4 backdrop-blur-sm">
        <div class="bg-slate-900 rounded-2xl max-w-md w-full p-6 space-y-4 shadow-2xl border border-blue-700/60 text-white">
            <div class="flex justify-between items-center">
                <h4 class="font-bold text-white text-base">新增作業 / 考試提醒</h4>
                <button onclick="closeModal('add-reminder-modal')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <form id="reminder-form" onsubmit="handleAddReminder(event)" class="space-y-3 text-xs">
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">類型</label>
                    <select id="rem-type" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                        <option value="考試">📝 小考 / 期中考</option>
                        <option value="作業">📚 課業 / 實驗報告</option>
                        <option value="實習">💉 實習考照準備</option>
                    </select>
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">科目 / 事項名稱</label>
                    <input type="text" id="rem-title" required placeholder="例：解剖學 期中跑台考試" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">截止 / 考試日期</label>
                    <input type="date" id="rem-date" required class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">備註說明</label>
                    <input type="text" id="rem-note" placeholder="例如：範圍包含 Chapter 1 - 5" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div class="flex justify-end gap-2 pt-2">
                    <button type="button" onclick="closeModal('add-reminder-modal')" class="px-3.5 py-2 bg-slate-800 rounded-xl text-slate-300">取消</button>
                    <button type="submit" class="px-4 py-2 bg-sky-400 text-slate-950 font-bold rounded-xl hover:bg-sky-300">建立提醒</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Modal: Add Post -->
    <div id="add-post-modal" class="fixed inset-0 bg-black/70 z-50 hidden flex items-center justify-center p-4 backdrop-blur-sm">
        <div class="bg-slate-900 rounded-2xl max-w-md w-full p-6 space-y-4 shadow-2xl border border-blue-700/60 text-white">
            <div class="flex justify-between items-center">
                <h4 class="font-bold text-white text-base">發起討論貼文</h4>
                <button onclick="closeModal('add-post-modal')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <form id="post-form" onsubmit="handleAddPost(event)" class="space-y-3 text-xs">
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">討論標籤</label>
                    <select id="post-tag" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                        <option value="課業發問">課業發問</option>
                        <option value="實習討論">實習討論</option>
                        <option value="生活雜談">生活雜談</option>
                        <option value="考照心得">考照心得</option>
                    </select>
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">你的暱稱</label>
                    <input type="text" id="post-author" required placeholder="例：基本護理小學霸" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">討論主題</label>
                    <input type="text" id="post-title" required placeholder="請輸入標題" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">詳細內容</label>
                    <textarea id="post-content" rows="4" required placeholder="分享你的想法或提出問題..." class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white"></textarea>
                </div>
                <div class="flex justify-end gap-2 pt-2">
                    <button type="button" onclick="closeModal('add-post-modal')" class="px-3.5 py-2 bg-slate-800 rounded-xl text-slate-300">取消</button>
                    <button type="submit" class="px-4 py-2 bg-sky-400 text-slate-950 font-bold rounded-xl hover:bg-sky-300">發布貼文</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Modal: Add Photo -->
    <div id="add-photo-modal" class="fixed inset-0 bg-black/70 z-50 hidden flex items-center justify-center p-4 backdrop-blur-sm">
        <div class="bg-slate-900 rounded-2xl max-w-md w-full p-6 space-y-4 shadow-2xl border border-blue-700/60 text-white">
            <div class="flex justify-between items-center">
                <h4 class="font-bold text-white text-base">新增活動紀錄相片</h4>
                <button onclick="closeModal('add-photo-modal')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <form id="photo-form" onsubmit="handleAddPhoto(event)" class="space-y-3 text-xs">
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">活動名稱</label>
                    <input type="text" id="photo-title" required placeholder="例如：迎新活動" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">日期</label>
                    <input type="date" id="photo-date" required class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">活動簡述</label>
                    <input type="text" id="photo-desc" required placeholder="簡單說明活動內容..." class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">照片網址 (URL)</label>
                    <input type="url" id="photo-url" required placeholder="https://images.unsplash.com/..." class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div class="flex justify-end gap-2 pt-2">
                    <button type="button" onclick="closeModal('add-photo-modal')" class="px-3.5 py-2 bg-slate-800 rounded-xl text-slate-300">取消</button>
                    <button type="submit" class="px-4 py-2 bg-sky-400 text-slate-950 font-bold rounded-xl hover:bg-sky-300">上傳相片</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Modal: Add Poll -->
    <div id="add-poll-modal" class="fixed inset-0 bg-black/70 z-50 hidden flex items-center justify-center p-4 backdrop-blur-sm">
        <div class="bg-slate-900 rounded-2xl max-w-md w-full p-6 space-y-4 shadow-2xl border border-blue-700/60 text-white">
            <div class="flex justify-between items-center">
                <h4 class="font-bold text-white text-base">發起班務投票</h4>
                <button onclick="closeModal('add-poll-modal')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <form id="poll-form" onsubmit="handleAddPoll(event)" class="space-y-3 text-xs">
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">投票主題</label>
                    <input type="text" id="poll-question" required placeholder="例如：班聚地點調查" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">選項 1</label>
                    <input type="text" id="poll-opt1" required placeholder="選項一" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">選項 2</label>
                    <input type="text" id="poll-opt2" required placeholder="選項二" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div>
                    <label class="block text-slate-300 font-semibold mb-1">選項 3 (選填)</label>
                    <input type="text" id="poll-opt3" placeholder="選項三" class="w-full bg-slate-800 border border-slate-700 rounded-xl p-2.5 text-white">
                </div>
                <div class="flex justify-end gap-2 pt-2">
                    <button type="button" onclick="closeModal('add-poll-modal')" class="px-3.5 py-2 bg-slate-800 rounded-xl text-slate-300">取消</button>
                    <button type="submit" class="px-4 py-2 bg-sky-400 text-slate-950 font-bold rounded-xl hover:bg-sky-300">開始投票</button>
                </div>
            </form>
        </div>
    </div>

    <script>
        /* --- Mock Data & Global States --- */
        let announcementsData = [
            {
                id: 1,
                category: "緊急",
                title: "【重要】基本護理學實驗課 PPE 裝備檢查通知",
                content: "請全班同學於本週三課前準備好標準護理袍、聽診器與白色護理鞋。未穿著規定服裝者將無法進入技術實驗室。",
                author: "副班長 林心怡",
                date: "2026-10-06"
            },
            {
                id: 2,
                category: "教務",
                title: "113-1 期中考解剖學跑台考試範圍公告",
                content: "解剖學跑台測試將於第10週進行，範圍包含骨骼系統與肌肉系統人體模型辨識，請同學利用時間前往模型室複習。",
                author: "學藝幹部 張哲瑋",
                date: "2026-10-04"
            },
            {
                id: 3,
                category: "實習",
                title: "導師 楊惠如 老師 實習組別指導說明會",
                content: "楊惠如導師將於本週五導師時間進行第一次臨床見習說明與提醒，請 26 位同學準時出席。",
                author: "班長 陳正修",
                date: "2026-09-30"
            },
            {
                id: 4,
                category: "班務",
                title: "護理一甲 班服訂製款式與尺寸統計",
                content: "經投票決定採用寶藍配白色接邊款式，請尚未填寫衣服尺寸表（S/M/L/XL）的同學於明晚前完成登錄。",
                author: "總務幹部 李佳穎",
                date: "2026-09-26"
            }
        ];

        let remindersData = [
            {
                id: 1,
                type: "考試",
                title: "解剖學 (Anatomy) 期中小考",
                date: "2026-10-15",
                note: "範圍：第1章至第4章 神經系統導論",
                completed: false
            },
            {
                id: 2,
                type: "作業",
                title: "基本護理學 無菌技術操作記錄表",
                date: "2026-10-12",
                note: "繳交至楊惠如導師研究室信箱",
                completed: false
            },
            {
                id: 3,
                type: "實習",
                title: "CPR + AED 急救員證照演練",
                date: "2026-10-20",
                note: "請著體育服，地點於體育館二樓",
                completed: false
            }
        ];

        const timetableData = [
            { period: "1", time: "08:10-09:00", mon: "國文", tue: "基本護理學", wed: "解剖學", thu: "英語會話", fri: "護理倫理" },
            { period: "2", time: "09:10-10:00", mon: "國文", tue: "基本護理學", wed: "解剖學", thu: "英語會話", fri: "護理倫理" },
            { period: "3", time: "10:10-11:00", mon: "心理學", tue: "基護實驗課", wed: "生理學", thu: "全民國防", fri: "導師時間" },
            { period: "4", time: "11:10-12:00", mon: "心理學", tue: "基護實驗課", wed: "生理學", thu: "全民國防", fri: "班會" },
            { period: "午休", time: "12:00-13:20", mon: "-- 午休 --", tue: "-- 午休 --", wed: "-- 午休 --", thu: "-- 午休 --", fri: "-- 午休 --" },
            { period: "5", time: "13:30-14:20", mon: "體育", tue: "解剖學實驗", wed: "資訊通識", thu: "護理導論", fri: "-- 自習 --" },
            { period: "6", time: "14:30-15:20", mon: "體育", tue: "解剖學實驗", wed: "資訊通識", thu: "護理導論", fri: "-- 自習 --" },
            { period: "7", time: "15:30-16:20", mon: "通識人文", tue: "-- 自習 --", wed: "社團活動", thu: "-- 自習 --", fri: "-- 自習 --" }
        ];

        const coursesDetailMap = {
            "基本護理學": { title: "基本護理學", code: "NUR101", teacher: "楊惠如 導師", credits: "3.0", desc: "奠定護理臨床照護理念、無菌技術、給藥與生命徵象量測等核心技能。" },
            "解剖學": { title: "解剖學", code: "NUR102", teacher: "張建國 教授", credits: "3.0", desc: "講授人體各器官系統之解剖結構與生理位置，包含大體解剖與組織學概念。" },
            "生理學": { title: "生理學", code: "NUR103", teacher: "陳美玲 副教授", credits: "2.0", desc: "探討人體細胞、器官及系統運作之生理機制與恆定調節。" },
            "基護實驗課": { title: "基本護理學實驗", code: "NUR101L", teacher: "楊惠如 導師", credits: "2.0", desc: "實作練習生命徵象測量、舒適與清潔護理、無菌包包紮與注射示範。" },
            "解剖學實驗": { title: "解剖學實驗", code: "NUR102L", teacher: "張建國 教授", credits: "1.0", desc: "利用人體三維立體模型與組織切片進行跑台辨識與構造解析。" },
            "護理倫理": { title: "護理倫理與法律", code: "NUR104", teacher: "王思晴 講師", credits: "2.0", desc: "討論護理臨床倫理困境、護理人員法規及自主權利保障。" },
            "護理導論": { title: "護理學導論", code: "NUR100", teacher: "楊惠如 導師", credits: "2.0", desc: "引導護理一甲 26 位新生了解護理歷史演進、專業角色定位與職涯展望。" }
        };

        const facultyData = [
            {
                name: "楊惠如 老師",
                role: "班級導師 / 助理教授",
                subject: "基本護理學、護理學導論、實習指導",
                office: "護理大樓 N508 室",
                hours: "週二 13:30 - 16:30, 週五 10:00 - 12:00",
                email: "hjyang@csu.edu.tw",
                specialty: "基礎護理學、內外科護理、護理照護倫理",
                avatar: "https://images.unsplash.com/photo-1594824813566-78a933758f46?w=300&auto=format&fit=crop&q=80"
            },
            {
                name: "張建國 教授",
                role: "專任教授",
                subject: "解剖學、解剖學實驗",
                office: "醫學科技大樓 M402 室",
                hours: "週一 14:00 - 16:00",
                email: "ckchang@csu.edu.tw",
                specialty: "神經解剖學、組織學、解剖學病理研究",
                avatar: "https://images.unsplash.com/photo-1622253692010-333f2da6031d?w=300&auto=format&fit=crop&q=80"
            },
            {
                name: "陳美玲 副教授",
                role: "副教授",
                subject: "生理學、病理學機轉",
                office: "護理大樓 N512 室",
                hours: "週三 09:00 - 11:30",
                email: "mlchen@csu.edu.tw",
                specialty: "心血管生理學、內分泌學",
                avatar: "https://images.unsplash.com/photo-1559839734-2b71ea197ec2?w=300&auto=format&fit=crop&q=80"
            }
        ];

        // 26 Students Data
        const studentsData = [
            { id: "01", name: "陳正修", officer: "班長", hobby: "排球、聽音樂", quote: "引領護一甲 26 位同學攜手並進！", avatar: "https://images.unsplash.com/photo-1539571696357-5a69c17a67c6?w=150&auto=format&fit=crop&q=80" },
            { id: "02", name: "林心怡", officer: "副班長", hobby: "閱讀、衛教繪圖", quote: "細心協助楊惠如導師與班務", avatar: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=150&auto=format&fit=crop&q=80" },
            { id: "03", name: "張哲瑋", officer: "學藝股長", hobby: "筆記整理、攝影", quote: "課業筆記整理一手包辦！", avatar: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=150&auto=format&fit=crop&q=80" },
            { id: "04", name: "李佳穎", officer: "總務股長", hobby: "理財、羽球", quote: "班務帳目清晰透明", avatar: "https://images.unsplash.com/photo-1517841905240-472988babdf9?w=150&auto=format&fit=crop&q=80" },
            { id: "05", name: "黃詩涵", officer: "實習股長", hobby: "慢跑、手作", quote: "臨床技術練習零缺失", avatar: "https://images.unsplash.com/photo-1524504388940-b1c1722653e1?w=150&auto=format&fit=crop&q=80" },
            { id: "06", name: "王威翔", officer: "康樂股長", hobby: "吉他、熱舞", quote: "活動歡笑少不了我！", avatar: "https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=150&auto=format&fit=crop&q=80" },
            { id: "07", name: "許庭瑄", officer: "", hobby: "瑜伽、手作護手霜", quote: "用心溫暖每一位對象", avatar: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=150&auto=format&fit=crop&q=80" },
            { id: "08", name: "鄭宇軒", officer: "", hobby: "籃球、模型組裝", quote: "護理國考一次順利過關！", avatar: "https://images.unsplash.com/photo-1522075469751-3a6694fb2f61?w=150&auto=format&fit=crop&q=80" },
            { id: "09", name: "吳沛蓁", officer: "", hobby: "閱讀、水彩畫", quote: "維持專注與熱情", avatar: "https://images.unsplash.com/photo-1544005313-94ddf0286df2?w=150&auto=format&fit=crop&q=80" },
            { id: "10", name: "蔡宗翰", officer: "", hobby: "游泳、電影", quote: "踏實做好每一件小事", avatar: "https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?w=150&auto=format&fit=crop&q=80" },
            { id: "11", name: "周羽婕", officer: "", hobby: "烹飪、韓文學習", quote: "保持微笑面對挑戰", avatar: "https://images.unsplash.com/photo-1517841905240-472988babdf9?w=150&auto=format&fit=crop&q=80" },
            { id: "12", name: "楊承翰", officer: "", hobby: "羽球、寫程式", quote: "護理與科技跨域學習", avatar: "https://images.unsplash.com/photo-1519085360753-af0119f7cbe7?w=150&auto=format&fit=crop&q=80" },
            { id: "13", name: "謝雅婷", officer: "", hobby: "彈鋼琴、植物植栽", quote: "安靜沉穩，堅定信念", avatar: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=150&auto=format&fit=crop&q=80" },
            { id: "14", name: "劉冠廷", officer: "", hobby: "慢跑、健身", quote: "體力是強大護理基礎", avatar: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=150&auto=format&fit=crop&q=80" },
            { id: "15", name: "陳韻如", officer: "", hobby: "看書、手作點心", quote: "把愛心落實在照護中", avatar: "https://images.unsplash.com/photo-1524504388940-b1c1722653e1?w=150&auto=format&fit=crop&q=80" },
            { id: "16", name: "潘柏宇", officer: "", hobby: "桌球、旅遊", quote: "珍惜護一甲青春歲月", avatar: "https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=150&auto=format&fit=crop&q=80" },
            { id: "17", name: "賴芷晴", officer: "", hobby: "攝影、登山", quote: "看見最美的風景與初心", avatar: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=150&auto=format&fit=crop&q=80" },
            { id: "18", name: "曾家豪", officer: "", hobby: "排球、長跑", quote: "永不言棄的精神", avatar: "https://images.unsplash.com/photo-1522075469751-3a6694fb2f61?w=150&auto=format&fit=crop&q=80" },
            { id: "19", name: "鄧郁婷", officer: "", hobby: "露營、手作皮件", quote: "細緻處理每個環節", avatar: "https://images.unsplash.com/photo-1544005313-94ddf0286df2?w=150&auto=format&fit=crop&q=80" },
            { id: "20", name: "柯智傑", officer: "", hobby: "吉他、唱歌", quote: "用音樂放鬆身心", avatar: "https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?w=150&auto=format&fit=crop&q=80" },
            { id: "21", name: "徐品涵", officer: "", hobby: "瑜伽、跳舞", quote: "保持身心靈平衡", avatar: "https://images.unsplash.com/photo-1517841905240-472988babdf9?w=150&auto=format&fit=crop&q=80" },
            { id: "22", name: "葉名揚", officer: "", hobby: "棒球、電玩", quote: "團隊合作至上", avatar: "https://images.unsplash.com/photo-1519085360753-af0119f7cbe7?w=150&auto=format&fit=crop&q=80" },
            { id: "23", name: "莊芯瑜", officer: "", hobby: "插畫、手帳記錄", quote: "彩繪護理豐富生活", avatar: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=150&auto=format&fit=crop&q=80" },
            { id: "24", name: "彭立偉", officer: "", hobby: "羽球、單車", quote: "向前邁進不退縮", avatar: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=150&auto=format&fit=crop&q=80" },
            { id: "25", name: "方語桐", officer: "", hobby: "文學、咖啡調製", quote: "享受知識的滋養", avatar: "https://images.unsplash.com/photo-1524504388940-b1c1722653e1?w=150&auto=format&fit=crop&q=80" },
            { id: "26", name: "江宜臻", officer: "", hobby: "影集、烘焙", quote: "甜蜜對待生活與學習", avatar: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=150&auto=format&fit=crop&q=80" }
        ];

        let galleryData = [
            {
                id: 1,
                title: "113學年度 護理一甲迎新闖關活動",
                date: "2026-09-15",
                desc: "護理系迎新特別活動，26 位同學歡樂解謎促進感情。",
                url: "https://images.unsplash.com/photo-1523240795612-9a054b0db644?w=800&auto=format&fit=crop&q=80"
            },
            {
                id: 2,
                title: "基本護理學 無菌技術示範課",
                date: "2026-09-22",
                desc: "楊惠如導師指導無菌洗手與隔離衣穿脫，同學們認真演練。",
                url: "https://images.unsplash.com/photo-1584515979956-d9f6e5d09982?w=800&auto=format&fit=crop&q=80"
            },
            {
                id: 3,
                title: "正修科大 校慶進場預演",
                date: "2026-10-01",
                desc: "護理一甲大會操練習，展現護理系精神與精神氣概。",
                url: "https://images.unsplash.com/photo-1511632765486-a01980e01a18?w=800&auto=format&fit=crop&q=80"
            }
        ];

        let forumPostsData = [
            {
                id: 1,
                author: "解剖小學霸",
                tag: "課業發問",
                title: "請教解剖學 臂神經叢 (Brachial plexus) 分支記憶口訣？",
                content: "大家在背神經分支根、幹、股、束時有特別口訣嗎？請高手指點！",
                likes: 15,
                time: "2小時前",
                comments: [
                    { name: "張哲瑋 (學藝)", text: "可以用『Real Truckers Drink Cold Beer』的英文口訣記憶！" }
                ]
            },
            {
                id: 2,
                author: "林心怡",
                tag: "生活雜談",
                title: "正修學校附近平價午餐分享",
                content: "整理了澄清路附近的便當與飲料店清單，歡迎大家留言補充！",
                likes: 22,
                time: "4小時前",
                comments: [
                    { name: "陳正修", text: "推後門紅帽卡多便當，CP值超高！" }
                ]
            }
        ];

        let pollsData = [
            {
                id: 1,
                question: "113-1 學期 護一甲 26人首次班聚餐廳投票",
                options: [
                    { text: "澄清湖附近 韓式燒肉", votes: 12 },
                    { text: "文山特區 義大利麵簡餐", votes: 9 },
                    { text: "巨蛋商圈 綜合火鍋", votes: 5 }
                ],
                userVoted: null
            },
            {
                id: 2,
                question: "楊惠如導師班會課 護理職涯專題主題表決",
                options: [
                    { text: "臨床護理師經驗與實習心得分享", votes: 16 },
                    { text: "護理護照與國考備考規劃", votes: 10 }
                ],
                userVoted: null
            }
        ];

        /* --- Navigation Switch Logic --- */
        function switchTab(tabName) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            
            const target = document.getElementById(`tab-${tabName}`);
            if (target) {
                target.classList.remove('hidden');
            }

            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active-tab'));
            const activeNavBtn = document.getElementById(`nav-${tabName}`);
            if (activeNavBtn) {
                activeNavBtn.classList.add('active-tab');
            }

            document.getElementById('mobile-menu').classList.add('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function toggleMobileMenu() {
            document.getElementById('mobile-menu').classList.toggle('hidden');
        }

        function openModal(id) {
            document.getElementById(id).classList.remove('hidden');
        }
        function closeModal(id) {
            document.getElementById(id).classList.add('hidden');
        }

        /* --- Section 1: Announcements --- */
        function renderAnnouncements(filterTag = 'all') {
            const container = document.getElementById('announcement-list');
            container.innerHTML = '';

            const filtered = filterTag === 'all' 
                ? announcementsData 
                : announcementsData.filter(a => a.category === filterTag);

            if (filtered.length === 0) {
                container.innerHTML = `<p class="col-span-2 text-center text-slate-400 py-8 text-sm">無 ${filterTag} 相關公告。</p>`;
                return;
            }

            filtered.forEach(ann => {
                let badgeStyle = "bg-slate-700 text-slate-200";
                if (ann.category === '緊急') badgeStyle = "bg-rose-500/20 text-rose-300 border border-rose-500/30";
                if (ann.category === '教務') badgeStyle = "bg-sky-500/20 text-sky-300 border border-sky-500/30";
                if (ann.category === '實習') badgeStyle = "bg-emerald-500/20 text-emerald-300 border border-emerald-500/30";
                if (ann.category === '班務') badgeStyle = "bg-amber-500/20 text-amber-300 border border-amber-500/30";

                const card = document.createElement('div');
                card.className = "bg-white/95 text-slate-800 p-5 rounded-2xl border border-blue-800/40 shadow-lg hover:shadow-xl transition space-y-3";
                card.innerHTML = `
                    <div class="flex justify-between items-start gap-2">
                        <span class="px-2.5 py-0.5 rounded-full text-xs font-bold ${badgeStyle}">${ann.category}</span>
                        <span class="text-xs text-slate-400"><i class="fa-regular fa-clock mr-1"></i>${ann.date}</span>
                    </div>
                    <h4 class="font-bold text-blue-950 text-base leading-snug">${ann.title}</h4>
                    <p class="text-xs text-slate-600 leading-relaxed">${ann.content}</p>
                    <div class="pt-2 border-t border-slate-200 text-[11px] text-slate-500 flex justify-between items-center">
                        <span><i class="fa-solid fa-user-pen mr-1"></i>發布：${ann.author}</span>
                        <span class="text-blue-700 font-bold">正修護一甲</span>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function filterAnnouncements(category) {
            renderAnnouncements(category);
        }

        function handleAddAnnouncement(e) {
            e.preventDefault();
            const category = document.getElementById('ann-category').value;
            const title = document.getElementById('ann-title').value;
            const content = document.getElementById('ann-content').value;
            const author = document.getElementById('ann-author').value;

            announcementsData.unshift({
                id: Date.now(),
                category,
                title,
                content,
                author,
                date: new Date().toISOString().split('T')[0]
            });

            renderAnnouncements();
            closeModal('add-announcement-modal');
            document.getElementById('announcement-form').reset();
        }

        /* --- Section 2: Reminders --- */
        function renderReminders() {
            const container = document.getElementById('reminders-list');
            container.innerHTML = '';
            const today = new Date();

            remindersData.forEach(item => {
                const dueDate = new Date(item.date);
                const diffTime = dueDate - today;
                const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
                
                let daysText = diffDays > 0 ? `剩 ${diffDays} 天` : (diffDays === 0 ? "今天截止！" : "已逾期");
                let badgeBg = diffDays <= 3 ? "bg-rose-500 text-white" : "bg-sky-400 text-slate-950 font-bold";

                const card = document.createElement('div');
                card.className = `bg-white/95 text-slate-800 p-5 rounded-2xl border ${item.completed ? 'opacity-60 bg-slate-200' : 'border-blue-800/40'} shadow-lg space-y-3 relative`;
                card.innerHTML = `
                    <div class="flex justify-between items-start">
                        <span class="text-xs px-2.5 py-1 rounded-lg ${badgeBg}">${daysText}</span>
                        <button onclick="toggleReminderComplete(${item.id})" class="text-slate-400 hover:text-emerald-600 transition">
                            <i class="${item.completed ? 'fa-solid fa-circle-check text-emerald-600 text-xl' : 'fa-regular fa-circle text-xl'}"></i>
                        </button>
                    </div>
                    <div>
                        <span class="text-[11px] font-bold text-slate-400 uppercase">${item.type}</span>
                        <h4 class="font-bold text-blue-950 text-base ${item.completed ? 'line-through text-slate-400' : ''}">${item.title}</h4>
                    </div>
                    <p class="text-xs text-slate-500"><i class="fa-regular fa-calendar mr-1"></i>日期：${item.date}</p>
                    <p class="text-xs text-slate-600 bg-slate-100 p-2 rounded-xl border border-slate-200">${item.note}</p>
                `;
                container.appendChild(card);
            });
        }

        function toggleReminderComplete(id) {
            const target = remindersData.find(r => r.id === id);
            if (target) {
                target.completed = !target.completed;
                renderReminders();
            }
        }

        function handleAddReminder(e) {
            e.preventDefault();
            const type = document.getElementById('rem-type').value;
            const title = document.getElementById('rem-title').value;
            const date = document.getElementById('rem-date').value;
            const note = document.getElementById('rem-note').value;

            remindersData.push({
                id: Date.now(),
                type,
                title,
                date,
                note: note || "無額外說明",
                completed: false
            });

            renderReminders();
            closeModal('add-reminder-modal');
            document.getElementById('reminder-form').reset();
        }

        /* --- Section 3: Timetable --- */
        function renderTimetable() {
            const tbody = document.getElementById('timetable-body');
            tbody.innerHTML = '';

            timetableData.forEach(row => {
                const tr = document.createElement('tr');
                tr.className = row.period === '午休' ? 'bg-slate-100 font-bold text-slate-500' : 'hover:bg-sky-50/60 transition';
                
                tr.innerHTML = `
                    <td class="p-3 font-bold text-blue-900 border-r border-slate-200">${row.period}</td>
                    <td class="p-3 text-xs text-slate-500 border-r border-slate-200">${row.time}</td>
                    <td class="p-2 border-r border-slate-200">${formatCell(row.mon)}</td>
                    <td class="p-2 border-r border-slate-200">${formatCell(row.tue)}</td>
                    <td class="p-2 border-r border-slate-200">${formatCell(row.wed)}</td>
                    <td class="p-2 border-r border-slate-200">${formatCell(row.thu)}</td>
                    <td class="p-2">${formatCell(row.fri)}</td>
                `;
                tbody.appendChild(tr);
            });
        }

        function formatCell(text) {
            if (!text || text.includes('--')) return `<span class="text-xs text-slate-400">${text}</span>`;
            return `
                <button onclick="showCourseDetails('${text}')" class="w-full py-1.5 px-2 rounded-xl bg-blue-50 hover:bg-blue-100 text-blue-900 text-xs font-bold transition border border-blue-200 shadow-2xs">
                    ${text}
                </button>
            `;
        }

        function showCourseDetails(courseKey) {
            const detail = coursesDetailMap[courseKey] || {
                title: courseKey,
                code: "NUR-CSU",
                teacher: "正修護理系專業教師",
                credits: "2.0",
                desc: "護理學專業核心課程。"
            };

            document.getElementById('course-modal-title').innerText = detail.title;
            document.getElementById('course-modal-code').innerText = detail.code;
            document.getElementById('course-modal-teacher').innerText = detail.teacher;
            document.getElementById('course-modal-credits').innerText = detail.credits;
            document.getElementById('course-modal-desc').innerText = detail.desc;

            openModal('course-modal');
        }

        /* --- Section 4: Faculty --- */
        function renderFaculty() {
            const container = document.getElementById('faculty-list');
            container.innerHTML = '';

            facultyData.forEach(f => {
                const card = document.createElement('div');
                card.className = "bg-white/95 text-slate-800 p-6 rounded-2xl border border-blue-800/40 shadow-lg flex flex-col items-center text-center space-y-3 hover:shadow-xl transition";
                card.innerHTML = `
                    <img src="${f.avatar}" alt="${f.name}" class="w-24 h-24 rounded-full object-cover border-4 border-sky-400 shadow-md">
                    <div>
                        <h4 class="font-bold text-blue-950 text-lg">${f.name}</h4>
                        <p class="text-xs font-bold text-sky-600">${f.role}</p>
                    </div>
                    <div class="w-full text-left bg-slate-100 p-3.5 rounded-xl space-y-1.5 text-xs text-slate-700 border border-slate-200">
                        <p><i class="fa-solid fa-book text-sky-600 w-4"></i><strong>主授科目：</strong> ${f.subject}</p>
                        <p><i class="fa-solid fa-location-dot text-rose-500 w-4"></i><strong>研究室：</strong> ${f.office}</p>
                        <p><i class="fa-regular fa-clock text-amber-500 w-4"></i><strong>諮詢時間：</strong> ${f.hours}</p>
                        <p><i class="fa-regular fa-envelope text-blue-600 w-4"></i><strong>Email：</strong> ${f.email}</p>
                    </div>
                    <p class="text-xs text-slate-500 italic">專長領域：${f.specialty}</p>
                `;
                container.appendChild(card);
            });
        }

        /* --- Section 5: Student Directory --- */
        function renderStudents() {
            const container = document.getElementById('students-grid');
            const searchVal = (document.getElementById('student-search-input')?.value || '').toLowerCase();
            container.innerHTML = '';

            const filtered = studentsData.filter(s => 
                s.name.toLowerCase().includes(searchVal) || 
                s.officer.toLowerCase().includes(searchVal) ||
                s.hobby.toLowerCase().includes(searchVal)
            );

            if (filtered.length === 0) {
                container.innerHTML = `<p class="col-span-full text-center text-slate-400 py-8 text-sm">找不到符合條件的同學。</p>`;
                return;
            }

            filtered.forEach(s => {
                const isOfficer = Boolean(s.officer);
                const card = document.createElement('div');
                card.className = `bg-white/95 text-slate-800 p-4 rounded-xl border ${isOfficer ? 'border-sky-400 ring-2 ring-sky-300' : 'border-blue-800/30'} shadow-md flex items-center space-x-3`;
                card.innerHTML = `
                    <img src="${s.avatar}" alt="${s.name}" class="w-12 h-12 rounded-full object-cover border border-slate-300 shrink-0">
                    <div class="flex-grow min-w-0">
                        <div class="flex items-center gap-1.5">
                            <h4 class="font-bold text-blue-950 text-sm truncate">${s.name}</h4>
                            ${isOfficer ? `<span class="bg-sky-500 text-slate-950 text-[10px] px-2 py-0.5 rounded-full font-extrabold shrink-0">${s.officer}</span>` : ''}
                        </div>
                        <p class="text-[11px] text-slate-500 truncate"><i class="fa-solid fa-heart text-rose-500 mr-1"></i>${s.hobby}</p>
                        <p class="text-[10px] text-slate-400 italic truncate mt-0.5">"${s.quote}"</p>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        /* --- Section 6: Photo Gallery --- */
        function renderGallery() {
            const container = document.getElementById('gallery-grid');
            container.innerHTML = '';

            galleryData.forEach(item => {
                const card = document.createElement('div');
                card.className = "bg-white/95 text-slate-800 rounded-2xl overflow-hidden border border-blue-800/40 shadow-lg hover:shadow-xl transition cursor-pointer group";
                card.onclick = () => openLightbox(item.url, item.title, item.desc);
                card.innerHTML = `
                    <div class="relative overflow-hidden aspect-video bg-slate-900">
                        <img src="${item.url}" alt="${item.title}" class="w-full h-full object-cover group-hover:scale-105 transition duration-300">
                        <div class="absolute inset-0 bg-black/40 opacity-0 group-hover:opacity-100 transition flex items-center justify-center text-white font-bold text-xs gap-1">
                            <i class="fa-solid fa-magnifying-glass-plus"></i> 點擊放大預覽
                        </div>
                    </div>
                    <div class="p-4 space-y-1">
                        <h4 class="font-bold text-blue-950 text-sm truncate">${item.title}</h4>
                        <p class="text-xs text-slate-600 line-clamp-2">${item.desc}</p>
                        <span class="text-[10px] text-slate-400 block pt-1"><i class="fa-regular fa-calendar mr-1"></i>${item.date}</span>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function openLightbox(url, title, desc) {
            document.getElementById('lightbox-img').src = url;
            document.getElementById('lightbox-title').innerText = title;
            document.getElementById('lightbox-desc').innerText = desc;
            openModal('lightbox-modal');
        }

        function handleAddPhoto(e) {
            e.preventDefault();
            const title = document.getElementById('photo-title').value;
            const date = document.getElementById('photo-date').value;
            const desc = document.getElementById('photo-desc').value;
            const url = document.getElementById('photo-url').value;

            galleryData.unshift({ id: Date.now(), title, date, desc, url });
            renderGallery();
            closeModal('add-photo-modal');
            document.getElementById('photo-form').reset();
        }

        /* --- Section 7: Forum --- */
        function renderForumPosts() {
            const container = document.getElementById('forum-posts');
            container.innerHTML = '';

            forumPostsData.forEach(post => {
                const card = document.createElement('div');
                card.className = "bg-white/95 text-slate-800 p-5 rounded-2xl border border-blue-800/40 shadow-lg space-y-3";
                
                let commentsHtml = post.comments.map(c => `
                    <div class="bg-slate-100 p-2.5 rounded-xl text-xs border border-slate-200">
                        <span class="font-bold text-blue-900">${c.name}：</span>
                        <span class="text-slate-700">${c.text}</span>
                    </div>
                `).join('');

                card.innerHTML = `
                    <div class="flex justify-between items-center text-xs">
                        <span class="px-2.5 py-0.5 rounded-full bg-blue-100 text-blue-900 font-bold">${post.tag}</span>
                        <span class="text-slate-400">${post.time}</span>
                    </div>
                    <div>
                        <h4 class="font-bold text-blue-950 text-base">${post.title}</h4>
                        <p class="text-xs text-slate-600 mt-1 leading-relaxed">${post.content}</p>
                    </div>
                    <div class="flex items-center justify-between text-xs text-slate-500 pt-2 border-t border-slate-200">
                        <span><i class="fa-regular fa-circle-user mr-1 text-sky-600"></i>${post.author}</span>
                        <button onclick="likePost(${post.id})" class="flex items-center gap-1 hover:text-rose-500 transition font-semibold">
                            <i class="fa-solid fa-heart text-rose-500"></i> 贊同 (${post.likes})
                        </button>
                    </div>
                    <div class="space-y-1.5 pt-1">
                        ${commentsHtml}
                        <div class="flex gap-2 pt-1">
                            <input type="text" id="comment-input-${post.id}" placeholder="撰寫回覆..." class="flex-grow text-xs bg-slate-50 border border-slate-300 rounded-xl px-3 py-1.5 focus:outline-none focus:ring-1 focus:ring-sky-500">
                            <button onclick="addComment(${post.id})" class="px-3.5 py-1.5 bg-blue-900 text-white rounded-xl text-xs hover:bg-blue-800 font-bold">回覆</button>
                        </div>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function likePost(postId) {
            const post = forumPostsData.find(p => p.id === postId);
            if (post) {
                post.likes += 1;
                renderForumPosts();
            }
        }

        function addComment(postId) {
            const input = document.getElementById(`comment-input-${postId}`);
            if (input && input.value.trim() !== '') {
                const post = forumPostsData.find(p => p.id === postId);
                if (post) {
                    post.comments.push({ name: "護一甲同學", text: input.value.trim() });
                    renderForumPosts();
                }
            }
        }

        function handleAddPost(e) {
            e.preventDefault();
            const tag = document.getElementById('post-tag').value;
            const author = document.getElementById('post-author').value;
            const title = document.getElementById('post-title').value;
            const content = document.getElementById('post-content').value;

            forumPostsData.unshift({
                id: Date.now(),
                tag,
                author,
                title,
                content,
                likes: 0,
                time: "剛剛",
                comments: []
            });

            renderForumPosts();
            closeModal('add-post-modal');
            document.getElementById('post-form').reset();
        }

        /* --- Section 8: Polls --- */
        function renderPolls() {
            const container = document.getElementById('polls-container');
            container.innerHTML = '';

            pollsData.forEach(poll => {
                const totalVotes = poll.options.reduce((sum, opt) => sum + opt.votes, 0);

                let optionsHtml = poll.options.map((opt, idx) => {
                    const percentage = totalVotes > 0 ? Math.round((opt.votes / totalVotes) * 100) : 0;
                    return `
                        <div class="space-y-1">
                            <div class="flex justify-between text-xs text-slate-700 font-semibold">
                                <span>${opt.text}</span>
                                <span class="font-bold text-blue-900">${opt.votes} 票 (${percentage}%)</span>
                            </div>
                            <div class="w-full bg-slate-200 h-3 rounded-full overflow-hidden flex items-center">
                                <div class="bg-gradient-to-r from-sky-400 to-blue-600 h-full transition-all duration-500" style="width: ${percentage}%"></div>
                            </div>
                            <button onclick="votePoll(${poll.id}, ${idx})" ${poll.userVoted !== null ? 'disabled' : ''} 
                                class="w-full py-1.5 text-xs rounded-xl border ${poll.userVoted === idx ? 'bg-sky-100 border-sky-400 text-sky-900 font-bold' : 'border-slate-300 hover:bg-slate-100 text-slate-700'} transition mt-1">
                                ${poll.userVoted === idx ? '✓ 已投此選項' : '投給此選項'}
                            </button>
                        </div>
                    `;
                }).join('');

                const card = document.createElement('div');
                card.className = "bg-white/95 text-slate-800 p-5 rounded-2xl border border-blue-800/40 shadow-lg space-y-4";
                card.innerHTML = `
                    <div class="flex justify-between items-start">
                        <h4 class="font-bold text-blue-950 text-base">${poll.question}</h4>
                        <span class="text-xs px-2.5 py-0.5 rounded bg-emerald-100 text-emerald-800 font-bold shrink-0">進行中</span>
                    </div>
                    <div class="space-y-3">${optionsHtml}</div>
                    <div class="text-[11px] text-slate-400 text-right pt-2 border-t border-slate-200">
                        總參與人數：${totalVotes} 票
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function votePoll(pollId, optionIndex) {
            const poll = pollsData.find(p => p.id === pollId);
            if (poll && poll.userVoted === null) {
                poll.options[optionIndex].votes += 1;
                poll.userVoted = optionIndex;
                renderPolls();
            }
        }

        function handleAddPoll(e) {
            e.preventDefault();
            const q = document.getElementById('poll-question').value;
            const o1 = document.getElementById('poll-opt1').value;
            const o2 = document.getElementById('poll-opt2').value;
            const o3 = document.getElementById('poll-opt3').value;

            const opts = [{ text: o1, votes: 0 }, { text: o2, votes: 0 }];
            if (o3.trim() !== '') opts.push({ text: o3, votes: 0 });

            pollsData.unshift({
                id: Date.now(),
                question: q,
                options: opts,
                userVoted: null
            });

            renderPolls();
            closeModal('add-poll-modal');
            document.getElementById('poll-form').reset();
        }

        /* --- Window Load Event Initialization --- */
        window.onload = function() {
            renderAnnouncements();
            renderReminders();
            renderTimetable();
            renderFaculty();
            renderStudents();
            renderGallery();
            renderForumPosts();
            renderPolls();
            switchTab('home');
        };
    </script>
</body>
</html>
