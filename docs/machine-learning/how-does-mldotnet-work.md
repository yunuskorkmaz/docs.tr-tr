---
title: ML.NET nedir ve nasıl çalışır?
description: ML.NET, çevrimiçi veya çevrimdışı senaryolarda .NET uygulamalarına makine öğrenimi ekleme olanağı sunar. Bu özellik sayesinde, ML.NET kullanmak üzere bir ağa bağlı kalmak zorunda kalmadan, uygulamanızın kullanabildiği verileri kullanarak otomatik tahminler yapabilirsiniz. Bu makalede, ML.NET ' de makine öğrenmesinin temelleri açıklanmaktadır.
ms.date: 08/26/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: af91819c66a2376f446d0f18537d2f6e718b446e
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104890"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>ML.NET nedir ve nasıl çalışır?

ML.NET, çevrimiçi veya çevrimdışı senaryolarda .NET uygulamalarına makine öğrenimi ekleme olanağı sunar. Bu özellik sayesinde, bir ağa bağlı kalmak zorunda kalmadan uygulamanızın kullanabildiği verileri kullanarak otomatik tahminler yapabilirsiniz. Bu makalede, ML.NET ' de makine öğrenmesinin temelleri açıklanmaktadır. 

ML.NET ile yapabileceğiniz tahmin türlerine örnek olarak şunlar verilebilir:

|||
|-|-|
|Sınıflandırma/kategori oluşturma|Müşteri geri bildirimini otomatik olarak pozitif ve negatif kategorilere bölün|
|Gerileme/sürekli değerleri tahmin etme|Boyut ve konuma göre barındırıldığı fiyatlarını tahmin etme|
|Anomali Algılama|Sahte bankacılık işlemlerini Algıla |
|Öneriler|Çevrimiçi alışverişçilerin, önceki satın alımlarına göre satın almasını isteyebileceğiniz ürünleri önerin|

## <a name="hello-mlnet-world"></a>Merhaba ML.NET dünya

Aşağıdaki kod parçacığındaki kod, en basit ML.NET uygulamasını gösterir. Bu örnek, ev boyutunu ve fiyat verilerini kullanarak ev fiyatlarını tahmin etmek için bir doğrusal regresyon modeli oluşturur. Gerçek yaşam uygulamalarınızda, verileriniz ve modeliniz çok daha karmaşık olacaktır.

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

Aşağıdaki diyagram, uygulama kodu yapısını, ayrıca model geliştirmenin yinelemeli işlemini temsil eder:
- Bir **ıdataview** nesnesinde eğitim verileri toplama ve yükleme
- Özellikleri ayıklamak ve makine öğrenimi algoritmasını uygulamak için bir işlem hattı belirtin
- İşlem hattına **sığdırma ()** yöntemini çağırarak bir modeli eğitme
- Modeli değerlendirin ve geliştirmeyi yineleyin
- Modeli bir uygulamada kullanılmak üzere ikili biçime Kaydet
- Modeli bir **ıranseski** nesnesine geri yükleme
- **CreatePredictionEngine. tahmin ()** öğesini çağırarak tahminleri yapın

![Veri oluşturma, işlem hattı geliştirme, model eğitimi, model değerlendirmesi ve model kullanımı bileşenleri dahil ML.NET uygulama geliştirme akışı](./media/mldotnet-annotated-workflow.png) 

Bu kavramların biraz daha ayrıntılı bir şekilde bakalım.

## <a name="machine-learning-model"></a>Machine Learning modeli

ML.NET modeli, tahmin edilen çıkışa ulaşmak üzere giriş verilerinizde gerçekleştirilecek dönüşümleri içeren bir nesnedir.

### <a name="basic"></a>Temel

En temel model, yukarıdaki ev fiyat örneğinde olduğu gibi, bir sürekli miktarın birbiriyle orantılı olduğu iki boyutlu doğrusal regresyon olur. 

![Sapma ve ağırlık parametrelerine sahip doğrusal regresyon modeli](./media/linear-regression-model.svg)

