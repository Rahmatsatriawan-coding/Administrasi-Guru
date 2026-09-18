# Database ERD Administrasi-Guru

## 1. Deskripsi

Database Administrasi-Guru digunakan untuk menyimpan dan mengelola
data pengguna, guru, siswa, kelas, mata pelajaran, materi, bank soal,
ujian, jawaban, absensi QR Code, pelanggaran ujian, dan aktivitas sistem.

Database menggunakan sistem relasional sehingga setiap data memiliki
hubungan yang jelas dan dapat digunakan oleh Front-End dan Back-End.

---

# 2. Role Pengguna

Sistem memiliki beberapa role:

- GURU
- SISWA
- ADMIN (opsional)

Role digunakan untuk menentukan hak akses pengguna terhadap sistem.

---

# 3. Struktur Database

Database terdiri dari tabel:

1. users
2. teachers
3. students
4. classes
5. subjects
6. materials
7. question_banks
8. questions
9. question_options
10. exams
11. exam_questions
12. exam_participants
13. exam_answers
14. attendance_sessions
15. attendance
16. exam_violations
17. activity_logs

---

# 4. Tabel Users

Menyimpan data akun yang digunakan untuk login.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| username | VARCHAR(100) | Username |
| password | VARCHAR(255) | Password yang sudah di-hash |
| role | ENUM | GURU/SISWA/ADMIN |
| is_active | BOOLEAN | Status akun |
| created_at | DATETIME | Waktu dibuat |
| updated_at | DATETIME | Waktu diperbarui |

Relasi:

- users → teachers
- users → students

---

# 5. Tabel Teachers

Menyimpan data guru.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| user_id | BIGINT | Foreign Key users.id |
| nip | VARCHAR(50) | Nomor identitas guru |
| name | VARCHAR(150) | Nama guru |
| email | VARCHAR(150) | Email |
| phone | VARCHAR(30) | Nomor telepon |
| created_at | DATETIME | Waktu dibuat |
| updated_at | DATETIME | Waktu diperbarui |

Relasi:

- teachers.user_id → users.id
- Satu guru dapat membuat banyak materi.
- Satu guru dapat membuat banyak bank soal.
- Satu guru dapat membuat banyak ujian.
- Satu guru dapat membuat banyak sesi absensi.

---

# 6. Tabel Students

Menyimpan data siswa.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| user_id | BIGINT | Foreign Key users.id |
| nis | VARCHAR(50) | Nomor induk siswa |
| nisn | VARCHAR(50) | NISN |
| name | VARCHAR(150) | Nama siswa |
| email | VARCHAR(150) | Email |
| class_id | BIGINT | Foreign Key classes.id |
| created_at | DATETIME | Waktu dibuat |
| updated_at | DATETIME | Waktu diperbarui |

Relasi:

- students.user_id → users.id
- students.class_id → classes.id
- Satu kelas memiliki banyak siswa.

---

# 7. Tabel Classes

Menyimpan data kelas.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| name | VARCHAR(100) | Nama kelas |
| grade | VARCHAR(20) | Tingkat kelas |
| academic_year | VARCHAR(20) | Tahun ajaran |
| created_at | DATETIME | Waktu dibuat |
| updated_at | DATETIME | Waktu diperbarui |

Relasi:

- classes → students
- classes → exams
- classes → attendance_sessions

---

# 8. Tabel Subjects

Menyimpan data mata pelajaran.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| name | VARCHAR(150) | Nama mata pelajaran |
| code | VARCHAR(50) | Kode mata pelajaran |
| created_at | DATETIME | Waktu dibuat |
| updated_at | DATETIME | Waktu diperbarui |

Relasi:

- subjects → materials
- subjects → exams
- subjects → attendance_sessions

---

# 9. Tabel Materials

Menyimpan data materi pembelajaran.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| teacher_id | BIGINT | Foreign Key teachers.id |
| subject_id | BIGINT | Foreign Key subjects.id |
| class_id | BIGINT | Foreign Key classes.id |
| title | VARCHAR(200) | Judul materi |
| description | TEXT | Deskripsi |
| file_name | VARCHAR(255) | Nama file |
| file_path | VARCHAR(500) | Lokasi file |
| file_type | VARCHAR(50) | Tipe file |
| created_at | DATETIME | Waktu dibuat |
| updated_at | DATETIME | Waktu diperbarui |

