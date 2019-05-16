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
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="274ac-104">Machine learning API ML.NET kullanmayı otomatik</span><span class="sxs-lookup"><span data-stu-id="274ac-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="274ac-105">Otomatik machine learning (AutoML), machine learning için verileri uygulamaya işlemini otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="274ac-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="274ac-106">Bir veri kümesi göz önünde bulundurulduğunda, bir AutoML çalıştırabilirsiniz **deneme** farklı veri featurizations yinelemek için makine öğrenimi algoritmaları ve en iyi modeli seçmek için hiperparametreleri.</span><span class="sxs-lookup"><span data-stu-id="274ac-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="274ac-107">Bu konu, otomatik makine şu anda Önizleme aşamasında olan ML.NET için API öğrenimi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="274ac-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="274ac-108">Malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="274ac-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="274ac-109">Veri yükleme</span><span class="sxs-lookup"><span data-stu-id="274ac-109">Load data</span></span>

<span data-ttu-id="274ac-110">Bir veri kümesine veri yüklemeyi destekliyor otomatik makine bir [IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="274ac-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="274ac-111">Veriler, virgülle ayrılmış değer (TSV) dosyaları ve virgülle ayrılmış değer (CSV) dosya biçiminde olabilir.</span><span class="sxs-lookup"><span data-stu-id="274ac-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="274ac-112">Örnek:</span><span class="sxs-lookup"><span data-stu-id="274ac-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="274ac-113">Makine öğrenimi görev türü seçin</span><span class="sxs-lookup"><span data-stu-id="274ac-113">Select the machine learning task type</span></span>
<span data-ttu-id="274ac-114">Bir deney oluşturmadan önce makine öğrenme problemi çözmek istediğiniz türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="274ac-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="274ac-115">Otomatik machine learning aşağıdaki ML görevleri destekler:</span><span class="sxs-lookup"><span data-stu-id="274ac-115">Automated machine learning supports the following ML tasks:</span></span>
* <span data-ttu-id="274ac-116">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="274ac-116">Binary Classification</span></span>
* <span data-ttu-id="274ac-117">Sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="274ac-117">Multiclass Classification</span></span>
* <span data-ttu-id="274ac-118">Regresyon</span><span class="sxs-lookup"><span data-stu-id="274ac-118">Regression</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="274ac-119">Deneme ayarları oluşturma</span><span class="sxs-lookup"><span data-stu-id="274ac-119">Create experiment settings</span></span>

<span data-ttu-id="274ac-120">Deneme ayarları için belirlenen ML görev türü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="274ac-120">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="274ac-121">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="274ac-121">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="274ac-122">Sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="274ac-122">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="274ac-123">Regresyon</span><span class="sxs-lookup"><span data-stu-id="274ac-123">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="274ac-124">Deneme ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="274ac-124">Configure experiment settings</span></span>

<span data-ttu-id="274ac-125">Denemeleri, yüksek oranda yapılandırılabilir özelliktedir.</span><span class="sxs-lookup"><span data-stu-id="274ac-125">Experiments are highly configurable.</span></span> <span data-ttu-id="274ac-126">Bkz: [AutoML API belgeleri](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) yapılandırma ayarlarının tam listesi için.</span><span class="sxs-lookup"><span data-stu-id="274ac-126">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) for a full list of configuration settings.</span></span>

<span data-ttu-id="274ac-127">Bazı örnekler:</span><span class="sxs-lookup"><span data-stu-id="274ac-127">Some examples include:</span></span>

