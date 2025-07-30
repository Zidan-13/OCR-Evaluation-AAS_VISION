# UAS Vision - Optical Character Recognition Evaluation

## Deskripsi Proyek

Proyek ini bertujuan untuk melakukan ekstraksi teks dari gambar menggunakan Optical Character Recognition (OCR), kemudian membandingkan hasilnya dengan ground truth untuk menghitung error. Sistem akan menghitung nilai Character Error Rate (CER) untuk setiap prediksi dan menyediakan metrik evaluasi secara keseluruhan.

## Struktur Folder

```
AAS_VISION/
├── generate_ground_truth_csv.py   # Menggabungkan label ground truth menjadi CSV
├── ocr_results.csv                # Hasil OCR + perhitungan error
├── UAS_VISION.py                  # Main program untuk OCR dan evaluasi
├── test/
│   ├── ground_truth.csv           # Data label acuan
│   ├── test00X_Y.jpg              # Gambar input
│   ├── test00X_Y.txt              # Ground truth per gambar
```

## Cara Menjalankan

1. **Persiapkan lingkungan Python**

   * Install dependensi: `opencv-python`, `pytesseract`, dan `pandas`

```bash
pip install opencv-python pytesseract pandas
```

2. **Jalankan file utama**

```bash
python UAS_VISION.py
```

Hasil akan disimpan dalam file `ocr_results.csv`.

3. **(Opsional) Generate ulang ground truth CSV:**

```bash
python generate_ground_truth_csv.py
```

## Penjelasan File Output (`ocr_results.csv`)

| Kolom         | Keterangan                                           |
| ------------- | ---------------------------------------------------- |
| image         | Nama file gambar                                     |
| ground\_truth | Label asli (dari file .txt)                          |
| prediction    | Hasil OCR dari gambar                                |
| CER\_score    | Nilai error karakter (semakin rendah = semakin baik) |

### COUNTIF = 5

Berarti terdapat 5 prediksi yang sama persis dengan ground truth.

### SUM / rata-rata CER

Mengukur seberapa "jauh" rata-rata kesalahan karakter dari semua prediksi.
Contoh:

* Total CER dari 10 gambar = 5
* Rata-rata CER = 4.65 / 10 = 0.465622843

  Contoh Output

```
image       ground_truth   prediction   CER_score
----------- -------------- ------------ ----------
test001.jpg  B1234XYZ       B1234XYZ      0.0000
...
```

## Catatan Tambahan

* Sistem ini sangat bergantung pada kualitas gambar dan hasil OCR Tesseract.
* File `.txt` pada folder `test/` menjadi acuan ground truth.

---

NAMA : MUHAMMAD ZIDAN SEMBIRING
NIM  : 4222201048
