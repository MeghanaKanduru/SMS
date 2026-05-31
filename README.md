# SMS
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Smart Campus Information System — DSCE</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@400;500&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
   /* Brand Accent Colors (From the main swatches) */
    --y1: #EBFFA1;        /* LEMON */
    --y2: #F6D5EE;        /* PINK */
    --y3: #A8A3F6;        /* LILAC */

    /* Deep UI Backgrounds */
    --b1: #000000;        /* Pure Black (Canvas Background) */
    --b2: #0D0E12;        /* Dark Navy / Darkest component tiles */
    --b3: #181922;        /* NAVY (#24316B dynamically muted for background blocks) */
    --b4: #212330;        /* Card background hover / active state */
    --b5: #2E3142;        /* Lighter card borders and separators */

    /* Typography & Text States */
    --text: #FFFFFF;      /* Primary White text and headers */
    --text-muted: #9BA1B6; /* Subtitles and secondary body text */
    --text-dim: #565B70;  /* Inactive states, utility icons, and grid borders */

    /* Borders & Interaction Styles */
    --border: rgba(255, 255, 255, 0.1);         /* Dashed layout outlines */
    --border-bright: rgba(168, 163, 246, 0.4); /* Lilac interactive focus state */

    /* Extra UI Accents (Extracted from component details) */
    --success: #24316B;   /* NAVY (Solid base swatch tone) */
    --danger: #FF6B6B;    /* Accent highlight/notification dot */
    --info: #5CE1E6;      /* Cyan detailing on specific widgets */
    --warn: #FFDE4D;      /* Yellow accent stars and coin badges */

    --radius: 8px;
    --radius-lg: 14px;
}

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: #111111;
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── HEADER ── */
  header {
    background: var(--b2);
    border-bottom: 1px solid var(--border-bright);
    padding: 0 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 64px;
    position: sticky; top: 0; z-index: 100;
  }
  .logo {
    display: flex; align-items: center; gap: 12px;
  }
  .logo-icon {
    width: 36px; height: 36px;
    background: var(--y1);
    border-radius: 20px;
    display: flex; align-items: center; justify-content: center;
  }
  .logo-icon svg { width: 20px; height: 20px; }
  .logo-text {
    font-family: 'Syne', sans-serif;
    font-weight: 800; font-size: 1rem;
    color: var(--y1); letter-spacing: 0.03em;
  }
  .logo-sub { font-size: 0.7rem; color: var(--text-muted); margin-top: 1px; }
  .header-badge {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem; color: var(--y2);
    background: rgba(255,215,0,0.08);
    border: 1px solid var(--border-bright);
    padding: 4px 10px; border-radius: 20px;
  }

  /* ── LAYOUT ── */
  .app {
    display: flex;
    min-height: calc(100vh - 64px);
  }

  /* ── SIDEBAR ── */
  nav.sidebar {
    width: 220px;
    flex-shrink: 0;
    background: var(--b2);
    border-right: 1px solid var(--border);
    padding: 1.5rem 0;
    position: sticky;
    top: 64px;
    height: calc(100vh - 64px);
    overflow-y: auto;
  }
  .nav-section-label {
    font-size: 0.65rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    color: var(--text-dim);
    text-transform: uppercase;
    padding: 0.75rem 1.2rem 0.4rem;
  }
  .nav-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 0.55rem 1.2rem;
    font-size: 0.85rem;
    color: var(--text-muted);
    cursor: pointer;
    border-left: 3px solid transparent;
    transition: all 0.15s;
    user-select: none;
  }
  .nav-item:hover { color: var(--text); background: rgba(255,215,0,0.04); }
  .nav-item.active {
    color: var(--y1);
    border-left-color: var(--y1);
    background: rgba(255,215,0,0.07);
    font-weight: 500;
  }
  .nav-item svg { width: 16px; height: 16px; flex-shrink: 0; }

  /* ── MAIN ── */
  main {
    flex: 1;
    padding: 2rem 2.5rem;
    max-width: 1100px;
  }

  /* ── PAGE ── */
  .page { display: none; }
  .page.active { display: block; animation: fadeIn 0.2s ease; }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }

  .page-header {
    margin-bottom: 2rem;
  }
  .page-header h1 {
    font-family: 'Syne', sans-serif;
    font-weight: 700; font-size: 1.6rem;
    color: var(--y1);
    margin-bottom: 4px;
  }
  .page-header p { font-size: 0.875rem; color: var(--text-muted); }

  /* ── CARDS ── */
  .card {
    background: var(--b3);
    border: 1px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 1.5rem;
    margin-bottom: 1.5rem;
  }
  .card-title {
    font-family: 'Syne', sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    color: var(--y2);
    margin-bottom: 1.25rem;
    display: flex; align-items: center; gap: 8px;
    text-transform: uppercase; letter-spacing: 0.06em;
  }
  .card-title svg { width: 15px; height: 15px; opacity: 0.8; }

  /* ── STAT GRID ── */
  .stat-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 1rem;
    margin-bottom: 1.5rem;
  }
  .stat-card {
    background: var(--b3);
    border: 1px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 1.25rem 1.4rem;
  }
  .stat-label {
    font-size: 0.72rem;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.08em;
    margin-bottom: 6px;
  }
  .stat-value {
    font-family: 'Syne', sans-serif;
    font-size: 2rem;
    font-weight: 800;
    color: var(--y1);
    line-height: 1;
  }
  .stat-sub { font-size: 0.72rem; color: var(--text-muted); margin-top: 4px; }

  /* ── FORM ELEMENTS ── */
  label.field-label {
    display: block;
    font-size: 0.78rem;
    font-weight: 500;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.07em;
    margin-bottom: 6px;
  }
  input[type=text], input[type=number], input[type=email], select, textarea {
    width: 100%;
    background: var(--b4);
    border: 1px solid var(--border-bright);
    border-radius: var(--radius);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.875rem;
    padding: 0.6rem 0.85rem;
    outline: none;
    transition: border-color 0.15s;
  }
  input:focus, select:focus, textarea:focus {
    border-color: var(--y1);
    box-shadow: 0 10px 30px rgba(0,0,0,0.08);
  }
  select option { background: var(--b3); }
  textarea { resize: vertical; min-height: 80px; }

  .form-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
    margin-bottom: 1rem;
  }
  .form-group { display: flex; flex-direction: column; }

  /* ── BUTTONS ── */
  .btn {
    display: inline-flex; align-items: center; gap: 6px;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.85rem; font-weight: 600;
    padding: 0.55rem 1.25rem;
    border-radius: var(--radius);
    border: 1.5px solid transparent;
    cursor: pointer;
    transition: all 0.15s;
    white-space: nowrap;
  }
  .btn-primary {
    background: var(--y1); color: var(--b1); border-color: var(--y1);
  }
  .btn-primary:hover { background: var(--y2); border-color: var(--y2); }
  .btn-outline {
    background: transparent; color: var(--y1); border-color: var(--border-bright);
  }
  .btn-outline:hover { border-color: var(--y1); background: rgba(255,215,0,0.07); }
  .btn-danger {
    background: transparent; color: var(--danger); border-color: rgba(239,68,68,0.3);
    font-size: 0.78rem; padding: 0.35rem 0.75rem;
  }
  .btn-danger:hover { background: rgba(239,68,68,0.1); }
  .btn-sm { font-size: 0.78rem; padding: 0.35rem 0.85rem; }
  .btn svg { width: 15px; height: 15px; }

  /* ── TABLE ── */
  .table-wrap { overflow-x: auto; }
  table {
    width: 100%; border-collapse: collapse;
    font-size: 0.85rem;
  }
  th {
    font-size: 0.7rem; text-transform: uppercase; letter-spacing: 0.08em;
    color: var(--text-muted);
    border-bottom: 1px solid var(--border);
    padding: 0.6rem 1rem;
    text-align: left; font-weight: 600;
    background: var(--b4);
  }
  td { padding: 0.75rem 1rem; border-bottom: 1px solid rgba(255,215,0,0.05); }
  tr:hover td { background: rgba(255,215,0,0.03); }
  .badge {
    display: inline-block;
    font-size: 0.7rem; font-weight: 600;
    padding: 2px 10px; border-radius: 20px;
  }
  .badge-A { background: rgba(34,197,94,0.15); color: #4ade80; }
  .badge-B { background: rgba(255,215,0,0.15); color: var(--y1); }
  .badge-C { background: rgba(96,165,250,0.15); color: var(--info); }
  .badge-D { background: rgba(245,158,11,0.15); color: var(--warn); }
  .badge-F { background: rgba(239,68,68,0.15); color: var(--danger); }

  /* ── ALERTS ── */
  .alert {
    padding: 0.85rem 1rem;
    border-radius: var(--radius);
    font-size: 0.85rem;
    margin-bottom: 1rem;
    display: none;
  }
  .alert.show { display: flex; align-items: center; gap: 8px; }
  .alert-success { background: rgba(34,197,94,0.12); border: 1px solid rgba(34,197,94,0.3); color: #4ade80; }
  .alert-error { background: rgba(239,68,68,0.12); border: 1px solid rgba(239,68,68,0.3); color: #f87171; }
  .alert-info { background: rgba(96,165,250,0.12); border: 1px solid rgba(96,165,250,0.3); color: var(--info); }

  /* ── SEARCH BAR ── */
  .search-bar {
    display: flex; gap: 10px; margin-bottom: 1.25rem; align-items: center;
  }
  .search-bar input { flex: 1; }
  .search-bar select { width: 160px; }

  /* ── PROGRESS BAR ── */
  .progress-wrap { margin: 4px 0; }
  .progress-bg {
    height: 6px; background: var(--b5); border-radius: 3px; overflow: hidden;
  }
  .progress-fill { height: 100%; border-radius: 3px; transition: width 0.4s; }

  /* ── ANALYTICS ── */
  .chart-canvas-wrap {
    position: relative; margin-top: 1rem;
  }
  canvas { display: block; max-height: 260px; }

  /* ── AI PANEL ── */
  .ai-panel {
    background: linear-gradient(135deg, rgba(255,215,0,0.06), rgba(255,215,0,0.02));
    border: 1px solid var(--border-bright);
    border-radius: var(--radius-lg);
    padding: 1.25rem 1.5rem;
    margin-top: 1.5rem;
  }
  .ai-label {
    font-size: 0.7rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.1em;
    color: var(--y2); margin-bottom: 0.75rem;
    display: flex; align-items: center; gap: 6px;
  }
  .ai-output {
    font-size: 0.875rem; color: var(--text); line-height: 1.7;
    white-space: pre-wrap; min-height: 40px;
  }
  .ai-loading { color: var(--text-muted); font-style: italic; }

  /* ── MONO TEXT ── */
  .mono { font-family: 'DM Mono', monospace; font-size: 0.82rem; }

  /* ── EMPTY STATE ── */
  .empty-state {
    text-align: center; padding: 3rem 1rem; color: var(--text-muted);
  }
  .empty-state svg { width: 48px; height: 48px; opacity: 0.2; margin: 0 auto 1rem; display: block; }
  .empty-state p { font-size: 0.875rem; }

  /* ── DASHBOARD GRID ── */
  .dash-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.25rem;
  }
  @media (max-width: 800px) { .dash-grid { grid-template-columns: 1fr; } nav.sidebar { display: none; } }

  /* ── FEE TABLE ── */
  .fee-breakdown td:last-child { text-align: right; font-family: 'DM Mono', monospace; }
  .fee-total { font-weight: 700; color: var(--y1); }
  .fee-total td { border-top: 1px solid var(--border-bright); }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--b2); }
  ::-webkit-scrollbar-thumb { background: var(--b5); border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: var(--y3); }

  /* ── FILE MANAGER ── */
  .file-item {
    display: flex; align-items: center; gap: 12px;
    padding: 0.75rem 1rem;
    border: 1px solid var(--border);
    border-radius: var(--radius);
    margin-bottom: 0.5rem;
    font-size: 0.85rem;
    transition: border-color 0.15s;
  }
  .file-item:hover { border-color: var(--border-bright); }
  .file-icon { width: 32px; height: 32px; border-radius: 6px; display: flex; align-items: center; justify-content: center; background: rgba(255,215,0,0.1); flex-shrink: 0; }
  .file-icon svg { width: 16px; height: 16px; color: var(--y2); }
  .file-name { font-weight: 500; color: var(--text); }
  .file-meta { font-size: 0.75rem; color: var(--text-muted); }
  .file-tags { display: flex; gap: 4px; flex-wrap: wrap; margin-top: 4px; }
  .file-tag { font-size: 0.65rem; padding: 2px 7px; border-radius: 10px; background: rgba(255,215,0,0.08); color: var(--y2); border: 1px solid rgba(255,215,0,0.2); }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="logo">
    <div class="logo-icon">
      <svg viewBox="0 0 24 24" fill="none" stroke="#0A0A0A" stroke-width="2.5">
        <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/>
        <polyline points="9 22 9 12 15 12 15 22"/>
      </svg>
    </div>
    <div>
      <div class="logo-text">SMART CAMPUS WEBSITE</div>
      <div class="logo-sub">Dayananda Sagar College of Engineering</div>
    </div>
  </div>
  <div class="header-badge">PYTHON Project </div>
