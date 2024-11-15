# Laporan Proyek Machine Learning - Majid Rahardi

## Domain Proyek
Jamur adalah organisme yang memiliki peran penting di alam sebagai pengurai, penghasil obat-obatan, dan sebagai sumber makanan [[1](https://pubs.aip.org/aip/acp/article-abstract/2979/1/030003/2917941/Mushroom-classification-using-machine-learning?redirectedFrom=fulltext)]. Namun, di balik manfaat tersebut, jamur juga memiliki sisi berbahaya. Beberapa jenis jamur sangat beracun dan dapat menyebabkan efek buruk jika dikonsumsi oleh manusia. Identifikasi jamur beracun dan dapat dimakan sering kali menjadi tantangan karena beberapa spesies memiliki penampilan yang sangat mirip. Kesalahan dalam identifikasi dapat berakibat fatal, termasuk kasus keracunan yang berujung pada kematian [[2](https://onlinelibrary.wiley.com/doi/10.1155/2020/8849011)].

Di lapangan, proses pengenalan jamur sering dilakukan secara manual berdasarkan ciri-ciri fisik seperti warna, bentuk, bau, dan tekstur. Pendekatan ini membutuhkan keahlian khusus dan pengalaman yang cukup mendalam untuk menghindari kesalahan yang berbahaya [[3](https://www.kaggle.com/datasets/uciml/mushroom-classification)]. Hal ini menciptakan kebutuhan akan metode klasifikasi yang lebih andal, otomatis, dan akurat, yang dapat membantu masyarakat umum dan pengumpul jamur untuk mengidentifikasi jamur secara aman [[4](https://pdfs.semanticscholar.org/75ff/daceb8726502211d5d6f8aa5588859507931.pdf)].

Dalam konteks teknologi dan data, perkembangan dalam pembelajaran mesin (machine learning) menawarkan peluang untuk membangun model prediktif yang mampu mengklasifikasikan jamur berdasarkan atribut fisiknya. Dengan dataset yang memadai, seperti yang tersedia pada dataset klasifikasi jamur dari Kaggle, kita dapat melatih model untuk membedakan antara jamur yang dapat dimakan dan yang beracun [[5](https://drpress.org/ojs/index.php/ajst/article/download/16801/16304)]. Proyek ini bertujuan untuk memanfaatkan pembelajaran mesin guna menciptakan alat klasifikasi otomatis yang dapat meningkatkan keamanan publik, mempercepat proses identifikasi, dan mengurangi risiko kesalahan fatal akibat konsumsi jamur beracun [[6](https://ieeexplore.ieee.org/abstract/document/10469539)].

Proyek ini tidak hanya memiliki nilai praktis, tetapi juga dapat berfungsi sebagai kontribusi penting dalam edukasi dan keselamatan publik. Dengan mengotomatiskan identifikasi jamur, kita dapat memberikan solusi inovatif yang berguna bagi kolektor jamur, komunitas peneliti, dan masyarakat umum yang terpapar risiko konsumsi jamur yang salah [[7](https://jurnal.iaii.or.id/index.php/RESTI/article/view/5498)].

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
- ```python
  df.shape
  ```
  Kode tersebut memiliki luaran:
  ```python
  (8124, 23)
  ```

- ```python
  df.keys()
  ```
  Kode tersebut memiliki luaran:
  ```python
  Index(['class', 'cap-shape', 'cap-surface', 'cap-color', 'bruises', 'odor',
       'gill-attachment', 'gill-spacing', 'gill-size', 'gill-color',
       'stalk-shape', 'stalk-root', 'stalk-surface-above-ring',
       'stalk-surface-below-ring', 'stalk-color-above-ring',
       'stalk-color-below-ring', 'veil-type', 'veil-color', 'ring-number',
       'ring-type', 'spore-print-color', 'population', 'habitat'],
      dtype='object')
  ```

- ```python
  df.isnull().sum()
  ```
  Kode tersebut memiliki luaran:
  ```python
  (gambar)
  ```
- ```python
  df.show()
  ```
  Kode tersebut memiliki luaran:
  ```python
  +-----+---------+-----------+---------+-------+----+---------------+------------+---------+----------+-----------+----------+------------------------+------------------------+----------------------+----------------------+---------+----------+-----------+---------+-----------------+----------+-------+
|class|cap-shape|cap-surface|cap-color|bruises|odor|gill-attachment|gill-spacing|gill-size|gill-color|stalk-shape|stalk-root|stalk-surface-above-ring|stalk-surface-below-ring|stalk-color-above-ring|stalk-color-below-ring|veil-type|veil-color|ring-number|ring-type|spore-print-color|population|habitat|
+-----+---------+-----------+---------+-------+----+---------------+------------+---------+----------+-----------+----------+------------------------+------------------------+----------------------+----------------------+---------+----------+-----------+---------+-----------------+----------+-------+
|    p|        x|          s|        n|      t|   p|              f|           c|        n|         k|          e|         e|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                k|         s|      u|
|    e|        x|          s|        y|      t|   a|              f|           c|        b|         k|          e|         c|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                n|         n|      g|
|    e|        b|          s|        w|      t|   l|              f|           c|        b|         n|          e|         c|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                n|         n|      m|
|    p|        x|          y|        w|      t|   p|              f|           c|        n|         n|          e|         e|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                k|         s|      u|
|    e|        x|          s|        g|      f|   n|              f|           w|        b|         k|          t|         e|                       s|                       s|                     w|                     w|        p|         w|          o|        e|                n|         a|      g|
|    e|        x|          y|        y|      t|   a|              f|           c|        b|         n|          e|         c|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                k|         n|      g|
|    e|        b|          s|        w|      t|   a|              f|           c|        b|         g|          e|         c|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                k|         n|      m|
|    e|        b|          y|        w|      t|   l|              f|           c|        b|         n|          e|         c|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                n|         s|      m|
|    p|        x|          y|        w|      t|   p|              f|           c|        n|         p|          e|         e|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                k|         v|      g|
|    e|        b|          s|        y|      t|   a|              f|           c|        b|         g|          e|         c|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                k|         s|      m|
|    e|        x|          y|        y|      t|   l|              f|           c|        b|         g|          e|         c|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                n|         n|      g|
|    e|        x|          y|        y|      t|   a|              f|           c|        b|         n|          e|         c|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                k|         s|      m|
|    e|        b|          s|        y|      t|   a|              f|           c|        b|         w|          e|         c|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                n|         s|      g|
|    p|        x|          y|        w|      t|   p|              f|           c|        n|         k|          e|         e|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                n|         v|      u|
|    e|        x|          f|        n|      f|   n|              f|           w|        b|         n|          t|         e|                       s|                       f|                     w|                     w|        p|         w|          o|        e|                k|         a|      g|
|    e|        s|          f|        g|      f|   n|              f|           c|        n|         k|          e|         e|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                n|         y|      u|
|    e|        f|          f|        w|      f|   n|              f|           w|        b|         k|          t|         e|                       s|                       s|                     w|                     w|        p|         w|          o|        e|                n|         a|      g|
|    p|        x|          s|        n|      t|   p|              f|           c|        n|         n|          e|         e|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                k|         s|      g|
|    p|        x|          y|        w|      t|   p|              f|           c|        n|         n|          e|         e|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                n|         s|      u|
|    p|        x|          s|        n|      t|   p|              f|           c|        n|         k|          e|         e|                       s|                       s|                     w|                     w|        p|         w|          o|        p|                n|         s|      u|
+-----+---------+-----------+---------+-------+----+---------------+------------+---------+----------+-----------+----------+------------------------+------------------------+----------------------+----------------------+---------+----------+-----------+---------+-----------------+----------+-------+
only showing top 20 rows
  ```


  

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

### 6. Analisis Korelasi
Analisis Korelasi adalah metode statistik yang digunakan untuk mengukur dan mengevaluasi hubungan antara dua variabel atau lebih. Tujuan utama dari analisis ini adalah untuk menentukan seberapa kuat hubungan tersebut dan apakah hubungan tersebut bersifat positif, negatif, atau netral.

### 7. Pemisahan Data
Data yang sudah bersih dan siap digunakan kemudian dibagi menjadi data latih (training set) dan data uji (testing set). Pembagian ini dilakukan untuk memastikan bahwa model dapat dievaluasi secara objektif, dengan mengukur kinerjanya pada data yang belum pernah dilihat sebelumnya.

### Tujuan
Proses persiapan data bertujuan untuk memastikan bahwa data yang dimasukkan ke dalam model pembelajaran mesin tidak hanya bersih dan berkualitas tinggi, tetapi juga siap secara format dan distribusi untuk diolah. Dengan mempersiapkan data secara hati-hati, kita dapat meminimalkan potensi bias, meningkatkan keandalan model, dan mendapatkan prediksi yang akurat dalam mengklasifikasikan jamur sebagai "dapat dimakan" atau "beracun".

## Modeling
### Random Forest:
#### Kelebihan Random Forest:
1. **Akurasi Tinggi** – Lebih akurat dibanding model tunggal.
2. **Tahan Overfitting** – Menggabungkan banyak pohon mengurangi overfitting.
3. **Resisten terhadap Noise** – Tidak mudah terpengaruh data yang salah atau acak.
4. **Menangani Banyak Fitur** – Efektif untuk dataset dengan fitur banyak.
5. **Estimasi Fitur Penting** – Bisa menilai pentingnya setiap fitur.

#### Kekurangan Random Forest:
1. **Kompleksitas Tinggi** – Butuh banyak komputasi dan memori.
2. **Interpretasi Sulit** – Hasilnya tidak mudah dipahami seperti pohon keputusan tunggal.
3. **Lambat untuk Prediksi Real-Time** – Kurang ideal untuk prediksi instan.
4. **Kurang Optimal untuk Data Waktu** – Tidak cocok untuk data berurutan atau time series.

### Logistic Regression:
#### Kelebihan Logistic Regression:
1. **Sederhana dan Mudah Diinterpretasi** – Modelnya sederhana dan mudah dipahami, sehingga memudahkan interpretasi hasil.
2. **Efisien untuk Dataset Kecil** – Logistic Regression bekerja baik dengan dataset yang lebih kecil dan memiliki fitur yang relevan.
3. **Cepat dan Ringan** – Proses training dan prediksi cepat, serta membutuhkan sumber daya komputasi yang lebih sedikit dibandingkan model kompleks.
4. **Probabilitas Output** – Menghasilkan nilai probabilitas, sehingga cocok untuk klasifikasi dengan pengukuran kepercayaan.

#### Kekurangan Logistic Regression:
1. **Tidak Efektif untuk Hubungan Non-Linear** – Logistic Regression hanya bisa menangani data yang memiliki hubungan linier; kurang efektif untuk hubungan non-linier.
2. **Rentan terhadap Outlier** – Outlier pada data dapat memengaruhi kinerja model, terutama tanpa normalisasi atau penanganan khusus.
3. **Tidak Ideal untuk Data yang Sangat Kompleks** – Kurang akurat pada data yang kompleks atau yang memiliki banyak fitur interaksi.
4. **Mengasumsikan Indepedensi Fitur** – Logistic Regression bekerja optimal jika fitur tidak saling bergantung, asumsi ini sering kali tidak realistis dalam data nyata.

### Decision Tree:
#### Kelebihan Decision Tree:
1. **Mudah Diinterpretasi** – Struktur pohon membuat model ini mudah dipahami, visualisasi langsung menunjukkan jalur keputusan.
2. **Menangani Data Non-Linear** – Decision Tree dapat menangani data yang memiliki hubungan non-linier, cocok untuk berbagai jenis data.
3. **Tidak Perlu Banyak Pra-pemrosesan** – Model ini tidak memerlukan normalisasi atau penskalaan fitur.
4. **Bisa Menangani Fitur Kategorikal dan Numerik** – Decision Tree fleksibel dalam menangani tipe data yang berbeda dalam satu model.

#### Kekurangan Decision Tree:
1. **Rentan terhadap Overfitting** – Decision Tree cenderung mempelajari data secara detail hingga berlebihan, terutama tanpa pemangkasan (*pruning*).
2. **Sensitif terhadap Variasi Data** – Sedikit perubahan pada data dapat menyebabkan perubahan besar dalam struktur pohon.
3. **Kurang Optimal pada Dataset Besar** – Pohon yang sangat dalam bisa menjadi lambat dan memori intensif pada dataset besar.
4. **Cenderung Bias pada Fitur yang Dominan** – Decision Tree cenderung lebih terfokus pada fitur yang memiliki banyak kategori atau nilai tinggi.

### Naive Bayes:
#### Kelebihan Naive Bayes:
1. **Cepat dan Efisien** – Naive Bayes memiliki waktu training yang cepat, bahkan pada dataset yang besar.
2. **Sederhana dan Mudah Diimplementasikan** – Model ini sangat mudah diimplementasikan dan interpretasinya sederhana.
3. **Performa Baik pada Data Kecil** – Naive Bayes bekerja baik pada dataset yang kecil dan terstruktur dengan baik.
4. **Bekerja Baik pada Data Kategorikal** – Sangat cocok untuk data kategorikal, seperti klasifikasi teks (misalnya, klasifikasi email sebagai spam atau bukan).

#### Kekurangan Naive Bayes:
1. **Mengasumsikan Indepedensi Fitur** – Asumsi bahwa setiap fitur bersifat independen tidak selalu realistis, terutama pada data nyata.
2. **Sensitif terhadap Data Tidak Relevan** – Naive Bayes bisa terpengaruh oleh fitur yang kurang relevan, sehingga perlu pemilihan fitur yang cermat.
3. **Rentan terhadap Data Tak Terlihat** – Kinerja bisa turun jika terdapat data atau kombinasi kategori yang belum pernah terlihat selama pelatihan.
4. **Tidak Cocok untuk Data dengan Interaksi Fitur yang Kuat** – Kurang efektif jika fitur memiliki korelasi tinggi, karena asumsi independensi tidak terpenuhi.

## Evaluation
### Confusion Matrix

Confusion Matrix adalah tabel yang digunakan untuk mengevaluasi kinerja model klasifikasi dengan menghitung jumlah prediksi yang benar dan salah dari setiap kelas. Tabel ini menunjukkan bagaimana model memprediksi setiap kelas dan membantu mengidentifikasi di mana kesalahan terjadi.

### Komponen Confusion Matrix

Confusion Matrix terdiri dari empat komponen utama:

1. **True Positive (TP)**: Prediksi yang benar di mana model memprediksi positif dan hasil sebenarnya juga positif.
2. **True Negative (TN)**: Prediksi yang benar di mana model memprediksi negatif dan hasil sebenarnya juga negatif.
3. **False Positive (FP)**: Prediksi salah di mana model memprediksi positif, tetapi hasil sebenarnya adalah negatif (*Type I Error*).
4. **False Negative (FN)**: Prediksi salah di mana model memprediksi negatif, tetapi hasil sebenarnya adalah positif (*Type II Error*).

### Struktur Confusion Matrix:

|                 | Prediksi Positif | Prediksi Negatif |
|-----------------|------------------|------------------|
| **Aktual Positif** | True Positive (TP)  | False Negative (FN) |
| **Aktual Negatif** | False Positive (FP) | True Negative (TN)  |

### Metrik dari Confusion Matrix

Confusion Matrix memungkinkan kita menghitung berbagai metrik evaluasi penting, antara lain:

- **Akurasi**: Proporsi prediksi yang benar dari seluruh prediksi. Akurasi = TP + TN / TP + TN + FP + FN

- **Presisi**: Proporsi prediksi positif yang benar dari seluruh prediksi positif. Presisi = TP / TP + FP

- **Recall (Sensitivitas)**: Proporsi kasus positif yang teridentifikasi dengan benar oleh model. Recall = TP / TP + FN
  
- **F1-Score**: Rata-rata harmonis dari presisi dan recall, mengukur keseimbangan antara keduanya. F1-Score = 2 (Presisi x Recall) / Presisi + Recall

### Kegunaan Confusion Matrix

Confusion Matrix sangat berguna untuk:

- Mengidentifikasi di mana kesalahan model terjadi, apakah lebih banyak FP atau FN.
- Mengevaluasi performa model, terutama pada data yang tidak seimbang.
- Memahami trade-off antara presisi dan recall, membantu dalam pemilihan model atau tuning parameter.

Dengan Confusion Matrix, kita bisa mendapatkan gambaran yang lebih mendalam tentang kinerja model, terutama dalam aplikasi di mana kesalahan positif atau negatif memiliki dampak yang signifikan, seperti dalam diagnosa medis atau deteksi penipuan.

## Referensi
[1] O. Tarawneh, M. Tarawneh, Y. Sharrab, and M. Husni, "Mushroom classification using machine-learning techniques," in AIP Conference Proceedings, vol. 2979, no. 1, Oct. 2023.

[2] Y. Wang, J. Du, H. Zhang, and X. Yang, "Mushroom toxicity recognition based on multigrained cascade forest," Scientific Programming, vol. 2020, no. 1, pp. 1-10, 2020.

[3] Kaggle Mushroom Classification Dataset Documentation, [Online]. Available: https://www.kaggle.com/uciml/mushroom-classification. Accessed: Nov. 3, 2024.

[4] H. Ujir, I. Hipiny, M. H. Bolhassan, K. N. Fazira Ku Azir, and S. A. Ali, "Automating Mushroom Culture Classification: A Machine Learning Approach," International Journal of Advanced Computer Science & Applications, vol. 15, no. 4, 2024.

[5] X. Guo, "Research on Mushroom Image Classification Algorithm Based on Deep Sparse Dictionary Learning," Academic Journal of Science and Technology, vol. 9, no. 1, pp. 235-240, 2024.

[6] R. Sahu, S. Pandey, R. Verma, and P. Pandey, "Ensemble Learning based Classification of Edible and Poisonous Agaricus Mushrooms," in 2024 Fourth International Conference on Advances in Electrical, Computing, Communication and Sustainable Technologies (ICAECT), Jan. 2024, pp. 1-7.

[7] L. Farokhah and S. Y. Riska, "Analysis and Development of Eight Deep Learning Architectures for the Classification of Mushrooms," Jurnal RESTI (Rekayasa Sistem dan Teknologi Informasi), vol. 8, no. 1, pp. 142-149, 2024.