Model yalnızca: $Price = b + size * w $. $B $ ve $w $ parametreleri, bir dizi (boyut, Fiyat) çiftleriyle bir satıra göre tahmin edilir. Modelin parametrelerini bulmak için kullanılan verilere **eğitim verileri**denir. Machine Learning modelinin girişleri **Özellikler**olarak adlandırılır. Bu örnekte, $Size $ tek özelliktir. Bir makine öğrenimi modelini eğitebilmeniz için kullanılan taban-Truth değerlerine **Etiketler**denir. Burada eğitim verileri kümesindeki $Price $ değerleri etiketlerdir.

### <a name="more-complex"></a>Daha karmaşık

Daha karmaşık bir model, işlem metni açıklamasını kullanarak finansal işlemleri kategoriler halinde sınıflandırır.

Her işlem açıklaması, gereksiz sözcük ve karakterleri kaldırarak ve sözcük ve karakter kombinasyonlarını sayarak bir özellik kümesine bölünür. Özellik kümesi, eğitim verilerinde kategori kümesini temel alan doğrusal bir modeli eğiteetmek için kullanılır. Daha benzer yeni bir açıklama, eğitim kümesindeki diğer bir deyişle, aynı kategoriye daha büyük olasılıkla atanır. 

![Metin sınıflandırması modeli](./media/text-classification-model.svg)

Hem ev fiyat modeli hem de metin sınıflandırma modeli **Doğrusal** modellerdir. Verilerinizin yapısına ve çözmeyle ilgili soruna bağlı olarak, **karar ağacı** modellerini, **Genelleştirilmiş** ek modellerini ve diğerlerini de kullanabilirsiniz. [Görevler](./resources/tasks.md)' de modeller hakkında daha fazla bilgi edinebilirsiniz.

## <a name="data-preparation"></a>Veri hazırlama

Çoğu durumda, kullanılabilir olan veriler makine öğrenimi modelini eğitmek için doğrudan kullanılmaya uygun değildir. Ham verilerin, modelinizin parametrelerini bulmak için kullanılmadan önce hazırlanması veya önceden işlenmesi gerekir. Verilerinizin dize değerlerinden sayısal bir gösterimine dönüştürülmesi gerekebilir. Giriş verilerinizde gereksiz bilgilere sahip olabilirsiniz. Giriş verilerinizin boyutlarını azaltmanız veya genişletmeniz gerekebilir. Verilerinizin normalleştirilmesi veya ölçeklendirilmesi gerekebilir.

[Ml.net öğreticileri](./tutorials/index.md) , belirli makine öğrenimi görevleri için kullanılan metin, görüntü, sayısal ve zaman serisi verileri için farklı veri işleme işlem hatları hakkında bilgi öğretin.

Verilerinizi [hazırlamak](./how-to-guides/prepare-data-ml-net.md) , veri hazırlığının daha genel olarak nasıl uygulanacağını gösterir.

Kaynaklar bölümünde tüm [kullanılabilir dönüşümlerinin](./resources/transforms.md) bir özetini bulabilirsiniz.

## <a name="model-evaluation"></a>Modeli değerlendirme

Modelinizi eğittikten sonra, gelecekteki tahminleri ne kadar iyi hale getirmek istediğinizi nasıl anlarsınız? ML.NET ile modelinizi bazı yeni test verileri için değerlendirebilirsiniz. 

Her makine öğrenimi görevi türü, modelin doğruluğunu ve duyarlığını test veri kümesine karşı değerlendirmek için kullanılan ölçümlere sahiptir.

Evin fiyat örneğimiz için **regresyon** görevini kullandık. Modeli değerlendirmek için, özgün örneğe aşağıdaki kodu ekleyin.

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

Değerlendirme ölçümleri, hatanın düşük bir şekilde olduğunu ve tahmin edilen çıkış ile test çıkışı arasındaki bağıntıdan yüksek olduğunu söyler. Bu çok kolay! Gerçek örneklerde, iyi model ölçümleri elde etmek için daha fazla ayarlama yapılır.

## <a name="mlnet-architecture"></a>ML.NET mimarisi

Bu bölümde, ML.NET mimari desenlerine gideceğiz. Deneyimli bir .NET geliştiricisiyseniz, bu desenlerden bazıları size tanıdık gelecektir ve bazıları daha az tanıdık olacaktır. Sıkı bir şekilde tutun.

