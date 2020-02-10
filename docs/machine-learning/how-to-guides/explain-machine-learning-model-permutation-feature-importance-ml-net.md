---
title: Permütasyon özelliği önem derecesine sahip ML.NET modellerini yorumlama
description: ML.NET içinde permütasyon özelliği önem derecesine sahip modellerin Özellik önemini anlayın
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c1163a41cd2feb0e8785ae9d4c6a71dfbedf3f12
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092622"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="8577f-103">Permütasyon özelliği önem derecesi kullanarak model tahminlerini yorumlama</span><span class="sxs-lookup"><span data-stu-id="8577f-103">Interpret model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="8577f-104">Permütasyon özelliği önem derecesi (PFI) kullanarak ML.NET Machine Learning model tahminlerini nasıl yorumlayacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="8577f-104">Using Permutation Feature Importance (PFI), learn how to interpret ML.NET machine learning model predictions.</span></span> <span data-ttu-id="8577f-105">PFI her bir özelliğin bir tahmine göre yaptığı göreli katkıyı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8577f-105">PFI gives the relative contribution each feature makes to a prediction.</span></span>

<span data-ttu-id="8577f-106">Makine öğrenimi modelleri genellikle giriş ve çıkış oluşturan siyah kutular olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="8577f-106">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="8577f-107">Çıktıyı etkileyen özellikler arasındaki ara adımlar veya etkileşimler nadiren anlaşılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8577f-107">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="8577f-108">Makine öğrenimi, sağlık hizmetleri gibi günlük hayatın daha belirgin yönlerine tanıtıldığında, Machine Learning modelinin neden yaptığı kararları nasıl yaptığını anlamak en önemli öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8577f-108">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="8577f-109">Örneğin, bir makine öğrenimi modeliyle tanılar yapılırsa, sağlık uzmanlarının, bu, bu, tanılar haline gelen faktörleri bulmak için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="8577f-109">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="8577f-110">Doğru tanısı sağlamak, hasta 'ın hızlı bir şekilde kurtarma yapıp yapmayacağı konusunda harika bir farklılık yapabilir.</span><span class="sxs-lookup"><span data-stu-id="8577f-110">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="8577f-111">Bu nedenle, bir modeldeki explainability düzeyi arttıkça, daha yüksek güvenilirlikli sağlık uzmanlarının model tarafından yapılan kararları kabul etmesi veya reddetmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8577f-111">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="8577f-112">Farklı teknikler, bunlardan biri PFI olan modelleri açıklamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8577f-112">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="8577f-113">PFı, [Breiman 'Nın *rastgele orman* kağıdı](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) tarafından ilham olan sınıflandırma ve regresyon modellerini açıklamak için kullanılan bir tekniktir (bkz. Bölüm 10).</span><span class="sxs-lookup"><span data-stu-id="8577f-113">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="8577f-114">Yüksek düzeyde, çalışma şekli, veri kümesinin tamamı için bir seferde bir özelliği rastgele karıştırarak ve ilgi çekici performans ölçüsünün ne kadarının azaldığından hesaplama.</span><span class="sxs-lookup"><span data-stu-id="8577f-114">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="8577f-115">Değişiklik ne kadar büyükse, bu özellik o kadar önemli olur.</span><span class="sxs-lookup"><span data-stu-id="8577f-115">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="8577f-116">Ayrıca, en önemli özellikleri vurgulayarak model oluşturucular, gürültü ve eğitim süresini azaltan daha anlamlı özelliklerin bir alt kümesini kullanmaya odaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="8577f-116">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="8577f-117">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="8577f-117">Load the data</span></span>

