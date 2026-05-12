# Email Spam Sınıflandırması — İstatistiksel Analiz

**Veri Bilimi için İstatistik | Proje 2A**  
Mustafa Yiğit Genç | 250121047 | Fen Edebiyat Fakültesi — Yapay Zeka ve Makine Öğrenmesi Bölümü | 2025–2026 Bahar Dönemi

---

## Proje Açıklaması

Bu projede UCI Spambase veri seti (4601 email, 57 özellik) üzerinde istatistiksel analiz yapılmıştır. Her email bağımsız bir Bernoulli denemesi olarak modellenmiş; spam sayısı Binom dağılımıyla ifade edilmiştir. Gaussian Naive Bayes sınıflandırıcısının başarımı hipotez testleri ve 5-Fold Cross Validation ile istatistiksel olarak doğrulanmıştır.

**Araştırma Sorusu:** Bir email sınıflandırma modeli istatistiksel olarak şans seviyesinin anlamlı biçimde üzerinde performans gösterebilir mi?

---

## Teslim Edilen Dosyalar

| Dosya | Açıklama |
|-------|----------|
| `main_analysis.ipynb` | Tüm analizleri içeren çalıştırılmış Jupyter Notebook |
| `report.pdf` | 15 sayfalık PDF rapor (7 bölüm) |
| `README.md` | Bu dosya |
| `spambase.csv` | Kullanılan veri seti |
| `requirements.txt` | Gerekli Python kütüphaneleri |

---

## Veri Seti

- **Kaynak:** UCI Machine Learning Repository — Spambase (Cranor & LaMacchia, 1998)
- **Link:** https://archive.ics.uci.edu/ml/datasets/spambase
- **Boyut:** 4601 email, 57 özellik + 1 hedef değişken
- **Özellikler:** Kelime frekansları (48), karakter frekansları (6), büyük harf istatistikleri (3)
- **Hedef:** `spam` — 1 = spam, 0 = ham (spam değil)
- **Sınıf dağılımı:** %31 spam (1426), %69 ham (3175)

---

## Kullanılan Yöntemler

| Yöntem | Amaç |
|--------|------|
| Bernoulli Dağılımı | Her emaili bağımsız Bernoulli denemesi olarak modelleme |
| Binom Dağılımı | n email içindeki spam sayısını modelleme |
| MLE (Maksimum Olabilirlik) | p parametresinin tahmini |
| Merkezi Limit Teoremi | Binom → Normal yaklaşımı |
| Gaussian Naive Bayes | Spam sınıflandırması |
| Binom Testi | Accuracy > 0.5 hipotez testi (kesin) |
| Z-Testi | MLT yaklaşımı altında hipotez testi |
| Wilson Güven Aralığı | %95 güven aralığı hesabı |
| 5-Fold Cross Validation | Model stabilitesi ve MLT doğrulaması |
| Shapiro-Wilk Testi | CV skorlarının normalliği |

---

## Kurulum ve Çalıştırma

### 1. Gereksinimleri yükle

```bash
pip install -r requirements.txt
```

### 2. Notebook'u aç

```bash
jupyter notebook main_analysis.ipynb
```

### 3. Tüm hücreleri çalıştır

Jupyter'da: **Kernel → Restart & Run All**

---

## Özet Bulgular

| Metrik | Değer |
|--------|-------|
| Model | Gaussian Naive Bayes |
| Test Accuracy | 0.9099 |
| Precision (Spam) | 0.7837 |
| Recall (Spam) | 0.9789 |
| F1 Score (Spam) | 0.8705 |
| 5-Fold CV Ortalama | 0.9098 ± 0.0093 |
| Binom Testi p-değeri | 3.79e-158 → H0 reddedilir |
| %95 Güven Aralığı | [0.8896, 0.9267] |
| Shapiro-Wilk p | 0.4395 → MLT doğrulandı |
