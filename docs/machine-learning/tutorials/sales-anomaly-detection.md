---
title: 'Öğretici: Ürün satış anomalileri algılayın'
description: Ürün satış verileri için anomali algılama uygulama oluşturmayı öğrenin. Bu öğreticide, bir .NET Core konsol uygulaması kullanarak oluşturur C# Visual Studio 2019 içinde.
ms.date: 06/11/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 3e3e368ed3bcb35e7e2c8bdf08abe71afd4ae87c
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306223"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a>Öğretici: ML.NET ile ürün satış anomalileri algılayın

Ürün satış verileri için anomali algılama uygulama oluşturmayı öğrenin. Bu öğreticide, bir .NET Core konsol uygulaması kullanarak oluşturur C# Visual Studio'da.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * Verileri yükleme
> * Depo anomali algılama için modeli eğitme
> * Eğitilen modeli ile depo anomalileri algılayın
> * Değişiklik noktası anomali algılama için modeli eğitme
> * Eğitilen modeli ile değişiklik noktası anomalileri algılayın

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) depo.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

* [Ürün sales.csv veri kümesi](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Verileri biçiminde `product-sales.csv` "Shampoo satış üzerinden bir üç yıl boyunca" Başlangıçta Datamarket'ten kaynaklıdır ve sağlanan veri kümesinde tarafından zaman serisi verileri kitaplığı (Rob Hyndman tarafından oluşturulan TSDL), temel alır. DataMarket varsayılan Open Lisansı altında lisanslı "Sales üç yıl boyunca shampoo" veri kümesi.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Oluşturma bir **.NET Core konsol uygulaması** "ProductSalesAnomalyDetection" denir.

2. Adlı bir dizin oluşturmak *veri* , projenizdeki veri kümesi dosyalarınızı kaydeder.

3. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**seçin **v1.0.0** paketini listede bulun ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz. Bu adımı yineleyin **Microsoft.ML.TimeSeries v0.12.0**.

4. Aşağıdaki `using` en üstündeki deyimleri, *Program.cs* dosyası:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Verilerinizi indirin

1. Veri kümesini indirin ve kaydetmesi *veri* daha önce oluşturduğunuz klasör:

   * Sağ tıklayın [ *ürün sales.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) seçip "bağlantısına (veya hedef) olarak kaydedin. …"

     Ya da kaydettiğinizden emin olun \*.csv dosyasına *veri* klasöründe veya başka bir yerde kaydettikten sonra taşıma \*.csv dosyasına *veri* klasör.

2. Çözüm Gezgini'nde sağ \*.csv dosyasını seçip alt **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

Aşağıdaki tabloda, bir veri Önizlemesi'nden vardır, \*.csv dosyası:

|Ay  |ProductSales |
|-------|-------------|
|1 Ocak  |    271      |
|2 - Ocak  |    150.9    |
|.....  |    .....    |
|1 Şubat  |    199.3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Yollarını tanımlamak ve sınıfları oluşturma

Ardından, girdi sınıfı data yapınız tanımlayın.

Yeni bir sınıf, projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle > Yeni öğe**.

2. İçinde **Yeni Öğe Ekle iletişim kutusu**seçin **sınıfı** değiştirip **adı** alanı *ProductSalesData.cs*. Ardından, **Ekle** düğmesi.

*ProductSalesData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *ProductSalesData.cs*:

```csharp
using Microsoft.ML.Data;
```

Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `ProductSalesData` ve `ProductSalesPrediction`, *ProductSalesData.cs* dosyası:

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

`ProductSalesData` bir giriş veri sınıfı belirtir. [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği (sütun dizini tarafından) veri kümesindeki sütunları yüklenmesi gerektiğini belirtir. 

Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

En son indirilen veri kümesi dosyası yolu ve kayıtlı modeli dosya yolu tutmak için iki genel alanlar oluşturmak ihtiyacınız vardır:

* `_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.
* `_docsize` veri kümesi dosyasında kayıt sayısını içeriyor. Bu hesaplamak için kullanacağınız `pvalueHistoryLength`.

Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollarını belirtmek için:

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

[MLContext sınıfı](xref:Microsoft.ML.MLContext) bir tüm ML.NET işlemleri için başlangıç noktası ve başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur. Bu, kavramsal olarak, benzer `DBContext` Entity Framework.

### <a name="initialize-variables-in-main"></a>Ana değişkenleri başlatma

Değiştirin `Console.WriteLine("Hello World!")` satırına `Main` bildirmek ve başlatmak için aşağıdaki kod ile yöntemi `mlContext` değişkeni:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a>Verileri yükleme

ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.ML.IDataView). `IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur. Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne. Sonraki satırı olarak aşağıdaki kodu ekleyin `Main()` yöntemi:

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur. Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`.

## <a name="ml-task---time-series-anomaly-detection"></a>ML görevi - zaman serisi anomali algılama 

Anomali algılama, olağan dışı ya da beklenmeyen olaylar veya davranışları işaretler. Bu sorunları ve yardımcı soruyu yanıtlamak için "Bu tuhaf nedir?" aranacağı ipuçları sağlar.

![Bu tuhaf mi](./media/sales-anomaly-detection/anomalydetection.png)

Anomali algılama zaman serisi verilerini aykırı değerleri algılama işlemidir; bir verilen giriş zaman serisi hakkında burada beklenen bir davranış değildir veya "tuhaf" işaret eder.

Bu şekilde çok sayıda yararlı olabilir. Örneğin:

Bir araba varsa bilmek isteyebilirsiniz: Bu Petrol ölçer normal okuma veya sızıntı sahip mi?
Güç tüketimini izliyorsanız bilmek istersiniz: Kesinti var mı?

Algılanabilir zaman serisi anomalileri iki tür vardır: 

* **Ani artışlar** sistemde geçici artışları anormal davranışları gösterir. 

* **Değiştirme noktaları** sistemde zaman içinde kalıcı değişiklikler başlangıcını gösterir. 

ML.NET içinde IID depo algılama veya işaret IID değişiklik algılama algoritmalarını için uygun [bağımsız ve aynı şekilde Dağıtılmış veri kümeleri](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables). 

Ani algılamak ve değişim noktaları için aynı ürün satış verilerini analiz etmek. Oluşturmanın ve eğitim modeli işlemi depo algılama ve değişiklik noktası algılama ile aynıdır; ikisi arasındaki temel fark, kullanılan belirli algılama algoritmasıdır.

## <a name="spike-detection"></a>Depo algılama 

Hedef depo algılama zaman serisi veri değerleri büyük çoğunluğu önemli ölçüde farklılık ani henüz geçici artışları belirlemektir. Bu şüpheli nadir öğeleri, olayları veya gözlemleri küçültülmesine için zamanında algılamak önemlidir. Aşağıdaki yaklaşımı gibi çeşitli anomalileri algılamak için kullanılabilir: kesintiler, siber saldırılardan veya viral web içeriği. Aşağıdaki görüntüde, ani bir zaman serisi veri kümesi örneğidir:

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a>DetectSpike() yöntemi oluşturma

Aşağıdaki çağrısı ekleyin `DetectSpike()`yöntemi sonraki kod satırı olarak `Main()` yöntemi:

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

`DetectSpike()` Yöntemi aşağıdaki görevleri yürütür:

* Modeli eğitir.
* Geçmiş satış verilerini temel alarak ani değişiklikleri algılar.
* Sonuçları görüntüler.

Oluşturma `DetectSpike()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

Kullanım [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) Depo'yu algılamak için modeli eğitmek için. Ekleyin `DetectChangepoint()` yöntemini aşağıdaki kod ile:

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

Modele uygun `productSales` sonraki kod satırı olarak aşağıdakileri ekleyerek veri `DetectSpike()` yöntemi:

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

[Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.

Kod dönüştürmek için aşağıdaki satırı ekleyin `productSales` sonraki satırı olarak veri `DetectSpike()` yöntemi:

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

Önceki kod [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) birden çok test veri kümesini girdi satırları sağlanan için tahminde bulunmak için yöntemi.

Dönüştürme, `transformedData` türü kesin belirlenmiş bir içine `IEnumerable` kullanarak daha kolay görüntüleme için [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) yöntemini aşağıdaki kod ile:

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

Aşağıdakileri kullanarak görünen üst bilgi satırı oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

Depo algılama sonuçlarınızı aşağıdaki bilgileri görüntüleyeceksiniz:

* `Alert` verilen veri noktası için bir depo uyarı gösterir.

* `Score` olan `ProductSales` kümesindeki belirli bir veri noktası değeri.

* `P-Value` "P" olasılık anlamına gelir. Bu nasıl büyük olasılıkla bu veri noktasına bir anomali olduğunu gösterir. 

Yinelemek için aşağıdaki kodu kullanın `predictions` `IEnumerable` ve sonuçları görüntüler:

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a>Depo algılama sonuçları

Sonuçlar aşağıdakine benzer olmalıdır. İşleme sırasında iletileri görüntülenir. Uyarıları ve iletileri işlemeyi görebilirsiniz. Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a>Değişiklik noktası algılama

`Change points` Düzey değişiklikleri ve eğilimleri gibi bir değerler zaman serisi olay akışı dağıtımı kalıcı değişiklikler var. Bu kalıcı değişiklikler çok son daha uzun `spikes` ve yıkıcı olaylar olduğunu gösteriyor olabilir. `Change points` genellikle çıplak gözle görünür değildir, ancak aşağıdaki yöntemi olduğu gibi bu yaklaşımları kullanarak veri algılandı.  Aşağıdaki resimde, bir değişiklik noktası algılama örneğidir:

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a>DetectChangepoint() yöntemi oluşturma

Aşağıdaki çağrısı ekleyin `DetectChangepoint()`yöntemi sonraki kod satırı olarak `Main()` yöntemi:

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

`DetectChangepoint()` Yöntemi aşağıdaki görevleri yürütür:

* Modeli eğitir.
* Değişim noktaları geçmiş satış verilerine göre algılar.
* Sonuçları görüntüler.

Oluşturma `DetectChangepoint()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

[İidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) değişiklik noktası algılama modeli eğitmek için kullanılır. Ekleyin `DetectChangepoint()` yöntemini aşağıdaki kod ile:

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

Daha önce yaptığınız gibi modele uygun `productSales` sonraki kod satırı olarak aşağıdakileri ekleyerek veri `DetectChangePoint()` yöntemi:

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

Kullanım `Transform()` dönüştürmek için yöntemi `Training` aşağıdakileri ekleyerek veri kod için `DetectChangePoint()`:

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

Daha önce yaptığınız gibi dönüştürme, `transformedData` türü kesin belirlenmiş bir içine `IEnumerable` kullanarak daha kolay görüntüleme için `CreateEnumerable()`yöntemini aşağıdaki kod ile:

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

Sonraki satırda olarak aşağıdaki kod ile bir görüntü başlığı oluşturun `DetectChangePoint()` yöntemi:

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

Değişiklik noktası algılama sonuçlarınızı aşağıdaki bilgileri görüntüleyeceksiniz:

* `Alert` verilen veri noktası için bir değişiklik noktası uyarısı gösterir.
* `Score` olan `ProductSales` kümesindeki belirli bir veri noktası değeri.
* `P-Value` "P" olasılık anlamına gelir. Bu nasıl büyük olasılıkla bu veri noktasına bir anomali olduğunu gösterir. 
* `Martingale value` "tuhaf" bir veri noktasına nasıl olduğunu belirlemek için kullanılan, P-değerlerinin sıralarına göre.  

Yinelemek `predictions` `IEnumerable` ve aşağıdaki kodla sonuçları görüntüleyin:

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a>Değişiklik noktası algılama sonuçları

Sonuçlar aşağıdakine benzer olmalıdır. İşleme sırasında iletileri görüntülenir. Uyarıları ve iletileri işlemeyi görebilirsiniz. Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

Tebrikler! Artık ani değişiklikleri algılama için machine learning modellerini başarıyla oluşturduktan ve satış veri noktası anomalileri değiştirin.

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) depo.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> * Verileri yükleme
> * Depo anomali algılama için modeli eğitme
> * Eğitilen modeli ile depo anomalileri algılayın
> * Değişiklik noktası anomali algılama için modeli eğitme
> * Eğitilen moduyla değişiklik noktası anomalileri algılayın

## <a name="next-steps"></a>Sonraki adımlar

Bir güç tüketimi Anomali algılama örnek keşfetmek için Machine Learning örnekleri GitHub havuzuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/machinelearning-samples GitHub deposu](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
