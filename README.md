# Laporan Proyek Machine Learning - Komang Wiweka Premana

## Project Overview
[Anime](http://www.bellaonline.com/articles/art4260.asp) (bahasa jepang :アニメ[Anime] ) adalah animasi dari Jepang yang digambar dengan tangan maupun menggunakan teknologi komputer. Kata anime merupakan singkatan dari "animation" dalam Bahasa Inggris, yang merujuk pada semua jenis animasi.Di luar Jepang, istilah ini digunakan secara spesifik untuk menyebutkan segala animasi yang diproduksi di Jepang.Meskipun demikian, tidak menutup kemungkinan bahwa anime dapat diproduksi di luar Jepang.Beberapa ahli berpendapat bahwa anime merupakan bentuk baru dari orientalisme.

Anime sudah menjadi ketertarikan tersendiri bagi pencinta animasi, dimana anime ini dapat dinikmati oleh semua kalangan umur. Banyak jenis anime yang cocok ditonton seperti anime tentang petualangan seperti One Piece, aksi seperti Naruto atau romantis seperti Kimi no Na Wa. Hal inilah yang membuat anime sangat pantas untuk  ditonton karena memenuhi semua kategori yang diinginkan sudah menjadi hal yang wajar bagi para pecinta animasi terutama animasi jepang. Untuk menonton anime saat ini, ada banyak sekali platform yang dapat kita manfaatkan untuk menonton serial anime. Mulai dari layanan tv, hingga layanan streaming anime online. Dengan demikian kita sangat mudah untuk mengakses sebuah anime dan karena hal tersebut anime juga menjadi makin populer dikalangan remaja hingga dewasa contohnya seperti di Indonesia. Karena banyak jenis anime banyak kalangan yang masih kebingungan dalam menentukan anime selanjutnya yang ingin ditonton, terlebih lagi jika orang tersebut hanya menyukai genre tertentu berdasarkan rating dari sebuah anime tersebut dan hal ini akan berbanding lurus dengan kurangnya informasi dari pencinta anime terhadap kriteria anime yang akan mereka tonton apakah sudah sesuai atau tidak. Dari kasus tersebut Maka diperlukannya Sistem Rekomendasi untuk menentukan rekomendasi anime yang cocok dengan pengguna tersebut. Dimana Sistem rekomendasi memprediksi rating atau preferensi pengguna terhadap item tertentu. Rekomendasi ini dibuat berdasarkan perilaku pengguna di masa lalu atau perilaku pengguna lainnya. Jadi, sistem ini akan merekomendasikan sesuatu terhadap pengguna berdasarkan data perilaku atau preferensi dari waktu ke waktu. 

![rmse](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/op2.jpg?raw=true?) 
## Business Understanding
### Problem Statement
Pada kasus dari permasalahan pada projek ini adalah beberapa anime yang memiliki episode per season (3 bulan) tentunya terasa kurang bagi pencinta anime sehingga mereka ingin mencari anime selanjutnya yang sesuai bagi mereka dan tentunya mereka akan ragu untuk memilih anime yang ingin ditonton musim ini atau anime yang sudah lewat. Oleh karena itu,  sistem rekomendasi hadir untuk memberikan rekomendasi anime yang tepat untuk user. Berdasarkan permasalah tersebut maka didapati problem statement sebagai berikut:
- Bagaimana sistem dapat merekomendasikan anime berdasarkan genre?
- Bagaimana sistem dapat merekomendasikan anime berdasarkan anime berdasarkan rating?

### Goal
Goal/tujuan dari Proyek ini adalah memberikan rekomendasi anime kepada pengguna berdasarkan data genre sekaligus memberikan rekomendasi anime kepada sebuah user bedasarkan hasil review/rating penonton lain terhadap anime.

### Solution Statment
Untuk mencapai tujuan dalam memberikan rekomendasi anime kepada user maka saya mengajukan 2 solusi approach (algoritma atau pendekatan sistem rekomendasi) dengan metode sebagai berikut:
- *Content-Based Filtering* berguna untuk memberikan sebuah rekomendasi anime berdasarkan genre sedangkan untuk modelnya akan menggunakan model *cosine similatiry*. Kelebihan *recommender system* dengan pendekatan content-based filtering adalah memiliki kemampuan untuk merekomendasikan item (contoh: film, lagu, artikel dll) yang sifatnya baru bagi user, karena prinsip kerjanya yaitu dengan melihat diskripsi konten yang dikandung oleh item yang pernah diberi nilai rating tinggi sebelumnya
- *Collaborative Filtering* berguna untuk memberikan sebuah rekomendasikan anime kepada pengguna berdasarkan penilaian dari seluruh pengguna/komunitas sedangkan untuk modelnya akan menggunakan *deep learning*. Kelebihan dari pendekantan user based collaborative filtering adalah dapat menghasilkan rekomendasi yang berkualitas baik. Metode ini merupakan metode rekomendasi yang didasari atas adanya kesamaan antara pemberian rating terhadap suatu item dengan item yang pernah dirating user lain

## Data Understanding
![banner](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/banner.jpeg?raw=true)
Pada kasus ini saya menggunakan dataset yang dapat dicari di [kaggle](https://www.kaggle.com/).Dalam membantu menyelesaikan kasus pada projek ini, saya mengambil dataset yang bernama [Anime Recommendations Database](https://www.kaggle.com/CooperUnion/anime-recommendations-database). Pada dataset yang ini terdapat 2 file csv diantaranya adalah **anime.csv** dan **rating.csv**. Pada masing-masing file tersebut terdapat beberapa variable atau kolom dengan rincian sebagai berikut:

**anime.csv**
* anime_id - sebuah unique id pada myanimelits.net untuk mengidentifikasi sebuah anime.
* name - judul pada sebuah anime.
* genre - daftar genre yang dipisahkan dengan koma.
* type - media streaming yang digunakan seperti movie, TV, OVA, etc.
* episodes - episode yang tersedia pada anime tertentu. (1 eps jika bertipe movie).
* rating - rata-rata rating yang diberikan.
* members - jumlah anggota komunitas yang ada di anime ini
"group".

**rating.csv**
* user_id - user id yang dibuat secara acak dan tidak terdefinisi.
* anime_id - anime yang telah di rating oleh pengguna.
* rating - rating yang diberikan pengguna dari 10 (-1 apabila user hanya menontonnya saja tetapi tidak memberikan rating pada anime tersebut).

Untuk melihat isi data pada masing-masing file maka kita dapat melakakukan loading data, setelah kita loading data maka didapatkan data sebagai berikut:
- anime.csv
 
    ![anime](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/animecsv.jpeg?raw=true)

- rating.csv
    Pada data rating dapat dilihat deskripsi statistiknya seperti berikut:
    ![rating](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/ratingcsv.jpeg?raw=true)
    ![ratingdesc](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/ratingdesc.jpeg?raw=true)
    
Dari dataset yang digunakan berikut merupakan karakteristik pada dataset tersebut:

![info](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/info.jpeg?raw=true)

Berdasarkan data diatas dapat dilihat bahwa pada data anime terdapat index sebanyak 12294 dan 7 kolom yang memiliki 1 tipe data float, 2 tipe data int dan 4 tipe data object. Pada data rating terdapat index sebanyak 7813737 dan 3 kolom yang memiliki 3 tipe data int. 

Langkah selanjutnya adalah mengecek data apakah terdapat data null atau tidak, variabel yang memiliki nilai null menandakan bahwa variabel tersebut tidak menunjuk pada object/nilai apapun. Dengan adanya data null dapat membuat suatu hasil prediksi model menjadi tidak akurat. Berikut cara untuk melihat dan mengatasi hal tersebut.

![null](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/isnull.jpeg?raw=true)

Dapat kita lihat pada kolom genres memiliki 62 data yang kosong, Rating memiliki 230 data yang kosong, dan type memiliki 25 data yang kosong, selain itu juga dapat melihat persentase dari data kosong tersebut. Sehingga, untuk mengatasi data null maka dilakukan pembersihan dengan menghapusnya menggunakan fungsi diatas.

Selanjutnya pada proses data understanding, saya telah melakukan visualisasi data terhadap tipe dari kolom 'type'(media streaming) dan genre yang paling sering terdapat/muncul dalam sebuah anime. dimana type media streaming yang dimaksud adalah jenis anime yang dikeluarkan apakah dia bertipe movie atau sebagainya. Berikut adalah visualisasi dari data media streaming seluruh anime pada animes.csv:

![type](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/type.jpeg?raw=true)

Pada diagram diatas dapat dilihat bahwa type media streaming yang paling banyak adalah type media streaming 'TV' dengan jumlah total 3668.

Selanjutnya untuk mengetahui jenis genre yang paling banyak terdapat dalam data tersebut maka saya menggunakan wordcloud untuk mengetahui lebih jelas mengenai jenis genre yang paling sering muncul pada data anime.  Berikut adalah visualisasi dari data genre anime pada animes.csv:

![genre](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/genre.png?raw=true)

Dari hasil wordcloud diatas dapat dilihat bahwa dari seluruh genre yang ada. genre Comedy merupakan jenis genre yang paling sering muncul pada data anime diikuti oleh genre Action dan advanture m yang paling banyak pada data anime dalam dataset.

Disamping itu juga saya melakukan visualisasikan data dalam bentuk tabel berdasarkan rating tertinggi berdasarkan tipe media streaming yang paling populer dan rating tertinggi dari media streaming seperti "movie",'TV' dan ''OVA'. Berikut merupakan visualisasi dari data tersebut.

**10 Anime dengan rating tertinggi**

![10best](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/animeTV.jpeg?raw=true)
Sebelumnya seperti yang kita dapat lihat pada gambar diatas dijelaskan bahwa seluruh anime dengan rating tertinggi dimiliki oleh anime dengan tipe media streaming 'TV' jadi saya tidak perlu memunculkan anime yang bertupe 'TV' lagi.

**10 Anime yang bertipe media streaming OVA dengan rating tertinggi**

![10bestOVA](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/animeOVA.jpeg?raw=true)

**10 Anime yang bertipe media streaming Movie dengan rating tertinggi**

![10bestMovie](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/animeMovie.jpeg?raw=true)

## Data Preparation 

Dalam data preparation, ada beberapa teknik yang saya gunakan untuk proses *preparation*. Selain itu, ada 2 dataset yang saya akan periksa yaitu rating.csv yang dinamakan sebagai df_rating, anime.csv yand dinamakan sebagai anime_data. Berikut penjelasan beberapa teknik yang akan digunakan untuk *data preparation*dan hasil dari teknik tersebut :

    
1. Melakukan text cleaning terhadap judul anime
    Text cleaning berfungsi untuk merubah karakter khusus pada judul anime karena masih terdapat judul anime yang menggunakan huruf jepang atau karakter khusus, maka dari itu dibuatkan fungsi untuk melakukan text cleaning. Berikut adalah fungsi dalam melakukan text cleaning.
    ![textclean](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/clean.jpeg?raw=true)

2. Menganailisi data rating sekaligus membuang rating yang tidak digunakan
   Karena pada masih banyak user yang sudah menonton anime tetapi tidak memberikan nilai/rating maka dibuat proses penghapusan rating dengan nilai = '-1' yang berarti pengguna tidak memberikan rating pada anime yang telah ditonton
    ![perbandingan](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/perbandingan-1.jpeg?raw=true)
    ![perbandingan](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/perbandingan-2.jpeg?raw=true)

    
3. Melakukan Label Encoder
    Label Encoder berfungsi untuk mengkonversi variabel target, label yang akan digunakan hanya pada user_id dan anime_id yang hasilnya akan digunakan untuk melakukan model deep learning. tahap ini sangat penting karena sistem dapat membuat model dengan menggunakan metode collaborative filtering.
    
    ![labelencoder](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/label.jpeg?raw=true)    

4. Melakukan Split Data
    Spliting data berfungsi untuk membagi string menjadi potongan-potongan tergantung pada pembatas yang bisa berupa apa saja mulai dari karakter atau angka atau bahkan teks 

Tahapan diatas wajib dilakukan karena proses ini akan mempengaruhi dalam pembuatan sistem rekomendasi dan model yang akan kita buat nanti.
## Modeling and Result

### Cosine Similatiry
Pada sistem rekomendasi yang berbasis *content-based-learning* saya melakukan modeling menggunakan *Cosine Simirality*. Cosine Similarity ‘ukuran kesamaan’, salah satu implementasinya adalah pada kasus mencari tingkat kemiripan teks pada teks itu sendiri atau sentence/kalimat . Kemiripan teks bisa kita gunakan untuk membuat steganografi ataupun steganalysis linguistik. Menghitung cosine similairity dari setiap dataset menggunakan fungsi cosine_similarity dari library Sklearn. Pada tahapan ini, menghitung cosine similarity pada dataset dengan fungsi 'genre_recommendations' untuk pemberian rekomendasi anime berdasarkan kesamaan genre. 
    
![cosinesimilatiry](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/cosine1.jpeg?raw=true)
![cosinesimilatiry](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/cosine2.jpeg?raw=true)
![cosinesimilatiry](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/cosine3.jpeg?raw=true)

Berikut merupakan hasil dari modelling tersebut: 
Mengecek informasi genre mengenai anime "One Punch Man"

![content-based](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/opm.jpeg?raw=true)  

Dari gambar di atas dapat dilihat detail dari anime favorit saya dengan judul "One Punch Man" yang memliki genre Action, Comedy, Parody, Sci-Fi, Seinen, Super Power. Berdasarkan genre yang terdapat pada anime 'One Punch Man' berikut merupakan 10 anime yang direkomendasikan berdasarkan genre dengan model cosine similatiry.

![content-based](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/opm2.jpeg?raw=true)    

Dari gambar diatas dapat disimpulkan bahwa terdapat 10 anime dengan kesamaan genre yang tinggi dengan anime "One Punch Man" dan seluruh anime yang direkomendasikan memiliki genre yang relevan dengan "One Punch man"

### Deep Learning
Pada sistem rekomendasi berbasis *collaborative filtering* dengan menggunakan model dalam melakukan modelling *deep learning*. Dimana model ini akan memberikan rekomendasi anime untuk seorang pengguna berdasarkan idnya. Disini saya melakukan Collaborative Filtering berdasarkan rating dari anime dari user, berikut tahapannya.
1. Menganalisis data rating.
2. Membuang rating yang tidak digunakan atau diperlukan.
3. Melakukan encoder terhadap 'user_id' dan 'anime_id'
4. Menghitung jumlah 'user_id' dan 'anime_id'
5. Melakukan modelling yang diawali dengan melakukan splitting terhadap data.
6. Membuat fungsi untuk model hingga evaluasi model
7. Membuat fungsi untuk melakukan prediksi terhadap anime yang akan direkomendasikan kepada pengguna.
8. Menentukan model terbaik dalam memberikan rekomendasi terhadap pengguna.

##### Model 1

![rmse](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/param.jpeg?raw=true) 
Dapat kita lihat diatas merupakan nilai paramater yang terdapat pada model menggunakan collaborative filtering dengan total params 7,952,700, trainable params: 7,952,700 dan non-trainable params 0. Pada model ini juga terdapat beberapa layer yang terdiri dari :
1. input_1 (InputLayer)
2. input_2(InputLayer)
3. embedding (embedding)
4. embedding_1 (embedding)
5. flatten (Flatten)
6. flatten_1 (Flatten)
7. dot (Dot)

Tahap ini melakukan sebuah prediksi terhdap rating pada anime 
![collaborative filtering 1](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/model1.jpeg?raw=true)    
Dari gambar diatas dapat dilihat bahwa hasil dari model diatas menghasilkan nilai rating_predict terhadap sebuah anime sebesar 10.166964


## Evaluation 

Dalam proses evaluasi ini akan dijelaskan mengenai informasi pada perbandingan model pertama dan kedua melalui dua metrik yakni *Mean Squared Error Loss* dan *Roor Mean Squared Loss* sebagai berikut:

### Loss (Mean Squared Error Loss)

Mean Squared Erorr Loss berfungsi untuk menghitung rata-rata kuadrat kesalahan antara label dan prediksi. Mean squared error dihitung sebagai rata-rata perbedaan kuadrat antara nilai yang diprediksi dan yang sebenarnya. Dengan demikian semakin rendahnya nilai loss (mean squared error loss) maka semakin baik dan akurat model yang dibuat. Berikut adalah hasil perbandingan loss dan val_loss pada model yang telah dibuat.

![Loss](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/loss.png?raw=true) 

### RMSE (Root Mean Squared Error)

RMSE adalah matrik yang berfungsi untuk menghitung kuadrat dari rata-rata selisih kuadrat antara nilai taksiran dan nilai sebenarnya dari variabel/fitur. Dengan demikian semakin rendahnya nilai RMSE makan semakin baik model tersebut dalam melakukan prediksi. Berikut rumus dari RMSE:

![rmse](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/RMSE.jpg?raw=true) 

Berikut adalah hasil perbandingan root_mean_squared_error dan val_root_mean_squared_error kedua model yang telah dibuat.

![rmse](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/rmsefix.png?raw=true) 

### Precision

 Precision adalah rasio prediksi data benar positif dibandingkan dengan keseluruhan hasil yang diprediksi positf. Precision juga menentukan tingkat ketepatan antara informasi yang diminta oleh pengguna dengan jawaban yang diberikan oleh sistem.  Berikut merukapan rumus dari Precision recomendation:

![precision](https://github.com/wiwekapremana/system-recommendation/blob/main/asset/presicion.jpeg?raw=true)
Sebelumnya karena tidak ada data target/label seperti pada supervised learning jadi kita tidak bisa menghitung dengan memanggil library scikit learn, jadi saya akan menghitung metrics evaluasinya secara manual. Maka hasil dari rekomendasi pada model cosine similarity terdapat 10/10 anime yang direkomendasikan yang memiliki genre yang relevan dengan "One Punch Man" maka metrik evaluasinya adalah 10/10 = 1. Jadi Precision dari model cosine similarity adalah 1.

Berdasarkan proses yang sudah dilakukan sebelumnya maka dapat disumpulkan bahwa dari pembuatan sistem rekomendasi anime dengan memanfaatkan *Content-Based Recommendation system* dan *Collaborative Filtering* maka didapatkan hasil yang sesuai seperti yang diharapkan sebelumnya, yaitu sistem dapat merekomendasikan judul anime berdasarkan genre yang relevan dan juga bedasarkan hasil review/rating penonton lain terhadap anime sekaligus dapat merekomendasikan anime terhadap sebuah user dengan prediksi yang cukup baik.
