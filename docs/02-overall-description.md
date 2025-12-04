# 2. Overall Description

## 2.1 Product Perspective

Platform **Nafas Bumi** merupakan sistem terintegrasi yang terdiri dari tiga komponen utama: aplikasi seluler untuk pengguna, aplikasi seluler untuk volunteer/driver, dan dashboard admin berbasis web. Seluruh komponen berbagi basis data dan layanan backend yang sama serta beroperasi di bawah satu organisasi.

Sistem ini menggantikan proses manual yang sebelumnya dilakukan melalui grup pesan instan dan spreadsheet, dengan menyediakan otomasi, pencatatan terpusat, serta pelacakan kontribusi dan dampak secara real-time.

Komponen sistem mencakup:

- **Frontend**: aplikasi seluler (pengguna & driver) dan dashboard admin web
- **Backend Services**: API, autentikasi, pemrosesan jadwal, validasi data
- **Database**: penyimpanan data transaksi, pengguna, kegiatan, dan laporan
- **Integrasi Eksternal**: Google Maps API untuk geolokasi & rute; Firebase Cloud Messaging untuk notifikasi

Sistem ini tidak dirancang sebagai multi-tenant; seluruh fitur ditujukan untuk satu organisasi pengelola saja.

## 2.2 User Classes and Characteristics

Terdapat beberapa kelas pengguna, masing-masing dengan kebutuhan dan perilaku khas:

### 1. **Pengguna Umum**

- Individu masyarakat yang menyetor sampah terpilah atau mengikuti kegiatan edukasi.
- Rentang usia dominan 18–45 tahun.
- Perlu antarmuka yang sederhana, jelas, dan mudah dipahami.
- Motivasi utama: kemudahan penyetoran sampah, penghargaan (Poin Bumi), dan akses edukasi.

### 2. **Volunteer / Driver**

- Petugas lapangan yang melakukan penjemputan sampah atau membantu kegiatan komunitas.
- Membutuhkan akses cepat ke daftar tugas, navigasi, dan input hasil penjemputan.
- Menggunakan perangkat mobile dalam kondisi yang bervariasi (lapangan, hujan, mobilitas tinggi).

### 3. **Administrator**

- Pengelola organisasi; mengatur jadwal, konten, mitra, dan laporan.
- Membutuhkan akses ke dashboard dengan tampilan data yang komprehensif dan dapat diandalkan.
- Menuntut efisiensi tinggi untuk mengurangi beban pekerjaan administratif.

### 4. **Mitra Daur Ulang / Sponsor** (akses terbatas atau read-only)

- Membutuhkan data ringkas mengenai pasokan sampah terpilah dan laporan dampak.
- Tidak menggunakan aplikasi secara penuh, namun memerlukan akses untuk melihat informasi tertentu.

## 2.3 Operating Environment

Lingkungan operasional sistem didasarkan pada Project Plan (halaman 10):

- **Platform Pengguna & Driver**:

  - Aplikasi seluler Android
  - Aplikasi seluler iOS

- **Platform Administrator**:

  - Dashboard web berbasis browser modern (Chrome, Edge, Safari)

- **Infrastruktur Sistem**:

  - Layanan backend berjalan di lingkungan cloud
  - Dukungan skalabilitas untuk peningkatan jumlah pengguna
  - Ketersediaan sistem yang memadai untuk operasional harian komunitas

- **Integrasi Eksternal**:
  - Google Maps API untuk geospasial & rute
  - Firebase Cloud Messaging untuk notifikasi push

## 2.4 Design and Implementation Constraints

Sistem harus mematuhi batasan berikut:

- **Regulasi Indonesia**  
  Mematuhi UU ITE, PP 71/2019, dan UU Perlindungan Data Pribadi untuk pengelolaan data pengguna dan transaksi elektronik.

- **Teknis**

  - Aplikasi mobile harus kompatibel dengan versi Android dan iOS yang masih umum digunakan.
  - Dashboard harus berjalan pada browser modern.
  - Integrasi hanya dilakukan pada API eksternal yang memiliki dukungan dokumentasi dan SLA jelas.

- **Organisasi**

  - Sistem dirancang untuk satu organisasi saja (single-organization architecture).
  - Perhitungan _Poin Bumi_ tidak ditetapkan dalam fase SRS (**TBD** oleh organisasi).

- **Lingkup Backend**
  - Perlu mendukung audit trail untuk perubahan penting.
  - Perlu mendukung pemrosesan jadwal dan rute tanpa ketergantungan pada pihak ketiga selain Google Maps.

## 2.5 Assumptions and Dependencies

### **Assumptions**

- Pengguna memiliki akses internet saat menggunakan aplikasi.
- Volunteer/driver memiliki perangkat mobile yang mendukung GPS.
- Organisasi menyediakan data rute, jadwal, dan konten edukasi secara berkala.
- Mekanisme perhitungan _Poin Bumi_ ditentukan kemudian dan akan disesuaikan pada fase desain.

### **Dependencies**

- Google Maps API untuk penentuan lokasi, rute, dan navigasi.
- Firebase Cloud Messaging untuk notifikasi.
- Infrastruktur cloud untuk menjalankan layanan backend dan database.
- Kebijakan organisasi terkait program reward dan klasifikasi sampah.
