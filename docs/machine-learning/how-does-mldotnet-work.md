---
title: ML.NET nedir ve nasıl çalışır?
description: ML.NET, .NET uygulamalarına çevrimiçi veya çevrimdışı senaryolarda makine öğrenimi ekleme olanağı sağlar. Bu özellik sayesinde, ML.NET kullanmak üzere bir ağa bağlanmak zorunda kalmadan uygulamanızın kullanabileceği verileri kullanarak otomatik öngörüler yapabilirsiniz. Bu makalede, ML.NET makine öğreniminin temelleri açıklanmaktadır.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 169250adf81992ad0025e78eb9c8f151107bcf40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185863"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>ML.NET nedir ve nasıl çalışır?

ML.NET, .NET uygulamalarına çevrimiçi veya çevrimdışı senaryolarda makine öğrenimi ekleme olanağı sağlar. Bu özellik sayesinde, uygulamanızın kullanabileceği verileri kullanarak otomatik öngörüler yapabilirsiniz. Makine öğrenimi uygulamaları, açıkça programlanması yerine öngörülerde bulunmak için verilerdeki desenlerden yararlanAr.

Merkezi ML.NET bir makine öğrenme **modelidir.** Model, giriş verilerinizi bir tahmine dönüştürmek için gereken adımları belirtir. ML.NET ile, bir algoritma belirterek özel bir modeli eğitebilir veya önceden eğitilmiş TensorFlow ve ONNX modellerini içe aktarabilirsiniz.

Bir modele sahip olduktan sonra, tahminleri yapmak için uygulamanıza ekleyebilirsiniz.

ML.NET .NET Core veya Windows kullanarak .NET Framework kullanarak Windows, Linux ve macOS'ta çalışır. 64 bit tüm platformlarda desteklenir. TensorFlow, LightGBM ve ONNX ile ilgili işlevler dışında Windows'da 32 bit desteklenir.

ML.NET ile yapabileceğiniz tahmin türüne örnekler:

|||
|-|-|
|Sınıflandırma/Kategorizasyon|Müşteri geri bildirimlerini otomatik olarak pozitif ve negatif kategorilere ayırın|
|Regresyon/Sürekli değerleri tahmin etme|Büyüklük ve konuma göre evlerin fiyatını tahmin edin|
|Anomali Algılama|Sahte bankacılık işlemlerini algılama |
|Öneriler|Çevrimiçi alışverişyapanların önceki satın alma işlemlerini temel alan satın almak isteyebileceği ürünler önerme|
|Zaman serisi/sıralı veriler|Hava durumu/ürün satışlarını tahmin edin|
|Resimleri sınıflandırma|Tıbbi görüntülerdeki patolojileri kategorilere ayırın|

## <a name="hello-mlnet-world"></a>Merhaba ML.NET Dünya

Aşağıdaki snippet kodu en basit ML.NET uygulama gösterir. Bu örnek, ev büyüklüğü ve fiyat verilerini kullanarak ev fiyatlarını tahmin etmek için doğrusal bir regresyon modeli oluşturuyor.

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;

    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }

        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }

        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();

            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));

            // 3. Train model
            var model = pipeline.Fit(trainingData);

            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    }
