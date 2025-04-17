# Sentiment Analysis Ulasan Shopee ✨

Selamat datang di proyek analisis sentimen untuk ulasan aplikasi Shopee! 🚀 Proyek ini menganalisis ulasan pengguna dari Google Play Store menggunakan machine learning untuk mengklasifikasikan sentimen menjadi **positif** 😊, **negatif** 😕, atau **netral** 😐. Dengan preprocessing teks dalam bahasa Indonesia, visualisasi keren, dan model canggih, proyek ini membantu memahami kepuasan pengguna Shopee! 📊

## Apa yang Bisa Kamu Lakukan? 🛠️
- 📝 Preprocessing teks bahasa Indonesia (case folding, stemming, stopwords)
- 📈 Visualisasi distribusi sentimen dan kata-kata populer
- 🤖 Melatih model seperti Logistic Regression, SVM, Random Forest, dan MLP
- 🔍 Memprediksi sentimen dari kalimat baru
- 🎨 Membuat "stiker" berupa word cloud atau grafik untuk laporan

## Persyaratan Sistem ⚙️
- **Python**: 3.12 🐍
- **OS**: Windows, macOS, atau Linux 🖥️
- **Virtual Environment**: Untuk isolasi dependensi 🔒
- **Koneksi Internet**: Untuk mengunduh dataset atau dependensi 🌐

## Setup Environment 🚀

### 1. Buat Virtual Environment 🌍
Buat dan aktifkan virtual environment dengan Python 3.12:

```bash
python3.12 -m venv venv
```

Aktifkan:
- **Windows**:
  ```bash
  venv\Scripts\activate
  ```
- **macOS/Linux**:
  ```bash
  source venv/bin/activate
  ```

### 2. Install Dependensi 📦
Instal semua dependensi dengan file `requirements.txt`:

```bash
pip install -r requirements.txt
```

Buat file `requirements.txt` dengan konten berikut:

```plaintext
pandas==2.2.2
numpy==1.26.4
matplotlib==3.9.2
seaborn==0.13.2
scikit-learn==1.5.1
imblearn==0.12.3
nltk==3.8.1
sastrawi==1.0.1
wordcloud==1.9.3
google-play-scraper==1.2.7
requests==2.32.3
```

Jalankan lagi perintah di atas setelah membuat file. ✅

### 3. Setup NLTK untuk Tokenisasi 🗣️
Unduh data NLTK untuk tokenisasi dan stopwords:

```python
import nltk
nltk.download('punkt_tab')
nltk.download('stopwords')
```

### 4. Gunakan Sastrawi untuk Bahasa Indonesia 🇮🇩
Library `Sastrawi` menangani stemming dan stopwords dalam bahasa Indonesia. Sudah termasuk di `requirements.txt`, jadi tidak perlu konfigurasi tambahan! 🎉

### 5. Siapkan Dataset 📂
Pastikan file `dataset_reviews.csv` ada di direktori proyek. File ini berisi ulasan Shopee dengan kolom seperti `content` (teks ulasan) dan `score`. Jika ingin mengambil ulasan baru, gunakan `google-play-scraper` dengan koneksi internet. 🌐

## Menjalankan Proyek 🏃‍♂️

1. **Buka Notebook** 📓:
   Jalankan Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
   Buka file `Sentiment Analysis using Machine Learning.ipynb`.

2. **Jalankan Kode** ▶️:
   Eksekusi sel kode secara berurutan untuk:
   - Mengimpor library 📚
   - Memuat dan memproses dataset 🗂️
   - Membuat visualisasi (distribusi sentimen, panjang teks, kata populer) 📊
   - Melatih model (Logistic Regression, SVM, Random Forest, MLP) 🤖
   - Memprediksi sentimen kalimat baru 🔍

3. **Prediksi Kalimat Baru** ✍️:
   Di bagian akhir, masukkan kalimat baru untuk diprediksi sentimennya menggunakan model terbaik (MLP). Contoh:
   ```
   Masukkan kalimat baru: Aplikasi Shopee sangat membantu, banyak diskon!
   Sentimen kalimat baru adalah: POSITIF.
   ```

## Membuat Stiker (Visualisasi Keren) 🎨✨
"Stiker" di sini merujuk pada visualisasi grafis seperti word cloud atau plot yang bisa digunakan untuk laporan atau dicetak sebagai stiker fisik. Berikut cara membuatnya:

### 1. Distribusi Sentimen 📊
Visualisasi distribusi kelas (positif, negatif, netral) menggunakan `seaborn.countplot`. Simpan sebagai gambar:
```python
plt.savefig('class_distribution.png', dpi=300, bbox_inches='tight')
```
**Hasil**: Diagram batang yang menunjukkan jumlah ulasan per sentimen. 🖼️

### 2. Histogram Panjang Teks 📏
Histogram panjang teks dibuat dengan `seaborn.histplot`. Simpan:
```python
plt.savefig('text_length_distribution.png', dpi=300, bbox_inches='tight')
```
**Hasil**: Grafik distribusi panjang ulasan. 📉

### 3. Kata Teratas 🔝
Diagram batang kata-kata paling sering (berdasarkan TF-IDF) menggunakan `seaborn.barplot`. Simpan:
```python
plt.savefig('most_frequent_words.png', dpi=300, bbox_inches='tight')
```
**Hasil**: Daftar kata populer dalam ulasan. 📋

### 4. Word Cloud (Stiker Keren!) ☁️
Buat word cloud untuk visualisasi kata-kata populer:
```python
from wordcloud import WordCloud
import matplotlib.pyplot as plt

# Gabungkan teks dari kolom 'text_akhir'
text = ' '.join(clean_df['text_akhir'])

# Buat word cloud
wordcloud = WordCloud(width=800, height=400, background_color='white', max_words=100).generate(text)

# Tampilkan dan simpan
plt.figure(figsize=(10, 5))
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis('off')
plt.savefig('wordcloud.png', dpi=300, bbox_inches='tight')
plt.show()
```
**Hasil**: Gambar word cloud yang menarik, cocok untuk laporan atau dicetak sebagai stiker! 🖨️

**Tips Stiker Fisik** 🏷️:
- Gunakan `wordcloud.png` atau visualisasi lain di alat desain seperti Canva untuk menambahkan elemen grafis.
- Cetak melalui penyedia stiker lokal dengan file PNG beresolusi tinggi.

## Catatan Penting ⚠️
- **Bahasa Indonesia** 🇮🇩: Pastikan input teks menggunakan bahasa Indonesia untuk hasil akurat. `Sastrawi` menangani stemming dan stopwords dengan baik.
- **Model Terbaik** 🏆: MLP memiliki akurasi tertinggi (0.9063). Gunakan untuk prediksi sentimen baru.
- **Performa** ⏱️: Pelatihan Random Forest dan MLP bisa memakan waktu. Pastikan perangkat Anda cukup kuat.
- **MemoryError** 💾: Jika terjadi error memori saat menggunakan `TfidfVectorizer`, kurangi `max_features` (misalnya, dari 10000 ke 5000). Berdasarkan pengalaman Anda sebelumnya, ini membantu mengatasi masalah memori.
- **Visualisasi** 📊: Untuk menghindari peringatan tata letak Matplotlib (seperti yang Anda temui sebelumnya), gunakan `bbox_inches='tight'` saat menyimpan gambar.
---
