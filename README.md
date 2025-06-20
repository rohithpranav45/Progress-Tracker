<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rohith's Transformation Journey</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #6c5ce7;
            --primary-dark: #5649c5;
            --secondary: #00cec9;
            --accent: #fd79a8;
            --light: #f7f7ff;
            --dark: #2d3436;
            --success: #00b894;
            --warning: #fdcb6e;
            --danger: #e17055;
            --gray: #dfe6e9;
            --card-bg: rgba(255, 255, 255, 0.92);
            --gradient: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
            --border-radius: 16px;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            min-height: 100vh;
            padding: 20px;
            color: var(--dark);
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: var(--card-bg);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            overflow: hidden;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }
        
        .header {
            background: var(--gradient);
            color: white;
            padding: 30px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .header::before {
            content: "";
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0) 70%);
            transform: rotate(30deg);
        }
        
        .header-content {
            position: relative;
            z-index: 2;
        }
        
        .header h1 {
            font-size: 2.8rem;
            margin-bottom: 12px;
            font-weight: 800;
            letter-spacing: -0.5px;
        }
        
        .header p {
            font-size: 1.1rem;
            max-width: 600px;
            margin: 0 auto 25px;
            opacity: 0.9;
        }
        
        .date-display {
            background: rgba(0, 0, 0, 0.15);
            padding: 12px 20px;
            border-radius: 50px;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 25px;
            font-size: 1.1rem;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .progress-overview {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        
        .progress-card {
            background: rgba(255,255,255,0.15);
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: transform 0.3s ease;
        }
        
        .progress-card:hover {
            transform: translateY(-5px);
        }
        
        .progress-card h3 {
            margin-bottom: 15px;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        
        .progress-bar {
            background: rgba(255,255,255,0.3);
            border-radius: 10px;
            height: 12px;
            overflow: hidden;
            margin: 15px 0;
        }
        
        .progress-fill {
            height: 100%;
            background: var(--success);
            transition: width 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
            box-shadow: 0 0 10px rgba(0, 184, 148, 0.3);
        }
        
        .main-content {
            padding: 30px;
        }
        
        .tabs {
            display: flex;
            background: #f1f2f6;
            border-radius: 12px;
            padding: 6px;
            margin-bottom: 30px;
            overflow-x: auto;
            gap: 5px;
        }
        
        .tab {
            padding: 14px 25px;
            border: none;
            background: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 16px;
            transition: all 0.3s ease;
            white-space: nowrap;
            font-weight: 600;
            color: var(--dark);
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .tab:hover {
            background: rgba(108, 92, 231, 0.1);
        }
        
        .tab.active {
            background: var(--primary);
            color: white;
            box-shadow: 0 4px 10px rgba(108, 92, 231, 0.3);
        }
        
        .tab-content {
            display: none;
            animation: fadeIn 0.4s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .tab-content.active {
            display: block;
        }
        
        .schedule-grid {
            display: grid;
            grid-template-columns: 90px 1fr;
            gap: 12px;
            margin: 20px 0;
        }
        
        .time-slot {
            background: var(--primary);
            color: white;
            padding: 15px 10px;
            border-radius: 12px;
            text-align: center;
            font-weight: 700;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.1rem;
            box-shadow: 0 4px 10px rgba(108, 92, 231, 0.2);
        }
        
        .activity {
            background: white;
            padding: 20px;
            border-radius: 12px;
            border-left: 5px solid var(--primary);
            position: relative;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease;
        }
        
        .activity:hover {
            transform: translateX(5px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.08);
        }
        
        .activity h4 {
            color: var(--dark);
            margin-bottom: 10px;
            font-size: 1.2rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .activity p {
            color: #666;
            font-size: 0.95rem;
            margin-bottom: 5px;
            line-height: 1.5;
        }
        
        .activity-tags {
            display: flex;
            gap: 8px;
            margin-top: 15px;
            flex-wrap: wrap;
        }
        
        .tag {
            background: #e3f2fd;
            color: #1976d2;
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
        }
        
        .checklist-section {
            background: white;
            border-radius: var(--border-radius);
            padding: 25px;
            margin: 25px 0;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }
        
        .checklist-section::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 5px;
            height: 100%;
            background: var(--primary);
        }
        
        .checklist-section h3 {
            color: var(--dark);
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1.3rem;
        }
        
        .checklist-items {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 15px;
        }
        
        .checklist-item {
            display: flex;
            align-items: flex-start;
            gap: 15px;
            padding: 15px;
            border-radius: 12px;
            background: #f8f9ff;
            transition: all 0.3s ease;
        }
        
        .checklist-item:hover {
            background: #f0f2ff;
            transform: translateY(-2px);
        }
        
        .checklist-item input[type="checkbox"] {
            width: 22px;
            height: 22px;
            accent-color: var(--primary);
            flex-shrink: 0;
            margin-top: 3px;
        }
        
        .checklist-content {
            flex: 1;
        }
        
        .checklist-item label {
            cursor: pointer;
            font-weight: 500;
            display: block;
            margin-bottom: 5px;
        }
        
        .checklist-date {
            font-size: 0.85rem;
            color: #777;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .checklist-item.completed .checklist-content label {
            text-decoration: line-through;
            color: #999;
        }
        
        .metrics-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        
        .metric-card {
            background: var(--gradient);
            color: white;
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(108, 92, 231, 0.2);
        }
        
        .metric-card::after {
            content: "";
            position: absolute;
            top: -20px;
            right: -20px;
            width: 70px;
            height: 70px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
        }
        
        .metric-value {
            font-size: 2.8rem;
            font-weight: 800;
            margin: 15px 0;
            position: relative;
            z-index: 2;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .metric-label {
            font-size: 1rem;
            opacity: 0.9;
            position: relative;
            z-index: 2;
        }
        
        .metric-controls {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 15px;
        }
        
        .metric-btn {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: white;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }
        
        .metric-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.1);
        }
        
        .week-selector {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin: 25px 0;
            flex-wrap: wrap;
        }
        
        .week-btn {
            padding: 12px 24px;
            border: 2px solid var(--primary);
            background: white;
            color: var(--primary);
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .week-btn:hover {
            background: rgba(108, 92, 231, 0.1);
        }
        
        .week-btn.active {
            background: var(--primary);
            color: white;
            box-shadow: 0 4px 15px rgba(108, 92, 231, 0.3);
        }
        
        .notes-section {
            background: #fff8e6;
            border-left: 4px solid var(--warning);
            padding: 25px;
            margin: 25px 0;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.03);
        }
        
        .emergency-section {
            background: #ffebee;
            border-left: 4px solid var(--danger);
            padding: 25px;
            margin: 25px 0;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.03);
        }
        
        .btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 14px 28px;
            border-radius: 12px;
            cursor: pointer;
            font-size: 16px;
            transition: all 0.3s ease;
            font-weight: 600;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 4px 15px rgba(108, 92, 231, 0.3);
        }
        
        .btn:hover {
            background: var(--primary-dark);
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(108, 92, 231, 0.4);
        }
        
        .btn:active {
            transform: translateY(0);
        }
        
        .priority-high { border-left-color: var(--danger); }
        .priority-medium { border-left-color: var(--warning); }
        .priority-low { border-left-color: var(--success); }
        
        .goals-section {
            background: white;
            border-radius: var(--border-radius);
            padding: 30px;
            margin: 25px 0;
            box-shadow: var(--shadow);
        }
        
        .goals-section h2 {
            color: var(--dark);
            margin-bottom: 25px;
            text-align: center;
            font-size: 1.8rem;
            position: relative;
            padding-bottom: 15px;
        }
        
        .goals-section h2::after {
            content: "";
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: var(--primary);
            border-radius: 2px;
        }
        
        .goals-list {
            list-style: none;
            padding: 0;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 15px;
        }
        
        .goals-list li {
            background: #f8f9ff;
            padding: 20px;
            margin: 10px 0;
            border-radius: 12px;
            border-left: 4px solid var(--primary);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.03);
            display: flex;
            align-items: flex-start;
            gap: 12px;
        }
        
        .goals-list li::before {
            content: "•";
            color: var(--primary);
            font-weight: bold;
            font-size: 1.5rem;
            line-height: 1;
        }
        
        .metrics-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
            margin-top: 25px;
        }
        
        .metric-item {
            background: white;
            padding: 20px;
            border-radius: 12px;
            text-align: center;
            border: 2px solid var(--gray);
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
        }
        
        .metric-item:hover {
            transform: translateY(-5px);
            border-color: var(--primary);
        }
        
        .controls {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
            margin: 30px 0;
        }
        
        .quote {
            text-align: center;
            font-style: italic;
            margin: 25px 0;
            padding: 20px;
            border-radius: var(--border-radius);
            background: rgba(108, 92, 231, 0.05);
            font-size: 1.1rem;
            border-left: 4px solid var(--primary);
        }
        
        .footer {
            text-align: center;
            padding: 20px;
            color: #777;
            font-size: 0.9rem;
            border-top: 1px solid var(--gray);
            margin-top: 30px;
        }
        
        .affirmation-section {
            background: #e8f5e9;
            border-left: 4px solid var(--success);
            padding: 20px;
            border-radius: 12px;
            margin: 20px 0;
            text-align: center;
        }
        
        .affirmation-content {
            font-size: 1.2rem;
            font-weight: 500;
            margin-bottom: 15px;
            font-style: italic;
        }
        
        .affirmation-author {
            color: #666;
            font-size: 0.9rem;
        }
        
        .completion-badge {
            display: inline-block;
            background: var(--success);
            color: white;
            padding: 8px 16px;
            border-radius: 50px;
            font-weight: 600;
            margin-top: 15px;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        .protocol-header {
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .protocol-content {
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px solid rgba(220, 53, 69, 0.3);
        }
        
        .reset-btn {
            background: var(--danger);
        }
        
        .daily-progress-section {
            background: white;
            border-radius: var(--border-radius);
            padding: 25px;
            margin: 25px 0;
            box-shadow: var(--shadow);
        }
        
        .daily-progress-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid var(--gray);
        }
        
        .daily-progress-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }
        
        .daily-progress-card {
            background: #f8f9ff;
            border-radius: 12px;
            padding: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
        }
        
        .daily-progress-card h3 {
            color: var(--primary);
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .daily-targets {
            list-style: none;
            padding: 0;
        }
        
        .daily-targets li {
            padding: 10px 0;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .daily-targets li:last-child {
            border-bottom: none;
        }
        
        .target-status {
            background: var(--success);
            color: white;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.85rem;
        }
        
        .target-status.pending {
            background: var(--warning);
        }
        
        @media (max-width: 768px) {
            .schedule-grid {
                grid-template-columns: 1fr;
            }
            
            .time-slot {
                justify-content: flex-start;
                padding-left: 20px;
            }
            
            .header h1 {
                font-size: 2rem;
            }
            
            .progress-overview {
                grid-template-columns: 1fr 1fr;
            }
            
            .tabs {
                flex-wrap: wrap;
            }
            
            .tab {
                flex: 1;
                min-width: 120px;
                justify-content: center;
                padding: 12px;
                font-size: 14px;
            }
            
            .controls {
                flex-direction: column;
                align-items: center;
            }
        }
        
        @media (max-width: 480px) {
            .header {
                padding: 20px 15px;
            }
            
            .progress-overview {
                grid-template-columns: 1fr;
            }
            
            .main-content {
                padding: 20px 15px;
            }
            
            .metric-value {
                font-size: 2.2rem;
            }
            
            .week-btn {
                width: 100%;
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="header-content">
                <h1><i class="fas fa-rocket"></i> Rohith's 40-Day Transformation</h1>
                <p>Career Mastery • Mental Health • Fitness • Relationships</p>
                
                <div class="date-display">
                    <i class="fas fa-calendar-day"></i>
                    <span id="current-date">Monday, June 21, 2025</span>
                    <span>• Day <span id="current-day-display">1</span>/40</span>
                </div>
                
                <div class="progress-overview">
                    <div class="progress-card">
                        <h3><i class="fas fa-tasks"></i> Overall Progress</h3>
                        <div class="progress-bar">
                            <div class="progress-fill" id="overall-progress" style="width: 0%"></div>
                        </div>
                        <span id="overall-percentage">0%</span>
                    </div>
                    <div class="progress-card">
                        <h3><i class="fas fa-laptop-code"></i> DSA Problems</h3>
                        <div class="progress-bar">
                            <div class="progress-fill" id="dsa-progress" style="width: 0%"></div>
                        </div>
                        <span id="dsa-count">0/100</span>
                    </div>
                    <div class="progress-card">
                        <h3><i class="fas fa-dumbbell"></i> Fitness Goals</h3>
                        <div class="progress-bar">
                            <div class="progress-fill" id="fitness-progress" style="width: 0%"></div>
                        </div>
                        <span id="fitness-percentage">0%</span>
                    </div>
                    <div class="progress-card">
                        <h3><i class="fas fa-fire"></i> Current Streak</h3>
                        <div class="metric-value" id="current-streak">0</div>
                        <div class="metric-label">days completed</div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="main-content">
            <div class="affirmation-section">
                <div class="affirmation-content" id="daily-affirmation">
                    "Every day is a new opportunity to become a better version of yourself."
                </div>
                <div class="affirmation-author">- Daily Motivation</div>
                <button class="btn" onclick="newAffirmation()" style="margin-top: 15px; background: var(--secondary);">
                    <i class="fas fa-sync"></i> New Affirmation
                </button>
            </div>
            
            <div class="week-selector">
                <button class="week-btn active" onclick="selectWeek(1)">
                    <i class="fas fa-layer-group"></i> Week 1-2: Foundation
                </button>
                <button class="week-btn" onclick="selectWeek(2)">
                    <i class="fas fa-chart-line"></i> Week 3-4: Building
                </button>
                <button class="week-btn" onclick="selectWeek(3)">
                    <i class="fas fa-fire"></i> Week 5-6: Transformation
                </button>
            </div>
            
            <div class="tabs">
                <button class="tab active" onclick="showTab('schedule')">
                    <i class="fas fa-calendar-alt"></i> Daily Schedule
                </button>
                <button class="tab" onclick="showTab('checklist')">
                    <i class="fas fa-check-circle"></i> Daily Checklist
                </button>
                <button class="tab" onclick="showTab('progress')">
                    <i class="fas fa-chart-line"></i> Daily Progress
                </button>
                <button class="tab" onclick="showTab('metrics')">
                    <i class="fas fa-chart-pie"></i> Progress Metrics
                </button>
                <button class="tab" onclick="showTab('goals')">
                    <i class="fas fa-bullseye"></i> Weekly Goals
                </button>
                <button class="tab" onclick="showTab('emergency')">
                    <i class="fas fa-first-aid"></i> Emergency Protocols
                </button>
            </div>
            
            <!-- DAILY SCHEDULE TAB -->
            <div class="tab-content active" id="schedule">
                <div class="schedule-grid" id="daily-schedule">
                    <!-- Schedule populated by JavaScript -->
                </div>
            </div>
            
            <!-- DAILY CHECKLIST TAB -->
            <div class="tab-content" id="checklist">
                <div class="checklist-section">
                    <h3><i class="fas fa-sun"></i> Morning Routine (8:00-10:00 AM)</h3>
                    <div class="checklist-items">
                        <div class="checklist-item">
                            <input type="checkbox" id="wake-up" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="wake-up">Wake up at 8:00 AM (no phone for 15 min)</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="water" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="water">Drink 500ml water + gratitude practice</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="skincare-morning" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="skincare-morning">Morning skincare routine + grooming</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="breakfast" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="breakfast">Protein-rich breakfast (no junk food)</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="checklist-section">
                    <h3><i class="fas fa-laptop"></i> Study & Career (10:00 AM - 5:00 PM)</h3>
                    <div class="checklist-items">
                        <div class="checklist-item">
                            <input type="checkbox" id="dsa-practice" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="dsa-practice">Solve 2-3 DSA problems (Striver's A2Z)</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="project-work" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="project-work">Work on project enhancement (2+ hours)</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="germany-prep" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="germany-prep">Germany preparation task</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="resume-work" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="resume-work">Resume/portfolio improvement</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="learning" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="learning">Technical skill learning (30+ min)</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="checklist-section">
                    <h3><i class="fas fa-heart"></i> Social & Mental Health (Throughout Day)</h3>
                    <div class="checklist-items">
                        <div class="checklist-item">
                            <input type="checkbox" id="social-interaction" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="social-interaction">Meaningful conversation (family/friends)</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="girl-interaction" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="girl-interaction">Natural interaction with her (if opportunity)</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="anxiety-management" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="anxiety-management">Practice anxiety management technique</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="confidence-building" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="confidence-building">One confidence-building activity</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="checklist-section">
                    <h3><i class="fas fa-moon"></i> Evening Routine (7:00-11:00 PM)</h3>
                    <div class="checklist-items">
                        <div class="checklist-item">
                            <input type="checkbox" id="workout" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="workout">Complete 45-60 min workout</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="healthy-dinner" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="healthy-dinner">Nutritious dinner with family</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="reflection" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="reflection">Daily reflection & tomorrow planning</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="skincare-evening" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="skincare-evening">Complete evening skincare routine</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="meditation" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="meditation">10 min meditation/breathing exercise</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="sleep-prep" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="sleep-prep">Sleep by 11 PM (phone away)</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="checklist-section">
                    <h3><i class="fas fa-chart-line"></i> Daily Metrics</h3>
                    <div class="checklist-items">
                        <div class="checklist-item">
                            <input type="checkbox" id="water-intake" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="water-intake">3+ liters water consumed</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="no-junk" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="no-junk">No junk food consumed</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="screen-time" onchange="updateProgress()">
                            <div class="checklist-content">
                                <label for="screen-time">Limited recreational screen time (< 2 hours)</label>
                                <div class="checklist-date"><i class="far fa-calendar"></i> Today</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="completion-badge" id="completion-badge" style="display: none;">
                    <i class="fas fa-trophy"></i> Day Completed!
                </div>
            </div>
            
            <!-- DAILY PROGRESS TAB -->
            <div class="tab-content" id="progress">
                <div class="daily-progress-section">
                    <div class="daily-progress-header">
                        <h2><i class="fas fa-calendar-check"></i> Daily Progress - Day <span id="progress-day">1</span></h2>
                        <div class="date-display">
                            <i class="fas fa-calendar-day"></i>
                            <span id="progress-date">Monday, June 21, 2025</span>
                        </div>
                    </div>
                    
                    <div class="daily-progress-content">
                        <div class="daily-progress-card">
                            <h3><i class="fas fa-bullseye"></i> Daily Targets</h3>
                            <ul class="daily-targets">
                                <li>
                                    <span>Complete morning routine</span>
                                    <span class="target-status" id="morning-target">Pending</span>
                                </li>
                                <li>
                                    <span>Solve DSA problems</span>
                                    <span class="target-status" id="dsa-target">Pending</span>
                                </li>
                                <li>
                                    <span>Work on projects</span>
                                    <span class="target-status" id="projects-target">Pending</span>
                                </li>
                                <li>
                                    <span>Complete workout</span>
                                    <span class="target-status" id="workout-target">Pending</span>
                                </li>
                                <li>
                                    <span>All daily metrics</span>
                                    <span class="target-status" id="metrics-target">Pending</span>
                                </li>
                            </ul>
                        </div>
                        
                        <div class="daily-progress-card">
                            <h3><i class="fas fa-check-circle"></i> Checklist Progress</h3>
                            <div class="progress-bar">
                                <div class="progress-fill" id="daily-checklist-progress" style="width: 0%"></div>
                            </div>
                            <div style="text-align: center; margin-top: 10px;">
                                <span id="daily-checklist-percentage">0%</span> completed
                            </div>
                        </div>
                        
                        <div class="daily-progress-card">
                            <h3><i class="fas fa-chart-pie"></i> Daily Metrics</h3>
                            <div class="metrics-grid" style="grid-template-columns: 1fr;">
                                <div class="metric-card">
                                    <div class="metric-label">DSA Problems Solved Today</div>
                                    <div class="metric-value" id="daily-dsa">0</div>
                                </div>
                                <div class="metric-card">
                                    <div class="metric-label">Workout Duration</div>
                                    <div class="metric-value" id="daily-workout">0 min</div>
                                </div>
                                <div class="metric-card">
                                    <div class="metric-label">Water Intake</div>
                                    <div class="metric-value" id="daily-water">0 L</div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div style="margin-top: 30px; text-align: center;">
                        <button class="btn" onclick="saveDailyProgress()">
                            <i class="fas fa-save"></i> Save Today's Progress
                        </button>
                    </div>
                </div>
            </div>
            
            <!-- PROGRESS METRICS TAB -->
            <div class="tab-content" id="metrics">
                <div class="metrics-grid">
                    <div class="metric-card">
                        <div class="metric-label">DSA Problems Solved</div>
                        <div class="metric-value" id="dsa-solved">0</div>
                        <div class="metric-label">Target: 100+ by Day 40</div>
                        <div class="metric-controls">
                            <button class="metric-btn" onclick="decrementDSA()">
                                <i class="fas fa-minus"></i>
                            </button>
                            <button class="metric-btn" onclick="incrementDSA()">
                                <i class="fas fa-plus"></i>
                            </button>
                        </div>
                    </div>
                    <div class="metric-card">
                        <div class="metric-label">Weight Loss</div>
                        <div class="metric-value" id="weight-loss">0 kg</div>
                        <div class="metric-label">Target: 8-10 kg</div>
                        <button class="btn" onclick="updateWeight()" style="margin-top: 15px; width: 100%;">
                            <i class="fas fa-weight"></i> Update Weight
                        </button>
                    </div>
                    <div class="metric-card">
                        <div class="metric-label">Workout Streak</div>
                        <div class="metric-value" id="workout-streak">0</div>
                        <div class="metric-label">days</div>
                        <div class="metric-controls">
                            <button class="metric-btn" onclick="decrementWorkout()">
                                <i class="fas fa-minus"></i>
                            </button>
                            <button class="metric-btn" onclick="incrementWorkout()">
                                <i class="fas fa-plus"></i>
                            </button>
                        </div>
                    </div>
                    <div class="metric-card">
                        <div class="metric-label">Projects Enhanced</div>
                        <div class="metric-value" id="projects-done">0</div>
                        <div class="metric-label">Target: 4 projects</div>
                        <div class="metric-controls">
                            <button class="metric-btn" onclick="decrementProjects()">
                                <i class="fas fa-minus"></i>
                            </button>
                            <button class="metric-btn" onclick="incrementProjects()">
                                <i class="fas fa-plus"></i>
                            </button>
                        </div>
                    </div>
                </div>
                
                <div class="notes-section">
                    <h3><i class="fas fa-edit"></i> Weekly Progress Notes</h3>
                    <textarea id="progress-notes" rows="4" style="width: 100%; padding: 15px; border: 1px solid #ffd54f; border-radius: 10px; margin-top: 15px; font-family: inherit;" placeholder="Record your weekly observations, challenges, wins, and adjustments needed..."></textarea>
                    <button class="btn" onclick="saveNotes()">
                        <i class="fas fa-save"></i> Save Notes
                    </button>
                </div>
                
                <div class="controls">
                    <button class="btn" onclick="incrementDSA()">
                        <i class="fas fa-plus"></i> Add DSA Problem
                    </button>
                    <button class="btn" onclick="updateWeight()">
                        <i class="fas fa-weight"></i> Update Weight
                    </button>
                    <button class="btn" onclick="incrementWorkout()">
                        <i class="fas fa-running"></i> Workout Done
                    </button>
                    <button class="btn" onclick="incrementProjects()">
                        <i class="fas fa-project-diagram"></i> Project Milestone
                    </button>
                    <button class="btn" onclick="nextDay()">
                        <i class="fas fa-arrow-right"></i> Next Day
                    </button>
                    <button class="btn reset-btn" onclick="resetDay()">
                        <i class="fas fa-redo"></i> Reset Day
                    </button>
                </div>
            </div>
            
            <!-- WEEKLY GOALS TAB -->
            <div class="tab-content" id="goals">
                <div id="week-goals">
                    <!-- Goals populated by JavaScript -->
                </div>
            </div>
            
            <!-- EMERGENCY PROTOCOLS TAB -->
            <div class="tab-content" id="emergency">
                <div class="emergency-section">
                    <div class="protocol-header" onclick="toggleProtocol('give-up')">
                        <h3><i class="fas fa-exclamation-triangle"></i> When You Feel Like Giving Up</h3>
                        <i class="fas fa-chevron-down" id="give-up-icon"></i>
                    </div>
                    <div class="protocol-content" id="give-up-content">
                        <ol>
                            <li><strong>Review your 'why':</strong> Germany goals, career dreams, relationship hopes</li>
                            <li><strong>Start small:</strong> Just do 10% of planned activity</li>
                            <li><strong>Call accountability partner:</strong> Friend, family member, or study group</li>
                            <li><strong>Visualize success:</strong> See yourself confident in Germany, getting dream internship</li>
                            <li><strong>Remember compound effect:</strong> Small daily actions create massive results</li>
                        </ol>
                    </div>
                </div>
                
                <div class="emergency-section">
                    <div class="protocol-header" onclick="toggleProtocol('overthinking')">
                        <h3><i class="fas fa-heart-broken"></i> When Overthinking About Her</h3>
                        <i class="fas fa-chevron-down" id="overthinking-icon"></i>
                    </div>
                    <div class="protocol-content" id="overthinking-content">
                        <ol>
                            <li><strong>Physical activity:</strong> Immediate 10 minutes exercise</li>
                            <li><strong>Redirect focus:</strong> Work on DSA problem or project</li>
                            <li><strong>Reality check:</strong> Write logical thoughts vs emotional thoughts</li>
                            <li><strong>Social connection:</strong> Call a friend, talk about other topics</li>
                            <li><strong>Future focus:</strong> Channel energy into becoming your best self</li>
                        </ol>
                    </div>
                </div>
                
                <div class="emergency-section">
                    <div class="protocol-header" onclick="toggleProtocol('junk-food')">
                        <h3><i class="fas fa-pizza-slice"></i> When Tempted by Junk Food</h3>
                        <i class="fas fa-chevron-down" id="junk-food-icon"></i>
                    </div>
                    <div class="protocol-content" id="junk-food-content">
                        <ol>
                            <li><strong>Drink water first:</strong> Often thirst masquerades as hunger</li>
                            <li><strong>Wait 10 minutes:</strong> Set timer, distract yourself</li>
                            <li><strong>Healthy substitute:</strong> Have prepared option ready</li>
                            <li><strong>Think long-term:</strong> Visualize your transformation goals</li>
                            <li><strong>Activity switch:</strong> Go for walk, call someone, do pushups</li>
                        </ol>
                    </div>
                </div>
                
                <div class="emergency-section">
                    <div class="protocol-header" onclick="toggleProtocol('unmotivated')">
                        <h3><i class="fas fa-bed"></i> When Feeling Unmotivated</h3>
                        <i class="fas fa-chevron-down" id="unmotivated-icon"></i>
                    </div>
                    <div class="protocol-content" id="unmotivated-content">
                        <ol>
                            <li><strong>5-minute rule:</strong> Just commit to 5 minutes of the task</li>
                            <li><strong>Success review:</strong> Look at progress photos, completed work</li>
                            <li><strong>Future visualization:</strong> See yourself successful and happy</li>
                            <li><strong>Accountability:</strong> Message your commitment to someone</li>
                            <li><strong>Environment change:</strong> Switch location, create energy</li>
                        </ol>
                    </div>
                </div>
                
                <div class="quote">
                    "The journey of a thousand miles begins with a single step. Every day you show up is a victory."
                </div>
            </div>
        </div>
        
        <div class="footer">
            <p>Rohith's Transformation Planner • Day <span id="footer-day">1</span> of 40</p>
        </div>
    </div>
    
    <script>
        // Schedule data for different weeks with updated times
        const schedules = {
            1: [ // Week 1-2: Foundation
                { time: "8:00 AM", activity: "Wake Up Protocol", description: "No phone, water, gratitude, light stretch", tags: ["Mental Health", "Foundation"], priority: "high" },
                { time: "8:30 AM", activity: "Self-Care Hour", description: "Shower, skincare routine, grooming, dress well", tags: ["Grooming", "Confidence"], priority: "medium" },
                { time: "9:30 AM", activity: "Nutritious Breakfast", description: "Protein-rich meal, plan day's nutrition", tags: ["Nutrition", "Health"], priority: "medium" },
                { time: "10:00 AM", activity: "DSA Practice Block 1", description: "2-3 basic problems: Arrays, Strings, Sorting", tags: ["Career", "DSA"], priority: "high" },
                { time: "12:00 PM", activity: "Social Connection", description: "Natural interactions, respond to messages", tags: ["Social", "Relationship"], priority: "medium" },
                { time: "1:00 PM", activity: "Lunch & Rest", description: "Mindful eating, short walk, relaxation", tags: ["Nutrition", "Recovery"], priority: "low" },
                { time: "2:00 PM", activity: "Project Development", description: "Enhance stampede detection or EEG-to-text project", tags: ["Career", "Projects"], priority: "high" },
                { time: "5:00 PM", activity: "Active Break", description: "Walk, dance practice, family time", tags: ["Social", "Recovery"], priority: "medium" },
                { time: "7:00 PM", activity: "Workout Session", description: "45-60 min strength training + cardio", tags: ["Fitness", "Health"], priority: "high" },
                { time: "8:00 PM", activity: "Dinner & Family", description: "Nutritious meal, family conversation", tags: ["Nutrition", "Social"], priority: "medium" },
                { time: "9:00 PM", activity: "Germany Preparation", description: "Research professors, prepare emails, language learning", tags: ["Career", "Germany"], priority: "high" },
                { time: "10:00 PM", activity: "Evening Wind Down", description: "Skincare, reflection, meditation", tags: ["Mental Health", "Recovery"], priority: "medium" },
                { time: "11:00 PM", activity: "Sleep", description: "Consistent bedtime, phone away", tags: ["Health", "Recovery"], priority: "high" }
            ],
            2: [ // Week 3-4: Building
                { time: "8:00 AM", activity: "Morning Routine", description: "Gratitude, intention setting, energizing stretch", tags: ["Mental Health", "Energy"], priority: "high" },
                { time: "8:30 AM", activity: "Enhanced Grooming", description: "Advanced skincare, appearance optimization", tags: ["Grooming", "Confidence"], priority: "medium" },
                { time: "9:30 AM", activity: "Optimized Nutrition", description: "Meal prep, supplements, intermittent fasting", tags: ["Nutrition", "Optimization"], priority: "medium" },
                { time: "10:00 AM", activity: "Advanced DSA Practice", description: "2-3 intermediate problems: Trees, DP, Graphs", tags: ["Career", "DSA"], priority: "high" },
                { time: "12:00 PM", activity: "Strategic Social Time", description: "Deeper connections, relationship building", tags: ["Social", "Relationship"], priority: "medium" },
                { time: "1:00 PM", activity: "Mindful Nutrition", description: "Balanced meal, hydration focus", tags: ["Nutrition", "Mindfulness"], priority: "low" },
                { time: "2:00 PM", activity: "Advanced Projects", description: "Full-stack development, AI/ML enhancement", tags: ["Career", "Technical Skills"], priority: "high" },
                { time: "5:00 PM", activity: "Confidence Building", description: "Social practice, public speaking, networking", tags: ["Confidence", "Social"], priority: "medium" },
                { time: "7:00 PM", activity: "Building Phase Workout", description: "60-75 min: Strength progression + HIIT cardio", tags: ["Fitness", "Strength"], priority: "high" },
                { time: "8:00 PM", activity: "Family & Connection", description: "Quality time, sharing progress", tags: ["Social", "Support"], priority: "medium" },
                { time: "9:00 PM", activity: "Skill Specialization", description: "Deep dive into chosen tech stack", tags: ["Career", "Expertise"], priority: "high" },
                { time: "10:00 PM", activity: "Reflection & Planning", description: "Progress review, tomorrow optimization", tags: ["Planning", "Growth"], priority: "medium" },
                { time: "11:00 PM", activity: "Quality Sleep", description: "Recovery optimization, dream preparation", tags: ["Health", "Recovery"], priority: "high" }
            ],
            3: [ // Week 5-6: Transformation
                { time: "8:00 AM", activity: "Peak Performance Morning", description: "Optimized routine, peak state creation", tags: ["Performance", "Excellence"], priority: "high" },
                { time: "8:30 AM", activity: "Peak Grooming", description: "Advanced skincare, style mastery", tags: ["Grooming", "Excellence"], priority: "medium" },
                { time: "9:30 AM", activity: "Performance Nutrition", description: "Optimized macros, body composition focus", tags: ["Nutrition", "Performance"], priority: "medium" },
                { time: "10:00 AM", activity: "Expert DSA Practice", description: "3-4 advanced problems: Company-specific challenges", tags: ["Career", "Excellence"], priority: "high" },
                { time: "12:00 PM", activity: "Confident Social Engagement", description: "Leadership practice, authentic connections", tags: ["Leadership", "Confidence"], priority: "medium" },
                { time: "1:00 PM", activity: "Peak Nutrition", description: "Precision eating, energy optimization", tags: ["Nutrition", "Peak Performance"], priority: "low" },
                { time: "2:00 PM", activity: "Portfolio Perfection", description: "Final project touches, presentation ready", tags: ["Career", "Portfolio"], priority: "high" },
                { time: "5:00 PM", activity: "Social Leadership", description: "Helping others, sharing knowledge", tags: ["Leadership", "Contribution"], priority: "medium" },
                { time: "7:00 PM", activity: "Transformation Workout", description: "75-90 min: High intensity, fat burning focus", tags: ["Fitness", "Transformation"], priority: "high" },
                { time: "8:00 PM", activity: "Family Success Sharing", description: "Celebrating progress, gratitude practice", tags: ["Gratitude", "Success"], priority: "medium" },
                { time: "9:00 PM", activity: "Germany Final Prep", description: "Application submissions, final preparations", tags: ["Career", "Germany"], priority: "high" },
                { time: "10:00 PM", activity: "Success Integration", description: "Identity reinforcement, future visioning", tags: ["Identity", "Vision"], priority: "medium" },
                { time: "11:00 PM", activity: "Recovery Excellence", description: "Peak recovery, transformation completion", tags: ["Recovery", "Excellence"], priority: "high" }
            ]
        };
        
        const weeklyGoals = {
            1: {
                title: "Week 1-2: Foundation Building",
                goals: [
                    "Solve 50 DSA problems (Arrays, Strings, Sorting, Linked Lists)",
                    "Establish consistent workout routine (4-5 days/week)",
                    "Complete basic skincare routine establishment",
                    "Start Germany research (identify 20 professors)",
                    "Enhance 1 major project with new features",
                    "Lose 2-3 kg through diet and exercise",
                    "Build morning routine consistency",
                    "Practice anxiety management techniques daily"
                ]
            },
            2: {
                title: "Week 3-4: Building Momentum",
                goals: [
                    "Solve 70 DSA problems (Trees, Dynamic Programming, Graphs)",
                    "Increase workout intensity (5-6 days/week)",
                    "Complete advanced skincare optimization",
                    "Send initial emails to 10 German professors",
                    "Enhance 2nd project with full-stack features",
                    "Lose additional 3-4 kg (total 5-7 kg)",
                    "Build confidence through social interactions",
                    "Master stress management techniques"
                ]
            },
            3: {
                title: "Week 5-6: Transformation Peak",
                goals: [
                    "Solve 100+ DSA problems (Advanced algorithms, System Design)",
                    "Achieve peak fitness routine (daily workouts)",
                    "Perfect grooming and style presentation",
                    "Complete Germany applications (submit to 15+ programs)",
                    "Finalize all 4 projects for portfolio",
                    "Reach target weight loss (8-10 kg total)",
                    "Demonstrate confident social leadership",
                    "Achieve mental clarity and emotional balance"
                ]
            }
        };
        
        const affirmations = [
            "Every day is a new opportunity to become a better version of yourself.",
            "Small consistent actions lead to massive transformations.",
            "Your discipline today is your freedom tomorrow.",
            "Progress, not perfection, is the key to success.",
            "Believe in the process and trust your journey.",
            "Your potential is limitless. Keep pushing forward.",
            "Every challenge is an opportunity for growth.",
            "Consistency is the bridge between goals and accomplishment.",
            "Your future self is counting on your present actions.",
            "Great things never came from comfort zones."
        ];
        
        let currentWeek = 1;
        let dailyMetrics = {
            dsaSolved: 0,
            weightLoss: 0,
            workoutStreak: 0,
            projectsDone: 0,
            currentDay: 1,
            currentStreak: 0,
            dailyDSA: 0,
            dailyWorkout: 0,
            dailyWater: 0
        };
        
        // Format date as "Monday, January 1, 2025"
        function formatDate(date) {
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            return date.toLocaleDateString('en-US', options);
        }
        
        // Update date display
        function updateDateDisplay() {
            const today = new Date();
            document.getElementById('current-date').textContent = formatDate(today);
            document.getElementById('progress-date').textContent = formatDate(today);
            document.getElementById('footer-day').textContent = dailyMetrics.currentDay;
            document.getElementById('current-day-display').textContent = dailyMetrics.currentDay;
            document.getElementById('progress-day').textContent = dailyMetrics.currentDay;
        }
        
        // Load saved data from localStorage
        function loadData() {
            const saved = localStorage.getItem('transformationData');
            if (saved) {
                const data = JSON.parse(saved);
                dailyMetrics = { ...dailyMetrics, ...data.metrics };
                currentWeek = data.currentWeek || 1;
                
                // Restore checkbox states
                Object.keys(data.checkboxes || {}).forEach(id => {
                    const checkbox = document.getElementById(id);
                    if (checkbox) {
                        checkbox.checked = data.checkboxes[id];
                        if (checkbox.checked) {
                            checkbox.closest('.checklist-item').classList.add('completed');
                        }
                    }
                });
                
                // Restore notes
                const notesTextarea = document.getElementById('progress-notes');
                if (notesTextarea && data.notes) {
                    notesTextarea.value = data.notes;
                }
                
                // Restore affirmation
                if (data.affirmation) {
                    document.getElementById('daily-affirmation').textContent = data.affirmation;
                }
            }
            updateProgress();
            updateMetricsDisplay();
            updateDateDisplay();
            updateDailyProgress();
        }
        
        // Save data to localStorage
        function saveData() {
            const checkboxes = {};
            document.querySelectorAll('.checklist-item input[type="checkbox"]').forEach(checkbox => {
                checkboxes[checkbox.id] = checkbox.checked;
            });
            
            const notesTextarea = document.getElementById('progress-notes');
            const notes = notesTextarea ? notesTextarea.value : '';
            
            const affirmation = document.getElementById('daily-affirmation').textContent;
            
            const data = {
                metrics: dailyMetrics,
                currentWeek: currentWeek,
                checkboxes: checkboxes,
                notes: notes,
                affirmation: affirmation,
                lastUpdated: new Date().toISOString()
            };
            
            localStorage.setItem('transformationData', JSON.stringify(data));
        }
        
        // Initialize the app
        function init() {
            loadData();
            selectWeek(currentWeek);
            updateSchedule();
            updateWeeklyGoals();
            updateAffirmation();
        }
        
        // Tab switching functionality
        function showTab(tabName) {
            // Hide all tab contents
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.remove('active');
            });
            
            // Remove active class from all tabs
            document.querySelectorAll('.tab').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Show selected tab content
            document.getElementById(tabName).classList.add('active');
            
            // Add active class to clicked tab
            event.currentTarget.classList.add('active');
        }
        
        // Week selection functionality
        function selectWeek(week) {
            currentWeek = week;
            
            // Update week button states
            document.querySelectorAll('.week-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            document.querySelectorAll('.week-btn')[week - 1].classList.add('active');
            
            updateSchedule();
            updateWeeklyGoals();
            saveData();
        }
        
        // Update daily schedule based on selected week
        function updateSchedule() {
            const scheduleContainer = document.getElementById('daily-schedule');
            const schedule = schedules[currentWeek];
            
            scheduleContainer.innerHTML = '';
            
            schedule.forEach(item => {
                // Time slot
                const timeSlot = document.createElement('div');
                timeSlot.className = 'time-slot';
                timeSlot.textContent = item.time;
                
                // Activity
                const activity = document.createElement('div');
                activity.className = `activity priority-${item.priority}`;
                
                activity.innerHTML = `
                    <h4><i class="far fa-clock"></i> ${item.activity}</h4>
                    <p>${item.description}</p>
                    <div class="activity-tags">
                        ${item.tags.map(tag => `<span class="tag">${tag}</span>`).join('')}
                    </div>
                `;
                
                scheduleContainer.appendChild(timeSlot);
                scheduleContainer.appendChild(activity);
            });
        }
        
        // Update weekly goals display
        function updateWeeklyGoals() {
            const goalsContainer = document.getElementById('week-goals');
            const goals = weeklyGoals[currentWeek];
            
            goalsContainer.innerHTML = `
                <div class="goals-section">
                    <h2>${goals.title}</h2>
                    <ul class="goals-list">
                        ${goals.goals.map(goal => `<li>${goal}</li>`).join('')}
                    </ul>
                </div>
            `;
        }
        
        // Update daily progress display
        function updateDailyProgress() {
            // Update daily metrics
            document.getElementById('daily-dsa').textContent = dailyMetrics.dailyDSA;
            document.getElementById('daily-workout').textContent = dailyMetrics.dailyWorkout + " min";
            document.getElementById('daily-water').textContent = dailyMetrics.dailyWater + " L";
            
            // Update progress bar
            const checkboxes = document.querySelectorAll('.checklist-item input[type="checkbox"]');
            const totalTasks = checkboxes.length;
            let completedTasks = 0;
            
            checkboxes.forEach(checkbox => {
                if (checkbox.checked) {
                    completedTasks++;
                }
            });
            
            const progressPercentage = Math.round((completedTasks / totalTasks) * 100);
            document.getElementById('daily-checklist-progress').style.width = progressPercentage + '%';
            document.getElementById('daily-checklist-percentage').textContent = progressPercentage + '%';
            
            // Update target status
            const morningCompleted = document.getElementById('wake-up').checked && 
                                   document.getElementById('water').checked && 
                                   document.getElementById('skincare-morning').checked && 
                                   document.getElementById('breakfast').checked;
            
            const dsaCompleted = document.getElementById('dsa-practice').checked;
            const projectsCompleted = document.getElementById('project-work').checked;
            const workoutCompleted = document.getElementById('workout').checked;
            const metricsCompleted = document.getElementById('water-intake').checked && 
                                   document.getElementById('no-junk').checked && 
                                   document.getElementById('screen-time').checked;
            
            document.getElementById('morning-target').textContent = morningCompleted ? "Completed" : "Pending";
            document.getElementById('morning-target').className = morningCompleted ? "target-status" : "target-status pending";
            
            document.getElementById('dsa-target').textContent = dsaCompleted ? "Completed" : "Pending";
            document.getElementById('dsa-target').className = dsaCompleted ? "target-status" : "target-status pending";
            
            document.getElementById('projects-target').textContent = projectsCompleted ? "Completed" : "Pending";
            document.getElementById('projects-target').className = projectsCompleted ? "target-status" : "target-status pending";
            
            document.getElementById('workout-target').textContent = workoutCompleted ? "Completed" : "Pending";
            document.getElementById('workout-target').className = workoutCompleted ? "target-status" : "target-status pending";
            
            document.getElementById('metrics-target').textContent = metricsCompleted ? "Completed" : "Pending";
            document.getElementById('metrics-target').className = metricsCompleted ? "target-status" : "target-status pending";
        }
        
        // Update progress based on completed tasks
        function updateProgress() {
            const checkboxes = document.querySelectorAll('.checklist-item input[type="checkbox"]');
            const totalTasks = checkboxes.length;
            let completedTasks = 0;
            
            checkboxes.forEach(checkbox => {
                const item = checkbox.closest('.checklist-item');
                if (checkbox.checked) {
                    completedTasks++;
                    item.classList.add('completed');
                } else {
                    item.classList.remove('completed');
                }
            });
            
            // Calculate overall progress
            const overallProgress = Math.round((completedTasks / totalTasks) * 100);
            
            // Update progress bars
            document.getElementById('overall-progress').style.width = overallProgress + '%';
            document.getElementById('overall-percentage').textContent = overallProgress + '%';
            
            // Update DSA progress
            const dsaProgress = Math.round((dailyMetrics.dsaSolved / 100) * 100);
            document.getElementById('dsa-progress').style.width = Math.min(dsaProgress, 100) + '%';
            document.getElementById('dsa-count').textContent = `${dailyMetrics.dsaSolved}/100`;
            
            // Update fitness progress
            const fitnessProgress = Math.round((dailyMetrics.weightLoss / 10) * 100);
            document.getElementById('fitness-progress').style.width = Math.min(fitnessProgress, 100) + '%';
            document.getElementById('fitness-percentage').textContent = Math.min(fitnessProgress, 100) + '%';
            
            // Update current day
            document.getElementById('current-day-display').textContent = dailyMetrics.currentDay;
            document.getElementById('footer-day').textContent = dailyMetrics.currentDay;
            
            // Update streak
            document.getElementById('current-streak').textContent = dailyMetrics.currentStreak;
            
            // Show completion badge if all tasks are completed
            const badge = document.getElementById('completion-badge');
            if (completedTasks === totalTasks) {
                badge.style.display = 'inline-block';
                
                // Increase streak if this is a new day completion
                if (!dailyMetrics.completedToday) {
                    dailyMetrics.currentStreak++;
                    dailyMetrics.completedToday = true;
                    updateMetricsDisplay();
                }
            } else {
                badge.style.display = 'none';
                dailyMetrics.completedToday = false;
            }
            
            // Update daily progress
            updateDailyProgress();
            
            saveData();
        }
        
        // Update metrics display
        function updateMetricsDisplay() {
            document.getElementById('dsa-solved').textContent = dailyMetrics.dsaSolved;
            document.getElementById('weight-loss').textContent = dailyMetrics.weightLoss + ' kg';
            document.getElementById('workout-streak').textContent = dailyMetrics.workoutStreak;
            document.getElementById('projects-done').textContent = dailyMetrics.projectsDone;
            document.getElementById('current-streak').textContent = dailyMetrics.currentStreak;
        }
        
        // Save notes functionality
        function saveNotes() {
            saveData();
            alert('Notes saved successfully!');
        }
        
        function saveDailyProgress() {
            saveData();
            alert('Daily progress saved successfully!');
        }
        
        // Increment metrics functions
        function incrementDSA() {
            dailyMetrics.dsaSolved++;
            dailyMetrics.dailyDSA += 2; // Assuming 2 problems per increment
            updateMetricsDisplay();
            updateProgress();
        }
        
        function decrementDSA() {
            if (dailyMetrics.dsaSolved > 0) {
                dailyMetrics.dsaSolved--;
                if (dailyMetrics.dailyDSA > 0) {
                    dailyMetrics.dailyDSA = Math.max(0, dailyMetrics.dailyDSA - 2);
                }
                updateMetricsDisplay();
                updateProgress();
            }
        }
        
        function updateWeight() {
            const newWeight = prompt('Enter current weight loss (kg):');
            if (newWeight !== null && !isNaN(newWeight)) {
                dailyMetrics.weightLoss = parseFloat(newWeight);
                updateMetricsDisplay();
                updateProgress();
            }
        }
        
        function incrementWorkout() {
            dailyMetrics.workoutStreak++;
            dailyMetrics.dailyWorkout += 45; // Assuming 45 minutes per workout
            updateMetricsDisplay();
            updateProgress();
        }
        
        function decrementWorkout() {
            if (dailyMetrics.workoutStreak > 0) {
                dailyMetrics.workoutStreak--;
                if (dailyMetrics.dailyWorkout > 0) {
                    dailyMetrics.dailyWorkout = Math.max(0, dailyMetrics.dailyWorkout - 45);
                }
                updateMetricsDisplay();
                updateProgress();
            }
        }
        
        function incrementProjects() {
            dailyMetrics.projectsDone++;
            updateMetricsDisplay();
            updateProgress();
        }
        
        function decrementProjects() {
            if (dailyMetrics.projectsDone > 0) {
                dailyMetrics.projectsDone--;
                updateMetricsDisplay();
                updateProgress();
            }
        }
        
        function nextDay() {
            if (dailyMetrics.currentDay < 40) {
                dailyMetrics.currentDay++;
                
                // Auto-advance weeks
                if (dailyMetrics.currentDay > 14 && currentWeek === 1) {
                    selectWeek(2);
                } else if (dailyMetrics.currentDay > 28 && currentWeek === 2) {
                    selectWeek(3);
                }
                
                // Reset daily checkboxes
                document.querySelectorAll('.checklist-item input[type="checkbox"]').forEach(checkbox => {
                    checkbox.checked = false;
                    checkbox.closest('.checklist-item').classList.remove('completed');
                });
                
                // Reset daily metrics
                dailyMetrics.dailyDSA = 0;
                dailyMetrics.dailyWorkout = 0;
                dailyMetrics.dailyWater = 0;
                
                // Reset completion flag
                dailyMetrics.completedToday = false;
                
                updateProgress();
                updateMetricsDisplay();
                updateDateDisplay();
                updateAffirmation();
            } else {
                alert("Congratulations! You've completed the 40-day transformation journey!");
            }
        }
        
        function resetDay() {
            if (confirm("Are you sure you want to reset today's progress?")) {
                document.querySelectorAll('.checklist-item input[type="checkbox"]').forEach(checkbox => {
                    checkbox.checked = false;
                    checkbox.closest('.checklist-item').classList.remove('completed');
                });
                
                dailyMetrics.dailyDSA = 0;
                dailyMetrics.dailyWorkout = 0;
                dailyMetrics.dailyWater = 0;
                
                dailyMetrics.completedToday = false;
                updateProgress();
            }
        }
        
        function updateAffirmation() {
            const affirmationElement = document.getElementById('daily-affirmation');
            affirmationElement.textContent = affirmations[Math.floor(Math.random() * affirmations.length)];
            saveData();
        }
        
        function newAffirmation() {
            updateAffirmation();
        }
        
        function toggleProtocol(protocol) {
            const content = document.getElementById(`${protocol}-content`);
            const icon = document.getElementById(`${protocol}-icon`);
            
            if (content.style.display === 'none' || content.style.display === '') {
                content.style.display = 'block';
                icon.className = 'fas fa-chevron-up';
            } else {
                content.style.display = 'none';
                icon.className = 'fas fa-chevron-down';
            }
        }
        
        // Initialize everything when page loads
        document.addEventListener('DOMContentLoaded', function() {
            init();
            
            // Initialize protocols to be expanded by default
            document.querySelectorAll('.protocol-content').forEach(el => {
                el.style.display = 'block';
            });
            document.querySelectorAll('.protocol-header i').forEach(el => {
                el.className = 'fas fa-chevron-up';
            });
        });
        
        // Save data before page unload
        window.addEventListener('beforeunload', saveData);
    </script>
</body>
</html>
