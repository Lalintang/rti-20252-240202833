# WS-02: Problem Statement

> **Bab 2 — Problem Formulation & System Context**

---

## Ringkasan Materi

### Problem Formation Model

Masalah riset melewati 5 tahap transformasi. Melompat langsung dari Reality ke Variable adalah kesalahan paling umum.

```
Reality → Observed Issue (Symptom) → Diagnosed Problem (Root Cause)
→ Researchable Problem (Scoped) → Measurable Variable (Operationalized)
```

### Topic ≠ Problem ≠ Research Problem

| Level | Contoh | Status |
|-------|--------|--------|
| **Topik** | Keamanan IoT | Terlalu luas, tidak bisa diuji |
| **Problem** | MQTT tidak terenkripsi | Spesifik tapi belum riset |
| **Research Problem** | Belum ada studi membandingkan overhead TLS 1.3 vs DTLS pada MQTT di IoT RAM < 64KB | Bisa dirancang eksperimennya |

### Symptom vs Root Cause

Apa yang diamati (gejala) ≠ mengapa terjadi (akar masalah). Gunakan **5 Whys** atau **Fishbone Diagram** untuk menggali.

Contoh: "User meninggalkan checkout" (symptom) → "Waktu loading > 8 detik karena API call sequential" (root cause).

### System Thinking

Setiap masalah riset TI harus terikat pada komponen sistem: **Input → Process → Output → Outcome → Constraints → Stakeholders**.

### Problem Quality Check

Masalah riset yang layak harus memenuhi 5 kriteria:
- **Clarity** — Satu orang membaca akan paham
- **Measurability** — Ada metrik kuantitatif
- **Relevance** — Penting untuk domain
- **Testability** — Bisa gagal (falsifiable)
- **Impact** — Ada kontribusi jika terjawab

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Menyelesaikan masalah (*solve*) | Memahami dan membuktikan (*understand & prove*) |
| Masalah | Bug, error, fitur belum ada | Gap dalam pengetahuan |
| Scope | Selesaikan semua yang perlu | Batasi agar bisa dibuktikan |
| Output | Working system | Evidence, paper, replicable findings |

### Istilah Penting

- **Problem Statement** — Formulasi tertulis: konteks sistem + gap + dampak + justifikasi
- **System Context** — Deskripsi lengkap: input, proses, output, outcome, constraints, stakeholders
- **Problem Drift** — Masalah "bermutasi" dari pendahuluan ke metodologi karena statement awal tidak presisi
- **Solution-First Thinking** — Memulai dari solusi tanpa masalah yang jelas — berbahaya dalam riset
- **Operational Definition** — Definisi variabel yang cukup jelas agar peneliti lain bisa mengukur hal yang sama

---

## Template A.2 — Problem Statement Builder

```
PROBLEM STATEMENT BUILDER

Domain & Konteks
  Domain   : Teknologi Informasi (Pariwisata Digital)
  Konteks  : Penerapan smart tourism dalam meningkatkan pengalaman wisata

System Context
  Input       : Data wisata, informasi destinasi, teknologi (aplikasi, IoT, dll)
  Process     : Pengolahan data dan penyajian informasi melalui sistem smart tourism
  Output      : Informasi wisata yang mudah diakses pengguna
  Outcome     : Meningkatnya pengalaman dan kepuasan wisatawan
  Constraints : Keterbatasan infrastruktur, jaringan, dan kesiapan teknologi
  Stakeholders: Wisatawan, pemerintah, pelaku industri pariwisata

Fenomena → Problem
  Fenomena yang diamati             : Perkembangan teknologi mendorong digitalisasi di bidang pariwisata
  Gejala (symptom) yang terukur     : Banyak sistem smart tourism belum optimal dan belum merata
  Masalah yang didiagnosis          : Kurangnya pemahaman dan penerapan teknologi secara efektif
  Masalah riset (researchable)      : Belum ada evaluasi yang jelas terkait efektivitas smart tourism dalam meningkatkan pengalaman wisata
  Variabel yang terukur             : Tingkat kepuasan pengguna, kemudahan akses, dan kualitas informasi

Problem Quality Check
  [✓] Clarity — Apakah satu orang membaca akan paham?
  [✓] Measurability — Apakah ada metrik kuantitatif?
  [✓] Relevance — Apakah penting untuk domain?
  [✓] Testability — Apakah bisa gagal?
  [✓] Impact — Apakah ada kontribusi jika terjawab?

Problem Statement (1 paragraf): Perkembangan teknologi informasi mendorong penerapan konsep smart tourism dalam bidang pariwisata untuk meningkatkan pengalaman wisatawan. Namun, penerapan tersebut belum sepenuhnya optimal dan belum merata di berbagai daerah. Hal ini disebabkan oleh kurangnya evaluasi yang jelas terhadap efektivitas penggunaan teknologi dalam smart tourism. Oleh karena itu, diperlukan penelitian untuk mengukur sejauh mana penerapan smart tourism dapat meningkatkan kepuasan dan pengalaman wisatawan berdasarkan variabel seperti kemudahan akses, kualitas informasi, dan tingkat kepuasan pengguna.

```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Smart Tourism

