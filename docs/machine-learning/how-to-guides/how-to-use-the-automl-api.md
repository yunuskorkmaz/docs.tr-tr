---
title: otomatik ML API ML.NET nasıl kullanılır?
description: otomatik ML API ML.NET model oluşturma işlemini otomatikleştirir ve dağıtıma hazır bir model oluşturur. Otomatik makine öğrenimi görevlerini yapılandırmak için kullanabileceğiniz seçenekleri öğrenin.
ms.date: 12/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b322c484282d025033d747d2093f7b5b4d216fde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75636568"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a>ML.NET otomatik makine öğrenme API'si nasıl kullanılır?

Otomatik makine öğrenimi (AutoML), veriye makine öğrenimi uygulama işlemini otomatikleştirir. Bir veri kümesi göz önüne alındığında, en iyi modeli seçmek için farklı veri featurizations, makine öğrenme algoritmaları ve hiperparametreler üzerinde yinelemek için bir AutoML **deneme** çalıştırabilirsiniz.

> [!NOTE]
> Bu konu, şu anda önizlemede olan ML.NET için otomatik makine öğrenimi API'sini ifade eder. Malzeme değiştirilebilir.

## <a name="load-data"></a>Veri yükleme

Otomatik makine öğrenimi, bir veri kümesinin [IDataView'a](xref:Microsoft.ML.IDataView)yüklenmesiyle desteklenir. Veriler sekmeden ayrılmış değer (TSV) dosyaları ve virgülle ayrılmış değer (CSV) dosyaları şeklinde olabilir.

Örnek:

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a>Makine öğrenimi görev türünü seçin

Bir deneme oluşturmadan önce, çözmek istediğiniz makine öğrenimi sorununun türünü belirleyin. Otomatik makine öğrenimi aşağıdaki ML görevlerini destekler:

* İkili Sınıflandırma
* Çok Sınıflı Sınıflandırma
* Regresyon
* Öneri

## <a name="create-experiment-settings"></a>Deneme ayarları oluşturma

Belirlenen ML görev türü için deneme ayarları oluşturun:

* İkili Sınıflandırma

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* Çok Sınıflı Sınıflandırma

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

Deneyler son derece yapılandırılabilir. Yapılandırma ayarlarının tam listesi için [AutoML API dokümanlarına](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) bakın.

Bazı örnekler:

1. Denemenin çalışmasına izin verilen maksimum süreyi belirtin.

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. Denemenin tamamlanması zamanlanmadan önce iptal etmek için bir iptal belirteci kullanın.

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. Farklı bir en iyi duruma alma ölçütbelirtin.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. Ayar, `CacheDirectory` AutoML görevi sırasında eğitilen tüm modellerin kaydedileceği bir dizine işaretçidir. Null `CacheDirectory` olarak ayarlanırsa, modeller diske yazılı yerine bellekte tutulur.

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. Otomatik ML'ye belirli eğitmenleri kullanmamasını öğretin.

    Görev başına en iyi duruma getirilen eğitmenlerin varsayılan listesi araştırılır. Bu liste her deneme için değiştirilebilir. Örneğin, veri setinizde yavaş çalışan eğitmenler listeden kaldırılabilir. Belirli bir eğitmen aramasını `experimentSettings.Trainers.Clear()`optimize etmek için, kullanmak istediğiniz eğitmeni ekleyin.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

ML görev başına desteklenen eğitmenlerin listesini aşağıdaki ilgili bağlantıda bulunabilir:

* [Desteklenen İkili Sınıflandırma Algoritmaları](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [Desteklenen Çok Sınıflı Sınıflandırma Algoritmaları](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [Desteklenen Regresyon Algoritmaları](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [Desteklenen Öneri Algoritmaları](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a>Metriğin optimizasyonu

Yukarıdaki örnekte gösterildiği gibi en iyi duruma getirme ölçüsü, model eğitimi sırasında en iyi duruma getirilecek ölçütü belirler. Seçebileceğiniz en iyi duruma alma ölçüsü seçtiğiniz görev türüne göre belirlenir. Aşağıda kullanılabilir ölçümlerin bir listesi yer almaktadır.

|[İkili Sınıflandırma](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [Çok Sınıflı Sınıflandırma](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[Regresyon & Önerisi](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|Doğru -luk| LogLoss | RSquared
|AreaUnderPrecisionRecallCurve | LogLossReduction | MeanAbsoluteError
|AlanUnderRocCurve | MakroDoğruluk | MeanSquaredHatası
|F1Puan | Mikro Doğruluk | RootMeanSquaredHatası
|Negatif Hassasiyet | TopKAccuracy
|Negatif Geri Çağırma |
|Pozitif Hassasiyet
|Pozitif Geri Çağırma

## <a name="data-pre-processing-and-featurization"></a>Veri ön işleme ve featurization

> [!NOTE]
> Özellik sütunu yalnızca <xref:System.Boolean>, <xref:System.Single>ve <xref:System.String>.

Veri ön işleme varsayılan olarak gerçekleşir ve aşağıdaki adımlar sizin için otomatik olarak gerçekleştirilir:

1. Yararlı bilgiler olmadan özellikleri bırakma

    Eğitim ve doğrulama kümelerinden yararlı bilgiler içeren özellikleri bırakın. Bunlar, tüm değerlerin eksik olduğu, tüm satırlarda aynı değere sahip veya son derece yüksek öneme sahip (örn. haşdi iş, iDc veya GUI'ler) özellikleri içerir.

1. Eksik değer göstergesi ve imputasyon

    Eksik değer hücrelerini veri türü için varsayılan değerle doldurun. Giriş sütunuyla aynı sayıda yuvaya sahip ek gösterge özellikleri. Eklenen gösterge özelliklerindeki değer, `1` giriş sütunundaki değerin eksik `0` olması veya başka bir şekilde olmasıdır.

1. Ek özellikler oluşturun

    Metin özellikleri için: Tek renkli ve üç karakterli gram kullanan sözcük torbası özellikleri.

    Kategorik özellikler için: Düşük kardinallik özellikleri için tek sıcak kodlama ve yüksek kardinallik kategorik özellikler için tek-sıcak karma kodlama.

1. Dönüşümler ve kodlamalar

    Çok az benzersiz değere sahip metin özellikleri, kategorik özelliklere dönüştürülür. Kategorik özelliklerin kardinalliğine bağlı olarak, tek sıcak kodlama veya tek sıcak karma kodlama gerçekleştirin.

## <a name="exit-criteria"></a>Çıkış kriterleri

Görevinizi tamamlamak için ölçütleri tanımlayın:

1. Bir süre sonra çıkın `MaxExperimentTimeInSeconds` - Deneme ayarlarınızı kullanarak bir görevin çalışmaya devam etmesi için saniyeler içinde ne kadar süre yle devam etmesi gerektiğini tanımlayabilirsiniz.

1. İptal jetonundan çıkın - Görevi bitirmeden önce iptal etmenizi sağlayan bir iptal jetonu kullanabilirsiniz.

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a>Deneme oluşturma

Deneme ayarlarını yapılandırıldıktan sonra, denemeyi oluşturmaya hazırsınız.

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a>Denemeyi çalıştırma

Denemenin çalıştırılsA, veri ön işleme, öğrenme algoritması seçimi ve hiperparametre ayarı tetikler. AutoML, deneme sona erene veya sonlandırılana kadar `MaxExperimentTimeInSeconds` featurization, öğrenme algoritmaları ve hiperparametrelerkombinasyonları oluşturmaya devam edecektir.

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

Doğrulama verilerini, `Execute()` sütun amacını belirten sütun bilgilerini veya prefeaturizers'i geçirmek istiyorsanız diğer aşırı yüklemeleri keşfedin.

## <a name="training-modes"></a>Eğitim modları

### <a name="training-dataset"></a>Eğitim veri seti

AutoML, eğitim verileri sağlamanıza olanak tanıyan aşırı yüklü bir deneme yürütme yöntemi sağlar. Dahili olarak, otomatik ML verileri tren doğrulama bölmelerine böler.

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a>Özel doğrulama veri kümesi

Zaman serisi verilerinde olduğu gibi, rasgele bölme kabul edilemezse özel doğrulama veri kümesini kullanın. Kendi doğrulama veri kümenizi belirtebilirsiniz. Model, bir veya daha fazla rasgele veri kümesi yerine belirtilen doğrulama veri kümesine göre değerlendirilir.

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a>Model ölçümlerini keşfedin

Bir ML deneyinin her yinelemeden sonra, bu göreve ilişkin ölçümler depolanır.

Örneğin, doğrulama ölçümlerine en iyi çalıştırmadan erişebiliriz:

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

Ml görevi başına tüm kullanılabilir ölçümler şunlardır:

* [İkili sınıflandırma ölçümleri](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [Çok sınıflı sınıflandırma ölçümleri](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [Öneri ölçümleri & regresyon](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a>Ayrıca bkz.

Tam kod örnekleri ve daha fazlası için [dotnet/machinelearning-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub deposunu ziyaret edin.