1. <span data-ttu-id="274ac-128">Denemeyi çalıştırmak için izin verilen en uzun süreyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="274ac-128">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="274ac-129">Tamamlanmak üzere zamanlanan önce denemeyi iptal etmek için bir iptal belirteci kullanın.</span><span class="sxs-lookup"><span data-stu-id="274ac-129">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="274ac-130">Farklı bir en iyi duruma getirme ölçüm belirtin.</span><span class="sxs-lookup"><span data-stu-id="274ac-130">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="274ac-131">`CacheDirectory` AutoML görev sırasında geliştirilen tüm modellerinin nereye kaydedileceği bir dizin için bir işaretçi bir ayardır.</span><span class="sxs-lookup"><span data-stu-id="274ac-131">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="274ac-132">Varsa `CacheDirectory` ayarlamak null modelleri yerine bellektir tutulacak diske.</span><span class="sxs-lookup"><span data-stu-id="274ac-132">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>
 
    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="274ac-133">Belirli Eğitmenler kullanmayı otomatik ML isteyin.</span><span class="sxs-lookup"><span data-stu-id="274ac-133">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="274ac-134">Varsayılan listesini Eğitmenler en iyi duruma getirme görev incelediniz.</span><span class="sxs-lookup"><span data-stu-id="274ac-134">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="274ac-135">Bu liste her deneme için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="274ac-135">This list can be modified for each experiment.</span></span> <span data-ttu-id="274ac-136">Örneğin, veri kümenize yavaş çalışmasına Eğitmenler listeden kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="274ac-136">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="274ac-137">Belirli bir eğitmen çağrıda en iyi duruma getirme `experimentSettings.Trainers.Clear()`, ardından kullanmak istediğiniz Eğitmeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="274ac-137">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="274ac-138">ML görev başına desteklenen Eğitmenler listesini aşağıdaki karşılık gelen bağlantıda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="274ac-138">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>
* [<span data-ttu-id="274ac-139">İkili sınıflandırma algoritmaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="274ac-139">Supported Binary Classification Algorithms</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.binaryclassificationtrainer?view=automl-dotnet)
* [<span data-ttu-id="274ac-140">Sınıflı sınıflandırma algoritmaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="274ac-140">Supported Multiclass Classification Algorithms</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.multiclassclassificationtrainer?view=automl-dotnet)
* [<span data-ttu-id="274ac-141">Desteklenen regresyon algoritmaları</span><span class="sxs-lookup"><span data-stu-id="274ac-141">Supported Regression Algorithms</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.regressiontrainer?view=automl-dotnet)

## <a name="optimizing-metric"></a><span data-ttu-id="274ac-142">Ölçüm en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="274ac-142">Optimizing metric</span></span>

<span data-ttu-id="274ac-143">Yukarıdaki örnekte gösterildiği gibi en iyi duruma getirme ölçüm modeli eğitimi sırasında en iyi duruma getirilmesi ölçüm belirler.</span><span class="sxs-lookup"><span data-stu-id="274ac-143">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="274ac-144">Seçebileceğiniz en iyi duruma getirme ölçüm seçtiğiniz görev türüne göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="274ac-144">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="274ac-145">Ölçümlerin bir listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="274ac-145">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="274ac-146">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="274ac-146">Binary Classification</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.binaryclassificationmetric?view=automl-dotnet) | [<span data-ttu-id="274ac-147">Sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="274ac-147">Multiclass Classification</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.multiclassclassificationmetric?view=automl-dotnet) | [<span data-ttu-id="274ac-148">Regresyon</span><span class="sxs-lookup"><span data-stu-id="274ac-148">Regression</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.regressionmetric?view=automl-dotnet)
|-- |-- |--
|<span data-ttu-id="274ac-149">Doğruluğu</span><span class="sxs-lookup"><span data-stu-id="274ac-149">Accuracy</span></span>| <span data-ttu-id="274ac-150">LogLoss</span><span class="sxs-lookup"><span data-stu-id="274ac-150">LogLoss</span></span> | <span data-ttu-id="274ac-151">RSquared</span><span class="sxs-lookup"><span data-stu-id="274ac-151">RSquared</span></span>
|<span data-ttu-id="274ac-152">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="274ac-152">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="274ac-153">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="274ac-153">LogLossReduction</span></span> | <span data-ttu-id="274ac-154">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="274ac-154">MeanAbsoluteError</span></span>
|<span data-ttu-id="274ac-155">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="274ac-155">AreaUnderRocCurve</span></span> | <span data-ttu-id="274ac-156">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="274ac-156">MacroAccuracy</span></span> | <span data-ttu-id="274ac-157">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="274ac-157">MeanSquaredError</span></span>
|<span data-ttu-id="274ac-158">F1Score</span><span class="sxs-lookup"><span data-stu-id="274ac-158">F1Score</span></span> | <span data-ttu-id="274ac-159">MicroAccuracy</span><span class="sxs-lookup"><span data-stu-id="274ac-159">MicroAccuracy</span></span> | <span data-ttu-id="274ac-160">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="274ac-160">RootMeanSquaredError</span></span>
|<span data-ttu-id="274ac-161">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="274ac-161">NegativePrecision</span></span> | <span data-ttu-id="274ac-162">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="274ac-162">TopKAccuracy</span></span>
|<span data-ttu-id="274ac-163">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="274ac-163">NegativeRecall</span></span> |
|<span data-ttu-id="274ac-164">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="274ac-164">PositivePrecision</span></span>
|<span data-ttu-id="274ac-165">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="274ac-165">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="274ac-166">Veri ön işleme ve özellik kazandırma sayesinde</span><span class="sxs-lookup"><span data-stu-id="274ac-166">Data pre-processing and featurization</span></span>

