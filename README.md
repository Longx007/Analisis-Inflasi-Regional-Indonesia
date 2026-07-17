
# Analisis-Inflasi-Regional-Indonesia
Analisis tren inflasi regional Indonesia (IHK) — Proyek Sertifikasi BNSP Data Analyst, GenBI Sulawesi Sela# Analisis Tren Inflasi Regional Indonesia

**Proyek Sertifikasi BNSP Data Analyst — GenBI Sulawesi Selatan 2025**
**Prepared by:** Muhammad Fajar

---

## Latar Belakang Proyek

Proyek ini disusun sebagai bagian dari portofolio wajib mengikuti ujian **Sertifikasi Kompetensi Data Analyst dari Badan Nasional Sertifikasi Profesi (BNSP)**, dalam program pelatihan GenBI Sulawesi Selatan 2025. Proyek menggunakan data resmi **Badan Pusat Statistik (BPS)** berupa Indeks Harga Konsumen (IHK) per Kota/Kabupaten periode Januari–Maret 2024, mencakup 150 Kabupaten/Kota di 34 provinsi Indonesia.

Tujuan proyek adalah mengidentifikasi tren inflasi regional dan faktor-faktor pendorongnya, guna mendukung rekomendasi kebijakan stabilisasi harga di tingkat nasional maupun daerah.

Proyek dikerjakan dalam tiga tahap:
- **Tahap 1** — Pembersihan Data (Data Cleansing) di Excel/Google Sheets
- **Tahap 2** — Analisis Data menggunakan Pivot Table
- **Tahap 3** — Visualisasi Data Interaktif menggunakan Looker Studio

---

## Tahap 1 — Pembersihan Data

### Struktur Dataset

Dataset mentah terdiri dari 3.300+ baris data dengan kolom-kolom berikut:

| Kolom | Keterangan |
|---|---|
| Kota/Kabupaten | Nama wilayah pencatatan |
| Provinsi | Provinsi wilayah tersebut berada |
| Bulan Pencatatan | Periode pencatatan (Feb / Mar 2024) |
| Kelompok Kategori | Kelompok pengeluaran rumah tangga |
| Kategori | Sub-kategori barang/jasa (Makanan, Pakaian, Rekreasi, dll) |
| Index Harga Konsumen (IHK) | Nilai IHK bulan berjalan |
| IHK Bulan Lalu | Nilai IHK bulan sebelumnya sebagai pembanding |
| Laju Inflasi (M-t-M) | Persentase perubahan harga Month-to-Month |
| Kriteria Inflasi | Klasifikasi tingkat tekanan inflasi |
| Perubahan Poin IHK | Selisih poin absolut IHK antar bulan |
| Status Perubahan Harga Relatif | Klasifikasi kualitatif perubahan harga |

### Proses Cleansing

- Standardisasi penulisan nama Kota/Kabupaten (kolom "Proper") mengacu pada tabel referensi resmi
- Pelengkapan kolom kategori berdasarkan acuan referensi standar BPS
- Validasi dan klasifikasi **Kriteria Inflasi** serta **Status Perubahan Harga Relatif** untuk setiap baris data

📄 **Dataset lengkap:** [`Dataset_IHK_Jan-Mar_2024.xlsx`](./Dataset_IHK_Jan-Mar_2024.xlsx)

---

## Tahap 2 — Analisis dengan Pivot Table

Data yang telah bersih dianalisis menggunakan Pivot Table untuk menjawab serangkaian pertanyaan bisnis, di antaranya:

| # | Pertanyaan Bisnis | Insight |
|---|---|---|
| 1 | Top 3 Kota/Kabupaten dengan laju inflasi M-t-M tertinggi (Maret 2024)? | Kota Tangerang, Kota Denpasar, dan Kab. Lampung Timur |
| 2 | Kategori dengan perubahan laju inflasi M-t-M terbesar antar bulan? | Kategori Makanan — naik dari 0,78 (Feb) menjadi 1,45 (Mar), selisih 0,67 |
| 3 | Persentase data dengan status Inflasi Normal? | 21,58% dari keseluruhan data |
| 4 | Perbandingan laju inflasi Jakarta vs Surabaya (Maret 2024)? | Jakarta 0,21% vs Surabaya 0,37% — selisih 0,16 poin |
| 5 | Provinsi dengan frekuensi "Perubahan Normal" tertinggi? | Jawa Timur — 104 kejadian (7,17% dari total) |

Pertanyaan bisnis lengkap (Business Question A & B) beserta jawaban rinci dapat dilihat pada sheet `Business Question` di dalam dataset.

---

## Tahap 3 — Dashboard Interaktif (Looker Studio)

