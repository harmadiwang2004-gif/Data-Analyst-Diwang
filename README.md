# Data Analyst GR VS DeltaPHI

Grafik ini dipakai buat membedakan jenis batuan / facies berdasarkan respon log.
Grafik ini menjelaskan bagaimana ML memisahkan facies berdasarkan GR dan DeltaPHI

<img width="499" height="374" alt="image" src="https://github.com/user-attachments/assets/4ccc60f1-6745-40da-bc7f-54d74c1e15a2" />

Sumbu X – GR (Gamma Ray)

Kecil menandakan batuan bersih (sandstone/karbonat). Besar menandakan shale / clay tinggi

Sumbu Y – DeltaPHI Selisih porositas (density – neutron)

Positif mengindikasikan gas effect atau porositas efektif. Negatif mengindikasikan shale, tight rock, atau efek bound water

# Model Klasifikasi
## Kmeans
<img width="486" height="385" alt="image" src="https://github.com/user-attachments/assets/c3e1d4a6-9df7-4596-8b1b-8d07727987c8" />

Data log GR (X) dan DeltaPHI (Y)
Sudah dikelompokkan otomatis oleh algoritma K-Means
Label 0–3 = cluster, bukan facies geologi langsung
Arti warna / cluster
Setiap warna menunjukkan kelompok data dengan karakter log mirip.
Cluster 0 (biru tua)
GR rendah (±20–60)
DeltaPHI kecil sampai negatif
maknanya, Clean–tight sand atau wet sand. Porositas ada, tapi belum tentu gas

Cluster 1 (biru muda)
GR rendah–menengah (±40–90)
DeltaPHI positif tinggi
maknanya, Strong gas effect. Kandidat gas sand / good reservoir

Cluster 2 (oranye)
GR tinggi (100–350)
DeltaPHI sedikit positif
maknanya, Shaly sand / shale, Non-reservoir dominan

Cluster 3 (oranye muda)
GR menengah (60–100)
DeltaPHI negatif besar
maknanya, Shale dengan bound water dan Tight / poor quality rock

## Gaussian Mixture
<img width="495" height="382" alt="image" src="https://github.com/user-attachments/assets/3bf85a49-c638-4104-8d23-2b675c648406" />

Interpretasi tiap cluster (secara geologi)
GM-0 (biru tua)
GR rendah (±20–50)
DeltaPHI rendah–negatif
menandakan, Clean sand / tight sand dan Reservoir kualitas rendah–sedang

GM-1 (biru muda)
GR rendah–menengah (±40–90)

DeltaPHI positif tinggi
maknanya, Gas effect kuat dan Gas sand / good reservoir

GM-2 (oranye)
GR menengah (±60–100)

DeltaPHI negatif
maknanya, Shaly sand / shale, Non-reservoir dominan

GM-3 (oranye muda)
GR tinggi (100–350)

DeltaPHI kecil–positif
maknanya, Shale murni / very shaly interval

## Agglomerative Clustering
<img width="489" height="375" alt="image" src="https://github.com/user-attachments/assets/e44b55c1-6cc2-4c93-ab71-02b0a2a81809" />

Interpretasi cluster di grafik
AC-0 (biru tua)
GR Rendah (±20–60)
DeltaPHI kecil–negatif
menandakan, Clean sand / tight sand dan Reservoir kualitas rendah–sedang

AC-1 (biru muda)
GR rendah–menengah (±40–90)

DeltaPHI positif tinggi
maknanya, Gas effect kuat. Gas sand / high quality reservoir

AC-2 (oranye)
GR menengah (±60–100)

DeltaPHI negatif besar
maknanya, Shaly sand / shale. Non-reservoir

AC-3 (oranye muda)
GR tinggi (100–350)

DeltaPHI kecil–positif
maknanya, Shale dominan / very shaly interval

# Kesimpulan dari penggunaan ketiga ML
Berdasarkan hasil analisis crossplot GR (Gamma Ray) terhadap DeltaPHI menggunakan tiga metode unsupervised machine learning yaitu K-Means, Gaussian Mixture (GM), dan Agglomerative Clustering, dapat disimpulkan bahwa seluruh metode mampu mengelompokkan data log berdasarkan kemiripan karakter petrofisika, khususnya kandungan shale dan respon porositas.

Metode K-Means menghasilkan pemisahan cluster yang tegas namun cenderung membentuk batas yang bersifat matematis dan kurang merepresentasikan transisi litologi alami. Metode ini efektif sebagai tahap awal pengelompokan, namun memiliki keterbatasan dalam menangkap heterogenitas reservoir.

Metode Gaussian Mixture (GM) menunjukkan kemampuan yang lebih baik dalam merepresentasikan kondisi geologi yang bersifat gradual dan heterogen. Adanya overlapping antar cluster mencerminkan transisi alami antara batuan bersih, shaly sand, dan shale, sehingga metode ini dinilai paling realistis secara geologi untuk interpretasi facies berbasis data log.

Sementara itu, Agglomerative Clustering mampu menghasilkan pemisahan cluster yang lebih terstruktur dan konsisten, dengan batas facies yang relatif jelas tanpa terlalu memaksakan bentuk cluster tertentu. Metode ini sesuai digunakan sebagai validasi hasil clustering lainnya serta untuk memahami hubungan hierarkis antar facies.

Secara keseluruhan, kombinasi interpretasi dari ketiga metode menunjukkan bahwa zona dengan GR rendah dan DeltaPHI positif berasosiasi dengan reservoir berkualitas baik, sedangkan zona dengan GR tinggi dan DeltaPHI negatif hingga mendekati nol diinterpretasikan sebagai shale atau non-reservoir. Dari ketiga metode yang digunakan, Gaussian Mixture Model memberikan hasil yang paling representatif terhadap kondisi geologi aktual, sehingga direkomendasikan sebagai metode utama dalam analisis facies berbasis data petrofisika.
