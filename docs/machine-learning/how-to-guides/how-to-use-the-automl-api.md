---
title: ML API ML.NET kullanmayı otomatik
description: ML API ML.NET otomatik oluşturma işlemi model otomatikleştirir ve dağıtım için hazır bir model oluşturur. Otomatik makine öğrenimi görevlerini yapılandırmak için kullanabileceğiniz seçenekleri öğrenin.
ms.date: 04/24/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 21bf594ba70e8c466cba757ca4dcfe39ddfa4d1e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641232"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a>Machine learning API ML.NET kullanmayı otomatik

Otomatik machine learning (AutoML), machine learning için verileri uygulamaya işlemini otomatikleştirir. Bir veri kümesi göz önünde bulundurulduğunda, bir AutoML çalıştırabilirsiniz **deneme** farklı veri featurizations yinelemek için makine öğrenimi algoritmaları ve en iyi modeli seçmek için hiperparametreleri.

> [!NOTE]
> Bu konu, otomatik makine şu anda Önizleme aşamasında olan ML.NET için API öğrenimi ifade eder. Malzeme değişiklik gösterebilir.

## <a name="load-data"></a>Veri yükleme

Bir veri kümesine veri yüklemeyi destekliyor otomatik makine bir [IDataView](xref:Microsoft.ML.IDataView). Veriler, virgülle ayrılmış değer (TSV) dosyaları ve virgülle ayrılmış değer (CSV) dosya biçiminde olabilir.

Örnek:

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a>Makine öğrenimi görev türü seçin
Bir deney oluşturmadan önce makine öğrenme problemi çözmek istediğiniz türünü belirler. Otomatik machine learning aşağıdaki ML görevleri destekler:
* İkili sınıflandırma
* Sınıflı sınıflandırma
* Regresyon

## <a name="create-experiment-settings"></a>Deneme ayarları oluşturma

Deneme ayarları için belirlenen ML görev türü oluşturun:

* İkili sınıflandırma

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* Sınıflı sınıflandırma

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* Regresyon

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a>Deneme ayarlarını yapılandırma

Denemeleri, yüksek oranda yapılandırılabilir özelliktedir. Bkz: [AutoML API belgeleri](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) yapılandırma ayarlarının tam listesi için.

Bazı örnekler:

1. Denemeyi çalıştırmak için izin verilen en uzun süreyi belirtin.

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. Tamamlanmak üzere zamanlanan önce denemeyi iptal etmek için bir iptal belirteci kullanın.

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. Farklı bir en iyi duruma getirme ölçüm belirtin.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. `CacheDirectory` AutoML görev sırasında geliştirilen tüm modellerinin nereye kaydedileceği bir dizin için bir işaretçi bir ayardır. Varsa `CacheDirectory` ayarlamak null modelleri yerine bellektir tutulacak diske.
 
    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. Belirli Eğitmenler kullanmayı otomatik ML isteyin.

    Varsayılan listesini Eğitmenler en iyi duruma getirme görev incelediniz. Bu liste her deneme için değiştirilebilir. Örneğin, veri kümenize yavaş çalışmasına Eğitmenler listeden kaldırılabilir. Belirli bir eğitmen çağrıda en iyi duruma getirme `experimentSettings.Trainers.Clear()`, ardından kullanmak istediğiniz Eğitmeni ekleyin.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

ML görev başına desteklenen Eğitmenler listesini aşağıdaki karşılık gelen bağlantıda bulunabilir:
* [İkili sınıflandırma algoritmaları desteklenir.](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.binaryclassificationtrainer?view=automl-dotnet)
* [Sınıflı sınıflandırma algoritmaları desteklenir.](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.multiclassclassificationtrainer?view=automl-dotnet)
* [Desteklenen regresyon algoritmaları](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.regressiontrainer?view=automl-dotnet)

## <a name="optimizing-metric"></a>Ölçüm en iyi duruma getirme

Yukarıdaki örnekte gösterildiği gibi en iyi duruma getirme ölçüm modeli eğitimi sırasında en iyi duruma getirilmesi ölçüm belirler. Seçebileceğiniz en iyi duruma getirme ölçüm seçtiğiniz görev türüne göre belirlenir. Ölçümlerin bir listesi aşağıda verilmiştir.

|[İkili sınıflandırma](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.binaryclassificationmetric?view=automl-dotnet) | [Sınıflı sınıflandırma](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.multiclassclassificationmetric?view=automl-dotnet) | [Regresyon](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.regressionmetric?view=automl-dotnet)
|-- |-- |--
|Doğruluğu| LogLoss | RSquared
|AreaUnderPrecisionRecallCurve | LogLossReduction | MeanAbsoluteError
|AreaUnderRocCurve | MacroAccuracy | MeanSquaredError
|F1Score | MicroAccuracy | RootMeanSquaredError
|NegativePrecision | TopKAccuracy
|NegativeRecall |
|PositivePrecision
|PositiveRecall

