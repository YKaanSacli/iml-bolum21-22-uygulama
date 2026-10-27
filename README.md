# 🔍 Özellik Etkileşimi (Bölüm 21) ve Fonksiyonel Ayrıştırma (Bölüm 22) — İnteraktif Türkçe Uygulama

**Hazırlayan:** Yusuf Kaan Saçlı (20269258011)
**Ders:** Açıklanabilir Yapay Zekâ (XAI), 2026 Güz
**Canlı uygulama:** https://iml-bolum21-22-uygulama.streamlit.app/
**Kaynak kod deposu:** https://github.com/YKaanSacli/iml-bolum21-22-uygulama

---

## 1. Bu uygulama nedir?

Bu uygulama, Christoph Molnar'ın **"Interpretable Machine Learning"** kitabının iki bölümünü tarayıcıda deneyerek öğrenmenizi sağlar:

- **Bölüm 21: Özellik Etkileşimi (Feature Interaction)**
- **Bölüm 22: Fonksiyonel Ayrıştırma (Functional Decomposition)**

Makine öğrenmesi, istatistik ya da programlama bilmeyen biri bile kaydırıcıları oynatarak, grafikleri açıp kapatarak ve her grafiğin altındaki Türkçe yorumları okuyarak konuyu kavrayabilir.

