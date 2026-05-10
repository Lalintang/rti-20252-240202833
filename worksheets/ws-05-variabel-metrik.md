# WS-05: Variabel & Metrik

> **Bab 5 — Metric, Measurement & Data**

---

## Ringkasan Materi

### Measurement Alignment Model

Setiap pengukuran yang valid harus bisa ditelusuri melalui rantai ini tanpa lompatan logis:

```
Problem → Concept → Variable → Metric → Data → Result
```

### Operationalization = Keputusan Desain

Menerjemahkan konsep abstrak menjadi variabel terukur bukan proses mekanis. "Code quality" yang diukur via SonarQube code smells membawa asumsi implisit. Setiap operasionalisasi harus didokumentasikan dan dijustifikasi.

### Empat Tipe Data (NOIR)

| Tipe | Ciri | Contoh | Operasi Valid |
|------|------|--------|---------------|
| **Nominal** | Kategori, tanpa urutan | Jenis algoritma (RF, SVM, CNN) | Modus, chi-square |
| **Ordinal** | Urutan, interval tidak sama | Skala Likert (1-5) | Median, Spearman |
| **Interval** | Jarak bermakna, tanpa nol absolut | Suhu Celsius | Mean, Pearson, t-test |
| **Ratio** | Jarak bermakna + nol absolut | Waktu eksekusi (ms) | Semua operasi |

Tipe data menentukan uji statistik yang valid. Kebanyakan metrik performa TI = ratio; persepsi pengguna = ordinal.

### Kriteria Pemilihan Metrik

- **Representative** — Mewakili konsep yang diteliti
- **Sensitive** — Cukup peka menangkap perbedaan bermakna (hindari ceiling effect)
- **Feasible** — Bisa dikumpulkan dalam batasan waktu dan biaya

### Pre-registration

Metrik harus ditentukan **sebelum** eksperimen. Memilih metrik setelah melihat data = **p-hacking**. Metrik tambahan yang ditemukan kemudian dilaporkan sebagai *exploratory*, bukan *confirmatory*.

### Primary vs Secondary Metric

- **Primary Metric** — Langsung terikat ke hipotesis, menentukan kesimpulan
- **Secondary Metric** — Pendukung, dilaporkan di samping primary; statusnya suplementer

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Pemilihan metrik | Berdasarkan kebiasaan/tool yang ada | Berdasarkan construct validity |
| Anomali | Dihapus untuk laporan bersih | Diinvestigasi — bisa jadi temuan |
| Kapan dipilih | Setelah sistem jadi (monitoring) | Sebelum eksperimen (by design) |

### Istilah Penting

- **Operationalization** — Transformasi konsep abstrak menjadi variabel terukur
- **Construct Validity** — Sejauh mana pengukuran benar-benar mengukur konsep yang dimaksud
- **Measurement Scale** — Klasifikasi data (NOIR) yang menentukan analisis valid
- **Multi-metric Evaluation** — Menggunakan beberapa metrik untuk menangkap konsep kompleks

---

## Template A.5 — Definisi Variabel, Metrik & Justifikasi

```
VARIABLE & METRIC DEFINITION

Research Question: Apakah dimensi Smart Tourism Technology (Informativeness, Accessibility, Interactivity, Personalization) berpengaruh secara signifikan terhadap peningkatan pengalaman wisatawan (skor kepuasan) di destinasi wisata digital?

| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
|Smart Tourism Tech (STT)    | IV   |Kualitas layanan teknologi digital pariwisata|Rata-rata skor dimensi STT|Ordinal|Skor (1-5)|Kuesioner dengan skala Likert 5 poin|Standar pengukuran kualitas sistem informasi (Delone & McLean)|
|Kepuasan Wisatawan          | DV   |Respon afektif setelah menggunakan layanan|Skor kepuasan keseluruhan|Ordinal|Skor (1-5)|Kuesioner pasca-kunjungan|Metrik psikometrik standar dalam riset perilaku konsumen|
|Frekuensi Kunjungan         | CV   |Tingkat keakraban dengan destinasi|Jumlah kunjungan dalam 1 tahun terakhir|Ratio|Kali|Pertanyaan demografi kuesioner|Pengalaman masa lalu dapat membiaskan persepsi terhadap teknologi baru|

Alignment Check:
  RQ → Concept → Variable → Metric → Data → Result
  [✓] Setiap langkah terdokumentasi
  [✓] Tidak ada "lompatan logis"
  [✓] Metrik mengukur apa yang dimaksud (construct validity)
```

