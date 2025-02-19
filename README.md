# Data Science & Machine Learning Materials for BI
## Mengenai Dataset Dummy synthetic_bank_data.csv:
Dataset ini memiliki beberapa fitur dengan tipe data yang berbeda (numerik, kategorikal, dan tanggal) serta beberapa karakteristik seperti missing values, duplikat, dan outliers yang bisa kamu gunakan untuk latihan EDA dan pembersihan data. Dataset ini juga dirancang sedemikian rupa sehingga terdapat korelasi antara beberapa fitur, misalnya:
* **Age (Umur)** berpengaruh terhadap **Annual_Income (Pendapatan Tahunan)**, di mana semakin tinggi umur, biasanya pendapatan juga cenderung lebih tinggi.
* **Annual_Income** juga mempengaruhi **Credit_Score (Skor Kredit)** karena skor kredit dihitung berdasarkan skala pendapatan.
* **Account_Balance (Saldo Akun)** memiliki korelasi dengan **Annual_Income** (saldo cenderung proporsional terhadap pendapatan) dan juga bisa mempengaruhi status **Is_Active** (apakah akun aktif atau tidak).
* Fitur **Account_Type** dan **Bank_Branch** adalah kategorikal yang bisa digunakan untuk latihan encoding.
* **Signup_Date (Tanggal Daftar)** berfungsi sebagai data temporal yang dapat diolah untuk feature engineering (misalnya menghitung lama nasabah bergabung).
