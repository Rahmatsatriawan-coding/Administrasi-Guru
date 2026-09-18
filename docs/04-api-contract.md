# API Contract Administrasi-Guru

## 1. Deskripsi

API Contract merupakan kesepakatan antara Front-End dan Back-End mengenai komunikasi data pada sistem Administrasi-Guru.

Dokumen ini menjadi acuan bagi:

- Wawan — Project Manager
- Guntur — Front-End Developer
- Rahmat — Back-End Developer

API menggunakan REST API dengan format data JSON.

---

## 2. Base URL

### Development

```text
http://localhost:3000/api
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
Dapatkan Pengguna Saat Ini

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
Mendapatkan Semua Materi

MENDAPATKAN

/api/materials
Dapatkan Detail Materi

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
Mendapatkan Semua Bank Soal

MENDAPATKAN

/api/question-banks
Dapatkan Detail Bank Soal

MENDAPATKAN

/api/question-banks/:id
Bank Soal

POS

/api/question-banks
Meminta
{
  "name": "Bank Soal Matematika Kelas X",
  "subject_id": 1,
  "class_id": 1
}
Mengubah Bank Soal

MELETAKKAN

/api/question-banks/:id
Bank Soal

MENGHAPUS

/api/question-banks/:id
8. Soal
Mendapatkan Semua Soal

MENDAPATKAN

/api/questions
Soal

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
Mengubah Soal

MELETAKKAN

/api/questions/:id
Menghapus Soal

MENGHAPUS

/api/questions/:id
Impor Soal

POS

/api/questions/import

Format:

multipart/form-data

File yang Didukung:

.xlsx
.csv
Unduh Templat Soal

MENDAPATKAN

/api/questions/template
9. Ujian
Mendapatkan Semua Ujian

MENDAPATKAN

/api/exams
Dapatkan Detail Ujian

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
Mengubah Ujian

MELETAKKAN

/api/exams/:id
Menghapus Ujian

MENGHAPUS

/api/exams/:id
Memulai / Memasukkan Ujian

POS

/api/exams/:id/start
Mengakhiri Ujian

POS

/api/exams/:id/finish
Mendapatkan Peserta Ujian

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

Memantau ujian menggunakan WebSocket.

Peristiwa
student_joined
student_submitted
connection_status
Status Koneksi
ONLINE
OFFLINE
Informasi Pemantauan
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
Dapatkan Semua

MENDAPATKAN

/api/exams/:id/violations
Mendapatkan Pelanggaran Siswa

MENDAPATKAN

/api/exams/:id/participants/:studentId/violations
Jenis λ
TAB_SWITCH
FULLSCREEN_EXIT
PAGE_LEAVE
CONNECTION_LOST

Catatan: Fitur anti-cheat hanya mencatat aktivitas yang dapat dideteksi oleh browser dan bukan jaminan pencegahan kondisi 100%.

12. Kode QR Absensi

Sistem absensi menggunakan QR Code.

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
Validasi Absensi

Sistem harus diperiksa:

Kode QR masih aktif
Sesi absensi sesuai
Siswa terdaftar di kelas
Siswa belum melakukan absensi
Waktu absensi masih berlaku

Jika valid:

HADIR
13. Data Absensi
Mendapatkan Semua Absensi

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
Mengubah Status Absensi

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

Mengawasi siswa
materi
Mengelola soal bank
Membuat ujian
Mengelola ketidakhadiran
Melihat pemantauan
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

pengguna
Mengelola sistem data
Konfigurasi Kepala
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
Front-End — Guntur

Bertanggung jawab terhadap:

Implementasi UI/UX
Masukan formulir
Validasi Tampilan
Integrasi API
Status pemuatan
Penanganan kesalahan
Klien WebSocket
Pemindai Kode QR
Desain responsif
Back-End — Rahmat

Bertanggung jawab terhadap:

API REST
Autentikasi
Otorisasi
Basis data
KOTORAN
Unggah file
Impor Excel/CSV
Sesi Kode QR
Validasi QR
Pencatatan anti-kecurangan
WebSocket
Laporan
Ekspor Excel/PDF
Manajer Proyek — Wawan

Bertanggung jawab terhadap:

Dokumentasi
Persyaratan
Alur Pengguna
ERD
Kontrak API
Pembagian tugas
Masalah GitHub
Pencapaian GitHub
Tinjau Permintaan Tarik (Pull Request)
Koordinasi Front-End dan Back-End
Pengujian dan integrasi
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
Pemantauan Waktu Nyata
Front-End
    ↕
 WebSocket
    ↕
Back-End
20. Catatan Perubahan API

Setiap perubahan API harus dicatat oleh tim.

Format
Tanggal:
Perubahan:
Endpoint:
Alasan:
Front-End terdampak:
Back-End terdampak:
Status:
Contoh
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


**Catatan:** Karena di dalamnya ada blok kode Markdown, kalau kamu menyalin dari tampilan chat ini, pastikan **semua isi dalam satu blok paling luar** ikut tersalin.
