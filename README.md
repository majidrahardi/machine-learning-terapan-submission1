# Laporan Proyek Machine Learning - Majid Rahardi

## Domain Proyek
Jamur adalah organisme yang memiliki peran penting di alam sebagai pengurai, penghasil obat-obatan, dan sebagai sumber makanan. Namun, di balik manfaat tersebut, jamur juga memiliki sisi berbahaya. Beberapa jenis jamur sangat beracun dan dapat menyebabkan efek buruk jika dikonsumsi oleh manusia. Identifikasi jamur beracun dan dapat dimakan sering kali menjadi tantangan karena beberapa spesies memiliki penampilan yang sangat mirip. Kesalahan dalam identifikasi dapat berakibat fatal, termasuk kasus keracunan yang berujung pada kematian.

Di lapangan, proses pengenalan jamur sering dilakukan secara manual berdasarkan ciri-ciri fisik seperti warna, bentuk, bau, dan tekstur. Pendekatan ini membutuhkan keahlian khusus dan pengalaman yang cukup mendalam untuk menghindari kesalahan yang berbahaya. Hal ini menciptakan kebutuhan akan metode klasifikasi yang lebih andal, otomatis, dan akurat, yang dapat membantu masyarakat umum dan pengumpul jamur untuk mengidentifikasi jamur secara aman.

Dalam konteks teknologi dan data, perkembangan dalam pembelajaran mesin (machine learning) menawarkan peluang untuk membangun model prediktif yang mampu mengklasifikasikan jamur berdasarkan atribut fisiknya. Dengan dataset yang memadai, seperti yang tersedia pada dataset klasifikasi jamur dari Kaggle, kita dapat melatih model untuk membedakan antara jamur yang dapat dimakan dan yang beracun. Proyek ini bertujuan untuk memanfaatkan pembelajaran mesin guna menciptakan alat klasifikasi otomatis yang dapat meningkatkan keamanan publik, mempercepat proses identifikasi, dan mengurangi risiko kesalahan fatal akibat konsumsi jamur beracun.

Proyek ini tidak hanya memiliki nilai praktis, tetapi juga dapat berfungsi sebagai kontribusi penting dalam edukasi dan keselamatan publik. Dengan mengotomatiskan identifikasi jamur, kita dapat memberikan solusi inovatif yang berguna bagi kolektor jamur, komunitas peneliti, dan masyarakat umum yang terpapar risiko konsumsi jamur yang salah.

## Business Understanding
### Problem Statements
1. **Klasifikasi Jamur Beracun dan Dapat Dimakan**  
   Banyak jamur yang terlihat serupa, tetapi memiliki efek yang sangat berbeda jika dikonsumsi. Beberapa jamur sangat beracun, sementara yang lain dapat dimakan dengan aman. Kesalahan dalam identifikasi dapat menyebabkan keracunan serius atau bahkan kematian. Oleh karena itu, diperlukan sistem klasifikasi yang akurat untuk membedakan jamur yang dapat dimakan dari yang beracun berdasarkan karakteristik fisiknya.
   
2. **Ketergantungan pada Ciri-ciri Fisik**  
   Identifikasi jamur di lapangan sering kali bergantung pada ciri-ciri fisik, seperti bentuk tudung, warna insang, dan bau. Proses ini tidak hanya memakan waktu tetapi juga memerlukan keahlian. Mengotomatiskan klasifikasi ini akan mempermudah pengguna umum, seperti kolektor jamur atau peneliti, dalam membuat keputusan yang aman.

### Goals
1. **Membangun Model Klasifikasi**  
   Tujuan utama adalah membangun model pembelajaran mesin yang dapat mengklasifikasikan jamur sebagai "dapat dimakan" atau "beracun" dengan tingkat akurasi tinggi berdasarkan atribut-atribut fisik yang diberikan dalam dataset.
   
2. **Meningkatkan Keamanan Publik**  
   Dengan memiliki alat klasifikasi yang andal, pengguna dapat mengurangi risiko kesalahan dalam identifikasi jamur yang berbahaya. Hal ini dapat mengurangi jumlah keracunan akibat jamur, memberikan keamanan lebih bagi pengumpul jamur dan masyarakat umum.
   
3. **Mengotomatiskan Identifikasi Jamur**  
   Membantu pengguna umum dalam mengidentifikasi jamur tanpa memerlukan pengetahuan mendalam tentang klasifikasi jamur dengan menggunakan ciri-ciri fisik yang diinputkan ke dalam model.

### Solution Statements
1. **Pengumpulan Data dan Pemrosesan Data**  
   Menggunakan dataset klasifikasi jamur dari Kaggle, dataset yang sudah tersedia ini berisi atribut-atribut fisik jamur. Langkah pertama adalah memastikan data bersih, mengatasi nilai yang hilang, dan menormalkan atribut.
   
