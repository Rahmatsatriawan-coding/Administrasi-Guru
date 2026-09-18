# GitHub Issues & Milestone — Administrasi-Guru

## 1. Tujuan

Dokumen ini digunakan sebagai panduan pembagian pekerjaan, pembuatan GitHub Issues, Milestone, prioritas, dan tracking progress proyek Administrasi-Guru.

Tujuan utama:
- Membagi pekerjaan tim secara jelas.
- Menentukan penanggung jawab setiap pekerjaan.
- Mempermudah monitoring progress.
- Mengurangi pekerjaan yang tumpang tindih.
- Menjadi acuan sebelum Pull Request dibuat.

---

## 2. Struktur Tim

| Anggota | Role | Tanggung Jawab |
|---|---|---|
| Wawan | Project Manager | Project management, dokumentasi, koordinasi, GitHub, testing, integrasi |
| Guntur | Front-End Developer | UI/UX implementation dan Front-End |
| Rahmat | Back-End Developer | API, database, authentication dan Back-End |

---

# 3. Milestone

## Milestone 1 — Project Foundation

Target:
- Repository
- Branch
- Dokumentasi
- UI/UX
- Database
- API Contract

Issues:

### Issue 01 — Setup Repository
**Assignee:** Wawan  
**Label:** DOCS

Task:
- Membuat repository GitHub.
- Membuat branch `main`.
- Membuat branch `develop`.
- Menyiapkan branch tim.

---

### Issue 02 — Project Documentation
**Assignee:** Wawan  
**Label:** DOCS

Task:
- Requirements
- User Flow
- ERD
- API Contract
- GitHub Workflow
- GitHub Issues & Milestone

---

### Issue 03 — UI/UX Design
**Assignee:** Wawan + Guntur  
**Label:** UIUX

Task:
- Design System
- Login
- Dashboard
- Data Siswa
- Materi
- Bank Soal
- Ujian
- Absensi
- Laporan
- Profile
- Responsive Mobile

---

### Issue 04 — Database Design
**Assignee:** Rahmat  
**Label:** DATABASE

Task:
- Membuat database.
- Membuat tabel.
- Menentukan primary key.
- Menentukan foreign key.
- Membuat relasi antar tabel.
- Testing database.

---

### Issue 05 — API Contract
**Assignee:** Wawan + Rahmat  
**Label:** API

Task:
- Menentukan endpoint.
- Menentukan request.
- Menentukan response.
- Menentukan authentication.
- Menentukan HTTP status code.

---

# 4. Milestone 2 — Authentication & Master Data

## Issue 06 — Authentication Backend

**Assignee:** Rahmat  
**Label:** BE, FEATURE

Task:
- Login.
- Logout.
- JWT.
- Password hashing.
- Role validation.
- Authentication middleware.

Acceptance Criteria:
- User dapat login.
- Token berhasil dibuat.
- User tidak dapat mengakses halaman tanpa authentication.
- Role GURU dan SISWA dapat dibedakan.

---

## Issue 07 — Login Front-End

**Assignee:** Guntur  
**Label:** FE, FEATURE

Task:
- Membuat halaman login.
- Input username/email.
- Input password.
- Tombol login.
- Validasi form.
- Menampilkan pesan error.
- Integrasi API login.

---

## Issue 08 — Data Siswa Backend

**Assignee:** Rahmat  
**Label:** BE, FEATURE

Task:
- CRUD siswa.
- Import Excel/CSV.
- Validasi data.
- Template import.

Acceptance Criteria:
- Tambah siswa.
- Lihat siswa.
- Update siswa.
- Hapus siswa.
- Import siswa.

---

## Issue 09 — Data Siswa Front-End

**Assignee:** Guntur  
**Label:** FE, FEATURE

Task:
- Tabel siswa.
- Search.
- Filter.
- Tambah siswa.
- Edit siswa.
- Hapus siswa.
- Import siswa.
- Download template.

---

# 5. Milestone 3 — Materi, Bank Soal & Ujian

## Issue 10 — Materi Backend

**Assignee:** Rahmat  
**Label:** BE, FEATURE

Task:
- Upload materi.
- Edit materi.
- Hapus materi.
- List materi.
- Preview materi.
- Pengelompokan kelas/mata pelajaran.

