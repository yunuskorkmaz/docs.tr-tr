---
title: 'Öğretici: Tahmin bisiklet kiralama talebi - zaman serisi'
description: Bu öğretici, tek değişkenli zaman serisi analizi ve ML.NET kullanarak bir bisiklet kiralama hizmeti için talebi tahmin nasıl gösterir.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 026421d7b1b2a0e39118ae712780ca7fc8f6e444
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921250"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Öğretici: Zaman serisi analizi ve ML.NET ile tahmin bisiklet kiralama hizmeti talebi

ML.NET ile sql server veritabanında depolanan veriler üzerinde tek değişkenli zaman serisi analizini kullanarak bisiklet kiralama hizmeti talebini nasıl tahmin edebilirsiniz öğrenin.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> * Sorunu anlama
> * Veritabanından veri yükleme
> * Tahmin modeli oluşturma
> * Tahmin modelini değerlendirme
> * Tahmin modelini kaydetme
> * Tahmin modeli kullanma

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.

## <a name="time-series-forecasting-sample-overview"></a>Zaman serisi tahmin örnek genel bakış

Bu örnek, Tek Spektrum Analizi olarak bilinen tek değişkenli zaman serileri analiz algoritması kullanarak bisiklet kiralama talebini tahmin eden bir **C# .NET Core konsol uygulamasıdır.** Bu örneğin kodu GitHub'daki [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) deposunda bulunabilir.

## <a name="understand-the-problem"></a>Sorunu anlama

Verimli bir çalışma yürütmek için, envanter yönetimi önemli bir rol oynar. Stokta çok fazla ürün olması, raflarda yer alan satılmayan ürünlerin herhangi bir gelir getirmeyecek olması anlamına gelir. Çok az ürün olması, satışların kaybolmasına ve müşterilere rakiplerinden satın alma yol açar. Bu nedenle, sürekli soru, ne stok en uygun miktarda elde tutmak nedir? Zaman serisi çözümlemesi, geçmiş verilere bakarak, desenleri tanımlayarak ve gelecekte değerleri tahmin etmek için bu bilgileri kullanarak bu soruların yanıtlanmasına yardımcı olur.

Bu öğreticide kullanılan verileri çözümleme tekniği, tek değişkenli zaman serisi çözümlemesidir. Univariate zaman serisi analizi, aylık satışlar gibi belirli aralıklarla belirli aralıklarla belirli bir zaman dilimi içinde tek bir sayısal gözleme bakar.

