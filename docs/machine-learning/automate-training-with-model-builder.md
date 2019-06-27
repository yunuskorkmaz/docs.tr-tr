---
title: Model Oluşturucu nedir ve nasıl çalışır?
description: ML.NET Model Oluşturucu otomatik olarak makine öğrenme modeli eğitmek için kullanma
author: natke
ms.date: 06/26/2019
ms.custom: overview
ms.openlocfilehash: 6f5bbe3c389e3ca42550a48ef3e6edbc963ac2e9
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410658"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Model Oluşturucu nedir ve nasıl çalışır?

ML.NET Model Oluşturucu oluşturmak, eğitmek ve özel makine öğrenimi modellerini dağıtmak için bir kolayca anlaşılır grafik Visual Studio uzantısıdır. 

Model oluşturucu farklı makine öğrenimi algoritmaları ve ayarları senaryonuza en uygun olanı bulmanıza yardımcı olmak için keşfetmek için otomatik machine learning (AutoML) kullanır.

Model Oluşturucu kullanmak için machine learning uzmanlık gerekmez. Tek ihtiyacınız olan bazı veriler ve bir sorunu çözmek için. Model Oluşturucu model .NET uygulamanıza eklemek için kod oluşturur.

![Model Oluşturucu Visual Studio uzantısı kullanıcı arabirimi animasyon](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Model Oluşturucu şu anda Önizleme aşamasındadır.

## <a name="scenarios"></a>Senaryolar

Bir machine learning modeli için uygulamanızı oluşturmak için Model Oluşturucu, birçok farklı senaryo getirebilirsiniz.

Verilerinizde yapmak istediğiniz tahmin türü açıklaması bir senaryodur. Örneğin:
- gelecekteki ürün satış hacmini geçmiş satış verilerini temel alarak tahmin etme
- Müşteri değerlendirmeleri bağlı olarak olumlu veya olumsuz yaklaşımları sınıflandırma
- bankacılık işlem sahte olup olmadığını Algıla
- Şirketinizdeki doğru takım rota müşteri geri bildirim sorunları

Model Oluşturucu'da senaryonuz üzerine eşlemek gereken bir [ML.NET görev](resources/tasks.md). Model Oluşturucu için kullanabileceğiniz **regresyon** (tahmin etme numaraları) ve **sınıflandırma** (kategorileri tahmin).

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Hangi machine learning senaryo bana uygundur?

Model Oluşturucu, yaklaşım analizi, sorun sınıflandırmasını, fiyat tahmini ve özel senaryolarına yönelik şablonlarla birlikte gelir. Bu şablonlar, belirli ML.NET senaryonuz için başlangıç noktası olarak kullanılabilir.

#### <a name="sentiment-analysis-binary-classification"></a>Yaklaşım analizi (ikili sınıflandırma)

Yaklaşım analizi, müşteri geri bildirimlerinden pozitif veya negatif yaklaşım tahmin etmek için kullanılabilir. İkili sınıflandırma görevi örneğidir.

İkili sınıflandırma iki sınıflara verileri sınıflandırmak için kullanılır (Evet/Hayır; geçer/başarısız, doğru/yanlış; olumlu/olumsuz). Soruları cevaplamak için kullanılabilir:

- Bu e-posta istenmeyen posta var mı? (istenmeyen posta algılama)
- Hangi başvuran üyeliğine uygun olabilir? (uygulama filtreleme)
- Hangi hesapların faturalarını zamanında ödeme yapabilir değil mi? (risk azaltma)
- Bu kredi kartı işlem sahte mi? (sahtekarlık algılama)

Sınıflandırma iki kategoriye senaryonuz gerektiriyorsa, bu şablonu kendi kümesiyle kullanabilirsiniz.
 
#### <a name="issue-classification-multiclass-classification"></a>Sorun sınıflandırması (çok sınıflı sınıflandırma)

Sorun sınıflandırması, müşteri geri bildirimi (örneğin GitHub) sorunları sorun başlığı ve açıklamayı kullanarak kategorilere ayırmak için kullanılabilir. Bu, çok sınıflı sınıflandırma görevi örneğidir.

Sınıflı sınıflandırma üç veya daha fazla sınıflara verileri kategorilere ayırmak için kullanılabilir. Soruları cevaplamak için kullanılabilir:

- Bölümü için bir destek bileti miyim yönlendirmek? (bilet yönlendirme desteği)
- Bir müşteri sorunu önceliğini nedir? (müşteri sorunu öncelik)
- Bir ürün için hangi kategoriye ait? (ürün sınıflandırma)
- Belgenin türü nedir? (belge/e-posta sınıflandırma)

Üç veya daha fazla kategoriye verileri kategorilere ayırmak istiyorsanız, sorunu sınıflandırma şablonu senaryonuz için kullanabilirsiniz.

#### <a name="price-prediction-regression"></a>Fiyat tahmini (gerileme)

Fiyat tahmini, konum, boyut ve evi diğer özelliklerini kullanarak merkezi fiyatlarını tahmin etmek için kullanılabilir. Regresyon görev örneğidir.

Sayı tahmin etmek için regresyon kullanılır. Soruları cevaplamak için kullanılabilir:

- Hangi fiyat için bir ev satılsın mı? (Fiyat tahmini)
- Ne kadar süre sonra bakım mekanik parçası gerekiyor mu? (Tahmine dayalı bakım)
- Bu kurutma makinesi nem içeriği nedir? (makine izleme)
- Ne bu bölge için toplam Yıllık satış olacaktır? (satış tahmini)

Kendi veri kümesiyle bir sayısal değer tahmin etmek istiyorsanız, senaryonuz için fiyat tahmini şablonu kullanabilirsiniz.

#### <a name="custom-scenario-choose-your-task"></a>Özel bir senaryo (göreviniz seçin)

Özel bir senaryo, kendi görev seçmenize olanak sağlar. Sorununuz için en anlamlı senaryo seçin.

Özel bir senaryo, görev kendi makine öğrenimi seçmenize olanak sağlar. Önceki şablonlarda, makine öğrenimi görev senaryoya düzeltildi: ikili Sınıflandırma, çok sınıflı sınıflandırma veya regresyon. Bu şablonda, verilerinizde kullanmak istediğiniz ML görev seçebilirsiniz.

## <a name="data"></a>Veri

Bir kez senaryonuz bir görev üzerine eşlediğiniz, Model Oluşturucu, bir veri kümesi sağlamak ister. Veri eğitmek, değerlendirin ve senaryonuz için en iyi modeli seçmek için kullanılır. Ayrıca tahmin etmek istediğiniz çıkış seçmeniz gerekebilir.

### <a name="choose-the-output-to-predict-label"></a>(Etiketi) tahmin etmek için bir çıkış seçin

Bir veri kümesi, eğitim örneklerin satır ve sütunları özniteliklerinin bir tablodur. Her bir satır vardır:
- bir **etiket** (tahmin etmek istediğiniz özniteliği)
- **özellikleri** (giriş olarak etiket tahmin etmek için kullanılan öznitelikleri).

Ev fiyat tahmini senaryo için özellikleri şunlardan biri olabilir:
- Metrekare house
- yatak ve özellikleri
- posta kodu

Etiket, ilgili satır kare görüntülerini ve Yatak odası banyo değerleri ve posta kodu için geçmiş ev fiyatıdır.

![Satırları ve sütunları ev fiyat veri boyutu odaları posta kodu ve fiyat etiket oluşan özelliklerle gösteren tablo](media/model-builder-data.png)

### <a name="data-formats"></a>Veri biçimleri

Model Oluşturucu aşağıdaki sınırlamalar veri yerleştirir:

- Veri dosyasında (.csv veya bir üst bilgi satırı ile .tsv) veya SQL server veritabanında depolanmalıdır.
- Bir eğitim veri kümesi sınırı 1 GB
- SQL server eğitimi için 100.000 satır sınırı vardır.
- SQL Server'dan veri sunucudan yerel makinenize eğitim önce kopyalanır.

### <a name="example-datasets"></a>Örnek veri kümeleri

Verileriniz henüz sahip değilseniz, bu veri kümelerinden birini deneyin:

|Senaryo|ML Task|Veri|Etiketle|Özellikler|
|-|-|-|-|-|
|Fiyat tahmini|Regresyon|[taksi taksi verileri](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Taksi|Seyahat süresi, uzaklık|
|Anomali algılama|İkili sınıflandırma|[Ürün satış verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Ürün satışları|Ay|
|Yaklaşım analizi|İkili sınıflandırma|[Web sitesi açıklama verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_SentimentAnalysis/SentimentAnalysis/Data/wikiDetoxAnnotated40kRows.tsv)|Etiket (0 yaklaşım, 1 pozitif, negatif olduğunda)|Yorum, yıl|
|Sahtekarlık algılama|İkili sınıflandırma|[Kredi kartı verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Sınıf (sahte, 1, aksi takdirde 0)|Tutar, V1-V28 (anonim özellikleri)|
|Metin sınıflandırma|Sınıflı sınıflandırma|[GitHub sorunu veri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Alan|Başlık, açıklama|

## <a name="train"></a>Eğitim

Senaryonuzu, veri ve etiketi seçtiğinizde, Model Oluşturucu modeli eğitir.

### <a name="what-is-training"></a>Eğitim nedir?

Eğitim, Model Oluşturucu senaryonuz için soruları nasıl cevaplıyor modelinizi öğretir otomatik bir işlemdir. Eğitim sonra modelinizi önce görmediği Öngörüler giriş verileri ile yapabilirsiniz. Örneğin, ev fiyatları tahmin etmeye yönelik ve yeni bir merkezi piyasadaki gelir, satış fiyatı tahmin edebilirsiniz.

Model Oluşturucu otomatik machine learning (AutoML) kullandığından, herhangi bir giriş veya eğitim sırasında sizden ayarlama gerektirmez.

### <a name="how-long-should-i-train-for"></a>İçin ne kadar süreyle eğitme?

Eğitim süresini sağlayabilir. Genel olarak, daha uzun bir süre için eğitim daha doğru bir model oluşturur. Eğitim veri kümesi boyutu arttıkça daha fazla eğitim süresini de gereklidir. Aşağıdaki tabloda boyutunu artırmayı veri kümeleri için bazı eğitim zaman yönergeler sağlar.

Veri kümesi boyutu  | Veri kümesi türü       | Ort. Eğitmek için saat
------------- | ------------------ | --------------
0 - 10 mb     | Sayısal ve metin   | 10 saniye
10 - 100 mb   | Sayısal ve metin   | 10 dakikalık 
100 - 500 mb  | Sayısal ve metin   | 30 dakika 
500 - 1 Gb    | Sayısal ve metin   | 60 dk önce 
1 Gb+         | Sayısal ve metin   | 3 saat + 

Eğitmek için tam zaman de bağlıdır:

- Sütun türü diğer bir deyişle, metin vs sayısal
- machine learning görevi (gerileme veya sınıflandırma) türünü
- Eğitim için kullanılan satır sayısı
- Eğitim için kullanılan özellik sütun sayısı

1 TB veri kümesi ile ölçeklendirme için model Oluşturucu test edilmiştir, ancak bu boyut veri kümesi için yüksek kaliteli model oluşturmaya kadar dört günler sürebilir!

## <a name="evaluate"></a>Değerlendir

Değerlendirme eğitilen modelin yeni test verileri ile tahminlerde kullanmayı işlemidir ve sonra ne kadar iyi tahmin ölçerek.

Model Oluşturucu eğitim verileri Eğitim kümesi ve bir sınama kümesi halinde böler. Eğitim verileri (% 80) model ve test verilerini (% 20) eğitmek için kullanılır modelinizi değerlendirilecek geri tutulur.  Değerlendirme için kullanılan ölçüm, ML görevine bağlıdır. Daha fazla bilgi için [model değerlendirme ölçümleri](resources/metrics.md).  

### <a name="sentiment-analysis-binary-classification"></a>Yaklaşım analizi (ikili sınıflandırma)

İkili sınıflandırma sorunlar için varsayılan ölçümü **doğruluğu**. Doğruluk oranı test veri modelinizi yapar doğru tahminler tanımlar. **% 100 yakın, daha iyi olduğu**.

Gerçek pozitif sonuç oranına hatalı pozitif sonuç oranı karşılaştırması ölçer, AUC (alan) eğrisi altında olması gibi büyük 0,50 edilebilir modellere ilişkin diğer ölçümleri bildirdi. 

F1 puanı gibi ek ölçümleri, duyarlık (doğru tahminler elde etmek için bu sınıfın toplam Öngörüler oranı) ve geri çağırma (doğru tahminler elde etmek için toplam fiili üyeleri söz konusu sınıfın oranını) arasındaki dengeyi denetlemek için kullanılabilir.

### <a name="issue-classification-multiclass-classification"></a>Sorun sınıflandırması (çok sınıflı sınıflandırma)

Sınıflı sınıflandırma sorunlar için varsayılan ölçümü **mikro doğruluğu**. **% 100 yakın, daha iyi olduğu**.

Veri çoklu sınıflarınızda burada kategorilere sorunları doğruluğu iki tür vardır:

- Micro-doğruluğu: tüm örneklerinde doğru tahminler kesir. Sorun sınıflandırması senaryosunda, mikro doğruluk oranı doğru kategorisine atanmış gelen sorunları ' dir. 
- Makro doğruluk: sınıf düzeyinde ortalama doğruluğu. Sorun sınıflandırması senaryosunda doğruluğu her kategori için ölçülür ve ardından kategori doğruluk ortalaması alınır. Bu ölçüm için tüm sınıflar eşit ağırlık verilir. Mükemmel dengeli veri kümeleri için (mevcut olduğu her kategori örnekleri eşit sayıda), mikro doğruluk ve makro doğruluğu aynıdır.


### <a name="price-prediction-regression"></a>Fiyat tahmini (gerileme)

Regresyon sorunlar için varsayılan ölçümü **RSquared**. 1 en iyi olası değerdir. Daha yakından RSquared, modelinizi daha iyi olduğu için 1 ' dir.

Diğer ölçümleri bildirilen, mutlak kaybı gibi kare-kayıp ve RMS kaybı modelinizi anlamak ve diğer regresyon modeli ile karşılaştırmak için kullanılabilir. 

## <a name="improve"></a>Geliştirin

Model performans puanınız değilse kadar iyi olmasını istiyorsanız, şunları yapabilirsiniz:

* Uzun bir süre için eğitin. Daha fazla zaman ile daha fazla bir algoritmalar ve ayarları denemek için otomatikleştirilmiş bir makine öğrenme altyapısı.

* Daha fazla veri ekleyin. Bazen veri miktarı, yüksek kaliteli makine öğrenme modeli eğitmek yeterli değil. 

* Verilerinizi dengeleyin. Sınıflandırma görevleri için Eğitim kümesi kategoriler arasında dengelenir emin olun. Örneğin, 100 eğitim örnekler için dört sınıf varsa ve iki ilk sınıflar (etiket1 ve etiket2) 90 kaydeder, ancak diğer iki için kullanılır (etiket3 ve tag4) kalan 10 kayıtlar üzerindeki kullanılan yalnızca, dengeli veri eksikliği modelinizin corr için uğraşır neden olabilir ectly etiket3 veya tag4 tahmin edin.

## <a name="code"></a>Kod

Değerlendirme Aşaması sonra bir model dosyası ve model uygulamanıza eklemek için kullanabileceğiniz kod Model Oluşturucu çıkarır. ML.NET modelleri zip dosyası olarak kaydedilir. Yük ve modelinizi kullanmak için kodu, çözümünüze yeni bir proje olarak eklenir. Model Oluşturucu ayrıca modelinizi iş başında görmek için çalıştırabileceğiniz örnek bir konsol uygulaması ekler.

Ayrıca, model oluşturmak için kullanılan adımlarla anlayabilmeniz modeli oluşturulan kod Model Oluşturucu çıkarır. Model eğitimi kod, yeni veri modelinizi yeniden eğitme için de kullanabilirsiniz.

## <a name="whats-next"></a>Sırada ne var?

Deneyin [fiyat tahmini veya herhangi bir regresyon senaryo](tutorials/predict-prices-with-model-builder.md)