---

## Issue 11 — Materi Front-End

**Assignee:** Guntur  
**Label:** FE, FEATURE

Task:
- Halaman materi.
- Upload.
- Edit.
- Delete.
- Search.
- Filter.
- Preview.

---

## Issue 12 — Bank Soal Backend

**Assignee:** Rahmat  
**Label:** BE, FEATURE

Task:
- CRUD bank soal.
- CRUD soal.
- Pilihan jawaban.
- Jawaban benar.
- Import soal.
- Validasi soal.

---

## Issue 13 — Bank Soal Front-End

**Assignee:** Guntur  
**Label:** FE, FEATURE

Task:
- List bank soal.
- Tambah soal.
- Edit soal.
- Hapus soal.
- Import soal.
- Preview soal.

---

## Issue 14 — Ujian Backend

**Assignee:** Rahmat  
**Label:** BE, FEATURE

Task:
- Membuat ujian.
- Menentukan jadwal.
- Menentukan durasi.
- Menentukan peserta.
- Memilih soal.
- Start exam.
- Submit exam.
- Menghitung nilai.
- Menyimpan jawaban.

Status:

DRAFT → SCHEDULED → LIVE → FINISHED

---

## Issue 15 — Ujian Front-End

**Assignee:** Guntur  
**Label:** FE, FEATURE

Task:
- Halaman daftar ujian.
- Detail ujian.
- Halaman pengerjaan.
- Timer.
- Navigasi soal.
- Submit ujian.
- Halaman hasil.

---

# 6. Milestone 4 — Absensi & Monitoring

## Issue 16 — QR Attendance Backend

**Assignee:** Rahmat  
**Label:** BE, FEATURE

Task:
- Membuat sesi absensi.
- Generate QR.
- Validasi QR.
- Validasi siswa.
- Validasi waktu.
- Mencegah absensi ganda.
- Menyimpan status HADIR.

---

## Issue 17 — QR Attendance Front-End

**Assignee:** Guntur  
**Label:** FE, FEATURE

Task:
- Halaman absensi guru.
- Generate QR.
- Scanner QR siswa.
- Status absensi.
- Pesan berhasil/gagal.

---

## Issue 18 — Attendance Recap

**Assignee:** Guntur + Rahmat  
**Label:** FE, BE, FEATURE

Task:
- Rekap harian.
- Rekap mingguan.
- Rekap bulanan.
- Rekap semester.
- Status HADIR.
- Status IZIN.
- Status SAKIT.
- Status ALPA.

---

## Issue 19 — Real-Time Monitoring

**Assignee:** Rahmat + Guntur  
**Label:** FE, BE, FEATURE

Task:
- WebSocket.
- Jumlah peserta.
- Status pengerjaan.
- Status selesai.
- Status belum mulai.
- Status koneksi.

---

## Issue 20 — Anti-Cheat

**Assignee:** Rahmat + Guntur  
**Label:** FE, BE, FEATURE

Event yang dicatat:
- TAB_SWITCH
- FULLSCREEN_EXIT
- PAGE_LEAVE
- CONNECTION_LOST

Catatan:

Fitur anti-cheat digunakan untuk mendeteksi dan mencatat aktivitas yang dapat mengindikasikan pelanggaran. Sistem tidak menjamin pencegahan kecurangan 100%.

---

# 7. Milestone 5 — Laporan & Finalisasi

## Issue 21 — Reports Backend

**Assignee:** Rahmat  
**Label:** BE, FEATURE

Task:
- Laporan absensi.
- Laporan siswa.
- Laporan ujian.
- Rekap nilai.
- Statistik.
- Export Excel.
- Export PDF.

---

## Issue 22 — Reports Front-End

**Assignee:** Guntur  
**Label:** FE, FEATURE

Task:
- Dashboard laporan.
- Filter laporan.
- Tabel laporan.
- Grafik.
- Export Excel.
- Export PDF.

---

## Issue 23 — Profile

**Assignee:** Guntur + Rahmat  
**Label:** FE, BE, FEATURE

Task:
- Menampilkan profile.
- Update profile.
- Update password.

---

## Issue 24 — Integration Testing

**Assignee:** Wawan + Guntur + Rahmat  
**Label:** TEST

