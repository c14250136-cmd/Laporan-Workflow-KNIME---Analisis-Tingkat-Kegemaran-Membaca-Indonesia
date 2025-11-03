## 🎯 Deskripsi Proyek
Workflow KNIME ini dirancang untuk menganalisis data Tingkat Kegemaran Membaca (TGM) di Indonesia periode 2020-2023. Workflow ini memproses data dari berbagai provinsi untuk menghasilkan visualisasi yang informatif tentang tren minat baca masyarakat Indonesia.

## 📁 Dataset
**File:** `TGM_2020-2023_clean.csv`

**Kolom-kolom data:**
- `Provinsi` - Nama provinsi di Indonesia
- `Year` - Tahun pengamatan (2020-2023)
- `Reading Frequency per week` - Frekuensi membaca per minggu
- `Number of Readings per Quarter` - Jumlah bacaan per kuartal
- `Daily Reading Duration (in minutes)` - Durasi membaca harian (menit)
- `Internet Access Frequency per Week` - Frekuensi akses internet per minggu
- `Daily Internet Duration (in minutes)` - Durasi internet harian (menit)
- `Tingkat Kegemaran Membaca (Reading Interest)` - Skor indeks minat baca
- `Category` - Kategori tingkat minat baca (High/Moderate)

## 🔄 Alur Workflow

### 1. **CSV Reader** 📥
- **Fungsi:** Membaca file CSV yang berisi data TGM
- **Input:** `TGM_2020-2023_clean.csv`
- **Output:** Tabel data mentah

### 2. **Column Filter** 🔍
- **Fungsi:** Memilih kolom-kolom yang relevan untuk analisis
- **Kolom yang Disertakan:**
  - Year
  - Daily Internet Duration
  - Tingkat Kegemaran Membaca (Reading Interest)
  - Category
- **Kolom yang Dikecualikan:**
  - Provinsi
  - Reading Frequency per week
  - Number of Readings per Quarter
  - Daily Reading Duration
  - Internet Access Frequency per Week

### 3. **Row Filter** 🎚️
- **Fungsi:** Menyaring data berdasarkan kategori minat baca
- **Kriteria:**
  - Filter column: `Category`
  - Operator: `Equals`
  - Value: `High`
  - Case matching: Case sensitive
- **Output:** Hanya data dengan kategori "High" yang lolos

### 4. **Duplicate Row Filter** 🔄
- **Fungsi:** Menghapus data duplikat untuk memastikan keunikan data
- **Kolom untuk Deteksi Duplikat:**
  - Year
  - Daily Internet Duration
  - Tingkat Kegemaran Membaca
  - Category

### 5. **Stacked Area Chart** 📈
- **Fungsi:** Membuat visualisasi area bertumpuk untuk melihat tren
- **Konfigurasi:**
  - Horizontal dimension: `Tingkat Kegemaran Membaca (Reading Interest)`
  - Aggregation: `Average`
  - Frequency dimension: `Year`
- **Tujuan:** Menampilkan rata-rata tingkat kegemaran membaca dari tahun ke tahun

### 6. **Pie Chart** 🥧
- **Fungsi:** Membuat diagram lingkaran untuk distribusi data
- **Konfigurasi:**
  - Category dimension: `Tingkat Kegemaran Membaca (Reading Interest)`
  - Aggregation: `None`
  - Frequency dimension: `Year`
- **Tujuan:** Menunjukkan proporsi distribusi minat baca per tahun

## 📊 Output Visualisasi

### 1. **Stacked Area Chart**
Menampilkan tren rata-rata tingkat kegemaran membaca kategori "High" dari tahun ke tahun dalam format area bertumpuk, memudahkan identifikasi pola peningkatan atau penurunan.

### 2. **Pie Chart**
Menunjukkan distribusi frekuensi tingkat kegemaran membaca berdasarkan tahun untuk kategori "High", memberikan gambaran proporsi data per periode.

## 🎯 Tujuan Analisis
1. Mengidentifikasi tren minat baca tingkat tinggi di Indonesia
2. Menganalisis hubungan antara durasi internet dan tingkat kegemaran membaca
3. Memvisualisasikan distribusi dan perkembangan minat baca dari waktu ke waktu
4. Fokus pada provinsi-provinsi dengan kategori minat baca "High"

## 💡 Insight yang Dapat Diperoleh
- Provinsi mana yang konsisten memiliki tingkat kegemaran membaca tinggi
- Bagaimana tren minat baca berubah dari 2020-2023
- Pola hubungan antara penggunaan internet dan kebiasaan membaca
- Distribusi temporal tingkat kegemaran membaca kategori tinggi

## 🛠️ Cara Menggunakan
1. Buka KNIME Analytics Platform
2. Import workflow ini
3. Pastikan file `TGM_2020-2023_clean.csv` berada di lokasi yang benar
4. Jalankan workflow secara berurutan dari CSV Reader
5. Lihat hasil visualisasi di node Stacked Area Chart dan Pie Chart

## 📝 Catatan
- Workflow ini hanya menganalisis data kategori "High"
- Duplikasi data otomatis dihapus untuk akurasi analisis
- Visualisasi dapat disesuaikan sesuai kebutuhan dengan mengubah konfigurasi pada node chart
