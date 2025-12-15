# 6. Quality Attributes

Bab ini mendefinisikan kebutuhan non-fungsional sistem Nafas Bumi berdasarkan atribut kualitas yang telah dianalisis, diseleksi, dan diprioritaskan. Atribut kualitas yang disertakan merupakan atribut yang relevan dengan tujuan sistem dan konteks operasional organisasi.

Urutan atribut dalam bab ini mencerminkan prioritas relatif berdasarkan hasil pairwise comparison.

---

## 6.1 Availability

Sistem harus tersedia secara konsisten untuk mendukung operasional harian pengelolaan sampah dan aktivitas komunitas.

**Requirements:**
- **NFR-AVAIL-1** Sistem harus memiliki tingkat ketersediaan minimum 99,5% per bulan.
- **NFR-AVAIL-2** Sistem harus mendukung pemulihan layanan dengan waktu pemulihan (MTTR) kurang dari 1 jam.
- **NFR-AVAIL-3** Sistem harus melakukan pencadangan data secara rutin.
- **NFR-AVAIL-4** Gangguan sistem tidak boleh menyebabkan kehilangan data operasional.

---

## 6.2 Security

Sistem harus melindungi data pengguna, data operasional, dan data organisasi dari akses tidak sah serta penyalahgunaan.

**Requirements:**
- **NFR-SEC-1** Sistem harus menerapkan autentikasi pengguna sebelum memberikan akses ke fitur.
- **NFR-SEC-2** Sistem harus membatasi akses berdasarkan peran pengguna (role-based access control).
- **NFR-SEC-3** Data sensitif harus disimpan dalam bentuk terenkripsi.
- **NFR-SEC-4** Semua komunikasi data harus menggunakan koneksi terenkripsi.
- **NFR-SEC-5** Sistem harus mencatat aktivitas penting untuk keperluan audit dan investigasi.

---

## 6.3 Scalability

Sistem harus mampu menangani peningkatan jumlah pengguna, transaksi, dan volume data tanpa penurunan kinerja yang signifikan.

**Requirements:**
- **NFR-SCAL-1** Sistem harus mampu menangani peningkatan jumlah pengguna aktif secara bertahap.
- **NFR-SCAL-2** Sistem harus mendukung penambahan kapasitas komputasi dan penyimpanan tanpa perubahan arsitektur besar.
- **NFR-SCAL-3** Penambahan beban tidak boleh mengganggu layanan yang sedang berjalan.

---

## 6.4 Reliability

Sistem harus dapat diandalkan untuk mendukung proses operasional yang bersifat rutin dan berulang.

**Requirements:**
- **NFR-REL-1** Sistem harus memproses permintaan pengguna secara konsisten tanpa kesalahan sistem.
- **NFR-REL-2** Sistem harus mampu melanjutkan operasional setelah gangguan tanpa menyebabkan inkonsistensi data.
- **NFR-REL-3** Sistem harus memiliki mekanisme pemantauan untuk mendeteksi kegagalan layanan.

---

## 6.5 Performance

Sistem harus memberikan respons yang cepat untuk menjaga pengalaman pengguna dan efektivitas operasional.

**Requirements:**
- **NFR-PERF-1** Waktu respons untuk operasi utama (penjadwalan, pencatatan setoran, melihat laporan) tidak boleh melebihi 3 detik pada kondisi normal.
- **NFR-PERF-2** Sistem harus mendukung pemrosesan data secara near real-time untuk laporan operasional.
- **NFR-PERF-3** Operasi analitik tidak boleh mengganggu transaksi operasional utama.

---

## 6.6 Integrity

Sistem harus menjamin keakuratan, konsistensi, dan keutuhan data selama siklus hidup data.

**Requirements:**
- **NFR-INTEG-1** Sistem harus melakukan validasi terhadap seluruh input data sebelum disimpan.
- **NFR-INTEG-2** Perubahan data penting harus tercatat dalam audit log.
- **NFR-INTEG-3** Data setoran sampah harus konsisten antara catatan driver dan validasi admin.
- **NFR-INTEG-4** Sistem harus mencegah duplikasi atau korupsi data.

