# Rotulos-Iris2
<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />
  <title>Rótulos Iris · App sincronizada</title>
  <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@1"></script>
  <meta name="theme-color" content="#0f172a" />

  <style>
    :root{
      --bg:#f3f6fb;
      --panel:#ffffff;
      --panel-2:#f8fbff;
      --text:#0f172a;
      --muted:#64748b;
      --line:#e2e8f0;
      --primary:#2563eb;
      --primary-2:#1d4ed8;
      --success:#16a34a;
      --success-2:#15803d;
      --warning:#f59e0b;
      --danger:#dc2626;
      --shadow:0 14px 36px rgba(15,23,42,.08);
      --radius:20px;
    }

    *{box-sizing:border-box}
    html,body{
      margin:0;
      padding:0;
      background:var(--bg);
      color:var(--text);
      font-family:Inter,ui-sans-serif,system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;
    }

    body{
      min-height:100vh;
    }

    .app-shell{
      min-height:100vh;
    }

    .wrap{
      width:min(1380px,100%);
      margin:0 auto;
      padding:22px;
    }

    .topbar{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:16px;
      margin-bottom:20px;
    }

    .brand{
      display:flex;
      align-items:center;
      gap:14px;
      min-width:0;
    }

    .logo{
      width:56px;
      height:56px;
      border-radius:18px;
      background:linear-gradient(135deg,#2563eb,#22c55e);
      color:#fff;
      display:grid;
      place-items:center;
      font-weight:800;
      font-size:22px;
      box-shadow:var(--shadow);
      flex:0 0 auto;
    }

    .brand-copy{
      min-width:0;
    }

    .brand-copy h1{
      margin:0;
      font-size:38px;
      line-height:1.05;
      letter-spacing:-.03em;
    }

    .brand-copy p{
      margin:8px 0 0;
      color:var(--muted);
      font-size:15px;
    }

    .userbox{
      display:flex;
      align-items:center;
      gap:10px;
      flex-wrap:wrap;
      justify-content:flex-end;
    }

    .chip{
      display:inline-flex;
      align-items:center;
      gap:8px;
      background:#eef4ff;
      color:#1e3a8a;
      border:1px solid #dbeafe;
      padding:8px 12px;
      border-radius:999px;
      font-size:13px;
      font-weight:700;
    }

    .chip.gray{
      background:#f8fafc;
      color:#334155;
      border-color:#e2e8f0;
    }

    .layout{
      display:grid;
      grid-template-columns:280px 1fr;
      gap:20px;
      align-items:start;
    }

    .sidebar,
    .panel,
    .hero,
    .kpi,
    .job-card,
    .task-card,
    .login-card{
      background:var(--panel);
      border:1px solid rgba(226,232,240,.95);
      box-shadow:var(--shadow);
      border-radius:var(--radius);
    }

    .sidebar{
      padding:16px;
      position:sticky;
      top:18px;
    }

    .nav-title{
      margin:4px 0 12px;
      font-size:13px;
      color:var(--muted);
      text-transform:uppercase;
      letter-spacing:.08em;
      font-weight:800;
    }

    .nav{
      display:grid;
      gap:8px;
    }

    .nav button{
      width:100%;
      text-align:left;
      border:none;
      background:#f8fafc;
      color:#0f172a;
      padding:14px 16px;
      border-radius:14px;
      cursor:pointer;
      font-size:15px;
      font-weight:700;
      transition:.18s ease;
    }

    .nav button:hover{
      background:#eef4ff;
      transform:translateY(-1px);
    }

    .nav button.active{
      background:linear-gradient(135deg,#2563eb,#1d4ed8);
      color:#fff;
    }

    .side-meta{
      margin-top:18px;
      padding-top:18px;
      border-top:1px solid var(--line);
      display:grid;
      gap:8px;
      color:var(--muted);
      font-size:14px;
    }

    .content{
      display:grid;
      gap:18px;
    }

    .hero{
      padding:18px;
      display:grid;
      gap:16px;
      background:
        radial-gradient(circle at top right, rgba(37,99,235,.08), transparent 38%),
        radial-gradient(circle at bottom left, rgba(34,197,94,.08), transparent 32%),
        var(--panel);
    }

    .kpis{
      display:grid;
      grid-template-columns:repeat(5,1fr);
      gap:14px;
    }

    .kpi{
      padding:16px;
      background:linear-gradient(180deg,#ffffff,#f8fbff);
    }

    .kpi .label{
      font-size:13px;
      color:var(--muted);
      font-weight:700;
      margin-bottom:10px;
    }

    .kpi .value{
      font-size:34px;
      line-height:1;
      font-weight:800;
      letter-spacing:-.04em;
    }

    .panel{
      padding:18px;
    }

    .panel h2{
      margin:0 0 6px;
      font-size:28px;
      letter-spacing:-.03em;
    }

    .subtext{
      margin:0;
      color:var(--muted);
      font-size:14px;
    }

    .toolbar{
      margin-top:16px;
      display:grid;
      grid-template-columns:1.2fr 1fr 1fr auto;
      gap:12px;
    }

    .grid-2{
      display:grid;
      grid-template-columns:1.2fr .8fr;
      gap:14px;
    }

    .grid-3{
      display:grid;
      grid-template-columns:repeat(3,1fr);
      gap:14px;
    }

    .jobs-list{
      display:grid;
      gap:16px;
      margin-top:18px;
    }

    .job-card{
      padding:18px;
      overflow:hidden;
    }

    .job-top{
      display:flex;
      align-items:flex-start;
      justify-content:space-between;
      gap:16px;
      flex-wrap:wrap;
    }

    .job-title{
      margin:0;
      font-size:32px;
      line-height:1.05;
      letter-spacing:-.03em;
    }

    .job-badges{
      display:flex;
      flex-wrap:wrap;
      gap:8px;
      margin-top:10px;
    }

    .badge{
      display:inline-flex;
      align-items:center;
      gap:7px;
      border-radius:999px;
      padding:7px 10px;
      font-size:12px;
      font-weight:800;
      background:#f8fafc;
      border:1px solid #e2e8f0;
      color:#334155;
    }

    .badge.primary{background:#eff6ff;border-color:#dbeafe;color:#1d4ed8}
    .badge.success{background:#f0fdf4;border-color:#dcfce7;color:#166534}
    .badge.warning{background:#fffbeb;border-color:#fde68a;color:#92400e}
    .badge.dark{background:#e2e8f0;border-color:#cbd5e1;color:#0f172a}

    .job-desc{
      margin:12px 0 0;
      color:#334155;
      font-size:15px;
      line-height:1.5;
    }

    .job-times{
      display:grid;
      gap:8px;
      min-width:260px;
      text-align:right;
      color:#334155;
      font-size:14px;
      font-weight:700;
    }

    .job-actions{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      margin-top:16px;
    }

    .tasks-grid{
      margin-top:16px;
      display:grid;
      grid-template-columns:repeat(3,1fr);
      gap:14px;
    }

    .task-card{
      padding:16px;
      background:linear-gradient(180deg,#ffffff,#fbfdff);
    }

    .task-title{
      margin:0 0 10px;
      font-size:18px;
      letter-spacing:-.02em;
    }

    .time-label{
      color:var(--muted);
      font-size:13px;
      font-weight:700;
      margin-top:6px;
    }

    .time-value{
      margin-top:6px;
      font-size:46px;
      line-height:1;
      font-weight:900;
      letter-spacing:-.05em;
    }

    .task-status{
      margin-top:10px;
      font-size:14px;
      font-weight:700;
      color:#334155;
    }

    .task-actions{
      margin-top:14px;
      display:grid;
      grid-template-columns:1fr 1fr;
      gap:10px;
    }

    .manual-grid,
    .hours-grid{
      display:grid;
      grid-template-columns:1fr 1fr auto;
      gap:10px;
      margin-top:14px;
    }

    details{
      margin-top:14px;
      border-top:1px solid var(--line);
      padding-top:14px;
    }

    summary{
      cursor:pointer;
      user-select:none;
      font-weight:800;
      color:#0f172a;
    }

    .hours-meta{
      margin-top:10px;
      color:var(--muted);
      font-size:13px;
      line-height:1.5;
    }

    .report-grid{
      margin-top:18px;
      display:grid;
      grid-template-columns:repeat(2,1fr);
      gap:14px;
    }

    .report-card{
      background:#fff;
      border:1px solid var(--line);
      border-radius:18px;
      padding:16px;
    }

    .report-card h3{
      margin:0 0 12px;
      font-size:18px;
    }

    .report-list{
      display:grid;
      gap:8px;
    }

    .report-row{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:12px;
      padding:10px 12px;
      background:#f8fafc;
      border:1px solid #e2e8f0;
      border-radius:12px;
      font-size:14px;
    }

    .login-shell{
      min-height:100vh;
      display:grid;
      place-items:center;
      padding:22px;
      background:
        radial-gradient(circle at top left, rgba(37,99,235,.10), transparent 30%),
        radial-gradient(circle at bottom right, rgba(34,197,94,.10), transparent 28%),
        var(--bg);
    }

    .login-card{
      width:min(520px,100%);
      padding:24px;
    }

    .login-card h2{
      margin:0 0 8px;
      font-size:34px;
      letter-spacing:-.04em;
    }

    .login-card p{
      margin:0 0 18px;
      color:var(--muted);
      line-height:1.5;
    }

    label{
      display:block;
      margin:14px 0 8px;
      font-size:14px;
      font-weight:800;
      color:#0f172a;
    }

    input,
    select,
    textarea,
    button{
      font:inherit;
    }

    input,
    select,
    textarea{
      width:100%;
      border:1px solid #dbe3ee;
      background:#fff;
      color:#0f172a;
      border-radius:14px;
      padding:13px 14px;
      outline:none;
      transition:border-color .18s ease, box-shadow .18s ease, transform .18s ease;
    }

    input:focus,
    select:focus,
    textarea:focus{
      border-color:#93c5fd;
      box-shadow:0 0 0 4px rgba(37,99,235,.10);
    }

    textarea{
      min-height:110px;
      resize:vertical;
    }

    .btn{
      border:none;
      border-radius:14px;
      padding:13px 16px;
      font-weight:800;
      cursor:pointer;
      transition:transform .18s ease, opacity .18s ease, box-shadow .18s ease, background .18s ease;
      box-shadow:0 8px 18px rgba(15,23,42,.08);
    }

    .btn:hover{transform:translateY(-1px)}
    .btn:disabled{opacity:.55;cursor:not-allowed;transform:none}

    .btn-primary{background:linear-gradient(135deg,var(--primary),var(--primary-2));color:#fff}
    .btn-success{background:linear-gradient(135deg,var(--success),var(--success-2));color:#fff}
    .btn-warning{background:linear-gradient(135deg,#f59e0b,#d97706);color:#fff}
    .btn-danger{background:linear-gradient(135deg,#ef4444,#dc2626);color:#fff}
    .btn-soft{background:#eef4ff;color:#1d4ed8}
    .btn-gray{background:#e2e8f0;color:#475569}

    .worker-picker{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      margin-top:6px;
    }

    .worker-pill{
      display:inline-flex;
      align-items:center;
      gap:8px;
      padding:10px 12px;
      border-radius:999px;
      border:1px solid #dbe3ee;
      background:#fff;
      cursor:pointer;
      font-weight:700;
      color:#334155;
      user-select:none;
    }

    .worker-pill input{display:none}
    .worker-pill.active{
      background:#eff6ff;
      border-color:#93c5fd;
      color:#1d4ed8;
    }

    .empty{
      padding:28px;
      border:1px dashed #cbd5e1;
      border-radius:16px;
      text-align:center;
      color:var(--muted);
      background:#f8fafc;
      margin-top:16px;
    }

    .muted{color:var(--muted)}
    .hidden{display:none !important}
    .mt-14{margin-top:14px}
    .mt-18{margin-top:18px}
    .mt-22{margin-top:22px}

    .error-box{
      margin-top:14px;
      border:1px solid #fecaca;
      background:#fef2f2;
      color:#991b1b;
      border-radius:14px;
      padding:12px 14px;
      font-size:14px;
      font-weight:700;
    }

    .ok-box{
      margin-top:14px;
      border:1px solid #bbf7d0;
      background:#f0fdf4;
      color:#166534;
      border-radius:14px;
      padding:12px 14px;
      font-size:14px;
      font-weight:700;
    }

    @media (max-width:1180px){
      .kpis{grid-template-columns:repeat(3,1fr)}
      .tasks-grid{grid-template-columns:1fr 1fr}
      .report-grid{grid-template-columns:1fr}
    }

    @media (max-width:900px){
      .layout{grid-template-columns:1fr}
      .sidebar{position:static}
      .toolbar,
      .grid-2,
      .grid-3{grid-template-columns:1fr}
      .job-top{flex-direction:column}
      .job-times{text-align:left;min-width:0}
      .kpis{grid-template-columns:1fr 1fr}
    }

    @media (max-width:680px){
      .wrap{padding:12px}
      .topbar{align-items:flex-start;flex-direction:column}
      .brand-copy h1{font-size:28px}
      .brand-copy p{font-size:13px}
      .sidebar,
      .panel,
      .hero,
      .job-card,
      .task-card,
      .login-card{border-radius:18px}
      .kpis,
      .tasks-grid,
      .task-actions,
      .manual-grid,
      .hours-grid{grid-template-columns:1fr}
      .kpi .value{font-size:28px}
      .time-value{font-size:38px}
      .btn{width:100%}
      input,select,textarea{font-size:16px}
      .userbox{width:100%;justify-content:flex-start}
      .job-title{font-size:24px}
    }
  </style>
</head>
<body>
  <div id="app"></div>

  <script type="module">
    import { createClient } from 'https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2/+esm';

    const SUPABASE_URL = 'https://zfdusqdyaauwdhegzdvi.supabase.co';
    const SUPABASE_ANON_KEY = 'sb_publishable_6_ewdXEtND8whXtkNqzLgg_oSEKnvF_';

    const PROJECT_TYPES = [
      'Vinilo',
      'Cristalera',
      'Vehículo',
      'Lona',
      'Letras corpóreas',
      'Señalética',
      'Impresión',
      'Otro'
    ];

    const DEFAULT_TASKS = ['Tarea 1', 'Tarea 2', 'Tarea 3'];

    const state = {
      view: 'trabajos',
      session: null,
      profile: null,
      profiles: [],
      jobs: [],
      loading: true,
      error: '',
      info: '',
      filters: {
        search: '',
        user: 'all',
        type: 'all'
      }
    };

    const app = document.getElementById('app');
    const supabase = window.supabase.createClient(SUPABASE_URL, SUPABASE_ANON_KEY);
    let tickTimer = null;
    let realtimeChannel = null;

    function esc(value){
      return String(value ?? '').replace(/[&<>"']/g, ch => ({
        '&':'&amp;',
        '<':'&lt;',
        '>':'&gt;',
        '"':'&quot;',
        "'":'&#39;'
      }[ch]));
    }

    function fmtDate(iso){
      if(!iso) return '—';
      const d = new Date(iso);
      return Number.isNaN(d.getTime()) ? '—' : d.toLocaleString('es-ES');
    }

    function toDatetimeLocal(iso){
      if(!iso) return '';
      const d = new Date(iso);
      if(Number.isNaN(d.getTime())) return '';
      const offset = d.getTimezoneOffset();
      const local = new Date(d.getTime() - offset * 60000);
      return local.toISOString().slice(0,16);
    }

    function fromDatetimeLocal(value){
      if(!value) return null;
      const d = new Date(value);
      return Number.isNaN(d.getTime()) ? null : d.toISOString();
    }

    function hms(ms){
      const safe = Math.max(0, Math.floor(ms || 0));
      const sec = Math.floor(safe / 1000);
      const hh = String(Math.floor(sec / 3600)).padStart(2,'0');
      const mm = String(Math.floor((sec % 3600) / 60)).padStart(2,'0');
      const ss = String(sec % 60).padStart(2,'0');
      return `${hh}:${mm}:${ss}`;
    }

    function hoursDecimal(ms){
      return ((ms || 0) / 3600000).toFixed(1).replace('.', ',');
    }

    function normalizeAssignedTo(value){
      if(!value) return [];
      if(Array.isArray(value)) return value.filter(Boolean);
      return [value].filter(Boolean);
    }

    function profileNameById(id){
      const found = state.profiles.find(p => String(p.id) === String(id));
      return found?.display_name || 'Usuario';
    }

    function assignedNames(ids){
      return normalizeAssignedTo(ids).map(profileNameById);
    }

    function currentUserId(){
      return state.session?.user?.id || null;
    }

    function isGeneral(){
      return state.profile?.role === 'general';
    }

    function isWorker(){
      return state.profile?.role === 'worker';
    }

    function taskMyTime(task){
      return (task.user_times || []).find(
        x => String(x.user_id) === String(currentUserId())
      ) || null;
    }

    function taskTotalMs(task){
      if(!task.user_times?.length) return 0;

      return task.user_times.reduce((total, row) => {
        if(row.started_at_ms){
          return total + (row.elapsed_ms || 0) + (Date.now() - row.started_at_ms);
        }
        return total + (row.elapsed_ms || 0);
      }, 0);
    }

    function taskMyMs(task){
      const row = taskMyTime(task);
      if(!row) return 0;
      if(row.started_at_ms){
        return (row.elapsed_ms || 0) + (Date.now() - row.started_at_ms);
      }
      return row.elapsed_ms || 0;
    }

    function taskIsRunningForMe(task){
      const row = taskMyTime(task);
      return !!row?.started_at_ms;
    }

    function jobTotalMs(job){
      return (job.tasks || []).reduce((sum, task) => sum + taskTotalMs(task), 0);
    }

    function visibleJobs(){
      let rows = [...state.jobs];

      if(isWorker()){
        rows = rows.filter(job =>
          normalizeAssignedTo(job.assigned_to).some(id => String(id) === String(currentUserId()))
        );
      }

      const q = state.filters.search.trim().toLowerCase();
      if(q){
        rows = rows.filter(job => {
          const haystack = [
            job.name,
            job.project_type,
            job.operario,
            job.description,
            ...assignedNames(job.assigned_to),
            ...(job.tasks || []).map(t => t.name)
          ].join(' ').toLowerCase();
          return haystack.includes(q);
        });
      }

      if(state.filters.type !== 'all'){
        rows = rows.filter(job => job.project_type === state.filters.type);
      }

      if(isGeneral() && state.filters.user !== 'all'){
        rows = rows.filter(job =>
          normalizeAssignedTo(job.assigned_to).some(id => String(id) === String(state.filters.user))
        );
      }

      return rows;
    }

    function workerProfiles(){
      return state.profiles.filter(p => p.role === 'worker');
    }

    function metrics(){
      const rows = visibleJobs();
      const totalMs = rows.reduce((sum, job) => sum + jobTotalMs(job), 0);
      const activeTasks = rows.reduce((sum, job) => {
        return sum + (job.tasks || []).filter(t => (t.user_times || []).some(x => !!x.started_at_ms)).length;
      }, 0);

      const visibleUsers = new Set();
      rows.forEach(job => normalizeAssignedTo(job.assigned_to).forEach(id => visibleUsers.add(String(id))));

      return {
        jobs: rows.length,
        totalMs,
        activeTasks,
        users: visibleUsers.size,
        jobsWithHours: rows.filter(job => jobTotalMs(job) > 0).length
      };
    }

    function clearNotice(){
      state.error = '';
      state.info = '';
    }

    async function initSupabase(){
      if(!SUPABASE_URL || !SUPABASE_ANON_KEY || SUPABASE_ANON_KEY.includes('sb_publishable_6_ewdXEtND8whXtkNqzLgg_oSEKnvF_')){
        state.loading = false;
        state.error = 'Falta pegar la publishable key de Supabase en el index.html.';
        render();
        return;
      }

      supabase = createClient(SUPABASE_URL, SUPABASE_ANON_KEY);
      const { data } = await supabase.auth.getSession();
      state.session = data.session || null;

      supabase.auth.onAuthStateChange((_event, session) => {
        state.session = session || null;
        bootstrap();
      });

      bootstrap();
    }

    async function bootstrap(){
      clearNotice();
      state.loading = true;
      render();

      if(!supabase){
        state.loading = false;
        render();
        return;
      }

      if(!state.session){
        state.profile = null;
        state.profiles = [];
        state.jobs = [];
        state.loading = false;
        renderLogin();
        stopTicking();
        await bindRealtime(false);
        return;
      }

      const uid = currentUserId();

      const [
        profileRes,
        profilesRes,
        jobsRes
      ] = await Promise.all([
        supabase.from('profiles').select('*').eq('id', uid).maybeSingle(),
        supabase.from('profiles').select('*').order('display_name', { ascending:true }),
        supabase
          .from('jobs')
          .select(`
            *,
            tasks (
              *,
              user_times:task_user_times (*)
            )
          `)
          .order('created_at', { ascending:false })
      ]);

      if(profileRes.error){
        state.error = profileRes.error.message;
      }

      if(profilesRes.error && !state.error){
        state.error = profilesRes.error.message;
      }

      if(jobsRes.error && !state.error){
        state.error = jobsRes.error.message;
      }

      state.profile = profileRes.data || null;
      state.profiles = profilesRes.data || [];
      state.jobs = (jobsRes.data || []).map(job => ({
        ...job,
        assigned_to: normalizeAssignedTo(job.assigned_to),
        tasks: (job.tasks || [])
          .map(task => ({
            ...task,
            user_times: task.user_times || []
          }))
          .sort((a,b) => (a.task_order || 0) - (b.task_order || 0))
      }));

      if(!isGeneral() && state.view === 'informes'){
        state.view = 'trabajos';
      }

      state.loading = false;
      render();
      startTicking();
      await bindRealtime(true);
    }

    function startTicking(){
      stopTicking();
      tickTimer = setInterval(() => {
        refreshLiveTimes();
      }, 1000);
    }

    function stopTicking(){
      if(tickTimer){
        clearInterval(tickTimer);
        tickTimer = null;
      }
    }

    async function bindRealtime(enabled){
      if(realtimeChannel){
        await supabase.removeChannel(realtimeChannel);
        realtimeChannel = null;
      }

      if(!enabled || !supabase) return;
      realtimeChannel = supabase
        .channel('realtime-iris')
        .on('postgres_changes', { event: '*', schema: 'public', table: 'jobs' }, bootstrap)
        .on('postgres_changes', { event: '*', schema: 'public', table: 'tasks' }, bootstrap)
        .on('postgres_changes', { event: '*', schema: 'public', table: 'task_user_times' }, bootstrap)
        .subscribe();
    }

    async function login(email, password){
      clearNotice();
      render();

      const { data, error } = await supabase.auth.signInWithPassword({
  email: email,
  password: password
});



if(error){
  state.error = error.message;
  render();
} else {
  state.user = data.user;
  state.view = 'trabajos';
  render();
}
}


    async function logout(){
      await supabase.auth.signOut();
      state.view = 'trabajos';
      clearNotice();
      render();
    }

    async function createJob(form){
      clearNotice();

      const name = form.name.value.trim();
      if(!name){
        state.error = 'Pon un nombre al trabajo.';
        render();
        return;
      }

      const assigned = Array.from(
        form.querySelectorAll('input[name="assigned"]:checked')
      ).map(i => i.value);

      if(!assigned.length){
        state.error = 'Selecciona al menos un operario.';
        render();
        return;
      }

      const { data: job, error } = await supabase
        .from('jobs')
        .insert({
          name,
          project_type: form.project_type.value || null,
          operario: form.operario.value.trim() || null,
          description: form.description.value.trim() || null,
          assigned_to: assigned,
          created_by: currentUserId()
        })
        .select()
        .single();

      if(error){
        state.error = error.message;
        render();
        return;
      }

      const tasks = DEFAULT_TASKS.map((name, i) => ({
        job_id: job.id,
        name,
        task_order: i + 1,
        created_by: currentUserId()
      }));

      const { data: createdTasks } = await supabase
        .from('tasks')
        .insert(tasks)
        .select();

      const rows = [];
      for(const task of createdTasks || []){
        for(const uid of assigned){
          rows.push({
            task_id: task.id,
            user_id: uid,
            elapsed_ms: 0,
            running: false
          });
        }
      }

      if(rows.length){
        await supabase.from('task_user_times').insert(rows);
      }

      form.reset();
      state.info = 'Trabajo creado correctamente';
      bootstrap();
    }

    async function deleteJob(jobId){
      if(!confirm('¿Eliminar este trabajo?')) return;

      await supabase.from('jobs').delete().eq('id', jobId);
      bootstrap();
    }

    async function updateTaskName(taskId, value){
      await supabase.from('tasks').update({ name: value }).eq('id', taskId);
    }

    async function startTask(task){
      const row = taskMyTime(task);
      if(!row) return;

      await supabase
        .from('task_user_times')
        .update({
          started_at_ms: Date.now(),
          running: true
        })
        .eq('id', row.id);
    }

    async function stopTask(task){
      const row = taskMyTime(task);
      if(!row) return;

      const extra = row.started_at_ms ? (Date.now() - row.started_at_ms) : 0;

      await supabase
        .from('task_user_times')
        .update({
          elapsed_ms: (row.elapsed_ms || 0) + extra,
          started_at_ms: null,
          running: false
        })
        .eq('id', row.id);
    }

    async function manualTime(task, h, m){
      const ms = (Number(h || 0) * 3600000) + (Number(m || 0) * 60000);

      const rows = task.user_times || [];
      if(!rows.length) return;

      const each = Math.floor(ms / rows.length);

      for(const r of rows){
        await supabase
          .from('task_user_times')
          .update({
            elapsed_ms: each,
            started_at_ms: null,
            running: false
          })
          .eq('id', r.id);
      }
    }

    async function updateActualTimes(task, start, end){
      await supabase
        .from('tasks')
        .update({
          actual_start: start,
          actual_end: end
        })
        .eq('id', task.id);
    }

    function refreshLiveTimes(){
      document.querySelectorAll('[data-live-ms]').forEach(el => {
        const ms = Number(el.dataset.liveMs || 0);
        el.textContent = hms(ms);
      });
    }

    function renderLogin(){
      app.innerHTML = `
        <div class="login-shell">
          <div class="login-card">
            <h2>Iniciar sesión</h2>
            <p>Accede con tu usuario para ver tus trabajos.</p>

            ${state.error ? `<div class="error-box">${esc(state.error)}</div>` : ''}

            <form id="login-form">
              <label>Email</label>
              <input type="email" name="email" required />

              <label>Contraseña</label>
              <input type="password" name="password" required />

              <div class="mt-18">
                <button class="btn btn-primary" style="width:100%">Entrar</button>
              </div>
            </form>
          </div>
        </div>
      `;

      document.getElementById('login-form').onsubmit = e => {
        e.preventDefault();
        login(e.target.email.value, e.target.password.value);
      };
    }
    function renderHeader(){
      return `
        <div class="topbar">
          <div>
            <div class="title">Rótulos Iris</div>
            <div class="subtitle">
              ${esc(state.profile?.display_name || '')}
            </div>
          </div>

          <div style="display:flex; gap:10px;">
            <select onchange="state.selectedUser=this.value; render()">
              <option value="all">Todos</option>
              ${state.profiles.map(p => `
                <option value="${p.id}" ${state.selectedUser===p.id?'selected':''}>
                  ${esc(p.display_name)}
                </option>
              `).join('')}
            </select>

            <button class="btn btn-ghost" onclick="logout()">Salir</button>
          </div>
        </div>
      `;
    }

    function renderCreateJob(){
      if(!isGeneral()) return '';

      return `
        <div class="card">
          <h3>Nuevo trabajo</h3>

          <form id="job-form">
            <input name="name" placeholder="Nombre" required />
            <input name="project_type" placeholder="Tipo (Vinilo...)" />
            <input name="operario" placeholder="Operario" />
            <textarea name="description" placeholder="Descripción"></textarea>

            <div class="mt-12">
              <strong>Asignar a:</strong><br>
              ${state.profiles.map(p => `
                <label style="display:block">
                  <input type="checkbox" name="assigned" value="${p.id}">
                  ${esc(p.display_name)}
                </label>
              `).join('')}
            </div>

            <div class="mt-18">
              <button class="btn btn-primary">Crear trabajo</button>
            </div>
          </form>
        </div>
      `;
    }

    function renderTask(task, job){
      const rows = task.user_times || [];

      const total = rows.reduce((sum, r) => {
        if(r.running && r.started_at_ms){
          return sum + (r.elapsed_ms || 0) + (Date.now() - r.started_at_ms);
        }
        return sum + (r.elapsed_ms || 0);
      }, 0);

      const my = taskMyTime(task);
      const running = my?.running;

      return `
        <div class="task">
          <input value="${esc(task.name)}"
            onblur="updateTaskName('${task.id}', this.value)" />

          <div class="mini">Tiempo acumulado</div>
          <div class="time" data-live-ms="${total}">
            ${hms(total)}
          </div>

          <div class="mini">
            ${running ? '🟢 Activo' : '⏸️ Parado'}
          </div>

          <div class="task-actions">
            ${
              my
              ? (
                  running
                  ? `<button class="btn btn-amber" onclick="stopTask(${JSON.stringify(task)})">Parar</button>`
                  : `<button class="btn btn-green" onclick="startTask(${JSON.stringify(task)})">Inicio</button>`
                )
              : ''
            }
          </div>

          <div class="manual">
            <input id="h_${task.id}" placeholder="h">
            <input id="m_${task.id}" placeholder="m">

            <button class="btn btn-soft"
              onclick="manualTime(
                ${JSON.stringify(task)},
                document.getElementById('h_${task.id}').value,
                document.getElementById('m_${task.id}').value
              )">
              Modificar
            </button>
          </div>

          ${
            isGeneral()
            ? `
              <details>
                <summary>Horas reales</summary>

                <input type="datetime-local" id="s_${task.id}">
                <input type="datetime-local" id="e_${task.id}">

                <button class="btn btn-soft"
                  onclick="updateActualTimes(
                    ${JSON.stringify(task)},
                    document.getElementById('s_${task.id}').value,
                    document.getElementById('e_${task.id}').value
                  )">
                  Guardar
                </button>
              </details>
            `
            : ''
          }
        </div>
      `;
    }
    function renderJobs(){
      return state.jobs.map(job => {
        const tasks = state.tasks
          .filter(t => t.job_id === job.id)
          .map(t => ({
            ...t,
            user_times: state.times.filter(r => r.task_id === t.id)
          }))
          .sort((a,b) => (a.task_order || 0) - (b.task_order || 0));

        return `
          <div class="card">
            <div style="display:flex; justify-content:space-between; align-items:center;">
              <div>
                <h3>${esc(job.name)}</h3>
                <div class="mini">
                  ${esc(job.project_type || '')} · ${esc(job.operario || '')}
                </div>
              </div>

              ${
                isGeneral()
                ? `<button class="btn btn-danger" onclick="deleteJob('${job.id}')">Eliminar</button>`
                : ''
              }
            </div>

            <div class="task-grid mt-18">
              ${tasks.map(t => renderTask(t, job)).join('')}
            </div>
          </div>
        `;
      }).join('');
    }

    function render(){
      if(state.loading){
        app.innerHTML = `<div class="loader"></div>`;
        return;
      }

      if(!state.session){
        renderLogin();
        return;
      }

      app.innerHTML = `
        ${renderHeader()}

        <div class="container">
          ${state.error ? `<div class="error-box">${esc(state.error)}</div>` : ''}
          ${state.info ? `<div class="info-box">${esc(state.info)}</div>` : ''}

          ${renderCreateJob()}

          <div class="card">
            <h3>Trabajos</h3>
            ${renderJobs()}
          </div>
        </div>
      `;

      refreshLiveTimes();
    }

    bootstrap();
  </script>
</body>
</html>
