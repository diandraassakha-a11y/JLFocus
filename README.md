# ZenFocus 🍅📱 — Pomodoro Anti-Prokrastinasi Berbasis Sensor Hardware

ZenFocus adalah aplikasi Android Pomodoro / Focus Timer inovatif yang dirancang untuk membantu pengguna tetap fokus belajar atau bekerja tanpa terdistraksi mengecek HP. Aplikasi ini memanfaatkan dua sensor hardware secara *real-time* untuk menegakkan kedisiplinan sesi fokus.

---

## 🌟 Fitur Utama

1. **Proximity Sensor (Position Sensor - Anti-Distraksi):**
   - Sesi fokus **HANYA** berjalan saat HP diletakkan tertelungkup (*face-down*) di atas meja (sensor proximity tertutup).
   - Jika HP diangkat (*face-up*) sebelum timer selesai, sesi langsung berhenti, tercatat sebagai **"Gagal (Terdistraksi)"**, dan otomatis tersimpan ke database lokal.

2. **Light Sensor (Environment Sensor - Cek Cahaya Ruangan):**
   - Mendeteksi intensitas cahaya ruangan dalam satuan **Lux**.
   - Jika ruangan terlalu gelap (`< 20 lux`), aplikasi memberikan peringatan visual (`"Terlalu Gelap ⚠️"`) dan menyesuaikan skema warna antarmuka kartu status agar pengguna sadar akan kesehatan mata saat membaca/belajar.

3. **Manajemen Sesi & Pilihan Durasi Fleksibel:**
   - Opsi durasi cepat menggunakan `FilterChip`: **1 Menit (Mode Demo)**, **15 Menit**, **25 Menit**, dan **45 Menit**.
   - Input kustom nama tugas/kegiatan fokus.

4. **Halaman Riwayat & Statistik (`History Screen`):**
   - Ringkasan statistik di bagian atas (Total Sesi Berhasil, Total Sesi Gagal, dan Total Waktu Fokus dalam menit).
   - `LazyColumn` menampilkan daftar riwayat sesi lengkap dengan badge status hijau (Berhasil) / merah (Gagal), durasi, timestamp, dan rata-rata tingkat cahaya ruangan (Lux).
   - Fitur hapus riwayat (hapus per item atau hapus semua).

5. **Mode Simulasi Sensor (Untuk Android Emulator):**
   - Dilengkapi *toggle* **Mode Simulasi Sensor** sehingga aplikasi tetap dapat diuji dengan mudah di Android Emulator tanpa memerlukan perangkat fisik yang memiliki sensor proximity/light fisik.

---

## 🏛️ Arsitektur & Tech Stack

Aplikasi ini dibangun menggunakan standar industri Android modern dengan arsitektur **MVVM (Model - View - ViewModel)** yang bersih:

- **Bahasa:** Kotlin
- **UI Framework:** Jetpack Compose & Material 3
- **Asinkronus & Reaktivitas:** Kotlin Coroutines & `StateFlow` / `callbackFlow` (untuk sensor *stream*)
- **Database Lokal:** SQLite menggunakan **Room Persistence Library**
- **Navigasi & Komponen:** Material Icons Extended, Lifecycle ViewModel Compose, Navigation/Tabs sederhana.
- **Minimum SDK:** API 26 (Android 8.0) | Target SDK: API 35

### Struktur Paket (`com.example.zenfocus`)
```text
com.example.zenfocus/
│
├── data/
│   ├── local/
│   │   ├── AppDatabase.kt
│   │   ├── FocusDao.kt
│   │   └── FocusSessionEntity.kt
│   │
│   └── sensor/
│       └── SensorRepository.kt
│
├── ui/
│   ├── screens/
│   │   ├── FocusScreen.kt
│   │   └── HistoryScreen.kt
│   │
│   ├── theme/
│   │   ├── Color.kt
│   │   ├── Theme.kt
│   │   └── Type.kt
│   │
│   └── viewmodel/
│       └── FocusViewModel.kt
│
├── MainActivity.kt
└── ZenFocusApp.kt
```

---

## 🚀 Cara Menjalankan Aplikasi

1. **Clone repository ini** atau buka folder project di **Android Studio** (Ladybug / Jellyfish atau versi terbaru).
2. Tunggu proses **Gradle Sync** selesai.
3. **Menjalankan di Perangkat Fisik (Disarankan):**
   - Pastikan perangkat mendukung Proximity dan Light Sensor.
   - Sambungkan HP via USB Debugging, lalu klik tombol **Run ▶️**.
4. **Menjalankan di Android Emulator:**
   - Karena emulator terkadang tidak mensimulasikan sensor fisik secara akurat, aktifkan **Toggle Mode Simulasi Sensor** di halaman utama aplikasi untuk menguji alur letak meja (*face-down*) secara virtual.

---

## 📸 Screenshot Placeholder

| Halaman Timer (Fokus) | Halaman Riwayat & Statistik | Peringatan Ruangan Gelap |
| :----------------: | :-------------------------: | :-----------------------: |
| *[Screenshot Timer]* | *[Screenshot History]* | *[Screenshot Warning]* |

---

## 📝 Lisensi
Project ini dibuat untuk keperluan pembelajaran dan pengembangan aplikasi Android profesional menggunakan Jetpack Compose & Hardware Sensors.
