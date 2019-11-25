---
title: ML.NET otomatik ML API 'sini kullanma
description: ML.NET otomatikleştirilen ML API 'SI, model oluşturma işlemini otomatikleştirir ve dağıtım için hazırlamış bir model oluşturur. Otomatik makine öğrenimi görevlerini yapılandırmak için kullanabileceğiniz seçenekleri öğrenin.
ms.date: 11/7/2019
ms.custom: mvc,how-to
ms.openlocfilehash: c1c18decc48bc1499aa55210becff305cdec4a53
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977123"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="6187f-104">ML.NET otomatik makine öğrenimi API 'sini kullanma</span><span class="sxs-lookup"><span data-stu-id="6187f-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="6187f-105">Otomatik makine öğrenimi (Otomatikml), verileri makineye öğrenmeyi uygulama işlemini otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="6187f-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="6187f-106">Bir veri kümesi verildiğinde, en iyi modeli seçmek için farklı veri özelliklerini, makine öğrenimi algoritmalarını ve hiper parametreleri yinelemek üzere bir **oto ml denemesi** çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6187f-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="6187f-107">Bu konu, şu anda önizleme aşamasında olan ML.NET için otomatik makine öğrenimi API 'sine başvurur.</span><span class="sxs-lookup"><span data-stu-id="6187f-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="6187f-108">Malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="6187f-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="6187f-109">Veri yükleme</span><span class="sxs-lookup"><span data-stu-id="6187f-109">Load data</span></span>

<span data-ttu-id="6187f-110">Otomatik makine öğrenimi, bir veri kümesinin bir [ıdataview](xref:Microsoft.ML.IDataView)içine yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="6187f-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="6187f-111">Veriler sekmeyle ayrılmış değer (TSV) dosyaları ve virgülle ayrılmış değer (CSV) dosyaları biçiminde olabilir.</span><span class="sxs-lookup"><span data-stu-id="6187f-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="6187f-112">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6187f-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="6187f-113">Machine Learning görev türünü seçin</span><span class="sxs-lookup"><span data-stu-id="6187f-113">Select the machine learning task type</span></span>

<span data-ttu-id="6187f-114">Bir deneme oluşturmadan önce, çözmek istediğiniz makine öğrenimi sorunu türünü saptayın.</span><span class="sxs-lookup"><span data-stu-id="6187f-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="6187f-115">Otomatik makine öğrenimi aşağıdaki ML görevlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="6187f-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="6187f-116">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="6187f-116">Binary Classification</span></span>
* <span data-ttu-id="6187f-117">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="6187f-117">Multiclass Classification</span></span>
* <span data-ttu-id="6187f-118">regresyon</span><span class="sxs-lookup"><span data-stu-id="6187f-118">Regression</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="6187f-119">Deneme ayarları oluşturma</span><span class="sxs-lookup"><span data-stu-id="6187f-119">Create experiment settings</span></span>

<span data-ttu-id="6187f-120">Belirlenen ML görev türü için deneme ayarları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="6187f-120">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="6187f-121">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="6187f-121">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="6187f-122">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="6187f-122">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="6187f-123">regresyon</span><span class="sxs-lookup"><span data-stu-id="6187f-123">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="6187f-124">Deneme ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6187f-124">Configure experiment settings</span></span>

<span data-ttu-id="6187f-125">Denemeleri, yüksek oranda yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6187f-125">Experiments are highly configurable.</span></span> <span data-ttu-id="6187f-126">Yapılandırma ayarlarının tam listesi için bkz. [oto ml API belgeleri](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) .</span><span class="sxs-lookup"><span data-stu-id="6187f-126">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) for a full list of configuration settings.</span></span>

<span data-ttu-id="6187f-127">Bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6187f-127">Some examples include:</span></span>

