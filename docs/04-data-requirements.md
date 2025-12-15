# 4. Data Requirements

Bagian ini menjelaskan kebutuhan data untuk platform Nafas Bumi, termasuk model data logis, definisi setiap entitas, kebutuhan laporan, serta ketentuan integritas dan retensi data.

---

## 4.1 Logical Data Model

Model data logis berikut dibangun berdasarkan seluruh fitur pada Chapter 3 dan interaksi yang muncul dalam backlog.

### **Daftar Entitas Utama**

1. **User**
2. **Role / Authorization**
3. **WastePickupRequest (Reguler & Khusus)**
4. **Schedule (Reguler)**
5. **Assignment (Penugasan Driver)**
6. **WasteSubmission / WasteRecord**
7. **Partner (Mitra)**
8. **PartnerFacility**
9. **Workshop**
10. **WorkshopRegistration**
11. **PointsTransaction**
12. **LeaderboardEntry**
13. **NotificationLog**
14. **AnalyticsSnapshot**
15. **ExportHistory**

### **Relationship Overview**

- Satu **User** dapat memiliki satu atau lebih **Role**.
- Satu **User (kontributor)** dapat membuat banyak **WastePickupRequest**.
- Satu **Schedule** digunakan untuk layanan reguler dan terhubung ke banyak **Assignment**.
- Satu **Driver (User)** dapat menerima banyak **Assignment**.
- Setiap **Assignment** menghasilkan satu atau lebih **WasteRecord**.
- **Partner** memiliki satu atau beberapa **PartnerFacility**.
- User dapat mendaftar ke banyak **Workshop** melalui **WorkshopRegistration**.
- Aktivitas kontribusi menghasilkan **PointsTransaction** dan juga memengaruhi **LeaderboardEntry**.
- Semua aktivitas penting menghasilkan catatan di **NotificationLog**.
- Sistem secara periodik menyimpan ringkasan operasional di **AnalyticsSnapshot**.
- Administrator dapat mengekspor data, dicatat dalam **ExportHistory**.

---

## 4.2 Data Dictionary

### **Tabel 1 — User**

| Field         | Type      | Description           |
| ------------- | --------- | --------------------- |
| user_id       | UUID      | ID unik pengguna      |
| name          | String    | Nama pengguna         |
| email         | String    | Email login           |
| phone         | String    | Nomor telepon         |
| password_hash | String    | Hash kata sandi       |
| role_id       | FK        | Role pengguna         |
| address       | String    | Alamat rumah          |
| created_at    | Timestamp | Waktu akun dibuat     |
| updated_at    | Timestamp | Waktu data diperbarui |

---

### **Tabel 2 — Role / Authorization**

| Field       | Type                                      | Description      |
| ----------- | ----------------------------------------- | ---------------- |
| role_id     | UUID                                      | ID unik role     |
| role_name   | Enum(admin, driver, contributor, partner) | Nama role        |
| permissions | JSON                                      | Daftar hak akses |

---

### **Tabel 3 — WastePickupRequest**

| Field          | Type                                                   | Description                         |
| -------------- | ------------------------------------------------------ | ----------------------------------- |
| request_id     | UUID                                                   | ID permintaan                       |
| user_id        | FK                                                     | Kontributor yang membuat permintaan |
| request_type   | Enum(reguler, khusus)                                  | Tipe permintaan                     |
| location       | GeoPoint                                               | Lokasi penjemputan                  |
| scheduled_time | Timestamp                                              | Waktu penjemputan                   |
| waste_type     | String                                                 | Jenis sampah                        |
| description    | Text                                                   | Catatan tambahan                    |
| photo_url      | String                                                 | Foto sampah (khusus layanan khusus) |
| status         | Enum(pending, approved, rejected, assigned, completed) | Status                              |
| created_at     | Timestamp                                              | Waktu dibuat                        |

---

### **Tabel 4 — Schedule (Reguler)**

| Field           | Type    | Description                      |
| --------------- | ------- | -------------------------------- |
| schedule_id     | UUID    | ID jadwal                        |
| recurrence_rule | String  | Frekuensi (daily/weekly/monthly) |
| day_of_week     | Integer | Opsional, untuk mingguan         |
| time_of_day     | Time    | Waktu pelaksanaan                |
| is_active       | Boolean | Apakah jadwal aktif              |

---

### **Tabel 5 — Assignment (Driver Task)**

| Field         | Type                              | Description            |
| ------------- | --------------------------------- | ---------------------- |
| assignment_id | UUID                              | ID penugasan           |
| driver_id     | FK(User)                          | Driver yang ditugaskan |
| request_id    | FK                                | Permintaan layanan     |
| assigned_at   | Timestamp                         | Waktu penugasan        |
| status        | Enum(assigned, in_progress, done) | Status                 |
| updated_at    | Timestamp                         | Pembaruan terakhir     |

---

### **Tabel 6 — WasteRecord**

| Field         | Type      | Description            |
| ------------- | --------- | ---------------------- |
| record_id     | UUID      | ID record              |
| assignment_id | FK        | Penugasan terkait      |
| waste_type    | String    | Jenis sampah           |
| volume        | Float     | Volume/berat sampah    |
| validated_by  | FK(User)  | Admin yang memvalidasi |
| created_at    | Timestamp | Waktu pencatatan       |

---

### **Tabel 7 — Partner**

| Field         | Type                            | Description      |
| ------------- | ------------------------------- | ---------------- |
| partner_id    | UUID                            | ID mitra         |
| org_name      | String                          | Nama organisasi  |
| contact_email | String                          | Email            |
| contact_phone | String                          | Nomor telepon    |
| status        | Enum(pending, active, inactive) | Status kemitraan |