---

## 6.7 Interoperability

Sistem harus dapat berinteraksi dengan sistem atau layanan eksternal yang relevan.

**Requirements:**
- **NFR-INTEROP-1** Sistem harus menyediakan API yang terdokumentasi dengan baik.
- **NFR-INTEROP-2** Sistem harus mendukung pertukaran data dengan layanan peta dan notifikasi.
- **NFR-INTEROP-3** Integrasi eksternal tidak boleh mengganggu stabilitas sistem inti.

---

## 6.8 Robustness

Sistem harus mampu menangani kesalahan input dan kondisi tak terduga tanpa menyebabkan kegagalan berantai.

**Requirements:**
- **NFR-ROB-1** Sistem harus menangani input tidak valid dengan pesan kesalahan yang jelas.
- **NFR-ROB-2** Kesalahan pada satu modul tidak boleh menyebabkan kegagalan sistem secara keseluruhan.
- **NFR-ROB-3** Sistem harus mampu melanjutkan operasi setelah error non-kritis.

---

## 6.9 Usability

Sistem harus mudah digunakan oleh berbagai jenis pengguna dengan tingkat literasi digital yang berbeda.

**Requirements:**
- **NFR-USE-1** Antarmuka pengguna harus intuitif dan konsisten.
- **NFR-USE-2** Proses utama (misalnya penjadwalan penjemputan) harus dapat diselesaikan dalam waktu singkat.
- **NFR-USE-3** Sistem harus menyediakan pesan bantuan atau petunjuk penggunaan.
- **NFR-USE-4** Aplikasi harus dapat digunakan dengan nyaman di kondisi lapangan.

---

## 6.10 Efficiency

Sistem harus mengoptimalkan penggunaan sumber daya komputasi dan biaya operasional.

**Requirements:**
- **NFR-EFF-1** Sistem harus menggunakan sumber daya komputasi secara efisien.
- **NFR-EFF-2** Proses backend harus dirancang untuk meminimalkan biaya operasional jangka panjang.
- **NFR-EFF-3** Sistem harus tetap stabil pada jam sibuk tanpa pemborosan sumber daya.

---

## 6.11 Modifiability

Sistem harus mudah disesuaikan terhadap perubahan kebutuhan bisnis dan kebijakan organisasi.

**Requirements:**
- **NFR-MOD-1** Perubahan fitur tidak boleh memerlukan penulisan ulang sistem secara keseluruhan.
- **NFR-MOD-2** Konfigurasi kebijakan (jadwal, poin, peran) harus dapat diubah dengan mudah.
- **NFR-MOD-3** Struktur kode harus mendukung pemeliharaan jangka panjang.

---

## 6.12 Portability

Sistem harus dapat dijalankan dan dipindahkan ke lingkungan operasional lain dengan usaha minimal.

**Requirements:**
- **NFR-PORT-1** Sistem harus mendukung proses deployment yang konsisten.
- **NFR-PORT-2** Ketergantungan pada platform tertentu harus diminimalkan.
- **NFR-PORT-3** Antarmuka pengguna harus konsisten di berbagai perangkat.

---

## 6.13 Reusability

Komponen sistem harus dapat digunakan kembali untuk pengembangan fitur di masa depan.

**Requirements:**
- **NFR-REUSE-1** Modul sistem harus dirancang agar dapat digunakan ulang.
- **NFR-REUSE-2** Komponen umum tidak boleh bergantung pada konteks fitur tertentu.
- **NFR-REUSE-3** Struktur kode harus mendukung pengujian ulang yang mudah.

---

## 6.14 Attributes Excluded from Scope

Atribut berikut tidak disertakan karena tidak relevan atau tidak realistis untuk konteks sistem:

- **Installability** — aplikasi diakses melalui app store atau web.
- **Safety** — tidak berhubungan langsung dengan risiko keselamatan fisik.
- **Verifiability** — sistem tidak dapat menjamin bebas bug sepenuhnya.

---

