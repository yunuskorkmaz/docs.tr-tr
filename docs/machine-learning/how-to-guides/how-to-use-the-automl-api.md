---
title: ML.NET otomatik ML API 'sini kullanma
description: ML.NET otomatikleştirilen ML API 'SI, model oluşturma işlemini otomatikleştirir ve dağıtım için hazırlamış bir model oluşturur. Otomatik makine öğrenimi görevlerini yapılandırmak için kullanabileceğiniz seçenekleri öğrenin.
ms.date: 04/24/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 02e4203b0d9f388c7bd7133f3cd4e97cc60cff14
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929377"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="b19bd-104">ML.NET otomatik makine öğrenimi API 'sini kullanma</span><span class="sxs-lookup"><span data-stu-id="b19bd-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="b19bd-105">Otomatik makine öğrenimi (Otomatikml), verileri makineye öğrenmeyi uygulama işlemini otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="b19bd-106">Bir veri kümesi verildiğinde, en iyi modeli seçmek için farklı veri özelliklerini, makine öğrenimi algoritmalarını ve hiper parametreleri yinelemek üzere bir **oto ml denemesi** çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b19bd-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="b19bd-107">Bu konu, şu anda önizleme aşamasında olan ML.NET için otomatik makine öğrenimi API 'sine başvurur.</span><span class="sxs-lookup"><span data-stu-id="b19bd-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="b19bd-108">Malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="b19bd-109">Veri yükleme</span><span class="sxs-lookup"><span data-stu-id="b19bd-109">Load data</span></span>

<span data-ttu-id="b19bd-110">Otomatik makine öğrenimi, bir veri kümesinin bir [ıdataview](xref:Microsoft.ML.IDataView)içine yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="b19bd-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="b19bd-111">Veriler sekmeyle ayrılmış değer (TSV) dosyaları ve virgülle ayrılmış değer (CSV) dosyaları biçiminde olabilir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="b19bd-112">Örnek:</span><span class="sxs-lookup"><span data-stu-id="b19bd-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="b19bd-113">Machine Learning görev türünü seçin</span><span class="sxs-lookup"><span data-stu-id="b19bd-113">Select the machine learning task type</span></span>
<span data-ttu-id="b19bd-114">Bir deneme oluşturmadan önce, çözmek istediğiniz makine öğrenimi sorunu türünü saptayın.</span><span class="sxs-lookup"><span data-stu-id="b19bd-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="b19bd-115">Otomatik makine öğrenimi aşağıdaki ML görevlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="b19bd-115">Automated machine learning supports the following ML tasks:</span></span>

* <span data-ttu-id="b19bd-116">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="b19bd-116">Binary Classification</span></span>
* <span data-ttu-id="b19bd-117">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="b19bd-117">Multiclass Classification</span></span>
* <span data-ttu-id="b19bd-118">Regresyon</span><span class="sxs-lookup"><span data-stu-id="b19bd-118">Regression</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="b19bd-119">Deneme ayarları oluşturma</span><span class="sxs-lookup"><span data-stu-id="b19bd-119">Create experiment settings</span></span>

<span data-ttu-id="b19bd-120">Belirlenen ML görev türü için deneme ayarları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b19bd-120">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="b19bd-121">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="b19bd-121">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="b19bd-122">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="b19bd-122">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="b19bd-123">Regresyon</span><span class="sxs-lookup"><span data-stu-id="b19bd-123">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="b19bd-124">Deneme ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b19bd-124">Configure experiment settings</span></span>

<span data-ttu-id="b19bd-125">Denemeleri, yüksek oranda yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-125">Experiments are highly configurable.</span></span> <span data-ttu-id="b19bd-126">Yapılandırma ayarlarının tam listesi için bkz. [oto ml API belgeleri](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="b19bd-126">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) for a full list of configuration settings.</span></span>

<span data-ttu-id="b19bd-127">Bazı örnekler:</span><span class="sxs-lookup"><span data-stu-id="b19bd-127">Some examples include:</span></span>