Relasi:

- teachers → materials
- subjects → materials
- classes → materials

---

# 10. Tabel Question Banks

Menyimpan kelompok bank soal.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| teacher_id | BIGINT | Foreign Key teachers.id |
| subject_id | BIGINT | Foreign Key subjects.id |
| title | VARCHAR(200) | Nama bank soal |
| description | TEXT | Deskripsi |
| created_at | DATETIME | Waktu dibuat |
| updated_at | DATETIME | Waktu diperbarui |

Relasi:

- teachers → question_banks
- subjects → question_banks
- question_banks → questions

---

# 11. Tabel Questions

Menyimpan pertanyaan.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| question_bank_id | BIGINT | Foreign Key question_banks.id |
| question_text | TEXT | Pertanyaan |
| question_type | ENUM | MULTIPLE_CHOICE/ESSAY |
| correct_option_id | BIGINT | Jawaban benar |
| score | DECIMAL | Bobot soal |
| created_at | DATETIME | Waktu dibuat |
| updated_at | DATETIME | Waktu diperbarui |

Relasi:

- question_banks → questions
- questions → question_options

---

# 12. Tabel Question Options

Menyimpan pilihan jawaban.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| question_id | BIGINT | Foreign Key questions.id |
| option_code | VARCHAR(5) | A/B/C/D |
| option_text | TEXT | Isi pilihan |
| created_at | DATETIME | Waktu dibuat |

Relasi:

- Satu question memiliki banyak question_options.

---

# 13. Tabel Exams

Menyimpan data ujian.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| teacher_id | BIGINT | Foreign Key teachers.id |
| subject_id | BIGINT | Foreign Key subjects.id |
| class_id | BIGINT | Foreign Key classes.id |
| title | VARCHAR(200) | Nama ujian |
| description | TEXT | Deskripsi |
| start_time | DATETIME | Waktu mulai |
| end_time | DATETIME | Waktu selesai |
| duration_minutes | INT | Durasi |
| status | ENUM | DRAFT/SCHEDULED/LIVE/FINISHED |
| created_at | DATETIME | Waktu dibuat |
| updated_at | DATETIME | Waktu diperbarui |

Relasi:

- teachers → exams
- subjects → exams
- classes → exams
- exams → exam_questions
- exams → exam_participants

---

# 14. Tabel Exam Questions

Menghubungkan ujian dengan soal.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| exam_id | BIGINT | Foreign Key exams.id |
| question_id | BIGINT | Foreign Key questions.id |
| question_order | INT | Urutan soal |
| score | DECIMAL | Bobot soal |

Relasi:

- exams → exam_questions
- questions → exam_questions

Tabel ini diperlukan karena satu ujian dapat memiliki banyak soal
dan satu soal dapat digunakan pada beberapa ujian.

---

# 15. Tabel Exam Participants

Menyimpan siswa yang mengikuti ujian.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| exam_id | BIGINT | Foreign Key exams.id |
| student_id | BIGINT | Foreign Key students.id |
| started_at | DATETIME | Waktu mulai |
| submitted_at | DATETIME | Waktu selesai |
| status | ENUM | NOT_STARTED/IN_PROGRESS/SUBMITTED |
| score | DECIMAL | Nilai |

Relasi:

- exams → exam_participants
- students → exam_participants
- exam_participants → exam_answers

---

# 16. Tabel Exam Answers

Menyimpan jawaban siswa.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| participant_id | BIGINT | Foreign Key exam_participants.id |
| question_id | BIGINT | Foreign Key questions.id |
| selected_option_id | BIGINT | Foreign Key question_options.id |
| answer_text | TEXT | Jawaban essay |
| is_correct | BOOLEAN | Status jawaban |
| score | DECIMAL | Nilai jawaban |
| answered_at | DATETIME | Waktu menjawab |

Relasi:

- exam_participants → exam_answers
- questions → exam_answers
- question_options → exam_answers

---

