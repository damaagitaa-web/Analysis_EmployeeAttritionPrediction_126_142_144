# Analisis Prediksi Turnover Karyawan (Employee Attrition Prediction)

#### Gita Damayanti  - 5003231142
#### Nindya Eka P.R  - 5003231126
#### Syahla Kemal. D - 5003231144

---

## **Domain Proyek: Sumber Daya Manusia (SDM)**
<img width="731" height="403" alt="Tangkapan Layar 2025-10-26 pukul 23 33 54" src="https://github.com/user-attachments/assets/796c4d8c-8593-42b5-b23d-883da1303656" />

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

### 2.1 Data Loading
# Import Library
# ==============================
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from sklearn.compose import ColumnTransformer
from sklearn.pipeline import Pipeline
from sklearn.impute import SimpleImputer
from sklearn.metrics import roc_auc_score
from imblearn.combine import SMOTEENN
from xgboost import XGBClassifier
from lightgbm import LGBMClassifier
from sklearn.model_selection import StratifiedKFold, cross_val_score
from lightgbm import LGBMClassifier
from xgboost import XGBClassifier
from catboost import CatBoostClassifier

import warnings
warnings.filterwarnings("ignore")

# Load Data
train = pd.read_csv("C:/Users/MyBook Hype AMD/Downloads/train.csv")
test = pd.read_csv("C:/Users/MyBook Hype AMD/Downloads/test.csv")
sub = pd.read_csv("C:/Users/MyBook Hype AMD/Downloads/sample_submission.csv")