1. <span data-ttu-id="b19bd-128">Denemenin çalışmasına izin verilen en uzun süreyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="b19bd-128">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="b19bd-129">Tamamlanmak üzere zamanlanmadan önce denemeyi iptal etmek için bir iptal belirteci kullanın.</span><span class="sxs-lookup"><span data-stu-id="b19bd-129">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="b19bd-130">Farklı bir iyileştirmeli ölçüm belirtin.</span><span class="sxs-lookup"><span data-stu-id="b19bd-130">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="b19bd-131">Bu `CacheDirectory` ayar, otomatik ml görevi sırasında eğitilen tüm modellerin kaydedileceği dizine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-131">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="b19bd-132">`CacheDirectory` Null olarak ayarlanırsa, modeller diske yazılmak yerine bellekte tutulur.</span><span class="sxs-lookup"><span data-stu-id="b19bd-132">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>
 
    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="b19bd-133">Otomatikleştirilmiş ML 'nin belirli eğitimleri kullanmamasını söyleyin.</span><span class="sxs-lookup"><span data-stu-id="b19bd-133">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="b19bd-134">En iyileştirmek için, görev başına araştırılan varsayılan bir liste.</span><span class="sxs-lookup"><span data-stu-id="b19bd-134">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="b19bd-135">Bu liste, her deneme için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-135">This list can be modified for each experiment.</span></span> <span data-ttu-id="b19bd-136">Örneğin, veri kümeniz üzerinde yavaş çalışan traıners listeden kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-136">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="b19bd-137">Tek bir belirli bir seyahat çağrısını `experimentSettings.Trainers.Clear()`iyileştirmek için, kullanmak istediğiniz eğitmen 'ı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b19bd-137">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="b19bd-138">ML başına desteklenen aers görevleri listesi aşağıdaki ilgili bağlantıda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="b19bd-138">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>