</header>

<div class="app">
  <!-- SIDEBAR -->
  <nav class="sidebar">
    <div class="nav-section-label">Modules</div>

    <div class="nav-item active" onclick="showPage('dashboard')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/></svg>
      Dashboard
    </div>
    <div class="nav-item" onclick="showPage('registration')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
      Registration
    </div>
    <div class="nav-item" onclick="showPage('enrollment')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/></svg>
      Enrollment
    </div>
    <div class="nav-item" onclick="showPage('records')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/></svg>
      Records
    </div>
    <div class="nav-item" onclick="showPage('search')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      Search & Sort
    </div>
    <div class="nav-item" onclick="showPage('fees')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="12" y1="1" x2="12" y2="23"/><path d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"/></svg>
      Fee Calculator
    </div>
    <div class="nav-item" onclick="showPage('files')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"/></svg>
      File Manager
    </div>
    <div class="nav-item" onclick="showPage('analytics')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
      Analytics
    </div>
    <div class="nav-item" onclick="showPage('ai')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 2a2 2 0 0 1 2 2c0 .74-.4 1.39-1 1.73V7h1a7 7 0 0 1 7 7h1a1 1 0 0 1 1 1v3a1 1 0 0 1-1 1h-1v1a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-1H2a1 1 0 0 1-1-1v-3a1 1 0 0 1 1-1h1a7 7 0 0 1 7-7h1V5.73c-.6-.34-1-.99-1-1.73a2 2 0 0 1 2-2z"/></svg>
      AI Advisor
    </div>
  </nav>

  <!-- MAIN CONTENT -->
  <main>

    <!-- ────────── DASHBOARD ────────── -->
    <div id="page-dashboard" class="page active">
      <div class="page-header">
        <h1>System Dashboard</h1>
        <p>Smart Campus Information System — All modules integrated</p>
      </div>

      <div class="stat-grid" id="dash-stats">
        <div class="stat-card">
          <div class="stat-label">Students</div>
          <div class="stat-value" id="stat-students">0</div>
          <div class="stat-sub">Registered</div>
        </div>
        <div class="stat-card">
          <div class="stat-label">Courses</div>
          <div class="stat-value" id="stat-courses">0</div>
          <div class="stat-sub">Active enrollments</div>
        </div>
        <div class="stat-card">
          <div class="stat-label">Avg Score</div>
          <div class="stat-value" id="stat-avg">—</div>
          <div class="stat-sub">All students</div>
        </div>
        <div class="stat-card">
          <div class="stat-label">Top Grade</div>
          <div class="stat-value" id="stat-top">—</div>
          <div class="stat-sub">Highest performer</div>
        </div>
      </div>

      <div class="dash-grid">
        <div class="card">
          <div class="card-title">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/><polyline points="17 6 23 6 23 12"/></svg>
            Grade Distribution
          </div>
          <div class="chart-canvas-wrap"><canvas id="gradeChart"></canvas></div>
        </div>
        <div class="card">
          <div class="card-title">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="18" height="18" rx="2"/><path d="M3 9h18M9 21V9"/></svg>
            Recent Registrations
          </div>
          <div id="recent-list">
            <div class="empty-state">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
              <p>No students yet. Register from Lab 1.</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- ────────── LAB 1: REGISTRATION ────────── -->
    <div id="page-registration" class="page">
      <div class="page-header">
        <h1> Student Registration & Grade Evaluation</h1>
        <p>Register students and auto-evaluate grades using conditional logic</p>
      </div>
      <div id="alert-reg" class="alert"></div>

      <div class="card">
        <div class="card-title">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
          Register New Student
        </div>
        <div class="form-grid">
          <div class="form-group">
            <label class="field-label">Student Name</label>
            <input type="text" id="reg-name" placeholder="e.g. Priya Sharma">
          </div>
          <div class="form-group">
            <label class="field-label">Student ID</label>
            <input type="text" id="reg-id" placeholder="e.g. 1BL22CS042">
          </div>
          <div class="form-group">
            <label class="field-label">Exam Score (0–100)</label>
            <input type="number" id="reg-score" placeholder="0–100" min="0" max="100">
          </div>
          <div class="form-group">
            <label class="field-label">Department</label>
            <select id="reg-dept">
              <option value="CSE">Computer Science (CSE)</option>
              <option value="ISE">Information Science (ISE)</option>
              <option value="ECE">Electronics (ECE)</option>
              <option value="ME">Mechanical (ME)</option>
              <option value="CV">Civil (CV)</option>
            </select>
          </div>
          <div class="form-group">
            <label class="field-label">Semester</label>
            <select id="reg-sem">
              <option value="1">Semester 1</option><option value="2">Semester 2</option>
              <option value="3">Semester 3</option><option value="4">Semester 4</option>
              <option value="5">Semester 5</option><option value="6">Semester 6</option>
              <option value="7">Semester 7</option><option value="8">Semester 8</option>
            </select>
          </div>
        </div>
        <div id="grade-preview" style="display:none; background:var(--b4); border:1px solid var(--border-bright); border-radius:var(--radius); padding:1rem; margin-bottom:1rem;">
          <div style="font-size:0.78rem; color:var(--text-muted); margin-bottom:8px; text-transform:uppercase; letter-spacing:0.07em;">Grade Preview</div>
          <div style="display:flex; gap:1.5rem; align-items:center;">
            <div>
              <div style="font-family:'Syne',sans-serif; font-size:2.5rem; font-weight:800; color:var(--y1);" id="prev-grade">—</div>
              <div style="font-size:0.75rem; color:var(--text-muted);">Grade</div>
            </div>
            <div>
              <div style="font-size:1rem; font-weight:600;" id="prev-remark">—</div>
              <div style="font-size:0.75rem; color:var(--text-muted);">Remark</div>
            </div>
          </div>
        </div>
        <button class="btn btn-primary" onclick="registerStudent()">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
          Register Student
        </button>
      </div>

      <div class="card">
        <div class="card-title">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
          All Registered Students
        </div>
        <div class="table-wrap">
          <table>
            <thead>
              <tr>
                <th>ID</th><th>Name</th><th>Dept</th><th>Sem</th><th>Score</th><th>Grade</th><th>Remark</th><th></th>
              </tr>
            </thead>
            <tbody id="student-table-body">
              <tr><td colspan="8"><div class="empty-state"><p>No students registered yet</p></div></td></tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- ────────── LAB 2: ENROLLMENT ────────── -->
    <div id="page-enrollment" class="page">
      <div class="page-header">
        <h1>Course Enrollment Management</h1>
        <p>Manage course enrollments with loop-based validation (max 5 per student)</p>
      </div>
      <div id="alert-enr" class="alert"></div>

      <div class="card">
        <div class="card-title">Enroll Student in Courses</div>
        <div class="form-grid">
          <div class="form-group">
            <label class="field-label">Select Student</label>
            <select id="enr-student"></select>
          </div>
          <div class="form-group">
            <label class="field-label">Course Name</label>
            <input type="text" id="enr-course" placeholder="e.g. Data Structures">
          </div>
          <div class="form-group">
            <label class="field-label">Credits (1–6)</label>
            <input type="number" id="enr-credits" placeholder="e.g. 4" min="1" max="6">
          </div>
        </div>
        <button class="btn btn-primary" onclick="addCourse()">Add Course</button>
      </div>

      <div class="card">
        <div class="card-title">Enrollment Records</div>
        <div class="table-wrap">
          <table>
            <thead><tr><th>Student</th><th>Course</th><th>Credits</th><th>Status</th><th></th></tr></thead>
            <tbody id="enr-table-body">
              <tr><td colspan="5"><div class="empty-state"><p>No enrollments yet</p></div></td></tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- ────────── LAB 3: RECORDS ────────── -->
    <div id="page-records" class="page">
      <div class="page-header">
        <h1>Academic Records Management</h1>
        <p>Store and manage student academic data using persistent backend storage</p>
      </div>
      <div id="alert-rec" class="alert"></div>

      <div class="card">
        <div class="card-title">Add / Update Academic Record</div>
        <div class="form-grid">
          <div class="form-group">
            <label class="field-label">Select Student</label>
            <select id="rec-student"></select>
          </div>
          <div class="form-group">
            <label class="field-label">Subject</label>
            <input type="text" id="rec-subject" placeholder="e.g. Mathematics">
          </div>
          <div class="form-group">
            <label class="field-label">Marks (out of 100)</label>
            <input type="number" id="rec-marks" placeholder="0–100" min="0" max="100">
          </div>
          <div class="form-group">
            <label class="field-label">Semester</label>
            <input type="number" id="rec-sem" placeholder="1–8" min="1" max="8">
          </div>
        </div>
        <button class="btn btn-primary" onclick="addRecord()">Save Record</button>
      </div>

      <div class="card">
        <div class="card-title">Academic Records</div>
        <div class="table-wrap">
          <table>
            <thead><tr><th>Student</th><th>Subject</th><th>Marks</th><th>Grade</th><th>Semester</th><th></th></tr></thead>
            <tbody id="rec-table-body">
              <tr><td colspan="6"><div class="empty-state"><p>No records yet</p></div></td></tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- ────────── LAB 4: SEARCH & SORT ────────── -->
    <div id="page-search" class="page">
      <div class="page-header">
        <h1>Search & Sort Student Data</h1>
        <p>Search by name/ID and sort by score, grade, or department</p>
      </div>

      <div class="card">
        <div class="card-title">Search & Filter</div>
        <div class="search-bar">
          <input type="text" id="search-input" placeholder="Search by name or student ID…" oninput="doSearch()">
          <select id="sort-by" onchange="doSearch()">
            <option value="name">Sort: Name (A–Z)</option>
            <option value="score-desc">Sort: Score (High–Low)</option>
            <option value="score-asc">Sort: Score (Low–High)</option>
            <option value="grade">Sort: Grade</option>
            <option value="dept">Sort: Department</option>
          </select>
        </div>
        <div class="table-wrap">
          <table>
            <thead><tr><th>Rank</th><th>ID</th><th>Name</th><th>Dept</th><th>Score</th><th>Grade</th><th>Remark</th></tr></thead>
            <tbody id="search-table-body">
              <tr><td colspan="7"><div class="empty-state"><p>Register students first</p></div></td></tr>
            </tbody>
          </table>
        </div>
        <div id="search-count" style="font-size:0.78rem; color:var(--text-muted); margin-top:0.75rem;"></div>
      </div>
    </div>

    <!-- ────────── LAB 5: FEES ────────── -->
    <div id="page-fees" class="page">
      <div class="page-header">
        <h1>Fee Calculation</h1>
        <p>Calculate tuition, hostel, and miscellaneous fees using Python functions</p>
      </div>

      <div class="card">
        <div class="card-title">Fee Calculator</div>
        <div class="form-grid">
          <div class="form-group">
            <label class="field-label">Select Student</label>
            <select id="fee-student"></select>
          </div>
          <div class="form-group">
            <label class="field-label">Hostel</label>
            <select id="fee-hostel">
              <option value="no">No Hostel</option>
              <option value="single">Single Room (₹60,000/yr)</option>
              <option value="shared">Shared Room (₹40,000/yr)</option>
            </select>
          </div>
          <div class="form-group">
            <label class="field-label">Scholarship (%)</label>
            <input type="number" id="fee-scholarship" placeholder="0–100" min="0" max="100" value="0">
          </div>
        </div>
        <button class="btn btn-primary" onclick="calcFee()">Calculate Fees</button>
      </div>

      <div class="card" id="fee-result-card" style="display:none;">
        <div class="card-title">Fee Breakdown</div>
        <div class="table-wrap">
          <table class="fee-breakdown">
            <tbody id="fee-breakdown-body"></tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- ────────── LAB 6 & 7: FILES ────────── -->
    <div id="page-files" class="page">
      <div class="page-header">
        <h1> File Management & Directory Scanning</h1>
        <p>Store academic records as files with exception handling</p>
      </div>
      <div id="alert-file" class="alert"></div>

      <div class="card">
        <div class="card-title">Create Academic Record File</div>
        <div class="form-grid">
          <div class="form-group">
            <label class="field-label">Select Student</label>
            <select id="file-student"></select>
          </div>
          <div class="form-group">
            <label class="field-label">File Tag</label>
            <select id="file-tag">
              <option>transcript</option>
              <option>result</option>
              <option>certificate</option>
              <option>report</option>
            </select>
          </div>
        </div>
        <button class="btn btn-primary" onclick="createFile()">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
          Generate File
        </button>
      </div>

      <div class="card">
        <div class="card-title">Directory — /campus/records/</div>
        <div id="file-list">
          <div class="empty-state">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"/></svg>
            <p>No files generated yet</p>
          </div>
        </div>
      </div>
    </div>

    <!-- ────────── LAB 8: ANALYTICS ────────── -->
    <div id="page-analytics" class="page">
      <div class="page-header">
        <h1>Performance Analytics</h1>
        <p>NumPy-style statistics, Pandas-style aggregations, Matplotlib-style charts</p>
      </div>

      <div class="stat-grid" id="analytics-stats">
        <div class="stat-card"><div class="stat-label">Mean Score</div><div class="stat-value" id="an-mean">—</div></div>
        <div class="stat-card"><div class="stat-label">Std Deviation</div><div class="stat-value" id="an-std">—</div></div>
        <div class="stat-card"><div class="stat-label">Median</div><div class="stat-value" id="an-med">—</div></div>
        <div class="stat-card"><div class="stat-label">Pass Rate</div><div class="stat-value" id="an-pass">—</div><div class="stat-sub">Score ≥ 40</div></div>
      </div>

      <div class="dash-grid">
        <div class="card">
          <div class="card-title">Score Distribution</div>
          <div class="chart-canvas-wrap"><canvas id="distChart"></canvas></div>
        </div>
        <div class="card">
          <div class="card-title">Dept Performance (Avg Score)</div>
          <div class="chart-canvas-wrap"><canvas id="deptChart"></canvas></div>
        </div>
      </div>

      <div class="card">
        <div class="card-title">Performance Progress Bars</div>
        <div id="perf-bars"></div>
      </div>
    </div>

    <!-- ────────── AI ADVISOR ────────── -->
    <div id="page-ai" class="page">
      <div class="page-header">
        <h1>AI Academic Advisor</h1>
        <p>Powered by Claude — ask about student performance, grades, or campus recommendations</p>
      </div>

      <div class="card">
        <div class="card-title">Ask the Advisor</div>
        <div class="form-group" style="margin-bottom:1rem;">
          <label class="field-label">Your Question</label>
          <textarea id="ai-question" placeholder="e.g. Which students need academic support? What's the grade distribution? Who are the top performers?"></textarea>
        </div>
        <div style="display:flex; gap:10px; flex-wrap:wrap; margin-bottom:1rem;">
          <button class="btn btn-outline btn-sm" onclick="setAiQ('Who are the top 3 performers?')">Top 3 performers</button>
          <button class="btn btn-outline btn-sm" onclick="setAiQ('Which students are at risk of failing?')">At-risk students</button>
          <button class="btn btn-outline btn-sm" onclick="setAiQ('Give a full performance summary')">Full summary</button>
          <button class="btn btn-outline btn-sm" onclick="setAiQ('Recommend study plans for weak students')">Study plan advice</button>
        </div>
        <button class="btn btn-primary" onclick="askAdvisor()">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
          Ask Advisor
        </button>
      </div>

      <div class="ai-panel" id="ai-panel" style="display:none;">
        <div class="ai-label">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>
          AI Response
        </div>
        <div class="ai-output" id="ai-output"></div>
      </div>
    </div>

  </main>
