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

Sementara pada category-plot terdapat insight menarik pada feature response yaitu adanya ketimpangan antara customer yang merespon dengan tidak merespon. Hal ini menunjukkan adanya class imbalance, dimana nantinya harus dilakukan over/undersampling pada tahap pre-processing.


### Multivariate Analysis
![eda heatmap](images/heatmap.png)
Dari heatmap plot, terlihat feature AcceptedCmp1 dan AcceptedCmp5 punya korelasi paling tinggi dengan target response dengan nilai masing-masing 0.33 dan 0.29.

Dan berikut merupakan beberapa feature yang kemungkinan akan kami pertahankan dan gunakan untuk analisis kedepannya:

Recency
MntWines
MntMeatProducts
NumCatalogPurchases
AcceptedCmp3
AcceptedCmp5
AcceptedCmp1 

Dari seluruh korelasi antara feature-target, seluruhnya berada di range 0.00 sampai 0.33. Oleh karena itu, kami memutuskan untuk membuat nilai threshold di angka 0.20. Feature-feature di atas yang kami pertahankan adalah feature yang memiliki nilai korelasi >0.20.
