# Analisis Prediksi Turnover Karyawan (Employee Attrition Prediction)

### Gita Damayanti  - 5003231142
### Syahla Kemal. D - 5003231144
### Nindya Eka P.R  - 5003231126

---

## **Domain Proyek: Sumber Daya Manusia (SDM)**

## 1. Business Understanding

### Problem Statements  
Tingkat turnover karyawan yang tinggi menimbulkan biaya besar (rekrutmen, pelatihan), mengganggu produktivitas, dan berdampak negatif pada moral tim. Mengidentifikasi faktor-faktor pemicu turnover adalah kunci untuk menjaga keberlanjutan dan daya saing perusahaan.

Berdasarkan hal tersebut, berikut adalah pernyataan masalah yang diangkat:

- **Pernyataan Masalah 1:** Bagaimana mengidentifikasi pola dan fitur (demografis, lingkungan kerja, beban kerja, kepuasan) yang paling signifikan memengaruhi keputusan karyawan untuk keluar (attrition)?
- **Pernyataan Masalah 2:** Bagaimana membangun model prediktif yang akurat yang mampu memperkirakan kemungkinan karyawan akan keluar, sambil mengatasi tantangan ketidakseimbangan kelas dan kompleksitas interaksi antar fitur? 
- **Pernyataan Masalah 3:** Bagaimana memastikan interpretabilitas model untuk memberikan wawasan strategis yang jelas bagi manajemen SDM, sehingga solusi yang dihasilkan dapat diterapkan secara nyata dan bermanfaat?

---

### Goals  
Untuk menjawab pernyataan masalah di atas, tujuan proyek ini dirumuskan sebagai berikut:

- **Tujuan 1:** Melakukan eksplorasi data untuk mengidentifikasi faktor-faktor utama yang memicu turnover karyawan.
- **Tujuan 2:** Mengembangkan dan mengoptimalkan model klasifikasi yang memiliki performa tinggi dan keandalan dalam memprediksi risiko attrition (termasuk penanganan ketidakseimbangan kelas).
- **Tujuan 3:** Menyediakan analisis fitur paling berpengaruh dan rekomendasi berbasis data yang dapat digunakan manajemen untuk intervensi retensi secara tepat sasaran.

---

### Solution Statements  
Untuk mencapai tujuan-tujuan tersebut, solusi yang akan diimplementasikan meliputi:

- **Eksperimen Berbagai Algoritma Klasifikasi:**  
   Membangun dan membandingkan performa model yang kuat seperti:
  - Decision Tree  
  - Random Forest  
  - LightGBM  

- **Optimasi Model dengan Hyperparameter Tuning:**  
  Menggunakan pendekatan sistematis untuk mendapatkan konfigurasi model terbaik.

- **Evaluasi Model dengan Metrik yang Relevan:**  
  Menggunakan metrik seperti:
  - Accuracy untuk mengukur prediksi keseluruhan  
  - Precision, Recall, F1-Score untuk menilai performa pada kelas churn  
  - ROC-AUC untuk mengevaluasi kemampuan model dalam membedakan kelas  
  - Confusion Matrix untuk melihat distribusi hasil prediksi

- **Analisis Fitur dan Visualisasi:**  
  Menyajikan visualisasi seperti feature importance dan correlation heatmap untuk menginterpretasikan fitur-fitur utama yang berkontribusi terhadap churn.

---

### Project Benefits  
Dengan implementasi solusi ini, manfaat utama yang diharapkan antara lain:

- **Pengurangan Biaya Turnover**: Mengurangi pengeluaran untuk rekrutmen dan pelatihan karyawan baru.  
- **Peningkatan Retensi Karyawan**: Memungkinkan intervensi proaktif dan terpersonalisasi pada karyawan berisiko tinggi.  
- **Wawasan Strategis yang Jelas**: Menyediakan pemahaman yang transparan mengenai pemicu attrition untuk perbaikan kebijakan internal.
- **Peningkatan Stabilitas Tenaga Kerja**: Menjaga kesinambungan operasional dan moral tim.  

---