<span data-ttu-id="8577f-118">Bu örnek için kullanılan veri kümesindeki Özellikler 1-12 sütunlarında bulunur.</span><span class="sxs-lookup"><span data-stu-id="8577f-118">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="8577f-119">Amaç `Price`tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8577f-119">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="8577f-120">Sütun</span><span class="sxs-lookup"><span data-stu-id="8577f-120">Column</span></span> | <span data-ttu-id="8577f-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="8577f-121">Feature</span></span> | <span data-ttu-id="8577f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8577f-122">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="8577f-123">1\.</span><span class="sxs-lookup"><span data-stu-id="8577f-123">1</span></span> | <span data-ttu-id="8577f-124">Crimerde</span><span class="sxs-lookup"><span data-stu-id="8577f-124">CrimeRate</span></span> | <span data-ttu-id="8577f-125">GDP suta hızı başına</span><span class="sxs-lookup"><span data-stu-id="8577f-125">Per capita crime rate</span></span>
| <span data-ttu-id="8577f-126">2</span><span class="sxs-lookup"><span data-stu-id="8577f-126">2</span></span> | <span data-ttu-id="8577f-127">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="8577f-127">ResidentialZones</span></span> | <span data-ttu-id="8577f-128">Kasadaki mesken bölgeleri</span><span class="sxs-lookup"><span data-stu-id="8577f-128">Residential zones in town</span></span>
| <span data-ttu-id="8577f-129">3</span><span class="sxs-lookup"><span data-stu-id="8577f-129">3</span></span> | <span data-ttu-id="8577f-130">Ticari bölgeler</span><span class="sxs-lookup"><span data-stu-id="8577f-130">CommercialZones</span></span> | <span data-ttu-id="8577f-131">Kasadaki yöresel olmayan bölgeler</span><span class="sxs-lookup"><span data-stu-id="8577f-131">Non-residential zones in town</span></span>
| <span data-ttu-id="8577f-132">4</span><span class="sxs-lookup"><span data-stu-id="8577f-132">4</span></span> | <span data-ttu-id="8577f-133">Yaklaştığında su</span><span class="sxs-lookup"><span data-stu-id="8577f-133">NearWater</span></span> | <span data-ttu-id="8577f-134">Su gövdesine yakınlık</span><span class="sxs-lookup"><span data-stu-id="8577f-134">Proximity to body of water</span></span>
| <span data-ttu-id="8577f-135">5</span><span class="sxs-lookup"><span data-stu-id="8577f-135">5</span></span> | <span data-ttu-id="8577f-136">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="8577f-136">ToxicWasteLevels</span></span> | <span data-ttu-id="8577f-137">Toxicity düzeyleri (PPM)</span><span class="sxs-lookup"><span data-stu-id="8577f-137">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="8577f-138">6</span><span class="sxs-lookup"><span data-stu-id="8577f-138">6</span></span> | <span data-ttu-id="8577f-139">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="8577f-139">AverageRoomNumber</span></span> | <span data-ttu-id="8577f-140">Evin ortalama oda sayısı</span><span class="sxs-lookup"><span data-stu-id="8577f-140">Average number of rooms in house</span></span>
| <span data-ttu-id="8577f-141">7</span><span class="sxs-lookup"><span data-stu-id="8577f-141">7</span></span> | <span data-ttu-id="8577f-142">HomeAge</span><span class="sxs-lookup"><span data-stu-id="8577f-142">HomeAge</span></span> | <span data-ttu-id="8577f-143">Evin yaşı</span><span class="sxs-lookup"><span data-stu-id="8577f-143">Age of home</span></span>
| <span data-ttu-id="8577f-144">8</span><span class="sxs-lookup"><span data-stu-id="8577f-144">8</span></span> | <span data-ttu-id="8577f-145">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="8577f-145">BusinessCenterDistance</span></span> | <span data-ttu-id="8577f-146">En yakın iş bölgesi uzaklığı</span><span class="sxs-lookup"><span data-stu-id="8577f-146">Distance to nearest business district</span></span>
| <span data-ttu-id="8577f-147">9</span><span class="sxs-lookup"><span data-stu-id="8577f-147">9</span></span> | <span data-ttu-id="8577f-148">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="8577f-148">HighwayAccess</span></span> | <span data-ttu-id="8577f-149">Üst yöntemlere yakınlık</span><span class="sxs-lookup"><span data-stu-id="8577f-149">Proximity to highways</span></span>
| <span data-ttu-id="8577f-150">10</span><span class="sxs-lookup"><span data-stu-id="8577f-150">10</span></span> | <span data-ttu-id="8577f-151">Vergilenrate</span><span class="sxs-lookup"><span data-stu-id="8577f-151">TaxRate</span></span> | <span data-ttu-id="8577f-152">Özellik vergi oranı</span><span class="sxs-lookup"><span data-stu-id="8577f-152">Property tax rate</span></span>
| <span data-ttu-id="8577f-153">11</span><span class="sxs-lookup"><span data-stu-id="8577f-153">11</span></span> | <span data-ttu-id="8577f-154">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="8577f-154">StudentTeacherRatio</span></span> | <span data-ttu-id="8577f-155">Öğrencilerin öğretmenler için oranı</span><span class="sxs-lookup"><span data-stu-id="8577f-155">Ratio of students to teachers</span></span>
| <span data-ttu-id="8577f-156">12</span><span class="sxs-lookup"><span data-stu-id="8577f-156">12</span></span> | <span data-ttu-id="8577f-157">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="8577f-157">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="8577f-158">Poverty 'in altında yaşayan popülasyon yüzdesi</span><span class="sxs-lookup"><span data-stu-id="8577f-158">Percent of population living below poverty</span></span>
| <span data-ttu-id="8577f-159">13</span><span class="sxs-lookup"><span data-stu-id="8577f-159">13</span></span> | <span data-ttu-id="8577f-160">Fiyat</span><span class="sxs-lookup"><span data-stu-id="8577f-160">Price</span></span> | <span data-ttu-id="8577f-161">Giriş fiyatı</span><span class="sxs-lookup"><span data-stu-id="8577f-161">Price of the home</span></span>

