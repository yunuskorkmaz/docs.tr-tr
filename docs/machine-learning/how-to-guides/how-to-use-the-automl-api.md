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
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="a063c-104">ML.NET otomatik makine öğrenme API'si nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="a063c-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="a063c-105">Otomatik makine öğrenimi (AutoML), veriye makine öğrenimi uygulama işlemini otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="a063c-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="a063c-106">Bir veri kümesi göz önüne alındığında, en iyi modeli seçmek için farklı veri featurizations, makine öğrenme algoritmaları ve hiperparametreler üzerinde yinelemek için bir AutoML **deneme** çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a063c-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="a063c-107">Bu konu, şu anda önizlemede olan ML.NET için otomatik makine öğrenimi API'sini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="a063c-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="a063c-108">Malzeme değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a063c-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="a063c-109">Veri yükleme</span><span class="sxs-lookup"><span data-stu-id="a063c-109">Load data</span></span>

<span data-ttu-id="a063c-110">Otomatik makine öğrenimi, bir veri kümesinin [IDataView'a](xref:Microsoft.ML.IDataView)yüklenmesiyle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a063c-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="a063c-111">Veriler sekmeden ayrılmış değer (TSV) dosyaları ve virgülle ayrılmış değer (CSV) dosyaları şeklinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="a063c-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="a063c-112">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a063c-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="a063c-113">Makine öğrenimi görev türünü seçin</span><span class="sxs-lookup"><span data-stu-id="a063c-113">Select the machine learning task type</span></span>

<span data-ttu-id="a063c-114">Bir deneme oluşturmadan önce, çözmek istediğiniz makine öğrenimi sorununun türünü belirleyin.</span><span class="sxs-lookup"><span data-stu-id="a063c-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="a063c-115">Otomatik makine öğrenimi aşağıdaki ML görevlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="a063c-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="a063c-116">İkili Sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="a063c-116">Binary Classification</span></span>
* <span data-ttu-id="a063c-117">Çok Sınıflı Sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="a063c-117">Multiclass Classification</span></span>
* <span data-ttu-id="a063c-118">Regresyon</span><span class="sxs-lookup"><span data-stu-id="a063c-118">Regression</span></span>
* <span data-ttu-id="a063c-119">Öneri</span><span class="sxs-lookup"><span data-stu-id="a063c-119">Recommendation</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="a063c-120">Deneme ayarları oluşturma</span><span class="sxs-lookup"><span data-stu-id="a063c-120">Create experiment settings</span></span>

<span data-ttu-id="a063c-121">Belirlenen ML görev türü için deneme ayarları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a063c-121">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="a063c-122">İkili Sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="a063c-122">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="a063c-123">Çok Sınıflı Sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="a063c-123">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="a063c-124">Regresyon</span><span class="sxs-lookup"><span data-stu-id="a063c-124">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* <span data-ttu-id="a063c-125">Öneri</span><span class="sxs-lookup"><span data-stu-id="a063c-125">Recommendation</span></span>

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="a063c-126">Deneme ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a063c-126">Configure experiment settings</span></span>

<span data-ttu-id="a063c-127">Deneyler son derece yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a063c-127">Experiments are highly configurable.</span></span> <span data-ttu-id="a063c-128">Yapılandırma ayarlarının tam listesi için [AutoML API dokümanlarına](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) bakın.</span><span class="sxs-lookup"><span data-stu-id="a063c-128">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) for a full list of configuration settings.</span></span>

<span data-ttu-id="a063c-129">Bazı örnekler:</span><span class="sxs-lookup"><span data-stu-id="a063c-129">Some examples include:</span></span>

1. <span data-ttu-id="a063c-130">Denemenin çalışmasına izin verilen maksimum süreyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="a063c-130">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="a063c-131">Denemenin tamamlanması zamanlanmadan önce iptal etmek için bir iptal belirteci kullanın.</span><span class="sxs-lookup"><span data-stu-id="a063c-131">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="a063c-132">Farklı bir en iyi duruma alma ölçütbelirtin.</span><span class="sxs-lookup"><span data-stu-id="a063c-132">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="a063c-133">Ayar, `CacheDirectory` AutoML görevi sırasında eğitilen tüm modellerin kaydedileceği bir dizine işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="a063c-133">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="a063c-134">Null `CacheDirectory` olarak ayarlanırsa, modeller diske yazılı yerine bellekte tutulur.</span><span class="sxs-lookup"><span data-stu-id="a063c-134">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="a063c-135">Otomatik ML'ye belirli eğitmenleri kullanmamasını öğretin.</span><span class="sxs-lookup"><span data-stu-id="a063c-135">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="a063c-136">Görev başına en iyi duruma getirilen eğitmenlerin varsayılan listesi araştırılır.</span><span class="sxs-lookup"><span data-stu-id="a063c-136">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="a063c-137">Bu liste her deneme için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a063c-137">This list can be modified for each experiment.</span></span> <span data-ttu-id="a063c-138">Örneğin, veri setinizde yavaş çalışan eğitmenler listeden kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a063c-138">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="a063c-139">Belirli bir eğitmen aramasını `experimentSettings.Trainers.Clear()`optimize etmek için, kullanmak istediğiniz eğitmeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a063c-139">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="a063c-140">ML görev başına desteklenen eğitmenlerin listesini aşağıdaki ilgili bağlantıda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="a063c-140">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="a063c-141">Desteklenen İkili Sınıflandırma Algoritmaları</span><span class="sxs-lookup"><span data-stu-id="a063c-141">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="a063c-142">Desteklenen Çok Sınıflı Sınıflandırma Algoritmaları</span><span class="sxs-lookup"><span data-stu-id="a063c-142">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="a063c-143">Desteklenen Regresyon Algoritmaları</span><span class="sxs-lookup"><span data-stu-id="a063c-143">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [<span data-ttu-id="a063c-144">Desteklenen Öneri Algoritmaları</span><span class="sxs-lookup"><span data-stu-id="a063c-144">Supported Recommendation Algorithms</span></span>](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="a063c-145">Metriğin optimizasyonu</span><span class="sxs-lookup"><span data-stu-id="a063c-145">Optimizing metric</span></span>

<span data-ttu-id="a063c-146">Yukarıdaki örnekte gösterildiği gibi en iyi duruma getirme ölçüsü, model eğitimi sırasında en iyi duruma getirilecek ölçütü belirler.</span><span class="sxs-lookup"><span data-stu-id="a063c-146">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="a063c-147">Seçebileceğiniz en iyi duruma alma ölçüsü seçtiğiniz görev türüne göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a063c-147">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="a063c-148">Aşağıda kullanılabilir ölçümlerin bir listesi yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="a063c-148">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="a063c-149">İkili Sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="a063c-149">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="a063c-150">Çok Sınıflı Sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="a063c-150">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="a063c-151">Regresyon & Önerisi</span><span class="sxs-lookup"><span data-stu-id="a063c-151">Regression & Recommendation</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="a063c-152">Doğru -luk</span><span class="sxs-lookup"><span data-stu-id="a063c-152">Accuracy</span></span>| <span data-ttu-id="a063c-153">LogLoss</span><span class="sxs-lookup"><span data-stu-id="a063c-153">LogLoss</span></span> | <span data-ttu-id="a063c-154">RSquared</span><span class="sxs-lookup"><span data-stu-id="a063c-154">RSquared</span></span>
|<span data-ttu-id="a063c-155">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="a063c-155">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="a063c-156">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="a063c-156">LogLossReduction</span></span> | <span data-ttu-id="a063c-157">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="a063c-157">MeanAbsoluteError</span></span>
|<span data-ttu-id="a063c-158">AlanUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="a063c-158">AreaUnderRocCurve</span></span> | <span data-ttu-id="a063c-159">MakroDoğruluk</span><span class="sxs-lookup"><span data-stu-id="a063c-159">MacroAccuracy</span></span> | <span data-ttu-id="a063c-160">MeanSquaredHatası</span><span class="sxs-lookup"><span data-stu-id="a063c-160">MeanSquaredError</span></span>
|<span data-ttu-id="a063c-161">F1Puan</span><span class="sxs-lookup"><span data-stu-id="a063c-161">F1Score</span></span> | <span data-ttu-id="a063c-162">Mikro Doğruluk</span><span class="sxs-lookup"><span data-stu-id="a063c-162">MicroAccuracy</span></span> | <span data-ttu-id="a063c-163">RootMeanSquaredHatası</span><span class="sxs-lookup"><span data-stu-id="a063c-163">RootMeanSquaredError</span></span>
|<span data-ttu-id="a063c-164">Negatif Hassasiyet</span><span class="sxs-lookup"><span data-stu-id="a063c-164">NegativePrecision</span></span> | <span data-ttu-id="a063c-165">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="a063c-165">TopKAccuracy</span></span>
|<span data-ttu-id="a063c-166">Negatif Geri Çağırma</span><span class="sxs-lookup"><span data-stu-id="a063c-166">NegativeRecall</span></span> |
|<span data-ttu-id="a063c-167">Pozitif Hassasiyet</span><span class="sxs-lookup"><span data-stu-id="a063c-167">PositivePrecision</span></span>
|<span data-ttu-id="a063c-168">Pozitif Geri Çağırma</span><span class="sxs-lookup"><span data-stu-id="a063c-168">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="a063c-169">Veri ön işleme ve featurization</span><span class="sxs-lookup"><span data-stu-id="a063c-169">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="a063c-170">Özellik sütunu yalnızca <xref:System.Boolean>, <xref:System.Single>ve <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a063c-170">The feature column only supported types of <xref:System.Boolean>, <xref:System.Single>, and <xref:System.String>.</span></span>

<span data-ttu-id="a063c-171">Veri ön işleme varsayılan olarak gerçekleşir ve aşağıdaki adımlar sizin için otomatik olarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="a063c-171">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="a063c-172">Yararlı bilgiler olmadan özellikleri bırakma</span><span class="sxs-lookup"><span data-stu-id="a063c-172">Drop features with no useful information</span></span>

    <span data-ttu-id="a063c-173">Eğitim ve doğrulama kümelerinden yararlı bilgiler içeren özellikleri bırakın.</span><span class="sxs-lookup"><span data-stu-id="a063c-173">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="a063c-174">Bunlar, tüm değerlerin eksik olduğu, tüm satırlarda aynı değere sahip veya son derece yüksek öneme sahip (örn. haşdi iş, iDc veya GUI'ler) özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a063c-174">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="a063c-175">Eksik değer göstergesi ve imputasyon</span><span class="sxs-lookup"><span data-stu-id="a063c-175">Missing value indication and imputation</span></span>

    <span data-ttu-id="a063c-176">Eksik değer hücrelerini veri türü için varsayılan değerle doldurun.</span><span class="sxs-lookup"><span data-stu-id="a063c-176">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="a063c-177">Giriş sütunuyla aynı sayıda yuvaya sahip ek gösterge özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a063c-177">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="a063c-178">Eklenen gösterge özelliklerindeki değer, `1` giriş sütunundaki değerin eksik `0` olması veya başka bir şekilde olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a063c-178">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="a063c-179">Ek özellikler oluşturun</span><span class="sxs-lookup"><span data-stu-id="a063c-179">Generate additional features</span></span>

    <span data-ttu-id="a063c-180">Metin özellikleri için: Tek renkli ve üç karakterli gram kullanan sözcük torbası özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a063c-180">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>

    <span data-ttu-id="a063c-181">Kategorik özellikler için: Düşük kardinallik özellikleri için tek sıcak kodlama ve yüksek kardinallik kategorik özellikler için tek-sıcak karma kodlama.</span><span class="sxs-lookup"><span data-stu-id="a063c-181">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="a063c-182">Dönüşümler ve kodlamalar</span><span class="sxs-lookup"><span data-stu-id="a063c-182">Transformations and encodings</span></span>

    <span data-ttu-id="a063c-183">Çok az benzersiz değere sahip metin özellikleri, kategorik özelliklere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a063c-183">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="a063c-184">Kategorik özelliklerin kardinalliğine bağlı olarak, tek sıcak kodlama veya tek sıcak karma kodlama gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="a063c-184">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="a063c-185">Çıkış kriterleri</span><span class="sxs-lookup"><span data-stu-id="a063c-185">Exit criteria</span></span>

<span data-ttu-id="a063c-186">Görevinizi tamamlamak için ölçütleri tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="a063c-186">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="a063c-187">Bir süre sonra çıkın `MaxExperimentTimeInSeconds` - Deneme ayarlarınızı kullanarak bir görevin çalışmaya devam etmesi için saniyeler içinde ne kadar süre yle devam etmesi gerektiğini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a063c-187">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="a063c-188">İptal jetonundan çıkın - Görevi bitirmeden önce iptal etmenizi sağlayan bir iptal jetonu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a063c-188">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="a063c-189">Deneme oluşturma</span><span class="sxs-lookup"><span data-stu-id="a063c-189">Create an experiment</span></span>

<span data-ttu-id="a063c-190">Deneme ayarlarını yapılandırıldıktan sonra, denemeyi oluşturmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="a063c-190">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="a063c-191">Denemeyi çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a063c-191">Run the experiment</span></span>

<span data-ttu-id="a063c-192">Denemenin çalıştırılsA, veri ön işleme, öğrenme algoritması seçimi ve hiperparametre ayarı tetikler.</span><span class="sxs-lookup"><span data-stu-id="a063c-192">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="a063c-193">AutoML, deneme sona erene veya sonlandırılana kadar `MaxExperimentTimeInSeconds` featurization, öğrenme algoritmaları ve hiperparametrelerkombinasyonları oluşturmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="a063c-193">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="a063c-194">Doğrulama verilerini, `Execute()` sütun amacını belirten sütun bilgilerini veya prefeaturizers'i geçirmek istiyorsanız diğer aşırı yüklemeleri keşfedin.</span><span class="sxs-lookup"><span data-stu-id="a063c-194">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="a063c-195">Eğitim modları</span><span class="sxs-lookup"><span data-stu-id="a063c-195">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="a063c-196">Eğitim veri seti</span><span class="sxs-lookup"><span data-stu-id="a063c-196">Training dataset</span></span>

<span data-ttu-id="a063c-197">AutoML, eğitim verileri sağlamanıza olanak tanıyan aşırı yüklü bir deneme yürütme yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a063c-197">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="a063c-198">Dahili olarak, otomatik ML verileri tren doğrulama bölmelerine böler.</span><span class="sxs-lookup"><span data-stu-id="a063c-198">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="a063c-199">Özel doğrulama veri kümesi</span><span class="sxs-lookup"><span data-stu-id="a063c-199">Custom validation dataset</span></span>

<span data-ttu-id="a063c-200">Zaman serisi verilerinde olduğu gibi, rasgele bölme kabul edilemezse özel doğrulama veri kümesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a063c-200">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="a063c-201">Kendi doğrulama veri kümenizi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a063c-201">You can specify your own validation dataset.</span></span> <span data-ttu-id="a063c-202">Model, bir veya daha fazla rasgele veri kümesi yerine belirtilen doğrulama veri kümesine göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a063c-202">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a><span data-ttu-id="a063c-203">Model ölçümlerini keşfedin</span><span class="sxs-lookup"><span data-stu-id="a063c-203">Explore model metrics</span></span>

<span data-ttu-id="a063c-204">Bir ML deneyinin her yinelemeden sonra, bu göreve ilişkin ölçümler depolanır.</span><span class="sxs-lookup"><span data-stu-id="a063c-204">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="a063c-205">Örneğin, doğrulama ölçümlerine en iyi çalıştırmadan erişebiliriz:</span><span class="sxs-lookup"><span data-stu-id="a063c-205">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="a063c-206">Ml görevi başına tüm kullanılabilir ölçümler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a063c-206">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="a063c-207">İkili sınıflandırma ölçümleri</span><span class="sxs-lookup"><span data-stu-id="a063c-207">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="a063c-208">Çok sınıflı sınıflandırma ölçümleri</span><span class="sxs-lookup"><span data-stu-id="a063c-208">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="a063c-209">Öneri ölçümleri & regresyon</span><span class="sxs-lookup"><span data-stu-id="a063c-209">Regression & recommendation metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="a063c-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a063c-210">See also</span></span>

<span data-ttu-id="a063c-211">Tam kod örnekleri ve daha fazlası için [dotnet/machinelearning-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub deposunu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="a063c-211">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
