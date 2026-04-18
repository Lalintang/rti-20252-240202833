# WS-03: Literature Mapping & Gap

> **Bab 3 — Literature Review, Research Gap & Baseline**

---

## Ringkasan Materi

### Literature Review = Positioning, Bukan Ringkasan

Literature review bukan merangkum paper satu per satu. Pendekatan yang benar adalah **concept-centric** — organisasi berdasarkan tema, metode, atau variabel. Tujuan: menemukan **pola, kontradiksi, dan gap**.

### Empat Jenis Research Gap

| Jenis Gap | Deskripsi | Contoh |
|-----------|----------|--------|
| **Performance Gap** | Performa belum memadai | Akurasi deteksi hanya 78% pada kasus tertentu |
| **Method Gap** | Pendekatan belum diterapkan | Belum ada yang pakai transformer untuk task ini |
| **Data Gap** | Dataset terbatas/tidak representatif | Semua studi pakai dataset sintetis |
| **Context Gap** | Belum diuji pada konteks berbeda | Belum ada evaluasi di negara berkembang |

Gap terkuat = kombinasi 2+ jenis.

### Systematic Search Strategy

1. **Database**: IEEE Xplore, ACM DL, Scopus, Google Scholar
2. **Boolean query** yang terdokumentasi eksplisit
3. **Snowballing**: backward (telusuri referensi) + forward (cari yang mengutip)
4. Klaim "belum ada penelitian" harus didukung **bukti pencarian**

### Baseline Selection — 3 Kriteria

| Kriteria | Pertanyaan |
|----------|-----------|
| **Relevan** | Apakah menyelesaikan masalah yang sama? |
| **Representatif** | Apakah mewakili common practice? |
| **State-of-the-Art** | Apakah terbaru/terbaik? |

Membandingkan deep learning 2024 dengan decision tree sederhana tanpa justifikasi = **straw man comparison** (perbandingan tidak jujur).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan baca literatur | Mencari solusi yang sudah ada | Memahami apa yang belum terjawab |
| Cara membaca paper | Tutorial, how-to | Metode, limitasi, gap |
| Baseline | Framework terpopuler | State-of-the-art yang rigorous |
| Dokumentasi pencarian | Tidak diperlukan | Wajib (reproducible) |

### Istilah Penting

- **Concept-centric** — Organisasi literatur berdasarkan konsep/metode, bukan per penulis
- **Snowballing** — Backward (telusuri referensi) + Forward (cari yang mengutip paper kunci)
- **Research Position** — Pernyataan eksplisit posisi riset terhadap studi sebelumnya
- **Straw man comparison** — Memilih baseline lemah agar metode sendiri terlihat lebih baik

---

## Template A.3 — Literature Mapping & Gap Identification

```
LITERATURE MAPPING

Topik      : Smart Tourism berbasis teknologi
Database   : Google Scholar
Query      : "smart tourism digitalization tourism ICT"
Tahun      : 2014–2020
Hasil awal : 15 paper → Screening → 5 paper final

Literature Matrix (concept-centric):

| Study | Tahun | Method | Data | Result | Limitation |
| Hanum et al. | 2020 |Kualitatif (literature review)|Studi literatur|Smart tourism meningkatkan pengalaman wisata|Smart tourism meningkatkan pengalaman wisata|
|  Gajdosik    | 2018 |  Konseptual |   Literatur   |   Smart tourism sebagai evolusi teknologi pariwisata     |     Tidak diuji langsung        |
|  Femenia-Serra | 2019 |  Konseptual |   Literatur   |   Smart tourism meningkatkan experience     |    Fokus teori        |
|  Lee et al. | 2017  |  Model analisis     |  Data wisatawan   |  Ada dimensi teknologi smart tourism    |    Terbatas pada lokasi tertentu      |
|   Guo et al. | 2014 |  IoT approach |  Data sistem | IoT mendukung smart tourism  |  Implementasi terbatas |

Pola yang ditemukan:
  Metode dominan     : Kualitatif dan konseptual
  Dataset umum       : Studi literatur dan data terbatas
  Limitasi berulang  : Tidak ada pengujian empiris langsung
GAP IDENTIFICATION

Gap 1: [Jenis: Data Gap + Method Gap]
  Deskripsi    : Sebagian besar penelitian tentang smart tourism hanya menggunakan studi literatur dan pendekatan konseptual, tanpa didukung data empiris atau pengukuran kuantitatif secara langsung.

  Bukti        : Dari beberapa paper yang dianalisis (Hanum et al., 2020; Gajdosik, 2018; Femenia-Serra, 2019)metode yang digunakan dominan kualitatif dan tidak melakukan pengujian langsung di lapangan.

  Signifikansi : Tanpa data empiris, klaim bahwa smart tourism dapat meningkatkan pengalaman wisata masih belum kuat. Penelitian lanjutan diperlukan agar hasilnya lebih valid, terukur, dan bisa dibuktikan secara nyata.

Gap 2: [Jenis: Context Gap]
  Deskripsi    : Penerapan smart tourism belum banyak diuji pada berbagai konteks wilayah, khususnya di negara berkembang seperti Indonesia.

  Bukti        : Beberapa penelitian hanya dilakukan pada lokasi tertentu atau bersifat umum, sehingga belum mencerminkan kondisi di berbagai daerah dengan infrastruktur yang berbeda.

  Signifikansi : Perbedaan kondisi infrastruktur dan kesiapan teknologi dapat mempengaruhi keberhasilan smart tourism, sehingga penting untuk diuji di berbagai konteks agar hasilnya lebih relevan dan aplikatif.

Baseline Selection:
| Baseline | Relevansi | Representatif | Source |
|Model konseptual Smart Tourism|Membahas konsep smart tourism yang sama|Banyak digunakan dalam penelitian sebelumnya|Gajdosik (2018)|
| Model dimensi Smart Tourism Technology | Mengukur pengalaman pengguna dalam smart tourism | Digunakan untuk analisis pengalaman wisatawan |Lee et al. (2017)|
```

