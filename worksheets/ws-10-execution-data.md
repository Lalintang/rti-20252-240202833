# WS-10: Experiment Execution & Data Collection

> **Bab 10 — Eksekusi Eksperimen & Pengumpulan Data**

---

## Ringkasan Materi

### Experiment Execution Pipeline

```
Design → Execution Plan → Controlled Execution → Data Collection → Data Logging → Dataset for Analysis
```

### Multiple Run = Non-Negotiable

Single run **tidak pernah cukup** untuk klaim ilmiah. Minimum 5-10 run per skenario dengan seed berbeda. Multiple run menghasilkan:
- Mean, std, confidence interval
- Distribusi hasil → uji statistik
- Variabilitas → error bar di grafik

### Execution Plan

Setiap eksperimen harus memiliki plan sebelum eksekusi:
- Daftar skenario
- Jumlah run per skenario
- Random seed per run (pre-determined!)
- Urutan eksekusi (randomisasi/counterbalancing)
- Pre-execution checklist

### Data Logging Komprehensif

Setiap run menghasilkan log terstruktur:
1. **Identitas** — Run ID, timestamp, skenario
2. **Konfigurasi** — Semua parameter, seed, code version
3. **Hasil** — Semua metrik, output detail
4. **Metadata** — Waktu eksekusi, resource usage, warning/error

Format: CSV/JSON/database — **bukan stdout yang di-copy-paste**.

### Engineering vs Research Execution

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Run | Sekali (deploy) | Multiple (min 5-10, seed berbeda) |
| Logging | Error log, access log | Semua parameter, metrik, metadata |
| Anomali | Bug → fix → redeploy | Investigasi → dokumentasi → analisis |
| Urutan | Tidak penting | Bisa bias — perlu randomisasi |

### Anomali = Dokumentasi, Bukan Hapus

Run gagal/anomali tidak boleh dihapus tanpa dokumentasi. Bisa jadi:
- **Bug** → fix & re-run (dokumentasikan!)
- **Batas kemampuan metode** → DNF = temuan
- **Data yang bias** jika hanya simpan run "berhasil"

### Jebakan Kognitif

1. "Satu angka cukup" → tanpa distribusi, tidak bisa diuji
2. "Seed tidak penting" → bahkan algoritma deterministik bisa dipengaruhi library stokastik
3. "Run gagal langsung hapus" → kehilangan temuan potensial
4. "Semua run harus hari ini" → thermal throttling, fatigue

---

## Template A.10 — Execution Plan & Data Log

```
EXECUTION PLAN

| Run # | Skenario | Seed | Parameter | Status | Waktu | Output File |
|-------|----------|------|-----------|--------|-------|-------------|
| 1     | Analisis Konsep Smart Tourism  |   42   |  Jurnal Smart Tourism  | Planned | 10 menit | hasil_run1.do |
| 2     | Analisis Definisi Smart Tourism |  123 |  Studi Literatur | Planned | 10 menit | hasil_run2.do |
| 3     | Analisis Komponen Smart Tourism | 456  |IoT, AI, Cloud Computing |Planned | Planned | hasil_run3.doc |
| 4     |Analisis Implementasi Smart Tourism  | 789 |Aplikasi, AR, NFC | Planned | 15 menit | hasil_run4.do  |
| 5     | Analisis Indikator Smart Tourism | 101 |Kenyamanan, Sharing, Dukungan Masyarakat | Planned | 10 menit | hasil_run5.do  |

Jumlah runs per skenario : 1
Total runs               : 5
DATA LOG (per run):
  Run ID    : run-001
  Timestamp : 23-06-2026 10:00
  Skenario  : Analisis Konsep Smart Tourism
  Input     : Jurnal "Konsep Smart Tourism sebagai Implementasi Digitalisasi di Bidang Pariwisata"
  Output    : Definisi dan konsep Smart Tourism berhasil diidentifikasi
  Anomali   : Tidak ada
  Catatan   : Data sesuai dengan tujuan penelitian
```

---

## Latihan 1 — Execution Plan

Susun execution plan untuk eksperimen Anda. Tentukan skenario, jumlah run, dan seed sebelum eksekusi.

| Run # | Skenario | Seed | Parameter Kunci | Status |
|-------|----------|------|----------------|--------|
| 1 |Analisis Jurnal Smart Tourism| 42 | Artikel Utama | Planned |
| 2 | Analisis Definisi Smart Tourism | 123 | Fokus Konsep | Planned |
| 3 |Analisis Komponen Smart Tourism |456 |IoT, AI, Cloud Computing |Planned |
| 4 |Analisis Implementasi Smart Tourism |789 |Aplikasi, AR, NFC |Planned |
| 5 |Analisis Indikator Keberhasilan |101 |Kenyamanan, Sharing, Dukungan Masyarakat |Planned |

**Total skenario:** 5
**Run per skenario:** 1
**Total run keseluruhan:** 5

---

## Latihan 2 — Data Log Terstruktur

Desain format data log untuk eksperimen Anda. Tentukan field apa saja yang akan dicatat.

**Identitas:**
| Field | Contoh |
|-------|--------|
| Run ID | run-001 |
| Timestamp |2026-06-23 10:00 |
|Skenario |Analisis Smart Tourism |

**Konfigurasi:**
| Field | Contoh |
|-------|--------|
| Seed | 42 |
|Sumber Data  | Jurnal Smart Tourism |
|Metode |Studi Literatur |

**Hasil:**
| Metrik | Tipe Data | Range Valid |
|--------|----------|-------------|
| Jumlah Komponen | Integer | > 0 |
|Jumlah Implementasi | Integer| > 0 |
|Jumlah Indikator |Integer | > 0 |

**Format output:** [☑] CSV / [☑] JSON / [ ] Database / [ ] Lainnya: ____

---

## Latihan 3 — Anomaly Protocol

Rencanakan bagaimana menangani anomali. Untuk setiap jenis, tentukan langkah yang diambil.

| Jenis Anomali | Contoh | Tindakan |
|---------------|--------|----------|
| Run gagal (crash) | File jurnal tidak dapat dibuka | Dokumentasi lalu ulangi analisis |
| Hasil ekstrem | Jumlah komponen berbeda jauh dengan literatur lain | Cek ulang sumber dan catat perbedaan |
| Waktu eksekusi anomali | Analisis lebih lama dari biasanya | Dokumentasikan penyebabnya |
| Inkonsistensi dengan run lain | Definisi berbeda antar jurnal | Bandingkan dan catat sebagai temuan |

**Prinsip:** Detect → Investigate → Document → Decide

---

## Refleksi

> Pernahkah Anda melaporkan hasil riset/tugas dari single run? Apa risikonya? Bagaimana multiple run mengubah kepercayaan terhadap hasil?

**Pengalaman sebelumnya:**
> Sebelumnya saya sering mengambil hasil hanya dari satu kali analisis atau satu sumber jurnal. Cara ini berisiko menghasilkan kesimpulan yang kurang akurat karena tidak ada pembanding dan validasi dari sumber lain.
**Yang akan dilakukan berbeda:**
> Saya akan menggunakan beberapa analisis dan membandingkan hasil dari berbagai bagian jurnal atau sumber pendukung. Dengan demikian hasil penelitian menjadi lebih valid, objektif, dan dapat dipertanggungjawabkan.