---

### **Tabel 8 — PartnerFacility**

| Field       | Type     | Description            |
| ----------- | -------- | ---------------------- |
| facility_id | UUID     | ID fasilitas           |
| partner_id  | FK       | Mitra terkait          |
| location    | GeoPoint | Lokasi fasilitas       |
| description | Text     | Catatan tambahan       |
| is_active   | Boolean  | Apakah fasilitas aktif |

---

### **Tabel 9 — Workshop**

| Field       | Type      | Description   |
| ----------- | --------- | ------------- |
| workshop_id | UUID      | ID workshop   |
| title       | String    | Judul         |
| description | Text      | Deskripsi     |
| date        | Timestamp | Jadwal        |
| created_by  | FK(User)  | Admin pembuat |

---

### **Tabel 10 — WorkshopRegistration**

| Field           | Type      | Description       |
| --------------- | --------- | ----------------- |
| registration_id | UUID      | ID registrasi     |
| user_id         | FK        | Peserta           |
| workshop_id     | FK        | Workshop          |
| registered_at   | Timestamp | Waktu pendaftaran |

---

### **Tabel 11 — PointsTransaction**

| Field          | Type                                 | Description       |
| -------------- | ------------------------------------ | ----------------- |
| transaction_id | UUID                                 | ID transaksi poin |
| user_id        | FK                                   | Kontributor       |
| source         | Enum(submission, workshop, activity) | Sumber poin       |
| points         | Integer                              | Jumlah poin       |
| timestamp      | Timestamp                            | Waktu pencatatan  |

---

### **Tabel 12 — LeaderboardEntry**

| Field          | Type    | Description |
| -------------- | ------- | ----------- |
| leaderboard_id | UUID    | ID entri    |
| user_id        | FK      | Kontributor |
| score          | Integer | Skor total  |
| rank           | Integer | Peringkat   |

---

### **Tabel 13 — NotificationLog**

| Field             | Type                              | Description      |
| ----------------- | --------------------------------- | ---------------- |
| notification_id   | UUID                              | ID notifikasi    |
| user_id           | FK                                | Pengguna         |
| message           | Text                              | Isi pesan        |
| sent_at           | Timestamp                         | Waktu pengiriman |
| notification_type | Enum(reminder, thank_you, system) | Tipe notifikasi  |

---

### **Tabel 14 — AnalyticsSnapshot**

| Field        | Type      | Description     |
| ------------ | --------- | --------------- |
| snapshot_id  | UUID      | ID snapshot     |
| metric_name  | String    | Nama metrik     |
| metric_value | Float     | Nilai           |
| period       | String    | Periode laporan |
| generated_at | Timestamp | Waktu pembuatan |

---

### **Tabel 15 — ExportHistory**

| Field         | Type           | Description           |
| ------------- | -------------- | --------------------- |
| export_id     | UUID           | ID ekspor             |
| admin_id      | FK(User)       | Admin yang mengekspor |
| export_format | Enum(pdf, csv) | Format                |
| created_at    | Timestamp      | Waktu ekspor          |

---

## 4.3 Reports

Berikut daftar laporan utama yang harus dapat dihasilkan sistem:

### **1. Laporan Pengelolaan Sampah**

- Total volume sampah per periode
- Rekap berdasarkan jenis sampah
- Rekap kontribusi per kontributor
- Rekap per titik mitra

### **2. Laporan Partisipasi Kegiatan**

- Jumlah peserta workshop
- Tren partisipasi dari waktu ke waktu
- Statistik keterlibatan per user

### **3. Laporan Kemitraan**

- Aktivitas penjemputan di lokasi mitra
- Status fasilitas pengumpulan mitra
- Riwayat kolaborasi

### **4. Laporan Sistem Poin**

- Akumulasi poin per user
- Riwayat transaksi poin
- Dampak kontribusi komunitas

### **5. Audit & Operasional**

- Log notifikasi
- Riwayat ekspor data
- Validasi setoran (driver vs admin)

Semua laporan harus dapat diekspor ke **PDF** atau **CSV**, sesuai backlog (US32).

---

## 4.4 Data Acquisition, Integrity, Retention, and Disposal

### **Data Acquisition**

Data diperoleh melalui:

- Input pengguna (jadwal, permintaan layanan khusus, pendaftaran workshop)
- Input driver (catatan setoran)
- Aktivitas admin (jadwal, validasi)
- Integrasi API eksternal (Google Maps, FCM)

### **Integrity Requirements**

Berdasarkan prioritas atribut kualitas _integrity_ yang ditandai sebagai “In” dalam dokumen kualitas Anda :contentReference[oaicite:1]{index=1}:

- Semua input harus divalidasi sebelum disimpan.
- Harus ada **audit log** untuk perubahan penting (setoran, poin, otorisasi).
- Data sampah tidak boleh rusak atau hilang.
- Perbandingan driver vs admin harus konsisten.

### **Retention Requirements**

Mengikuti UU PDP & PP 71/2019:

- Data operasional dan log minimal disimpan **5 tahun**.
- Data yang tidak relevan harus dihapus atau dianonimkan.
- Data pengguna dapat dihapus berdasarkan permintaan (right to erasure).

### **Disposal Requirements**

- Penghapusan data harus dilakukan dengan proses yang memastikan tidak dapat dipulihkan.
- Backup lama harus dihapus secara terjadwal.
- Akses hanya diberikan kepada admin dengan otorisasi khusus.

---
