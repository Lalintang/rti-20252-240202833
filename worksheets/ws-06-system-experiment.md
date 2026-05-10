# WS-06: System-Experiment Mapping

> **Bab 6 — System Design sebagai Experimental Artifact**

---

## Ringkasan Materi

### Sistem = Instrumen Pengujian, Bukan Produk

Seorang engineer bertanya "apakah sistem bekerja?" — seorang peneliti bertanya "apa yang bisa dibuktikan sistem ini?" Sistem dalam riset adalah **artifact** — objek yang sengaja dibuat untuk menguji klaim spesifik.

### System as Experiment Model

```
RQ → Variable → System Component → Experimental Setup → Output
```

Setiap komponen sistem harus bisa ditelusuri ke variabel riset (top-down), dan setiap pengukuran harus menjawab RQ (bottom-up).

### Mapping Variabel ke Komponen

| Tipe Variabel | Peran di Sistem | Contoh |
|---------------|----------------|--------|
| **IV** (Independent) | Modul yang bisa di-toggle/swap | Algoritma A vs B |
| **DV** (Dependent) | Modul pengukuran | Logger, metrics collector |
| **CV** (Control) | Config yang dikunci | Dataset, parameter tetap |

Jika variabel tidak bisa di-map ke komponen apapun → arsitektur perlu didesain ulang.

### 4 Prinsip Desain Eksperimental

| Prinsip | Pertanyaan Kunci |
|---------|-----------------|
| **Traceability** | Komponen ini melayani variabel yang mana? |
| **Modularity** | Bisakah IV diubah tanpa memengaruhi yang lain? |
| **Controllability** | Apakah CV dieksternalisasi ke config file? |
| **Measurability** | Apakah sistem otomatis menghasilkan data yang dibutuhkan? |

### Variable Isolation melalui Arsitektur

- **Modular architecture** — Pisahkan berdasarkan variabel
- **Configuration-driven** — Ubah config (YAML/JSON), bukan code
- **Feature toggles** — On/off flag untuk ablation study

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan sistem | Memenuhi kebutuhan user | Menguji hipotesis, menghasilkan bukti |
| Arsitektur | Optimasi performa & skalabilitas | Optimasi isolasi variabel & reprodusibilitas |
| Konfigurasi | Sering hardcoded | Dieksternalisasi ke config file |
| Fitur tambahan | Menambah nilai user | Menambah noise jika tidak terkait RQ |

### Istilah Penting

- **Artifact** — Objek yang sengaja dibuat untuk memecahkan masalah atau menguji proposisi
- **Traceability** — Kemampuan menelusuri hubungan RQ → variabel → komponen → output
- **Variable Isolation** — Mengubah hanya satu variabel sambil menahan yang lain konstan
- **Ablation Study** — Menguji kontribusi tiap komponen dengan melepasnya satu per satu
- **Configuration-driven Execution** — Semua parameter di config file, bukan hardcoded

---

## Template A.6 — Mapping RQ ke Arsitektur Sistem

```
SYSTEM-EXPERIMENT MAPPING

Research Question: Apakah dimensi Smart Tourism Technology (Informativeness, Accessibility, Interactivity, Personalization) berpengaruh secara signifikan terhadap peningkatan pengalaman wisatawan (skor kepuasan) di destinasi wisata digital?

Variable → Component Mapping:
| Variabel | Tipe | Komponen Sistem | Cara Manipulasi/Pengukuran |
|----------|------|-----------------|---------------------------|
| STT Dimensions| IV   |UI/UX & Content Module (Informativeness, Access, dsb)|Fitur aplikasi yang diaktifkan atau konten informasi yang dipersonalisasi|
| Kepuasan Wisatawan| DV   |Survey Engine / Feedback Module|Kuesioner Likert yang muncul otomatis setelah user mencoba fitur sistem|
| Frekuensi Kunjungan| CV   |User Profile / Log History|Data dari database yang dikunci (filter hanya untuk user tertentu) agar tidak bias|

4 Prinsip Desain:
  [✓] Traceability — etiap fitur aplikasi (misal: menu navigasi) mewakili dimensi Accessibility
  [✓] Variable Isolation — Kamu bisa menguji satu dimensi (misal: hanya fitur Personalization) tanpa mengganggu fitur lainnya
  [✓] Measurement Integration — Form penilaian kepuasan tertanam langsung di dalam aplikasi
  [✓] Reproducibility — Aplikasi dapat dideploy ulang dengan konfigurasi fitur yang sama oleh peneliti lain

Experimental Setup:
  Input data     : Data profil wisatawan (usia, domisili, frekuensi kunjungan) dan respons interaksi real-time user terhadap fitur aplikasi Smart Tourism (klik, durasi baca, dan penggunaan fitur peta).
  Parameter      : Parameter dalam penelitian ini dikunci melalui beberapa pengaturan ketat, mulai dari kontrol status aktif-nonaktif pada modul fitur (Informativeness, Accessibility, Interactivity, dan Personalization) hingga penggunaan skala Likert 1-5 untuk mengukur persepsi pengguna secara konsisten. Validitas hasil ditentukan dengan ambang signifikansi P-value < 0,05 untuk pengujian hipotesis, dengan target sampel minimal 100 responden guna menjamin kekuatan statistik dan akurasi data dalam menggambarkan pengaruh teknologi terhadap pengalaman wisatawan.
  Output format  : Output format dalam penelitian ini disajikan dalam bentuk dataset mentah berbasis file .csv atau .xlsx yang merangkum seluruh jawaban kuesioner dan log aktivitas pengguna secara sistematis. Data tersebut kemudian ditransformasikan ke dalam laporan statistik yang mencakup tabel koefisien regresi, nilai T-test, dan R-Square untuk menguji signifikansi pengaruh teknologi terhadap kepuasan wisatawan. Sebagai bentuk interpretasi visual, hasil analisis akan dilengkapi dengan grafik batang atau diagram radar yang memetakan perbandingan kontribusi setiap dimensi teknologi guna mempermudah penarikan kesimpulan ilmiah.
```

