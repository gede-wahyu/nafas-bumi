# 4. Data Requirements

Bab ini mendefinisikan kebutuhan data untuk platform Nafas Bumi, mencakup model data logis, definisi entitas, kebutuhan pelaporan, serta ketentuan terkait integritas dan retensi data.

---

## 4.1 Logical Data Model

Model data logis disusun berdasarkan fitur-fitur sistem yang didefinisikan pada Chapter 3 serta interaksi yang tercermin dalam backlog kebutuhan.

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
12. **PointRule**
13. **LeaderboardEntry**
14. **ContributionProfile**
15. **SessionLog**
16. **AnalyticsSnapshot**
17. **ExportHistory**

### **Relationship Overview**

#### **Autentikasi & Autorisasi**
- Satu **User** dapat memiliki satu atau lebih **Role**.
- Setiap login **User** menciptakan **SessionLog** untuk tracking keamanan.

#### **Layanan Pengumpulan Sampah**
- Satu **User (kontributor)** dapat membuat banyak **WastePickupRequest** (reguler & khusus).
- Satu **Schedule** digunakan untuk layanan reguler dan terhubung ke banyak **Assignment**.
- Satu **Driver (User)** dapat menerima banyak **Assignment**.
- Setiap **Assignment** menghasilkan satu atau lebih **WasteRecord**.

#### **Kemitraan & Fasilitas**
- **Partner** memiliki satu atau beberapa **PartnerFacility**.
- **PartnerFacility** dapat menjadi lokasi penjemputan dalam **WastePickupRequest**.

#### **Workshop & Edukasi**
- **User** dapat mendaftar ke banyak **Workshop** melalui **WorkshopRegistration**.
- Setiap **Workshop** dapat memiliki banyak peserta melalui **WorkshopRegistration**.

#### **Sistem Poin & Gamifikasi**
- Aktivitas kontribusi menghasilkan **PointsTransaction** berdasarkan **PointRule**.
- **PointsTransaction** mempengaruhi skor di **LeaderboardEntry**.
- Setiap **User** memiliki satu **ContributionProfile** yang merangkum dampak kontribusi.

#### **Notifikasi & Interaksi**
- Sistem mengirim push notification real-time menggunakan layanan FCM/APNs.
- Push notification tidak disimpan dalam database.

#### **Analitik & Pelaporan**
- Sistem secara periodik menyimpan ringkasan operasional di **AnalyticsSnapshot**.
- Administrator dapat mengekspor data, dicatat dalam **ExportHistory**.

### **Entity Relationship Diagram (ERD)**

![Nafas Bumi ERD](./assets/erd/nafas-bumi-erd.png)

---

## 4.2 Data Dictionary

### **Tabel 1 — User**

| Field              | Type                                    | Description           |
| ------------------ | --------------------------------------- | --------------------- |
| user_id            | UUID                                    | ID unik pengguna      |
| name               | String                                  | Nama pengguna         |
| email              | String                                  | Email login           |
| phone              | String                                  | Nomor telepon         |
| password_hash      | String                                  | Hash kata sandi       |
| role_id            | FK                                      | Role pengguna         |
| address            | String                                  | Alamat rumah          |
| profile_visibility | Enum(public, private, friends_only)     | Pengaturan privasi    |
| last_login         | Timestamp                               | Waktu login terakhir  |
| created_at         | Timestamp                               | Waktu akun dibuat     |
| updated_at         | Timestamp                               | Waktu data diperbarui |

---

### **Tabel 2 — Role / Authorization**

| Field       | Type                                      | Description      |
| ----------- | ----------------------------------------- | ---------------- |
| role_id     | UUID                                      | ID unik role     |
| role_name   | Enum(admin, driver, contributor, partner) | Nama role        |
| permissions | JSON                                      | Daftar hak akses |
| created_at  | Timestamp                                 | Waktu dibuat     |
| updated_at  | Timestamp                                 | Waktu diperbarui |

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

### **Tabel 12 — PointRule**

| Field         | Type      | Description          |
| ------------- | --------- | -------------------- |
| rule_id       | UUID      | ID aturan poin       |
| activity_type | String    | Tipe aktivitas       |
| points_awarded| Integer   | Poin yang diberikan  |
| description   | Text      | Deskripsi aturan     |
| is_active     | Boolean   | Status aktif         |
| created_at    | Timestamp | Waktu dibuat         |
| updated_at    | Timestamp | Waktu diperbarui     |

