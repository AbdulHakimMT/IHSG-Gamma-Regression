# Analisis Prediksi Besarnya Pergerakan Pasar IHSG Menggunakan Regresi Gamma

## Deskripsi Proyek

Proyek ini bertujuan untuk menganalisis dan memprediksi besarnya pergerakan harian Indeks Harga Saham Gabungan (IHSG) menggunakan metode **Gamma Regression**.

Data yang digunakan diperoleh dari Yahoo Finance dengan ticker `^JKSE`. Penelitian berfokus pada besarnya rentang pergerakan harga harian IHSG (*daily price range*), bukan pada prediksi arah kenaikan atau penurunan indeks.

## Tujuan

1. Menganalisis karakteristik pergerakan harian IHSG.
2. Mengidentifikasi hubungan variabel historis IHSG dengan besarnya pergerakan harian.
3. Membangun model prediksi menggunakan Gamma Regression dengan fungsi link log.
4. Mengevaluasi performa model menggunakan MAE dan RMSE.

## Dataset

- **Sumber:** Yahoo Finance
- **Ticker:** `^JKSE`
- **Periode:** 23 Oktober 2021 – 23 Oktober 2026
- **Variabel utama:** Open, High, Low, Close, dan Volume.

## Metodologi

Tahapan analisis yang dilakukan:

1. Data collection
2. Data preprocessing
3. Exploratory Data Analysis (EDA)
4. Feature engineering
5. Model diagnostics
6. Gamma Regression modeling
7. Model evaluation
8. Interpretation and conclusion

## Target Variabel

Target yang digunakan adalah `Target_Range`, yaitu rasio rentang harga tertinggi dan terendah harian terhadap harga penutupan hari sebelumnya.

\[
Target\_Range_t = \frac{High_t-Low_t}{Close_{t-1}}
\]

## Model

Model yang digunakan adalah Generalized Linear Model (GLM) dengan:

- Distribution: Gamma
- Link function: Log
- Estimation method: Iteratively Reweighted Least Squares (IRLS)

## Evaluasi Model

Performa model dievaluasi menggunakan:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)

Model Gamma Regression juga dibandingkan dengan baseline berupa rata-rata target data training.

| Model | MAE | RMSE |
|---|---:|---:|
| Baseline | 0.009057 | 0.014881 |
| Gamma Regression | 0.007832 | 0.014443 |

Berdasarkan hasil evaluasi, Gamma Regression menghasilkan MAE dan RMSE yang lebih rendah dibandingkan baseline.

## Hasil dan Temuan

- Lagged volatility 5 hari dan lagged range 1 hari memiliki hubungan positif dan signifikan secara statistik terhadap target.
- Lagged return 1 hari dan lagged log volume 1 hari tidak signifikan pada taraf 5%.
- Hasil pengujian Ljung–Box menunjukkan adanya autokorelasi pada residual model.
- Model Gamma Regression memberikan performa lebih baik daripada baseline berdasarkan MAE dan RMSE.

## Tools

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Statsmodels
- Yahoo Finance (`yfinance`)

## Repository Contents

- `ihsg_gamma_regression.ipynb`: Notebook yang berisi proses pengumpulan data, preprocessing, eksplorasi data, pemodelan, evaluasi, dan interpretasi hasil.

## Catatan

Proyek ini merupakan proyek pembelajaran dan portofolio analisis kuantitatif. Hasil model tidak dimaksudkan sebagai rekomendasi investasi atau jaminan prediksi pergerakan pasar di masa mendatang.
