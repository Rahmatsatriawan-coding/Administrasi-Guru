# Administrasi-Guru

1. Deskripsi Sistem

Administrasi-Guru adalah aplikasi berbasis web yang membantu guru
mengelola administrasi pembelajaran, data siswa, materi, soal,
ujian, absensi, dan laporan secara terintegrasi.

2. Tujuan Sistem

Sistem dibuat untuk:

1. Mempermudah guru mengelola data siswa.
2. Mempermudah guru mengelola dan membagikan materi.
3. Mempermudah pembuatan dan pengelolaan soal.
4. Menyelenggarakan ujian secara online.
5. Memantau ujian secara real-time.
6. Mendeteksi aktivitas mencurigakan selama ujian.
7. Mengelola absensi siswa.
8. Membuat laporan administrasi secara otomatis.

3. Role Pengguna

GURU
Guru dapat:

- Login ke sistem.
- Mengelola data siswa.
- Mengimpor data siswa dari Excel/CSV.
- Mengelola materi.
- Melihat preview materi.
- Mengelola bank soal.
- Mengimpor soal menggunakan template.
- Membuat dan mengatur ujian.
- Memantau ujian secara real-time.
- Melihat aktivitas mencurigakan.
- Mengelola absensi.
- Melihat dan mengunduh laporan.

SISWA
Siswa dapat:

- Login.
- Melihat materi.
- Mengikuti ujian.
- Mengirim jawaban.
- Melihat status ujian.
- Melihat riwayat/nilai sesuai aturan sistem.
- Melakukan absensi.

 4. Fitur Utama
 4.1 Authentication

- Login guru.
- Login siswa.
- Logout.
- Role-based access.
- Validasi username/password.

 4.2 Data Siswa

- Menampilkan daftar siswa.
- Menambah siswa.
- Mengubah data siswa.
- Menghapus siswa.
- Import siswa dari Excel/CSV.
- Validasi data hasil import.
- Download template import.

4.3 Materi

- Upload materi.
- Edit materi.
- Hapus materi.
- Daftar materi.
- Preview materi tanpa harus mengunduh.
- Pengelompokan materi berdasarkan kelas/mata pelajaran.

 4.4 Bank Soal

- Membuat bank soal.
- Menambah soal.
- Mengubah soal.
- Menghapus soal.
- Import soal menggunakan template.
- Validasi soal hasil import.
- Menentukan jawaban benar.

4.5 Ujian

- Membuat ujian.
- Menentukan waktu ujian.
- Menentukan durasi.
- Menentukan kelas peserta.
- Memilih soal.
- Membuka ujian.
- Menutup ujian.
- Mengirim jawaban.
- Menghitung nilai.

4.6 Monitoring Real-Time

Guru dapat melihat:

- Jumlah siswa yang mengikuti ujian.
- Siswa yang sedang mengerjakan.
- Siswa yang sudah selesai.
- Status koneksi siswa.
- Waktu pengerjaan.

4.7 Anti-Cheat

Sistem mencatat aktivitas mencurigakan seperti:

- Keluar dari halaman ujian.
- Keluar dari fullscreen.
- Berpindah tab.
- Kehilangan koneksi.
- Aktivitas lain yang dapat dideteksi oleh browser.

Catatan:
Fitur anti-cheat berfungsi sebagai mekanisme deteksi dan mitigasi,
bukan jaminan bahwa kecurangan dapat dicegah 100%.

4.8 Absensi Online Berbasis QR Code

Sistem menyediakan fitur absensi online menggunakan QR Code
yang dibuat oleh guru dan dipindai oleh siswa melalui perangkat
masing-masing.

Guru dapat:

- Membuat sesi absensi.
- Memilih kelas.
- Memilih mata pelajaran.
- Menentukan tanggal dan waktu absensi.
- Generate QR Code absensi.
- Menentukan masa berlaku QR Code.
- Melihat siswa yang sudah melakukan absensi secara real-time.
- Menutup sesi absensi.
- Melihat dan mengubah status absensi secara manual.
- Melihat rekap kehadiran.

Siswa dapat:

- Melihat sesi absensi yang tersedia.
- Membuka fitur scan QR Code.
- Memindai QR Code menggunakan kamera perangkat.
- Mendapatkan notifikasi bahwa absensi berhasil atau gagal.
- Melihat status absensi yang telah dilakukan.

Validasi Absensi

Sistem melakukan validasi sebelum menyimpan absensi:

1. QR Code masih aktif.
2. QR Code sesuai dengan sesi absensi.
3. Siswa terdaftar pada kelas yang dipilih.
4. Siswa belum melakukan absensi pada sesi tersebut.
5. Waktu absensi masih berada dalam periode yang ditentukan.

Jika seluruh validasi berhasil, sistem mencatat absensi siswa.

Status Absensi

Status absensi terdiri dari:

- Hadir
- Izin
- Sakit
- Alpa

Data Absensi

Sistem mencatat:

- ID siswa.
- Nama siswa.
- Kelas.
- Mata pelajaran.
- Tanggal.
- Waktu scan.
- Sesi absensi.
- Status absensi.
   
 9. Output Sistem
Sistem menghasilkan:

- Data siswa.
- Data materi.
- Bank soal.
- Data ujian.
- Hasil ujian.
- Sesi absensi QR Code.
- Rekap absensi siswa.
- Riwayat waktu scan absensi.
- Laporan absensi.
- Laporan ujian.
- Rekap nilai.
- Grafik statistik.
- File laporan Excel.
- File laporan PDF.