</div>

<!-- CHART.JS -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>

<script>
// ─── STATE ───────────────────────────────────────────────
let state = {
  students: [],
  enrollments: [],
  records: [],
  files: []
};

// ─── STORAGE ─────────────────────────────────────────────
const KEY = 'scis_data_v2';
function saveState() {
  try { localStorage.setItem(KEY, JSON.stringify(state)); } catch(e) {}
}
function loadState() {
  try {
    const raw = localStorage.getItem(KEY);
    if (raw) state = JSON.parse(raw);
  } catch(e) {}
}

// ─── NAVIGATION ──────────────────────────────────────────
function showPage(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  document.getElementById('page-' + id).classList.add('active');
  event.currentTarget.classList.add('active');
  if (id === 'dashboard') refreshDashboard();
  if (id === 'search') doSearch();
  if (id === 'analytics') refreshAnalytics();
  if (id === 'enrollment' || id === 'records' || id === 'fees' || id === 'files' || id === 'ai') refreshSelects();
}

// ─── GRADE LOGIC (Lab 1 / Python equivalent) ─────────────
function evalGrade(score) {
  if (score >= 90) return { grade: 'A', remark: 'Excellent' };
  if (score >= 75) return { grade: 'B', remark: 'Very Good' };
  if (score >= 60) return { grade: 'C', remark: 'Good' };
  if (score >= 40) return { grade: 'D', remark: 'Average' };
  return { grade: 'F', remark: 'Needs Improvement' };
}

