# 3. System Features

Dokumen ini merinci kebutuhan fungsional berdasarkan backlog resmi, disusun per Feature tanpa pengelompokan per-Epic.  
Setiap Feature memiliki uraian, user story terkait, dan daftar Functional Requirements (FR) yang diturunkan dari kebutuhan pengguna.

---

## 3.1 Feature: Penjadwalan dan Penugasan Layanan Reguler

### 3.1.1 Description

Sistem menyediakan mekanisme untuk mengatur jadwal layanan pengumpulan sampah reguler secara repetitif dan mengalokasikan driver sesuai kebutuhan.

### 3.1.2 Related User Stories

- US60 — Admin mengatur jadwal repetitif layanan reguler.
- US61 — Admin menyesuaikan jadwal repetitif apabila terjadi situasi tertentu.

### 3.1.3 Functional Requirements

- **FR-F59-1** Sistem harus memungkinkan admin membuat jadwal pengumpulan reguler secara repetitif.
- **FR-F59-2** Sistem harus menyediakan opsi konfigurasi frekuensi (harian, mingguan, bulanan).
- **FR-F59-3** Sistem harus memungkinkan admin mengubah jadwal reguler yang sudah dibuat.
- **FR-F59-4** Sistem harus memperbarui jadwal ke seluruh driver yang terkait.
- **FR-F59-5** Sistem harus memberikan notifikasi perubahan jadwal kepada driver dan kontributor.

---

## 3.2 Feature: Pencatatan Setoran Layanan Reguler

### 3.2.1 Description

Fitur pencatatan setoran yang dilakukan driver setelah menerima sampah dari kontributor atau masyarakat umum.

### 3.2.2 Related User Stories

- US63 — Driver memvalidasi jenis dan volume sampah.
- US64 — Driver mencatat jenis dan volume sampah.
- US65 — Kontributor menerima konfirmasi setoran.
- US66 — Admin memvalidasi data setoran sampah.

### 3.2.3 Functional Requirements

- **FR-F62-1** Sistem harus menyediakan formulir input bagi driver untuk mencatat jenis dan volume sampah.
- **FR-F62-2** Sistem harus memungkinkan driver melakukan validasi setoran sebelum pengiriman data.
- **FR-F62-3** Sistem harus mengirim konfirmasi digital kepada kontributor setelah driver mencatat data.
- **FR-F62-4** Sistem harus memungkinkan admin meninjau dan memvalidasi data setoran.
- **FR-F62-5** Sistem harus menyimpan riwayat setoran untuk keperluan audit dan laporan.

---

## 3.3 Feature: Permintaan Layanan Khusus

### 3.3.1 Description

Fitur yang memungkinkan kontributor mengajukan penjemputan sampah khusus di luar jadwal reguler dengan informasi lokasi, waktu, jenis sampah, foto, dan deskripsi.

### 3.3.2 Related User Stories

- US24 — Kontributor mengajukan permintaan penjemputan khusus.
- US25 — Admin mengelola permintaan penjemputan yang masuk.

### 3.3.3 Functional Requirements

- **FR-F11-1** Sistem harus menyediakan formulir pengajuan layanan khusus.
- **FR-F11-2** Sistem harus mendukung upload foto dan deskripsi.
- **FR-F11-3** Sistem harus mengirim notifikasi ke admin setiap ada permintaan baru.
- **FR-F11-4** Sistem harus memungkinkan admin menerima atau menolak permintaan.
- **FR-F11-5** Sistem harus menampilkan status permintaan kepada kontributor secara real-time.

---

## 3.4 Feature: Penjadwalan & Penugasan Layanan Khusus

### 3.4.1 Description

Sistem mendukung otomatisasi pembagian tugas kepada driver dan memungkinkan admin melakukan penyesuaian manual bila diperlukan.

### 3.4.2 Related User Stories

- US28 — Sistem otomatis membagi tugas ke driver.
- US31 — Admin menyesuaikan jadwal dan penugasan manual.
- US30 — Driver menerima jadwal penjemputan dengan jelas.

### 3.4.3 Functional Requirements

- **FR-F13-1** Sistem harus memiliki mekanisme auto-assignment berdasarkan kapasitas dan lokasi driver.
- **FR-F13-2** Sistem harus memungkinkan admin menyesuaikan penugasan secara manual.
- **FR-F13-3** Sistem harus menampilkan daftar tugas kepada driver secara jelas.
- **FR-F13-4** Sistem harus memperbarui status tugas secara real-time.
- **FR-F13-5** Sistem harus memberikan notifikasi tugas baru kepada driver.

---

## 3.5 Feature: Pencatatan Setoran Layanan Khusus

### 3.5.1 Description

Proses pencatatan dan validasi sampah yang diserahkan dalam layanan penjemputan khusus.

