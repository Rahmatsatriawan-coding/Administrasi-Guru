# User Flow Administrasi-Guru

## 1. Gambaran Umum

User Flow menjelaskan alur penggunaan sistem **Administrasi-Guru**
berdasarkan jenis pengguna, yaitu **Guru** dan **Siswa**.

Alur utama sistem meliputi:

1. Authentication
2. Dashboard
3. Data Siswa
4. Materi
5. Bank Soal
6. Ujian
7. Monitoring Ujian Real-Time
8. Anti-Cheat
9. Absensi QR Code
10. Laporan
11. Profil
12. Logout

---

# 2. User Flow Guru

## 2.1 Login Guru

Alur login guru:

```text
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
```

Jika username dan password valid, guru diarahkan ke **Dashboard Guru**.

---

## 2.2 Dashboard Guru

Setelah berhasil login, guru masuk ke Dashboard.

```text
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
```

Dashboard menampilkan informasi ringkas:

- Jumlah siswa
- Jumlah materi
- Jumlah bank soal
- Ujian aktif
- Rekap kehadiran
- Aktivitas terbaru

---

# 3. User Flow Data Siswa

## 3.1 Melihat Data Siswa

```text
Dashboard
    ↓
Data Siswa
    ↓
Daftar Siswa
```

Guru dapat:

- Melihat data siswa
- Mencari siswa
- Memfilter siswa
- Melihat detail siswa
- Menambah siswa
- Mengubah data siswa
- Menghapus siswa

---

## 3.2 Menambah Siswa

```text
Data Siswa
    ↓
Tambah Siswa
    ↓
Isi Form Siswa
    ↓
Validasi Data
    ↓
Simpan
    ↓
Data Berhasil Ditambahkan
```

---

## 3.3 Import Siswa

Guru dapat memasukkan data siswa menggunakan file **Excel/CSV**.

```text
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
Apakah Data Valid?
   ┌──┴──┐
  Tidak  Ya
   ↓      ↓
Perbaiki  Import
Data      ↓
          Data Siswa
```

Guru dapat mengunduh template terlebih dahulu sebelum melakukan import.

---

# 4. User Flow Materi

## 4.1 Mengelola Materi

```text
Dashboard
    ↓
Materi
    ↓
Daftar Materi
```

Guru dapat:

- Mengunggah materi
- Melihat materi
- Melakukan preview materi
- Mengubah materi
- Menghapus materi
- Mengelompokkan materi berdasarkan kelas
- Mengelompokkan materi berdasarkan mata pelajaran

---

## 4.2 Preview Materi

```text
Daftar Materi
    ↓
Pilih Materi
    ↓
Preview Materi
    ↓
Guru Membaca/Melihat Materi
```

Materi dapat ditampilkan melalui fitur **preview tanpa harus mengunduh file**.

---

# 5. User Flow Bank Soal

## 5.1 Mengelola Bank Soal

```text
Dashboard
    ↓
Bank Soal
    ↓
Daftar Bank Soal
```

Guru dapat:

- Membuat bank soal
- Melihat bank soal
- Menambah soal
- Mengubah soal
- Menghapus soal
- Mengimpor soal menggunakan template

---

## 5.2 Import Soal

Guru dapat membuat banyak soal menggunakan template yang telah disediakan.

```text
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
Apakah Data Valid?
   ┌──┴──┐
  Tidak  Ya
   ↓      ↓
Perbaiki  Simpan
Data      ↓
          Bank Soal
```

---

# 6. User Flow Ujian

## 6.1 Membuat Ujian

```text
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
```

Informasi ujian meliputi:

- Nama ujian
- Mata pelajaran
- Kelas
- Daftar soal
- Tanggal ujian
- Waktu mulai
- Waktu selesai
- Durasi
- Status ujian

---

## 6.2 Membuka Ujian

```text
Daftar Ujian
    ↓
Pilih Ujian
    ↓
Review Pengaturan
    ↓
Aktifkan Ujian
    ↓
Status = LIVE
    ↓
Siswa Dapat Mengikuti Ujian
```

Status ujian:

```text
DRAFT
  ↓
SCHEDULED
  ↓
LIVE
  ↓
FINISHED
```

---

# 7. User Flow Siswa Mengikuti Ujian

```text
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
```

### Jika waktu ujian habis

```text
Timer = 00:00
     ↓
Sistem Mengakhiri Ujian
     ↓
Jawaban Disimpan
     ↓
Ujian Selesai
```

---

# 8. User Flow Monitoring Ujian Real-Time

Guru dapat memantau peserta selama ujian berlangsung.