1. <span data-ttu-id="6187f-128">Denemenin çalışmasına izin verilen en uzun süreyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="6187f-128">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="6187f-129">Tamamlanmak üzere zamanlanmadan önce denemeyi iptal etmek için bir iptal belirteci kullanın.</span><span class="sxs-lookup"><span data-stu-id="6187f-129">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="6187f-130">Farklı bir iyileştirmeli ölçüm belirtin.</span><span class="sxs-lookup"><span data-stu-id="6187f-130">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="6187f-131">`CacheDirectory` ayarı, otomatik ml görevi sırasında eğitilen tüm modellerin kaydedileceği dizine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="6187f-131">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="6187f-132">`CacheDirectory` null olarak ayarlandıysa, modeller diske yazılmak yerine bellekte tutulur.</span><span class="sxs-lookup"><span data-stu-id="6187f-132">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="6187f-133">Otomatikleştirilmiş ML 'nin belirli eğitimleri kullanmamasını söyleyin.</span><span class="sxs-lookup"><span data-stu-id="6187f-133">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="6187f-134">En iyileştirmek için, görev başına araştırılan varsayılan bir liste.</span><span class="sxs-lookup"><span data-stu-id="6187f-134">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="6187f-135">Bu liste, her deneme için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6187f-135">This list can be modified for each experiment.</span></span> <span data-ttu-id="6187f-136">Örneğin, veri kümeniz üzerinde yavaş çalışan traıners listeden kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6187f-136">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="6187f-137">Tek bir belirli bir ariner çağrısında `experimentSettings.Trainers.Clear()` iyileştirmek için, kullanmak istediğiniz bir eğitmen ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6187f-137">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="6187f-138">ML başına desteklenen aers görevleri listesi aşağıdaki ilgili bağlantıda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="6187f-138">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="6187f-139">Desteklenen Ikili sınıflandırma algoritmaları</span><span class="sxs-lookup"><span data-stu-id="6187f-139">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="6187f-140">Desteklenen birden çok Lass sınıflandırma algoritması</span><span class="sxs-lookup"><span data-stu-id="6187f-140">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="6187f-141">Desteklenen Regresyon algoritmaları</span><span class="sxs-lookup"><span data-stu-id="6187f-141">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="6187f-142">Ölçümü iyileştirme</span><span class="sxs-lookup"><span data-stu-id="6187f-142">Optimizing metric</span></span>

<span data-ttu-id="6187f-143">Yukarıdaki örnekte gösterildiği gibi en iyileştirme ölçümü, model eğitimi sırasında en iyi duruma getirilecek ölçümü belirler.</span><span class="sxs-lookup"><span data-stu-id="6187f-143">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="6187f-144">Seçebileceğiniz ölçüm en iyi duruma getirme, seçtiğiniz görev türüne göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6187f-144">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="6187f-145">Kullanılabilir ölçümlerin listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6187f-145">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="6187f-146">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="6187f-146">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="6187f-147">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="6187f-147">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="6187f-148">Regresyon</span><span class="sxs-lookup"><span data-stu-id="6187f-148">Regression</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="6187f-149">Veritabanınızın</span><span class="sxs-lookup"><span data-stu-id="6187f-149">Accuracy</span></span>| <span data-ttu-id="6187f-150">Logkaybetme</span><span class="sxs-lookup"><span data-stu-id="6187f-150">LogLoss</span></span> | <span data-ttu-id="6187f-151">RKARE</span><span class="sxs-lookup"><span data-stu-id="6187f-151">RSquared</span></span>
|<span data-ttu-id="6187f-152">Areaunderperrecallcurve</span><span class="sxs-lookup"><span data-stu-id="6187f-152">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="6187f-153">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="6187f-153">LogLossReduction</span></span> | <span data-ttu-id="6187f-154">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="6187f-154">MeanAbsoluteError</span></span>
|<span data-ttu-id="6187f-155">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="6187f-155">AreaUnderRocCurve</span></span> | <span data-ttu-id="6187f-156">Makro doğruluğu</span><span class="sxs-lookup"><span data-stu-id="6187f-156">MacroAccuracy</span></span> | <span data-ttu-id="6187f-157">Ortalamasquare</span><span class="sxs-lookup"><span data-stu-id="6187f-157">MeanSquaredError</span></span>
|<span data-ttu-id="6187f-158">F1Score</span><span class="sxs-lookup"><span data-stu-id="6187f-158">F1Score</span></span> | <span data-ttu-id="6187f-159">Mikro doğruluk</span><span class="sxs-lookup"><span data-stu-id="6187f-159">MicroAccuracy</span></span> | <span data-ttu-id="6187f-160">Rootortalamasquarebir</span><span class="sxs-lookup"><span data-stu-id="6187f-160">RootMeanSquaredError</span></span>
|<span data-ttu-id="6187f-161">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="6187f-161">NegativePrecision</span></span> | <span data-ttu-id="6187f-162">Topkdoğruluk</span><span class="sxs-lookup"><span data-stu-id="6187f-162">TopKAccuracy</span></span>
|<span data-ttu-id="6187f-163">Negatiftiverecall</span><span class="sxs-lookup"><span data-stu-id="6187f-163">NegativeRecall</span></span> |
|<span data-ttu-id="6187f-164">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="6187f-164">PositivePrecision</span></span>
|<span data-ttu-id="6187f-165">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="6187f-165">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="6187f-166">Veri ön işleme ve korleştirme</span><span class="sxs-lookup"><span data-stu-id="6187f-166">Data pre-processing and featurization</span></span>

