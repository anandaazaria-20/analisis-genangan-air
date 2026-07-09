# Tugas Metodologi Penelitian - Analisis Spasial Genangan Air

**Oleh:** Ananda Azaria Khairunnisa (Nanda)  
**Institusi:** IPB University  

---

## 📌 Deskripsi dan Tujuan
Penelitian ini bertujuan untuk mereproduksi analisis deteksi genangan air permukaan secara interaktif menggunakan data citra satelit **Sentinel-2** dan perhitungan **Normalized Difference Water Index (NDWI)**. 

Fokus area studi (*Region of Interest*) pada penelitian ini adalah **Waduk Jatiluhur, Purwakarta**, dengan batasan radius 12 KM dari titik pusat koordinat. Pengambilan citra difokuskan pada periode **musim kemarau (Juni - September 2024)** untuk meminimalisir tutupan awan sehingga objek badan air dapat terekstraksi dengan sempurna.

## 📂 Struktur Repositori
Repositori ini terdiri dari beberapa berkas pendukung untuk memastikan riset dapat direproduksi dengan baik:

    analisis-genangan-air/
    │
    ├── analisis_air_permukaan.ipynb   # Skrip utama analisis spasial (Jupyter/Colab)
    ├── requirements.txt               # Daftar pustaka/library Python yang dibutuhkan
    ├── README.md                      # Dokumentasi alur kerja repositori
    └── LICENSE                        # Lisensi hak cipta kode (MIT)

## 🛠️ Software dan Spesifikasi Lingkungan
Analisis ini tidak memproses data satelit secara lokal karena ukuran data yang masif, melainkan menggunakan komputasi berbasis awan (*cloud-computing*).
* **Bahasa Pemrograman:** Python 3
* **Platform:** Google Colab / Jupyter Lab
* **Data Sumber:** Copernicus Sentinel-2 Level-2A Surface Reflectance
* **Cloud API:** Google Earth Engine (GEE)
* **Library Utama:** `earthengine-api` (untuk komputasi spasial), `geemap` (untuk visualisasi peta interaktif)

## 🔄 Alur dan Langkah Analisis
Kode di dalam riset ini bekerja secara sekuensial dengan alur kerja berikut:
1. **Autentikasi & Inisialisasi:** Menghubungkan skrip dengan *server* Google Earth Engine menggunakan *Project ID* yang terdaftar.
2. **Penentuan Area (ROI):** Membuat geometri titik pusat dan melakukan *buffering* sejauh radius 12.000 meter (12 KM).
3. **Penyaringan Citra (Filtering):** Memanggil koleksi Sentinel-2, memfilter berdasarkan lokasi (Waduk Jatiluhur), rentang waktu (musim kemarau 2024), dan mereduksi awan menggunakan nilai median.
4. **Perhitungan Indeks (NDWI):** Melakukan kalkulasi matematis antara pita warna Hijau (*Band 3*) dan Inframerah Dekat (*Band 8*).
5. **Masking & Clipping:** Menyaring hanya piksel yang merepresentasikan air (NDWI > 0) dan memotong (*clip*) visualisasinya agar presisi berada di dalam lingkaran radius 12 KM.

## 🚀 Cara Menjalankan (Reproduksi)
Bagi pengguna yang ingin menjalankan ulang riset ini, ikuti langkah berikut:
1. Pastikan Anda memiliki proyek Google Cloud yang telah disetujui untuk akses Google Earth Engine (Non-Komersial/Akademik).
2. Buat *environment* Python baru dan pasang pustaka yang dibutuhkan melalui terminal/CMD: 
   `pip install -r requirements.txt`
3. Buka file `analisis_air_permukaan.ipynb`.
4. Sesuaikan `ee.Initialize(project='NAMA_PROJECT_ANDA')` dengan ID proyek Google Cloud Anda.
5. Jalankan seluruh sel kode dari atas ke bawah (*Run All*). 
6. Berikan izin akses (*Allow/Continue*) pada *pop-up* autentikasi Google yang muncul.

## 📊 Output
Skrip akan menghasilkan sebuah antarmuka peta interaktif yang memuat dua lapisan (*layers*):
1. **Citra Asli (Jatiluhur - Kemarau):** Kondisi daratan asli Waduk Jatiluhur dengan *True Color Composite*.
2. **Deteksi Genangan Air:** Hamparan piksel berwarna biru terang yang mengekstraksi dan memisahkan tubuh air waduk dari daratan di sekitarnya secara otomatis.
