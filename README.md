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
Jumlah Missing Value per Kolom:

id                          0
Age                         0
BusinessTravel              0
DailyRate                   0
Department                  0
DistanceFromHome            0
Education                   0
EducationField              0
EmployeeCount               0
EmployeeNumber              0
EnvironmentSatisfaction     0
Gender                      0
HourlyRate                  0
JobInvolvement              0
JobLevel                    0
JobRole                     0
JobSatisfaction             0
MaritalStatus               0
MonthlyIncome               0
MonthlyRate                 0
NumCompaniesWorked          0
Over18                      0
OverTime                    0
PercentSalaryHike           0
PerformanceRating           0
RelationshipSatisfaction    0
StandardHours               0
StockOptionLevel            0
TotalWorkingYears           0
TrainingTimesLastYear       0
WorkLifeBalance             0
YearsAtCompany              0
YearsInCurrentRole          0
YearsSinceLastPromotion     0
YearsWithCurrManager        0
Attrition                   0
dtype: int64

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