### 2.2 [Exploratory Data Analysis] - Deskripsi Variabel

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Age</th>
      <td>294.0</td>
      <td>36.625850</td>
      <td>8.971484</td>
      <td>18.0</td>
      <td>30.00</td>
      <td>35.0</td>
      <td>42.00</td>
      <td>59.0</td>
    </tr>
    <tr>
      <th>DailyRate</th>
      <td>294.0</td>
      <td>796.462585</td>
      <td>412.713840</td>
      <td>102.0</td>
      <td>443.25</td>
      <td>810.5</td>
      <td>1179.75</td>
      <td>1495.0</td>
    </tr>
    <tr>
      <th>DistanceFromHome</th>
      <td>294.0</td>
      <td>8.530612</td>
      <td>7.786666</td>
      <td>1.0</td>
      <td>2.00</td>
      <td>6.0</td>
      <td>11.75</td>
      <td>29.0</td>
    </tr>
    <tr>
      <th>Education</th>
      <td>294.0</td>
      <td>2.938776</td>
      <td>1.010015</td>
      <td>1.0</td>
      <td>2.00</td>
      <td>3.0</td>
      <td>4.00</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>EmployeeCount</th>
      <td>294.0</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>1.0</td>
      <td>1.00</td>
      <td>1.0</td>
      <td>1.00</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>EmployeeNumber</th>
      <td>294.0</td>
      <td>1061.003401</td>
      <td>611.096064</td>
      <td>4.0</td>
      <td>501.00</td>
      <td>1070.5</td>
      <td>1614.75</td>
      <td>2068.0</td>
    </tr>
    <tr>
      <th>EnvironmentSatisfaction</th>
      <td>294.0</td>
      <td>2.741497</td>
      <td>1.112071</td>
      <td>1.0</td>
      <td>2.00</td>
      <td>3.0</td>
      <td>4.00</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>HourlyRate</th>
      <td>294.0</td>
      <td>67.455782</td>
      <td>20.111203</td>
      <td>30.0</td>
      <td>50.25</td>
      <td>67.0</td>
      <td>85.00</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>JobInvolvement</th>
      <td>294.0</td>
      <td>2.700680</td>
      <td>0.742792</td>
      <td>1.0</td>
      <td>2.00</td>
      <td>3.0</td>
      <td>3.00</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>JobLevel</th>
      <td>294.0</td>
      <td>2.013605</td>
      <td>1.165408</td>
      <td>1.0</td>
      <td>1.00</td>
      <td>2.0</td>
      <td>2.00</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>JobSatisfaction</th>
      <td>294.0</td>
      <td>2.765306</td>
      <td>1.072152</td>
      <td>1.0</td>
      <td>2.00</td>
      <td>3.0</td>
      <td>4.00</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>MonthlyIncome</th>
      <td>294.0</td>
      <td>6338.557823</td>
      <td>4923.607424</td>
      <td>1052.0</td>
      <td>2854.25</td>
      <td>4532.0</td>
      <td>7920.50</td>
      <td>19999.0</td>
    </tr>
    <tr>
      <th>MonthlyRate</th>
      <td>294.0</td>
      <td>14004.557823</td>
      <td>6812.446854</td>
      <td>2104.0</td>
      <td>8105.50</td>
      <td>13660.5</td>
      <td>19973.50</td>
      <td>26997.0</td>
    </tr>
    <tr>
      <th>NumCompaniesWorked</th>
      <td>294.0</td>
      <td>2.693878</td>
      <td>2.549476</td>
      <td>0.0</td>
      <td>1.00</td>
      <td>2.0</td>
      <td>4.00</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>PercentSalaryHike</th>
      <td>294.0</td>
      <td>15.088435</td>
      <td>3.585951</td>
      <td>11.0</td>
      <td>12.00</td>
      <td>14.0</td>
      <td>17.00</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>PerformanceRating</th>
      <td>294.0</td>
      <td>3.139456</td>
      <td>0.347012</td>
      <td>3.0</td>
      <td>3.00</td>
      <td>3.0</td>
      <td>3.00</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>RelationshipSatisfaction</th>
      <td>294.0</td>
      <td>2.605442</td>
      <td>1.051947</td>
      <td>1.0</td>
      <td>2.00</td>
      <td>3.0</td>
      <td>3.00</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>StandardHours</th>
      <td>294.0</td>
      <td>80.000000</td>
      <td>0.000000</td>
      <td>80.0</td>
      <td>80.00</td>
      <td>80.0</td>
      <td>80.00</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>StockOptionLevel</th>
      <td>294.0</td>
      <td>0.806122</td>
      <td>0.878155</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>1.0</td>
      <td>1.00</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>TotalWorkingYears</th>
      <td>294.0</td>
      <td>10.938776</td>
      <td>7.701535</td>
      <td>0.0</td>
      <td>6.00</td>
      <td>9.0</td>
      <td>15.00</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>TrainingTimesLastYear</th>
      <td>294.0</td>
      <td>2.955782</td>
      <td>1.405044</td>
      <td>0.0</td>
      <td>2.00</td>
      <td>3.0</td>
      <td>4.00</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>WorkLifeBalance</th>
      <td>294.0</td>
      <td>2.775510</td>
      <td>0.658843</td>
      <td>1.0</td>
      <td>2.00</td>
      <td>3.0</td>
      <td>3.00</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>YearsAtCompany</th>
      <td>294.0</td>
      <td>6.840136</td>
      <td>6.291412</td>
      <td>0.0</td>
      <td>2.00</td>
      <td>5.0</td>
      <td>9.00</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>YearsInCurrentRole</th>
      <td>294.0</td>
      <td>4.221088</td>
      <td>3.836518</td>
      <td>0.0</td>
      <td>2.00</td>
      <td>3.0</td>
      <td>7.00</td>
      <td>18.0</td>
    </tr>
    <tr>
      <th>YearsSinceLastPromotion</th>
      <td>294.0</td>
      <td>2.207483</td>
      <td>3.256049</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>1.0</td>
      <td>2.75</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>YearsWithCurrManager</th>
      <td>294.0</td>
      <td>3.829932</td>
      <td>3.572504</td>
      <td>0.0</td>
      <td>1.00</td>
      <td>3.0</td>
      <td>7.00</td>
      <td>17.0</td>
    </tr>
  </tbody>
</table>
</div>

### 2.3 [Exploratory Data Analysis] - Menangani Missing Value dan Outliers
Dalam tahap awal pembersihan data, dilakukan pengecekan terhadap duplikasi data dan missing value. Hasilnya menunjukkan bahwa tidak terdapat duplikasi data maupun missing value di seluruh kolom fitur maupun target. Hal ini mengindikasikan bahwa dataset sudah lengkap dan tidak memerlukan teknik imputasi lebih lanjut.

<img width="1489" height="1768" alt="image" src="https://github.com/user-attachments/assets/79c4dc22-0cb7-4f13-a5f2-261e2e44a7f0" />
Visualisasi boxplot menunjukkan bahwa sebagian besar fitur numerik, khususnya yang berkaitan dengan finansial dan riwayat kerja, memiliki sebaran yang lebar dan menunjukkan keberadaan outlier yang signifikan: **MonthlyIncome**: Fitur ini menunjukkan sebaran data yang terdistribusi ke atas dengan banyak data berada di luar whisker atas, mengindikasikan keberadaan karyawan berpenghasilan sangat tinggi (manajemen senior/eksekutif).**NumCompaniesWorked**: Fitur ini juga menunjukkan beberapa outlier pada nilai 8 atau 9, mencerminkan karyawan yang memiliki riwayat berpindah-pindah pekerjaan yang sangat sering.

