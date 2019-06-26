---
title: Çapraz doğrulama kullanarak makine öğrenme modeli eğitme
description: Çapraz doğrulama ML.NET daha güçlü makine öğrenimi modelleri oluşturmak için kullanmayı öğrenin. Çapraz doğrulama, eğitim ve veriler çeşitli bölümlere ayırır ve bu bölümler birden çok algoritmalarına eğitir model değerlendirme teknik ' dir.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: c68c2b61054f59f03b4743ec30a694e94086ebab
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397654"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="1adf7-104">Çapraz doğrulama kullanarak makine öğrenme modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="1adf7-104">Train a machine learning model using cross validation</span></span>

<span data-ttu-id="1adf7-105">Çapraz doğrulama ML.NET daha güçlü makine öğrenimi modelleri eğitmek için kullanmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="1adf7-105">Learn how to use cross validation to train more robust machine learning models in ML.NET.</span></span> 

<span data-ttu-id="1adf7-106">Çapraz doğrulama, eğitim ve veriler çeşitli bölümlere ayırır ve bu bölümler birden çok algoritmalarına eğitir model değerlendirme teknik ' dir.</span><span class="sxs-lookup"><span data-stu-id="1adf7-106">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="1adf7-107">Bu teknik, eğitim işlem verileri tutarak modelinin sağlamlık artırır.</span><span class="sxs-lookup"><span data-stu-id="1adf7-107">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="1adf7-108">Görünmeyen gözlemler performans iyileştirme yanı sıra veri kısıtlı ortamlarında, daha küçük bir veri kümesiyle eğitim modelleri için etkili bir aracı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1adf7-108">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="1adf7-109">Veri ve veri modeli</span><span class="sxs-lookup"><span data-stu-id="1adf7-109">The data and data model</span></span>

<span data-ttu-id="1adf7-110">Belirtilen bir dosyadan veri, aşağıdaki biçime sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1adf7-110">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="1adf7-111">Verileri gibi bir sınıf tarafından modellenebilir `HousingData`:</span><span class="sxs-lookup"><span data-stu-id="1adf7-111">The data can be modeled by a class like `HousingData`:</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }
 
    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

