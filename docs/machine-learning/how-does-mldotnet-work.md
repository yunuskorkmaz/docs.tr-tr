---
title: ML.NET nedir ve nasıl çalışır?
description: ML.NET machine Learning'i .NET uygulamalarına ekleme olanağı sunar. Bu özellik sayesinde, uygulamanızın kullanabileceği verileri kullanarak otomatik tahmin yapabilirsiniz. Bu makalede, makine öğrenimi ML.NET temelleri açıklanır.
ms.date: 04/10/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 30e96d85ecc04332bc5e6c8f57badd000f729904
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660643"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>ML.NET nedir ve nasıl çalışır?

ML.NET machine Learning'i .NET uygulamalarına ekleme olanağı sunar. Bu özellik sayesinde, uygulamanızın kullanabileceği verileri kullanarak otomatik tahmin yapabilirsiniz. Bu makalede, makine öğrenimi ML.NET temelleri açıklanır. 

ML.NET ile yapabileceğiniz Öngörüler türü örnekleri şunlardır:

|||
|-|-|
|Sınıflandırma/kategorilere ayırma|Müşteri geri bildirimi pozitif ve negatif kategoriler halinde otomatik olarak Böl|
|Regresyon/Predıct sürekli değerleri|Görev açısından kritik uygulamaları boyutu ve konuma bağlı fiyatını tahmin edin|
|Anomali Algılama|Sahte bankacılık işlemleri algılayın |
|Öneriler|Önceki aldıklarını temel satın almak için çevrimiçi bir adamın isteyebileceğiniz ürünler önerin|

## <a name="hello-mlnet-world"></a>ML.NET World Hello

Aşağıdaki kod parçacığında kod basit ML.NET uygulamayı gösterir. Bu örneği kullanarak merkezi boyutu ve fiyat veri merkezi fiyatlarını tahmin etmek için bir doğrusal regresyon modeli oluşturur. Gerçek zamanlı konuşmaların uygulamalarınızı, verilerinizi ve model çok daha karmaşık olacaktır.

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

## <a name="code-workflow"></a>İş akışı kodu

Aşağıdaki diyagramda, yinelemeli model geliştirme sürecinin yanı sıra uygulama kod yapısını temsil eder:
- Toplama ve yük eğitim verilerini bir **IDataView** nesnesi
- İşlem özellikleri ayıklayın ve makine öğrenme algoritmasına uygulamak için bir işlem hattı belirtin
- Çağırarak bir model eğitip **Fit()** işlem hattında
- Modeli değerlendirme ve geliştirmek için yineleme
- Model kullanmak bir uygulamada ikili biçimde kaydedin
- Modeline geri yüklemek bir **ITransformer** nesnesi
- Çağırarak tahminlerde **CreatePredictionEngine.Predict()**

![ML.NET verisi oluşturma, ardışık düzen geliştirme, model eğitiminin, model değerlendirme ve model kullanımı için bileşenler dahil olmak üzere uygulama geliştirme akışı](./media/mldotnet-annotated-workflow.png) 

Biraz söz konusu kavrama biraz daha ayrıntılı açıklayalım.

## <a name="machine-learning-model"></a>Machine learning modeli

ML.NET modeli tahmin edilen çıktısına gelmesi giriş verileriniz üzerinde gerçekleştirmek için dönüşümleri içeren bir nesnedir.

### <a name="basic"></a>Temel

En temel iki boyutlu doğrusal regresyon, sürekli bir miktar yukarıdaki ev fiyat örnekte olduğu gibi başka orantılı olduğu modelidir. 

![Doğrusal regresyon modeli sapması ve Ağırlık parametrelere sahip](./media/linear-regression-model.svg)