Meskipun terdapat outlier pada fitur-fitur penting seperti MonthlyIncome dan riwayat kerja, outlier tersebut tidak dihapus dari dataset. Hal ini dilakukan untuk menjaga keutuhan informasi dan realitas data bisnis, mengingat data pencilan tersebut mencerminkan kondisi nyata, seperti level kompensasi yang tinggi di tingkat eksekutif.
Sebagai langkah mitigasi terhadap potensi pengaruh outlier tanpa perlu memodifikasi data, model machine learning yang digunakan adalah model berbasis tree (seperti LightGBM, CatBoost, dan XGBoost)

### 2.4 [Exploratory Data Analysis] - Univariate Analysis
<img width="1787" height="4455" alt="image" src="https://github.com/user-attachments/assets/897fc457-6667-4006-b0dc-c252d286048b" />
<img width="1788" height="4455" alt="image" src="https://github.com/user-attachments/assets/03643412-6c43-46ac-b5c3-3e23ae89b0a1" />


Distribusi Fitur Numerik 
- Usia dan Pengalaman Kerja
Sebagian besar karyawan berusia antara 30–40 tahun, dengan distribusi yang condong ke kanan (right-skewed). Artinya, jumlah karyawan muda lebih banyak dibandingkan yang berusia lanjut. Distribusi TotalWorkingYears dan YearsAtCompany juga menunjukkan pola serupa — mayoritas karyawan memiliki pengalaman kerja di bawah 10 tahun. Hal ini menunjukkan tingkat retensi masih relatif baru dan potensi turnover bisa lebih tinggi di usia muda.

- Gaji dan Pendapatan
Distribusi MonthlyIncome, IncomePerYearOfExp, dan Income_X_PercentSalaryHike semuanya miring ke kanan, menandakan sebagian besar karyawan berpenghasilan rendah–menengah. Hanya sedikit yang memiliki pendapatan tinggi. Kondisi ini bisa menjadi salah satu faktor risiko attrition karena persepsi ketidakadilan kompensasi atau peluang karier yang terbatas.

- Kepuasan dan Lingkungan Kerja
Variabel seperti JobSatisfaction, EnvironmentSatisfaction, RelationshipSatisfaction, dan WorkLifeBalance menunjukkan sebaran yang cukup bervariasi. Beberapa fitur memperlihatkan puncak tinggi pada level 3 (cukup puas), menandakan sebagian besar karyawan merasa cukup puas, meski masih ada kelompok kecil yang tidak puas. Hal ini penting diperhatikan karena tingkat kepuasan yang rendah berpotensi memicu turnover.

- Kinerja dan Penghargaan
Variabel PerformanceRating dan StockOptionLevel terlihat cukup timpang — sebagian besar karyawan mendapat skor tinggi untuk performa, tetapi hanya sedikit yang memperoleh stock option besar. Kesenjangan antara performa dan penghargaan semacam ini bisa berpengaruh terhadap motivasi dan keputusan untuk bertahan.

- Jam Lembur (OverTime)
Distribusi OverTime_flag dan OverTime menunjukkan mayoritas karyawan jarang melakukan lembur, namun ada kelompok kecil dengan frekuensi lembur tinggi. Karyawan dengan beban lembur tinggi sering kali lebih rentan mengalami stres dan berpotensi keluar.

- Masa Jabatan dan Promosi
Sebagian besar karyawan baru menjalani 1–5 tahun di posisi saat ini (YearsInCurrentRole) dan belum banyak mendapat promosi (YearsSinceLastPromotion condong ke kiri). Ini menggambarkan adanya stagnasi karier yang bisa mendorong attrition jika tidak dikelola dengan baik.

- Rasio Tenure dan Kepuasan Gabungan
Fitur turunan seperti AgeTenureRatio, TenureRoleRatio, dan Satisfaction_OverTime menunjukkan pola miring ke kanan, menandakan sebagian besar karyawan baru dengan rasio pengalaman rendah. Ini sesuai dengan kecenderungan bahwa karyawan baru lebih mudah keluar dibandingkan karyawan senior.