## <a name="data-pre-processing-and-featurization"></a>Veri ön işleme ve özellik kazandırma sayesinde

Varsayılan olarak veri ön işleme olur ve aşağıdaki adımları sizin için otomatik olarak gerçekleştirilir:

1. Hiçbir yararlı bilgiler özelliklerle bırak

    Hiçbir yararlı bilgiler özellikleriyle, eğitim ve doğrulama kümesinden bırakın. Bu, eksik, tüm değerlerin tüm satırlar boyunca veya son derece yüksek kardinalite (örneğin, karmaları kimlikleri veya GUID'leri) ile aynı değere sahip özellikler içerir.

1. İmputation ve eksik değer göstergesi

    Veri türü için varsayılan değer ile eksik değer hücrelere doldurun. Göstergesi özelliklerle aynı yuva sayısı giriş sütun olarak ekleyin. Eklenen gösterge özellikleri değer `1` giriş sütunundaki değeri eksik olup olmadığını ve `0` Aksi takdirde.

1. Ek özellikler oluşturma
    
    Metin özellikleri: Unigrams ve üç karakter gram kullanarak word paketi özellik.
    
    Kategorik özellikleri: Bir sık erişimli düşük önem düzeyi özellikleri için kodlama ve bir-sık erişimli-hash kodlama için yüksek kardinalite kategorik özellikleri.

1. Dönüşümler ve kodlamaları

    Metin özellikleri kategorik özelliklerini dönüştürülmüş çok az benzersiz değerlere sahip. Bağlı olarak kardinalite kategorik özelliklerinin kodlama bir seyrek veya sık erişimli bir karma kodlama gerçekleştirin.

## <a name="exit-criteria"></a>Sonlandırma kriteri

Görevinizi tamamlamak için ölçütleri tanımlayın:

1. Bir süre boyunca - sonra çıkış kullanarak `MaxExperimentTimeInSeconds` deneme ayarlarınızda ne kadar süreyle bir görevi çalıştırmaya devam etmeli saniyeler içinde tanımlayabilirsiniz.

1. Çıkış bir iptal belirteci - tamamlanmak üzere zamanlanan önce görevi iptal olanak sağlayan bir iptal belirteci kullanabilirsiniz.

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a>Bir deneme oluşturma

Deneme ayarlarını yapılandırdıktan sonra bir deneme oluşturmak hazır olursunuz.

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a>Denemeyi çalıştırma

Ön işleme, öğrenme algoritması seçme ve hiper parametre ayarı deneme Tetikleyicileri veri çalışıyor. Özellik kazandırma sayesinde, öğrenme algoritmaları ve kadar hiperparametreleri bileşimi oluşturmak AutoML devam `MaxExperimentTimeInSeconds` ulaşıldığında veya denemeyi sonlandırılır.

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

Diğer aşırı yüklemeler için keşfetmek `Execute()` doğrulama verileri, sütun amaçlı ya da prefeaturizers gösteren sütun bilgileri geçirmek istiyorsanız.

## <a name="training-modes"></a>Eğitim modları

### <a name="training-dataset"></a>Eğitim veri kümesi

AutoML sağlar, aşırı yüklenmiş bir deneme yürütme yöntemi, eğitim verilerini sağlamanıza olanak verir. Dahili olarak, otomatik ML veri train-validate bölmelerini böler.

```csharp
experiment.Execute(trainDataView);   
```

### <a name="custom-validation-dataset"></a>Özel doğrulama veri kümesi

Genellikle zaman serisi verileri ile olduğu gibi rastgele bölünmüş kabul edilebilir değilse, özel doğrulama veri kümesi kullanın. Kendi doğrulama veri kümesi belirtebilirsiniz. Model doğrulama veri kümesi bir veya daha fazla rastgele veri kümeleri yerine belirtilen karşı değerlendirilir.

```csharp
experiment.Execute(trainDataView, validationDataView);   
```

## <a name="explore-model-metrics"></a>Model ölçümleri keşfedin

ML denemesi her yinelemeden sonra bu görevle ilgili ölçümleri depolanır.

Örneğin, size en iyi çalıştırmadan doğrulama ölçümleri erişebilirsiniz:

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

ML görev başına kullanılabilen tüm ölçümler şunlardır:
* [İkili sınıflandırma ölçümleri](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.binaryclassificationmetric?view=automl-dotnet
)
* [Sınıflı sınıflandırma ölçümleri](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.multiclassclassificationmetric?view=automl-dotnet
)
* [Regresyon ölçümleri](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.regressionmetric?view=automl-dotnet
)

## <a name="see-also"></a>Ayrıca bkz.

Tam kod örnekleri ve daha fazla bilgi için ziyaret [machinelearning/dotnet-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub deposu.