Yalnızca modelidir: $Price = b + boyutu * w$. Bir dizi üzerinde bir uydurur $w$ ve parametreleri $b$ tahmini (boyut, Fiyat) çiftleri. Model parametreleri bulmak için kullanılan verileri çağrılır **eğitim verilerini**. Makine öğrenme modeli girişleri olarak adlandırılan **özellikleri**. Bu örnekte, $Size$ yalnızca özelliğidir. Machine learning modelini eğitmek için kullanılan taban truth değerler olarak adlandırılan **etiketleri**. Burada, $Price$ eğitim veri kümesi etiketleri değerler.

### <a name="more-complex"></a>Daha karmaşık

Daha karmaşık bir model kullanarak işlem metin açıklama kategoriler halinde Finansal işlemler sınıflandırır.

Her bir işlem açıklaması bir özellikler kümesi yedekli sözcükler ve karakterleri kaldırarak ve word ve karakter birleşimini sayım ayrılmıştır. Özellik kümesini kategorileri eğitim veri kümesi temel olarak doğrusal bir model eğitip için kullanılır. Daha yeni bir açıklama için Eğitim kümesi dışındaki benzer, büyük olasılıkla aynı kategoriye atanır. 

![Metin sınıflandırma modeli](./media/text-classification-model.svg)

Hem merkezi fiyat modeli, hem de metin sınıflandırma modeli **doğrusal** modelleri. Verilerinizi ve Çözdüğünüz sorunun doğasına bağlı olarak da kullanabilirsiniz **karar ağacı** modelleri **eklenebilir genelleştirilmiş** modelleri ve diğerleri. Modelleri hakkında daha fazla bilgi bulabilirsiniz [görevleri](./resources/tasks.md).

## <a name="data-preparation"></a>Veri hazırlama

Çoğu durumda veriler kullanılabilir olduğunu doğrudan makine öğrenme modeli eğitmek için kullanılacak uygun değildir. Ham verileri hazırlanmış veya modelinizin parametreleri bulmak için kullanılmadan önce ön işlemden gerekir. Verilerinizi dize değerlerden bir sayısal gösterimine dönüştürülmesi gerekebilir. Girdi verilerinizi yedekli bilgiler olabilir. Azaltın veya girişinizi boyutlarını genişletin gerekebilir. Verilerinizi normalleştirilmiş veya ölçeklendirildiğinde gerekebilir.

[ML.NET öğreticiler](./tutorials/index.md) görüntü farklı veri işleme komut zincirini metin için ilgili öğretin, belirli bir makine öğrenimi görevlerini için kullanılan sayısal ve zaman serisi verileri.

[Verilerinizi hazırlama](./how-to-guides/prepare-data-ml-net.md) gösterilmektedir veri hazırlama daha genel olarak uygulanır.

Tüm ek bulabilirsiniz [kullanılabilir dönüştürmeler](./resources/transforms.md) kaynaklar bölümünde.

## <a name="model-evaluation"></a>Modeli değerlendirme

Nasıl modelinizi eğitim almış sonra ne kadar iyi gelecekteki tahminler yapar biliyor musunuz? ML.NET ile modelinizi yeni bazı test verilerini karşı değerlendirebilirsiniz. 

Machine learning görevinin her türü doğruluk ve sınama veri kümesi modelinde duyarlığını değerlendirmek için kullanılan ölçümü mevcuttur.

Ev fiyat Örneğimiz için kullandığımız **regresyon** görev. Modeli değerlendirme için özgün örneğe aşağıdaki kodu ekleyin.

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

Değerlendirme ölçümleri low-ish bir hatadır ve bu bağıntı tahmin edilen çıkış ve test çıkışı arasında yüksek olduğunu bildirin. Bu kadar kolay! Gerçek örneklerde, daha fazla iyi model ölçümleri elde etmek için ayarlama alır.

## <a name="mlnet-architecture"></a>ML.NET mimarisi

Bu bölümde, biz ML.NET Mimari desenleri gidin. Deneyimli bir .NET geliştiricisi kullanıyorsanız, bu desenleri bazıları size tanıdık gelecektir ve bazı küçük tanıdık gelecektir. Biz kolları sıvayın sıkı, basılı!

