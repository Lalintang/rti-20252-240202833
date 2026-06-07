# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

### Reproducible Implementation Model

```
Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result
```

Setiap transisi memiliki syarat:
- Design → Implementation: kode sesuai mapping variabel-ke-komponen
- Implementation → Environment: versi, dependency, seed, path, OS eksplisit
- Environment → Consistency: seed terkunci, urutan deterministik
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: siapa pun ikuti dokumentasi → hasil sama/serupa

### Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|---------|-------------|-------|
| **Repeatability** | Sama | Sama | Sama persis |
| **Reproducibility** | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

Capai **repeatability** dulu, baru **reproducibility**.

### Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Sistem berfungsi untuk user | Instrumen pengukuran konsisten |
| Dependency | Update ke terbaru | Lock di versi spesifik |
| Testing | Unit, integration, E2E | Repeatability test (run ulang → sama?) |
| Dokumentasi | User guide, API docs | Environment spec, execution steps, expected output |
| Config | Default masuk akal | Setiap parameter eksplisit & adjustable |

### Jebakan Kognitif

1. Menunda environment setup → bug sulit dilacak
2. Tidak pakai version control → hasil tidak bisa direkonstruksi
3. Menolak Docker/container → "di laptop saya bisa" saat review
4. 3× hasil sama ≠ repeatable (bisa cache/state tersimpan)

### Istilah Penting

- **Environment Specification** — Deskripsi lengkap: hardware, OS, runtime, library + versi, config, seed
- **Dependency** — Komponen eksternal yang harus di-lock versinya
- **Config-driven** — Parameter dieksternalisasi ke file konfigurasi, bukan hardcode

---

## Template A.9 — Dokumentasi Setup Eksperimen

```
EXPERIMENT SETUP DOCUMENTATION

Hardware:
  CPU     : AMD Ryzen 5 5600H (6 Cores, 12 Threads)
  RAM     : 16 GB DDR4 Dual-Channel
  GPU     : Integrated AMD Radeon Graphics (CPU-only untuk running skrip statistik)
  Storage : SSD NVMe 512 GB 

Software:
  OS        : Windows 11 Home 64-bit
  Runtime   : Python 3.10.11 & Node.js v18.16.0
  Framework : Express.js (Backend API), Flask v2.3.2 (Data Analytics)

Dependencies:
| Library | Version | Sumber | Hash/Checksum |
|---------|---------|--------|---------------|
| statsmodels  | 0.14.0   | pip  | sha256-... |
| scipy        | 1.10.1   | pip  | sha256-... |

Konfigurasi:
  Config file     : config.json / .env.example
  Random seed     : 42
  Hyperparameters : alpha_threshold = 0.05, ablat_mode = "full_vs_control"

Reproducibility Check:
  [✓] Dependency terdokumentasi (requirements.txt & package.json)
  [✓] Seed ditetapkan di semua level (Python, NumPy, PostgreSQL sequence)
  [✓] Config di version control (file .env di-ignore, template .env.example masuk Git)
  [✓] README instruksi reproduksi lengkap
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment untuk eksperimen Anda (boleh environment saat ini atau yang direncanakan).

| Komponen | Spesifikasi |
|----------|------------|
| CPU | AMD Ryzen 5 5600H |
| RAM | 16 GB DDR4 |
| GPU | CPU-only (tidak memerlukan akselerasi CUDA GPU untuk regresi) |
| OS | Windows 11 64-bit |
| Runtime | Python 3.10.11 & Node.js v18.16.0 |
| Framework | Flask v2.3.2 (Python) & Express.js v4.18.2 (Node) |
| Random Seed | 42  |

**Dependencies (minimal 5):**

| Library | Version | Alasan Dibutuhkan |
|---------|---------|-------------------|
|statsmodels | 0.14.0 | Untuk kalkulasi uji Regresi Linear Berganda (melihat pengaruh X1, X2, X3, X4 secara simultan). |
|scipy | 1.10.1 | Menghitung nilai P-value dan melakukan uji-t (T-test) guna menguji hipotesis H1. |
|pandas | 2.0.2 | Membaca file .csv hasil ekspor dari komponen Survey Engine aplikasi. |
|pg (node-postgres) | 8.11.0 | Driver untuk menghubungkan modul backend aplikasi ke database PostgreSQL. |
|dotenv | 16.0.3 |Membaca file .env untuk melakukan toggle activation pada modul sistem pariwisata. |

---

## Latihan 2 — Repeatability Test Plan

Rancang tes repeatability sederhana: jalankan kode yang sama 3× di environment yang sama.

| Run | Seed | Metrik Utama | Hasil Sama? |
|-----|------|-------------|-------------|
| 1 | 42 | R-Square & P-value | — |
| 2 | 42 | R-Square & P-value | [✓] Ya / [ ] Tidak |
| 3 | 42 | R-Square & P-value | [✓] Ya / [ ] Tidak |

**Jika hasil berbeda, kemungkinan penyebab:**
> ___________________________________________________

**Checklist kontrol yang sudah diterapkan:**
- [✓] Random seed di-set di semua level
- [✓] Tidak ada background process yang mengganggu
- [✓] Cache dibersihkan antar-run
- [✓] Config file yang sama untuk semua run

---

## Latihan 3 — README Eksperimen

Tulis README minimum untuk eksperimen Anda (6 komponen wajib).

```
# Judul Eksperimen: Evaluasi Dimensi Kualitas Smart Tourism Technology Terhadap Tingkat Kepuasan Wisatawan Aplikasi Daerah (Studi Kuantitatif Berbasis Teori Lee et al., 2017)
## 1. Environment
> OS: Windows 11 / Ubuntu 22.04 LTS
  Runtime: Python 3.10.11, Node.js v18.16.0
  DB: PostgreSQL 15

## 2. Installation
> 1. Clone repositori ini ke komputer lokal.
  2. Install dependency backend aplikasi pariwisata:
     $ npm install
  3. Install dependency skrip pengolah data statistik:
     $ pip install -r requirements.txt
## 3. Data
> - Sumber: Hasil ekspor data mentah kuesioner skala       Likert teragregasi (100 sampel).
  - Format: `dataset_responses.csv`
  - Atribut: Skor rata-rata Informativeness,       Accessibility, Interactivity, Personalization, dan User Satisfaction Score.
## 4. Execution
> Untuk menjalankan pengujian regresi dan melihat signifikansi p-value, ketik command:
$ python run_regression_analysis.py

## 5. Configuration
> Pengaturan eksperimen dikontrol secara eksternal melalui file `config.json`:
{
  "alpha_threshold": 0.05,
  "random_seed": 42,
  "ablation_mode": "full_system"
}

## 6. Expected Output
> Terminal akan menampilkan hasil ringkasan statistik berupa:
- Nilai R-Square (Koefisien Determinasi)
- Nilai F-statistic dan Signifikansi F (Uji Simultan)
- Nilai P-value untuk tiap variabel (X1, X2, X3, X4) untuk pembuktian hipotesis H1.
```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?

**Level saat ini:** [✓] Repeatability / [ ] Reproducibility / [ ] Belum keduanya
**Komponen yang belum terdokumentasi:**
> Dokumentasi mengenai langkah restore dump file database awal (.sql) untuk skema tabel PostgreSQL dan seeding data awal destinasi pariwisata belum ditulis di README. Akibatnya, orang lain yang mau mencoba mereplikasi sistem ini harus membuat skema database secara manual dari nol.