---

### **Tabel 13 — LeaderboardEntry**

| Field          | Type    | Description             |
| -------------- | ------- | ----------------------- |
| leaderboard_id | UUID    | ID entri                |
| user_id        | FK      | Kontributor             |
| score          | Integer | Skor total              |
| rank           | Integer | Peringkat               |
| period         | String  | Periode (bulanan/total) |

---

### **Tabel 14 — ContributionProfile**

| Field               | Type      | Description            |
| ------------------- | --------- | ---------------------- |
| profile_id          | UUID      | ID profil              |
| user_id             | FK        | Kontributor            |
| total_contributions | Integer   | Total kontribusi       |
| total_waste_volume  | Float     | Total volume sampah    |
| impact_summary      | JSON      | Ringkasan dampak       |
| share_token         | String    | Token untuk sharing    |
| privacy_settings    | JSON      | Pengaturan privasi     |
| created_at          | Timestamp | Waktu dibuat           |
| updated_at          | Timestamp | Waktu diperbarui       |

---

### **Tabel 15 — SessionLog**

| Field       | Type      | Description      |
| ----------- | --------- | ---------------- |
| session_id  | UUID      | ID sesi          |
| user_id     | FK        | Pengguna         |
| login_at    | Timestamp | Waktu login      |
| logout_at   | Timestamp | Waktu logout     |
| ip_address  | String    | Alamat IP        |
| device_info | String    | Info perangkat   |

---

### **Tabel 16 — AnalyticsSnapshot**

| Field        | Type      | Description     |
| ------------ | --------- | --------------- |
| snapshot_id  | UUID      | ID snapshot     |
| metric_name  | String    | Nama metrik     |
| metric_value | Float     | Nilai           |
| period       | String    | Periode laporan |
| generated_at | Timestamp | Waktu pembuatan |

---

### **Tabel 17 — ExportHistory**

| Field         | Type           | Description           |
| ------------- | -------------- | --------------------- |
| export_id     | UUID           | ID ekspor             |
| admin_id      | FK(User)       | Admin yang mengekspor |
| export_format | Enum(pdf, csv) | Format                |
| created_at    | Timestamp      | Waktu ekspor          |

---

## 4.3 Reports

Sistem harus mendukung penyusunan dan penyajian laporan utama sebagai berikut:

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

### **5. Laporan Profil Kontribusi Individual**

- Riwayat kontribusi per pengguna
- Ringkasan dampak kontribusi (total volume, jenis sampah, periode aktif)
- Statistik peringkat dan ranking
- Profil kontribusi yang dibagikan

### **6. Laporan Autentikasi & Keamanan**

- Riwayat login/logout pengguna
- Aktivitas sesi mencurigakan
- Riwayat perubahan kredensial

### **7. Operasional**

- Riwayat ekspor data
- Validasi setoran (driver vs admin)

Semua laporan harus dapat diekspor ke **PDF** atau **CSV**, sesuai backlog (US32).

---

## 4.4 Data Acquisition, Integrity, Retention, and Disposal

### **Data Acquisition**

Data sistem diperoleh melalui sumber-sumber berikut:

- Input pengguna (jadwal, permintaan layanan khusus, pendaftaran workshop)
- Input driver (catatan setoran)
- Aktivitas admin (jadwal, validasi)
- Integrasi API eksternal (Google Maps, FCM)

### **Integrity Requirements**

Berdasarkan prioritas atribut kualitas integrity yang ditetapkan dalam dokumen analisis kualitas:

- Semua input harus divalidasi sebelum disimpan.
- Data sampah tidak boleh rusak atau hilang.
- Perbandingan driver vs admin harus konsisten.

### **Retention Requirements**

Ketentuan retensi data ditetapkan dengan mengacu pada Undang-Undang Perlindungan Data Pribadi (UU PDP) dan Peraturan Pemerintah No. 71 Tahun 2019:

- Data operasional dan log minimal disimpan **5 tahun**.
- Data yang tidak relevan harus dihapus atau dianonimkan.
- Data pengguna dapat dihapus berdasarkan permintaan (right to erasure).

### **Disposal Requirements**

- Penghapusan data harus dilakukan dengan proses yang memastikan tidak dapat dipulihkan.
- Backup lama harus dihapus secara terjadwal.
- Akses hanya diberikan kepada admin dengan otorisasi khusus.

---
