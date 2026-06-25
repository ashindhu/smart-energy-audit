# Prediksi Konsumsi Listrik Melalui Evaluasi Kinerja Model Long Short-Term Memory (LSTM) dan Random Forest

## Deskripsi Proyek

Proyek ini dikembangkan sebagai Tugas Besar mata kuliah **Pembelajaran Mesin dan Aplikasi** di Telkom University.

Tujuan utama proyek ini adalah membangun sistem prediksi konsumsi daya listrik berdasarkan data historis yang diperoleh dari platform Internet of Things (IoT) ThingSpeak, kemudian membandingkan performa dua algoritma machine learning, yaitu Random Forest dan Long Short-Term Memory (LSTM).

Model yang telah dilatih kemudian diimplementasikan ke dalam aplikasi web menggunakan Streamlit sehingga pengguna dapat melihat data konsumsi daya secara real-time sekaligus memperoleh hasil prediksi konsumsi daya beberapa jam ke depan.

---

## Tujuan

- Mengumpulkan data konsumsi daya listrik dari ThingSpeak.
- Melakukan preprocessing dan pembersihan data.
- Membangun model Random Forest dan LSTM.
- Membandingkan performa kedua model.
- Melakukan deployment model menggunakan Streamlit.

---

## Dataset

### Sumber Data

ThingSpeak IoT Cloud Platform

### Variabel yang Digunakan

Target Prediksi:

- Konsumsi Daya (Power / Field 7)

Tahapan preprocessing meliputi:

- Mengurutkan data berdasarkan waktu
- Menghapus data kosong (missing value)
- Resampling menjadi data per jam
- Interpolasi maksimal 3 jam data kosong
- Feature engineering menggunakan fitur lag
- Normalisasi data menggunakan MinMaxScaler (khusus LSTM)

---

## Model Machine Learning

### 1. Random Forest

Random Forest menggunakan beberapa nilai konsumsi daya sebelumnya sebagai fitur prediksi.

Fitur yang digunakan:

- lag_1
- lag_2
- lag_3
- lag_6
- lag_12
- lag_24

Optimasi parameter dilakukan menggunakan:

- GridSearchCV
- TimeSeriesSplit Cross Validation

---

### 2. Long Short-Term Memory (LSTM)

LSTM digunakan untuk mempelajari pola deret waktu (time series) konsumsi daya listrik.

Konfigurasi model:

- Window Size : 24 Jam
- Hidden Layer : 64 Unit
- Optimizer : Adam
- Loss Function : Mean Squared Error (MSE)
- Epoch : 50
- Batch Size : 16

---

## Hasil Evaluasi Model

| Model | MAE | RMSE | R² |
|------|------:|------:|------:|
| Random Forest | 991.33 | 1385.22 | 0.8207 |
| LSTM | 1008.68 | 1320.19 | 0.8371 |

### Kesimpulan

Berdasarkan hasil pengujian:

- Random Forest menghasilkan nilai MAE paling kecil.
- LSTM menghasilkan nilai RMSE paling kecil.
- LSTM memperoleh nilai R² paling tinggi sehingga mampu mengikuti pola konsumsi daya lebih baik dibandingkan Random Forest.

---

## Deployment

Model yang telah dilatih diimplementasikan menggunakan **Streamlit Community Cloud**.

Fitur dashboard meliputi:

- Monitoring konsumsi daya secara real-time
- Grafik konsumsi daya per jam
- Prediksi 5 jam ke depan menggunakan Random Forest
- Prediksi 5 jam ke depan menggunakan LSTM
- Perbandingan performa kedua model

---

## Struktur Proyek

```text
smart-energy-audit/
│
├── app.py
├── requirements.txt
├── rf_model.pkl
├── lstm_model.keras
├── scaler.pkl
├── README.md
└── runtime.txt
```

---

## Cara Menjalankan

Clone repository

```bash
git clone https://github.com/ashindhu/smart-energy-audit.git
```

Masuk ke folder proyek

```bash
cd smart-energy-audit
```

Install library

```bash
pip install -r requirements.txt
```

Jalankan aplikasi

```bash
python -m streamlit run app.py
```

---

## Teknologi yang Digunakan

- Python
- Pandas
- NumPy
- Scikit-learn
- TensorFlow / Keras
- Streamlit
- Plotly
- Joblib
- ThingSpeak

---

## Demo Aplikasi dan link youtube

streamlit
[https://smart-energy-audit-ashindhu.streamlit.app/](https://prediksi-konsumsi-listrik-ml.streamlit.app/)

youtube
https://youtu.be/KzW0LZl_ERY
---

## Mata Kuliah

Pembelajaran Mesin dan Aplikasi

Program Studi S1 Teknik Elektro

Telkom University

---

## Anggota Kelompok
-Ashura Sindhu Santhana / 1102223224
-Andreas Beckham Silalahi / 1102220292
-Dimaz Rajendra Heryanto / 1102220235
-Rafiqy Naufaleri / 1102220032


---

## Lisensi

Proyek ini dikembangkan untuk keperluan akademik sebagai Tugas Besar mata kuliah Pembelajaran Mesin dan Aplikasi di Telkom University.
