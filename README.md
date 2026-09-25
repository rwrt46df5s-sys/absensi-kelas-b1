# absensi-kelas-b1
absensib1
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Absensi Siswa - MADZ PROJECT AI</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
  }

  body {
    min-height: 100vh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
    background-attachment: fixed;
    padding: 20px;
    overflow-x: hidden;
    position: relative;
  }

  /* Animasi background bubble */
  body::before, body::after {
    content: '';
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0.5;
    z-index: 0;
    animation: float 15s infinite ease-in-out;
  }
  body::before {
    width: 400px; height: 400px;
    background: #ff6ec4;
    top: -100px; left: -100px;
  }
  body::after {
    width: 500px; height: 500px;
    background: #7873f5;
    bottom: -150px; right: -150px;
    animation-delay: -7s;
  }

  @keyframes float {
    0%, 100% { transform: translate(0, 0) scale(1); }
    50% { transform: translate(50px, 50px) scale(1.1); }
  }

  .container {
    max-width: 1100px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }

  /* HEADER */
  .header {
    background: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.25);
    border-radius: 25px;
    padding: 30px;
    text-align: center;
    color: white;
    margin-bottom: 25px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
    animation: slideDown 0.8s ease;
  }

  @keyframes slideDown {
    from { opacity: 0; transform: translateY(-30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .header h1 {
    font-size: 2.5rem;
    font-weight: 800;
    background: linear-gradient(90deg, #fff, #ffd6ff, #fff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 8px;
    text-shadow: 0 2px 10px rgba(0,0,0,0.1);
  }

  .header p {
    font-size: 1rem;
    opacity: 0.9;
    font-weight: 300;
  }

  .clock-box {
    display: flex;
    justify-content: center;
    gap: 20px;
    margin-top: 20px;
    flex-wrap: wrap;
  }

  .clock-item {
    background: rgba(255, 255, 255, 0.2);
    padding: 15px 25px;
    border-radius: 15px;
    min-width: 180px;
    border: 1px solid rgba(255, 255, 255, 0.3);
    transition: transform 0.3s;
  }
  .clock-item:hover { transform: translateY(-3px); }

  .clock-label {
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 2px;
    opacity: 0.8;
  }

  .clock-value {
    font-size: 1.6rem;
    font-weight: 700;
    margin-top: 5px;
  }

  .wib-badge {
    display: inline-block;
    background: linear-gradient(45deg, #ff6ec4, #7873f5);
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 0.7rem;
    font-weight: 600;
    margin-left: 8px;
    box-shadow: 0 2px 10px rgba(255, 110, 196, 0.5);
  }

  /* MAIN GRID */
  .main-grid {
    display: grid;
    grid-template-columns: 1fr 1.5fr;
    gap: 25px;
  }

  @media (max-width: 900px) {
    .main-grid { grid-template-columns: 1fr; }
    .header h1 { font-size: 1.8rem; }
  }

  .card {
    background: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.25);
    border-radius: 25px;
    padding: 30px;
    color: white;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
    animation: fadeUp 0.8s ease;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .card-title {
    font-size: 1.3rem;
    font-weight: 700;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .card-title .icon {
    width: 35px; height: 35px;
    background: linear-gradient(45deg, #ff6ec4, #7873f5);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.2rem;
  }

  /* FORM */
  .form-group {
    margin-bottom: 18px;
  }

  .form-group label {
    display: block;
    font-size: 0.85rem;
    font-weight: 500;
    margin-bottom: 8px;
    opacity: 0.95;
  }

  .form-group input[type="text"] {
    width: 100%;
    padding: 12px 16px;
    background: rgba(255, 255, 255, 0.2);
    border: 2px solid rgba(255, 255, 255, 0.3);
    border-radius: 12px;
    color: white;
    font-size: 1rem;
    font-family: inherit;
    transition: all 0.3s;
  }

  .form-group input[type="text"]::placeholder { color: rgba(255,255,255,0.6); }
  .form-group input[type="text"]:focus {
    outline: none;
    border-color: #ff6ec4;
    background: rgba(255, 255, 255, 0.3);
    box-shadow: 0 0 0 4px rgba(255, 110, 196, 0.2);
  }

  /* CHECKBOX KEHADIRAN */
  .attendance-options {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }

  .att-option {
    position: relative;
  }

  .att-option input {
    position: absolute;
    opacity: 0;
    pointer-events: none;
  }

  .att-option label {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    padding: 14px;
    background: rgba(255, 255, 255, 0.15);
    border: 2px solid rgba(255, 255, 255, 0.3);
    border-radius: 12px;
    cursor: pointer;
    font-weight: 600;
    transition: all 0.3s;
    margin: 0;
    font-size: 0.9rem;
  }

  .att-option label:hover {
    transform: translateY(-2px);
    background: rgba(255, 255, 255, 0.25);
  }

  .att-option input:checked + label.hadir {
    background: linear-gradient(45deg, #11998e, #38ef7d);
    border-color: #38ef7d;
    box-shadow: 0 5px 20px rgba(56, 239, 125, 0.4);
  }
  .att-option input:checked + label.izin {
    background: linear-gradient(45deg, #f7971e, #ffd200);
    border-color: #ffd200;
    color: #333;
    box-shadow: 0 5px 20px rgba(255, 210, 0, 0.4);
  }
  .att-option input:checked + label.sakit {
    background: linear-gradient(45deg, #ff512f, #dd2476);
    border-color: #dd2476;
    box-shadow: 0 5px 20px rgba(221, 36, 118, 0.4);
  }
  .att-option input:checked + label.alpha {
    background: linear-gradient(45deg, #434343, #000000);
    border-color: #666;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.4);
  }

  /* TOMBOL SUBMIT */
  .btn-submit {
    width: 100%;
    padding: 15px;
    background: linear-gradient(45deg, #ff6ec4, #7873f5);
    border: none;
    border-radius: 12px;
    color: white;
    font-size: 1rem;
    font-weight: 700;
    cursor: pointer;
    margin-top: 10px;
    transition: all 0.3s;
    text-transform: uppercase;
    letter-spacing: 1px;
    box-shadow: 0 5px 20px rgba(255, 110, 196, 0.4);
  }

  .btn-submit:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 30px rgba(255, 110, 196, 0.6);
  }

  .btn-submit:active { transform: translateY(0); }

  /* STATISTIK */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    margin-bottom: 20px;
  }

  .stat-item {
    background: rgba(255, 255, 255, 0.15);
    border-radius: 12px;
    padding: 15px 10px;
    text-align: center;
    border: 1px solid rgba(255, 255, 255, 0.2);
  }

  .stat-num {
    font-size: 1.8rem;
    font-weight: 800;
  }

  .stat-label {
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    opacity: 0.85;
    margin-top: 3px;
  }

  .stat-item.hadir .stat-num { color: #38ef7d; }
  .stat-item.izin .stat-num { color: #ffd200; }
  .stat-item.sakit .stat-num { color: #ff512f; }
  .stat-item.alpha .stat-num { color: #aaa; }

  /* TABEL */
  .table-wrapper {
    max-height: 400px;
    overflow-y: auto;
    border-radius: 15px;
    background: rgba(0, 0, 0, 0.15);
  }

  .table-wrapper::-webkit-scrollbar { width: 8px; }
  .table-wrapper::-webkit-scrollbar-track { background: rgba(255,255,255,0.1); }
  .table-wrapper::-webkit-scrollbar-thumb {
    background: linear-gradient(45deg, #ff6ec4, #7873f5);
    border-radius: 10px;
  }

  table {
    width: 100%;
    border-collapse: collapse;
    color: white;
  }

  thead {
    position: sticky;
    top: 0;
    background: rgba(120, 115, 245, 0.9);
    backdrop-filter: blur(10px);
  }

  th, td {
    padding: 12px;
    text-align: left;
    font-size: 0.9rem;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  th {
    font-weight: 600;
    text-transform: uppercase;
    font-size: 0.75rem;
    letter-spacing: 1px;
  }

  tbody tr {
    transition: background 0.2s;
  }
  tbody tr:hover { background: rgba(255, 255, 255, 0.1); }

  .badge {
    display: inline-block;
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 0.75rem;
    font-weight: 600;
  }
  .badge.hadir { background: linear-gradient(45deg, #11998e, #38ef7d); }
  .badge.izin { background: linear-gradient(45deg, #f7971e, #ffd200); color: #333; }
  .badge.sakit { background: linear-gradient(45deg, #ff512f, #dd2476); }
  .badge.alpha { background: linear-gradient(45deg, #434343, #000); }

  .empty-state {
    text-align: center;
    padding: 40px 20px;
    opacity: 0.7;
  }
  .empty-state .emoji { font-size: 3rem; margin-bottom: 10px; }

  .action-bar {
    display: flex;
    gap: 10px;
    margin-bottom: 15px;
    flex-wrap: wrap;
  }

  .btn-small {
    padding: 8px 16px;
    background: rgba(255, 255, 255, 0.2);
    border: 1px solid rgba(255, 255, 255, 0.3);
    border-radius: 10px;
    color: white;
    font-size: 0.8rem;
    cursor: pointer;
    transition: all 0.3s;
    font-family: inherit;
  }
  .btn-small:hover {
    background: rgba(255, 255, 255, 0.3);
    transform: translateY(-2px);
  }
  .btn-small.danger:hover { background: linear-gradient(45deg, #ff512f, #dd2476); }

  /* NOTIFIKASI */
  .notif {
    position: fixed;
    top: 20px;
    right: 20px;
    padding: 15px 25px;
    border-radius: 12px;
    color: white;
    font-weight: 600;
    z-index: 1000;
    transform: translateX(400px);
    transition: transform 0.4s;
    box-shadow: 0 10px 30px rgba(0,0,0,0.3);
  }
  .notif.show { transform: translateX(0); }
  .notif.success { background: linear-gradient(45deg, #11998e, #38ef7d); }
  .notif.error { background: linear-gradient(45deg, #ff512f, #dd2476); }

  .footer {
    text-align: center;
    color: white;
    margin-top: 25px;
    opacity: 0.7;
    font-size: 0.85rem;
  }
</style>
</head>
<body>

<div class="container">
  <!-- HEADER -->
  <div class="header">
    <h1>📋 Absensi Siswa</h1>
    <p>MADZ PROJECT AI • Sistem Kehadiran Digital</p>
    <div class="clock-box">
      <div class="clock-item">
        <div class="clock-label">📅 Hari & Tanggal</div>
        <div class="clock-value" id="dateDisplay">-</div>
      </div>
      <div class="clock-item">
        <div class="clock-label">⏰ Waktu Sekarang</div>
        <div class="clock-value" id="timeDisplay">--:--:-- <span class="wib-badge">WIB</span></div>
      </div>
    </div>
  </div>

  <!-- MAIN -->
  <div class="main-grid">
    <!-- FORM ABSEN -->
    <div class="card">
      <div class="card-title"><div class="icon">✍️</div> Form Absensi</div>

      <div class="form-group">
        <label>👤 Nama Lengkap Siswa</label>
        <input type="text" id="namaSiswa" placeholder="Ketik nama kamu di sini..." maxlength="50">
      </div>

      <div class="form-group">
        <label>✅ Pilih Status Kehadiran</label>
        <div class="attendance-options">
          <div class="att-option">
            <input type="radio" name="status" id="hadir" value="Hadir" checked>
            <label for="hadir" class="hadir">✅ Hadir</label>
          </div>
          <div class="att-option">
            <input type="radio" name="status" id="izin" value="Izin">
            <label for="izin" class="izin">📝 Izin</label>
          </div>
          <div class="att-option">
            <input type="radio" name="status" id="sakit" value="Sakit">
            <label for="sakit" class="sakit">🤒 Sakit</label>
          </div>
          <div class="att-option">
            <input type="radio" name="status" id="alpha" value="Alpha">
            <label for="alpha" class="alpha">❌ Alpha</label>
          </div>
        </div>
      </div>

      <button class="btn-submit" onclick="submitAbsen()">🚀 Kirim Absensi</button>
    </div>

    <!-- RIWAYAT -->
    <div class="card">
      <div class="card-title"><div class="icon">📊</div> Riwayat Absensi</div>

      <div class="stats-grid">
        <div class="stat-item hadir">
          <div class="stat-num" id="countHadir">0</div>
          <div class="stat-label">Hadir</div>
        </div>
        <div class="stat-item izin">
          <div class="stat-num" id="countIzin">0</div>
          <div class="stat-label">Izin</div>
        </div>
        <div class="stat-item sakit">
          <div class="stat-num" id="countSakit">0</div>
          <div class="stat-label">Sakit</div>
        </div>
        <div class="stat-item alpha">
          <div class="stat-num" id="countAlpha">0</div>
          <div class="stat-label">Alpha</div>
        </div>
      </div>

      <div class="action-bar">
        <button class="btn-small" onclick="exportData()">📥 Export CSV</button>
        <button class="btn-small danger" onclick="hapusSemua()">🗑️ Hapus Semua</button>
      </div>

      <div class="table-wrapper">
        <table>
          <thead>
            <tr>
              <th>No</th>
              <th>Nama</th>
              <th>Tanggal</th>
              <th>Jam Submit</th>
              <th>Status</th>
            </tr>
          </thead>
          <tbody id="tableBody">
            <tr><td colspan="5"><div class="empty-state"><div class="emoji">📭</div>Belum ada data absensi</div></td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>

  <div class="footer">
    © 2026 MADZ PROJECT AI • Dibuat dengan ❤️ untuk pendidikan Indonesia
  </div>
</div>

<div class="notif" id="notif"></div>

<script>
  // ============ JAM & TANGGAL REAL-TIME (WIB = UTC+7) ============
  const hari = ['Minggu','Senin','Selasa','Rabu','Kamis','Jumat','Sabtu'];
  const bulan = ['Januari','Februari','Maret','April','Mei','Juni','Juli','Agustus','September','Oktober','November','Desember'];

  function getWIB() {
    // Ambil waktu sekarang, konversi ke WIB (UTC+7)
    const now = new Date();
    const utc = now.getTime() + (now.getTimezoneOffset() * 60000);
    return new Date(utc + (7 * 3600000));
  }

  function updateClock() {
    const wib = getWIB();
    const h = String(wib.getHours()).padStart(2,'0');
    const m = String(wib.getMinutes()).padStart(2,'0');
    const s = String(wib.getSeconds()).padStart(2,'0');
    document.getElementById('timeDisplay').innerHTML = `${h}:${m}:${s} <span class="wib-badge">WIB</span>`;

    const tgl = wib.getDate();
    const bln = bulan[wib.getMonth()];
    const thn = wib.getFullYear();
    const hr = hari[wib.getDay()];
    document.getElementById('dateDisplay').textContent = `${hr}, ${tgl} ${bln} ${thn}`;
  }

  updateClock();
  setInterval(updateClock, 1000); // update tiap detik

  // ============ DATA ABSENSI ============
  let dataAbsen = JSON.parse(localStorage.getItem('dataAbsen') || '[]');

  function simpanData() {
    localStorage.setItem('dataAbsen', JSON.stringify(dataAbsen));
  }

  function renderTable() {
    const tbody = document.getElementById('tableBody');
    if (dataAbsen.length === 0) {
      tbody.innerHTML = '<tr><td colspan="5"><div class="empty-state"><div class="emoji">📭</div>Belum ada data absensi</div></td></tr>';
    } else {
      tbody.innerHTML = dataAbsen.map((d, i) => `
        <tr>
          <td>${i+1}</td>
          <td><strong>${escapeHtml(d.nama)}</strong></td>
          <td>${d.tanggal}</td>
          <td>${d.jam} <span class="wib-badge" style="font-size:0.6rem;padding:2px 6px;">WIB</span></td>
          <td><span class="badge ${d.status.toLowerCase()}">${d.status}</span></td>
        </tr>
      `).join('');
    }
    updateStats();
  }

  function updateStats() {
    document.getElementById('countHadir').textContent = dataAbsen.filter(d=>d.status==='Hadir').length;
    document.getElementById('countIzin').textContent  = dataAbsen.filter(d=>d.status==='Izin').length;
    document.getElementById('countSakit').textContent = dataAbsen.filter(d=>d.status==='Sakit').length;
    document.getElementById('countAlpha').textContent = dataAbsen.filter(d=>d.status==='Alpha').length;
  }

  function escapeHtml(str) {
    const div = document.createElement('div');
    div.textContent = str;
    return div.innerHTML;
  }

  // ============ SUBMIT ABSEN ============
  function submitAbsen() {
    const nama = document.getElementById('namaSiswa').value.trim();
    const status = document.querySelector('input[name="status"]:checked').value;

    if (!nama) {
      showNotif('❌ Nama siswa harus diisi!', 'error');
      return;
    }
    if (nama.length < 2) {
      showNotif('❌ Nama terlalu pendek!', 'error');
      return;
    }

    const wib = getWIB();
    const tgl = `${String(wib.getDate()).padStart(2,'0')}/${String(wib.getMonth()+1).padStart(2,'0')}/${wib.getFullYear()}`;
    const jam = `${String(wib.getHours()).padStart(2,'0')}:${String(wib.getMinutes()).padStart(2,'0')}:${String(wib.getSeconds()).padStart(2,'0')}`;

    dataAbsen.unshift({ nama, status, tanggal: tgl, jam });
    simpanData();
    renderTable();

    document.getElementById('namaSiswa').value = '';
    showNotif(`✅ Absensi ${status} berhasil dikirim!`, 'success');
  }

  // ============ NOTIFIKASI ============
  function showNotif(msg, type) {
    const n = document.getElementById('notif');
    n.textContent = msg;
    n.className = `notif ${type} show`;
    setTimeout(() => n.classList.remove('show'), 3000);
  }

  // ============ EXPORT CSV ============
  function exportData() {
    if (dataAbsen.length === 0) {
      showNotif('⚠️ Tidak ada data untuk diexport!', 'error');
      return;
    }
    let csv = 'No,Nama,Tanggal,Jam Submit (WIB),Status\n';
    dataAbsen.forEach((d, i) => {
      csv += `${i+1},"${d.nama}",${d.tanggal},${d.jam},${d.status}\n`;
    });
    const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = `absensi_${new Date().toISOString().slice(0,10)}.csv`;
    a.click();
    showNotif('📥 Data berhasil diexport!', 'success');
  }

  // ============ HAPUS SEMUA ============
  function hapusSemua() {
    if (dataAbsen.length === 0) {
      showNotif('⚠️ Data sudah kosong!', 'error');
      return;
    }
    if (confirm('Yakin ingin menghapus semua data absensi?')) {
      dataAbsen = [];
      simpanData();
      renderTable();
      showNotif('🗑️ Semua data berhasil dihapus!', 'success');
    }
  }

  // Enter untuk submit
  document.getElementById('namaSiswa').addEventListener('keypress', e => {
    if (e.key === 'Enter') submitAbsen();
  });

  renderTable();
</script>

</body>
</html>