| Tahap | Hasil |
|-------|-------|
| Reality | Perkembangan teknologi digunakan dalam sektor pariwisata |
| Observed Issue (Symptom) | Penerapan smart tourism belum merata dan belum optimal |
| Diagnosed Problem (Root Cause) | Kurangnya evaluasi dan pengukuran efektivitas teknologi |
| Researchable Problem | Bagaimana pengaruh smart tourism terhadap pengalaman wisatawan |
| Measurable Variable | Kepuasan pengguna, kemudahan akses, kualitas layanan |

**Apakah terjebak solution-first thinking?** [ ] Ya / [✓] Tidak
> Jika ya, kembali ke tahap mana? Karena dimulai dari fenomena dulu, bukan langsung solusi
---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Data destinasi wisata, informasi pengguna |
| Process | Pengolahan data melalui aplikasi atau sistem smart tourism |
| Output | Informasi wisata yang akurat dan mudah diakses |
| Outcome | Peningkatan pengalaman dan kepuasan wisatawan |
| Constraints | Infrastruktur teknologi terbatas, jaringan internet |
| Stakeholders | Wisatawan, pemerintah, pelaku usaha |

**Komponen mana yang paling relevan dengan masalah riset?** Process dan Outcome

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 4 | Sudah jelas tapi masih bisa dipersempit lagi |
| Measurability | 4 | Ada variabel, tapi belum detail metode ukurnya |
| Relevance | 5 | Sangat penting di bidang pariwisata digital |
| Testability | 4 | Bisa diuji, tapi perlu desain eksperimen |
| Impact | 5 | Berdampak pada peningkatan kualitas pariwisata |

**Skor total:** 22 / 25

**Problem statement versi final (1 paragraf):**
> Penerapan smart tourism sebagai bentuk digitalisasi dalam bidang pariwisata bertujuan untuk meningkatkan pengalaman wisatawan melalui pemanfaatan teknologi informasi. Namun, implementasi smart tourism saat ini belum optimal dan belum merata, sehingga efektivitasnya masih belum dapat diukur secara jelas. Oleh karena itu, diperlukan penelitian untuk menganalisis pengaruh penerapan smart tourism terhadap kepuasan dan pengalaman wisatawan dengan menggunakan variabel yang terukur seperti kemudahan akses, kualitas informasi, dan tingkat kepuasan pengguna.
> 
---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
> Masalah saat coding biasanya berupa bug atau error yang jelas terlihat, misalnya program tidak jalan atau output salah. Jadi pendekatannya langsung ke solusi, yaitu mencari letak kesalahan lalu memperbaikinya supaya sistem bisa berjalan dengan benar.
> Sedangkan masalah riset tidak selalu terlihat secara langsung, tapi harus dicari dulu akar masalahnya dari suatu fenomena. Dalam riset, masalah harus didefinisikan dengan jelas, punya variabel yang bisa diukur, dan harus bisa diuji benar atau salah. Pendekatannya juga lebih sistematis dan tidak langsung ke solusi, tapi fokus ke memahami dan membuktikan masalah tersebut.