// live preview
document.getElementById('reg-score').addEventListener('input', function() {
  const v = parseFloat(this.value);
  if (!isNaN(v) && v >= 0 && v <= 100) {
    const { grade, remark } = evalGrade(v);
    document.getElementById('prev-grade').textContent = grade;
    document.getElementById('prev-remark').textContent = remark;
    document.getElementById('grade-preview').style.display = 'block';
  } else {
    document.getElementById('grade-preview').style.display = 'none';
  }
});

// ─── REGISTRATION (Lab 1) ─────────────────────────────────
function registerStudent() {
  const name = document.getElementById('reg-name').value.trim();
  const id   = document.getElementById('reg-id').value.trim();
  const score = parseFloat(document.getElementById('reg-score').value);
  const dept = document.getElementById('reg-dept').value;
  const sem  = document.getElementById('reg-sem').value;

  if (!name || !id) return showAlert('alert-reg', 'error', 'Please fill in Name and Student ID.');
  if (isNaN(score) || score < 0 || score > 100) return showAlert('alert-reg', 'error', 'Score must be between 0 and 100.');
  if (state.students.find(s => s.id === id)) return showAlert('alert-reg', 'error', `Student ID "${id}" already exists.`);

  const { grade, remark } = evalGrade(score);
  state.students.push({ name, id, score, dept, sem, grade, remark, regDate: new Date().toLocaleDateString() });
  saveState();
  refreshStudentTable();
  refreshSelects();
  showAlert('alert-reg', 'success', `✓ ${name} registered — Grade ${grade} (${remark})`);
  ['reg-name','reg-id','reg-score'].forEach(f => document.getElementById(f).value = '');
  document.getElementById('grade-preview').style.display = 'none';
}

