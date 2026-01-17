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
