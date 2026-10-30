\# Hipotesis Bagian B



Ditulis sebelum menjalankan eksperimen Bagian B dengan CEPAT = False.



\## B2 Dropout (0 · 0,2 · 0,5)

Hipotesis: Dropout 0,2 memberi val MAE yang sama atau sedikit lebih baik daripada

dropout 0 (selisih kecil, mungkin masih dalam rentang simpangan baku antar seed).

Dropout 0,5 memperburuk val MAE pada keempat model, paling terasa pada model

berukuran kecil.

Alasan: Data train hanya 672 sampel sehingga overfitting mungkin terjadi, dan

dropout ringan bisa membantu. Namun model yang dipakai kecil (hidden 32-68),

sehingga dropout 0,5 membuang terlalu banyak kapasitas dan menyebabkan underfitting.

Pada model rekuren satu lapisan, efek dropout bisa lebih kecil dibanding ANN

karena dropout hanya berlaku di bagian tertentu arsitektur.



\## B7 Gradient clipping (tidak ada · 0,5 · 1,0, lr 0,01)

Hipotesis: Pada lr 0,01, clipping terutama menurunkan simpangan baku antar seed,

terutama pada RNN, sementara perbaikan rata-rata val MAE-nya kecil. LSTM dan GRU

hampir tidak terpengaruh. Clip 0,5 sedikit lebih stabil daripada 1,0 tetapi

konvergensinya lebih lambat.

Alasan: RNN biasa rentan terhadap gradien meledak pada learning rate besar karena

gradien dikalikan berulang sepanjang 24 langkah waktu. Clipping membatasi ukuran

langkah update. Gerbang pada LSTM dan GRU sudah mengatur aliran gradien, jadi

manfaat clipping pada keduanya lebih kecil.