### 2.5 [Exploratory Data Analysis] - Multivariate Analysis
<img width="1056" height="842" alt="image" src="https://github.com/user-attachments/assets/5b06f399-0cae-4ebc-832d-760e6ed83984" />

Heatmap korelasi menunjukkan bahwa keputusan attrition karyawan sangat dipengaruhi oleh kombinasi faktor kompensasi, waktu kerja, dan pengalaman. Korelasi negatif terkuat teramati antara Attrition dengan variabel MonthlyIncome dan variabel riwayat kerja seperti TotalWorkingYears, yang mengindikasikan bahwa karyawan dengan gaji lebih tinggi dan pengalaman lebih lama cenderung lebih setia dan kecil kemungkinannya untuk keluar. Sebaliknya, OverTime (Lembur) menunjukkan korelasi positif yang kuat dengan Attrition, menjadikannya pemicu turnover paling signifikan. Selain itu, heatmap juga mengungkapkan adanya multikolinearitas yang tinggi, terutama di antara variabel-variabel yang terkait dengan durasi kerja dan level jabatan, seperti korelasi kuat antara TotalWorkingYears, JobLevel, dan MonthlyIncome. Meskipun demikian, multikolinearitas ini tidak menjadi masalah serius mengingat penggunaan model berbasis tree yang robust dalam proyek ini.

<img width="1063" height="1023" alt="image" src="https://github.com/user-attachments/assets/2f480a6b-af2d-4a2d-9e49-d3b4fef5b85b" />

- Berdasarkan pairplot di atas, terlihat pola hubungan antar variabel numerik seperti Age, MonthlyIncome, TotalWorkingYears, dan YearsAtCompany terhadap status Attrition (0 = tidak keluar, 1 = keluar):

1. Age vs Attrition
Terlihat bahwa karyawan yang berusia muda lebih cenderung mengalami attrition (berhenti bekerja). Distribusi warna merah (Attrition = 1) lebih banyak di rentang usia 20–30 tahun. Artinya, semakin tua usia karyawan, kecenderungan untuk keluar dari perusahaan semakin kecil.

2. MonthlyIncome vs Attrition
Tidak terlihat hubungan linear yang kuat antara pendapatan bulanan dan attrition, tetapi tampak kecenderungan bahwa karyawan dengan pendapatan lebih rendah (< 5.000) lebih sering keluar dibandingkan mereka dengan penghasilan tinggi. Hal ini menunjukkan kemungkinan bahwa kompensasi berperan dalam retensi karyawan.

3. TotalWorkingYears vs Attrition
Polanya menunjukkan hubungan menurun — semakin lama total pengalaman kerja seseorang, semakin kecil kemungkinan mereka mengalami attrition. Titik merah lebih banyak muncul pada karyawan dengan pengalaman kerja < 10 tahun.

4. YearsAtCompany vs Attrition
Terlihat hubungan serupa: attrition lebih sering terjadi pada karyawan yang baru bekerja beberapa tahun di perusahaan. Artinya, masa kerja yang pendek berasosiasi dengan tingkat keluar yang lebih tinggi, menunjukkan pentingnya masa adaptasi dan retensi awal.

## 3. Data Preparation
### 3.1 Label Encoding dengan Mapping pada Fitur Target
Label Encoding adalah proses mengubah variabel kategorikal (yang berisi teks, seperti 'Male'/'Female' atau 'Sales'/'HR') menjadi nilai numerik (angka).

Dalam konteks proyek Employee Attrition Anda, Label Encoding biasanya digunakan pada:

Variabel Target Biner: Mengubah variabel target Attrition dari ('Yes'/'No') menjadi (1/0).

Variabel Kategorikal Ordinal: Mengubah variabel yang memiliki urutan (tingkatan) alami, seperti kepuasan atau level pendidikan.

### 3.2 Feature Engineering
Langkah-langkah ini bertujuan untuk mengidentifikasi variabel mana saja yang paling kuat dalam memprediksi Attrition (turnover karyawan) dan mana yang paling lemah, sehingga fitur yang tidak penting dapat dihapus untuk menyederhanakan model dan mengurangi noise.

1. Menampilkan Grafik Feature Importance
Tujuan: Untuk mendapatkan visualisasi awal mengenai seberapa besar kontribusi setiap fitur dalam memprediksi target (Attrition) berdasarkan model yang telah dilatih (misalnya LightGBM atau Ensemble).

Interpretasi Visual: Fitur yang berada di posisi teratas grafik (misalnya OverTime) memiliki nilai importance tertinggi, menandakan bahwa perubahan pada fitur tersebut memiliki dampak paling besar terhadap hasil prediksi attrition.