function deleteStudent(id) {
  state.students = state.students.filter(s => s.id !== id);
  state.enrollments = state.enrollments.filter(e => e.studentId !== id);
  state.records = state.records.filter(r => r.studentId !== id);
  saveState();
  refreshStudentTable();
  refreshSelects();
}

function refreshStudentTable() {
  const tbody = document.getElementById('student-table-body');
  if (!state.students.length) {
    tbody.innerHTML = '<tr><td colspan="8"><div class="empty-state"><p>No students registered yet</p></div></td></tr>';
    return;
  }
  tbody.innerHTML = state.students.map(s => `
    <tr>
      <td class="mono">${s.id}</td>
      <td style="font-weight:500">${s.name}</td>
      <td>${s.dept}</td>
      <td>${s.sem}</td>
      <td class="mono">${s.score}</td>
      <td><span class="badge badge-${s.grade}">${s.grade}</span></td>
      <td style="color:var(--text-muted); font-size:0.8rem">${s.remark}</td>
      <td><button class="btn btn-danger" onclick="deleteStudent('${s.id}')">Remove</button></td>
    </tr>`).join('');
}

// ─── ENROLLMENT (Lab 2) ──────────────────────────────────
function addCourse() {
  const studentId = document.getElementById('enr-student').value;
  const course = document.getElementById('enr-course').value.trim();
  const credits = parseInt(document.getElementById('enr-credits').value);

  if (!studentId) return showAlert('alert-enr', 'error', 'Select a student first.');
  if (!course) return showAlert('alert-enr', 'error', 'Enter course name.');
  if (isNaN(credits) || credits < 1 || credits > 6) return showAlert('alert-enr', 'error', 'Credits must be 1–6 (invalid entry skipped).');

  // Max 5 courses per student (break logic)
  const existing = state.enrollments.filter(e => e.studentId === studentId);
  if (existing.length >= 5) return showAlert('alert-enr', 'error', 'Maximum 5 courses per student reached (break triggered).');

  state.enrollments.push({ studentId, course, credits, date: new Date().toLocaleDateString() });
  saveState();
  refreshEnrTable();
  showAlert('alert-enr', 'success', `✓ "${course}" (${credits} credits) added.`);
  document.getElementById('enr-course').value = '';
  document.getElementById('enr-credits').value = '';
}

