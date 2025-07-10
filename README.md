
# Uçuş Gecikmeleri Analizi - Kapsamlı R Markdown Projesi
## Proje Başlığı
### Havalimanı Büyüklüğü, Mevsimsel Faktörler ve Uçuş Rotası Özelliklerinin Uçuş Gecikmeleri Üzerindeki Etkisinin İncelenmesi ve Bu Faktörler Arasındaki İlişkilerin Analizi


## Proje Özeti
Bu kapsamlı araştırma projesi, Amerika Birleşik Devletleri'ndeki iç hat uçuşlarında karşılaşılan gecikmelerin temel nedenlerini ve bu gecikmeleri tetikleyen çeşitli faktörleri R Markdown kullanarak analiz etmektedir. 2024 yılına ait 7.079.081 uçuş kaydı üzerinde gerçekleştirilen analizler, havacılık sektörü için kritik bulgular ortaya koymaktadır.

## İçindekiler
### Giriş

* Araştırmanın Amacı
* Veri Seti Tanıtımı
* Araştırma Soruları

### Veri Okuma ve Ön İşleme

* Kütüphanelerin Yüklenmesi
* Veri Okuma ve Birleştirme
* Değişken Açıklamaları
* Eksik Veri Analizi
* Veri Dönüşümleri
* Yeni Değişkenlerin Türetilmesi

### Analiz ve Görselleştirmeler (20 farklı analiz)

* Gecikme Kategorileri Analizi
* Havalimanı Büyüklüğü Etkisi
* Mevsimsel Analizler
* Tatil Günleri Etkisi
* Eyaletler Arası Rota Performansı
* Ve daha fazlası...
  
### Sonuçlar ve Gelecek Çalışmalar

## Veri Kaynağı
**Kaynak:** U.S. Department of Transportation - Bureau of Transportation Statistics (BTS) 

