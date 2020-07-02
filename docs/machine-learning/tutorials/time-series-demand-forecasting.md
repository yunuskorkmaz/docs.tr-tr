---
title: 'Öğretici: tahmin Bisiklet Kiralama talep-süre serisi'
description: Bu öğreticide, tek bir zaman serisi analizi ve ML.NET kullanarak bir bisiklet kiralama hizmeti için talebin nasıl tahmin yapılacağı gösterilir.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 4ea002b690de877fd6f955c05eb8235f46e0a870
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803228"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>Öğretici: zaman serisi analizi ve ML.NET ile tahmin Bisiklet kiralama hizmeti talebi

ML.NET ile SQL Server veritabanında depolanan veriler üzerinde bağımsız zamanlı bir zaman serisi analizi kullanarak bir bisiklet kiralama hizmeti için talebi tahmin etme hakkında bilgi edinin.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Sorunu anlama
> * Veritabanından veri yükleme
> * Tahmin modeli oluşturma
> * Tahmin modelini değerlendir
> * Tahmin modelini kaydetme
> * Tahmin modeli kullan

## <a name="prerequisites"></a>Ön koşullar

- [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya üzeri ya da visual Studio 2017 sürüm 15,6 veya üzeri, ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="time-series-forecasting-sample-overview"></a>Zaman serisi tahmin örneğine genel bakış

Bu örnek, tek bir Spekme analizi olarak bilinen bağımsız bir zaman serisi analiz algoritmasını kullanarak bisiklet için talebi tahmin eden bir **C# .NET Core konsol uygulamasıdır** . Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) deposunda bulunabilir.

## <a name="understand-the-problem"></a>Sorunu anlama

Verimli bir işlem çalıştırmak için, envanter yönetimi bir anahtar rol oynar. Ücretteki bir ürünün çok fazla olması, raflardan herhangi bir gelir üretmeden satışa açık ürünler anlamına gelir. Çok az ürün, rakiplerden satın alınan satışları ve müşterileri kaybetmeyecek. Bu nedenle, sabit soru, elinizin altında tutulacak en uygun stok miktarı nedir? Zaman serisi analizi, geçmiş verileri inceleyerek, desenleri tanımlayarak ve bu bilgileri gelecekte bir süre tahmin etmek için kullanarak bu sorulara yanıt sağlanmasına yardımcı olur.

Bu öğreticide kullanılan verileri çözümlemeye yönelik teknik, zaman serisi analizinden bağımsız bir yöntemdir. Tek bir zaman serisi analizi, aylık satış gibi belirli aralıklarda tek bir sayısal izlemeye göz atacağız.

Bu öğreticide kullanılan algoritma, [tek bir Spekme analizidir (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf). SSA, bir dizi sorumlu bileşen için zaman serisini kaldırarak işe yarar. Bu bileşenler, eğilimler, gürültü, mevsimsellik ve birçok başka etkene karşılık gelen bir sinyalin parçaları olarak yorumlanamaz. Ardından, bu bileşenler yeniden yapılandırılır ve gelecekte değerleri tahmin etmek için kullanılır.

## <a name="create-console-application"></a>Konsol uygulaması oluşturma

1. "Bikeisteğtahmini" adlı yeni bir **C# .NET Core konsol uygulaması** oluşturun.
1. **Microsoft.ml** sürümü NuGet paketini yükler

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.
    1. Paket kaynağı olarak "nuget.org" öğesini seçin, **Gözden** geçirme sekmesini seçin, **Microsoft.ml**için arama yapın.
    1. **Ön sürümü dahil et** onay kutusunu işaretleyin.
    1. **Install** düğmesini seçin.
    1. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız Lisans Kabulü iletişim kutusunda **kabul ediyorum** düğmesini seçin.
    1. **System. Data. SqlClient** ve **Microsoft. ml. timeseries**için bu adımları tekrarlayın.

### <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

1. *Veri*adlı bir dizin oluşturun.
1. [ *Dailydemand. mdf* veritabanı dosyasını](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) indirin ve *veri* dizinine kaydedin.

> [!NOTE]
> Bu öğreticide kullanılan veriler, [UCI bisiklet paylaşımı veri kümesinden](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)gelir. Fanaee-T, hadi ve gama, Joao, ' olay etiketleme birleştirme algılayıcıları ve arka plan bilgisi ', yapay zeka 'da Ilerleme (2013): PP. 1-15, Sprümlberg, [Web bağlantısı](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).

Özgün veri kümesi mevsimsellik ve hava durumu ile ilgili birkaç sütun içerir. Breçekimi ve bu öğreticide kullanılan algoritma yalnızca tek bir sayısal sütundan değer gerektirdiğinden, özgün veri kümesi yalnızca aşağıdaki sütunları içerecek şekilde yoğunlaştırılmış:

- **dteday**: Gözlem tarihi.
- **yıl**: gözlemin kodlanmış yılı (0 = 2011, 1 = 2012).
- **sayisi**: o güne ait bisiklet salları toplam sayısı.

Özgün veri kümesi, bir SQL Server veritabanında aşağıdaki şemaya sahip bir veritabanı tablosuyla eşlenir.

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

Aşağıda, verilerin bir örneği verilmiştir:

| RentalDate | Yıl | TotalRentals |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>Giriş ve çıkış sınıfları oluşturma

1. *Program.cs* dosyasını açın ve var olan `using` deyimleri şu şekilde değiştirin:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. `ModelInput` sınıfını oluşturun. Sınıfının altına `Program` aşağıdaki kodu ekleyin.

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    `ModelInput`Sınıfı şu sütunları içerir:

    - **Rentaldate**: Gözlem tarihi.
    - **Yıl**: gözlemin kodlanmış yılı (0 = 2011, 1 = 2012).
    - **Totalrentals**: Bu güne ait toplam Bisiklet randevu sayısı.

1. `ModelOutput`Yeni oluşturulan sınıfın altında sınıf oluşturun `ModelInput` .

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    `ModelOutput`Sınıfı şu sütunları içerir:

    - **ForecastedRentals**: tahmin edilen dönem için tahmin edilen değerler.
    - **Ials Boundrentals**: tahmin edilen dönem için öngörülen minimum değerler.
    - **Üsteboundrentals**: tahmin edilen dönem için öngörülen maksimum değer.

### <a name="define-paths-and-initialize-variables"></a>Yolları tanımlama ve değişkenleri başlatma

1. Yöntemi içinde `Main` , verilerinizin konumunu, Bağlantı dizenizi ve eğitilen modelin kaydedileceği yeri depolamak için değişkenleri tanımlayın.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. `mlContext` [`MLContext`](xref:Microsoft.ML.MLContext) Yöntemine aşağıdaki satırı ekleyerek değişkeni yeni bir örneğiyle başlatın `Main` .

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    [`MLContext`](xref:Microsoft.ML.MLContext)Sınıfı tüm ml.NET işlemleri için bir başlangıç noktasıdır ve mlContext 'i başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal olarak da benzerdir `DBContext` .

## <a name="load-the-data"></a>Verileri yükleme

1. `DatabaseLoader`Bu tür kayıtları yükleyen oluşturma `ModelInput` .

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. Veritabanından verileri yükleyecek sorguyu tanımlayın.

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET algoritmaları verilerin türünde olmasını bekler [`Single`](xref:System.Single) . Bu nedenle, tek duyarlıklı kayan noktalı bir değer olan, türünde olmayan veritabanından gelen sayısal değerlerin [`Real`](xref:System.Data.SqlDbType) olarak dönüştürülmesi gerekir [`Real`](xref:System.Data.SqlDbType) .

    `Year`Ve `TotalRental` sütunları, veritabanındaki tamsayı türlerdir. `CAST`Yerleşik işlevi kullanarak, her ikisi de ' a dönüştürülür `Real` .

1. `DatabaseSource`Veritabanına bağlanmak ve sorguyu yürütmek için oluşturun.

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. Verileri bir öğesine yükleyin `IDataView` .

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. Veri kümesi iki yıl değer içerir. Eğitim için yalnızca ilk yılın verileri kullanılır, ikinci yıl, gerçek değerleri model tarafından üretilen tahmine göre karşılaştırmak için tutulur. Dönüştürme kullanarak verileri filtreleyin [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) .

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    İlk yılda, `Year` parametre 1 olarak ayarlanarak yalnızca sütundaki değerler 1 ' den az `upperBound` olacak şekilde seçilir. Bunun tersine, ikinci yıl için 1 ' den büyük veya eşit değerler `lowerBound` parametresi 1 olarak ayarlanarak seçilir.

## <a name="define-time-series-analysis-pipeline"></a>Zaman serisi analizi ardışık düzenini tanımlama

1. Bir zaman serisi veri kümesindeki değerleri tahmin etmek için [Ssaforekılaringestimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) kullanan bir işlem hattı tanımlayın.

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    , `forecastingPipeline` İlk yıl ve örnekler için 365 veri noktası alır ya da zaman serisi veri kümesini parametre tarafından belirtilen 30 günlük (aylık) aralıklarına böler `seriesLength` . Bu örneklerin her biri haftalık veya 7 günlük bir pencere ile çözümlenir. Sonraki periyotalar için tahmin edilen değerin ne olduğu belirlenirken, önceki yedi günün değerleri bir tahmin yapmak için kullanılır. Model, daha sonra parametresi tarafından tanımlanan şekilde yedi dönemi tahmin etmek üzere ayarlanır `horizon` . Tahmin bilinçli bir tahmin olduğundan, her zaman %100 doğru değildir. Bu nedenle, üst ve alt sınırlar tarafından tanımlanan en iyi ve en kötü durum senaryolarında değer aralığını bilmemiz yararlı olur. Bu durumda, alt ve üst sınırlara yönelik güven düzeyi %95 olarak ayarlanmıştır. Güvenirlik düzeyi, uygun şekilde artırılabilir veya azaltılabilir. Değerin ne kadar yüksekse, istenen güven düzeyini elde etmek için Aralık üst ve alt sınır arasındadır.

1. [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*)Modeli eğitme ve verileri daha önce tanımlanan öğesine sığdırmak için yöntemini kullanın `forecastingPipeline` .

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Sonraki yılın verilerini tahmin ederek ve gerçek değerlerle karşılaştırarak modelin ne kadar iyi performans kullandığını değerlendirin.

1. Yönteminin altında `Main` adlı yeni bir yardımcı program yöntemi oluşturun `Evaluate` .

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. Yöntemi içinde `Evaluate` , eğitim modeliyle yöntemi kullanarak ikinci yılın verilerini tahmin edin [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) .

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. Yöntemini kullanarak verilerden gerçek değerleri alın [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. Yöntemini kullanarak tahmin değerlerini alın [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. Yaygın olarak hata olarak adlandırılan gerçek ve tahmin değerleri arasındaki farkı hesaplayın.

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. Ortalama mutlak hata ve kök ortalama kare hata değerlerini hesaplayarak performansı ölçün.

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    Performansı değerlendirmek için aşağıdaki ölçümler kullanılır:

    - **Mutlak ortalama hata**: kapanış tahminlerinin gerçek değere nasıl geldiğini ölçer. Bu değer 0 ile sonsuz arasında aralıklar. 0 ' a yaklaşarak modelin kalitesi daha iyidir.
    - **Kök ortalama kare hatası**: modeldeki hatayı özetler. Bu değer 0 ile sonsuz arasında aralıklar. 0 ' a yaklaşarak modelin kalitesi daha iyidir.

1. Ölçümleri konsola çıkış.

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. Yöntemi `Evaluate` içindeki yöntemini kullanın `Main` .

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>Modeli kaydetme

Modelinize memnun kaldıysanız, daha sonra diğer uygulamalarda kullanmak üzere kaydedin.

1. `Main`Yönteminde, oluşturun [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) . [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602), tek tahminleri yapmak için kullanışlı bir yöntemdir.

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. Modeli, `MLModel.zip` daha önce tanımlanan değişken tarafından belirtilen şekilde adlandırılan bir dosyaya kaydedin `modelPath` . [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*)Modeli kaydetmek için yöntemini kullanın.

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>Talebi tahmin etmek için modeli kullanın

1. Yönteminin altında `Evaluate` adlı yeni bir yardımcı program yöntemi oluşturun `Forecast` .

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. Yöntemi içinde `Forecast` , [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) sonraki yedi güne ait bir süre için bu yöntemi kullanın.

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. Gerçek ve tahmin değerlerini yedi dönem için hizalayın.

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. Tahmin çıktısını yineleyin ve konsolunda görüntüleyin.

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Yöntemi içinde `Main` `Forecast` yöntemini çağırın.

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. Uygulamayı çalıştırın. Aşağıdakine benzer bir çıktı konsolunda görünmelidir. Breçekimi için çıkış yoğunlaştırılmış.

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

Gerçek ve tahmin edilen değerlerin incelemesinde aşağıdaki ilişkiler gösterilmektedir:

![Gerçek vs tahmini karşılaştırması](./media/time-series-demand-forecasting/forecast.png)

Tahmin edilen değerler tam sayı sayısını tahmin etmez, ancak bir işlemin kaynakları kullanımlarını en uygun hale getirmesine izin veren daha dar bir değer aralığı sağlarlar.

Tebrikler! Artık Bisiklet Kiralama talebini tahmin etmek için bir zaman serisi makine öğrenimi modelini başarıyla oluşturdunuz.

Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [ML.NET 'de makine öğrenimi görevleri](../resources/tasks.md)
- [Model doğruluğunu artırma](../resources/improve-machine-learning-model-ml-net.md)
