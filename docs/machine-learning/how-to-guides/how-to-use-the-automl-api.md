---
title: ML.NET otomatik ML API 'sini kullanma
description: ML.NET otomatikleştirilen ML API 'SI, model oluşturma işlemini otomatikleştirir ve dağıtım için hazırlamış bir model oluşturur. Otomatik makine öğrenimi görevlerini yapılandırmak için kullanabileceğiniz seçenekleri öğrenin.
ms.date: 12/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 31204610d471f13aca177f0d599c1eba5cd7a624
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876349"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a>ML.NET otomatik makine öğrenimi API 'sini kullanma

Otomatik makine öğrenimi (Otomatikml), verileri makineye öğrenmeyi uygulama işlemini otomatikleştirir. Bir veri kümesi verildiğinde, en iyi modeli seçmek için farklı veri özelliklerini, makine öğrenimi algoritmalarını ve hiper parametreleri yinelemek üzere bir **oto ml denemesi** çalıştırabilirsiniz.

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET için otomatik makine öğrenimi API 'sine başvurur. Malzemeler değişebilir.

## <a name="load-data"></a>Veri yükleme

Otomatik makine öğrenimi, bir veri kümesinin bir [ıdataview](xref:Microsoft.ML.IDataView)içine yüklenmesini destekler. Veriler sekmeyle ayrılmış değer (TSV) dosyaları ve virgülle ayrılmış değer (CSV) dosyaları biçiminde olabilir.

Örnek:

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a>Machine Learning görev türünü seçin

Bir deneme oluşturmadan önce, çözmek istediğiniz makine öğrenimi sorunu türünü saptayın. Otomatik makine öğrenimi aşağıdaki ML görevlerini destekler:

* İkili sınıflandırma
* Birden çok Lass sınıflandırması
* Regresyon
* Öneri

## <a name="create-experiment-settings"></a>Deneme ayarları oluşturma

Belirlenen ML görev türü için deneme ayarları oluşturun:

* İkili sınıflandırma

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* Birden çok Lass sınıflandırması

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* Regresyon

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* Öneri

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a>Deneme ayarlarını yapılandırma

Denemeleri, yüksek oranda yapılandırılabilir. Yapılandırma ayarlarının tam listesi için bkz. [oto ml API belgeleri](/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) .

Bazı örnekler:

1. Denemenin çalışmasına izin verilen en uzun süreyi belirtin.

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. Tamamlanmak üzere zamanlanmadan önce denemeyi iptal etmek için bir iptal belirteci kullanın.

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. Farklı bir iyileştirmeli ölçüm belirtin.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. Bu `CacheDirectory` ayar, otomatik ml görevi sırasında eğitilen tüm modellerin kaydedileceği dizine yönelik bir işaretçidir. `CacheDirectory`Null olarak ayarlanırsa, modeller diske yazılmak yerine bellekte tutulur.

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. Otomatikleştirilmiş ML 'nin belirli eğitimleri kullanmamasını söyleyin.

    En iyileştirmek için, görev başına araştırılan varsayılan bir liste. Bu liste, her deneme için değiştirilebilir. Örneğin, veri kümeniz üzerinde yavaş çalışan traıners listeden kaldırılabilir. Tek bir belirli bir seyahat çağrısını iyileştirmek için `experimentSettings.Trainers.Clear()` , kullanmak istediğiniz eğitmen 'ı ekleyin.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

ML başına desteklenen aers görevleri listesi aşağıdaki ilgili bağlantıda bulunabilir:

