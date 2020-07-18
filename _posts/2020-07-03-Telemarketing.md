---
title: "Bank Telemarketing Analysis - Classification"
date: 2020-07-03
tags: [data wrangling, data science, messy data]
header:
excerpt: "Project ini bertujuan untuk membantu tim telemarketing dalam memilih nasabah-nasabah yang potensial untuk melakukan deposito atau tidak. Model-model yang digunakan adalah Logistic Regression, Random Forest Classifier, dan XGBoost Classifier. Dilakukannya juga resampling menggunakan SMOTE dan Near-Miss Algorithm. Dan model terbaik dipilih berdasarkan Recall tertinggi."
mathjax: "true"
---

## Introduction

Ini adalah Final Project Purwadhika untuk Program Data Science dan Machine Learning. Dimana data didapatkan dari UCI yang dapat diaskes secara publik di [sini](https://archive.ics.uci.edu/ml/datasets/bank+marketing). Project ini menggunakan <b>Logistic Regression, Random Forest Classifier, dan XGBoost Classifier</b>, dilakukan juga resampling menggunakan <b>SMOTE dan Near-miss Algorithm.</b> 

## Overview

Pada repo ini terbagi menjadi lima bagian:

<b>Bagian pertama:</b> Data cleaning and exploratory analysis
<b>Bagian kedua:</b> Modelling
<b>Bagian ketiga:</b> Adjusting Threshold
<b>Bagian keempat</b> Feature Importances
<b>Bagian kelima:</b> Model Deployment

## Summary

Pada <b>bagian pertama</b>: saya membersihkan data, dimana di data ini terdapat missing value yang ditandai dengan data berisikan <i>unknown</i> dan <i>non-existent</i>, kemudian saya juga melakukan eksplorasi data yang berisikan rekomendasi-rekomendasi seperti memberitahu profiling orang-orang yang tepat dikontak dan ditawarkan deposito dan juga dilakukannya analisa statistik (normality test & significance test). Untuk lebih lengkapnya dapat dilihat di [notebook ini](https://github.com/Stev-create/Bank-Telemarketing-Analysis---ML-Classification/blob/master/notebook/1.%20Data%20cleaning%20and%20exploratory%20analysis.ipynb)

Kemudian pada <b>bagian kedua</b>: dilakukannya resampling menggunakan SMOTE dan near-miss. Yang saya juga melakukan eksplorasi model dari model default hingga model yang telah di tuning. Untuk lebih lengkapnya dapat dilihat di [notebook ini untuk default](https://github.com/Stev-create/Bank-Telemarketing-Analysis---ML-Classification/blob/master/notebook/2.%20ML_Classification_Part_1%20(Default%20Model).ipynb) dan [notebook ini untuk model yang telah di tuning](https://github.com/Stev-create/Bank-Telemarketing-Analysis---ML-Classification/blob/master/notebook/3.%20ML_Classifiation_Part_2%20(Hyperparamater%20Tuning).ipynb). Di project ini, model terbaik dilihat dari F1-macro terbaik, dikarenakan dataset ini termasuk kategori <i>highly-imbalanced</i>. 

Selanjutnya pada <b>bagian ketiga</b>: saya melakukan adjusting threshold dengan bantuan precision-recall curve yang dapat dilihat lebih lengkapnya di [notebook ini](https://github.com/Stev-create/Bank-Telemarketing-Analysis---ML-Classification/blob/master/notebook/4.%20Adjusting%20threshold.ipynb)

Dan untuk <b>bagian keempat</b>: saya menunjukkan feature importances, yang dimakusdkan untuk memberitahu fitur apa yang paling membantu model melakukan klasifikasi. Yang juga dapat membantu bank untuk menyusun strategi selanjutnya. Untuk lengkapnya ada di [notebook ini](https://github.com/Stev-create/Bank-Telemarketing-Analysis---ML-Classification/blob/master/notebook/5.%20Feature%20Importances.ipynb)

Sedangkan di <b>bagian kelima</b>: Karena tujuan akhir project ini juga membuat dashboard. Maka saya mencoba untuk melihat gambarannya, yang lengkapnya dapat dilihat di [notebook ini](https://github.com/Stev-create/Bank-Telemarketing-Analysis---ML-Classification/blob/master/notebook/6.%20Model%20Deployment%20(try).ipynb)

## Result

### Bussiness Insight

Dari eksplorasi dapat disimpulkan bahwa:

1. Bank seharusnya target ke anak-anak muda yang masih berkuliah atau orang-orang tua yang sudah pensiun. Analisanya adalah anak-anak muda masih belum memilki banyak pengetahuan yang berurusan dengan investasi. Maka deposito akan menjadi alat investasi yang cocok untuk mereka, mengingat deposito memiliki resiko yang rendah. Begitu juga dengan orang-orang tua yang sudah pensiunan, deposito juga menjadi alat investasi yang cocok buat mereka, karena deposito punya resiko yang rendah. 

2. Bulan maret menjadi bulan terbaik untuk mengontak nasabah-nasabah. Karena dalam [notebook ini](https://github.com/Stev-create/Bank-Telemarketing-Analysis---ML-Classification/blob/master/notebook/1.%20Data%20cleaning%20and%20exploratory%20analysis.ipynb), ditunjukkan bahwa tingkat kesuksesan tertinggi ada pada bulan maret. 

3. Dari segi <i>socio-economics</i>, di dataset ini peluang orang-orang melakukan deposito lebih tinggi saat Euribor rendah, CCI rendah, CPI rendah, Jumlah pegawai bank rendah, dan tingkat variasi pada pegawai bank rendah. Sebetulnya ini dapat dijadikan diskusi, mengingat ternyata peluang orang-orang melakukan deposito lebih tinggi saat Euribor rendah. Kenapa? Karena Euribor adalah alat yang biasa dipakai bank untuk menentukan suatu suku bunga, suku bunga deposito maupun suku bunga pinjaman. Jadi terlihat adanya kejanggalan, melihat saat Euribor rendah yang artinya suku bunga deposito rendah, tapi malah peluang orang-orang melakukan deposito lebih tinggi saat Euribor merendah. 

Untuk lebih lengkapnya ada di [notebook ini](https://github.com/Stev-create/Bank-Telemarketing-Analysis---ML-Classification/blob/master/notebook/1.%20Data%20cleaning%20and%20exploratory%20analysis.ipynb).

### Evaluation Metrics

Dikarenakan data termasuk kategori <i>highly-imbalanced</i>, dan menurut saya ini juga permasalahan bisnis yang <i>highly-imbalanced</i>. Maka evaluasi metrik objektif pada project ini adalah f1_macro. Atau sebagai alternatif, orang lain mungkin juga ada yang ingin melihat Matthews Correlation Coefficient sebagai evaluasi metrik utamanya karena saya menunjukkannya juga. Tapi f1_macro yang saya gunakan di project ini.  


| Classifier | Macro F1 Score | Macro Recall | Macro Precision | Matthews correlation coefficient| 
|   :---:      |     :---:      |    :---:      |   :---:   |          :---: |
| Logistic Regression   | 0.639009    |  	0.604403   | 0.781723   |  0.343002   |
| Random Forest Classifier  (experiment 1)   | 0.618911       |  	0.587297     | 	0.816189  |  0.332280      |
| Random Forest Classifier  (experiment 2)   | 0.622705       |  	0.590151     | 	0.813908  |  0.336447      |
| XGBoost Classifier  (experiment 1) | 0.648942    |  	0.611661   | 0.796106   |  0.363668   |
| XGBoost Classifier (experiment 2) | 0.638802    |  	0.603841   | 0.787810   |  0.345753   |

### Reference

[Moro et al., 2014] S. Moro, P. Cortez and P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22-31, June 2014</p>


