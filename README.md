# KLASIFIKASI KENDARAAN PADA OBJEK BERGERAK MENGGUNAKAN METODE BACKGROUND SUBTRACTION PADA CITRA CCTV🏍️🚗

Proyek ini bertujuan untuk **mendeteksi dan klasifikasi kendaraan** (motor dan mobil) dalam video lalu lintas menggunakan metode pemrosesan citra klasik. Proses dimulai dari ekstraksi frame video, konversi ke grayscale, perhitungan background secara otomatis menggunakan median, membedakan frame dengan background, thresholding Otsu, morfologi, pelabelan objek, klasifikasi berdasarkan zona, hingga penyimpanan video output yang telah dianotasi.


## 📁 Struktur File

```
├── Background_Subtraction.ipynb   # Notebook utama deteksi kendaraan (untuk dijalankan di Google Colab)
├── README.md                      # Dokumentasi proyek ini
└── jogja.mp4                      # Video input lalu lintas
```

---

## 🪜 Langkah-langkah

1. **Download Video:**
   Gunakan video rekaman CCTV yang telah dilampirkan.
   https://drive.google.com/file/d/19K1Tpf5T529FqPPZFI__4RlVEfWMX50f/view?usp=sharing
   
3. **Siapkan Video**
   Unggah file video lyang telah diunduh langsung di Colab lewat panel Files dengan cara klik ikon folder di sisi kiri → Klik tombol Upload → Pilih file jogja.mp4

4. **Instalasi Dependensi**
   Jalankan perintah berikut di Colab:

	```python
	pip install opencv-python numpy scikit-image
	```


## 🧪 Cara Menjalankan

1. Buka file **Background_Subtraction.ipynb** di Google Colab
2. Jalankan semua sel dari atas ke bawah, jangan lupa pastikan path video benar
3. Simpan Output
---

## 🔍 Alur Proses

1. Ekstrak seluruh frame dari video input
2. Konversi frame ke **grayscale**
3. Hitung **median** dari seluruh frame → dijadikan **background**
4. Hitung selisih absolut frame saat ini dengan background
5. Terapkan **Otsu Thresholding**
6. Terapkan **morfologi closing & opening** untuk hilangkan noise
7. Deteksi dan **label objek** menggunakan `skimage.measure.label`
8. Bagi frame jadi **3 zona** (atas, tengah, bawah)
9. Klasifikasikan objek berdasarkan **luas bounding box di zona masing-masing**
10. Anotasi frame dengan **bounding box + label (“Motor” / “Mobil”)**
11. Simpan video output hasil deteksi

---

## ✅ Hasil

* Video output akan berisi:

  * **Kotak (bounding box)** di sekitar kendaraan
  * Label **“Motor”** atau **“Mobil”**
* Disimpan di:

  ```python
  /content/klasifikasi_kendaraan.mp4
  ```

---

## 📌 Catatan

* **Parameter penting yang dapat disesuaikan:**

  * Ukuran kernel morfologi (default: 3x3)
  * Ambang batas luas objek untuk klasifikasi
  * Zona vertikal frame (atas/tengah/bawah)

* **Keterbatasan:**

  * Akurasi tergantung pada kualitas video, cahaya, dan sudut kamera
  * Tidak menggunakan model machine learning
  * Deteksi terbatas pada motor dan mobil

---

## 🔄 Pengembangan Selanjutnya

* Integrasi dengan machine learning atau deep learning
* Analisis Jumlah kendaraan
* Deteksi lebih banyak jenis kendaraan (truk, bus, sepeda, dll)

---

