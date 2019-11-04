---
title: 'Öğretici: ürün satışlardaki anormallikleri algılama'
description: Ürün satış verileri için anomali algılama uygulaması oluşturmayı öğrenin. Bu öğretici, Visual Studio 2019 ' de kullanarak C# bir .NET Core konsol uygulaması oluşturur.
ms.date: 07/17/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 37c6b99fbd7db63c19201e0c6dce9b2b6d9f1932
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423604"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a>Öğretici: ML.NET ile ürün satışlardaki anormallikleri algılama

Ürün satış verileri için anomali algılama uygulaması oluşturmayı öğrenin. Bu öğretici, Visual Studio 'da kullanarak C# bir .NET Core konsol uygulaması oluşturur.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Verileri yükleme
> * Ani anomali algılama için bir dönüşüm oluşturun
> * Dönüşümle birlikte ani bozukluklar Algıla
> * Değişiklik noktası anomali algılama için bir dönüşüm oluşturun
> * Dönüşümle değişiklik noktası bozuklularını Algıla

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Prerequisites

* [Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

* [Product-Sales. csv veri kümesi](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> `product-sales.csv` ' deki veri biçimi, ilk olarak DataMarket 'ten kaynaklıdır ve Ramiz Hyndman tarafından oluşturulan zaman serisi veri kitaplığı (TSDL) tarafından sağlanmış olan "üç yıllık dönem Içinde" Shampoo Sales "veri kümesini temel alır.
> "Üç yıllık dönem Içinde Shampoo Sales" veri kümesi, varsayılan DataMarket açık lisansı kapsamında lisanslanır.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "Productsalesanomalyıdetection" adlı bir **.NET Core konsol uygulaması** oluşturun.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.

3. **Microsoft.ml NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden **v 1.0.0** paketini seçin ve sonra da **Install** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin. **Microsoft. ml. TimeSeries v 0.12.0**için bu adımları tekrarlayın.

4. Aşağıdaki `using` deyimlerini *program.cs* dosyanızın üst kısmına ekleyin:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Verilerinizi indirin

1. Veri kümesini indirin ve daha önce oluşturduğunuz *veri* klasörüne kaydedin:

   * [*Product-Sales. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) ' ye sağ tıklayın ve "bağlantıyı (veya hedefi) farklı kaydet" i seçin.

     \*. csv dosyasını *veri* klasörüne kaydettiğinizden ya da başka bir yere kaydettikten sonra, \*. csv dosyasını *veri* klasörüne taşıyın.

2. Çözüm Gezgini ' de, \*. csv dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

Aşağıdaki tabloda \*. csv dosyanızdaki bir veri önizlemesi verilmiştir:

|Başından  |ProductSales |
|-------|-------------|
|1-Jan  |    271      |
|2-Jan  |    150,9    |
|.....  |    .....    |
|1-Şub  |    199,3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

Sonra, giriş ve tahmin sınıfı veri yapılarınızı tanımlayın.

Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **> yeni öğe Ekle**' yi seçin.

2. **Yeni öğe Ekle iletişim kutusunda** **sınıf** ' ı seçin ve **ad** alanını *ProductSalesData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

   *ProductSalesData.cs* dosyası kod düzenleyicisinde açılır.

3. Aşağıdaki `using` ifadesini *ProductSalesData.cs*öğesinin en üstüne ekleyin:

   ```csharp
   using Microsoft.ML.Data;
   ```

4. Mevcut sınıf tanımını kaldırın ve *ProductSalesData.cs* dosyasına `ProductSalesData` ve `ProductSalesPrediction`iki sınıfa sahip aşağıdaki kodu ekleyin:

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    `ProductSalesData` bir giriş verileri sınıfını belirtir. [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yükleneceğini belirtir.

    `ProductSalesPrediction`, tahmin verileri sınıfını belirtir. Anomali algılama için tahmin, bir anomali, ham puan ve p değeri olup olmadığını belirten bir uyarıdan oluşur. P değeri 0 ' a yaklaşarak daha büyük bir anomali meydana geldi.

5. Son indirilen veri kümesi dosya yolunu ve kaydedilen model dosyası yolunu tutmak için iki genel alan oluşturun:

    * `_dataPath`, modeli eğitmek için kullanılan veri kümesinin yoludur.
    * `_docsize`, veri kümesi dosyasındaki kayıt sayısına sahiptir. `pvalueHistoryLength`hesaplamak için `_docSize` kullanacaksınız.

6. Aşağıdaki kodu, bu yolları belirtmek için `Main` yönteminin hemen üstüne ekleyin:

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

1. `mlContext` değişkenini bildirmek ve başlatmak için `Main` yöntemindeki `Console.WriteLine("Hello World!")` satırı aşağıdaki kodla değiştirin:

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

    [Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve `mlContext` başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.

### <a name="load-the-data"></a>Verileri yükleme

ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya diğer kaynaklardan (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesnesine yüklenebilir.

1. `Main()` yönteminin sonraki satırı olarak aşağıdaki kodu ekleyin:

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

    [Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar. Veri yolu değişkenlerini alır ve `IDataView` döndürür.

## <a name="time-series-anomaly-detection"></a>Zaman serisi anomali algılama

Anomali algılama, beklenmeyen veya olağandışı olayları ya da davranışları işaretler. Sorunları nerede aramak ve "Bu tuhaf?" sorusunu cevaplamanıza yardımcı olacak ipuçları verir.

!["Bu tuhaf" anomali algılama örneğidir.](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

Anomali algılama, zaman serisi veri aykırı durumları algılama işlemidir; belirli bir giriş zaman serisini, davranışın beklenmediği veya "tuhaf" olduğunu gösterir.

Anomali algılama çok sayıda şekilde yararlı olabilir. Örneğin:

Bir otomobil varsa şunları bilmeniz gerekebilir: Bu yağ ölçer normal okunuyor mu yoksa bir sızıntı var mı?
Güç tüketimini izliyorsanız şunları öğrenmek istersiniz: bir kesinti mi var?

Tespit edilebilir iki tür zaman serisi bozukluklar vardır:

* **Ani artışlar** , sistemde anormal davranıştaki geçici bir davranış gösterir.

* **Değişiklik noktaları** , sistemdeki zaman içindeki kalıcı değişikliklerin başlangıcını belirtir.

ML.NET ' de, IID depo algılama veya IID değişiklik noktası algılama algoritmaları [bağımsız ve benzer şekilde dağıtılmış veri kümelerine](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)uygundur.

Diğer öğreticilerdeki modellerin aksine, anomali algılayıcı dönüştürmeleri doğrudan giriş verilerinde çalışır. `IEstimator.Fit()` yöntemi, dönüştürmeyi üretmek için eğitim verileri gerektirmez. Boş bir `ProductSalesData`listesinden oluşturulan veri görünümü tarafından sağlanmış olan veri şeması da gerekir.

Artışlar ve değişiklik noktalarını algılamak için aynı ürün satış verilerini analiz edersiniz. Derleme ve eğitim modeli işlemi, ani algılama ve değişiklik noktası algılama için aynıdır; Ana fark, kullanılan belirli bir algılama algoritmasıdır.

## <a name="spike-detection"></a>Depo algılama

Ani algılamanın amacı, zaman serisi veri değerlerinin çoğunluğunun önemli ölçüde farklı olduğu ani, geçici bir artışlarıyla 'yi belirlemektir. Bu şüpheli nadir öğe, olay veya gözlemlerin en aza indirme zamanında algılanması önemlidir. Aşağıdaki yaklaşım,: kesintiler, Cyber saldırıları veya viral web içeriği gibi çeşitli anormallikleri algılamak için kullanılabilir. Aşağıdaki görüntü, zaman serisi veri kümesindeki ani artışlar örneğidir:

![İki ani algılama gösteren ekran görüntüsü.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a>CreateEmptyDataView () yöntemi ekleme

`Program.cs`için aşağıdaki yöntemi ekleyin:

[!code-csharp[CreateEmptyDataView](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEmptyDataView)]

`CreateEmptyDataView()`, `IEstimator.Fit()` yöntemine giriş olarak kullanılacak doğru şemaya sahip boş bir veri görünümü nesnesi oluşturur.

### <a name="create-the-detectspike-method"></a>Detectani () yöntemini oluşturma

`DetectSpike()` yöntemi:

* Estimator 'dan dönüşüm oluşturur.
* Geçmiş satış verilerine göre ani artışları algılar.
* Sonuçları görüntüler.

1. Aşağıdaki kodu kullanarak, `Main()` yönteminden hemen sonra `DetectSpike()` yöntemini oluşturun:

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. Modeli ani algılamayı eğitmek için [ııdspikeestimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) 'ı kullanın. `DetectSpike()` yöntemine aşağıdaki kodla ekleyin:

    [!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

1. `DetectSpike()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek depo algılama dönüşümü oluşturun:

    [!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

1. `productSales` verileri `DetectSpike()` yönteminin sonraki satırı olarak dönüştürmek için aşağıdaki kod satırını ekleyin:

    [!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

    Önceki kod, bir veri kümesinin birden çok giriş satırına ilişkin tahminleri yapmak için [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.

1. Aşağıdaki kodla [Createsıralanabilir ()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) yöntemini kullanarak daha kolay görüntülenmesi için `transformedData` türü kesin belirlenmiş bir `IEnumerable` dönüştürün:

    [!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

1. Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodunu kullanarak bir görüntüleme üst bilgisi satırı oluşturun:

    [!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

    Aşağıdaki bilgileri, depo algılama sonuçlarında görüntüleriz:

    * `Alert`, belirli bir veri noktası için ani bir uyarı gösterir.
    * `Score`, veri kümesindeki belirli bir veri noktası için `ProductSales` değerdir.
    * "P" `P-Value` olasılık anlamına gelir. P değerinin 0 olması, büyük olasılıkla veri noktasının bir anomali olması olabilir.

1. `predictions` `IEnumerable` üzerinden yinelemek ve sonuçları göstermek için aşağıdaki kodu kullanın:

    [!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

1. `Main()` yönteminde `DetectSpike()`metoduna çağrıyı ekleyin:

    [!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a>Depo algılama sonuçları

Sonuçlarınız aşağıdakine benzer olmalıdır. İşlem sırasında iletiler görüntülenir. Uyarıları görebilir veya iletileri işleme alabilirsiniz. Bazı iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.

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

`Change points`, bir zaman serisi olay akışı, düzey değişiklikler ve eğilimler gibi değerlerin dağıtımında kalıcı değişikliklerdir. Bu kalıcı değişiklikler `spikes` son olarak çok daha uzun ve çok zararlı olay (ler) i gösteriyor olabilir. `Change points`, genellikle çıplak gözle görünmez, ancak verilerinizde aşağıdaki yöntemde olduğu gibi yaklaşımlar kullanılarak algılanabilir.  Aşağıdaki görüntü, değişiklik noktası algılamayı bir örneğidir:

![Değişiklik noktası algılamayı gösteren ekran görüntüsü.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a>DetectChangepoint () metodunu oluşturma

`DetectChangepoint()` yöntemi aşağıdaki görevleri yürütür:

* Estimator 'dan dönüşüm oluşturur.
* Geçmiş satış verilerine göre değişiklik noktalarını algılar.
* Sonuçları görüntüler.

1. Aşağıdaki kodu kullanarak, `Main()` yönteminden hemen sonra `DetectChangepoint()` yöntemini oluşturun:

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. `DetectChangepoint()` yönteminde aşağıdaki kodla [ııdchangepointestiyıtor](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) öğesini oluşturun:

    [!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

1. Daha önce yaptığınız gibi, aşağıdaki kod satırını `DetectChangePoint()` yöntemine ekleyerek tahmin aracı 'dan dönüştürmeyi oluşturun:

    [!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

1. Aşağıdaki kodu `DetectChangePoint()`ekleyerek verileri dönüştürmek için `Transform()` yöntemini kullanın:

    [!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

1. Daha önce yaptığınız gibi, aşağıdaki kodla `CreateEnumerable()`yöntemini kullanarak daha kolay görüntülenmesi için `transformedData` kesin olarak yazılmış bir `IEnumerable` dönüştürün:

    [!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

1. `DetectChangePoint()` yönteminde sonraki satır olarak aşağıdaki kodla bir görüntüleme üstbilgisi oluşturun:

    [!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

    Değişiklik noktası algılama sonuçlarında aşağıdaki bilgileri görüntüleyebilirsiniz:

    * `Alert`, belirli bir veri noktası için bir değişiklik noktası uyarısı olduğunu gösterir.
    * `Score`, veri kümesindeki belirli bir veri noktası için `ProductSales` değerdir.
    * "P" `P-Value` olasılık anlamına gelir. P değerinin 0 olması, büyük olasılıkla veri noktasının bir anomali olması olabilir.
    * `Martingale value`, bir veri noktasının P-değerleri dizisine göre nasıl olduğunu belirlemek için kullanılır.

1. `predictions` `IEnumerable` üzerinden yineleyin ve sonuçları aşağıdaki kodla görüntüleyin:

    [!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

1. Aşağıdaki çağrıyı `Main()` yönteminde `DetectChangepoint()`yöntemine ekleyin:

    [!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a>Nokta algılama sonuçlarını değiştirme

Sonuçlarınız aşağıdakine benzer olmalıdır. İşlem sırasında iletiler görüntülenir. Uyarıları görebilir veya iletileri işleme alabilirsiniz. Bazı iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.

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

Mühendisi! Artık, satış verilerinde ani artışları ve değişiklik noktası bozukluklarını algılamak için makine öğrenimi modellerini başarıyla oluşturdunuz.

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.

Bu öğreticide, nasıl yapılacağını öğrendiniz:
> [!div class="checklist"]
>
> * Verileri yükleme
> * Modeli, ani anomali algılama için eğitme
> * Eğitilen modeliyle ani bozukluklar algılama
> * Modeli değişiklik noktası anomali algılama için eğitme
> * Eğitilen mod ile değişiklik noktası bozuklulıkları Algıla

## <a name="next-steps"></a>Sonraki adımlar

Güç tüketimi anomali algılama örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/machinöğrenim-Samples GitHub deposu](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