```

## <a name="code-workflow"></a>Kod iş akışı

Aşağıdaki diyagram, uygulama kodu yapısını ve model geliştirme işlemini temsil eder:

- Eğitim verilerini bir **IDataView** nesnesine toplama ve yükleme
- Özellikleri ayıklamak ve makine öğrenimi algoritması uygulamak için bir işlem ardışık hattı belirtin
- Boru hattında **Fit()** numaralı telefonu arayarak bir model eğitin
- Modeli değerlendirin ve geliştirmek için yineleyin
- Bir uygulamada kullanılmak üzere modeli ikili biçime kaydetme
- Modeli bir **ITransformer** nesnesine geri yükleme
- **CreatePredictionEngine.Predict()** numaralı telefonu arayarak öngörülerde bulunun

![veri üretimi, boru hattı geliştirme, model eğitimi, model değerlendirmesi ve model kullanımı için bileşenler de dahil olmak üzere ML.NET uygulama geliştirme akışı](./media/mldotnet-annotated-workflow.png)

Bu kavramları biraz daha derinlemesine araştıralım.

## <a name="machine-learning-model"></a>Makine öğrenimi modeli

ML.NET modeli, tahmin edilen çıktıya ulaşmak için giriş verilerinizde gerçekleştirmek için dönüşümler içeren bir nesnedir.

### <a name="basic"></a>Temel

En temel model iki boyutlu doğrusal regresyon, bir sürekli miktar başka bir orantılı olduğu, yukarıdaki ev fiyat örneği gibi.

![Yanlı ve ağırlık parametrelerli Lineer Regresyon Modeli](./media/linear-regression-model.svg)

Model basitçe: $Price = b + Boyut * w$. $b$ ve $w$ parametreleri, bir dizi (boyut, fiyat) çifte bir satır takılarak tahmin edilir. Modelin parametrelerini bulmak için kullanılan **verilere eğitim verileri**denir. Bir makine öğrenme modelinin girdileri **özellikleri**denir. Bu örnekte, $Size$ tek özelliktir. Bir makine öğrenme modelini eğitmek için kullanılan zemin-gerçeğdeğerlerine **etiketler**denir. Burada, eğitim veri kümesindeki $Price$ değerleri etiketlerdir.

### <a name="more-complex"></a>Daha karmaşık

Daha karmaşık bir model, hareket metni açıklamasını kullanarak mali hareketleri kategorilere ayırır.

Her işlem açıklaması, gereksiz sözcükleri ve karakterleri kaldırarak ve sözcük ve karakter birleşimlerini sayarak bir dizi özelliğe ayrılır. Özellik kümesi, eğitim verilerindeki kategoriler kümesine dayalı doğrusal bir model eğitmek için kullanılır. Yeni bir açıklama, eğitim kümesindekilere ne kadar benzerse, aynı kategoriye atanmanın olasılığı da o kadar yüksek tir.

![Metin Sınıflandırma Modeli](./media/text-classification-model.svg)

Hem ev fiyat modeli hem de metin sınıflandırma modeli **doğrusal** modellerdir. Verilerinizin yapısına ve çözdüğünüz soruna bağlı olarak, **karar ağacı** modellerini, **genelleştirilmiş katkı maddesi modellerini** ve diğerlerini de kullanabilirsiniz. [Görevler'deki](./resources/tasks.md)modeller hakkında daha fazla bilgi edinebilirsiniz.

## <a name="data-preparation"></a>Veri hazırlama

Çoğu durumda, mevcut veriler doğrudan bir makine öğrenme modeli eğitmek için kullanılmak üzere uygun değildir. Modelinizin parametrelerini bulmak için kullanılabilmesi için ham verilerin hazırlanması veya önceden işlenmesi gerekir. Verilerinizin dize değerlerinden sayısal gösterime dönüştürülmesi gerekebilir. Giriş verilerinizde gereksiz bilgiler olabilir. Giriş verilerinizin boyutlarını azaltmanız veya genişletmeniz gerekebilir. Verilerinizin normalleştirilmesi veya ölçeklendirilmesi gerekebilir.

[ML.NET öğreticiler,](./tutorials/index.md) belirli makine öğrenimi görevleri için kullanılan metin, resim, sayısal ve zaman serisi verileri için farklı veri işleme ardışık lıkları hakkında bilgi verir.

[Verilerinizin nasıl hazırlanacağı,](./how-to-guides/prepare-data-ml-net.md) veri hazırlamayı nasıl daha genel olarak uygulayacağınızı gösterir.

Kaynaklar bölümünde mevcut tüm [dönüşümlerin](./resources/transforms.md) bir ekini bulabilirsiniz.

## <a name="model-evaluation"></a>Model değerlendirmesi

Modelinizi eğittikten sonra, bunun gelecekteki tahminleri ne kadar iyi yapacağını nasıl biliyorsunuz? ML.NET ile, modelinizi bazı yeni test verilerine göre değerlendirebilirsiniz.

Her tür makine öğrenimi görevi, test veri kümesine karşı modelin doğruluğunu ve hassasiyetini değerlendirmek için kullanılan ölçümlere sahiptir.

Bizim ev fiyat örneği için, biz **Regresyon** görevi kullanılır. Modeli değerlendirmek için özgün örneğe aşağıdaki kodu ekleyin.

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);

        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

Değerlendirme ölçümleri, hatanın düşük olduğunu ve öngörülen çıktı ile test çıktısı arasındaki korelasyonun yüksek olduğunu söyler. Çok kolaydı! Gerçek örneklerde, iyi model ölçümleri elde etmek için daha fazla atokalma alır.

## <a name="mlnet-architecture"></a>ML.NET mimarisi

Bu bölümde ML.NET mimari desenleri üzerinden geçeceğiz. Deneyimli bir .NET geliştiricisiyseniz, bu desenlerden bazıları size tanıdık gelecektir ve bazıları daha az tanıdık olacaktır. Biz dalırken sıkıca tutun!

ML.NET uygulaması bir <xref:Microsoft.ML.MLContext> nesneyle başlar. Bu singleton nesne **katalogları**içerir. Katalog, veri yükleme ve kaydetme, dönüşümler, eğitmenler ve model işletim bileşenleri için bir fabrikadır. Her katalog nesnesinin farklı bileşen türlerini oluşturmak için yöntemleri vardır:

|||||
|-|-|-|-|
|Veri yükleme ve kaydetme||<xref:Microsoft.ML.DataOperationsCatalog>||
|Veri hazırlama||<xref:Microsoft.ML.TransformsCatalog>||
|Eğitim algoritmaları|İkili sınıflandırma|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||Çok sınıflı sınıflandırma|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||Anormallik algılama|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||Kümeleme|<xref:Microsoft.ML.ClusteringCatalog>||
||Tahmin etme|<xref:Microsoft.ML.ForecastingCatalog>||
||Sıralama|<xref:Microsoft.ML.RankingCatalog>||
||Regresyon|<xref:Microsoft.ML.RegressionCatalog>||
||Öneri|<xref:Microsoft.ML.RecommendationCatalog>|NuGet `Microsoft.ML.Recommender` paketini ekleyin|
||Zaman Serisi|<xref:Microsoft.ML.TimeSeriesCatalog>|NuGet `Microsoft.ML.TimeSeries` paketini ekleyin|
|Model kullanımı ||<xref:Microsoft.ML.ModelOperationsCatalog>||

Yukarıdaki kategorilerin her birinde oluşturma yöntemlerine gidebilirsiniz. Visual Studio'yu kullanarak kataloglar IntelliSense üzerinden ortaya çıkar.

   ![Regresyon Eğitmenler için Intellisense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>Boru hattını oluşturun

Her kataloğun içinde bir dizi uzatma yöntemi vardır. Bir eğitim boru hattı oluşturmak için uzantı yöntemlerinin nasıl kullanıldığına bakalım.

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

Snippet ve `Concatenate` `Sdca` katalogda her iki yöntem vardır. Her biri, ardışık almaya eklenen bir [IEstimator](xref:Microsoft.ML.IEstimator%601) nesnesi oluşturur.

Bu noktada, nesneler yalnızca oluşturulur. İdam gerçekleşmemiş.

### <a name="train-the-model"></a>Modeli eğitme

Ardışık ardışık ardışık nesneler oluşturulduktan sonra, verileri modeli eğitmek için kullanılabilir.

```csharp
    var model = pipeline.Fit(trainingData);