---

## Latihan 1 — Variable-to-Component Mapping

Gunakan RQ dan variabel dari WS-05. Petakan ke komponen sistem.

**RQ:** Apakah dimensi Smart Tourism Technology (Informativeness, Accessibility, Interactivity, Personalization) berpengaruh secara signifikan terhadap peningkatan pengalaman wisatawan (skor kepuasan) di destinasi wisata digital?

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi / Pengukuran |
|----------|------|-----------------|---------------------------|
|Dimensi STT| IV | Feature Modules (Informasi, Peta, Chat, Profil) | Mengaktifkan/menonaktifkan modul tertentu melalui dashboard admin atau config file |
|Kepuasan Wisatawan| DV | Feedback Engine (Pop-up Survey/Rating) | Rekam skor Likert (1-5) yang diinput user setelah mencoba fitur ke dalam database |
|Usia & Frekuensi| CV | User Profile DB | Melakukan filter data (query SQL) agar analisis hanya fokus pada kelompok tertentu guna menghindari bias |

**Apakah semua variabel bisa di-map?** [✓] Ya / [ ] Tidak
> Jika tidak, komponen apa yang perlu ditambahkan? _________

---

## Latihan 2 — 4 Prinsip Desain

Evaluasi desain sistem terhadap 4 prinsip.

| Prinsip | Status | Bukti / Penjelasan |
|---------|--------|-------------------|
| Traceability | ✅ | Modul "Rekomendasi" dalam aplikasi jelas merupakan perwujudan dari variabel Personalization |
| Modularity | ✅ | Fitur Chatbot (Interactivity) bisa dimatikan via admin panel tanpa merusak fitur peta |
| Controllability | ✅ | Lokasi wisata yang ditampilkan bisa dikontrol melalui konfigurasi database (hanya destinasi digital tertentu) |
| Measurability | ✅ | Sistem merekam berapa lama user melihat informasi (metrik tambahan) dan skor kepuasan akhir |

**Prinsip mana yang paling sulit dipenuhi?** Variable Isolation (Modularity)
**Strategi untuk mengatasinya:**
> Memastikan kode aplikasi tidak saling bergantung (tightly coupled). Menggunakan arsitektur modular sehingga jika satu fitur (misal: peta) error, fitur informasi (teks) tetap bisa diuji secara terpisah.

---

## Latihan 3 — Ablation Study Planning

Jika sistem memiliki 3 komponen utama, rencanakan ablation study.

| Kondisi | Komponen A | Komponen B | Komponen C | Hasil yang Diharapkan |
|---------|-----------|-----------|-----------|----------------------|
| Full | ✅ Aktif| ✅ Aktif | ✅ Aktif  | Baseline Penuh: Kepuasan tertinggi |
| – A | ❌ Nonaktif | ✅ | ✅ | Mengukur seberapa penting Accessibility bagi user |
| – B | ✅ | ❌ Nonaktif | ❌ Nonaktif | Mengukur dampak hilangnya Personalization |
| – C | ✅ | ✅ | ❌ Nonaktif | Mengukur dampak hilangnya Informativeness |

**Komponen mana yang diprediksi paling berkontribusi?** Informasi Detail (C).
**Mengapa?**
> Sesuai teori Smart Tourism, wisatawan datang untuk mencari informasi. Tanpa informasi yang akurat (Informativeness), fitur canggih seperti peta atau rekomendasi tidak akan berguna bagi mereka.
---

## Refleksi

> Apa risiko jika sistem dibangun seperti produk (monolitik, fitur lengkap) lalu baru dilakukan eksperimen? Mengapa arsitektur modular penting untuk riset?

**Jawaban:**
> Risikonya adalah "Confounding Variables". Jika aplikasinya monolitik dan user merasa tidak puas, kita tidak tahu bagian mana yang salah—apakah karena informasinya buruk, petanya sulit dibuka, atau desainnya jelek. Kita tidak bisa menarik kesimpulan ilmiah yang spesifik.
> Arsitektur modular penting karena memungkinkan peneliti untuk mengisolasi variabel. Dengan mematikan/menyalakan fitur tertentu, kita bisa membuktikan secara empiris fitur mana yang benar-benar memberikan dampak signifikan pada kepuasan user.
