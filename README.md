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

### Solution Statements
1. **Pengumpulan Data dan Pemrosesan Data**  
   Menggunakan dataset klasifikasi jamur dari Kaggle, dataset yang sudah tersedia ini berisi atribut-atribut fisik jamur. Langkah pertama adalah memastikan data bersih, mengatasi nilai yang hilang, dan menormalkan atribut.
   
2. **Pengembangan Model Pembelajaran Mesin**  
   Menggunakan metode pembelajaran mesin yang sesuai seperti algoritma klasifikasi untuk membangun model klasifikasi yang dapat memprediksi label "dapat dimakan" atau "beracun" berdasarkan atribut fisik.
   
3. **Evaluasi Model**  
   Mengevaluasi model menggunakan metrik seperti akurasi, presisi, dan recall untuk memastikan kinerja yang baik. 

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

### Eksplorasi Data Awal
Dataset yang digunakan berisi informasi tentang spesies jamur, termasuk label klasifikasi "edible" (dapat dimakan) atau "poisonous" (beracun) serta 22 atribut fisik lainnya. Tahap awal mencakup eksplorasi data untuk memahami distribusi atribut, identifikasi tipe data, dan analisis awal nilai-nilai yang ada pada setiap atribut.
- ```python
  df.shape
  ```
  Kode tersebut memiliki luaran:
  ```python
  (8124, 23)
  ```
- Jumlah entri (baris): 8.124
- Jumlah atribut (kolom): 23


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
Melihat Nama variabel pada dataset

- ```python
  df.isnull().sum()
  ```
  Kode tersebut memiliki luaran:
  