2. **Pengembangan Model Pembelajaran Mesin**  
   Menggunakan metode pembelajaran mesin yang sesuai seperti algoritma klasifikasi (contoh: Random Forest, Decision Tree, atau Logistic Regression) untuk membangun model klasifikasi yang dapat memprediksi label "dapat dimakan" atau "beracun" berdasarkan atribut fisik.
   
3. **Evaluasi Model dan Optimalisasi**  
   Mengevaluasi model menggunakan metrik seperti akurasi, presisi, dan recall untuk memastikan kinerja yang baik. Melakukan optimalisasi model untuk meningkatkan performa dan mengurangi tingkat kesalahan.
   
4. **Implementasi dan Penyediaan Alat Identifikasi**  
   Mengimplementasikan model dalam aplikasi yang dapat digunakan oleh pengguna umum untuk mengidentifikasi jamur berdasarkan input karakteristik fisik, sehingga mengurangi potensi risiko konsumsi jamur yang beracun.

## Data Understanding
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
Tahap Data Preparation bertujuan untuk memastikan bahwa data yang digunakan dalam pembuatan model klasifikasi memiliki kualitas yang baik dan siap untuk diolah. Data yang bersih, bebas dari inkonsistensi, dan disiapkan dengan baik merupakan prasyarat penting untuk mendapatkan hasil analisis yang akurat dan model pembelajaran mesin yang optimal. Berikut adalah langkah-langkah yang dilakukan dalam proses persiapan data pada proyek klasifikasi jamur ini:

### 1. Eksplorasi Data Awal
Dataset yang digunakan berisi informasi tentang spesies jamur, termasuk label klasifikasi "edible" (dapat dimakan) atau "poisonous" (beracun) serta 22 atribut fisik lainnya. Tahap awal mencakup eksplorasi data untuk memahami distribusi atribut, identifikasi tipe data, dan analisis awal nilai-nilai yang ada pada setiap atribut.

### 2. Penanganan Data yang Hilang
Salah satu tantangan utama dalam dataset ini adalah adanya atribut dengan nilai yang hilang, khususnya pada kolom `stalk-root`, yang memiliki beberapa nilai yang direpresentasikan dengan tanda '?' (missing). Nilai-nilai yang hilang ini memerlukan penanganan yang tepat, seperti:
- Penggantian dengan nilai tertentu (imputasi)
- Penghapusan baris
- Transformasi data

### 3. Pembersihan Data
Proses pembersihan mencakup penanganan inkonsistensi data, memastikan format data konsisten, serta menghapus atau menangani atribut yang kurang relevan. Sebagai contoh, atribut `veil-type` memiliki nilai yang seragam ('p') untuk semua entri, sehingga atribut ini dihapus karena tidak memberikan variasi atau informasi yang berguna.

### 4. Transformasi dan Encoding Data Kategorikal
Sebagian besar atribut dalam dataset adalah kategori, dengan nilai-nilai berbentuk simbol atau huruf. Agar data ini dapat digunakan dalam model pembelajaran mesin, diperlukan proses encoding untuk mengubah data kategorikal menjadi bentuk numerik. Teknik seperti:
- **One-hot encoding**
- **Label encoding**  
digunakan sesuai kebutuhan untuk setiap atribut.

### 5. Pemeriksaan Ketidakseimbangan Kelas
Mengingat bahwa target prediksi adalah label klasifikasi jamur (dapat dimakan atau beracun), penting untuk memeriksa keseimbangan distribusi kelas target. Ketidakseimbangan kelas yang signifikan dapat mempengaruhi performa model. Jika ditemukan, langkah-langkah penanganan seperti:
- **Synthetic Minority Oversampling Technique (SMOTE)**

### 6. Pemisahan Data
Data yang sudah bersih dan siap digunakan kemudian dibagi menjadi data latih (training set) dan data uji (testing set). Pembagian ini dilakukan untuk memastikan bahwa model dapat dievaluasi secara objektif, dengan mengukur kinerjanya pada data yang belum pernah dilihat sebelumnya.

### Tujuan
Proses persiapan data bertujuan untuk memastikan bahwa data yang dimasukkan ke dalam model pembelajaran mesin tidak hanya bersih dan berkualitas tinggi, tetapi juga siap secara format dan distribusi untuk diolah. Dengan mempersiapkan data secara hati-hati, kita dapat meminimalkan potensi bias, meningkatkan keandalan model, dan mendapatkan prediksi yang akurat dalam mengklasifikasikan jamur sebagai "dapat dimakan" atau "beracun".

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