# 17. Tabel Attendance Sessions

Menyimpan sesi absensi yang dibuat guru.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| teacher_id | BIGINT | Foreign Key teachers.id |
| class_id | BIGINT | Foreign Key classes.id |
| subject_id | BIGINT | Foreign Key subjects.id |
| qr_token | VARCHAR(255) | Token QR |
| started_at | DATETIME | Waktu mulai |
| expired_at | DATETIME | Waktu QR kedaluwarsa |
| status | ENUM | ACTIVE/CLOSED |
| created_at | DATETIME | Waktu dibuat |

Relasi:

- teachers → attendance_sessions
- classes → attendance_sessions
- subjects → attendance_sessions
- attendance_sessions → attendance

---

# 18. Tabel Attendance

Menyimpan data hasil absensi siswa.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| session_id | BIGINT | Foreign Key attendance_sessions.id |
| student_id | BIGINT | Foreign Key students.id |
| scanned_at | DATETIME | Waktu scan |
| status | ENUM | HADIR/IZIN/SAKIT/ALPA |
| note | TEXT | Catatan |

Relasi:

- attendance_sessions → attendance
- students → attendance

Constraint:

Satu siswa hanya dapat melakukan absensi satu kali
pada satu sesi absensi.

---

# 19. Tabel Exam Violations

Menyimpan aktivitas mencurigakan selama ujian.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| exam_id | BIGINT | Foreign Key exams.id |
| student_id | BIGINT | Foreign Key students.id |
| violation_type | VARCHAR(100) | Jenis pelanggaran |
| description | TEXT | Detail aktivitas |
| occurred_at | DATETIME | Waktu kejadian |

Contoh violation_type:

- TAB_SWITCH
- FULLSCREEN_EXIT
- PAGE_LEAVE
- CONNECTION_LOST

---

# 20. Tabel Activity Logs

Menyimpan aktivitas pengguna di sistem.

| Field | Tipe | Keterangan |
|---|---|---|
| id | BIGINT | Primary Key |
| user_id | BIGINT | Foreign Key users.id |
| action | VARCHAR(100) | Jenis aktivitas |
| description | TEXT | Deskripsi |
| ip_address | VARCHAR(45) | IP pengguna |
| created_at | DATETIME | Waktu aktivitas |

---

# 21. ERD

```mermaid
erDiagram

    USERS ||--o| TEACHERS : has
    USERS ||--o| STUDENTS : has

    CLASSES ||--o{ STUDENTS : contains

    TEACHERS ||--o{ MATERIALS : creates
    SUBJECTS ||--o{ MATERIALS : has
    CLASSES ||--o{ MATERIALS : receives

    TEACHERS ||--o{ QUESTION_BANKS : creates
    SUBJECTS ||--o{ QUESTION_BANKS : contains

    QUESTION_BANKS ||--o{ QUESTIONS : contains
    QUESTIONS ||--o{ QUESTION_OPTIONS : has

    TEACHERS ||--o{ EXAMS : creates
    SUBJECTS ||--o{ EXAMS : uses
    CLASSES ||--o{ EXAMS : takes

    EXAMS ||--o{ EXAM_QUESTIONS : contains
    QUESTIONS ||--o{ EXAM_QUESTIONS : used_in

    EXAMS ||--o{ EXAM_PARTICIPANTS : has
    STUDENTS ||--o{ EXAM_PARTICIPANTS : joins

    EXAM_PARTICIPANTS ||--o{ EXAM_ANSWERS : gives
    QUESTIONS ||--o{ EXAM_ANSWERS : answered

    TEACHERS ||--o{ ATTENDANCE_SESSIONS : creates
    CLASSES ||--o{ ATTENDANCE_SESSIONS : has
    SUBJECTS ||--o{ ATTENDANCE_SESSIONS : for

    ATTENDANCE_SESSIONS ||--o{ ATTENDANCE : records
    STUDENTS ||--o{ ATTENDANCE : has

    EXAMS ||--o{ EXAM_VIOLATIONS : records
    STUDENTS ||--o{ EXAM_VIOLATIONS : commits

    USERS ||--o{ ACTIVITY_LOGS : performs
