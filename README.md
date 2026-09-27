# 🧠 Derin Öğrenme ile Felç (Stroke) Riski Tahminleme Projesi

Bu proje, bireylerin demografik ve klinik sağlık verilerini analiz ederek, gelecekte felç (stroke) geçirme risklerini tahmin eden uçtan uca bir **Yapay Sinir Ağı (ANN)** modelidir.

## 🛠️ Kullanılan Teknolojiler ve Kütüphaneler
* **Veri Analizi & Ön İşleme:** Python, Pandas, NumPy
* **Veri Görselleştirme:** Matplotlib, Seaborn
* **Makine Öğrenmesi & Metrikler:** Scikit-Learn (StandardScaler, train_test_split, LabelEncoder)
* **Derin Öğrenme:** TensorFlow & Keras (Sequential, Dense, Dropout, EarlyStopping)

## 📊 Veri Seti ve Ön İşleme Adımları
Projede Kaggle üzerinde bulunan `healthcare-dataset-stroke-data.csv` veri seti kullanılmıştır (5110 satır, 12 sütun).
1. **Eksik Veri Yönetimi:** `bmi` sütunundaki eksik veriler, veri dağılımını bozmamak adına medyan (median) değeri ile doldurulmuştur.
2. **Kategorik Değişken Dönüşümü:** `gender`, `smoking_status`, `work_type` gibi kategorik veriler `pd.get_dummies` yöntemi kullanılarak One-Hot Encoding işlemine tabi tutulmuştur.
3. **Özellik Ölçeklendirme:** Yapay Sinir Ağlarının hızlı ve kararlı öğrenmesi için bağımsız değişkenler `StandardScaler` ile standartlaştırılmıştır.

## 🧠 Model Mimarisi (ANN)
Model, aşırı öğrenmeyi (overfitting) engellemek adına `Dropout` katmanlarıyla desteklenmiş ardışık bir yapay sinir ağıdır:
* **Giriş Katmanı + Gizli Katman 1:** 32 Nöron, Aktivasyon: ReLU, %30 Dropout [2]
* **Gizli Katman 2:** 16 Nöron, Aktivasyon: ReLU, %30 Dropout [2]
* **Çıkış Katmanı:** 1 Nöron, Aktivasyon: Sigmoid (İkili sınıflandırma riski tahmini için) [2]
* **Optimizasyon:** Adam Optimizer, Kayıp Fonksiyonu: Binary Crossentropy [2]

## 🎯 Dengesiz Veri (Imbalanced Data) Yaklaşımı & Başarı Metrikleri
Veri setinde felç geçiren hastaların oranı çok düşük olduğundan modelin "0" (Felç Geçirmeyen) sınıfına ezberlemesini engellemek için **Sınıf Ağırlıkları (Class Weights)** hesaplanmış ve `model.fit()` esnasında modele aktarılmıştır. Riskli hastaları kaçırmamak (Yüksek Recall) amacıyla sınıflandırma eskenar değeri (threshold) `0.15` olarak ayarlanmıştır.

**Test Seti Sonuçları:**
* **Doğruluk (Accuracy):** %62.72 [2]
* **Duyarlılık (Recall - Felçlileri Yakalama Oranı):** %84.00 🚀 *(Risk gruplarını yakalamada oldukça başarılı)* [2]
* **F1-Skoru:** 0.18 [2]
# 🧠 Derin Öğrenme ile Felç (Stroke) Riski Tahminleme Projesi

Bu proje, bireylerin demografik ve klinik sağlık verilerini analiz ederek, gelecekte felç (stroke) geçirme risklerini tahmin eden uçtan uca bir **Yapay Sinir Ağı (ANN)** modelidir.

## 🛠️ Kullanılan Teknolojiler ve Kütüphaneler
* **Veri Analizi & Ön İşleme:** Python, Pandas, NumPy
* **Veri Görselleştirme:** Matplotlib, Seaborn
* **Makine Öğrenmesi & Metrikler:** Scikit-Learn (StandardScaler, train_test_split, LabelEncoder)
* **Derin Öğrenme:** TensorFlow & Keras (Sequential, Dense, Dropout, EarlyStopping)

## 📊 Veri Seti ve Ön İşleme Adımları
Projede Kaggle üzerinde bulunan `healthcare-dataset-stroke-data.csv` veri seti kullanılmıştır (5110 satır, 12 sütun).
1. **Eksik Veri Yönetimi:** `bmi` sütunundaki eksik veriler, veri dağılımını bozmamak adına medyan (median) değeri ile doldurulmuştur.
2. **Kategorik Değişken Dönüşümü:** `gender`, `smoking_status`, `work_type` gibi kategorik veriler `pd.get_dummies` yöntemi kullanılarak One-Hot Encoding işlemine tabi tutulmuştur.
3. **Özellik Ölçeklendirme:** Yapay Sinir Ağlarının hızlı ve kararlı öğrenmesi için bağımsız değişkenler `StandardScaler` ile standartlaştırılmıştır.

## 🧠 Model Mimarisi (ANN)
Model, aşırı öğrenmeyi (overfitting) engellemek adına `Dropout` katmanlarıyla desteklenmiş ardışık bir yapay sinir ağıdır:
* **Giriş Katmanı + Gizli Katman 1:** 32 Nöron, Aktivasyon: ReLU, %30 Dropout [2]
* **Gizli Katman 2:** 16 Nöron, Aktivasyon: ReLU, %30 Dropout [2]
* **Çıkış Katmanı:** 1 Nöron, Aktivasyon: Sigmoid (İkili sınıflandırma riski tahmini için) [2]
* **Optimizasyon:** Adam Optimizer, Kayıp Fonksiyonu: Binary Crossentropy [2]

## 🎯 Dengesiz Veri (Imbalanced Data) Yaklaşımı & Başarı Metrikleri
Veri setinde felç geçiren hastaların oranı çok düşük olduğundan modelin "0" (Felç Geçirmeyen) sınıfına ezberlemesini engellemek için **Sınıf Ağırlıkları (Class Weights)** hesaplanmış ve `model.fit()` esnasında modele aktarılmıştır. Riskli hastaları kaçırmamak (Yüksek Recall) amacıyla sınıflandırma eskenar değeri (threshold) `0.15` olarak ayarlanmıştır.

**Test Seti Sonuçları:**
* **Doğruluk (Accuracy):** %62.72 [2]
* **Duyarlılık (Recall - Felçlileri Yakalama Oranı):** %84.00 🚀 *(Risk gruplarını yakalamada oldukça başarılı)* [2]
* **F1-Skoru:** 0.18 [2]
