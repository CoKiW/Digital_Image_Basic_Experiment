# Digital Image Basic Experiment

Project ini berisi implementasi eksperimen operasi dasar pada **sinyal diskrit 1D** dan **citra 2D** menggunakan Python. Eksperimen mencakup operasi penjumlahan, penggeseran (*shifting*), dan amplifikasi, serta pengujian sifat linieritas sistem melalui uji homogenitas dan additivitas.
 
Fokus utama adalah memahami bagaimana operasi matematis sederhana menjadi fondasi dari konsep yang lebih besar dalam Pengolahan Sinyal Digital, seperti superposisi, sistem linier, *filtering*, *image blending*, dan augmentasi data citra.
 
---
 
## Topik yang Dieksperimenkan
 
- **Bagian A** — Operasi pada Sinyal 1D
  - A.1 Membuat sinyal diskrit (sinusoidal & unit step)
  - A.2 Operasi penjumlahan sinyal
  - A.3 Operasi penggeseran sinyal (time shifting)
  - A.4 Operasi amplifikasi sinyal
- **Bagian B** — Operasi pada Citra 2D
  - B.1 Membaca dan menampilkan citra
  - B.2 Operasi penjumlahan citra (clipping & normalisasi)
  - B.3 Operasi penggeseran citra (translasi)
  - B.4 Operasi amplifikasi citra + histogram
- **Bagian C** — Uji Sistem Linier
  - C.1 Uji homogenitas
  - C.2 Uji additivitas
  - C.3 Perbandingan sistem linier vs nonlinier
- **Bagian D** — Analisis HOTS & Studi Kasus
---
 
## Library yang Digunakan
 
| Library | Versi | Kegunaan |
|---------|-------|----------|
| `numpy` | ≥ 1.24 | Operasi array dan sinyal diskrit |
| `matplotlib` | ≥ 3.7 | Visualisasi sinyal dan citra |
| `opencv-python` | ≥ 4.8 | Operasi citra 2D |
| `Pillow` | ≥ 10.0 | Dukungan pembacaan format citra |
 
---
 
## Cara Menjalankan Notebook
 
### 1. Clone Repository
 
```bash
git clone https://github.com/naufalrazzaq/operasi-dasar-sinyal-citra.git
cd operasi-dasar-sinyal-citra
```
 
### 2. Install Dependencies
 
```bash
pip install -r requirements.txt
```
 
### 3. Jalankan Notebook
 
```bash
jupyter notebook notebook/operasi_sinyal_citra.ipynb
```
 
Atau buka langsung di **Google Colab** dengan mengupload file `.ipynb` dari folder `notebook/`.
 
> **Catatan:** Pastikan file citra (`image1.jpg`, `image2.jpg`) tersedia di folder `images/` sebelum menjalankan sel pada Bagian B.
 
---
 
## Ringkasan Hasil Eksperimen
 
### Operasi Sinyal 1D
 
| Operasi | Parameter | Hasil |
|---------|-----------|-------|
| Penjumlahan | $x_1[n] + x_2[n]$ | Superposisi; untuk $n \geq 5$ terjadi pergeseran DC +1 |
| Penggeseran | $k = -3, 0, 4$ | $k > 0$ = delay; $k < 0$ = advance; $k = 0$ = identitas |
| Amplifikasi | $\alpha = 0.5, 1, 2, -1$ | $\alpha < 0$ membalik fase 180°; $\alpha > 1$ memperbesar amplitudo |
 
### Operasi Citra 2D
 
| Operasi | Metode | Hasil |
|---------|--------|-------|
| Penjumlahan | Clipping (`cv2.add`) | Area overlap jenuh putih (255) |
| Penjumlahan | Normalisasi | Detail terjaga, kontras global berubah |
| Translasi | `cv2.warpAffine` | Objek bergeser; area kosong diisi 0 (hitam) |
| Amplifikasi | `cv2.multiply` | $\alpha > 1$ terang; $\alpha < 1$ gelap; clipping otomatis |
 
### Uji Sistem Linier
 
| Sistem | Homogenitas | Additivitas | Kesimpulan |
|--------|-------------|-------------|------------|
| $T_1(x) = 2x$ | ✅ Ya | ✅ Ya | **Linier** |
| $T_2(x) = x^2$ | ❌ Tidak | ❌ Tidak | **Nonlinier** |
 
Selisih numerik uji additivitas $T_1 = 0$ (identik), sedangkan $T_2 \neq 0$ karena suku silang $2x_1 x_2$.
 
---
 
## Kesimpulan Singkat
 
1. Penjumlahan sinyal menghasilkan superposisi — dasar dari prinsip *linear time-invariant* (LTI) system.
2. Penggeseran memodelkan *delay* transmisi; penting dalam *time alignment* multi-sinyal.
3. Amplifikasi negatif ($\alpha < 0$) membalik fase, bukan sekadar mengubah amplitudo.
4. Pada citra 2D, *clipping* dan normalisasi memberikan trade-off berbeda antara saturasi dan preservasi detail.
5. $T_1(x) = 2x$ terbukti linier; $T_2(x) = x^2$ terbukti nonlinier secara matematis dan numerik.
6. Pemahaman linieritas menentukan apakah alat analisis seperti FFT dan filter konvensional dapat diterapkan secara valid.