```

Arama, `Fit()` modelin parametrelerini tahmin etmek için giriş eğitim verilerini kullanır. Bu modeli eğitim olarak bilinir. Unutmayın, yukarıdaki doğrusal regresyon modeliiki model parametreleri vardı: **önyargı** ve **ağırlık**. `Fit()` Aramadan sonra parametrelerin değerleri bilinir. Çoğu model bundan çok daha fazla parametreye sahip olacaktır.

[Modelinizi nasıl eğitebileceğiniz](./how-to-guides/train-machine-learning-model-ml-net.md)konusunda model eğitimi hakkında daha fazla bilgi edinebilirsiniz.

Ortaya çıkan model nesnesi <xref:Microsoft.ML.ITransformer> arabirimi uygular. Diğer bir deyişle, model giriş verilerini öngörülere dönüştürür.

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>Modeli kullanma

Giriş verilerini toplu olarak tahminlere veya aynı anda bir girişe dönüştürebilirsiniz. Ev fiyat örneğinde, biz her ikisini de yaptı: model değerlendirmek amacıyla toplu olarak, ve birseferde yeni bir tahmin yapmak için. Tek tahminlerde bulunalım.

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

Yöntem `CreatePredictionEngine()` bir giriş sınıfı ve bir çıktı sınıfı alır. Alan adları ve/veya kod öznitelikleri, model eğitimi ve tahmini sırasında kullanılan veri sütunlarının adlarını belirler. Nasıl Yapılır bölümünde [tek bir tahmin nasıl yapılır](./how-to-guides/single-predict-model-ml-net.md) hakkında bilgi edinebilirsiniz.

### <a name="data-models-and-schema"></a>Veri modelleri ve şema

Bir ML.NET makine öğrenme boru hattının özünde [DataView](xref:Microsoft.ML.IDataView) nesneleri vardır.

Ardışık ardışık yoldaki her dönüşümün bir girdi şeması vardır (dönüşümün girdisinde görmeyi beklediği veri adları, türleri ve boyutları); ve bir çıktı şeması (dönüşümün dönüşümden sonra ürettiği veri adları, türleri ve boyutları). Aşağıdaki [belge, IDataView arabiriminin ve tür sisteminin](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html)ayrıntılı bir açıklamasını sağlar.

Ardışık ardışık bir dönüşümden çıkış şeması bir sonraki dönüşümün giriş şemasıyla eşleşmiyorsa, ML.NET bir özel durum oluşturur.

Veri görünümü nesnesi sütunları ve satırları vardır. Her sütunun bir adı, bir türü ve uzunluğu vardır. Örneğin, ev fiyat örneğindeki giriş sütunları **Boyut** ve **Fiyat'dır.** Her ikisi de tür ve vektör olanlar yerine skaler miktarları vardır.

   ![ev fiyat tahmini verileri ile ML.NET Veri Görünümü örneği](./media/ml-net-dataview.png)

Tüm ML.NET algoritmaları bir vektör olan bir giriş sütunu arar. Varsayılan olarak bu vektör sütunu **Özellikler**olarak adlandırılır. Bu nedenle **Size** sütununu ev fiyat örneğimizde **Özellikler** adlı yeni bir sütuna dönüştürdük.

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

Tüm algoritmalar, bir tahmin gerçekleştirdikten sonra da yeni sütunlar oluşturur. Bu yeni sütunların sabit adları makine öğrenimi algoritmasının türüne bağlıdır. Regresyon görevi için, yeni sütunlardan biri **Puan**olarak adlandırılır. Bu nedenle fiyat verilerimizi bu adla ilişkilendirdik.

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

[Makine Öğrenimi Görevleri](resources/tasks.md) kılavuzunda farklı makine öğrenimi görevlerinin çıktı sütunları hakkında daha fazla bilgi bulabilirsiniz.

DataView nesnelerinin önemli bir özelliği, **onların tembel olarak**değerlendirilmiş olmasıdır. Veri görünümleri yalnızca model eğitimi ve değerlendirmesi ve veri tahmini sırasında yüklenir ve çalıştırılır. ML.NET uygulamanızı yazarken ve test ederken, [Önizleme](xref:Microsoft.ML.DebuggerExtensions.Preview*) yöntemini arayarak herhangi bir veri görünümü nesnesine göz atmak için Visual Studio hata ayıklama sını kullanabilirsiniz.

```csharp
    var debug = testPriceDataView.Preview();
```

Hata ayıklamadaki değişkeni `debug` izleyebilir ve içeriğini inceleyebilirsiniz. Performansı önemli ölçüde düşürdüğünüz için üretim kodunda Önizleme yöntemini kullanmayın.

### <a name="model-deployment"></a>Model Dağıtımı

Gerçek hayattaki uygulamalarda, model eğitim ve değerlendirme kodunuz tahmininizden ayrı olacaktır. Aslında, bu iki etkinlik genellikle ayrı takımlar tarafından gerçekleştirilir. Model geliştirme ekibiniz modeli tahmin uygulamasında kullanılmak üzere kaydedebilir.

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a>Sonraki adımlar

* Öğreticilerde daha gerçekçi veri [kümeleri](./tutorials/index.md)ile farklı makine öğrenimi görevleri kullanarak uygulamaları oluşturmak için nasıl öğrenin.

* [Nasıl Kılavuzlar](./how-to-guides/index.md)için daha derinlemesine belirli konular hakkında bilgi edinin.

* Eğer süper hevesli iseniz, doğrudan [API Başvuru belgeleri](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)içine dalış yapabilirsiniz.
