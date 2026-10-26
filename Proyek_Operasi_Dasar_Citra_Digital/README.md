# Proyek Operasi Dasar Citra Digital

**Nama:** Andre Wijaya  
**NIM:** 24260024

Proyek ini berisi dua contoh operasi dasar pengolahan citra digital menggunakan foto `foto.jpg` sebagai citra sumber:

1. `Tugas_Gaussian_Median_Filter.ipynb` — perbandingan Gaussian Blur dan Median Filter.
2. `Tugas_Deteksi_Tepi_Sobel.ipynb` — deteksi tepi menggunakan operator Sobel.

## Tujuan
Menerapkan operator Sobel untuk menonjolkan perubahan intensitas pada foto. Metode ini menghitung gradien pada arah X dan Y lalu menggabungkannya menjadi peta kekuatan tepi. Foto sumber tidak diubah.

## Struktur folder

```text
Proyek_Operasi_Dasar_Citra_Digital/
├── foto.jpg
├── README.md
├── Tugas_Gaussian_Median_Filter.ipynb
├── Tugas_Deteksi_Tepi_Sobel.ipynb
└── hasil/
    ├── gaussian_blur.png
    ├── median_filter.png
    ├── salt_pepper_noise.png
    ├── hasil_sobel.png
    ├── gradien_x.png
    └── gradien_y.png
```

Folder `hasil/` berisi contoh hasil yang dibuat dengan menjalankan operasi pada foto sumber. Jika notebook dijalankan kembali, file hasil dapat dibuat ulang.

## 1. Membaca citra dan memeriksa data
OpenCV membaca kanal warna dalam urutan BGR; untuk Matplotlib gambar dikonversi menjadi RGB.
<img width="359" height="223" alt="image" src="https://github.com/user-attachments/assets/60f23778-37fe-412a-8dd9-c5e1d205ec3c" />
## 2. Menghitung gradien Sobel
`Gx` menunjukkan perubahan intensitas pada arah X dan `Gy` pada arah Y. Magnitudo menggabungkan kedua arah tersebut. Data gradien dihitung dalam tipe float agar nilai negatif dan nilai di luar rentang 0–255 tidak terpotong sebelum perhitungan.
<img width="263" height="73" alt="image" src="https://github.com/user-attachments/assets/211cb4aa-c2a4-4926-99b9-270ad3025ea8" />
## 3. Visualisasi hasil
Bagian terang pada peta Sobel menunjukkan perubahan intensitas yang kuat. Tekstur, tulisan, dan detail latar juga dapat muncul sebagai tepi.
<img width="358" height="158" alt="image" src="https://github.com/user-attachments/assets/0922a5fd-e1f4-47b3-ba32-d3209d2ae7ef" />
## 4. Analisis gradien X dan Y
Visualisasi nilai absolut menunjukkan kekuatan gradien tanpa membedakan tanda positif dan negatif. Tabel berikut merangkum nilai gradien yang dihitung dari foto.
<img width="368" height="314" alt="image" src="https://github.com/user-attachments/assets/0ffb57e2-6841-4e08-8f36-00184d224a92" />
## 5. Menyimpan hasil
Hasil deteksi tepi dan gradien disimpan di folder `hasil/`. File foto asli tetap aman.
<img width="419" height="64" alt="image" src="https://github.com/user-attachments/assets/c672e3f6-7e00-4af0-84b3-0812b66f8e2d" />

## Instalasi

Pastikan Python 3 sudah terpasang. Dari terminal pada folder proyek, jalankan:

```bash
python -m pip install jupyter ipykernel opencv-python numpy matplotlib pandas pillow
```

Buka folder ini di VS Code, buka salah satu file `.ipynb`, pilih kernel Python, lalu jalankan sel secara berurutan atau gunakan **Run All**.

Alternatifnya, jalankan Jupyter Notebook dari terminal:

```bash
jupyter notebook
```

## Notebook 1 — Gaussian Blur dan Median Filter

Notebook pertama membaca foto, menampilkan informasi dimensi dan nilai piksel, membuat simulasi salt-and-pepper noise pada salinan citra grayscale, lalu membandingkan Gaussian Blur dengan Median Filter. Hasil dibandingkan menggunakan MSE dan PSNR. Foto asli tidak ditimpa.

## Notebook 2 — Sobel Edge Detection

Notebook kedua mengubah foto menjadi grayscale, menghitung gradien Sobel arah X dan Y, menggabungkan gradien menjadi magnitudo, menampilkan visualisasi, dan menyimpan hasil deteksi tepi.

## Catatan interpretasi

- Nilai piksel grayscale umumnya berada pada rentang 0–255.
- MSE mengukur rata-rata kuadrat perbedaan piksel terhadap citra referensi; semakin kecil berarti semakin dekat secara numerik.
- PSNR dinyatakan dalam dB; angka lebih besar umumnya berarti hasil lebih dekat secara numerik dengan referensi.
- MSE/PSNR tidak selalu sepenuhnya mewakili kualitas visual yang dirasakan.
- Sobel mendeteksi perubahan intensitas, sehingga tekstur dan tulisan juga dapat terlihat sebagai tepi.
- File sumber `foto.jpg` dipertahankan; semua hasil ditulis sebagai file baru di folder `hasil/`.
