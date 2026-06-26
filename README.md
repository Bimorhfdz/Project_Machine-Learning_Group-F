# 📊 Analisis Klasifikasi Subscription Deposito Bank Menggunakan Machine Learning

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Latest-orange.svg)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Latest-blueviolet.svg)](https://pandas.pydata.org/)
[![Framework](https://img.shields.io/badge/Machine_Learning-Random_Forest-green.svg)]()

Repository ini berisi proyek *machine learning* yang bertujuan untuk memprediksi probabilitas seorang nasabah bank akan memilih untuk mengambil program deposito berjangka (*term deposit*). Model dibangun menggunakan bahasa pemrograman Python dengan fokus optimalisasi algoritma **Random Forest Classifier**.

---

## 👥 Tim Peneliti (Kelompok F)
Proyek ini disusun oleh mahasiswa Program Studi Statistika, Fakultas Matematika dan Ilmu Pengetahuan Alam, **Universitas Jenderal Soedirman (2026)**:
* 🧑‍💻 **Emanuel Christmas P.F** — (K1D024065)
* 👩‍💻 **Bertha Misella Silalahi** — (K1D024068)
* 🧑‍💻 **Bimo Rahman H** — (K1D024069)
* 👩‍💻 **Rexitalia Zarisma** — (K1D024075)

---

## 📌 Deskripsi Proyek
Proyek ini menggunakan **Bank Marketing Dataset** yang merekam aktivitas kampanye pemasaran langsung (*direct marketing campaigns*) dari sebuah lembaga perbankan di Portugal. 

Tantangan utama dalam dataset ini adalah adanya ketidakseimbangan kelas (*class imbalance*) yang sangat tinggi pada variabel target (`y`), di mana jumlah nasabah yang menolak jauh lebih mendominasi. Untuk mengatasi hal tersebut, proyek ini menerapkan alur rekayasa data (*data engineering*) yang ketat sebelum melakukan pemodelan.

---

## 🛠️ Alur Kerja & Metodologi
`[Raw Dataset] ➡️ [Data Cleaning] ➡️ [Winsorizing (Outliers)] ➡️ [One-Hot Encoding] ➡️ [SMOTE Balancing] ➡️ [Random Forest + Tuning]`

### 1. Pembersihan Data (Data Cleaning)
* **Missing Values:** Hasil pemeriksaan menunjukkan tidak terdapat data kosong (*null/missing values*).
* **Data Duplikat:** Mengidentifikasi dan menghapus **12 baris data duplikat**, menyesuaikan ukuran dataset dari 41.188 menjadi **41.176 baris**.

### 2. Penanganan Outlier (Winsorizing)
* Menggunakan metode **Winsorizing** untuk membatasi nilai ekstrem tanpa membuang baris data penting.
* **Batas Persentil:** Persentil ke-5 (batas bawah) dan persentil ke-95 (batas atas).
* **Variabel Target:** Diaplikasikan secara khusus pada variabel numerik `age`, `duration`, `campaign`, dan `previous`.

### 3. Transformasi Data
* Mengubah variabel target `y` menjadi biner (`yes` -> 1, `no` -> 0).
* Mengonversi variabel kategorikal nominal menggunakan teknik **One-Hot Encoding** (`pd.get_dummies`).

### 4. Penanganan Imbalance Data (SMOTE)
* Menerapkan **Synthetic Minority Over-sampling Technique (SMOTE)** untuk meningkatkan proporsi kelas minoritas secara sintetis pada data latih agar model tidak bias terhadap kelas mayoritas.

### 5. Optimasi Model (Hyperparameter Tuning)
* Menggunakan **GridSearchCV** untuk mencari kombinasi parameter terbaik pada algoritma Random Forest Classifier demi menekan angka *False Positive* dan *False Negative*.

---

## 📈 Hasil Evaluasi Model

Model akhir **Random Forest Classifier (Tuned)** memberikan performa klasifikasi yang sangat kuat dan optimal:

| Metrik Evaluasi | Nilai Capaian |
| :--- | :---: |
| **Akurasi Model** | **~91.42%** |
| **Skor ROC-AUC** | **0.9480** |

💡 **Temuan Kunci (Feature Importance):** Berdasarkan analisis bobot fitur, variabel **`duration`** (durasi panggilan telepon terakhir dengan nasabah) memiliki pengaruh paling signifikan dan dominan dalam menentukan keberhasilan nasabah untuk mengambil keputusan berlangganan deposito.

---

## 💻 Prasyarat Sistem (Requirements)
Jalankan perintah berikut pada terminal atau command prompt Anda untuk mengonfigurasi *environment* dependensi library:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn kagglehub
```

---

## 🚀 Cara Menjalankan Proyek
1. Unduh / Clone Repository ini ke komputer lokal Anda.
2. Buka file notebook proyek menggunakan platform pilihan Anda (Jupyter Notebook, Jupyter Lab, atau Google Colab).
3. Jalankan cell kode secara berurutan pada berkas:
   * `Project_ML_F_(Revisi).ipynb`

> ⚠️ **Catatan:** Dataset tidak perlu diunduh manual. Kode sudah terintegrasi dengan pustaka `kagglehub` untuk mengambil file asli `bank-additional-full.csv` secara otomatis langsung dari server Kaggle.

---

## 📁 Struktur File Pendukung
* 📓 **Project_ML_F_(Revisi).ipynb** : Berkas notebook utama berisi implementasi kode dari hulu ke hilir.
* 📝 **Laporan_Project_ML_FIX_ABIS_1.docx** : Dokumen laporan analitis resmi lengkap (Format Word) dari Bab I s.d Bab IV.
* 📘 **Project_ML_F_(Revisi).pdf** : Salinan cetak visualisasi dari notebook eksperimen pemodelan.
