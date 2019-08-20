---
title: Model Oluşturucu nedir ve nasıl çalışır?
description: Makine öğrenimi modelini otomatik olarak eğiteiçin ML.NET model Oluşturucu 'Yu kullanma
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: a871c3a3751a93bdf0104c873215b164616f0664
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611456"
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

## <a name="choose-a-model-type"></a>Model türü seçin

Model Oluşturucu 'da, bir makine öğrenimi model türü seçmeniz gerekir. Modelin türü, yapmaya çalıştığınız tahmine göre farklılık gösterir.

Bir sayıyı tahmin eden senaryolar için makine öğrenimi model türü çağırılır `regression`.

Bir kategoriyi tahmin eden senaryolar için model türü olur `classification`. İki tür sınıflandırma vardır:
- yalnızca 2 kategorinin bulunduğu yer: `binary classification`.
- üç veya daha fazla kategorinin bulunduğu yer: `multiclass classification`.

### <a name="which-model-type-is-right-for-me"></a>Benim için hangi model türü uygun?

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>Kategori tahmin etme (yalnızca iki kategori olduğunda)

İkili sınıflandırma, verileri iki kategoride kategorilere ayırmak için kullanılır (Evet/Hayır; geçti/başarısız; true/false; pozitif/negatif).

![Sahtekarlık algılama, risk azaltma ve uygulama filtreleme dahil olmak üzere ikili sınıflandırma örneklerini gösteren diyagram](media/binary-classification-examples.png)

Yaklaşım analizi, müşteri geri bildirimlerine yönelik olumlu veya olumsuz yaklaşımı tahmin etmek için kullanılabilir. İkili sınıflandırma modeli türüne bir örnektir.

Senaryonuz iki kategoriye sınıflandırma gerektiriyorsa, bu şablonu kendi veri kümeniz ile birlikte kullanabilirsiniz.

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>Kategori tahmin etme (üç veya daha fazla kategori olduğunda)

Birden çok Lass sınıflandırması, verileri üç veya daha fazla sınıfa kategorize etmek için kullanılabilir. 

![Belge ve ürün sınıflandırması, destek bileti yönlendirmesi ve müşteri sorunu önceliklendirmesi dahil birden çok Lass sınıflandırması örnekleri](media/multiclass-classification-examples.png)