```text
Dashboard Guru
      ↓
Ujian
      ↓
Pilih Ujian Aktif
      ↓
Monitoring Real-Time
```

Informasi yang ditampilkan:

- Total peserta
- Sedang mengerjakan
- Sudah selesai
- Belum mulai
- Status koneksi
- Waktu pengerjaan

Contoh:

```text
Total Peserta       : 30
Sedang Mengerjakan  : 24
Sudah Selesai       : 4
Belum Mulai         : 2
```

---

# 9. User Flow Anti-Cheat

Sistem mendeteksi dan mencatat aktivitas mencurigakan yang dapat
dideteksi oleh browser selama ujian berlangsung.

```text
Siswa Mengerjakan Ujian
          ↓
Sistem Memantau Aktivitas
          ↓
Aktivitas Mencurigakan?
      ┌───┴───┐
     Tidak    Ya
      ↓        ↓
   Lanjut   Catat Pelanggaran
                   ↓
            Monitoring Guru
```

Aktivitas yang dapat dicatat:

- Berpindah tab
- Keluar dari mode fullscreen
- Meninggalkan halaman ujian
- Kehilangan koneksi
- Aktivitas lain yang dapat dideteksi oleh browser

### Catatan

> Fitur anti-cheat merupakan mekanisme **deteksi dan mitigasi**.
> Sistem tidak menjamin pencegahan kecurangan secara 100%.

---

# 10. User Flow Absensi QR Code

Absensi dilakukan secara online menggunakan **QR Code**.

## 10.1 Guru Membuat Sesi Absensi

```text
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
```

QR Code memiliki **masa berlaku tertentu**.

---

## 10.2 Siswa Melakukan Absensi

```text
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
QR Masih Aktif?
   ┌──┴──┐
  Tidak  Ya
   ↓      ↓
 Gagal   Validasi Siswa
              ↓
        Terdaftar di Kelas?
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
```

### Validasi Absensi

Sistem melakukan validasi:

1. QR Code masih aktif.
2. QR Code sesuai dengan sesi absensi.
3. Siswa terdaftar pada kelas tersebut.
4. Siswa belum melakukan absensi pada sesi tersebut.
5. Waktu absensi masih berada dalam periode yang ditentukan.

---

## 10.3 Hasil Absensi

Jika absensi berhasil:

```text
✓ ABSENSI BERHASIL

Nama       : Nama Siswa
Kelas      : Kelas Siswa
Tanggal    : Tanggal
Waktu      : Waktu Scan
Status     : HADIR
```

Jika QR Code sudah tidak aktif:

```text
✕ ABSENSI GAGAL

QR Code sudah kedaluwarsa.

Silakan gunakan QR Code yang masih aktif.
```

---

# 11. User Flow Rekap Absensi Guru

```text
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
```

Guru dapat melihat:

- Hadir
- Izin
- Sakit
- Alpa
- Jumlah siswa
- Persentase kehadiran

---

# 12. User Flow Laporan

```text
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
```

Jenis laporan:

- Laporan siswa
- Laporan absensi
- Laporan ujian
- Laporan nilai
- Statistik

---

# 13. User Flow Profil

```text
Dashboard
    ↓
Profil
    ↓
Lihat Profil
    ↓
Edit Profil
    ↓
Simpan Perubahan
```

Guru dapat mengubah informasi profil sesuai dengan hak akses.

---

# 14. User Flow Logout

```text
Dashboard
    ↓
Logout
    ↓
Konfirmasi
    ↓
Logout Berhasil
    ↓
Halaman Login
```

---

# 15. Ringkasan User Flow Guru

```text
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
```

---

# 16. Ringkasan User Flow Siswa

```text
LOGIN
  ↓
DASHBOARD SISWA
  │
  ├── MATERI
  │     └── LIHAT / PREVIEW
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
  └── RIWAYAT / NILAI
```

---

# 17. Kesimpulan

User Flow ini menjadi dasar dalam pengembangan sistem
**Administrasi-Guru**, terutama untuk:

1. Perancangan UI/UX.
2. Perancangan database.
3. Perancangan API.
4. Pembagian tugas Front-End dan Back-End.
5. Pengembangan sistem.
6. Pengujian sistem.
7. Integrasi sistem.

Dokumen ini menjadi acuan bersama bagi:

- **Wawan** — Project Manager
- **Guntur** — Front-End Developer
- **Rahmat** — Back-End Developer

Setiap perubahan pada alur sistem harus didiskusikan dan disepakati
oleh tim sebelum diterapkan pada tahap pengembangan.
