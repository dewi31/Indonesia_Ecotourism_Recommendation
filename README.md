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

|   Parameter   |   rating  | 
|---------------|--------|
| count         | 182  | 
| mean          | 4.42 |   
| std           | 0.22  | 
| min           | 3.40   |
| 25%           | 4.30     | 
| 50%           | 4.40     | 
| 75%           | 4.60     |  
| max           | 5.00    | 

Tabel 1. Deskripsi statistik data rating

Pada Tabel 1 dapat dilihat bahwa nilai rating terendah adalah 3.40 dari 5 dan nilai rating tertinggi adalah 5.00 dari 5.

#### Analisis distribusi rata-rata data `rating`

![image](https://github.com/dewi31/Indonesia_Ecotourism_Recommendation/assets/87901348/41873bba-36fa-432d-a5ad-6af969ab0cb9)

Gambar 1. Persebaran rating ekowisata

Pada Gambar 1. dapat dilihat bahwa rata-rata rating ekowisata tersebar dari rating 3.9 hingga 5.0.

#### Analisis fitur kategorik pada `category` ekowisata

![image](https://github.com/dewi31/Indonesia_Ecotourism_Recommendation/assets/87901348/69c256ea-e6bf-4c74-b2a4-42be8b0a1f21)

Gambar 2. Kategori pada ekowisata

Dari Gambar 2. dapat diambil kesimpulan bahwa satu tempat ekowisata memiliki beberapa kategori atau satu kategori. Dari gambar tersebut juga dapat dilihat bahwa kategori cagar alam memiliki jumlah data yang paling banyak yakni 41 tempat ekowisata.

#### Analisis fitur kategorik pada `city` ekowisata

|   Kota  |   Jumlah | 
|---------------|--------|
| Yogyakarta         | 53  | 
| Bandung          | 36 |   
| Semarang          | 17  | 
| Jakarta          | 12  | 

Tabel 2. Top-4 kota dengan ekowisata terbanyak

Pada Tabel 2 merupakan 4 kota dengan jumlah ekowisata terbanyak. Kategori kota lainnya hanya memiliki ekowisata berkisar 1-3.

## Data Preparation
Tahap ini bertujuan untuk mempersiapkan data yang akan digunakan untuk bisa masuk ke dalam tahapan *modelling*. Di sini dilakukan penghapusan kolom yang tidak diperlukan , pengecekan, dan pembersihkan data yang bernilai kosong.

1. Penghapusan kolom yang tidak diperlukan.
   Pada dataset `eco_place.csv` variabel yang dibutuhkan diantaranya `place_id`, `place_name`, dan `category` karena digunakan untuk membuat model sistem rekomendasi. Variabel selain ketiga tersebut kemudian dihapus
2. Pengecekan data yang bernilai kosong
   Berdasarkan hasil pengecekan, data pada `place_id`, `place_name`, dan `category` tidak ada yang bernilai kosong. 

## Modeling


## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
