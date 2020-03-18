---
title: 'Öğretici: Ürün satışlarındaki anormallikleri tespit edin'
description: Ürün satış verileri için bir anomali algılama uygulaması oluşturmayı öğrenin. Bu öğretici, Visual Studio 2019'da C# kullanarak bir .NET Core konsol uygulaması oluşturur.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: c3fd4aa715a64a20f1eff9b789f6a87eaa749163
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78239995"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a>Öğretici: ML.NET ile ürün satışlarında anormallikleri tespit

Ürün satış verileri için bir anomali algılama uygulaması oluşturmayı öğrenin. Bu öğretici Visual Studio'da C# kullanarak bir .NET Core konsol uygulaması oluşturur.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> * Verileri yükleme
> * Ani anomali tespiti için dönüşüm oluşturun
> * Dönüşüm ile ani anomalileri tespit edin
> * Değişim noktası anomali tespiti için dönüşüm oluşturma
> * Dönüşüm ile değişim noktası anomalileri tespit

Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.

* [Product-sales.csv veri kümesi](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> Veri formatı, `product-sales.csv` "Şampuan Satışları Üç Yıllık Bir Dönem Boyunca" veri setine dayanmaktadır ve başlangıçta DataMarket'ten temin edilir ve Rob Hyndman tarafından oluşturulan Time Series Data Library (TSDL) tarafından sağlanır.
> "Üç Yıllık Bir Süre Boyunca Şampuan Satışları" Dataset DataMarket Varsayılan Açık Lisans altında lisanslı.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "ProductSalesAnomalyDetection" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *Veri* adlı bir dizin oluşturun.

3. Microsoft.ML **NuGet Paketini**Yükleyin:

    Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML** arayın ve **Yükle** düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin. **Microsoft.ML.TimeSeries**için bu adımları yineleyin.

4. `using` *Program.cs* dosyanızın üst kısmında aşağıdaki ifadeleri ekleyin:

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Verilerinizi indirin

1. Veri kümesini indirin ve daha önce oluşturduğunuz *Veri* klasörüne kaydedin:

   * [*Product-sales.csv'ye*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) sağ tıklayın ve "Bağlantıyı Kaydet (veya Hedef) Olarak..." seçeneğini belirleyin.

     .csv dosyasını \* *Veri* klasörüne kaydettiğinizi veya başka bir yere kaydettikten sonra .csv dosyasını \* *Veri* klasörüne taşıdığınızdan emin olun.

2. Çözüm Gezgini'nde .csv dosyasına \*sağ tıklayın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

Aşağıdaki tablo .csv \*dosyanızdan bir veri önizlemesidir:

|Ay  |Ürün Satışları |
|-------|-------------|
|1-Ocak  |    271      |
|2-Ocak  |    150.9    |
|.....  |    .....    |
|1-Şubat  |    199.3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Sınıflar oluşturma ve yolları tanımlama

Ardından, giriş ve tahmin sınıfı veri yapılarınızı tanımlayın.

Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini'nde**projeyi sağ tıklatın ve ardından **Yeni Öğe > ekle'yi**seçin.

2. Yeni **Öğe Ekle iletişim kutusunda,** **Sınıf'ı** seçin ve **Ad** alanını *ProductSalesData.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

   ProductSalesData.cs *ProductSalesData.cs* dosyası kod düzenleyicisinde açılır.

3. ProductSalesData.cs üstüne `using` aşağıdaki ifadeyi *ProductSalesData.cs*ekleyin:

   ```csharp
   using Microsoft.ML.Data;
   ```

4. Varolan sınıf tanımını kaldırın ve iki sınıfı `ProductSalesData` `ProductSalesPrediction`ve ProductSalesData.cs *dosyasına* aşağıdaki kodu ekleyin:

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    `ProductSalesData`bir giriş veri sınıfı belirtir. [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yüklenmesi gerektiğini belirtir.

    `ProductSalesPrediction`tahmin veri sınıfını belirtir. Anomali tespiti için, tahmin bir anomali, ham skor ve p-değeri olup olmadığını belirtmek için bir uyarı oluşur. P değeri 0'a ne kadar yakınsa, bir anomali oluşma olasılığı da o kadar artar.

5. En son indirilen veri kümesi dosya yolunu ve kaydedilen model dosya yolunu tutmak için iki genel alan oluşturun:

    * `_dataPath`modeli eğitmek için kullanılan veri kümesine giden yola sahiptir.
    * `_docsize`dataset dosyasındaki kayıt sayısına sahiptir. Hesaplamak `pvalueHistoryLength`için `_docSize` kullanacaksın.

6. Bu yolları belirtmek için yöntemin `Main` hemen üstündeki satıra aşağıdaki kodu ekleyin:

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>Main'deki değişkenleri başlatma

1. Değişkeni `Console.WriteLine("Hello World!")` `Main` bildirmek ve başlatmak için yöntemdeki satırı `mlContext` aşağıdaki kodla değiştirin:

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    [MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç `mlContext` noktasıdır ve başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur. Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.

### <a name="load-the-data"></a>Verileri yükleme

ML.NET'daki veriler [IDataView sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`tabular verileri (sayısal ve metin) tanımlamanın esnek ve etkili bir yoludur. Veriler bir metin dosyasından veya başka kaynaklardan (örneğin, SQL veritabanı `IDataView` veya günlük dosyaları) bir nesneye yüklenebilir.

1. `Main()` Yöntemin bir sonraki satırı olarak aşağıdaki kodu ekleyin:

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyada okur. Veri yolu değişkenlerini alır ve `IDataView`bir .

## <a name="time-series-anomaly-detection"></a>Zaman serisi anomali tespiti

Anomali algılama, beklenmeyen veya olağandışı olaylar veya davranışlar alabını işaretler. Nerede sorunları aramak için ipuçları verir ve sorusuna cevap yardımcı olur "Bu garip mi?".

!["Bu garip" anomali tespiti örneği.](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

Anomali tespiti, zaman serisi veri aykırılıklarını tespit etme işlemidir; davranışın beklendiği gibi olmadığı veya "garip" olmadığı belirli bir giriş zaman serisine işaret edin.

Anomali tespiti birçok yönden yararlı olabilir. Örneğin:

Eğer bir araba varsa, bilmek isteyebilirsiniz: Bu yağ göstergesi normal okuma, ya da bir sızıntı var mı?
Eğer güç tüketimini izliyorsanız, şunu bilmek istersiniz: Bir kesinti var mı?

Algılanabilen iki tür zaman serisi anomalileri vardır:

* **Ani artışlar** sistemde geçici anormal davranış patlamaları olduğunu gösteriyor.

* **Değişiklik noktaları,** sistemde zaman içinde kalıcı değişikliklerin başlangıcını gösterir.

ML.NET, IID Spike Detection veya IID Change nokta Algılama algoritmaları [bağımsız ve aynı şekilde dağıtılan veri kümeleri](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)için uygundur.

Diğer öğreticilerde modellerin aksine, zaman serisi anomali dedektörü dönüşümleri doğrudan giriş verileri üzerinde çalışır. Dönüştürmeyi `IEstimator.Fit()` üretmek için yöntemin eğitim verilerine ihtiyacı yoktur. Boş bir listeden oluşturulan bir veri görünümü tarafından sağlanan olsa da, `ProductSalesData`veri şeması gerekir.

Ani artışları ve noktaları değiştirmek için aynı ürün satış verilerini analiz ememezsiniz. Bina ve eğitim modeli süreci başak algılama ve değişim noktası algılama için aynıdır; ana fark kullanılan özel algılama algoritmasıdır.

## <a name="spike-detection"></a>Başak algılama

Başak algılamanın amacı, zaman serisi veri değerlerinin çoğundan önemli ölçüde farklı olan ani ama geçici patlamaları belirlemektir. Bu şüpheli nadir öğeleri, olayları veya gözlemleri en aza indirilecek şekilde zamanında tespit etmek önemlidir. Aşağıdaki yaklaşım, kesintiler, siber saldırılar veya viral web içeriği gibi çeşitli anormallikleri tespit etmek için kullanılabilir. Aşağıdaki resim, bir zaman serisi veri kümesindeki ani artışlara bir örnektir:

![İki ani algılama gösteren ekran görüntüsü.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a>CreateEmptyDataView() yöntemini ekleyin

Aşağıdaki yöntemi `Program.cs`ekleyin:

[!code-csharp[CreateEmptyDataView](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEmptyDataView)]

Yönteme `CreateEmptyDataView()` giriş olarak kullanılacak doğru şemaya sahip boş bir veri `IEstimator.Fit()` görünümü nesnesi üretir.

### <a name="create-the-detectspike-method"></a>DetectSpike() yöntemini oluşturma

Yöntem: `DetectSpike()`

* Tahminciden dönüşümü oluşturur.
* Geçmiş satış verilerine göre ani artışlar algılar.
* Sonuçları görüntüler.

1. Yöntemden `DetectSpike()` `Main()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. Modeli ani algılama için eğitmek için [IidSpikeEstimator'u](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) kullanın. Yönteme `DetectSpike()` aşağıdaki kodla ekleyin:

    [!code-csharp[AddSpikeTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddSpikeTrainer)]

1. `DetectSpike()` Yöntemde bir sonraki kod satırı olarak aşağıdakileri ekleyerek başak algılama dönüşümü oluşturun:

    [!code-csharp[TrainModel1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel1)]

1. Yöntemde `productSales` verileri bir sonraki satır olarak dönüştürmek için `DetectSpike()` aşağıdaki kod satırını ekleyin:

    [!code-csharp[TransformData1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData1)]

    Önceki kod, bir veri kümesinin birden çok giriş satırı için öngörüler yapmak için [Dönüştür()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.

1. `transformedData` Aşağıdaki kodla [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) yöntemini kullanarak daha kolay görüntü için güçlü bir şekilde yazılan `IEnumerable` bir ekrana dönüştürün:

    [!code-csharp[CreateEnumerable1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable1)]

1. Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu kullanarak bir ekran üstbilgi satırı oluşturun:

    [!code-csharp[DisplayHeader1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader1)]

    Başak algılama sonuçlarınızda aşağıdaki bilgileri görüntülersiniz:

    * `Alert`belirli bir veri noktası için ani bir uyarı gösterir.
    * `Score`veri `ProductSales` kümesindeki belirli bir veri noktasının değeridir.
    * `P-Value`"P" olasılık anlamına gelir. P değeri 0'a ne kadar yakınsa, veri noktası nın anomali olma olasılığı da o kadar yüksektir.

1. Aşağıdaki kodu kullanarak aşağıdaki kodu `predictions` `IEnumerable` kullanarak sonuçları yineleyin ve görüntüleyin:

    [!code-csharp[DisplayResults1](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults1)]

1. Yöntemde `DetectSpike()`yönteme çağrı `Main()` ekleyin:

    [!code-csharp[CallDetectSpike](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a>Başak algılama sonuçları

Sonuçlarınız aşağıdakilere benzer olmalıdır. İşlem sırasında iletiler görüntülenir. Uyarılar veya iletileri işleme görebilirsiniz. Bazı iletiler netlik için aşağıdaki sonuçlardan kaldırıldı.

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

## <a name="change-point-detection"></a>Nokta algılamayı değiştirme

`Change points`düzey değişiklikleri ve eğilimleri gibi değerlerin zaman serisi olay akışı dağıtımında kalıcı değişikliklerdir. Bu kalıcı değişiklikler çok `spikes` daha uzun sürer ve felaket olay (lar) gösterebilir. `Change points`genellikle çıplak gözle görülemez, ancak aşağıdaki yöntemdeki gibi yaklaşımlar kullanılarak verilerinizde algılanabilir.  Aşağıdaki resim bir değişim noktası algılama örneğidir:

![Değişiklik noktası algılamayı gösteren ekran görüntüsü.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a>DetectChangepoint() yöntemini oluşturma

Yöntem `DetectChangepoint()` aşağıdaki görevleri yürütür:

* Tahminciden dönüşümü oluşturur.
* Geçmiş satış verilerine dayalı değişim noktalarını algılar.
* Sonuçları görüntüler.

1. Yöntemden `DetectChangepoint()` `Main()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. `DetectChangepoint()` Yöntemde aşağıdaki kodla [iidChangePointEstimator'u](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) oluşturun:

    [!code-csharp[AddChangepointTrainer](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#AddChangepointTrainer)]

1. Daha önce yaptığınız gibi, yönteme aşağıdaki kod satırını ekleyerek tahminciden dönüştürmeyi `DetectChangePoint()` oluşturun:

    [!code-csharp[TrainModel2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TrainModel2)]

1. Aşağıdaki `Transform()` kodu ekleyerek verileri dönüştürmek için `DetectChangePoint()`yöntemi kullanın:

    [!code-csharp[TransformData2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#TransformData2)]

1. Daha önce yaptığınız gibi, `transformedData` aşağıdaki kodu kullanarak `IEnumerable` `CreateEnumerable()`yöntemi kullanarak daha kolay görüntü için güçlü bir şekilde yazılan bir görüntüye dönüştürün:

    [!code-csharp[CreateEnumerable2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CreateEnumerable2)]

1. Yöntemde bir sonraki satır olarak aşağıdaki kodu `DetectChangePoint()` içeren bir ekran üstbilgisi oluşturun:

    [!code-csharp[DisplayHeader2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayHeader2)]

    Değişim noktası algılama sonuçlarınızda aşağıdaki bilgileri görüntülersiniz:

    * `Alert`belirli bir veri noktası için bir değişim noktası uyarısı gösterir.
    * `Score`veri `ProductSales` kümesindeki belirli bir veri noktasının değeridir.
    * `P-Value`"P" olasılık anlamına gelir. P değeri 0'a ne kadar yakınsa, veri noktası nın anomali olma olasılığı da o kadar yüksektir.
    * `Martingale value`P-değerlerinin sırasına göre bir veri noktasının ne kadar "garip" olduğunu belirlemek için kullanılır.

1. Sonuçları aşağıdaki kodla titretin `predictions` `IEnumerable` ve görüntüleyin:

    [!code-csharp[DisplayResults2](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#DisplayResults2)]

1. Yöntemde yönteme `DetectChangepoint()`aşağıdaki çağrıyı `Main()` ekleyin:

    [!code-csharp[CallDetectChangepoint](~/samples/snippets/machine-learning/ProductSalesAnomalyDetection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a>Nokta algılama sonuçlarını değiştirme

Sonuçlarınız aşağıdakilere benzer olmalıdır. İşlem sırasında iletiler görüntülenir. Uyarılar veya iletileri işleme görebilirsiniz. Bazı iletiler netlik için aşağıdaki sonuçlardan kaldırıldı.

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

Tebrikler! Şimdi başarıyla ani tespit ve satış verilerinde nokta anomalileri değiştirmek için makine öğrenme modelleri oluşturduk.

Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Verileri yükleme
> * Ani anomali tespiti için modeli eğitin
> * Eğitimli model ile başak anomalileri tespit
> * Değişim noktası anomali tespiti için modeli eğitin
> * Eğitilmiş mod ile değişim noktası anomalilerini tespit

## <a name="next-steps"></a>Sonraki adımlar

Güç Tüketimi Anomali Algılama örneğini keşfetmek için GitHub deposundaki Machine Learning örneklerine göz atın.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-örnekleri GitHub deposu](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
