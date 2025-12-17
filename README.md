<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <title>Taskify Elite ✨</title>

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
            display: flex;
            justify-content: space-between;
            align-items: center;
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
    </style>
</head>
<body>
    <!-- Header Bar -->
    <div class="header-bar">
        <h1 class="text-2xl font-bold gradient-text">Taskify Elite ✨</h1>
        <div style="display: flex; gap: 8px;">
            <button class="icon-btn" onclick="toggleTheme()" title="Toggle Theme">🌓</button>
            <button class="icon-btn" onclick="openSettingsModal()" title="Settings">⚙️</button>
        </div>
    </div>

    <!-- Hub View (Dashboard) -->
    <div id="hub-view" class="view-container active">
        <h2 class="text-3xl font-bold mb-6">Command Center</h2>

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

        <div class="card mb-6">
            <h3 class="text-xl font-bold mb-4">📌 Today's Focus</h3>
            <div id="today-tasks"></div>
        </div>

        <div class="card">
            <h3 class="text-xl font-bold mb-4">🎯 Quick Stats</h3>
            <div class="grid grid-cols-2 gap-4">
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

    <!-- Pulse View (Timeline) -->
    <div id="pulse-view" class="view-container">
        <h2 class="text-3xl font-bold mb-6">Pulse</h2>

        <div class="card mb-6">
            <div class="flex items-center gap-4 mb-4">
                <button class="btn btn-secondary" onclick="changePulseDate(-1)">← Previous</button>
                <input type="date" class="input" id="pulse-date" onchange="renderPulse()">
                <button class="btn btn-secondary" onclick="changePulseDate(1)">Next →</button>
            </div>
        </div>

        <div id="pulse-timeline"></div>
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
                <button class="btn btn-primary" style="padding: 16px 48px; font-size: 18px;" onclick="startTimer()">
                    ▶️ Start
                </button>
                <button class="btn btn-secondary" style="padding: 16px 48px; font-size: 18px;" onclick="pauseTimer()">
                    ⏸️ Pause
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

    <!-- Floating Action Button -->
    <button class="fab" onclick="openTaskModal()" title="Add New Task">+</button>

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
                        <input type="time" id="task-end-time">
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
                    <label class="form-label">Dependencies</label>
                    <input type="text" class="input" id="task-dependencies" placeholder="Dependent task IDs separated by commas">
                </div>

                <div class="form-group">
                    <label class="checkbox-group">
                        <input type="checkbox" id="task-recurring">
                        <span>Recurring Task</span>
                    </label>
                </div>

                <div class="form-group" id="recurring-options" style="display: none;">
                    <label class="form-label">Recurrence Pattern</label>
                    <select class="select" id="task-recurrence">
                        <option value="daily">Daily</option>
                        <option value="weekly">Weekly</option>
                        <option value="monthly">Monthly</option>
                    </select>
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
                <h3 class="text-lg font-bold mb-4">☁️ Server Sync</h3>
                <div class="form-group">
                    <label class="form-label">Server URL</label>
                    <input type="text" class="input" id="server-url" value="https://rtd-n-line-api.onrender.com" placeholder="Enter server URL">
                </div>
                <div class="form-group">
                    <label class="form-label">User ID</label>
                    <input type="text" class="input" id="user-id" placeholder="Enter your user ID">
                </div>
                <button class="btn btn-primary" style="width: 100%;" onclick="syncWithServer()">
                    🔄 Sync Now
                </button>
                <div id="sync-status" class="mt-4 text-sm text-secondary"></div>
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

            <div class="card">
                <h3 class="text-lg font-bold mb-2">About</h3>
                <p class="text-sm text-secondary">Taskify Elite v2.0</p>
                <p class="text-sm text-secondary">Modern task management for productive people</p>
            </div>
        </div>
    </div>

    <script>
        // Global Variables
        const API_BASE_URL = 'https://rtd-n-line-api.onrender.com';
        let tasks = [];
        let currentEditingTask = null;
        let timerInterval = null;
        let timerSeconds = 25 * 60;
        let timerRunning = false;
        let sessionsCompleted = 0;
        let currentFilter = 'all';

        // Initialize App
        document.addEventListener('DOMContentLoaded', function() {
            loadTasks();
            loadNotes();
            loadTheme();
            loadSettings();
            renderHub();
            renderBoard();
            renderPulse();
            initializeSortable();

            // Set today's date in pulse view
            document.getElementById('pulse-date').valueAsDate = new Date();

            // Load recurring task checkbox handler
            document.getElementById('task-recurring').addEventListener('change', function(e) {
                document.getElementById('recurring-options').style.display = e.target.checked ? 'block' : 'none';
            });
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
            const serverUrl = localStorage.getItem('taskify_server_url');
            const userId = localStorage.getItem('taskify_user_id');
            if (serverUrl) document.getElementById('server-url').value = serverUrl;
            if (userId) document.getElementById('user-id').value = userId;

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
            const total = tasks.length;
            const completed = tasks.filter(t => t.status === 'done').length;
            const active = tasks.filter(t => t.status === 'in-progress').length;
            const completionRate = total > 0 ? Math.round((completed / total) * 100) : 0;
            const highPriority = tasks.filter(t => t.priority === 'high' && t.status !== 'done').length;

            // Calculate overdue
            const today = new Date().toISOString().split('T')[0];
            const overdue = tasks.filter(t => t.dueDate && t.dueDate < today && t.status !== 'done').length;

            // Calculate this week's tasks
            const weekFromNow = new Date();
            weekFromNow.setDate(weekFromNow.getDate() + 7);
            const weekFromNowStr = weekFromNow.toISOString().split('T')[0];
            const thisWeek = tasks.filter(t => t.dueDate && t.dueDate <= weekFromNowStr && t.dueDate >= today).length;

            document.getElementById('completion-rate').textContent = `${completionRate}%`;
            document.getElementById('completed-count').textContent = completed;
            document.getElementById('active-count').textContent = active;
            document.getElementById('high-priority-count').textContent = highPriority;
            document.getElementById('overdue-count').textContent = overdue;
            document.getElementById('week-count').textContent = thisWeek;
            document.getElementById('total-count').textContent = total;

            // Render today's tasks
            const todayTasks = tasks.filter(t => {
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

            // Filter tasks
            let filteredTasks = tasks;
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

        function createTaskCard(task) {
            const card = document.createElement('div');
            card.className = 'task-card';
            card.setAttribute('data-id', task.id);
            card.onclick = () => editTask(task.id);

            let tagsHTML = '';
            if (task.tags && task.tags.length > 0) {
                tagsHTML = task.tags.map(tag => `<span class="tag" style="background: rgba(139, 92, 246, 0.2); color: var(--accent-secondary);">${tag}</span>`).join('');
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
                        onEnd: function(evt) {
                            const taskId = evt.item.getAttribute('data-id');
                            const newStatus = statusMap[evt.to.id];

                            const task = tasks.find(t => t.id === taskId);
                            if (task) {
                                task.status = newStatus;
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
                        }
                    });
                }
            });
        }

        // Pulse View (Timeline)
        function renderPulse() {
            const selectedDate = document.getElementById('pulse-date').value;
            const dateTasks = tasks.filter(t => t.dueDate === selectedDate);

            // Sort by start time
            dateTasks.sort((a, b) => {
                if (!a.startTime) return 1;
                if (!b.startTime) return -1;
                return a.startTime.localeCompare(b.startTime);
            });

            const container = document.getElementById('pulse-timeline');

            if (dateTasks.length === 0) {
                container.innerHTML = '<div class="empty-state"><div class="empty-state-icon">📅</div><div>No tasks scheduled for this day</div></div>';
                return;
            }

            container.innerHTML = dateTasks.map(task => `
                <div class="time-block" onclick="editTask('${task.id}')">
                    <div style="display: flex; justify-content: space-between; align-items: start; margin-bottom: 8px;">
                        <div>
                            <div style="font-weight: 700; font-size: 18px; margin-bottom: 4px;">${task.title}</div>
                            <div style="font-size: 14px; color: var(--text-secondary);">
                                ${task.startTime ? `⏰ ${task.startTime}` : ''}
                                ${task.startTime && task.endTime ? ` - ${task.endTime}` : ''}
                            </div>
                        </div>
                        <span class="tag status-${task.status}">${task.status.replace('-', ' ')}</span>
                    </div>
                    ${task.description ? `<div style="margin-top: 8px; color: var(--text-secondary);">${task.description}</div>` : ''}
                    <div style="display: flex; gap: 8px; margin-top: 8px; flex-wrap: wrap;">
                        <span class="tag priority-${task.priority}">${task.priority}</span>
                        ${task.category ? `<span class="tag" style="background: rgba(99, 102, 241, 0.2);">${task.category}</span>` : ''}
                        ${task.project ? `<span class="tag" style="background: rgba(139, 92, 246, 0.2);">📁 ${task.project}</span>` : ''}
                    </div>
                </div>
            `).join('');
        }

        function changePulseDate(days) {
            const dateInput = document.getElementById('pulse-date');
            const currentDate = new Date(dateInput.value);
            currentDate.setDate(currentDate.getDate() + days);
            dateInput.valueAsDate = currentDate;
            renderPulse();
        }

        // Focus Mode (Timer)
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
                    document.getElementById('task-dependencies').value = task.dependencies ? task.dependencies.join(', ') : '';
                    document.getElementById('task-recurring').checked = task.recurring || false;
                    document.getElementById('task-recurrence').value = task.recurrence || 'daily';

                    if (task.recurring) {
                        document.getElementById('recurring-options').style.display = 'block';
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
                dependencies: document.getElementById('task-dependencies').value.split(',').map(d => d.trim()).filter(d => d),
                recurring: document.getElementById('task-recurring').checked,
                recurrence: document.getElementById('task-recurrence').value,
                subtasks: getSubtasks(),
                createdAt: currentEditingTask ? tasks.find(t => t.id === currentEditingTask).createdAt : new Date().toISOString(),
                updatedAt: new Date().toISOString()
            };

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

            // Show success message
            showNotification(currentEditingTask ? 'Task updated!' : 'Task created!', 'success');
        }

        function deleteTask() {
            if (!currentEditingTask) return;

            if (confirm('Are you sure you want to delete this task?')) {
                tasks = tasks.filter(t => t.id !== currentEditingTask);
                saveTasks();
                closeTaskModal();
                showNotification('Task deleted!', 'success');
            }
        }

        function editTask(taskId) {
            openTaskModal(taskId);
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

            // Save settings
            localStorage.setItem('taskify_server_url', document.getElementById('server-url').value);
            localStorage.setItem('taskify_user_id', document.getElementById('user-id').value);
        }

        // Server Sync
        async function syncWithServer() {
            const serverUrl = document.getElementById('server-url').value;
            const userId = document.getElementById('user-id').value;
            const statusDiv = document.getElementById('sync-status');

            if (!serverUrl || !userId) {
                statusDiv.textContent = '❌ Please enter server URL and user ID';
                statusDiv.style.color = 'var(--accent-danger)';
                return;
            }

            try {
                statusDiv.textContent = '🔄 Syncing...';
                statusDiv.style.color = 'var(--text-secondary)';

                // Upload local tasks
                const response = await fetch(`${serverUrl}/sync`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({
                        userId: userId,
                        tasks: tasks
                    })
                });

                if (response.ok) {
                    const data = await response.json();
                    statusDiv.textContent = '✅ Sync successful!';
                    statusDiv.style.color = 'var(--accent-success)';
                    showNotification('Synced successfully!', 'success');
                } else {
                    throw new Error('Sync failed');
                }
            } catch (error) {
                statusDiv.textContent = '❌ Sync failed. Check your connection.';
                statusDiv.style.color = 'var(--accent-danger)';
                console.error('Sync error:', error);
            }
        }

        // Data Management
        function exportData() {
            const data = {
                tasks: tasks,
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
                    saveTasks();
                    showNotification('All data cleared!', 'success');
                    location.reload();
                }
            }
        }

        // Utility Functions
        function generateId() {
            return 'task_' + Date.now() + '_' + Math.random().toString(36).substr(2, 9);
        }

        function formatDate(dateString) {
            if (!dateString) return '';
            const date = new Date(dateString);
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
            }

            // Cmd/Ctrl + K to open task modal
            if ((e.metaKey || e.ctrlKey) && e.key === 'k') {
                e.preventDefault();
                openTaskModal();
            }
        });
    </script>
</body>
</html>
