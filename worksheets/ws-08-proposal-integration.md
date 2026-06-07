# WS-08: Proposal Integration (UTS)

> **Bab 8 — Proposal & Checkpoint**

---

## Ringkasan Materi

### Proposal = Satu Argumen Utuh

Proposal riset bukan kumpulan bab yang independen. Ia adalah **satu argumen** yang mengalir dari masalah ke rencana solusi. Jika satu koneksi putus, seluruh proposal kehilangan koherensi.

### Integration Map — 6 Koneksi Kritis

```
Problem (Bab 2) → Gap (Bab 3) → RQ & H (Bab 4) → Metrik (Bab 5) → Sistem (Bab 6) → Eksperimen (Bab 7)
```

| Koneksi | Pertanyaan Verifikasi |
|---------|----------------------|
| Problem → Gap | Apakah gap muncul dari analisis literatur terhadap masalah? |
| Gap → RQ | Apakah RQ langsung menjawab gap yang teridentifikasi? |
| RQ → Metrik | Apakah setiap variabel di RQ punya metrik terdefinisi? |
| Metrik → Sistem | Apakah setiap metrik bisa diukur oleh komponen sistem? |
| Sistem → Eksperimen | Apakah desain eksperimen menggunakan sistem sebagai instrumen? |

### Koherensi Vertikal + Horizontal

- **Vertikal** — Alur logis atas-ke-bawah (problem → experiment)
- **Horizontal** — Konsistensi terminologi (nama variabel di RQ = di hipotesis = di metrik = di desain)

### Jebakan Kognitif

| Jebakan | Deskripsi |
|---------|----------|
| "Selling" Introduction | Menulis promosi, bukan menyajikan data dan gap |
| Copy-paste Methodology | Menyalin deskripsi tekstbook tanpa menyesuaikan ke RQ |
| Optimistic Timeline | Meremehkan waktu implementasi; selalu tambah buffer 30-50% |
| No Possibility of Failure | Mengimplikasikan hasil pasti sukses — proposal jujur mengakui H₀ mungkin tidak ditolak |

### Struktur Proposal

1. **Pendahuluan** — Latar belakang + problem statement (Bab 1-2)
2. **Tinjauan Pustaka** — Literature review + gap + baseline (Bab 3)
3. **RQ / Kontribusi / Hipotesis** — (Bab 4)
4. **Metodologi** — Metrik + sistem + desain eksperimen (Bab 5-7)
5. **Timeline & Output**

### Istilah Penting

- **Integration Map** — Diagram 6 koneksi kritis antar komponen proposal
- **Vertical Coherence** — Alur logis atas-ke-bawah
- **Horizontal Coherence** — Konsistensi terminologi di semua bagian
- **Checkpoint** — Titik self-assessment sebelum transisi dari desain ke eksekusi

---

## Template A.8 — Integration Checklist

```
PROPOSAL INTEGRATION CHECKLIST

Koneksi Vertikal (Flow Atas-Bawah):
  [✓] Problem → Gap: Masalah rendahnya kepuasan pengguna aplikasi pariwisata daerah di Bab 2 divalidasi oleh analisis literatur Bab 3 yang mengungkap kelangkaan metode evaluasi fitur teknis secara terisolasi di tingkat lokal.
  [✓] Gap → RQ: RQ secara spesifik mempertanyakan kekuatan pengaruh dari dimensi kualitas fitur teknis (Informativeness, Accessibility, Interactivity) yang diidentifikasi sebagai method gap pada Bab 3.
  [✓] RQ → Hypothesis: Hipotesis H₁ secara langsung memprediksi arah hubungan positif dan signifikansi statistik dari dimensi-dimensi sistem (IV) yang dipertanyakan di dalam RQ terhadap tingkat kepuasan (DV).
  [✓] Hypothesis → Metric: Variabel dalam hipotesis diturunkan menjadi skor indeks Interval (kalkulasi rata-rata skor indikator Likert) dengan batas threshold signifikansi uji statistik P-value < 0,05.
  [✓] Metric → System: Indikator Accessibility diukur lewat modul LBS/Peta, Informativeness lewat modul detail info, Interactivity lewat fitur feedback/chat, dan skor kepuasan ditampung langsung oleh komponen Survey Engine.
  [✓] System → Experiment: Arsitektur modular sistem yang berbasis configuration-driven (toggle file config.json) digunakan sebagai instrumen pengkondisian subjek ke dalam Control Group dan Treatment Group.

Koneksi Horizontal (Konsistensi):
  [✓] Istilah sama di semua bagian
  [✓] Variabel di RQ = variabel di hipotesis = metrik di desain
  [✓] Scope tidak berubah dari masalah ke eksperimen

Rubrik Self-Assessment:
| Kriteria | 1 (Lemah) | 2 (Cukup) | 3 (Baik) | Skor |
|----------|-----------|-----------|----------|------|
| Koherensi |          |           |    ✓      |   3   |
| Specificity |        |           |    ✓      |   3   |
| Feasibility |        |     ✓     |           |   2   |
| Rigor     |          |           |    ✓      |   3   |
```