Sorun sınıflandırması, sorun başlığı ve açıklaması kullanılarak müşteri geri bildirimini (örneğin, GitHub 'da) kategorilere ayırmak için kullanılabilir. Bu, çok sınıflı sınıflandırma modeli türüne bir örnektir.

Verileri üç veya daha fazla kategoride sınıflandırmak istiyorsanız senaryonuz için sorun sınıflandırması şablonunu kullanabilirsiniz.

#### <a name="predict-a-number"></a>Bir sayı tahmin edin

Regresyon, sayıları tahmin etmek için kullanılır.

![Fiyat tahmini, satış tahmini ve tahmine dayalı bakım gibi gerileme örneklerini gösteren diyagram](media/regression-examples.png)

Fiyat tahmini, evin konum, boyut ve diğer özelliklerini kullanarak ev fiyatlarını tahmin etmek için kullanılabilir. Regresyon modeli türüne bir örnektir.

Kendi veri kümeniz ile sayısal bir değer tahmin etmek istiyorsanız senaryonuz için fiyat tahmini şablonunu kullanabilirsiniz.

#### <a name="custom-scenario-choose-your-model-type"></a>Özel senaryo (model türünü seçin)

Özel senaryo, model türünü el ile seçmenizi sağlar.

## <a name="data"></a>Veri

Model türünü seçtikten sonra model Oluşturucu sizden bir veri kümesi sağlamanızı ister. Veriler, senaryonuza yönelik en iyi modeli eğlendirmek, değerlendirmek ve seçmek için kullanılır.

![Model Oluşturucu adımlarını gösteren diyagram](media/model-builder-steps.png)

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

|Senaryo|Model türü|Veri|Etiketle|Özellikler|
|-|-|-|-|-|
|Fiyat tahmini|regresyon|[taxı tarifeli havayolu verileri](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Tarifeli havayolu|Seyahat süresi, uzaklık|
|Anomali algılama|ikili sınıflandırma|[ürün satış verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Ürün satışları|Başından|
|Yaklaşım analizi|ikili sınıflandırma|[Web sitesi açıklama verileri](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Etiket (negatif yaklaşım olduğunda 0, pozitif olduğunda 1)|Açıklama, yıl|
|Sahtekarlık algılama|ikili sınıflandırma|[kredi kartı verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Sınıf (sahte olduğunda 1, aksi durumda 0)|Miktar, v1-V28 (anonimleştirilmiş Özellikler)|
|Metin sınıflandırması|birden çok Lass sınıflandırması|[GitHub sorun verileri](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Alan|Başlık, açıklama|

## <a name="train"></a>Eğitim

Senaryonuzu, verilerinizi ve etiketini seçtikten sonra model Oluşturucu modeli izleyin.

### <a name="what-is-training"></a>Eğitim nedir?

Eğitim, model Oluşturucu 'nun, senaryonuza yönelik soruların nasıl yanıtlanarak modelinizi öğretirken otomatik bir işlemdir. Eğittikten sonra modelinize, daha önce görmemiş olan giriş verileriyle ilgili tahmin yapılabilir. Örneğin, ev fiyatlarını tahmin ediyorsanız ve pazara yeni bir ev geliyorsa, satış fiyatını tahmin edebilirsiniz.

Model Oluşturucu otomatik makine öğrenimi (Otomatikml) kullandığından, eğitim sırasında sizin için herhangi bir giriş veya ayarlama gerekmez.

## <a name="evaluate"></a>Değerlendirmesini

Değerlendirme, eğitilen modeli kullanarak yeni test verileriyle tahminleri yapabilir ve daha sonra tahmine göre ne kadar iyi olduğunu ölçmeye yönelik bir işlemdir.

Model Oluşturucu eğitim verilerini bir eğitim kümesine ve bir test kümesine böler. Eğitim verileri (% 80) modelinizi ve test verilerini eğiteetmek için kullanılır (% 20) , modelinizi değerlendirmek için geri tutulur. Model Oluşturucu, modelin ne kadar iyi olduğunu ölçmek için ölçümleri kullanır. Kullanılan belirli ölçümler modelin türüne bağlıdır. Daha fazla bilgi için bkz. [model değerlendirme ölçümleri](resources/metrics.md).

## <a name="improve"></a>Enizi

Model performans puanınız istediğiniz kadar iyi değilse şunları yapabilirsiniz:

* Daha uzun bir süre için eğitme. Daha fazla zaman, daha fazla algoritma ve ayar denemek için otomatik makine öğrenimi altyapısı.

* Daha fazla veri ekleyin. Bazen veri miktarı yüksek kaliteli bir makine öğrenimi modelini eğitmek için yeterli değildir.

* Verilerinizi dengeleyin. Sınıflandırma görevleri için, eğitim kümesinin Kategoriler genelinde dengeli olduğundan emin olun. Örneğin, 100 eğitim örnekleri için dört sınıfınız varsa ve bu iki sınıf (etiket1 ve etiket2), 90 kayıt için kullanılırsa, ancak diğer iki (etiket3 ve TAG4) yalnızca kalan 10 kayıtta kullanılıyorsa, dengeli verilerin bulunmaması modelinizin eksikliğine zarar verebilir etiket3 veya TAG4 ' i tahmin edin.

## <a name="code"></a>Kod

Değerlendirme aşamasından sonra, model Oluşturucu bir model dosyası ve uygulamayı uygulamanıza eklemek için kullanabileceğiniz kodu verir. ML.NET modelleri bir ZIP dosyası olarak kaydedilir. Modelinize yüklenecek ve kullanılacak kod, çözümünüze yeni bir proje olarak eklenir. Model Oluşturucu Ayrıca, modelinizi işlem içinde görmek için çalıştırabileceğiniz bir örnek konsol uygulaması da ekler.

Ayrıca model Oluşturucu, modeli oluşturmak için kullanılan adımları anlayabilmeniz için modeli oluşturan kodu çıktı. Modelinize yeni verilerle yeniden eğitebilmeniz için model eğitim kodunu da kullanabilirsiniz.

## <a name="whats-next"></a>Sırada ne var?

Model Oluşturucu Visual Studio uzantısını [yükler](how-to-guides/install-model-builder.md)

[Fiyat tahmini veya herhangi bir gerileme senaryosu](tutorials/predict-prices-with-model-builder.md) deneyin
