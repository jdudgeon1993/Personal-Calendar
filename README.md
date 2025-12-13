<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <title>Ultimate Planner Pro ✨</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; }

        :root {
            --primary: #6366F1; --primary-light: #818CF8; --primary-dark: #4F46E5;
            --success: #10B981; --warning: #F59E0B; --error: #EF4444; --info: #3B82F6;
            --work: #3B82F6; --school: #EC4899; --personal: #8B5CF6; --health: #10B981; --finance: #F59E0B;
            --priority-high: #EF4444; --priority-medium: #F59E0B; --priority-low: #10B981;
            --bg-primary: #FAFAFA; --bg-secondary: #FFFFFF; --bg-tertiary: #F3F4F6;
            --text-primary: #1F2937; --text-secondary: #6B7280; --text-tertiary: #9CA3AF;
            --border: #E5E7EB; --shadow: rgba(0,0,0,0.05); --shadow-lg: rgba(0,0,0,0.1);
            --spacing-xs: 4px; --spacing-sm: 8px; --spacing-md: 16px; --spacing-lg: 24px; --spacing-xl: 32px;
            --radius-sm: 8px; --radius-md: 12px; --radius-lg: 16px; --radius-xl: 24px; --radius-full: 9999px;
            --transition: all 0.3s cubic-bezier(0.4,0,0.2,1);
        }

        [data-theme="dark"] {
            --bg-primary: #0F172A; --bg-secondary: #1E293B; --bg-tertiary: #334155;
            --text-primary: #F1F5F9; --text-secondary: #CBD5E1; --text-tertiary: #94A3B8;
            --border: #334155; --shadow: rgba(0,0,0,0.3); --shadow-lg: rgba(0,0,0,0.5);
        }

        html {
            width: 100%;
            overflow-x: hidden;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: var(--bg-primary); color: var(--text-primary); line-height: 1.6;
            -webkit-font-smoothing: antialiased; 
            overflow-x: hidden; 
            padding-bottom: 80px;
            transition: var(--transition);
            width: 100%;
            max-width: 100vw;
        }

        /* Mobile overflow fix */
        * {
            max-width: 100%;
        }

        .container {
            max-width: 1200px; 
            margin: 0 auto; 
            padding: var(--spacing-md);
            width: 100%;
            box-sizing: border-box;
        }

        @media (max-width: 768px) {
            .container {
                padding: var(--spacing-sm);
            }

            .form-row {
                grid-template-columns: 1fr;
            }

            .stats-grid {
                grid-template-columns: 1fr;
            }

            .board-container {
                grid-template-columns: 1fr;
            }
        }

        .header {
            background: var(--bg-secondary); border-bottom: 1px solid var(--border);
            padding: var(--spacing-md) var(--spacing-lg); position: sticky; top: 0; z-index: 100;
            backdrop-filter: blur(10px); box-shadow: 0 1px 3px var(--shadow);
        }

        .header-content {
            max-width: 1200px; margin: 0 auto; display: flex;
            justify-content: space-between; align-items: center;
        }

        .logo {
            font-size: 24px; font-weight: 800;
            background: linear-gradient(135deg, var(--primary), var(--primary-light));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            display: flex; align-items: center; gap: var(--spacing-sm);
        }

        .header-actions { display: flex; gap: var(--spacing-sm); align-items: center; }

        .icon-btn {
            width: 40px; height: 40px; border-radius: var(--radius-full); border: none;
            background: var(--bg-tertiary); color: var(--text-primary);
            display: flex; align-items: center; justify-content: center;
            cursor: pointer; transition: var(--transition); font-size: 18px;
        }

        .icon-btn:hover { background: var(--primary); color: white; transform: scale(1.05); }
        .icon-btn:active { transform: scale(0.95); }

        .container { max-width: 1200px; margin: 0 auto; padding: var(--spacing-lg); }

        .search-box {
            background: var(--bg-secondary); border: 2px solid var(--border);
            border-radius: var(--radius-xl); padding: var(--spacing-md) var(--spacing-lg);
            display: flex; align-items: center; gap: var(--spacing-md);
            transition: var(--transition); box-shadow: 0 2px 8px var(--shadow);
            margin-bottom: var(--spacing-lg);
        }

        .search-box:focus-within {
            border-color: var(--primary);
            box-shadow: 0 4px 16px var(--shadow-lg), 0 0 0 4px rgba(99,102,241,0.1);
        }

        .search-input {
            flex: 1; border: none; background: transparent; font-size: 16px;
            color: var(--text-primary); outline: none;
        }

        .search-input::placeholder { color: var(--text-tertiary); }

        .filter-chips {
            display: flex; gap: var(--spacing-sm); overflow-x: auto;
            padding-bottom: var(--spacing-sm); -webkit-overflow-scrolling: touch;
            scrollbar-width: none; margin-bottom: var(--spacing-lg);
        }

        .filter-chips::-webkit-scrollbar { display: none; }

        .chip {
            background: var(--bg-secondary); border: 2px solid var(--border);
            border-radius: var(--radius-full); padding: var(--spacing-sm) var(--spacing-md);
            font-size: 14px; font-weight: 600; color: var(--text-secondary);
            cursor: pointer; transition: var(--transition); white-space: nowrap;
            user-select: none;
        }

        .chip:active { transform: scale(0.95); }

        .chip.active {
            background: var(--primary); border-color: var(--primary); color: white;
            box-shadow: 0 4px 12px rgba(99,102,241,0.3);
        }

        .task-card {
            background: var(--bg-secondary); border-radius: var(--radius-lg);
            padding: var(--spacing-md); margin-bottom: var(--spacing-md);
            box-shadow: 0 2px 8px var(--shadow); border: 2px solid transparent;
            transition: var(--transition); cursor: pointer; position: relative; overflow: hidden;
        }

        .task-card::before {
            content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 4px;
            background: var(--priority-medium); transition: var(--transition);
        }

        .task-card.priority-high::before { background: var(--priority-high); }
        .task-card.priority-low::before { background: var(--priority-low); }

        .task-card:hover {
            transform: translateY(-2px); box-shadow: 0 8px 24px var(--shadow-lg);
            border-color: var(--primary);
        }

        .task-card:active { transform: translateY(0); }
        .task-card.completed { opacity: 0.6; }
        .task-card.completed .task-title { text-decoration: line-through; }

        .task-header {
            display: flex; align-items: flex-start; gap: var(--spacing-md);
            margin-bottom: var(--spacing-sm);
        }

        .task-checkbox {
            width: 24px; height: 24px; min-width: 24px; border-radius: var(--radius-sm);
            border: 2px solid var(--border); background: var(--bg-primary);
            cursor: pointer; display: flex; align-items: center; justify-content: center;
            transition: var(--transition);
        }

        .task-checkbox:hover { border-color: var(--success); transform: scale(1.1); }

        .task-checkbox.checked {
            background: var(--success); border-color: var(--success);
            animation: checkPop 0.3s cubic-bezier(0.68,-0.55,0.265,1.55);
        }

        @keyframes checkPop {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        .task-checkbox.checked::after {
            content: '✓'; color: white; font-weight: bold; font-size: 16px;
        }

        .task-content { flex: 1; min-width: 0; }

        .task-title {
            font-size: 16px; font-weight: 600; color: var(--text-primary);
            margin-bottom: var(--spacing-xs); line-height: 1.4;
        }

        .task-meta {
            display: flex; flex-wrap: wrap; gap: var(--spacing-xs); align-items: center;
        }

        .badge {
            display: inline-flex; align-items: center; gap: 4px; padding: 4px 8px;
            border-radius: var(--radius-sm); font-size: 12px; font-weight: 600;
            white-space: nowrap;
        }

        .badge-category { color: white; }
        .badge-time { background: var(--bg-tertiary); color: var(--text-secondary); }
        .badge-duration { background: var(--bg-tertiary); color: var(--text-secondary); }

        .section {
            margin-bottom: var(--spacing-xl);
        }

        .section-header {
            display: flex; justify-content: space-between; align-items: center;
            margin-bottom: var(--spacing-md); padding: var(--spacing-sm) 0;
            border-bottom: 2px solid var(--border);
        }

        .section-title {
            font-size: 18px; font-weight: 700; color: var(--text-primary);
            display: flex; align-items: center; gap: var(--spacing-sm);
        }

        .section-count {
            background: var(--primary); color: white; padding: 2px 8px;
            border-radius: var(--radius-full); font-size: 12px; font-weight: 700;
        }

        .timeline-container {
            background: var(--bg-secondary); border-radius: var(--radius-lg);
            padding: var(--spacing-md); box-shadow: 0 2px 8px var(--shadow);
            position: relative; overflow: hidden;
        }

        .timeline-grid {
            position: relative; height: 1020px; overflow-y: auto;
        }

        .timeline-hours {
            position: absolute; left: 0; top: 0; bottom: 0; width: 60px;
            border-right: 2px solid var(--border);
        }

        .timeline-hour {
            height: 60px; display: flex; align-items: flex-start; padding: 4px;
            font-size: 12px; font-weight: 600; color: var(--text-tertiary);
            border-bottom: 1px solid var(--border);
        }

        .timeline-tasks {
            position: absolute; left: 60px; right: 0; top: 0; bottom: 0;
        }

        .timeline-task {
            position: absolute; left: var(--spacing-sm); right: var(--spacing-sm);
            border-radius: var(--radius-md); padding: var(--spacing-sm);
            overflow: hidden; cursor: pointer; transition: var(--transition);
            box-shadow: 0 2px 4px var(--shadow);
        }

        .timeline-task:hover {
            transform: translateX(4px); box-shadow: 0 4px 12px var(--shadow-lg);
        }

        .timeline-task-title {
            font-size: 13px; font-weight: 600; color: white; margin-bottom: 2px;
            overflow: hidden; text-overflow: ellipsis; white-space: nowrap;
        }

        .timeline-task-time {
            font-size: 11px; color: rgba(255,255,255,0.9);
        }

        .timeline-now {
            position: absolute; left: 60px; right: 0; height: 2px;
            background: var(--error); z-index: 10;
        }

        .timeline-now::before {
            content: ''; position: absolute; left: -6px; top: -4px;
            width: 10px; height: 10px; border-radius: 50%; background: var(--error);
        }

        .calendar-grid {
            display: grid; gap: var(--spacing-sm);
        }

        .calendar-day {
            background: var(--bg-secondary); border-radius: var(--radius-md);
            padding: var(--spacing-sm); min-height: 100px; border: 2px solid var(--border);
            overflow-y: auto; max-height: 200px;
        }

        .calendar-day.today {
            border-color: var(--primary);
            background: linear-gradient(to bottom, rgba(99,102,241,0.1), var(--bg-secondary));
        }

        .calendar-day-header {
            font-size: 12px; font-weight: 700; margin-bottom: var(--spacing-xs);
            padding-bottom: var(--spacing-xs); border-bottom: 1px solid var(--border);
            text-align: center;
        }

        .calendar-task {
            font-size: 11px; padding: 4px 6px; background: var(--bg-tertiary);
            border-radius: var(--radius-sm); margin-bottom: 4px;
            border-left: 2px solid var(--text-tertiary); cursor: pointer;
            overflow: hidden; text-overflow: ellipsis; white-space: nowrap;
            transition: var(--transition);
        }

        .calendar-task:hover {
            background: var(--primary); color: white; transform: translateX(2px);
        }

        .board-container {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: var(--spacing-md);
        }

        .board-column {
            background: var(--bg-secondary); border-radius: var(--radius-lg);
            padding: var(--spacing-md); min-height: 400px;
            box-shadow: 0 2px 8px var(--shadow);
        }

        .board-column-header {
            font-size: 14px; font-weight: 700; text-transform: uppercase;
            letter-spacing: 0.5px; margin-bottom: var(--spacing-md);
            display: flex; align-items: center; justify-content: space-between;
            padding-bottom: var(--spacing-sm); border-bottom: 2px solid var(--border);
        }

        .stats-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: var(--spacing-md); margin-bottom: var(--spacing-lg);
        }

        .stat-card {
            background: var(--bg-secondary); border-radius: var(--radius-lg);
            padding: var(--spacing-lg); box-shadow: 0 2px 8px var(--shadow);
        }

        .stat-value {
            font-size: 36px; font-weight: 800; color: var(--primary);
            margin-bottom: var(--spacing-xs);
        }

        .stat-label {
            font-size: 14px; font-weight: 600; color: var(--text-secondary);
        }

        .fab {
            position: fixed; bottom: 90px; right: var(--spacing-lg);
            width: 64px; height: 64px; border-radius: var(--radius-full);
            background: linear-gradient(135deg, var(--primary), var(--primary-light));
            color: white; border: none; font-size: 28px; cursor: pointer;
            box-shadow: 0 8px 24px rgba(99,102,241,0.4); transition: var(--transition);
            z-index: 999; display: flex; align-items: center; justify-content: center;
        }

        .fab:hover {
            transform: scale(1.1) rotate(90deg);
            box-shadow: 0 12px 32px rgba(99,102,241,0.6);
        }

        .fab:active { transform: scale(0.95); }

        .bottom-nav {
            position: fixed; bottom: 0; left: 0; right: 0;
            background: var(--bg-secondary); border-top: 1px solid var(--border);
            padding: var(--spacing-sm) var(--spacing-md); display: flex;
            justify-content: space-around; z-index: 100; backdrop-filter: blur(10px);
            box-shadow: 0 -2px 8px var(--shadow);
        }

        .nav-btn {
            flex: 1; display: flex; flex-direction: column; align-items: center;
            gap: 4px; padding: var(--spacing-sm); border: none; background: transparent;
            color: var(--text-tertiary); font-size: 24px; cursor: pointer;
            transition: var(--transition); border-radius: var(--radius-md);
        }

        .nav-btn span { font-size: 11px; font-weight: 600; }
        .nav-btn.active { color: var(--primary); background: rgba(99,102,241,0.1); }
        .nav-btn:active { transform: scale(0.95); }

        .modal {
            display: none; position: fixed; inset: 0;
            background: rgba(0,0,0,0.5); backdrop-filter: blur(4px);
            z-index: 1000; align-items: flex-end; padding: 0;
        }

        .modal.active { display: flex; animation: fadeIn 0.2s ease-out; }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .modal-content {
            background: var(--bg-secondary); width: 100%; max-height: 90vh;
            border-radius: var(--radius-xl) var(--radius-xl) 0 0;
            padding: var(--spacing-lg); overflow-y: auto;
            animation: slideUp 0.3s cubic-bezier(0.4,0,0.2,1);
        }

        @keyframes slideUp { from { transform: translateY(100%); } to { transform: translateY(0); } }

        @media (min-width: 768px) {
            .modal { align-items: center; padding: var(--spacing-lg); }
            .modal-content {
                max-width: 600px; max-height: 80vh;
                border-radius: var(--radius-xl); margin: 0 auto;
            }
            .timeline-grid { height: 800px; }
        }

        .modal-header {
            display: flex; justify-content: space-between; align-items: center;
            margin-bottom: var(--spacing-lg); padding-bottom: var(--spacing-md);
            border-bottom: 2px solid var(--border);
        }

        .modal-title {
            font-size: 24px; font-weight: 800; color: var(--text-primary);
        }

        .close-btn {
            width: 32px; height: 32px; border-radius: var(--radius-full);
            border: none; background: var(--bg-tertiary); color: var(--text-secondary);
            font-size: 20px; cursor: pointer; transition: var(--transition);
        }

        .close-btn:hover {
            background: var(--error); color: white; transform: rotate(90deg);
        }

        .form-group { margin-bottom: var(--spacing-md); }

        .form-row {
            display: grid; grid-template-columns: 1fr 1fr; gap: var(--spacing-md);
        }

        .form-label {
            display: block; font-size: 14px; font-weight: 600;
            color: var(--text-secondary); margin-bottom: var(--spacing-xs);
        }

        .form-input, .form-select, .form-textarea {
            width: 100%; padding: var(--spacing-md); border: 2px solid var(--border);
            border-radius: var(--radius-md); background: var(--bg-primary);
            color: var(--text-primary); font-size: 16px; font-family: inherit;
            transition: var(--transition);
        }

        .form-input:focus, .form-select:focus, .form-textarea:focus {
            outline: none; border-color: var(--primary);
            box-shadow: 0 0 0 4px rgba(99,102,241,0.1);
        }

        .form-textarea { resize: vertical; min-height: 100px; }

        .btn {
            padding: var(--spacing-md) var(--spacing-lg); border: none;
            border-radius: var(--radius-md); font-size: 16px; font-weight: 600;
            cursor: pointer; transition: var(--transition); display: inline-flex;
            align-items: center; justify-content: center; gap: var(--spacing-sm);
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary), var(--primary-light));
            color: white; box-shadow: 0 4px 12px rgba(99,102,241,0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 16px rgba(99,102,241,0.4);
        }

        .btn-primary:active { transform: translateY(0); }

        .btn-secondary {
            background: var(--bg-tertiary); color: var(--text-primary);
        }

        .btn-secondary:hover { background: var(--border); }

        .tag-container {
            display: flex; flex-wrap: wrap; gap: var(--spacing-xs);
            padding: var(--spacing-sm); border: 2px solid var(--border);
            border-radius: var(--radius-md); background: var(--bg-primary);
            min-height: 44px; cursor: text;
        }

        .tag-item {
            background: var(--primary); color: white; padding: 4px 8px;
            border-radius: var(--radius-sm); font-size: 12px; font-weight: 600;
            display: flex; align-items: center; gap: 4px;
        }

        .tag-remove { cursor: pointer; font-weight: bold; }

        .tag-input {
            border: none; background: transparent; outline: none;
            flex: 1; min-width: 100px; padding: 4px;
            color: var(--text-primary); font-size: 14px;
        }

        .subtask-list {
            display: flex; flex-direction: column; gap: var(--spacing-sm);
        }

        .subtask-item {
            display: flex; gap: var(--spacing-sm); align-items: center;
        }

        .subtask-input {
            flex: 1; padding: var(--spacing-sm); border: 1px solid var(--border);
            border-radius: var(--radius-sm); background: var(--bg-primary);
            color: var(--text-primary);
        }

        .empty-state {
            text-align: center; padding: var(--spacing-xl);
            color: var(--text-tertiary);
        }

        .empty-state-icon {
            font-size: 64px; margin-bottom: var(--spacing-md); opacity: 0.5;
        }

        .empty-state-text {
            font-size: 18px; font-weight: 600; color: var(--text-secondary);
        }

        .hidden { display: none !important; }
        .text-center { text-align: center; }

        @supports (padding: max(0px)) {
            .header, .bottom-nav {
                padding-left: max(var(--spacing-lg), env(safe-area-inset-left));
                padding-right: max(var(--spacing-lg), env(safe-area-inset-right));
            }
            .bottom-nav {
                padding-bottom: max(var(--spacing-sm), env(safe-area-inset-bottom));
            }
        }

        html { scroll-behavior: smooth; }

        /* Mobile Responsive Fixes */
        @media (max-width: 768px) {
            .container {
                padding: var(--spacing-sm);
            }

            .header {
                padding: var(--spacing-sm) var(--spacing-md);
            }

            .logo {
                font-size: 20px;
            }

            .form-row {
                grid-template-columns: 1fr !important;
            }

            .stats-grid {
                grid-template-columns: 1fr !important;
            }

            .board-container {
                grid-template-columns: 1fr !important;
            }

            .timeline-container {
                margin-left: calc(-1 * var(--spacing-sm));
                margin-right: calc(-1 * var(--spacing-sm));
            }

            .search-box {
                margin-left: 0;
                margin-right: 0;
            }

            .filter-chips {
                margin-left: 0;
                margin-right: 0;
            }

            .modal-content {
                padding: var(--spacing-md);
            }

            .task-card {
                padding: var(--spacing-sm);
            }

            .task-title {
                font-size: 14px;
            }

            .badge {
                font-size: 11px;
                padding: 3px 6px;
            }
        }
    </style>