* [Desteklenen Ikili sınıflandırma algoritmaları](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [Desteklenen birden çok Lass sınıflandırma algoritması](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [Desteklenen Regresyon algoritmaları](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [Desteklenen öneri algoritmaları](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a>Ölçümü iyileştirme

Yukarıdaki örnekte gösterildiği gibi en iyileştirme ölçümü, model eğitimi sırasında en iyi duruma getirilecek ölçümü belirler. Seçebileceğiniz ölçüm en iyi duruma getirme, seçtiğiniz görev türüne göre belirlenir. Kullanılabilir ölçümlerin listesi aşağıda verilmiştir.

|[İkili sınıflandırma](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [Birden çok Lass sınıflandırması](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[Gerileme & önerisi](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|Veritabanınızın| Logkaybetme | RKARE
|Areaunderperrecallcurve | LogLossReduction | MeanAbsoluteError
|AreaUnderRocCurve | Makro doğruluğu | Ortalamasquare
|F1Score | Mikro doğruluk | Rootortalamasquarebir
|NegativePrecision | Topkdoğruluk
|Negatiftiverecall |
|PositivePrecision
|PositiveRecall

## <a name="data-pre-processing-and-featurization"></a>Veri ön işleme ve korleştirme

> [!NOTE]
> Özellik sütunu yalnızca, ve türleri için <xref:System.Boolean> desteklenir <xref:System.Single> <xref:System.String> .

Verilerin ön işlemesi varsayılan olarak gerçekleşir ve aşağıdaki adımlar sizin için otomatik olarak gerçekleştirilir:

1. Yararlı bilgiler olmadan bırakma özellikleri

    Eğitim ve doğrulama kümelerinden yararlı bilgiler olmadan özellikleri bırakın. Bunlar tüm değerler eksik, tüm satırlarda aynı değere sahip olan veya son derece yüksek kardinalite (örn. karma, kimlik veya GUID) ile özellikleri içerir.

1. Eksik değer gösterimi ve imputation

    Eksik değer hücrelerini, veri türü için varsayılan değerle doldur. Giriş sütunuyla aynı sayıda yuva içeren gösterge özellikleri ekleyin. Eklenen gösterge özelliklerinin değeri, `1` giriş sütunundaki değerin eksik olması ve `0` Aksi durumda.

1. Ek özellikler oluştur

    Metin özellikleri için: unigram ve üçlü karakter-gram kullanan sözcük paketi özellikleri.

    Kategorik özellikler için: düşük kardinalite özelliklerine yönelik tek yönlü bir kodlama ve yüksek kardinalite kategorik özellikleri için tek Hot-Hash kodlaması.

1. Dönüşümler ve kodlamalar

    Kategorik özelliklere dönüştürülen çok az benzersiz değerler içeren metin özellikleri. Kategorik özelliklerin kardinalitesine bağlı olarak, tek başına kodlama veya tek yönlü karma kodlama gerçekleştirin.

## <a name="exit-criteria"></a>Çıkış kriterleri

Görevinizi tamamlamaya yönelik ölçütleri tanımlayın:

1. Deneme ayarlarınızda bir süre geçtikten sonra çık `MaxExperimentTimeInSeconds` bir görevin çalışmaya devam etmesi için saniye cinsinden süreyi tanımlayabilirsiniz.

1. İptal belirtecinden çıkma-işlemi tamamlamak için zamanlanmadan önce, görevi iptal etmenizi sağlayan bir iptal belirteci kullanabilirsiniz.

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a>Deneme oluşturma

Deneme ayarlarını yapılandırdıktan sonra, denemeyi oluşturmaya hazırlanın.

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a>Denemeyi çalıştırma

Denemeyi çalıştırmak, verileri önceden işleme, öğrenme algoritması seçimi ve hiper parametre ayarlamayı tetikler. Oto, `MaxExperimentTimeInSeconds` ulaşılıncaya veya deneme sonlandırılana kadar doğru şekilde, öğrenme algoritmalarının ve hiper parametrelerin birleşimlerini oluşturmaya devam edecektir.

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

`Execute()`Doğrulama verilerini, sütun amacını veya ön ek türleyicileri belirten sütun bilgilerini geçirmek istiyorsanız için diğer aşırı yüklemeleri keşfet.

## <a name="training-modes"></a>Eğitim modları

### <a name="training-dataset"></a>Eğitim veri kümesi

Oto ml, eğitim verileri sağlamanıza olanak tanıyan aşırı yüklenmiş bir deneme yürütme yöntemi sağlar. Dahili olarak, otomatik ML verileri eğitme-doğrulama bölmelere ayırır.

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a>Özel doğrulama veri kümesi

Genellikle zaman serisi verilerinde olduğu gibi rastgele bölme kabul edilebilir değilse, özel doğrulama veri kümesini kullanın. Kendi doğrulama veri kümenizi belirtebilirsiniz. Model, bir veya daha fazla rastgele veri kümesi yerine belirtilen doğrulama veri kümesine göre değerlendirilir.

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a>Model ölçümlerini keşfet

Her bir ML denemesinin yinelemesinden sonra, bu görevle ilgili ölçümler depolanır.

Örneğin, en iyi çalıştırmasından doğrulama ölçümlerine erişebiliriz:

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

Her ML görevi için kullanılabilir ölçümler şunlardır:

* [İkili sınıflandırma ölçümleri](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [Birden çok Lass sınıflandırma ölçümleri](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [Gerileme & öneri ölçümleri](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a>Ayrıca bkz.

Tam kod örnekleri için [DotNet/machinöğrenim-Samples](https://github.com/dotnet/machinelearning-samples/tree/main#automate-mlnet-models-generation-preview-state) GitHub deposunu ziyaret edin.