---

## Latihan 1 — Kompilasi Proposal Mini

Kumpulkan hasil dari WS-02 sampai WS-07 menjadi satu ringkasan proposal.

| Komponen | Sumber | Isi (1-2 kalimat) |
|----------|--------|-------------------|
| Problem Statement | WS-02 | Pemanfaatan platform smart tourism pariwisata daerah saat ini belum optimal karena sering menyajikan data yang tidak mutakhir serta antarmuka yang membingungkan, sehingga mengakibatkan rendahnya tingkat adopsi dan kepuasan pengguna. |
| Gap | WS-03 | Evaluasi smart tourism saat ini masih dominan menggunakan kuesioner persepsi visual (UX) secara makro pada smart city, serta belum ada penelitian berbasis controlled experiment yang mengukur dampak fitur teknis (Informativeness, Accessibility, Interactivity) secara terisolasi pada aplikasi daerah. |
| RQ | WS-04 | Apakah dimensi kualitas sistem pada Smart Tourism Technology (Informativeness, Accessibility, Interactivity) berpengaruh secara positif dan signifikan terhadap tingkat kepuasan pengguna (User Satisfaction Score) platform pariwisata daerah? |
| Hipotesis | WS-04 | H₀: Dimensi Informativeness, Accessibility, dan Interactivity tidak memiliki pengaruh positif dan signifikan terhadap kepuasan pengguna. H₁: Setidaknya ada satu dimensi dari Smart Tourism Technology yang berpengaruh positif dan signifikan terhadap kepuasan pengguna. |
| Variabel & Metrik | WS-05 | IV: Skor indeks Informativeness (X1), Accessibility (X2), dan Interactivity (X3). DV: User Satisfaction Score (Y). Seluruhnya diukur lewat skala Likert teragregasi (data Interval). |
| Sistem | WS-06 | Aplikasi panduan wisata digital daerah berbasis configuration-driven execution, di mana modul fitur (Location-Based Service, Chatbot, dan Detail Info) dapat di-toggle On/Off via config.json untuk isolasi variabel. |
| Desain Eksperimen | WS-07 | Controlled Comparison Study yang membagi responden menjadi Control Group (aplikasi dengan fitur standar/minimalis) dan Treatment Group (aplikasi dengan fitur penuh) menggunakan analisis uji Regresi Linear Berganda dan T-test pada alpha = 0,05. |

---

## Latihan 2 — Integration Checklist

Verifikasi 6 koneksi kritis. Isi dengan merujuk tabel di Latihan 1.

| Koneksi | Status | Bukti |
|---------|--------|-------|
| Problem → Gap | ✅ | Masalah operasional aplikasi pariwisata daerah yang tidak optimal di Bab 2 divalidasi oleh analisis literatur Bab 3 yang menunjukkan adanya kelangkaan metode evaluasi fitur teknis di tingkat daerah. |
| Gap → RQ | ✅ | RQ secara spesifik mempertanyakan pengaruh dari dimensi fitur teknis (Informativeness, Accessibility, Interactivity) yang diidentifikasi sebagai method gap pada Bab 3. |
| RQ → Hypothesis | ✅ | Hipotesis H1 memprediksi arah hubungan positif dan signifikansi statistik dari variabel-variabel (X) yang dipertanyakan di dalam RQ terhadap variabel kepuasan (Y). |
| Hypothesis → Metric | ✅ | Variabel dalam hipotesis diturunkan langsung menjadi skor indeks Interval (kalkulasi rata-rata skor indikator Likert) dengan batas threshold signifikansi P-value < 0,05. |
| Metric → System | ✅ | Indikator Accessibility diukur lewat modul peta, Informativeness lewat modul detail data, dan skor kepuasan diolah otomatis oleh komponen Feedback Engine di database. |
| System → Experiment | ✅ | Arsitektur modular sistem yang berbasis configuration-driven digunakan sebagai instrumen pengkondisian subjek ke dalam kelompok Control dan Treatment. |

