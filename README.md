Nama    : Muhammad Fawwaz
NIM     : 13519206

## Simple Tensorflow 

Tensorflow merupakan open source library yang digunakan dalam bidang pembelajaran mesin atau machine learning. Tensorflow ditulis dengan menggunakan C++ dan biasanya digunakan dalam bahasa Python.

Kali ini, akan dibuat program klasifikasi pakaian menggunakan tensorflow secara singkat.
Untuk memulai menggunakan tensorflow, import library yang digunakan.

```
import tensorflow as tf
from tensorflow import keras

import numpy as np
```

Kemudain load dataset dari keras.
```
 fashion = keras.datasets.fashion_mnist

(train_images, train_labels), (test_images, test_labels) = fashion.load_data()
```

Dataset tersebut akan dimuat dalam NumPy arrays pada `train_images` dan `train_labels` sebagai model latih serta `test_images` dan `test_labels` sebagai model uji.

Label dari dataset berisi nilai integer 0-9 yang tiap integer merepresentasikan sebuah kategori. Dengan tiap kategori adalah sebagai berikut (urut 0-9)
`['T-shirt/top', 'Trouser', 'Pullover', 'Dress', 'Coat', 'Sandal', 'Shirt', 'Sneaker', 'Bag', 'Ankle boot']`
               
 Selanjutnya akan dilakukan data wrangling and exploration yang tidak dibahas disini. Kemudian akan dibuat model dari data latih.
 
 Pertama layer akan diatur
 ```
 model = keras.Sequential([
    keras.layers.Flatten(input_shape=(28, 28)),
    keras.layers.Dense(128, activation='relu'),
    keras.layers.Dense(10, activation='softmax')
])
```

28x28 merupakan ukuruan tiap gambar dalam dataset, 128 menunjukkan bahwa layer pertama memiliki 128 node dan 10 menunjukkan layer terakhir memiliki 10 node yang merepresentasikan 10 nilai probabilitas yang jumlahnya adalah 1. Layer terakhir tersebut di-set 10 sebab akan diklasifikasi 10 jenis pakaian.

Kemudian sebelum melatih dataset, akan dilakukan beberapa pengaturan
```
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])
```

- Optimizer adalah bagaimana cara suatu model untuk memperbarui dirinya berdasarkan data yang dilihat dan berdasarkan loss function
- Loss function merupakan fungsi untuk menghitung seberapa akurat model ketika dilakukan pelatihan
- Metrics digunakan untuk mengevaluasi langkah pelatihan dan pengujian 

Selanjutnya data siap untuk dilatih.
`model.fit(train_images, train_labels, epochs=10)`

Kemudian akan dilakukan prediksi pada data uji
`predictions = model.predict(test_images)`

Kita juga dapat memprediksi sebuah gambar lain, misal kita memiliki gambar yang akan diprediksi dengan nama `img`, maka untuk memprediksinya
```
img_pred = model.predict(img)
```
Untuk mengetahui hasil prediksi kita bisa menggunakan
`np.argmax(img_pred[0])`

Nilai yang keluar adalah hasil prediksi sesuai kategori berikut urut dari 0-9
`['T-shirt/top', 'Trouser', 'Pullover', 'Dress', 'Coat', 'Sandal', 'Shirt', 'Sneaker', 'Bag', 'Ankle boot']`

Bila yang keluar adalah 1 maka hasil prediksi adalah Trouser dan seterusnya.