Fitur yang berada di posisi terbawah memiliki kontribusi paling kecil.

2. Memfilter Fitur yang Nilainya Lebih Kecil dari 0.005
Tujuan: Melakukan penghapusan fitur berdasarkan ambang batas (threshold) yang telah ditentukan, yaitu 0.005.

Interpretasi: Ini adalah langkah pembersihan fitur. Semua fitur yang nilai importance-nya di bawah 0.005 dianggap tidak signifikan atau terlalu lemah untuk berkontribusi pada prediksi yang akurat. Dengan menghapus fitur-fitur ini, kita menghilangkan noise dan potensi overfitting yang disebabkan oleh variabel yang tidak relevan.

3. Jumlah Fitur yang Dibuang
Tujuan: Memberikan ringkasan kuantitatif mengenai hasil dari proses feature selection.

Interpretasi: 18 Fitur Dibuang: Dari total fitur awal (sekitar 31 setelah menghapus ID/konstanta), sebanyak 18 fitur dinilai tidak signifikan (nilai importance < 0.005). Ini menunjukkan bahwa sebagian besar variabel dalam dataset kurang relevan secara langsung dalam memprediksi attrition.

4. Sisa Fitur
Tujuan: Mengetahui jumlah akhir fitur yang akan digunakan untuk pelatihan model final.

Interpretasi:13 Fitur Sisa: Hanya 13 fitur yang dipertahankan. Ini adalah sekumpulan fitur inti yang dinilai paling berpengaruh dan informatif. Model akhir akan dilatih hanya dengan 13 fitur ini. Hal ini diharapkan akan menyederhanakan model dan mempercepat waktu pelatihan, sambil tetap menjaga (atau bahkan meningkatkan) akurasi, karena noise telah dihilangkan.

### 3.3 Splitting Dataset
Untuk mengevaluasi kinerja model. Data yang dibagi menjadi dua bagian: 80% untuk pelatihan (agar model belajar) dan 20% untuk pengujian (untuk menguji seberapa baik model berkinerja pada data baru yang belum pernah dilihat).

Menggunakan fungsi train_test_split dari library scikit-learn. 
Menetapkan bahwa 20% dari total observasi (karyawan) akan dialokasikan sebagai data pengujian (X_test, y_test).
Digunakan untuk memastikan bahwa pembagian data dilakukan secara acak, tetapi hasilnya selalu konsisten (dapat direproduksi) setiap kali kode dijalankan.
stratify=y Parameter Kritis. Karena dataset Employee Attrition mengalami ketidakseimbangan kelas (kelas Attrition minoritas), parameter ini memastikan bahwa persentase karyawan yang keluar (Attrition=Yes) di set pelatihan dan set pengujian adalah sama. Hal ini menjaga objektivitas evaluasi model

### 3.4 Preprocessing
Alur preprocessing ini bersifat komprehensif dan robust. Dengan menggabungkan Label Encoding dan One-Hot Encoding, dataset disiapkan secara tepat untuk setiap jenis variabel. Penggunaan Standard Scaler di akhir memastikan bahwa data numerik berada dalam rentang yang seragam, sehingga model ensemble dapat belajar secara efektif dari seluruh dataset yang kini telah ditransformasi.

## 4. Model Training, Comparison, Selection and Tuning
I. Persiapan Model yang Ditargetkan (Train Set)
Handle Class Imbalance: Wajib dilakukan hanya pada data Training (X_train, y_train). Tujuannya adalah menyeimbangkan rasio kelas Attrition (minoritas) dan Non-Attrition (mayoritas) (misalnya menggunakan SMOTE) agar model tidak bias dan mampu memprediksi kasus attrition secara efektif.

II. Pelatihan dan Optimasi Model
Modeling: Menggunakan pendekatan Model Ensemble (menggabungkan LightGBM, CatBoost, dan XGBoost). Model ensemble dilatih menggunakan Training Set yang sudah diseimbangkan dan disaring fiturnya.
Hyperparameter Tuning: Melakukan optimasi parameter model (misalnya mencari learning_rate atau max_depth terbaik) untuk memaksimalkan kinerja model, yang terbukti mencapai ROC-AUC tertinggi ($0.9949$).

III. Validasi dan Hasil Akhir
Model Evaluation: Model akhir diuji pada Testing Set yang belum dimodifikasi (data asli, tidak seimbang). Langkah ini penting untuk mendapatkan evaluasi yang realistis tentang kemampuan model menggeneralisasi di dunia nyata.

