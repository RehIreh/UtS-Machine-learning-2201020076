# Polynomial Regression & Regularization Analysis (UTS Machine Learning)

## Deskripsi
Proyek ini bertujuan untuk menganalisis performa model **Polynomial Regression** dengan variasi derajat (degree 1–5) dan metode regularisasi (**Ridge** & **Lasso**) dalam memprediksi harga properti.  
Eksperimen dilakukan menggunakan dataset simulasi `dataset_properti.csv`, dengan preprocessing menggunakan *scaling* dan pembuatan *polynomial features*.  

Hasil terbaik diperoleh pada:
**Polynomial Regression Degree 3 dengan Lasso Regularization (alpha = 10)**  
dengan **R² test = 0.9729** dan **RMSE test = 222.48**

---

## ⚙️ Instalasi Dependencies
Pastikan Python versi ≥ 3.8 telah terinstal.  
Kemudian, jalankan perintah berikut untuk menginstal semua library yang dibutuhkan:

```bash
pip install -r requirements.txt
Cara Menjalankan Proyek
Clone atau salin folder project ini.

Buka file Jupyter Notebook:

bash
Copy code
jupyter notebook UTS_ML_76.ipynb
Jalankan seluruh sel secara berurutan.

Hasil eksplorasi, visualisasi, serta perbandingan model akan tampil langsung di notebook.

File model terbaik (best_property_price_model.pkl) dan scaler (scaler.pkl) dapat digunakan untuk prediksi baru.

Struktur Folder Project
bash
Copy code
.
├── dataset_properti.csv            # Dataset utama (data simulasi properti)
├── UTS_ML_76.ipynb                 # Notebook utama berisi analisis & training model
├── Laporan UTS_ML_76.md            # Laporan analisis hasil eksperimen
├── README.md                       # Panduan penggunaan project (file ini)
├── requirements.txt                # Daftar dependencies Python
├── scaler.pkl                      # File scaler (StandardScaler) untuk preprocessing
├── best_property_price_model.pkl   # Model terbaik (Degree 3 - Lasso alpha=10)

Hasil Eksperimen
Model	Train R²	Test R²	Train RMSE	Test RMSE
Degree 3 - Lasso (α=10)	0.9858	0.9729	177.12	222.48
Degree 3 - Lasso (α=1)**	0.9898	0.9699	150.43	234.48
Degree 3 - Ridge (α=1)**	0.9886	0.9698	158.79	234.97

Model terbaik: Polynomial Regression Degree 3 – Lasso (alpha=10)

Insight Utama
Degree terlalu rendah → underfitting
Degree terlalu tinggi → overfitting
Regularisasi Lasso membantu menjaga keseimbangan bias–variance
Ridge stabil, tapi sedikit lebih rendah performanya di dataset ini

Rencana Pengembangan
Menambahkan cross-validation (k-fold) untuk evaluasi lebih akurat.
Mengoptimalkan nilai alpha menggunakan GridSearchCV.
Menggunakan ElasticNet Regression untuk menggabungkan kelebihan Ridge & Lasso.
Menguji model dengan data properti nyata.