**Koneksi mana yang paling lemah?** Koneksi Metric → System pada pengumpulan variabel kontrol.
**Bagaimana cara memperkuatnya?**
> Dengan menambahkan modul Event Logger otomatis pada source code aplikasi untuk mencatat data demografi dan log durasi akses pengguna secara presisi, bukan cuma mengandalkan input manual kuesioner.
**Konsistensi horizontal — apakah istilah dan scope konsisten?** [✓] Ya / [ ] Tidak
> Jika tidak, di bagian mana terjadi inkonsistensi? 


---

## Latihan 3 — Rubrik Self-Assessment

Evaluasi proposal mini menggunakan rubrik.

| Kriteria | Skor (1-3) | Justifikasi |
|----------|-----------|-------------|
| Koherensi | 3 | Alur argumen sangat runtut. Eksperimen di Bab 7 terbukti merupakan alat uji yang valid untuk menjawab RQ di Bab 4 guna menyelesaikan masalah di Bab 2. |
| Specificity | 3 | Metrik sudah didefinisikan secara operasional menggunakan data skala Interval, nilai alpha = 0,05, dan pengujian statistik parametrik yang jelas. |
| Feasibility | 2 | Sangat mungkin dikerjakan dalam satu semester, namun tantangannya ada pada mobilisasi 100+ responden umum di luar kampus agar sampelnya adil (fair). |
| Rigor | 3 | Desain eksperimen sudah mengantisipasi threats to validity (seperti Hawthorne effect dan selection bias) serta menyediakan fairness checklist yang ketat. |

**Skor total:** 11 / 12

**Apakah proposal siap untuk fase eksekusi?** [✓] Ya / [ ] Belum
> Jika belum, apa yang perlu diperbaiki? 

---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-08, bagian mana yang paling mudah dan paling sulit? Mengapa? Apa yang akan dilakukan berbeda jika mengulang dari awal?

**Bagian termudah:** WS-02 (Problem Statement) dan WS-06 (System Mapping). Karena mendeskripsikan masalah aplikasi di lapangan dan merancang komponen modul sistem adalah makanan sehari-hari mahasiswa informatika saat melakukan coding atau analisis sistem.
**Bagian tersulit:** WS-03 (Literature Gap) dan WS-07 (Experimental Validity). Karena sulit untuk mencari paper SOTA terbaru yang benar-benar pas, serta mengubah mindset dari yang biasanya sekadar "bikin aplikasi sampai jalan" menjadi "mengisolasi fitur sistem demi validitas ilmiah agar tidak terjadi confounding variables".
**Yang akan dilakukan berbeda:**
> Melakukan Screening Paper SOTA di Awal Sebelum Coding Sistem.
aya akan mengunci pencarian literatur (3 tahun terakhir) sebelum menyentuh arsitektur aplikasi. Tujuannya agar modul sistem yang dibangun sejak awal sudah memiliki landasan sitasi yang kuat. Ini mencegah bongkar-pasang kode di tengah jalan akibat variabel kuesioner yang tidak sinkron dengan teori acuan.
> Merancang Komponen Event Logger Otomatis Sejak Awal Desain Database.
Saya akan mengintegrasikan skrip pelacakan aktivitas (clickstream analytics) ke dalam skema database dari hari pertama. Dengan begitu, data kontrol seperti durasi akses dan intensitas klik pengguna dapat direkam secara objektif oleh sistem, sehingga tidak hanya bergantung pada data subjektif kuesioner manual.
