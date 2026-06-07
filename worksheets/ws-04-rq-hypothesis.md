# WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : Kurangnya data empiris dan metode kuantitatif dalam mengukur efektivitas smart tourism.

Research Question:
  Tipe         : [ ] Comparison  [ ] Improvement  [✓] Exploratory
  Formulasi    : Apakah penerapan smart tourism berpengaruh terhadap peningkatan pengalaman wisatawan berdasarkan tingkat kepuasan, kemudahan akses, dan kualitas informasi?
  Variabel IV  : Penerapan smart tourism
  Variabel DV  : Pengalaman wisatawan
  Metrik       : Skor kepuasan, kemudahan akses, kualitas informasi (skala likert)
  Dataset      : Data survei wisatawan
  Baseline     : Kondisi pariwisata tanpa smart tourism
Quality Check RQ:
  [✓] Variabel spesifik
  [✓] Metrik jelas
  [✓] Baseline ada
  [✓] Konteks disebutkan
  [✓] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:
  Apa yang baru diketahui : Adanya bukti empiris mengenai pengaruh smart tourism terhadap pengalaman wisatawan
  Jenis kontribusi        : [✓] Improvement  [ ] Comparison  [ ] Novel approach
  Gap yang diisi          : Data gap dan method gap terkait kurangnya pengukuran kuantitatif

Hypothesis Pair:
  H₀ : Tidak ada pengaruh signifikan dari dimensi Smart Tourism Technology terhadap tingkat kepuasan pengalaman wisatawan
  H₁ : Terdapat pengaruh positif dan signifikan dari setidaknya satu dimensi Smart Tourism Technology terhadap peningkatan pengalaman wisatawan
  Threshold              : P-value < 0,05
  Justifikasi threshold  : Batas standar signifikansi statistik yang umum digunakan dalam penelitian kuantitatif ilmu sosial untuk menolak H₀
```

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. 
**Gap dari WS-03:** Kurangnya data empiris dan pengukuran kuantitatif pada smart tourism.

**RQ versi pertama (tulis bebas):**
> Bagaimana pengaruh smart tourism terhadap pengalaman wisatawan?

**Evaluasi RQ:**

| Komponen | Ada? | Isi |
|----------|------|-----|
| Metode spesifik | Ya | Analisis pengaruh dimensi Smart Tourism Technology (STT). |
| Metrik terukur | Ya | Skor Likert (1-5) pada dimensi Informativeness, Accessibility, Interactivity, dan Personalization. |
| Baseline | Ya | Kondisi wisatawan tanpa dukungan alat smart tourism. |
| Dataset/konteks | Ya | Data kuesioner dari wisatawan di destinasi digital. |

**Tipe RQ:** [ ] Comparison / [ ] Improvement / [✓] Exploratory

**RQ versi revisi (setelah evaluasi):**
> Apakah dimensi Smart Tourism Technology (Informativeness, Accessibility, Interactivity, Personalization) berpengaruh secara signifikan terhadap peningkatan pengalaman wisatawan (skor kepuasan) di destinasi wisata digital?

---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen | Isi |
|----------|-----|
| H₀ | Tidak ada pengaruh signifikan dari dimensi Smart Tourism Technology terhadap tingkat kepuasan pengalaman wisatawan |
| H₁ | Terdapat pengaruh positif dan signifikan dari setidaknya satu dimensi Smart Tourism Technology terhadap peningkatan pengalaman wisatawan |
| Metrik | Skor rata-rata variabel kepuasan (DV) dan variabel STT (IV) |
| Threshold | P-value < 0,05 |
| Justifikasi threshold | Batas standar signifikansi statistik untuk menolak H₀ dalam penelitian kuantitatif sosial |

**Apakah hipotesis ini falsifiable?** [✓] Ya / [ ] Tidak
> Bagaimana cara membuktikannya salah? Jika hasil uji regresi atau korelasi menunjukkan nilai p > 0,05, maka hipotesis H₁ ditolak, yang berarti teknologi tersebut tidak terbukti efektif memperbaiki pengalaman wisatawan secara nyata.
---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap | Isi |
|-------|-----|
| RQ | Apakah STT (Informativeness, Accessibility, Interactivity, Personalization) meningkatkan pengalaman wisatawan? |
| Variable (IV) | Dimensi Smart Tourism Technology (STT) |
| Variable (DV) | Pengalaman wisatawan (Tingkat Kepuasan) |
| Metric | Skala Likert 1-5 (Sangat Tidak Setuju s.d Sangat Setuju) |
| Data source | Survei/Kuesioner dari wisatawan pengguna aplikasi wisata digital |
| Analysis method | Regresi Linear Berganda (untuk melihat pengaruh tiap variabel IV ke DV) |

**Apakah rantai lengkap?** [✓] Ya / [ ] Tidak
> Jika tidak, tahap mana yang perlu direvisi?

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** KONSEP SMART TOURISM SEBAGAI IMPLEMENTASI DIGITALISASI DI BIDANG PARIWISATA
**RQ yang diekstrak:** Bagaimana konsep smart tourism tersebut dan bagaimana bentuk pemanfaatannya dalam bidang pariwisata?
**Komponen yang hilang:** Q dalam paper tersebut masih bersifat sangat umum/deskriptif (Engineering-style). Komponen yang hilang adalah metrik terukur, variabel DV yang spesifik, dan pengujian hipotesis karena paper tersebut menggunakan metode kualitatif deskriptif (hanya studi literatur).
