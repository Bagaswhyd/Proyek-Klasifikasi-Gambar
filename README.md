Proyek Klasifikasi Gambar: 5 Flower Types Classification

Nama: Muhammad Bagas Wahyudi

Email: mbagaswahyudi03@gmail.com

ID Dicoding: muhammadbagaswhyudi

Deskripsi Proyek
Proyek ini bertujuan untuk membangun model Computer Vision menggunakan Convolutional Neural Network (CNN) untuk mengklasifikasikan gambar bunga ke dalam 5 kategori berbeda. Model dikembangkan dengan memanfaatkan teknik Transfer Learning menggunakan arsitektur MobileNetV2 sebagai base model, serta menambahkan layer konvolusi kustom secara eksplisit untuk memenuhi kriteria arsitektur.

Dataset
Dataset yang digunakan adalah 5 Flower Types Classification Dataset yang diambil dari Kaggle.
https://www.kaggle.com/datasets/kausthubkannan/5-flower-types-classification-dataset

Sumber: Kaggle - 5 Flower Types Classification Dataset
Total Gambar: 5.000 gambar.
Kelas (Labels):
Lilly
Lotus
Orchid
Sunflower
Tulip

Pembagian Data:
Train Set: 4.000 gambar (80%)
Validation Set: 500 gambar (10%)
Test Set: 500 gambar (10%)
Arsitektur Model
Model menggunakan pendekatan Sequential dengan kombinasi layer pre-trained dan layer konvolusi kustom.

Base Model: MobileNetV2 (Input shape: 224x224x3)
Weight: ImageNet
Status: Frozen (Trainable = False).

Layer Kustom (Conv2D & Pooling):
Conv2D (256 filters, 3x3 kernel, activation='relu')
MaxPooling2D (2x2 pool size)
Layer ini ditambahkan secara eksplisit untuk memenuhi kriteria arsitektur CNN standar.

Classification Head:
GlobalAveragePooling2D
Dropout (0.5)
Dense (512 units, ReLU activation)
Dense Output (5 units, Softmax activation)
Prosedur Training
Preprocessing: Resizing gambar ke 224x224, normalisasi pixel (1/255), dan data augmentation (RandomFlip, RandomRotation, RandomZoom).

Optimizer: Adam dengan Learning Rate awal 0.001.
Loss Function: Categorical Crossentropy.

Callbacks:
EarlyStopping: Untuk menghentikan training jika val_loss tidak membaik (patience=10).
ReduceLROnPlateau: Untuk menurunkan learning rate jika metric mentok (patience=5).

Hasil Akhir:
Training Accuracy: 92.00%
Test Accuracy: 90.04%

Status: ✅ LULUS (Target > 85%)
Konversi Model
Model telah berhasil disimpan dalam tiga format sesuai ketentuan:

SavedModel: Format standar TensorFlow untuk deployment server/cloud (saved_model.pb & variables).
TF-Lite: Format ringan untuk perangkat mobile dan embedded (model.tflite & label.txt).
TensorFlow.js: Format untuk deployment aplikasi berbasis web browser (model.json & biner).

Cara Menjalankan (How to Run)
Buka file notebook.ipynb di Google Colaboratory atau Jupyter Notebook.
Pastikan runtime menggunakan GPU untuk mempercepat training.
Jalankan semua cell secara berurutan dari atas sampai bawah.
Model akan otomatis terdownload dari Kaggle, dilatih, dan disimpan ke dalam folder saved_model, tflite, dan tfjs_model.
