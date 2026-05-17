# WS-07: Experimental Design & Validity

> **Bab 7 — Experimental Design & Validity**

---

## Ringkasan Materi

### Correlation ≠ Causality

Kausalitas membutuhkan 3 syarat:
1. **Covariance** — X dan Y bergerak bersama
2. **Temporal precedence** — X berubah sebelum Y
3. **Elimination of alternatives** — Tidak ada faktor lain yang menjelaskan Y

Controlled experiment adalah satu-satunya metode yang bisa membuktikan kausalitas.

### Empat Jenis Validitas

| Jenis | Pertanyaan | Ancaman Umum |
|-------|-----------|-------------|
| **Internal** | Apakah hubungan IV→DV nyata? | Confounding variable, selection bias |
| **External** | Apakah bisa digeneralisasi? | Dataset terlalu spesifik |
| **Construct** | Apakah mengukur konsep yang benar? | Metrik tidak sesuai |
| **Conclusion** | Apakah kesimpulan statistik valid? | Sample size kecil, uji salah |

Internal dan external validity sering berkonflik: semakin terkontrol (internal kuat) → semakin artificial (external lemah).

### Tiga Tipe Eksperimen dalam Riset TI

| Tipe | Deskripsi | Kapan Digunakan |
|------|----------|----------------|
| **Comparison Study** | Metode A vs B pada kondisi identik | Membandingkan pendekatan berbeda |
| **Ablation Study** | Full system → lepas komponen satu per satu | Mengukur kontribusi tiap komponen |
| **Parameter Study** | Variasikan satu parameter, amati dampak | Uji sensitifitas/robustness |

### Fairness dalam Perbandingan

Perbandingan yang adil = **kondisi identik** untuk semua metode: dataset sama, preprocessing sama, tuning effort sebanding, environment sama, metrik sama.

Contoh tidak adil: Transformer (30 fitur tambahan + Bayesian optimization) vs RF (default params) → hasilnya misleading.

### Threats to Validity = Diidentifikasi Sebelum Eksperimen

Ancaman validitas harus diidentifikasi **sebelum** eksperimen dan mitigasinya dirancang sebagai bagian dari desain — bukan ditulis sebagai boilerplate setelah selesai.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan testing | Memastikan sistem memenuhi requirement | Membuktikan hubungan kausal antar variabel |
| Baseline | Versi sebelumnya (last release) | Metode tervalidasi dari literatur |
| Kegagalan | Bug → fix → release | H₀ tidak ditolak → tetap kontribusi ilmiah |
| Sukses | 100% test pass | Evidence valid — mendukung atau menolak hipotesis |

### Istilah Penting

- **Causality** — Hubungan sebab-akibat (covariance + temporal + elimination)
- **Controlled Experiment** — Ubah satu variabel, kontrol sisanya, amati efek
- **Fairness** — Semua metode diuji pada kondisi yang benar-benar identik
- **Threats to Validity** — Faktor yang bisa melemahkan kesimpulan jika tidak dimitigasi
- **Conclusion Validity** — Validitas statistik: power, sample size, uji yang tepat

---

## Template A.7 — Desain Eksperimen Lengkap

```
EXPERIMENT DESIGN

Research Question : Apakah dimensi Smart Tourism Technology (Informativeness, Accessibility, Interactivity, Personalization) berpengaruh secara signifikan terhadap peningkatan pengalaman wisatawan (skor kepuasan) di destinasi wisata digital?
Hypothesis        : Wisatawan yang pake sistem dengan fitur lengkap (ada Personalization) bakal punya skor kepuasan yang lebih tinggi dibanding yang cuma pake fitur standar.
Tipe Eksperimen   : [ ] Comparison  [✓] Ablation  [ ] Parameter

Kondisi Eksperimen:
| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control |Aplikasi standar tanpa fitur custom |Info, Akses, Interaksi |Destinasi sama, device sama, waktu akses dibatasi 15 menit |
| Treatment |Aplikasi full fitur (ada rekomendasi)|Info, Akses, Interaksi, Personalization |Destinasi sama, device sama, waktu akses dibatasi 15 menit |

Fairness Checklist:
  [✓] Dataset identik untuk semua kondisi
  [✓] Preprocessing setara
  [✓] Tuning effort setara
  [✓] Environment identik
  [✓] Metrik evaluasi sama

Threat Analysis: 
| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal    |Responden asal isi atau pengen "nyenengin" peneliti (bias jawaban) |Kuesioner dibikin anonim dan dikasih tau kalo jawaban nggak ngaruh ke nilai apapun |
| External    |Responden kebanyakan cuma anak muda, jadi nggak mewakili turis tua |Pas bagi kuesioner, usahain dapet profil umur yang beda-beda (stratified) |
| Construct   |Pertanyaan kuesioner mungkin kurang pas buat ngukur "kepuasan" |Pake indikator dimensi dari jurnal Lee dkk (2017) biar pertanyaannya valid secara teori |
| Conclusion  |Jumlah orang yang ngetes terlalu dikit (sampel nggak cukup) |Targetin minimal 100 orang biar hasil uji statistiknya kuat dan sah |

Statistical Plan:
  Uji statistik    : Independent Samples T-Test 
  Justifikasi      : Soalnya saya mau ngebandingin rata-rata skor kepuasan dari dua kelompok yang beda (kelompok standar vs kelompok full fitur)
  Alpha            : 0,05 (Standar skripsi lah, tingkat kesalahan 5%)
  Effect size min  : 0,5 (Cohen's d). Biar perbedaannya nggak cuma keliatan di angka, tapi emang ada efek nyata di lapangan.
```