Task:
- Testing Front-End.
- Testing Back-End.
- Testing API.
- Testing database.
- Testing authentication.
- Testing ujian.
- Testing absensi.
- Testing laporan.

---

## Issue 25 — Bug Fixing

**Assignee:** Semua anggota  
**Label:** BUG

Task:
- Mencatat bug.
- Menentukan penyebab.
- Memperbaiki bug.
- Testing ulang.

---

## Issue 26 — Final Documentation

**Assignee:** Wawan  
**Label:** DOCS

Task:
- Dokumentasi aplikasi.
- Dokumentasi instalasi.
- Dokumentasi penggunaan.
- Dokumentasi API.
- Dokumentasi database.
- Dokumentasi GitHub.
- Persiapan presentasi.

---

# 8. Labels

Gunakan label berikut:

| Label | Fungsi |
|---|---|
| FE | Front-End |
| BE | Back-End |
| DOCS | Dokumentasi |
| UIUX | UI/UX |
| DATABASE | Database |
| API | API |
| FEATURE | Fitur |
| BUG | Bug |
| TEST | Testing |

---

# 9. Prioritas

Gunakan prioritas berdasarkan kebutuhan pengembangan:

### P0 — Critical
Fitur yang harus tersedia agar aplikasi dapat berjalan.

Contoh:
- Authentication
- Database
- API
- Ujian
- Absensi

### P1 — High
Fitur utama yang diperlukan untuk MVP.

Contoh:
- Data Siswa
- Materi
- Bank Soal
- Laporan

### P2 — Medium
Fitur tambahan.

Contoh:
- Monitoring Real-Time
- Anti-Cheat
- Statistik

### P3 — Low
Fitur tambahan yang dapat dikerjakan setelah fitur utama selesai.

---

# 10. Definition of Done

Sebuah Issue dianggap selesai apabila:

- [ ] Coding selesai.
- [ ] Tidak ada error utama.
- [ ] Sudah dilakukan testing.
- [ ] API sudah terintegrasi jika diperlukan.
- [ ] UI sudah sesuai desain.
- [ ] Tidak merusak fitur lain.
- [ ] Commit sudah dibuat.
- [ ] Pull Request sudah dibuat.
- [ ] Sudah direview.
- [ ] Sudah di-merge ke `develop`.

---

# 11. Workflow Issue

```text
OPEN
  ↓
IN PROGRESS
  ↓
TESTING
  ↓
PULL REQUEST
  ↓
CODE REVIEW
  ↓
MERGED
  ↓
DONE
```

---

# 12. Aturan Penamaan Issue

Gunakan format:

```text
[FE] Nama fitur
[BE] Nama fitur
[DOCS] Nama dokumentasi
[UIUX] Nama desain
[TEST] Nama testing
[BUG] Deskripsi bug
```

Contoh:

```text
[FE] Membuat halaman Data Siswa
[BE] Membuat API Data Siswa
[BE] Membuat Authentication
[UIUX] Membuat Design Dashboard
[TEST] Testing Login
[BUG] Login gagal setelah refresh
```

---

# 13. Tanggung Jawab Project Manager

Wawan bertanggung jawab untuk:

- Membuat Issues.
- Membuat Milestone.
- Membagi tugas.
- Memantau progress.
- Mengatur prioritas.
- Memastikan FE dan BE terkoordinasi.
- Review Pull Request.
- Memantau integrasi.
- Mengatur testing.
- Menyiapkan dokumentasi.
- Menyiapkan laporan akhir.
- Menyiapkan presentasi.

---

# 14. Target Akhir

Target akhir proyek:

```text
Requirements
     ↓
UI/UX
     ↓
Database
     ↓
API
     ↓
Front-End + Back-End
     ↓
Integration
     ↓
Testing
     ↓
Bug Fixing
     ↓
Documentation
     ↓
Deployment
     ↓
Final Presentation
```

---

# 15. Kesimpulan

GitHub Issues dan Milestone digunakan untuk memastikan seluruh pekerjaan Administrasi-Guru dapat dibagi, dikerjakan, dipantau, diuji, dan diselesaikan secara terstruktur.

Setiap anggota wajib mengerjakan Issue sesuai tugasnya dan menggunakan workflow GitHub yang telah ditentukan.
