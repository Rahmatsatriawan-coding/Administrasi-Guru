 User Flow Administrasi-Guru
1. Gambaran Umum

User Flow menjelaskan alur penggunaan sistem Administrasi-Guru
berdasarkan jenis pengguna, yaitu Guru dan Siswa.

Alur sistem dibagi menjadi:

1. Authentication
2. Dashboard
3. Data Siswa
4. Materi
5. Bank Soal
6. Ujian
7. Monitoring Ujian
8. Anti-Cheat
9. Absensi QR Code
10. Laporan
11. Profil

2. User Flow Guru
2.1 Login Guru
    text
Halaman Login
      ↓
Input Username
      ↓
Input Password
      ↓
Klik Login
      ↓
Validasi Data
      ↓
Apakah data valid?
   ┌──┴──┐
  Tidak  Ya
   ↓      ↓
Pesan    Dashboard Guru
Error
2.2 Dasbor Guru

Setelah berhasil login, guru masuk ke Dashboard.
Dashboard Guru
      │
      ├── Data Siswa
      ├── Materi
      ├── Bank Soal
      ├── Ujian
      ├── Monitoring
      ├── Absensi
      ├── Laporan
      └── Profil

Dashboard menampilkan informasi ringkas:

Jumlah siswa.
Jumlah materi.
Jumlah soal bank.
Ujian aktif.
Rekap kehadiran.
Aktivitas terbaru.

3. Alur Data Pengguna Siswa
3.1 Melihat Data Siswa
Dashboard
    ↓
Data Siswa
    ↓
Daftar Siswa

Guru dapat:

Melihat data siswa.
Mencari siswa.
Memfilter siswa.
Memperhatikan detail siswa.
Menambah siswa.
Mengubah siswa.
Menghapus siswa.

3.2 Menambah Siswa
Data Siswa
    ↓
Tambah Siswa
    ↓
Isi Form Siswa
    ↓
Validasi
    ↓
Simpan
    ↓
Data berhasil ditambahkan

3.3 Impor Siswa
Data Siswa
    ↓
Import Excel/CSV
    ↓
Upload File
    ↓
Validasi File
    ↓
Preview Data
    ↓
Apakah data valid?
   ┌──┴──┐
  Tidak  Ya
   ↓      ↓
Perbaiki  Import
Data      ↓
          Data Siswa

Guru dapat mengunduh template sebelum melakukan import.

4. Alur Pengguna Materi
4.1 Mengelola Materi
Dashboard
    ↓
Materi
    ↓
Daftar Materi

Guru dapat:

Unggah materi.
Melihat materi.
Pratinjau materi.
Mengubah materi.
Menghapus materi.
Mengelompokkan materi berdasarkan kelas.
Mengelompokkan materi berdasarkan mata pelajaran.

4.2 Pratinjau Materi
Daftar Materi
    ↓
Pilih Materi
    ↓
Preview Materi
    ↓
Guru membaca/melihat materi

Materi dapat ditampilkan melalui preview tanpa harus mengunduh file.

5. Alur Pengguna Bank Soal
5.1 Mengelola Bank Soal
Dashboard
    ↓
Bank Soal
    ↓
Daftar Bank Soal

Guru dapat:

Membuat soal bank.
Melihat soal bank.
Menambah soal.
Mengubah soal.
Menghapus soal.
Mengimpor soal menggunakan template.

5.2 Impor Soal
Bank Soal
    ↓
Import Soal
    ↓
Download Template
    ↓
Isi Template
    ↓
Upload File
    ↓
Validasi
    ↓
Preview Soal
    ↓
Apakah valid?
   ┌──┴──┐
  Tidak  Ya
   ↓      ↓
Perbaiki  Simpan
Data      ↓
          Bank Soal

6. Ujian Alur Pengguna
6.1 Membuat Ujian
Dashboard
    ↓
Ujian
    ↓
Buat Ujian
    ↓
Isi Informasi Ujian
    ↓
Pilih Kelas
    ↓
Pilih Soal
    ↓
Atur Jadwal
    ↓
Atur Durasi
    ↓
Simpan
    ↓
Ujian Berstatus Draft

Informasi ujian meliputi:

Nama ujian.
Mata pelajaran.
Kelas.
Daftar soal.
Tanggal ujian.
Waktu mulai.
Waktu selesai.
Durasi.
Status ujian.

6.2 Membuka Ujian
Daftar Ujian
    ↓
Pilih Ujian
    ↓
Review Pengaturan
    ↓
Aktifkan Ujian
    ↓
Status = Live
    ↓
Siswa dapat mengikuti ujian

7. Alur Pengguna Siswa Mengikuti Ujian
Login Siswa
    ↓
Dashboard Siswa
    ↓
Ujian
    ↓
Pilih Ujian Aktif
    ↓
Lihat Detail Ujian
    ↓
Mulai Ujian
    ↓
Konfirmasi
    ↓
Kerjakan Soal
    ↓
Timer Berjalan
    ↓
Kirim Jawaban
    ↓
Konfirmasi Pengumpulan
    ↓
Ujian Selesai

Jika waktu habis:

Timer = 00:00
     ↓
Sistem mengakhiri ujian
     ↓
Jawaban disimpan
     ↓
Ujian selesai

8. Pemantauan Alur Pengguna Ujian Real-Time

Guru dapat ikut serta dalam peserta ketika ujian berlangsung.

Dashboard Guru
      ↓
Ujian
      ↓
Pilih Ujian Aktif
      ↓
Monitoring Real-Time

Informasi yang ditampilkan:

