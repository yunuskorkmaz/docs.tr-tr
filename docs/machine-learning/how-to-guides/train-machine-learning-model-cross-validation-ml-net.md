---
title: Çapraz doğrulama yı kullanarak bir makine öğrenme modeli eğitin
description: ML.NET daha sağlam makine öğrenimi modelleri oluşturmak için çapraz doğrulamayı nasıl kullanacağınızı öğrenin. Çapraz doğrulama, verileri birkaç bölüme bölen ve bu bölümlerde birden çok algoritma eğiten bir eğitim ve model değerlendirme tekniğidir.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: 87eae789478752423f3e682d4db6cead0391aa6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976923"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="1313c-104">Çapraz doğrulama yı kullanarak bir makine öğrenme modeli eğitin</span><span class="sxs-lookup"><span data-stu-id="1313c-104">Train a machine learning model using cross validation</span></span>

<span data-ttu-id="1313c-105">ML.NET daha sağlam makine öğrenimi modellerini eğitmek için çapraz doğrulamayı nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="1313c-105">Learn how to use cross validation to train more robust machine learning models in ML.NET.</span></span>

<span data-ttu-id="1313c-106">Çapraz doğrulama, verileri birkaç bölüme bölen ve bu bölümlerde birden çok algoritma eğiten bir eğitim ve model değerlendirme tekniğidir.</span><span class="sxs-lookup"><span data-stu-id="1313c-106">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="1313c-107">Bu teknik, eğitim sürecinden verileri tutarak modelin sağlamlığını artırır.</span><span class="sxs-lookup"><span data-stu-id="1313c-107">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="1313c-108">Görünmeyen gözlemlerde performansı artırmanın yanı sıra, veri kısıtlamalı ortamlarda daha küçük bir veri kümesine sahip modelleri eğitmek için etkili bir araç olabilir.</span><span class="sxs-lookup"><span data-stu-id="1313c-108">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="1313c-109">Veri ve veri modeli</span><span class="sxs-lookup"><span data-stu-id="1313c-109">The data and data model</span></span>

<span data-ttu-id="1313c-110">Aşağıdaki biçime sahip bir dosyadan alınan veriler verilir:</span><span class="sxs-lookup"><span data-stu-id="1313c-110">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="1313c-111">Veriler gibi `HousingData` bir sınıf tarafından modellenebilir ve [`IDataView`](xref:Microsoft.ML.IDataView)bir .</span><span class="sxs-lookup"><span data-stu-id="1313c-111">The data can be modeled by a class like `HousingData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="prepare-the-data"></a><span data-ttu-id="1313c-112">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="1313c-112">Prepare the data</span></span>

<span data-ttu-id="1313c-113">Makine öğrenme modelini oluşturmak için kullanmadan önce verileri önceden işleme.</span><span class="sxs-lookup"><span data-stu-id="1313c-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="1313c-114">Bu örnekte, `Size` `HistoricalPrices` ve sütunlar tek bir özellik vektörü içinde birleştirilir [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) ve bu da yöntem kullanılarak adlandırılan `Features` yeni bir sütuna çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="1313c-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="1313c-115">ML.NET algoritmaları tarafından beklenen biçime veri almanın yanı sıra, sütunları birleştirme, ayrı sütunların her biri yerine bir kez işlem uygulayarak ardışık ardışık sonraki işlemleri en iyi duruma getirmektedir.</span><span class="sxs-lookup"><span data-stu-id="1313c-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span>

<span data-ttu-id="1313c-116">Sütunlar tek bir vektörde [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) birleştirildiğinde, `Features` 0-1 `Size` `HistoricalPrices` arasında ve aynı aralıkta almak için sütuna uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1313c-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span>

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

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="1313c-117">Çapraz doğrulamalı tren modeli</span><span class="sxs-lookup"><span data-stu-id="1313c-117">Train model with cross validation</span></span>

<span data-ttu-id="1313c-118">Veriler önceden işlendikten sonra, modeli eğitmenin zamanı gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="1313c-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="1313c-119">İlk olarak, gerçekleştirilecek makine öğrenme göreviyle en yakın hizalayan algoritmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="1313c-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="1313c-120">Öngörülen değer sayısal olarak sürekli bir değer olduğundan, görev gerilemedir.</span><span class="sxs-lookup"><span data-stu-id="1313c-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="1313c-121">ML.NET tarafından uygulanan regresyon algoritmalarından [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) biri de algoritmadır.</span><span class="sxs-lookup"><span data-stu-id="1313c-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="1313c-122">Çapraz doğrulama ile modeli eğitmek için [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1313c-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span>

> [!NOTE]
> <span data-ttu-id="1313c-123">Bu örnek doğrusal bir regresyon modeli kullansa da, CrossValidate Anomaly Detection hariç ML.NET diğer tüm makine öğrenimi görevleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1313c-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="1313c-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*)aşağıdaki işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="1313c-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="1313c-125">Verileri `numberOfFolds` parametrede belirtilen değere eşit bir dizi bölüme ayırır.</span><span class="sxs-lookup"><span data-stu-id="1313c-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="1313c-126">Her bölümün sonucu bir [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) nesnedir.</span><span class="sxs-lookup"><span data-stu-id="1313c-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="1313c-127">Bir model, eğitim veri kümesinde belirtilen makine öğrenme algoritması tahmincisi kullanılarak bölümlerin her biri üzerinde eğitilir.</span><span class="sxs-lookup"><span data-stu-id="1313c-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="1313c-128">Her modelin performansı test veri [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) kümesindeki yöntem kullanılarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1313c-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span>
1. <span data-ttu-id="1313c-129">Model, ölçümleri ile birlikte her model için döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1313c-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="1313c-130">Depolanan sonuç `cvResults` [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesnelerin bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="1313c-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objects.</span></span> <span data-ttu-id="1313c-131">Bu nesne, hem erişilebilir form [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) hem [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) de özellikleri sırasıyla, eğitimli modeli yanı sıra ölçümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1313c-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) properties respectively.</span></span> <span data-ttu-id="1313c-132">Bu örnekte, `Model` özellik türünde [`ITransformer`](xref:Microsoft.ML.ITransformer) `Metrics` ve özellik [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics)türündedir.</span><span class="sxs-lookup"><span data-stu-id="1313c-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="1313c-133">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1313c-133">Evaluate the model</span></span>

<span data-ttu-id="1313c-134">Farklı eğitilmiş modeller için ölçümlertek bir `Metrics` [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesnenin özelliği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="1313c-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="1313c-135">Bu durumda, [R-Squared metrik](https://en.wikipedia.org/wiki/Coefficient_of_determination) erişilir ve değişkende `rSquared`saklanır.</span><span class="sxs-lookup"><span data-stu-id="1313c-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span>

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="1313c-136">`rSquared` Değişkenin içeriğini incelerseniz, çıktı 0-1 arasında değişen beş değer olmalıdır ve 1'e yakın olmak en iyi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1313c-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span> <span data-ttu-id="1313c-137">R-Squared gibi ölçümleri kullanarak, modelleri en iyiden en kötü performansa doğru seçin.</span><span class="sxs-lookup"><span data-stu-id="1313c-137">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="1313c-138">Ardından, öngörülerde bulunmak veya ek işlemler gerçekleştirmek için en üst modeli seçin.</span><span class="sxs-lookup"><span data-stu-id="1313c-138">Then, select the top model to make predictions or perform additional operations with.</span></span>

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