---

## Latihan 1 — Desain Eksperimen

Susun desain eksperimen berdasarkan RQ, variabel, dan sistem dari WS-04 sampai WS-06.

**RQ:** Apakah dimensi Smart Tourism Technology (Informativeness, Accessibility, Interactivity, Personalization) berpengaruh secara signifikan terhadap peningkatan pengalaman wisatawan (skor kepuasan) di destinasi wisata digital?
**Tipe eksperimen:** [ ] Comparison / [✓] Ablation / [ ] Parameter

| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control |Sistem dasar tanpa fitur kustomisasi/rekomendasi |Informativeness, Accessibility, Interactivity (Modul Personalization dimatikan) |Dataset destinasi yang sama, durasi uji coba 15 menit, perangkat (smartphone) dengan spesifikasi setara |
| Treatment |Sistem lengkap sesuai dengan desain arsitektur penuh |Semua dimensi aktif (Informativeness, Accessibility, Interactivity, Personalization) |Dataset destinasi yang sama, durasi uji coba 15 menit, perangkat (smartphone) dengan spesifikasi setara |

---

## Latihan 2 — Fairness Checklist

Evaluasi apakah desain eksperimen di Latihan 1 sudah fair.

| Kriteria | Status | Detail |
|----------|--------|--------|
| Dataset identik |✅ |Semua partisipan melihat informasi destinasi, foto, dan deskripsi wisata yang sama dari database pusat |
| Preprocessing setara |✅ |Data mentah dari log user (klik dan durasi) dibersihkan dan dihitung dengan rumus yang sama sebelum masuk ke analisis statistik |
| Tuning effort setara |✅ |Tidak ada perlakuan khusus pada kecepatan server untuk salah satu grup. Keduanya mendapatkan performa aplikasi yang sama stabilnya |
| Environment identik |✅ |Pengujian dilakukan menggunakan perangkat yang spesifikasinya setara (misal: pengujian di laboratorium komputer atau browser yang seragam) |
| Metrik evaluasi sama |✅ |Semua responden mengisi kuesioner kepuasan yang butir-butir pertanyaannya sama persis |

**Ada yang tidak fair?** [ ] Ya / [✓] Tidak
> Jika tidak, bagaimana cara memperbaikinya? Karena konfigurasi sistem dikunci melalui file config (seperti yang direncanakan di WS-06), sehingga perbedaan hasil murni karena aktif/tidaknya fitur Personalization, bukan karena faktor teknis lainnya.

---

## Latihan 3 — Threat Analysis

Identifikasi ancaman validitas untuk desain eksperimen ini.

| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal |Effect Bias: Responden mungkin menjawab kuesioner dengan skor tinggi hanya karena merasa tidak enak pada peneliti |Menggunakan sistem kuesioner anonim dan menjelaskan bahwa data mereka tidak akan memengaruhi nilai atau reputasi mereka |
| External |Selection Bias: Jika semua responden adalah mahasiswa IT, hasil ini mungkin tidak berlaku untuk wisatawan umum (orang tua atau orang non-IT) |Berusaha menyebarkan uji coba ke luar lingkungan kampus atau melibatkan kelompok usia yang lebih luas agar sampel lebih representatif |
| Construct |Metrik Kurang Pas: Skor kepuasan mungkin hanya mencerminkan "senang sesaat" karena tampilan aplikasi bagus, bukan karena kegunaan STT |Menggunakan kuesioner yang sudah tervalidasi dari jurnal (seperti Lee et al., 2017) yang spesifik mengukur efektivitas dimensi STT |
| Conclusion |Sample Size: Jumlah orang yang ikut eksperimen terlalu sedikit sehingga hasilnya tidak bisa dianggap mewakili pola secara umum |Menetapkan target minimal 100 responden untuk menjamin bahwa hasil uji regresi atau T-test memiliki statistical power yang cukup |

**Ancaman mana yang paling sulit dimitigasi?** External Validity (Generalisasi hasil).
**Mengapa?**
> Karena sulit untuk menjamin bahwa sistem STT yang sukses di satu destinasi (misal: museum digital) akan sukses juga jika diterapkan di destinasi yang sifatnya terbuka seperti wisata alam, karena kebutuhan informasi wisatawannya pasti berbeda.

---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**
1. Apakah perbandingannya dilakukan secara adil (Fair Comparison)? Kita perlu mempertanyakan apakah metode baseline (pembanding) diberikan perlakuan, parameter, dan sumber daya yang sama optimalnya dengan metode yang diusulkan, atau jangan-jangan metode baseline hanya dijalankan dengan setelan default sementara metode baru dioptimalkan secara berlebihan.
2. Bagaimana kondisi lingkungan pengujian dan dataset yang digunakan? Penting untuk mengevaluasi apakah pengujian dilakukan pada dataset yang sama (identik) dan lingkungan (hardware/software) yang seragam. Klaim "mengalahkan" sering kali tidak valid jika metode baru hanya unggul di satu dataset spesifik yang sudah sangat dikenal oleh peneliti (data snooping).
3. Apakah perbedaan hasilnya signifikan secara statistik? Klaim keunggulan tidak boleh hanya dilihat dari selisih angka rata-rata yang tipis. Kita harus menanyakan hasil uji signifikansi (seperti P-value) untuk memastikan bahwa kemenangan metode tersebut memang nyata secara ilmiah dan bukan karena kebetulan atau fluktuasi acak pada data.
