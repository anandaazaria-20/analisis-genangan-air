# Tugas Metodologi Penelitian - Analisis Spasial Genangan Air

**Oleh:** Ananda Azaria Khairunnisa
**Institusi:** IPB University  

---

## 📌 Deskripsi dan Tujuan
Penelitian ini bertujuan untuk mereproduksi analisis deteksi genangan air permukaan secara interaktif menggunakan data citra satelit **Sentinel-2** dan perhitungan **Normalized Difference Water Index (NDWI)**. 

Fokus area studi (*Region of Interest*) pada penelitian ini adalah **Waduk Jatiluhur, Purwakarta**, dengan batasan radius 12 KM dari titik pusat koordinat. Pengambilan citra difokuskan pada periode **musim kemarau (Juni - September 2024)** untuk meminimalisir tutupan awan sehingga objek badan air dapat terekstraksi dengan sempurna.

## 📂 Struktur Repositori
Repositori ini terdiri dari beberapa berkas pendukung untuk memastikan riset dapat direproduksi dengan baik:
```text
analisis-genangan-air/
│
├── analisis_air_permukaan.ipynb   # Skrip utama analisis spasial (Jupyter/Colab)
├── requirements.txt               # Daftar pustaka/library Python yang dibutuhkan
├── README.md                      # Dokumentasi alur kerja repositori
└── LICENSE                        # Lisensi hak cipta kode (MIT)
