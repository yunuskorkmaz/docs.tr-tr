---
title: Model Oluşturucu nedir ve nasıl çalışır?
description: Otomatik olarak bir makine öğrenme modeli eğitmek için ML.NET Model Builder nasıl kullanılır
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 9cf66455109908ebd9fc10e62cf4f067609b57d9
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344782"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Model Oluşturucu nedir ve nasıl çalışır?

ML.NET Model Builder, özel makine öğrenme modelleri oluşturmak, eğitmek ve dağıtmak için sezgisel bir grafik Görsel Stüdyo uzantısıdır.

Model Builder, senaryonuza en uygun algoritmayı bulmanıza yardımcı olmak için farklı makine öğrenimi algoritmalarını ve ayarlarını keşfetmek için otomatik makine öğrenimi (AutoML) kullanır.

Model Builder'ı kullanmak için makine öğrenimi uzmanlığına ihtiyacınız yoktur. İhtiyacınız olan tek şey bazı veriler ve çözmeniz gereken bir sorun. Model Oluşturucu, modeli .NET uygulamanıza eklemek için kodu oluşturur.

![Model Builder Visual Studio uzantısı kullanıcı arabirimi animasyon](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Model Oluşturucu şu anda Önizleme'de.

## <a name="scenario"></a>Senaryo

Uygulamanız için bir makine öğrenme modeli oluşturmak için Model Oluşturucu'ya birçok farklı senaryo getirebilirsiniz.

Senaryo, verilerinizi kullanarak yapmak istediğiniz tahmin türünün açıklamasıdır. Örnek:

- geçmiş satış verilerine dayalı gelecekteki ürün satış hacmini tahmin etme
- müşteri yorumlarına göre duyguları olumlu veya olumsuz olarak sınıflandırmak
- bir bankacılık işleminin sahte olup olmadığını algılama
- müşteri geri bildirim sorunlarını şirketinizdeki doğru ekibe yönlendirin

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Hangi makine öğrenme senaryosu benim için doğru?

Model Oluşturucu'da bir senaryo seçmeniz gerekir. Senaryonun türü, ne tür bir tahmin oluşturmaya çalıştığınıza bağlıdır.

#### <a name="text-classification"></a>Metin sınıflandırması

Sınıflandırma, verileri kategorilere ayırmak için kullanılır.

![Sahtekarlık tespiti, risk azaltma ve uygulama taraması dahil olmak üzere ikili sınıflandırma örneklerini gösteren diyagram](media/binary-classification-examples.png)

![Belge ve ürün sınıflandırması, destek bileti yönlendirmesi ve müşteri sorunu önceliklendirmesi dahil olmak üzere çok sınıflı sınıflandırma örnekleri](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a>Değer tahmini

Regresyon sayıları tahmin etmek için kullanılır.

![Fiyat tahmini, satış tahmini ve tahmine dayalı bakım gibi regresyon örneklerini gösteren diyagram](media/regression-examples.png)

#### <a name="image-classification"></a>Resimleri sınıflandırma

Resim sınıflandırması, farklı kategorilerdeki görüntüleri tanımlamak için kullanılabilir. Örneğin, arazi veya hayvan veya üretim kusurları farklı türleri.

Bir resim setiniz varsa ve görüntüleri farklı kategorilere sınıflandırmak istiyorsanız görüntü sınıflandırma senaryosunu kullanabilirsiniz.

#### <a name="recommendation"></a>Öneri

Öneri senaryosu, beğenmelerinin ve beğenmedikleri öğenin diğer kullanıcılarla ne kadar benzer olduğuna bağlı olarak, belirli bir kullanıcı için önerilen öğelerin listesini öngörür.

Bir kullanıcı kümesiniz ve satın alınacak öğeler, filmler, kitaplar veya TV programları gibi bir dizi "ürün" ve kullanıcının bu ürünlerin "derecelendirmeleri" kümesi varsa, öneri senaryosunu kullanabilirsiniz.

## <a name="environment"></a>Ortam

Makine öğrenimi modelinizi makinenizde veya Azure'daki bulutta yerel olarak eğitebilirsiniz.

Yerel olarak eğitim aldığınızda, bilgisayar kaynaklarınızın (CPU, bellek ve disk) kısıtlamaları içinde çalışırsınız. Bulutta eğitim aldığınızda, kaynaklarınızı senaryonuzun taleplerini karşılamak üzere ölçeklendirebilirsiniz, özellikle de büyük veri kümeleri için.

Yerel eğitim tüm senaryolar için desteklenir.

Azure eğitimi Görüntü Sınıflandırması için desteklenir.

## <a name="data"></a>Veri

Senaryonuzu seçtikten sonra, Model Oluşturucu sizden bir veri kümesi sağlamanızı ister. Veriler, senaryonuz için en iyi modeli eğitmek, değerlendirmek ve seçmek için kullanılır.

![Model Oluşturucu adımlarını gösteren diyagram](media/model-builder-steps.png)

Model Oluşturucu,.tsv, .csv, .txt biçimlerinde ve SQL veritabanı biçiminde veri kümelerini destekler. .txt dosyanız varsa, sütunlar ile `,` `;` ayrılmalı veya `/t` dosyanın bir üstbilgi satırı olmalıdır.

Veri kümesi resimlerden oluşuyorsa, desteklenen dosya `.jpg` türleri `.png`ve.

Daha fazla bilgi için [Model Oluşturucu'ya Yük eğitim verilerine](how-to-guides/load-data-model-builder.md)bakın.

### <a name="choose-the-output-to-predict-label"></a>Tahmin etmek için çıktıyı seçin (etiket)

Veri kümesi, eğitim örnekleri satırları ve özniteliklersütunları tablosudur. Her satırda:

- bir **etiket** (tahmin etmek istediğiniz öznitelik)
- **özellikleri** (etiketi tahmin etmek için giriş olarak kullanılan öznitelikler).

Ev fiyatı tahmin senaryosu için özellikler şu şekilde olabilir:

- evin kare görüntüleri
- yatak odası ve banyo sayısı
- posta kodu

Etiket kare görüntüleri, yatak odası ve banyo değerleri ve posta kodu bu satır için tarihsel ev fiyatıdır.

![Boyut odaları posta kodu ve fiyat etiketinden oluşan özelliklere sahip ev fiyat verilerinin satır ve sütunlarını gösteren tablo](media/model-builder-data.png)

### <a name="example-datasets"></a>Örnek veri kümeleri

Henüz kendi verileriniz yoksa, şu veri kümelerinden birini deneyin:

|Senaryo|Örnek|Veri|Etiketle|Özellikler|
|-|-|-|-|-|
|Sınıflandırma|Satış anormalliklerini tahmin etme|[ürün satış verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Ürün Satışları|Ay|
||Web sitesi yorumlarının duyarlılığını tahmin edin|[web sitesi yorum verileri](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Etiket (0 negatif duygu, 1 pozitif)|Yorum, Yıl|
||Sahte kredi kartı hareketlerini tahmin etme|[kredi kartı verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Sınıf (1 sahte, 0 aksi takdirde)|Tutar, V1-V28 (anonimleştirilmiş özellikler)|
||GitHub deposundaki sorunun türünü tahmin etme|[GitHub sorun verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Alan|Başlık, Açıklama|
|Değer tahmini|Taksi ücret fiyatını tahmin edin|[taksi ücreti verileri](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Ücret|Yolculuk süresi, mesafe|
|Resimleri sınıflandırma|Sorunun kategorisini tahmin etme|[çiçek görüntüleri](http://download.tensorflow.org/example_images/flower_photos.tgz)|Çiçek türü: papatya, karahindiba, gül, ayçiçeği, lale|Görüntü verilerinin kendisi|
|Öneri|Birinin beğeneceği filmleri tahmin edin|[film reytingleri](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|Kullanıcılar, Filmler|Derecelendirmeler|

## <a name="train"></a>Eğitim

Senaryonuzu, verilerinizi ve etiketinizi seçtikten sonra Model Oluşturucu modeli çalıştırAn modeli çalıştırZ.

### <a name="what-is-training"></a>Eğitim nedir?

Eğitim, Model Oluşturucu'nun modelinize senaryonuzla ilgili soruları nasıl yanıtlayabildiğini öğrettiği otomatik bir işlemdir. Bir kez eğitildikten sonra, modeliniz daha önce görmediği giriş verileriyle öngörülerde bulunabilir. Örneğin, ev fiyatları tahmin ediyorsanız ve yeni bir ev piyasaya geliyor, onun satış fiyatı tahmin edebilirsiniz.

Model Oluşturucu otomatik makine öğrenimi (AutoML) kullandığından, eğitim sırasında sizden herhangi bir giriş veya asetama gerektirmez.

### <a name="how-long-should-i-train-for"></a>Ne kadar süre antrenman yapmalıyım?

Model Oluşturucu, size en iyi performans gösteren modeli bulmak için birden çok modeli keşfetmek için AutoML kullanır.

Daha uzun eğitim süreleri, AutoML'nin daha geniş bir ayarı yelpazesine sahip daha fazla modeli keşfetmesine olanak tanır.

Aşağıdaki tablo, yerel bir makinede örnek veri kümeleri paketi için iyi performans elde etmek için geçen ortalama süreyi özetleyin.

|Dataset boyutu|Eğitim için ortalama süre|
|------------|---------------------|
|0 - 10 MB|10 sn|
|10 - 100 MB|10 dk|
|100 - 500 MB|30 dk|
|500 - 1 GB Arası|60 dk|
|1 GB+|3+ saat|

Bu sayılar sadece bir rehberdir. Eğitimin tam uzunluğu şuna bağlıdır:

- modele giriş olarak kullanılan özellik (sütun) sayısı
- sütun türü
- ML görev
- eğitim için kullanılan makinenin CPU, disk ve bellek performansı

## <a name="evaluate"></a>Değerlendir

Değerlendirme, modelinizin ne kadar iyi olduğunu ölçme işlemidir. Model Oluşturucu, yeni test verileriyle öngörülerde bulunmak için eğitilmiş modeli kullanır ve ardından tahminlerin ne kadar iyi olduğunu ölçer.

Model Oluşturucu, eğitim verilerini bir eğitim kümesine ve test kümesine böler. Eğitim verileri (%80) modelinizi ve test verilerini eğitmek için kullanılır (%20) modelinizi değerlendirmek için geri tutulur.

### <a name="how-do-i-understand-my-model-performance"></a>Model performansımı nasıl anlarım?

Bir senaryo, makine öğrenimi görevine eş ler. Her ML görevinin kendi değerlendirme ölçütleri kümesi vardır.

#### <a name="value-prediction"></a>Değer tahmini

Değer tahmin sorunları için varsayılan metrik RSquared' dir, RSquared değeri 0 ile 1 arasında değişir. 1 mümkün olan en iyi değer dir veya başka bir deyişle rsquared değeri daha yakın 1 modeli daha iyi performans.

Mutlak kayıp, kare-kayıp ve RMS kaybı gibi bildirilen diğer ölçümler, modelinizin nasıl performans gösterdiğini anlamak ve diğer değer tahmin modelleri ile karşılaştırmak için kullanılabilecek ek ölçümlerdir.

#### <a name="classification-2-categories"></a>Sınıflandırma (2 kategori)

Sınıflandırma sorunları için varsayılan metrik doğruluktır. Doğruluk, modelinizin test veri kümesi üzerinde yaptığı doğru tahminlerin oranını tanımlar. %100 veya %1.0'a ne kadar yakınsa o kadar iyi olur.

AUC (eğrinin altındaki alan) gibi bildirilen diğer ölçümler, modellerin kabul edilememesi için doğru pozitif oranı ve yanlış pozitif oranı ölçen 0,50'den büyük olmalıdır.

Hassasve Geri Çağırma arasındaki dengeyi kontrol etmek için F1 puanı gibi ek ölçümler kullanılabilir.

#### <a name="classification-3-categories"></a>Sınıflandırma (3+ kategori)

Çok sınıflı sınıflandırma için varsayılan metrik Mikro Doğruluk'tır. Mikro Doğruluk %100 veya %1.0'a ne kadar yakınsa o kadar iyi olur.

Çok sınıflı sınıflandırma için bir diğer önemli metrik makro-doğruluk, Mikro-doğruluk benzer 1.0 daha iyi. Doğruluk bu iki tür hakkında düşünmek için iyi bir yoldur:

- Mikro doğruluk: Gelen bilet ne sıklıkta doğru takıma sınıflandırılır?
- Makro doğruluk: Ortalama bir takım için gelen bilet takım için ne sıklıkta doğrudur?

### <a name="more-information-on-evaluation-metrics"></a>Değerlendirme ölçümleri hakkında daha fazla bilgi

Daha fazla bilgi için [model değerlendirme ölçümlerine](resources/metrics.md)bakın.

## <a name="improve"></a>Geliştirmek

Model performans puanınız istediğiniz kadar iyi değilse, şunları yapabilirsiniz:

- Daha uzun bir süre için tren. Daha fazla zaman ile, daha fazla algoritma ve ayarları ile otomatik makine öğrenme motoru deneyleri.

- Daha fazla veri ekleyin. Bazen veri miktarı yüksek kaliteli bir makine öğrenme modeli eğitmek için yeterli değildir.

- Verilerinizi dengeleyin. Sınıflandırma görevleri için, eğitim kümesinin kategoriler arasında dengeli olduğundan emin olun. Örneğin, 100 eğitim örneği için dört sınıfınız varsa ve iki birinci sınıf (tag1 ve tag2) 90 kayıt için kullanılıyorsa, ancak diğer ikisi (tag3 ve tag4) yalnızca kalan 10 kayıtta kullanılıyorsa, dengeli veri eksikliği modelinizin tag3 veya tag4'u doğru tahmin edin.

## <a name="code"></a>Kod

Değerlendirme aşamasından sonra, Model Oluşturucu bir model dosyası ve uygulamanıza modeli eklemek için kullanabileceğiniz kod çıktır. ML.NET modelleri zip dosyası olarak kaydedilir. Modelinizi yüklemek ve kullanmak için kod çözümünüze yeni bir proje olarak eklenir. Model Oluşturucu ayrıca, modelinizi iş başında görmek için çalıştırabileceğiniz örnek bir konsol uygulaması da ekler.

Ayrıca, Modeli oluşturmak için kullanılan adımları anlayabilmeniz için Modeli oluşturan kodu Model Oluşturucu çıktır. Modelinizi yeni verilerle yeniden eğitmek için model eğitim kodunu da kullanabilirsiniz.

## <a name="whats-next"></a>Sırada ne var?

Model Oluşturucu Visual Studio uzantısını [yükleyin](how-to-guides/install-model-builder.md)

[Fiyat tahminini veya herhangi bir gerileme senaryosuni](tutorials/predict-prices-with-model-builder.md) deneyin