Tüm hesaplamalar (Friedman'ın H-istatistiği, 1B/2B Kısmi Bağımlılık, 1B/2B ALE ve Fonksiyonel ANOVA) hazır bir pakete bağlı kalmadan, mantığı açıkça görülebilsin diye saf **numpy** ile yazılmıştır. Uygulama çalışırken **internet bağlantısı gerektirmez**.

Bu uygulama **tek bir Streamlit uygulamasıdır**: iki bölüm arasında ekranın üstündeki yatay gezinti çubuğundan geçiş yapılır. Aynı uygulama, hocanın klasör düzeni gereği hem `21_feature-interaction/uygulama/` hem de `22_functional-decomposition/uygulama/` klasörlerinde bulunur. İki klasördeki dosyalar birebir aynıdır.

---

## 2. Uygulamayı hemen denemek istiyorsanız (kurulum gerekmez)

Tarayıcıdan şu adrese gidin:

👉 **https://iml-bolum21-22-uygulama.streamlit.app/**

Uygulama bir süre kullanılmazsa "uykuya" geçebilir. Açılışta **"Yes, get this app back up!"** düğmesi çıkarsa tıklayın, 1 dakika içinde açılır.

---

## 3. Kendi bilgisayarınıza kurmak (Windows, adım adım)

Hiç kurulum bilgisi gerekmez, adımları sırayla izleyin.

### Adım 1: Python kurulu mu kontrol edin
1. Klavyede **Windows Tuşu + R**'ye basın, açılan kutuya `cmd` yazıp **Enter**'a basın.
2. Siyah ekrana `python --version` yazıp **Enter**'a basın.
3. `Python 3.10.x` veya daha yeni bir sürüm yazıyorsa **Adım 2'ye** geçin.
4. Hata alırsanız (`'python' is not recognized...`) https://www.python.org/downloads/ adresinden Python'u indirin. Kurulum ekranının en altındaki **"Add Python to PATH"** kutucuğunu **mutlaka işaretleyin** ve **"Install Now"**'a tıklayın. Sonra CMD'yi kapatıp yenisini açın ve `python --version` komutunu tekrar deneyin.

### Adım 2: Dosyaları bilgisayarınıza alın
1. Bu klasörün (veya https://github.com/YKaanSacli/iml-bolum21-22-uygulama deposunun) dosyalarını indirin: sayfadaki yeşil **Code** düğmesi > **Download ZIP**.
2. ZIP'i bir klasöre çıkarın (örneğin `C:\uygulama`). Klasörün içinde `main.py`, `requirements.txt` ve `penguins.csv` dosyaları görünmelidir.

### Adım 3: Klasörde CMD açın
1. Dosya Gezgini'nde klasörün içine girin.
2. Üstteki **adres çubuğuna** tıklayın, yazıları silip `cmd` yazın ve **Enter**'a basın.
3. Siyah pencerede satır `C:\...\uygulama>` ile bitiyorsa doğru yerdesiniz.

### Adım 4: Sanal ortam oluşturun (önerilir)
Sırayla şu iki komutu yazın (her birinden sonra Enter):

```
python -m venv .venv
.venv\Scripts\activate
```

Satırın başında `(.venv)` yazısı çıkarsa başarılıdır.

### Adım 5: Gerekli paketleri kurun
```
pip install -r requirements.txt
```
Bu işlem internet hızınıza göre 1-5 dakika sürer.

### Adım 6: Uygulamayı başlatın
```
streamlit run main.py
```
Birkaç saniye sonra tarayıcınız otomatik açılır. Açılmazsa adres çubuğuna şunu yazın:

```
http://localhost:8501
```

### Uygulamayı kapatmak
CMD penceresine tıklayıp **Ctrl + C**'ye basın.

### Bir sonraki sefer
Sadece klasörde CMD açıp şu iki komutu yazmanız yeterlidir:

```
.venv\Scripts\activate
streamlit run main.py
```

> **macOS / Linux:** Adım 4'te `source .venv/bin/activate` komutunu, adım 1'de `python3 --version` komutunu kullanın. Diğer adımlar aynıdır.

---

## 4. Sık karşılaşılan hatalar ve çözümleri

| Hata | Çözüm |
|---|---|
| `'python' is not recognized` | Python'u kurarken "Add Python to PATH" işaretlenmemiştir. Python'u kaldırıp tekrar kurun ya da kurulumu "Modify" ile onarın. |
| `'streamlit' is not recognized` | Sanal ortam aktif değil. `.venv\Scripts\activate` komutunu çalıştırın ya da `python -m streamlit run main.py` yazın. |
| `ModuleNotFoundError: No module named ...` | Paketler kurulmamıştır. `pip install -r requirements.txt` komutunu çalıştırın. |
| `Port 8501 is already in use` | Uygulama zaten açık. Eski CMD penceresini kapatın ya da `streamlit run main.py --server.port 8502` yazın. |
| `Cannot be loaded because running scripts is disabled` | PowerShell kullanıyorsunuz. CMD (siyah pencere) kullanın ya da `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` komutuyla izin verin. |
| Tarayıcı açılmıyor | Adres çubuğuna `http://localhost:8501` yazın. |
| `penguins.csv` bulunamadı | `main.py` ile `penguins.csv` aynı klasörde olmalıdır. |
| Hesaplama yavaş | Penguen ve H-istatistiği sayfalarındaki **örneklem boyutu** kaydırıcısını küçültün (varsayılan 200). |
| Grafikler boş/hatalı görünüyor | Sayfayı yenileyin (F5). Sorun sürerse CMD'deki hata satırını okuyun. |

---

## 5. Sayfalar ve kitaptaki karşılıkları

Ekranın üstündeki gezinti çubuğundan **Ana Sayfa**, **Bölüm 21**, **Bölüm 22** ve **Kaynaklar** arasında geçiş yapılır. Her bölümün alt konuları ikinci seviye sekmelerdir.

### Ana Sayfa
Uygulamanın ne işe yaradığını, iki bölümün haritasını ve önerilen gezinti sırasını gösterir.

### Bölüm 21: Özellik Etkileşimi
| Sekme | Ne yapar? | Kitap karşılığı |
|---|---|---|
| **Etkileşim nedir?** | Ev fiyatı örneğiyle (konum x büyüklük) etkileşimin ne demek olduğunu gösterir. Kaydırıcılarla etkileri değiştirirsiniz, tablo ve grafik anında güncellenir. Çizgiler paralelse etkileşim yoktur. | Bölüm 21, "Özellik etkileşimleri nedir?" |
| **H-istatistiği adım adım** | Friedman'ın H-istatistiğini canlı hesaplar. Etkileşim gücünü artırdıkça H'nin nasıl büyüdüğünü, örneklem boyutunun sonucu nasıl kararsızlaştırdığını gösterir. | Bölüm 21, "Friedman'ın H-istatistiği" |
| **Penguen uygulaması** | Penguen cinsiyetini tahmin eden bir model kurar ve hangi özelliklerin birbiriyle etkileşime girdiğini H-istatistiğiyle ölçer. Model seçebilirsiniz. | Bölüm 21, "Örnekler" |
| **Kendi verinle dene** | Hazır bir veri seti seçer ya da kendi CSV dosyanızı yükleyerek en güçlü etkileşimleri bulur. | Bölüm 21 (uygulama) |
| **Mini sınav** | Bölüm 21'den çoktan seçmeli sorular, anında geri bildirim. | Bölüm 21 |

### Bölüm 22: Fonksiyonel Ayrıştırma
| Sekme | Ne yapar? | Kitap karşılığı |
|---|---|---|
| **Bileşenlerin tanımı** | Bir tahmin fonksiyonunu kesişim, ana etkiler ve etkileşim bileşenlerine ayırır. Bileşenleri tek tek açıp kapatarak toplamın gerçek fonksiyonla örtüştüğünü görürsünüz. | Bölüm 22, "Bir fonksiyonun ayrıştırılması" |
| **Benzersizlik ve fonksiyonel ANOVA** | Kısıt olmadan ayrıştırmanın neden benzersiz olmadığını gösterir. Fonksiyonel ANOVA'nın üç aksiyomunu (sıfır ortalama, diklik, varyans ayrıştırması) sayısal olarak sınar. | Bölüm 22, "Fonksiyonel ANOVA" |
| **ALE ve PDP karşılaştırması** | Kısmi bağımlılık ve birikimli yerel etkileri yan yana çizer. Korelasyonlu özelliklerde PDP'nin neden yanıltıcı olduğunu gösterir. | Bölüm 22, "Birikimli Yerel Etkiler" |
| **Mini sınav** | Bölüm 22'den çoktan seçmeli sorular. | Bölüm 22 |

### Kaynaklar
Terimlerin İngilizce-Türkçe sözlüğü, kaynakça ve lisans bilgisi.

---

## 6. Uygulama nasıl kullanılır?

1. Ekranın üstündeki gezinti çubuğundan bir bölüm seçin (önce **Ana Sayfa**'dan başlamanız önerilir).
2. Bölümün içindeki sekmelere sırayla bakın. Her sekmede şu üç kutu bulunur:
   - **Basit anlatım:** Konuyu sade bir dille anlatır.
   - **Kitapta ne diyor?:** Bölüm numarasıyla kitaptaki karşılığını gösterir.
   - **Bu grafik ne diyor?:** Açtığınızda grafiği adım adım yorumlar.
3. Sol kenar çubuğundaki **kaydırıcılar, model seçimi ve örneklem boyutu** ile deney yapın. Sonuçlar anında güncellenir.
4. Her sekmenin sonundaki "dene" önerilerini uygulayın (örneğin "etkileşimi 0 yap, çizgilere ne oldu?").
5. Son olarak **Mini sınav** ile öğrendiklerinizi sınayın.

> **Not:** Kitapta bulunmayan örnekler ve ek anlatımlar **"Ek örnek (kitapta yok)"** etiketiyle ayrıca işaretlenmiştir.

---

## 7. Dosya yapısı

```
uygulama/
├── main.py            # Uygulamanın tamamı (giriş noktası)
├── requirements.txt   # Gerekli Python paketleri
├── penguins.csv       # Penguen veri seti (internet gerekmez)
└── README.md          # Bu dosya
```

---

## 8. Kullanılan kütüphaneler

Güncel paket ve sürüm listesi için `requirements.txt` dosyasına bakın. Temel olarak: `streamlit`, `numpy`, `pandas`, `scikit-learn` ve grafik kütüphanesi (`matplotlib` veya `plotly`).

H-istatistiği, kısmi bağımlılık (PD), birikimli yerel etkiler (ALE) ve fonksiyonel ANOVA hesapları hazır bir XAI paketi kullanılmadan **doğrudan numpy ile** yazılmıştır.

---

## 9. İnternette yayınlama (isteğe bağlı)

Uygulama [Streamlit Community Cloud](https://streamlit.io/cloud) üzerinde ücretsiz yayınlanmıştır:

1. Kodu bir GitHub deposuna yükleyin (`main.py`, `requirements.txt`, `penguins.csv`).
2. https://share.streamlit.io adresine GitHub hesabınızla girin.
3. **Create app** düğmesine basın, deponuzu ve `main.py` dosyasını seçin.
4. **Deploy** düğmesine tıklayın. Birkaç dakika sonra herkese açık bir bağlantınız olur.

---

## 10. Lisans ve atıf

- Konuların anlatımı, kavramlar ve örnekler Christoph Molnar'ın **[Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/)** kitabına dayanır ve **CC BY-NC-SA 4.0** lisansı altındadır. Bu uygulama ticari olmayan eğitim amaçlı hazırlanmıştır ve aynı lisansla paylaşılmaktadır.
- Uygulama kodu bağımsız olarak yazılmış olup depo kökündeki lisans dosyasına tabidir.

### Kaynakça
- Molnar, C. (2022). *Interpretable Machine Learning: A Guide for Making Black Box Models Explainable.*
- Friedman, J. H., & Popescu, B. E. (2008). Predictive learning via rule ensembles. *The Annals of Applied Statistics, 2*(3), 916–954.
- Hooker, G. (2004). Discovering additive structure in black box functions. *KDD*, 575–580.
- Hooker, G. (2007). Generalized functional ANOVA diagnostics for high-dimensional functions of dependent variables. *Journal of Computational and Graphical Statistics, 16*(3), 709–732.
- Apley, D. W., & Zhu, J. (2020). Visualizing the effects of predictor variables in black box supervised learning models. *JRSS-B, 82*(4), 1059–1086.

---

**Hazırlayan:** Yusuf Kaan Saçlı · 2026 Güz · Açıklanabilir Yapay Zekâ Dersi
