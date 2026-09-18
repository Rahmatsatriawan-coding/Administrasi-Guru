# API Contract Administrasi-Guru

## 1. Deskripsi

API Contract merupakan kesepakatan antara Front-End dan Back-End
mengenai komunikasi data pada sistem Administrasi-Guru.

Dokumen ini menjadi acuan bagi:

- Wawan — Project Manager
- Guntur — Front-End Developer
- Rahmat — Back-End Developer

API menggunakan REST API dengan format data JSON.
Produksi
https://domain-aplikasi.com/api
3. Format Tanggapan
Kesuksesan
{
  "success": true,
  "message": "Data berhasil diambil",
  "data": {}
}
Kesalahan
{
  "success": false,
  "message": "Terjadi kesalahan",
  "errors": {}
}
4. Otentikasi
Login
POS
/api/auth/login
Meminta
{
  "username": "guru01",
  "password": "password123"
}
Tanggapan
{
  "success": true,
  "message": "Login berhasil",
  "data": {
    "token": "JWT_TOKEN",
    "user": {
      "id": 1,
      "username": "guru01",
      "role": "GURU"
    }
  }
}
Dapatkan Login Pengguna
MENDAPATKAN
/api/auth/me
Keluar
POS
/api/auth/logout
Otorisasi
Authorization: Bearer JWT_TOKEN
5. Data Siswa
Mendapatkan Semua Siswa
MENDAPATKAN
/api/students
Dapatkan Detail Siswa
MENDAPATKAN
/api/students/:id
Siswa
POS
/api/students
Meminta
{
  "nis": "2026001",
  "name": "Budi Santoso",
  "class_id": 1,
  "gender": "L",
  "phone": "08123456789"
}
Mengubah Siswa
MELETAKKAN
/api/students/:id
Menghapus Siswa
MENGHAPUS
/api/students/:id
Impor Siswa
POS
/api/students/import

Format:

multipart/form-data

File yang Didukung:

.xlsx
.csv
Unduh Templat Siswa
MENDAPATKAN
/api/students/template
6. Materi
Semua Materi
MENDAPATKAN
/api/materials
Detail Materi
MENDAPATKAN
/api/materials/:id
Unggah Materi
POS
/api/materials

Format:

multipart/form-data

Data:

title
description
class_id
subject_id
file
Pembaruan Materi
MELETAKKAN
/api/materials/:id
Hapus Materi
MENGHAPUS
/api/materials/:id
Pratinjau Materi
MENDAPATKAN
/api/materials/:id/preview
7. Bank Soal
Semua Bank Soal
MENDAPATKAN
/api/question-banks
Detail Bank Soal
MENDAPATKAN
/api/question-banks/:id
Tambah Bank Soal
POS
/api/question-banks
Meminta
{
  "name": "Bank Soal Matematika Kelas X",
  "subject_id": 1,
  "class_id": 1
}
Pembaruan Bank Soal
MELETAKKAN
/api/question-banks/:id
Hapus Bank Soal
MENGHAPUS
/api/question-banks/:id
8. Soal
Semua Soal
MENDAPATKAN
/api/questions
Tambah Soal
POS
/api/questions
Meminta
{
  "question_bank_id": 1,
  "question": "Berapakah hasil dari 2 + 2?",
  "type": "MULTIPLE_CHOICE",
  "options": [
    {
      "option": "A",
      "text": "3"
    },
    {
      "option": "B",
      "text": "4"
    },
    {
      "option": "C",
      "text": "5"
    }
  ],
  "correct_answer": "B"
}
Pembaruan Soal
MELETAKKAN
/api/questions/:id
Hapus Soal
MENGHAPUS
/api/questions/:id
Impor Soal
POS
/api/questions/import

Format:

multipart/form-data

Mengajukan:

