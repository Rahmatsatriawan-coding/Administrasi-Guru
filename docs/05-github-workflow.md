 GitHub Workflow — Administrasi-Guru

## 1. Tujuan

Dokumen ini menjelaskan aturan penggunaan GitHub dalam pengembangan aplikasi **Administrasi-Guru**.

Tujuannya adalah:

- Mengatur pembagian pekerjaan tim
- Menghindari konflik kode
- Menentukan aturan branch
- Mengatur proses commit dan Pull Request
- Memudahkan proses review
- Menjaga kode tetap terorganisir

---

# 2. Struktur Tim

| Nama | Role | Tanggung Jawab |
|------|------|----------------|
| Wawan | Project Manager | Dokumentasi, koordinasi, GitHub, review dan integrasi |
| Guntur | Front-End Developer | UI/UX dan implementasi Front-End |
| Rahmat | Back-End Developer | API, database dan Back-End |

---

# 3. Struktur Branch

Branch utama yang digunakan:

```text
main
  ↓
develop
  ↓
├── feature/frontend-guntur
└── feature/backend-rahmat
Utama

Branch maindigunakan untuk kode yang sudah stabil dan siap digunakan sebagai versi utama aplikasi.

Kode pada maintidak boleh digunakan untuk fitur pekerjaan yang masih dalam proses.

Mengembangkan

Cabang developdigunakan sebagai integrasi cabang.

Semua fitur yang sudah selesai akan digabungkan ke developmelalui Pull Request.

feature
   ↓
Pull Request
   ↓
develop
Cabang Fitur

Setiap pengembang bekerja pada cabang masing-masing.

Antarmuka Pengguna
feature/frontend-guntur
Bagian Belakang
feature/backend-rahmat
Manajer Proyek / Dokumentasi

Jika Wawan perlu melakukan perubahan kode atau dokumentasi melalui cabang sendiri:

feature/pm-wawan
4. Aturan Cabang
Jangan bekerja langsung di main

terhindar:

main → coding → commit

Gunakan:

develop
   ↓
feature branch
   ↓
coding
   ↓
commit
   ↓
push
   ↓
Pull Request
   ↓
develop
5. Pembagian Tugas
Wawan — Manajer Proyek

Tugas:

Mengatur peta jalan proyek
Membuat Pengaturan dan Masalah GitHub
Membuat Tonggak Sejarah
Mengatur tugas
Menjaga dokumentasi proyek
Kemajuan Mengawasi
Tinjau Permintaan Tarik (Pull Request)
Mengkoordinasikan Front-End dan Back-End
Melakukan pengujian bersama tim
Mengatur proses integrasi
dokumentasi akhir

Dokumentasi utama:

docs/01-requirements.md
docs/02-user-flow.md
docs/03-database-erd.md
docs/04-api-contract.md
docs/05-github-workflow.md
6. Guntur — Pengembang Front-End

Cabang:

feature/frontend-guntur

Tugas utama:

Membuat halaman Login
Membuat Dasbor
Membuat halaman Data Siswa
Membuat halaman Materi
Membuat halaman Bank Soal
Membuat halaman Ujian
Membuat halaman Monitoring
Membuat halaman Absensi
Membuat Pemindai QR
Membuat halaman Laporan
Membuat halaman Profil
Desain responsif
Integrasi API
Integrasi WebSocket
Tampilan Pengujian
7. Rahmat — Pengembang Back-End

Cabang:

feature/backend-rahmat

Tugas utama:

Membuat struktur Back-End
Membuat basis data
Membuat Otentikasi
Buat Otorisasi
Membuat API Data Siswa
Membuat API Materi
Membuat API Bank Soal
Membuat API Soal
Membuat API Ujian
Membuat API Monitoring
Membuat API Anti-Cheat
Membuat API Absensi QR
Membuat API Laporan
Membuat WebSocket
Membuat Ekspor Excel/PDF
Pengujian API
8. Alur Kerja Developer

Setiap pengembang mengikuti alur berikut:

1. Update branch develop
        ↓
2. Buat / gunakan feature branch
        ↓
3. Coding
        ↓
4. Testing
        ↓
5. Commit
        ↓
6. Push ke GitHub
        ↓
7. Buat Pull Request
        ↓
8. Review
        ↓
9. Merge ke develop
9. Perbarui Cabang Sebelum Pengkodean

Sebelum mulai bekerja:

git checkout develop
git pull origin develop

Kemudian pindah ke cabang masing-masing.

Guntur
git checkout feature/frontend-guntur
git merge develop
Rahmat
git checkout feature/backend-rahmat
git merge develop
10. Komitmen Konvensi

Gunakan format commit yang jelas.

Fitur
feat: menambahkan fitur login
Memperbaiki
fix: memperbaiki validasi login
Dokumentasi
docs: memperbarui API contract
Gaya
style: memperbaiki tampilan dashboard
Memperbaiki faktorisasi
refactor: merapikan struktur API
Tes
test: menambahkan pengujian login
11. Contoh Commit
Antarmuka Pengguna
git add .
git commit -m "feat: menambahkan halaman dashboard"
git push origin feature/frontend-guntur
Bagian Belakang
git add .
git commit -m "feat: menambahkan API data siswa"
git push origin feature/backend-rahmat
Dokumentasi
git add .
git commit -m "docs: memperbarui dokumentasi proyek"
git push origin feature/pm-wawan
12. Permintaan Tarik (Pull Request)

Setelah fitur selesai, pengembang membuat Pull Request.

Contoh:

feature/frontend-guntur
        ↓
Pull Request
        ↓
develop

atau:

feature/backend-rahmat
        ↓
Pull Request
        ↓
develop
13. Format Permintaan Tarik (Pull Request)

Judul Pull Request harus jelas.

Contoh:

feat: menambahkan halaman data siswa

Isi Pull Request:

## Perubahan

- Menambahkan halaman Data Siswa
- Menambahkan tabel siswa
- Menambahkan tombol tambah siswa
- Menambahkan tombol edit dan hapus

## Testing

- [x] Halaman dapat dibuka
- [x] Form dapat digunakan
- [x] Data tampil dengan benar
- [x] Tidak ada error pada console

## Catatan

Fitur siap untuk direview.
14. Tinjau Permintaan Tarik (Pull Request)

Sebelum Pull Request di-merge:

Kode harus dapat dijalankan
Tidak ada error utama
Fitur sesuai persyaratan
API sesuai dengan Kontrak API
Tidak merusak fitur lain
Sudah melakukan pengujian
Dokumentasi diperbarui jika diperlukan

Reviewer dapat memberikan:

Approve
Request Changes
Comment
15. Aturan Penggabungan

Penggabungan Alur:

Feature Branch
      ↓
Pull Request
      ↓
Review
      ↓
Approve
      ↓
Merge
      ↓
develop

Setelah fitur masuk ke develop, lakukan pengujian integrasi.

Jika semua fitur sudah stabil:

develop
   ↓
Pull Request
   ↓
main
16. Masalah GitHub

Setiap pekerjaan besar dibuat sebagai Issue.

Contoh:

[FE] Membuat halaman Login
[FE] Membuat Dashboard
[FE] Membuat halaman Data Siswa
[BE] Membuat API Authentication
[BE] Membuat API Data Siswa
[BE] Membuat Database
[DOCS] Membuat dokumentasi API
[TEST] Testing fitur Login
17. Label GitHub

Gunakan label berikut:

Label	Keterangan
FE	Antarmuka Pengguna
MENJADI	Bagian Belakang
DOKUMEN	Dokumentasi
UI/UX	Desain UI/UX
SERANGGA	Perbaikan bug
TES	Pengujian
BASIS DATA	Basis data
API	API
FITUR	Fitur baru
18. Tonggak Sejarah

Milestone digunakan untuk mengelompokkan pekerjaan.

Tahapan 1 — Yayasan Proyek

Pekerjaan:

Repositori GitHub
Cabang
Struktur folder
Persyaratan
Alur Pengguna
ERD
Kontrak API
Dasar-dasar UI/UX
Tahapan 2 — Otentikasi & Data Utama

Pekerjaan:

Login
Peran
Data Siswa
Materi
Basis data
API dasar
Milestone 3 — Soal & Ujian Bank

Pekerjaan:

Bank Soal
Soal
Impor Soal
Membuat Ujian
Peserta Ujian
Jawaban
Penilaian
Milestone 4 — Ketidakhadiran & Pemantauan

Pekerjaan:

Kode QR Absensi
Rekap Absensi
Pemantauan Waktu Nyata
Anti-Kecurangan
WebSocket
Milestone 5 — Laporan & Finalisasi

Pekerjaan:

Laporan
Statistik
Ekspor Excel
Ekspor PDF
Pengujian
Perbaikan bug
Dokumentasi
Penyebaran
19. Definisi Selesai

Sebuah tugas dianggap selesai jika:

 Fitur sudah dibuat
 Fitur dapat dijalankan
 Tidak terdapat error utama
 Sudah melakukan pengujian
 API sesuai kontrak
 UI sesuai desain
 Tidak merusak fitur lain
 Komitmen sudah dibuat
 Sudah push ke GitHub
 Pull Request sudah dibuat
 Sudah ditinjau
 Sudah masuk kedevelop
20. Aturan Komunikasi Tim

Jika terjadi perubahan:

Basis data
API
UI
Persyaratan
Struktur folder
Fitur

Maka perubahan harus dikomunikasikan kepada anggota tim.

Contoh:

[API CHANGE]

Endpoint:
POST /api/attendance/scan

Perubahan:
Menambahkan QR Token

Dampak:
Front-End perlu menyesuaikan request scan QR.
21. Penanganan Konflik Git

Jika terjadi konflik:

1. Jangan langsung menghapus kode anggota lain.
2. Periksa bagian yang conflict.
3. Diskusikan dengan anggota yang membuat kode tersebut.
4. Tentukan kode yang benar.
5. Selesaikan conflict.
6. Jalankan testing.
7. Commit kembali.

Contoh:

git pull origin develop

Jika terjadi konflik:

git status

Setelah konflik teratasi:

git add .
git commit -m "fix: resolve merge conflict"
git push
22. Struktur Repositori

Struktur awal repositori:

Administrasi-Guru/
│
├── frontend/
│
├── backend/
│
├── docs/
│   ├── 01-requirements.md
│   ├── 02-user-flow.md
│   ├── 03-database-erd.md
│   ├── 04-api-contract.md
│   └── 05-github-workflow.md
│
├── README.md
│
└── .gitignore
23. Alur Pengembangan Proyek
REQUIREMENT
     ↓
USER FLOW
     ↓
ERD
     ↓
UI/UX
     ↓
API CONTRACT
     ↓
GITHUB SETUP
     ↓
FRONT-END + BACK-END
     ↓
INTEGRATION
     ↓
TESTING
     ↓
BUG FIXING
     ↓
FINAL REVIEW
     ↓
DEPLOYMENT
24. Alur Kerja Tim
                 WAWAN
            Project Manager
                  │
        ┌─────────┴─────────┐
        ↓                   ↓
     GUNTUR              RAHMAT
   Front-End             Back-End
        │                   │
        ↓                   ↓
   Front-End UI          REST API
        │                   │
        └─────────┬─────────┘
                  ↓
             INTEGRATION
                  ↓
                TESTING
                  ↓
                DEPLOY
25. Target Akhir

Target akhir proyek adalah menghasilkan aplikasi Administrasi-Guru yang:

Memiliki akti dan peran
Memiliki pengelolaan data siswa
Memiliki pengelolaan materi
Memiliki bank soal
Memiliki sistem ujian online
Memiliki pemantauan waktu nyata
Memiliki pencatatan aktivitas anti-cheat
Memiliki absensi QR Code
Memiliki laporan
Memiliki desain responsif
Memiliki dokumen
Memiliki struktur GitHub yang diselenggarakan
26. Kesimpulan

GitHub digunakan sebagai pusat pengembangan dan kolaborasi proyek Administrasi-Guru.

Setiap anggota tim harus bekerja berdasarkan peran dan cabang masing-masing.

Alur utama:

Issue
  ↓
Task
  ↓
Feature Branch
  ↓
Coding
  ↓
Testing
  ↓
Commit
  ↓
Push
  ↓
Pull Request
  ↓
Review
  ↓
Merge ke develop
  ↓
Integration Testing
  ↓
Merge ke main