Bir ml.NET uygulaması bir <xref:Microsoft.ML.MLContext> nesneyle başlar. Bu tekil nesne **kataloglar**içerir. Katalog, veri yükleme ve kaydetme, dönüşümler, tracılar ve model işlemi bileşenlerine yönelik bir fabrikadır. Her Katalog nesnesi farklı bileşen türlerini oluşturma yöntemlerine sahiptir:

|||||
|-|-|-|-|
|Veri yükleme ve kaydetme||<xref:Microsoft.ML.DataOperationsCatalog>||
|Veri hazırlama||<xref:Microsoft.ML.TransformsCatalog>||
|Eğitim algoritmaları|İkili sınıflandırma|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||Birden çok Lass sınıflandırması|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||Anomali algılama|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||Lenmesi|<xref:Microsoft.ML.ClusteringCatalog>||
||Tahmin etme|<xref:Microsoft.ML.ForecastingCatalog>||
||Sıralamasına|<xref:Microsoft.ML.RankingCatalog>||
||Regresyon|<xref:Microsoft.ML.RegressionCatalog>||
||Öneri|<xref:Microsoft.ML.RecommendationCatalog>|`Microsoft.ML.Recommender` NuGet paketini ekleme|
||Zaman serisi|<xref:Microsoft.ML.TimeSeriesCatalog>|`Microsoft.ML.TimeSeries` NuGet paketini ekleme|
|Model kullanımı ||<xref:Microsoft.ML.ModelOperationsCatalog>||