.xlsx
.csv
Unduh Templat Soal
MENDAPATKAN
/api/questions/template
9. Ujian
Semua Ujian
MENDAPATKAN
/api/exams
Detail Ujian
MENDAPATKAN
/api/exams/:id
Membuat Ujian
POS
/api/exams
Meminta
{
  "title": "Ujian Matematika",
  "class_id": 1,
  "subject_id": 1,
  "duration": 60,
  "start_time": "2026-09-20 08:00:00",
  "end_time": "2026-09-20 09:00:00"
}
Pembaruan Ujian
MELETAKKAN
/api/exams/:id
Hapus Ujian
MENGHAPUS
/api/exams/:id
Memulai / Memasukkan Ujian
POS
/api/exams/:id/start
Mengakhiri Ujian
POS
/api/exams/:id/finish
Peserta Ujian
MENDAPATKAN
/api/exams/:id/participants
Simpan Jawaban
POS
/api/exams/:id/answers
Meminta
{
  "question_id": 10,
  "answer": "B"
}
Kirim Ujian
POS
/api/exams/:id/submit
Melihat Hasil Ujian
MENDAPATKAN
/api/exams/:id/result
Status Ujian
DRAFT
SCHEDULED
LIVE
FINISHED
10. Pemantauan Waktu Nyata

Pemantauan menggunakan WebSocket .

Peristiwa:

student_joined
student_submitted
connection_status

Status koneksi:

ONLINE
OFFLINE

Pemantauan informasi:

Nama siswa
Status ujian
Waktu mulai
Waktu selesai
Status koneksi
11. Anti-Kecurangan

Sistem mencatat aktivitas yang dapat terdeteksi selama ujian.

Simpan
POS
/api/exams/:id/violations
Meminta
{
  "type": "TAB_SWITCH",
  "description": "Siswa berpindah tab"
}
Semua
MENDAPATKAN
/api/exams/:id/violations
Siswa
MENDAPATKAN
/api/exams/:id/participants/:studentId/violations
Jenis λ
TAB_SWITCH
FULLSCREEN_EXIT
PAGE_LEAVE
CONNECTION_LOST

Catatan: fitur anti-cheat hanya mencatat aktivitas yang dapat dideteksi oleh browser dan bukan jaminan pencegahan kondisi 100%.

12. Kode QR Absensi

Absensi menggunakan QR Code.

Membuat Sesi Absensi
POS
/api/attendance/sessions
Meminta
{
  "class_id": 1,
  "subject_id": 1,
  "duration": 15
}
Tanggapan
{
  "success": true,
  "message": "Sesi absensi berhasil dibuat",
  "data": {
    "session_id": 1,
    "qr_token": "QR_TOKEN",
    "started_at": "2026-09-20 07:00:00",
    "expired_at": "2026-09-20 07:15:00",
    "status": "ACTIVE"
  }
}
Melihat Sesi Absensi
MENDAPATKAN
/api/attendance/sessions
Menutup Sesi Absensi
POS
/api/attendance/sessions/:id/close
Pindai Kode QR
POS
/api/attendance/scan
Meminta
{
  "qr_token": "QR_TOKEN"
}
Validasi

Sistem harus diperiksa:

QR masih aktif
Sesi absensi sesuai
Siswa terdaftar di kelas
Siswa belum melakukan absensi
Waktu absensi masih berlaku

Jika valid:

HADIR
13. Data Absensi
Semua Absensi
MENDAPATKAN
/api/attendance
Absensi Harian
MENDAPATKAN
/api/attendance/daily
Absensi Mingguan
MENDAPATKAN
/api/attendance/weekly
Absensi Bulanan
MENDAPATKAN
/api/attendance/monthly
Semester Absensi
MENDAPATKAN
/api/attendance/semester
Perbarui Status Absensi
MELETAKKAN
/api/attendance/:id
Meminta
{
  "status": "IZIN",
  "description": "Keperluan keluarga"
}
Status Absensi
HADIR
IZIN
SAKIT
ALPA
14. Laporan
Laporan Absensi
MENDAPATKAN
/api/reports/attendance
Statistik Absensi
MENDAPATKAN
/api/reports/attendance/chart
Ekspor Excel
MENDAPATKAN
/api/reports/attendance/export?format=xlsx
Ekspor PDF
MENDAPATKAN
/api/reports/attendance/export?format=pdf
15. Peran dan Otorisasi

