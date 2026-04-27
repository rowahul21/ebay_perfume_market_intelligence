# eBay Perfume Market Intelligence
## *Membaca Perilaku Konsumen & Peluang Bisnis di Pasar Parfum Online*

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Domain-Retail%20Analytics-2563EB?style=for-the-badge"/>
</p>

---

## Gambaran Proyek

Proyek ini menganalisis **2.000 listing parfum** dari platform eBay — 1.000 produk pria dan 1.000 produk wanita — untuk mengungkap pola penjualan, perilaku konsumen, dan peluang bisnis yang tersembunyi di balik data mentah.

Di industri ritel parfum yang bernilai miliaran dolar, keputusan bisnis sering kali diambil berdasarkan intuisi. Proyek ini membuktikan bahwa data berbicara lebih keras: **siapa yang memahami data lebih dahulu, dialah yang memenangkan pasar.**

### Pertanyaan Bisnis yang Dijawab

> - Segmen mana — pria atau wanita — yang lebih menguntungkan secara komersial, dan mengapa?
> - Brand, tipe produk, dan tier harga apa yang benar-benar mendorong pendapatan?
> - Di mana peluang pertumbuhan yang belum dimanfaatkan?

---

## Struktur Dataset

Kedua dataset memiliki skema yang identik:

| Kolom | Tipe | Deskripsi |
|---|---|---|
| `brand` | String | Nama merek parfum |
| `title` | String | Judul listing produk |
| `type` | String | Tipe parfum (EDT, EDP, Parfum, dll.) |
| `price` | Float | Harga dalam USD |
| `available` | Float | Stok tersedia |
| `sold` | Int | Total unit terjual |
| `lastUpdated` | String | Tanggal update listing |
| `itemLocation` | String | Lokasi penjual |

**Fitur rekayasa (feature engineering):**
- `revenue` = `price × sold` (estimasi total nilai penjualan)
- `price_segment` = segmentasi harga: Budget / Mid-Range / Premium / Luxury
- `country` = negara penjual (diekstrak dari `itemLocation`)

---

## Tujuan Analisis

1. **Validasi & perluas** analisis awal pada segmen parfum pria
2. **Lakukan analisis penuh** pada segmen parfum wanita dengan kerangka yang sama
3. **Bandingkan** kedua segmen secara head-to-head dari sisi harga, volume, pendapatan, dan konsentrasi brand
4. **Hasilkan rekomendasi bisnis** yang konkret, realistis, dan berbasis data

---

## Insight Utama

### 1. Segmen Pria adalah Mesin Pendapatan Utama
Parfum pria menghasilkan estimasi **~$25,8 juta** — hampir **86% lebih tinggi** dibanding parfum wanita (~$13,9 juta), meski jumlah listing sama. Dua faktor yang saling memperkuat: harga rata-rata 16,5% lebih tinggi ($46,48 vs $39,89) **dan** volume penjualan 54% lebih besar per listing.

### 2. Segmen Harga Menengah ($25–$60) adalah Zona Emas
Tier ini menyumbang **~64% pendapatan** di kedua segmen, meski hanya mewakili sekitar setengah dari total SKU. Inilah titik optimal antara margin keuntungan dan volume penjualan.

### 3. Produk Luxury Tidak Mengkonversi Sesuai Potensinya
Listing >$100 menyumbang hanya **3,6% (pria) dan 1,3% (wanita)** dari total pendapatan, padahal persentase SKU-nya jauh lebih besar. Ini menunjukkan adanya *trust gap* yang perlu diselesaikan, bukan menambah stok.

### 4. Pasar Wanita Lebih Terfragmentasi — Peluang untuk Pemain Baru
Segmen pria didominasi oleh beberapa brand raksasa (Versace, Calvin Klein, Azzaro). Segmen wanita lebih tersebar luas, membuka ruang bagi brand niche atau brand yang belum jenuh di platform untuk masuk dan menguasai ceruk pasar.

### 5. Preferensi Tipe Parfum Berbeda Signifikan
Pria cenderung memilih **Eau de Toilette** (44% listing), sementara wanita secara dominan memilih **Eau de Parfum** (56% listing). Kekeliruan pelabelan tipe produk secara langsung mempengaruhi konversi dan tingkat pengembalian barang.

### 6. "Sold-Out Stars" adalah Tambang Emas yang Terabaikan
Produk dengan penjualan tinggi tapi stok mendekati nol adalah sinyal terkuat untuk restocking prioritas. Produk ini sudah terbukti laku — tidak perlu diuji lagi.

---

## Rekomendasi Bisnis

| # | Rekomendasi | Dampak |
|---|---|---|
| 1 | Alokasikan 60–65% anggaran inventori ke segmen pria | Tinggi |
| 2 | Dominasi tier harga $25–$60 dengan listing berkualitas tinggi | Tinggi |
| 3 | Perbaiki kualitas listing luxury sebelum menambah SKU baru | Sedang |
| 4 | Eksplorasi brand wanita dengan permintaan tinggi tapi suplai rendah di eBay | Tinggi |
| 5 | Segera restock produk "sold-out stars" (top 20% sold, stok < 5) | Kritis |
| 6 | Pastikan tipe parfum (EDT/EDP) tertera akurat di judul listing | Sedang |

---

## Tools & Teknologi

| Kategori | Tools |
|---|---|
| Bahasa Pemrograman | Python 3.10+ |
| Manipulasi Data | Pandas, NumPy |
| Visualisasi | Matplotlib, Seaborn |
| Lingkungan Kerja | Jupyter Notebook |
| Pengelolaan Versi | Git & GitHub |

---

## Struktur Folder

```
ebay-perfume-market-intelligence/
│
├── perfume_market_analysis.ipynb   # Notebook analisis utama
├── ebay_mens_perfume.csv           # Dataset parfum pria (1.000 listing)
├── ebay_womens_perfume.csv         # Dataset parfum wanita (1.000 listing)
└── README.md                       # Dokumentasi proyek ini
```

---

*Data bersumber dari listing publik eBay. Estimasi pendapatan dihitung sebagai harga × unit terjual dan bersifat indikatif, bukan absolut.*
