# UTS Machine Learning – Linear & Logistic Regression

- **Nama** : Ihya Alif Pramono
- **NIM**  : 241011401192
- **Kelas**: Reg B (05TPLM003)
- **random_state**: 92 (2 digit terakhir NIM)

## Isi Repositori
- `tugas_UTS.ipynb` – notebook lengkap (kode, output, dan analisis)
- `Ads_Data.csv` – data biaya iklan vs penjualan (40 data)
- `Email_Data.csv` – data jumlah link, kata promosi, dan label spam (60 data)

Model dan metrik evaluasi dibuat sendiri dengan NumPy. scikit-learn hanya dipakai pada soal bonus untuk perbandingan.

## Ringkasan Hasil

### Bagian A – Linear Regression (test_size = 0.2)
- Persamaan (normal equation): ŷ = 27.7242 + 9.1831·X
- Data testing: MAE = 3.391, RMSE = 4.214, R² = 0.974
- Data training: MAE = 4.778, RMSE = 6.377, R² = 0.934
- Gradient descent (5000 iterasi): lr 0.001 terlalu lambat, lr 0.02 sama dengan normal equation, lr 0.1 divergen (overflow)
- Prediksi penjualan: biaya iklan 4.5 juta → 69.05; 7 juta → 92.01; 12 juta → 137.92 (ekstrapolasi, kurang bisa dipercaya)

### Bagian B – Logistic Regression (test_size = 0.25, lr = 0.1, 10000 iterasi)
- P(Spam) = σ(-8.9171 + 0.7964·JumlahLink + 0.7573·KataPromo)
- Data testing (threshold 0.5): accuracy = 1.000, precision = 1.000, recall = 1.000, F1 = 1.000
- Threshold pilihan: 0.5
- Prediksi email baru: E1 → Bukan Spam (P = 0.001); E2 → Bukan Spam (P = 0.403); E3 → Spam (P = 0.997); E4 → Spam (P = 0.732)

### Bonus – scikit-learn
Koefisien Linear Regression sama persis dengan implementasi sendiri. Pada Logistic Regression koefisiennya berbeda karena scikit-learn memakai regularisasi L2 (C = 1) secara default.
