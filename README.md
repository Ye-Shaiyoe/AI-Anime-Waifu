<div align="center">

# 📬 Sistem Arsip Surat Digital
### Balai Pengelolaan SUML

[![Laravel](https://img.shields.io/badge/Laravel-12.x-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)](https://laravel.com)
[![PHP](https://img.shields.io/badge/PHP-8.x-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://php.net)
[![License](https://img.shields.io/badge/License-Internal-blue?style=for-the-badge)](.)

> Sistem pengarsipan dan manajemen surat digital berbasis web untuk Balai Pengelolaan SUML — mempercepat alur pemrosesan surat dari pengajuan hingga pengarsipan secara efisien dan transparan.

</div>

---

## 📋 Daftar Isi

- [Tentang Aplikasi](#-tentang-aplikasi)
- [Fitur Utama](#-fitur-utama)
- [Alur Tracking Surat](#-alur-tracking-surat-10-tahapan)
- [Fitur User Dashboard](#-fitur-user-dashboard)
- [Fitur Admin Dashboard](#-fitur-admin-dashboard)
- [Role Admin](#-role-based-admin)
- [Jenis & Sifat Surat](#-jenis--sifat-surat)
- [Keamanan](#-keamanan)
- [Teknologi](#-teknologi)
- [Instalasi](#-instalasi)

---

## 📖 Tentang Aplikasi

Sistem Arsip Surat Digital adalah platform manajemen surat keluar berbasis web yang dirancang khusus untuk Balai Pengelolaan SUML. Aplikasi ini mengotomasi seluruh alur pemrosesan surat — mulai dari pengajuan oleh pegawai, verifikasi berjenjang oleh pejabat terkait, penomoran, penandatanganan, pengiriman, hingga pengarsipan akhir.

Dengan sistem ini, setiap surat dapat dipantau secara real-time, terdokumentasi dengan baik, dan diproses sesuai standar layanan dengan SLA yang terukur.

---

## ✨ Fitur Utama

| Fitur | Deskripsi |
|---|---|
| 🔐 **Autentikasi Lengkap** | Login & register dengan reCAPTCHA v2, lupa password via email |
| 📤 **Upload Surat** | Upload dokumen utama & file revisi |
| 🔍 **Tracking Surat** | Pantau posisi surat dalam 10 tahapan alur kerja |
| 🔔 **Notifikasi Real-time** | Notifikasi setiap perubahan status surat |
| 👤 **Role-based Access** | Hak akses terpisah untuk user dan tiga jenis admin |
| 📊 **Dashboard & Statistik** | Rekap surat per bulan, tahun, jenis, dan sifat |
| 📁 **Pengarsipan Digital** | Arsip terpusat dengan QR Code verifikasi |
| 🌙 **Dark / Light Mode** | Tampilan adaptif sesuai preferensi pengguna |

---

## 🔄 Alur Tracking Surat (10 Tahapan)

```
[0] Draft  →  [1] Diajukan  →  [2] Verifikasi Aspirasi  →  [3] Verifikasi KasubagTU
    →  [4] Verifikasi Kepala Balai  →  [5] Penomoran oleh Aspirasi
    →  [6] Tanda Tangan DS  →  [7] Pengiriman via TNDe
    →  [8] Pengiriman via Srikandi  →  [9] Pengarsipan  →  [10] ✅ Selesai
```

> **SLA:** Setiap tahap memiliki batas waktu **24 jam**. Surat yang melewati batas waktu akan otomatis ditandai **Terlambat**.

---

## 👤 Fitur User Dashboard

### Ringkasan & Monitoring
- Kartu ringkasan: jumlah surat **Total / Diproses / Selesai / Ditolak**
- Tabel monitoring surat dengan filter berdasarkan bulan dan tahun
- Pencarian surat dengan filter lanjutan

### Manajemen Profil
- Edit foto profil, username, email, NIP (pegawai), dan password

### Pengajuan Surat
- Isi formulir pengajuan dengan upload **1 file dokumen / lampiran**
- Tersedia **template surat** yang dapat diunduh
- Preview file Word dan lampiran langsung di aplikasi
- QR Code verifikasi pada setiap surat keluar

### Tracking & Notifikasi
- Pantau posisi surat di 10 tahap secara real-time
- Notifikasi otomatis setiap perubahan status
- Lihat komentar/catatan yang diberikan admin di setiap tahap

### Revisi & Penolakan
- Surat ditolak → ajukan ulang atau hapus
- Surat direvisi → upload ulang dokumen, proses dimulai dari **Verifikasi Aspirasi**

### Riwayat & Statistik
- Riwayat pemrosesan surat lengkap
- Riwayat revisi dan riwayat penghapusan surat
- Statistik surat per bulan & tahun dengan fitur **export**

### Fitur Tambahan
- **Jam Kerja:** Senin–Jumat, 08:00–16:00. Upload di luar jam kerja akan ditandai *"Di Luar Jam Kerja"*
- **Hapus file fisik** (Word/Lampiran) setelah surat selesai tanpa menghapus riwayat tracking
- Pusat Bantuan / FAQ terintegrasi dengan WhatsApp dan email admin
- Halaman About aplikasi

---

## 🛠️ Fitur Admin Dashboard

### Panel Utama (`/admin/dashboard`)
- Kartu ringkasan surat: Total / Diproses / Selesai / Ditolak
- Tabel surat terbaru dengan filter
- Rekap surat per jenis
- Riwayat pemrosesan oleh admin

### Manajemen Surat (`/admin/surat`)
- Daftar lengkap semua surat dalam tabel dengan filter
- **Detail Surat** (`/admin/surat/{uuid}`):
  - Preview Word dan Lampiran
  - Timeline & komentar admin per tahap
  - Setujui / tolak surat dengan catatan
  - Riwayat revisi, penomoran, dan penghapusan
  - QR Code verifikasi
  - Export surat ke PDF
  - Upload ulang file (pada tahap Verifikasi Aspirasi)

### Laporan (`/admin/laporan`)
- Rekap surat per bulan, tahun, dan jenis
- Export data surat

### Riwayat (`/admin/riwayat`)
- Riwayat semua surat yang pernah diajukan
- Indikator surat sudah/belum diproses
- Informasi admin yang mengelola setiap surat

### Fitur Lainnya
| Menu | Fungsi |
|---|---|
| `/admin/notifikasi` | Notifikasi surat masuk, keluar, revisi, tolak, hapus, proses, selesai |
| `/admin/template` | Kelola template surat (tambah / hapus) |
| `/admin/users` | Data user & admin, statistik surat per akun, info role |
| `/admin/logs` | Log aktivitas aplikasi dan pengguna |
| `/admin/chart` | Grafik statistik per bulan, tahun, jenis, dan sifat surat |

### Ketentuan Admin
- Admin **tidak dapat mengubah role** sendiri setelah ditetapkan
- Surat selesai → file otomatis dihapus setelah **3 hari**
- Surat ditolak & tidak direvisi → otomatis dihapus setelah **5 hari**

---

## 👥 Role-based Admin

| Role | Kewenangan Tahap |
|---|---|
| `admin_aspirasi` | Verifikasi Aspirasi · Penomoran · Tanda Tangan DS · Pengiriman TNDe · Pengiriman Srikandi · Pengarsipan |
| `admin_tu` | Verifikasi KasubagTU |
| `admin_kabag` | Verifikasi Kepala Balai |

---

## 📂 Jenis & Sifat Surat

**Jenis Surat:**
- Nota Dinas
- Surat Dinas
- Surat Keputusan
- Surat Pernyataan
- Surat Keterangan
- Surat Undangan
- Surat Lainnya

**Sifat Surat:**
- Biasa
- Segera
- Rahasia

---

## 🔒 Keamanan

| Fitur Keamanan | Detail |
|---|---|
| **Hashing Password** | bcrypt |
| **Proteksi XSS & SQL Injection** | Validasi dan sanitasi input |
| **CSRF Protection** | Token CSRF pada setiap form |
| **Rate Limit Login** | Maks. 5 percobaan/menit per IP |
| **reCAPTCHA v2** | Google reCAPTCHA pada halaman register |
| **Validasi Upload** | Pemeriksaan MIME type dan ukuran file |
| **QR Code Verifikasi** | Setiap surat keluar dilengkapi QR Code autentikasi |

---

## 🛠️ Teknologi

- **Framework:** Laravel 12
- **Bahasa:** PHP 8.x
- **Frontend:** Blade Template, Animasi smooth
- **Autentikasi:** Laravel Auth + reCAPTCHA v2
- **Notifikasi Email:** Laravel Mail (lupa password, notifikasi surat)
- **Jadwal Otomatis:** Laravel Scheduler (auto-refresh pukul 08:00 & 16:00, hapus surat otomatis)
- **Keamanan:** bcrypt, CSRF, rate limiting, validasi MIME

---

## 🚀 Instalasi

```bash
# 1. Clone repositori
git clone https://github.com/your-org/arsip-surat-suml.git
cd arsip-surat-suml

# 2. Install dependensi
composer install
npm install && npm run build

# 3. Konfigurasi environment
cp .env.example .env
php artisan key:generate

# 4. Atur database dan variabel di .env
# (DB_*, MAIL_*, RECAPTCHA_SITE_KEY, RECAPTCHA_SECRET_KEY)

# 5. Migrasi & seeding database
php artisan migrate --seed

# 6. Jalankan aplikasi
php artisan serve
```

> Pastikan scheduler Laravel berjalan untuk fitur auto-refresh dan penghapusan surat otomatis:
> ```bash
> php artisan schedule:work
> ```

---

<div align="center">

Dibuat dengan ❤️ untuk Balai Pengelolaan SUML

</div>