Dashboard dirancang untuk menjawab kebutuhan visualisasi berikut:
- Data agregat (jumlah kota/kabupaten, provinsi, rata-rata laju inflasi M-t-M)
- Tren inflasi nasional Februari–Maret 2024
- Peta panas regional per provinsi
- Distribusi peringatan inflasi (Akselerasi Kuat vs Akselerasi Persentase)
- Perbandingan sektor ekonomi (IHK bulan ini vs bulan lalu)
- Hitungan kota/kabupaten yang mengalami deflasi
- Top 5 kontributor perubahan poin IHK
- Kontrol interaktif berdasarkan Provinsi dan Kelompok Kategori

🔗 **Dashboard interaktif:** [Looker Studio — Analisis Laju Inflasi (M-t-M) Nasional](https://lookerstudio.google.com/reporting/b991661d-c355-4b9b-a80c-94fffc71f99f)

---

## Temuan Utama & Analisis

**Tren nasional:** Dari 150 Kabupaten/Kota di 34 provinsi, rata-rata laju inflasi nasional (M-t-M) naik dua kali lipat — dari **0,12% pada Februari** menjadi **0,26% pada Maret 2024** — seiring 139 dari 150 wilayah masih mencatat deflasi ringan. Kenaikan ini terjadi menjelang bulan Ramadan, didorong oleh peningkatan permintaan barang dan jasa yang tidak diimbangi peningkatan pasokan, sehingga menciptakan kelangkaan yang mendorong kenaikan harga.

**Persebaran regional:** Provinsi dengan laju inflasi tinggi terkonsentrasi di **Pulau Jawa dan Sumatera**, dengan pola persebaran yang saling berdekatan — mengindikasikan adanya masalah distribusi pasokan yang menyebabkan efek domino ke daerah-daerah sekitarnya (tekanan harga menyebar secara berantai).

**Akselerasi inflasi:** Proporsi wilayah dengan "Akselerasi Kuat" meningkat dari 35,7% (Februari) menjadi 39,4% (Maret 2024), sejalan dengan penurunan jumlah wilayah deflasi dari 119 menjadi 115 — menandakan tekanan inflasi mulai merambah ke lebih banyak daerah, tidak lagi bersifat lokal.

**Sektor pendorong utama:** Tiga sektor dengan Indeks Harga Konsumen tertinggi dan paling memicu fluktuasi inflasi nasional adalah:
1. **Makanan dan Pakaian**
2. **Rekreasi dan Kendaraan**
3. **Pendidikan dan Kesehatan**

Sektor Makanan & Pakaian serta Rekreasi & Kendaraan merupakan sektor yang secara musiman meningkat menjelang bulan puasa.

**Kontributor poin tertinggi:** Lima Kabupaten/Kota dengan perubahan poin IHK tertinggi adalah Kab. Nunukan (1,35 poin — tertinggi), Kab. Pasaman Barat, Kota Tangerang, Kab. Aceh Tengah, dan Kota Denpasar — kelimanya berkontribusi besar terhadap kenaikan akselerasi kuat pada Maret 2024.

---

## Rekomendasi Kebijakan

1. **Pemantauan harga intensif** pada provinsi dengan inflasi tinggi, khususnya di Pulau Jawa dan Sumatera, serta mitigasi dini untuk wilayah Kalimantan yang mulai menunjukkan tanda kenaikan
2. **Penguatan distribusi pasokan** antar provinsi untuk mencegah kelangkaan barang dan jasa, khususnya pada sektor Makanan & Pakaian, Rekreasi & Kendaraan, dan Pendidikan & Kesehatan
3. **Investigasi rantai distribusi** (distributor/supplier) di daerah dengan inflasi tinggi untuk mencegah penahanan pasokan yang tidak wajar
4. **Operasi pasar murah** khusus menjelang periode konsumsi tinggi (Ramadan), difokuskan pada lima kabupaten/kota dengan kontribusi poin IHK tertinggi
5. **Pemantauan mingguan** pada wilayah dengan akselerasi kuat sebagai sistem peringatan dini terhadap perluasan tekanan inflasi

---

## Tools & Metodologi

| Tahap | Tools |
|---|---|
| Data Cleansing | Microsoft Excel / Google Sheets |
| Analisis Data | Pivot Table |
| Visualisasi Data | Looker Studio |

## Isi Repository

```
├── Dataset_IHK_Jan-Mar_2024.xlsx     # Dataset mentah, cleansing, pivot table, business question
├── Laporan_Portofolio_BNSP.pptx      # Dokumentasi lengkap proses & analisis (slide deck)
└── README.md
```

---
*Proyek ini merupakan bagian dari portofolio Sertifikasi Kompetensi Data Analyst — BNSP, program pelatihan GenBI Sulawesi Selatan 2025.*
tan 2025. Data cleansing &amp; pivot table di Excel, dashboard interaktif di Looker Studio.
