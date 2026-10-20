# 🧬 Protein Classification with Machine Learning

Protein amino asit dizilimlerinden (sequence) proteinin hangi biyolojik aileye ait olduğunu tahmin eden bir makine öğrenmesi projesi.

## 📊 Veri Seti

- **Kaynak:** [Kaggle - Protein Data Set (RCSB PDB)](https://www.kaggle.com/datasets/shahir/protein-data-set)
- **Dosyalar:** `pdb_data_no_dups.csv` + `pdb_data_seq.csv` → `structureId` üzerinden birleştirildi
- **Toplam Veri:** ~346.000 protein kaydı
- **Analiz Edilen Veri:** ~188.000 kayıt (en yaygın 10 protein sınıfı)

> ⚠️ Veri dosyaları boyut nedeniyle repoya dahil edilmemiştir. Yukarıdaki Kaggle linkinden indirilebilir.

## 🎯 Hedef

Proteinin `classification` sütunundaki biyolojik ailesini tahmin etmek:

| Sınıf | Açıklama |
|---|---|
| HYDROLASE | Hidrolaz enzimleri |
| TRANSFERASE | Transferaz enzimleri |
| OXIDOREDUCTASE | Oksidoredüktaz enzimleri |
| IMMUNE SYSTEM | Bağışıklık sistemi proteinleri |
| LYASE | Liyaz enzimleri |
| HYDROLASE/HYDROLASE INHIBITOR | Hidrolaz inhibitörleri |
| TRANSCRIPTION | Transkripsiyon faktörleri |
| VIRAL PROTEIN | Viral proteinler |
| TRANSPORT PROTEIN | Taşıyıcı proteinler |
| VIRUS | Virüs proteinleri |

## ⚙️ Yöntem

### 1. Veri Ön İşleme
- İki CSV dosyası `structureId` üzerinden birleştirildi
- Eksik değerler temizlendi
- Sadece protein türündeki kayıtlar filtrelendi
- En yaygın 10 sınıf seçildi

### 2. Özellik Çıkarımı — K-mer Tekniği
Protein dizilimleri **3'lü K-mer** (tri-peptide) yöntemiyle parçalandı:

```
AALKDQL... → AAL ALK LKD KDQ DQL ...
```

Bu sayede her protein, makine öğrenmesi modeline verilebilecek bir **kelime vektörüne** dönüştürüldü.

### 3. Model — LinearSVC (TF-IDF + SVM)
- `CountVectorizer` ile K-mer'ler sayısallaştırıldı
- `TfidfTransformer` ile TF-IDF ağırlıkları hesaplandı
- `LinearSVC` ile sınıflandırma yapıldı

## 📈 Sonuçlar

Model, 10 farklı protein sınıfını başarıyla ayırt edebilmektedir. Detaylı metrikler ve karmaşıklık matrisi (confusion matrix) notebook içinde yer almaktadır.

## 🚀 Kurulum & Çalıştırma

```bash
# Gerekli kütüphaneleri yükle
pip install pandas numpy matplotlib seaborn scikit-learn jupyter

# Veri setini Kaggle'dan indir ve proje klasörüne koy:
# - pdb_data_no_dups.csv
# - pdb_data_seq.csv

# Notebook'u çalıştır
jupyter notebook protein_classification.ipynb
```

## 🛠️ Kullanılan Teknolojiler

- **Python** — Ana programlama dili
- **Pandas / NumPy** — Veri işleme
- **Matplotlib / Seaborn** — Veri görselleştirme
- **Scikit-learn** — Makine öğrenmesi (CountVectorizer, TfidfTransformer, LinearSVC)
- **Jupyter Notebook** — Geliştirme ortamı

## 👤 Yazar

**Alper Saygın Etci**