<span data-ttu-id="274ac-167">Varsayılan olarak veri ön işleme olur ve aşağıdaki adımları sizin için otomatik olarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="274ac-167">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="274ac-168">Hiçbir yararlı bilgiler özelliklerle bırak</span><span class="sxs-lookup"><span data-stu-id="274ac-168">Drop features with no useful information</span></span>

    <span data-ttu-id="274ac-169">Hiçbir yararlı bilgiler özellikleriyle, eğitim ve doğrulama kümesinden bırakın.</span><span class="sxs-lookup"><span data-stu-id="274ac-169">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="274ac-170">Bu, eksik, tüm değerlerin tüm satırlar boyunca veya son derece yüksek kardinalite (örneğin, karmaları kimlikleri veya GUID'leri) ile aynı değere sahip özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="274ac-170">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="274ac-171">İmputation ve eksik değer göstergesi</span><span class="sxs-lookup"><span data-stu-id="274ac-171">Missing value indication and imputation</span></span>

    <span data-ttu-id="274ac-172">Veri türü için varsayılan değer ile eksik değer hücrelere doldurun.</span><span class="sxs-lookup"><span data-stu-id="274ac-172">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="274ac-173">Göstergesi özelliklerle aynı yuva sayısı giriş sütun olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="274ac-173">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="274ac-174">Eklenen gösterge özellikleri değer `1` giriş sütunundaki değeri eksik olup olmadığını ve `0` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="274ac-174">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="274ac-175">Ek özellikler oluşturma</span><span class="sxs-lookup"><span data-stu-id="274ac-175">Generate additional features</span></span>
    
    <span data-ttu-id="274ac-176">Metin özellikleri: Unigrams ve üç karakter gram kullanarak word paketi özellik.</span><span class="sxs-lookup"><span data-stu-id="274ac-176">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>
    
    <span data-ttu-id="274ac-177">Kategorik özellikleri: Bir sık erişimli düşük önem düzeyi özellikleri için kodlama ve bir-sık erişimli-hash kodlama için yüksek kardinalite kategorik özellikleri.</span><span class="sxs-lookup"><span data-stu-id="274ac-177">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="274ac-178">Dönüşümler ve kodlamaları</span><span class="sxs-lookup"><span data-stu-id="274ac-178">Transformations and encodings</span></span>

    <span data-ttu-id="274ac-179">Metin özellikleri kategorik özelliklerini dönüştürülmüş çok az benzersiz değerlere sahip.</span><span class="sxs-lookup"><span data-stu-id="274ac-179">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="274ac-180">Bağlı olarak kardinalite kategorik özelliklerinin kodlama bir seyrek veya sık erişimli bir karma kodlama gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="274ac-180">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="274ac-181">Sonlandırma kriteri</span><span class="sxs-lookup"><span data-stu-id="274ac-181">Exit criteria</span></span>

<span data-ttu-id="274ac-182">Görevinizi tamamlamak için ölçütleri tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="274ac-182">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="274ac-183">Bir süre boyunca - sonra çıkış kullanarak `MaxExperimentTimeInSeconds` deneme ayarlarınızda ne kadar süreyle bir görevi çalıştırmaya devam etmeli saniyeler içinde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="274ac-183">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="274ac-184">Çıkış bir iptal belirteci - tamamlanmak üzere zamanlanan önce görevi iptal olanak sağlayan bir iptal belirteci kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="274ac-184">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="274ac-185">Bir deneme oluşturma</span><span class="sxs-lookup"><span data-stu-id="274ac-185">Create an experiment</span></span>

<span data-ttu-id="274ac-186">Deneme ayarlarını yapılandırdıktan sonra bir deneme oluşturmak hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="274ac-186">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="274ac-187">Denemeyi çalıştırma</span><span class="sxs-lookup"><span data-stu-id="274ac-187">Run the experiment</span></span>

<span data-ttu-id="274ac-188">Ön işleme, öğrenme algoritması seçme ve hiper parametre ayarı deneme Tetikleyicileri veri çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="274ac-188">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="274ac-189">Özellik kazandırma sayesinde, öğrenme algoritmaları ve kadar hiperparametreleri bileşimi oluşturmak AutoML devam `MaxExperimentTimeInSeconds` ulaşıldığında veya denemeyi sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="274ac-189">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="274ac-190">Diğer aşırı yüklemeler için keşfetmek `Execute()` doğrulama verileri, sütun amaçlı ya da prefeaturizers gösteren sütun bilgileri geçirmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="274ac-190">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="274ac-191">Eğitim modları</span><span class="sxs-lookup"><span data-stu-id="274ac-191">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="274ac-192">Eğitim veri kümesi</span><span class="sxs-lookup"><span data-stu-id="274ac-192">Training dataset</span></span>

<span data-ttu-id="274ac-193">AutoML sağlar, aşırı yüklenmiş bir deneme yürütme yöntemi, eğitim verilerini sağlamanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="274ac-193">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="274ac-194">Dahili olarak, otomatik ML veri train-validate bölmelerini böler.</span><span class="sxs-lookup"><span data-stu-id="274ac-194">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);   
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="274ac-195">Özel doğrulama veri kümesi</span><span class="sxs-lookup"><span data-stu-id="274ac-195">Custom validation dataset</span></span>

