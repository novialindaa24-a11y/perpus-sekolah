
📚 Sistem Informasi Perpustakaan Sekolah
 
🌐 URL: https://perpustakaansekolahhh.site.je/index.php?i=1
🏫 Institusi: SMA Negeri 1 Bantul
📅 Versi: 1.0.0 | ✅ Status: Berjalan & Diuji
🛠️ Dibuat dengan: PHP 7+, MySQL, HTML5, CSS3, JavaScript, Font Awesome
 
 
 
📋 DAFTAR ISI
 
- 📖 Tentang Proyek
- 🎨 Mockup UI
- 📊 Use Case Diagram
- 🔄 Activity Diagram
- 🧮 Algoritma Kerja
- 📈 Flowchart & User Flow
- 🗄️ ERD — Entity Relationship Diagram
- ✨ Fitur Utama
- 🛠️ Teknologi yang Digunakan
- 📦 Cara Install
- 📂 Struktur File & Database
- 📞 Kontak
 
 
 
📖 TENTANG PROYEK
 
Sistem Informasi Perpustakaan Sekolah berbasis web yang dikembangkan untuk memudahkan pengelolaan perpustakaan di SMA Negeri 1 Bantul. Sistem ini mengotomatisasi proses peminjaman, pengembalian, perhitungan denda, hingga pembuatan laporan — dengan 3 tingkatan pengguna: Admin, Petugas, dan Siswa.
 
💡 Kebijakan Perpustakaan:
 
- Batas pengembalian: 7 hari sejak pinjam
- Maksimal pinjam: 3 buku per siswa
- Denda keterlambatan: Rp 10.000 / hari
 
🎨 1. MOCKUP UI
 
Tampilan antarmuka sistem — Dashboard Admin dengan Logo SMA Negeri 1 Bantul
 
plaintext
  