function refreshEnrTable() {
  const tbody = document.getElementById('enr-table-body');
  if (!state.enrollments.length) {
    tbody.innerHTML = '<tr><td colspan="5"><div class="empty-state"><p>No enrollments yet</p></div></td></tr>';
    return;
  }
  tbody.innerHTML = state.enrollments.map((e, i) => {
    const s = state.students.find(st => st.id === e.studentId) || {};
    const count = state.enrollments.filter(x => x.studentId === e.studentId).length;
    return `<tr>
      <td><span style="font-weight:500">${s.name || e.studentId}</span><br><span class="mono" style="font-size:0.72rem; color:var(--text-muted)">${e.studentId}</span></td>
      <td>${e.course}</td>
      <td class="mono">${e.credits}</td>
      <td><span class="badge badge-B">Active</span></td>
      <td><button class="btn btn-danger" onclick="removeEnrollment(${i})">Remove</button></td>
    </tr>`;
  }).join('');
}

function removeEnrollment(i) {
  state.enrollments.splice(i, 1);
  saveState();
  refreshEnrTable();
}

// ─── RECORDS (Lab 3) ──────────────────────────────────────
function addRecord() {
  const studentId = document.getElementById('rec-student').value;
  const subject = document.getElementById('rec-subject').value.trim();
  const marks = parseFloat(document.getElementById('rec-marks').value);
  const sem = document.getElementById('rec-sem').value;

  if (!studentId) return showAlert('alert-rec', 'error', 'Select a student.');
  if (!subject) return showAlert('alert-rec', 'error', 'Enter subject name.');
  if (isNaN(marks) || marks < 0 || marks > 100) return showAlert('alert-rec', 'error', 'Marks must be 0–100.');

  const { grade } = evalGrade(marks);
  state.records.push({ studentId, subject, marks, grade, sem, date: new Date().toLocaleDateString() });
  saveState();
  refreshRecTable();
  showAlert('alert-rec', 'success', `✓ Record saved for "${subject}" — Grade ${grade}`);
  ['rec-subject','rec-marks','rec-sem'].forEach(f => document.getElementById(f).value = '');
}

function refreshRecTable() {
  const tbody = document.getElementById('rec-table-body');
  if (!state.records.length) {
    tbody.innerHTML = '<tr><td colspan="6"><div class="empty-state"><p>No records yet</p></div></td></tr>';
    return;
  }
  tbody.innerHTML = state.records.map((r, i) => {
    const s = state.students.find(st => st.id === r.studentId) || {};
    return `<tr>
      <td style="font-weight:500">${s.name || r.studentId}</td>
      <td>${r.subject}</td>
      <td class="mono">${r.marks}</td>
      <td><span class="badge badge-${r.grade}">${r.grade}</span></td>
      <td>${r.sem || '—'}</td>
      <td><button class="btn btn-danger" onclick="removeRecord(${i})">Remove</button></td>
    </tr>`;
  }).join('');
}

function removeRecord(i) {
  state.records.splice(i, 1);
  saveState();
  refreshRecTable();
}

// ─── SEARCH & SORT (Lab 4) ───────────────────────────────
function doSearch() {
  const q = document.getElementById('search-input').value.toLowerCase();
  const sortBy = document.getElementById('sort-by').value;
  let list = [...state.students];

  if (q) list = list.filter(s => s.name.toLowerCase().includes(q) || s.id.toLowerCase().includes(q));

  if (sortBy === 'name') list.sort((a,b) => a.name.localeCompare(b.name));
  else if (sortBy === 'score-desc') list.sort((a,b) => b.score - a.score);
  else if (sortBy === 'score-asc') list.sort((a,b) => a.score - b.score);
  else if (sortBy === 'grade') list.sort((a,b) => a.grade.localeCompare(b.grade));
  else if (sortBy === 'dept') list.sort((a,b) => a.dept.localeCompare(b.dept));

  const tbody = document.getElementById('search-table-body');
  if (!list.length) {
    tbody.innerHTML = '<tr><td colspan="7"><div class="empty-state"><p>No results found</p></div></td></tr>';
    document.getElementById('search-count').textContent = '';
    return;
  }
  tbody.innerHTML = list.map((s, i) => `
    <tr>
      <td class="mono" style="color:var(--y2)">#${i+1}</td>
      <td class="mono">${s.id}</td>
      <td style="font-weight:500">${s.name}</td>
      <td>${s.dept}</td>
      <td class="mono">${s.score}</td>
      <td><span class="badge badge-${s.grade}">${s.grade}</span></td>
      <td style="color:var(--text-muted); font-size:0.8rem">${s.remark}</td>
    </tr>`).join('');
  document.getElementById('search-count').textContent = `Showing ${list.length} of ${state.students.length} students`;
}