<span data-ttu-id="1adf7-112">İçinde verilerin bir [ `IDataView` ](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="1adf7-112">Load the data in into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="1adf7-113">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="1adf7-113">Prepare the data</span></span>

<span data-ttu-id="1adf7-114">Veri machine learning modeli oluşturmak üzere kullanmadan önce önceden işler.</span><span class="sxs-lookup"><span data-stu-id="1adf7-114">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="1adf7-115">Bu örnekte `Size` ve `HistoricalPrices` sütunları adlı yeni bir sütun için çıkış tek özellik vektör içine birleştirilir `Features` kullanarak [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1adf7-115">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="1adf7-116">ML.NET algoritmalarda beklenen biçime veri alma yanı sıra sütunlarını ardışık düzende sonraki işlemleri her ayrı sütun yerine birleştirilmiş sütun için bir kez işlemi uygulayarak en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="1adf7-116">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span> 

<span data-ttu-id="1adf7-117">Sütunları tek bir vektörü birleştirilir sonra [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) uygulanan `Features` almak için sütun `Size` ve `HistoricalPrices` aynı 0-1 aralığında.</span><span class="sxs-lookup"><span data-stu-id="1adf7-117">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span> 

```csharp
// Define data prep estimator
IEstimator<ITransformer> dataPrepEstimator = 
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Transform data
IDataView transformedData = dataPrepTransformer.Transform(data);
```

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="1adf7-118">Çapraz doğrulama modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="1adf7-118">Train model with cross validation</span></span>

<span data-ttu-id="1adf7-119">Önceden işlenmiş hesaplandıktan sonra modeli eğitmek için zaman gelir.</span><span class="sxs-lookup"><span data-stu-id="1adf7-119">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="1adf7-120">İlk olarak, en yakın olan makine öğrenme gerçekleştirilecek görevi uygun algoritmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="1adf7-120">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="1adf7-121">Tahmin edilen değer sayısal sürekli bir değeri olduğundan, regresyon görevdir.</span><span class="sxs-lookup"><span data-stu-id="1adf7-121">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="1adf7-122">ML.NET tarafından uygulanan regresyon algoritmalarından biri olan [ `StochasticDualCoordinateAscentCoordinator` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algoritması.</span><span class="sxs-lookup"><span data-stu-id="1adf7-122">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="1adf7-123">Çapraz doğrulama kullanımı modeli eğitmek için [ `CrossValidate` ](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1adf7-123">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span> 

> [!NOTE]
> <span data-ttu-id="1adf7-124">Bu örnek bir doğrusal regresyon modeli kullansa da, CrossValidate Anomali algılama hariç ML.NET görevlerinde öğrenme tüm makine için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1adf7-124">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="1adf7-125">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) aşağıdaki işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="1adf7-125">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="1adf7-126">Belirli bölümleri içinde belirtilen değere eşit sayıda veriyi bölümler `numberOfFolds` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1adf7-126">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="1adf7-127">Her bölüm sonucu bir [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) nesne.</span><span class="sxs-lookup"><span data-stu-id="1adf7-127">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="1adf7-128">Belirtilen makine öğrenimi algoritma estimator eğitim veri kümesi üzerinde kullanarak bölümlerin her bir modeli eğitilir.</span><span class="sxs-lookup"><span data-stu-id="1adf7-128">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="1adf7-129">Her modelin performans kullanarak değerlendirilir [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) sınama veri kümesi üzerinde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1adf7-129">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span> 
1. <span data-ttu-id="1adf7-130">Model, ölçümlerle birlikte modellerinin her biri için döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1adf7-130">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="1adf7-131">Sonuç depolanan `cvResults` koleksiyonudur [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1adf7-131">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objects.</span></span> <span data-ttu-id="1adf7-132">Bu nesne eğitilen model yanı sıra erişilebilir her iki formu olan ölçümler içerir [ `Model` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) ve [ `Metrics` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) özellikleri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="1adf7-132">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) properties respectively.</span></span> <span data-ttu-id="1adf7-133">Bu örnekte `Model` özelliği türüdür [ `ITransformer` ](xref:Microsoft.ML.ITransformer) ve `Metrics` özelliği türüdür [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics).</span><span class="sxs-lookup"><span data-stu-id="1adf7-133">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span> 

## <a name="evaluate-the-model"></a><span data-ttu-id="1adf7-134">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1adf7-134">Evaluate the model</span></span>

<span data-ttu-id="1adf7-135">Ölçümleri farklı eğitilen modelleri için üzerinden erişilebilir `Metrics` kişinin özelliği [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesne.</span><span class="sxs-lookup"><span data-stu-id="1adf7-135">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="1adf7-136">Bu durumda, [R karesi alınmış ölçüm](https://en.wikipedia.org/wiki/Coefficient_of_determination) erişilen ve değişkeninde depolanan `rSquared`.</span><span class="sxs-lookup"><span data-stu-id="1adf7-136">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span> 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="1adf7-137">İçeriğini incelemek, `rSquared` değişken çıktısı beş değerleri 0-1'den daha yakın yerlerde 1 arasında en iyi anlamına gelir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1adf7-137">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span> <span data-ttu-id="1adf7-138">R kare seçme gibi ölçümleri kötü gerçekleştirmek için en iyi modellerinden kullanma.</span><span class="sxs-lookup"><span data-stu-id="1adf7-138">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="1adf7-139">Ardından, tahminlerde veya ile ek işlemleri gerçekleştirmek için en iyi modeli seçin.</span><span class="sxs-lookup"><span data-stu-id="1adf7-139">Then, select the top model to make predictions or perform additional operations with.</span></span>

```csharp
// Select all models
ITransformer[] models =
    cvResults
        .OrderByDescending(fold => fold.Metrics.RSquared)
        .Select(fold => fold.Model)
        .ToArray();

// Get Top Model
ITransformer topModel = models[0];
```