</head>
<body>
    <header class="header">
        <div class="header-content">
            <div class="logo"><span>✨</span><span>Planner</span></div>
            <div class="header-actions">
                <button class="icon-btn" id="syncBtn" title="Cloud Sync">☁️</button>
                <button class="icon-btn" id="themeBtn" title="Toggle Theme">🌙</button>
                <button class="icon-btn" id="menuBtn" title="Menu">⚙️</button>
            </div>
        </div>
    </header>

    <main class="container">
        <div class="search-box">
            <span style="font-size: 20px;">🔍</span>
            <input type="text" class="search-input" id="searchInput" placeholder="Search tasks...">
        </div>

        <div class="filter-chips" id="filterChips">
            <button class="chip active" data-filter="all">All</button>
            <button class="chip" data-filter="today">Today</button>
            <button class="chip" data-filter="urgent">Urgent</button>
            <button class="chip" data-filter="high">High Priority</button>
            <button class="chip" data-filter="work">Work</button>
            <button class="chip" data-filter="school">School</button>
            <button class="chip" data-filter="personal">Personal</button>
            <button class="chip" data-filter="health">Health</button>
        </div>

        <div id="contentArea"></div>
    </main>

    <button class="fab" id="fabBtn">+</button>

    <nav class="bottom-nav">
        <button class="nav-btn active" data-view="tasks">
            <span>📋</span><span>Tasks</span>
        </button>
        <button class="nav-btn" data-view="calendar">
            <span>📅</span><span>Calendar</span>
        </button>
        <button class="nav-btn" data-view="board">
            <span>📊</span><span>Board</span>
        </button>
        <button class="nav-btn" data-view="stats">
            <span>📈</span><span>Stats</span>
        </button>
    </nav>

    <div class="modal" id="taskModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="modal-title" id="modalTitle">New Task</h2>
                <button class="close-btn" onclick="closeTaskModal()">×</button>
            </div>
            <form id="taskForm">
                <div class="form-group">
                    <label class="form-label">Task Title *</label>
                    <input type="text" class="form-input" id="taskTitle" placeholder="What needs to be done?" required>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Category</label>
                        <select class="form-select" id="taskCategory">
                            <option value="personal">Personal</option>
                            <option value="work">Work</option>
                            <option value="school">School</option>
                            <option value="health">Health</option>
                            <option value="finance">Finance</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Priority</label>
                        <select class="form-select" id="taskPriority">
                            <option value="low">Low</option>
                            <option value="medium" selected>Medium</option>
                            <option value="high">High</option>
                        </select>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Due Date</label>
                        <input type="date" class="form-input" id="taskDate">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Time Block</label>
                        <select class="form-select" id="taskTimeBlock">
                            <option value="">Not set</option>
                            <option value="morning">🌅 Morning</option>
                            <option value="afternoon">☀️ Afternoon</option>
                            <option value="evening">🌙 Evening</option>
                        </select>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Start Time</label>
                        <input type="time" class="form-input" id="taskStartTime" onchange="calculateDuration()">
                    </div>
                    <div class="form-group">
                        <label class="form-label">End Time</label>
                        <input type="time" class="form-input" id="taskEndTime" onchange="calculateDuration()">
                    </div>
                </div>

                <div class="form-group">
                    <label class="form-label">Duration (auto-calculated)</label>
                    <input type="number" class="form-input" id="taskDuration" placeholder="Minutes" readonly style="background: var(--bg-tertiary);">
                </div>

                <div class="form-group">
                    <label class="form-label">Project</label>
                    <input type="text" class="form-input" id="taskProject" placeholder="Optional project name">
                </div>

                <div class="form-group">
                    <label class="form-label">Tags (press Enter to add)</label>
                    <div class="tag-container" id="tagContainer" onclick="document.getElementById('tagInput').focus()">
                        <input type="text" class="tag-input" id="tagInput" placeholder="Add tags...">
                    </div>
                </div>

                <div class="form-group">
                    <label class="form-label">Subtasks</label>
                    <div class="subtask-list" id="subtaskList">
                        <div class="subtask-item">
                            <input type="text" class="subtask-input" placeholder="Add subtask...">
                            <button type="button" class="btn btn-secondary" onclick="addSubtask()">+</button>
                        </div>
                    </div>
                </div>

                <div class="form-group">
                    <label class="form-label">Notes</label>
                    <textarea class="form-textarea" id="taskNotes" placeholder="Add any additional notes..."></textarea>
                </div>

                <div class="form-group">
                    <label style="display: flex; align-items: center; gap: 8px; cursor: pointer;">
                        <input type="checkbox" id="taskRecurring" onchange="toggleRecurring()">
                        <span class="form-label" style="margin: 0;">Recurring Task</span>
                    </label>
                    <select class="form-select hidden" id="recurringFreq">
                        <option value="daily">Daily</option>
                        <option value="weekly">Weekly</option>
                        <option value="monthly">Monthly</option>
                    </select>
                </div>

                <button type="submit" class="btn btn-primary" style="width: 100%;">
                    <span>💾</span><span>Save Task</span>
                </button>
            </form>
        </div>
    </div>

    <div class="modal" id="syncModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="modal-title">Cloud Sync</h2>
                <button class="close-btn" onclick="closeSyncModal()">×</button>
            </div>
            <div id="syncContent"></div>
        </div>
    </div>

    <script>
        const API_BASE_URL = 'https://rtd-n-line-api.onrender.com';
        let tasks = [];
        let currentView = 'tasks';
        let currentFilter = 'all';
        let searchQuery = '';
        let editingTaskId = null;
        let userToken = null;

        function init() {
            loadData();
            setupEventListeners();
            render();
            checkTheme();
        }

        function setupEventListeners() {
            document.getElementById('fabBtn').addEventListener('click', openNewTaskModal);
            document.getElementById('searchInput').addEventListener('input', (e) => {
                searchQuery = e.target.value.toLowerCase();
                render();
            });

            document.querySelectorAll('.chip').forEach(chip => {
                chip.addEventListener('click', () => {
                    document.querySelectorAll('.chip').forEach(c => c.classList.remove('active'));
                    chip.classList.add('active');
                    currentFilter = chip.dataset.filter;
                    render();
                });
            });

            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.addEventListener('click', () => {
                    document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
                    btn.classList.add('active');
                    currentView = btn.dataset.view;
                    render();
                });
            });

            document.getElementById('themeBtn').addEventListener('click', toggleTheme);
            document.getElementById('syncBtn').addEventListener('click', openSyncModal);
            document.getElementById('taskForm').addEventListener('submit', handleTaskSubmit);

            document.getElementById('tagInput').addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    e.preventDefault();
                    addTag();
                }
            });

            document.getElementById('taskModal').addEventListener('click', (e) => {
                if (e.target.id === 'taskModal') closeTaskModal();
            });

            document.getElementById('syncModal').addEventListener('click', (e) => {
                if (e.target.id === 'syncModal') closeSyncModal();
            });
        }

        function checkTheme() {
            const theme = localStorage.getItem('theme') || 'light';
            document.documentElement.setAttribute('data-theme', theme);
            document.getElementById('themeBtn').textContent = theme === 'dark' ? '☀️' : '🌙';
        }

        function toggleTheme() {
            const current = document.documentElement.getAttribute('data-theme');
            const newTheme = current === 'dark' ? 'light' : 'dark';
            document.documentElement.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);
            document.getElementById('themeBtn').textContent = newTheme === 'dark' ? '☀️' : '🌙';
        }

        function loadData() {
            const saved = localStorage.getItem('plannerTasks');
            if (saved) tasks = JSON.parse(saved);
            
            const savedToken = localStorage.getItem('plannerToken');
            if (savedToken) {
                userToken = savedToken;
                syncFromServer();
            }
        }

        function saveData() {
            localStorage.setItem('plannerTasks', JSON.stringify(tasks));
            autoSync();
        }

        async function syncFromServer() {
            if (!userToken) return;
            
            try {
                const response = await fetch(`${API_BASE_URL}/api/planner/tasks/${userToken}`);
                const data = await response.json();
                
                if (data.success && data.tasks && data.tasks.length > 0) {
                    tasks = data.tasks;
                    localStorage.setItem('plannerTasks', JSON.stringify(tasks));
                    render();
                }
            } catch (error) {
                console.error('Sync error:', error);
            }
        }

        async function autoSync() {
            if (!userToken) return;
            
            try {
                await fetch(`${API_BASE_URL}/api/planner/tasks/${userToken}`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ tasks })
                });
            } catch (error) {
                console.error('Auto-sync error:', error);
            }
        }

        function render() {
            switch (currentView) {
                case 'tasks':
                    renderTasks();
                    break;
                case 'calendar':
                    renderCalendar();
                    break;
                case 'board':
                    renderBoard();
                    break;
                case 'stats':
                    renderStats();
                    break;
            }
        }

        function filterTasks() {
            return tasks.filter(task => {
                if (searchQuery && !task.title.toLowerCase().includes(searchQuery)) {
                    return false;
                }
                
                if (currentFilter === 'all') return true;
                if (currentFilter === 'today') {
                    const today = new Date().toISOString().split('T')[0];
                    return task.dueDate === today;
                }
                if (currentFilter === 'urgent') {
                    if (!task.dueDate) return false;
                    const due = new Date(task.dueDate);
                    const today = new Date();
                    today.setHours(0, 0, 0, 0);
                    return due <= today && task.status !== 'done';
                }
                if (currentFilter === 'high') return task.priority === 'high';
                return task.category === currentFilter;
            });
        }

        function renderTasks() {
            const container = document.getElementById('contentArea');
            const filteredTasks = filterTasks();
            const pending = filteredTasks.filter(t => t.status !== 'done');
            const completed = filteredTasks.filter(t => t.status === 'done');

            let html = '';

            if (pending.length > 0) {
                html += `
                    <div class="section">
                        <div class="section-header">
                            <div class="section-title">
                                <span>📌</span><span>To Do</span>
                                <span class="section-count">${pending.length}</span>
                            </div>
                        </div>
                        ${pending.map(task => createTaskCard(task)).join('')}
                    </div>
                `;
            }

            if (completed.length > 0) {
                html += `
                    <div class="section">
                        <div class="section-header">
                            <div class="section-title">
                                <span>✅</span><span>Completed</span>
                                <span class="section-count">${completed.length}</span>
                            </div>
                        </div>
                        ${completed.map(task => createTaskCard(task)).join('')}
                    </div>
                `;
            }

            if (filteredTasks.length === 0) {
                html = `
                    <div class="empty-state">
                        <div class="empty-state-icon">📝</div>
                        <div class="empty-state-text">No tasks found</div>
                    </div>
                `;
            }

            container.innerHTML = html;
            attachTaskListeners();
        }

        function createTaskCard(task) {
            const isCompleted = task.status === 'done';
            const isUrgent = task.dueDate && new Date(task.dueDate) <= new Date() && !isCompleted;

            return `
                <div class="task-card priority-${task.priority} ${isCompleted ? 'completed' : ''}" data-id="${task.id}">
                    <div class="task-header">
                        <div class="task-checkbox ${isCompleted ? 'checked' : ''}" data-id="${task.id}"></div>
                        <div class="task-content">
                            <div class="task-title">${task.title}</div>
                            <div class="task-meta">
                                <span class="badge badge-category" style="background: linear-gradient(135deg, var(--${task.category}), var(--primary-light));">
                                    ${getCategoryIcon(task.category)} ${task.category}
                                </span>
                                ${task.startTime && task.endTime ? `<span class="badge badge-time">⏰ ${formatTime(task.startTime)} - ${formatTime(task.endTime)}</span>` : ''}
                                ${task.duration ? `<span class="badge badge-duration">⏱️ ${task.duration}m</span>` : ''}
                                ${isUrgent ? `<span class="badge badge-urgent">🔥 Urgent</span>` : ''}
                                ${task.project ? `<span class="badge badge-time">📁 ${task.project}</span>` : ''}
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        function renderCalendar() {
            const container = document.getElementById('contentArea');
            const today = new Date();
            const year = today.getFullYear();
            const month = today.getMonth();
            
            const filteredTasks = filterTasks();

            container.innerHTML = `
                <div class="timeline-container">
                    <div class="timeline-header">
                        <h3 style="font-size: 20px; font-weight: 700;">📅 Today's Timeline</h3>
                        <div style="font-size: 14px; color: var(--text-secondary);">
                            ${today.toLocaleDateString('en-US', { weekday: 'long', month: 'long', day: 'numeric' })}
                        </div>
                    </div>
                    ${renderTimelineDay(filteredTasks)}
                </div>
            `;
        }

        function renderTimelineDay(filteredTasks) {
            const todayStr = new Date().toISOString().split('T')[0];
            const todayTasks = filteredTasks.filter(t => t.dueDate === todayStr && t.startTime && t.endTime);
            
            const hours = [];
            for (let i = 6; i <= 23; i++) {
                hours.push(i);
            }

            const now = new Date();
            const currentMinutes = now.getHours() * 60 + now.getMinutes();
            const startMinutes = 6 * 60;
            const nowOffset = ((currentMinutes - startMinutes) / 60) * 60;

            let tasksHtml = '';
            todayTasks.forEach(task => {
                const [startHours, startMins] = task.startTime.split(':').map(Number);
                const [endHours, endMins] = task.endTime.split(':').map(Number);
                
                const startMinutes = startHours * 60 + startMins;
                const endMinutes = endHours * 60 + endMins;
                const duration = endMinutes - startMinutes;
                
                const topOffset = ((startMinutes - (6 * 60)) / 60) * 60;
                const height = (duration / 60) * 60;

                const categoryColors = {
                    work: '#3B82F6',
                    school: '#EC4899',
                    personal: '#8B5CF6',
                    health: '#10B981',
                    finance: '#F59E0B'
                };

                tasksHtml += `
                    <div class="timeline-task" 
                         style="top: ${topOffset}px; height: ${height}px; background: ${categoryColors[task.category] || '#6366F1'};"
                         onclick="editTask(${task.id})">
                        <div class="timeline-task-title">${task.title}</div>
                        <div class="timeline-task-time">${formatTime(task.startTime)} - ${formatTime(task.endTime)}</div>
                    </div>
                `;
            });

            return `
                <div class="timeline-grid">
                    <div class="timeline-hours">
                        ${hours.map(h => `
                            <div class="timeline-hour">
                                ${h === 12 ? '12 PM' : h > 12 ? `${h-12} PM` : h === 0 ? '12 AM' : `${h} AM`}
                            </div>
                        `).join('')}
                    </div>
                    <div class="timeline-tasks">
                        ${tasksHtml}
                        ${currentMinutes >= (6 * 60) && currentMinutes <= (23 * 60) ? 
                            `<div class="timeline-now" style="top: ${nowOffset}px;"></div>` : ''}
                    </div>
                </div>
            `;
        }

        function renderBoard() {
            const container = document.getElementById('contentArea');
            const filteredTasks = filterTasks();
            
            const notStarted = filteredTasks.filter(t => t.status === 'not-started');
            const inProgress = filteredTasks.filter(t => t.status === 'in-progress');
            const done = filteredTasks.filter(t => t.status === 'done');

            container.innerHTML = `
                <div class="board-container">
                    ${createBoardColumn('Not Started', notStarted, 'not-started')}
                    ${createBoardColumn('In Progress', inProgress, 'in-progress')}
                    ${createBoardColumn('Done', done, 'done')}
                </div>
            `;
            
            attachTaskListeners();
        }

        function createBoardColumn(title, tasks, status) {
            return `
                <div class="board-column">
                    <div class="board-column-header">
                        <span>${title}</span>
                        <span class="section-count">${tasks.length}</span>
                    </div>
                    <div class="board-tasks">
                        ${tasks.map(task => createTaskCard(task)).join('')}
                    </div>
                </div>
            `;
        }

        function renderStats() {
            const container = document.getElementById('contentArea');
            const total = tasks.length;
            const completed = tasks.filter(t => t.status === 'done').length;
            const pending = tasks.filter(t => t.status !== 'done').length;
            const urgent = tasks.filter(t => {
                if (!t.dueDate || t.status === 'done') return false;
                return new Date(t.dueDate) <= new Date();
            }).length;
            const completionRate = total > 0 ? Math.round((completed / total) * 100) : 0;

            container.innerHTML = `
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-value">${total}</div>
                        <div class="stat-label">Total Tasks</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">${completed}</div>
                        <div class="stat-label">Completed</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">${pending}</div>
                        <div class="stat-label">Pending</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">${urgent}</div>
                        <div class="stat-label">Urgent</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">${completionRate}%</div>
                        <div class="stat-label">Completion Rate</div>
                    </div>
                </div>

                <div class="section">
                    <div class="section-header">
                        <div class="section-title">📊 Category Breakdown</div>
                    </div>
                    ${renderCategoryStats()}
                </div>
            `;
        }

        function renderCategoryStats() {
            const categories = ['work', 'school', 'personal', 'health', 'finance'];
            return categories.map(cat => {
                const catTasks = tasks.filter(t => t.category === cat);
                const catCompleted = catTasks.filter(t => t.status === 'done').length;
                const percentage = catTasks.length > 0 ? Math.round((catCompleted / catTasks.length) * 100) : 0;

                return `
                    <div style="margin-bottom: var(--spacing-md); padding: var(--spacing-md); background: var(--bg-secondary); border-radius: var(--radius-md);">
                        <div style="display: flex; justify-content: space-between; margin-bottom: var(--spacing-xs);">
                            <span style="font-weight: 600;">${getCategoryIcon(cat)} ${cat.charAt(0).toUpperCase() + cat.slice(1)}</span>
                            <span>${catCompleted}/${catTasks.length} (${percentage}%)</span>
                        </div>
                        <div style="height: 8px; background: var(--bg-tertiary); border-radius: 4px; overflow: hidden;">
                            <div style="height: 100%; background: var(--${cat}); width: ${percentage}%;"></div>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function attachTaskListeners() {
            document.querySelectorAll('.task-checkbox').forEach(checkbox => {
                checkbox.addEventListener('click', (e) => {
                    e.stopPropagation();
                    const taskId = parseInt(checkbox.dataset.id);
                    toggleTaskStatus(taskId);
                });
            });

            document.querySelectorAll('.task-card').forEach(card => {
                card.addEventListener('click', () => {
                    const taskId = parseInt(card.dataset.id);
                    editTask(taskId);
                });
            });
        }

        function toggleTaskStatus(taskId) {
            const task = tasks.find(t => t.id === taskId);
            if (task) {
                task.status = task.status === 'done' ? 'not-started' : 'done';
                saveData();
                render();
            }
        }

        function openNewTaskModal() {
            editingTaskId = null;
            document.getElementById('modalTitle').textContent = 'New Task';
            document.getElementById('taskForm').reset();
            document.getElementById('tagContainer').querySelectorAll('.tag-item').forEach(el => el.remove());
            document.getElementById('subtaskList').innerHTML = `
                <div class="subtask-item">
                    <input type="text" class="subtask-input" placeholder="Add subtask...">
                    <button type="button" class="btn btn-secondary" onclick="addSubtask()">+</button>
                </div>
            `;
            document.getElementById('taskModal').classList.add('active');
        }

        function editTask(taskId) {
            editingTaskId = taskId;
            const task = tasks.find(t => t.id === taskId);
            
            document.getElementById('modalTitle').textContent = 'Edit Task';
            document.getElementById('taskTitle').value = task.title;
            document.getElementById('taskCategory').value = task.category;
            document.getElementById('taskPriority').value = task.priority;
            document.getElementById('taskDate').value = task.dueDate || '';
            document.getElementById('taskTimeBlock').value = task.timeBlock || '';
            document.getElementById('taskStartTime').value = task.startTime || '';
            document.getElementById('taskEndTime').value = task.endTime || '';
            document.getElementById('taskDuration').value = task.duration || '';
            document.getElementById('taskProject').value = task.project || '';
            document.getElementById('taskNotes').value = task.notes || '';
            document.getElementById('taskRecurring').checked = task.recurring || false;
            
            if (task.recurring) {
                document.getElementById('recurringFreq').classList.remove('hidden');
                document.getElementById('recurringFreq').value = task.recurringFreq || 'daily';
            }

            const tagContainer = document.getElementById('tagContainer');
            tagContainer.querySelectorAll('.tag-item').forEach(el => el.remove());
            if (task.tags) {
                task.tags.forEach(tag => {
                    const tagEl = createTagElement(tag);
                    tagContainer.insertBefore(tagEl, document.getElementById('tagInput'));
                });
            }

            const subtaskList = document.getElementById('subtaskList');
            subtaskList.innerHTML = '';
            if (task.subtasks) {
                task.subtasks.forEach(sub => {
                    addSubtaskInput(sub.text);
                });
            }
            addSubtaskInput();

            document.getElementById('taskModal').classList.add('active');
        }

        function handleTaskSubmit(e) {
            e.preventDefault();
            
            const subtaskInputs = document.querySelectorAll('.subtask-input');
            const subtasks = Array.from(subtaskInputs)
                .map(input => input.value.trim())
                .filter(text => text)
                .map(text => ({ text, completed: false }));

            const tagItems = document.querySelectorAll('.tag-item');
            const tags = Array.from(tagItems).map(el => el.textContent.replace('×', '').trim());

            const taskData = {
                id: editingTaskId || Date.now(),
                title: document.getElementById('taskTitle').value,
                category: document.getElementById('taskCategory').value,
                priority: document.getElementById('taskPriority').value,
                dueDate: document.getElementById('taskDate').value,
                timeBlock: document.getElementById('taskTimeBlock').value,
                startTime: document.getElementById('taskStartTime').value,
                endTime: document.getElementById('taskEndTime').value,
                duration: parseInt(document.getElementById('taskDuration').value) || null,
                project: document.getElementById('taskProject').value,
                notes: document.getElementById('taskNotes').value,
                subtasks: subtasks,
                tags: tags,
                recurring: document.getElementById('taskRecurring').checked,
                recurringFreq: document.getElementById('taskRecurring').checked ? 
                    document.getElementById('recurringFreq').value : null,
                status: editingTaskId ? tasks.find(t => t.id === editingTaskId).status : 'not-started',
                created: editingTaskId ? tasks.find(t => t.id === editingTaskId).created : Date.now()
            };

            if (editingTaskId) {
                const index = tasks.findIndex(t => t.id === editingTaskId);
                tasks[index] = taskData;
            } else {
                tasks.push(taskData);
            }

            saveData();
            closeTaskModal();
            render();
        }

        function closeTaskModal() {
            document.getElementById('taskModal').classList.remove('active');
        }

        function calculateDuration() {
            const startTime = document.getElementById('taskStartTime').value;
            const endTime = document.getElementById('taskEndTime').value;
            
            if (startTime && endTime) {
                const [startHours, startMinutes] = startTime.split(':').map(Number);
                const [endHours, endMinutes] = endTime.split(':').map(Number);
                
                const startTotalMinutes = startHours * 60 + startMinutes;
                const endTotalMinutes = endHours * 60 + endMinutes;
                
                let duration = endTotalMinutes - startTotalMinutes;
                if (duration < 0) duration += 24 * 60;
                
                document.getElementById('taskDuration').value = duration;
            }
        }

        function toggleRecurring() {
            const recurring = document.getElementById('taskRecurring').checked;
            const freqSelect = document.getElementById('recurringFreq');
            if (recurring) {
                freqSelect.classList.remove('hidden');
            } else {
                freqSelect.classList.add('hidden');
            }
        }

        function addTag() {
            const input = document.getElementById('tagInput');
            const value = input.value.trim();
            
            if (value) {
                const tagEl = createTagElement(value);
                const container = document.getElementById('tagContainer');
                container.insertBefore(tagEl, input);
                input.value = '';
            }
        }

        function createTagElement(text) {
            const tag = document.createElement('div');
            tag.className = 'tag-item';
            tag.innerHTML = `${text} <span class="tag-remove" onclick="this.parentElement.remove()">×</span>`;
            return tag;
        }

        function addSubtask() {
            addSubtaskInput();
        }

        function addSubtaskInput(text = '') {
            const list = document.getElementById('subtaskList');
            const item = document.createElement('div');
            item.className = 'subtask-item';
            item.innerHTML = `
                <input type="text" class="subtask-input" placeholder="Add subtask..." value="${text}">
                <button type="button" class="btn btn-secondary" onclick="addSubtask()">+</button>
            `;
            list.appendChild(item);
        }

        function openSyncModal() {
            document.getElementById('syncModal').classList.add('active');
            renderSyncContent();
        }

        function closeSyncModal() {
            document.getElementById('syncModal').classList.remove('active');
        }

        function renderSyncContent() {
            const content = document.getElementById('syncContent');
            
            if (!userToken) {
                content.innerHTML = `
                    <div class="text-center" style="padding: var(--spacing-lg);">
                        <div style="font-size: 48px; margin-bottom: var(--spacing-md);">☁️</div>
                        <h3 style="margin-bottom: var(--spacing-md);">Connect Your Planner</h3>
                        <p style="color: var(--text-secondary); margin-bottom: var(--spacing-lg);">
                            Sync your tasks across devices with a free account
                        </p>
                        <button class="btn btn-primary" onclick="registerToken()">Get Sync Token</button>
                        <div style="margin-top: var(--spacing-lg);">
                            <input type="text" class="form-input" id="tokenInput" placeholder="Enter existing token" 
                                style="margin-bottom: var(--spacing-sm);">
                            <button class="btn btn-secondary" onclick="loginToken()">Connect Token</button>
                        </div>
                    </div>
                `;
            } else {
                content.innerHTML = `
                    <div style="padding: var(--spacing-lg);">
                        <div class="text-center" style="margin-bottom: var(--spacing-lg);">
                            <div style="font-size: 48px; margin-bottom: var(--spacing-md);">✅</div>
                            <h3>Connected</h3>
                        </div>
                        <div class="form-group">
                            <label class="form-label">Your Sync Token</label>
                            <div style="display: flex; gap: var(--spacing-sm);">
                                <input type="text" class="form-input" value="${userToken}" readonly>
                                <button class="btn btn-secondary" onclick="copyToken()">Copy</button>
                            </div>
                        </div>
                        <button class="btn btn-primary" style="width: 100%; margin-bottom: var(--spacing-sm);" 
                            onclick="manualSync()">Sync Now</button>
                        <button class="btn btn-secondary" style="width: 100%;" 
                            onclick="disconnectSync()">Disconnect</button>
                    </div>
                `;
            }
        }

        async function registerToken() {
            try {
                const response = await fetch(`${API_BASE_URL}/api/planner/register`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' }
                });
                const data = await response.json();
                
                if (data.success) {
                    userToken = data.token;
                    localStorage.setItem('plannerToken', userToken);
                    await autoSync();
                    alert(`Your sync token: ${userToken}\n\nSave this token to access your tasks on other devices!`);
                    renderSyncContent();
                }
            } catch (error) {
                alert('Error creating sync token. Please try again.');
            }
        }

        async function loginToken() {
            const token = document.getElementById('tokenInput').value.trim().toUpperCase();
            if (!token) return;
            
            try {
                const response = await fetch(`${API_BASE_URL}/api/planner/login`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ token })
                });
                const data = await response.json();
                
                if (data.success) {
                    userToken = token;
                    localStorage.setItem('plannerToken', userToken);
                    await syncFromServer();
                    renderSyncContent();
                }
            } catch (error) {
                alert('Invalid token. Please check and try again.');
            }
        }

        function copyToken() {
            navigator.clipboard.writeText(userToken);
            alert('Token copied to clipboard!');
        }

        async function manualSync() {
            await autoSync();
            alert('Synced successfully!');
        }

        function disconnectSync() {
            if (confirm('Disconnect sync? Your tasks will remain on this device.')) {
                userToken = null;
                localStorage.removeItem('plannerToken');
                renderSyncContent();
            }
        }

        function getCategoryIcon(category) {
            const icons = {
                work: '💼',
                school: '🎓',
                personal: '✨',
                health: '🏃',
                finance: '💰'
            };
            return icons[category] || '📌';
        }

        function formatTime(time) {
            const [hours, minutes] = time.split(':');
            const h = parseInt(hours);
            const ampm = h >= 12 ? 'PM' : 'AM';
            const h12 = h % 12 || 12;
            return `${h12}:${minutes} ${ampm}`;
        }

        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
