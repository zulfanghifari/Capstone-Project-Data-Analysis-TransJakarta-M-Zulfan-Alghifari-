# 📊 Analisis TransJakarta: Profil Pengguna dan Pola Perjalanan

## 📋 Deskripsi Proyek

Proyek analisis data ini bertujuan untuk mengoptimalkan layanan TransJakarta melalui pemahaman mendalam tentang profil pengguna dan pola perjalanan penumpang. Analisis ini fokus pada tiga permasalahan utama: keamanan penumpang (terutama perempuan), aksesibilitas untuk kelompok rentan (anak-anak dan lansia), dan pengelolaan kepadatan pada jam-jam tertentu.

## 🎯 Latar Belakang

TransJakarta, sebagai sistem Bus Rapid Transit (BRT) pertama di Asia Tenggara dan Selatan yang beroperasi sejak 2004, melayani lebih dari 800.000 penumpang per hari. Meskipun telah mengimplementasikan sistem tap in dan tap out untuk meningkatkan efisiensi, masih terdapat tantangan seperti:

- 🚨 Kasus pelecehan seksual terhadap penumpang perempuan
- ♿ Kurangnya fasilitas ramah untuk lansia dan anak-anak
- 🚌 Kepadatan ekstrem pada jam-jam tertentu

## 🔍 Rumusan Masalah

### 1. Profil Pengguna TransJakarta
- Bagaimana proporsi pengguna berdasarkan gender?
- Bagaimana persebaran usia pengguna?

### 2. Pola Perjalanan Berdasarkan Profil Pengguna
- Koridor mana yang sering digunakan oleh penumpang perempuan?
- Koridor mana yang sering digunakan oleh anak-anak?
- Koridor mana yang sering digunakan oleh lansia?
- Koridor mana yang berpotensi untuk promosi?

### 3. Jam Sibuk
- Kapan puncak jam sibuk yang menyebabkan kepadatan penumpang?

## 📊 Dataset

Dataset mencakup 22 kolom dengan informasi:
- **Data Demografis**: Gender, tahun lahir pengguna
- **Detail Transaksi**: ID transaksi, waktu tap in/out
- **Data Kartu Pembayaran**: Bank penerbit, jenis kartu
- **Rute Perjalanan**: Koridor, arah, halte
- **Informasi Lokasi**: Koordinat latitude/longitude halte
- **Nominal Transaksi**: Jumlah pembayaran

**Jumlah Data Awal**: 37,900 transaksi  
**Jumlah Data Setelah Cleaning**: 34,686 transaksi

## 🛠️ Teknologi yang Digunakan

```python
- Python 3.x
- Pandas - Data manipulation
- NumPy - Numerical computing
- Matplotlib - Data visualization
- Seaborn - Statistical visualization
- Missingno - Missing data visualization
```

## 📈 Metodologi

### 1. Data Understanding
- Eksplorasi struktur dataset
- Identifikasi tipe data dan missing values

### 2. Data Cleaning
- **Handling Missing Values**:
  - `payAmount`: Diisi berdasarkan `corridorID`
  - `corridorID` & `corridorName`: Mapping menggunakan mode
  - `tapInStops` & `tapOutStops`: Mapping dengan nama halte
  - `stopEndSeq`: Mapping dengan `stopStartSeq`
  - Penghapusan data yang tidak dapat diisi (3,214 rows)

### 3. Feature Engineering
Menambahkan kolom baru:
- `tapInHour` & `tapOutHour`: Jam tap in/out
- `tapInDay`: Hari dalam minggu
- `tapInWeek`: Minggu dalam bulan
- `age`: Usia pengguna (2023 - tahun lahir)
- `ageGroup`: Kategori usia (anak-anak, remaja, dewasa awal, dewasa akhir, lansia)
- `transType`: Jenis layanan (RoyalTrans, Regular TJ, JakLingko)

### 4. Analisis Data
- Analisis profil pengguna (gender & usia)
- Analisis pola perjalanan berdasarkan profil
- Analisis jam sibuk (weekday & weekend)
- Analisis koridor dan halte terpadat

## 🔑 Temuan Utama

### Profil Pengguna

#### Gender
- **Perempuan**: 53.3% (18,482 pengguna)
- **Laki-laki**: 46.7% (16,204 pengguna)
- Selisih 6.4% menunjukkan kebijakan armada khusus wanita masih relevan

#### Usia
1. **Dewasa Awal** (20-39 tahun): 18,169 pengguna (52.4%)
2. **Dewasa Akhir** (40-59 tahun): 9,347 pengguna (26.9%)
3. **Remaja** (13-19 tahun): 5,061 pengguna (14.6%)
4. **Anak-anak** (0-12 tahun): 1,414 pengguna (4.1%)
5. **Lansia** (≥60 tahun): 695 pengguna (2.0%)