> [!NOTE]
> <span data-ttu-id="6187f-167">Özellik sütunu yalnızca <xref:System.Boolean>, <xref:System.Single> ve <xref:System.String> türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="6187f-167">The feature column only supported types of <xref:System.Boolean>, <xref:System.Single>, and <xref:System.String>.</span></span>

<span data-ttu-id="6187f-168">Verilerin ön işlemesi varsayılan olarak gerçekleşir ve aşağıdaki adımlar sizin için otomatik olarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="6187f-168">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="6187f-169">Yararlı bilgiler olmadan bırakma özellikleri</span><span class="sxs-lookup"><span data-stu-id="6187f-169">Drop features with no useful information</span></span>

    <span data-ttu-id="6187f-170">Eğitim ve doğrulama kümelerinden yararlı bilgiler olmadan özellikleri bırakın.</span><span class="sxs-lookup"><span data-stu-id="6187f-170">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="6187f-171">Bunlar tüm değerler eksik, tüm satırlarda aynı değere sahip olan veya son derece yüksek kardinalite (örn. karma, kimlik veya GUID) ile özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6187f-171">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="6187f-172">Eksik değer gösterimi ve imputation</span><span class="sxs-lookup"><span data-stu-id="6187f-172">Missing value indication and imputation</span></span>

    <span data-ttu-id="6187f-173">Eksik değer hücrelerini, veri türü için varsayılan değerle doldur.</span><span class="sxs-lookup"><span data-stu-id="6187f-173">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="6187f-174">Giriş sütunuyla aynı sayıda yuva içeren gösterge özellikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6187f-174">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="6187f-175">Giriş sütunundaki değer eksikse ve `0` yoksa, eklenen gösterge özelliklerinin değeri `1`.</span><span class="sxs-lookup"><span data-stu-id="6187f-175">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="6187f-176">Ek özellikler oluştur</span><span class="sxs-lookup"><span data-stu-id="6187f-176">Generate additional features</span></span>

    <span data-ttu-id="6187f-177">Metin özellikleri için: unigram ve üçlü karakter-gram kullanan sözcük paketi özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6187f-177">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>

    <span data-ttu-id="6187f-178">Kategorik özellikler için: düşük kardinalite özelliklerine yönelik tek yönlü bir kodlama ve yüksek kardinalite kategorik özellikleri için tek Hot-Hash kodlaması.</span><span class="sxs-lookup"><span data-stu-id="6187f-178">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="6187f-179">Dönüşümler ve kodlamalar</span><span class="sxs-lookup"><span data-stu-id="6187f-179">Transformations and encodings</span></span>

    <span data-ttu-id="6187f-180">Kategorik özelliklere dönüştürülen çok az benzersiz değerler içeren metin özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6187f-180">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="6187f-181">Kategorik özelliklerin kardinalitesine bağlı olarak, tek başına kodlama veya tek yönlü karma kodlama gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="6187f-181">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="6187f-182">Çıkış kriterleri</span><span class="sxs-lookup"><span data-stu-id="6187f-182">Exit criteria</span></span>

