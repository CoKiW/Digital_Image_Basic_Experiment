# Digital Image Basic Experiment

## Deskripsi Project
 
Eksperimen operasi dasar pada **sinyal diskrit 1D** dan **citra 2D** menggunakan Python. Mencakup penjumlahan, penggeseran, amplifikasi, dan pengujian sifat linieritas sistem (homogenitas & additivitas).
 
---
 
## Library yang Digunakan
 
| Library | Kegunaan |
|---------|----------|
| `numpy` | Operasi array dan sinyal diskrit |
| `matplotlib` | Visualisasi sinyal dan citra |
| `opencv-python` | Operasi citra 2D |
| `Pillow` | Dukungan format citra |
 
---
 
## Cara Menjalankan
 
```bash
git clone https://github.com/CoKiW/Digital_Image_Basic_Experiment.git
cd operasi-dasar-sinyal-citra
pip install -r requirements.txt
jupyter notebook notebook/TugasEksperimen_PSD_A2_NaufalRazzaqMu_afa.ipynb
```
 
---

## Ringkasan Hasil Eksperimen
 
### Sinyal 1D
 
| Operasi | Parameter | Hasil |
|---------|-----------|-------|
| Penjumlahan | `x1 + x2` | Superposisi; untuk n≥5 terjadi pergeseran DC +1 |
| Penggeseran | k = -3, 0, 4 | k>0 = delay; k<0 = advance |
| Amplifikasi | α = 0.5, 1, 2, -1 | α=-1 membalik fase 180°; α>1 perbesar amplitudo |
 
### Citra 2D
 
Dua citra sintetik grayscale 200×200 piksel: lingkaran (nilai 180) dan kotak (nilai 100).
 
| Operasi | Metode | Hasil |
|---------|--------|-------|
| Penjumlahan | `cv2.add` (clipping) | Area overlap jenuh di 255 |
| Penjumlahan | Normalisasi | Detail terjaga, kontras global berubah |
| Translasi | `cv2.warpAffine` | Objek bergeser; area kosong diisi 0 |
| Amplifikasi | `cv2.multiply` | α>1 terang; α<1 gelap; clipping otomatis |
 
### Uji Sistem Linier
 
| Sistem | Homogenitas | Additivitas | Kesimpulan |
|--------|-------------|-------------|------------|
| T₁(x) = 2x | ✅ Ya | ✅ Ya (selisih = 0.0) | **Linier** |
| T₂(x) = x² | ❌ Tidak | ❌ Tidak (ada suku silang 2x₁x₂) | **Nonlinier** |
 
---
 
## Kesimpulan
 
1. Penjumlahan sinyal menghasilkan superposisi element-wise — dasar prinsip LTI.
2. Penggeseran k>0 memodelkan delay transmisi; k<0 memodelkan advance.
3. Amplifikasi α<0 membalik fase 180°, bukan sekadar mengubah amplitudo.
4. Clipping dan normalisasi pada penjumlahan citra punya trade-off berbeda.
5. T₁(x)=2x terbukti linier secara matematis dan numerik (selisih=0).
6. Linieritas menentukan apakah FFT dan filter konvensional bisa diterapkan secara valid.
