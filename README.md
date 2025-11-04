# 🏡 Polynomial Regression & Regularization Analysis  
**UTS Machine Learning – Analisis Model Prediksi Harga Properti**

---

## 📘 Deskripsi  
Proyek ini bertujuan untuk menganalisis performa model **Polynomial Regression** dengan variasi derajat (degree 1–5) serta metode regularisasi **Ridge** dan **Lasso** dalam memprediksi harga properti.  

Eksperimen dilakukan menggunakan dataset simulasi `dataset_properti.csv`, dengan tahapan preprocessing berupa *feature scaling* dan *polynomial feature expansion*.  

> 🔹 **Model terbaik diperoleh pada:**  
> **Polynomial Regression Degree 3 dengan Lasso Regularization (α = 10)**  
> **R² Test = 0.9729 | RMSE Test = 222.48**

---

## ⚙️ Instalasi Dependencies  

Pastikan **Python ≥ 3.8** telah terinstal.  
Kemudian jalankan perintah berikut di terminal untuk menginstal semua library yang dibutuhkan:

```bash
pip install -r requirements.txt
```

---

## 🚀 Cara Menjalankan Proyek  

1. **Clone atau salin** folder project ini ke komputer Anda.  
2. Buka terminal atau command prompt, lalu jalankan:
   ```bash
   jupyter notebook UTS_ML_76.ipynb
   ```
3. Jalankan seluruh *cell* notebook secara berurutan.  
4. Hasil eksplorasi data, visualisasi, serta perbandingan performa model akan langsung tampil di notebook.  

> File model terbaik (`best_property_price_model.pkl`) dan scaler (`scaler.pkl`) dapat digunakan untuk melakukan **prediksi data baru**.

---

## 📂 Struktur Folder  

```
.
├── dataset_properti.csv            # Dataset utama (data simulasi properti)
├── UTS_ML_76.ipynb                 # Notebook utama berisi analisis & training model
├── Laporan UTS_ML_76.md            # Laporan analisis hasil eksperimen
├── README.md                       # Panduan penggunaan project (file ini)
├── requirements.txt                # Daftar dependencies Python
├── scaler.pkl                      # File scaler (StandardScaler) untuk preprocessing
├── best_property_price_model.pkl   # Model terbaik (Degree 3 - Lasso α=10)
```

---

## 📊 Hasil Eksperimen  

| Model | Train R² | Test R² | Train RMSE | Test RMSE |
|:--|:--:|:--:|:--:|:--:|
| **Degree 3 – Lasso (α = 10)** | **0.9858** | **0.9729** | **177.12** | **222.48** |
| Degree 3 – Lasso (α = 1) | 0.9898 | 0.9699 | 150.43 | 234.48 |
| Degree 3 – Ridge (α = 1) | 0.9886 | 0.9698 | 158.79 | 234.97 |

📈 **Model terbaik:** Polynomial Regression **Degree 3 – Lasso (α = 10)**

---

## 💡 Insight Utama  

- Degree terlalu rendah → **underfitting**  
- Degree terlalu tinggi → **overfitting**  
- Regularisasi **Lasso** membantu menjaga keseimbangan **bias–variance**  
- **Ridge** lebih stabil, namun sedikit lebih rendah performanya pada dataset ini  

---

## 🧮 Contoh Prediksi Baru  

Gunakan model dan scaler yang telah disimpan untuk melakukan prediksi pada data baru:

```python
import pickle
import numpy as np

# Load model dan scaler
with open('best_property_price_model.pkl', 'rb') as f:
    model = pickle.load(f)

with open('scaler.pkl', 'rb') as f:
    scaler = pickle.load(f)

# Contoh data baru (urutan fitur sesuai dataset)
data_baru = np.array([[120, 3, 2, 1]])  # contoh: luas, kamar tidur, kamar mandi, lantai
data_scaled = scaler.transform(data_baru)

# Prediksi harga
prediksi = model.predict(data_scaled)
print(f"💰 Prediksi Harga Properti: {prediksi[0]:,.2f}")
```

---

## 🔭 Rencana Pengembangan  

- [ ] Menambahkan **k-fold cross-validation** untuk evaluasi yang lebih akurat.  
- [ ] Mengoptimalkan nilai **alpha** menggunakan **GridSearchCV**.  
- [ ] Menerapkan **ElasticNet Regression** untuk menggabungkan kelebihan Ridge & Lasso.  
- [ ] Menguji model menggunakan **data properti nyata** untuk validasi eksternal.  