<span data-ttu-id="6187f-183">Görevinizi tamamlamaya yönelik ölçütleri tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="6187f-183">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="6187f-184">Süre dolduktan sonra çık-deneme ayarlarınızda `MaxExperimentTimeInSeconds` kullanarak, bir görevin çalışmaya devam etmesi gereken saniye cinsinden süreyi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6187f-184">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="6187f-185">İptal belirtecinden çıkma-işlemi tamamlamak için zamanlanmadan önce, görevi iptal etmenizi sağlayan bir iptal belirteci kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6187f-185">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="6187f-186">Deneme oluşturma</span><span class="sxs-lookup"><span data-stu-id="6187f-186">Create an experiment</span></span>

<span data-ttu-id="6187f-187">Deneme ayarlarını yapılandırdıktan sonra, denemeyi oluşturmaya hazırlanın.</span><span class="sxs-lookup"><span data-stu-id="6187f-187">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="6187f-188">Denemeyi çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6187f-188">Run the experiment</span></span>

<span data-ttu-id="6187f-189">Denemeyi çalıştırmak, verileri önceden işleme, öğrenme algoritması seçimi ve hiper parametre ayarlamayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="6187f-189">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="6187f-190">Oto, `MaxExperimentTimeInSeconds` ulaşılıncaya veya deneme sonlandırılana kadar, doğru şekilde, öğrenme algoritmalarının ve hiper parametrelerin birleşimlerini oluşturmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="6187f-190">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="6187f-191">Doğrulama verilerini geçirmek istiyorsanız, sütun amacını veya önceden yapılan türleyicileri belirten sütun bilgilerini `Execute()` için diğer aşırı yüklemeleri keşfet.</span><span class="sxs-lookup"><span data-stu-id="6187f-191">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="6187f-192">Eğitim modları</span><span class="sxs-lookup"><span data-stu-id="6187f-192">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="6187f-193">Eğitim veri kümesi</span><span class="sxs-lookup"><span data-stu-id="6187f-193">Training dataset</span></span>

<span data-ttu-id="6187f-194">Oto ml, eğitim verileri sağlamanıza olanak tanıyan aşırı yüklenmiş bir deneme yürütme yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6187f-194">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="6187f-195">Dahili olarak, otomatik ML verileri eğitme-doğrulama bölmelere ayırır.</span><span class="sxs-lookup"><span data-stu-id="6187f-195">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="6187f-196">Özel doğrulama veri kümesi</span><span class="sxs-lookup"><span data-stu-id="6187f-196">Custom validation dataset</span></span>

<span data-ttu-id="6187f-197">Genellikle zaman serisi verilerinde olduğu gibi rastgele bölme kabul edilebilir değilse, özel doğrulama veri kümesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6187f-197">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="6187f-198">Kendi doğrulama veri kümenizi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6187f-198">You can specify your own validation dataset.</span></span> <span data-ttu-id="6187f-199">Model, bir veya daha fazla rastgele veri kümesi yerine belirtilen doğrulama veri kümesine göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6187f-199">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a><span data-ttu-id="6187f-200">Model ölçümlerini keşfet</span><span class="sxs-lookup"><span data-stu-id="6187f-200">Explore model metrics</span></span>

<span data-ttu-id="6187f-201">Her bir ML denemesinin yinelemesinden sonra, bu görevle ilgili ölçümler depolanır.</span><span class="sxs-lookup"><span data-stu-id="6187f-201">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="6187f-202">Örneğin, en iyi çalıştırmasından doğrulama ölçümlerine erişebiliriz:</span><span class="sxs-lookup"><span data-stu-id="6187f-202">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="6187f-203">Her ML görevi için kullanılabilir ölçümler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6187f-203">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="6187f-204">İkili sınıflandırma ölçümleri</span><span class="sxs-lookup"><span data-stu-id="6187f-204">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="6187f-205">Birden çok Lass sınıflandırma ölçümleri</span><span class="sxs-lookup"><span data-stu-id="6187f-205">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="6187f-206">Gerileme ölçümleri</span><span class="sxs-lookup"><span data-stu-id="6187f-206">Regression metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="6187f-207">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6187f-207">See also</span></span>

<span data-ttu-id="6187f-208">Tam kod örnekleri için [DotNet/machinöğrenim-Samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub deposunu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="6187f-208">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