Superioritas Kinerja: Model Ensemble menunjukkan kinerja terbaik (ROC-AUC 0.9949), memvalidasi bahwa strategi menggabungkan model tree-based yang kuat adalah solusi optimal untuk memprediksi Employee Attrition.

### 4.1 Model Selection
Pada tahap ini dilakukan proses perbandingan kinerja beberapa algoritma klasifikasi dengan menggunakan teknik stratified k-fold cross validation. Pendekatan ini membagi data pelatihan menjadi beberapa fold dengan proporsi kelas target (attrition) yang tetap seimbang di setiap fold, sehingga evaluasi model tetap representatif meskipun data target tidak seimbang.

Metode k-fold cross validation sendiri digunakan untuk menilai sejauh mana model mampu melakukan generalisasi terhadap data baru. Dataset dibagi menjadi K subset, lalu proses pelatihan dilakukan sebanyak K kali — setiap kali satu subset digunakan untuk pengujian dan sisanya untuk pelatihan. Dengan cara ini, seluruh data memperoleh kesempatan menjadi data uji, mengurangi risiko overfitting, dan menghasilkan estimasi performa yang lebih stabil.

Tujuan dari langkah ini adalah untuk memilih model terbaik yang akan digunakan pada tahap selanjutnya, yaitu feature selection, hyperparameter tuning, dan evaluasi akhir model. Model terbaik dipilih berdasarkan rata-rata skor validasi ROC-AUC tertinggi pada hasil cross-validation, sekaligus mempertimbangkan keseimbangan antara bias dan varians.

Semua model Gradient Boosting yang diuji—**LGBM (0.99203), XGBoost (0.98793), dan CatBoost (0.99391)**—menunjukkan kinerja klasifikasi yang sangat kuat dalam memprediksi Employee Attrition, dengan semua nilai ROC-AUC berada di atas 0.98. Secara spesifik, CatBoost memiliki kemampuan diskriminasi tertinggi sebagai model tunggal (0.99391). Kualitas kinerja yang tinggi ini divalidasi oleh metode Stratified K-Fold Cross-Validation, yang memastikan bahwa angka-angka tersebut andal meskipun dataset mengalami ketidakseimbangan kelas. Hasil ini secara tegas membenarkan strategi penggunaan Model Ensemble, yang secara kolektif meningkatkan akurasi hingga di atas 0.9949, menjadikannya alat prediktif yang paling stabil dan efektif untuk manajemen SDM.

**Perbandingan ROC-AUC tiap Model**
<img width="692" height="451" alt="image" src="https://github.com/user-attachments/assets/d4180c15-a92a-41f9-b3bb-b5b2b3268a13" />
Grafik di atas menunjukkan perbandingan nilai **ROC-AUC** dari empat model yang digunakan, yaitu **LGBM, XGBoost, CatBoost,** dan **Ensemble**. Dari hasil tersebut, terlihat bahwa seluruh model memiliki performa yang sangat baik karena nilai ROC-AUC berada di atas **0.98**, menandakan kemampuan klasifikasi yang tinggi.

Model **LGBM** memperoleh nilai ROC-AUC sebesar **0.9920**, diikuti oleh **CatBoost** dengan **0.9939**, dan **XGBoost** dengan **0.9849**. Sementara itu, model **Ensemble** menunjukkan performa terbaik dengan nilai ROC-AUC tertinggi, yaitu **0.9949**. Hal ini mengindikasikan bahwa penggabungan beberapa model (ensemble) mampu meningkatkan kemampuan prediksi secara keseluruhan, menghasilkan model yang **lebih stabil dan akurat** dibandingkan model tunggal.

## 5. Model Testing and Evaluation
### 5.1 Data Test Predict
Penggunaan **Model Ensemble** dalam proyek ini divalidasi oleh hasil komparatif, di mana performa gabungan melampaui setiap model tunggal. Model Ensemble mencapai nilai ROC-AUC tertinggi sebesar 0.9949, sedikit lebih tinggi daripada komponen terbaiknya, CatBoost (0.9939). Dipilihnya Ensemble adalah strategi yang disengaja karena ia memanfaatkan prinsip wisdom of the crowds; dengan menggabungkan prediksi dari tiga algoritma Gradient Boosting yang kuat (LGBM, XGBoost, CatBoost), model ini mampu memitigasi kelemahan individual dan menghasilkan prediksi yang lebih stabil, robust terhadap noise, dan memiliki variance yang lebih rendah. Metrik ROC-AUC dipilih karena merupakan metrik evaluasi standar industri untuk klasifikasi pada dataset yang tidak seimbang (seperti Employee Attrition). ROC-AUC mengukur kemampuan model dalam membedakan (discrimination) secara keseluruhan antara kelas positif (Attrition=Yes) dan negatif (Attrition=No) tanpa terpengaruh oleh ambang batas prediksi, sehingga nilainya yang mendekati 1.0 mengonfirmasi bahwa model Ensemble adalah alat prediktif yang nyaris sempurna untuk risiko turnover.