<span data-ttu-id="8577f-162">Veri kümesinin bir örneği aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8577f-162">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="8577f-163">Bu örnekteki veriler, `HousingPriceData` gibi bir sınıfa göre modellenebilir ve bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8577f-163">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
class HousingPriceData
{
    [LoadColumn(0)]
    public float CrimeRate { get; set; }

    [LoadColumn(1)]
    public float ResidentialZones { get; set; }

    [LoadColumn(2)]
    public float CommercialZones { get; set; }

    [LoadColumn(3)]
    public float NearWater { get; set; }

    [LoadColumn(4)]
    public float ToxicWasteLevels { get; set; }

    [LoadColumn(5)]
    public float AverageRoomNumber { get; set; }

    [LoadColumn(6)]
    public float HomeAge { get; set; }

    [LoadColumn(7)]
    public float BusinessCenterDistance { get; set; }

    [LoadColumn(8)]
    public float HighwayAccess { get; set; }

    [LoadColumn(9)]
    public float TaxRate { get; set; }

    [LoadColumn(10)]
    public float StudentTeacherRatio { get; set; }

    [LoadColumn(11)]
    public float PercentPopulationBelowPoverty { get; set; }

    [LoadColumn(12)]
    [ColumnName("Label")]
    public float Price { get; set; }
}
```

## <a name="train-the-model"></a><span data-ttu-id="8577f-164">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8577f-164">Train the model</span></span>

<span data-ttu-id="8577f-165">Aşağıdaki kod örneği, ev fiyatlarını tahmin etmek için bir doğrusal regresyon modeli eğitimi sürecini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8577f-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

```csharp
// 1. Get the column name of input features.
string[] featureColumnNames =
    data.Schema
        .Select(column => column.Name)
        .Where(columnName => columnName != "Label").ToArray();

// 2. Define estimator with data pre-processing steps
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", featureColumnNames)
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// 3. Create transformer using the data pre-processing estimator
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// 4. Pre-process the training data
IDataView preprocessedTrainData = dataPrepTransformer.Transform(data);

// 5. Define Stochastic Dual Coordinate Ascent machine learning estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// 6. Train machine learning model
var sdcaModel = sdcaEstimator.Fit(preprocessedTrainData);
```

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="8577f-166">Modeli permütasyon özelliği önem derecesi (PFı) ile açıklayın</span><span class="sxs-lookup"><span data-stu-id="8577f-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="8577f-167">ML.NET içinde, ilgili göreviniz için [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8577f-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="8577f-168">Eğitim veri kümesindeki [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) kullanmanın sonucu [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) nesnelerinin bir [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) .</span><span class="sxs-lookup"><span data-stu-id="8577f-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="8577f-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) , `permutationCount` parametresi tarafından belirtilen permütasyon sayısına eşit olan [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) birden çok gözlemye yönelik ortalama ve standart sapma gibi özet istatistikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8577f-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="8577f-170">Önem derecesi veya bu durumda, [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) tarafından hesaplanan R-kare ölçümünde mutlak ortalama azalma, daha sonra en önemli olandan en az önemli olan şekilde sıralanır.</span><span class="sxs-lookup"><span data-stu-id="8577f-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

```csharp
// Order features by importance
var featureImportanceMetrics =
    permutationFeatureImportance
        .Select((metric, index) => new { index, metric.RSquared })
        .OrderByDescending(myFeatures => Math.Abs(myFeatures.RSquared.Mean));