### 3.5.2 Related User Stories

- US67 — Driver memvalidasi sampah.
- US33 — Driver mencatat sampah.
- US34 — Kontributor menerima konfirmasi.
- US35 — Admin memvalidasi data setoran.

### 3.5.3 Functional Requirements

- **FR-F14-1** Sistem harus memungkinkan driver mencatat dan memvalidasi data setoran layanan khusus.
- **FR-F14-2** Sistem harus mengirim konfirmasi digital kepada kontributor.
- **FR-F14-3** Sistem harus menyediakan antarmuka validasi bagi admin.
- **FR-F14-4** Sistem harus menyimpan catatan setoran untuk pelaporan kontribusi.

---

## 3.6 Feature: Inisiasi & Manajemen Kemitraan

### 3.6.1 Description

Kemampuan sistem untuk mengelola pendaftaran, persetujuan, dan pemantauan kemitraan.

### 3.6.2 Related User Stories

- US37 — Mitra mendaftarkan kerja sama.
- US38 — Admin menyetujui pengajuan mitra.
- US39 — Admin memantau status kemitraan.

### 3.6.3 Functional Requirements

- **FR-F16-1** Sistem harus menyediakan formulir pendaftaran mitra.
- **FR-F16-2** Sistem harus memungkinkan admin meninjau dan menyetujui pengajuan.
- **FR-F16-3** Sistem harus menyimpan status dan riwayat kemitraan.
- **FR-F16-4** Sistem harus menyediakan tampilan monitoring status kemitraan.

---

## 3.7 Feature: Pemantauan Kegiatan Workshop

### 3.7.1 Description

Manajemen workshop termasuk publikasi jadwal, pendaftaran peserta, dan monitoring.

### 3.7.2 Related User Stories

- US47 — Admin mempublikasi jadwal workshop.
- US48 — User melihat dan mendaftar workshop.
- US50 — Mitra memantau peserta.

### 3.7.3 Functional Requirements

- **FR-F20-1** Sistem harus memungkinkan admin membuat dan mempublikasi workshop.
- **FR-F20-2** Sistem harus menampilkan daftar workshop kepada user.
- **FR-F20-3** Sistem harus memungkinkan user mendaftar workshop.
- **FR-F20-4** Sistem harus menampilkan jumlah peserta kepada mitra.
- **FR-F20-5** Sistem harus menyimpan riwayat kegiatan workshop.

---

## 3.8 Feature: Fasilitas Pengumpulan di Lokasi Mitra

### 3.8.1 Description

Manajemen titik pengumpulan sampah di lokasi mitra dan pemantauan jadwal penjemputan.

### 3.8.2 Related User Stories

- US41 — Mitra mengajukan fasilitas pengumpulan.
- US43 — Mitra mengetahui status penjemputan.
- US45 — Admin memantau titik pengumpulan mitra.

### 3.8.3 Functional Requirements

- **FR-F19-1** Sistem harus menyediakan formulir pengajuan titik pengumpulan.
- **FR-F19-2** Sistem harus menyediakan status real-time penjemputan sampah mitra.
- **FR-F19-3** Sistem harus memungkinkan admin memantau titik pengumpulan.
- **FR-F19-4** Sistem harus mencatat aktivitas penjemputan di lokasi mitra.

---

## 3.9 Feature: Pusat Pengetahuan Daring

### 3.9.1 Description

Sistem menyediakan konten edukasi berupa artikel, modul, atau media lain.

### 3.9.2 Related User Stories

- US52 — User mengakses konten edukasi.
- US54 — Admin mengunggah dan memperbarui konten.

### 3.9.3 Functional Requirements

- **FR-F22-1** Sistem harus menampilkan daftar konten edukasi daring.
- **FR-F22-2** Sistem harus memungkinkan admin mengunggah konten.
- **FR-F22-3** Sistem harus memungkinkan admin memperbarui konten.
- **FR-F22-4** Sistem harus menyimpan riwayat versi konten.

---

## 3.10 Feature: Pengelolaan Sistem Poin

### 3.10.1 Description

Pengelolaan mekanisme pemberian dan akumulasi poin atas kontribusi.

### 3.10.2 Related User Stories

- US40 — Kontributor mendapatkan poin.
- US42 — Kontributor melihat akumulasi poin.
- US44 — Admin mengatur tata cara pemberian poin.

### 3.10.3 Functional Requirements

- **FR-F17-1** Sistem harus mencatat poin berdasarkan aktivitas kontribusi.
- **FR-F17-2** Sistem harus menampilkan total poin kepada kontributor.
- **FR-F17-3** Sistem harus menyediakan konfigurasi aturan poin (TBD oleh organisasi).
- **FR-F17-4** Sistem harus menyimpan riwayat pemberian poin.

---

## 3.11 Feature: Pengakuan & Peringkat