// ─── FEE CALCULATION (Lab 5) ────────────────────────────
function calcFee() {
  const studentId = document.getElementById('fee-student').value;
  const hostel = document.getElementById('fee-hostel').value;
  const scholarship = parseFloat(document.getElementById('fee-scholarship').value) || 0;

  const s = state.students.find(st => st.id === studentId);
  if (!s) return;

  const tuition = 120000;
  const examFee = 5000;
  const library = 3000;
  const sports = 2000;
  let hostelFee = 0;
  if (hostel === 'single') hostelFee = 60000;
  else if (hostel === 'shared') hostelFee = 40000;

  const subtotal = tuition + examFee + library + sports + hostelFee;
  const discount = subtotal * (scholarship / 100);
  const total = subtotal - discount;

  const rows = [
    ['Tuition Fee', tuition],
    ['Examination Fee', examFee],
    ['Library Fee', library],
    ['Sports Fee', sports],
    hostelFee ? ['Hostel Fee', hostelFee] : null,
    ['Subtotal', subtotal],
    scholarship ? [`Scholarship Discount (${scholarship}%)`, -discount] : null,
    ['NET PAYABLE', total, true]
  ].filter(Boolean);

  const tbody = document.getElementById('fee-breakdown-body');
  tbody.innerHTML = rows.map(([label, amt, isTotal]) => `
    <tr class="${isTotal ? 'fee-total' : ''}">
      <td style="${isTotal ? 'font-weight:700; padding-top:12px' : ''}">${label}</td>
      <td style="${isTotal ? 'font-weight:700; padding-top:12px' : ''}; ${amt < 0 ? 'color:var(--success)' : ''}">
        ${amt < 0 ? '– ' : ''}₹${Math.abs(amt).toLocaleString('en-IN')}
      </td>
    </tr>`).join('');

  document.getElementById('fee-result-card').style.display = 'block';
}

// ─── FILES (Lab 6 & 7) ─────────────────────────────────
function createFile() {
  const studentId = document.getElementById('file-student').value;
  const tag = document.getElementById('file-tag').value;
  const s = state.students.find(st => st.id === studentId);
  if (!s) return showAlert('alert-file', 'error', 'Select a student first.');

  const filename = `${s.id}_${tag}_${Date.now()}.txt`;
  const recs = state.records.filter(r => r.studentId === studentId);
  const enrs = state.enrollments.filter(e => e.studentId === studentId);

  const content = `=== SMART CAMPUS IS — ACADEMIC RECORD ===
Student: ${s.name}  |  ID: ${s.id}  |  Dept: ${s.dept}  |  Sem: ${s.sem}
Generated: ${new Date().toLocaleString()}
Type: ${tag.toUpperCase()}

--- EXAM SCORE ---
Score: ${s.score}  |  Grade: ${s.grade}  |  Remark: ${s.remark}

--- ENROLLED COURSES ---
${enrs.length ? enrs.map(e => `  • ${e.course} (${e.credits} credits)`).join('\n') : '  No enrollments'}

--- ACADEMIC RECORDS ---
${recs.length ? recs.map(r => `  • ${r.subject}: ${r.marks}/100 (Grade ${r.grade})`).join('\n') : '  No subject records'}
`;

  state.files.push({ filename, studentId, studentName: s.name, tag, content, date: new Date().toLocaleDateString(), size: content.length });
  saveState();
  refreshFileList();
  showAlert('alert-file', 'success', `✓ File "${filename}" created successfully.`);
}

function refreshFileList() {
  const wrap = document.getElementById('file-list');
  if (!state.files.length) {
    wrap.innerHTML = `<div class="empty-state">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"/></svg>
      <p>No files generated yet</p></div>`;
    return;
  }
  wrap.innerHTML = state.files.map((f, i) => `
    <div class="file-item">
      <div class="file-icon"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/></svg></div>
      <div style="flex:1">
        <div class="file-name mono">${f.filename}</div>
        <div class="file-meta">${f.studentName} · ${f.date} · ${f.size} bytes</div>
        <div class="file-tags"><span class="file-tag">${f.tag}</span><span class="file-tag">/campus/records/</span></div>
      </div>
      <div style="display:flex; gap:6px;">
        <button class="btn btn-outline btn-sm" onclick="viewFile(${i})">View</button>
        <button class="btn btn-danger" onclick="deleteFile(${i})">Delete</button>
      </div>
    </div>`).join('');
}

function viewFile(i) {
  const f = state.files[i];
  alert(`File: ${f.filename}\n\n${f.content}`);
}
function deleteFile(i) {
  state.files.splice(i, 1);
  saveState();
  refreshFileList();
}

// ─── ANALYTICS (Lab 8) ─────────────────────────────────
let distChart, deptChart;

function refreshAnalytics() {
  const scores = state.students.map(s => s.score);
  if (!scores.length) {
    ['an-mean','an-std','an-med','an-pass'].forEach(id => document.getElementById(id).textContent = '—');
    renderPerfBars([]);
    return;
  }

  const mean = scores.reduce((a,b) => a+b, 0) / scores.length;
  const std = Math.sqrt(scores.reduce((a,b) => a + (b-mean)**2, 0) / scores.length);
  const sorted = [...scores].sort((a,b) => a-b);
  const med = sorted.length % 2 ? sorted[Math.floor(sorted.length/2)] : (sorted[sorted.length/2-1]+sorted[sorted.length/2])/2;
  const passRate = (scores.filter(s => s >= 40).length / scores.length * 100).toFixed(0);

  document.getElementById('an-mean').textContent = mean.toFixed(1);
  document.getElementById('an-std').textContent = std.toFixed(1);
  document.getElementById('an-med').textContent = med.toFixed(1);
  document.getElementById('an-pass').textContent = passRate + '%';

  const bins = [0,0,0,0,0];
  scores.forEach(s => {
    if (s < 40) bins[4]++;
    else if (s < 60) bins[3]++;
    else if (s < 75) bins[2]++;
    else if (s < 90) bins[1]++;
    else bins[0]++;
  });

  if (distChart) distChart.destroy();
  distChart = new Chart(document.getElementById('distChart'), {
    type: 'bar',
    data: {
      labels: ['A (90+)', 'B (75-89)', 'C (60-74)', 'D (40-59)', 'F (<40)'],
      datasets: [{ data: bins, backgroundColor: ['#4ade80','#FFD700','#60a5fa','#f59e0b','#ef4444'], borderRadius: 6, borderWidth: 0 }]
    },
    options: { plugins: { legend: { display: false } }, scales: { x: { grid: { color: 'rgba(255,255,255,0.05)' }, ticks: { color: '#888' } }, y: { grid: { color: 'rgba(255,255,255,0.05)' }, ticks: { color: '#888', stepSize: 1 }, beginAtZero: true } }, animation: { duration: 600 } }
  });

  const depts = {};
  state.students.forEach(s => {
    if (!depts[s.dept]) depts[s.dept] = [];
    depts[s.dept].push(s.score);
  });
  const deptLabels = Object.keys(depts);
  const deptAvgs = deptLabels.map(d => (depts[d].reduce((a,b) => a+b, 0) / depts[d].length).toFixed(1));

  if (deptChart) deptChart.destroy();
  deptChart = new Chart(document.getElementById('deptChart'), {
    type: 'bar',
    data: {
      labels: deptLabels,
      datasets: [{ data: deptAvgs, backgroundColor: '#FFD700', borderRadius: 6, borderWidth: 0 }]
    },
    options: { indexAxis: 'y', plugins: { legend: { display: false } }, scales: { x: { grid: { color: 'rgba(255,255,255,0.05)' }, ticks: { color: '#888' }, max: 100 }, y: { grid: { color: 'rgba(255,255,255,0.05)' }, ticks: { color: '#888' } } }, animation: { duration: 600 } }
  });

  renderPerfBars(state.students);
}

