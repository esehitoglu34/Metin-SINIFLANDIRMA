# Metin Sınıflandırma Projesi

Bu proje, Türkçe metinleri farklı kategorilere sınıflandırmak için geliştirilmiş bir makine öğrenmesi uygulamasıdır. Proje, hem PySpark hem de geleneksel Python kütüphaneleri kullanılarak iki farklı yaklaşımla gerçekleştirilmiştir.

## Proje İçeriği

Proje aşağıdaki ana bileşenlerden oluşmaktadır:

1. **PySpark ile Metin Sınıflandırma**
   - `PySpark-ile-cok-Sinifli-Metin-Siniflandirma.ipynb`
   - `pyspark.ipynb`
   - `pyspark yeni.ipynb`

2. **Geleneksel Python ile Metin Sınıflandırma**
   - `text_classification_colab.py`
   - `text_classification_colab.ipynb`
   - `text classification.ipynb`

3. **Veri ve Yardımcı Dosyalar**
   - `temiz_metin.txt`: İşlenmiş metin verileri
   - `stopwords.txt`: Türkçe durdurma kelimeleri
   - `stopwords-en.txt`: İngilizce durdurma kelimeleri

## Kategoriler

Metinler aşağıdaki 7 kategoriye sınıflandırılmaktadır:
- Siyaset
- Ekonomi
- Dünya
- Kültür
- Sağlık
- Spor
- Teknoloji

Her kategori için 700 adet metin örneği bulunmaktadır.

## Kullanılan Teknolojiler

### PySpark Versiyonu
- PySpark 3.5.0
- Spark ML
- RegexTokenizer
- StopWordsRemover
- CountVectorizer
- LogisticRegression

### Python Versiyonu
- NLTK
- scikit-learn
- TensorFlow
- XGBoost
- LightGBM
- Zemberek (Türkçe doğal dil işleme)

## Metin İşleme Adımları

1. **Ön İşleme**
   - Küçük harfe çevirme
   - Noktalama işaretlerini kaldırma
   - Durdurma kelimelerini kaldırma
   - Sayıları kaldırma
   - 2 karakterden kısa kelimeleri kaldırma
   - Fazla boşlukları temizleme

2. **Türkçe Özel İşlemler**
   - Zemberek ile lemmatization
   - Türkçe durdurma kelimeleri filtreleme

3. **Özellik Çıkarımı**
   - TF-IDF vektörizasyonu
   - N-gram özellikleri (1-2 gram)

## Sınıflandırma Modelleri

Projede kullanılan sınıflandırma algoritmaları:
- K-En Yakın Komşu (KNN)
- Lojistik Regresyon
- Karar Ağaçları
- Destek Vektör Makineleri (SVM)
- XGBoost
- LightGBM

## Performans Metrikleri

Her model için aşağıdaki metrikler hesaplanmaktadır:
- Doğruluk (Accuracy)
- Kesinlik (Precision)
- Duyarlılık (Recall)
- F1-Skoru
- Ortalama Mutlak Hata (MAE)
- Ortalama Kare Hata (MSE)

## Kurulum

1. Gerekli Python paketlerinin kurulumu:
```bash
pip install pyspark findspark nltk scikit-learn tensorflow xgboost lightgbm
```

2. NLTK verilerinin indirilmesi:
```python
import nltk
nltk.download("stopwords")
nltk.download('punkt')
nltk.download('wordnet')
```

3. Zemberek kurulumu:
- Zemberek JAR dosyasının proje dizinine eklenmesi gerekmektedir.

## Kullanım

1. PySpark versiyonu için:
```python
from pyspark.sql import SparkSession
spark = SparkSession.builder \
    .master("local[4]") \
    .appName("multiclass") \
    .config("spark.executor.memory","4g") \
    .config("spark.driver.memory","2g") \
    .getOrCreate()
```

2. Python versiyonu için:
```python
from text_classification_colab import *
```

