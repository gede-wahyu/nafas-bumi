# 8. Other Requirements

Bab ini mencakup persyaratan tambahan yang diperlukan untuk memastikan sistem Nafas Bumi dapat beroperasi secara andal, aman, patuh regulasi, serta mudah dikelola sepanjang siklus hidupnya. Persyaratan dalam bab ini melengkapi kebutuhan fungsional dan non-fungsional yang telah didefinisikan sebelumnya.

---

## 8.1 Legal and Regulatory Requirements

- **OR-LEGAL-1** Sistem harus mematuhi Undang-Undang Informasi dan Transaksi Elektronik (UU ITE) beserta peraturan turunannya.
- **OR-LEGAL-2** Sistem harus mematuhi Peraturan Pemerintah No. 71 Tahun 2019 tentang Penyelenggaraan Sistem dan Transaksi Elektronik.
- **OR-LEGAL-3** Sistem harus mematuhi Undang-Undang Perlindungan Data Pribadi (UU PDP).
- **OR-LEGAL-4** Data pribadi pengguna hanya boleh diproses untuk tujuan yang sah dan relevan dengan layanan.
- **OR-LEGAL-5** Sistem harus menyediakan mekanisme penghapusan atau anonimisasi data pribadi sesuai permintaan yang sah dari pengguna.

---

## 8.2 Audit and Logging Requirements

- **OR-AUDIT-1** Sistem harus mencatat aktivitas penting pengguna dan administrator dalam audit log.
- **OR-AUDIT-2** Aktivitas yang dicatat mencakup login, perubahan data penting, validasi setoran, pengaturan poin, dan perubahan otorisasi.
- **OR-AUDIT-3** Audit log harus dilindungi dari pengubahan tanpa otorisasi.
- **OR-AUDIT-4** Audit log harus dapat diakses oleh administrator berwenang untuk keperluan pemeriksaan dan pelaporan.
- **OR-AUDIT-5** Audit log harus disimpan sesuai kebijakan retensi data.

---

## 8.3 Backup and Recovery Requirements

- **OR-BACKUP-1** Sistem harus melakukan pencadangan data secara berkala.
- **OR-BACKUP-2** Proses pencadangan harus mencakup data operasional, konfigurasi sistem, dan log penting.
- **OR-BACKUP-3** Sistem harus mendukung proses pemulihan data apabila terjadi kegagalan sistem.
- **OR-BACKUP-4** Proses pemulihan harus diuji secara berkala untuk memastikan keandalannya.

---

## 8.4 Monitoring and Alerting Requirements

- **OR-MON-1** Sistem harus menyediakan mekanisme pemantauan ketersediaan dan kinerja layanan.
- **OR-MON-2** Sistem harus menghasilkan peringatan apabila terjadi kegagalan layanan atau penurunan kinerja signifikan.
- **OR-MON-3** Administrator harus dapat menerima notifikasi terkait kondisi kritis sistem.
- **OR-MON-4** Data hasil pemantauan harus digunakan untuk evaluasi dan perbaikan berkelanjutan.

---

## 8.5 Data Privacy and Access Control

- **OR-PRIV-1** Akses terhadap data pengguna harus dibatasi berdasarkan peran dan otorisasi.
- **OR-PRIV-2** Data pribadi tidak boleh ditampilkan kepada pihak yang tidak berwenang.
- **OR-PRIV-3** Sistem harus menyediakan mekanisme pengelolaan hak akses oleh administrator.
- **OR-PRIV-4** Aktivitas akses data sensitif harus dicatat untuk keperluan audit.

---

## 8.6 Deployment and Configuration Requirements

- **OR-DEP-1** Sistem harus mendukung proses deployment yang konsisten di lingkungan operasional.
- **OR-DEP-2** Konfigurasi sistem harus dipisahkan dari kode program.
- **OR-DEP-3** Perubahan konfigurasi tidak boleh memerlukan perubahan kode utama.
- **OR-DEP-4** Sistem harus mendukung rollback apabila terjadi kegagalan deployment.

---

## 8.7 Operational and Maintenance Requirements

- **OR-OPS-1** Sistem harus menyediakan dokumentasi teknis untuk pengelolaan dan pemeliharaan.
- **OR-OPS-2** Sistem harus menyediakan dokumentasi penggunaan bagi administrator.
- **OR-OPS-3** Prosedur pemeliharaan sistem harus meminimalkan gangguan layanan.
- **OR-OPS-4** Sistem harus mendukung perbaikan bug dan pembaruan fitur secara bertahap.

---