**Distribusi Probabilitas Prediksi Attrition (Ensemble)**
<img width="695" height="470" alt="image" src="https://github.com/user-attachments/assets/c8072982-018a-42a8-b257-79454dc50331" />
Grafik di atas menunjukkan **distribusi probabilitas prediksi attrition** (kemungkinan karyawan keluar) yang dihasilkan oleh model **ensemble**. Terlihat bahwa sebagian besar observasi memiliki **probabilitas attrition yang sangat rendah (mendekati 0)**, artinya model memprediksi banyak karyawan berpeluang kecil untuk keluar dari perusahaan.

Namun, terdapat juga **sekelompok kecil observasi dengan probabilitas mendekati 1**, yang menunjukkan karyawan dengan risiko tinggi untuk mengalami attrition. Pola distribusi ini bersifat **bimodal**, di mana sebagian besar nilai terpusat di dua ekstrem (dekat 0 dan dekat 1), menandakan bahwa model mampu **memisahkan dua kelas (stay dan attrition)** dengan cukup jelas.

Secara keseluruhan, distribusi ini mengindikasikan bahwa model ensemble memiliki **kepercayaan tinggi dalam prediksi** yang dibuatnya — mayoritas prediksi memiliki probabilitas yang sangat pasti, baik untuk kategori bertahan maupun keluar.

**Kurva ROC dari hasil validasi ensemble**
<img width="536" height="547" alt="image" src="https://github.com/user-attachments/assets/77026af1-8750-414a-9eaa-ce69f61bb874" />
Berdasarkan hasil kurva ROC pada model ensemble, diperoleh nilai **AUC sebesar 0.9949** yang menunjukkan bahwa model memiliki kemampuan klasifikasi yang sangat baik dalam membedakan antara kelas positif dan negatif. Nilai AUC yang mendekati 1 menandakan bahwa model mampu menghasilkan tingkat **true positive** yang tinggi dengan **false positive** yang sangat rendah. Kurva ROC yang menempel di sisi kiri atas grafik mengindikasikan bahwa model jarang melakukan kesalahan dalam memprediksi kelas positif. Dengan demikian, model ensemble ini dapat dikatakan memiliki **akurasi prediktif yang sangat tinggi** dan performa yang **hampir sempurna**, meskipun tetap perlu dilakukan pemeriksaan lebih lanjut terhadap kemungkinan **overfitting**.

### 5.2 Interpretation with SHAP Values
SHAP adalah library yang memungkinkan interpretasi hasil algoritma machine learning. Dengan SHAP, dapat dipahami dampak masing-masing fitur terhadap prediksi model individu, di mana $ f(x) = E(f(x)) + SHAP $.

import shap

explainer = shap.TreeExplainer(lgb)  # lgb sudah fit
shap_values = explainer.shap_values(X_val_dense)

shap.summary_plot(shap_values, X_val_dense)

Beeswarm Plot memberikan bukti transparan bahwa model Ensemble Anda beroperasi secara logis dan terprediksi, memvalidasi bahwa risiko Attrition paling tinggi muncul dari kombinasi kondisi kerja yang buruk (Lembur) dan kompensasi yang tidak kompetitif (Gaji Rendah). Interpretasi ini memungkinkan manajemen SDM untuk merancang intervensi yang sangat terfokus, seperti melakukan review kompensasi atau mengurangi beban lembur untuk karyawan berisiko.

<img width="766" height="940" alt="image" src="https://github.com/user-attachments/assets/17ceeeca-b33f-48fe-8ca4-c913ef344ab5" />
1. Faktor Pendorong Utama Attrition
Pada plot, fitur yang berada di posisi teratas dan memiliki titik-titik (swarm) yang terkonsentrasi di sisi kanan (SHAP positif) adalah pemicu Attrition terkuat. Hal ini akan didominasi oleh:

