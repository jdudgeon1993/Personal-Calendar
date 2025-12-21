<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <title>Taskify || Planner Dashboard ✨</title>

    <!-- External Libraries -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/sortablejs@1.15.0/Sortable.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700;800&display=swap" rel="stylesheet">

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Plus Jakarta Sans', sans-serif;
        }

        :root {
            --bg-primary: #0a0a0f;
            --bg-secondary: #13131a;
            --bg-card: #1a1a24;
            --text-primary: #e8e8f0;
            --text-secondary: #a0a0b8;
            --accent-primary: #6366f1;
            --accent-secondary: #8b5cf6;
            --accent-success: #10b981;
            --accent-warning: #f59e0b;
            --accent-danger: #ef4444;
            --border-color: #2a2a38;
            --shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
        }

        [data-theme="light"] {
            --bg-primary: #f8f9fa;
            --bg-secondary: #ffffff;
            --bg-card: #ffffff;
            --text-primary: #1a1a24;
            --text-secondary: #6b7280;
            --border-color: #e5e7eb;
            --shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        body {
            background: var(--bg-primary);
            color: var(--text-primary);
            overflow-x: hidden;
            transition: background 0.3s ease, color 0.3s ease;
        }

        .gradient-text {
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .glass-effect {
            background: rgba(26, 26, 36, 0.8);
            backdrop-filter: blur(20px);
            border: 1px solid var(--border-color);
        }

        [data-theme="light"] .glass-effect {
            background: rgba(255, 255, 255, 0.9);
        }

        .card {
            background: var(--bg-card);
            border-radius: 16px;
            padding: 20px;
            border: 1px solid var(--border-color);
            transition: all 0.3s ease;
        }

        .card:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow);
        }

        .btn {
            padding: 12px 24px;
            border-radius: 12px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 14px;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            color: white;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(99, 102, 241, 0.4);
        }

        .btn-secondary {
            background: var(--bg-secondary);
            color: var(--text-primary);
            border: 1px solid var(--border-color);
        }

        .btn-secondary:hover {
            background: var(--bg-card);
        }

        .modal-overlay {
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(10px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            padding: 20px;
        }

        .modal-content {
            background: var(--bg-card);
            border-radius: 24px;
            padding: 32px;
            max-width: 600px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            border: 1px solid var(--border-color);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.8);
        }

        .modal-content::-webkit-scrollbar {
            width: 8px;
        }

        .modal-content::-webkit-scrollbar-track {
            background: var(--bg-secondary);
            border-radius: 4px;
        }

        .modal-content::-webkit-scrollbar-thumb {
            background: var(--accent-primary);
            border-radius: 4px;
        }

        .input, .textarea, .select {
            width: 100%;
            padding: 12px 16px;
            background: var(--bg-secondary);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            color: var(--text-primary);
            font-size: 14px;
            transition: all 0.3s ease;
        }

        .input:focus, .textarea:focus, .select:focus {
            outline: none;
            border-color: var(--accent-primary);
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
        }

        .textarea {
            resize: vertical;
            min-height: 100px;
        }

        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: var(--bg-card);
            border-top: 1px solid var(--border-color);
            display: flex;
            justify-content: space-around;
            padding: 12px 8px;
            z-index: 100;
            box-shadow: 0 -4px 20px rgba(0, 0, 0, 0.3);
        }

        .nav-btn {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 4px;
            padding: 8px 16px;
            background: none;
            border: none;
            color: var(--text-secondary);
            cursor: pointer;
            transition: all 0.3s ease;
            border-radius: 12px;
            font-size: 12px;
        }

        .nav-btn.active {
            color: var(--accent-primary);
            background: rgba(99, 102, 241, 0.1);
        }

        .nav-btn:hover {
            color: var(--accent-primary);
        }

        .view-container {
            display: none;
            padding: 20px 20px 100px 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .view-container.active {
            display: block;
        }

        .stat-card {
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            border-radius: 20px;
            padding: 24px;
            color: white;
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
        }

        .kanban-column {
            background: var(--bg-card);
            border-radius: 16px;
            padding: 16px;
            min-height: 200px;
            border: 1px solid var(--border-color);
        }

        .task-card {
            background: var(--bg-secondary);
            border-radius: 12px;
            padding: 16px;
            margin-bottom: 12px;
            border: 1px solid var(--border-color);
            cursor: move;
            transition: all 0.3s ease;
        }

        .task-card:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow);
            border-color: var(--accent-primary);
        }

        .sortable-ghost {
            opacity: 0.4;
        }

        .sortable-drag {
            transform: rotate(5deg);
        }

        .time-block {
            background: var(--bg-card);
            border-left: 4px solid var(--accent-primary);
            border-radius: 8px;
            padding: 16px;
            margin-bottom: 8px;
            transition: all 0.3s ease;
        }

        .time-block:hover {
            transform: translateX(4px);
            box-shadow: var(--shadow);
        }

        .focus-timer {
            text-align: center;
            padding: 60px 20px;
        }

        .timer-display {
            font-size: 96px;
            font-weight: 800;
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin: 40px 0;
            font-variant-numeric: tabular-nums;
        }

        .tag {
            display: inline-block;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            margin: 2px;
        }

        .priority-high { background: rgba(239, 68, 68, 0.2); color: var(--accent-danger); }
        .priority-medium { background: rgba(245, 158, 11, 0.2); color: var(--accent-warning); }
        .priority-low { background: rgba(16, 185, 129, 0.2); color: var(--accent-success); }

        .status-not-started { background: rgba(156, 163, 175, 0.2); color: #9ca3af; }
        .status-in-progress { background: rgba(99, 102, 241, 0.2); color: var(--accent-primary); }
        .status-done { background: rgba(16, 185, 129, 0.2); color: var(--accent-success); }

        .fab {
            position: fixed;
            bottom: 90px;
            right: 20px;
            width: 64px;
            height: 64px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            color: white;
            border: none;
            font-size: 28px;
            cursor: pointer;
            box-shadow: 0 8px 24px rgba(99, 102, 241, 0.4);
            transition: all 0.3s ease;
            z-index: 50;
        }

        .fab:hover {
            transform: scale(1.1) rotate(90deg);
            box-shadow: 0 12px 32px rgba(99, 102, 241, 0.6);
        }

        .header-bar {
            background: var(--bg-card);
            padding: 20px;
            border-bottom: 1px solid var(--border-color);
            position: sticky;
            top: 0;
            z-index: 99;
            backdrop-filter: blur(20px);
        }

        .icon-btn {
            background: var(--bg-secondary);
            border: 1px solid var(--border-color);
            width: 40px;
            height: 40px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 18px;
        }

        .icon-btn:hover {
            background: var(--accent-primary);
            color: white;
            transform: translateY(-2px);
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            font-size: 14px;
            color: var(--text-primary);
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
        }

        .checkbox-group {
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 12px;
            background: var(--bg-secondary);
            border-radius: 8px;
            cursor: pointer;
        }

        .checkbox-group input[type="checkbox"] {
            width: 20px;
            height: 20px;
            cursor: pointer;
        }

        .subtask-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 12px;
            background: var(--bg-secondary);
            border-radius: 8px;
            margin-bottom: 8px;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: var(--bg-secondary);
            border-radius: 8px;
            overflow: hidden;
            margin: 12px 0;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--accent-primary), var(--accent-secondary));
            transition: width 0.3s ease;
        }

        .empty-state {
            text-align: center;
            padding: 60px 20px;
            color: var(--text-secondary);
        }

        .empty-state-icon {
            font-size: 64px;
            margin-bottom: 16px;
            opacity: 0.5;
        }

        @media (max-width: 768px) {
            .form-row {
                grid-template-columns: 1fr;
            }
            .timer-display {
                font-size: 64px;
            }
            .modal-content {
                padding: 24px;
            }
            .view-container {
                padding: 12px 12px 100px 12px;
            }
            .calendar-event {
                font-size: 11px;
                padding: 6px 10px;
            }
            .header-bar {
                padding: 16px;
            }
            .stat-card {
                padding: 20px;
            }
            #sync-indicator {
                font-size: 10px;
                padding: 4px 8px;
            }
        }

        .search-bar {
            width: 100%;
            padding: 16px 20px;
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            color: var(--text-primary);
            font-size: 16px;
            margin-bottom: 20px;
        }

        .search-bar:focus {
            outline: none;
            border-color: var(--accent-primary);
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
        }

        .filter-buttons {
            display: flex;
            gap: 8px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 8px 16px;
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            color: var(--text-secondary);
            font-size: 14px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .filter-btn.active {
            background: var(--accent-primary);
            color: white;
            border-color: var(--accent-primary);
        }

        /* Calendar Timeline Styles */
        .calendar-timeline {
            position: relative;
            background: var(--bg-card);
            border-radius: 16px;
            padding: 20px;
            min-height: 600px;
        }

        .timeline-hours {
            position: relative;
            height: 1440px; /* 24 hours * 60px per hour */
        }

        .hour-row {
            position: relative;
            height: 60px;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            align-items: flex-start;
        }

        .hour-label {
            width: 70px;
            font-size: 11px;
            color: var(--text-secondary);
            font-weight: 600;
            padding-top: 4px;
        }

        .hour-content {
            flex: 1;
            position: relative;
            height: 100%;
        }

        .calendar-event {
            position: absolute;
            left: 0;
            right: 0;
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            border-radius: 8px;
            padding: 8px 12px;
            color: white;
            font-size: 13px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            z-index: 1;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
            min-height: auto;
            height: auto;
            overflow: visible;
        }

        .calendar-event:hover {
            transform: translateX(4px);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
        }

        .calendar-event.active {
            animation: glow-pulse 2s ease-in-out infinite;
            box-shadow: 0 0 20px rgba(99, 102, 241, 0.8), 0 0 40px rgba(99, 102, 241, 0.4);
            z-index: 2;
        }

        @keyframes glow-pulse {
            0%, 100% {
                box-shadow: 0 0 20px rgba(99, 102, 241, 0.8), 0 0 40px rgba(99, 102, 241, 0.4);
            }
            50% {
                box-shadow: 0 0 30px rgba(99, 102, 241, 1), 0 0 60px rgba(99, 102, 241, 0.6);
            }
        }

        .current-time-indicator {
            position: absolute;
            left: 70px;
            right: 0;
            height: 2px;
            background: #ef4444;
            z-index: 10;
            pointer-events: none;
        }

        .current-time-indicator::before {
            content: '';
            position: absolute;
            left: -6px;
            top: -5px;
            width: 12px;
            height: 12px;
            background: #ef4444;
            border-radius: 50%;
            box-shadow: 0 0 10px rgba(239, 68, 68, 0.6);
        }

        .current-time-indicator::after {
            content: attr(data-time);
            position: absolute;
            left: -65px;
            top: -8px;
            font-size: 10px;
            font-weight: 700;
            color: #ef4444;
            background: var(--bg-card);
            padding: 2px 6px;
            border-radius: 4px;
        }

        .fab-menu {
            position: fixed;
            bottom: 160px;
            right: 20px;
            display: flex;
            flex-direction: column;
            gap: 12px;
            z-index: 49;
        }

        .fab-menu.hidden {
            display: none;
        }

        .fab-option {
            width: 56px;
            height: 56px;
            border-radius: 50%;
            background: var(--bg-card);
            border: 2px solid var(--accent-primary);
            color: var(--text-primary);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            cursor: pointer;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
        }

        .fab-option:hover {
            transform: scale(1.1);
            background: var(--accent-primary);
            color: white;
        }

        /* Loading Screen */
        #loading-screen {
            position: fixed;
            inset: 0;
            background: linear-gradient(135deg, #0a0a0f 0%, #1a1a24 100%);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 10000;
            transition: opacity 0.5s ease, visibility 0.5s ease;
        }

        #loading-screen.hidden {
            opacity: 0;
            visibility: hidden;
        }

        .loading-logo {
            font-size: 48px;
            font-weight: 800;
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 30px;
            animation: pulse 2s ease-in-out infinite;
        }

        .loading-spinner {
            width: 60px;
            height: 60px;
            border: 4px solid rgba(99, 102, 241, 0.2);
            border-top-color: var(--accent-primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        .loading-text {
            margin-top: 20px;
            color: var(--text-secondary);
            font-size: 14px;
            animation: fade 1.5s ease-in-out infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        @keyframes fade {
            0%, 100% { opacity: 0.5; }
            50% { opacity: 1; }
        }

        /* Focus Mode Overlay */
        #focus-mode-overlay {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(10, 10, 15, 0.98);
            z-index: 9999;
            overflow-y: auto;
        }

        #focus-mode-overlay.active {
            display: block;
        }
    </style>
</head>
<body>
    <!-- Loading Screen -->
    <div id="loading-screen">
        <div class="loading-logo">Taskify || Planner</div>
        <div class="loading-spinner"></div>
        <div class="loading-text">Loading your dashboard...</div>
    </div>

    <!-- Header Bar -->
    <div class="header-bar" style="padding: 20px 24px; border-bottom: none;">
        <div style="margin-bottom: 8px;">
            <h1 style="font-size: 32px; font-weight: 800; margin: 0; color: var(--text-primary);">Taskify || Planner Dashboard</h1>
        </div>
        <div style="margin-bottom: 6px;">
            <div id="header-datetime" style="font-size: 15px; color: var(--text-secondary);"></div>
        </div>
        <div style="margin-bottom: 12px;">
            <div id="header-greeting" style="font-size: 18px; font-weight: 600; color: #4A90E2;"></div>
        </div>
        <div style="display: flex; gap: 8px; align-items: center;">
            <div id="sync-indicator" style="display: none; font-size: 12px; color: var(--accent-success); font-weight: 600; padding: 6px 12px; background: rgba(16, 185, 129, 0.1); border-radius: 8px;" title="Sync active">
                🔄 Synced
            </div>
            <button class="icon-btn" onclick="toggleTheme()" title="Toggle Theme">🌓</button>
            <button class="icon-btn" onclick="openSettingsModal()" title="Settings">⚙️</button>
        </div>
    </div>

    <!-- Hub View (Dashboard) -->
    <div id="hub-view" class="view-container active">
        <h2 class="text-3xl font-bold mb-6">Command Center</h2>

        <!-- Stats Cards -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
            <div class="stat-card">
                <div style="position: relative; z-index: 1;">
                    <div class="text-4xl mb-2">📊</div>
                    <div class="text-sm opacity-90">Completion Rate</div>
                    <div class="text-3xl font-bold mt-2" id="completion-rate">0%</div>
                </div>
            </div>
            <div class="stat-card" style="background: linear-gradient(135deg, #10b981, #059669);">
                <div style="position: relative; z-index: 1;">
                    <div class="text-4xl mb-2">✅</div>
                    <div class="text-sm opacity-90">Completed Tasks</div>
                    <div class="text-3xl font-bold mt-2" id="completed-count">0</div>
                </div>
            </div>
            <div class="stat-card" style="background: linear-gradient(135deg, #f59e0b, #d97706);">
                <div style="position: relative; z-index: 1;">
                    <div class="text-4xl mb-2">🔥</div>
                    <div class="text-sm opacity-90">Active Tasks</div>
                    <div class="text-3xl font-bold mt-2" id="active-count">0</div>
                </div>
            </div>
        </div>

        <!-- Today Section -->
        <div style="margin-bottom: 24px;">
            <h2 class="text-2xl font-bold mb-4" style="color: var(--text-primary);">📍 Today</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="card">
                    <h3 class="text-xl font-bold mb-4">✅ Tasks</h3>
                    <div id="today-tasks"></div>
                </div>
                <div class="card">
                    <h3 class="text-xl font-bold mb-4">📅 Events</h3>
                    <div id="today-events"></div>
                </div>
            </div>
        </div>

        <!-- Upcoming Section -->
        <div style="margin-bottom: 24px;">
            <h2 class="text-2xl font-bold mb-4" style="color: var(--text-primary);">🗓️ Upcoming</h2>
            <div class="card">
                <h3 class="text-xl font-bold mb-4">Next 7 Days</h3>
                <div id="upcoming-events"></div>
            </div>
        </div>

        <!-- Quick Stats -->
        <div class="card mb-6">
            <h3 class="text-xl font-bold mb-4">🎯 Quick Stats</h3>
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                <div>
                    <div class="text-sm text-secondary">High Priority</div>
                    <div class="text-2xl font-bold" id="high-priority-count">0</div>
                </div>
                <div>
                    <div class="text-sm text-secondary">Overdue</div>
                    <div class="text-2xl font-bold text-danger" id="overdue-count">0</div>
                </div>
                <div>
                    <div class="text-sm text-secondary">This Week</div>
                    <div class="text-2xl font-bold" id="week-count">0</div>
                </div>
                <div>
                    <div class="text-sm text-secondary">Total Tasks</div>
                    <div class="text-2xl font-bold" id="total-count">0</div>
                </div>
            </div>
        </div>

        <!-- All Tasks -->
        <div class="card">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 16px;">
                <h3 class="text-xl font-bold">📋 All Tasks</h3>
                <select id="task-filter" class="select" style="width: auto; padding: 8px 12px;" onchange="renderHub()">
                    <option value="active">Active Tasks</option>
                    <option value="all">All Tasks</option>
                    <option value="overdue">Overdue</option>
                    <option value="upcoming">Upcoming</option>
                    <option value="completed">Completed</option>
                </select>
            </div>
            <div id="all-tasks-list"></div>
        </div>
    </div>

    <!-- Board View (Kanban) -->
    <div id="board-view" class="view-container">
        <h2 class="text-3xl font-bold mb-6">Board</h2>

        <input type="text" class="search-bar" id="board-search" placeholder="🔍 Search tasks..." oninput="filterBoardTasks()">

        <div class="filter-buttons" id="board-filters">
            <button class="filter-btn active" onclick="filterBoard('all')">All</button>
            <button class="filter-btn" onclick="filterBoard('work')">Work</button>
            <button class="filter-btn" onclick="filterBoard('personal')">Personal</button>
            <button class="filter-btn" onclick="filterBoard('school')">School</button>
            <button class="filter-btn" onclick="filterBoard('health')">Health</button>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div class="kanban-column">
                <h3 class="text-lg font-bold mb-4 flex items-center gap-2">
                    <span>⭕</span> Not Started
                </h3>
                <div id="not-started-column" class="min-h-[200px]"></div>
            </div>
            <div class="kanban-column">
                <h3 class="text-lg font-bold mb-4 flex items-center gap-2">
                    <span>🔄</span> In Progress
                </h3>
                <div id="in-progress-column" class="min-h-[200px]"></div>
            </div>
            <div class="kanban-column">
                <h3 class="text-lg font-bold mb-4 flex items-center gap-2">
                    <span>✅</span> Done
                </h3>
                <div id="done-column" class="min-h-[200px]"></div>
            </div>
        </div>
    </div>

    <!-- Pulse View (Calendar) -->
    <div id="pulse-view" class="view-container">
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 16px;">
            <h2 class="text-2xl font-bold">Calendar</h2>
            <button class="btn btn-primary" style="padding: 8px 16px;" onclick="scrollToCurrentTime()">📍 Now</button>
        </div>

        <div style="display: flex; gap: 8px; margin-bottom: 16px; flex-wrap: wrap;">
            <button class="btn btn-secondary" style="padding: 8px 16px; font-size: 14px;" onclick="changePulseDate(-1)">←</button>
            <input type="date" class="input" id="pulse-date" onchange="renderPulse()" style="flex: 1; min-width: 150px; padding: 8px 12px;">
            <button class="btn btn-secondary" style="padding: 8px 16px; font-size: 14px;" onclick="changePulseDate(1)">→</button>
        </div>

        <div class="calendar-timeline">
            <div id="pulse-timeline" class="timeline-hours"></div>
        </div>
    </div>

    <!-- Notes View -->
    <div id="notes-view" class="view-container">
        <h2 class="text-3xl font-bold mb-6">Notes</h2>

        <div class="card">
            <textarea
                id="notes-textarea"
                class="textarea"
                placeholder="✍️ Write your thoughts, ideas, and notes here..."
                style="min-height: 500px; font-size: 16px; line-height: 1.8;"
                oninput="saveNotes()"
            ></textarea>
            <div class="mt-4 text-sm text-secondary">
                Auto-saved • Last updated: <span id="notes-timestamp">Never</span>
            </div>
        </div>
    </div>

    <!-- Focus View (Timer) -->
    <div id="focus-view" class="view-container">
        <div class="focus-timer">
            <h2 class="text-4xl font-bold mb-4">🎯 Focus Mode</h2>
            <p class="text-secondary mb-8">Stay focused and productive with the Pomodoro technique</p>

            <div class="timer-display" id="timer-display">25:00</div>

            <div style="display: flex; gap: 16px; justify-content: center; flex-wrap: wrap;">
                <button class="btn btn-primary" style="padding: 16px 48px; font-size: 18px;" onclick="enterFocusMode()">
                    ▶️ Start Focus Session
                </button>
                <button class="btn btn-secondary" style="padding: 16px 48px; font-size: 18px;" onclick="resetTimer()">
                    🔄 Reset
                </button>
            </div>

            <div class="mt-12">
                <div class="card inline-block">
                    <h3 class="text-lg font-bold mb-4">⏱️ Timer Settings</h3>
                    <div class="form-group">
                        <label class="form-label">Focus Duration (minutes)</label>
                        <input type="number" class="input" id="focus-duration" value="25" min="1" max="60" onchange="updateTimerDuration()">
                    </div>
                </div>
            </div>

            <div class="mt-8">
                <div class="card inline-block">
                    <div class="text-2xl font-bold mb-2" id="sessions-completed">0</div>
                    <div class="text-sm text-secondary">Sessions Completed Today</div>
                </div>
            </div>
        </div>
    </div>

    <!-- Focus Mode Fullscreen Overlay -->
    <div id="focus-mode-overlay">
        <div style="max-width: 1200px; margin: 0 auto; padding: 40px 20px;">
            <!-- Focus Mode Header -->
            <div style="text-align: center; margin-bottom: 40px;">
                <h1 class="text-5xl font-bold gradient-text mb-4">🎯 Focus Session</h1>
                <p class="text-secondary">All other actions are paused. Focus on what matters.</p>
            </div>

            <!-- Timer Display -->
            <div class="focus-timer" style="padding: 20px;">
                <div class="timer-display" id="focus-overlay-timer">25:00</div>

                <div style="display: flex; gap: 16px; justify-content: center; flex-wrap: wrap; margin-top: 30px;">
                    <button class="btn btn-secondary" style="padding: 16px 48px; font-size: 18px;" onclick="pauseFocusMode()">
                        ⏸️ Pause
                    </button>
                    <button class="btn btn-secondary" style="padding: 16px 48px; font-size: 18px; background: var(--accent-danger); color: white; border: none;" onclick="exitFocusMode()">
                        ❌ Exit Focus Mode
                    </button>
                </div>
            </div>

            <!-- Today's High Priority Tasks -->
            <div style="margin-top: 60px;">
                <h3 class="text-2xl font-bold mb-6">📌 Today's High Priority Tasks</h3>
                <div id="focus-high-priority-tasks"></div>
            </div>
        </div>
    </div>

    <!-- Floating Action Button Menu -->
    <div class="fab-menu hidden" id="fab-menu">
        <button class="fab-option" onclick="openTaskModal(); toggleFabMenu()" title="Add Task">✅</button>
        <button class="fab-option" onclick="openEventModal(); toggleFabMenu()" title="Add Event">📅</button>
    </div>
    <button class="fab" onclick="toggleFabMenu()" title="Add Task or Event">+</button>

    <!-- Bottom Navigation -->
    <div class="bottom-nav">
        <button class="nav-btn active" onclick="switchView('hub')">
            <span style="font-size: 24px;">🏠</span>
            <span>Hub</span>
        </button>
        <button class="nav-btn" onclick="switchView('board')">
            <span style="font-size: 24px;">📋</span>
            <span>Board</span>
        </button>
        <button class="nav-btn" onclick="switchView('pulse')">
            <span style="font-size: 24px;">⚡</span>
            <span>Pulse</span>
        </button>
        <button class="nav-btn" onclick="switchView('notes')">
            <span style="font-size: 24px;">📝</span>
            <span>Notes</span>
        </button>
        <button class="nav-btn" onclick="switchView('focus')">
            <span style="font-size: 24px;">🎯</span>
            <span>Focus</span>
        </button>
    </div>

    <!-- Task Modal -->
    <div id="task-modal" class="modal-overlay" style="display: none;">
        <div class="modal-content">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 24px;">
                <h2 class="text-2xl font-bold" id="task-modal-title">Add New Task</h2>
                <button class="icon-btn" onclick="closeTaskModal()">✕</button>
            </div>

            <form id="task-form" onsubmit="saveTask(event)">
                <div class="form-group">
                    <label class="form-label">Task Title *</label>
                    <input type="text" class="input" id="task-title" placeholder="Enter task title" required>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Category</label>
                        <select class="select" id="task-category">
                            <option value="work">Work</option>
                            <option value="personal">Personal</option>
                            <option value="school">School</option>
                            <option value="health">Health</option>
                            <option value="finance">Finance</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Priority</label>
                        <select class="select" id="task-priority">
                            <option value="low">Low</option>
                            <option value="medium">Medium</option>
                            <option value="high">High</option>
                        </select>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Status</label>
                        <select class="select" id="task-status">
                            <option value="not-started">Not Started</option>
                            <option value="in-progress">In Progress</option>
                            <option value="done">Done</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Due Date</label>
                        <input type="date" class="input" id="task-due-date">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Start Time</label>
                        <input type="time" class="input" id="task-start-time">
                    </div>
                    <div class="form-group">
                        <label class="form-label">End Time</label>
                        <input type="time" class="input" id="task-end-time">
                    </div>
                </div>

                <div class="form-group">
                    <label class="form-label">Project</label>
                    <input type="text" class="input" id="task-project" placeholder="Project name (optional)">
                </div>

                <div class="form-group">
                    <label class="form-label">Tags</label>
                    <input type="text" class="input" id="task-tags" placeholder="Enter tags separated by commas">
                </div>

                <div class="form-group">
                    <label class="form-label">Description</label>
                    <textarea class="textarea" id="task-description" placeholder="Add task description..."></textarea>
                </div>

                <div class="form-group">
                    <label class="form-label">Milestone</label>
                    <input type="text" class="input" id="task-milestone" placeholder="Associated milestone (optional)">
                </div>

                <div class="form-group">
                    <label class="form-label">Dependencies (tasks that must be completed first)</label>
                    <select multiple class="select" id="task-dependencies" style="min-height: 100px; padding: 8px;">
                        <!-- Options populated dynamically -->
                    </select>
                    <div style="font-size: 12px; color: var(--text-secondary); margin-top: 4px;">
                        Hold Ctrl/Cmd to select multiple tasks
                    </div>
                </div>

                <div class="form-group">
                    <label class="checkbox-group">
                        <input type="checkbox" id="task-recurring">
                        <span>Recurring Task</span>
                    </label>
                </div>

                <div class="form-group" id="recurring-options" style="display: none;">
                    <label class="form-label">Recurrence Pattern</label>
                    <select class="select" id="task-recurrence" onchange="updateRecurringOptions('task')">
                        <option value="daily">Daily</option>
                        <option value="weekly">Weekly</option>
                        <option value="monthly">Monthly</option>
                    </select>

                    <!-- Daily: Select days of week -->
                    <div id="task-daily-options" style="display: none; margin-top: 12px;">
                        <label class="form-label" style="margin-bottom: 8px;">Select Days</label>
                        <div style="display: flex; gap: 8px; flex-wrap: wrap;">
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="task-day" value="0"> Sun
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="task-day" value="1"> Mon
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="task-day" value="2"> Tue
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="task-day" value="3"> Wed
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="task-day" value="4"> Thu
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="task-day" value="5"> Fri
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="task-day" value="6"> Sat
                            </label>
                        </div>
                    </div>

                    <!-- Weekly: Every X weeks -->
                    <div id="task-weekly-options" style="display: none; margin-top: 12px;">
                        <label class="form-label">Repeat every</label>
                        <div style="display: flex; align-items: center; gap: 8px;">
                            <input type="number" class="input" id="task-weekly-interval" min="1" max="52" value="1" style="width: 80px;">
                            <span>week(s)</span>
                        </div>
                        <div style="font-size: 12px; color: var(--text-secondary); margin-top: 4px;">
                            e.g., 1 = weekly, 2 = biweekly, 3 = every 3 weeks
                        </div>
                    </div>

                    <!-- Monthly: Every X months -->
                    <div id="task-monthly-options" style="display: none; margin-top: 12px;">
                        <label class="form-label">Repeat every</label>
                        <div style="display: flex; align-items: center; gap: 8px;">
                            <input type="number" class="input" id="task-monthly-interval" min="1" max="12" value="1" style="width: 80px;">
                            <span>month(s)</span>
                        </div>
                        <div style="font-size: 12px; color: var(--text-secondary); margin-top: 4px;">
                            e.g., 1 = monthly, 2 = every 2 months, 3 = quarterly
                        </div>
                    </div>
                </div>

                <div class="form-group">
                    <label class="form-label">Subtasks</label>
                    <div id="subtasks-container"></div>
                    <button type="button" class="btn btn-secondary" style="width: 100%; margin-top: 8px;" onclick="addSubtask()">
                        + Add Subtask
                    </button>
                </div>

                <div style="display: flex; gap: 12px; margin-top: 24px;">
                    <button type="submit" class="btn btn-primary" style="flex: 1;">Save Task</button>
                    <button type="button" class="btn btn-secondary" onclick="closeTaskModal()">Cancel</button>
                    <button type="button" class="btn btn-secondary" onclick="deleteTask()" id="delete-task-btn" style="display: none; background: var(--accent-danger); color: white;">Delete</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Event Modal -->
    <div id="event-modal" class="modal-overlay" style="display: none;">
        <div class="modal-content">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 24px;">
                <h2 class="text-2xl font-bold" id="event-modal-title">Add New Event</h2>
                <button class="icon-btn" onclick="closeEventModal()">✕</button>
            </div>

            <form id="event-form" onsubmit="saveEvent(event)">
                <div class="form-group">
                    <label class="form-label">Event Title *</label>
                    <input type="text" class="input" id="event-title" placeholder="Enter event title" required>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Date *</label>
                        <input type="date" class="input" id="event-date" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Category</label>
                        <select class="select" id="event-category">
                            <option value="work">Work</option>
                            <option value="personal">Personal</option>
                            <option value="school">School</option>
                            <option value="health">Health</option>
                            <option value="finance">Finance</option>
                        </select>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Start Time *</label>
                        <input type="time" class="input" id="event-start-time" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label">End Time *</label>
                        <input type="time" class="input" id="event-end-time" required>
                    </div>
                </div>

                <div class="form-group">
                    <label class="form-label">Location</label>
                    <input type="text" class="input" id="event-location" placeholder="Event location (optional)">
                </div>

                <div class="form-group">
                    <label class="form-label">Description</label>
                    <textarea class="textarea" id="event-description" placeholder="Add event description..."></textarea>
                </div>

                <div class="form-group">
                    <label class="checkbox-group">
                        <input type="checkbox" id="event-recurring">
                        <span>Recurring Event</span>
                    </label>
                </div>

                <div class="form-group" id="event-recurring-options" style="display: none;">
                    <label class="form-label">Recurrence Pattern</label>
                    <select class="select" id="event-recurrence" onchange="updateRecurringOptions('event')">
                        <option value="daily">Daily</option>
                        <option value="weekly">Weekly</option>
                        <option value="monthly">Monthly</option>
                    </select>

                    <!-- Daily: Select days of week -->
                    <div id="event-daily-options" style="display: none; margin-top: 12px;">
                        <label class="form-label" style="margin-bottom: 8px;">Select Days</label>
                        <div style="display: flex; gap: 8px; flex-wrap: wrap;">
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="event-day" value="0"> Sun
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="event-day" value="1"> Mon
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="event-day" value="2"> Tue
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="event-day" value="3"> Wed
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="event-day" value="4"> Thu
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="event-day" value="5"> Fri
                            </label>
                            <label style="display: flex; align-items: center; gap: 4px; cursor: pointer; padding: 6px 12px; background: var(--bg-secondary); border-radius: 8px; font-size: 14px;">
                                <input type="checkbox" class="event-day" value="6"> Sat
                            </label>
                        </div>
                    </div>

                    <!-- Weekly: Every X weeks -->
                    <div id="event-weekly-options" style="display: none; margin-top: 12px;">
                        <label class="form-label">Repeat every</label>
                        <div style="display: flex; align-items: center; gap: 8px;">
                            <input type="number" class="input" id="event-weekly-interval" min="1" max="52" value="1" style="width: 80px;">
                            <span>week(s)</span>
                        </div>
                        <div style="font-size: 12px; color: var(--text-secondary); margin-top: 4px;">
                            e.g., 1 = weekly, 2 = biweekly, 3 = every 3 weeks
                        </div>
                    </div>

                    <!-- Monthly: Every X months -->
                    <div id="event-monthly-options" style="display: none; margin-top: 12px;">
                        <label class="form-label">Repeat every</label>
                        <div style="display: flex; align-items: center; gap: 8px;">
                            <input type="number" class="input" id="event-monthly-interval" min="1" max="12" value="1" style="width: 80px;">
                            <span>month(s)</span>
                        </div>
                        <div style="font-size: 12px; color: var(--text-secondary); margin-top: 4px;">
                            e.g., 1 = monthly, 2 = every 2 months, 3 = quarterly
                        </div>
                    </div>
                </div>

                <div style="display: flex; gap: 12px; margin-top: 24px;">
                    <button type="submit" class="btn btn-primary" style="flex: 1;">Save Event</button>
                    <button type="button" class="btn btn-secondary" onclick="closeEventModal()">Cancel</button>
                    <button type="button" class="btn btn-secondary" onclick="deleteEvent()" id="delete-event-btn" style="display: none; background: var(--accent-danger); color: white;">Delete</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Settings Modal -->
    <div id="settings-modal" class="modal-overlay" style="display: none;">
        <div class="modal-content">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 24px;">
                <h2 class="text-2xl font-bold">Settings</h2>
                <button class="icon-btn" onclick="closeSettingsModal()">✕</button>
            </div>

            <div class="card mb-4">
                <h3 class="text-lg font-bold mb-4">🎨 Appearance</h3>
                <div class="checkbox-group">
                    <input type="checkbox" id="dark-mode-toggle" onchange="toggleTheme()">
                    <span>Dark Mode</span>
                </div>
            </div>

            <div class="card mb-4">
                <h3 class="text-lg font-bold mb-4">☁️ Calendar Sync</h3>

                <!-- Login Status -->
                <div id="sync-login-status" style="display: none; padding: 12px; background: var(--bg-secondary); border-radius: 8px; margin-bottom: 16px; border: 2px solid var(--accent-success);">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px;">
                        <div>
                            <div style="font-size: 12px; color: var(--text-secondary); margin-bottom: 4px;">🔒 Logged In with Token:</div>
                            <div id="logged-in-token" style="font-family: monospace; font-size: 14px; font-weight: 600; color: var(--accent-success);"></div>
                        </div>
                    </div>
                    <button class="btn btn-secondary" style="width: 100%; background: var(--accent-danger); color: white; border: none;" onclick="logoutSync()">
                        🚪 Logout
                    </button>
                </div>

                <div id="sync-login-section">
                    <div style="margin-bottom: 16px;">
                        <button class="btn btn-primary" style="width: 100%; margin-bottom: 8px;" onclick="generateSyncToken()">
                            🔑 Generate Sync Token
                        </button>
                        <div id="sync-token-display" style="display: none; padding: 12px; background: var(--bg-secondary); border-radius: 8px; margin-top: 8px;">
                            <div style="font-size: 12px; color: var(--text-secondary); margin-bottom: 4px;">Your Sync Token:</div>
                            <div id="sync-token-value" style="font-family: monospace; font-size: 14px; word-break: break-all; margin-bottom: 8px;"></div>
                            <div style="display: flex; gap: 8px;">
                                <button class="btn btn-secondary" style="flex: 1;" onclick="copySyncToken()">
                                    📋 Copy Token
                                </button>
                                <button class="btn btn-primary" style="flex: 1;" onclick="loginWithCurrentToken()">
                                    🔐 Use This Token
                                </button>
                            </div>
                        </div>
                    </div>

                    <div style="border-top: 1px solid var(--border-color); padding-top: 16px;">
                        <div class="form-group">
                            <label class="form-label">Enter Sync Token to Login</label>
                            <textarea class="textarea" id="sync-token-input" placeholder="Paste sync token here to login and enable auto-sync..." style="min-height: 80px; font-family: monospace; font-size: 12px;"></textarea>
                        </div>
                        <button class="btn btn-primary" style="width: 100%;" onclick="loginWithToken()">
                            🔐 Login & Sync
                        </button>
                        <div id="sync-status" class="mt-4 text-sm text-secondary"></div>
                    </div>
                </div>
            </div>

            <div class="card mb-4">
                <h3 class="text-lg font-bold mb-4">💾 Data Management</h3>
                <div style="display: flex; gap: 12px; flex-direction: column;">
                    <button class="btn btn-secondary" style="width: 100%;" onclick="exportData()">
                        📥 Export Data
                    </button>
                    <button class="btn btn-secondary" style="width: 100%;" onclick="importData()">
                        📤 Import Data
                    </button>
                    <button class="btn btn-secondary" style="width: 100%; background: var(--accent-danger); color: white;" onclick="clearAllData()">
                        🗑️ Clear All Data
                    </button>
                </div>
            </div>

            <div class="card mb-4">
                <h3 class="text-lg font-bold mb-4">🔗 Quick Links</h3>
                <div style="display: flex; gap: 12px; flex-direction: column;">
                    <a href="https://commute-dashboard.onrender.com" target="_blank" rel="noopener noreferrer" class="btn btn-secondary" style="width: 100%; text-decoration: none; text-align: center; display: block;">
                        🚗 Commute Dashboard
                    </a>
                    <a href="https://smart-pantry.onrender.com" target="_blank" rel="noopener noreferrer" class="btn btn-secondary" style="width: 100%; text-decoration: none; text-align: center; display: block;">
                        🍽️ Smart Pantry
                    </a>
                </div>
            </div>

            <div class="card">
                <h3 class="text-lg font-bold mb-2">About</h3>
                <p class="text-sm text-secondary">Taskify || Planner Dashboard v2.0</p>
                <p class="text-sm text-secondary">Modern task management for productive people</p>
            </div>
        </div>
    </div>

    <script>
        // Global Variables
        const API_BASE_URL = 'https://rtd-n-line-api.onrender.com';
        let tasks = [];
        let events = [];
        let currentEditingTask = null;
        let currentEditingEvent = null;
        let timerInterval = null;
        let timerSeconds = 25 * 60;
        let timerRunning = false;
        let sessionsCompleted = 0;
        let currentFilter = 'all';
        let currentTimeInterval = null;

        // Initialize App
        document.addEventListener('DOMContentLoaded', function() {
            loadTasks();
            loadEvents();

            // Generate recurring instances after loading data
            generateRecurringInstances();

            loadNotes();
            loadTheme();
            loadSettings();
            loadSyncStatus();
            renderHub();
            renderBoard();
            renderPulse();
            initializeSortable();
            startCurrentTimeUpdater();

            // Set today's date in pulse view
            document.getElementById('pulse-date').valueAsDate = new Date();

            // Load recurring task checkbox handler
            document.getElementById('task-recurring').addEventListener('change', function(e) {
                document.getElementById('recurring-options').style.display = e.target.checked ? 'block' : 'none';
            });

            // Hide loading screen after everything is loaded
            setTimeout(() => {
                document.getElementById('loading-screen').classList.add('hidden');
            }, 1000);

            // Update header date/time and greeting
            updateHeaderDateTime();
            setInterval(updateHeaderDateTime, 60000); // Update every minute

            // Load recurring event checkbox handler
            document.getElementById('event-recurring').addEventListener('change', function(e) {
                document.getElementById('event-recurring-options').style.display = e.target.checked ? 'block' : 'none';
            });

            // Setup sync and auto-refresh intervals
            setupSyncIntervals();
        });

        // Local Storage Functions
        function loadTasks() {
            const stored = localStorage.getItem('taskify_elite');
            if (stored) {
                tasks = JSON.parse(stored);
            }
        }

        function saveTasks() {
            localStorage.setItem('taskify_elite', JSON.stringify(tasks));
            renderHub();
            renderBoard();
            renderPulse();
            // Trigger auto-sync when data changes (debounced via uploadLocalChanges)
            uploadLocalChanges();
        }

        function loadEvents() {
            const stored = localStorage.getItem('taskify_events');
            if (stored) {
                events = JSON.parse(stored);
            }
        }

        function saveEvents() {
            localStorage.setItem('taskify_events', JSON.stringify(events));
            renderHub();
            renderPulse();
            // Trigger auto-sync when data changes (debounced via uploadLocalChanges)
            uploadLocalChanges();
        }

        function loadNotes() {
            const notes = localStorage.getItem('taskify_notes');
            if (notes) {
                document.getElementById('notes-textarea').value = notes;
            }
            const timestamp = localStorage.getItem('taskify_notes_timestamp');
            if (timestamp) {
                document.getElementById('notes-timestamp').textContent = new Date(timestamp).toLocaleString();
            }
        }

        function saveNotes() {
            const notes = document.getElementById('notes-textarea').value;
            localStorage.setItem('taskify_notes', notes);
            localStorage.setItem('taskify_notes_timestamp', new Date().toISOString());
            document.getElementById('notes-timestamp').textContent = new Date().toLocaleString();
        }

        function loadTheme() {
            const theme = localStorage.getItem('taskify_theme') || 'dark';
            document.documentElement.setAttribute('data-theme', theme);
            const toggle = document.getElementById('dark-mode-toggle');
            if (toggle) {
                toggle.checked = theme === 'dark';
            }
        }

        function loadSettings() {
            const focusDuration = localStorage.getItem('taskify_focus_duration') || 25;
            document.getElementById('focus-duration').value = focusDuration;
            timerSeconds = focusDuration * 60;
            updateTimerDisplay();
        }

        // Theme Toggle
        function toggleTheme() {
            const currentTheme = document.documentElement.getAttribute('data-theme');
            const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
            document.documentElement.setAttribute('data-theme', newTheme);
            localStorage.setItem('taskify_theme', newTheme);
            const toggle = document.getElementById('dark-mode-toggle');
            if (toggle) {
                toggle.checked = newTheme === 'dark';
            }
        }

        // View Switching
        function switchView(viewName) {
            // Hide all views
            document.querySelectorAll('.view-container').forEach(view => {
                view.classList.remove('active');
            });

            // Show selected view
            document.getElementById(`${viewName}-view`).classList.add('active');

            // Update nav buttons
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.currentTarget.classList.add('active');

            // Refresh view data
            if (viewName === 'hub') renderHub();
            if (viewName === 'board') renderBoard();
            if (viewName === 'pulse') renderPulse();
        }

        // Hub View (Dashboard)
        function renderHub() {
            // Filter out recurring templates (only show actual instances and non-recurring tasks)
            const visibleTasks = tasks.filter(t => !t.isRecurringTemplate);
            const visibleEvents = events.filter(e => !e.isRecurringTemplate);

            const total = visibleTasks.length;
            const completed = visibleTasks.filter(t => t.status === 'done').length;
            const active = visibleTasks.filter(t => t.status === 'in-progress').length;
            const completionRate = total > 0 ? Math.round((completed / total) * 100) : 0;
            const highPriority = visibleTasks.filter(t => t.priority === 'high' && t.status !== 'done').length;

            // Calculate overdue
            const today = getTodayDateString();
            const overdue = visibleTasks.filter(t => t.dueDate && t.dueDate < today && t.status !== 'done').length;

            // Calculate this week's tasks
            const weekFromNow = new Date();
            weekFromNow.setDate(weekFromNow.getDate() + 7);
            const year = weekFromNow.getFullYear();
            const month = String(weekFromNow.getMonth() + 1).padStart(2, '0');
            const day = String(weekFromNow.getDate()).padStart(2, '0');
            const weekFromNowStr = `${year}-${month}-${day}`;
            const thisWeek = visibleTasks.filter(t => t.dueDate && t.dueDate <= weekFromNowStr && t.dueDate >= today).length;

            document.getElementById('completion-rate').textContent = `${completionRate}%`;
            document.getElementById('completed-count').textContent = completed;
            document.getElementById('active-count').textContent = active;
            document.getElementById('high-priority-count').textContent = highPriority;
            document.getElementById('overdue-count').textContent = overdue;
            document.getElementById('week-count').textContent = thisWeek;
            document.getElementById('total-count').textContent = total;

            // Render today's tasks
            const todayTasks = visibleTasks.filter(t => {
                if (!t.dueDate) return false;
                return t.dueDate === today && t.status !== 'done';
            });

            const todayContainer = document.getElementById('today-tasks');
            if (todayTasks.length === 0) {
                todayContainer.innerHTML = '<div class="empty-state"><div class="empty-state-icon">🎉</div><div>No tasks due today! Great job!</div></div>';
            } else {
                todayContainer.innerHTML = todayTasks.map(task => `
                    <div class="task-card" onclick="editTask('${task.id}')">
                        <div style="display: flex; justify-content: space-between; align-items: start; margin-bottom: 8px;">
                            <div style="flex: 1;">
                                <div style="font-weight: 600; margin-bottom: 4px;">${task.title}</div>
                                <div style="display: flex; gap: 8px; flex-wrap: wrap;">
                                    <span class="tag priority-${task.priority}">${task.priority}</span>
                                    <span class="tag status-${task.status}">${task.status.replace('-', ' ')}</span>
                                    ${task.category ? `<span class="tag" style="background: rgba(99, 102, 241, 0.2);">${task.category}</span>` : ''}
                                </div>
                            </div>
                            ${task.startTime ? `<div style="font-size: 12px; color: var(--text-secondary);">${task.startTime}</div>` : ''}
                        </div>
                        ${task.description ? `<div style="font-size: 14px; color: var(--text-secondary); margin-top: 8px;">${task.description}</div>` : ''}
                    </div>
                `).join('');
            }

            // Render today's events
            const todayEvents = visibleEvents.filter(e => e.date === today);
            const eventsContainer = document.getElementById('today-events');
            if (todayEvents.length === 0) {
                eventsContainer.innerHTML = '<div class="empty-state"><div class="empty-state-icon">📅</div><div>No events scheduled today</div></div>';
            } else {
                eventsContainer.innerHTML = todayEvents.sort((a, b) => a.startTime.localeCompare(b.startTime)).map(event => `
                    <div class="task-card" onclick="editEvent('${event.id}')">
                        <div style="display: flex; justify-content: space-between; align-items: start; margin-bottom: 8px;">
                            <div style="flex: 1;">
                                <div style="font-weight: 600; margin-bottom: 4px;">${event.title}</div>
                                <div style="display: flex; gap: 8px; flex-wrap: wrap;">
                                    <span class="tag" style="background: rgba(99, 102, 241, 0.2);">${event.category || 'event'}</span>
                                    ${event.location ? `<span class="tag" style="background: rgba(139, 92, 246, 0.2);">📍 ${event.location}</span>` : ''}
                                </div>
                            </div>
                            <div style="font-size: 12px; color: var(--text-secondary);">${event.startTime} - ${event.endTime}</div>
                        </div>
                        ${event.description ? `<div style="font-size: 14px; color: var(--text-secondary); margin-top: 8px;">${event.description}</div>` : ''}
                    </div>
                `).join('');
            }

            // Render upcoming events (next 7 days, excluding today)
            const weekFromNowDate = new Date();
            weekFromNowDate.setDate(weekFromNowDate.getDate() + 7);
            const upcomingEvents = visibleEvents.filter(e => e.date > today && e.date <= weekFromNowStr).sort((a, b) => {
                if (a.date === b.date) return a.startTime.localeCompare(b.startTime);
                return a.date.localeCompare(b.date);
            });

            const upcomingEventsContainer = document.getElementById('upcoming-events');
            if (upcomingEvents.length === 0) {
                upcomingEventsContainer.innerHTML = '<div class="empty-state"><div class="empty-state-icon">🗓️</div><div>No upcoming events in the next 7 days</div></div>';
            } else {
                upcomingEventsContainer.innerHTML = upcomingEvents.map(event => {
                    const eventDate = new Date(event.date + 'T00:00:00');
                    const dateStr = eventDate.toLocaleDateString('en-US', { weekday: 'short', month: 'short', day: 'numeric' });
                    return `
                    <div class="task-card" onclick="editEvent('${event.id}')">
                        <div style="display: flex; justify-content: space-between; align-items: start; margin-bottom: 8px;">
                            <div style="flex: 1;">
                                <div style="font-weight: 600; margin-bottom: 4px;">${event.title}</div>
                                <div style="display: flex; gap: 8px; flex-wrap: wrap;">
                                    <span class="tag" style="background: rgba(59, 130, 246, 0.2);">📅 ${dateStr}</span>
                                    <span class="tag" style="background: rgba(99, 102, 241, 0.2);">${event.category || 'event'}</span>
                                    ${event.location ? `<span class="tag" style="background: rgba(139, 92, 246, 0.2);">📍 ${event.location}</span>` : ''}
                                </div>
                            </div>
                            <div style="font-size: 12px; color: var(--text-secondary);">${event.startTime} - ${event.endTime}</div>
                        </div>
                        ${event.description ? `<div style="font-size: 14px; color: var(--text-secondary); margin-top: 8px;">${event.description}</div>` : ''}
                    </div>
                `;
                }).join('');
            }

            // Render all tasks list
            const filterSelect = document.getElementById('task-filter');
            const filterValue = filterSelect ? filterSelect.value : 'active';

            let filteredTasks = [];
            switch(filterValue) {
                case 'active':
                    filteredTasks = visibleTasks.filter(t => t.status !== 'done');
                    break;
                case 'overdue':
                    filteredTasks = visibleTasks.filter(t => t.dueDate && t.dueDate < today && t.status !== 'done');
                    break;
                case 'upcoming':
                    filteredTasks = visibleTasks.filter(t => t.dueDate && t.dueDate >= today && t.status !== 'done');
                    break;
                case 'completed':
                    filteredTasks = visibleTasks.filter(t => t.status === 'done');
                    break;
                case 'all':
                default:
                    filteredTasks = [...visibleTasks];
                    break;
            }

            // Sort by due date, then priority
            filteredTasks.sort((a, b) => {
                // Sort by due date first
                if (a.dueDate && b.dueDate) {
                    if (a.dueDate !== b.dueDate) return a.dueDate.localeCompare(b.dueDate);
                } else if (a.dueDate) return -1;
                else if (b.dueDate) return 1;

                // Then by priority
                const priorityOrder = { high: 0, medium: 1, low: 2 };
                return (priorityOrder[a.priority] || 1) - (priorityOrder[b.priority] || 1);
            });

            const allTasksContainer = document.getElementById('all-tasks-list');
            if (filteredTasks.length === 0) {
                allTasksContainer.innerHTML = '<div class="empty-state"><div class="empty-state-icon">📭</div><div>No tasks to show</div></div>';
            } else {
                allTasksContainer.innerHTML = filteredTasks.map(task => {
                    // Check if task is blocked
                    const { met: depsMet, blocking } = checkDependenciesMet(task);
                    const isBlocked = !depsMet && task.status === 'not-started';
                    const blockedStyle = isBlocked ? 'opacity: 0.7; border-left: 3px solid var(--accent-danger);' : '';

                    let blockedIndicator = '';
                    if (isBlocked) {
                        const blockingNames = blocking.map(t => t.title).join(', ');
                        blockedIndicator = `
                            <div style="margin-top: 8px; padding: 8px; background: rgba(239, 68, 68, 0.1); border-left: 3px solid var(--accent-danger); border-radius: 4px;">
                                <div style="font-size: 11px; font-weight: 600; color: var(--accent-danger); margin-bottom: 2px;">
                                    ⛔ BLOCKED
                                </div>
                                <div style="font-size: 10px; color: var(--text-secondary);">
                                    Waiting for: ${blockingNames}
                                </div>
                            </div>
                        `;
                    }

                    return `
                        <div class="task-card" onclick="editTask('${task.id}')" style="cursor: pointer; ${blockedStyle}">
                            <div style="display: flex; justify-content: space-between; align-items: start; margin-bottom: 8px;">
                                <div style="flex: 1;">
                                    <div style="font-weight: 600; margin-bottom: 4px;">${task.title}</div>
                                    <div style="display: flex; gap: 8px; flex-wrap: wrap;">
                                        <span class="tag priority-${task.priority}">${task.priority}</span>
                                        <span class="tag status-${task.status}">${task.status.replace('-', ' ')}</span>
                                        ${task.category ? `<span class="tag" style="background: rgba(99, 102, 241, 0.2);">${task.category}</span>` : ''}
                                    </div>
                                </div>
                                <div style="text-align: right;">
                                    ${task.dueDate ? `<div style="font-size: 12px; color: var(--text-secondary); margin-bottom: 4px;">📅 ${formatDate(task.dueDate)}</div>` : ''}
                                    ${task.startTime ? `<div style="font-size: 12px; color: var(--text-secondary);">${task.startTime}</div>` : ''}
                                </div>
                            </div>
                            ${task.description ? `<div style="font-size: 14px; color: var(--text-secondary); margin-top: 8px;">${task.description}</div>` : ''}
                            ${blockedIndicator}
                        </div>
                    `;
                }).join('');
            }
        }

        // Board View (Kanban)
        function renderBoard() {
            const columns = {
                'not-started': document.getElementById('not-started-column'),
                'in-progress': document.getElementById('in-progress-column'),
                'done': document.getElementById('done-column')
            };

            // Clear columns
            Object.values(columns).forEach(col => col.innerHTML = '');

            // Filter out recurring templates (only show actual instances and non-recurring tasks)
            let filteredTasks = tasks.filter(t => !t.isRecurringTemplate);
            const searchTerm = document.getElementById('board-search')?.value.toLowerCase();
            if (searchTerm) {
                filteredTasks = filteredTasks.filter(t =>
                    t.title.toLowerCase().includes(searchTerm) ||
                    (t.description && t.description.toLowerCase().includes(searchTerm))
                );
            }
            if (currentFilter !== 'all') {
                filteredTasks = filteredTasks.filter(t => t.category === currentFilter);
            }

            // Render tasks in columns
            filteredTasks.forEach(task => {
                const column = columns[task.status];
                if (column) {
                    const taskCard = createTaskCard(task);
                    column.appendChild(taskCard);
                }
            });

            // Show empty state if no tasks
            Object.entries(columns).forEach(([status, col]) => {
                if (col.children.length === 0) {
                    col.innerHTML = '<div class="empty-state" style="padding: 20px;"><div style="font-size: 32px; margin-bottom: 8px;">📭</div><div style="font-size: 12px;">No tasks</div></div>';
                }
            });
        }

        // Global flag to track if we're currently dragging
        let isDraggingTask = false;

        function createTaskCard(task) {
            const card = document.createElement('div');
            card.className = 'task-card';
            card.setAttribute('data-id', task.id);

            // Use click event which doesn't fire after drag
            card.addEventListener('click', (e) => {
                if (!isDraggingTask) {
                    editTask(task.id);
                }
            });

            let tagsHTML = '';
            if (task.tags && task.tags.length > 0) {
                tagsHTML = task.tags.map(tag => `<span class="tag" style="background: rgba(139, 92, 246, 0.2); color: var(--accent-secondary);">${tag}</span>`).join('');
            }

            // Check if task is blocked by dependencies
            const { met: depsMet, blocking } = checkDependenciesMet(task);
            const isBlocked = !depsMet && task.status === 'not-started';

            let blockedIndicator = '';
            if (isBlocked) {
                const blockingNames = blocking.map(t => t.title).join(', ');
                blockedIndicator = `
                    <div style="margin-top: 8px; padding: 8px; background: rgba(239, 68, 68, 0.1); border-left: 3px solid var(--accent-danger); border-radius: 4px;">
                        <div style="font-size: 11px; font-weight: 600; color: var(--accent-danger); margin-bottom: 2px;">
                            ⛔ BLOCKED
                        </div>
                        <div style="font-size: 10px; color: var(--text-secondary);">
                            Waiting for: ${blockingNames}
                        </div>
                    </div>
                `;
                // Add visual styling to blocked card
                card.style.opacity = '0.7';
                card.style.borderLeft = '3px solid var(--accent-danger)';
            }

            let subtaskProgress = '';
            if (task.subtasks && task.subtasks.length > 0) {
                const completed = task.subtasks.filter(st => st.completed).length;
                const total = task.subtasks.length;
                const percentage = (completed / total) * 100;
                subtaskProgress = `
                    <div style="margin-top: 12px;">
                        <div style="font-size: 12px; color: var(--text-secondary); margin-bottom: 4px;">
                            Subtasks: ${completed}/${total}
                        </div>
                        <div class="progress-bar">
                            <div class="progress-fill" style="width: ${percentage}%;"></div>
                        </div>
                    </div>
                `;
            }

            card.innerHTML = `
                <div style="display: flex; justify-content: space-between; align-items: start; margin-bottom: 8px;">
                    <div style="font-weight: 600; flex: 1;">${task.title}</div>
                    ${task.dueDate ? `<div style="font-size: 12px; color: var(--text-secondary);">📅 ${formatDate(task.dueDate)}</div>` : ''}
                </div>
                ${task.description ? `<div style="font-size: 14px; color: var(--text-secondary); margin-bottom: 8px;">${task.description}</div>` : ''}
                <div style="display: flex; gap: 8px; flex-wrap: wrap; margin-top: 8px;">
                    <span class="tag priority-${task.priority}">${task.priority}</span>
                    ${task.category ? `<span class="tag" style="background: rgba(99, 102, 241, 0.2);">${task.category}</span>` : ''}
                    ${tagsHTML}
                </div>
                ${subtaskProgress}
                ${blockedIndicator}
            `;

            return card;
        }

        function filterBoard(category) {
            currentFilter = category;

            // Update active button
            document.querySelectorAll('#board-filters .filter-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.currentTarget.classList.add('active');

            renderBoard();
        }

        function filterBoardTasks() {
            renderBoard();
        }

        // Initialize Sortable.js for drag and drop
        function initializeSortable() {
            const columns = ['not-started-column', 'in-progress-column', 'done-column'];
            const statusMap = {
                'not-started-column': 'not-started',
                'in-progress-column': 'in-progress',
                'done-column': 'done'
            };

            columns.forEach(colId => {
                const element = document.getElementById(colId);
                if (element) {
                    new Sortable(element, {
                        group: 'tasks',
                        animation: 150,
                        ghostClass: 'sortable-ghost',
                        dragClass: 'sortable-drag',
                        onStart: function(evt) {
                            isDraggingTask = true;
                        },
                        onEnd: function(evt) {
                            const taskId = evt.item.getAttribute('data-id');
                            const newStatus = statusMap[evt.to.id];
                            const oldStatus = statusMap[evt.from.id];

                            const task = tasks.find(t => t.id === taskId);
                            if (task) {
                                // Check if trying to start a blocked task
                                if (newStatus === 'in-progress' && oldStatus === 'not-started') {
                                    const { met, blocking } = checkDependenciesMet(task);
                                    if (!met) {
                                        // Revert the move
                                        evt.item.remove();
                                        const oldColumn = document.getElementById(evt.from.id);
                                        oldColumn.appendChild(evt.item);

                                        const blockingNames = blocking.map(t => t.title).join(', ');
                                        alert(`⛔ Cannot start "${task.title}"\n\nThis task is blocked by:\n${blockingNames}\n\nComplete those tasks first!`);

                                        setTimeout(() => {
                                            isDraggingTask = false;
                                        }, 100);
                                        return;
                                    }
                                }

                                task.status = newStatus;
                                task.updatedAt = new Date().toISOString();
                                saveTasks();

                                // Celebration on completion
                                if (newStatus === 'done') {
                                    confetti({
                                        particleCount: 100,
                                        spread: 70,
                                        origin: { y: 0.6 }
                                    });
                                }
                            }

                            // Reset drag flag after a short delay to prevent click from firing
                            setTimeout(() => {
                                isDraggingTask = false;
                            }, 100);
                        }
                    });
                }
            });
        }

        // Pulse View (Calendar Timeline)
        function renderPulse() {
            const selectedDate = document.getElementById('pulse-date').value;
            const dateEvents = events.filter(e => e.date === selectedDate);

            const container = document.getElementById('pulse-timeline');

            // Create 24-hour timeline
            let hoursHTML = '';
            for (let hour = 0; hour < 24; hour++) {
                const hourStr = String(hour).padStart(2, '0');
                const hourLabel = hour === 0 ? '12 AM' : hour < 12 ? `${hour} AM` : hour === 12 ? '12 PM' : `${hour - 12} PM`;

                hoursHTML += `
                    <div class="hour-row" data-hour="${hour}">
                        <div class="hour-label">${hourLabel}</div>
                        <div class="hour-content" id="hour-${hour}"></div>
                    </div>
                `;
            }

            container.innerHTML = hoursHTML;

            // Position events on timeline
            dateEvents.forEach(event => {
                const [startHour, startMin] = event.startTime.split(':').map(Number);
                const [endHour, endMin] = event.endTime.split(':').map(Number);

                // Calculate position and height
                const startMinutes = startHour * 60 + startMin;
                const endMinutes = endHour * 60 + endMin;
                const durationMinutes = endMinutes - startMinutes;

                // Position from top (in pixels, 1 minute = 1px)
                const topPosition = startMin;
                const height = durationMinutes;

                // Find the hour container
                const hourContainer = document.getElementById(`hour-${startHour}`);
                if (hourContainer) {
                    const eventDiv = document.createElement('div');
                    eventDiv.className = 'calendar-event';
                    eventDiv.style.top = `${topPosition}px`;
                    // Use min-height for duration indicator, but allow content to expand
                    eventDiv.style.minHeight = `${Math.max(height, 40)}px`;
                    eventDiv.onclick = () => editEvent(event.id);

                    // Check if event is currently active
                    if (selectedDate === getTodayDateString()) {
                        const now = new Date();
                        const nowMinutes = now.getHours() * 60 + now.getMinutes();
                        if (nowMinutes >= startMinutes && nowMinutes <= endMinutes) {
                            eventDiv.classList.add('active');
                        }
                    }

                    eventDiv.innerHTML = `
                        <div style="font-weight: 700; margin-bottom: 2px; line-height: 1.3;">${event.title}</div>
                        <div style="font-size: 11px; opacity: 0.9; line-height: 1.3;">${event.startTime} - ${event.endTime}</div>
                        ${event.location ? `<div style="font-size: 11px; margin-top: 2px; line-height: 1.3;">📍 ${event.location}</div>` : ''}
                        ${event.description ? `<div style="font-size: 11px; margin-top: 4px; opacity: 0.8; line-height: 1.3;">${event.description}</div>` : ''}
                    `;

                    hourContainer.appendChild(eventDiv);
                }
            });

            // Add or update current time indicator
            updateCurrentTimeIndicator();
        }

        function updateCurrentTimeIndicator() {
            const selectedDate = document.getElementById('pulse-date').value;
            const today = getTodayDateString();

            // Remove existing indicator
            const existingIndicator = document.querySelector('.current-time-indicator');
            if (existingIndicator) {
                existingIndicator.remove();
            }

            // Only show indicator if viewing today
            if (selectedDate !== today) return;

            const now = new Date();
            const hours = now.getHours();
            const minutes = now.getMinutes();
            const totalMinutes = hours * 60 + minutes;

            // Calculate position (60px per hour)
            const topPosition = (totalMinutes / 60) * 60;

            const indicator = document.createElement('div');
            indicator.className = 'current-time-indicator';
            indicator.style.top = `${topPosition}px`;
            indicator.setAttribute('data-time', `${String(hours).padStart(2, '0')}:${String(minutes).padStart(2, '0')}`);

            const timeline = document.getElementById('pulse-timeline');
            if (timeline) {
                timeline.appendChild(indicator);
            }

            // Re-check active events
            const dateEvents = events.filter(e => e.date === selectedDate);
            dateEvents.forEach(event => {
                const [startHour, startMin] = event.startTime.split(':').map(Number);
                const [endHour, endMin] = event.endTime.split(':').map(Number);
                const startMinutes = startHour * 60 + startMin;
                const endMinutes = endHour * 60 + endMin;

                const eventElements = document.querySelectorAll('.calendar-event');
                eventElements.forEach(el => {
                    if (totalMinutes >= startMinutes && totalMinutes <= endMinutes) {
                        if (!el.classList.contains('active')) {
                            el.classList.add('active');
                        }
                    } else {
                        el.classList.remove('active');
                    }
                });
            });
        }

        function startCurrentTimeUpdater() {
            // Update current time indicator every minute
            currentTimeInterval = setInterval(() => {
                const selectedDate = document.getElementById('pulse-date').value;
                const today = getTodayDateString();
                if (selectedDate === today && document.getElementById('pulse-view').classList.contains('active')) {
                    updateCurrentTimeIndicator();
                }
            }, 60000); // Update every minute
        }

        function scrollToCurrentTime() {
            const now = new Date();
            const hours = now.getHours();
            const minutes = now.getMinutes();
            const totalMinutes = hours * 60 + minutes;
            const topPosition = (totalMinutes / 60) * 60;

            const pulseView = document.getElementById('pulse-view');
            if (pulseView) {
                pulseView.scrollTo({
                    top: topPosition - 100,
                    behavior: 'smooth'
                });
            }
        }

        function changePulseDate(days) {
            const dateInput = document.getElementById('pulse-date');
            const currentDate = new Date(dateInput.value);
            currentDate.setDate(currentDate.getDate() + days);
            dateInput.valueAsDate = currentDate;
            renderPulse();
        }

        // Focus Mode (Timer)
        // Enhanced Focus Mode Functions
        function enterFocusMode() {
            // Show overlay
            document.getElementById('focus-mode-overlay').classList.add('active');

            // Load high priority tasks for today
            renderFocusModeTasks();

            // Start timer
            if (!timerRunning) {
                timerRunning = true;
                timerInterval = setInterval(() => {
                    if (timerSeconds > 0) {
                        timerSeconds--;
                        updateTimerDisplay();
                        updateFocusOverlayTimer();
                    } else {
                        // Timer completed
                        pauseFocusMode();
                        sessionsCompleted++;
                        document.getElementById('sessions-completed').textContent = sessionsCompleted;

                        // Celebration
                        confetti({
                            particleCount: 150,
                            spread: 100,
                            origin: { y: 0.6 }
                        });

                        // Play sound (if supported)
                        const audio = new Audio('data:audio/wav;base64,UklGRnoGAABXQVZFZm10IBAAAAABAAEAQB8AAEAfAAABAAgAZGF0YQoGAACBhYqFbF1fdJivrJBhNjVgodDbq2EcBj+a2/LDciUFLIHO8tiJNwgZaLvt559NEAxQp+PwtmMcBjiR1/LMeSwFJHfH8N2QQAoUXrTp66hVFApGn+DyvmwhBi+K0O7Tm0IJHV606+qNRww');
                        audio.play().catch(() => {});

                        alert('🎉 Focus session complete! Great work!');
                        exitFocusMode();
                    }
                }, 1000);
            }
        }

        function exitFocusMode() {
            // Hide overlay
            document.getElementById('focus-mode-overlay').classList.remove('active');

            // Stop timer
            pauseTimer();
            resetTimer();
        }

        function pauseFocusMode() {
            timerRunning = false;
            if (timerInterval) {
                clearInterval(timerInterval);
                timerInterval = null;
            }
        }

        function renderFocusModeTasks() {
            const today = getTodayDateString();

            // Get high priority tasks due today
            const highPriorityTasks = tasks.filter(t =>
                t.priority === 'high' &&
                t.dueDate === today &&
                t.status !== 'done'
            );

            const container = document.getElementById('focus-high-priority-tasks');

            if (highPriorityTasks.length === 0) {
                container.innerHTML = '<div class="empty-state"><div class="empty-state-icon">✨</div><div>No high priority tasks for today!</div></div>';
            } else {
                container.innerHTML = highPriorityTasks.map(task => `
                    <div class="task-card" style="margin-bottom: 16px;">
                        <div style="display: flex; justify-content: space-between; align-items: start; margin-bottom: 8px;">
                            <div style="flex: 1;">
                                <div style="font-weight: 600; margin-bottom: 4px; font-size: 18px;">${task.title}</div>
                                <div style="display: flex; gap: 8px; flex-wrap: wrap;">
                                    <span class="tag status-${task.status}">${task.status.replace('-', ' ')}</span>
                                    ${task.category ? `<span class="tag" style="background: rgba(99, 102, 241, 0.2);">${task.category}</span>` : ''}
                                    ${task.startTime ? `<span class="tag" style="background: rgba(139, 92, 246, 0.2);">⏰ ${task.startTime}</span>` : ''}
                                </div>
                            </div>
                        </div>
                        ${task.description ? `<div style="font-size: 14px; color: var(--text-secondary); margin-top: 8px;">${task.description}</div>` : ''}
                    </div>
                `).join('');
            }
        }

        function updateFocusOverlayTimer() {
            const minutes = Math.floor(timerSeconds / 60);
            const seconds = timerSeconds % 60;
            const display = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
            document.getElementById('focus-overlay-timer').textContent = display;
        }

        function startTimer() {
            if (!timerRunning) {
                timerRunning = true;
                timerInterval = setInterval(() => {
                    if (timerSeconds > 0) {
                        timerSeconds--;
                        updateTimerDisplay();
                    } else {
                        // Timer completed
                        pauseTimer();
                        sessionsCompleted++;
                        document.getElementById('sessions-completed').textContent = sessionsCompleted;

                        // Celebration
                        confetti({
                            particleCount: 150,
                            spread: 100,
                            origin: { y: 0.6 }
                        });

                        // Play sound (if supported)
                        const audio = new Audio('data:audio/wav;base64,UklGRnoGAABXQVZFZm10IBAAAAABAAEAQB8AAEAfAAABAAgAZGF0YQoGAACBhYqFbF1fdJivrJBhNjVgodDbq2EcBj+a2/LDciUFLIHO8tiJNwgZaLvt559NEAxQp+PwtmMcBjiR1/LMeSwFJHfH8N2QQAoUXrTp66hVFApGn+DyvmwhBi+K0O7Tm0IJHV606+qNRww');
                        audio.play().catch(() => {});

                        alert('🎉 Focus session complete! Great work!');
                        resetTimer();
                    }
                }, 1000);
            }
        }

        function pauseTimer() {
            timerRunning = false;
            if (timerInterval) {
                clearInterval(timerInterval);
                timerInterval = null;
            }
        }

        function resetTimer() {
            pauseTimer();
            const duration = parseInt(document.getElementById('focus-duration').value) || 25;
            timerSeconds = duration * 60;
            updateTimerDisplay();
        }

        function updateTimerDisplay() {
            const minutes = Math.floor(timerSeconds / 60);
            const seconds = timerSeconds % 60;
            document.getElementById('timer-display').textContent =
                `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
        }

        function updateTimerDuration() {
            const duration = parseInt(document.getElementById('focus-duration').value) || 25;
            localStorage.setItem('taskify_focus_duration', duration);
            if (!timerRunning) {
                timerSeconds = duration * 60;
                updateTimerDisplay();
            }
        }

        // Task Modal Functions
        function openTaskModal(taskId = null) {
            currentEditingTask = taskId;
            const modal = document.getElementById('task-modal');
            const form = document.getElementById('task-form');
            const title = document.getElementById('task-modal-title');
            const deleteBtn = document.getElementById('delete-task-btn');

            form.reset();
            document.getElementById('subtasks-container').innerHTML = '';
            document.getElementById('recurring-options').style.display = 'none';

            // Reset recurring checkboxes and intervals
            document.querySelectorAll('.task-day').forEach(cb => cb.checked = false);
            document.getElementById('task-weekly-interval').value = 1;
            document.getElementById('task-monthly-interval').value = 1;

            // Populate dependencies dropdown
            const depsSelect = document.getElementById('task-dependencies');
            depsSelect.innerHTML = '';

            // Get all tasks except the current one being edited
            const availableTasks = tasks.filter(t => t.id !== taskId);
            availableTasks.forEach(t => {
                const option = document.createElement('option');
                option.value = t.id;
                option.textContent = `${t.title} (${t.status})`;
                depsSelect.appendChild(option);
            });

            if (taskId) {
                // Edit mode
                const task = tasks.find(t => t.id === taskId);
                if (task) {
                    title.textContent = 'Edit Task';
                    deleteBtn.style.display = 'block';

                    document.getElementById('task-title').value = task.title || '';
                    document.getElementById('task-category').value = task.category || 'work';
                    document.getElementById('task-priority').value = task.priority || 'medium';
                    document.getElementById('task-status').value = task.status || 'not-started';
                    document.getElementById('task-due-date').value = task.dueDate || '';
                    document.getElementById('task-start-time').value = task.startTime || '';
                    document.getElementById('task-end-time').value = task.endTime || '';
                    document.getElementById('task-project').value = task.project || '';
                    document.getElementById('task-tags').value = task.tags ? task.tags.join(', ') : '';
                    document.getElementById('task-description').value = task.description || '';
                    document.getElementById('task-milestone').value = task.milestone || '';

                    // Select dependencies
                    if (task.dependencies && task.dependencies.length > 0) {
                        Array.from(depsSelect.options).forEach(opt => {
                            if (task.dependencies.includes(opt.value)) {
                                opt.selected = true;
                            }
                        });
                    }

                    document.getElementById('task-recurring').checked = task.recurring || false;
                    document.getElementById('task-recurrence').value = task.recurrence || 'daily';

                    if (task.recurring) {
                        document.getElementById('recurring-options').style.display = 'block';
                        updateRecurringOptions('task');

                        // Populate recurring days
                        if (task.recurringDays && task.recurringDays.length > 0) {
                            document.querySelectorAll('.task-day').forEach(cb => {
                                cb.checked = task.recurringDays.includes(parseInt(cb.value));
                            });
                        }

                        // Populate intervals
                        if (task.recurringWeeklyInterval) {
                            document.getElementById('task-weekly-interval').value = task.recurringWeeklyInterval;
                        }
                        if (task.recurringMonthlyInterval) {
                            document.getElementById('task-monthly-interval').value = task.recurringMonthlyInterval;
                        }
                    }

                    if (task.subtasks) {
                        task.subtasks.forEach(subtask => {
                            addSubtask(subtask.title, subtask.completed);
                        });
                    }
                }
            } else {
                // Add mode
                title.textContent = 'Add New Task';
                deleteBtn.style.display = 'none';
            }

            modal.style.display = 'flex';
        }

        function updateRecurringOptions(type) {
            const pattern = document.getElementById(`${type}-recurrence`).value;

            // Hide all options first
            document.getElementById(`${type}-daily-options`).style.display = 'none';
            document.getElementById(`${type}-weekly-options`).style.display = 'none';
            document.getElementById(`${type}-monthly-options`).style.display = 'none';

            // Show the appropriate options
            if (pattern === 'daily') {
                document.getElementById(`${type}-daily-options`).style.display = 'block';
            } else if (pattern === 'weekly') {
                document.getElementById(`${type}-weekly-options`).style.display = 'block';
            } else if (pattern === 'monthly') {
                document.getElementById(`${type}-monthly-options`).style.display = 'block';
            }
        }

        function closeTaskModal() {
            document.getElementById('task-modal').style.display = 'none';
            currentEditingTask = null;
        }

        function saveTask(event) {
            event.preventDefault();

            const taskData = {
                id: currentEditingTask || generateId(),
                title: document.getElementById('task-title').value,
                category: document.getElementById('task-category').value,
                priority: document.getElementById('task-priority').value,
                status: document.getElementById('task-status').value,
                dueDate: document.getElementById('task-due-date').value,
                startTime: document.getElementById('task-start-time').value,
                endTime: document.getElementById('task-end-time').value,
                project: document.getElementById('task-project').value,
                tags: document.getElementById('task-tags').value.split(',').map(t => t.trim()).filter(t => t),
                description: document.getElementById('task-description').value,
                milestone: document.getElementById('task-milestone').value,
                dependencies: Array.from(document.getElementById('task-dependencies').selectedOptions).map(opt => opt.value),
                recurring: document.getElementById('task-recurring').checked,
                recurrence: document.getElementById('task-recurrence').value,
                recurringDays: Array.from(document.querySelectorAll('.task-day:checked')).map(cb => parseInt(cb.value)),
                recurringWeeklyInterval: parseInt(document.getElementById('task-weekly-interval').value) || 1,
                recurringMonthlyInterval: parseInt(document.getElementById('task-monthly-interval').value) || 1,
                isRecurringTemplate: document.getElementById('task-recurring').checked, // Mark as template if recurring
                subtasks: getSubtasks(),
                createdAt: currentEditingTask ? tasks.find(t => t.id === currentEditingTask).createdAt : new Date().toISOString(),
                updatedAt: new Date().toISOString()
            };

            // Check if trying to start a task with unmet dependencies
            if (taskData.status === 'in-progress') {
                const { met, blocking } = checkDependenciesMet(taskData);
                if (!met) {
                    const blockingNames = blocking.map(t => t.title).join(', ');
                    if (!confirm(`⚠️ Warning: This task has incomplete dependencies:\n\n${blockingNames}\n\nAre you sure you want to start it anyway?`)) {
                        return;
                    }
                }
            }

            if (currentEditingTask) {
                // Update existing task
                const index = tasks.findIndex(t => t.id === currentEditingTask);
                if (index !== -1) {
                    tasks[index] = taskData;
                }
            } else {
                // Add new task
                tasks.push(taskData);
            }

            saveTasks();
            closeTaskModal();

            // Generate recurring instances if this is a recurring task
            if (taskData.recurring && taskData.isRecurringTemplate) {
                generateRecurringInstances();
            }

            // Show success message
            showNotification(currentEditingTask ? 'Task updated!' : 'Task created!', 'success');
        }

        function deleteTask() {
            if (!currentEditingTask) return;

            const task = tasks.find(t => t.id === currentEditingTask);
            if (!task) return;

            // Check if this is a recurring instance
            if (task.recurringParentId) {
                const choice = confirm(
                    '⚠️ This is a recurring task instance.\n\n' +
                    'Click OK to delete ONLY this occurrence\n' +
                    'Click Cancel to delete ALL FUTURE occurrences'
                );

                if (choice) {
                    // Delete only this instance
                    tasks = tasks.filter(t => t.id !== currentEditingTask);
                    saveTasks();
                    closeTaskModal();
                    showNotification('Task occurrence deleted!', 'success');
                } else {
                    // Delete all future occurrences (and the template)
                    const instanceDate = task.instanceDate;
                    tasks = tasks.filter(t => {
                        // Keep if not related to this recurring series
                        if (t.recurringParentId !== task.recurringParentId && t.id !== task.recurringParentId) {
                            return true;
                        }
                        // Keep if it's an instance before this date
                        if (t.instanceDate && t.instanceDate < instanceDate) {
                            return true;
                        }
                        // Delete template and all future instances
                        return false;
                    });
                    saveTasks();
                    closeTaskModal();
                    showNotification('Future occurrences deleted!', 'success');
                }
            } else if (task.isRecurringTemplate) {
                // Deleting the template - confirm deletion of all instances
                if (confirm('⚠️ This will delete the recurring task and ALL its future occurrences. Continue?')) {
                    tasks = tasks.filter(t => t.id !== currentEditingTask && t.recurringParentId !== currentEditingTask);
                    saveTasks();
                    closeTaskModal();
                    showNotification('Recurring task deleted!', 'success');
                }
            } else {
                // Regular task deletion
                if (confirm('Are you sure you want to delete this task?')) {
                    tasks = tasks.filter(t => t.id !== currentEditingTask);
                    saveTasks();
                    closeTaskModal();
                    showNotification('Task deleted!', 'success');
                }
            }
        }

        function editTask(taskId) {
            openTaskModal(taskId);
        }

        // Event Modal Functions
        function openEventModal(eventId = null) {
            currentEditingEvent = eventId;
            const modal = document.getElementById('event-modal');
            const form = document.getElementById('event-form');
            const title = document.getElementById('event-modal-title');
            const deleteBtn = document.getElementById('delete-event-btn');

            form.reset();
            document.getElementById('event-recurring-options').style.display = 'none';

            // Reset recurring checkboxes and intervals
            document.querySelectorAll('.event-day').forEach(cb => cb.checked = false);
            document.getElementById('event-weekly-interval').value = 1;
            document.getElementById('event-monthly-interval').value = 1;

            if (eventId) {
                // Edit mode
                const event = events.find(e => e.id === eventId);
                if (event) {
                    title.textContent = 'Edit Event';
                    deleteBtn.style.display = 'block';

                    document.getElementById('event-title').value = event.title || '';
                    document.getElementById('event-date').value = event.date || '';
                    document.getElementById('event-category').value = event.category || 'work';
                    document.getElementById('event-start-time').value = event.startTime || '';
                    document.getElementById('event-end-time').value = event.endTime || '';
                    document.getElementById('event-location').value = event.location || '';
                    document.getElementById('event-description').value = event.description || '';
                    document.getElementById('event-recurring').checked = event.recurring || false;
                    document.getElementById('event-recurrence').value = event.recurrence || 'daily';

                    if (event.recurring) {
                        document.getElementById('event-recurring-options').style.display = 'block';
                        updateRecurringOptions('event');

                        // Populate recurring days
                        if (event.recurringDays && event.recurringDays.length > 0) {
                            document.querySelectorAll('.event-day').forEach(cb => {
                                cb.checked = event.recurringDays.includes(parseInt(cb.value));
                            });
                        }

                        // Populate intervals
                        if (event.recurringWeeklyInterval) {
                            document.getElementById('event-weekly-interval').value = event.recurringWeeklyInterval;
                        }
                        if (event.recurringMonthlyInterval) {
                            document.getElementById('event-monthly-interval').value = event.recurringMonthlyInterval;
                        }
                    }
                }
            } else {
                // Add mode
                title.textContent = 'Add New Event';
                deleteBtn.style.display = 'none';
                // Set default date to today
                document.getElementById('event-date').valueAsDate = new Date();
            }

            modal.style.display = 'flex';
        }

        function closeEventModal() {
            document.getElementById('event-modal').style.display = 'none';
            currentEditingEvent = null;
        }

        function saveEvent(e) {
            e.preventDefault();

            const eventData = {
                id: currentEditingEvent || generateId(),
                title: document.getElementById('event-title').value,
                date: document.getElementById('event-date').value,
                category: document.getElementById('event-category').value,
                startTime: document.getElementById('event-start-time').value,
                endTime: document.getElementById('event-end-time').value,
                location: document.getElementById('event-location').value,
                description: document.getElementById('event-description').value,
                recurring: document.getElementById('event-recurring').checked,
                recurrence: document.getElementById('event-recurrence').value,
                recurringDays: Array.from(document.querySelectorAll('.event-day:checked')).map(cb => parseInt(cb.value)),
                recurringWeeklyInterval: parseInt(document.getElementById('event-weekly-interval').value) || 1,
                recurringMonthlyInterval: parseInt(document.getElementById('event-monthly-interval').value) || 1,
                isRecurringTemplate: document.getElementById('event-recurring').checked, // Mark as template if recurring
                createdAt: currentEditingEvent ? events.find(e => e.id === currentEditingEvent).createdAt : new Date().toISOString(),
                updatedAt: new Date().toISOString()
            };

            if (currentEditingEvent) {
                // Update existing event
                const index = events.findIndex(e => e.id === currentEditingEvent);
                if (index !== -1) {
                    events[index] = eventData;
                }
            } else {
                // Add new event
                events.push(eventData);
            }

            saveEvents();
            closeEventModal();

            // Generate recurring instances if this is a recurring event
            if (eventData.recurring && eventData.isRecurringTemplate) {
                generateRecurringInstances();
            }

            showNotification(currentEditingEvent ? 'Event updated!' : 'Event created!', 'success');
        }

        function deleteEvent() {
            if (!currentEditingEvent) return;

            const event = events.find(e => e.id === currentEditingEvent);
            if (!event) return;

            // Check if this is a recurring instance
            if (event.recurringParentId) {
                const choice = confirm(
                    '⚠️ This is a recurring event instance.\n\n' +
                    'Click OK to delete ONLY this occurrence\n' +
                    'Click Cancel to delete ALL FUTURE occurrences'
                );

                if (choice) {
                    // Delete only this instance
                    events = events.filter(e => e.id !== currentEditingEvent);
                    saveEvents();
                    closeEventModal();
                    showNotification('Event occurrence deleted!', 'success');
                } else {
                    // Delete all future occurrences (and the template)
                    const instanceDate = event.instanceDate;
                    events = events.filter(e => {
                        // Keep if not related to this recurring series
                        if (e.recurringParentId !== event.recurringParentId && e.id !== event.recurringParentId) {
                            return true;
                        }
                        // Keep if it's an instance before this date
                        if (e.instanceDate && e.instanceDate < instanceDate) {
                            return true;
                        }
                        // Delete template and all future instances
                        return false;
                    });
                    saveEvents();
                    closeEventModal();
                    showNotification('Future occurrences deleted!', 'success');
                }
            } else if (event.isRecurringTemplate) {
                // Deleting the template - confirm deletion of all instances
                if (confirm('⚠️ This will delete the recurring event and ALL its future occurrences. Continue?')) {
                    events = events.filter(e => e.id !== currentEditingEvent && e.recurringParentId !== currentEditingEvent);
                    saveEvents();
                    closeEventModal();
                    showNotification('Recurring event deleted!', 'success');
                }
            } else {
                // Regular event deletion
                if (confirm('Are you sure you want to delete this event?')) {
                    events = events.filter(e => e.id !== currentEditingEvent);
                    saveEvents();
                    closeEventModal();
                    showNotification('Event deleted!', 'success');
                }
            }
        }

        function editEvent(eventId) {
            openEventModal(eventId);
        }

        // FAB Menu Toggle
        function toggleFabMenu() {
            const menu = document.getElementById('fab-menu');
            menu.classList.toggle('hidden');
        }

        function addSubtask(title = '', completed = false) {
            const container = document.getElementById('subtasks-container');
            const subtaskDiv = document.createElement('div');
            subtaskDiv.className = 'subtask-item';
            subtaskDiv.innerHTML = `
                <input type="checkbox" ${completed ? 'checked' : ''} style="width: 20px; height: 20px;">
                <input type="text" class="input" placeholder="Subtask title" value="${title}" style="flex: 1; margin: 0;">
                <button type="button" class="icon-btn" onclick="this.parentElement.remove()" style="width: 32px; height: 32px; font-size: 14px;">✕</button>
            `;
            container.appendChild(subtaskDiv);
        }

        function getSubtasks() {
            const subtasks = [];
            document.querySelectorAll('#subtasks-container .subtask-item').forEach(item => {
                const checkbox = item.querySelector('input[type="checkbox"]');
                const input = item.querySelector('input[type="text"]');
                if (input.value.trim()) {
                    subtasks.push({
                        title: input.value.trim(),
                        completed: checkbox.checked
                    });
                }
            });
            return subtasks;
        }

        // Settings Modal
        function openSettingsModal() {
            document.getElementById('settings-modal').style.display = 'flex';
        }

        function closeSettingsModal() {
            document.getElementById('settings-modal').style.display = 'none';
        }

        // Token-Based Sync Functions
        function loadSyncStatus() {
            const storedToken = localStorage.getItem('taskify_sync_token');
            if (storedToken) {
                showLoggedInStatus(storedToken);
                // Perform initial sync
                autoSync();
            }
        }

        function showLoggedInStatus(token) {
            document.getElementById('sync-login-status').style.display = 'block';
            document.getElementById('sync-login-section').style.display = 'none';
            document.getElementById('logged-in-token').textContent = token;
            document.getElementById('sync-indicator').style.display = 'block';
        }

        function showLoggedOutStatus() {
            document.getElementById('sync-login-status').style.display = 'none';
            document.getElementById('sync-login-section').style.display = 'block';
            document.getElementById('sync-token-display').style.display = 'none';
            document.getElementById('sync-status').textContent = '';
            document.getElementById('sync-indicator').style.display = 'none';
        }

        async function loginWithToken() {
            const tokenInput = document.getElementById('sync-token-input').value.trim().toUpperCase();
            const statusDiv = document.getElementById('sync-status');

            if (!tokenInput) {
                statusDiv.textContent = '❌ Please enter a sync token';
                statusDiv.style.color = 'var(--accent-danger)';
                return;
            }

            // Validate token format (PLAN-XXXXX)
            if (!tokenInput.match(/^PLAN-[A-Z0-9]{5}$/)) {
                statusDiv.textContent = '❌ Invalid token format. Use PLAN-XXXXX';
                statusDiv.style.color = 'var(--accent-danger)';
                return;
            }

            try {
                statusDiv.textContent = '🔄 Logging in and syncing...';
                statusDiv.style.color = 'var(--text-secondary)';

                // Extract token ID (remove PLAN- prefix)
                const tokenId = tokenInput.substring(5);

                // Fetch data from server to verify token exists
                const response = await fetch(`${API_BASE_URL}/sync/${tokenId}`, {
                    method: 'GET',
                    headers: {
                        'Content-Type': 'application/json',
                    }
                });

                if (!response.ok) {
                    if (response.status === 404) {
                        throw new Error('Token not found. Please check and try again.');
                    }
                    throw new Error('Failed to connect to sync server');
                }

                const syncData = await response.json();

                // Validate the data
                if (!syncData.tasks || !syncData.events) {
                    throw new Error('Invalid sync data format');
                }

                // Merge the data
                if (tasks.length > 0 || events.length > 0) {
                    if (!confirm('This will merge the synced data with your current data. Continue?')) {
                        statusDiv.textContent = '';
                        return;
                    }
                }

                // Merge tasks (avoid duplicates by checking IDs)
                const existingTaskIds = new Set(tasks.map(t => t.id));
                const newTasks = syncData.tasks.filter(t => !existingTaskIds.has(t.id));
                tasks = [...tasks, ...newTasks];

                // Merge events
                const existingEventIds = new Set(events.map(e => e.id));
                const newEvents = syncData.events.filter(e => !existingEventIds.has(e.id));
                events = [...events, ...newEvents];

                // Save
                saveTasks();
                saveEvents();

                // Store the token
                localStorage.setItem('taskify_sync_token', tokenInput);

                // Update UI
                showLoggedInStatus(tokenInput);
                document.getElementById('sync-token-input').value = '';
                statusDiv.textContent = '';

                // Re-render views with new data
                renderHub();
                renderBoard();
                renderPulse();

                showNotification(`Logged in! Synced ${newTasks.length} tasks and ${newEvents.length} events`, 'success');

                // Close modal after successful login
                setTimeout(() => closeSettingsModal(), 500);
            } catch (error) {
                statusDiv.textContent = `❌ ${error.message || 'Login failed. Check your connection.'}`;
                statusDiv.style.color = 'var(--accent-danger)';
                console.error('Login error:', error);
            }
        }

        function loginWithCurrentToken() {
            const token = document.getElementById('sync-token-value').textContent;
            if (token) {
                localStorage.setItem('taskify_sync_token', token);
                showLoggedInStatus(token);
                document.getElementById('sync-token-display').style.display = 'none';
                showNotification('Logged in with this token!', 'success');
                setTimeout(() => closeSettingsModal(), 500);
            }
        }

        function logoutSync() {
            if (confirm('Are you sure you want to logout? You can login again later with your token.')) {
                localStorage.removeItem('taskify_sync_token');
                showLoggedOutStatus();
                showNotification('Logged out successfully', 'success');
            }
        }

        async function autoSync() {
            const storedToken = localStorage.getItem('taskify_sync_token');
            if (!storedToken) return;

            try {
                const tokenId = storedToken.substring(5); // Remove PLAN- prefix

                // Step 1: Fetch latest data from server
                const fetchResponse = await fetch(`${API_BASE_URL}/sync/${tokenId}`, {
                    method: 'GET',
                    headers: {
                        'Content-Type': 'application/json',
                    }
                });

                let hasChanges = false;

                if (fetchResponse.ok) {
                    const serverData = await fetchResponse.json();

                    // Step 2: Merge server data with local data
                    if (serverData.tasks && serverData.events) {
                        const originalTaskCount = tasks.length;
                        const originalEventCount = events.length;

                        // Merge tasks - keep most recently updated version
                        const taskMap = new Map();

                        // Add local tasks to map
                        tasks.forEach(task => {
                            taskMap.set(task.id, task);
                        });

                        // Merge server tasks (only if newer or doesn't exist locally)
                        serverData.tasks.forEach(serverTask => {
                            const localTask = taskMap.get(serverTask.id);
                            if (!localTask || (serverTask.updatedAt && localTask.updatedAt && serverTask.updatedAt > localTask.updatedAt)) {
                                taskMap.set(serverTask.id, serverTask);
                                hasChanges = true;
                            }
                        });

                        // Merge events
                        const eventMap = new Map();

                        events.forEach(event => {
                            eventMap.set(event.id, event);
                        });

                        serverData.events.forEach(serverEvent => {
                            const localEvent = eventMap.get(serverEvent.id);
                            if (!localEvent || (serverEvent.updatedAt && localEvent.updatedAt && serverEvent.updatedAt > localEvent.updatedAt)) {
                                eventMap.set(serverEvent.id, serverEvent);
                                hasChanges = true;
                            }
                        });

                        // Convert maps back to arrays
                        tasks = Array.from(taskMap.values());
                        events = Array.from(eventMap.values());

                        // Save if there were changes
                        if (hasChanges) {
                            localStorage.setItem('taskify_elite', JSON.stringify(tasks));
                            localStorage.setItem('taskify_events', JSON.stringify(events));
                            renderHub();
                            renderBoard();
                            renderPulse();
                            console.log('Auto-sync: Downloaded and merged changes from server');
                        }
                    }
                }

                // Step 3: Upload current (possibly merged) data back to server
                const syncData = {
                    tasks: tasks,
                    events: events,
                    timestamp: new Date().toISOString(),
                    version: '2.0'
                };

                await fetch(`${API_BASE_URL}/sync/${tokenId}`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify(syncData)
                });

                console.log('Auto-sync completed (bidirectional)');
            } catch (error) {
                console.error('Auto-sync error:', error);
                // Don't show error notifications for auto-sync to avoid interrupting user
            }
        }

        // Upload only - used when local changes are made
        let uploadTimeout = null;
        async function uploadLocalChanges() {
            const storedToken = localStorage.getItem('taskify_sync_token');
            if (!storedToken) return;

            // Debounce uploads to avoid too many requests
            if (uploadTimeout) clearTimeout(uploadTimeout);

            uploadTimeout = setTimeout(async () => {
                try {
                    const tokenId = storedToken.substring(5);
                    const syncData = {
                        tasks: tasks,
                        events: events,
                        timestamp: new Date().toISOString(),
                        version: '2.0'
                    };

                    await fetch(`${API_BASE_URL}/sync/${tokenId}`, {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json',
                        },
                        body: JSON.stringify(syncData)
                    });

                    console.log('Local changes uploaded');
                } catch (error) {
                    console.error('Upload error:', error);
                }
            }, 1000); // Wait 1 second after last change before uploading
        }

        // Setup periodic sync and auto-refresh
        function setupSyncIntervals() {
            // Bidirectional sync every 30 seconds (download + upload)
            setInterval(() => {
                const storedToken = localStorage.getItem('taskify_sync_token');
                if (storedToken) {
                    autoSync();
                }
            }, 30 * 1000);

            // Auto-refresh page every 15 minutes if logged in
            setInterval(() => {
                const storedToken = localStorage.getItem('taskify_sync_token');
                if (storedToken) {
                    console.log('Auto-refreshing page to stay in sync...');
                    location.reload();
                }
            }, 15 * 60 * 1000);
        }

        async function generateSyncToken() {
            const statusDiv = document.getElementById('sync-status');

            try {
                statusDiv.textContent = '🔄 Generating token...';
                statusDiv.style.color = 'var(--text-secondary)';

                // Generate short 5-character token ID
                const tokenId = generateShortTokenId();
                const token = `PLAN-${tokenId}`;

                const syncData = {
                    tasks: tasks,
                    events: events,
                    timestamp: new Date().toISOString(),
                    version: '2.0'
                };

                // Upload to server
                const response = await fetch(`${API_BASE_URL}/sync/${tokenId}`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify(syncData)
                });

                if (!response.ok) {
                    throw new Error('Failed to upload data to server');
                }

                // Display the short token
                document.getElementById('sync-token-value').textContent = token;
                document.getElementById('sync-token-display').style.display = 'block';

                statusDiv.textContent = '✅ Token generated! You can copy it or use it to login.';
                statusDiv.style.color = 'var(--accent-success)';
                showNotification('Sync token generated!', 'success');
            } catch (error) {
                statusDiv.textContent = '❌ Failed to generate token. Check your connection.';
                statusDiv.style.color = 'var(--accent-danger)';
                console.error('Token generation error:', error);
            }
        }

        function generateShortTokenId() {
            // Generate 5-character alphanumeric ID
            const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
            let id = '';
            for (let i = 0; i < 5; i++) {
                id += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            return id;
        }

        function copySyncToken() {
            const tokenValue = document.getElementById('sync-token-value').textContent;

            // Copy to clipboard
            if (navigator.clipboard && navigator.clipboard.writeText) {
                navigator.clipboard.writeText(tokenValue).then(() => {
                    showNotification('Token copied to clipboard!', 'success');
                }).catch(() => {
                    fallbackCopyTextToClipboard(tokenValue);
                });
            } else {
                fallbackCopyTextToClipboard(tokenValue);
            }
        }

        function fallbackCopyTextToClipboard(text) {
            const textArea = document.createElement('textarea');
            textArea.value = text;
            textArea.style.position = 'fixed';
            textArea.style.left = '-999999px';
            document.body.appendChild(textArea);
            textArea.focus();
            textArea.select();

            try {
                document.execCommand('copy');
                showNotification('Token copied to clipboard!', 'success');
            } catch (err) {
                showNotification('Failed to copy token', 'error');
            }

            document.body.removeChild(textArea);
        }


        // Data Management
        function exportData() {
            const data = {
                tasks: tasks,
                events: events,
                notes: localStorage.getItem('taskify_notes'),
                settings: {
                    theme: localStorage.getItem('taskify_theme'),
                    serverUrl: localStorage.getItem('taskify_server_url'),
                    userId: localStorage.getItem('taskify_user_id'),
                    focusDuration: localStorage.getItem('taskify_focus_duration')
                },
                exportedAt: new Date().toISOString()
            };

            const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `taskify-elite-backup-${new Date().toISOString().split('T')[0]}.json`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);

            showNotification('Data exported successfully!', 'success');
        }

        function importData() {
            const input = document.createElement('input');
            input.type = 'file';
            input.accept = 'application/json';
            input.onchange = (e) => {
                const file = e.target.files[0];
                if (!file) return;

                const reader = new FileReader();
                reader.onload = (event) => {
                    try {
                        const data = JSON.parse(event.target.result);

                        if (confirm('This will replace all current data. Continue?')) {
                            if (data.tasks) {
                                tasks = data.tasks;
                                saveTasks();
                            }
                            if (data.events) {
                                events = data.events;
                                saveEvents();
                            }
                            if (data.notes) {
                                localStorage.setItem('taskify_notes', data.notes);
                                loadNotes();
                            }
                            if (data.settings) {
                                if (data.settings.theme) localStorage.setItem('taskify_theme', data.settings.theme);
                                if (data.settings.serverUrl) localStorage.setItem('taskify_server_url', data.settings.serverUrl);
                                if (data.settings.userId) localStorage.setItem('taskify_user_id', data.settings.userId);
                                if (data.settings.focusDuration) localStorage.setItem('taskify_focus_duration', data.settings.focusDuration);
                                loadTheme();
                                loadSettings();
                            }

                            showNotification('Data imported successfully!', 'success');
                            location.reload();
                        }
                    } catch (error) {
                        alert('Error importing data. Please check the file format.');
                        console.error('Import error:', error);
                    }
                };
                reader.readAsText(file);
            };
            input.click();
        }

        function clearAllData() {
            if (confirm('⚠️ This will delete ALL your data permanently. Are you absolutely sure?')) {
                if (confirm('This action cannot be undone. Click OK to confirm deletion.')) {
                    localStorage.clear();
                    tasks = [];
                    events = [];
                    saveTasks();
                    saveEvents();
                    showNotification('All data cleared!', 'success');
                    location.reload();
                }
            }
        }

        // Utility Functions
        function generateId() {
            return 'task_' + Date.now() + '_' + Math.random().toString(36).substr(2, 9);
        }

        // Recurring Task/Event Generation
        function generateRecurringInstances() {
            const today = new Date();
            const daysToGenerate = 90; // Generate 3 months ahead

            // Generate recurring tasks
            const recurringTasks = tasks.filter(t => t.recurring && t.isRecurringTemplate);
            recurringTasks.forEach(template => {
                generateTaskInstances(template, today, daysToGenerate);
            });

            // Generate recurring events
            const recurringEvents = events.filter(e => e.recurring && e.isRecurringTemplate);
            recurringEvents.forEach(template => {
                generateEventInstances(template, today, daysToGenerate);
            });
        }

        function generateTaskInstances(template, startDate, daysAhead) {
            const endDate = new Date(startDate);
            endDate.setDate(endDate.getDate() + daysAhead);

            const instances = [];
            let currentDate = new Date(template.dueDate || startDate);

            while (currentDate <= endDate) {
                if (shouldGenerateInstance(template, currentDate)) {
                    const dateStr = formatDateString(currentDate);

                    // Check if instance already exists
                    const existsAlready = tasks.some(t =>
                        t.recurringParentId === template.id && t.instanceDate === dateStr
                    );

                    if (!existsAlready) {
                        const instance = {
                            ...template,
                            id: generateId(),
                            recurringParentId: template.id,
                            instanceDate: dateStr,
                            isRecurringTemplate: false,
                            dueDate: dateStr,
                            status: 'not-started', // Reset status for new instances
                            createdAt: new Date().toISOString(),
                            updatedAt: new Date().toISOString()
                        };
                        instances.push(instance);
                    }
                }

                // Move to next potential date
                currentDate.setDate(currentDate.getDate() + 1);
            }

            if (instances.length > 0) {
                tasks.push(...instances);
                saveTasks();
            }
        }

        function generateEventInstances(template, startDate, daysAhead) {
            const endDate = new Date(startDate);
            endDate.setDate(endDate.getDate() + daysAhead);

            const instances = [];
            let currentDate = new Date(template.date || startDate);

            while (currentDate <= endDate) {
                if (shouldGenerateInstance(template, currentDate)) {
                    const dateStr = formatDateString(currentDate);

                    // Check if instance already exists
                    const existsAlready = events.some(e =>
                        e.recurringParentId === template.id && e.instanceDate === dateStr
                    );

                    if (!existsAlready) {
                        const instance = {
                            ...template,
                            id: generateId(),
                            recurringParentId: template.id,
                            instanceDate: dateStr,
                            isRecurringTemplate: false,
                            date: dateStr,
                            createdAt: new Date().toISOString(),
                            updatedAt: new Date().toISOString()
                        };
                        instances.push(instance);
                    }
                }

                // Move to next potential date
                currentDate.setDate(currentDate.getDate() + 1);
            }

            if (instances.length > 0) {
                events.push(...instances);
                saveEvents();
            }
        }

        function shouldGenerateInstance(template, date) {
            const { recurrence, recurringDays, recurringWeeklyInterval, recurringMonthlyInterval } = template;
            const startDate = new Date(template.dueDate || template.date);

            if (recurrence === 'daily') {
                // Check if this day of week is selected
                const dayOfWeek = date.getDay();
                return recurringDays && recurringDays.includes(dayOfWeek);
            } else if (recurrence === 'weekly') {
                // Check if correct week interval
                const daysDiff = Math.floor((date - startDate) / (1000 * 60 * 60 * 24));
                const weeksDiff = Math.floor(daysDiff / 7);
                const interval = recurringWeeklyInterval || 1;
                return weeksDiff % interval === 0 && date.getDay() === startDate.getDay();
            } else if (recurrence === 'monthly') {
                // Check if correct month interval and same day of month
                const monthsDiff = (date.getFullYear() - startDate.getFullYear()) * 12 +
                                   (date.getMonth() - startDate.getMonth());
                const interval = recurringMonthlyInterval || 1;
                return monthsDiff % interval === 0 && date.getDate() === startDate.getDate();
            }

            return false;
        }

        function formatDateString(date) {
            const year = date.getFullYear();
            const month = String(date.getMonth() + 1).padStart(2, '0');
            const day = String(date.getDate()).padStart(2, '0');
            return `${year}-${month}-${day}`;
        }

        function updateHeaderDateTime() {
            const now = new Date();

            // Format date and time
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            const dateStr = now.toLocaleDateString('en-US', options);
            const timeStr = now.toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit' });

            document.getElementById('header-datetime').textContent = `${dateStr} • ${timeStr}`;

            // Determine greeting based on time
            const hour = now.getHours();
            let greeting;
            if (hour < 12) {
                greeting = 'Good Morning • Have a great Workday';
            } else if (hour < 17) {
                greeting = 'Good Afternoon • Keep up the momentum';
            } else {
                greeting = 'Good Evening • Finish strong';
            }

            document.getElementById('header-greeting').textContent = greeting;
        }

        function getTodayDateString() {
            // Get local date in YYYY-MM-DD format (avoids timezone offset issues)
            const now = new Date();
            const year = now.getFullYear();
            const month = String(now.getMonth() + 1).padStart(2, '0');
            const day = String(now.getDate()).padStart(2, '0');
            return `${year}-${month}-${day}`;
        }

        // Dependency Management
        function checkDependenciesMet(task) {
            if (!task.dependencies || task.dependencies.length === 0) {
                return { met: true, blocking: [] };
            }

            const blockingTasks = [];
            for (const depId of task.dependencies) {
                const depTask = tasks.find(t => t.id === depId);
                if (depTask && depTask.status !== 'done') {
                    blockingTasks.push(depTask);
                }
            }

            return {
                met: blockingTasks.length === 0,
                blocking: blockingTasks
            };
        }

        function isTaskBlocked(task) {
            const { met } = checkDependenciesMet(task);
            return !met && task.status === 'not-started';
        }

        function getBlockingTasksInfo(task) {
            const { blocking } = checkDependenciesMet(task);
            if (blocking.length === 0) return null;

            return blocking.map(t => t.title).join(', ');
        }

        function formatDate(dateString) {
            if (!dateString) return '';
            const date = new Date(dateString + 'T00:00:00'); // Parse as local date
            const today = new Date();
            const tomorrow = new Date(today);
            tomorrow.setDate(tomorrow.getDate() + 1);

            if (date.toDateString() === today.toDateString()) return 'Today';
            if (date.toDateString() === tomorrow.toDateString()) return 'Tomorrow';

            return date.toLocaleDateString('en-US', { month: 'short', day: 'numeric' });
        }

        function showNotification(message, type = 'info') {
            // Simple notification system
            const notification = document.createElement('div');
            notification.textContent = message;
            notification.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                padding: 16px 24px;
                background: ${type === 'success' ? 'var(--accent-success)' : 'var(--accent-primary)'};
                color: white;
                border-radius: 12px;
                font-weight: 600;
                box-shadow: var(--shadow);
                z-index: 10000;
                animation: slideIn 0.3s ease;
            `;
            document.body.appendChild(notification);

            setTimeout(() => {
                notification.style.animation = 'slideOut 0.3s ease';
                setTimeout(() => notification.remove(), 300);
            }, 3000);
        }

        // Close modals on background click
        document.querySelectorAll('.modal-overlay').forEach(modal => {
            modal.addEventListener('click', (e) => {
                if (e.target === modal) {
                    modal.style.display = 'none';
                    currentEditingTask = null;
                    currentEditingEvent = null;
                }
            });
        });

        // Keyboard shortcuts
        document.addEventListener('keydown', (e) => {
            // Escape to close modals
            if (e.key === 'Escape') {
                document.querySelectorAll('.modal-overlay').forEach(modal => {
                    modal.style.display = 'none';
                });
                currentEditingTask = null;
                currentEditingEvent = null;
                // Close FAB menu
                document.getElementById('fab-menu').classList.add('hidden');
            }

            // Cmd/Ctrl + K to open task modal
            if ((e.metaKey || e.ctrlKey) && e.key === 'k') {
                e.preventDefault();
                openTaskModal();
            }

            // Cmd/Ctrl + E to open event modal
            if ((e.metaKey || e.ctrlKey) && e.key === 'e') {
                e.preventDefault();
                openEventModal();
            }
        });
    </script>
</body>
</html>
