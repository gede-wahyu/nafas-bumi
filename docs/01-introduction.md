# 1. Introduction

## 1.1 Purpose

Dokumen _Software Requirements Specification_ (SRS) ini disusun untuk mendefinisikan kebutuhan perangkat lunak bagi pengembangan platform digital **Nafas Bumi**, sebuah sistem yang digunakan oleh satu organisasi peduli lingkungan untuk mengelola proses operasionalnya. Dokumen ini menjadi dasar bagi tim pengembang, analis sistem, penguji, serta pemangku kepentingan dalam melakukan desain, implementasi, verifikasi, dan validasi sistem.

Cakupan dokumen ini mencakup deskripsi fungsional, batasan teknis, persyaratan kualitas, model data, antarmuka eksternal, serta ketentuan lain yang diperlukan agar sistem dapat dikembangkan dan berjalan sesuai tujuan organisasi.

## 1.2 Document Conventions

Dokumen ini menggunakan konvensi berikut:

- Istilah domain spesifik dituliskan **tebal** pada kemunculan pertama.
- Kebutuhan fungsional menggunakan kode **FR-x.y**.
- Kebutuhan non-fungsional menggunakan kode **NFR-x.y**.
- Elemen yang masih menunggu keputusan organisasi dicatat sebagai **TBD** (_To Be Determined_).
- Diagram, model data, atau tabel tambahan ditempatkan pada bagian terkait atau lampiran.

## 1.3 Project Scope

### In-Scope

1. **Aplikasi Seluler Pengguna (Android & iOS)**

   - Registrasi dan autentikasi
   - Penjadwalan penjemputan sampah
   - Kalender workshop dan kegiatan edukasi
   - Sistem _Poin Bumi_ (perhitungan poin: **TBD**)
   - Penukaran poin dengan hadiah
   - Pelacakan riwayat kontribusi
   - Notifikasi aktivitas dan pengingat

2. **Aplikasi Seluler Volunteer/Driver**

   - Daftar tugas penjemputan
   - Informasi rute dan lokasi
   - Konfirmasi penjemputan
   - Input jenis dan jumlah sampah

3. **Dashboard Admin (Web-Based)**

   - Manajemen pengguna, jadwal, dan rute
   - Manajemen konten edukasi dan kegiatan
   - Manajemen mitra dan katalog hadiah
   - Pembuatan laporan operasional dan dampak
   - Monitoring kontribusi pengguna

4. **Infrastruktur Backend**
   - Layanan API
   - Basis data
   - Sistem autentikasi
   - Integrasi layanan eksternal (Google Maps API, Firebase Cloud Messaging)

### Out-of-Scope

- Fitur e-commerce untuk jual beli produk daur ulang
- Sistem pembayaran atau dompet digital internal
- Identifikasi otomatis jenis sampah berbasis AI
- Integrasi real-time dengan sistem logistik pihak ketiga
- Multi-tenancy (sistem digunakan oleh satu organisasi saja)

## 1.4 References

Sumber rujukan yang digunakan:

1. **Project Plan “Nafas Bumi” v1.0** — mencakup latar belakang, stakeholder, scope, dan lingkungan operasional.
2. **Quality Attributes – Step 1 (In/Out Reasoning)** — keputusan atribut kualitas yang relevan / tidak relevan.
3. **Quality Attributes – Step 2 (Prioritization Table)** — tabel pairwise comparison prioritas atribut kualitas.
4. Regulasi Indonesia:
   - Undang-Undang ITE
   - PP No. 71 Tahun 2019 tentang Penyelenggaraan Sistem dan Transaksi Elektronik
   - Undang-Undang Perlindungan Data Pribadi (UU PDP)
