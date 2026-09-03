📚 Sistem Informasi Perpustakaan Sekolah

Sistem Informasi Perpustakaan Sekolah adalah aplikasi berbasis web yang dibuat untuk membantu mengelola kegiatan perpustakaan secara lebih mudah, cepat, dan terorganisir.

Website ini dapat digunakan untuk mengelola data buku, data anggota, serta proses peminjaman dan pengembalian buku.

🌐 Website

✨ Fitur

Beberapa fitur yang tersedia dalam sistem perpustakaan ini antara lain:

- 🏠 Halaman utama
- 📖 Data buku
- 👥 Data anggota perpustakaan
- 📚 Peminjaman buku
- 🔄 Pengembalian buku
- 📋 Riwayat transaksi
- 🔐 Login admin
- 🚪 Logout
- 📊 Pengelolaan data perpustakaan

🎯 Tujuan

Aplikasi ini dibuat untuk:

1. Mempermudah pengelolaan data buku.
2. Mempermudah pencatatan data anggota.
3. Membantu proses peminjaman dan pengembalian buku.
4. Mengurangi pencatatan secara manual.
5. Membuat pengelolaan perpustakaan menjadi lebih terstruktur.

🛠️ Teknologi

Aplikasi ini dikembangkan menggunakan:

- HTML — struktur halaman web
- CSS — tampilan dan desain
- JavaScript — interaksi pada halaman
- PHP — pemrograman sisi server
- MySQL — penyimpanan database
- XAMPP — server lokal saat proses pengembangan

📁 Struktur Folder

Contoh struktur file aplikasi:

ukk_perpustakaan/
│
├── index.php
├── login_admin.php
├── proses_login.php
├── dashboard_admin.php
├── logout.php
│
├── data_buku.php
├── tambah_buku.php
├── edit_buku.php
├── hapus_buku.php
│
├── data_anggota.php
├── tambah_anggota.php
├── edit_anggota.php
├── hapus_anggota.php
│
├── peminjaman.php
├── proses_pinjam.php
├── pengembalian.php
│
├── koneksi.php
└── style.css

🗄️ Database

Database digunakan untuk menyimpan berbagai data perpustakaan, seperti:

- Data admin
- Data anggota
- Data buku
- Data peminjaman
- Data pengembalian

Pastikan konfigurasi database pada file "koneksi.php" sudah sesuai dengan server yang digunakan.

💻 Cara Menjalankan di XAMPP

1. Install XAMPP.
2. Jalankan Apache dan MySQL.
3. Simpan folder project ke:

C:\xampp\htdocs\

4. Buat database melalui phpMyAdmin.
5. Import file database ".sql".
6. Sesuaikan username, password, dan nama database pada "koneksi.php".
7. Buka browser dan akses:

http://localhost/ukk_perpustakaan/

🔑 Login Admin

Halaman login admin digunakan untuk membatasi akses ke halaman pengelolaan perpustakaan.

«Username dan password dapat disesuaikan dengan data admin yang terdapat pada database.»

👤 Pengguna Sistem

Admin

Admin dapat:

- Mengelola data buku.
- Mengelola data anggota.
- Mengelola transaksi peminjaman.
- Mengelola pengembalian buku.
- Melihat riwayat transaksi.

Anggota

Anggota dapat menggunakan sistem sesuai fitur yang disediakan pada halaman pengguna.

📱 Tampilan

Aplikasi dirancang agar dapat digunakan melalui browser pada komputer maupun perangkat lainnya.

🚀 Pengembangan

Project ini masih dapat dikembangkan dengan menambahkan beberapa fitur, seperti:

- 🔍 Pencarian buku
- 📊 Dashboard statistik
- 🖨️ Cetak laporan
- 📅 Notifikasi batas pengembalian
- 📱 Tampilan yang lebih responsif
- 🔐 Peningkatan keamanan sistem

👩‍💻 Pembuat

Nama: Novia
Program Keahlian: Rekayasa Perangkat Lunak (RPL)
Project: Sistem Informasi Perpustakaan Sekolah

📄 Lisensi

Project ini dibuat untuk keperluan pembelajaran dan pengembangan aplikasi perpustakaan sekolah.