Jumlah peserta.
Sedang mengerjakan.
Sudah selesai.
Belum dimulai.
Status koneksi.
Waktu pengerjaan.

Contoh:

Total Peserta : 30

Sedang Mengerjakan : 24
Sudah Selesai      : 4
Belum Mulai        : 2

9. Anti-Kecurangan Alur Pengguna

Sistem mendeteksi aktivitas yang dapat dicatat oleh browser.

Siswa Mengerjakan Ujian
          ↓
Sistem Memantau Aktivitas
          ↓
Aktivitas Mencurigakan?
      ┌───┴───┐
     Tidak    Ya
      ↓        ↓
Lanjut     Catat Pelanggaran
               ↓
        Monitoring Guru

Aktivitas yang dapat dicatat:

Berpindah tab.
Keluar dari mode layar penuh.
Meninggalkan halaman ujian.
Kehilangan koneksi.
Aktivitas lain yang dapat dideteksi browser.

Catatan:

Fitur anti-cheat merupakan mekanisme deteksi dan mitigasi.
Sistem tidak menjamin pencegahan kondisi secara 100%.

10. Alur Pengguna Kode QR Absensi
10.1 Guru Membuat Sesi Absensi
Dashboard Guru
      ↓
Absensi
      ↓
Buat Sesi Absensi
      ↓
Pilih Kelas
      ↓
Pilih Mata Pelajaran
      ↓
Atur Waktu
      ↓
Generate QR Code
      ↓
QR Code Aktif

QR Code memiliki masa berlaku tertentu.

10.2 Siswa Melakukan Absensi
Login Siswa
      ↓
Absensi
      ↓
Scan QR Code
      ↓
Sistem Membaca QR
      ↓
Validasi QR
      ↓
QR masih aktif?
   ┌──┴──┐
  Tidak  Ya
   ↓      ↓
Gagal   Validasi Siswa
          ↓
      Terdaftar di kelas?
        ┌──┴──┐
       Tidak  Ya
        ↓      ↓
       Gagal  Sudah Absen?
                 ┌──┴──┐
                Ya     Belum
                ↓       ↓
              Gagal   Simpan
                        ↓
                   HADIR
10.3 Hasil Absensi

Jika berhasil:

✓ Absensi Berhasil

Nama       : Nama Siswa
Kelas      : Kelas Siswa
Tanggal    : Tanggal
Waktu      : Waktu Scan
Status     : HADIR

Jika QR sudah tidak aktif:

✕ Absensi Gagal

QR Code sudah kedaluwarsa.
Silakan gunakan QR Code yang masih aktif.
11. Alur Pengguna Rekap Absensi Guru
Dashboard Guru
      ↓
Absensi
      ↓
Rekap Absensi
      ↓
Pilih Periode
      ↓
Hari / Minggu / Bulan / Semester
      ↓
Tampilkan Data
      ↓
Lihat Rekap
      ↓
Export Excel/PDF

Guru dapat melihat:

Hadir.
Izin.
Sakit.
Alpa.
Jumlah siswa.
Persentase hadir.

12. Laporan Alur Pengguna
Dashboard Guru
      ↓
Laporan
      ↓
Pilih Jenis Laporan
      ↓
Pilih Periode
      ↓
Pilih Kelas
      ↓
Tampilkan Data
      ↓
Laporan
   ┌──┴──┐
  Excel  PDF

Jenis laporan:

Laporan siswa.
Laporan absensi.
Laporan ujian.
Laporan nilai.
Statistik.
13. Profil Alur Pengguna
Dashboard
    ↓
Profil
    ↓
Lihat Profil
    ↓
Edit Profil
    ↓
Simpan Perubahan

Guru dapat mengubah informasi profil sesuai hak akses.

14. Alur Pengguna Keluar
Dashboard
    ↓
Logout
    ↓
Konfirmasi
    ↓
Logout
    ↓
Halaman Login

15. Ringkasan Alur Guru
LOGIN
  ↓
DASHBOARD
  │
  ├── DATA SISWA
  │     ├── CRUD
  │     └── IMPORT EXCEL/CSV
  │
  ├── MATERI
  │     ├── UPLOAD
  │     └── PREVIEW
  │
  ├── BANK SOAL
  │     ├── CRUD
  │     └── IMPORT TEMPLATE
  │
  ├── UJIAN
  │     ├── BUAT UJIAN
  │     ├── MONITORING REAL-TIME
  │     └── ANTI-CHEAT
  │
  ├── ABSENSI
  │     ├── GENERATE QR
  │     ├── MONITORING
  │     └── REKAP
  │
  ├── LAPORAN
  │     ├── ABSENSI
  │     ├── UJIAN
  │     ├── NILAI
  │     ├── EXCEL
  │     └── PDF
  │
  └── PROFIL

16. Ringkasan Alur Siswa
LOGIN
  ↓
DASHBOARD SISWA
  │
  ├── MATERI
  │     └── LIHAT/PREVIEW
  │
  ├── UJIAN
  │     ├── LIHAT UJIAN
  │     ├── MULAI
  │     ├── KERJAKAN
  │     └── KIRIM
  │
  ├── ABSENSI
  │     ├── SCAN QR
  │     └── ABSENSI BERHASIL
  │
  └── RIWAYAT/NILAI

17. Kesimpulan

Alur Pengguna ini menjadi dasar untuk:

Perancangan UI/UX.
Basis data Peranangan.
Peranangan API.
Pembagian tugas Front-End dan Back-End.
Pengembangan sistem.
Pengujian sistem.
