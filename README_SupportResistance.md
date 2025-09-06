# Pine Script - Support & Resistance Levels

Script Pine Script yang canggih untuk mendeteksi dan menampilkan level support dan resistance berdasarkan pivot points dengan validasi kekuatan level.

## Fitur Utama

### 🎯 Deteksi Pivot Points
- Menggunakan algoritma `ta.pivothigh()` dan `ta.pivotlow()` untuk mendeteksi pivot points
- Dapat disesuaikan panjang pivot (default: 5 bars)
- Menyimpan riwayat pivot points untuk analisis level

### 📊 Validasi Level
- **Minimum Touches**: Level harus disentuh minimal 2 kali untuk valid
- **Touch Tolerance**: Toleransi persentase untuk menentukan "sentuhan" (default: 0.1%)
- **Strength Scoring**: Level dinilai berdasarkan jumlah sentuhan
- **Level Filtering**: Menghapus level duplikat dan mengurutkan berdasarkan kekuatan

### 🎨 Visualisasi
- **Support Levels**: Garis hijau untuk level support
- **Resistance Levels**: Garis merah untuk level resistance
- **Dynamic Colors**: Warna berubah berdasarkan kekuatan level
- **Labels**: Menampilkan harga dan jumlah sentuhan
- **Table**: Tabel informasi level terkuat di pojok kanan atas

### ⚡ Alerts
- Alert otomatis ketika harga mendekati level penting
- Frekuensi alert dapat dikontrol untuk menghindari spam

## Cara Menggunakan

### 1. Instalasi
1. Buka TradingView
2. Tekan `Alt + E` atau klik "Pine Editor"
3. Copy seluruh kode dari file `support_resistance.pine`
4. Paste ke Pine Editor
5. Klik "Add to Chart"

### 2. Pengaturan Parameter

#### Deteksi Pivot
- **Pivot Length** (5): Jumlah bars untuk mencari pivot kiri dan kanan
- **Minimum Touches** (2): Minimum sentuhan untuk validasi level
- **Touch Tolerance %** (0.1): Toleransi persentase untuk sentuhan

#### Filter Level
- **Maximum Levels** (10): Maksimum level yang ditampilkan
- **Minimum Strength** (2): Skor minimum untuk menampilkan level
- **Lookback Bars** (200): Jumlah bars untuk mencari level

#### Tampilan
- **Show Support Levels**: Tampilkan level support
- **Show Resistance Levels**: Tampilkan level resistance
- **Show Labels**: Tampilkan label harga dan kekuatan
- **Extend Lines to Right**: Perpanjang garis ke kanan

#### Warna dan Style
- **Support Color**: Warna untuk level support (default: hijau)
- **Resistance Color**: Warna untuk level resistance (default: merah)
- **Line Style**: Solid, Dashed, atau Dotted
- **Line Width**: Ketebalan garis (1-5)

### 3. Interpretasi Level

#### Kekuatan Level
- **2-3 touches**: Level lemah (transparansi tinggi)
- **4+ touches**: Level kuat (transparansi rendah)

#### Label Format
- **S: 1.2345 (3)**: Support di 1.2345 dengan 3 sentuhan
- **R: 1.2500 (5)**: Resistance di 1.2500 dengan 5 sentuhan

#### Tabel Informasi
Tabel di pojok kanan atas menampilkan:
- **Type**: S (Support) atau R (Resistance)
- **Price**: Harga level
- **Strength**: Jumlah sentuhan

## Strategi Trading

### 1. Level Support
- **Buy Signal**: Harga bounce dari level support yang kuat
- **Stop Loss**: Di bawah level support
- **Target**: Level resistance terdekat

### 2. Level Resistance
- **Sell Signal**: Harga reject dari level resistance yang kuat
- **Stop Loss**: Di atas level resistance
- **Target**: Level support terdekat

### 3. Breakout Strategy
- **Bullish Breakout**: Harga break di atas resistance dengan volume tinggi
- **Bearish Breakout**: Harga break di bawah support dengan volume tinggi

### 4. Range Trading
- **Buy**: Dekat level support
- **Sell**: Dekat level resistance
- **Condition**: Level harus teruji minimal 3-4 kali

## Tips Penggunaan

### 1. Timeframe
- **Scalping**: 1m, 5m dengan pivot length 3-5
- **Day Trading**: 15m, 1h dengan pivot length 5-10
- **Swing Trading**: 4h, 1D dengan pivot length 10-20

### 2. Optimasi Parameter
- **Volatile Market**: Tingkatkan touch tolerance ke 0.2-0.3%
- **Sideways Market**: Kurangi minimum touches ke 2
- **Trending Market**: Tingkatkan minimum strength ke 3-4

### 3. Kombinasi dengan Indikator Lain
- **Volume**: Konfirmasi breakout dengan volume tinggi
- **RSI**: Divergence di level support/resistance
- **Moving Average**: Konfirmasi trend direction

## Troubleshooting

### Level Tidak Muncul
1. Kurangi `Minimum Strength`
2. Tingkatkan `Touch Tolerance`
3. Tingkatkan `Lookback Bars`

### Terlalu Banyak Level
1. Tingkatkan `Minimum Strength`
2. Kurangi `Maximum Levels`
3. Kurangi `Touch Tolerance`

### Level Tidak Akurat
1. Sesuaikan `Pivot Length` dengan timeframe
2. Tingkatkan `Minimum Touches`
3. Periksa `Touch Tolerance`

## Kode Struktur

### Fungsi Utama
- `find_levels()`: Mencari dan validasi level dari pivot points
- `remove_duplicates()`: Menghapus level duplikat
- `sort_by_strength()`: Mengurutkan level berdasarkan kekuatan
- `get_level_color()`: Menentukan warna berdasarkan kekuatan

### Data Structure
```pinescript
type LevelInfo
    float price          // Harga level
    int touches         // Jumlah sentuhan
    int strength        // Skor kekuatan
    int first_touch_bar // Bar pertama disentuh
    int last_touch_bar  // Bar terakhir disentuh
    bool is_support     // True jika support, false jika resistance
```

## Update dan Maintenance

Script ini menggunakan Pine Script v5 dan kompatibel dengan semua fitur TradingView terbaru. Untuk update atau modifikasi:

1. Backup pengaturan parameter yang sudah optimal
2. Test di demo account sebelum live trading
3. Monitor performa dan sesuaikan parameter jika diperlukan

---

**⚠️ Disclaimer**: Script ini adalah alat bantu analisis teknikal. Selalu lakukan analisis tambahan dan manajemen risiko yang proper sebelum melakukan trading.