ML.NET uygulama ile başlayan bir <xref:Microsoft.ML.MLContext> nesne. Bu tekil nesnesini içeren **katalogları**. Veri yükleme ve kaydetme, dönüşümler ve Eğitmenler modeli işlemi bileşenleri için bir üreteci kataloğudur. Her bir katalog nesnesi bileşenleri farklı türleri oluşturmak için yöntemleri vardır:

|||||
|-|-|-|-|
|Veri yükleme ve kaydetme||<xref:Microsoft.ML.DataOperationsCatalog>||
|Veri hazırlama||<xref:Microsoft.ML.TransformsCatalog>||
|Eğitim algoritmaları|İkili sınıflandırma|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||Sınıflı sınıflandırma|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||Anomali algılama|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||Kümeleme|<xref:Microsoft.ML.ClusteringCatalog>||
||Tahmin etme|<xref:Microsoft.ML.ForecastingCatalog>||
||Derecelendirme|<xref:Microsoft.ML.RankingCatalog>||
||Regresyon|<xref:Microsoft.ML.RegressionCatalog>||
||Öneri|<xref:Microsoft.ML.RecommendationCatalog>|ekleme `Microsoft.ML.Recommender` NuGet paketi|
||Zaman serisi|<xref:Microsoft.ML.TimeSeriesCatalog>|ekleme `Microsoft.ML.TimeSeries` NuGet paketi|
|Model kullanımı ||<xref:Microsoft.ML.ModelOperationsCatalog>||