Sistem menggunakan peran:

GURU
SISWA
ADMIN
GURU

Dapat:

Mengelola siswa
Mengelola materi
Mengelola bank soal
Membuat ujian
Mengelola absensi
Melihat monitoring
Melihat laporan
SISWA

Dapat:

Melihat materi
Mengikuti ujian
Melihat hasil ujian
Melakukan absensi QR
Melihat profil
ADMIN

Jika digunakan, dapat:

Mengelola user
Mengelola data sistem
Mengelola konfigurasi
16. Kode Status HTTP
Status	Keterangan
200	Berhasil
201	Berhasil membuat data
400	Permintaan tidak valid
401	Belum login
403	Tidak memiliki akses
404	Data tidak ditemukan
409	Data |
422	Validasi gagal
500	Kesalahan server
17. Aturan API
Semua API menggunakan awalan /api.
Data menggunakan format JSON.
Berkas menggunakan multipart/form-data.
API yang membutuhkan login menggunakan JWT.
Peran pengguna harus divalidasi oleh Back-End.
Kata sandi tidak boleh disimpan dalam bentuk plaintext.
Semua input harus divalidasi.
File upload harus divalidasi tipe dan ukurannya.
Kode QR harus memiliki masa berlaku.
Siswa hanya dapat melakukan satu absensi pada satu sesi.
Waktu ujian menggunakan waktu dari server.
Setiap perubahan API harus dikomunikasikan ke Front-End.
18. Pembagian Tanggung Jawab
Front-End - Guntur

Bertanggung jawab terhadap:

UI/UX implementation
Form input
Validasi tampilan
API integration
Loading state
Error handling
WebSocket client
QR Code scanner
Responsive design
Back-End - Rahmat

Bertanggung jawab terhadap:

REST API
Authentication
Authorization
Database
CRUD
File upload
Import Excel/CSV
QR Code session
QR validation
Anti-cheat logging
WebSocket
Reports
Export Excel/PDF
Manajer Proyek - Wawan

Bertanggung jawab terhadap:

Dokumentasi
Requirement
User Flow
ERD
API Contract
Pembagian tugas
GitHub Issues
GitHub Milestone
Review Pull Request
Koordinasi Front-End dan Back-End
Testing dan integrasi
19. Alur Komunikasi Front-End dan Back-End
User
  ↓
Front-End
  ↓
REST API
  ↓
Back-End
  ↓
Database
  ↓
Back-End
  ↓
JSON Response
  ↓
Front-End
  ↓
User

Untuk fitur pemantauan waktu nyata:

Front-End
     ↕
 WebSocket
     ↕
Back-End
20. Catatan Perubahan API

Setiap perubahan API harus dicatat oleh tim.

Format:

Tanggal:
Perubahan:
Endpoint:
Alasan:
Front-End terdampak:
Back-End terdampak:
Status:

Contoh:

Tanggal: 20 September 2026
Perubahan: Menambahkan endpoint scan QR
Endpoint: POST /api/attendance/scan
Alasan: Implementasi absensi QR Code
Front-End terdampak: Ya
Back-End terdampak: Ya
Status: Selesai
21. Kesimpulan

Kontrak API ini menjadi acuan komunikasi antara Front-End dan Back-End.

Setiap endpoint yang dibuat harus mengikuti dokumentasi ini agar proses integrasi aplikasi Administrasi-Guru berjalan terstruktur dan mengurangi kesalahan komunikasi antar anggota tim.


### Cara memasukkannya ke GitHub

1. Buka repository **Administrasi-Guru**
2. Masuk folder **`docs`**
3. Klik **`04-api-contract.md`**
4. Klik ikon **pensil (Edit)**
5. **Ctrl + A**
6. Hapus isi lama
7. **Paste** isi di atas
8. Scroll ke bawah
9. Isi commit, misalnya:
   ```text
   docs: update API contract

---

# 2. Base URL

Development:

```text
http://localhost:3000/api
