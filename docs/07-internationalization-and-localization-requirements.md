# 7. Internationalization and Localization Requirements

Bab ini mendefinisikan kebutuhan sistem terkait *internationalization* (i18n) dan *localization* (l10n) untuk memastikan aplikasi Nafas Bumi dapat digunakan secara efektif oleh pengguna dengan latar belakang bahasa dan budaya yang berbeda, serta mudah diperluas ke konteks geografis lain di masa depan.

---

## 7.1 Localization Requirements

### 7.1.1 Language Support
- **L10N-1** Bahasa Indonesia digunakan sebagai bahasa utama sistem pada seluruh antarmuka pengguna.
- **L10N-2** Seluruh teks antarmuka, notifikasi, dan pesan kesalahan harus menggunakan Bahasa Indonesia yang jelas dan mudah dipahami.
- **L10N-3** Penggunaan istilah teknis harus disesuaikan dengan konteks masyarakat umum dan tidak ambigu.

### 7.1.2 Date, Time, and Number Formats
- **L10N-4** Sistem harus menggunakan format tanggal Indonesia (DD-MM-YYYY).
- **L10N-5** Sistem harus menggunakan format waktu 24 jam.
- **L10N-6** Sistem harus menggunakan format angka dan pemisah ribuan sesuai standar Indonesia.

### 7.1.3 Currency Representation
- **L10N-7** Apabila sistem menampilkan nilai moneter (misalnya nilai hadiah atau insentif), maka harus menggunakan mata uang Rupiah (IDR).
- **L10N-8** Simbol mata uang dan format penulisan harus mengikuti standar lokal.

### 7.1.4 Address and Location Format
- **L10N-9** Sistem harus mendukung format alamat yang umum digunakan di Indonesia.
- **L10N-10** Informasi lokasi harus disajikan dalam konteks wilayah administratif lokal (kota, kecamatan, dsb.) bila tersedia.

---

## 7.2 Internationalization Requirements

### 7.2.1 Language Extensibility
- **I18N-1** Sistem harus dirancang agar mendukung penambahan bahasa lain di masa depan tanpa perubahan arsitektur besar.
- **I18N-2** Seluruh teks antarmuka harus dipisahkan dari kode program dan dikelola melalui mekanisme konfigurasi atau resource bundle.

### 7.2.2 Unicode Support
- **I18N-3** Sistem harus mendukung Unicode (UTF-8) untuk memastikan kompatibilitas karakter multibahasa.
- **I18N-4** Penyimpanan dan pemrosesan teks harus mempertahankan karakter khusus tanpa kehilangan informasi.

### 7.2.3 Regional Configuration
- **I18N-5** Sistem harus memungkinkan konfigurasi format tanggal, waktu, dan angka berdasarkan locale.
- **I18N-6** Sistem harus memungkinkan penyesuaian aturan tampilan konten sesuai kebutuhan regional di masa depan.

---

## 7.3 Cultural and Contextual Considerations

- **I18N-7** Konten edukasi dan pesan sistem harus memperhatikan norma sosial dan budaya lokal.
- **I18N-8** Penggunaan ikon, warna, dan simbol harus menghindari makna yang dapat menimbulkan salah tafsir.
- **I18N-9** Sistem harus menghindari penggunaan istilah yang berpotensi menyinggung kelompok tertentu.

---

## 7.4 Future Expansion Considerations

- Sistem dirancang dengan asumsi penggunaan utama di Indonesia pada fase awal.
- Jika diperlukan ekspansi ke wilayah atau negara lain:
  - Bahasa tambahan dapat ditambahkan melalui modul lokalisasi.
  - Format data dapat disesuaikan dengan locale baru.
  - Konten edukasi dapat disesuaikan dengan konteks lokal setempat.

---

