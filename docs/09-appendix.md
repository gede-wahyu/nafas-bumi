# Appendix A: Glossary

Bagian ini mendefinisikan istilah, singkatan, dan konsep penting yang digunakan dalam dokumen SRS untuk menghindari ambiguitas pemahaman.

| Term | Definition |
|------|------------|
| Nafas Bumi | Platform digital untuk pengelolaan sampah berkelanjutan dan aktivitas komunitas lingkungan. |
| User | Pengguna umum aplikasi yang berpartisipasi dalam kegiatan komunitas dan pengelolaan sampah. |
| Kontributor | User yang secara aktif menyetor sampah atau mengikuti kegiatan kontribusi lingkungan. |
| Volunteer | Anggota komunitas yang membantu operasional non-komersial. |
| Driver | Pengguna yang bertugas melakukan penjemputan sampah dan pencatatan setoran di lapangan. |
| Administrator (Admin) | Pengelola sistem yang mengatur pengguna, jadwal, konten, dan laporan melalui dashboard web. |
| Mitra | Pihak eksternal (perusahaan, sekolah, komunitas) yang bekerja sama dengan Nafas Bumi. |
| Layanan Reguler | Layanan penjemputan sampah yang dijadwalkan secara berkala dan repetitif. |
| Layanan Khusus | Layanan penjemputan sampah berdasarkan permintaan ad-hoc dari kontributor. |
| Poin Bumi | Sistem penghargaan berbasis poin atas kontribusi pengguna dalam kegiatan lingkungan. |
| Feature | Kapabilitas sistem yang memberikan nilai bisnis atau operasional tertentu. |
| User Story | Pernyataan kebutuhan dari sudut pandang pengguna dengan format “Sebagai…, saya ingin…”. |
| Functional Requirement (FR) | Kebutuhan fungsional sistem yang dinyatakan secara eksplisit dan dapat diuji. |
| Non-Functional Requirement (NFR) | Kebutuhan kualitas sistem seperti kinerja, keamanan, dan keandalan. |
| Audit Log | Catatan aktivitas sistem yang digunakan untuk keperluan pengawasan dan investigasi. |
| Analytics Snapshot | Ringkasan data operasional pada periode tertentu. |
| Localization (L10N) | Penyesuaian sistem terhadap bahasa dan konteks lokal. |
| Internationalization (I18N) | Desain sistem agar mudah diadaptasi ke bahasa dan wilayah lain. |

---

# Appendix B: Analysis Models

Appendix ini menyajikan model analisis yang digunakan sebagai dasar penyusunan kebutuhan sistem.

---

## B.1 Stakeholder–System Interaction Overview

### **Aktor Utama**
- Kontributor / User
- Driver
- Administrator
- Mitra

### **Interaksi Utama**
- Kontributor mengajukan permintaan layanan, melihat kontribusi, dan menerima poin.
- Driver menerima tugas, mencatat setoran, dan memperbarui status penjemputan.
- Administrator mengelola jadwal, pengguna, kemitraan, dan laporan.
- Mitra memantau aktivitas kemitraan dan kegiatan terkait.

---

## B.2 High-Level Use Case List

| Use Case | Actor |
|--------|-------|
| Registrasi & Login | User, Driver, Admin |
| Penjadwalan Layanan Reguler | Admin |
| Permintaan Layanan Khusus | Kontributor |
| Penugasan Driver | Admin |
| Penjemputan & Pencatatan Sampah | Driver |
| Validasi Setoran | Admin |
| Manajemen Kemitraan | Admin, Mitra |
| Pendaftaran Workshop | User |
| Manajemen Konten Edukasi | Admin |
| Pengelolaan Poin & Peringkat | Admin |
| Analitik & Pelaporan | Admin |
| Ekspor Data | Admin |

---

## B.3 Logical Data Model Summary

Model data logis sistem mencakup entitas utama berikut:
- User & Role
- WastePickupRequest
- Schedule & Assignment
- WasteRecord
- Partner & PartnerFacility
- Workshop & WorkshopRegistration
- PointsTransaction & LeaderboardEntry
- NotificationLog
- AnalyticsSnapshot
- ExportHistory

Relasi antar entitas mengikuti pola satu-ke-banyak dan banyak-ke-banyak sesuai dengan kebutuhan operasional sistem.

---

## B.4 Requirements Traceability Overview

Dokumen SRS ini memiliki keterkaitan langsung dengan backlog Agile melalui prinsip traceability berikut:

- **User Story → Feature → Functional Requirement**
- Setiap Feature di Chapter 3 diturunkan langsung dari backlog.
- Setiap Functional Requirement memiliki referensi implisit ke User Story terkait.
- Atribut kualitas pada Chapter 6 mendukung keseluruhan Feature dan kebutuhan operasional.

Traceability Matrix terperinci dapat disusun sebagai artefak tambahan jika diperlukan.

---

## B.5 Assumptions Summary

- Sistem digunakan oleh satu organisasi (single-organization).
- Formula Poin Bumi didefinisikan di luar dokumen SRS.
- Infrastruktur berbasis cloud.
- Bahasa utama sistem adalah Bahasa Indonesia.
- Pengguna memiliki akses internet saat menggunakan aplikasi.

---