## Notlar

- Proje Google Colab üzerinde geliştirilmiştir
- Büyük veri setleri için PySpark versiyonu önerilmektedir
- Daha hızlı sonuçlar için Python versiyonu tercih edilebilir
- Türkçe metin işleme için Zemberek kütüphanesi kullanılmıştır

## Dosya Detayları

### PySpark Dosyaları

#### 1. PySpark-ile-cok-Sinifli-Metin-Siniflandirma.ipynb
- **Açıklama**: Ana PySpark sınıflandırma notebook'u
- **İçerik**:
  - Veri yükleme ve ön işleme
  - SparkSession konfigürasyonu
  - Metin tokenizasyonu
  - Özellik çıkarımı
  - Lojistik regresyon modeli
  - Model değerlendirme
- **Özellikler**:
  - 7 farklı kategori için sınıflandırma
  - Spark ML pipeline kullanımı
  - Performans metrikleri hesaplama

#### 2. pyspark.ipynb
- **Açıklama**: PySpark ile alternatif sınıflandırma yaklaşımı
- **İçerik**:
  - Farklı özellik çıkarım yöntemleri
  - Model optimizasyonu
  - Cross-validation
- **Özellikler**:
  - Daha detaylı veri analizi
  - Model karşılaştırmaları

#### 3. pyspark yeni.ipynb
- **Açıklama**: Güncellenmiş PySpark implementasyonu
- **İçerik**:
  - İyileştirilmiş ön işleme adımları
  - Yeni özellik mühendisliği
  - Model performans iyileştirmeleri

### Python Dosyaları

#### 1. text_classification_colab.py
- **Açıklama**: Ana Python sınıflandırma modülü
- **İçerik**:
  - Metin temizleme fonksiyonları
  - Zemberek entegrasyonu
  - Çoklu sınıflandırıcı implementasyonları
- **Özellikler**:
  - Türkçe metin işleme
  - Çoklu model desteği
  - Detaylı performans analizi

#### 2. text_classification_colab.ipynb
- **Açıklama**: Python sınıflandırma notebook'u
- **İçerik**:
  - Görselleştirmeler
  - Model eğitimi
  - Sonuç analizi
- **Özellikler**:
  - İnteraktif analiz
  - Görsel sonuçlar
  - Model karşılaştırmaları

#### 3. text classification.ipynb
- **Açıklama**: Alternatif Python sınıflandırma yaklaşımı
- **İçerik**:
  - Farklı özellik çıkarım yöntemleri
  - Model denemeleri
  - Sonuç değerlendirme

### Veri ve Yardımcı Dosyalar

#### 1. temiz_metin.txt
- **Açıklama**: Ön işlenmiş metin verileri
- **İçerik**:
  - Temizlenmiş metinler
  - Kategori etiketleri
- **Format**: Her satır bir metin örneği

#### 2. stopwords.txt
- **Açıklama**: Türkçe durdurma kelimeleri listesi
- **İçerik**:
  - Türkçe yaygın kelimeler
  - Gereksiz kelimeler
- **Kullanım**: Metin temizleme işlemlerinde

#### 3. stopwords-en.txt
- **Açıklama**: İngilizce durdurma kelimeleri listesi
- **İçerik**:
  - İngilizce yaygın kelimeler
  - Gereksiz kelimeler
- **Kullanım**: İngilizce metin işleme için

### Diğer Dosyalar

#### 1. result 1 deneme.ipynb
- **Açıklama**: Model sonuçlarının analizi
- **İçerik**:
  - Performans metrikleri
  - Karşılaştırmalı analizler
  - Sonuç görselleştirmeleri

#### 2. Untitled.ipynb ve Untitled1.ipynb
- **Açıklama**: Geçici deneme notebook'ları
- **İçerik**:
  - Kod denemeleri
  - Hızlı testler
  - Prototip implementasyonlar
