# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (artefak dibuat sebagai instrumen pengujian hipotesis, bukan tujuan akhir).

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : Egalian Lalintang
Tanggal          : 16 April 2026

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: Akurasi 95% itu dihitung pakai dataset apa? dan apakah datanya seimbang atau tidak?
   - Data yang dibutuhkan untuk verifikasi: Dataset yang digunakan, metode pengujian (train-test atau cross validation),serta perbandingan dengan metode lain sebagai baseline.

2. Posisi paradigma:
   - Pendekatan: [ ] Positivis  [ ] Interpretivis  [✓] Design Science  [ ] Mixed
   - Alasan: Karena penelitian membahas penerapan teknologi (smart tourism) sebagai solusi,jadi lebih fokus ke pembangunan konsep/artefak dan pemanfaatannya, bukan hanya uji hipotesis saja.

3. Identifikasi distorsi:
   - Asumsi tersembunyi: Smart tourism dianggap selalu memberikan dampak positif bagi semua pihak.
   - Sumber bias potensial: Data hanya berasal dari studi literatur tanpa data lapangan, jadi bisa bias dari penulis sebelumnya.
   - Langkah mitigasi: Menambahkan data empiris (observasi atau survey), serta membandingkan dengan kondisi nyata di lapangan.

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Semua data hasil penelitian dan referensi jurnal yang digunakan.
   - Batasan yang diakui sejak awal: Penelitian hanya berdasarkan studi literatur, sehingga hasilnya belum tentu bisa digeneralisasi ke semua kondisi.
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

**Paper yang dipilih:**
> Judul: Konsep Smart Tourism sebagai Implementasi Digitalisasi di Bidang Pariwisata
> Penulis (Tahun): Fauziah Hanum dkk. (2020)

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | Peneliti mengambil data dari berbagai jurnal (studi literatur) tentang smart tourism | Data tidak langsung dari lapangan → bisa tidak merepresentasikan kondisi nyata |
| Data → Processing | Data dari berbagai sumber dikumpulkan dan dirangkum | Pemilihan sumber bisa bias (hanya ambil yang mendukung) |
| Processing → Analysis | Data dianalisis secara deskriptif untuk menjelaskan konsep smart tourism | Tidak ada analisis kuantitatif → rawan subjektivitas |
| Analysis → Inference | Disimpulkan bahwa smart tourism adalah solusi terbaik untuk pariwisata | Generalisasi terlalu luas tanpa pembuktian eksperimen |
| Inference → Knowledge | Dihasilkan pengetahuan bahwa smart tourism meningkatkan pengalaman dan daya saing | Klaim belum tentu berlaku di semua kondisi (external validity lemah) |

**Distorsi paling besar di tahap:** Processing → Analysis

**Dua distorsi spesifik yang teridentifikasi:**
1. Bias sumber (literature bias)
Peneliti hanya menggunakan studi literatur tanpa validasi langsung ke lapangan, jadi bisa aja referensinya cuma yang mendukung konsep smart tourism.
2. Overgeneralization (generalisasi berlebihan)
Kesimpulan bilang smart tourism adalah “solusi terbaik”, padahal tidak diuji secara empiris di semua kondisi atau daerah.

---

## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah | Data outlier tidak boleh langsung dihapus hanya supaya hasil signifikan. Harus dilaporkan dua-duanya (pakai dan tanpa outlier). |
| Transparansi | Peneliti wajib menjelaskan kenapa data outlier dihapus atau tidak, termasuk dampaknya ke hasil penelitian. |
| Peer review | Reviewer biasanya akan mempertanyakan alasan penghapusan data, jadi harus ada justifikasi yang jelas dan logis. |

**Keputusan akhir dan justifikasi:**
> Data tetap dilaporkan secara lengkap (dengan dan tanpa outlier), karena menghapus data tanpa alasan kuat bisa dianggap manipulasi. Kalau outlier dihapus, harus ada alasan yang jelas (misalnya error pengukuran), bukan karena ingin hasilnya signifikan.
---

## Latihan 3 — Posisi Paradigma

**Topik riset:** Penerapan Smart Tourism berbasis teknologi dalam meningkatkan pengalaman wisata

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | 3 — bisa dipakai kalau mau uji data | 2 — kurang fokus ke makna | 5 — paling cocok karena membahas penerapan teknologi |
| Jenis data yang dikumpulkan | Data numerik, statistik wisatawan | Wawancara, pengalaman pengguna | Hasil implementasi sistem, fitur teknologi |
| Limitasi paradigma | Butuh data kuantitatif yang jelas | Cenderung subjektif | Kadang kurang kuat di pembuktian empiris |

**Paradigma yang dipilih:** Design Science
**Alasan:** Karena penelitian ini lebih fokus pada konsep dan penerapan teknologi (smart tourism) sebagai solusi, jadi lebih cocok ke design science yang menekankan pembangunan dan pemanfaatan sistem/konsep.

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?

**Jawaban:**
> Sebelum membaca materi ini, biasanya saya langsung percaya kalau ada klaim seperti “akurasi 95%” tanpa mikir panjang. Tapi setelah memahami adanya kemungkinan distorsi, sekarang saya jadi lebih kritis.
> Pertanyaan yang akan saya ajukan misalnya: datanya dari mana, apakah metode pengujiannya benar, apakah hasilnya bisa diterapkan di kondisi lain, dan apakah ada bias dalam penelitian tersebut.