![isNull](https://github.com/user-attachments/assets/d4a3117d-6d0b-400f-942a-7ffd65d4c1fd)

Output tersebut menunjukkan bahwa tidak ada nilai yang hilang (null) dalam DataFrame, karena setiap kolom memiliki jumlah nilai kosong (atau nilai null) sama dengan 0. Artinya, data lengkap tersedia untuk semua kolom, dan tidak ada informasi yang hilang atau tidak tercatat di dalam dataset.

- ```python
  df.show()
  ```
  Kode tersebut memiliki luaran:

| class | cap-shape | cap-surface | cap-color | bruises | odor | gill-attachment | gill-spacing | gill-size | gill-color | stalk-shape | stalk-root | stalk-surface-above-ring | stalk-surface-below-ring | stalk-color-above-ring | stalk-color-below-ring | veil-type | veil-color | ring-number | ring-type | spore-print-color | population | habitat |
|-------|-----------|-------------|-----------|---------|------|-----------------|--------------|-----------|------------|-------------|------------|--------------------------|--------------------------|------------------------|------------------------|-----------|------------|-------------|-----------|-------------------|------------|---------|
| p     | x         | s           | n         | t       | p    | f               | c            | n         | k          | e           | e          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | k                 | s          | u       |
| e     | x         | s           | y         | t       | a    | f               | c            | b         | k          | e           | c          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | n                 | n          | g       |
| e     | b         | s           | w         | t       | l    | f               | c            | b         | n          | e           | c          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | n                 | n          | m       |
| p     | x         | y           | w         | t       | p    | f               | c            | n         | n          | e           | e          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | k                 | s          | u       |
| e     | x         | s           | g         | f       | n    | f               | w            | b         | k          | t           | e          | s                        | s                        | w                      | w                      | p         | w          | o           | e         | n                 | a          | g       |
| e     | x         | y           | y         | t       | a    | f               | c            | b         | n          | e           | c          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | k                 | n          | g       |
| e     | b         | s           | w         | t       | a    | f               | c            | b         | g          | e           | c          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | k                 | n          | m       |
| e     | b         | y           | w         | t       | l    | f               | c            | b         | n          | e           | c          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | n                 | s          | m       |
| p     | x         | y           | w         | t       | p    | f               | c            | n         | p          | e           | e          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | k                 | v          | g       |
| e     | b         | s           | y         | t       | a    | f               | c            | b         | g          | e           | c          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | k                 | s          | m       |
| e     | x         | y           | y         | t       | l    | f               | c            | b         | g          | e           | c          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | n                 | n          | g       |
| e     | x         | y           | y         | t       | a    | f               | c            | b         | n          | e           | c          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | k                 | s          | m       |
| e     | b         | s           | y         | t       | a    | f               | c            | b         | w          | e           | c          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | n                 | s          | g       |
| p     | x         | y           | w         | t       | p    | f               | c            | n         | k          | e           | e          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | n                 | v          | u       |
| e     | x         | f           | n         | f       | n    | f               | w            | b         | n          | t           | e          | s                        | f                        | w                      | w                      | p         | w          | o           | e         | k                 | a          | g       |
| e     | s         | f           | g         | f       | n    | f               | c            | n         | k          | e           | e          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | n                 | y          | u       |
| e     | f         | f           | w         | f       | n    | f               | w            | b         | k          | t           | e          | s                        | s                        | w                      | w                      | p         | w          | o           | e         | n                 | a          | g       |
| p     | x         | s           | n         | t       | p    | f               | c            | n         | n          | e           | e          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | k                 | s          | g       |
| p     | x         | y           | w         | t       | p    | f               | c            | n         | n          | e           | e          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | n                 | s          | u       |
| p     | x         | s           | n         | t       | p    | f               | c            | n         | k          | e           | e          | s                        | s                        | w                      | w                      | p         | w          | o           | p         | n                 | s          | u       |

only showing top 20 rows

- ```python
   total_records = df.count()
   print(f"Total number of records: {total_records}")
   class_distribution = df.groupBy('class').count()
   print("Class distribution:")
   class_distribution.show()
  ```
  Kode tersebut memiliki luaran:
  ```python
  Total number of records: 8124
  Class distribution:
   | class | count |
   |-------|-------|
   | e     | 4208  |
   | p     | 3916  |

  ```

Output tersebut menunjukkan bahwa DataFrame memiliki total 8124 catatan, yang terbagi menjadi dua kelas: "e" (dengan 4208 catatan) dan "p" (dengan 3916 catatan). Ini mengindikasikan bahwa dataset memiliki distribusi kelas yang hampir seimbang, dengan sedikit lebih banyak catatan untuk kelas "e" dibandingkan dengan kelas "p".

### Cek Missing Value 
Salah satu tantangan utama dalam dataset ini adalah adanya atribut dengan nilai yang hilang, oleh karena itu perlu diadakan pengecekan data hilang.

- ```python
    for colname in df.columns:
    null_count = df.filter(col(colname).isNull()).count()
    print(f" {colname}: {null_count}")
  ```
  Kode tersebut memiliki luaran:
  ```python
    class: 0
    cap-shape: 0
    cap-surface: 0
    cap-color: 0
    bruises: 0
    odor: 0
    gill-attachment: 0
    gill-spacing: 0
    gill-size: 0
    gill-color: 0
    stalk-shape: 0
    stalk-root: 0
    stalk-surface-above-ring: 0
    stalk-surface-below-ring: 0
    stalk-color-above-ring: 0
    stalk-color-below-ring: 0
    veil-type: 0
    veil-color: 0
    ring-number: 0
    ring-type: 0
    spore-print-color: 0
    population: 0
    habitat: 0
  ```

Output tersebut menunjukkan bahwa tidak ada nilai yang hilang dalam dataset untuk setiap kolom, karena semua kolom memiliki jumlah nilai kosong (null) sama dengan 0. Ini berarti dataset sepenuhnya lengkap dan tidak memerlukan proses imputasi atau penanganan data hilang sebelum analisis lebih lanjut.

### Analisis Korelasi
Analisis Korelasi adalah metode statistik yang digunakan untuk mengukur dan mengevaluasi hubungan antara dua variabel atau lebih. Tujuan utama dari analisis ini adalah untuk menentukan seberapa kuat hubungan tersebut dan apakah hubungan tersebut bersifat positif, negatif, atau netral.
- ```python
	#Menampilkan heatmap menggunakan Seaborn dan Matplotlib
	plt.figure(figsize=(12, 8))
	sns.heatmap(correlation_df, annot=True, cmap="coolwarm", fmt=".2f", linewidths=.5)
	plt.title("Correlation Matrix Heatmap (Numeric Columns Only)")
	plt.show()
  ```
  Kode tersebut memiliki luaran:
  ![CorrelationAnalysis](https://github.com/user-attachments/assets/006b7361-5a54-4953-8541-e80b90179eef)

Gambar tersebut menunjukkan heatmap dari matriks korelasi yang merepresentasikan hubungan antara kolom-kolom numerik dalam dataset. Warna dalam heatmap berkisar dari -1 (biru tua) hingga +1 (merah tua), di mana angka yang lebih tinggi atau lebih dekat dengan +1 menunjukkan korelasi positif yang kuat, angka yang lebih rendah atau mendekati -1 menunjukkan korelasi negatif yang kuat, dan angka mendekati 0 menunjukkan korelasi yang lemah atau tidak ada korelasi. Diagonal utama semuanya merah tua dengan nilai +1 karena setiap variabel memiliki korelasi sempurna dengan dirinya sendiri. Ada beberapa korelasi signifikan yang dapat diamati, seperti hubungan kuat antara "ring-type_index" dan "ring-number_index," yang menunjukkan bahwa ada pola atau ketergantungan di antara atribut-atribut ini.

## Data Preparation
Tahap Data Preparation bertujuan untuk memastikan bahwa data yang digunakan dalam pembuatan model klasifikasi memiliki kualitas yang baik dan siap untuk diolah. Data yang bersih, bebas dari inkonsistensi, dan disiapkan dengan baik merupakan prasyarat penting untuk mendapatkan hasil analisis yang akurat dan model pembelajaran mesin yang optimal. Berikut adalah langkah-langkah yang dilakukan dalam proses persiapan data pada proyek klasifikasi jamur ini:

### Transformasi dan Encoding Data Kategorikal
Sebagian besar atribut dalam dataset adalah kategori, dengan nilai-nilai berbentuk simbol atau huruf. Agar data ini dapat digunakan dalam model pembelajaran mesin, diperlukan proses encoding untuk mengubah data kategorikal menjadi bentuk numerik. 

- ```python
	string_columns = [col_name for col_name, col_type in df.dtypes if col_type == 'string']
	indexers = [StringIndexer(inputCol=col_name, outputCol=col_name+"_index", handleInvalid="skip").fit(df) for col_name in string_columns]
	pipeline = Pipeline(stages=indexers)
	df_encoded = pipeline.fit(df).transform(df)
	df_encoded.select([col_name+"_index" for col_name in string_columns]).show()
  ```
  Kode tersebut memiliki luaran:
  
  | class_index | cap-shape_index | cap-surface_index | cap-color_index | bruises_index | odor_index | gill-attachment_index | gill-spacing_index | gill-size_index | gill-color_index | stalk-shape_index | stalk-root_index | stalk-surface-above-ring_index | stalk-surface-below-ring_index | stalk-color-above-ring_index | stalk-color-below-ring_index | veil-type_index | veil-color_index | ring-number_index | ring-type_index | spore-print-color_index | population_index | habitat_index |
   |-------------|-----------------|-------------------|-----------------|---------------|------------|-----------------------|--------------------|-----------------|------------------|-------------------|------------------|------------------------------|------------------------------|----------------------------|----------------------------|-----------------|------------------|-------------------|-----------------|-------------------------|------------------|---------------|
   | 1.0         | 0.0             | 1.0               | 0.0             | 1.0           | 6.0        | 0.0                   | 0.0                | 1.0             | 7.0              | 1.0               | 2.0              | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0             | 2.0                     | 2.0              | 4.0           |
   | 0.0         | 0.0             | 1.0               | 3.0             | 1.0           | 4.0        | 0.0                   | 0.0                | 0.0             | 7.0              | 1.0               | 3.0              | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0             | 1.0                     | 3.0              | 1.0           |
   | 0.0         | 3.0             | 1.0               | 4.0             | 1.0           | 5.0        | 0.0                   | 0.0                | 0.0             | 3.0              | 1.0               | 3.0              | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0             | 1.0                     | 3.0              | 5.0           |
   | 1.0         | 0.0             | 0.0               | 4.0             | 1.0           | 6.0        | 0.0                   | 0.0                | 1.0             | 3.0              | 1.0               | 2.0              | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0             | 2.0                     | 2.0              | 4.0           |
   | 0.0         | 0.0             | 1.0               | 1.0             | 0.0           | 0.0        | 0.0                   | 1.0                | 0.0             | 7.0              | 0.0               | 2.0              | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 1.0             | 1.0                     | 4.0              | 1.0           |
   | 0.0         | 0.0             | 0.0               | 3.0             | 1.0           | 4.0        | 0.0                   | 0.0                | 0.0             | 3.0              | 1.0               | 3.0              | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0             | 2.0                     | 3.0              | 1.0           |
   | 0.0         | 3.0             | 1.0               | 4.0             | 1.0           | 4.0        | 0.0                   | 0.0                | 0.0             | 4.0              | 1.0               | 3.0              | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0             | 2.0                     | 3.0              | 5.0           |
   | 0.0         | 3.0             | 0.0               | 4.0             | 1.0           | 5.0        | 0.0                   | 0.0                | 0.0             | 3.0              | 1.0               | 3.0              | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0             | 1.0                     | 2.0              | 5.0           |
   | 1.0         | 0.0             | 0.0               | 4.0             | 1.0           | 6.0        | 0.0                   | 0.0                | 1.0             | 1.0              | 1.0               | 2.0              | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0             | 2.0                     | 0.0              | 1.0           |
   | 0.0         | 3.0             | 1.0               | 3.0             | 1.0           | 4.0        | 0.0                   | 0.0                | 0.0             | 4.0              | 1.0               | 3.0              | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0             | 2.0                     | 2.0              | 5.0           |

only showing top 20 rows

Output tersebut menunjukkan bahwa data awal telah dikodekan atau diubah menjadi indeks numerik, di mana setiap kolom atribut, seperti "class," "cap-shape," dan "odor," kini direpresentasikan dengan nilai numerik (misalnya, 0.0, 1.0, dll.) untuk memfasilitasi analisis dan pemrosesan lebih lanjut, seperti pelatihan model machine learning. Setiap nilai indeks tersebut mengacu pada kategori unik dari atribut yang sesuai, dan hanya 20 baris pertama dari data yang dikodekan yang ditampilkan sebagai sampel.

- ```python
	numeric_features = [t[0] for t in df.dtypes if t[1] in ['int','double']]
	numeric_summary = df.select(numeric_features).summary()
	numeric_summary.show(truncate=False)
  ```
  Kode tersebut memiliki luaran:

| summary | class_index | cap-shape_index | cap-surface_index | cap-color_index | bruises_index | odor_index | gill-attachment_index | gill-spacing_index | gill-size_index | gill-color_index | stalk-shape_index | stalk-root_index | stalk-surface-above-ring_index | stalk-surface-below-ring_index | stalk-color-above-ring_index | stalk-color-below-ring_index | veil-type_index | veil-color_index | ring-number_index | ring-type_index | spore-print-color_index | population_index | habitat_index |
|---------|-------------|-----------------|-------------------|-----------------|---------------|------------|-----------------------|--------------------|-----------------|------------------|-------------------|------------------|------------------------------|------------------------------|----------------------------|----------------------------|-----------------|------------------|-------------------|------------------|-------------------------|------------------|---------------|
| count  | 8124        | 8124            | 8124              | 8124            | 8124          | 8124       | 8124                  | 8124               | 8124            | 8124             | 8124              | 8124             | 8124                         | 8124                         | 8124                       | 8124                       | 8124            | 8124             | 8124              | 8124             | 8124                    | 8124             | 8124          |
| mean   | 0.482       | 0.777           | 0.887             | 1.785            | 0.416          | 1.453       | 0.026                 | 0.161              | 0.309           | 2.703            | 0.433             | 0.881             | 0.437                        | 0.536                        | 0.978                      | 1.018                      | 0.0             | 0.038            | 0.083             | 0.696            | 1.495                   | 1.064             | 1.356          |
| stddev | 0.500       | 0.876           | 0.821             | 1.650            | 0.493          | 1.916       | 0.159                 | 0.368              | 0.462           | 2.401            | 0.495             | 1.037             | 0.632                        | 0.779                        | 1.483                      | 1.523                      | 0.0             | 0.258            | 0.291             | 0.787            | 1.381                   | 1.392             | 1.544          |
| min    | 0.0         | 0.0             | 0.0               | 0.0              | 0.0            | 0.0         | 0.0                   | 0.0                | 0.0             | 0.0               | 0.0               | 0.0               | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0              | 0.0                     | 0.0              | 0.0           |
| 25%    | 0.0         | 0.0             | 0.0               | 0.0              | 0.0            | 0.0         | 0.0                   | 0.0                | 0.0             | 1.0               | 0.0               | 0.0               | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 0.0              | 0.0                     | 0.0              | 0.0           |
| 50%    | 0.0         | 1.0             | 1.0               | 1.0              | 0.0            | 1.0         | 0.0                   | 0.0                | 0.0             | 2.0               | 0.0               | 1.0               | 0.0                          | 0.0                          | 0.0                        | 0.0                        | 0.0             | 0.0              | 0.0               | 1.0              | 1.0                     | 1.0              | 1.0           |
| 75%    | 1.0         | 1.0             | 2.0               | 3.0              | 1.0            | 2.0         | 0.0                   | 0.0                | 1.0             | 4.0               | 1.0               | 1.0               | 1.0                          | 1.0                          | 1.0                        | 1.0                        | 0.0             | 0.0              | 0.0               | 1.0              | 2.0                     | 2.0              | 2.0           |
| max    | 1.0         | 5.0             | 3.0               | 9.0              | 1.0            | 8.0         | 1.0                   | 1.0                | 1.0             | 11.0              | 1.0               | 4.0               | 3.0                          | 3.0                          | 8.0                        | 8.0                        | 0.0             | 3.0              | 2.0               | 4.0              | 8.0                     | 5.0              | 6.0           |


Output tersebut memberikan ringkasan statistik dari kolom-kolom terkode dalam dataset, termasuk jumlah data (count), rata-rata (mean), standar deviasi (stddev), nilai minimum (min), kuartil pertama (25%), median (50%), kuartil ketiga (75%), dan nilai maksimum (max) untuk setiap kolom yang bertipe data numerik. Ini membantu memahami distribusi dan rentang nilai dari atribut terkode, yang mencakup informasi seperti "class_index" hingga "habitat_index," di mana nilai-nilai ini mewakili kategori yang telah diubah menjadi bentuk numerik untuk keperluan analisis dan model machine learning.

### Pemeriksaan Ketidakseimbangan Kelas
Mengingat bahwa target prediksi adalah label klasifikasi jamur (dapat dimakan atau beracun), penting untuk memeriksa keseimbangan distribusi kelas target. Ketidakseimbangan kelas yang signifikan dapat mempengaruhi performa model. Jika ditemukan, langkah-langkah penanganan seperti:
- **Synthetic Minority Oversampling Technique (SMOTE)**
- ```python
	class_counts_after = df_resampled.groupBy("class_index").count()
	print("Class counts after SMOTE:")
	class_counts_after.show()
  ```
  Kode tersebut memiliki luaran:

**Class counts after SMOTE:**
| class_index | count |
|-------------|-------|
| 0.0         | 4208  |
| 1.0         | 4208  |

Output tersebut menunjukkan hasil dari proses oversampling menggunakan SMOTE (Synthetic Minority Over-sampling Technique), di mana jumlah data untuk kedua kelas dalam kolom "class_index" kini seimbang, masing-masing memiliki 4208 catatan. Sebelumnya, kelas yang kurang terwakili telah ditingkatkan jumlahnya untuk mengatasi ketidakseimbangan kelas, sehingga dataset menjadi lebih seimbang dan dapat meningkatkan kinerja model machine learning dalam memprediksi kedua kelas secara adil.

### Fitur Selection (Pearson Correlation)
- ```python
	# Menentukan ambang korelasi yang dianggap relevan
	threshold = 0.1
	# Memfilter fitur-fitur yang memiliki korelasi lebih besar dari ambang dengan class_index
	relevant_features = [col_name for col_name in correlation_df.index
                     if abs(correlation_df.loc[col_name, 'class_index']) > threshold
                     and col_name != "class_index"]

	# Menampilkan 5 fitur teratas yang dianggap relevan
	print("5 Fitur Teratas yang Dianggap Relevan terhadap class_index:")
	for feature in relevant_features[:5]:
   	 print(feature)
  	```
  Kode tersebut memiliki luaran:
  ```python
 	5 Fitur Teratas yang Dianggap Relevan terhadap class_index:
	cap-surface_index
	bruises_index
	odor_index
	gill-attachment_index
	gill-spacing_index
  ```
Output tersebut menunjukkan lima fitur teratas yang paling relevan terhadap "class_index," yaitu "cap-surface_index," "bruises_index," "odor_index," "gill-attachment_index," dan "gill-spacing_index." Ini berarti bahwa fitur-fitur ini memiliki hubungan yang lebih signifikan dengan variabel target "class_index" dibandingkan dengan fitur lainnya, yang dapat mempengaruhi prediksi atau klasifikasi dalam model machine learning. Relevansi ini dapat diukur melalui korelasi atau metode pemilihan fitur lainnya, dan fitur-fitur yang dipilih diharapkan memberikan kontribusi besar dalam meningkatkan kinerja model.

### Pemisahan Data
Data yang sudah bersih dan siap digunakan kemudian dibagi menjadi data latih (training set) dan data uji (testing set). Pembagian ini dilakukan untuk memastikan bahwa model dapat dievaluasi secara objektif, dengan mengukur kinerjanya pada data yang belum pernah dilihat sebelumnya.
- ```python
	# Membagi data menjadi train (50%), test (25%), dan validation (25%)
	train, temp = df_split.randomSplit([0.5, 0.5], seed=42)
	test, validation = temp.randomSplit([0.5, 0.5], seed=42)
	print("Training Dataset Count: " + str(train.count()))
	print("Test Dataset Count: " + str(test.count()))
	print("Validation Dataset Count: " + str(validation.count()))
  ```
  Kode tersebut memiliki luaran:
  ```python
 	Training Dataset Count: 4115
	Test Dataset Count: 2044
	Validation Dataset Count: 1965
  ```
Output tersebut menunjukkan bahwa dataset telah dibagi menjadi tiga subset: training, test, dan validation, menggunakan metode randomSplit dengan rasio 50:50 untuk pembagian awal, diikuti oleh pembagian 50:50 dari subset sementara untuk menghasilkan set test dan validation. Hasilnya, dataset training memiliki 4115 catatan, dataset test memiliki 2044 catatan, dan dataset validation memiliki 1965 catatan. Pembagian ini dilakukan untuk melatih model pada data training, menguji kinerjanya pada data test, dan memvalidasi atau menyetel model lebih lanjut menggunakan data validation.

## Modeling

- ```python
	# Inisialisasi model
	rf = RandomForestClassifier(featuresCol='features', labelCol='class_index')
	lr = LogisticRegression(featuresCol='features', labelCol='class_index')
	dt = DecisionTreeClassifier(featuresCol='features', labelCol='class_index')
	nb = NaiveBayes(featuresCol='features', labelCol='class_index')
	
	# Fit model pada data latih
	rf_model = rf.fit(train)
	lr_model = lr.fit(train)
	dt_model = dt.fit(train)
	nb_model = nb.fit(train)
	
	# Transformasi data uji dan validasi dengan model yang sudah dilatih
	rf_test_predictions = rf_model.transform(test)
	lr_test_predictions = lr_model.transform(test)
	dt_test_predictions = dt_model.transform(test)
	nb_test_predictions = nb_model.transform(test)
	
	rf_validation_predictions = rf_model.transform(validation)
	lr_validation_predictions = lr_model.transform(validation)
	dt_validation_predictions = dt_model.transform(validation)
	nb_validation_predictions = nb_model.transform(validation)
  ```
Kode tersebut menginisialisasi empat model klasifikasi dari pustaka PySpark ML, yaitu RandomForestClassifier, LogisticRegression, DecisionTreeClassifier, dan NaiveBayes. 
Keempat model yang digunakan dalam proyek ini memiliki cara kerja yang berbeda. Semua model yang digunakan di sini menggunakan nilai parameter default yang telah ditentukan oleh pustaka yang digunakan yaitu pustaka PySpark ML.

### Random Forest:
Random Forest adalah algoritma ensemble yang menggabungkan banyak pohon keputusan untuk meningkatkan ketepatan prediksi dan mengurangi overfitting. Setiap pohon dalam hutan dibangun menggunakan subset acak dari data pelatihan dan subset acak dari fitur, sehingga meningkatkan variasi antar pohon dan membuat model lebih robust. Dengan parameter default seperti `n_estimators=100` dan `criterion='gini'`, Random Forest sangat efektif dalam menangani data besar dengan fitur yang banyak, serta memberikan hasil yang stabil meski sering kali lebih lambat dalam pelatihan dibandingkan model pohon tunggal.

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
Logistic Regression adalah algoritma klasifikasi yang digunakan untuk memodelkan probabilitas suatu kelas berdasarkan kombinasi linier dari fitur yang ada. Meskipun bernama "regresi", model ini lebih sering digunakan untuk klasifikasi, dengan menggunakan fungsi sigmoid untuk mengubah log-odds menjadi probabilitas antara 0 dan 1. Dengan parameter default seperti `solver='lbfgs'` dan `max_iter=100`, Logistic Regression efisien dalam menangani masalah klasifikasi biner dan dapat diperbaiki dengan regularisasi untuk meningkatkan performa pada data yang kompleks.

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
Decision Tree adalah algoritma klasifikasi yang membangun pohon keputusan dengan membagi data berdasarkan fitur-fitur yang paling informatif, diukur dengan kriteria seperti Gini Impurity atau Entropy. Proses ini berlanjut hingga data tidak dapat dibagi lebih lanjut atau mencapai kriteria berhenti yang ditentukan. Dengan menggunakan parameter default seperti `criterion='gini'`, `max_depth=None`, dan `min_samples_split=2`, Decision Tree mampu menangani data yang kompleks, meskipun cenderung mudah overfitting jika tidak diatur dengan baik.

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
Naive Bayes adalah model klasifikasi berbasis probabilistik yang mengasumsikan independensi antar fitur untuk menghitung probabilitas suatu kelas berdasarkan data yang ada. Menggunakan Teorema Bayes, model ini menghitung probabilitas kelas yang diberikan fitur dan memilih kelas dengan probabilitas tertinggi. Meskipun seringkali tidak realistis untuk mengasumsikan bahwa fitur-fitur saling independen, Naive Bayes sering kali memberikan hasil yang sangat baik, terutama pada masalah klasifikasi teks, dengan nilai parameter default seperti `var_smoothing=1e-9` untuk mencegah pembagian dengan nol.

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

### Hasil Confusion Matrix

- Confusion Matrix Random Forest
  
![Confusion Matrix Random Forest](https://github.com/user-attachments/assets/4887a649-59b6-4080-81e1-0229f1665152)


- Confusion Matrix Logistic Regression
  
![Confusion Matrix Logistic Regression](https://github.com/user-attachments/assets/a524b311-af1b-4a49-8407-d62f2894012d)

  
- Confusion Matrix Decision Tree
  
![Confusion Matrix Decision Tree](https://github.com/user-attachments/assets/f50d58bb-19cb-487d-b326-ce415c09e928)

  
- Confusion Matrix Naive Bayes
  
![Confusion Matrix Naive Bayes](https://github.com/user-attachments/assets/038cda72-d1cd-485b-8427-1fdf662f193c)


### Kesimpulan
- ```python
	print_metrics('Random Forest', rf_val_metrics, 'Validation')
	print_metrics('Logistic Regression', lr_val_metrics, 'Validation')
	print_metrics('Decision Tree', dt_val_metrics, 'Validation')
	print_metrics('Naive Bayes', nb_val_metrics, 'Validation')
	print_metrics('Random Forest', rf_test_metrics, 'Test')
	print_metrics('Logistic Regression', lr_test_metrics, 'Test')
	print_metrics('Decision Tree', dt_test_metrics, 'Test')
	print_metrics('Naive Bayes', nb_test_metrics, 'Test')
  ```
  Kode tersebut memiliki luaran:
    ```python
  	Random Forest (Test)
	Accuracy: 98.87%
	Precision: 98.90%
	Recall: 98.87%
	F1-Score: 98.87%
	
	Logistic Regression (Test)
	Accuracy: 84.49%
	Precision: 84.92%
	Recall: 84.49%
	F1-Score: 84.47%
	
	Decision Tree (Test)
	Accuracy: 98.24%
	Precision: 98.24%
	Recall: 98.24%
	F1-Score: 98.24%
	
	Naive Bayes (Test)
	Accuracy: 75.54%
	Precision: 75.59%
	Recall: 75.54%
	F1-Score: 75.49%
  ```

Berdasarkan hasil evaluasi model yang diterapkan pada dataset ini, Random Forest menunjukkan kinerja terbaik dengan akurasi, presisi, recall, dan F1-Score masing-masing mencapai 98.87%. Angka ini menunjukkan bahwa model Random Forest dapat dengan sangat baik mengklasifikasikan data, dengan kesalahan klasifikasi yang sangat minimal.

Model Decision Tree juga menunjukkan kinerja yang sangat baik, dengan hasil yang hampir serupa dengan Random Forest, yaitu akurasi, presisi, recall, dan F1-Score masing-masing mencapai 98.24%. Meskipun sedikit lebih rendah dibandingkan Random Forest, Decision Tree tetap memberikan performa yang sangat baik dalam klasifikasi data.

Di sisi lain, Logistic Regression memiliki hasil yang cukup baik dengan akurasi 84.49%, presisi 84.92%, recall 84.49%, dan F1-Score 84.47%. Meskipun lebih rendah dibandingkan Random Forest dan Decision Tree, Logistic Regression masih menunjukkan performa yang solid, namun kurang optimal dibandingkan dengan model lainnya.

Terakhir, Naive Bayes menunjukkan hasil yang lebih rendah dengan akurasi 75.54%, presisi 75.59%, recall 75.54%, dan F1-Score 75.49%. Hasil ini mengindikasikan bahwa model Naive Bayes kurang efektif dibandingkan dengan model lainnya dalam hal klasifikasi data pada dataset ini.

Secara keseluruhan, Random Forest dan Decision Tree adalah model yang lebih unggul dalam mengklasifikasikan data, sedangkan Logistic Regression dan Naive Bayes memiliki performa yang lebih rendah. Oleh karena itu, untuk aplikasi yang membutuhkan akurasi dan performa tinggi, Random Forest atau Decision Tree akan menjadi pilihan yang lebih baik.

Dalam laporan ini, kita mengevaluasi dampak dari model klasifikasi jamur yang dikembangkan terhadap Business Understanding yang telah diidentifikasi. Tujuan dari model ini adalah untuk mengatasi tantangan kritis dalam mengklasifikasikan jamur sebagai "dapat dimakan" atau "beracun," mengingat bahwa kesalahan dalam identifikasi dapat berdampak fatal bagi kesehatan manusia. Model ini dirancang untuk menjawab problem statement yang sangat spesifik: memberikan sistem klasifikasi yang akurat dan efisien berdasarkan karakteristik fisik jamur, yang sering menjadi dasar dalam identifikasi manual yang memakan waktu dan memerlukan keahlian tinggi.

Evaluasi menunjukkan bahwa model yang dikembangkan, khususnya algoritma seperti Random Forest dan Decision Tree, berhasil mencapai tingkat akurasi yang tinggi (lebih dari 98%) dalam mengklasifikasikan jamur. Ini menunjukkan bahwa model sudah cukup menjawab problem statement dengan memberikan solusi yang meminimalkan risiko kesalahan identifikasi. Dengan tingkat akurasi yang tinggi, model ini juga berhasil mencapai tujuan untuk meningkatkan keamanan publik. Pengguna umum, seperti kolektor jamur, dapat lebih percaya diri dalam membedakan jamur beracun dari yang dapat dimakan, yang berpotensi mengurangi insiden keracunan.

Dampak dari solution statement yang direncanakan juga cukup signifikan. Melalui pemrosesan data yang teliti dan pengembangan model yang dioptimalkan, model ini mampu memberikan prediksi yang akurat dengan memanfaatkan atribut fisik yang sudah tersedia dalam dataset. Implementasi alat identifikasi berbasis model ini akan sangat berguna, karena tidak hanya mengotomatisasi proses klasifikasi yang kompleks tetapi juga memberikan kemudahan akses bagi masyarakat umum tanpa memerlukan keahlian khusus. Dengan demikian, solusi ini memiliki dampak positif yang nyata dalam meningkatkan keselamatan dan efisiensi identifikasi jamur.

## Referensi
[1] O. Tarawneh, M. Tarawneh, Y. Sharrab, and M. Husni, "Mushroom classification using machine-learning techniques," in AIP Conference Proceedings, vol. 2979, no. 1, Oct. 2023.

[2] Y. Wang, J. Du, H. Zhang, and X. Yang, "Mushroom toxicity recognition based on multigrained cascade forest," Scientific Programming, vol. 2020, no. 1, pp. 1-10, 2020.

[3] Kaggle Mushroom Classification Dataset Documentation, [Online]. Available: https://www.kaggle.com/uciml/mushroom-classification. Accessed: Nov. 3, 2024.

[4] H. Ujir, I. Hipiny, M. H. Bolhassan, K. N. Fazira Ku Azir, and S. A. Ali, "Automating Mushroom Culture Classification: A Machine Learning Approach," International Journal of Advanced Computer Science & Applications, vol. 15, no. 4, 2024.

[5] X. Guo, "Research on Mushroom Image Classification Algorithm Based on Deep Sparse Dictionary Learning," Academic Journal of Science and Technology, vol. 9, no. 1, pp. 235-240, 2024.

[6] R. Sahu, S. Pandey, R. Verma, and P. Pandey, "Ensemble Learning based Classification of Edible and Poisonous Agaricus Mushrooms," in 2024 Fourth International Conference on Advances in Electrical, Computing, Communication and Sustainable Technologies (ICAECT), Jan. 2024, pp. 1-7.

[7] L. Farokhah and S. Y. Riska, "Analysis and Development of Eight Deep Learning Architectures for the Classification of Mushrooms," Jurnal RESTI (Rekayasa Sistem dan Teknologi Informasi), vol. 8, no. 1, pp. 142-149, 2024.