<span data-ttu-id="274ac-196">Genellikle zaman serisi verileri ile olduğu gibi rastgele bölünmüş kabul edilebilir değilse, özel doğrulama veri kümesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="274ac-196">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="274ac-197">Kendi doğrulama veri kümesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="274ac-197">You can specify your own validation dataset.</span></span> <span data-ttu-id="274ac-198">Model doğrulama veri kümesi bir veya daha fazla rastgele veri kümeleri yerine belirtilen karşı değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="274ac-198">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);   
```

## <a name="explore-model-metrics"></a><span data-ttu-id="274ac-199">Model ölçümleri keşfedin</span><span class="sxs-lookup"><span data-stu-id="274ac-199">Explore model metrics</span></span>

<span data-ttu-id="274ac-200">ML denemesi her yinelemeden sonra bu görevle ilgili ölçümleri depolanır.</span><span class="sxs-lookup"><span data-stu-id="274ac-200">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="274ac-201">Örneğin, size en iyi çalıştırmadan doğrulama ölçümleri erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="274ac-201">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="274ac-202">ML görev başına kullanılabilen tüm ölçümler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="274ac-202">The following are all the available metrics per ML task:</span></span>
* [<span data-ttu-id="274ac-203">İkili sınıflandırma ölçümleri</span><span class="sxs-lookup"><span data-stu-id="274ac-203">Binary classification metrics</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.binaryclassificationmetric?view=automl-dotnet
)
* [<span data-ttu-id="274ac-204">Sınıflı sınıflandırma ölçümleri</span><span class="sxs-lookup"><span data-stu-id="274ac-204">Multiclass classification metrics</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.multiclassclassificationmetric?view=automl-dotnet
)
* [<span data-ttu-id="274ac-205">Regresyon ölçümleri</span><span class="sxs-lookup"><span data-stu-id="274ac-205">Regression metrics</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl.regressionmetric?view=automl-dotnet
)

## <a name="see-also"></a><span data-ttu-id="274ac-206">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="274ac-206">See also</span></span>

<span data-ttu-id="274ac-207">Tam kod örnekleri ve daha fazla bilgi için ziyaret [machinelearning/dotnet-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="274ac-207">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