Yukarıdaki kategorilerden her biri oluşturma yöntemleri gidebilirsiniz. Visual Studio kullanarak, katalogları IntelliSense gösterilir.

   ![Regresyon Eğitmenler için IntelliSense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>İşlem hattı oluşturma

İçinde her kataloğunu genişletme yöntemleri kümesidir. Genişletme yöntemleri bir eğitim işlem hattı oluşturmak için nasıl kullanılacağını bakalım.

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

Kod parçacığında `Concatenate` ve `Sdca` katalogdaki her iki yöntemlerdir. Oluşturdukları her bir [IEstimator](xref:Microsoft.ML.IEstimator%601) ardışık düzenine eklenen nesne.

Bu noktada, nesneleri yalnızca oluşturulabilir. Hiçbir yürütme gerçekleştirilmedi.

### <a name="train-the-model"></a>Modeli eğitme

İşlem hattı nesneleri için oluşturduktan sonra modeli eğitmek için verilerin kullanılabilir.

```csharp
    var model = pipeline.Fit(trainingData);
```

Çağırma `Fit()` parametreleri modelin tahmin etmek için giriş eğitim verileri kullanır. Bu, modeli eğitmek olarak bilinir. Unutmayın, doğrusal regresyon modelinin Yukarıdaki iki modeli parametre vardı: **sapması** ve **ağırlık**. Sonra `Fit()` çağrısı, parametre değerlerini bilinir. Çoğu modelleri bundan çok daha fazla parametre gerekir.

Model eğitimi hakkında daha fazla bilgi [nasıl modelinizi eğitin](./how-to-guides/train-machine-learning-model-ml-net.md)

Oluşturulan model nesnesi uygulayan <xref:Microsoft.ML.ITransformer> arabirimi. Diğer bir deyişle, model öngörülere giriş verilerini dönüştürür.

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>Kullanım modeli

Giriş verileri aynı anda Öngörüler toplu ya da bir giriş içine dönüştürebilirsiniz. Ev fiyat örnekte, her ikisi de yaptık: model ve yeni bir tahminde bulunmak için birer tane Değerlendirme amacıyla toplu. Tek Öngörüler kolaylaştırmayı bakalım.

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```
 
`CreatePredictionEngine()` Yöntemi, bir giriş ve çıkış sınıfı alır. Alan adları ve/veya kod öznitelikleri model eğitim ve tahmin sırasında kullanılan veri sütunlarının adlarını belirleyin. Okuyabilirsiniz [tek bir tahminde bulunmak nasıl](./how-to-guides/single-predict-model-ml-net.md) bölümünde yapılır.

### <a name="data-models-and-schema"></a>Veri modelleri ve şema

Bir ML.NET makine öğrenimi işlem hattı özünde olan [DataView](xref:Microsoft.ML.IDataView) nesneleri.

İşlem hattındaki her dönüştürme bir giriş şeması (veri adları, türleri ve boyutları dönüştürme hücredeki girişe göre görmek için beklediği); sahip ve bir çıkış şeması (veri adları, türleri ve sonra dönüştürme dönüştürme üreten boyutları). 

ML.NET, işlem hattındaki bir dönüşüm çıkış şemasından sonraki dönüştürme giriş şemasını eşleşmiyorsa bir özel durum oluşturur.

Veri Görünümü nesnesi satırları ve sütunları vardır. Her sütun bir ad ve bir tür ve bir süre vardır. Örneğin: ev fiyat örnekte giriş sütunlar **boyutu** ve **fiyat**. Bunlar olan hem de yazın ve bunlar skaler miktarlarının yerine olanları vektör.

   ![Ev fiyatı tahmin verileriyle ML.NET veri görünümü örneği](./media/ml-net-dataview.png)

Tüm ML.NET algoritmalar bir vektördür bir giriş sütun arayın. Varsayılan olarak bu vektörü sütun çağrılır **özellikleri**. Biz birleştirilmiş bu yüzden **boyutu** adlı yeni bir sütun sütununa **özellikleri** ev fiyat örneğimizde.

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

Tahmin gerçekleştirmemiş olan sonra tüm algoritmaları da yeni bir sütun oluşturun. Bu yeni sütunların sabit adları, makine öğrenme algoritmasına türüne bağlıdır. Regresyon görev için yeni sütunlar birini çağrılır **puanı**. Biz bu ada sahip fiyat verilerimizi öznitelikli nedeni budur.

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

Çıkış sütunları farklı makine öğrenimi görevleri hakkında daha fazla bilgi bulabilirsiniz [makine öğrenimi görevlerini](resources/tasks.md) Kılavuzu.

DataView önemli bir özelliği nesnelerindeki değerlendirilme **gevşek**. Veri görünümleri yalnızca yüklenir ve üzerinde model eğitim ve değerlendirme ve veri tahmin sırasında işletilir. Yazma ve ML.NET uygulamanızı test ederken, Visual Studio hata ayıklayıcısını çağırarak herhangi bir veri görünümü nesne göz atalım için kullanabileceğiniz [Önizleme](xref:Microsoft.ML.DebuggerExtensions.Preview*) yöntemi.

```csharp
    var debug = testPriceDataView.Preview();
```

İzleyebilir `debug` hata ayıklayıcı değişken ve içeriğini inceleyin. Önemli ölçüde performansı düşürür gibi üretim kodunda Önizleme yöntemi kullanmayın.

### <a name="model-deployment"></a>Model dağıtımı

Gerçek zamanlı konuşmaların uygulamalarda, model eğitimi ve değerlendirmesi kodunuzu tahmininizde ayrı olacaktır. Aslında, bu iki etkinliği genellikle ayrı takımlar tarafından gerçekleştirilir. Model Geliştirme ekibiniz, tahmin uygulama modelini kullanmak için kaydedebilirsiniz.

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a>Şimdi nereye?

Daha gerçekçi veri kümelerinde farklı makine öğrenimi görevlerini kullanarak uygulamaları nasıl oluşturabileceğinizi öğrenebilirsiniz [öğreticiler](./tutorials/index.md).

Veya belirli konuları bölümünde daha ayrıntılı olarak hakkında bilgi edinebilirsiniz [nasıl yapılır kılavuzları](./how-to-guides/index.md).

Ve Süper içeriğimizi, düz içine başlayabilirsiniz [API başvuru belgeleri](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!
