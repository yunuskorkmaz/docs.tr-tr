---
title: 'Öğretici: telefon aramalarındaki bozukluklar'
description: Zaman serisi verileri için anomali algılama uygulaması oluşturmayı öğrenin. Bu öğretici, Visual Studio 2019 ' de C# kullanarak bir .NET Core konsol uygulaması oluşturur.
ms.date: 12/04/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 69b617e760c1dd6a579c925168c92630756f92fc
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596617"
---
# <a name="tutorial-detect-anomalies-in-time-series-with-mlnet"></a>Öğretici: ML.NET ile zaman serisinde anomali algılama

Zaman serisi verileri için anomali algılama uygulaması oluşturmayı öğrenin. Bu öğretici, Visual Studio 2019 ' de C# kullanarak bir .NET Core konsol uygulaması oluşturur.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Verileri yükleme
> * Zaman serisi için dönemi algılama
> * Süreli bir zaman serisi için anomali algılama

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

* [Visual Studio 2019 sürüm 16.7.8 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

* [phone-calls.csv veri kümesi](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrCnnDetection/Data/phone-calls.csv)

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "Productsalesanomalyıdetection" adlı bir **C# .NET Core konsol uygulaması** oluşturun.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.

3. **Microsoft.ml NuGet paketini** yükler:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml** araması yapın ve **yüklemeyi** seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin. **Microsoft. ml. TimeSeries** için bu adımları tekrarlayın.

4. `using` *Program.cs* dosyanızın en üstüne aşağıdaki deyimleri ekleyin:

    [!code-csharp[AddUsings](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>Verilerinizi indirin

1. Veri kümesini indirin ve daha önce oluşturduğunuz *veri* klasörüne kaydedin:

    [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrCnnDetection/Data/phone-calls.csv) sağ tıklayıp "bağlantıyı (veya hedefi) farklı kaydet" i seçin.

     \*. Csv dosyasını *veri* klasörüne kaydettiğinizden ya da başka bir yere kaydettikten sonra, \* . csv dosyasını *veri* klasörüne taşıdığınızdan emin olun.

2. Çözüm Gezgini, \* . csv dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala** olarak değiştirin.

Aşağıdaki tabloda,. csv dosyanızdaki bir veri önizlemesi verilmiştir \* :

| timestamp  | değer |
|--------|--------------|
| 2018/9/3  | 36,69670857  |
| 2018/9/4  | 35,74160571  |
| .....  | .....  |
| 2018/10/3  | 34,49893429  |
| ...    | ....   |

Bu dosya bir zaman serisini temsil eder. Dosyadaki her bir satır bir veri noktasıdır. Her bir `timestamp` `value` günde telefon araması sayısını reprensent için her bir veri pizı iki özniteliğe sahiptir. Telefon çağrılarının sayısı, büyük/küçük harfe dönüştürülür.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

Sonra, giriş ve tahmin sınıfı veri yapılarınızı tanımlayın.

Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **> yeni öğe Ekle**' yi seçin.

2. **Yeni öğe Ekle iletişim kutusunda** **sınıf** ' ı seçin ve **ad** alanını *PhoneCallsData.cs* olarak değiştirin. Sonra **Ekle** düğmesini seçin.

   *PhoneCallsData.cs* dosyası kod düzenleyicisinde açılır.

3. Aşağıdaki `using` ifadeyi *PhoneCallsData.cs* öğesinin en üstüne ekleyin:

   ```csharp
   using Microsoft.ML.Data;
   ```

4. Mevcut sınıf tanımını kaldırın ve iki sınıfa `PhoneCallsData` ve `PhoneCallsPrediction` *PhoneCallsData.cs* dosyasına sahip olan aşağıdaki kodu ekleyin:

    [!code-csharp[DeclareTypes](./snippets/phone-calls-anomaly-detection/csharp/PhoneCallsData.cs#DeclareTypes "Declare data record types")]

    `PhoneCallsData` bir giriş veri sınıfını belirtir. [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yükleneceğini belirtir. İki özniteliğe sahiptir `timestamp` ve `value` veri dosyasındaki aynı özniteliklere karşılık gelir.

    `PhoneCallsPrediction` tahmin verileri sınıfını belirtir. SR-CNN algılayıcısı için tahmin, belirtilen [algılama moduna](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) bağlıdır. Bu örnekte modu seçtik `AnomalyAndMargin` . Çıktı yedi sütun içerir. Çoğu durumda,, `IsAnomaly` , `ExpectedValue` `UpperBoundary` ve çok `LowerBoundary` bilgilendirme yeterlidir. Bir noktanın bir anomali, noktanın beklenen değeri ve noktanın alt/üst sınır bölgesi olduğunu bildirir.

5. Aşağıdaki kodu, `Main` veri dosyanızın yolunu belirtmek için yönteminin hemen üzerindeki satıra ekleyin:

    [!code-csharp[Declare global variables](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

1. `Console.WriteLine("Hello World!")` `Main` Yöntemi bildirmek ve başlatmak için yöntemindeki satırı aşağıdaki kodla değiştirin `mlContext` :

    [!code-csharp[CreateMLContext](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    [Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor, `mlContext` model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal olarak da benzerdir `DBContext` .

### <a name="load-the-data"></a>Verileri yükleme

ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView` , tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya diğer kaynaklardan (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.

1. Aşağıdaki kodu yönteminin sonraki satırı olarak ekleyin `Main` :

    [!code-csharp[LoadData](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    [Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar. Veri yolu değişkenlerini alır ve döndürür `IDataView` .

## <a name="time-series-anomaly-detection"></a>Zaman serisi anomali algılama

Zaman serisi anomali algılama, zaman serisi veri aykırı durumları algılama işlemidir; belirli bir giriş zaman serisini, davranışın beklenmediği veya "tuhaf" olduğunu gösterir. Bu anormaller genellikle sorun etki alanı ile ilgili bazı olayları ifade eder: Kullanıcı hesaplarında bir Cyber-saldırı, güç kesintisi, bir sunucu üzerinde RPS, bellek sızıntısı vb.

Zaman serisinde anomali bulmak için, önce serinin dönemini belirlemelisiniz. Daha sonra, zaman serisi çeşitli bileşenlere ayrılabilir `Y = T + S + R` , burada `Y` özgün seriler, `T` eğilim bileşenidir ve bu da `S` serinin farklı `R` bileşenidir. Bu adım [ayrıştırma](https://en.wikipedia.org/wiki/Decomposition_of_time_series)olarak adlandırılır. Son olarak, algılama işlemi, diğer bileşende, anormallikleri bulmak için gerçekleştirilir. ML.NET ' de, SR-CNN algoritması, zaman serisi üzerinde anomali algılama (Bu algoritmayla ilgili daha fazla bilgi için Microsoft kağıdına yönelik [zaman serisi anomali algılama hizmetine](https://arxiv.org/pdf/1906.03821.pdf) bakın) Ile Spectral ARTıMı (SR) ve evsel sinir ağı (CNN) temel alan gelişmiş ve önemli bir algoritmadır.

Bu öğreticide, bu yordamların iki işlev kullanılarak tamamlanbir şekilde görülecektir.

## <a name="detect-period"></a>Süreyi Algıla

İlk adımda, `DetectSeasonality` serinin dönemini belirlemede işlevi çağıracağız.

### <a name="create-the-detectperiod-method"></a>DetectPeriod metodunu oluşturma

1. `DetectPeriod` `Main` Aşağıdaki kodu kullanarak yönteminin hemen altındaki yöntemini oluşturun:

    ```csharp
    static void DetectPeriod(MLContext mlContext, IDataView phoneCalls)
    {

    }
    ```

2. Dönemi saptamak için [Detectmevsimsellik](xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality) işlevini kullanın. `DetectPeriod`Aşağıdaki kodla yöntemine ekleyin:

    [!code-csharp[DetectSeasonality](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectSeasonality)]

3. Yöntemine sonraki kod satırı olarak aşağıdakini ekleyerek period değerini görüntüleyin `DetectPeriod` :

    [!code-csharp[DisplayPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayPeriod)]

4. Yöntemine aşağıdaki çağrıyı ekleyin `DetectPeriod` `Main` :

    [!code-csharp[CallDetectPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectPeriod)]

### <a name="period-detection-results"></a>Süre algılama sonuçları

Uygulamayı çalıştırın. Sonuçlarınız aşağıdakine benzer olmalıdır.

```console
Period of the series is: 7.
```

## <a name="detect-anomaly"></a>Anomali algılama

Bu adımda, [`SrCnnEntireDetector`](xref:Microsoft.ML.Transforms.TimeSeries.SrCnnEntireAnomalyDetector) anomali bulmak için öğesini kullanırsınız.

### <a name="create-the-detectanomaly-method"></a>DetectAnomaly yöntemini oluşturma

1. `DetectAnomaly` `DetectPeriod` Aşağıdaki kodu kullanarak yönteminin hemen altındaki yöntemini oluşturun:

    ```csharp
    static void DetectAnomaly(MLContext mlContext, IDataView phoneCalls, int period)
    {

    }
    ```

2. Yönteminde aşağıdaki kodla [Srcnnentireanoydetectoroçenayarları](xref:Microsoft.ML.Transforms.TimeSeries.SrCnnEntireAnomalyDetectorOptions) `DetectAnomaly` yapın:

    [!code-csharp[SetupSrCnnParameters](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#SetupSrCnnParameters)]

3. Aşağıdaki kod satırını yöntemine ekleyerek SR-CNN algoritmasına göre anomali algılama `DetectAnomaly` :

    [!code-csharp[DetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectAnomaly)]

4. `IEnumerable`Aşağıdaki kodla yöntemi kullanılarak daha kolay görüntülenmek üzere çıkış veri görünümünü kesin bir şekilde belirlenmiş bir [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) şekilde dönüştürün:

    [!code-csharp[CreateEnumerableForResult](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateEnumerableForResult)]

5. Yönteminde bir sonraki satır olarak aşağıdaki kodla bir görüntüleme üstbilgisi oluşturun `DetectAnomaly` :

    [!code-csharp[DisplayHeader](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayHeader)]

    Değişiklik noktası algılama sonuçlarında aşağıdaki bilgileri görüntüleyebilirsiniz:

    * `Index` her noktanın dizinidir.
    * `Anomaly` her noktanın anomali olarak algılandığına ilişkin bir göstergedir.
    * `ExpectedValue` her noktanın tahmini değeridir.
    * `LowerBoundary` her noktanın en düşük değeri anomali olamaz.
    * `UpperBoundary` en yüksek değer, her noktanın anomali olmaması olabilir.

6. Üzerinde yineleme `predictions` `IEnumerable` yapın ve sonuçları aşağıdaki kodla görüntüleyin:

    [!code-csharp[DisplayAnomalyDetectionResults](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayAnomalyDetectionResults)]

7. Yöntemine aşağıdaki çağrıyı ekleyin `DetectAnomaly` `Main` :

    [!code-csharp[CallDetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectAnomaly)]

## <a name="anomaly-detection-results"></a>Anomali algılama sonuçları

Uygulamayı çalıştırın. Sonuçlarınız aşağıdakine benzer olmalıdır. İşlem sırasında iletiler görüntülenir. Uyarıları görebilir veya iletileri işleme alabilirsiniz. Bazı iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.

```console
Detect period of the series
Period of the series is: 7.
Detect anomaly points in the series
Index   Data    Anomaly AnomalyScore    Mag     ExpectedValue   BoundaryUnit    UpperBoundary   LowerBoundary
0,0,36.841787256739266,41.14206982401966,32.541504689458876
1,0,35.67303618137362,39.97331874865401,31.372753614093227
2,0,34.710132999891826,39.029491313022824,30.390774686760828
3,0,33.44765248883495,37.786086547816545,29.10921842985335
4,0,28.937110922276364,33.25646923540736,24.61775260914537
5,0,5.143895892785781,9.444178460066171,0.843613325505391
6,0,5.163325228419392,9.463607795699783,0.8630426611390014
7,0,36.76414836240396,41.06443092968435,32.46386579512357
8,0,35.77908590657007,40.07936847385046,31.478803339289676
9,0,34.547259536635245,38.847542103915636,30.246976969354854
10,0,33.55193524820608,37.871293561337076,29.23257693507508
11,0,29.091800129624648,33.392082696905035,24.79151756234426
12,0,5.154836630338823,9.455119197619213,0.8545540630584334
13,0,5.234332502492464,9.534615069772855,0.934049935212073
14,0,36.54992549471526,40.85020806199565,32.24964292743487
15,0,35.79526470980883,40.095547277089224,31.494982142528443
16,0,34.34099013096804,38.64127269824843,30.040707563687647
17,0,33.61201516582131,37.9122977331017,29.31173259854092
18,0,29.223563320561812,33.5238458878422,24.923280753281425
19,0,5.170512168851533,9.470794736131923,0.8702296015711433
20,0,5.2614938889462834,9.561776456226674,0.9612113216658926
21,0,36.37103858487317,40.67132115215356,32.07075601759278
22,0,35.813544599026855,40.113827166307246,31.513262031746464
23,0,34.05600492733225,38.356287494612644,29.755722360051863
24,0,33.65828319077884,37.95856575805923,29.358000623498448
25,0,29.381125690882463,33.681408258162854,25.080843123602072
26,0,5.261543539820418,9.561826107100808,0.9612609725400283
27,0,5.4873712582971805,9.787653825577571,1.1870886910167897
28,1,36.504694001629254,40.804976568909645,32.20441143434886  <-- alert is on, detecte anomaly
...
```

Tebrikler! Artık bir dönemsel serisinde dönem ve anomali algılama için makine öğrenimi modellerini başarıyla oluşturdunuz.

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Verileri yükleme
> * Zaman serisi verilerinde süreyi Algıla
> * Zaman serisi verilerinde anomali algılama

## <a name="next-steps"></a>Sonraki adımlar

Güç tüketimi anomali algılama örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/machinöğrenim-Samples GitHub deposu](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