**Web Sitesi:** BTS On-Time Performance  [https://www.transtats.bts.gov/DL_SelectFields.aspx?gnoyr_VQ=FGJ&QO_fu146_anzr=b0-gvzr]

**Dönem:** 2024 yılı (12 aylık veri)

**Toplam Kayıt:** 7.079.081 uçuş

**Analiz Edilen Kayıt:** 6.965.267 uçuş (eksik veriler temizlendikten sonra)

## Kullanılan Teknolojiler ve Kütüphaneler

### R Paketleri
```r
library(tidyverse)   # Veri manipülasyonu
library(lubridate)   # Tarih işlemleri
library(scales)      # Ölçeklendirme
library(ggplot2)     # Veri görselleştirme
library(gridExtra)   # Çoklu grafik düzenleme
library(magrittr)    # Pipe operatörleri
library(bookdown)    # PDF rapor oluşturma
```

## Temel Değişkenler
* Zaman: YEAR, MONTH, FL_DATE
* Lokasyon: ORIGIN, DEST, ORIGIN_STATE_NM, DEST_STATE_NM
* Performans: DEP_DELAY, ARR_DELAY, CANCELLED
* Gecikme Nedenleri: CARRIER_DELAY, WEATHER_DELAY, NAS_DELAY, SECURITY_DELAY, LATE_AIRCRAFT_DELAY
* Türetilen: SEASON, WEEKDAY_WEEKEND, DISTANCE_CATEGORY, ORIGIN_SIZE, DELAY_REASON_STATUS

## Araştırma Soruları
* Havalimanı büyüklüğü uçuş gecikmelerini nasıl etkiler?
* Hangi mevsimde uçuş gecikmeleri daha fazla yaşanır?
* Kalkış ve varış gecikmeleri arasında ilişki var mıdır?
* Uçuş mesafesi gecikme süresini nasıl etkiler?
* Tatil günlerinde gecikme ve iptal oranları nasıl değişir?
* Hafta içi/hafta sonu gecikme oranları nelerdir?

## Analiz Metodolojisi
### Gecikme Sınıflandırması
Erken: <-15 dakika önce

Zamanında: ±15 dakika

Gecikmeli: >15 dakika sonra

Not: BTS standardına göre 15 dakika eşik değeri kullanılmıştır.

## İstatistiksel Testler
**Ki-kare Bağımsızlık Testi:** Kategorik değişkenler arası ilişki

**ANOVA:** Gruplar arası ortalama farkları

**Tukey HSD:** Çoklu karşılaştırma testleri

## Temel Bulgular
### 📊 Genel İstatistikler
Uçuşların %79.2'si kabul edilebilir zaman aralığında tamamlanmıştır

%20.8 oranında 15+ dakika gecikme yaşanmıştır

Sadece 2 uçuşta gecikme nedeni kaydedilmemiştir (veri kalitesi yüksek)

### ✈️ Gecikme Nedenleri Dağılımı
Geç Gelen Uçak: %40.4 (en büyük neden)

Havayolu Kaynaklı: %34.5

Ulusal Hava Sistemi: %18.9

Hava Durumu: %6.0

Güvenlik: %0.2

### 🏢 Havalimanı Büyüklüğü Etkisi
Büyük havalimanları: Daha yüksek gecikme oranı (%21+)

Küçük havalimanları: Daha uzun gecikme süresi (8.4 dk)

### 🌞 Mevsimsel Bulgular
Yaz: En yüksek gecikme (13.5 dk) ve iptal oranı (%2.09)

Sonbahar: En düşük gecikme (-0.2 dk)

Temmuz: Yılın en gecikmeli ayı (18.1 dk)

### 🎉 Tatil Günleri Etkisi
MLK Günü: %49.1 gecikme oranı (en yüksek)

Şükran Günü: %8 gecikme oranı (en düşük)

Tatil günlerinde iptal oranı %2.18'e yükseliyor

### 🗺️ En Problemli Rotalar
Wyoming → Texas: 51.9 dk ortalama gecikme

West Virginia → Florida: 42.1 dk

Puerto Rico ↔ Connecticut: ~30 dk (her iki yönde)

## Görselleştirmeler (20 Adet)
Proje, aşağıdaki görselleştirmeleri içermektedir:

Pasta grafikler (gecikme nedenleri)

Çubuk grafikler (mevsimsel karşılaştırmalar)

Isı haritası (kalkış-varış ilişkisi)

Çizgi grafikler (aylık trendler)

Gruplandırılmış grafikler (çoklu faktör analizi)

## Kurulum ve Çalıştırma

### Gereksinimler
R (≥ 4.0.0)

RStudio

LaTeX (PDF çıktısı için)

### Adımlar
Gerekli paketleri yükleyin:
```r
install.packages(c("tidyverse", "lubridate", "scales", 
                   "ggplot2", "gridExtra", "magrittr", "bookdown"))
```
Veri dosyalarını indirin ve doğru dizine yerleştirin:

```text
eda-sunum/
├── 01-T_ONTIME_REPORTING.csv
├── 02-T_ONTIME_REPORTING.csv
└── ... (12 aylık veri)
```
RMarkdown dosyasını çalıştırın:

```r
rmarkdown::render("flight_delay_analysis.Rmd")
```

Dosya Yapısı
```text
flight-delay-analysis/
│   README.md
│   flight_delay_analysis.Rmd
│   flight_delay_analysis.pdf
│   
└───eda-sunum/
    ├── 01-T_ONTIME_REPORTING.csv
    ├── 02-T_ONTIME_REPORTING.csv
    └── ... (12 aylık veri dosyaları)
```

## Gelecek Çalışmalar
**Çoklu Regresyon Analizi:** Faktörlerin birlikte etkisinin modellenmesi

**Makine Öğrenimi:** Gecikme tahmin modelleri (Random Forest, XGBoost)

**Gerçek Zamanlı Analiz:** Canlı veri entegrasyonu

**Coğrafi Görselleştirme:** İnteraktif haritalar

## Kaynaklar
Bureau of Transportation Statistics (BTS)

Airline On-Time Performance Data

US Federal Holidays 2024

Post-Hoc Testleri

## İletişim
Proje hakkında sorularınız için:

Yazar: Merve Çalışkan

(https://www.linkedin.com/in/mervecaliskann/)

## Lisans

Bu proje akademik amaçlar için hazırlanmıştır. Kaynak gösterilerek kullanılabilir.
