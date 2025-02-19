# About

# EDA, Data Preprocessing, & Data Visualization
## Mengenai Dataset Dummy synthetic_bank_data.csv:
Dataset ini memiliki beberapa fitur dengan tipe data yang berbeda (numerik, kategorikal, dan tanggal) serta beberapa karakteristik seperti missing values, duplikat, dan outliers yang bisa kamu gunakan untuk latihan EDA dan pembersihan data. Dataset ini juga dirancang sedemikian rupa sehingga terdapat korelasi antara beberapa fitur, misalnya:
* **Age (Umur)** berpengaruh terhadap **Annual_Income (Pendapatan Tahunan)**, di mana semakin tinggi umur, biasanya pendapatan juga cenderung lebih tinggi.
* **Annual_Income** juga mempengaruhi **Credit_Score (Skor Kredit)** karena skor kredit dihitung berdasarkan skala pendapatan.
* **Account_Balance (Saldo Akun)** memiliki korelasi dengan **Annual_Income** (saldo cenderung proporsional terhadap pendapatan) dan juga bisa mempengaruhi status **Is_Active** (apakah akun aktif atau tidak).
* Fitur **Account_Type** dan **Bank_Branch** adalah kategorikal yang bisa digunakan untuk latihan encoding.
* **Signup_Date (Tanggal Daftar)** berfungsi sebagai data temporal yang dapat diolah untuk feature engineering (misalnya menghitung lama nasabah bergabung).

## Mengenai Introduction_to_EDA_Data_Preprocessing_n_Data_Visualization.ipynb:
* **Exploratory Data Analysis (EDA) Awal:**
   * `head()` & `tail()`: Untuk melihat sampel data awal dan akhir.
   * `columns`: Menampilkan daftar nama kolom.
   * `shape`: Untuk mengetahui jumlah baris dan kolom.
   * `describe()`: Untuk mendapatkan ringkasan statistik dari data numerik.
   * `info()`: Untuk mengecek tipe data dan jumlah non-null.
* **Penanganan Format Data:**
   * **Cek Tipe Data**: Gunakan `data.dtypes` untuk memastikan setiap kolom memiliki tipe data yang tepat.
   * **Konversi Tipe Data**: Misalnya, mengkonversi kolom `Signup_Date` menjadi format datetime.
   * **Standarisasi Format String**: Misalnya, mengubah semua teks pada kolom `Account_Type` dan `Bank_Branch` menjadi lowercase dan menghapus spasi ekstra.
* **Penanganan Data Duplikat:**
   * **Deteksi Duplikat**: Gunakan `data.duplicated().sum()` untuk mengetahui jumlah baris duplikat.
   * **Penghapusan Duplikat**: Terapkan `drop_duplicates(inplace=True)` untuk membersihkan data dari duplikat.
* **Penanganan Missing Value:**
   * **Deteksi Missing Value**: Gunakan `data.isna().sum()` untuk mengetahui jumlah missing value per kolom.
   * **Pengisian Missing Value**:
      * **Numerik**: Menggunakan mean atau median (misalnya, pada kolom `Annual_Income` dan `Credit_Score`).
      * **Kategorikal**: Menggunakan mode atau imputasi kategori yang paling sering muncul.
      * **Interpolasi**: Jika data berurutan (misalnya, data time series).
   * **Penghapusan Baris**: Jika missing value terlalu banyak dan tidak memungkinkan untuk imputasi.
* **Handling Outliers:**
   * **Deteksi Outliers**: Gunakan visualisasi (boxplot, histogram) atau metode statistik (misalnya, Z-score) untuk mengidentifikasi outlier di kolom seperti `Account_Balance`.
   * **Penanganan Outliers**:
      * **Winsorizing**: Membatasi nilai ekstrim ke batas tertentu.
      * **Log Transform**: Jika data skewed.
* **Korelasi dan Visualisasi:**
   * **Analisis Korelasi:**
      * Gunakan `corr()` untuk mengecek hubungan antar fitur numerik.
      * Fokus pada korelasi antara:
         * `Age` dan `Annual_Income`
         * `Annual_Income` dan `Credit_Score`
         * `Annual_Income` dan `Account_Balance`
   * **Visualisasi Hubungan Antar Variabel:**
      * **Scatter Plot:**
         * Menampilkan hubungan antara `Age` dan `Annual_Income`.
         * Menampilkan hubungan antara `Annual_Income` dan `Credit_Score`.
      * **Bar Chart:**
         * Menampilkan rata-rata `Account_Balance` berdasarkan kategori `Is_Active`.
         * Menampilkan distribusi nasabah berdasarkan `Bank_Branch` atau `Account_Type`.
* **Feature Engineering:**
   * **Membuat Kolom Baru**: Misalnya, membuat kolom baru “Customer_Tenure” yang dihitung dari selisih tanggal hari ini dengan `Signup_Date`.
   * **One-Hot Encoding**: Untuk kolom kategorikal seperti `Account_Type` dan `Bank_Branch`.
   * **Label Encoding**: Jika terdapat kategori dengan urutan tertentu (misalnya, level skor kredit).
* **Normalisasi & Standarisasi:**
   * **Min-Max Scaling**: Untuk mengubah skala data numerik (misalnya, mengubah nilai antara 0 dan 1).
   * **Standarisasi (Z-Score)**: Untuk menyamakan distribusi fitur numerik.
* **Principal Component Analysis (PCA):**
   * Digunakan untuk mereduksi dimensi data, khususnya jika terdapat banyak fitur numerik yang saling berkorelasi. PCA dapat membantu dalam visualisasi dan pengurangan noise.

# Introduction to Nowcasting
## Mengenai Dataset Dummy synthetic_nowcasting_data.csv:
Dataset ini disusun dengan mempertimbangkan beberapa korelasi yang masuk akal, misalnya:
* **GDP_Growth**: Mewakili pertumbuhan ekonomi bulanan (dalam %). Semakin tinggi pertumbuhan, biasanya tingkat pengangguran cenderung menurun dan kepercayaan konsumen meningkat.
* **Unemployment_Rate**: Dibuat dengan korelasi negatif terhadap GDP_Growth, artinya jika pertumbuhan ekonomi tinggi, tingkat pengangguran akan lebih rendah.
* **Money_Supply**: Disimulasikan dengan tren naik selama 10 tahun, yang dapat berkontribusi pada peningkatan **Inflation_Rate**.
* **Inflation_Rate**: Dipengaruhi oleh tingkat money supply. Jika money supply meningkat, inflasi cenderung naik.
* **Interest_Rate**: Ditetapkan berdasarkan inflasi (bank sentral biasanya menaikkan suku bunga untuk mengendalikan inflasi). Dengan demikian, Interest_Rate cenderung lebih tinggi ketika inflasi tinggi.
* **Exchange_Rate**: Mewakili nilai tukar lokal (misalnya Rupiah per USD) dan dipengaruhi oleh money supply (kebijakan moneter longgar dapat menyebabkan depresiasi) serta Interest_Rate (suku bunga yang lebih tinggi cenderung menarik investasi asing sehingga menguatkan nilai tukar).
* **Consumer_Confidence_Index**: Dibentuk dari pengaruh positif GDP_Growth dan negatif Unemployment_Rate. Indeks ini mewakili tingkat kepercayaan konsumen terhadap kondisi ekonomi.

## 
