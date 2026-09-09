# Data Preprocessing — Movie Sample Dataset

Proyek ini merupakan latihan *hands-on* dalam bidang **Data Preprocessing**, menggunakan dataset sampel film (*movie sample dataset*) yang berisi informasi seperti nama sutradara, durasi film, pendapatan (*gross*), anggaran (*budget*), genre, tahun rilis, bahasa, negara, skor IMDb, hingga daftar aktor.

Dataset mentah ini memiliki berbagai masalah kualitas data yang umum ditemukan di dunia nyata, seperti:

- Missing value pada beberapa kolom
- Penulisan teks yang tidak konsisten (huruf besar/kecil campur)
- Nilai tidak standar seperti `"N/A"`
- Nilai negatif yang tidak valid pada kolom numerik (durasi, skor IMDb, budget, gross)
- Kolom genre yang berisi banyak nilai sekaligus dalam satu string (dipisah tanda `|`)

Melalui proses ini, data mentah diubah menjadi dataset yang **bersih, konsisten, dan siap dianalisis**, termasuk pemecahan kolom genre menjadi fitur biner per genre untuk mempermudah analisis lebih lanjut.

## 🎯 Tujuan

1. Mengidentifikasi dan menangani *missing value* pada dataset.
2. Melakukan normalisasi teks pada kolom kategorikal (judul kolom & isi kolom).
3. Menangani nilai tidak standar (`"N/A"`) dan nilai negatif yang tidak valid.
4. Memastikan kolom numerik (`gross`, `budget`, `duration`, `imdb_score`) memiliki tipe data yang benar.
5. Melakukan *feature engineering* dengan memecah kolom `genres` menjadi kolom biner per genre.
6. Menyimpan hasil akhir ke file CSV yang siap digunakan untuk analisis.

## 🛠️ Tools & Library

- **Python 3**
- **pandas** — manipulasi dan pembersihan data
- **numpy** — penanganan nilai negatif/tidak valid

## 📂 Struktur Proyek

```
├── Prepocessing_Data_Nafa.ipynb        # Notebook utama proses preprocessing
├── movie_sample_dataset.csv            # Data mentah (input)
└── movie_dataset_normalized_final.csv  # Data hasil preprocessing (output)
```

## 🔄 Alur Proses (Workflow)

1. **Import Library**
   Mengimpor `pandas` dan `numpy` untuk keperluan manipulasi data.

2. **Memuat Dataset**
   Membaca `movie_sample_dataset.csv` dan meninjau lima baris pertama serta dimensi (jumlah baris & kolom) dataset.

3. **Membersihkan Data**
   - **a. Mengidentifikasi Missing Value**
     Mengecek jumlah missing value per kolom, menampilkan baris yang mengandung nilai kosong, lalu menghapus baris tersebut dengan `dropna()` dan mereset index.
   - **b. Normalisasi Teks**
     Menyeragamkan nama kolom dan nilai teks pada kolom `Color`, `Country`, `Language`, `Genres`, dan `Director_Name` menjadi format *Title Case*.
   - **c. Menangani Nilai Tidak Standar**
     Mengganti nilai `"N/A"` dengan `NaN`, menghapus baris yang tersisa memiliki nilai kosong, menghapus baris dengan `budget`/`gross` negatif, dan mengubah nilai `duration`/`imdb_score` yang negatif menjadi `NaN`.

4. **Transformasi Data**
   - **a. Konversi Tipe Numerik**
     Memastikan kolom `gross`, `budget`, `duration`, dan `imdb_score` bertipe numerik menggunakan `pd.to_numeric()`.
   - **b. Memisahkan Kolom Genres**
     Memecah kolom `genres` (dipisah tanda `|`) menjadi daftar genre, lalu membuat kolom biner baru untuk setiap genre unik yang ditemukan.

5. **Menyimpan Data Hasil Preprocessing**
   Data bersih disimpan ke file `movie_dataset_normalized_final.csv`.

## ▶️ Cara Menjalankan

1. Pastikan Python dan library yang dibutuhkan sudah terpasang:
   ```bash
   pip install pandas numpy
   ```
2. Letakkan file `movie_sample_dataset.csv` pada direktori yang sama dengan notebook/script.
3. Jalankan notebook `Prepocessing_Data_Nafa.ipynb` secara berurutan dari sel pertama hingga terakhir (atau jalankan versi `.py`-nya jika ada).
4. Hasil preprocessing akan tersimpan otomatis sebagai `movie_dataset_normalized_final.csv`.



---
*Proyek ini dibuat sebagai bagian dari latihan mengenai Data Preprocessing pada dataset film.*
#Movie Dataset Preprocessing 