Console.WriteLine("Feature\tPFI");

foreach (var feature in featureImportanceMetrics)
{
    Console.WriteLine($"{featureColumnNames[feature.index],-20}|\t{feature.RSquared.Mean:F6}");
}
```

<span data-ttu-id="8577f-171">`featureImportanceMetrics` her bir özelliğin değerlerini yazdırmak, aşağıdakine benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="8577f-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="8577f-172">Bu değerler verilen verilere göre farklılık gösterdiğinden, farklı sonuçlar görmeyi beklemeniz gerektiğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8577f-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="8577f-173">Özellik</span><span class="sxs-lookup"><span data-stu-id="8577f-173">Feature</span></span> | <span data-ttu-id="8577f-174">R-kare olarak değiştir</span><span class="sxs-lookup"><span data-stu-id="8577f-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="8577f-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="8577f-175">HighwayAccess</span></span>       |   <span data-ttu-id="8577f-176">-0,042731</span><span class="sxs-lookup"><span data-stu-id="8577f-176">-0.042731</span></span>
<span data-ttu-id="8577f-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="8577f-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="8577f-178">-0,012730</span><span class="sxs-lookup"><span data-stu-id="8577f-178">-0.012730</span></span>
<span data-ttu-id="8577f-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="8577f-179">BusinessCenterDistance</span></span>| <span data-ttu-id="8577f-180">-0,010491</span><span class="sxs-lookup"><span data-stu-id="8577f-180">-0.010491</span></span>
<span data-ttu-id="8577f-181">Vergilenrate</span><span class="sxs-lookup"><span data-stu-id="8577f-181">TaxRate</span></span>             |   <span data-ttu-id="8577f-182">-0,008545</span><span class="sxs-lookup"><span data-stu-id="8577f-182">-0.008545</span></span>
<span data-ttu-id="8577f-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="8577f-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="8577f-184">-0,003949</span><span class="sxs-lookup"><span data-stu-id="8577f-184">-0.003949</span></span>
<span data-ttu-id="8577f-185">Crimerde</span><span class="sxs-lookup"><span data-stu-id="8577f-185">CrimeRate</span></span>           |   <span data-ttu-id="8577f-186">-0,003665</span><span class="sxs-lookup"><span data-stu-id="8577f-186">-0.003665</span></span>
<span data-ttu-id="8577f-187">Ticari bölgeler</span><span class="sxs-lookup"><span data-stu-id="8577f-187">CommercialZones</span></span>     |   <span data-ttu-id="8577f-188">0,002749</span><span class="sxs-lookup"><span data-stu-id="8577f-188">0.002749</span></span>
<span data-ttu-id="8577f-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="8577f-189">HomeAge</span></span>             |   <span data-ttu-id="8577f-190">-0,002426</span><span class="sxs-lookup"><span data-stu-id="8577f-190">-0.002426</span></span>
<span data-ttu-id="8577f-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="8577f-191">ResidentialZones</span></span>    |   <span data-ttu-id="8577f-192">-0,002319</span><span class="sxs-lookup"><span data-stu-id="8577f-192">-0.002319</span></span>
<span data-ttu-id="8577f-193">Yaklaştığında su</span><span class="sxs-lookup"><span data-stu-id="8577f-193">NearWater</span></span>           |   <span data-ttu-id="8577f-194">0,000203</span><span class="sxs-lookup"><span data-stu-id="8577f-194">0.000203</span></span>
<span data-ttu-id="8577f-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="8577f-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="8577f-196">0,000031</span><span class="sxs-lookup"><span data-stu-id="8577f-196">0.000031</span></span>
<span data-ttu-id="8577f-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="8577f-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="8577f-198">-0,000019</span><span class="sxs-lookup"><span data-stu-id="8577f-198">-0.000019</span></span>

<span data-ttu-id="8577f-199">Bu veri kümesi için en önemli beş özelliğe göz atmak için, bu model tarafından tahmin edilen bir evin fiyatı, bir yakınlık, alanda okulların öğrencisi oranı, önemli iş merkezlerine yakınlık, özellik vergi oranı ve giriş alanındaki ortalama oda sayısı.</span><span class="sxs-lookup"><span data-stu-id="8577f-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