Yukarıdaki kategorilerin her birinde oluşturma yöntemlerine gidebilirsiniz. Visual Studio 'yu kullanarak kataloglar IntelliSense aracılığıyla gösterilir.

   ![Gerileme Eğitiminleri için IntelliSense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>İşlem hattını oluşturma

Her kataloğun içinde bir genişletme yöntemleri kümesidir. Bir eğitim işlem hattı oluşturmak için uzantı yöntemlerinin nasıl kullanıldığına göz atalım.

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

Kod parçacığında `Concatenate` ve `Sdca` her iki yöntemde de bulunur. Bunlar, işlem hattının sonuna eklenen bir [ıestimator](xref:Microsoft.ML.IEstimator%601) nesnesi oluşturur.

Bu noktada, nesneler yalnızca oluşturulur. Yürütme yapılmadı.

### <a name="train-the-model"></a>Modeli eğitme

İşlem hattındaki nesneler oluşturulduktan sonra, modeli eğitebilmeniz için veriler kullanılabilir.

```csharp
    var model = pipeline.Fit(trainingData);
```

Çağırma `Fit()` , modelin parametrelerini tahmin etmek için giriş eğitim verilerini kullanır. Bu, modeli eğitme olarak bilinir. Yukarıdaki doğrusal regresyon modelinin iki model parametresi olduğunu unutmayın: **sapma** ve **Ağırlık**. `Fit()` Çağrıdan sonra parametrelerin değerleri bilinmektedir. Çoğu modelde bundan çok daha fazla parametre olacaktır.

[Modelinizi eğitme](./how-to-guides/train-machine-learning-model-ml-net.md) hakkında daha fazla bilgi için model eğitimi hakkında daha fazla bilgi edinebilirsiniz

Elde edilen model nesnesi <xref:Microsoft.ML.ITransformer> arabirimini uygular. Diğer bir deyişle, model giriş verilerini tahmine göre dönüştürür.

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>Modeli kullanma

Giriş verilerini toplu olarak veya bir girişte tek seferde tahmin edilecek şekilde dönüştürebilirsiniz. Ev fiyatı örneğinde, her ikisi de, modeli değerlendirmek amacıyla toplu olarak ve yeni bir tahmin oluşturmak için bir seferde bir kez yaptık. Tek tahmin yapmaya bakalım.

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```
 
`CreatePredictionEngine()` Yöntemi bir giriş sınıfı ve bir çıkış sınıfı alır. Alan adları ve/veya kod öznitelikleri, model eğitimi ve tahmin sırasında kullanılan veri sütunlarının adlarını belirlenir. Nasıl yapılır bölümünde [tek bir tahmin yapma](./how-to-guides/single-predict-model-ml-net.md) hakkında bilgi edinebilirsiniz.

### <a name="data-models-and-schema"></a>Veri modelleri ve şema

Bir ML.NET Machine Learning işlem hattının Core 'da [DataView](xref:Microsoft.ML.IDataView) nesneleri bulunur.

İşlem hattındaki her dönüşümde bir giriş şeması (veri adları, türler ve boyutlar, dönüştürmenin girişte görmeyi beklediği boyutlar) vardır; ve bir çıkış şeması (veri adları, türler ve dönüşümün dönüşümden sonra ürettiği boyutlar). Aşağıdaki belge, [ıdataview arabiriminin ve tür sisteminin](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html)ayrıntılı bir açıklamasını sunmaktadır.

İşlem hattındaki bir dönüşümden çıkış şeması, sonraki dönüşümün giriş şemasıyla eşleşmiyorsa, ML.NET bir özel durum oluşturur.

Veri görünümü nesnesinin sütunları ve satırları vardır. Her sütunun bir adı ve bir türü ve uzunluğu vardır. Örneğin: ev fiyatı örnekteki giriş sütunları **Boyut** ve **fiyattır**. Bunlar her ikisi de aynıdır ve vektörler yerine skaler miktarlardır.

   ![ML.NET veri görünümü örneği, ev fiyatı tahmin verileri](./media/ml-net-dataview.png)

Tüm ML.NET algoritmaları vektör olan bir giriş sütununu arar. Varsayılan olarak bu vektör sütununa **Özellikler**denir. Bu nedenle, **Boyut** sütununu, evin fiyat örneğimizde **Özellikler** adlı yeni bir sütuna bitiştirtik.

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

Tüm algoritmalar Ayrıca bir tahmin gerçekleştirildikten sonra yeni sütunlar oluşturur. Bu yeni sütunların sabit adları makine öğrenimi algoritmasının türüne bağlıdır. Regresyon görevi için, yeni sütunlardan birine **puan**denir. Bu nedenle fiyat verilerimizi bu adla ekledik.

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

[Machine Learning görevler](resources/tasks.md) kılavuzunda, farklı makine öğrenimi görevlerinin çıkış sütunları hakkında daha fazla bilgi edinebilirsiniz.

DataView nesnelerinin önemli bir özelliği, **geç**değerlendirilmesinden kaynaklanmaktadır. Veri görünümleri yalnızca model eğitimi ve değerlendirmesi sırasında yüklenir ve üzerinde çalıştırılır ve veri tahmini yapılır. ML.NET uygulamanızı yazarken ve test ederken, [Önizleme](xref:Microsoft.ML.DebuggerExtensions.Preview*) yöntemini çağırarak herhangi bir veri görünümü nesnesine bir göz atma işlemleri yapmak Için Visual Studio hata ayıklayıcısını kullanabilirsiniz.

```csharp
    var debug = testPriceDataView.Preview();
```

`debug` Değişkeni hata ayıklayıcıda izleyebilir ve içeriğini inceleyebilirsiniz. Performansı önemli ölçüde düşürür, üretim kodunda önizleme yöntemini kullanmayın.

### <a name="model-deployment"></a>Model dağıtımı

Gerçek yaşam uygulamalarında, model eğitimi ve değerlendirme kodunuz tahmininizden ayrı olacaktır. Aslında, bu iki etkinlik genellikle ayrı takımlar tarafından gerçekleştirilir. Model geliştirme ekibiniz, modeli tahmin uygulamasında kullanım için kaydedebilir.

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a>Şimdi nereden?

[Öğreticilerde](./tutorials/index.md)daha gerçekçi veri kümeleriyle farklı makine öğrenimi görevleri kullanarak nasıl uygulama oluşturacağınızı öğrenebilirsiniz.

Ya da [nasıl yapılır kılavuzlarında](./how-to-guides/index.md)daha ayrıntılı bilgi edinmek için belirli konular hakkında bilgi edinebilirsiniz.

Süper KEDE kullanıyorsanız, [API başvuru belgelerine](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)doğrudan gidebilirsiniz!