### 3.11.1 Description

Fitur yang menyediakan papan peringkat kontribusi komunitas.

### 3.11.2 Related User Stories

- US46 — Kontributor melihat peringkat kontribusi.

### 3.11.3 Functional Requirements

- **FR-F18-1** Sistem harus menampilkan peringkat kontribusi semua kontributor.
- **FR-F18-2** Sistem harus memperbarui peringkat secara periodik atau real-time.
- **FR-F18-3** Sistem harus mendukung filter atau kategori kontribusi.

---

## 3.12 Feature: Interaksi & Notifikasi Personal

### 3.12.1 Description

Fitur pengingat, ucapan terima kasih, dan notifikasi personal.

### 3.12.2 Related User Stories

- US53 — Pengingat penjemputan.
- US55 — Ucapan terima kasih personal.

### 3.12.3 Functional Requirements

- **FR-F21-1** Sistem harus mengirim pengingat penjemputan kepada kontributor.
- **FR-F21-2** Sistem harus mengirim ucapan terima kasih setelah aktivitas kontribusi.
- **FR-F21-3** Sistem harus memiliki log notifikasi yang dapat diaudit.

---

## 3.13 Feature: Profil Kontribusi Individu

### 3.13.1 Description

Ringkasan dampak, riwayat kontribusi, dan kemampuan berbagi profil.

### 3.13.2 Related User Stories

- US56 — Riwayat kontribusi pribadi.
- US57 — Membagikan profil kontribusi.
- US58 — Melihat profil kontributor lain.

### 3.13.3 Functional Requirements

- **FR-F23-1** Sistem harus menampilkan riwayat kontribusi pengguna.
- **FR-F23-2** Sistem harus memungkinkan pengguna membagikan profil kontribusi.
- **FR-F23-3** Sistem harus menampilkan profil kontribusi kontributor lain.
- **FR-F23-4** Sistem harus melindungi privasi pengguna sesuai regulasi.

---

## 3.14 Feature: Analitik Operasional

### 3.14.1 Description

Visualisasi dan rangkuman data operasional untuk pemantauan internal.

### 3.14.2 Related User Stories

- US26 — Admin memantau data pengelolaan sampah.
- US27 — Admin melihat tingkat partisipasi reguler & khusus.
- US29 — Admin melihat tingkat partisipasi kegiatan eventual.

### 3.14.3 Functional Requirements

- **FR-F12-1** Sistem harus menyediakan dashboard operasional.
- **FR-F12-2** Sistem harus menampilkan grafik partisipasi kontributor.
- **FR-F12-3** Sistem harus menyediakan analitik kegiatan workshop.
- **FR-F12-4** Sistem harus mengarsipkan data analitik untuk riwayat historis.

---

## 3.15 Feature: Distribusi dan Ekspor Data

### 3.15.1 Description

Kemampuan ekspor data ke format PDF atau CSV.

### 3.15.2 Related User Stories

- US32 — Admin mengekspor laporan data.

### 3.15.3 Functional Requirements

- **FR-F15-1** Sistem harus mengekspor laporan ke format PDF.
- **FR-F15-2** Sistem harus mengekspor laporan ke format CSV.
- **FR-F15-3** Sistem harus menyediakan opsi periode laporan.
- **FR-F15-4** Sistem harus mencatat riwayat ekspor laporan.

---

## 3.16 Feature: Autentikasi Pengguna

### 3.16.1 Description

Identifikasi pengguna dan pembaruan kredensial.

### 3.16.2 Related User Stories

- US71 — Pengguna dikenali sistem (login).
- US72 — Pengguna menghapus sesi (logout).
- US75 — Pengguna memperbarui kredensial.

### 3.16.3 Functional Requirements

- **FR-F69-1** Sistem harus memungkinkan login menggunakan kredensial valid.
- **FR-F69-2** Sistem harus mendukung mekanisme logout.
- **FR-F69-3** Sistem harus menyediakan fitur pembaruan kredensial.
- **FR-F69-4** Sistem harus menjaga keamanan sesi pengguna.

---

## 3.17 Feature: Autorisasi Pengguna

### 3.17.1 Description

Pengaturan kewenangan pengguna sesuai peran.

### 3.17.2 Related User Stories

- US73 — Pengguna diberikan otoritas sesuai peran.
- US74 — Admin mengatur otoritas pengguna.

### 3.17.3 Functional Requirements

- **FR-F70-1** Sistem harus menetapkan akses berdasarkan peran pengguna.
- **FR-F70-2** Sistem harus memungkinkan admin mengelola otorisasi setiap pengguna.
- **FR-F70-3** Sistem harus memberikan akses hanya kepada pengguna yang berhak.
- **FR-F70-4** Sistem harus menyediakan audit trail perubahan otorisasi.