### Pola Perjalanan Berdasarkan Profil

#### Top 5 Koridor untuk Perempuan
1. Pasar Minggu - Tanah Abang (213)
2. Poris Plawad - Bundaran Senayan (211)
3. Rusun Rawa Bebek - Kodamar (205)
4. Terminal Tanah Merah - Pulo Gadung (195)
5. Cilangkap - Cililitan (187)

#### Top 5 Koridor untuk Anak-anak
1. Kampung Rambutan - Juanda via Pasar Baru (89)
2. Pinang Ranti - Pluit (65)
3. Kampung Melayu - Ragunan (42)
4. Rusun Rawa Bebek - Bukit Duri (40)
5. Puri Beta - Pancoran Barat (40)

#### Top 5 Koridor untuk Lansia
1. Ragunan - Gelora Bung Karno (71)
2. Blok M - Kota (38)
3. Kampung Rambutan - Tanjung Priok (38)
4. Lebak Bulus - Petukangan (37)
5. Cibubur - BKN (37)

### Jam Sibuk (Weekday)

#### Pagi (05:00 - 09:00)
- **Peak Tap-In**: Jam 06:00 (~5,300 pengguna)
- **Peak Tap-Out**: Jam 07:00 (~3,700 pengguna)

**Top 5 Koridor Terpadat**:
1. Cibubur - Balai Kota (187)
2. Ciputat - CSW (180)
3. Pulo Gadung - Monas (159)
4. Harmoni - Jakarta International Stadium (158)
5. Rusun Pondok Bambu - Walikota Jakarta Timur (157)

**Top 5 Halte Tap-In**:
1. Garuda Taman Mini (131)
2. Rusun Kapuk Muara (97)
3. Penjaringan (85)
4. Rawa Selatan (79)
5. Tendean (78)

**Top 5 Halte Tap-Out**:
1. Penjaringan (162)
2. BKN (150)
3. Monas (129)
4. Kejaksaan Agung (98)
5. Pecenongan (95)

#### Sore (16:00 - 21:00)
- **Peak Tap-In**: Jam 17:00 (~5,000 pengguna)
- **Peak Tap-Out**: Jam 18:00 (~4,200 pengguna)

**Top 5 Koridor Terpadat**:
1. Cibubur - Balai Kota (183)
2. Ciputat - CSW (176)
3. Harmoni - Jakarta International Stadium (163)
4. Pulo Gadung - Monas (163)
5. Kampung Rambutan - Pondok Gede (162)

**Top 5 Halte Tap-In**:
1. Penjaringan (133)
2. Cibubur Junction (96)
3. Pejaten (95)
4. BKN (93)
5. Seskoal (80)

**Top 5 Halte Tap-Out**:
1. Term. Senen (148)
2. BKN (137)
3. Pinang Ranti (117)
4. Term. Kampung Rambutan (98)
5. Rusun Kapuk Muara (92)

### Pola Weekend

**Top 5 Koridor Weekend**:
1. Pinang Ranti - Kampung Rambutan (31)
2. Pinang Ranti - Bundaran Senayan (30)
3. JIS - Terminal Muara Angke (30)
4. Harapan Indah - ASMI (28)
5. Rusun Cipinang Muara - Jatinegara (26)

Pola weekend menunjukkan pergeseran dari perjalanan komuter ke rekreasi dan keluarga.

## 💡 Rekomendasi Strategis

### 1. Peningkatan Keamanan dan Inklusi

#### Untuk Perempuan
- ✅ Perluas layanan bus khusus wanita di koridor prioritas:
  - Pasar Minggu - Tanah Abang
  - Poris Plawad - Bundaran Senayan
  - Rusun Rawa Bebek - Kodamar
- 🎥 Tambahkan CCTV dan petugas keamanan di halte ramai
- 📢 Kampanye anti-pelecehan dan sosialisasi hotline pengaduan

#### Untuk Anak-anak
- 🎨 Sediakan area bermain dan waiting area khusus di halte prioritas
- 👨‍👩‍👧 Training staf untuk menangani anak-anak
- 📚 Program edukasi keselamatan berkendara TransJakarta
- 🎫 Prioritas boarding untuk keluarga dengan anak kecil

#### Untuk Lansia
- ♿ Jamin ketersediaan tempat duduk prioritas di semua bus
- 🔍 Informasi visual yang jelas dan mudah dibaca
- 🛠️ Revitalisasi aksesibilitas (ramp, lift, eskalator) di halte prioritas:
  - Ragunan - Gelora Bung Karno
  - Blok M - Kota
  - Kampung Rambutan - Tanjung Priok
- 👨‍⚕️ Petugas siaga untuk membantu mobilitas lansia

### 2. Optimalisasi Operasional Jam Sibuk

