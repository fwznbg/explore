Nama    : Muhammad Fawwaz
NIM     : 13519206

## Tensorflow

Tensorflow merupakan open source library yang digunakan dalam bidang pembelajaran mesin atau machine learning. Tensorflow ditulis dengan menggunakan C++ dan biasanya digunakan dalam bahasa Python.

Selanjutnya, akan dibuat program klasifikasi pakaian menggunakan tensorflow.
Untuk memulai menggunakan tensorflow, import library yang digunakan.

```
import tensorflow as tf
from tensorflow import keras

import numpy as np
import matplotlib.pyplot as plt
```

Kemudain load dataset dari keras.
```
 fashion = keras.datasets.fashion_mnist

(train_images, train_labels), (test_images, test_labels) = fashion.load_data()
```

Dataset tersebut akan dimuat dalam NumPy arrays pada `train_images` dan `train_labels` sebagai model latih serta `test_images` dan `test_labels` sebagai model uji.
