# eBay Perfume Market Analysis
## *Membaca Perilaku Konsumen & Peluang Bisnis di Pasar Parfum Online*

---

## Gambaran Proyek

Proyek ini menganalisis **2.000 listing parfum** dari platform eBay (1.000 produk pria dan 1.000 produk wanita) untuk mengungkap pola penjualan, perilaku konsumen, dan peluang bisnis yang tersembunyi di balik data mentah.

Di industri ritel parfum, keputusan sering kali masih berbasis intuisi. Melalui proyek ini, saya mencoba menunjukkan bagaimana data bisa membantu melihat pola dan mendukung keputusan yang lebih tepat.

### Pertanyaan Bisnis yang Dijawab

> - Segmen mana (pria atau wanita) yang lebih menguntungkan secara komersial, dan mengapa?
> - Brand, tipe produk, dan tier harga apa yang benar-benar mendorong pendapatan?
> - Di mana peluang pertumbuhan yang belum dimanfaatkan?

## Tujuan Analisis

1. **Melakukan Validasi & perluas** analisis awal pada segmen parfum pria
2. **Melakukan analisis penuh** pada segmen parfum wanita dengan kerangka yang sama
3. **Membandingkan** kedua segmen secara head-to-head dari sisi harga, volume, pendapatan, dan konsentrasi brand
4. **Menghasilkan rekomendasi bisnis** yang konkret, realistis, dan berbasis data

---

## Struktur Dataset

Kedua dataset memiliki skema yang identik sebagaimana keterangan pada tabel berikut:

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

**feature engineering:**
- `revenue` = `price × sold` (estimasi total nilai penjualan)
- `price_segment` = segmentasi harga: Budget / Mid-Range / Premium / Luxury
- `country` = negara penjual (diekstrak dari `itemLocation`)

---

## Insight Utama

### 1. Segmen Pria adalah Mesin Pendapatan Utama
Parfum pria menghasilkan estimasi **$25,8 juta** — hampir **86% lebih tinggi** dibanding parfum wanita ($13,9 juta), meski jumlah listing sama. Dua faktor yang saling memperkuat: harga rata-rata 16,5% lebih tinggi ($46,48 vs $39,89) dan volume penjualan 54% lebih besar per listing.

### 2. Segmen Harga Menengah ($25–$60) adalah Zona Emas
Tier ini menyumbang **64% pendapatan** di kedua segmen, meski hanya mewakili sekitar setengah dari total SKU. Inilah titik optimal antara margin keuntungan dan volume penjualan.

### 3. Produk Luxury Tidak Mengkonversi Sesuai Potensinya
Listing >$100 menyumbang hanya **3,6% (pria) dan 1,3% (wanita)** dari total pendapatan, padahal persentase SKU-nya jauh lebih besar. Ini menunjukkan adanya *trust gap* yang perlu diselesaikan, bukan menambah stok.

### 4. Pasar Wanita Lebih Terfragmentasi
Segmen pria didominasi oleh beberapa brand raksasa (Versace, Calvin Klein, Azzaro). Segmen wanita lebih tersebar luas, membuka ruang bagi brand niche atau brand yang belum jenuh di platform untuk masuk dan menguasai ceruk pasar.

### 5. Preferensi Tipe Parfum Berbeda Signifikan
Pria cenderung memilih **Eau de Toilette** (44% listing), sementara wanita secara dominan memilih **Eau de Parfum** (56% listing). 

### 6. "Sold-Out Stars" adalah Tambang Emas yang Terabaikan
Produk dengan penjualan tinggi tapi stoknya malah mendekati nol adalah sinyal terkuat untuk restocking prioritas. Produk ini sudah terbukti laku dan tidak perlu diuji lagi.

---

## Rekomendasi Bisnis

1. Mengalokasikan 60–65% anggaran inventori ke segmen pria
2. Dominasi tier harga $25–$60 dengan listing berkualitas tinggi
3. Memperbaiki kualitas listing luxury sebelum menambah SKU baru
4. Eksplorasi brand wanita dengan permintaan tinggi tapi suplai rendah di eBay
5. Segera melakukan restock produk "sold-out stars" (top 20% sold, stok < 5)
6. Memastikan tipe parfum (EDT/EDP) tertera akurat di judul listing

---

*Data didapat dari [kaggle](https://www.kaggle.com/datasets/degiaparlopapasaribu/data-parfume-men-and-women-at-ebay-ecomerce) yang bersumber dari listing publik eBay. Estimasi pendapatan dihitung sebagai harga × unit terjual dan bersifat indikatif, bukan absolut.*