Bu eğitimde kullanılan algoritma [Tek Spektrum Analizi(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf)olduğunu. SSA, bir zaman serisini bir dizi ana bileşene ayrıştarak çalışır. Bu bileşenler, bir sinyalin eğilimlere, gürültüye, mevsimselliğe ve diğer birçok faktöre karşılık gelen parçaları olarak yorumlanabilir. Daha sonra, bu bileşenler yeniden oluşturulur ve gelecekte bir süre değerleri tahmin etmek için kullanılır.

## <a name="create-console-application"></a>Konsol uygulaması oluşturma

1. "BikeDemandForecasting" adlı yeni bir **C# .NET Core konsol uygulaması** oluşturun.
1. sürüm **1.4.0** NuGet **paketini Microsoft.ML** yükleyin
    1. Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.
    1. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, **Gözat** sekmesini seçin, **Microsoft.ML**arayın.
    1. Yayın **aet'i ekle** onay kutusunu işaretleyin.
    1. **Yükle** düğmesini seçin.
    1. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul Et** düğmesini seçin.
    1. **System.Data.SqlClient** sürüm **4.7.0** ve **Microsoft.ML.TimeSeries** sürüm **1.4.0**için bu adımları yineleyin.

### <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

1. *Veri*adlı bir dizin oluşturun.
1. [ *DailyDemand.mdf* veritabanı dosyasını](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) indirin ve *Veri* dizinine kaydedin.

> [!NOTE]
> Bu öğreticide kullanılan veriler [UCI Bike Sharing Dataset'ten](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)gelir. Fanaee-T, Hadi ve Gama, Joao, 'Topluluk dedektörleri ve arka plan bilgisi birleştiren olay etiketleme', İlerleme Yapay Zeka (2013): s. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

Orijinal veri kümesi mevsimsellik ve hava koşullarına karşılık gelen birkaç sütun içerir. Kısaltma için ve bu öğreticide kullanılan algoritma yalnızca tek bir sayısal sütundaki değerleri gerektirdiğinden, özgün veri kümesi yalnızca aşağıdaki sütunları içerecek şekilde yoğunlaştırılmıştır:

- **dteday**: Gözlem tarihi.
- **yıl**: Gözlemin kodlanmış yılı (0=2011, 1=2012).
- **cnt**: O gün için toplam bisiklet kiralama sayısı.

Özgün veri kümesi, sql server veritabanında aşağıdaki şemaya sahip bir veritabanı tablosuna eşlenir.

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

Aşağıdaki verilerin bir örneğidir:

| Kiralama Tarihi | Yıl | Toplam Kiralama |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Giriş ve çıktı sınıfları oluşturma

1. *Dosya Program.csyı açın* `using` ve varolan deyimleri aşağıdakilerle değiştirin:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. `ModelInput` sınıfını oluşturun. `Program` Sınıfın altına aşağıdaki kodu ekleyin.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    Sınıf `ModelInput` aşağıdaki sütunları içerir:

    - **Kiralama Tarihi**: Gözlem tarihi.
    - **Yıl**: Gözlemin kodlanmış yılı (0=2011, 1=2012).
    - **Toplam Kiralama**: O gün için toplam bisiklet kiralama sayısı.

1. Yeni `ModelOutput` oluşturulan sınıfın `ModelInput` altında sınıf oluşturun.

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    Sınıf `ModelOutput` aşağıdaki sütunları içerir:

    - **Tahmini Kiralamalar**: Tahmin edilen dönem için öngörülen değerlerdir.
    - **LowerBoundRentals**: Öngörülen dönem için öngörülen minimum değerlerdir.
    - **UpperBoundRentals**: Tahmin edilen dönem için öngörülen maksimum değerlerdir.

### <a name="define-paths-and-initialize-variables"></a>Yolları tanımlayın ve değişkenleri başlatma

1. Yöntemin `Main` içinde, verilerinizin konumunu, bağlantı dizesini ve eğitilmiş modeli nerede kaydedebileceğinizi depolamak için değişkenleri tanımlayın.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. Yönteme `mlContext` aşağıdaki satırı ekleyerek [`MLContext`](xref:Microsoft.ML.MLContext) değişkeni yeni bir örnekle başharfe ait hale getirmek. `Main`

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    Sınıf [`MLContext`](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç noktasıdır ve mlContext'ı başlatmak, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur. Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.

## <a name="load-the-data"></a>Verileri yükleme

1. Bu `DatabaseLoader` tür `ModelInput`kayıtları yükler oluşturun.

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Veritabanından veri yüklemek için sorgu tanımlayın.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET algoritmaları veri türü [`Single`](xref:System.Single)olmasını bekliyoruz. Bu nedenle, tür [`Real`](xref:System.Data.SqlDbType)olmayan veritabanından gelen sayısal değerlerin , tek bir hassas kayan nokta [`Real`](xref:System.Data.SqlDbType)değerine dönüştürülmesi gerekir.

    Ve `Year` `TotalRental` sütunlar veritabanında hem de sasayı türleridir. Dahili `CAST` işlevi kullanarak, her ikisi `Real`de döküm .

1. Veritabanına `DatabaseSource` bağlanmak için a oluşturun ve sorguyu çalıştırın.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Verileri bir `IDataView`' ye yükleyin.

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Veri kümesi iki yıllık veri içerir. Yalnızca ilk yıla ait veriler eğitim için kullanılır, ikinci yıl ise model tarafından üretilen tahminle gerçek değerleri karşılaştırmak için düzenlenir. Dönüşümü kullanarak verileri [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) filtreleyin.

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    İlk yıl için, `Year` `upperBound` parametre 1 olarak ayarlanırken yalnızca sütundaki 1'den küçük değerler seçilir. Tersine, ikinci yıl için, parametre 1'e `lowerBound` ayarlayarak 1'den büyük veya eşit değerler seçilir.

## <a name="define-time-series-analysis-pipeline"></a>Zaman serisi analiz boru hattını tanımla

1. Zaman serisi veri kümesindeki değerleri tahmin etmek için [SsaForecastingEstimator'u](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) kullanan bir ardışık kaynak tanımlayın.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    İlk `forecastingPipeline` yıl için 365 veri puanı alır ve zaman serisi veri kümesini `seriesLength` parametrede belirtildiği şekilde 30 günlük (aylık) aralıklara böler. Bu örneklerin her biri haftalık veya 7 günlük bir süre ile analiz edilir. Bir sonraki dönem(ler) için öngörülen değerin ne olduğu belirlenirken, önceki yedi güne ait değerler tahmin yapmak için kullanılır. Model, `horizon` parametre tarafından tanımlandığı şekilde geleceğe yedi dönem tahmin etmek üzere ayarlanır. Bir tahmin bilinçli bir tahmin olduğundan, her zaman % 100 doğru değildir. Bu nedenle, üst ve alt sınırlar tarafından tanımlanan en iyi ve en kötü durum senaryolarında değerlerin aralığını bilmek iyidir. Bu durumda, alt ve üst sınırlar için güven düzeyi% 95 olarak ayarlanır. Güven düzeyi buna göre artırılabilir veya azaltılabilir. Değer ne kadar yüksekse, istenilen güven düzeyine ulaşmak için üst ve alt sınırlar arasındaki aralık da o kadar geniştir.

1. Modeli [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) eğitmek ve verileri daha önce tanımlanana `forecastingPipeline`sığdırmak için yöntemi kullanın.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Modelin gelecek yılın verilerini tahmin ederek ve gerçek değerlerle karşılaştırarak ne kadar iyi performans gösterdiğini değerlendirin.

1. Yöntemin `Main` altında, adı verilen `Evaluate`yeni bir yardımcı program yöntemi oluşturun.

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. Yöntemin `Evaluate` içinde, eğitilmiş model ile [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) yöntemi kullanarak ikinci yılın verilerini tahmin edin.

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) Yöntemi kullanarak verilerden gerçek değerleri alın.

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) Yöntemi kullanarak tahmin değerlerini alın.

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Hata olarak adanılan gerçek ve tahmin değerleri arasındaki farkı hesaplayın.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Ortalama Mutlak Hata ve Kök Ortalama Kareli Hata değerlerini hesaplayarak performansı ölçün.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    Performansı değerlendirmek için aşağıdaki ölçümler kullanılır:

    - **Ortalama Mutlak Hata**: Tahminlerin gerçek değere ne kadar yakın olduğunu ölçer. Bu değer 0 ile sonsuzluk arasında değişir. 0'a ne kadar yakınsa, modelin kalitesi de o kadar iyi.
    - **Kök Ortalama Kareli Hata**: Modeldeki hatayı özetler. Bu değer 0 ile sonsuzluk arasında değişir. 0'a ne kadar yakınsa, modelin kalitesi de o kadar iyi.

1. Ölçümleri konsola çıktın.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. `Evaluate` Yöntem in içindeki yöntemi `Main` kullanın.

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Modeli kaydetme

Modelinizden memnunsanız, modelinizi diğer uygulamalarda daha sonra kullanmak üzere kaydedin.

1. Yöntemde, `Main` bir [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602). [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)tek tahminler yapmak için bir kolaylık yöntemidir.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Modeli daha önce tanımlanan `MLModel.zip` değişken tarafından belirtildiği `modelPath` gibi çağrılan bir dosyaya kaydedin. Modeli [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) kaydetmek için yöntemi kullanın.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Talebi tahmin etmek için modeli kullanma

1. Yöntemin `Evaluate` altında, adı verilen `Forecast`yeni bir yardımcı program yöntemi oluşturun.

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. Yöntemin `Forecast` içinde, [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) önümüzdeki yedi gün için kiralama tahmin etmek için yöntemi kullanın.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Yedi dönem için gerçek ve tahmin değerlerini hizala.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Tahmin çıktısını yineleyin ve konsolda görüntüleyin.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Yöntemin `Main` içinde, `Forecast` yöntemi arayın.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Uygulamayı çalıştırın. Aşağıdakine benzer çıkış konsolda görünmelidir. Kısalık için, çıkış yoğunlaştırılmış tır.

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

Gerçek ve tahmin edilen değerlerin incelenmesi aşağıdaki ilişkileri gösterir:

![Gerçek vs Tahmin Karşılaştırması](./media/time-series-demand-forecasting/forecast.png)

Tahmin edilen değerler tam kiralama sayısını tahmin etmese de, bir işlemin kaynak kullanımını optimize etmesine olanak tanıyan daha dar bir değer aralığı sağlar.

Tebrikler! Şimdi başarılı bisiklet kiralama talebi tahmin etmek için bir zaman serisi makine öğrenme modeli inşa ettik.

Bu öğreticinin kaynak kodunu [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [ML.NET makine öğrenimi görevleri](../resources/tasks.md)
- [Model doğruluğunu geliştirme](../resources/improve-machine-learning-model-ml-net.md)
