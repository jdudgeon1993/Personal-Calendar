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

        html { width: 100%; overflow-x: hidden; scroll-behavior: smooth; }
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: var(--bg-primary); color: var(--text-primary); line-height: 1.6;
            -webkit-font-smoothing: antialiased; overflow-x: hidden; padding-bottom: 80px;
            transition: var(--transition); width: 100%; max-width: 100vw;
        }

        * { max-width: 100%; }

        .container {
            max-width: 1200px; margin: 0 auto; padding: var(--spacing-lg);
            width: 100%; box-sizing: border-box;
        }

        @media (max-width: 768px) {
            .container { padding: var(--spacing-sm); }
            .form-row, .stats-grid, .board-container { grid-template-columns: 1fr; }
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

        /* Dynamic Board Task Status Colors */
        .task-card.due-today {
            background: rgba(245, 158, 11, 0.15);
            border-color: var(--warning);
        }
        .task-card.urgent-overdue {
            background: rgba(239, 68, 68, 0.15);
            border-color: var(--error);
        }

        /* Dragging state */
        .task-card.dragging {
            opacity: 0.5;
            cursor: grabbing;
        }

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

        .task-checkbox.in-progress {
            background: var(--bg-primary);
            border-color: var(--primary);
            animation: checkPop 0.3s cubic-bezier(0.68,-0.55,0.265,1.55);
        }

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
        .badge-time, .badge-duration { background: var(--bg-tertiary); color: var(--text-secondary); }

        .section { margin-bottom: var(--spacing-xl); }

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

        /* Timeline (Daily) Styles */
        .timeline-container {
            background: var(--bg-secondary); border-radius: var(--radius-lg);
            padding: var(--spacing-md); box-shadow: 0 2px 8px var(--shadow);
            position: relative; overflow: hidden;
        }

        .timeline-header {
            margin-bottom: var(--spacing-md);
            padding-bottom: var(--spacing-md);
            border-bottom: 2px solid var(--border);
        }

        .timeline-grid {
            position: relative; 
            min-height: 600px;
            max-height: 800px;
            overflow-y: auto;
        }

        .timeline-hours {
            position: absolute; left: 0; top: 0; width: 60px;
            border-right: 2px solid var(--border);
        }

        .timeline-hour {
            height: 60px; display: flex; align-items: flex-start; padding: 4px;
            font-size: 12px; font-weight: 600; color: var(--text-tertiary);
            border-bottom: 1px solid var(--border);
        }

        .timeline-tasks {
            margin-left: 60px;
            position: relative;
            min-height: 1080px; /* 18 hours * 60px */
        }

        .timeline-task {
            position: absolute; 
            left: var(--spacing-sm); 
            right: var(--spacing-sm);
            border-radius: var(--radius-md); 
            padding: var(--spacing-sm);
            overflow: hidden; 
            cursor: pointer; 
            transition: var(--transition);
            box-shadow: 0 2px 4px var(--shadow);
        }

        .timeline-task:hover {
            transform: translateX(4px); 
            box-shadow: 0 4px 12px var(--shadow-lg);
            z-index: 10;
        }

        .timeline-task-title {
            font-size: 13px; font-weight: 600; color: white; margin-bottom: 2px;
            overflow: hidden; text-overflow: ellipsis; white-space: nowrap;
        }

        .timeline-task-time {
            font-size: 11px; color: rgba(255,255,255,0.9);
        }

        .timeline-now {
            position: absolute; 
            left: 0; 
            right: 0; 
            height: 2px;
            background: var(--error); 
            z-index: 20;
            pointer-events: none;
        }

        .timeline-now::before {
            content: ''; 
            position: absolute; 
            left: -6px; 
            top: -4px;
            width: 10px; 
            height: 10px; 
            border-radius: 50%; 
            background: var(--error);
        }
        
        /* Calendar Navigation */
        .calendar-nav {
            display: flex; gap: var(--spacing-sm); margin-bottom: var(--spacing-md);
            overflow-x: auto; padding-bottom: var(--spacing-sm);
        }

        .calendar-nav-btn {
            padding: 8px 16px; border-radius: var(--radius-md); border: 2px solid var(--border);
            background: var(--bg-secondary); color: var(--text-secondary);
            font-weight: 600; cursor: pointer; transition: var(--transition);
            white-space: nowrap;
        }

        .calendar-nav-btn.active {
            background: var(--primary); border-color: var(--primary); color: white;
            box-shadow: 0 2px 8px rgba(99,102,241,0.3);
        }

        .calendar-nav-btn:hover:not(.active) {
            border-color: var(--primary-light);
            color: var(--primary);
        }

        /* Weekly Grid */
        .weekly-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 1px;
            border: 1px solid var(--border);
            border-radius: var(--radius-md);
            overflow: hidden;
            background: var(--border);
        }
        
        .weekly-day-container {
            background: var(--bg-secondary);
            min-height: 120px;
            overflow-y: auto;
            max-height: 250px;
        }
        
        .weekly-day-header {
            text-align: center; padding: var(--spacing-sm);
            font-size: 14px; font-weight: 700; background: var(--bg-tertiary);
            position: sticky; top: 0; z-index: 5;
            border-bottom: 1px solid var(--border);
        }

        .calendar-task {
            padding: 6px 8px;
            margin: 4px;
            border-radius: var(--radius-sm);
            font-size: 12px;
            border-left: 3px solid;
            cursor: pointer;
            transition: var(--transition);
        }

        .calendar-task:hover {
            transform: translateX(2px);
            box-shadow: 0 2px 8px var(--shadow);
        }

        /* Monthly Grid */
        .monthly-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 1px;
            border: 1px solid var(--border);
            border-radius: var(--radius-md);
            overflow: hidden;
            background: var(--border);
        }

        .monthly-day-container {
            background: var(--bg-secondary);
            min-height: 100px;
            padding: var(--spacing-xs);
            border: 1px solid transparent;
        }

        .monthly-day-container.today {
            border-color: var(--primary);
            background: rgba(99,102,241,0.05);
        }

        .monthly-date {
            font-size: 14px; font-weight: 700; margin-bottom: 4px;
            display: block; text-align: right; padding-right: 4px;
        }

        .monthly-task-badge {
            font-size: 10px; padding: 2px 4px; margin-bottom: 2px;
            border-radius: 4px; overflow: hidden; white-space: nowrap;
            text-overflow: ellipsis; display: block; color: white;
            cursor: pointer;
        }
        
        /* Board View Styles */
        .board-container {
            display: grid; 
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: var(--spacing-md);
        }

        .board-column {
            background: var(--bg-secondary); 
            border-radius: var(--radius-lg);
            padding: var(--spacing-md); 
            min-height: 400px;
            box-shadow: 0 2px 8px var(--shadow);
            transition: var(--transition);
        }

        .board-column.drag-over {
            box-shadow: 0 0 0 4px var(--primary-light);
            background: var(--bg-tertiary);
        }

        .board-column-header {
            font-size: 14px; font-weight: 700; text-transform: uppercase;
            letter-spacing: 0.5px; margin-bottom: var(--spacing-md);
            display: flex; align-items: center; justify-content: space-between;
            padding-bottom: var(--spacing-sm); border-bottom: 2px solid var(--border);
        }

        .board-tasks {
            min-height: 300px;
        }

        /* Stats View Styles */
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

        /* Gantt Chart Styles */
        .gantt-container {
            background: var(--bg-secondary);
            border-radius: var(--radius-lg);
            padding: var(--spacing-md);
            box-shadow: 0 2px 8px var(--shadow);
            overflow-x: auto;
        }

        .gantt-header {
            margin-bottom: var(--spacing-md);
            padding-bottom: var(--spacing-md);
            border-bottom: 2px solid var(--border);
        }

        .gantt-placeholder {
            text-align: center;
            padding: var(--spacing-xl) var(--spacing-md);
            color: var(--text-secondary);
        }

        .gantt-placeholder-icon {
            font-size: 80px;
            margin-bottom: var(--spacing-md);
            opacity: 0.5;
        }

        .gantt-placeholder-title {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: var(--spacing-sm);
            color: var(--text-primary);
        }

        .gantt-placeholder-text {
            font-size: 16px;
            margin-bottom: var(--spacing-lg);
            line-height: 1.5;
        }

        .gantt-features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: var(--spacing-md);
            margin-top: var(--spacing-lg);
            text-align: left;
        }

        .gantt-feature {
            background: var(--bg-tertiary);
            padding: var(--spacing-md);
            border-radius: var(--radius-md);
        }

        .gantt-feature-icon {
            font-size: 24px;
            margin-bottom: var(--spacing-xs);
        }

        .gantt-feature-title {
            font-weight: 600;
            margin-bottom: var(--spacing-xs);
            color: var(--text-primary);
        }

        .gantt-feature-desc {
            font-size: 14px;
            color: var(--text-tertiary);
        }

        .gantt-controls {
            display: flex;
            gap: var(--spacing-sm);
            margin-bottom: var(--spacing-md);
            flex-wrap: wrap;
        }

        .gantt-control-btn {
            padding: var(--spacing-xs) var(--spacing-md);
            background: var(--bg-tertiary);
            border: 2px solid var(--border);
            border-radius: var(--radius-sm);
            color: var(--text-primary);
            cursor: pointer;
            transition: var(--transition);
            font-size: 14px;
            font-weight: 500;
        }

        .gantt-control-btn.active {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        .gantt-control-btn:hover {
            border-color: var(--primary);
        }

        .gantt-timeline {
            position: relative;
            overflow-x: auto;
            background: var(--bg-primary);
            border-radius: var(--radius-md);
        }

        .gantt-timeline-header {
            display: flex;
            position: sticky;
            top: 0;
            background: var(--bg-secondary);
            border-bottom: 2px solid var(--border);
            z-index: 2;
        }

        .gantt-timeline-date {
            flex: 1;
            min-width: 120px;
            padding: var(--spacing-sm);
            text-align: center;
            border-right: 1px solid var(--border);
            font-size: 13px;
            font-weight: 600;
            color: var(--text-primary);
        }

        .gantt-timeline-date.today {
            background: var(--primary-light);
            color: white;
        }

        .gantt-rows {
            position: relative;
        }

        .gantt-row {
            display: flex;
            position: relative;
            min-height: 60px;
            border-bottom: 1px solid var(--border);
        }

        .gantt-row:hover {
            background: var(--bg-secondary);
        }

        .gantt-row-label {
            position: sticky;
            left: 0;
            width: 200px;
            min-width: 200px;
            padding: var(--spacing-sm) var(--spacing-md);
            background: var(--bg-secondary);
            border-right: 2px solid var(--border);
            display: flex;
            flex-direction: column;
            justify-content: center;
            z-index: 1;
        }

        .gantt-row-title {
            font-weight: 600;
            font-size: 14px;
            color: var(--text-primary);
            margin-bottom: var(--spacing-xs);
        }

        .gantt-row-subtitle {
            font-size: 12px;
            color: var(--text-secondary);
        }

        .gantt-row-timeline {
            flex: 1;
            display: flex;
            position: relative;
        }

        .gantt-timeline-cell {
            flex: 1;
            min-width: 120px;
            border-right: 1px solid var(--border);
            position: relative;
        }

        .gantt-timeline-cell.today {
            background: rgba(99, 102, 241, 0.05);
        }

        .gantt-task-bar {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            height: 32px;
            border-radius: var(--radius-sm);
            padding: 0 var(--spacing-sm);
            display: flex;
            align-items: center;
            font-size: 12px;
            font-weight: 500;
            color: white;
            cursor: pointer;
            transition: var(--transition);
            overflow: hidden;
            white-space: nowrap;
            text-overflow: ellipsis;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .gantt-task-bar:hover {
            filter: brightness(1.1);
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
            z-index: 10;
        }

        .gantt-task-bar.priority-high {
            background: linear-gradient(135deg, var(--priority-high), #DC2626);
        }

        .gantt-task-bar.priority-medium {
            background: linear-gradient(135deg, var(--priority-medium), #D97706);
        }

        .gantt-task-bar.priority-low {
            background: linear-gradient(135deg, var(--priority-low), #059669);
        }

        .gantt-task-bar.status-done {
            opacity: 0.6;
            text-decoration: line-through;
        }

        .gantt-task-bar.dragging {
            opacity: 0.5;
            cursor: grabbing;
        }

        .gantt-task-bar.critical-path {
            box-shadow: 0 0 0 2px #EF4444, 0 4px 8px rgba(0,0,0,0.2);
        }

        .gantt-task-progress {
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            background: rgba(255, 255, 255, 0.3);
            border-right: 2px solid rgba(255, 255, 255, 0.6);
            pointer-events: none;
            transition: width 0.3s ease;
        }

        .gantt-milestone {
            position: absolute;
            top: 50%;
            transform: translateY(-50%) rotate(45deg);
            width: 24px;
            height: 24px;
            background: linear-gradient(135deg, #F59E0B, #D97706);
            border: 2px solid white;
            cursor: pointer;
            box-shadow: 0 2px 4px rgba(0,0,0,0.2);
            transition: var(--transition);
        }

        .gantt-milestone:hover {
            transform: translateY(-50%) rotate(45deg) scale(1.2);
            box-shadow: 0 4px 8px rgba(0,0,0,0.3);
        }

        .gantt-milestone-label {
            position: absolute;
            top: -30px;
            left: 50%;
            transform: translateX(-50%) rotate(-45deg);
            font-size: 11px;
            font-weight: 600;
            white-space: nowrap;
            color: var(--text-primary);
            background: var(--bg-secondary);
            padding: 2px 6px;
            border-radius: var(--radius-sm);
            pointer-events: none;
        }

        .gantt-dependency-line {
            position: absolute;
            height: 2px;
            background: var(--primary);
            pointer-events: none;
            z-index: 0;
        }

        .gantt-dependency-arrow {
            position: absolute;
            right: -6px;
            top: -3px;
            width: 0;
            height: 0;
            border-left: 6px solid var(--primary);
            border-top: 4px solid transparent;
            border-bottom: 4px solid transparent;
        }

        .gantt-empty-state {
            text-align: center;
            padding: var(--spacing-xl);
            color: var(--text-secondary);
        }

        /* Global / Nav / Modal Styles */
        .fab {
            position: fixed; bottom: 90px; right: var(--spacing-lg);
            width: 64px; height: 64px; border-radius: var(--radius-full);
            background: linear-gradient(135deg, var(--primary), var(--primary-light));
            color: white; border: none; font-size: 28px; cursor: pointer;
            box-shadow: 0 8px 24px rgba(99,102,241,0.4); transition: var(--transition);
            z-index: 999; display: flex; align-items: center; justify-content: center;
        }

        .fab:hover { transform: scale(1.1) rotate(90deg); box-shadow: 0 12px 32px rgba(99,102,241,0.6); }
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
        }

        .modal-header {
            display: flex; justify-content: space-between; align-items: center;
            margin-bottom: var(--spacing-lg); padding-bottom: var(--spacing-md);
            border-bottom: 2px solid var(--border);
        }

        .modal-title { font-size: 24px; font-weight: 800; color: var(--text-primary); }

        .close-btn {
            width: 32px; height: 32px; border-radius: var(--radius-full);
            border: none; background: var(--bg-tertiary); color: var(--text-secondary);
            font-size: 20px; cursor: pointer; transition: var(--transition);
        }

        .close-btn:hover { background: var(--error); color: white; transform: rotate(90deg); }

        .form-group { margin-bottom: var(--spacing-md); }

        .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: var(--spacing-md); }

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

        .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 6px 16px rgba(99,102,241,0.4); }
        .btn-primary:active { transform: translateY(0); }

        .btn-secondary { background: var(--bg-tertiary); color: var(--text-primary); }
        .btn-secondary:hover { background: var(--border); }

        .tag-container {
            display: flex; flex-wrap: wrap; gap: var(--spacing-xs);
            padding: var(--spacing-sm); border: 2px solid var(--border);
            border-radius: var(--radius-md); background: var(--bg-primary);
            min-height: 44px;
        }

        .tag-item {
            background: var(--primary); color: white; padding: 4px 8px;
            border-radius: var(--radius-sm); font-size: 12px; font-weight: 600;
            display: flex; align-items: center; gap: 4px;
        }

        .tag-remove { cursor: pointer; font-weight: bold; }

        .tag-input {
            border: none; background: transparent; outline: none;
            flex: 1; min-width: 120px; padding: 8px;
            color: var(--text-primary); font-size: 16px;
        }

        .subtask-list { display: flex; flex-direction: column; gap: var(--spacing-sm); }
        .subtask-item { display: flex; gap: var(--spacing-sm); align-items: center; }

        .subtask-input {
            flex: 1; padding: var(--spacing-sm); border: 1px solid var(--border);
            border-radius: var(--radius-sm); background: var(--bg-primary);
            color: var(--text-primary);
        }

        .empty-state { text-align: center; padding: var(--spacing-xl); color: var(--text-tertiary); }
        .empty-state-icon { font-size: 64px; margin-bottom: var(--spacing-md); opacity: 0.5; }
        .empty-state-text { font-size: 18px; font-weight: 600; color: var(--text-secondary); }

        .hidden { display: none !important; }
        .text-center { text-align: center; }

        /* Mobile Responsive Fixes */
        @media (max-width: 768px) {
            .container { padding: var(--spacing-sm); }
            .header { padding: var(--spacing-sm) var(--spacing-md); }
            .logo { font-size: 20px; }
            .form-row, .stats-grid, .board-container { grid-template-columns: 1fr !important; }
            .timeline-container { margin-left: calc(-1 * var(--spacing-sm)); margin-right: calc(-1 * var(--spacing-sm)); }
            .search-box, .filter-chips { margin-left: 0; margin-right: 0; }
            .modal-content { padding: var(--spacing-md); }
            .task-card { padding: var(--spacing-sm); }
            .task-title { font-size: 14px; }
            .badge { font-size: 11px; padding: 3px 6px; }
            .weekly-day-container, .monthly-day-container { max-height: 150px; }
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
        <button class="nav-btn" data-view="gantt">
            <span>📈</span><span>Gantt</span>
        </button>
        <button class="nav-btn" data-view="stats">
            <span>📉</span><span>Stats</span>
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
                    <div class="tag-container" id="tagContainer">
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

                <div class="form-group">
                    <label style="display: flex; align-items: center; gap: 8px; cursor: pointer;">
                        <input type="checkbox" id="taskMilestone">
                        <span class="form-label" style="margin: 0;">🎯 Milestone</span>
                    </label>
                    <div style="font-size: 12px; color: var(--text-secondary); margin-top: 4px;">Mark this as a key project milestone</div>
                </div>

                <div class="form-group">
                    <label class="form-label">Dependencies (Task IDs, comma-separated)</label>
                    <input type="text" class="form-input" id="taskDependencies" placeholder="e.g., 12345, 67890">
                    <div style="font-size: 12px; color: var(--text-secondary); margin-top: 4px;">Tasks that must be completed before this one</div>
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
    
    <div class="modal" id="detailModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="modal-title" id="detailModalTitle"></h2>
                <div class="header-actions">
                    <button class="icon-btn" onclick="openEditFromDetail()">✏️</button>
                    <button class="close-btn" onclick="closeDetailModal()">×</button>
                </div>
            </div>
            <div id="detailContent"></div>
            <div style="margin-top: var(--spacing-lg);">
                <button class="btn btn-primary" style="width: 100%;" onclick="closeDetailModal()">Got It</button>
            </div>
        </div>
    </div>

    <div class="modal" id="settingsModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="modal-title">⚙️ Settings</h2>
                <button class="close-btn" onclick="closeSettingsModal()">×</button>
            </div>

            <div style="padding: var(--spacing-md) 0;">
                <!-- Theme Settings -->
                <div style="margin-bottom: var(--spacing-lg);">
                    <h3 style="font-size: 16px; font-weight: 600; margin-bottom: var(--spacing-md); color: var(--text-primary);">🎨 Appearance</h3>
                    <div class="form-group">
                        <label class="form-label">Theme</label>
                        <div style="display: flex; gap: var(--spacing-sm);">
                            <button class="btn btn-secondary" onclick="setTheme('light')" id="lightThemeBtn" style="flex: 1;">☀️ Light</button>
                            <button class="btn btn-secondary" onclick="setTheme('dark')" id="darkThemeBtn" style="flex: 1;">🌙 Dark</button>
                        </div>
                    </div>
                </div>

                <!-- Data Management -->
                <div style="margin-bottom: var(--spacing-lg);">
                    <h3 style="font-size: 16px; font-weight: 600; margin-bottom: var(--spacing-md); color: var(--text-primary);">💾 Data Management</h3>

                    <div class="form-group">
                        <label class="form-label">Export/Import</label>
                        <div style="display: flex; gap: var(--spacing-sm); flex-direction: column;">
                            <button class="btn btn-secondary" onclick="exportData()" style="width: 100%;">
                                <span>📥</span><span>Export All Tasks</span>
                            </button>
                            <label class="btn btn-secondary" style="width: 100%; cursor: pointer; margin: 0;">
                                <span>📤</span><span>Import Tasks</span>
                                <input type="file" id="importFile" accept=".json" style="display: none;" onchange="importData(event)">
                            </label>
                        </div>
                    </div>

                    <div class="form-group">
                        <button class="btn" onclick="clearAllTasks()" style="width: 100%; background: var(--error); color: white;">
                            <span>🗑️</span><span>Clear All Tasks</span>
                        </button>
                    </div>
                </div>

                <!-- About -->
                <div>
                    <h3 style="font-size: 16px; font-weight: 600; margin-bottom: var(--spacing-md); color: var(--text-primary);">ℹ️ About</h3>
                    <div style="padding: var(--spacing-md); background: var(--bg-tertiary); border-radius: var(--radius-md); font-size: 14px; color: var(--text-secondary);">
                        <div style="margin-bottom: var(--spacing-sm);"><strong>Personal Calendar & Task Planner</strong></div>
                        <div>Version 2.0</div>
                        <div style="margin-top: var(--spacing-sm);">
                            Features: Tasks, Calendar, Kanban Board, Gantt Chart, Statistics
                        </div>
                    </div>
                </div>
            </div>
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
        let currentCalendarMode = 'daily';
        let currentDetailTaskId = null;
        let draggedTaskId = null;

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
            document.getElementById('menuBtn').addEventListener('click', openSettingsModal);
            document.getElementById('taskForm').addEventListener('submit', handleTaskSubmit);

            document.getElementById('tagInput').addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    e.preventDefault();
                    addTag();
                }
            });

            // Focus tag input when clicking container (but not on tags themselves)
            document.getElementById('tagContainer').addEventListener('click', (e) => {
                if (e.target.id === 'tagContainer' || e.target.classList.contains('tag-input')) {
                    document.getElementById('tagInput').focus();
                }
            });

            document.getElementById('taskModal').addEventListener('click', (e) => {
                if (e.target.id === 'taskModal') closeTaskModal();
            });

            document.getElementById('syncModal').addEventListener('click', (e) => {
                if (e.target.id === 'syncModal') closeSyncModal();
            });
            
            document.getElementById('detailModal').addEventListener('click', (e) => {
                if (e.target.id === 'detailModal') closeDetailModal();
            });

            document.getElementById('settingsModal').addEventListener('click', (e) => {
                if (e.target.id === 'settingsModal') closeSettingsModal();
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
                case 'gantt':
                    renderGantt();
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

        function createTaskCard(task, isBoard = false) {
            const isCompleted = task.status === 'done';
            const todayStr = new Date().toISOString().split('T')[0];
            const isDueToday = task.dueDate === todayStr && !isCompleted;
            
            let isUrgentOrOverdue = false;
            if (task.dueDate && !isCompleted) {
                // Compare date strings to avoid timezone issues
                if (task.dueDate < todayStr) {
                    isUrgentOrOverdue = true;
                }
            }

            let statusClass = '';
            if (isBoard && !isCompleted) {
                if (isUrgentOrOverdue && !isDueToday) {
                     statusClass = 'urgent-overdue'; 
                } else if (isDueToday) {
                     statusClass = 'due-today';
                }
            }
            
            const draggableAttr = isBoard && !isCompleted ? 'draggable="true"' : '';

            // Determine checkbox state based on task status
            let checkboxClass = '';
            let checkboxContent = '';
            if (task.status === 'done') {
                checkboxClass = 'checked';
                checkboxContent = '';
            } else if (task.status === 'in-progress') {
                checkboxClass = 'in-progress';
                checkboxContent = '<div style="width: 8px; height: 2px; background: var(--primary); border-radius: 1px;"></div>';
            } else {
                checkboxClass = '';
                checkboxContent = '';
            }

            return `
                <div class="task-card priority-${task.priority} ${isCompleted ? 'completed' : ''} ${statusClass}"
                     data-id="${task.id}"
                     ${draggableAttr}>
                    <div class="task-header">
                        <div class="task-checkbox ${checkboxClass}"
                             data-id="${task.id}"
                             onclick="event.stopPropagation(); toggleTaskStatus(${task.id});"
                             title="Click to cycle status: Not Started → In Progress → Done">${checkboxContent}</div>
                        <div class="task-content">
                            <div class="task-title">${task.title}</div>
                            <div class="task-meta">
                                <span class="badge badge-category" style="background: linear-gradient(135deg, var(--${task.category}), var(--primary-light));">
                                    ${getCategoryIcon(task.category)} ${task.category}
                                </span>
                                ${task.startTime && task.endTime && !isBoard ? `<span class="badge badge-time">⏰ ${formatTime(task.startTime)} - ${formatTime(task.endTime)}</span>` : ''}
                                ${task.duration && !isBoard ? `<span class="badge badge-duration">⏱️ ${task.duration}m</span>` : ''}
                                ${isUrgentOrOverdue ? `<span class="badge badge-urgent" style="background: var(--error); color: white;">🔥 Urgent</span>` : ''}
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
            const filteredTasks = filterTasks();

            let contentHtml = '';

            const navHtml = `
                <div class="calendar-nav">
                    <button class="calendar-nav-btn ${currentCalendarMode === 'daily' ? 'active' : ''}" 
                        onclick="setCalendarMode('daily')">Daily Timeline</button>
                    <button class="calendar-nav-btn ${currentCalendarMode === 'weekly' ? 'active' : ''}" 
                        onclick="setCalendarMode('weekly')">Weekly Grid</button>
                    <button class="calendar-nav-btn ${currentCalendarMode === 'monthly' ? 'active' : ''}" 
                        onclick="setCalendarMode('monthly')">Monthly View</button>
                </div>
            `;

            switch (currentCalendarMode) {
                case 'daily':
                    contentHtml = `
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
                    break;
                case 'weekly':
                    contentHtml = renderWeeklyView(filteredTasks, today);
                    break;
                case 'monthly':
                    contentHtml = renderMonthlyView(filteredTasks, today);
                    break;
            }

            container.innerHTML = navHtml + contentHtml;
            attachTaskListeners();
        }

        function setCalendarMode(mode) {
            currentCalendarMode = mode;
            render();
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

            // Process tasks to detect overlaps
            const processedTasks = todayTasks.map(task => {
                const [startHours, startMins] = task.startTime.split(':').map(Number);
                const [endHours, endMins] = task.endTime.split(':').map(Number);
                
                const startMinutes = startHours * 60 + startMins;
                const endMinutes = endHours * 60 + endMins;
                const duration = endMinutes - startMinutes;
                
                return {
                    ...task,
                    startMinutes,
                    endMinutes,
                    duration
                };
            });

            // Sort by start time, then by duration (longer first)
            processedTasks.sort((a, b) => {
                if (a.startMinutes !== b.startMinutes) {
                    return a.startMinutes - b.startMinutes;
                }
                return b.duration - a.duration; // Longer tasks first
            });

            // Detect overlaps and assign columns
            const columns = [];
            processedTasks.forEach(task => {
                // Find a column where this task doesn't overlap
                let columnIndex = 0;
                let placed = false;
                
                while (!placed) {
                    if (!columns[columnIndex]) {
                        columns[columnIndex] = [];
                    }
                    
                    // Check if this task overlaps with any task in this column
                    const hasOverlap = columns[columnIndex].some(existingTask => {
                        return !(task.endMinutes <= existingTask.startMinutes || 
                                task.startMinutes >= existingTask.endMinutes);
                    });
                    
                    if (!hasOverlap) {
                        columns[columnIndex].push(task);
                        task.column = columnIndex;
                        placed = true;
                    } else {
                        columnIndex++;
                    }
                }
            });

            const totalColumns = columns.length;
            const categoryColors = {
                work: 'var(--work)', school: 'var(--school)', personal: 'var(--personal)',
                health: 'var(--health)', finance: 'var(--finance)'
            };

            let tasksHtml = '';
            processedTasks.forEach(task => {
                const topOffset = ((task.startMinutes - (6 * 60)) / 60) * 60;
                const height = (task.duration / 60) * 60;
                
                // Calculate width and left offset based on column
                const widthPercent = totalColumns > 1 ? (100 / totalColumns) : 100;
                const leftPercent = totalColumns > 1 ? (task.column * widthPercent) : 0;

                tasksHtml += `
                    <div class="timeline-task" 
                         style="top: ${topOffset}px; 
                                height: ${height}px; 
                                left: calc(var(--spacing-sm) + ${leftPercent}%);
                                width: calc(${widthPercent}% - var(--spacing-sm));
                                background: ${categoryColors[task.category] || 'var(--primary)'};"
                         onclick="openDetailModal(${task.id})">
                        <div class="timeline-task-title">${task.title}</div>
                        <div class="timeline-task-time">${formatTime(task.startTime)} - ${formatTime(task.endTime)}</div>
                    </div>
                `;
            });

            const showNowLine = currentMinutes >= (6 * 60) && currentMinutes <= (23 * 60);

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
                        ${showNowLine ? `<div class="timeline-now" style="top: ${nowOffset}px;"></div>` : ''}
                    </div>
                </div>
            `;
        }

        function renderWeeklyView(filteredTasks, today) {
            const startOfWeek = getStartOfWeek(today);
            const todayStr = today.toISOString().split('T')[0];
            let weeklyHtml = '<div class="weekly-grid">';

            const categoryColors = {
                work: 'var(--work)', school: 'var(--school)', personal: 'var(--personal)',
                health: 'var(--health)', finance: 'var(--finance)'
            };

            for (let i = 0; i < 7; i++) {
                const day = new Date(startOfWeek);
                day.setDate(startOfWeek.getDate() + i);
                const dayStr = day.toISOString().split('T')[0];
                const isToday = dayStr === todayStr;

                const dayTasks = filteredTasks.filter(t => t.dueDate === dayStr && t.status !== 'done');
                const dayName = day.toLocaleDateString('en-US', { weekday: 'short' });
                const dayDate = day.toLocaleDateString('en-US', { month: 'numeric', day: 'numeric' });

                let taskHtml = dayTasks.map(task => `
                    <div class="calendar-task" 
                         style="border-left-color: ${categoryColors[task.category] || 'var(--primary)'}; background: var(--bg-tertiary);"
                         onclick="openDetailModal(${task.id})">
                        ${task.title}
                    </div>
                `).join('');
                
                if (dayTasks.length === 0) {
                    taskHtml = `<div class="empty-state" style="padding: 10px; font-size: 12px; height: auto; min-height: 40px;">No tasks</div>`;
                }

                weeklyHtml += `
                    <div class="weekly-day-container">
                        <div class="weekly-day-header" style="${isToday ? 'color: var(--primary);' : ''}">
                            ${dayName} ${dayDate}
                        </div>
                        <div style="padding: 8px;">
                            ${taskHtml}
                        </div>
                    </div>
                `;
            }

            weeklyHtml += '</div>';
            return weeklyHtml;
        }
        
        function renderMonthlyView(filteredTasks, today) {
            const year = today.getFullYear();
            const month = today.getMonth();
            const todayStr = today.toISOString().split('T')[0];

            const firstDayOfMonth = new Date(year, month, 1);
            const startDay = new Date(firstDayOfMonth);
            startDay.setDate(firstDayOfMonth.getDate() - firstDayOfMonth.getDay());

            let monthlyHtml = `
                <div style="text-align: center; font-size: 20px; font-weight: 700; margin-bottom: var(--spacing-md);">
                    ${today.toLocaleDateString('en-US', { month: 'long', year: 'numeric' })}
                </div>
                <div class="monthly-grid">
                    <div class="weekly-day-header">Sun</div>
                    <div class="weekly-day-header">Mon</div>
                    <div class="weekly-day-header">Tue</div>
                    <div class="weekly-day-header">Wed</div>
                    <div class="weekly-day-header">Thu</div>
                    <div class="weekly-day-header">Fri</div>
                    <div class="weekly-day-header">Sat</div>
            `;

            const categoryColors = {
                work: 'var(--work)', school: 'var(--school)', personal: 'var(--personal)',
                health: 'var(--health)', finance: 'var(--finance)'
            };
            
            let currentDay = new Date(startDay);
            for (let i = 0; i < 42; i++) {
                const dayStr = currentDay.toISOString().split('T')[0];
                const isCurrentMonth = currentDay.getMonth() === month;
                const isToday = dayStr === todayStr;

                const dayTasks = filteredTasks.filter(t => t.dueDate === dayStr && t.status !== 'done');
                
                let taskBadges = dayTasks.map(task => `
                    <span class="monthly-task-badge" 
                          style="background: ${categoryColors[task.category] || 'var(--primary)'};"
                          title="${task.title}"
                          onclick="openDetailModal(${task.id})">
                        ${task.title}
                    </span>
                `).slice(0, 3).join('');

                monthlyHtml += `
                    <div class="monthly-day-container ${isToday ? 'today' : ''}" 
                         style="opacity: ${isCurrentMonth ? 1 : 0.5};">
                        <span class="monthly-date">${currentDay.getDate()}</span>
                        ${taskBadges}
                        ${dayTasks.length > 3 ? `<span class="monthly-task-badge" style="background: var(--text-tertiary);">+${dayTasks.length - 3} more</span>` : ''}
                    </div>
                `;

                currentDay.setDate(currentDay.getDate() + 1);
            }

            monthlyHtml += '</div>';
            return monthlyHtml;
        }

        function getStartOfWeek(date) {
            const d = new Date(date);
            const day = d.getDay();
            const diff = d.getDate() - day;
            d.setDate(diff);
            d.setHours(0, 0, 0, 0);
            return d;
        }

        function renderBoard() {
            const container = document.getElementById('contentArea');
            const filteredTasks = filterTasks();
            
            const notStarted = filteredTasks.filter(t => t.status === 'not-started' || !t.status);
            const inProgress = filteredTasks.filter(t => t.status === 'in-progress');
            const done = filteredTasks.filter(t => t.status === 'done');

            container.innerHTML = `
                <div class="board-container">
                    ${createBoardColumn('To Do', notStarted, 'not-started')}
                    ${createBoardColumn('In Progress', inProgress, 'in-progress')}
                    ${createBoardColumn('Done', done, 'done')}
                </div>
            `;
            
            attachTaskListeners();
            attachBoardDragListeners();
        }

        function createBoardColumn(title, tasks, status) {
            return `
                <div class="board-column" data-status="${status}">
                    <div class="board-column-header">
                        <span>${title}</span>
                        <span class="section-count">${tasks.length}</span>
                    </div>
                    <div class="board-tasks" id="board-tasks-${status}">
                        ${tasks.map(task => createTaskCard(task, true)).join('')}
                    </div>
                </div>
            `;
        }

        function attachBoardDragListeners() {
            const columns = document.querySelectorAll('.board-column');
            
            columns.forEach(column => {
                column.addEventListener('dragover', handleDragOver);
                column.addEventListener('dragleave', handleDragLeave);
                column.addEventListener('drop', handleDrop);
            });

            const draggableCards = document.querySelectorAll('.task-card[draggable="true"]');
            draggableCards.forEach(card => {
                card.addEventListener('dragstart', handleDragStart);
                card.addEventListener('dragend', handleDragEnd);
            });
        }

        function handleDragStart(e) {
            draggedTaskId = parseInt(e.target.dataset.id);
            e.target.classList.add('dragging');
            e.dataTransfer.effectAllowed = 'move';
            e.dataTransfer.setData('text/html', e.target.innerHTML);
        }

        function handleDragEnd(e) {
            e.target.classList.remove('dragging');
        }

        function handleDragOver(e) {
            e.preventDefault();
            e.dataTransfer.dropEffect = 'move';
            
            const column = e.currentTarget;
            if (column.classList.contains('board-column')) {
                column.classList.add('drag-over');
            }
        }

        function handleDragLeave(e) {
            const column = e.currentTarget;
            if (column.classList.contains('board-column')) {
                column.classList.remove('drag-over');
            }
        }

        function handleDrop(e) {
            e.preventDefault();
            e.stopPropagation();
            
            const column = e.currentTarget;
            column.classList.remove('drag-over');
            
            if (!draggedTaskId) return;
            
            const newStatus = column.dataset.status;
            const taskIndex = tasks.findIndex(t => t.id === draggedTaskId);
            
            if (taskIndex !== -1 && tasks[taskIndex].status !== newStatus) {
                tasks[taskIndex].status = newStatus;
                saveData();
                render();
            }
            
            draggedTaskId = null;
        }

        let ganttViewMode = 'week'; // 'day', 'week', or 'month'

        function renderGantt() {
            const container = document.getElementById('contentArea');
            const filteredTasks = filterTasks().filter(t => t.dueDate);

            if (filteredTasks.length === 0) {
                container.innerHTML = `
                    <div class="gantt-container">
                        <div class="gantt-header">
                            <h3 style="font-size: 20px; font-weight: 700;">📊 Gantt Chart</h3>
                            <div style="font-size: 14px; color: var(--text-secondary);">
                                Project Timeline Visualization
                            </div>
                        </div>
                        <div class="gantt-empty-state">
                            <div style="font-size: 48px; margin-bottom: var(--spacing-md);">📅</div>
                            <div style="font-size: 18px; font-weight: 600; color: var(--text-primary); margin-bottom: var(--spacing-sm);">
                                No Tasks with Due Dates
                            </div>
                            <div style="font-size: 14px;">
                                Add tasks with due dates to see them in the Gantt chart timeline.
                            </div>
                        </div>
                    </div>
                `;
                return;
            }

            // Calculate date range
            const { startDate, endDate, dates } = calculateGanttDateRange(filteredTasks);

            // Group tasks by project or category
            const groupedTasks = groupTasksForGantt(filteredTasks);

            // Build header
            let headerHTML = '<div class="gantt-timeline-header"><div class="gantt-timeline-date" style="min-width: 200px; border-right: 2px solid var(--border);"></div>';
            const todayStr = new Date().toISOString().split('T')[0];

            dates.forEach(date => {
                const isToday = date === todayStr;
                const dateObj = new Date(date);
                const label = formatGanttDate(dateObj, ganttViewMode);
                headerHTML += `<div class="gantt-timeline-date ${isToday ? 'today' : ''}">${label}</div>`;
            });
            headerHTML += '</div>';

            // Build rows
            let rowsHTML = '<div class="gantt-rows">';

            for (const [groupName, groupTasks] of Object.entries(groupedTasks)) {
                groupTasks.forEach(task => {
                    const rowHTML = renderGanttRow(task, groupName, dates, startDate);
                    rowsHTML += rowHTML;
                });
            }

            rowsHTML += '</div>';

            // Build controls
            const controlsHTML = `
                <div class="gantt-controls">
                    <button class="gantt-control-btn ${ganttViewMode === 'day' ? 'active' : ''}" onclick="setGanttViewMode('day')">Day</button>
                    <button class="gantt-control-btn ${ganttViewMode === 'week' ? 'active' : ''}" onclick="setGanttViewMode('week')">Week</button>
                    <button class="gantt-control-btn ${ganttViewMode === 'month' ? 'active' : ''}" onclick="setGanttViewMode('month')">Month</button>
                </div>
            `;

            container.innerHTML = `
                <div class="gantt-container">
                    <div class="gantt-header">
                        <h3 style="font-size: 20px; font-weight: 700;">📊 Gantt Chart</h3>
                        <div style="font-size: 14px; color: var(--text-secondary);">
                            Project Timeline Visualization
                        </div>
                    </div>
                    ${controlsHTML}
                    <div class="gantt-timeline">
                        ${headerHTML}
                        ${rowsHTML}
                    </div>
                </div>
            `;

            attachGanttListeners();
        }

        function calculateGanttDateRange(tasks) {
            const today = new Date();
            today.setHours(0, 0, 0, 0);

            let minDate = new Date(today);
            let maxDate = new Date(today);

            // Find min and max dates from tasks
            tasks.forEach(task => {
                if (task.dueDate) {
                    const taskDate = new Date(task.dueDate);
                    if (taskDate < minDate) minDate = taskDate;
                    if (taskDate > maxDate) maxDate = taskDate;
                }
            });

            // Expand range based on view mode
            if (ganttViewMode === 'day') {
                // Show 2 weeks
                minDate = new Date(today);
                minDate.setDate(minDate.getDate() - 3);
                maxDate = new Date(today);
                maxDate.setDate(maxDate.getDate() + 11);
            } else if (ganttViewMode === 'week') {
                // Show 8 weeks
                minDate = new Date(today);
                minDate.setDate(minDate.getDate() - 7);
                maxDate = new Date(today);
                maxDate.setDate(maxDate.getDate() + 49);
            } else {
                // Month view - show 6 months
                minDate = new Date(today);
                minDate.setMonth(minDate.getMonth() - 1);
                maxDate = new Date(today);
                maxDate.setMonth(maxDate.getMonth() + 5);
            }

            // Generate date array
            const dates = [];
            const currentDate = new Date(minDate);

            if (ganttViewMode === 'day') {
                while (currentDate <= maxDate) {
                    dates.push(currentDate.toISOString().split('T')[0]);
                    currentDate.setDate(currentDate.getDate() + 1);
                }
            } else if (ganttViewMode === 'week') {
                // Start from Monday of the week
                currentDate.setDate(currentDate.getDate() - currentDate.getDay() + 1);
                while (currentDate <= maxDate) {
                    dates.push(currentDate.toISOString().split('T')[0]);
                    currentDate.setDate(currentDate.getDate() + 7);
                }
            } else {
                // Month view
                currentDate.setDate(1);
                while (currentDate <= maxDate) {
                    dates.push(currentDate.toISOString().split('T')[0]);
                    currentDate.setMonth(currentDate.getMonth() + 1);
                }
            }

            return { startDate: minDate, endDate: maxDate, dates };
        }

        function groupTasksForGantt(tasks) {
            const grouped = {};

            tasks.forEach(task => {
                const groupKey = task.project || task.category || 'Other';
                if (!grouped[groupKey]) {
                    grouped[groupKey] = [];
                }
                grouped[groupKey].push(task);
            });

            // Sort tasks within each group by due date
            for (const key in grouped) {
                grouped[key].sort((a, b) => new Date(a.dueDate) - new Date(b.dueDate));
            }

            return grouped;
        }

        function formatGanttDate(date, mode) {
            const options = { month: 'short', day: 'numeric' };

            if (mode === 'day') {
                return date.toLocaleDateString('en-US', { month: 'short', day: 'numeric', weekday: 'short' });
            } else if (mode === 'week') {
                const weekEnd = new Date(date);
                weekEnd.setDate(weekEnd.getDate() + 6);
                return `${date.toLocaleDateString('en-US', { month: 'short', day: 'numeric' })} - ${weekEnd.toLocaleDateString('en-US', { month: 'short', day: 'numeric' })}`;
            } else {
                return date.toLocaleDateString('en-US', { month: 'long', year: 'numeric' });
            }
        }

        function renderGanttRow(task, groupName, dates, startDate) {
            const taskDate = new Date(task.dueDate);

            // Calculate position and width
            let cellIndex = -1;
            let barWidth = 100; // default width for single cell

            if (ganttViewMode === 'day') {
                cellIndex = dates.findIndex(d => d === task.dueDate);
            } else if (ganttViewMode === 'week') {
                cellIndex = dates.findIndex(weekStart => {
                    const weekEnd = new Date(weekStart);
                    weekEnd.setDate(weekEnd.getDate() + 6);
                    return taskDate >= new Date(weekStart) && taskDate <= weekEnd;
                });
            } else {
                cellIndex = dates.findIndex(monthStart => {
                    const monthEnd = new Date(monthStart);
                    monthEnd.setMonth(monthEnd.getMonth() + 1);
                    monthEnd.setDate(monthEnd.getDate() - 1);
                    return taskDate >= new Date(monthStart) && taskDate <= monthEnd;
                });
            }

            if (cellIndex === -1) return '';

            // Calculate progress from subtasks
            let progress = 0;
            if (task.subtasks && task.subtasks.length > 0) {
                const completed = task.subtasks.filter(s => s.completed).length;
                progress = Math.round((completed / task.subtasks.length) * 100);
            } else if (task.status === 'done') {
                progress = 100;
            } else if (task.status === 'in-progress') {
                progress = 50;
            }

            // Check if task is on critical path
            const isCriticalPath = isTaskOnCriticalPath(task);

            // Build timeline cells
            let timelineCells = '';
            const todayStr = new Date().toISOString().split('T')[0];

            dates.forEach((date, idx) => {
                const isToday = ganttViewMode === 'day' && date === todayStr;
                let cellContent = '';

                if (idx === cellIndex) {
                    if (task.milestone) {
                        // Render milestone marker
                        cellContent = `
                            <div class="gantt-milestone"
                                 style="left: 50%; margin-left: -12px;"
                                 data-task-id="${task.id}">
                                <div class="gantt-milestone-label">${task.title}</div>
                            </div>
                        `;
                    } else {
                        // Render task bar
                        const statusClass = task.status === 'done' ? 'status-done' : '';
                        const criticalClass = isCriticalPath ? 'critical-path' : '';
                        cellContent = `
                            <div class="gantt-task-bar priority-${task.priority} ${statusClass} ${criticalClass}"
                                 style="width: ${barWidth}%; left: 0;"
                                 data-task-id="${task.id}"
                                 data-cell-index="${cellIndex}"
                                 draggable="true">
                                ${progress > 0 ? `<div class="gantt-task-progress" style="width: ${progress}%;"></div>` : ''}
                                ${task.title}
                            </div>
                        `;
                    }
                }

                timelineCells += `<div class="gantt-timeline-cell ${isToday ? 'today' : ''}">${cellContent}</div>`;
            });

            const categoryIcon = getCategoryIcon(task.category);

            return `
                <div class="gantt-row" data-task-id="${task.id}">
                    <div class="gantt-row-label">
                        <div class="gantt-row-title">${task.title}${task.milestone ? ' 🎯' : ''}</div>
                        <div class="gantt-row-subtitle">${categoryIcon} ${groupName}${progress > 0 && !task.milestone ? ` • ${progress}%` : ''}</div>
                    </div>
                    <div class="gantt-row-timeline">
                        ${timelineCells}
                    </div>
                </div>
            `;
        }

        function isTaskOnCriticalPath(task) {
            // A task is on the critical path if:
            // 1. It has dependencies and any of them are not complete
            // 2. Other tasks depend on it
            if (!task.dependencies || task.dependencies.length === 0) {
                return false;
            }

            const hasIncompleteDeps = task.dependencies.some(depId => {
                const depTask = tasks.find(t => t.id === depId);
                return depTask && depTask.status !== 'done';
            });

            const othersDependOnThis = tasks.some(t =>
                t.dependencies && t.dependencies.includes(task.id)
            );

            return hasIncompleteDeps || othersDependOnThis;
        }

        function setGanttViewMode(mode) {
            ganttViewMode = mode;
            renderGantt();
        }

        let draggedTaskElement = null;
        let draggedTask = null;

        function attachGanttListeners() {
            // Click events for task bars and milestones
            const taskBars = document.querySelectorAll('.gantt-task-bar, .gantt-milestone');
            taskBars.forEach(bar => {
                bar.addEventListener('click', (e) => {
                    e.stopPropagation();
                    const taskId = parseInt(e.currentTarget.dataset.taskId);
                    editTask(taskId);
                });
            });

            // Drag and drop for task bars
            const draggableBars = document.querySelectorAll('.gantt-task-bar[draggable="true"]');
            draggableBars.forEach(bar => {
                bar.addEventListener('dragstart', handleGanttDragStart);
                bar.addEventListener('dragend', handleGanttDragEnd);
            });

            // Drop zones for timeline cells
            const cells = document.querySelectorAll('.gantt-timeline-cell');
            cells.forEach(cell => {
                cell.addEventListener('dragover', handleGanttDragOver);
                cell.addEventListener('drop', handleGanttDrop);
            });

            // Render dependency lines
            renderDependencyLines();
        }

        function handleGanttDragStart(e) {
            draggedTaskElement = e.target;
            const taskId = parseInt(e.target.dataset.taskId);
            draggedTask = tasks.find(t => t.id === taskId);

            e.target.classList.add('dragging');
            e.dataTransfer.effectAllowed = 'move';
            e.dataTransfer.setData('text/html', e.target.innerHTML);
        }

        function handleGanttDragEnd(e) {
            e.target.classList.remove('dragging');
            draggedTaskElement = null;
            draggedTask = null;
        }

        function handleGanttDragOver(e) {
            if (e.preventDefault) {
                e.preventDefault();
            }
            e.dataTransfer.dropEffect = 'move';
            return false;
        }

        function handleGanttDrop(e) {
            if (e.stopPropagation) {
                e.stopPropagation();
            }
            e.preventDefault();

            if (!draggedTask) return false;

            // Find which row and cell this is
            const cell = e.currentTarget;
            const row = cell.closest('.gantt-row');
            const rowTaskId = parseInt(row.dataset.taskId);

            // Only allow dropping in the same row
            if (rowTaskId !== draggedTask.id) return false;

            // Find the date for this cell
            const allCells = Array.from(row.querySelectorAll('.gantt-timeline-cell'));
            const cellIndex = allCells.indexOf(cell);

            // Calculate the date range for Gantt view
            const filteredTasks = filterTasks().filter(t => t.dueDate);
            const { dates } = calculateGanttDateRange(filteredTasks);

            if (cellIndex >= 0 && cellIndex < dates.length) {
                const newDate = dates[cellIndex];

                // Update task due date
                const taskIndex = tasks.findIndex(t => t.id === draggedTask.id);
                if (taskIndex !== -1) {
                    tasks[taskIndex].dueDate = newDate;
                    saveData();
                    renderGantt();
                }
            }

            return false;
        }

        function renderDependencyLines() {
            // Remove existing dependency lines
            document.querySelectorAll('.gantt-dependency-line').forEach(el => el.remove());

            const filteredTasks = filterTasks().filter(t => t.dueDate);

            filteredTasks.forEach(task => {
                if (!task.dependencies || task.dependencies.length === 0) return;

                task.dependencies.forEach(depId => {
                    const depTask = tasks.find(t => t.id === depId);
                    if (!depTask || !depTask.dueDate) return;

                    // Find the DOM elements for both tasks
                    const taskRow = document.querySelector(`.gantt-row[data-task-id="${task.id}"]`);
                    const depRow = document.querySelector(`.gantt-row[data-task-id="${depId}"]`);

                    if (!taskRow || !depRow) return;

                    const taskBar = taskRow.querySelector('.gantt-task-bar, .gantt-milestone');
                    const depBar = depRow.querySelector('.gantt-task-bar, .gantt-milestone');

                    if (!taskBar || !depBar) return;

                    // Calculate positions
                    const taskRect = taskBar.getBoundingClientRect();
                    const depRect = depBar.getBoundingClientRect();
                    const container = document.querySelector('.gantt-timeline');
                    const containerRect = container.getBoundingClientRect();

                    // Create line element
                    const line = document.createElement('div');
                    line.className = 'gantt-dependency-line';

                    const x1 = depRect.right - containerRect.left;
                    const y1 = depRect.top - containerRect.top + depRect.height / 2;
                    const x2 = taskRect.left - containerRect.left;
                    const y2 = taskRect.top - containerRect.top + taskRect.height / 2;

                    const length = Math.sqrt(Math.pow(x2 - x1, 2) + Math.pow(y2 - y1, 2));
                    const angle = Math.atan2(y2 - y1, x2 - x1) * 180 / Math.PI;

                    line.style.width = `${length}px`;
                    line.style.left = `${x1}px`;
                    line.style.top = `${y1}px`;
                    line.style.transform = `rotate(${angle}deg)`;
                    line.style.transformOrigin = '0 0';

                    // Add arrow
                    const arrow = document.createElement('div');
                    arrow.className = 'gantt-dependency-arrow';
                    line.appendChild(arrow);

                    container.appendChild(line);
                });
            });
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
                        <div class="stat-value" style="color: var(--error);">${urgent}</div>
                        <div class="stat-label">Urgent</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value" style="color: var(--success);">${completionRate}%</div>
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
                    <div style="margin-bottom: var(--spacing-md); padding: var(--spacing-md); background: var(--bg-secondary); border-radius: var(--radius-md); box-shadow: 0 1px 4px var(--shadow);">
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
            document.querySelectorAll('.task-card').forEach(card => {
                const contentDiv = card.querySelector('.task-content');
                if (contentDiv) {
                    contentDiv.onclick = (e) => {
                        e.stopPropagation(); 
                        const taskId = parseInt(card.dataset.id);
                        openDetailModal(taskId);
                    };
                }
            });
        }

        function toggleTaskStatus(taskId) {
            const task = tasks.find(t => t.id === taskId);
            if (task) {
                // Cycle through: not-started → in-progress → done → not-started
                if (task.status === 'not-started') {
                    task.status = 'in-progress';
                } else if (task.status === 'in-progress') {
                    task.status = 'done';
                } else {
                    task.status = 'not-started';
                }
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
            document.getElementById('recurringFreq').classList.add('hidden');
            document.getElementById('taskModal').classList.add('active');
        }

        function editTask(taskId) {
            editingTaskId = taskId;
            const task = tasks.find(t => t.id === taskId);
            
            document.getElementById('modalTitle').textContent = 'Edit Task';
            document.getElementById('taskTitle').value = task.title || '';
            document.getElementById('taskCategory').value = task.category || 'personal';
            document.getElementById('taskPriority').value = task.priority || 'medium';
            document.getElementById('taskDate').value = task.dueDate || '';
            document.getElementById('taskTimeBlock').value = task.timeBlock || '';
            document.getElementById('taskStartTime').value = task.startTime || '';
            document.getElementById('taskEndTime').value = task.endTime || '';
            document.getElementById('taskDuration').value = task.duration || '';
            document.getElementById('taskProject').value = task.project || '';
            document.getElementById('taskNotes').value = task.notes || '';
            document.getElementById('taskRecurring').checked = task.recurring || false;
            document.getElementById('taskMilestone').checked = task.milestone || false;
            document.getElementById('taskDependencies').value = task.dependencies ? task.dependencies.join(', ') : '';

            if (task.recurring) {
                document.getElementById('recurringFreq').classList.remove('hidden');
                document.getElementById('recurringFreq').value = task.recurringFreq || 'daily';
            } else {
                 document.getElementById('recurringFreq').classList.add('hidden');
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
            if (task.subtasks && task.subtasks.length > 0) {
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

            const dependenciesInput = document.getElementById('taskDependencies').value.trim();
            const dependencies = dependenciesInput
                ? dependenciesInput.split(',').map(id => parseInt(id.trim())).filter(id => !isNaN(id))
                : [];

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
                milestone: document.getElementById('taskMilestone').checked,
                dependencies: dependencies,
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
        
        function openDetailModal(taskId) {
            const task = tasks.find(t => t.id === taskId);
            if (!task) return;
            
            currentDetailTaskId = taskId;
            document.getElementById('detailModalTitle').textContent = task.title;

            let html = `
                <div style="display: flex; flex-wrap: wrap; gap: var(--spacing-md); margin-bottom: var(--spacing-lg);">
                    ${renderDetailBadge('Category', task.category, 'var(--' + task.category + ')')}
                    ${renderDetailBadge('Priority', task.priority, getPriorityColor(task.priority))}
                    ${task.dueDate ? renderDetailBadge('Due Date', task.dueDate, 'var(--primary)') : ''}
                    ${task.project ? renderDetailBadge('Project', task.project, 'var(--info)') : ''}
                    ${task.startTime && task.endTime ? renderDetailBadge('Time Block', `${formatTime(task.startTime)} - ${formatTime(task.endTime)} (${task.duration}m)`, 'var(--warning)') : ''}
                    ${task.recurring ? renderDetailBadge('Recurring', task.recurringFreq, 'var(--success)') : ''}
                </div>
                
                ${task.notes ? `
                    <div class="form-group">
                        <label class="form-label">Notes</label>
                        <div class="form-input" style="min-height: 80px; background: var(--bg-tertiary);">${task.notes.replace(/\n/g, '<br>')}</div>
                    </div>
                ` : ''}

                ${task.subtasks && task.subtasks.length > 0 ? `
                    <div class="form-group">
                        <label class="form-label">Subtasks (${task.subtasks.filter(s => s.completed).length}/${task.subtasks.length})</label>
                        <ul style="list-style-type: none; padding: 0;">
                            ${task.subtasks.map((sub, index) => `
                                <li style="display: flex; align-items: center; gap: 10px; padding: 6px 0;">
                                    <input type="checkbox" ${sub.completed ? 'checked' : ''} onchange="toggleSubtask(${taskId}, ${index})">
                                    <span style="${sub.completed ? 'text-decoration: line-through; opacity: 0.6;' : ''}">${sub.text}</span>
                                </li>
                            `).join('')}
                        </ul>
                    </div>
                ` : ''}

                ${task.tags && task.tags.length > 0 ? `
                    <div class="form-group">
                        <label class="form-label">Tags</label>
                        <div class="tag-container" style="border: none; background: transparent; padding: 0;">
                            ${task.tags.map(tag => `<div class="tag-item" style="background: var(--text-tertiary);">${tag}</div>`).join('')}
                        </div>
                    </div>
                ` : ''}
            `;

            document.getElementById('detailContent').innerHTML = html;
            document.getElementById('detailModal').classList.add('active');
        }

        function closeDetailModal() {
            document.getElementById('detailModal').classList.remove('active');
            currentDetailTaskId = null;
        }

        function openEditFromDetail() {
            if (currentDetailTaskId) {
                const taskId = currentDetailTaskId;
                closeDetailModal();
                setTimeout(() => {
                    editTask(taskId);
                }, 100);
            }
        }

        function renderDetailBadge(label, value, color) {
            return `
                <div style="background: ${color}; color: white; padding: 8px 12px; border-radius: var(--radius-md); font-size: 13px; font-weight: 600;">
                    ${label}: ${value}
                </div>
            `;
        }

        function getPriorityColor(priority) {
            const colors = {
                high: 'var(--priority-high)',
                medium: 'var(--priority-medium)',
                low: 'var(--priority-low)'
            };
            return colors[priority] || 'var(--primary)';
        }

        function toggleSubtask(taskId, subtaskIndex) {
            const task = tasks.find(t => t.id === taskId);
            if (task && task.subtasks && task.subtasks[subtaskIndex]) {
                task.subtasks[subtaskIndex].completed = !task.subtasks[subtaskIndex].completed;
                saveData();
                openDetailModal(taskId);
            }
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

        function openSettingsModal() {
            document.getElementById('settingsModal').classList.add('active');
            updateThemeButtons();
        }

        function closeSettingsModal() {
            document.getElementById('settingsModal').classList.remove('active');
        }

        function updateThemeButtons() {
            const currentTheme = document.documentElement.getAttribute('data-theme');
            const lightBtn = document.getElementById('lightThemeBtn');
            const darkBtn = document.getElementById('darkThemeBtn');

            lightBtn.classList.remove('active');
            darkBtn.classList.remove('active');

            if (currentTheme === 'dark') {
                darkBtn.classList.add('active');
                darkBtn.style.background = 'var(--primary)';
                darkBtn.style.color = 'white';
                lightBtn.style.background = '';
                lightBtn.style.color = '';
            } else {
                lightBtn.classList.add('active');
                lightBtn.style.background = 'var(--primary)';
                lightBtn.style.color = 'white';
                darkBtn.style.background = '';
                darkBtn.style.color = '';
            }
        }

        function setTheme(theme) {
            document.documentElement.setAttribute('data-theme', theme);
            localStorage.setItem('theme', theme);
            updateThemeButtons();
        }

        function exportData() {
            const dataStr = JSON.stringify(tasks, null, 2);
            const dataBlob = new Blob([dataStr], { type: 'application/json' });
            const url = URL.createObjectURL(dataBlob);
            const link = document.createElement('a');
            link.href = url;
            link.download = `planner-tasks-${new Date().toISOString().split('T')[0]}.json`;
            link.click();
            URL.revokeObjectURL(url);
        }

        function importData(event) {
            const file = event.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = (e) => {
                try {
                    const importedTasks = JSON.parse(e.target.result);
                    if (Array.isArray(importedTasks)) {
                        if (confirm(`Import ${importedTasks.length} tasks? This will add to your existing tasks.`)) {
                            tasks = [...tasks, ...importedTasks];
                            saveData();
                            render();
                            closeSettingsModal();
                            alert('Tasks imported successfully!');
                        }
                    } else {
                        alert('Invalid file format. Please upload a valid task JSON file.');
                    }
                } catch (error) {
                    alert('Error reading file. Please make sure it\'s a valid JSON file.');
                }
            };
            reader.readAsText(file);
            event.target.value = ''; // Reset file input
        }

        function clearAllTasks() {
            if (confirm('Are you sure you want to delete ALL tasks? This action cannot be undone!')) {
                if (confirm('Really delete everything? This is your last chance!')) {
                    tasks = [];
                    saveData();
                    render();
                    closeSettingsModal();
                    alert('All tasks have been cleared.');
                }
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
                } else {
                    alert('Login failed. Invalid token.');
                }
            } catch (error) {
                alert('Could not reach API. Please check the network connection.');
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
                work: '💼', school: '🎓', personal: '✨', health: '🏃', finance: '💰'
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