---

## Latihan 1 — Operationalization Chain

Gunakan RQ dari WS-04. Definisikan variabel dan metriknya.

**RQ:** Apakah STT berpengaruh secara signifikan terhadap peningkatan pengalaman wisatawan (skor kepuasan) di destinasi wisata digital?
| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|---------------|----------------|-------------|--------|
|Dimensi STT | IV | Kualitas Informasi & Akses | Skor rata-rata 4 dimensi STT | Ordinal | Skor |
|Pengalaman Wisata | DV |Kepuasan Pengguna |Skor Indeks Kepuasan |Ordinal |Skor |
|Usia Wisatawan | CV |Literasi Digital |Kelompok umur |Ordinal |Tahun (Range) |

**Apakah ada lompatan logis dalam rantai?** [ ] Ya / [✓] Tidak
> Jika ya, di mana? 

---

## Latihan 2 — Evaluasi Metrik

Evaluasi metrik DV yang dipilih di Latihan 1 menggunakan 3 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Representative | 5 | Skala Likert secara luas diterima untuk mewakili persepsi subyektif manusia terhadap layanan digital. |
| Sensitive | 3 | Skala 1-5 terkadang kurang sensitif (responden cenderung pilih tengah). Skala 1-7 atau 1-10 bisa lebih peka. |
| Feasible | 5 | Sangat mudah dikumpulkan melalui survei online dan cepat diisi oleh responden. |

**Apakah perlu secondary metric?** [✓] Ya / [ ] Tidak
> Jika ya, apa dan mengapa? Perlu metrik "Net Promoter Score (NPS)" (keinginan merekomendasikan) untuk memvalidasi apakah kepuasan tersebut berujung pada loyalitas, bukan sekadar "puas saat itu saja".

**Contoh kasus ceiling effect untuk metrik ini:**
> Jika kuesioner diberikan tepat saat wisatawan mendapat diskon besar, semua orang mungkin menjawab "5" (sangat puas), sehingga data tidak bisa membedakan pengaruh teknologi yang sebenarnya karena skor sudah "mentok" di atas.

---

## Latihan 3 — Data Quality Check

Bayangkan data yang akan dikumpulkan dari eksperimen. Evaluasi 4 dimensi kualitas data.

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|---------|-----------|---------|------------------|
| Completeness | Apakah semua data point terkumpul? | Berisiko ada jawaban kosong pada kuesioner panjang | Mengaktifkan fitur "Required" pada form online. |
| Consistency | Apakah ada kontradiksi internal? | Responden mungkin menjawab asal (skor 5 di semua kolom) | Menambahkan reverse-coded questions untuk mengecek konsistensi jawaban |
| Validity | Apakah benar-benar mengukur yang dimaksud? | Mungkin mengukur "kesenangan" bukan "efektivitas teknologi" | Melakukan uji validitas konstruk (CFA) sebelum analisis utama |
| Representativeness | Apakah sampel mewakili populasi target? | Hanya menjangkau wisatawan yang melek gadget (bias) | Melakukan penyebaran survei di berbagai titik lokasi destinasi (bukan hanya via medsos) |

---

## Refleksi

> Mengapa memilih metrik setelah melihat data dianggap p-hacking? Apa bedanya dengan eksplorasi data yang sah?

**Jawaban:**
> Memilih metrik setelah melihat data (p-hacking) dianggap tidak etis karena peneliti cenderung memilih metrik yang hanya menunjukkan hasil signifikan (p < 0,05) agar hipotesisnya diterima, sehingga menipu realitas ilmiah. Ini seperti menembakkan panah ke tembok, lalu baru menggambar lingkaran target di sekeliling panah tersebut.
> Bedanya dengan eksplorasi data yang sah: Eksplorasi data bertujuan untuk mencari pola baru atau membangkitkan hipotesis untuk penelitian berikutnya, sedangkan metrik dalam pengujian hipotesis (konfirmatori) harus ditetapkan di awal sebagai janji objektifitas peneliti bahwa hasil "gagal" pun akan tetap dilaporkan.