---

## Latihan 1 — Concept-Centric Literature Table

Gunakan topik riset dari WS-02. Cari minimal 5 paper relevan menggunakan Google Scholar atau database lain.

**Topik riset:** Smart Tourism dalam meningkatkan pengalaman wisata
**Query pencarian:** "smart tourism ICT experience tourism"
**Database:** Google Scholar
| # | Study | Tahun | Method | Dataset | Result | Limitasi |
|---|-------|-------|--------|---------|--------|----------|
| 1 |Hanum et al.|2020|Kualitatif|Literatur|Meningkatkan pengalaman wisata |Tidak empiris|
| 2 |Gajdosik |2018 |Konseptual |Literatur |Evolusi digital tourism |Tidak diuji|
| 3 |Femenia-Serra |2019 |Konseptual |Literatur |Experience meningkat |Teoritis|
| 4 |Lee et al. |2017 |Model analisis |Wisatawan |Ada dimensi teknologi |Terbatas lokasi|
| 5 |Guo et al. |2014 |IoT |Sistem |Teknologi mendukung |Implementasi terbatas|

**Pola yang terlihat — Metode dominan:** Kualitatif dan konseptual
**Limitasi yang berulang:** Kurangnya data empiris dan pengujian langsung
---

## Latihan 2 — Gap Identification

Berdasarkan tabel di Latihan 1, identifikasi gap.

| Jenis Gap | Ditemukan? | Gap Statement |
|-----------|-----------|---------------|
| Performance Gap | [ ] Ya / [✓] Tidak |-|
| Method Gap | [✓] Ya / [ ] Tidak |Belum banyak penelitian menggunakan metode kuantitatif untuk mengukur efektivitas smart tourism |
| Data Gap | [✓] Ya / [ ] Tidak |Sebagian besar penelitian hanya menggunakan studi literatur tanpa data nyata |
| Context Gap | [✓] Ya / [ ] Tidak |Belum banyak diuji di berbagai daerah, khususnya negara berkembang |

**Gap utama yang dipilih:** Data Gap + Method Gap
**Mengapa gap ini penting (bukan sekadar "belum ada yang meneliti")?**
> Karena tanpa data empiris dan metode pengukuran yang jelas, klaim bahwa smart tourism meningkatkan pengalaman wisata masih belum terbukti secara nyata. Jadi penelitian perlu dilakukan untuk memberikan bukti yang lebih kuat dan bisa diuji.
---

## Latihan 3 — Baseline Selection

Pilih 2 baseline dari literatur yang sudah dibaca.

| # | Baseline | Mengapa Relevan | Mengapa Representatif | Apakah SOTA? | Sumber |
|---|----------|----------------|----------------------|-------------|--------|
| 1 |Model konseptual smart tourism |Sama-sama membahas smart tourism |Banyak digunakan di penelitian |Bukan |Gajdosik (2018) |
| 2 |Model dimensi teknologi smart tourism |Mengukur pengalaman pengguna |Digunakan dalam studi wisatawan |Mendekati |Lee et al. (2017) |

**Apakah pemilihan baseline ini bisa dianggap straw man?** [ ] Ya / [✓] Tidak
> Justifikasi: Karena baseline yang dipilih relevan dan memang digunakan dalam penelitian sebelumnya, bukan sengaja memilih metode yang lemah.
---

## Refleksi

> Apa perbedaan antara "belum ada yang meneliti ini" (klaim tanpa bukti) dengan research gap yang valid? Bagaimana cara membuktikan bahwa sebuah gap benar-benar ada?

**Jawaban:**
> Klaim “belum ada yang meneliti ini” biasanya hanya asumsi tanpa bukti yang jelas. Sedangkan research gap yang valid harus didukung dari hasil membaca beberapa penelitian sebelumnya dan menemukan pola atau kekurangan yang sama.
> Cara membuktikan gap itu ada adalah dengan melakukan pencarian literatur secara sistematis, membandingkan beberapa paper, lalu menunjukkan bagian mana yang belum diteliti atau masih memiliki keterbatasan.