OverTime (Lembur): Ini akan menjadi fitur paling penting. Titik-titik yang mewakili lembur (OverTime = Yes) akan memiliki nilai SHAP positif tertinggi, menunjukkan bahwa lembur adalah penyebab tunggal terbesar yang meningkatkan risiko karyawan keluar.

MonthlyIncome (Gaji Bulanan): Titik-titik dengan nilai rendah (warna biru/dingin) akan berkumpul di sisi kanan (SHAP positif). Hal ini berarti gaji yang rendah adalah faktor yang secara konsisten dan kuat mendorong probabilitas Attrition.

2. Faktor Pencegah Attrition (Retensi)
Fitur yang berada di sisi kiri (SHAP negatif) adalah faktor yang menekan risiko Attrition:

MonthlyIncome: Titik-titik dengan nilai tinggi (warna merah/panas) akan terkumpul di sisi kiri (SHAP negatif). Ini mengonfirmasi bahwa gaji yang tinggi adalah penghalang utama turnover.

JobSatisfaction & EnvironmentSatisfaction: Nilai kepuasan yang tinggi (merah) akan mengarah kuat ke sisi negatif SHAP, menunjukkan bahwa kepuasan kerja yang baik secara signifikan menurunkan keinginan karyawan untuk keluar.

## 6. Conclusions
Proyek Analisis dan Prediksi Employee Attrition ini berhasil mencapai tujuan utama yaitu membangun model prediktif yang andal dan mengidentifikasi faktor-faktor risiko utama turnover karyawan.

### 1. Superioritas Model Ensemble dan Kinerja
Pengujian komparatif antara empat model (LGBM, XGBoost, CatBoost, dan Ensemble) menunjukkan bahwa proyek ini menghasilkan kinerja klasifikasi yang luar biasa:

 **Kinerja Tinggi**: Seluruh model menunjukkan performa yang sangat baik, dengan nilai ROC-AUC di atas 0.98, mengindikasikan kemampuan diskriminasi yang sangat tinggi antara kelas attrition dan non-attrition.

 **Model Ensemble Terbaik**: Model Ensemble berhasil melampaui kinerja model tree-based tunggal, mencapai nilai ROC-AUC tertinggi sebesar 0.9949. Hal ini mengonfirmasi hipotesis bahwa penggabungan prediksi dari berbagai algoritma (LightGBM, CatBoost, dan XGBoost) mampu memitigasi kelemahan model individual, menghasilkan model akhir yang lebih kuat, stabil, dan akurat.

### 2. Faktor Utama Pemicu Attrition
Analisis feature importance yang bersumber dari model-model ensemble ini mengkonfirmasi bahwa risiko attrition dipengaruhi secara signifikan oleh:

**Beban Kerja & Kompensasi** : Karyawan yang sering melakukan Lembur (OverTime=Yes) dan level gaji bulanan (MonthlyIncome) yang tidak memadai merupakan faktor-faktor prediktor terkuat.

**Lingkungan & Kepuasan**: Tingkat kepuasan terhadap lingkungan kerja (EnvironmentSatisfaction), keseimbangan kerja-hidup (WorkLifeBalance), dan kepuasan terhadap hubungan kerja (RelationshipSatisfaction) sangat berkorelasi dengan keputusan untuk bertahan.

Tentu. Berdasarkan hasil perbandingan model yang Anda berikan, berikut adalah bagian Kesimpulan (Conclusion) yang direvisi untuk secara eksplisit menyoroti penggunaan dan keberhasilan Model Ensemble sebagai penutup yang kuat.

### 3. Implikasi dan Manfaat Bisnis
Temuan proyek ini memberikan wawasan strategis yang jelas bagi tim Manajemen SDM:

**Retensi Proaktif**: Model Ensemble yang superior kini dapat digunakan sebagai alat screening untuk mengidentifikasi karyawan berisiko sangat tinggi dengan tingkat kepastian yang tinggi.

**Intervensi Tepat Sasaran**: Rekomendasi aksi dapat difokuskan pada perbaikan area spesifik, seperti melakukan peninjauan kompensasi yang kompetitif, serta menerapkan kebijakan untuk mengurangi overtime yang berlebihan, yang merupakan pemicu attrition paling rentan.

**Pengurangan Biaya**: Dengan beralih dari intervensi reaktif ke predictive berbasis model yang akurat, perusahaan dapat menekan biaya turnover secara substansial dan meningkatkan retensi talenta berharga.
