function renderPerfBars(students) {
  const wrap = document.getElementById('perf-bars');
  if (!students.length) { wrap.innerHTML = '<div class="empty-state"><p>No students to analyze</p></div>'; return; }
  const sorted = [...students].sort((a,b) => b.score - a.score);
  wrap.innerHTML = sorted.map(s => `
    <div style="margin-bottom:0.85rem;">
      <div style="display:flex; justify-content:space-between; margin-bottom:4px; font-size:0.82rem;">
        <span style="font-weight:500">${s.name}</span>
        <span class="mono" style="color:var(--y1)">${s.score} / 100</span>
      </div>
      <div class="progress-bg">
        <div class="progress-fill" style="width:${s.score}%; background:${s.score>=75?'#FFD700':s.score>=40?'#f59e0b':'#ef4444'}"></div>
      </div>
    </div>`).join('');
}

// ─── DASHBOARD ─────────────────────────────────────────
let gradeChart;
function refreshDashboard() {
  document.getElementById('stat-students').textContent = state.students.length;
  document.getElementById('stat-courses').textContent = state.enrollments.length;

  const scores = state.students.map(s => s.score);
  if (scores.length) {
    const avg = (scores.reduce((a,b)=>a+b,0)/scores.length).toFixed(1);
    const top = state.students.reduce((a,b)=>a.score>b.score?a:b);
    document.getElementById('stat-avg').textContent = avg;
    document.getElementById('stat-top').textContent = top.name.split(' ')[0];
  } else {
    document.getElementById('stat-avg').textContent = '—';
    document.getElementById('stat-top').textContent = '—';
  }

  const bins = { A:0, B:0, C:0, D:0, F:0 };
  state.students.forEach(s => bins[s.grade]++);

  if (gradeChart) gradeChart.destroy();
  gradeChart = new Chart(document.getElementById('gradeChart'), {
    type: 'doughnut',
    data: {
      labels: ['A', 'B', 'C', 'D', 'F'],
      datasets: [{ data: Object.values(bins), backgroundColor: ['#4ade80','#FFD700','#60a5fa','#f59e0b','#ef4444'], borderWidth: 0, hoverOffset: 4 }]
    },
    options: { cutout: '65%', plugins: { legend: { position: 'bottom', labels: { color: '#888', padding: 12, font: { size: 12 } } } }, animation: { duration: 600 } }
  });

  const recent = document.getElementById('recent-list');
  if (!state.students.length) {
    recent.innerHTML = '<div class="empty-state"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg><p>No students yet.</p></div>';
    return;
  }
  const last5 = [...state.students].reverse().slice(0,5);
  recent.innerHTML = last5.map(s => `
    <div style="display:flex; align-items:center; justify-content:space-between; padding:0.6rem 0; border-bottom:1px solid rgba(255,215,0,0.05);">
      <div>
        <div style="font-weight:500; font-size:0.875rem">${s.name}</div>
        <div style="font-size:0.72rem; color:var(--text-muted)">${s.id} · ${s.dept}</div>
      </div>
      <span class="badge badge-${s.grade}">${s.grade} — ${s.score}</span>
    </div>`).join('');
}

// ─── SELECTS REFRESH ────────────────────────────────────
function refreshSelects() {
  const ids = ['enr-student','rec-student','fee-student','file-student'];
  ids.forEach(id => {
    const el = document.getElementById(id);
    if (!el) return;
    const prev = el.value;
    el.innerHTML = state.students.length
      ? state.students.map(s => `<option value="${s.id}">${s.name} (${s.id})</option>`).join('')
      : '<option value="">— No students registered —</option>';
    if (prev) el.value = prev;
  });
}

// ─── AI ADVISOR ─────────────────────────────────────────
function setAiQ(q) { document.getElementById('ai-question').value = q; }

async function askAdvisor() {
  const q = document.getElementById('ai-question').value.trim();
  if (!q) return;

  const panel = document.getElementById('ai-panel');
  const out = document.getElementById('ai-output');
  panel.style.display = 'block';
  out.innerHTML = '<span class="ai-loading">Analyzing campus data…</span>';

  const context = `You are an AI academic advisor for Dayananda Sagar College of Engineering's Smart Campus Information System.

Current campus data:
- Total students: ${state.students.length}
- Students: ${JSON.stringify(state.students.map(s => ({ name: s.name, id: s.id, score: s.score, grade: s.grade, dept: s.dept, remark: s.remark })))}
- Total enrollments: ${state.enrollments.length}
- Academic records: ${state.records.length} entries
- Departments: ${[...new Set(state.students.map(s => s.dept))].join(', ') || 'None'}

Grade scale: A=90-100(Excellent), B=75-89(Very Good), C=60-74(Good), D=40-59(Average), F=<40(Needs Improvement)

Answer the administrator's question clearly, concisely, and helpfully using the data above. If no students exist, say so.`;

  try {
    const resp = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: 1000,
        system: context,
        messages: [{ role: 'user', content: q }]
      })
    });
    const data = await resp.json();
    const text = data.content?.map(c => c.text || '').join('') || 'No response received.';
    out.textContent = text;
  } catch (e) {
    out.innerHTML = '<span style="color:var(--danger)">Error connecting to AI. Please try again.</span>';
  }
}

// ─── ALERTS ─────────────────────────────────────────────
function showAlert(id, type, msg) {
  const el = document.getElementById(id);
  el.className = `alert alert-${type} show`;
  el.textContent = msg;
  setTimeout(() => { el.className = 'alert'; }, 4000);
}

// ─── INIT ───────────────────────────────────────────────
loadState();
refreshStudentTable();
refreshEnrTable();
refreshRecTable();
refreshFileList();
refreshDashboard();
refreshSelects();
</script>
</body>
</html>
