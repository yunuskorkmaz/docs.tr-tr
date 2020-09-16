---
title: Çapraz doğrulama kullanarak makine öğrenimi modelini eğitme
description: ML.NET içinde daha güçlü makine öğrenimi modelleri oluşturmak için çapraz doğrulamayı nasıl kullanacağınızı öğrenin. Çapraz doğrulama, verileri birkaç bölüme ayıran ve bu bölümlerde birden çok algoritmaya yönelik bir eğitim ve model değerlendirme tekniğidir.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: 02cec3d22588d8f10d36216422bc19faafffe94b
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679527"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="e46ff-104">Çapraz doğrulama kullanarak makine öğrenimi modelini eğitme</span><span class="sxs-lookup"><span data-stu-id="e46ff-104">Train a machine learning model using cross validation</span></span>

<span data-ttu-id="e46ff-105">ML.NET içinde daha güçlü makine öğrenimi modelleri eğitmek için çapraz doğrulamayı nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="e46ff-105">Learn how to use cross validation to train more robust machine learning models in ML.NET.</span></span>

<span data-ttu-id="e46ff-106">Çapraz doğrulama, verileri birkaç bölüme ayıran ve bu bölümlerde birden çok algoritmaya yönelik bir eğitim ve model değerlendirme tekniğidir.</span><span class="sxs-lookup"><span data-stu-id="e46ff-106">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="e46ff-107">Bu teknik eğitim sürecinde veri tutarak modelin sağlamlığını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="e46ff-107">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="e46ff-108">Veri kısıtlı ortamlarda, görünmeyen gözlemlerdeki performansı iyileştirmeye ek olarak, daha küçük bir veri kümesiyle eğitim modelleri için etkili bir araç olabilir.</span><span class="sxs-lookup"><span data-stu-id="e46ff-108">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="e46ff-109">Veri ve veri modeli</span><span class="sxs-lookup"><span data-stu-id="e46ff-109">The data and data model</span></span>

<span data-ttu-id="e46ff-110">Aşağıdaki biçime sahip bir dosyadan verilen veriler:</span><span class="sxs-lookup"><span data-stu-id="e46ff-110">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="e46ff-111">Veriler, gibi bir sınıfa göre modellenebilir `HousingData` ve ' a yüklenir [`IDataView`](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="e46ff-111">The data can be modeled by a class like `HousingData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="prepare-the-data"></a><span data-ttu-id="e46ff-112">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="e46ff-112">Prepare the data</span></span>

<span data-ttu-id="e46ff-113">Machine Learning modelini derlemek için kullanmadan önce verileri önceden işleyin.</span><span class="sxs-lookup"><span data-stu-id="e46ff-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="e46ff-114">Bu örnekte, `Size` ve sütunları, `HistoricalPrices` yöntemi kullanılarak adlı yeni bir sütuna çıktı olan tek bir özellik vektörü içinde birleştirilir `Features` [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) .</span><span class="sxs-lookup"><span data-stu-id="e46ff-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="e46ff-115">ML.NET algoritmaları tarafından beklenen biçimde verileri almaya ek olarak sütunları bitiştirme, her ayrı sütun yerine birleştirilmiş sütun için işlemi bir kez uygulayarak işlem hattındaki sonraki işlemleri iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="e46ff-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span>

<span data-ttu-id="e46ff-116">Sütunlar tek bir vektörde birleştirildikten sonra, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) `Features` almak için sütuna, `Size` `HistoricalPrices` 0-1 arasındaki aynı aralığa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e46ff-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span>

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

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="e46ff-117">Çapraz doğrulama ile modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="e46ff-117">Train model with cross validation</span></span>

<span data-ttu-id="e46ff-118">Veriler önceden işlendikten sonra modeli eğitmeniz zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="e46ff-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="e46ff-119">İlk olarak, gerçekleştirilecek makine öğrenimi göreviyle en yakından hizalanan algoritmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="e46ff-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="e46ff-120">Tahmin edilen değer sayısal bir sürekli değer olduğundan, görev gerileme olur.</span><span class="sxs-lookup"><span data-stu-id="e46ff-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="e46ff-121">ML.NET tarafından uygulanan regresyon algoritmalarından biri [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algoritmadır.</span><span class="sxs-lookup"><span data-stu-id="e46ff-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="e46ff-122">Çapraz doğrulama ile modeli eğitme [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate%2A) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e46ff-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate%2A) method.</span></span>

> [!NOTE]
> <span data-ttu-id="e46ff-123">Bu örnek, bir doğrusal regresyon modeli kullansa da, çapraz doğrulama, ML.NET içinde anomali algılama hariç diğer tüm makine öğrenimi görevleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e46ff-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="e46ff-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate%2A) Aşağıdaki işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="e46ff-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate%2A) performs the following operations:</span></span>

1. <span data-ttu-id="e46ff-125">Verileri, parametresinde belirtilen değere eşit sayıda bölüm için bölümler `numberOfFolds` .</span><span class="sxs-lookup"><span data-stu-id="e46ff-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="e46ff-126">Her bölümün sonucu bir [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) nesnedir.</span><span class="sxs-lookup"><span data-stu-id="e46ff-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="e46ff-127">Bir model, eğitim veri kümesindeki belirtilen makine öğrenimi algoritması tahmin aracı 'ı kullanılarak bölümlerin her birinde eğitilir.</span><span class="sxs-lookup"><span data-stu-id="e46ff-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="e46ff-128">Her modelin performansı, [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) test veri kümesindeki yöntemi kullanılarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e46ff-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method on the test data set.</span></span>
1. <span data-ttu-id="e46ff-129">Modeller, modellerin her biri için, ölçümleriyle birlikte döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e46ff-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="e46ff-130">İçinde depolanan sonuç `cvResults` bir [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesne koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="e46ff-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objects.</span></span> <span data-ttu-id="e46ff-131">Bu nesne, hem eğitilen modeli hem de her ikisi de sırasıyla erişilebilir olan ölçümleri [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) ve [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e46ff-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) properties respectively.</span></span> <span data-ttu-id="e46ff-132">Bu örnekte, `Model` özelliği türündedir [`ITransformer`](xref:Microsoft.ML.ITransformer) ve `Metrics` özelliği türündedir [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) .</span><span class="sxs-lookup"><span data-stu-id="e46ff-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="e46ff-133">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="e46ff-133">Evaluate the model</span></span>

<span data-ttu-id="e46ff-134">Farklı eğitilen modellere yönelik ölçümlere `Metrics` tekil nesnenin özelliği aracılığıyla erişilebilir [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) .</span><span class="sxs-lookup"><span data-stu-id="e46ff-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="e46ff-135">Bu durumda, [R-kare ölçüsüne](https://en.wikipedia.org/wiki/Coefficient_of_determination) erişilir ve değişkenine depolanır `rSquared` .</span><span class="sxs-lookup"><span data-stu-id="e46ff-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span>

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="e46ff-136">`rSquared`Değişkenin içeriğini inceleyebileceğiniz çıktının en iyi şekilde 1 ' e yakın olduğu 0-1 arasında beş değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e46ff-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span> <span data-ttu-id="e46ff-137">R-kare gibi ölçümleri kullanarak en iyi performansa sahip modelleri seçin.</span><span class="sxs-lookup"><span data-stu-id="e46ff-137">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="e46ff-138">Daha sonra, tahmine dayalı hale getirmek veya ek işlemleri gerçekleştirmek için en iyi modeli seçin.</span><span class="sxs-lookup"><span data-stu-id="e46ff-138">Then, select the top model to make predictions or perform additional operations with.</span></span>

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
