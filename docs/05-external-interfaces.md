# 5. External Interface Requirements

Bab ini mendefinisikan seluruh antarmuka eksternal yang digunakan oleh sistem Nafas Bumi, meliputi antarmuka pengguna, antarmuka perangkat lunak, perangkat keras, dan antarmuka komunikasi. Tujuan utama bagian ini adalah memastikan interoperabilitas, kejelasan integrasi, serta pengalaman pengguna yang konsisten.

---

## 5.1 User Interfaces

### 5.1.1 Aplikasi Seluler Pengguna (Kontributor / User)

Antarmuka aplikasi seluler dirancang dengan fokus pada kemudahan penggunaan dan efisiensi interaksi, sesuai dengan karakteristik pengguna masyarakat umum.

**Komponen UI utama:**
- Halaman registrasi dan login
- Beranda (ringkasan jadwal, dan poin)
- Formulir permintaan penjemputan (reguler & khusus)
- Riwayat kontribusi dan profil pengguna
- Profil kontribusi dengan kemampuan sharing
- Pengaturan privasi profil
- Lihat profil kontributor lain
- Kalender dan pendaftaran workshop
- Pusat pengetahuan daring
- Halaman poin, peringkat (dengan filter periode), dan pengakuan
- Notifikasi dan pesan sistem

**Kriteria UI:**
- Navigasi sederhana dan konsisten
- Mendukung penggunaan satu tangan
- Waktu penyelesaian penjadwalan < 1 menit
- Bahasa Indonesia sebagai bahasa utama

---

### 5.1.2 Aplikasi Seluler Volunteer / Driver

Antarmuka driver difokuskan pada kejelasan tugas lapangan dan minim interaksi kompleks.

**Komponen UI utama:**
- Login dan autentikasi
- Daftar tugas penjemputan
- Detail tugas (lokasi, waktu, jenis sampah)
- Navigasi peta
- Form pencatatan dan validasi setoran
- Konfirmasi digital ke kontributor
- Status tugas dan riwayat

**Kriteria UI:**
- Informasi ditampilkan secara ringkas
- Dukungan penggunaan di kondisi lapangan
- Navigasi peta mudah diakses
- Minim input manual yang berulang

---

### 5.1.3 Dashboard Admin (Web-Based)

Dashboard admin menyediakan antarmuka terpusat untuk pengelolaan seluruh operasional sistem.

**Komponen UI utama:**
- Manajemen pengguna dan otorisasi
- Manajemen jadwal dan penugasan
- Manajemen permintaan layanan
- Validasi data setoran sampah
- Manajemen mitra dan fasilitas
- View monitoring untuk mitra (peserta workshop, status penjemputan)
- Manajemen dan publikasi workshop
- Konfigurasi aturan sistem poin
- Manajemen konten edukasi
- Dashboard analitik dan laporan
- Ekspor data dan audit log

**Kriteria UI:**
- Berbasis web dan responsif
- Mendukung tampilan tabel dan grafik
- Akses berbasis role
- Optimal untuk penggunaan desktop/laptop

---

## 5.2 Software Interfaces

### 5.2.1 Backend API

Sistem backend menyediakan API untuk mendukung seluruh interaksi aplikasi seluler dan dashboard.

**Karakteristik API:**
- Arsitektur RESTful
- Format data JSON
- Endpoint terpisah berdasarkan domain (user, pickup, points, analytics, dsb.)
- Autentikasi berbasis token

**Contoh kelompok endpoint:**

#### Autentikasi & Manajemen Sesi
- `/auth/login` — login pengguna
- `/auth/logout` — logout pengguna
- `/auth/sessions` — manajemen sesi aktif
- `/auth/credentials` — update kredensial pengguna

#### Manajemen Pengguna
- `/users/*` — CRUD pengguna
- `/users/:id/role` — update role pengguna

#### Profil Kontribusi
- `/profiles/:id` — detail profil kontribusi
- `/profiles/:id/share` — generate token untuk sharing profil
- `/profiles/:id/privacy` — pengaturan privasi profil

#### Layanan Pengumpulan
- `/pickup/*` — permintaan & jadwal penjemputan
- `/waste-records/*` — pencatatan setoran
- `/waste-records/validate` — validasi setoran oleh admin

#### Sistem Poin & Gamifikasi
- `/points/transactions` — riwayat transaksi poin
- `/points/rules` — CRUD aturan pemberian poin
- `/leaderboard` — peringkat (query params: `period=monthly|total`)

#### Kemitraan & Fasilitas
- `/partners/*` — manajemen mitra
- `/partners/:id/facilities` — fasilitas pengumpulan mitra
- `/partners/:id/facilities/:facilityId/status` — status penjemputan di fasilitas

#### Workshop & Edukasi
- `/workshops/*` — CRUD workshop
- `/workshops/:id/participants` — daftar peserta (untuk monitoring mitra)

#### Analitik & Pelaporan
- `/reports/*` — laporan & ekspor

---

### 5.2.2 Integrasi Layanan Pihak Ketiga

#### a. Layanan Peta & Geospasial

**Layanan:** Google Maps API atau alternatif (OpenStreetMap, Mapbox)

Digunakan untuk:
- Penentuan lokasi penjemputan
- Perencanaan rute driver
- Visualisasi titik pengumpulan mitra

Data yang dipertukarkan:
- Koordinat lokasi (latitude, longitude)
- Estimasi jarak dan waktu tempuh
- Data routing dan navigasi

#### b. Layanan Notifikasi Push

**Layanan:** Firebase Cloud Messaging (FCM) untuk Android, Apple Push Notification Service (APNs) untuk iOS

Digunakan untuk:
- Pengingat penjemputan
- Pemberitahuan perubahan jadwal
- Ucapan terima kasih dan pesan sistem
- Notifikasi real-time untuk driver dan kontributor

Data yang dipertukarkan:
- ID pengguna / device token
- Isi pesan
- Tipe notifikasi
- Metadata terkait (timestamp, priority)

---

## 5.3 Hardware Interfaces

Sistem tidak bergantung pada perangkat keras khusus, namun memiliki kebutuhan minimum sebagai berikut:

### 5.3.1 Perangkat Pengguna & Driver
- Smartphone Android atau iOS
- GPS aktif untuk fitur lokasi
- Koneksi internet seluler atau Wi-Fi

### 5.3.2 Perangkat Administrator
- Laptop atau PC
- Browser modern (Chrome, Edge, Firefox, Safari)
- Koneksi internet stabil

Tidak ada integrasi dengan perangkat IoT, sensor fisik, atau mesin khusus dalam lingkup sistem saat ini.

---

## 5.4 Communications Interfaces

### 5.4.1 Protokol Komunikasi
- HTTPS untuk seluruh komunikasi data
- TLS untuk enkripsi data dalam transmisi

### 5.4.2 Jaringan
- Akses melalui internet publik
- Tidak memerlukan VPN khusus untuk pengguna umum
- Akses administratif dapat dibatasi berdasarkan kebijakan organisasi

### 5.4.3 Keamanan Komunikasi
- Semua request API harus diautentikasi
- Token akses harus memiliki masa berlaku
- Proteksi terhadap request tidak sah dan replay attack
- Logging komunikasi penting untuk audit dan monitoring

---

