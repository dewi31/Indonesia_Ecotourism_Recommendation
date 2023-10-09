# Indonesia's Ecotourism Recommendation - Dewi Wahidatul Karimah

## Project Overview

  Ekowisata merupakan suatu konsep pengembangan wisata yang menawarkan bentuk wisata yang ramah terhadap kelestarian alam dan budaya. Pengertian ekowisata adalah kegiatan wisata bertanggung jawab yang berbasis utama pada kegiatan wisata alam, dengan mengikutsertakan pula sebagian kegiatan wisata pedesaan dan wisata budaya. Pada dasarnya ekowisata merupakan kegiatan konservasi terhadap alam dan lingkungan yang dikemas dalam sebuah destinasi pariwiata, yang juga memiliki dampak terhadap perekonomian setempat [1].

  Ekowisata  di  Indonesia  setiap  tahunnya  mengalami  perkembangan  yang  cukup baik. Menurut *Forbes Advisor* Indonesia menempati urutan ke-9 indeks ekowisata (*Ecotourism Index*) di antara negara-negara destinasi wisata internasional dengan perolehan 80,1 poin dari 100 poin pada tahun 2023[2]. Beberapa contoh destinasi ekowisata yang sudah dikenal diberbagai penjuru dunia diantaranya Taman Nasional Komodo, Tangkahan Ecotourism, Desa Wisata Penglipuran,  Pulau  Rubiah,  Gunung  Api  Nglanggeran,  Desa  Wisata  Tembi,  serta Kawah  Ijen [1].  Dari  ketujuh destinasi  yang  sudah  terkenal  tersebut  masih  banyak  lagi ekowisata di Indonesia yang belum dikenal wisatawan domestik ataupun mancanegara.

  Berdasarkan permasalahan tersebut, maka proyek ini dilakukan untuk memberi rekomendasi ekowisata di Indonesia berdasarkan kemiripan dari preferensi ekowisata yang dikunjungi oleh wisatawan sebelumnya. Diharapkan dengan memberikan rekomendasi ekowisata yang sesuai, wisatawan dapat mengetahui ekowisata yang tersedia di Indonesia dan juga mendatangkan keuntungan bagi pengelola tempat ekowisata.

## Business Understanding

### Problem Statements

1. Bagaimana cara menyiapkan data sebelum dimasukkan ke dalam model *machine learning* ?
2. Bagaimana membuat model *machine learning* yang dapat memberikan sistem rekomendasi ekowisata berdasarkan kemiripan ekowisata yang dikunjungi oleh wisatawan sebelumnya ?

### Goals

Berdasarkan permasalahan yang diuraikan, maka tujuan dari proyek ini adalah:
1. Melakukan analisa data dan *data preparation* sebelum dimasukkan ke dalam model *machine learning* ?
2. Membuat model *machine learning* yang dapat memberikan sistem rekomendasi ekowisata berdasarkan kemiripan ekowisata yang dikunjungi oleh wisatawan sebelumnya

### Solution statements

Solusi yang dapat dilakukan untuk mencapai tujuan proyek ini diantaranya:
1. Melakukan analisis univariat pada data untuk mengetahui dan mengidentifikasi karakteristik dari suatu variabel.
2. Melakukan beberapa tahapan *data preparation* seperti penghapusan beberapa kolom yang tidak diperlukan dan pengecekan *missing value* pada data.
3. Melakukan pembuatan model rekomendasi dengan pendekatan *content based filtering*. Pendekatan *Content-based filtering* bertujuan untuk memberikan rekomendasi berdasarkan kemiripan atribut dari item atau barang yang disukai. 

## Data Understanding
Dataset yang digunakan dalam proyek ini adalah dataset [Indonesia's Ecotourism](https://www.kaggle.com/datasets/farazbeniqnomf/indonesiaecotourism?select=eco_rating.csv) yang diambil dari *Kaggle* dengan `eco_place.csv` sebagai dataset yang digunakan.

Berikut informasi pada dataset `eco_place.csv` :
+ Dataset memiliki format CSV.
+ Dataset memiliki 182 sample dengan 13 fitur.
+ Dataset memiliki 1 fitur bertipe float(64), 1 fitur bertipe int64, dan 11 fitur bertipe object.
+ Terdapat missing value pada dataset.

### Variabel-variabel pada dataset:
+ place_id = ID dari setiap tempat ekowisata
+ place_name = Nama tempat ekowisata
+ place_description = Deskripsi dari tempat ekowisata
+ category = Kategoti ekowisata (Bahari, Tempat Wisata, Budaya, dll)
+ city = Kota dari tempat ekowisata
+ price = Harga masuk tempat ekowisata
+ rating = rating tempat ekowisata
+ description_location = Alamat tempat ekowisata
+ place_img = link foto tempat ekowisata
+ gallery_photo_img1 = link foto keadaan di dalam tempat ekowisata ke-1
+ gallery_photo_img2 = link foto keadaan di dalam tempat ekowisata ke-2
+ gallery_photo_img3 = link foto keadaan di dalam tempat ekowisata ke-3
+ place_map = link alamat untuk menuju tempat ekowisata

### Univariate Analysis

Univariate Analysis digunakan untuk menganalisis tiap variabel dalam suatu data

#### Analisis data `rating`

|   Parameter   |   age  | a
|---------------|--------|-------------------|-------|
| count         | 4981   |   4981            | 4981  |
| mean          | 43.42  |   105.94          | 28.50 |
| std           | 22.66  |   45.08           | 6.79  |
| min           | 0.08   |   55.12           | 14    |
| 25%           | 25     |   77.23           | 23.7  |
| 50%           | 45     |   91.85           | 28.1  |
| 75%           | 61     |   113.86          | 32.6  |
| max           | 82     |   271.74          | 48.9  |

Tabel 1. Deskripsi statistik data rating

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
