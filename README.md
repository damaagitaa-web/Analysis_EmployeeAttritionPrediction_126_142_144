# Analisis Prediksi Turnover Karyawan (Employee Attrition Prediction)

#### Gita Damayanti  - 5003231142
#### Nindya Eka P.R  - 5003231126
#### Syahla Kemal. D - 5003231144

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

## 2. Data Understanding
### Sumber Data  
Dataset yang digunakan dalam proyek ini diperoleh dari situs [Kaggle](https://www.kaggle.com/competitions/tugas-1-sml-a-2025/data). Data ini berfokus pada prediksi employee attrition atau turnover karyawan. Dataset utama (gabungan train dan test yang diasumsikan) mencakup informasi tentang sekitar **1.470 hingga 2.000 karyawan** (Angka ini merupakan asumsi yang umum untuk dataset attrition).

Dataset ini memiliki **35 variabel**(termasuk variabel target), mencakup aspek seperti usia (Age), gaji (MonthlyIncome), status pernikahan (MaritalStatus), tingkat kepuasan kerja (JobSatisfaction), jam lembur (OverTime), dan riwayat tahunan (TotalWorkingYears, YearsAtCompany), serta faktor-faktor lain yang memengaruhi keputusan bertahan atau keluar.

Di antara seluruh karyawan, sekitar **16% hingga 20%** diasumsikan termasuk dalam kategori Attrition (keluar dari perusahaan). Tingkat ketidakseimbangan kelas ini merupakan tantangan kunci, yang memerlukan penanganan khusus dalam proses pelatihan model prediktif untuk memastikan kinerja yang andal pada kelas minoritas (Attrition=Yes).

---
| Nama Fitur                  | Deskripsi                                                                 |
|----------------------------|---------------------------------------------------------------------------|
| `id`                       | ID unik karyawan untuk identifikasi                                       |
| `Attrition`                | SVariabel Target: apakah karyawan keluar dari perusahaan (1 = Yes/ 0 = No)|
| `BusinessTravel`           | Frekuensi perjalanan dinas (Non-Travel,Travel_Rarely,Travel_Frequently)   |
| `Age`                      | Usia Karyawan                                                             |
| `Gender`                   | Jenis kelamin pelanggan (`M`/`F`)                                         |
| `Department`              | Departemen tempat bekerja (Sales, Research & Development, Human Resources)  |
| `Education`               | Tingkat pendidikan: 1 = Below College, 2 = College, 3 = Bachelor, 4 = Master, 5 = Doctor.                 |
| `DistanceFromHome`         | Jarak tempat tinggal karyawan ke kantor                                  |
| `EducationField`          |Bidang studi terakhir karyawan (contoh: Life Sciences, Medical, Marketing).  |
| `EmployeeCount`            | Jumlah karyawan (selalu 1 dalam dataset)                                   |
| `EmployeeNumber`           | Nomor unik karyawan dalam sistem HR                                      |
| `EnvironmentSatisfaction` | Tingkat kepuasan terhadap lingkungan kerja                                   |
| `HourlyRate`              | Upah per jam                                                                |
| `JobInvolvement`           | Tingkat keterlibatan pekerjaan 1 = Low, 2 = Medium, 3 = High, 4 = Very High.                                         |
| `JobLevel`                | Level jabatan karyawan.                                                           |
| `JobRole`                | Posisi/jabatan spesifik karyawan                                             |
| `JobSatisfaction`         | Tingkat kepuasan pekerjaa                     |
| `MaritalStatus`            | Status pernikahan karyawan (Single, Married, Divorced)                                 |
| `MonthlyIncome`           | Gaji bulanan karyawan                          |
| `MonthlyRate  `          | Total jumlah transaksi selama 12 bulan terakhir                           |
| `NumCompaniesWorked`     | Jumlah perusahaan tempat karyawan pernah bekerja sebelumnya.              |
| `Over18`                    | Status usia di atas 18 tahun (selalu Y dalam dataset)                  |
| `OverTime`                 | Apakah karyawan sering lembur (Yes/No)                                 |
| `PercentSalaryHike`   |Persentase kenaikan gaji tahunan terakhir                                |
| `PerformanceRating`          | Penilaian kinerja terakhir 1 = Low, 2 = Good, 3 = Excellent, 4 = Outstanding.                         |
| `RelationshipSatisfaction`     | Tingkat kepuasan terhadap hubungan kerja    1 = Low, 2 = Medium, 3 = High, 4 = Very High.                             |
| `StandardHours`   |Jam kerja standar (selalu 80 dalam dataset)                               |
| `TotalWorkingYears`          | Total tahun pengalaman kerja.                        |
| `TrainingTimesLastYear`     | Jumlah pelatihan yang diikuti dalam setahun terakhir.                                |
| `StockOptionLevel`   | Level kepemilikan saham perusahaan.                                |
| `WorkLifeBalance`     | Tingkat keseimbangan kerja–hidup: 1 = Bad, 2 = Good, 3 = Better, 4 = Best.                               |
| `YearsAtCompany`   | Total tahun bekerja di perusahaan saat ini.                           |
| `YearsSinceLastPromotion`     | Tahun sejak promosi terakhir.                              |
| `YearsWithCurrManager`   | Tahun bekerja dengan manajer saat ini.                              |
| `YearsInCurrentRole`   | Total tahun di posisi/jabatan saat ini.                              |

---




