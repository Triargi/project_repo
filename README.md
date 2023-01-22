# Final Project: Marketing Campaign

Kelompok 9 Halcyon <br>
Rakamin Academy Data Science Bootcamp Batch 28: <br>
1. Aditya Ridwan
2. Ann Sinaga
3. Irvandri Lawinata
4. Jesslyn Jane
5. Lhutfia Ichsan
6. M. Triargi
7. Mustiadi Zakki

Datataset dapat diakses pada [Marketing Campaign Dataset](https://www.kaggle.com/datasets/rodsaldanha/arketing-campaign)

## 1. Problem Statement
Sebuah perusahaan diketahui memiliki tingkat acceptance marketing campaign sekitar 14.91%, yang mana hal tersebut masih dianggap kurang oleh manajemen dalam menghadapi persaingan bisnis. 

Sehingga pihak manajemen meminta tim marketing untuk meningkatkan lagi tingkat acceptance marketing campaign tersebut agar cost yang dikeluarkan perusahaan dalam melakukan marketing campaign lebih efisien dan jumlah revenue yang mereka raih pada tahun-tahun berikutnya meningkat.

Maka dari itu, tim marketing berencana menerapkan strategi Targeted Marketing dengan bantuan tim data science untuk mengolah data historis penjualan yang telah mereka rekap sebelumnya dan mengelompokkan user ke dalam sebuah kategori tertentu sesuai dengan karakteristiknya masing-masing, sehingga dapat dipilah antara yang layak mendapatkan campaign dengan yang tidak mendapatkan campaign.


## 2. Objective, Business Metrics dan Goal
Objective:
Membuat sistem prediksi model klasifikasi/clustering yang dapat menentukan targeting user yang tepat. Dengan ini tentu akan memperbesar nilai business metrics yang telah ditentukan seperti traffic dan sales performance. Sistem sudah menentukan mana user yang memang sedang tertarik atau bagian dari market untuk campaign yang akan dijalankan.

Business Metrics:
1. Response rate
2. Revenue rate

Goal: <br>
Dapat meningkatkan response rate campaign perusahaan, sehingga profit perusahaan dapat meningkat. 

## 3. Exploratory Data Analysis (EDA)
### Descriptive Analysis
Dataset terdiri atas 28 feature dan 1 target, yaitu Rensponse(rasio jumlah customer yang merespon dibandingkan dengan total impresi campaign)

### Univariate Analysis

![eda numerik](images/git1.PNG)

Dengan menggunakan boxplot, ditemukan adanya outlier pada feature Year_Birth dan Income.

![eda numerik](images/git2.PNG)

Selain itu, ditemukan juga outlier pada feature pembelian barang ('MntWines', 'MntFruits', 'MntMeatProducts', 'MntFishProducts', 'MntSweetProducts','MntGoldProds'). 

![eda numerik](images/git3.PNG)

Begitu pula dengan feature purchases ('NumWebPurchases','NumCatalogPurchases','NumStorePurchases',' NumWebVisitsMonth') juga ditemukan outlier. 

![eda response](images/git4.PNG)

> Sementara pada category-plot terdapat insight menarik pada feature response yaitu adanya ketimpangan antara customer yang merespon dengan tidak merespon. Hal ini menunjukkan adanya class imbalance, dimana nantinya harus dilakukan over/undersampling pada tahap pre-processing.


### Multivariate Analysis
![eda heatmap](images/heatmap.png)
> Dari heatmap plot, terlihat feature AcceptedCmp1 dan AcceptedCmp5 punya korelasi paling tinggi dengan target response dengan nilai masing-masing 0.33 dan 0.29.

Dan berikut merupakan beberapa feature yang kemungkinan akan kami pertahankan dan gunakan untuk analisis kedepannya:
- Recency
- MntWines
- MntMeatProducts
- NumCatalogPurchases
- AcceptedCmp3
- AcceptedCmp5
- AcceptedCmp1 

> Dari seluruh korelasi antara feature-target, seluruhnya berada di range 0.00 sampai 0.33. Oleh karena itu, kami memutuskan untuk membuat nilai threshold di angka 0.20. Feature-feature di atas yang kami pertahankan adalah feature yang memiliki nilai korelasi >0.20.

Selain itu, berdasarkan analisa awal antar-fitur yang kami lakukan terhadap fitur yang memiliki korelasi lebih tinggi dengan target, didapatkan hasil sebagai berikut:

*[Recency]*: Nilai korelasi Recency dengan feature lainnya memiliki range 0.00 sampai 0.05

*[MntWines]*: Berikut adalah feature yang berkorelasi dengan MntWines: Income(0.58), NumCatalogPurchases(0.64), NumStorePurchases(0.64)

*[MntMeatProducts]*: Berikut adalah feature yang berkorelasi dengan MntMeatProducts: NumCatalogPurchases(0.72), Income(0.58), MntWines(0.56)

*[NumCatalogPurchases]*: Berikut adalah feature yang berkorelasi dengan NumCatalogPurchases: MntMeatProducts(0.72), MntWines(0.64),Income(0.59)

*[AcceptedCmp3]*: Berikut adalah feature yang berkorelasi dengan AcceptedCmp3: MntGoldProducts(0.12)

*[AcceptedCmp5]*: Berikut adalah feature yang berkorelasi dengan AcceptedCmp5: MntWines(0.47), MntMeatProducts(0.37), Income(0.34)

*[AcceptedCmp1]*: Berikut adalah feature yang berkorelasi dengan AcceptedCmp1: AcceptedCmp5(0.40), MntWines(0.35), MntMeatProducts(0.31), NumCatalogPurchases(0.31)

> Dari hasil tersebut, kemungkinan besar nantinya akan kami gunakan sebagai fitur prioritas dalam keputusan penentuan indikator pendukung untuk pengkategorisasian customer mana yang layak diberikan campaign.

## 4. Business Insights & Recommendations
### Business Insights
- Bagaimana pengaruh memiliki kidhome dan teenhome terhadap tingkat respon customer?
<img width="221" alt="image" src="https://user-images.githubusercontent.com/88579085/212469050-f9328cc6-cb05-4a3a-bffc-8ee05c6fd780.png">
<img width="240" alt="image" src="https://user-images.githubusercontent.com/88579085/212469071-dcc51597-7187-4304-bb56-0b508b9f4ff3.png">
<img width="442" alt="image" src="https://user-images.githubusercontent.com/88579085/212469081-afb0c656-ee40-47a8-9b13-81a6829ac992.png">
<img width="432" alt="image" src="https://user-images.githubusercontent.com/88579085/212469095-d0848247-7312-43ff-ba11-1125d3c55b4d.png">

- Bagaimana persentase customer yang Respon dan Tidak Respon dengan status pernikahan?
<img width="728" alt="image" src="https://user-images.githubusercontent.com/88579085/212469194-ef9914e6-2a94-40e0-ba3b-9de3a57d4126.png">

- Bagaimana persentase customer yang Respon dan Tidak Respon dengan education level?
<img width="709" alt="image" src="https://user-images.githubusercontent.com/88579085/212469226-864b4796-1dae-4a4d-8e37-457ca67c6150.png">

### Business Recommendations
Berdasarkan data visualisasi, maka tim Data Scientist dapat memberikan rekomendasi untuk tim marketing, berupa:

- Dari visualisasi kidhome dan teenhome, dapat dilihat bahwa customer yang merespon terbanyak berasal dari customer yang tidak mempunyai anak dan tidak mempunyai remaja (0.265403), sehingga marketing team dapat memfokuskan campaign ke customer yang tidak mempunyai anak dan tidak mempunyai remaja.
- Dari visualisasi piechart Marital Status, dapat dilihat bahwa customer yang merespon terbanyak berasal dari customer yang berstatus Absurd (50%) dan Yolo(50%), disusul dengan Alone(33%) dan Widow (25%), sehingga marketing team dapat memfokuskan campaign ke customer "Absurd" dan "Yolo".
- Dari visualisai piechart Education, dapat dilihat bahwa customer yang merespon terbanyak berasal dari customer yang memiliki edukasi PhD (20.78%), disusul dengan Master (15.41%), sehingga marketing team dapat memfokuskan campaign ke customer yang beredukasi "PhD".

### Next Improvement
Selain dari tiga business insight tersebut, kami juga memiliki satu buah insight lagi berupa sebuah trend suatu product yang memiliki korelasi kuat (Gold, Meat, dan Wines) terhadap campaign 1 sampai dengan campaign 5. Kemudian, hasil dari visualisasi insight tersebut nantinya dapat digunakan oleh perusahaan untuk memprioritaskan produk mana yang akan dijual atau dipromosikan guna menarik jumlah customer. Sehingga diharapkan dengan adanya kenaikan jumlah customer tersebut, jumlah revenue perusahaan pun dapat bertambah.

Namun, dikarenakan keterbatasan waktu, kami belum sempat membuat visualisasi insight terakhir tersebut dan berencana untuk menjadikannya sebagai next improvements.

## 5. Data PreProcessing
### Data Cleansing & Feature Engineering
#### Handle Missing Values
<img width="169" alt="image" src="https://user-images.githubusercontent.com/88579085/213911728-2146d73b-5ae0-4b7c-8e5b-07dc220b363b.png">

> Berdasarkan hasil analisa awal, dapat diketahui bahwa terdapat data kosong pada kolom income sebanyak 24 baris dengan persentase sebesar 1,07% dari keseluruhan data, yang berarti tergolong jauh di bawah batas aman penghapusan data (10%). Sehingga keputusan yang kami lakukan terhadap missing value tersebut, yaitu dengan menghapus keseluruhan baris pada kolom Income yang memiliki nilai null (kosong)
<img width="300" alt="image" src="https://user-images.githubusercontent.com/88579085/213911819-aae8c1b5-28bd-4f75-ac5b-ac2d2a48e052.png">

#### Handle Duplicated Data
> Berdasarkan hasil pengecekan, tidak ditemui baris data yang memiliki duplikat. Sehingga kami tidak perlu melakukan handling duplicated data

#### Handle Outliers
<img width="642" alt="image" src="https://user-images.githubusercontent.com/88579085/213911867-96706d1e-ad23-457e-a1ab-eac426bcbd3b.png">
<img width="645" alt="image" src="https://user-images.githubusercontent.com/88579085/213911878-635a87b3-cc62-4ff4-bbda-a708ca3dce4c.png">
<img width="648" alt="image" src="https://user-images.githubusercontent.com/88579085/213911900-b849123e-2692-4ba8-b56a-ede8f51c1c7c.png">

> Berdasarkan grafik yang telah ditampilkan di atas, terlihat bahwa adanya outliers pada fitur 'Income', 'Year_Birth', 'Recency', 'MntWines', 'MntFruits', 'MntMeatProducts', 'MntFishProducts', 'MntSweetProducts', 'MntGoldProds', 'NumDealsPurchases', 'NumWebPurchases', 'NumWebVisitsMonth'. Sehingga, kami melakukan perbaikan pada fitur tersebut dengan menggunakan metode Z-score dan juga IQR untuk meminimalisir jumlah outliers yang terkandung dalam dataset.

##### Remove Outliers berdasarkan Z-score
<img width="266" alt="image" src="https://user-images.githubusercontent.com/88579085/213911935-f124f965-9aef-4ae7-b34f-0c9f360786b7.png">

##### Remove Outliers berdasarkan IQR
<img width="271" alt="image" src="https://user-images.githubusercontent.com/88579085/213911947-9f947ea7-ed65-4aec-adea-59423e98a1ef.png">
> Berdasarkan hasil perhitungan menggunakan Z-score dan juga IQR, dapat diketahui bahwa jumlah baris yang dihapus berdasarkan IQR jauh lebih banyak dibandingkan dengan Z-score, yaitu sekitar >30% dari total baris data yang dihapus. Maka dari itu, kami memutuskan untuk memilih metode Z-score untuk melakukan penghapusan pada baris outliers.

Setelah itu, kami melakukan plotting boxplot untuk melihat kembali persebaran outliers pada masing-masing fitur.
<img width="651" alt="image" src="https://user-images.githubusercontent.com/88579085/213911967-c2489736-df69-4b58-a54f-e7392315e145.png">
<img width="650" alt="image" src="https://user-images.githubusercontent.com/88579085/213911972-24b2d496-c0f4-4105-86dc-c10e1c743504.png">
<img width="654" alt="image" src="https://user-images.githubusercontent.com/88579085/213911983-2aa5c3f2-3c03-4c77-81c7-ff9026c166ec.png">

#### Feature Transformation
<img width="940" alt="image" src="https://user-images.githubusercontent.com/88579085/213912057-41853e15-6707-4fa8-8768-a374abe8b230.png">
<img width="943" alt="image" src="https://user-images.githubusercontent.com/88579085/213912067-c4bfcb6b-83cf-480f-aab1-e82c8bde63c2.png">
<img width="929" alt="image" src="https://user-images.githubusercontent.com/88579085/213912078-e9783b68-a1f2-461d-8cd9-67fad33ed8cd.png">

> Berdasarkan grafik yang telah ditampilkan di atas, terlihat bahwa adanya positively skewed pada fitur 'MntWines', 'MntFruits', 'MntMeatProducts', 'MntFishProducts', 'MntSweetProducts', 'MntGoldProds', 'NumDealsPurchases', 'NumWebPurchases', 'NumCatalogPurchases'. Sehingga, kami melakukan perbaikan pada feature tersebut dengan teknik feature transformation menggunakan metode log transformation.

<img width="368" alt="image" src="https://user-images.githubusercontent.com/88579085/213912103-c0130629-21da-418f-a34f-3ed39eb5e2fe.png">

##### Log Transformation
<img width="953" alt="image" src="https://user-images.githubusercontent.com/88579085/213912234-700d41b6-fe25-47ab-8478-1eb90856cc61.png">
<img width="948" alt="image" src="https://user-images.githubusercontent.com/88579085/213912244-494b6d9b-0161-43be-a044-83de8e7f4459.png">
<img width="472" alt="image" src="https://user-images.githubusercontent.com/88579085/213912251-b0e34142-3e8a-4c9f-a942-c171e3592034.png">
<img width="372" alt="image" src="https://user-images.githubusercontent.com/88579085/213912259-69ad4a1e-2343-4043-b622-1bf38437860f.png">

> Berdasarkan hasil pengecekan pada beberapa fitur yang telah diproses menggunakan log transformation sebelumnya, dapat diketahui bahwa keseluruhan nilai skewnessnya sudah memiliki rentang yang lebih seragam (tidak jauh dan tidak terlalu bervariasi). Sehingga dapat disimpulkan bahwa teknik fitur transformation yang telah kami lakukan sudah valid dan kami memutuskan untuk membuat kolom baru dengan isian nilai pada fitur yang sudah diolah tersebut.

<img width="962" alt="image" src="https://user-images.githubusercontent.com/88579085/213912286-08069ad1-9bf0-494b-b3c1-f27aa8540d32.png">

#### Feature Encoding
Setelah melakukan feature transformation, disini kami juga memutuskan untuk melakukan feature encoding pada kolom yang memiliki tipe data categorical untuk diubah menjadi numerical. Hal ini kami lakukan dengan harapan agar kemampuan machine learning yang kami buat dapat meningkat. Berikut merupakan beberapa feature yang kami olah pada tahap ini:

1. Mapping_marital, based on Marital_status
2. Mapping_education, based on Education

##### Label Encoding
Mapping_marital, based on Marital_status
![image](https://user-images.githubusercontent.com/88579085/213912402-e830deeb-3d11-4ee3-a498-5a6ea691ec51.png)
Mapping_education, based on Education
![image](https://user-images.githubusercontent.com/88579085/213912429-d8836507-690d-4e2c-85d7-830f44a9b5aa.png)

##### One Hot Encoding
<img width="666" alt="image" src="https://user-images.githubusercontent.com/88579085/213912485-7b434af6-d506-4205-aad0-96fec4a946bd.png">

<img width="213" alt="image" src="https://user-images.githubusercontent.com/88579085/213912490-3bf70fe7-570f-4f66-9f99-47051bed50a9.png">

<img width="295" alt="image" src="https://user-images.githubusercontent.com/88579085/213912511-be28f70e-9f51-4300-beb9-5115176f417f.png">

#### Feature Extraction
> Setelah melakukan feature encoding, disini kami juga memutuskan untuk melakukan feature extraction. Hal ini kami lakukan dengan tujuan untuk mempermudah tahapan feature selection yang akan dilakukan selanjutnya. Berikut merupakan beberapa feature yang kami ciptakan pada tahap ini:
1. primer_purcahase & tersier_purchase, yaitu sebuah fitur yang menggabungkan kolom pembelian buah, daging dan ikan, wine, makanan manis, dan gold ke dalam 2 golongan, yaitu primer dan tersier.
2. total_accepted_campaign, yaitu sebuah fitur yang menggabungkan acceptedcmp 1 - 5. Fitur ini dibuat untuk melihat intensitas customer dalam accepting campaign dari keseluruhan campaign yang telah dilakukan oleh perusahaan.
3. total_revenue, yaitu sebuah fitur yang dibuat dengan menjumlahkan total acceptence customer pada keseluruhan campaign sebelumnya (1-5) dengan jumlah revenue per accepted campaign.
4. total_spent, yaitu sebuah fitur yang menggabungkan total pembelian pada keseluruhan produk darimulai wines, fruits, meat, fish, sweet, sampai dengan gold untuk merekap total pengeluaran yang telah dilakukan oleh masing-masing customer.
5. total_order, yaitu sebuah fitur yang berisikan summary dari total purchases atau order yang telah dilakukan oleh pelanggan dari berbagai metode purchases.
6. month_customer, yaitu fitur bulan dimana customer mulai enroll/ register ke marketing campaign.
7. age, yaitu sebuah fitur yang mengkategorisasikan customer ke dalam 3 kelompok umur, yaitu: Elderly (2), Middle Age (1), dan Young (0).
8. income_category, yaitu sebuah fitur yang mengkategorisasikan customer berdasarkan pendapatannya ke dalam 3 kategori, yaitu High-Income (2), Mid-Income (1), dan Low-Income (0)
9. total_dependents, yaitu sebuah fitur yang menggabungkan kolom marital status, kidhome, dan teen home untuk melihat jumlah orang dalam 1 rumah yang dianggap sebagai tanggungan rumah tangga.

> Keseluruhan fitur tersebut nantinya akan diuji ulang saat feature selection untuk melihat seberapa besar pengaruhnya terhadap target atau probabilitas response yang diberikan customer dalam sebuah campaign.

Primer and tersier product
<img width="988" alt="image" src="https://user-images.githubusercontent.com/88579085/213912690-e76e8fcf-8c03-4d48-8e47-e5b69ebb7246.png">

Total accepted campaign
<img width="975" alt="image" src="https://user-images.githubusercontent.com/88579085/213912707-8c64d389-8496-4a52-af79-7dea33cc883c.png">

Total revenue
<img width="170" alt="image" src="https://user-images.githubusercontent.com/88579085/213912721-564e455a-0025-4226-967f-509677265208.png">

Total spent
<img width="987" alt="image" src="https://user-images.githubusercontent.com/88579085/213912730-91ae3c72-afec-44f2-ab50-25716a66c50b.png">

Total purchase/total order
<img width="967" alt="image" src="https://user-images.githubusercontent.com/88579085/213912750-144c7039-ba13-4002-be49-d5816ddbfe58.png">

Convert the date of enrolment to datetime
<img width="976" alt="image" src="https://user-images.githubusercontent.com/88579085/213912791-dd594ae2-c7da-480d-808c-118a057d6d14.png">

Age_category customer menurut WHO:
<img width="968" alt="image" src="https://user-images.githubusercontent.com/88579085/213912827-a6ff8999-f82b-4f63-aec9-36f7a262c733.png">

<img width="183" alt="image" src="https://user-images.githubusercontent.com/88579085/213912832-6045c4e1-358b-454a-9dc0-e6cf74c988b5.png">

Income Category
<img width="974" alt="image" src="https://user-images.githubusercontent.com/88579085/213912856-bf69b2a8-d894-423a-9f31-622dcf95fe13.png">

Jumlah tanggungan/ Total Dependants
<img width="977" alt="image" src="https://user-images.githubusercontent.com/88579085/213912878-2251be60-db6b-4bec-9b88-79bebba6344c.png">

<img width="283" alt="image" src="https://user-images.githubusercontent.com/88579085/213912893-1979e639-e1dd-4816-b76e-92d4b216076f.png">

#### Feature Selection
> Setelah melakukan feature extraction, pada tahap inilah saatnya kami untuk menyeleksi beberapa fitur yang kami anggap kurang penting khususnya yang memiliki korelasi rendah dengan target maupun fitur lainnya. Hal ini kami lakukan guna mempermudah tahap pembelajaran ML yang kami ciptakan nantinya.

> Gambar di bawah ini menunjukkan heatmap sebelum melakukan feature selection. Gambar setelahnya menunjukkan heatmap setelah melakukan feature selection. Kami membuat threshold 0.19 dimana di atas angka threshold, maka korelasi fitur dengan target cukup tinggi sehingga fitur tersebut diambil. Sementara itu, fitur-target dengan korelasi <0.19 tidak diambil.

Before

<img width="647" alt="image" src="https://user-images.githubusercontent.com/88579085/213912951-ef645a87-f70b-435d-b525-d2777a8392b0.png">

After

<img width="653" alt="image" src="https://user-images.githubusercontent.com/88579085/213912977-26285817-2f5f-465a-b514-b264786e5f94.png">

#### Handle Class Imbalance
Ratio Check for target

<img width="148" alt="image" src="https://user-images.githubusercontent.com/88579085/213912995-a3dedb0c-2462-473d-9f37-420bf8e04874.png">
<img width="162" alt="image" src="https://user-images.githubusercontent.com/88579085/213913002-a4e669cd-8f54-4427-8b0c-281bb3a71eed.png">

Use oversampling

<img width="73" alt="image" src="https://user-images.githubusercontent.com/88579085/213913020-755e076f-0114-4c78-aab3-c7a1168736fe.png">

> Dikarenakan adanya class imbalance atau ketimpangan data yang sangat jauh pada kolom target (response) dan jumlah sample yang dipelajari ML lebih banyak (1692 sample), maka dari itu kami memutuskan menggunakan oversampling untuk menghandle problem tersebut.

#### Feature Tambahan
1. ***Area/ Region*** Lokasi tempat tinggal customer dapat mempengaruhi tingkat respon customer terhadap pembelian barang. Semakin dekat tempat tinggal mereka dengan pusat kota, kemungkinan semakin sedikit yang merespon dikarenakan banyaknya kompetisi campaign dari market lainnya di sekitar kota.
2. ***Time call*** Waktu ketika ditelepon: pada saat jam kerja atau jam istirahat.
3. ***Day call*** Hari ketika ditelepon: weekend/ weekday.
4. ***Payment method*** Metode pembayaran yang digunakan untuk membeli barang: credit card/ COD/ Bank transfer/ e-money. Customer yang memakai metode credit card, kemungkinan tingkat respon dapat lebih tinggi daripada metode pembayaran lainnya.
5. ***Job position*** Jenis pekerjaan customer dapat mempengaruhi tingkat respon campaign: student/ professional/ unemployed.
