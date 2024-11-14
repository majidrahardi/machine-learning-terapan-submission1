# Laporan Proyek Machine Learning - Majid Rahardi

## Domain Proyek

Pada bagian ini, kamu perlu menuliskan latar belakang yang relevan dengan proyek yang diangkat.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Jelaskan mengapa dan bagaimana masalah tersebut harus diselesaikan
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.
  
  Format Referensi: [Judul Referensi](https://scholar.google.com/) 

## Business Understanding

Pada bagian ini, kamu perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Pernyataan Masalah 1
- Pernyataan Masalah 2
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Jawaban pernyataan masalah 1
- Jawaban pernyataan masalah 2
- Jawaban pernyataan masalah n

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Statement” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution statement. Misalnya, menggunakan dua atau lebih algoritma untuk mencapai solusi yang diinginkan atau melakukan improvement pada baseline model dengan hyperparameter tuning.
    - Solusi yang diberikan harus dapat terukur dengan metrik evaluasi.

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai data yang Anda gunakan dalam proyek. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

### Deskripsi Dataset
Dataset ini berisi data tentang berbagai spesies jamur, dengan tujuan mengklasifikasikan apakah jamur tersebut dapat dimakan (edible) atau beracun (poisonous). Setiap entri dalam dataset mewakili satu spesimen jamur dengan berbagai atribut yang menggambarkan karakteristik fisiknya. Adapun dataset dapat diakses secara publik di [link dataset](https://www.kaggle.com/datasets/uciml/mushroom-classification).

### Ukuran Dataset
- **Jumlah entri (baris)**: 8.124
- **Jumlah atribut (kolom)**: 23

### Atribut dalam Dataset
1. **class**: Kategori jamur
   - Nilai: 'e' (edible), 'p' (poisonous)
2. **cap-shape**: Bentuk tudung jamur
   - Nilai: 'b' (bell), 'c' (conical), 'x' (convex), 'f' (flat), 'k' (knobbed), 's' (sunken)
3. **cap-surface**: Permukaan tudung jamur
   - Nilai: 'f' (fibrous), 'g' (grooves), 'y' (scaly), 's' (smooth)
4. **cap-color**: Warna tudung jamur
   - Nilai: 'n' (brown), 'b' (buff), 'c' (cinnamon), 'g' (gray), 'r' (green), 'p' (pink), 'u' (purple), 'e' (red), 'w' (white), 'y' (yellow)
5. **bruises**: Adanya memar pada jamur
   - Nilai: 't' (true), 'f' (false)
6. **odor**: Bau jamur
   - Nilai: 'a' (almond), 'l' (anise), 'c' (creosote), 'y' (fishy), 'f' (foul), 'm' (musty), 'n' (none), 'p' (pungent), 's' (spicy)
7. **gill-attachment**: Keterikatan insang
   - Nilai: 'a' (attached), 'd' (descending), 'f' (free), 'n' (notched)
8. **gill-spacing**: Jarak antar insang
   - Nilai: 'c' (close), 'w' (crowded)
9. **gill-size**: Ukuran insang
   - Nilai: 'b' (broad), 'n' (narrow)
10. **gill-color**: Warna insang
    - Nilai: 'k' (black), 'n' (brown), 'b' (buff), 'h' (chocolate), 'g' (gray), 'r' (green), 'o' (orange), 'p' (pink), 'u' (purple), 'e' (red), 'w' (white), 'y' (yellow)
11. **stalk-shape**: Bentuk batang
    - Nilai: 'e' (enlarging), 't' (tapering)
12. **stalk-root**: Akar batang
    - Nilai: 'b' (bulbous), 'c' (club), 'u' (cup), 'e' (equal), 'z' (rhizomorphs), 'r' (rooted), '?' (missing)
13. **stalk-surface-above-ring**: Permukaan batang di atas cincin
    - Nilai: 'f' (fibrous), 'y' (scaly), 'k' (silky), 's' (smooth)
14. **stalk-surface-below-ring**: Permukaan batang di bawah cincin
    - Nilai: 'f' (fibrous), 'y' (scaly), 'k' (silky), 's' (smooth)
15. **stalk-color-above-ring**: Warna batang di atas cincin
    - Nilai: 'n' (brown), 'b' (buff), 'c' (cinnamon), 'g' (gray), 'o' (orange), 'p' (pink), 'e' (red), 'w' (white), 'y' (yellow)
16. **stalk-color-below-ring**: Warna batang di bawah cincin
    - Nilai: 'n' (brown), 'b' (buff), 'c' (cinnamon), 'g' (gray), 'o' (orange), 'p' (pink), 'e' (red), 'w' (white), 'y' (yellow)
17. **veil-type**: Jenis selubung
    - Nilai: 'p' (partial), 'u' (universal) (Catatan: Semua entri memiliki nilai 'p')
18. **veil-color**: Warna selubung
    - Nilai: 'n' (brown), 'o' (orange), 'w' (white), 'y' (yellow)
19. **ring-number**: Jumlah cincin pada batang
    - Nilai: 'n' (none), 'o' (one), 't' (two)
20. **ring-type**: Jenis cincin
    - Nilai: 'c' (cobwebby), 'e' (evanescent), 'f' (flaring), 'l' (large), 'n' (none), 'p' (pendant), 's' (sheathing), 'z' (zone)
21. **spore-print-color**: Warna cetakan spora
    - Nilai: 'k' (black), 'n' (brown), 'b' (buff), 'h' (chocolate), 'r' (green), 'o' (orange), 'u' (purple), 'w' (white), 'y' (yellow)
22. **population**: Populasi jamur
    - Nilai: 'a' (abundant), 'c' (clustered), 'n' (numerous), 's' (scattered), 'v' (several), 'y' (solitary)
23. **habitat**: Habitat jamur
    - Nilai: 'g' (grasses), 'l' (leaves), 'm' (meadows), 'p' (paths), 'u' (urban), 'w' (waste), 'd' (woods)

### Catatan Penting
- Atribut `veil-type` memiliki nilai yang sama untuk semua entri ('p'), sehingga tidak memberikan informasi yang bervariasi dan dapat diabaikan dalam analisis.
- Atribut `stalk-root` memiliki beberapa nilai yang hilang ('?'), sehingga memerlukan penanganan khusus selama analisis data.

Dataset ini dapat digunakan untuk membangun model klasifikasi yang memprediksi apakah suatu jamur dapat dimakan atau beracun berdasarkan karakteristik fisiknya.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
