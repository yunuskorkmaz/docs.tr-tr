---
title: Model Oluşturucu için yükleme eğitim verileri
description: ML.NET için Model Oluşturucu senaryolarından birinde kullanılmak üzere bir SQL Server veritabanından veya bir dosyadan eğitim verilerini nasıl yükleyin öğrenin.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 23de2d06090f4c1eaa2c79178ba4c346698d45e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849165"
---
# <a name="load-training-data-into-model-builder"></a>Eğitim verilerini Model Oluşturucu'ya yükleyin

ML.NET için Model Oluşturucu senaryolarından birinde kullanılmak üzere bir dosyadan veya SQL Server veritabanından eğitim veri kümelerinizi nasıl yükleyebilirsiniz öğrenin. Model Oluşturucu senaryoları, SQL Server veritabanlarını, görüntü dosyalarını ve CSV veya TSV dosya biçimlerini eğitim verileri olarak kullanabilir.

## <a name="training-dataset-limitations-in-model-builder"></a>Model Oluşturucu'da veri kümesi sınırlamalarını geliştirme

Model Oluşturucu, eğitim modelleri için kullanabileceğiniz veri miktarını ve türünü sınırlar:

- SQL Server verileri: 100.000 satır
- CSV ve TSV dosyaları: Boyut sınırı yok
- Görüntüler: Sadece PNG ve JPG.

## <a name="model-builder-scenarios"></a>Model Oluşturucu senaryoları

Model Oluşturucu, aşağıdaki makine öğrenimi senaryoları için modeller oluşturmanıza yardımcı olur:

- Duyarlılık analizi (ikili sınıflandırma): Metinsel verileri iki kategoriye ayırın.
- Sorun sınıflandırması (çok sınıflı sınıflandırma): Metin verilerini 3 veya daha fazla kategoriye ayırın.
- Fiyat tahmini (regresyon): Sayısal bir değeri tahmin edin.
- Görüntü sınıflandırması (derin öğrenme): Görüntüleri özelliklerine göre kategorilere ayırın.
- Özel senaryo: Regresyon, sınıflandırma ve diğer görevleri kullanarak verilerinizden özel senaryolar oluşturun.

Bu makalede, metinsel veya sayısal verilerle sınıflandırma ve regresyon senaryoları ve görüntü sınıflandırma senaryoları ele alınız.

## <a name="load-text-or-numeric-data-from-a-file"></a>Dosyadan metin veya sayısal veri yükleme

Bir dosyadaki metin veya sayısal verileri Model Oluşturucu'ya yükleyebilirsiniz. Virgülle sınırlandırılmış (CSV) veya sekme-sınırlandırma (TSV) dosya biçimlerini kabul eder.

1. Model Oluşturucu'nun veri adımında, veri kaynağı açılır tarafından **Dosya'yı** seçin.
2. Dosya metin kutusunu **seç'in** yanındaki düğmeyi seçin ve veri dosyasına göz atmak ve seçmek için Dosya Gezgini'ni kullanın.
3. **Sütunda Tahmin (Etiket)** açılır düşüşünü tahmin etmek için bir kategori seçin.
4. Giriş **Sütunları (Özellikler)** açılır düşüşünden, eklemek istediğiniz veri sütunlarının denetleniyi onaylayın.

Model Oluşturucu için veri kaynağı dosyanızı ayarlamayı bitirdiniz. Model Oluşturucu'da bir sonraki adıma geçmek için **Tren** bağlantısını seçin.

## <a name="load-data-from-a-sql-server-database"></a>SQL Server veritabanından veri yükleme

Model Oluşturucu, yerel ve uzak SQL Server veritabanlarından veri yüklemeyi destekler.

SQL Server veritabanından Modül Oluşturucu'ya veri yüklemek için:

1. Model Oluşturucu'nun veri adımında, veri kaynağı açılır tarafından **SQL Server'ı** seçin.
1. **SQL Server veritabanına bağlan** metin kutusunun yanındaki düğmeyi seçin.
    1. Veri **Seç** iletişim kutusunda **Microsoft SQL Server Database File'yi**seçin.
    1. **Her Zaman bu seçim** onay kutusunu kullan denetiminden kaldırın ve Devam **et'i** seçin
    1. Bağlantı **Özellikleri** iletişim kutusunda **Gözat'ı** seçin ve indirilenleri seçin. MDF dosyası.
    1. **Tamam'ı** seçin
1. **Tablo Adı** açılır toplantısından veri kümesi adını seçin.
1. **Sütundan Tahmin (Etiket)** açılır goluna kadar, tahmin de bulunmak istediğiniz veri kategorisini seçin.
1. Giriş **Sütunları (Özellikler)** açılır düşüşünden, eklemek istediğiniz sütunların kontrol edildiğini onaylayın.

Model Oluşturucu için veri kaynağı dosyanızı ayarlamayı bitirdiniz. Model Oluşturucu'da bir sonraki adıma geçmek için **Tren** bağlantısını seçin.

## <a name="set-up-image-data-files"></a>Görüntü veri dosyalarını ayarlama

Model Builder, görüntü verilerinin sınıflandırma kategorilerine karşılık gelen klasörlerde düzenlenmiş JPG veya PNG dosyaları olmasını bekler.

Görüntüleri Model Oluşturucu'ya yüklemek için, tek bir üst düzey dizin için yol sağlayın:

- Bu üst düzey dizin, her kategoriiçin tahmin etmek için bir alt klasör içerir.
- Her alt klasör kendi kategorisine ait resim dosyalarını içerir.

Aşağıda gösterilen klasör yapısında, üst düzey dizin *flower_photos.* Tahmin etmek istediğiniz kategorilere karşılık gelen beş alt dizin vardır: papatya, karahindiba, gül, ayçiçeği ve lale. Bu alt dizinlerin her biri kendi kategorisine ait görüntüler içerir.

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

Model Builder ile makine öğrenimi uygulamaları oluşturmak için aşağıdaki öğreticileri izleyin:

- [Gerileme kullanarak fiyatları tahmin edin](../tutorials/predict-prices-with-model-builder.md)
- [İkili sınıflandırmayı kullanarak bir web uygulamasında ki duyarlılığı analiz edin](../tutorials/sentiment-analysis-model-builder.md )

Kodu kullanarak bir modeli eğittiyseniz, [ML.NET API'yi kullanarak verileri nasıl yükleyeceğimiz öğrenin.](load-data-ml-net.md)
