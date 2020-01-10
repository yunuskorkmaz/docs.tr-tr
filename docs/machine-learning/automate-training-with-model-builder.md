---
title: Model Oluşturucu nedir ve nasıl çalışır?
description: Makine öğrenimi modelini otomatik olarak eğiteiçin ML.NET model Oluşturucu 'Yu kullanma
ms.date: 01/07/2020
ms.custom: overview
ms.openlocfilehash: ac704b7961a8442a9174cdef5a4cd2a619236a4e
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777400"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Model Oluşturucu nedir ve nasıl çalışır?

ML.NET model Oluşturucu, özel makine öğrenimi modellerini derlemek, eğitme ve dağıtmaya yönelik sezgisel bir grafik Visual Studio uzantısıdır.

Model Oluşturucu, senaryonuza en uygun olanı bulmanıza yardımcı olmak üzere farklı makine öğrenimi algoritmalarını ve ayarlarını araştırmak için otomatik makine öğrenimi (Otomatikml) kullanır.

Model Oluşturucuyu kullanmak için Machine Learning uzmanlığına ihtiyacınız yoktur. Bazı veriler ve çözübir sorun var. Model Oluşturucu, modeli .NET uygulamanıza eklemek için kodu oluşturur.

![Model Oluşturucu Visual Studio uzantısı kullanıcı arabirimi animasyonu](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Model Oluşturucu Şu anda önizleme aşamasındadır.

## <a name="scenarios"></a>Senaryolar

Uygulamanız için bir makine öğrenimi modeli oluşturmak için model Oluşturucu 'ya birçok farklı senaryo getirebilirsiniz.

Senaryo, verilerinizi kullanarak yapmak istediğiniz tahmin türünün bir açıklamasıdır. Örneğin:

- geçmiş satış verilerine göre gelecek ürün satış hacmini tahmin edin
- müşterilerin gözden geçirmeleri temelinde olumlu veya olumsuz şekilde sınıflandırın
- Bankacılık işleminin sahte olup olmadığını Algıla
- Müşteri geri bildirim sorunlarını şirketinizdeki doğru ekibe yönlendirin

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Hangi makine öğrenimi senaryosu bana uygun?

Model Oluşturucu 'da bir senaryo seçmeniz gerekir. Senaryonun türü, yapmaya çalıştığınız tahmin türüne bağlıdır.

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>Kategori tahmin etme (yalnızca iki kategori olduğunda)

İkili sınıflandırma, verileri iki kategoride kategorilere ayırmak için kullanılır (Evet/Hayır; geçti/başarısız; true/false; pozitif/negatif).

![Sahtekarlık algılama, risk azaltma ve uygulama filtreleme dahil olmak üzere ikili sınıflandırma örneklerini gösteren diyagram](media/binary-classification-examples.png)

Yaklaşım analizi, müşteri geri bildirimlerine yönelik olumlu veya olumsuz yaklaşımı tahmin etmek için kullanılabilir. Bu, ikili sınıflandırma makinesi öğrenimi görevinin bir örneğidir.

Senaryonuz iki kategoriye sınıflandırma gerektiriyorsa, bu şablonu kendi veri kümeniz ile birlikte kullanabilirsiniz.

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>Kategori tahmin etme (üç veya daha fazla kategori olduğunda)

Birden çok Lass sınıflandırması, verileri üç veya daha fazla sınıfa kategorize etmek için kullanılabilir.

![Belge ve ürün sınıflandırması, destek bileti yönlendirmesi ve müşteri sorunu önceliklendirmesi dahil birden çok Lass sınıflandırması örnekleri](media/multiclass-classification-examples.png)

Sorun sınıflandırması, sorun başlığı ve açıklaması kullanılarak müşteri geri bildirimini (örneğin, GitHub 'da) kategorilere ayırmak için kullanılabilir. Bu, çok sınıflı sınıflandırma makinesi öğrenimi görevinin bir örneğidir.

Verileri üç veya daha fazla kategoride sınıflandırmak istiyorsanız senaryonuz için sorun sınıflandırması şablonunu kullanabilirsiniz.

#### <a name="predict-a-number"></a>Bir sayı tahmin edin

Regresyon, sayıları tahmin etmek için kullanılır.

![Fiyat tahmini, satış tahmini ve tahmine dayalı bakım gibi gerileme örneklerini gösteren diyagram](media/regression-examples.png)

Fiyat tahmini, evin konum, boyut ve diğer özelliklerini kullanarak ev fiyatlarını tahmin etmek için kullanılabilir. Gerileme makine öğrenimi görevi örneğidir.

Kendi veri kümeniz ile sayısal bir değer tahmin etmek istiyorsanız senaryonuz için fiyat tahmini şablonunu kullanabilirsiniz.

#### <a name="classify-images-into-categories"></a>Görüntüleri kategoriler halinde sınıflandır

Bu senaryo, kategorize edilecek giriş verilerinin bir görüntü kümesi olduğu birden çok Lass sınıflandırmasının özel bir durumdur.

Görüntü sınıflandırması, farklı kategorilerin görüntülerini belirlemek için kullanılabilir. Örneğin, farklı türlerde terur veya hayvanlar veya üretim kusurları vardır.

Bir görüntü kümesine sahipseniz ve görüntüleri farklı kategorilerde sınıflandırmak istiyorsanız senaryonuz için görüntü sınıflandırması şablonunu kullanabilirsiniz.

#### <a name="custom-scenario"></a>Özel senaryo

Özel senaryo, senaryonuzu el ile seçmenizi sağlar.

## <a name="data"></a>Veri

Senaryonuzu seçtikten sonra model Oluşturucu sizden bir veri kümesi sağlamanızı ister. Veriler, senaryonuza yönelik en iyi modeli eğlendirmek, değerlendirmek ve seçmek için kullanılır.

![Model Oluşturucu adımlarını gösteren diyagram](media/model-builder-steps.png)

Model Oluşturucu,. tsv,. csv,. txt biçimlerinin yanı sıra SQL veritabanı biçiminde veri kümelerini destekler. . Txt dosyanız varsa, sütunların `,`, `;` veya `/t` ile ayrılması ve dosyanın bir başlık satırı olması gerekir.

Veri kümesi görüntülerden birini yapılırsa, desteklenen dosya türleri `.jpg` ve `.png`.

Daha fazla bilgi için bkz. [model Oluşturucu 'da eğitim verilerini yükleme](how-to-guides/load-data-model-builder.md).

### <a name="choose-the-output-to-predict-label"></a>Tahmin edilecek çıktıyı seçin (etiket)

Veri kümesi, eğitim örneklerinden ve özniteliklerin sütunlarından oluşan bir tablodur. Her satır şunları içerir:

- bir **etiket** (tahmin etmek istediğiniz öznitelik)
- **Özellikler** (etiketi tahmin etmek için giriş olarak kullanılan öznitelikler).

Ev fiyat tahmini senaryosu için özellikler şu şekilde olabilir:

- Evin kare çekimi
- yatak odaları ve külikler sayısı
- posta kodu

Etiket, bu kare çekimi, yatak odası ve banyo değerleri ve posta kodu satırı için geçmiş bir evin fiyatıdır.

![Boyut Odalar ZIP kodu ve fiyat etiketinden oluşan özelliklerle birlikte, ev fiyatı verilerinin satırlarını ve sütunlarını gösteren tablo](media/model-builder-data.png)

### <a name="example-datasets"></a>Örnek veri kümeleri

Henüz kendi verileriniz yoksa, bu veri kümelerinden birini deneyin:

|Senaryo|ML görevi|Veri|Etiketle|Özellikler|
|-|-|-|-|-|
|Fiyat tahmini|regresyon|[taxı tarifeli havayolu verileri](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Tarifeli havayolu|Seyahat süresi, uzaklık|
|Anomali algılama|ikili sınıflandırma|[ürün satış verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Ürün satışları|Ay|
|Yaklaşım analizi|ikili sınıflandırma|[Web sitesi açıklama verileri](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Etiket (negatif yaklaşım olduğunda 0, pozitif olduğunda 1)|Açıklama, yıl|
|Sahtekarlık algılama|ikili sınıflandırma|[kredi kartı verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Sınıf (sahte olduğunda 1, aksi durumda 0)|Miktar, v1-V28 (anonimleştirilmiş Özellikler)|
|Metin sınıflandırması|birden çok Lass sınıflandırması|[GitHub sorun verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Alan|Başlık, açıklama|
|Görüntü sınıflandırma|birden çok Lass sınıflandırması|[Çiçekler görüntüleri](http://download.tensorflow.org/example_images/flower_photos.tgz)|Çiçek türü: da, Dandelion, Roses, sunçiçekler, TULIP 'ler|Görüntü verilerinin kendisi|

## <a name="train"></a>Eğitim

Senaryonuzu, verilerinizi ve etiketini seçtikten sonra model Oluşturucu modeli izleyin.

### <a name="what-is-training"></a>Eğitim nedir?

Eğitim, model Oluşturucu 'nun, senaryonuza yönelik soruların nasıl yanıtlanarak modelinizi öğretirken otomatik bir işlemdir. Eğittikten sonra modelinize, daha önce görmemiş olan giriş verileriyle ilgili tahmin yapılabilir. Örneğin, ev fiyatlarını tahmin ediyorsanız ve pazara yeni bir ev geliyorsa, satış fiyatını tahmin edebilirsiniz.

Model Oluşturucu otomatik makine öğrenimi (Otomatikml) kullandığından, eğitim sırasında sizin için herhangi bir giriş veya ayarlama gerekmez.

### <a name="how-long-should-i-train-for"></a>Ne kadar eğitmem gerekir?

Model Oluşturucu, sizi en iyi şekilde gerçekleştiren modeli bulmak için birden çok modeli araştırmak üzere oto ml kullanır.

Daha uzun eğitim dönemleri, oto ml 'nin daha geniş bir ayar aralığıyla daha fazla modeli keşfetmesine olanak tanır.

Aşağıdaki tabloda, yerel bir makinedeki bir örnek veri kümesi paketi için iyi performans sağlamak üzere harcanan ortalama süre özetlenmektedir.

|Veri kümesi boyutu|Ortalama eğitim süresi|
|------------|---------------------|
|0-10 MB|10 sn|
|10-100 MB|10 dakika|
|100-500 MB|30 dakika|
|500-1 GB|60 dk|
|1 GB +|3 + saat|

Bu numaralar yalnızca bir kılavuzdur. Eğitimin tam uzunluğu şu şekilde bağımlıdır:

- modele girdi olarak kullanılan özellik sayısı (sütun)
- sütun türü
- ML görevi
- Eğitim için kullanılan makinenin CPU, disk ve bellek performansı

## <a name="evaluate"></a>'i Değerlendirme

Değerlendirme, modelinizin ne kadar iyi olduğunu ölçmeye yönelik bir işlemdir. Model Oluşturucu, yeni test verileriyle tahmine dayalı hale getirmek için eğitilen modeli kullanır ve daha sonra tahminlerin ne kadar iyi olduğunu ölçer.

Model Oluşturucu eğitim verilerini bir eğitim kümesine ve bir test kümesine böler. Eğitim verileri (%80) modelinizi ve test verilerini eğiteetmek için kullanılır (%20) , modelinizi değerlendirmek için geri tutulur. 

### <a name="how-do-i-understand-my-model-performance"></a>Nasıl yaparım? model performansımı anladım mı?

Bir senaryo bir makine öğrenimi göreviyle eşlenir. Her ML görevinin kendi değerlendirme ölçümleri kümesi vardır.

#### <a name="regression-for-example-price-prediction"></a>Gerileme (örneğin, fiyat tahmini)

Gerileme sorunları için varsayılan ölçüm RKARE, RKARE değeri 0 ile 1 arasında aralıklar olur. 1 mümkün olan en iyi değer veya diğer bir deyişle, modelinizin daha iyi bir performans elde etmek için, RKARE değerinin 1 ' e yakın olması.

Mutlak kayıp, kareli kayıp ve RMS kaybı gibi bildirilen diğer ölçümler, modelinizin nasıl çalıştığını anlamak ve diğer gerileme modelleriyle karşılaştırmak için kullanılabilecek ek ölçümlerdir.

#### <a name="binary-classification-for-example-sentiment-analysis"></a>İkili Sınıflandırma (örneğin, Yaklaşım Analizi)

Sınıflandırma sorunları için varsayılan ölçüm doğruluk ' dir. Doğruluk, modelinizin test veri kümesi üzerinde yapmakta olduğu doğru tahminlerden oranını tanımlar. %100 veya 1,0 ' e yakın olan daha iyi bir seçenektir.

Doğru pozitif oranı içeren AUC (eğri kapsamındaki alan) gibi bildirilen diğer ölçümler, modellerin kabul edilebilir olması için 0,50 ' den büyük olmalıdır.

Duyarlılık ve geri çekme arasındaki dengeyi denetlemek için F1 puanı gibi ek ölçümler de kullanılabilir.

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a>Çok sınıf sınıflandırması (örneğin, sorun sınıflandırması, görüntü sınıflandırması)

Çoklu Sınıf sınıflandırması için varsayılan ölçüm mikro doğruluk ' dir. Mikro doğruluk %100 veya 1,0 ' e daha iyi.

Çok sınıf sınıflandırma için başka bir önemli ölçüm, daha iyi olan 1,0 ' e yakın olan mikro doğrulukta olduğu gibi, makro doğruluğuna benzer. Bu iki tür doğruluğu düşünmek için iyi bir yoldur:

- Mikro doğruluk: bir gelen bilet, doğru ekibe ne sıklıkla sınıflandırıldı?
- Makro doğruluğu: ortalama bir ekip Için, takımlarına yönelik gelen bir bilet ne sıklıkta doğru?

### <a name="more-information-on-evaluation-metrics"></a>Değerlendirme ölçümleri hakkında daha fazla bilgi

Daha fazla bilgi için bkz. [model değerlendirme ölçümleri](resources/metrics.md).

## <a name="improve"></a>.NET becerilerinizi

Model performans puanınız istediğiniz kadar iyi değilse şunları yapabilirsiniz:

- Daha uzun bir süre için eğitme. Daha fazla zaman, daha fazla algoritma ve ayar denemek için otomatik makine öğrenimi altyapısı.

- Daha fazla veri ekleyin. Bazen veri miktarı yüksek kaliteli bir makine öğrenimi modelini eğitmek için yeterli değildir.

- Verilerinizi dengeleyin. Sınıflandırma görevleri için, eğitim kümesinin Kategoriler genelinde dengeli olduğundan emin olun. Örneğin, 100 eğitim örnekleri için dört sınıfınız varsa ve bu iki sınıf (etiket1 ve etiket2), 90 kayıt için kullanılırsa, ancak diğer iki (etiket3 ve TAG4) yalnızca kalan 10 kayıtta kullanılıyorsa, dengeli verilerin bulunmaması modelinizin eksikliğine zarar verebilir etiket3 veya TAG4 ' i tahmin edin.

## <a name="code"></a>Kod

Değerlendirme aşamasından sonra, model Oluşturucu bir model dosyası ve uygulamayı uygulamanıza eklemek için kullanabileceğiniz kodu verir. ML.NET modelleri bir ZIP dosyası olarak kaydedilir. Modelinize yüklenecek ve kullanılacak kod, çözümünüze yeni bir proje olarak eklenir. Model Oluşturucu Ayrıca, modelinizi işlem içinde görmek için çalıştırabileceğiniz bir örnek konsol uygulaması da ekler.

Ayrıca model Oluşturucu, modeli oluşturmak için kullanılan adımları anlayabilmeniz için modeli oluşturan kodu çıktı. Modelinize yeni verilerle yeniden eğitebilmeniz için model eğitim kodunu da kullanabilirsiniz.

## <a name="whats-next"></a>Sırada ne var?

Model Oluşturucu Visual Studio uzantısını [yükler](how-to-guides/install-model-builder.md)

[Fiyat tahmini veya herhangi bir gerileme senaryosu](tutorials/predict-prices-with-model-builder.md) deneyin
