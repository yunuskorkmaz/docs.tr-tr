---
title: Model Oluşturucu için eğitim verilerini yükleme
description: ML.NET için model Oluşturucu senaryolarından birinde kullanılmak üzere bir SQL Server veritabanından veya bir dosyadan eğitim verileri yüklemeyi öğrenin.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 47dd32d18d00c33bcf51aa0ea3be8b22494ebc5f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041277"
---
# <a name="load-training-data-into-model-builder"></a>Eğitim verilerini model Oluşturucu 'ya yükleme

Eğitim veri kümelerinizi bir dosya veya SQL Server veritabanından, ML.NET için model Oluşturucu senaryolarından birinde kullanmak üzere nasıl yükleyeceğinizi öğrenin. Model Oluşturucu senaryoları, eğitim verileri olarak SQL Server veritabanlarını, görüntü dosyalarını ve CSV 'yi ya da TSV dosya biçimlerini kullanabilir.

## <a name="training-dataset-limitations-in-model-builder"></a>Model Oluşturucu 'da eğitim veri kümesi sınırlamaları

Model Oluşturucu, eğitim modelleri için kullanabileceğiniz veri miktarını ve türünü sınırlar:

- SQL Server verileri: 100.000 satır 
- CSV ve TSV dosyaları: boyut sınırı yok
- Görüntüler: yalnızca PNG ve JPG.

## <a name="model-builder-scenarios"></a>Model Oluşturucu senaryoları 

Model Oluşturucu aşağıdaki makine öğrenimi senaryoları için modeller oluşturmanıza yardımcı olur:

- Yaklaşım Analizi (ikili sınıflandırma): metinsel verileri iki kategoride sınıflandırın.
- Sorun sınıflandırması (birden çok Lass sınıflandırması): metinsel verileri 3 veya daha fazla kategoride sınıflandırın.
- Fiyat tahmini (gerileme): sayısal bir değer tahmin edin.
- Görüntü sınıflandırması (derin öğrenme): görüntüleri özelliklere göre kategorilere ayırın.
- Özel senaryo: gerileme, sınıflandırma ve diğer görevleri kullanarak verilerinize özel senaryolar oluşturun.

Bu makale, metin veya sayısal verilerle sınıflandırma ve regresyon senaryolarına ve görüntü sınıflandırma senaryolarıyla birlikte ele alınmaktadır. 

## <a name="load-text-or-numeric-data-from-a-file"></a>Dosyadan metin veya sayısal veri yükleme  

Bir dosyadaki metin veya sayısal verileri model Oluşturucu 'ya yükleyebilirsiniz. Virgülle ayrılmış (CSV) veya sekmeyle ayrılmış (TSV) dosya biçimlerini kabul eder. 

1. Model oluşturucunun veri adımında, veri kaynağı açılır listesinden **Dosya** ' yı seçin.
2. **Dosya seçin** metin kutusunun yanındaki düğmeyi seçin ve veri dosyasına gidip seçmek Için dosya Gezgini 'ni kullanın.
3. **Tahmin edilecek sütun (etiket)** açılan listesinden bir kategori seçin.
4. **Giriş sütunları (Özellikler)** açılır listesinden, dahil etmek istediğiniz veri sütunlarının denetlenmesini onaylayın.

Model Oluşturucu için veri kaynağı dosyanızı ayarlamayı tamamladınız. Model Oluşturucu 'daki sonraki adıma geçmek için **eğitme** bağlantısını seçin.

## <a name="load-data-from-a-sql-server-database"></a>SQL Server veritabanından veri yükleme

Model Oluşturucu, yerel ve uzak SQL Server veritabanlarından veri yüklenmesini destekler.

SQL Server veritabanından modül Oluşturucusu 'na veri yüklemek için:

1. Model oluşturucunun veri adımında, veri kaynağı açılır listesinden **SQL Server** ' yi seçin.
1. **SQL Server veritabanına Bağlan** metin kutusunun yanındaki düğmeyi seçin.
    1. **Veri Seç** iletişim kutusunda **Microsoft SQL Server veritabanı dosyası**' nı seçin. 
    1. **Her zaman bu seçimi kullan** onay kutusunu temizleyin ve **devam** ' ı seçin.
    1. **Bağlantı özellikleri** iletişim kutusunda, **Araştır** ' ı seçin ve indirilen ' u seçin. MDF dosyası.
    1. **Tamam 'ı** seçin
1. **Tablo adı** açılan listesinden veri kümesi adını seçin.
1. **Sütunun tahmin edilmesi için (etiket)** aşağı açılan listesinden tahmin yapmak istediğiniz veri kategorisini seçin.
1. **Giriş sütunları (Özellikler)** açılır listesinden, dahil etmek istediğiniz sütunları onaylayın. 

Model Oluşturucu için veri kaynağı dosyanızı ayarlamayı tamamladınız. Model Oluşturucu 'daki sonraki adıma geçmek için **eğitme** bağlantısını seçin.

## <a name="set-up-image-data-files"></a>Görüntü veri dosyalarını ayarlama

Model Oluşturucu, sınıflandırma kategorilerine karşılık gelen klasörlerde görüntü verilerinin JPG veya PNG dosyaları olmasını bekler. 

Model Oluşturucusu 'na görüntü yüklemek için, tek bir üst düzey dizinin yolunu belirtin:

- Bu üst düzey dizin, tahmin edilecek kategorilerin her biri için bir alt klasör içerir. 
- Her alt klasör, kategorisine ait olan resim dosyalarını içerir. 
 
Aşağıda gösterilen klasör yapısında, en üst düzey dizin *flower_photos*' dir. Tahmin etmek istediğiniz kategorilere karşılık gelen beş alt dizin vardır: daya, Dandelion, Roses, sunçiçekler ve TULIP. Bu alt dizinlerin her biri ilgili kategorisine ait resimleri içerir. 

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |       
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |       
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |       
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |       
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg  
```

## <a name="next-steps"></a>Sonraki adımlar
Model Oluşturucu ile makine öğrenimi uygulamaları oluşturmak için bu öğreticileri izleyin:

- [Gerileme kullanarak fiyatları tahmin etme](../tutorials/predict-prices-with-model-builder.md)
- [İkili sınıflandırma kullanarak bir Web uygulamasındaki yaklaşımı çözümleme](../tutorials/sentiment-analysis-model-builder.md )

Kodu kullanarak bir modele eğitim yapıyorsanız, [ml.NET API 'sini kullanarak nasıl veri yükleneceğini öğrenin](load-data-ml-net.md).
