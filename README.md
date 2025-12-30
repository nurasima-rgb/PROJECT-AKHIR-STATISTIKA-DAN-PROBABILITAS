# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun
- **Nama:** Nur Asima Manik
- **NIM:** 2515091006
- **Program Studi:** Sistem Informasi
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek
Dataset yang digunakan merupakan data startup SaaS yang terdiri dari 650 observasi dan 6 variabel numerik. Pada analisis ini, saya ingin menyoroti hubungan antara Pendapatan_Tahunan_Miliar_IDR sebagai variabel dependen dan Biaya_Akuisisi_Pelanggan_Juta_IDR sebagai variabel independen. Tujuan analisis ini untuk memahami karatkteristik distribusi data, menguji asumsi normalitas, mengidentifikasi kekuatan hubungan antarvariabel, serta membangun model regresi guna memprediksi pendapatan tahunan startup SaaS

---

## 3. Struktur Proyek
Proyek ini diorganisir ke dalam beberapa folder:
- `/data`: Berisi dataset mentah yang digunakan untuk analisis.
- `/scripts`: Berisi semua skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results`: Berisi output dari analisis, seperti plot, gambar, atau tabel ringkasan.
- README.md: dokumentasi lengkap proyek
  
---

## 4. Cara Menjalankan Analisis
Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi
### 5.1. Statistik Deskriptif
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - Mean: 31.88 miliar IDR
  - Median: 31.30 miliar IDR
  - Modus: 1.87 miliar IDR
  - *Interpretasi:* Nilai Mean dan Median yang relatif berdekatan yang artinya pusat data pendapatan berada pada kisaran yang sama, meskipun terdapat nilai ekstrem pada data.
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - Standar deviasi: 19.79
  - Range: 1.00 - 66.90
  - kuartil (Q1-Q3): 14.30 - 49.00
  - *Interpretasi:* Nilai standar deviasi dan range yang cukup besar menunjukkan bahwa data pendapatan memiliki tingkat variasi yang tinggi antar startup.
- **Visualisasi (Histogram/Boxplot):**
  *Interpretasi:* Histogram menunjukkan distribusi pendapatan yang tidak simetris dan cenderung memiliki ekor kanan. dan Boxplot memperlihatkan adanya beberapa nilai ekstrem pada pendapatan tinggi. Dari visualisasi tersebut mengindikasikan bahwa sebagian besar startup memiliki pendapatan menengah, sementara beberapa startup memiliki pendapatan yang jauh lebih tinggi.

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value: 0
  - *Interpretasi:* Karena nilai p-value ≤ 0.05, maka data pendapatan tahunan tidak terdistribusi normal.
- **Plot Q-Q:**
  - *Interpretasi:* Titik-titik pada Q-Q plot tidak mengikuti garis diagonal secara sempurna. Pola ini memperkuat hasil uji Shapiro-Wilk bahwa data tidak memenuhi asumsi normalitas.

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai koefisien korelasi (r):* 0.996.
  - *Interpretasi:* Nilai koefisien korelasi yang mendekati 1 menunjukan hubungan antara biaya akuisisi pelanggan dan pendapatan tahunan startup SaaS tergolong Sangat kuat dan bersifat positif. Hubungan positif ini berarti, terdapat peningkatan biaya akuisisi pelanggan cenderung diikuti oleh peningkatan pendapatan tahunan perusahaan. Secara statistik, nilai korelasi yang tinggi mengindikasikan bahwa, kedua variabel bergerak searah dan memiliki keterkaitan yang konsisten.
- **Visualisasi (Scatter Plot):**
   *Interpretasi:* Scatter plot menunjukkan pola titik data yang membentuk garis naik dari kiri ke kanan. Pola linear yang terlihat pada scatter plot memperkuat hasil perhitungan koefisien korelasi. Titik-titik data yang tersebar rapat di sekitar garis imajiner menunjukkan, hubungan antara biaya akuisisi pelanggan dan pendapatan bersifat stabil dan tidak acak. Hal ini mengindikasikan bahwa strategi pengeluaran perusahaan untuk memperoleh pelanggan memiliki kontribusi nyata terhadap peningkatan pendapatan startup SaaS.

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = -1.06 + 0.98X
  - *Interpretasi:* Model regresi linier sederhana ini menunjukkan hubungan kuantitatif antara biaya akuisisi pelanggan sebagai variabel independen dan pendapatan tahunan sebagai variabel dependen. Nilai intercept sebesar -1.06 menggambarkan nilai pendapatan ketika biaya akuisisi pelanggan bernilai nol. Sementara itu, nilai koefisien slope sebesar 0.98 menunjukkan, setiap kenaikan 1 juta IDR biaya akuisisi pelanggan akan meningkatkan pendapatan tahunan startup sekitar 0.98 miliar IDR.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared*: 0.991
  - *Interpretasi:* Nilai Adjusted R-squared yang sangat tinggi menunjukkan bahwa sekitar 99.1% variasi pendapatan tahunan startup SaaS dapat dijelaskan oleh variasi biaya akuisisi pelanggan. Hal ini menandakan bahwa model regresi memiliki tingkat kecocokan yang sangat baik dan kemampuan prediktif yang kuat.
- **Visualisasi (Garis Regresi pada Scatter Plot):**
   *Interpretasi:* Garis regresi yang ditampilkan pada scatter plot menunjukkan kecocokan yang sangat baik dengan sebaran data. Garis regresi yang mengikuti pola titik data mengonfirmasi bahwa hubungan antara biaya akuisisi pelanggan dan pendapatan bersifat linear dan konsisten. Visualisasi ini memperjelas bahwa peningkatan biaya akuisisi pelanggan secara sistematis berkaitan dengan peningkatan pendapatan, sehingga model regresi yang dibangun dapat digunakan sebagai dasar dalam pengambilan keputusan bisnis terkait strategi pemasaran dan pertumbuhan startup.
    
---

## 6. Kesimpulan
Berdasarkan hasil analisis statistik yang telah dilakukan, dapat disimpulkan bahwa data pendapatan tahunan startup SaaS tidak terdistribusi normal dan memiliki tingkat variasi yang cukup tinggi antar perusahaan. Hasil analisis korelasi menunjukkan adanya hubungan positif yang sangat kuat dan signifikan antara biaya akuisisi pelanggan dan pendapatan tahunan startup SaaS. Model regresi linier sederhana yang dibangun memperlihatkan bahwa biaya akuisisi pelanggan merupakan prediktor yang sangat kuat dalam menjelaskan dan memprediksi pendapatan tahunan, dengan nilai R-squared yang sangat tinggi. Temuan ini memberikan wawasan penting bahwa peningkatan investasi dalam akuisisi pelanggan berpotensi memberikan dampak langsung dan signifikan terhadap peningkatan pendapatan startup SaaS, sehingga strategi pemasaran dan pengelolaan pelanggan menjadi faktor kunci dalam pertumbuhan bisnis.