#### Pagi (05:00 - 09:00)
- 🚌 **Penambahan Armada** di koridor tersibuk:
  - Cibubur - Balai Kota
  - Ciputat - CSW
  - Pulo Gadung - Monas
- ⏱️ **Kurangi Headway** menjadi 3-5 menit di peak hours
- 🏗️ **Revitalisasi Halte** dengan prioritas:
  1. Garuda Taman Mini (perluasan area tunggu)
  2. Rusun Kapuk Muara (tambah gate tap-in)
  3. Penjaringan (manajemen antrian)

#### Sore (16:00 - 21:00)
- 🚌 **Penambahan Armada** di koridor tersibuk
- 🚪 **Tambah Gate Tap-Out** di halte drop-off utama:
  - Terminal Senen
  - BKN
  - Pinang Ranti
- 👮 **Tambah Petugas** untuk manajemen crowd control
- 🔄 **Optimasi Integrasi Moda** di terminal utama

#### Redistribusi Armada
- 📊 Real-time monitoring okupansi bus
- 🔀 Realokasi armada dari koridor sepi ke koridor padat saat peak hours
- 📱 Implementasi sistem prediksi kepadatan berbasis AI

### 3. Peningkatan Layanan Weekend

- 🎡 Tambah frekuensi bus di rute wisata:
  - JIS - Terminal Muara Angke
  - Pinang Ranti - Bundaran Senayan
- 👨‍👩‍👧‍👦 Prioritaskan bus berkapasitas besar untuk keluarga
- 🎫 Paket tiket khusus weekend untuk wisata keluarga
- 📍 Kolaborasi dengan objek wisata untuk promosi terintegrasi

### 4. Peningkatan Revenue

#### Naming Rights & Advertising
Halte dengan potensi tinggi untuk monetisasi:
1. **Penjaringan** (tap-in sore: 133, tap-out pagi: 162)
2. **BKN** (tap-in sore: 93, tap-out pagi: 150, tap-out sore: 137)
3. **Garuda Taman Mini** (tap-in pagi: 131)
4. **Monas** (tap-out pagi: 129)
5. **Terminal Senen** (tap-out sore: 148)

**Strategi**:
- 💰 **Naming Rights**: Seperti MRT/LRT (estimasi Rp 500jt - 1M/tahun per halte)
- 📺 **Digital Advertising Board**: Di halte dengan traffic tinggi
- 🏢 **Partnership Korporat**: Zona tunggu premium sponsor di halte utama
- 🛍️ **Retail Space**: Kios/vending machine di halte besar

### 5. Implementasi Teknologi

- 📱 **Mobile App Enhancement**:
  - Real-time bus tracking
  - Prediksi okupansi
  - Seat reservation untuk lansia/disabilitas
- 🎟️ **Smart Ticketing**: Integrasi dengan e-wallet
- 📊 **Dashboard Analytics**: Monitoring performa real-time
- 🔔 **Push Notification**: Info gangguan dan alternatif rute

## 📂 Struktur File

```
📦 Transjakarta-Analysis
├── 📄 README.md
├── 📓 Transjakarta_Analysis.ipynb
├── 📊 Transjakarta.csv (data original)
├── 📊 Transjakarta_clean_new.csv (data cleaned)
└── 📊 Tableau Dashboard (link)
```

## 🎨 Dashboard Tableau

Dashboard interaktif dapat diakses di:
[TransJakarta Dashboard](https://public.tableau.com/app/profile/muhammad.zulfan.alghifari/viz/TransJakartaDashboard_17606988230300/ProfilPengguna)




## 📊 Hasil Analisis

### Metrics Summary
- **Total Transaksi Dianalisis**: 34,686
- **Jumlah Koridor**: 216
- **Jumlah Halte**: 2,602
- **Periode Data**: April 2023
- **Jam Sibuk Pagi**: 05:00 - 09:00
- **Jam Sibuk Sore**: 16:00 - 21:00

## 🎯 Impact & Business Value

### Estimated Impact
1. **Peningkatan Kepuasan Pelanggan**: +15-20%
2. **Pengurangan Complaint**: -30%
3. **Peningkatan Ridership**: +10%
4. **Additional Revenue** (naming rights + ads): Rp 5-10M/tahun
5. **Efisiensi Operasional**: +20%


## 👨‍💻 Author

**Muhammad Zulfan Alghifari**

## 📚 References

1. [Tempo.co - Pelecehan Seksual di TransJakarta](https://metro.tempo.co/read/1805094/)
2. [Kompas.id - Halte TransJakarta Inklusif](https://www.kompas.id/baca/metro/2023/03/15/)
3. [Kompas.com - Kepadatan Penumpang](https://megapolitan.kompas.com/read/2023/01/17/)
4. [Suara.com - Naming Rights](https://www.suara.com/lifestyle/2025/03/03/)