* [<span data-ttu-id="b19bd-139">Desteklenen Ikili sınıflandırma algoritmaları</span><span class="sxs-lookup"><span data-stu-id="b19bd-139">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="b19bd-140">Desteklenen birden çok Lass sınıflandırma algoritması</span><span class="sxs-lookup"><span data-stu-id="b19bd-140">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="b19bd-141">Desteklenen Regresyon algoritmaları</span><span class="sxs-lookup"><span data-stu-id="b19bd-141">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="b19bd-142">Ölçümü iyileştirme</span><span class="sxs-lookup"><span data-stu-id="b19bd-142">Optimizing metric</span></span>

<span data-ttu-id="b19bd-143">Yukarıdaki örnekte gösterildiği gibi en iyileştirme ölçümü, model eğitimi sırasında en iyi duruma getirilecek ölçümü belirler.</span><span class="sxs-lookup"><span data-stu-id="b19bd-143">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="b19bd-144">Seçebileceğiniz ölçüm en iyi duruma getirme, seçtiğiniz görev türüne göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-144">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="b19bd-145">Kullanılabilir ölçümlerin listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-145">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="b19bd-146">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="b19bd-146">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="b19bd-147">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="b19bd-147">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="b19bd-148">Regresyon</span><span class="sxs-lookup"><span data-stu-id="b19bd-148">Regression</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="b19bd-149">veritabanınızın</span><span class="sxs-lookup"><span data-stu-id="b19bd-149">Accuracy</span></span>| <span data-ttu-id="b19bd-150">Logkaybetme</span><span class="sxs-lookup"><span data-stu-id="b19bd-150">LogLoss</span></span> | <span data-ttu-id="b19bd-151">RKARE</span><span class="sxs-lookup"><span data-stu-id="b19bd-151">RSquared</span></span>
|<span data-ttu-id="b19bd-152">Areaunderperrecallcurve</span><span class="sxs-lookup"><span data-stu-id="b19bd-152">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="b19bd-153">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="b19bd-153">LogLossReduction</span></span> | <span data-ttu-id="b19bd-154">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="b19bd-154">MeanAbsoluteError</span></span>
|<span data-ttu-id="b19bd-155">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="b19bd-155">AreaUnderRocCurve</span></span> | <span data-ttu-id="b19bd-156">Makro doğruluğu</span><span class="sxs-lookup"><span data-stu-id="b19bd-156">MacroAccuracy</span></span> | <span data-ttu-id="b19bd-157">Ortalamasquare</span><span class="sxs-lookup"><span data-stu-id="b19bd-157">MeanSquaredError</span></span>
|<span data-ttu-id="b19bd-158">F1Score</span><span class="sxs-lookup"><span data-stu-id="b19bd-158">F1Score</span></span> | <span data-ttu-id="b19bd-159">Mikro doğruluk</span><span class="sxs-lookup"><span data-stu-id="b19bd-159">MicroAccuracy</span></span> | <span data-ttu-id="b19bd-160">Rootortalamasquarebir</span><span class="sxs-lookup"><span data-stu-id="b19bd-160">RootMeanSquaredError</span></span>
|<span data-ttu-id="b19bd-161">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="b19bd-161">NegativePrecision</span></span> | <span data-ttu-id="b19bd-162">Topkdoğruluk</span><span class="sxs-lookup"><span data-stu-id="b19bd-162">TopKAccuracy</span></span>
|<span data-ttu-id="b19bd-163">Negatiftiverecall</span><span class="sxs-lookup"><span data-stu-id="b19bd-163">NegativeRecall</span></span> |
|<span data-ttu-id="b19bd-164">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="b19bd-164">PositivePrecision</span></span>
|<span data-ttu-id="b19bd-165">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="b19bd-165">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="b19bd-166">Veri ön işleme ve özellik kazandırma sayesinde</span><span class="sxs-lookup"><span data-stu-id="b19bd-166">Data pre-processing and featurization</span></span>

<span data-ttu-id="b19bd-167">Verilerin ön işlemesi varsayılan olarak gerçekleşir ve aşağıdaki adımlar sizin için otomatik olarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="b19bd-167">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="b19bd-168">Yararlı bilgiler olmadan bırakma özellikleri</span><span class="sxs-lookup"><span data-stu-id="b19bd-168">Drop features with no useful information</span></span>

    <span data-ttu-id="b19bd-169">Hiçbir yararlı bilgiler özellikleriyle, eğitim ve doğrulama kümesinden bırakın.</span><span class="sxs-lookup"><span data-stu-id="b19bd-169">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="b19bd-170">Bu, eksik, tüm değerlerin tüm satırlar boyunca veya son derece yüksek kardinalite (örneğin, karmaları kimlikleri veya GUID'leri) ile aynı değere sahip özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-170">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="b19bd-171">Eksik değer gösterimi ve imputation</span><span class="sxs-lookup"><span data-stu-id="b19bd-171">Missing value indication and imputation</span></span>

    <span data-ttu-id="b19bd-172">Eksik değer hücrelerini, veri türü için varsayılan değerle doldur.</span><span class="sxs-lookup"><span data-stu-id="b19bd-172">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="b19bd-173">Giriş sütunuyla aynı sayıda yuva içeren gösterge özellikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b19bd-173">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="b19bd-174">Eklenen gösterge özelliklerinin `1` değeri, giriş sütunundaki değerin eksik olması ve `0` Aksi durumda.</span><span class="sxs-lookup"><span data-stu-id="b19bd-174">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="b19bd-175">Ek özellikler oluşturma</span><span class="sxs-lookup"><span data-stu-id="b19bd-175">Generate additional features</span></span>
    
    <span data-ttu-id="b19bd-176">Metin özellikleri için: Unigram ve üçlü karakter-gram kullanan sözcük paketi özellikleri.</span><span class="sxs-lookup"><span data-stu-id="b19bd-176">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>
    
    <span data-ttu-id="b19bd-177">Kategorik özellikler için: Düşük kardinalite özellikleri için tek yönlü kodlama ve yüksek kardinalite kategorik özellikleri için bir adet etkin karma kodlama.</span><span class="sxs-lookup"><span data-stu-id="b19bd-177">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="b19bd-178">Dönüşümler ve kodlamaları</span><span class="sxs-lookup"><span data-stu-id="b19bd-178">Transformations and encodings</span></span>

    <span data-ttu-id="b19bd-179">Kategorik özelliklere dönüştürülen çok az benzersiz değerler içeren metin özellikleri.</span><span class="sxs-lookup"><span data-stu-id="b19bd-179">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="b19bd-180">Kategorik özelliklerin kardinalitesine bağlı olarak, tek başına kodlama veya tek yönlü karma kodlama gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="b19bd-180">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="b19bd-181">Çıkış kriterleri</span><span class="sxs-lookup"><span data-stu-id="b19bd-181">Exit criteria</span></span>

<span data-ttu-id="b19bd-182">Görevinizi tamamlamaya yönelik ölçütleri tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="b19bd-182">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="b19bd-183">Deneme ayarlarınızda bir süre `MaxExperimentTimeInSeconds` geçtikten sonra çık bir görevin çalışmaya devam etmesi için saniye cinsinden süreyi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b19bd-183">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="b19bd-184">İptal belirtecinden çıkma-işlemi tamamlamak için zamanlanmadan önce, görevi iptal etmenizi sağlayan bir iptal belirteci kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b19bd-184">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="b19bd-185">Deneme oluşturma</span><span class="sxs-lookup"><span data-stu-id="b19bd-185">Create an experiment</span></span>

<span data-ttu-id="b19bd-186">Deneme ayarlarını yapılandırdıktan sonra, denemeyi oluşturmaya hazırlanın.</span><span class="sxs-lookup"><span data-stu-id="b19bd-186">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="b19bd-187">Denemeyi çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b19bd-187">Run the experiment</span></span>

<span data-ttu-id="b19bd-188">Denemeyi çalıştırmak, verileri önceden işleme, öğrenme algoritması seçimi ve hiper parametre ayarlamayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="b19bd-188">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="b19bd-189">Oto, ulaşılıncaya veya deneme sonlandırılana kadar `MaxExperimentTimeInSeconds` doğru şekilde, öğrenme algoritmalarının ve hiper parametrelerin birleşimlerini oluşturmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-189">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="b19bd-190">Doğrulama verilerini, sütun `Execute()` amacını veya ön ek türleyicileri belirten sütun bilgilerini geçirmek istiyorsanız için diğer aşırı yüklemeleri keşfet.</span><span class="sxs-lookup"><span data-stu-id="b19bd-190">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="b19bd-191">Eğitim modları</span><span class="sxs-lookup"><span data-stu-id="b19bd-191">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="b19bd-192">Eğitim veri kümesi</span><span class="sxs-lookup"><span data-stu-id="b19bd-192">Training dataset</span></span>

<span data-ttu-id="b19bd-193">Oto ml, eğitim verileri sağlamanıza olanak tanıyan aşırı yüklenmiş bir deneme yürütme yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b19bd-193">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="b19bd-194">Dahili olarak, otomatik ML verileri eğitme-doğrulama bölmelere ayırır.</span><span class="sxs-lookup"><span data-stu-id="b19bd-194">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);   
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="b19bd-195">Özel doğrulama veri kümesi</span><span class="sxs-lookup"><span data-stu-id="b19bd-195">Custom validation dataset</span></span>

<span data-ttu-id="b19bd-196">Genellikle zaman serisi verilerinde olduğu gibi rastgele bölme kabul edilebilir değilse, özel doğrulama veri kümesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b19bd-196">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="b19bd-197">Kendi doğrulama veri kümesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b19bd-197">You can specify your own validation dataset.</span></span> <span data-ttu-id="b19bd-198">Model, bir veya daha fazla rastgele veri kümesi yerine belirtilen doğrulama veri kümesine göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b19bd-198">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);   
```

## <a name="explore-model-metrics"></a><span data-ttu-id="b19bd-199">Model ölçümleri keşfedin</span><span class="sxs-lookup"><span data-stu-id="b19bd-199">Explore model metrics</span></span>

<span data-ttu-id="b19bd-200">Her bir ML denemesinin yinelemesinden sonra, bu görevle ilgili ölçümler depolanır.</span><span class="sxs-lookup"><span data-stu-id="b19bd-200">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="b19bd-201">Örneğin, en iyi çalıştırmasından doğrulama ölçümlerine erişebiliriz:</span><span class="sxs-lookup"><span data-stu-id="b19bd-201">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="b19bd-202">Her ML görevi için kullanılabilir ölçümler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b19bd-202">The following are all the available metrics per ML task:</span></span>

* [<span data-ttu-id="b19bd-203">İkili sınıflandırma ölçümleri</span><span class="sxs-lookup"><span data-stu-id="b19bd-203">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="b19bd-204">Birden çok Lass sınıflandırma ölçümleri</span><span class="sxs-lookup"><span data-stu-id="b19bd-204">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="b19bd-205">Gerileme ölçümleri</span><span class="sxs-lookup"><span data-stu-id="b19bd-205">Regression metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="b19bd-206">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b19bd-206">See also</span></span>

<span data-ttu-id="b19bd-207">Tam kod örnekleri için [DotNet/machinöğrenim-Samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub deposunu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="b19bd-207">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
