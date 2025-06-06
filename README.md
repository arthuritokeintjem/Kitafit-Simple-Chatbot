# Simple FAQ Chatbot for KitaFit

![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-≥1.0-blue.svg)
![Python](https://img.shields.io/badge/Python-3.8+-brightgreen.svg)
![Sastrawi](https://img.shields.io/badge/Stemmer-Sastrawi-lightgrey.svg)

## Deskripsi Proyek

Proyek ini adalah implementasi chatbot sederhana yang mampu menjawab pertanyaan umum (FAQ) seputar aplikasi fiktif bernama **KitaFit**. Chatbot ini memanfaatkan model *Natural Language Understanding* (NLU) untuk mengklasifikasikan maksud (intent) dari pertanyaan pengguna dan memberikan jawaban yang relevan.

Tujuan utama proyek ini adalah untuk mendemonstrasikan alur kerja end-to-end dalam pembuatan chatbot berbasis AI, mulai dari persiapan data, preprocessing teks, pelatihan model deep learning, hingga implementasi interaktif.

## Fitur Utama

-   **Klasifikasi Intent**: Mampu mengenali 10 kategori pertanyaan yang berbeda, seperti informasi umum, pendaftaran, fitur, biaya, privasi, dan lainnya.
-   **Respons Dinamis**: Memberikan variasi jawaban untuk intent yang sama agar interaksi terasa lebih alami dan tidak repetitif.
-   **Penanganan Ketidakpastian**: Jika chatbot tidak yakin dengan maksud pengguna (skor kepercayaan di bawah ambang batas), ia akan merespons secara jujur bahwa ia tidak mengerti.

## Teknologi yang Digunakan

-   **Machine Learning & Deep Learning**:
    -   **TensorFlow / Keras**: Untuk membangun dan melatih model neural network kustom untuk klasifikasi intent.
    -   **Scikit-learn**: Untuk ekstraksi fitur teks menggunakan `TfidfVectorizer` dan encoding label.
-   **Natural Language Processing (NLP)**:
    -   **Sastrawi**: Untuk proses *stemming* (mengubah kata ke bentuk dasarnya) yang akurat untuk Bahasa Indonesia.
    -   **NLTK (Natural Language Toolkit)**: Untuk tokenisasi dan penghapusan *stop words*.
-   **Manajemen Data**:
    -   **Pandas & NumPy**: Untuk memuat, mengelola, dan memanipulasi data secara efisien.

## Struktur Proyek

```
.
├── faq_dataset_100.csv     # Dataset berisi pertanyaan dan intent untuk training
├── notebook_update.ipynb   # Notebook utama berisi semua proses (data, training, evaluasi)
├── README.md               # File dokumentasi ini
└── requirements.txt        # Daftar library Python yang dibutuhkan
```

## Instalasi dan Setup

Untuk menjalankan proyek ini di lingkungan lokal Anda, ikuti langkah-langkah berikut:

1.  **Clone Repository**
    ```bash
    git clone [https://github.com/](https://github.com/)[YourUsername]/[YourRepositoryName].git
    cd [YourRepositoryName]
    ```

2.  **Buat dan Aktifkan Virtual Environment (Sangat Direkomendasikan)**
    ```bash
    # Membuat environment
    python -m venv venv
    
    # Aktivasi di Windows
    .\venv\Scripts\activate
    
    # Aktivasi di macOS/Linux
    source venv/bin/activate
    ```

3.  **Install Dependencies**
    Proyek ini memerlukan beberapa library Python. Install semuanya menggunakan file `requirements.txt`.
    ```bash
    pip install -r requirements.txt
    ```
    *Catatan: Jika file `requirements.txt` belum ada, Anda bisa membuatnya dengan `pip freeze > requirements.txt` setelah menginstall library di bawah ini secara manual:*
    ```bash
    pip install pandas numpy scikit-learn tensorflow nltk Sastrawi
    ```

4.  **Download Resource NLTK**
    Jalankan notebook, dan kode di dalamnya akan secara otomatis mengunduh resource NLTK yang diperlukan (`stopwords`, `punkt`).

## Cara Menjalankan

1.  Pastikan semua dependensi sudah ter-install dan virtual environment sudah aktif.
2.  Jalankan Jupyter Notebook:
    ```bash
    jupyter notebook
    ```
3.  Buka file `notebook_update.ipynb` dari antarmuka Jupyter di browser Anda.
4.  Jalankan setiap sel kode secara berurutan dari atas ke bawah. Sel terakhir berisi loop interaktif di mana Anda dapat mulai mengobrol dengan chatbot.

## Alur Kerja Model

1.  **Data Loading**: Dataset `faq_dataset_100.csv` dimuat ke dalam DataFrame Pandas.
2.  **Text Preprocessing**: Setiap pertanyaan pengguna dibersihkan melalui beberapa tahap:
    -   Konversi ke huruf kecil.
    -   Penghapusan tanda baca dan karakter spesial.
    -   Tokenisasi menggunakan NLTK.
    -   Penghapusan *stop words* Bahasa Indonesia.
    -   *Stemming* ke kata dasar menggunakan **Sastrawi**.
3.  **Feature Extraction**: Teks yang sudah bersih diubah menjadi vektor numerik menggunakan **TF-IDF**, yang mengukur pentingnya sebuah kata dalam dataset.
4.  **Model Training**: Vektor TF-IDF digunakan untuk melatih model *Sequential Neural Network* sederhana dengan TensorFlow/Keras untuk mengklasifikasikan intent dari setiap input teks.
5.  **Inference**: Saat pengguna memasukkan pertanyaan baru, pertanyaan tersebut melewati proses preprocessing dan TF-IDF yang sama, lalu dimasukkan ke model yang sudah dilatih untuk mendapatkan prediksi intent.

## Potensi Peningkatan

-   **Penambahan Data Training**: Menambah lebih banyak variasi kalimat dan pertanyaan untuk setiap intent adalah cara paling efektif untuk meningkatkan akurasi dan ketahanan model.
-   **Hyperparameter Tuning**: Melakukan eksperimen lebih lanjut dengan parameter model (misalnya, learning rate, jumlah neuron, dropout rate) untuk menemukan konfigurasi optimal.
-   **Menambah Intent Baru**: Memperluas kemampuan chatbot dengan menambahkan lebih banyak kategori FAQ, seperti "keamanan akun" atau "integrasi perangkat".
-   **Deployment**: Menyimpan model yang telah dilatih dan mendeploy-nya sebagai API service (misal: menggunakan Flask/FastAPI) agar bisa diintegrasikan dengan aplikasi lain.
