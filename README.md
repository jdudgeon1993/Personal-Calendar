<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <title>Ultimate Planner Pro</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        :root {
            --bg: #f8f9fa;
            --card: #ffffff;
            --text: #1a1a1a;
            --text-dim: #6c757d;
            --border: #e9ecef;
            --accent: #4CAF50;
            --overdue: #dc3545;
            --urgent: #ff6b35;
            --today: #4CAF50;
            --tomorrow: #17a2b8;
            --status-not-started: #6c757d;
            --status-in-progress: #ffc107;
            --status-done: #28a745;
            --status-blocked: #dc3545;
            --shadow: rgba(0,0,0,0.08);
            --work: #2196F3;
            --personal: #9C27B0;
            --health: #4CAF50;
            --finance: #FF9800;
            --school: #673AB7;
            --priority-high: #dc3545;
            --priority-medium: #ffc107;
            --priority-low: #28a745;
        }

        /* Theme Variants */
        body.dark {
            --bg: #1a1a1a;
            --card: #2d2d2d;
            --text: #e9ecef;
            --text-dim: #adb5bd;
            --border: #404040;
            --shadow: rgba(0,0,0,0.3);
        }

        body.ocean {
            --bg: #e0f2f7;
            --card: #ffffff;
            --accent: #0288d1;
            --today: #0288d1;
        }

        body.forest {
            --bg: #e8f5e9;
            --card: #ffffff;
            --accent: #388e3c;
            --today: #388e3c;
        }

        body.sunset {
            --bg: #fff3e0;
            --card: #ffffff;
            --accent: #ff6f00;
            --today: #ff6f00;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: var(--bg);
            color: var(--text);
            font-size: 15px;
            line-height: 1.5;
            padding-bottom: 80px;
            transition: background 0.3s;
        }

        /* Header */
        .header {
            background: var(--card);
            padding: 16px;
            box-shadow: 0 2px 8px var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .urgent-banner {
            background: linear-gradient(135deg, var(--urgent), #ff8c61);
            color: white;
            padding: 12px;
            border-radius: 8px;
            margin-bottom: 12px;
            font-weight: 600;
            text-align: center;
            animation: pulse 2s infinite;
            cursor: pointer;
            display: none;
        }

        .urgent-banner.show {
            display: block;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }

        .header-top {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }

        .app-title {
            font-size: 1.3em;
            font-weight: 700;
            background: linear-gradient(135deg, var(--accent), #45a049);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .header-controls {
            display: flex;
            gap: 8px;
            align-items: center;
        }

        .icon-btn {
            background: transparent;
            border: none;
            font-size: 1.3em;
            cursor: pointer;
            padding: 6px;
            border-radius: 6px;
            transition: background 0.2s;
        }

        .icon-btn:hover {
            background: var(--border);
        }

        .header-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.9em;
            color: var(--text-dim);
            flex-wrap: wrap;
            gap: 8px;
        }

        .workload {
            font-weight: 600;
        }

        .workload.heavy {
            color: var(--overdue);
        }

        /* Quick Search Bar */
        .quick-search {
            background: var(--card);
            margin: 12px;
            padding: 12px;
            border-radius: 12px;
            box-shadow: 0 2px 8px var(--shadow);
        }

        .search-input {
            width: 100%;
            padding: 12px;
            border: 2px solid var(--border);
            border-radius: 8px;
            font-size: 1em;
            background: var(--bg);
            color: var(--text);
        }

        .search-input:focus {
            outline: none;
            border-color: var(--accent);
        }

        /* Quick Add */
        .quick-add {
            background: var(--card);
            margin: 0 12px 12px;
            padding: 12px;
            border-radius: 12px;
            box-shadow: 0 2px 8px var(--shadow);
        }

        .quick-add-input {
            width: 100%;
            padding: 14px;
            border: 2px solid var(--accent);
            border-radius: 8px;
            font-size: 1em;
            background: var(--bg);
            color: var(--text);
            margin-bottom: 8px;
        }

        .quick-add-hint {
            font-size: 0.85em;
            color: var(--text-dim);
            font-style: italic;
        }

        /* Filter Bar */
        .filter-bar {
            background: var(--card);
            margin: 0 12px 12px;
            padding: 12px;
            border-radius: 12px;
            box-shadow: 0 2px 8px var(--shadow);
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            align-items: center;
        }

        .filter-chip {
            padding: 6px 12px;
            border-radius: 16px;
            border: 2px solid var(--border);
            background: var(--bg);
            font-size: 0.85em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
            white-space: nowrap;
        }

        .filter-chip.active {
            background: var(--accent);
            color: white;
            border-color: var(--accent);
        }

        /* Sections */
        .section {
            margin: 16px 12px;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 8px 12px;
            margin-bottom: 8px;
            background: var(--card);
            border-radius: 8px;
            cursor: pointer;
            user-select: none;
        }

        .section-title {
            font-size: 0.95em;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .section-count {
            background: var(--text-dim);
            color: white;
            padding: 2px 8px;
            border-radius: 12px;
            font-size: 0.85em;
            font-weight: 600;
        }

        .section.overdue .section-title { color: var(--overdue); }
        .section.overdue .section-count { background: var(--overdue); }
        .section.today .section-title { color: var(--today); }
        .section.today .section-count { background: var(--today); }
        .section.tomorrow .section-title { color: var(--tomorrow); }
        .section.tomorrow .section-count { background: var(--tomorrow); }
        .section.completed .section-title { color: var(--status-done); }
        .section.completed .section-count { background: var(--status-done); }

        .section-content {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .section-content.collapsed {
            display: none;
        }

        .collapse-icon {
            transition: transform 0.2s;
        }

        .section-header.collapsed .collapse-icon {
            transform: rotate(-90deg);
        }

        /* Task Cards */
        .task-card {
            background: var(--card);
            border-radius: 10px;
            padding: 14px;
            box-shadow: 0 2px 6px var(--shadow);
            border-left: 4px solid var(--status-not-started);
            position: relative;
            transition: all 0.2s;
            cursor: grab;
        }

        .task-card:active {
            cursor: grabbing;
        }

        .task-card.dragging {
            opacity: 0.5;
            cursor: grabbing;
        }

        .task-card.priority-high {
            border-left-color: var(--priority-high);
        }

        .task-card.priority-medium {
            border-left-color: var(--priority-medium);
        }

        .task-card.priority-low {
            border-left-color: var(--priority-low);
        }

        .task-card.status-in-progress {
            border-left-color: var(--status-in-progress);
        }

        .task-card.status-done {
            border-left-color: var(--status-done);
            opacity: 0.7;
        }

        .task-card.urgent {
            animation: urgentGlow 2s infinite;
            box-shadow: 0 0 20px rgba(255, 107, 53, 0.3);
        }

        @keyframes urgentGlow {
            0%, 100% { box-shadow: 0 0 20px rgba(255, 107, 53, 0.3); }
            50% { box-shadow: 0 0 30px rgba(255, 107, 53, 0.6); }
        }

        .task-card.overdue:not(.status-done) {
            background: linear-gradient(to right, rgba(220, 53, 69, 0.05), var(--card));
        }

        .urgent-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background: var(--urgent);
            color: white;
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 0.75em;
            font-weight: 700;
            animation: pulse 1s infinite;
        }

        .task-main {
            display: flex;
            gap: 10px;
            margin-bottom: 10px;
        }

        .task-checkbox {
            width: 24px;
            height: 24px;
            border-radius: 50%;
            border: 2px solid var(--status-not-started);
            flex-shrink: 0;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            margin-top: 2px;
        }

        .task-card.status-in-progress .task-checkbox {
            border-color: var(--status-in-progress);
            background: var(--status-in-progress);
            color: white;
        }

        .task-card.status-done .task-checkbox {
            border-color: var(--status-done);
            background: var(--status-done);
            color: white;
        }

        .task-content {
            flex: 1;
            min-width: 0;
        }

        .task-title {
            font-weight: 600;
            font-size: 1.05em;
            margin-bottom: 6px;
            word-wrap: break-word;
        }

        .task-card.status-done .task-title {
            text-decoration: line-through;
            opacity: 0.6;
        }

        .task-meta {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            font-size: 0.85em;
            color: var(--text-dim);
            margin-bottom: 8px;
        }

        .meta-item {
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .category-badge {
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 0.9em;
            font-weight: 600;
            color: white;
        }

        .category-work { background: var(--work); }
        .category-personal { background: var(--personal); }
        .category-health { background: var(--health); }
        .category-finance { background: var(--finance); }
        .category-school { background: var(--school); }

        .tag-badge {
            padding: 2px 6px;
            border-radius: 10px;
            font-size: 0.8em;
            background: var(--border);
            color: var(--text);
        }

        .project-badge {
            padding: 2px 6px;
            border-radius: 10px;
            font-size: 0.8em;
            background: var(--accent);
            color: white;
        }

        .energy-badge {
            padding: 2px 6px;
            border-radius: 10px;
            font-size: 0.8em;
            font-weight: 600;
        }

        .energy-high { background: #ff5252; color: white; }
        .energy-medium { background: #ffc107; color: black; }
        .energy-low { background: #4caf50; color: white; }

        .progress-container {
            margin: 8px 0;
        }

        .progress-bar {
            height: 6px;
            background: var(--border);
            border-radius: 10px;
            overflow: hidden;
            margin-bottom: 4px;
        }

        .progress-fill {
            height: 100%;
            background: var(--accent);
            transition: width 0.3s;
        }

        .progress-text {
            font-size: 0.8em;
            color: var(--text-dim);
        }

        .task-actions {
            display: flex;
            gap: 6px;
            margin-top: 10px;
            flex-wrap: wrap;
        }

        .task-btn {
            flex: 1;
            min-width: fit-content;
            padding: 8px;
            border: 1px solid var(--border);
            background: var(--card);
            color: var(--text);
            border-radius: 6px;
            font-size: 0.85em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
        }

        .task-btn:hover {
            background: var(--border);
        }

        .task-btn.primary {
            background: var(--status-in-progress);
            color: white;
            border: none;
        }

        .task-btn.success {
            background: var(--status-done);
            color: white;
            border: none;
        }

        .task-btn.danger {
            background: var(--overdue);
            color: white;
            border: none;
        }

        /* Subtasks */
        .subtasks {
            margin-top: 12px;
            padding: 12px;
            background: var(--bg);
            border-radius: 8px;
            border: 1px solid var(--border);
        }

        .subtask {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 8px;
            font-size: 0.95em;
            border-bottom: 1px solid var(--border);
        }

        .subtask:last-child {
            border-bottom: none;
        }

        .subtask input[type="checkbox"] {
            width: 20px;
            height: 20px;
            cursor: pointer;
            flex-shrink: 0;
        }

        .subtask.completed {
            opacity: 0.5;
        }

        .subtask.completed .subtask-text {
            text-decoration: line-through;
        }

        /* Pomodoro Timer */
        .pomodoro-timer {
            background: var(--card);
            padding: 12px;
            border-radius: 8px;
            margin-top: 8px;
            border: 2px solid var(--accent);
            text-align: center;
        }

        .timer-display {
            font-size: 2em;
            font-weight: 700;
            color: var(--accent);
            margin: 10px 0;
        }

        .timer-controls {
            display: flex;
            gap: 8px;
            justify-content: center;
        }

        /* Stats Dashboard */
        .stats-dashboard {
            background: var(--card);
            margin: 12px;
            padding: 16px;
            border-radius: 12px;
            box-shadow: 0 2px 8px var(--shadow);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-bottom: 16px;
        }

        .stat-card {
            background: var(--bg);
            padding: 12px;
            border-radius: 8px;
            text-align: center;
        }

        .stat-value {
            font-size: 2em;
            font-weight: 700;
            color: var(--accent);
        }

        .stat-label {
            font-size: 0.85em;
            color: var(--text-dim);
            margin-top: 4px;
        }

        .chart-container {
            margin-top: 16px;
        }

        .chart-bar {
            display: flex;
            align-items: center;
            margin-bottom: 8px;
        }

        .chart-label {
            width: 80px;
            font-size: 0.85em;
            font-weight: 600;
        }

        .chart-fill-container {
            flex: 1;
            height: 24px;
            background: var(--border);
            border-radius: 12px;
            overflow: hidden;
            margin: 0 8px;
        }

        .chart-fill {
            height: 100%;
            background: var(--accent);
            transition: width 0.3s;
        }

        .chart-value {
            font-size: 0.85em;
            font-weight: 600;
            min-width: 30px;
        }

        /* Bottom Nav */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: var(--card);
            border-top: 1px solid var(--border);
            display: flex;
            padding: 8px;
            box-shadow: 0 -2px 8px var(--shadow);
            z-index: 100;
        }

        .nav-btn {
            flex: 1;
            padding: 10px;
            background: transparent;
            border: none;
            color: var(--text-dim);
            font-size: 0.85em;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 4px;
            transition: color 0.2s;
        }

        .nav-btn.active {
            color: var(--accent);
        }

        .nav-icon {
            font-size: 1.5em;
        }

        /* FAB */
        .fab {
            position: fixed;
            bottom: 80px;
            right: 16px;
            width: 56px;
            height: 56px;
            background: var(--accent);
            color: white;
            border: none;
            border-radius: 50%;
            font-size: 2em;
            box-shadow: 0 4px 12px rgba(76, 175, 80, 0.4);
            cursor: pointer;
            z-index: 99;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: transform 0.2s;
        }

        .fab:active {
            transform: scale(0.95);
        }

        /* Modal */
        .modal {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.5);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            padding: 20px;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: var(--card);
            border-radius: 12px;
            padding: 20px;
            max-width: 600px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-header {
            font-size: 1.2em;
            font-weight: 700;
            margin-bottom: 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .close-btn {
            background: transparent;
            border: none;
            font-size: 1.5em;
            cursor: pointer;
            color: var(--text-dim);
        }

        .form-group {
            margin-bottom: 14px;
        }

        .form-label {
            display: block;
            font-size: 0.9em;
            font-weight: 600;
            margin-bottom: 6px;
            color: var(--text-dim);
        }

        input[type="text"],
        input[type="date"],
        input[type="time"],
        input[type="number"],
        select,
        textarea {
            width: 100%;
            padding: 10px;
            border: 2px solid var(--border);
            border-radius: 8px;
            font-size: 1em;
            background: var(--bg);
            color: var(--text);
            font-family: inherit;
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--accent);
        }

        textarea {
            resize: vertical;
            min-height: 60px;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
        }

        .checkbox-group {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-top: 8px;
        }

        .btn-group {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }

        .btn {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 8px;
            font-size: 1em;
            font-weight: 600;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .btn:active {
            transform: scale(0.98);
        }

        .btn-primary {
            background: var(--accent);
            color: white;
        }

        .btn-secondary {
            background: var(--border);
            color: var(--text);
        }

        .tag-input-container {
            display: flex;
            flex-wrap: wrap;
            gap: 6px;
            padding: 8px;
            border: 2px solid var(--border);
            border-radius: 8px;
            background: var(--bg);
            min-height: 44px;
        }

        .tag-item {
            padding: 4px 8px;
            background: var(--accent);
            color: white;
            border-radius: 12px;
            font-size: 0.85em;
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .tag-remove {
            cursor: pointer;
            font-weight: bold;
        }

        .empty-state {
            text-align: center;
            padding: 40px 20px;
            color: var(--text-dim);
        }

        .empty-icon {
            font-size: 3em;
            margin-bottom: 10px;
            opacity: 0.3;
        }

        /* Keyboard Shortcuts Help */
        .shortcuts-help {
            background: var(--card);
            padding: 16px;
            border-radius: 8px;
            font-size: 0.9em;
        }

        .shortcut-item {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px solid var(--border);
        }

        .shortcut-item:last-child {
            border-bottom: none;
        }

        .shortcut-key {
            background: var(--bg);
            padding: 4px 8px;
            border-radius: 4px;
            font-family: monospace;
            font-weight: 600;
        }

        @media (max-width: 768px) {
            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .form-row {
                grid-template-columns: 1fr;
            }
        }

        /* Loading animation */
        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        .loading {
            display: inline-block;
            animation: spin 1s linear infinite;
        }

        /* Celebration animation */
        @keyframes celebrate {
            0% { transform: scale(1); }
            50% { transform: scale(1.2) rotate(10deg); }
            100% { transform: scale(1) rotate(0deg); }
        }

        .celebrating {
            animation: celebrate 0.5s ease-in-out;
        }

        /* Calendar View Styles */
        .calendar-day {
            background: var(--card);
            border-radius: 8px;
            padding: 8px;
            min-height: 120px;
            border: 1px solid var(--border);
            overflow-y: auto;
            max-height: 300px;
        }

        @media (max-width: 768px) {
            .calendar-day {
                min-height: 100px;
                max-height: 200px;
                font-size: 0.85em;
            }
            
            #calendarGrid {
                gap: 4px !important;
                padding: 8px !important;
            }
        }

        .calendar-day.today {
            border: 2px solid var(--accent);
            background: linear-gradient(to bottom, rgba(76, 175, 80, 0.1), var(--card));
        }

        .calendar-day-header {
            font-size: 0.75em;
            font-weight: 700;
            margin-bottom: 6px;
            text-align: center;
            padding-bottom: 4px;
            border-bottom: 1px solid var(--border);
            position: sticky;
            top: 0;
            background: var(--card);
            z-index: 1;
        }

        @media (max-width: 768px) {
            .calendar-day-header {
                font-size: 0.7em;
                padding-bottom: 2px;
            }
        }

        .calendar-day.today .calendar-day-header {
            color: var(--accent);
        }

        .calendar-task {
            font-size: 0.7em;
            padding: 4px 6px;
            background: var(--border);
            border-radius: 4px;
            margin-bottom: 4px;
            border-left: 2px solid var(--status-not-started);
            cursor: pointer;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
            transition: all 0.2s;
        }

        @media (max-width: 768px) {
            .calendar-task {
                font-size: 0.65em;
                padding: 3px 4px;
                margin-bottom: 3px;
            }
        }

        .calendar-task:hover {
            background: var(--text-dim);
            color: white;
            transform: translateX(2px);
        }

        .calendar-task.status-in-progress {
            border-left-color: var(--status-in-progress);
        }

        .calendar-task.status-done {
            border-left-color: var(--status-done);
            opacity: 0.5;
        }

        .calendar-task.priority-high {
            border-left-color: var(--priority-high);
            border-left-width: 3px;
        }

        .calendar-task-count {
            font-size: 0.75em;
            color: var(--text-dim);
            text-align: center;
            padding: 4px;
            font-weight: 600;
        }

        /* Board View Styles */
        .board-column {
            background: var(--card);
            border-radius: 12px;
            padding: 12px;
            min-height: 400px;
            box-shadow: 0 2px 8px var(--shadow);
        }

        .board-column-header {
            font-size: 0.9em;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding-bottom: 8px;
            border-bottom: 2px solid var(--border);
        }

        .board-column.not-started .board-column-header {
            color: var(--status-not-started);
            border-bottom-color: var(--status-not-started);
        }

        .board-column.in-progress .board-column-header {
            color: var(--status-in-progress);
            border-bottom-color: var(--status-in-progress);
        }

        .board-column.done .board-column-header {
            color: var(--status-done);
            border-bottom-color: var(--status-done);
        }

        .board-tasks {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .board-task-card {
            background: var(--bg);
            border-radius: 8px;
            padding: 12px;
            border-left: 3px solid var(--status-not-started);
            cursor: pointer;
            transition: all 0.2s;
            box-shadow: 0 2px 4px var(--shadow);
        }

        .board-task-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px var(--shadow);
        }

        .board-task-card.status-in-progress {
            border-left-color: var(--status-in-progress);
        }

        .board-task-card.status-done {
            border-left-color: var(--status-done);
            opacity: 0.7;
        }

        .board-task-card.priority-high {
            border-left-color: var(--priority-high);
            border-left-width: 4px;
        }

        .board-task-card.urgent {
            animation: urgentGlow 2s infinite;
        }

        .board-task-title {
            font-weight: 600;
            margin-bottom: 6px;
            font-size: 0.95em;
        }

        .board-task-meta {
            display: flex;
            flex-wrap: wrap;
            gap: 6px;
            font-size: 0.75em;
            color: var(--text-dim);
        }

        @media (max-width: 768px) {
            #boardContainer {
                grid-template-columns: 1fr !important;
            }
        }
    </style>
</head>
<body>
    <div class="header">
        <div class="urgent-banner" id="urgentBanner" onclick="scrollToUrgent()">
            ⚠️ <span id="urgentCount">0</span> tasks due soon!
        </div>
        
        <div class="header-top">
            <div class="app-title">✨ Ultimate Planner Pro</div>
            <div class="header-controls">
                <button class="icon-btn" id="syncBtn" title="Cloud Sync" onclick="openSyncModal()">☁️</button>
                <button class="icon-btn" id="statsBtn" title="Stats Dashboard">📊</button>
                <button class="icon-btn" id="settingsBtn" title="Settings">⚙️</button>
                <button class="icon-btn" id="themeBtn" title="Change Theme">🎨</button>
            </div>
        </div>
        <div class="header-meta">
            <div id="dateDisplay"></div>
            <div style="display: flex; align-items: center; gap: 12px;">
                <div id="weatherDisplay" style="font-size: 0.9em; color: var(--text-dim);">☀️ 72°F</div>
                <div class="workload" id="workloadDisplay"></div>
            </div>
        </div>
    </div>

    <div id="mainView">
        <!-- Search Bar -->
        <div class="quick-search">
            <input type="text" class="search-input" id="searchInput" placeholder="🔍 Search tasks...">
        </div>

        <!-- Quick Add with NLP -->
        <div class="quick-add">
            <input type="text" class="quick-add-input" id="quickAddInput" 
                placeholder="Quick add: 'Meeting tomorrow 2pm 30m' or just type a task...">
            <div class="quick-add-hint">💡 Try: "Study session Friday 3pm school high" or "Gym tonight 60m"</div>
        </div>

        <!-- Filter Bar -->
        <div class="filter-bar" id="filterBar">
            <span style="font-size: 0.85em; font-weight: 600;">Filter:</span>
            <div class="filter-chip active" data-filter="all">All</div>
            <div class="filter-chip" data-filter="priority-high">High Priority</div>
            <div class="filter-chip" data-filter="today">Today</div>
            <div class="filter-chip" data-filter="work">Work</div>
            <div class="filter-chip" data-filter="school">School</div>
        </div>

        <!-- Task Sections -->
        <div id="sectionsContainer"></div>
    </div>

    <!-- Calendar View -->
    <div id="calendarView" style="display: none;">
        <div style="padding: 12px; background: var(--card); margin: 12px; border-radius: 8px; box-shadow: 0 2px 8px var(--shadow);">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px;">
                <button class="task-btn" style="flex: 0; min-width: auto;" onclick="changeCalendarView(-1)">◀</button>
                <div style="display: flex; gap: 8px;">
                    <button class="task-btn" id="dayViewBtn" onclick="setCalendarMode('day')">Day</button>
                    <button class="task-btn" id="weekViewBtn" onclick="setCalendarMode('week')">Week</button>
                    <button class="task-btn" id="monthViewBtn" onclick="setCalendarMode('month')">Month</button>
                </div>
                <button class="task-btn" style="flex: 0; min-width: auto;" onclick="changeCalendarView(1)">▶</button>
            </div>
            <div id="calendarTitle" style="text-align: center; font-weight: 600; font-size: 1.1em; margin-bottom: 8px;"></div>
        </div>
        <div id="calendarGrid" style="display: grid; gap: 8px; padding: 12px;"></div>
    </div>

    <!-- Board View -->
    <div id="boardView" style="display: none;">
        <div style="padding: 12px;">
            <div id="boardContainer" style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px;"></div>
        </div>
    </div>

    <!-- Stats Dashboard View -->
    <div id="statsView" style="display: none;">
        <div class="stats-dashboard">
            <h2 style="margin-bottom: 16px;">📊 Your Productivity</h2>
            
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-value" id="totalTasksStat">0</div>
                    <div class="stat-label">Total Tasks</div>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="completedStat">0</div>
                    <div class="stat-label">Completed</div>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="completionRateStat">0%</div>
                    <div class="stat-label">Completion Rate</div>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="streakStat">0</div>
                    <div class="stat-label">Day Streak 🔥</div>
                </div>
            </div>

            <h3 style="margin: 16px 0 8px;">Tasks by Category</h3>
            <div class="chart-container" id="categoryChart"></div>

            <h3 style="margin: 16px 0 8px;">This Week's Progress</h3>
            <div class="chart-container" id="weekChart"></div>

            <button class="btn btn-secondary" onclick="exportData()" style="margin-top: 16px;">💾 Export Backup</button>
            <input type="file" id="importFile" accept=".json" style="display: none;" onchange="importData(event)">
            <button class="btn btn-secondary" onclick="document.getElementById('importFile').click()" style="margin-top: 8px;">📥 Import Backup</button>
        </div>
    </div>

    <button class="fab" id="fabBtn">+</button>

    <div class="bottom-nav">
        <button class="nav-btn active" data-view="main">
            <div class="nav-icon">📋</div>
            <div>Tasks</div>
        </button>
        <button class="nav-btn" data-view="calendar">
            <div class="nav-icon">📅</div>
            <div>Calendar</div>
        </button>
        <button class="nav-btn" data-view="board">
            <div class="nav-icon">📊</div>
            <div>Board</div>
        </button>
        <button class="nav-btn" data-view="stats">
            <div class="nav-icon">📈</div>
            <div>Stats</div>
        </button>
        <button class="nav-btn" data-view="settings">
            <div class="nav-icon">⚙️</div>
            <div>More</div>
        </button>
    </div>

    <!-- Task Modal -->
    <div class="modal" id="taskModal">
        <div class="modal-content">
            <div class="modal-header">
                <span id="modalTitle">Add Task</span>
                <button class="close-btn" onclick="closeModal('taskModal')">×</button>
            </div>
            <form id="taskForm">
                <div class="form-group">
                    <label class="form-label">Task Title *</label>
                    <input type="text" id="taskTitleInput" placeholder="What needs to be done?" required>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Category</label>
                        <select id="taskCategory">
                            <option value="work">💼 Work</option>
                            <option value="school">📚 School</option>
                            <option value="personal">🏠 Personal</option>
                            <option value="health">💪 Health</option>
                            <option value="finance">💰 Finance</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Priority</label>
                        <select id="taskPriority">
                            <option value="low">Low</option>
                            <option value="medium" selected>Medium</option>
                            <option value="high">High</option>
                        </select>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Due Date</label>
                        <input type="date" id="taskDueDate">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Due Time</label>
                        <input type="time" id="taskDueTime">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Time Block</label>
                        <select id="taskTimeBlock">
                            <option value="">Not set</option>
                            <option value="morning">🌅 Morning</option>
                            <option value="afternoon">☀️ Afternoon</option>
                            <option value="evening">🌙 Evening</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Start Time</label>
                        <input type="time" id="taskStartTime" onchange="calculateDuration()">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">End Time</label>
                        <input type="time" id="taskEndTime" onchange="calculateDuration()">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Duration (mins)</label>
                        <input type="number" id="taskDuration" placeholder="Auto-calculated" min="5" step="5" readonly style="background: var(--border);">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Energy Level</label>
                        <select id="taskEnergy">
                            <option value="">Not set</option>
                            <option value="high">⚡ High Energy</option>
                            <option value="medium">💪 Medium Energy</option>
                            <option value="low">🌱 Low Energy</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Project</label>
                        <input type="text" id="taskProject" placeholder="Optional project name">
                    </div>
                </div>

                <div class="form-group">
                    <label class="form-label">Depends On</label>
                    <select id="taskDependency">
                        <option value="">No dependency</option>
                    </select>
                </div>

                <div class="form-group">
                    <label class="form-label">Tags (press Enter or click + to add)</label>
                    <div class="tag-input-container" id="tagContainer" onclick="document.getElementById('tagInput').focus()">
                        <input type="text" id="tagInput" 
                            style="border: none; background: transparent; flex: 1; min-width: 100px; outline: none;"
                            placeholder="Add tags...">
                        <button type="button" class="task-btn" onclick="addTagFromInput()" style="flex: 0; padding: 4px 8px; font-size: 0.9em;">+ Add</button>
                    </div>
                </div>

                <div class="form-group">
                    <label class="checkbox-group">
                        <input type="checkbox" id="taskRecurring">
                        <span>Recurring Task</span>
                    </label>
                    <select id="recurringFreq" style="margin-top: 8px; display: none;">
                        <option value="daily">Daily</option>
                        <option value="weekly">Weekly</option>
                        <option value="weekdays">Weekdays (Mon-Fri)</option>
                    </select>
                </div>

                <div class="form-group">
                    <label class="form-label">Notes</label>
                    <textarea id="taskNotes" placeholder="Additional details..."></textarea>
                </div>

                <div class="form-group">
                    <label class="form-label">Subtasks</label>
                    <div id="subtasksContainer"></div>
                    <button type="button" class="btn btn-secondary" id="addSubtaskBtn" style="margin-top: 8px;">+ Add Subtask</button>
                </div>

                <div class="btn-group">
                    <button type="button" class="btn btn-secondary" onclick="closeModal('taskModal')">Cancel</button>
                    <button type="submit" class="btn btn-primary">Save Task</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Settings Modal -->
    <div class="modal" id="settingsModal">
        <div class="modal-content">
            <div class="modal-header">
                <span>⚙️ Settings</span>
                <button class="close-btn" onclick="closeModal('settingsModal')">×</button>
            </div>
            
            <div class="form-group">
                <label class="form-label">Theme</label>
                <select id="themeSelect">
                    <option value="light">☀️ Light</option>
                    <option value="dark">🌙 Dark</option>
                    <option value="ocean">🌊 Ocean</option>
                    <option value="forest">🌲 Forest</option>
                    <option value="sunset">🌅 Sunset</option>
                </select>
            </div>

            <div class="form-group">
                <label class="form-label">Week Starts On</label>
                <select id="weekStartSelect">
                    <option value="0">Sunday</option>
                    <option value="1">Monday</option>
                </select>
            </div>

            <div class="form-group">
                <label class="form-label">Default Task Duration (minutes)</label>
                <input type="number" id="defaultDuration" value="30" min="5" step="5">
            </div>

            <div class="form-group">
                <label class="form-label">Urgent Task Alert (minutes before)</label>
                <input type="number" id="urgentThreshold" value="30" min="5" step="5">
            </div>

            <div class="form-group">
                <label class="checkbox-group">
                    <input type="checkbox" id="soundAlerts">
                    <span>Sound Alerts for Urgent Tasks</span>
                </label>
            </div>

            <h3 style="margin: 20px 0 12px;">⌨️ Keyboard Shortcuts</h3>
            <div class="shortcuts-help">
                <div class="shortcut-item">
                    <span>New Task</span>
                    <span class="shortcut-key">N</span>
                </div>
                <div class="shortcut-item">
                    <span>Search</span>
                    <span class="shortcut-key">/</span>
                </div>
                <div class="shortcut-item">
                    <span>Toggle Stats</span>
                    <span class="shortcut-key">S</span>
                </div>
                <div class="shortcut-item">
                    <span>Settings</span>
                    <span class="shortcut-key">?</span>
                </div>
            </div>

            <button class="btn btn-primary" onclick="saveSettings()" style="margin-top: 16px;">Save Settings</button>
        </div>
    </div>

    <!-- Sync Modal -->
    <div class="modal" id="syncModal">
        <div class="modal-content">
            <div class="modal-header">
                <span>☁️ Cloud Sync</span>
                <button class="close-btn" onclick="closeModal('syncModal')">×</button>
            </div>
            
            <div id="syncStatusView">
                <!-- Not logged in view -->
                <div id="notLoggedInView">
                    <p style="text-align: center; color: var(--text-dim); margin-bottom: 20px;">
                        Sync your tasks across all devices!<br>
                        Get a simple token to access your data anywhere.
                    </p>
                    
                    <button class="btn btn-primary" onclick="registerNewToken()" style="width: 100%; margin-bottom: 10px;">
                        🎟️ Get New Sync Token
                    </button>
                    
                    <div style="text-align: center; margin: 20px 0; color: var(--text-dim);">
                        — OR —
                    </div>
                    
                    <div class="form-group">
                        <label class="form-label">Enter Existing Token</label>
                        <input type="text" id="tokenInput" placeholder="PLAN-ABC123" style="text-transform: uppercase;">
                    </div>
                    <button class="btn btn-secondary" onclick="loginWithToken()" style="width: 100%;">
                        🔐 Login with Token
                    </button>
                </div>

                <!-- Logged in view -->
                <div id="loggedInView" style="display: none;">
                    <div style="background: var(--bg); padding: 16px; border-radius: 8px; margin-bottom: 16px;">
                        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px;">
                            <span style="font-weight: 600;">Your Token:</span>
                            <button class="task-btn" onclick="copyToken()">📋 Copy</button>
                        </div>
                        <div style="font-family: monospace; font-size: 1.2em; padding: 12px; background: var(--card); border-radius: 6px; text-align: center; font-weight: 700; letter-spacing: 2px;" id="displayToken"></div>
                        <p style="font-size: 0.85em; color: var(--text-dim); margin-top: 8px; text-align: center;">
                            ⚠️ Save this somewhere safe! You'll need it to login on other devices.
                        </p>
                    </div>

                    <div style="background: var(--bg); padding: 16px; border-radius: 8px; margin-bottom: 16px;">
                        <h4 style="margin-bottom: 12px;">📊 Sync Status</h4>
                        <div style="display: flex; justify-content: space-between; padding: 8px 0; border-bottom: 1px solid var(--border);">
                            <span>Tasks Synced:</span>
                            <span id="syncedTaskCount">-</span>
                        </div>
                        <div style="display: flex; justify-content: space-between; padding: 8px 0; border-bottom: 1px solid var(--border);">
                            <span>Last Sync:</span>
                            <span id="lastSyncDisplay">Never</span>
                        </div>
                        <div style="display: flex; justify-content: space-between; padding: 8px 0;">
                            <span>Status:</span>
                            <span id="syncStatusText">✅ Synced</span>
                        </div>
                    </div>

                    <button class="btn btn-primary" onclick="manualSync()" style="width: 100%; margin-bottom: 10px;" id="syncNowBtn">
                        🔄 Sync Now
                    </button>
                    
                    <button class="btn btn-secondary" onclick="logout()" style="width: 100%;">
                        🚪 Logout
                    </button>
                </div>

                <!-- Loading view -->
                <div id="syncLoadingView" style="display: none; text-align: center; padding: 40px;">
                    <div style="font-size: 3em; margin-bottom: 16px;" class="loading">⏳</div>
                    <p id="syncLoadingText">Processing...</p>
                </div>
            </div>
        </div>
    </div>

    <script>
        // ==================== CONFIGURATION ====================
        // Update this with your Render server URL!
        const API_BASE_URL = 'https://rtd-n-line-api.onrender.com'; // ← YOUR ACTUAL URL!
        
        // ==================== STATE ====================
        let tasks = [];
        let templates = [];
        let habits = [];
        let currentView = 'main';
        let editingTaskId = null;
        let currentFilter = 'all';
        let searchQuery = '';
        let calendarMode = 'week'; // 'day', 'week', 'month'
        let calendarOffset = 0; // days, weeks or months to offset from current
        let userToken = null; // Sync token
        let isSyncing = false;
        let lastSyncTime = null;
        let settings = {
            theme: 'light',
            weekStart: 0,
            defaultDuration: 30,
            urgentThreshold: 30,
            soundAlerts: false
        };
        let stats = {
            streak: 0,
            lastCompletionDate: null,
            weeklyData: {}
        };

        const icons = {
            work: '💼',
            personal: '🏠',
            health: '💪',
            finance: '💰',
            school: '📚'
        };

        const statusIcons = {
            'not-started': '⚪',
            'in-progress': '🟡',
            'done': '✅'
        };

        // ==================== CLOUD SYNC FUNCTIONS ====================
        
        async function registerNewToken() {
            showSyncLoading('Getting your token...');
            
            try {
                const response = await fetch(`${API_BASE_URL}/api/planner/register`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' }
                });
                
                const data = await response.json();
                
                if (data.success) {
                    userToken = data.token;
                    localStorage.setItem('plannerToken', userToken);
                    
                    // Upload current data to server
                    await syncToServer();
                    
                    showLoggedInView();
                    alert(`✅ Your sync token: ${userToken}\n\n⚠️ SAVE THIS TOKEN!\nYou'll need it to access your data on other devices.`);
                } else {
                    throw new Error(data.error || 'Registration failed');
                }
            } catch (error) {
                console.error('Register error:', error);
                hideSyncLoading();
                alert('❌ Failed to register: ' + error.message);
            }
        }

        async function loginWithToken() {
            const input = document.getElementById('tokenInput');
            const token = input.value.trim().toUpperCase();
            
            if (!token) {
                alert('Please enter a token');
                return;
            }
            
            showSyncLoading('Logging in...');
            
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
                    
                    // Load data from server
                    await syncFromServer();
                    
                    showLoggedInView();
                    alert('✅ Logged in successfully!');
                } else {
                    throw new Error(data.error || 'Invalid token');
                }
            } catch (error) {
                console.error('Login error:', error);
                hideSyncLoading();
                alert('❌ Login failed: ' + error.message);
            }
        }

        async function syncToServer() {
            if (!userToken) return;
            
            isSyncing = true;
            updateSyncButton();
            
            try {
                // Save tasks
                const tasksResponse = await fetch(`${API_BASE_URL}/api/planner/tasks/${userToken}`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ tasks })
                });
                
                if (!tasksResponse.ok) throw new Error('Failed to sync tasks');
                
                // Save settings
                await fetch(`${API_BASE_URL}/api/planner/settings/${userToken}`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ settings })
                });
                
                // Save stats
                await fetch(`${API_BASE_URL}/api/planner/stats/${userToken}`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ stats })
                });
                
                lastSyncTime = new Date();
                updateSyncStatus();
                console.log('✅ Synced to server');
                
            } catch (error) {
                console.error('Sync to server error:', error);
            } finally {
                isSyncing = false;
                updateSyncButton();
            }
        }

        async function syncFromServer() {
            if (!userToken) return;
            
            isSyncing = true;
            updateSyncButton();
            
            try {
                // Load tasks
                const tasksResponse = await fetch(`${API_BASE_URL}/api/planner/tasks/${userToken}`);
                const tasksData = await tasksResponse.json();
                
                if (tasksData.success && tasksData.tasks.length > 0) {
                    tasks = tasksData.tasks;
                }
                
                // Load settings
                const settingsResponse = await fetch(`${API_BASE_URL}/api/planner/settings/${userToken}`);
                const settingsData = await settingsResponse.json();
                
                if (settingsData.success && settingsData.settings) {
                    settings = { ...settings, ...settingsData.settings };
                    applyTheme(settings.theme);
                }
                
                // Load stats
                const statsResponse = await fetch(`${API_BASE_URL}/api/planner/stats/${userToken}`);
                const statsData = await statsResponse.json();
                
                if (statsData.success && statsData.stats) {
                    stats = { ...stats, ...statsData.stats };
                }
                
                saveData(); // Save to localStorage too
                lastSyncTime = new Date();
                updateSyncStatus();
                renderAll();
                console.log('✅ Synced from server');
                
            } catch (error) {
                console.error('Sync from server error:', error);
            } finally {
                isSyncing = false;
                updateSyncButton();
            }
        }

        async function manualSync() {
            if (isSyncing) return;
            
            const btn = document.getElementById('syncNowBtn');
            const originalText = btn.textContent;
            btn.textContent = '⏳ Syncing...';
            btn.disabled = true;
            
            await syncToServer();
            
            btn.textContent = originalText;
            btn.disabled = false;
            
            alert('✅ Sync complete!');
        }

        function logout() {
            if (confirm('Logout and stop syncing? Your data will remain on this device.')) {
                userToken = null;
                localStorage.removeItem('plannerToken');
                lastSyncTime = null;
                showNotLoggedInView();
                updateSyncButton();
                alert('👋 Logged out successfully');
            }
        }

        function copyToken() {
            if (navigator.clipboard) {
                navigator.clipboard.writeText(userToken);
                alert('✅ Token copied to clipboard!');
            } else {
                // Fallback
                const input = document.createElement('input');
                input.value = userToken;
                document.body.appendChild(input);
                input.select();
                document.execCommand('copy');
                document.body.removeChild(input);
                alert('✅ Token copied!');
            }
        }

        function openSyncModal() {
            if (userToken) {
                showLoggedInView();
            } else {
                showNotLoggedInView();
            }
            openModal('syncModal');
        }

        function showSyncLoading(text) {
            document.getElementById('notLoggedInView').style.display = 'none';
            document.getElementById('loggedInView').style.display = 'none';
            document.getElementById('syncLoadingView').style.display = 'block';
            document.getElementById('syncLoadingText').textContent = text;
        }

        function hideSyncLoading() {
            document.getElementById('syncLoadingView').style.display = 'none';
        }

        function showNotLoggedInView() {
            hideSyncLoading();
            document.getElementById('notLoggedInView').style.display = 'block';
            document.getElementById('loggedInView').style.display = 'none';
        }

        function showLoggedInView() {
            hideSyncLoading();
            document.getElementById('notLoggedInView').style.display = 'none';
            document.getElementById('loggedInView').style.display = 'block';
            document.getElementById('displayToken').textContent = userToken;
            updateSyncStatus();
        }

        function updateSyncStatus() {
            if (!userToken) return;
            
            document.getElementById('syncedTaskCount').textContent = tasks.length;
            
            if (lastSyncTime) {
                const now = new Date();
                const diff = now - lastSyncTime;
                const minutes = Math.floor(diff / 60000);
                
                if (minutes < 1) {
                    document.getElementById('lastSyncDisplay').textContent = 'Just now';
                } else if (minutes < 60) {
                    document.getElementById('lastSyncDisplay').textContent = `${minutes}m ago`;
                } else {
                    const hours = Math.floor(minutes / 60);
                    document.getElementById('lastSyncDisplay').textContent = `${hours}h ago`;
                }
            }
            
            document.getElementById('syncStatusText').textContent = isSyncing ? '⏳ Syncing...' : '✅ Synced';
        }

        function updateSyncButton() {
            const btn = document.getElementById('syncBtn');
            if (userToken) {
                btn.textContent = isSyncing ? '⏳' : '☁️';
                btn.style.color = 'var(--accent)';
            } else {
                btn.textContent = '☁️';
                btn.style.color = 'var(--text-dim)';
            }
        }

        // Auto-sync on changes (debounced)
        let syncTimeout;
        function autoSync() {
            if (!userToken) return;
            
            clearTimeout(syncTimeout);
            syncTimeout = setTimeout(() => {
                syncToServer();
            }, 2000); // Sync 2 seconds after last change
        }

        // ==================== INITIALIZATION ====================
        function init() {
            loadData();
            setupEventListeners();
            updateDateTime();
            checkUrgentTasks();
            renderAll();
            setInterval(updateDateTime, 1000);
            setInterval(checkUrgentTasks, 60000); // Check every minute
            setupDragAndDrop();
        }

        function loadData() {
            const saved = localStorage.getItem('ultimatePlannerTasks');
            const savedSettings = localStorage.getItem('ultimatePlannerSettings');
            const savedStats = localStorage.getItem('ultimatePlannerStats');
            const savedTemplates = localStorage.getItem('ultimatePlannerTemplates');
            const savedToken = localStorage.getItem('plannerToken');
            
            if (saved) tasks = JSON.parse(saved);
            if (savedSettings) settings = { ...settings, ...JSON.parse(savedSettings) };
            if (savedStats) stats = { ...stats, ...JSON.parse(savedStats) };
            if (savedTemplates) templates = JSON.parse(savedTemplates);
            if (savedToken) {
                userToken = savedToken;
                // Sync from server on startup
                syncFromServer();
            }
            
            applyTheme(settings.theme);
            generateRecurringTasks();
            updateStreak();
            updateSyncButton();
        }

        function saveData() {
            localStorage.setItem('ultimatePlannerTasks', JSON.stringify(tasks));
            localStorage.setItem('ultimatePlannerSettings', JSON.stringify(settings));
            localStorage.setItem('ultimatePlannerStats', JSON.stringify(stats));
            localStorage.setItem('ultimatePlannerTemplates', JSON.stringify(templates));
            
            // Auto-sync if logged in
            autoSync();
        }

        // ==================== DATE/TIME UTILITIES ====================
        function updateDateTime() {
            const now = new Date();
            const dateOptions = { weekday: 'long', month: 'short', day: 'numeric' };
            const timeOptions = { hour: 'numeric', minute: '2-digit', hour12: true };
            const dateStr = now.toLocaleDateString('en-US', dateOptions);
            const timeStr = now.toLocaleTimeString('en-US', timeOptions);
            
            document.getElementById('dateDisplay').innerHTML = `
                <div style="display: flex; flex-direction: column; gap: 2px;">
                    <div style="font-weight: 600;">${dateStr}</div>
                    <div style="font-size: 0.9em; color: var(--text-dim);">${timeStr}</div>
                </div>
            `;
            updateWorkloadDisplay();
        }

        function parseLocalDate(dateString) {
            if (!dateString) return null;
            const [year, month, day] = dateString.split('-').map(Number);
            return new Date(year, month - 1, day);
        }

        function formatTime12Hour(time24) {
            if (!time24) return '';
            const [hours, minutes] = time24.split(':');
            const hour = parseInt(hours);
            const ampm = hour >= 12 ? 'PM' : 'AM';
            const hour12 = hour % 12 || 12;
            return `${hour12}:${minutes} ${ampm}`;
        }

        function isOverdue(task) {
            if (!task.dueDate || task.status === 'done') return false;
            const now = new Date();
            const due = parseLocalDate(task.dueDate);
            if (!due) return false;
            
            if (task.dueTime) {
                const [hours, minutes] = task.dueTime.split(':');
                due.setHours(parseInt(hours), parseInt(minutes));
            } else {
                due.setHours(23, 59);
            }
            return due < now;
        }

        function isUrgent(task) {
            if (!task.dueDate || task.status === 'done' || !task.dueTime) return false;
            const now = new Date();
            const due = parseLocalDate(task.dueDate);
            if (!due) return false;
            
            const [hours, minutes] = task.dueTime.split(':');
            due.setHours(parseInt(hours), parseInt(minutes));
            
            const diffMinutes = (due - now) / (1000 * 60);
            return diffMinutes > 0 && diffMinutes <= settings.urgentThreshold;
        }

        function getTaskSection(task) {
            if (isOverdue(task)) return 'overdue';
            if (!task.dueDate) return 'later';
            
            const now = new Date();
            const due = parseLocalDate(task.dueDate);
            if (!due) return 'later';
            
            const today = new Date(now.getFullYear(), now.getMonth(), now.getDate());
            const dueDay = new Date(due.getFullYear(), due.getMonth(), due.getDate());
            
            const diffTime = dueDay - today;
            const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
            
            if (diffDays === 0) return 'today';
            if (diffDays === 1) return 'tomorrow';
            if (diffDays <= 7) return 'week';
            return 'later';
        }

        // ==================== URGENT TASK CHECKING ====================
        function checkUrgentTasks() {
            const urgentTasks = tasks.filter(t => isUrgent(t));
            const banner = document.getElementById('urgentBanner');
            
            if (urgentTasks.length > 0) {
                banner.classList.add('show');
                document.getElementById('urgentCount').textContent = urgentTasks.length;
                
                if (settings.soundAlerts) {
                    // Optional: play sound (browser dependent)
                    // new Audio('data:audio/wav;base64,...').play();
                }
            } else {
                banner.classList.remove('show');
            }
        }

        function scrollToUrgent() {
            const urgentTask = document.querySelector('.task-card.urgent');
            if (urgentTask) {
                urgentTask.scrollIntoView({ behavior: 'smooth', block: 'center' });
            }
        }

        // ==================== RECURRING TASKS ====================
        function generateRecurringTasks() {
            const today = new Date().toISOString().split('T')[0];
            const recurringTemplates = tasks.filter(t => t.recurring);
            
            recurringTemplates.forEach(template => {
                const shouldGenerate = shouldGenerateRecurringTask(template, today);
                if (shouldGenerate) {
                    const newTask = { ...template };
                    newTask.id = Date.now() + Math.random();
                    newTask.dueDate = today;
                    newTask.status = 'not-started';
                    newTask.generatedFrom = template.id;
                    delete newTask.recurring;
                    tasks.push(newTask);
                }
            });
            
            saveData();
        }

        function shouldGenerateRecurringTask(template, today) {
            // Check if already generated today
            const alreadyExists = tasks.some(t => 
                t.generatedFrom === template.id && t.dueDate === today
            );
            if (alreadyExists) return false;
            
            const dayOfWeek = new Date(today).getDay();
            
            if (template.recurringFreq === 'daily') return true;
            if (template.recurringFreq === 'weekdays' && dayOfWeek >= 1 && dayOfWeek <= 5) return true;
            if (template.recurringFreq === 'weekly' && dayOfWeek === 0) return true;
            
            return false;
        }

        // ==================== WORKLOAD TRACKING ====================
        function updateWorkloadDisplay() {
            const todayTasks = tasks.filter(t => {
                const section = getTaskSection(t);
                return section === 'today' && t.status !== 'done';
            });
            
            const totalMinutes = todayTasks.reduce((sum, t) => sum + (parseInt(t.duration) || 0), 0);
            const hours = Math.floor(totalMinutes / 60);
            const mins = totalMinutes % 60;
            
            const display = document.getElementById('workloadDisplay');
            if (totalMinutes === 0) {
                display.textContent = 'No tasks today';
                display.className = 'workload';
            } else {
                const text = hours > 0 ? `${hours}h ${mins}m today` : `${mins}m today`;
                display.textContent = text;
                display.className = totalMinutes > 240 ? 'workload heavy' : 'workload';
            }
        }

        // ==================== STREAK TRACKING ====================
        function updateStreak() {
            const today = new Date().toDateString();
            const lastDate = stats.lastCompletionDate;
            
            if (!lastDate) {
                stats.streak = 0;
                return;
            }
            
            const yesterday = new Date();
            yesterday.setDate(yesterday.getDate() - 1);
            
            if (lastDate === today) {
                // Continue current streak
            } else if (lastDate === yesterday.toDateString()) {
                // Continues from yesterday
            } else {
                stats.streak = 0;
            }
            
            saveData();
        }

        function recordCompletion() {
            const today = new Date().toDateString();
            if (stats.lastCompletionDate !== today) {
                stats.streak++;
                stats.lastCompletionDate = today;
                saveData();
            }
        }

        // ==================== NATURAL LANGUAGE PARSING ====================
        function parseNaturalLanguage(input) {
            const task = {
                title: input,
                category: 'personal',
                priority: 'medium',
                dueDate: '',
                dueTime: '',
                timeBlock: '',
                duration: ''
            };
            
            // Remove and parse duration (30m, 60m, 2h)
            const durationMatch = input.match(/\b(\d+)(m|h)\b/i);
            if (durationMatch) {
                const value = parseInt(durationMatch[1]);
                task.duration = durationMatch[2].toLowerCase() === 'h' ? value * 60 : value;
                input = input.replace(durationMatch[0], '').trim();
            }
            
            // Parse date keywords
            const today = new Date();
            const tomorrow = new Date(today);
            tomorrow.setDate(today.getDate() + 1);
            
            if (/\btoday\b/i.test(input)) {
                task.dueDate = today.toISOString().split('T')[0];
                input = input.replace(/\btoday\b/i, '').trim();
            } else if (/\btomorrow\b/i.test(input)) {
                task.dueDate = tomorrow.toISOString().split('T')[0];
                input = input.replace(/\btomorrow\b/i, '').trim();
            } else {
                // Check for day names
                const days = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday'];
                for (let i = 0; i < days.length; i++) {
                    const regex = new RegExp(`\\b${days[i]}\\b`, 'i');
                    if (regex.test(input)) {
                        const targetDay = i;
                        const currentDay = today.getDay();
                        const daysAhead = (targetDay - currentDay + 7) % 7 || 7;
                        const targetDate = new Date(today);
                        targetDate.setDate(today.getDate() + daysAhead);
                        task.dueDate = targetDate.toISOString().split('T')[0];
                        input = input.replace(regex, '').trim();
                        break;
                    }
                }
            }
            
            // Parse time (2pm, 14:00, 3:30pm)
            const timeMatch = input.match(/\b(\d{1,2})(?::(\d{2}))?\s?(am|pm)?\b/i);
            if (timeMatch) {
                let hours = parseInt(timeMatch[1]);
                const minutes = timeMatch[2] || '00';
                const meridiem = timeMatch[3]?.toLowerCase();
                
                if (meridiem === 'pm' && hours < 12) hours += 12;
                if (meridiem === 'am' && hours === 12) hours = 0;
                if (!meridiem && hours < 8) hours += 12; // Assume PM for small numbers
                
                task.dueTime = `${String(hours).padStart(2, '0')}:${minutes}`;
                input = input.replace(timeMatch[0], '').trim();
            }
            
            // Parse category keywords
            const categories = ['work', 'school', 'personal', 'health', 'finance'];
            for (const cat of categories) {
                if (new RegExp(`\\b${cat}\\b`, 'i').test(input)) {
                    task.category = cat;
                    input = input.replace(new RegExp(`\\b${cat}\\b`, 'i'), '').trim();
                    break;
                }
            }
            
            // Parse priority
            if (/\bhigh\b/i.test(input)) {
                task.priority = 'high';
                input = input.replace(/\bhigh\b/i, '').trim();
            } else if (/\blow\b/i.test(input)) {
                task.priority = 'low';
                input = input.replace(/\blow\b/i, '').trim();
            }
            
            // Parse time blocks
            if (/\bmorning\b/i.test(input)) {
                task.timeBlock = 'morning';
                input = input.replace(/\bmorning\b/i, '').trim();
            } else if (/\bafternoon\b/i.test(input)) {
                task.timeBlock = 'afternoon';
                input = input.replace(/\bafternoon\b/i, '').trim();
            } else if (/\bevening|night\b/i.test(input)) {
                task.timeBlock = 'evening';
                input = input.replace(/\bevening|night\b/i, '').trim();
            }
            
            // Clean up title
            task.title = input.replace(/\s+/g, ' ').trim();
            if (!task.title) task.title = 'New Task';
            
            return task;
        }

        // ==================== RENDERING ====================
        function renderAll() {
            if (currentView === 'main') {
                renderListView();
            } else if (currentView === 'calendar') {
                renderCalendarView();
            } else if (currentView === 'board') {
                renderBoardView();
            } else if (currentView === 'stats') {
                renderStatsView();
            }
            checkUrgentTasks();
        }

        function renderListView() {
            const sections = {
                overdue: { title: '🔴 OVERDUE', tasks: [], class: 'overdue' },
                today: { title: '🎯 TODAY', tasks: [], class: 'today' },
                tomorrow: { title: '📅 TOMORROW', tasks: [], class: 'tomorrow' },
                week: { title: '📆 THIS WEEK', tasks: [], class: 'week' },
                later: { title: '📋 LATER', tasks: [], class: 'later' },
                completed: { title: '✅ COMPLETED', tasks: [], class: 'completed' }
            };

            // Filter tasks
            let filteredTasks = filterTasks(tasks);
            
            // Separate completed from active
            const activeTasks = filteredTasks.filter(t => t.status !== 'done');
            const completedTasks = filteredTasks.filter(t => t.status === 'done');

            // Sort active tasks into sections
            activeTasks.forEach(task => {
                const section = getTaskSection(task);
                sections[section].tasks.push(task);
            });

            // Sort by priority within each section
            Object.values(sections).forEach(section => {
                section.tasks.sort((a, b) => {
                    const priorityOrder = { high: 0, medium: 1, low: 2 };
                    return priorityOrder[a.priority] - priorityOrder[b.priority];
                });
            });

            sections.completed.tasks = completedTasks;

            const container = document.getElementById('sectionsContainer');
            container.innerHTML = '';

            // Render active sections
            ['overdue', 'today', 'tomorrow', 'week', 'later'].forEach(key => {
                const section = sections[key];
                if (section.tasks.length === 0 && key !== 'today') return;

                const sectionEl = createSectionElement(section, key);
                container.appendChild(sectionEl);
            });

            // Render completed section
            if (completedTasks.length > 0) {
                const section = sections.completed;
                const sectionEl = createSectionElement(section, 'completed', true);
                container.appendChild(sectionEl);
            }
        }

        function createSectionElement(section, key, collapsed = false) {
            const sectionEl = document.createElement('div');
            sectionEl.className = `section ${section.class}`;
            sectionEl.dataset.section = key;
            
            const header = document.createElement('div');
            header.className = `section-header ${collapsed ? 'collapsed' : ''}`;
            header.innerHTML = `
                <div class="section-title">
                    <span>${section.title}</span>
                    <span class="section-count">${section.tasks.length}</span>
                </div>
                <div class="collapse-icon">▼</div>
            `;
            header.onclick = () => toggleSection(sectionEl);

            const content = document.createElement('div');
            content.className = `section-content ${collapsed ? 'collapsed' : ''}`;

            if (section.tasks.length === 0) {
                content.innerHTML = '<div class="empty-state"><div class="empty-icon">✨</div><div>No tasks yet</div></div>';
            } else {
                section.tasks.forEach(task => {
                    content.appendChild(createTaskCard(task));
                });
            }

            // Add clear button for completed section
            if (key === 'completed' && section.tasks.length > 0) {
                const clearBtn = document.createElement('button');
                clearBtn.className = 'btn btn-danger';
                clearBtn.textContent = '🗑️ Clear All Completed';
                clearBtn.style.margin = '10px 0';
                clearBtn.onclick = (e) => {
                    e.stopPropagation();
                    if (confirm('Delete all completed tasks?')) {
                        tasks = tasks.filter(t => t.status !== 'done');
                        saveData();
                        renderAll();
                    }
                };
                content.appendChild(clearBtn);
            }

            sectionEl.appendChild(header);
            sectionEl.appendChild(content);
            return sectionEl;
        }

        function createTaskCard(task) {
            const card = document.createElement('div');
            let classes = `task-card status-${task.status || 'not-started'} priority-${task.priority}`;
            if (isOverdue(task)) classes += ' overdue';
            if (isUrgent(task)) classes += ' urgent';
            card.className = classes;
            card.draggable = true;
            card.dataset.taskId = task.id;

            const statusIcon = statusIcons[task.status || 'not-started'];
            const completedSubtasks = task.subtasks ? task.subtasks.filter(s => s.completed).length : 0;
            const totalSubtasks = task.subtasks ? task.subtasks.length : 0;
            const progress = totalSubtasks > 0 ? (completedSubtasks / totalSubtasks * 100) : 0;

            let dueText = '';
            if (task.dueDate) {
                const due = parseLocalDate(task.dueDate);
                if (due) {
                    dueText = task.dueTime 
                        ? `${due.toLocaleDateString('en-US', { month: 'short', day: 'numeric' })} at ${formatTime12Hour(task.dueTime)}`
                        : due.toLocaleDateString('en-US', { month: 'short', day: 'numeric' });
                }
            }

            const dependsOn = task.dependsOn ? tasks.find(t => t.id == task.dependsOn) : null;
            const isDependencyMet = !dependsOn || dependsOn.status === 'done';

            card.innerHTML = `
                ${isUrgent(task) ? '<div class="urgent-badge">URGENT</div>' : ''}
                <div class="task-main">
                    <div class="task-checkbox">${statusIcon}</div>
                    <div class="task-content">
                        <div class="task-title">${task.title}</div>
                        <div class="task-meta">
                            <span class="category-badge category-${task.category}">${icons[task.category]} ${task.category}</span>
                            ${task.duration ? `<span class="meta-item">⏱️ ${task.duration}m</span>` : ''}
                            ${task.timeBlock ? `<span class="meta-item">${task.timeBlock === 'morning' ? '🌅' : task.timeBlock === 'afternoon' ? '☀️' : '🌙'}</span>` : ''}
                            ${dueText ? `<span class="meta-item due-time ${isOverdue(task) ? 'overdue' : ''}">📅 ${dueText}</span>` : ''}
                            ${task.energy ? `<span class="energy-badge energy-${task.energy}">${task.energy}</span>` : ''}
                            ${task.project ? `<span class="project-badge">${task.project}</span>` : ''}
                            ${task.tags && task.tags.length > 0 ? task.tags.map(tag => `<span class="tag-badge">#${tag}</span>`).join('') : ''}
                        </div>
                    </div>
                </div>
                ${totalSubtasks > 0 ? `
                    <div class="progress-container">
                        <div class="progress-bar">
                            <div class="progress-fill" style="width: ${progress}%"></div>
                        </div>
                        <div class="progress-text">${completedSubtasks}/${totalSubtasks} subtasks completed</div>
                    </div>
                ` : ''}
                ${!isDependencyMet ? `
                    <div style="background: rgba(255,193,7,0.1); padding: 8px; border-radius: 6px; font-size: 0.85em; margin: 8px 0;">
                        ⚠️ Blocked: Waiting for "${dependsOn.title}"
                    </div>
                ` : ''}
                ${totalSubtasks > 0 ? `
                    <div class="subtasks" id="subtasks-${task.id}" style="display: none;">
                        ${task.subtasks.map((subtask, idx) => `
                            <div class="subtask ${subtask.completed ? 'completed' : ''}">
                                <input type="checkbox" ${subtask.completed ? 'checked' : ''} 
                                    onchange="toggleSubtaskStatus(${task.id}, ${idx})" 
                                    style="cursor: pointer;">
                                <span class="subtask-text">${subtask.text}</span>
                            </div>
                        `).join('')}
                    </div>
                ` : ''}
                <div class="task-actions">
                    ${totalSubtasks > 0 ? `
                        <button class="task-btn" onclick="toggleSubtasksView(${task.id})">📋 Subtasks</button>
                    ` : ''}
                    ${task.status === 'not-started' ? `
                        <button class="task-btn primary" onclick="updateTaskStatus(${task.id}, 'in-progress')">▶ Start</button>
                    ` : ''}
                    ${task.status === 'in-progress' ? `
                        <button class="task-btn success" onclick="updateTaskStatus(${task.id}, 'done')">✓ Done</button>
                    ` : ''}
                    ${task.status === 'done' ? `
                        <button class="task-btn" onclick="updateTaskStatus(${task.id}, 'not-started')">↺ Undo</button>
                    ` : ''}
                    <button class="task-btn" onclick="editTask(${task.id})">✏️</button>
                    <button class="task-btn danger" onclick="deleteTask(${task.id})">🗑️</button>
                </div>
            `;

            // Add click handler for checkbox
            const checkbox = card.querySelector('.task-checkbox');
            checkbox.onclick = () => cycleTaskStatus(task.id);

            return card;
        }

        // ==================== DRAG AND DROP ====================
        function setupDragAndDrop() {
            document.addEventListener('dragstart', (e) => {
                if (e.target.classList.contains('task-card')) {
                    e.target.classList.add('dragging');
                    e.dataTransfer.effectAllowed = 'move';
                    e.dataTransfer.setData('text/plain', e.target.dataset.taskId);
                }
            });

            document.addEventListener('dragend', (e) => {
                if (e.target.classList.contains('task-card')) {
                    e.target.classList.remove('dragging');
                }
            });

            document.addEventListener('dragover', (e) => {
                e.preventDefault();
                const section = e.target.closest('.section');
                if (section) {
                    e.dataTransfer.dropEffect = 'move';
                }
            });

            document.addEventListener('drop', (e) => {
                e.preventDefault();
                const section = e.target.closest('.section');
                if (section) {
                    const taskId = parseInt(e.dataTransfer.getData('text/plain'));
                    const task = tasks.find(t => t.id === taskId);
                    if (task) {
                        const sectionName = section.dataset.section;
                        moveTaskToSection(task, sectionName);
                    }
                }
            });
        }

        function moveTaskToSection(task, sectionName) {
            const today = new Date();
            const tomorrow = new Date(today);
            tomorrow.setDate(today.getDate() + 1);
            const nextWeek = new Date(today);
            nextWeek.setDate(today.getDate() + 7);

            switch(sectionName) {
                case 'today':
                    task.dueDate = today.toISOString().split('T')[0];
                    break;
                case 'tomorrow':
                    task.dueDate = tomorrow.toISOString().split('T')[0];
                    break;
                case 'week':
                    task.dueDate = nextWeek.toISOString().split('T')[0];
                    break;
                case 'later':
                    task.dueDate = '';
                    break;
                case 'completed':
                    task.status = 'done';
                    break;
            }

            saveData();
            renderAll();
        }

        // ==================== FILTERING ====================
        function filterTasks(taskList) {
            let filtered = taskList;

            // Apply search
            if (searchQuery) {
                const query = searchQuery.toLowerCase();
                filtered = filtered.filter(t => 
                    t.title.toLowerCase().includes(query) ||
                    t.notes?.toLowerCase().includes(query) ||
                    t.project?.toLowerCase().includes(query) ||
                    t.tags?.some(tag => tag.toLowerCase().includes(query))
                );
            }

            // Apply filters
            if (currentFilter !== 'all') {
                if (currentFilter === 'priority-high') {
                    filtered = filtered.filter(t => t.priority === 'high');
                } else if (currentFilter === 'today') {
                    filtered = filtered.filter(t => getTaskSection(t) === 'today');
                } else if (['work', 'school', 'personal', 'health', 'finance'].includes(currentFilter)) {
                    filtered = filtered.filter(t => t.category === currentFilter);
                }
            }

            return filtered;
        }

        // ==================== TASK OPERATIONS ====================
        function toggleSubtasksView(taskId) {
            const el = document.getElementById(`subtasks-${taskId}`);
            if (el) el.style.display = el.style.display === 'none' ? 'block' : 'none';
        }

        function toggleSubtaskStatus(taskId, idx) {
            const task = tasks.find(t => t.id === taskId);
            if (task?.subtasks?.[idx]) {
                task.subtasks[idx].completed = !task.subtasks[idx].completed;
                saveData();
                renderAll();
            }
        }

        function cycleTaskStatus(taskId) {
            const task = tasks.find(t => t.id === taskId);
            if (!task) return;

            const statusCycle = ['not-started', 'in-progress', 'done'];
            const currentIndex = statusCycle.indexOf(task.status || 'not-started');
            const nextIndex = (currentIndex + 1) % statusCycle.length;
            task.status = statusCycle[nextIndex];

            if (task.status === 'done') {
                recordCompletion();
                // Celebration animation
                const card = document.querySelector(`[data-task-id="${taskId}"]`);
                if (card) {
                    card.classList.add('celebrating');
                    setTimeout(() => card.classList.remove('celebrating'), 500);
                }
            }

            saveData();
            renderAll();
        }

        function updateTaskStatus(taskId, newStatus) {
            const task = tasks.find(t => t.id === taskId);
            if (task) {
                task.status = newStatus;
                if (newStatus === 'done') recordCompletion();
                saveData();
                renderAll();
            }
        }

        function editTask(taskId) {
            editingTaskId = taskId;
            const task = tasks.find(t => t.id === taskId);
            
            document.getElementById('modalTitle').textContent = 'Edit Task';
            document.getElementById('taskTitleInput').value = task.title;
            document.getElementById('taskCategory').value = task.category;
            document.getElementById('taskPriority').value = task.priority;
            document.getElementById('taskDueDate').value = task.dueDate || '';
            document.getElementById('taskDueTime').value = task.dueTime || '';
            document.getElementById('taskTimeBlock').value = task.timeBlock || '';
            
            // Set start/end times if available, otherwise use duration
            if (task.startTime && task.endTime) {
                document.getElementById('taskStartTime').value = task.startTime;
                document.getElementById('taskEndTime').value = task.endTime;
                document.getElementById('taskDuration').value = task.duration || '';
            } else if (task.duration && task.dueTime) {
                // Calculate start/end from due time and duration
                const [hours, minutes] = task.dueTime.split(':').map(Number);
                const endMinutes = hours * 60 + minutes;
                const startMinutes = endMinutes - parseInt(task.duration);
                
                const startHours = Math.floor(startMinutes / 60);
                const startMins = startMinutes % 60;
                
                document.getElementById('taskStartTime').value = `${String(startHours).padStart(2, '0')}:${String(startMins).padStart(2, '0')}`;
                document.getElementById('taskEndTime').value = task.dueTime;
                document.getElementById('taskDuration').value = task.duration;
            } else {
                document.getElementById('taskStartTime').value = '';
                document.getElementById('taskEndTime').value = '';
                document.getElementById('taskDuration').value = task.duration || '';
            }
            
            document.getElementById('taskEnergy').value = task.energy || '';
            document.getElementById('taskProject').value = task.project || '';
            document.getElementById('taskNotes').value = task.notes || '';
            document.getElementById('taskDependency').value = task.dependsOn || '';
            document.getElementById('taskRecurring').checked = task.recurring || false;
            if (task.recurring) {
                document.getElementById('recurringFreq').style.display = 'block';
                document.getElementById('recurringFreq').value = task.recurringFreq || 'daily';
            }
            
            // Render tags
            const tagContainer = document.getElementById('tagContainer');
            const tagInput = document.getElementById('tagInput');
            tagContainer.querySelectorAll('.tag-item').forEach(el => el.remove());
            if (task.tags) {
                task.tags.forEach(tag => {
                    const tagEl = createTagElement(tag);
                    tagContainer.insertBefore(tagEl, tagInput);
                });
            }
            
            // Render subtasks
            const container = document.getElementById('subtasksContainer');
            container.innerHTML = '';
            if (task.subtasks) {
                task.subtasks.forEach((sub) => {
                    addSubtaskInput(sub.text);
                });
            }
            
            updateDependencyOptions();
            openModal('taskModal');
        }

        function deleteTask(taskId) {
            if (confirm('Delete this task?')) {
                tasks = tasks.filter(t => t.id !== taskId);
                saveData();
                renderAll();
            }
        }

        function toggleSection(sectionEl) {
            const content = sectionEl.querySelector('.section-content');
            const header = sectionEl.querySelector('.section-header');
            content.classList.toggle('collapsed');
            header.classList.toggle('collapsed');
        }

        // ==================== STATS VIEW ====================
        function renderCalendarView() {
            const grid = document.getElementById('calendarGrid');
            const titleEl = document.getElementById('calendarTitle');
            grid.innerHTML = '';

            const today = new Date();
            let startDate, numDays;

            if (calendarMode === 'day') {
                // Show just today
                startDate = new Date(today);
                startDate.setDate(today.getDate() + calendarOffset);
                numDays = 1;
                grid.style.gridTemplateColumns = '1fr';
                titleEl.textContent = startDate.toLocaleDateString('en-US', { 
                    weekday: 'long', 
                    month: 'long', 
                    day: 'numeric', 
                    year: 'numeric' 
                });
            } else if (calendarMode === 'week') {
                startDate = new Date(today);
                startDate.setDate(today.getDate() - today.getDay() + (calendarOffset * 7));
                numDays = 7;
                grid.style.gridTemplateColumns = 'repeat(7, 1fr)';
                const endDate = new Date(startDate);
                endDate.setDate(startDate.getDate() + 6);
                titleEl.textContent = `${startDate.toLocaleDateString('en-US', { month: 'short', day: 'numeric' })} - ${endDate.toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' })}`;
            } else if (calendarMode === 'month') {
                startDate = new Date(today.getFullYear(), today.getMonth() + calendarOffset, 1);
                startDate.setDate(1 - startDate.getDay());
                const monthEnd = new Date(today.getFullYear(), today.getMonth() + calendarOffset + 1, 0);
                const endDate = new Date(monthEnd);
                endDate.setDate(monthEnd.getDate() + (6 - monthEnd.getDay()));
                numDays = Math.ceil((endDate - startDate) / (1000 * 60 * 60 * 24)) + 1;
                grid.style.gridTemplateColumns = 'repeat(7, 1fr)';
                titleEl.textContent = new Date(today.getFullYear(), today.getMonth() + calendarOffset, 1).toLocaleDateString('en-US', { month: 'long', year: 'numeric' });
            }

            // Highlight active view button
            document.getElementById('dayViewBtn').style.background = calendarMode === 'day' ? 'var(--accent)' : 'var(--border)';
            document.getElementById('dayViewBtn').style.color = calendarMode === 'day' ? 'white' : 'var(--text)';
            document.getElementById('weekViewBtn').style.background = calendarMode === 'week' ? 'var(--accent)' : 'var(--border)';
            document.getElementById('weekViewBtn').style.color = calendarMode === 'week' ? 'white' : 'var(--text)';
            document.getElementById('monthViewBtn').style.background = calendarMode === 'month' ? 'var(--accent)' : 'var(--border)';
            document.getElementById('monthViewBtn').style.color = calendarMode === 'month' ? 'white' : 'var(--text)';

            for (let i = 0; i < numDays; i++) {
                const date = new Date(startDate);
                date.setDate(startDate.getDate() + i);
                
                const dayEl = document.createElement('div');
                dayEl.className = 'calendar-day';
                
                if (date.toDateString() === today.toDateString()) {
                    dayEl.classList.add('today');
                }

                const isCurrentMonth = calendarMode === 'month' ? 
                    date.getMonth() === (today.getMonth() + calendarOffset) : true;
                
                if (!isCurrentMonth) {
                    dayEl.style.opacity = '0.4';
                }

                const dayTasks = getTasksForDate(date);
                
                // Determine max tasks to show based on mode
                const maxTasksToShow = calendarMode === 'day' ? 50 : calendarMode === 'week' ? 5 : 3;
                const visibleTasks = dayTasks.slice(0, maxTasksToShow);
                const remainingCount = dayTasks.length - maxTasksToShow;

                const headerText = calendarMode === 'day' 
                    ? date.toLocaleDateString('en-US', { weekday: 'long' })
                    : calendarMode === 'month' 
                        ? date.toLocaleDateString('en-US', { month: 'short', day: 'numeric' })
                        : `${date.toLocaleDateString('en-US', { weekday: 'short' })}<br>${date.getDate()}`;

                dayEl.innerHTML = `
                    <div class="calendar-day-header">${headerText}</div>
                    ${visibleTasks.map(task => {
                        let classes = `calendar-task status-${task.status || 'not-started'} priority-${task.priority}`;
                        if (isUrgent(task)) classes += ' urgent';
                        
                        // Smart truncation based on view mode
                        let displayTitle = task.title;
                        const maxLength = calendarMode === 'day' ? 50 : calendarMode === 'week' ? 20 : 12;
                        if (displayTitle.length > maxLength) {
                            displayTitle = displayTitle.substring(0, maxLength) + '...';
                        }
                        
                        return `
                            <div class="${classes}" onclick="editTask(${task.id})" title="${task.title}">
                                ${displayTitle}
                            </div>
                        `;
                    }).join('')}
                    ${remainingCount > 0 ? `<div class="calendar-task-count">+${remainingCount} more</div>` : ''}
                `;

                grid.appendChild(dayEl);
            }
        }

        function getTasksForDate(date) {
            const dateStr = date.toISOString().split('T')[0];
            return tasks.filter(t => t.dueDate === dateStr);
        }

        function setCalendarMode(mode) {
            calendarMode = mode;
            calendarOffset = 0;
            renderCalendarView();
        }

        function changeCalendarView(direction) {
            calendarOffset += direction;
            renderCalendarView();
        }

        // ==================== BOARD VIEW ====================
        function renderBoardView() {
            const container = document.getElementById('boardContainer');
            container.innerHTML = '';

            const columns = [
                { id: 'not-started', title: '⚪ Not Started', tasks: [] },
                { id: 'in-progress', title: '🟡 In Progress', tasks: [] },
                { id: 'done', title: '✅ Done', tasks: [] }
            ];

            // Filter and sort tasks
            let filteredTasks = filterTasks(tasks);

            filteredTasks.forEach(task => {
                const status = task.status || 'not-started';
                const column = columns.find(c => c.id === status);
                if (column) column.tasks.push(task);
            });

            // Sort by priority within each column
            columns.forEach(column => {
                column.tasks.sort((a, b) => {
                    const priorityOrder = { high: 0, medium: 1, low: 2 };
                    return priorityOrder[a.priority] - priorityOrder[b.priority];
                });
            });

            columns.forEach(column => {
                const columnEl = document.createElement('div');
                columnEl.className = `board-column ${column.id}`;
                
                columnEl.innerHTML = `
                    <div class="board-column-header">
                        <span>${column.title}</span>
                        <span style="background: var(--border); padding: 2px 8px; border-radius: 12px; font-size: 0.85em;">${column.tasks.length}</span>
                    </div>
                    <div class="board-tasks"></div>
                `;

                const tasksContainer = columnEl.querySelector('.board-tasks');
                
                if (column.tasks.length === 0) {
                    tasksContainer.innerHTML = '<div class="empty-state" style="padding: 20px; font-size: 0.9em;">No tasks</div>';
                } else {
                    column.tasks.forEach(task => {
                        const card = createBoardTaskCard(task);
                        tasksContainer.appendChild(card);
                    });
                }

                container.appendChild(columnEl);
            });
        }

        function createBoardTaskCard(task) {
            const card = document.createElement('div');
            let classes = `board-task-card status-${task.status || 'not-started'} priority-${task.priority}`;
            if (isUrgent(task)) classes += ' urgent';
            card.className = classes;
            card.onclick = () => editTask(task.id);

            let dueText = '';
            if (task.dueDate) {
                const due = parseLocalDate(task.dueDate);
                if (due) {
                    dueText = task.dueTime 
                        ? `${due.toLocaleDateString('en-US', { month: 'short', day: 'numeric' })} ${formatTime12Hour(task.dueTime)}`
                        : due.toLocaleDateString('en-US', { month: 'short', day: 'numeric' });
                }
            }

            const completedSubtasks = task.subtasks ? task.subtasks.filter(s => s.completed).length : 0;
            const totalSubtasks = task.subtasks ? task.subtasks.length : 0;

            card.innerHTML = `
                <div class="board-task-title">${task.title}</div>
                <div class="board-task-meta">
                    <span class="category-badge category-${task.category}">${icons[task.category]}</span>
                    ${task.duration ? `<span>⏱️ ${task.duration}m</span>` : ''}
                    ${dueText ? `<span ${isOverdue(task) ? 'style="color: var(--overdue); font-weight: 600;"' : ''}>📅 ${dueText}</span>` : ''}
                    ${totalSubtasks > 0 ? `<span>✓ ${completedSubtasks}/${totalSubtasks}</span>` : ''}
                    ${task.energy ? `<span class="energy-badge energy-${task.energy}">${task.energy}</span>` : ''}
                    ${task.project ? `<span class="project-badge">${task.project}</span>` : ''}
                </div>
            `;

            return card;
        }

        // ==================== STATS VIEW ====================
        function renderStatsView() {
            const total = tasks.length;
            const completed = tasks.filter(t => t.status === 'done').length;
            const completionRate = total > 0 ? Math.round((completed / total) * 100) : 0;

            document.getElementById('totalTasksStat').textContent = total;
            document.getElementById('completedStat').textContent = completed;
            document.getElementById('completionRateStat').textContent = completionRate + '%';
            document.getElementById('streakStat').textContent = stats.streak;

            // Category breakdown
            const categoryData = {};
            tasks.forEach(task => {
                categoryData[task.category] = (categoryData[task.category] || 0) + 1;
            });

            const categoryChart = document.getElementById('categoryChart');
            categoryChart.innerHTML = '';
            Object.entries(categoryData).forEach(([cat, count]) => {
                const bar = document.createElement('div');
                bar.className = 'chart-bar';
                const percent = (count / total * 100).toFixed(0);
                bar.innerHTML = `
                    <div class="chart-label">${icons[cat]} ${cat}</div>
                    <div class="chart-fill-container">
                        <div class="chart-fill" style="width: ${percent}%"></div>
                    </div>
                    <div class="chart-value">${count}</div>
                `;
                categoryChart.appendChild(bar);
            });

            // Week chart (placeholder)
            const weekChart = document.getElementById('weekChart');
            weekChart.innerHTML = '<p style="color: var(--text-dim); text-align: center;">Track your progress over time!</p>';
        }

        // ==================== MODAL MANAGEMENT ====================
        function calculateDuration() {
            const startTime = document.getElementById('taskStartTime').value;
            const endTime = document.getElementById('taskEndTime').value;
            
            if (startTime && endTime) {
                const [startHours, startMinutes] = startTime.split(':').map(Number);
                const [endHours, endMinutes] = endTime.split(':').map(Number);
                
                const startTotalMinutes = startHours * 60 + startMinutes;
                const endTotalMinutes = endHours * 60 + endMinutes;
                
                let duration = endTotalMinutes - startTotalMinutes;
                
                // Handle overnight tasks
                if (duration < 0) {
                    duration += 24 * 60;
                }
                
                document.getElementById('taskDuration').value = duration;
            }
        }

        function addTagFromInput() {
            const input = document.getElementById('tagInput');
            const value = input.value.trim();
            
            if (value) {
                const tagEl = createTagElement(value);
                const container = document.getElementById('tagContainer');
                container.insertBefore(tagEl, input);
                input.value = '';
            }
        }

        function openModal(modalId) {
            document.getElementById(modalId).classList.add('active');
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('active');
            if (modalId === 'taskModal') {
                editingTaskId = null;
                document.getElementById('taskForm').reset();
                document.getElementById('subtasksContainer').innerHTML = '';
                document.getElementById('tagContainer').querySelectorAll('.tag-item').forEach(el => el.remove());
            }
        }

        function updateDependencyOptions() {
            const select = document.getElementById('taskDependency');
            select.innerHTML = '<option value="">No dependency</option>';
            
            tasks.filter(t => t.id !== editingTaskId && t.status !== 'done').forEach(task => {
                const option = document.createElement('option');
                option.value = task.id;
                option.textContent = `${task.title} (${task.category})`;
                select.appendChild(option);
            });
        }

        // ==================== TAG MANAGEMENT ====================
        function createTagElement(tagText) {
            const tagEl = document.createElement('div');
            tagEl.className = 'tag-item';
            tagEl.innerHTML = `${tagText} <span class="tag-remove" onclick="this.parentElement.remove()">×</span>`;
            return tagEl;
        }

        // ==================== SUBTASK MANAGEMENT ====================
        function addSubtaskInput(text = '') {
            const container = document.getElementById('subtasksContainer');
            const div = document.createElement('div');
            div.className = 'form-group';
            div.innerHTML = `<input type="text" class="subtask-input" placeholder="Subtask..." value="${text}">`;
            container.appendChild(div);
        }

        // ==================== SETTINGS ====================
        function applyTheme(theme) {
            document.body.className = theme;
        }

        function saveSettings() {
            settings.theme = document.getElementById('themeSelect').value;
            settings.weekStart = parseInt(document.getElementById('weekStartSelect').value);
            settings.defaultDuration = parseInt(document.getElementById('defaultDuration').value);
            settings.urgentThreshold = parseInt(document.getElementById('urgentThreshold').value);
            settings.soundAlerts = document.getElementById('soundAlerts').checked;
            
            applyTheme(settings.theme);
            saveData();
            closeModal('settingsModal');
        }

        // ==================== DATA EXPORT/IMPORT ====================
        function exportData() {
            const data = {
                tasks,
                settings,
                stats,
                templates,
                exportDate: new Date().toISOString()
            };
            
            const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `planner-backup-${new Date().toISOString().split('T')[0]}.json`;
            a.click();
            URL.revokeObjectURL(url);
        }

        function importData(event) {
            const file = event.target.files[0];
            if (!file) return;
            
            const reader = new FileReader();
            reader.onload = (e) => {
                try {
                    const data = JSON.parse(e.target.result);
                    if (confirm('This will replace all current data. Continue?')) {
                        tasks = data.tasks || [];
                        settings = { ...settings, ...(data.settings || {}) };
                        stats = { ...stats, ...(data.stats || {}) };
                        templates = data.templates || [];
                        saveData();
                        applyTheme(settings.theme);
                        renderAll();
                        alert('Data imported successfully!');
                    }
                } catch (err) {
                    alert('Error importing data: ' + err.message);
                }
            };
            reader.readAsText(file);
        }

        // ==================== EVENT LISTENERS ====================
        function setupEventListeners() {
            // Quick add with NLP
            document.getElementById('quickAddInput').addEventListener('keypress', (e) => {
                if (e.key === 'Enter' && e.target.value.trim()) {
                    const parsed = parseNaturalLanguage(e.target.value);
                    const newTask = {
                        id: Date.now(),
                        ...parsed,
                        status: 'not-started',
                        subtasks: [],
                        tags: [],
                        created: Date.now()
                    };
                    tasks.push(newTask);
                    saveData();
                    renderAll();
                    e.target.value = '';
                }
            });

            // Search
            document.getElementById('searchInput').addEventListener('input', (e) => {
                searchQuery = e.target.value;
                renderAll();
            });

            // Filter chips
            document.querySelectorAll('.filter-chip').forEach(chip => {
                chip.addEventListener('click', () => {
                    document.querySelectorAll('.filter-chip').forEach(c => c.classList.remove('active'));
                    chip.classList.add('active');
                    currentFilter = chip.dataset.filter;
                    renderAll();
                });
            });

            // FAB
            document.getElementById('fabBtn').addEventListener('click', () => {
                editingTaskId = null;
                document.getElementById('modalTitle').textContent = 'Add Task';
                document.getElementById('taskForm').reset();
                document.getElementById('subtasksContainer').innerHTML = '';
                document.getElementById('tagContainer').querySelectorAll('.tag-item').forEach(el => el.remove());
                updateDependencyOptions();
                openModal('taskModal');
            });

            // Task form submission
            document.getElementById('taskForm').addEventListener('submit', (e) => {
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
                    title: document.getElementById('taskTitleInput').value,
                    category: document.getElementById('taskCategory').value,
                    priority: document.getElementById('taskPriority').value,
                    dueDate: document.getElementById('taskDueDate').value,
                    dueTime: document.getElementById('taskDueTime').value,
                    timeBlock: document.getElementById('taskTimeBlock').value,
                    startTime: document.getElementById('taskStartTime').value,
                    endTime: document.getElementById('taskEndTime').value,
                    duration: document.getElementById('taskDuration').value,
                    energy: document.getElementById('taskEnergy').value,
                    project: document.getElementById('taskProject').value,
                    dependsOn: document.getElementById('taskDependency').value || null,
                    notes: document.getElementById('taskNotes').value,
                    subtasks: subtasks,
                    tags: tags,
                    recurring: document.getElementById('taskRecurring').checked,
                    recurringFreq: document.getElementById('taskRecurring').checked ? document.getElementById('recurringFreq').value : null,
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
                closeModal('taskModal');
                renderAll();
            });

            // Tag input
            document.getElementById('tagInput').addEventListener('keypress', (e) => {
                if (e.key === 'Enter' && e.target.value.trim()) {
                    e.preventDefault();
                    const tagEl = createTagElement(e.target.value.trim());
                    const container = document.getElementById('tagContainer');
                    container.insertBefore(tagEl, e.target);
                    e.target.value = '';
                }
            });

            // Recurring toggle
            document.getElementById('taskRecurring').addEventListener('change', (e) => {
                document.getElementById('recurringFreq').style.display = e.target.checked ? 'block' : 'none';
            });

            // Add subtask button
            document.getElementById('addSubtaskBtn').addEventListener('click', () => addSubtaskInput());

            // Navigation
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.addEventListener('click', () => {
                    const view = btn.dataset.view;
                    currentView = view;
                    
                    document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
                    btn.classList.add('active');

                    document.getElementById('mainView').style.display = view === 'main' ? 'block' : 'none';
                    document.getElementById('calendarView').style.display = view === 'calendar' ? 'block' : 'none';
                    document.getElementById('boardView').style.display = view === 'board' ? 'block' : 'none';
                    document.getElementById('statsView').style.display = view === 'stats' ? 'block' : 'none';

                    if (view === 'settings') {
                        document.getElementById('themeSelect').value = settings.theme;
                        document.getElementById('weekStartSelect').value = settings.weekStart;
                        document.getElementById('defaultDuration').value = settings.defaultDuration;
                        document.getElementById('urgentThreshold').value = settings.urgentThreshold;
                        document.getElementById('soundAlerts').checked = settings.soundAlerts;
                        openModal('settingsModal');
                    } else {
                        renderAll();
                    }
                });
            });

            // Header buttons
            document.getElementById('statsBtn').addEventListener('click', () => {
                currentView = 'stats';
                document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
                document.querySelector('[data-view="stats"]').classList.add('active');
                document.getElementById('mainView').style.display = 'none';
                document.getElementById('statsView').style.display = 'block';
                renderStatsView();
            });

            document.getElementById('settingsBtn').addEventListener('click', () => {
                document.getElementById('themeSelect').value = settings.theme;
                document.getElementById('weekStartSelect').value = settings.weekStart;
                document.getElementById('defaultDuration').value = settings.defaultDuration;
                document.getElementById('urgentThreshold').value = settings.urgentThreshold;
                document.getElementById('soundAlerts').checked = settings.soundAlerts;
                openModal('settingsModal');
            });

            document.getElementById('themeBtn').addEventListener('click', () => {
                const themes = ['light', 'dark', 'ocean', 'forest', 'sunset'];
                const currentIndex = themes.indexOf(settings.theme);
                const nextIndex = (currentIndex + 1) % themes.length;
                settings.theme = themes[nextIndex];
                applyTheme(settings.theme);
                saveData();
            });

            // Keyboard shortcuts
            document.addEventListener('keydown', (e) => {
                // Ignore if typing in input
                if (e.target.tagName === 'INPUT' || e.target.tagName === 'TEXTAREA') return;

                if (e.key === 'n' || e.key === 'N') {
                    document.getElementById('fabBtn').click();
                } else if (e.key === '/') {
                    e.preventDefault();
                    document.getElementById('searchInput').focus();
                } else if (e.key === 's' || e.key === 'S') {
                    document.getElementById('statsBtn').click();
                } else if (e.key === '?') {
                    document.getElementById('settingsBtn').click();
                }
            });

            // Close modals on outside click
            document.querySelectorAll('.modal').forEach(modal => {
                modal.addEventListener('click', (e) => {
                    if (e.target === modal) {
                        closeModal(modal.id);
                    }
                });
            });
        }

        // ==================== INITIALIZE ====================
        init();
    </script>
</body>
</html>