╔══════════════════════════════════════════════════════════════════════╗
║  📸 [LOGO.JPEG]  PERPUSTAKAAN                                        ║
║  SMA NEGERI 1 BANTUL                                                 ║
╠══════════════════════════════════╦═══════════════════════════════════╣
║  🟢 SIDEBAR — HIJAU TUA (#166534) │  📊 DASHBOARD — HALAMAN UTAMA     ║
║                                  │                                   ║
║  🏠 Dashboard (aktif)            │  ┌──────────┐ ┌──────────┐       ║
║  📖 Kelola Buku                  │  │ 📚 Buku  │ │ 👤 Anggota│       ║
║  👤 Kelola Anggota               │  │   150    │ │   450     │       ║
║  📝 Transaksi Pinjam             │  └──────────┘ └──────────┘       ║
║  📤 Pengembalian                 │  ┌──────────┐ ┌──────────┐       ║
║  ✅ Konfirmasi Pinjam            │  │ 📅 Pinjam │ │ 📤 Kembali│       ║
║  📊 Laporan                      │  │   12     │ │    8     │       ║
║  💰 Kelola Denda                 │  └──────────┘ └──────────┘       ║
║  👤 Profil Admin                 │                                   ║
║  🚪 Logout                       │  ⚠️ Peringatan Keterlambatan      ║
║                                  │  ┌─────────────────────────────┐  ║
║                                  │  │ Nama Siswa — Judul Buku     │  ║
║                                  │  │ Terlambat 3 hari | Rp30.000 │  ║
║                                  │  └─────────────────────────────┘  ║
║                                  │                                   ║
║                                  │  📈 Grafik Statistik Peminjaman   ║
║                                  │  └─────────────────────────────── ║
╚══════════════════════════════════╩═══════════════════════════════════╝
 
 
 
 
📊 2. USE CASE DIAGRAM
 
Hubungan Aktor ↔ Fungsi Sistem
 
plaintext
  
                  ┌──────────────────────────────────┐
                  │     SISTEM PERPUSTAKAAN          │
                  │      SMA NEGERI 1 BANTUL         │
                  └────────────┬─────────────────────┘
                               │
          ┌────────────────────┼────────────────────┐
          │                    │                    │
   ┌──────┴──────┐      ┌─────┴──────┐      ┌──────┴──────┐
   │   🔐 ADMIN   │      │   📝 PETUGAS │      │   🎓 SISWA    │
   └──────┬───────┘      └─────┬───────┘      └──────┬───────┘
          │                    │                    │
          │  Login ────────────┼────────────────────┤
          │                    │                    │
          ├─ Kelola Buku ──────┤                    │
          ├─ Kelola Anggota ───┤                    │
          ├─ Laporan Pinjam ───┤                    │
          ├─ Laporan Kembali ──┤                    │
          │                    ├─ Proses Pinjam ────┤
          │                    ├─ Pengembalian ─────┤
          │                    ├─ Hitung Denda ─────┤
          │                    ├─ Tandai Bayar ─────┤
          │                    │                    ├─ Lihat Katalog
          │                    │                    ├─ Ajukan Pinjam
          │                    │                    ├─ Cek Status
          │                    │                    ├─ Riwayat
          │                    │                    └─ Notifikasi Denda
          │
          └─── HANYA ADMIN ────┐
               ├─ Kelola Akun Petugas
               ├─ Hapus Data
               └─ Backup Database
 
 
 
 
🔄 3. ACTIVITY DIAGRAM
 
Alur Proses Utama — Peminjaman & Pengembalian
 
📖 Alur Peminjaman
 
plaintext
  
   MULAI
     │
     ▼
   ┌──────────────┐
   │  Login Siswa  │  NIS + Password
   └──────┬───────┘
          │
          ▼
   ┌──────────────┐
   │ Ajukan Pinjam │  Pilih Buku
   └──────┬───────┘
          │
          ▼
   ┌──────────────┐        TIDAK TERSEDIA
   │ Cek Stok Buku │ ────────────────→ ❌ DITOLAK
   └──────┬───────┘
          │ TERSEDIA
          ▼
   ┌──────────────┐        ≥ 3 BUKU
   │ Cek Maksimal  │ ────────────────→ ❌ DITOLAK
   │ Pinjam (3)    │
   └──────┬───────┘
          │ < 3
          ▼
   ┌──────────────────┐
   │ Petugas Konfirmasi │
   └──────┬───────────┘
          │
          ▼
   ┌──────────────────────┐
   │ Simpan Peminjaman    │  tgl_batas = +7 hari
   └──────┬───────────────┘
          │
          ▼
        ✅ SELESAI
 
 
💰 Alur Pengembalian & Denda
 
plaintext
  
   BUKU DIKEMBALIKAN
          │
          ▼
   ┌──────────────────────┐
   │ Cek Tgl Batas Kembali│
   └──────────┬───────────┘
              │
       ┌──────┴──────┐
       │ Tepat Waktu │  TERLAMBAT
       ▼             ▼
   ┌─────────┐   ┌──────────────────────────────┐
   │ Denda=0 │   │ Hitung Denda:                │
   └─────────┘   │ Hari × Rp 10.000/hari        │
                 └──────────────┬───────────────┘
                                │
                        ┌───────▼───────┐
                        │ Simpan Denda  │ Status: Belum Bayar
                        └───────┬───────┘
                                │
                        ▼ Notifikasi ke Siswa
                                │
                        ┌───────▼───────┐
                        │ Siswa Bayar    │
                        └───────┬───────┘
                                │
                        ▼ Tandai: Sudah Bayar
                                │
                              ✅ SELESAI
 
 
 
 
🧮 4. ALGORITMA
 
Logika Perhitungan — Denda, Validasi Pinjam, Login
 
plaintext
  
┌──────────────────────────────────────────────────────────────┐
│             📐 ALGORITMA SISTEM PERPUSTAKAAN                 │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  🔹 ALGORITMA 1: PERHITUNGAN DENDA                           │
│  ──────────────────────────────────────────────────────────  │
│  INPUT: tgl_batas_kembali, tgl_dikembalikan                  │
│  OUTPUT: hari_terlambat, total_denda                         │
│                                                              │
│  1. HARI_TERLAMBAT = SELISIH_HARI(tgl_dikembalikan,          │
│                                 tgl_batas_kembali)           │
│  2. JIKA HARI_TERLAMBAT > 0 MAKA:                            │
│       DENDA_PER_HARI = 10.000                                │
│       TOTAL_DENDA = HARI_TERLAMBAT × DENDA_PER_HARI          │
│     SELAIN ITU:                                              │
│       TOTAL_DENDA = 0                                        │
│       HARI_TERLAMBAT = 0                                     │
│  3. SIMPAN ke tabel pengembalian                             │
│  4. KIRIM notifikasi ke halaman siswa                        │
│                                                              │
│  🔹 ALGORITMA 2: VALIDASI PEMINJAMAN                         │
│  ──────────────────────────────────────────────────────────  │
│  INPUT: id_anggota, kode_buku                                │
│  ATURAN: Maksimal 3 buku sedang dipinjam                      │
│                                                              │
│  1. JUMLAH_PINJAM = COUNT(*) FROM peminjaman                 │
│       WHERE id_anggota = ? AND status = 'Dipinjam'           │
│  2. JIKA JUMLAH_PINJAM >= 3 → TOLAK (Maksimal 3 buku)        │
│  3. CEK stok_buku dari tabel buku                            │
│  4. JIKA stok_buku <= 0 → TOLAK (Buku tidak tersedia)       │
│  5. SIMPAN peminjaman, kurangi stok buku                     │
│  6. BERHASIL — Tampilkan notifikasi                          │
│                                                              │
│  🔹 ALGORITMA 3: LOGIN SISWA                                 │
│  ──────────────────────────────────────────────────────────  │
│  INPUT: nis, password                                        │
│  OUTPUT: Session, nama_pengguna, notifikasi                  │
│                                                              │
│  1. CARI di tabel anggota WHERE nis = nis_input              │
│  2. JIKA TIDAK ADA → "NIS tidak terdaftar!"                 │
│  3. JIKA password TIDAK SAMA → Cek terbalik NIS/Password?    │
│  4. JIKA password BENAR:                                     │
│       BUAT Session: id_siswa, nama_siswa                     │
│       PUTAR suara notifikasi                                 │
│       TAMPILKAN: "Selamat datang, {nama}!"                    │
│       PINDAH ke halaman utama siswa                          │
│                                                              │
└──────────────────────────────────────────────────────────────┘
 
 
 
 
📈 5. FLOWCHART & USER FLOW
 
Alur Navigasi Pengguna dalam Sistem
 
plaintext
  
         ┌──────────────────────┐
         │   🏠 HALAMAN UTAMA   │
         │  Perpustakaan SMAN 1 │
         └──────────┬───────────┘
                    │
          ┌─────────┼──────────┐
          │         │          │
          ▼         ▼          ▼
      ┌────────┐ ┌────────┐ ┌────────┐
      │ 🔐 Admin│ │📝 Petugas│ │🎓 Siswa │
      │ Login   │ │ Login   │ │ Login   │
      └────┬───┘ └────┬───┘ └────┬───┘
           │          │          │
           ▼          ▼          ▼
      ┌────────┐ ┌────────┐ ┌────────┐
      │Dashboard│ │Dashboard│ │Beranda │
      │ Admin   │ │ Petugas │ │ Siswa  │
      └────┬───┘ └────┬───┘ └────┬───┘
           │          │          │
    ┌──────┼──────────┼──────────┤
    │      │          │          │
    │  Kelola Buku    │          │
    │  Kelola Anggota│          │
    │      │      Transaksi      │
    │      │    Pinjam/Kembali   │
    │      │          │          │
    │      │          │      Katalog Buku
    │      │          │      Ajukan Pinjam
    │      │          │      Cek Status
    │      │          │      Riwayat
    │      │          │      Notifikasi Denda
    │      │          │
    └──────┼──────────┘
           │
           ▼
        🚪 LOGOUT
           │
           ▼
    ┌────────────────┐
    │ Kembali ke     │
    │ Halaman Login  │
    └────────────────┘
 
 
 
 
🗄️ 6. ERD — ENTITY RELATIONSHIP DIAGRAM
 
Hubungan Antar Tabel Database
 
plaintext
  
  ┌──────────────────┐        1:N        ┌──────────────────┐
  │     ANGGOTA      │◄─────────────────►│   PEMINJAMAN     │
  │ ├─ id_anggota (PK)│                   │ ├─ id_peminjaman (PK)
  │ │─ nis            │                   │ │─ id_anggota (FK)
  │ │─ nama_anggota   │                   │ │─ kode_buku (FK)
  │ │─ username       │                   │ │─ tgl_pinjam
  │ │─ password       │                   │ │─ tgl_batas_kembali
  │ │─ no_hp          │                   │ │─ status (Dipinjam/Dikembalikan)
  │ │─ alamat         │                   │ └──────────────────
  │ └─────────────────┘                          │
         │                                       │ 1:1
         │                                       ▼
         │                                ┌──────────────────┐
         │                                │  PENGEMBALIAN    │
  ┌──────┴──────┐                        │ ├─ id_pengembalian (PK)
  │    BUKU     │◄───────────N:1─────────►│ │─ id_peminjaman (FK)
  │ ├─ kode_buku(PK)│                     │ │─ tgl_kembali
  │ │─ judul_buku   │                     │ │─ denda
  │ │─ pengarang    │                     │ │─ status_denda (Belum Bayar/Sudah Bayar)
  │ │─ penerbit     │                     │ │─ tgl_bayar
  │ │─ tahun        │                     │ │─ dibayar_oleh
  │ │─ nomor_rak    │                     │ └──────────────────
  │ │─ lokasi_rak   │
  │ │─ buku_tersedia│
  │ └───────────────┘
         │
         │
  ┌──────┴──────┐
  │   PETUGAS   │
  │ ├─ id_petugas (PK)
  │ │─ username
  │ │─ nama_petugas
  │ │─ password
  │ └────────────┘

  ┌──────────────────────────────────────────────────────────────┐
  │  📌 KETERANGAN RELASI:                                       │
  │  • ANGGOTA (1) ──── (N) PEMINJAMAN    1 siswa pinjam banyak │
  │  • BUKU    (1) ──── (N) PEMINJAMAN    1 buku dipinjam berkali│
  │  • PEMINJAMAN (1) ── (1) PENGEMBALIAN 1 pinjam = 1 kembali  │
  │  • PETUGAS (1) ──── (N) PENGEMBALIAN  Petugas memproses     │
  └──────────────────────────────────────────────────────────────┘
 
 
 
 
📥 Cara Menyimpan ke Gambar:
 
1. Salin kode kotak di atas → Buka asciiflow.com → Tempel → Simpan sebagai gambar
2. Atau Print Screen bagian yang dibutuhkan → Simpan sebagai PNG/JPG
3. Upload ke folder proyek → Tambahkan di README.md
 
Semua diagram di atas sudah sesuai dengan sistem perpustakaan yang sedang Anda kembangkan — tinggal pakai langsung! 🎒📚a 
 
 
 
✅ FITUR UTAMA
 
Fitur Admin Petugas Siswa 
🔐 Login & Hak Akses ✅ ✅ ✅ 
📊 Dashboard & Statistik ✅ ✅ ✅ 
📖 Kelola Data Buku ✅ ✅ ❌ 
👤 Kelola Data Anggota ✅ ✅ ❌ 
📝 Ajukan Pinjam Buku ❌ ❌ ✅ 
✅ Konfirmasi Pinjam ✅ ✅ ❌ 
📤 Pengembalian Buku ✅ ✅ ❌ 
💰 Hitung & Kelola Denda ✅ ✅ ✅ Lihat 
🔔 Notifikasi Keterlambatan ✅ ✅ ✅ 
📊 Laporan Peminjaman ✅ ✅ ❌ 
📊 Laporan Pengembalian ✅ ✅ ❌ 
📈 Grafik Statistik ✅ ✅ ❌ 
👤 Profil Pengguna ✅ ✅ ✅ 
🔧 Kelola Akun Petugas ✅ ❌ ❌ 
 
 
 
🛠️ TEKNOLOGI YANG DIGUNAKAN
 
Kategori Teknologi 
Bahasa Backend PHP 7+ (Prosedural) 
Database MySQL 
Server Apache / XAMPP 
HTML/CSS HTML5, CSS3, Responsive Design 
JavaScript Vanilla JS 
Ikon Font Awesome 4.7 
Grafik Chart.js v4.4 
File Tambahan  logo.jpeg  (logo sekolah),  notif.mpeg  (suara notifikasi),  vidio.mp4  (background login) 
 
 
 
📦 CARA INSTALL & DEPLOY
 
bash
  
# 1. Upload File
# Letakkan semua file ke folder web server atau hosting

# 2. Buat Database
- Buka phpMyAdmin → Buat database bernama: perpustakaan
- Import file database/perpustakaan.sql

# 3. Konfigurasi Koneksi
- Buka file koneksi.php
- Sesuaikan baris berikut:
  $host = 'localhost';
  $user = 'nama_user_database';
  $pass = 'password_database';
  $db   = 'perpustakaan';

# 4. Letakkan Logo Sekolah
- Simpan logo sekolah dengan nama: logo.jpeg di folder utama

# 5. Akses Sistem
- Lokal: http://localhost/nama_folder/
- Online: https://perpustakaansekolahhh.site.je/index.php?i=1
 
 
 
 
📂 STRUKTUR FILE & DATABASE
 
plaintext
  
perpustakaan/
├── koneksi.php                  # Koneksi database
├── index.php                    # Halaman utama
├── login.php                    # Login Admin & Petugas
├── login_siswa.php              # Login Siswa
├── logout.php                   # Logout
├── dashboard_admin.php         # Dashboard Admin
├── dashboard_petugas.php       # Dashboard Petugas
├── index_siswa.php             # Beranda Siswa
├── kelola_buku.php             # Kelola data buku
├── kelola_anggota.php          # Kelola data anggota
├── transaksi_pinjam.php        # Proses peminjaman
├── pengembalian.php            # Pengembalian & hitung denda
├── konfirmasi_pinjam.php       # Konfirmasi ajukan pinjam siswa
├── laporan_peminjaman.php      # Laporan peminjaman
├── laporan_pengembalian.php    # Laporan pengembalian
├── bayar_denda.php             # Tandai denda sudah dibayar
├── profil_admin.php            # Profil Admin
├── profil_petugas.php          # Profil Petugas
├── logo.jpeg                   # Logo SMA Negeri 1 Bantul 📸
├── notif.mpeg                  # Suara notifikasi 🔊
├── vidio.mp4                   # Background video login 🎬
└── README.md                   # Dokumentasi proyek 📖
 
 
Tabel Utama Database:
 
-  anggota  — data siswa/anggota
-  buku  — data koleksi buku
-  peminjaman  — data transaksi pinjam
-  pengembalian  — data kembali & denda
-  petugas  — data admin & petugas perpustakaan
 
 
 
📞 KONTAK & INFORMASI
 
Item Keterangan 
Nama Proyek Sistem Informasi Perpustakaan Sekolah 
Institusi SMA Negeri 1 Bantul 
URL Website https://perpustakaansekolahhh.site.je/index.php?i=1 
Versi 1.0.0 
Status ✅ Berjalan & Diuji 
Kebijakan Denda Rp 10.000/hari · Batas 7 hari · Maks 3 buku 
Pengembang Tim Perpustakaan SMAN 1 Bantul 
 
 
 
📖 README ini menjadi dokumentasi resmi Sistem Perpustakaan Sekolah. Semoga bermanfaat dan memudahkan pengelolaan perpustakaan!
🎒📚 — SMA Negeri 1 Bantul —
