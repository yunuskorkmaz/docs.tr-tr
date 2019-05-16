---
title: PERMÜTASYON özellik önem kullanarak model tahmin açıklayın
description: Modelleri özellik önemini ML.NET özellik önemi permütasyon ile anlama
ms.date: 05/02/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 51ef4b55b1518381881e57d83fd43f8ec7f786c6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645060"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="9df39-103">PERMÜTASYON özellik önem kullanarak model tahmin açıklayın</span><span class="sxs-lookup"><span data-stu-id="9df39-103">Explain model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="9df39-104">ML.NET makine tarafından anlama permütasyon özellik önem derecesi (PFI) kullanarak tahmin için katkı özelliklere sahip model tahminlerini öğrenme açıklayacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="9df39-104">Learn how to explain ML.NET machine learning model predictions by understanding the contribution features have to predictions using Permutation Feature Importance (PFI).</span></span>

<span data-ttu-id="9df39-105">Makine öğrenimi modelleri genellikle kara kutular girişleri almak ve bir çıkış oluşturmak zorlayıcı.</span><span class="sxs-lookup"><span data-stu-id="9df39-105">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="9df39-106">Çıkış etkileyen özellikler arasındaki etkileşimleri ve Ara adımları nadiren anlaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="9df39-106">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="9df39-107">Machine learning gündelik yaşamla sağlık gibi daha fazla yönünü halinde sunulan gibi neden makine modeli yapar kararları öğrenme yaptığını anlamak için dayanıklılığı olur.</span><span class="sxs-lookup"><span data-stu-id="9df39-107">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="9df39-108">Örneğin, tanılama machine learning modeli tarafından yapılan, sağlık uzmanları, tanılama yapmak içine giden Etkenler içine aramak için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="9df39-108">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="9df39-109">Doğru tanılama sağlamak veya bir Hasta kurtarma içerip içermediğine üzerinde büyük bir fark hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="9df39-109">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="9df39-110">Bu nedenle daha yüksek düzeyde bir modelde explainability, kabul etme veya reddetme model tarafından alınan kararları daha fazla güvenle sağlık uzmanları sahip.</span><span class="sxs-lookup"><span data-stu-id="9df39-110">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="9df39-111">Çeşitli teknikler PFI biri olan modeller, açıklamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9df39-111">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="9df39-112">PFI olan ilham almıştır sınıflandırma ve regresyon modellerini açıklamak için kullanılan bir teknik [Breiman'ın *rastgele ormanları* kağıt](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(10 bölümüne bakın).</span><span class="sxs-lookup"><span data-stu-id="9df39-112">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(see section 10).</span></span> <span data-ttu-id="9df39-113">Yüksek bir düzeyde çalıştığını rastgele tüm veri kümesi için bir kerede veri bir özellik karıştırma ve ilgi ne kadar performans ölçümü azaltır hesaplama yoludur.</span><span class="sxs-lookup"><span data-stu-id="9df39-113">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="9df39-114">Büyük değişiklik, daha da önemlisi, özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="9df39-114">The larger the change, the more important that feature is.</span></span> 

<span data-ttu-id="9df39-115">Ayrıca, en önemli özelliklere vurgulayarak modeli oluşturucular gürültü ve eğitim süresini azaltmak daha anlamlı özelliklerinin bir alt kümesi ile üzerinde odaklanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9df39-115">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="9df39-116">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="9df39-116">Load the data</span></span>

<span data-ttu-id="9df39-117">Bu örnek için kullanılan veri kümesindeki sütunları 1-12 özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="9df39-117">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="9df39-118">Hedef tahmin etmektir `Price`.</span><span class="sxs-lookup"><span data-stu-id="9df39-118">The goal is to predict `Price`.</span></span> 

| <span data-ttu-id="9df39-119">Sütun</span><span class="sxs-lookup"><span data-stu-id="9df39-119">Column</span></span> | <span data-ttu-id="9df39-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="9df39-120">Feature</span></span> | <span data-ttu-id="9df39-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9df39-121">Description</span></span> 
| --- | --- | --- |
| <span data-ttu-id="9df39-122">1.</span><span class="sxs-lookup"><span data-stu-id="9df39-122">1</span></span> | <span data-ttu-id="9df39-123">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="9df39-123">CrimeRate</span></span> | <span data-ttu-id="9df39-124">Gdp suç oranı</span><span class="sxs-lookup"><span data-stu-id="9df39-124">Per capita crime rate</span></span>
| <span data-ttu-id="9df39-125">2</span><span class="sxs-lookup"><span data-stu-id="9df39-125">2</span></span> | <span data-ttu-id="9df39-126">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="9df39-126">ResidentialZones</span></span> | <span data-ttu-id="9df39-127">Belediye konut bölgelere</span><span class="sxs-lookup"><span data-stu-id="9df39-127">Residential zones in town</span></span>
| <span data-ttu-id="9df39-128">3</span><span class="sxs-lookup"><span data-stu-id="9df39-128">3</span></span> | <span data-ttu-id="9df39-129">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="9df39-129">CommercialZones</span></span> | <span data-ttu-id="9df39-130">Belediye olmayan konut bölgelere</span><span class="sxs-lookup"><span data-stu-id="9df39-130">Non-residential zones in town</span></span>
| <span data-ttu-id="9df39-131">4</span><span class="sxs-lookup"><span data-stu-id="9df39-131">4</span></span> | <span data-ttu-id="9df39-132">NearWater</span><span class="sxs-lookup"><span data-stu-id="9df39-132">NearWater</span></span> | <span data-ttu-id="9df39-133">Su body yakınlık</span><span class="sxs-lookup"><span data-stu-id="9df39-133">Proximity to body of water</span></span>
| <span data-ttu-id="9df39-134">5</span><span class="sxs-lookup"><span data-stu-id="9df39-134">5</span></span> | <span data-ttu-id="9df39-135">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="9df39-135">ToxicWasteLevels</span></span> | <span data-ttu-id="9df39-136">Toxicity düzeyleri (PPM)</span><span class="sxs-lookup"><span data-stu-id="9df39-136">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="9df39-137">6</span><span class="sxs-lookup"><span data-stu-id="9df39-137">6</span></span> | <span data-ttu-id="9df39-138">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="9df39-138">AverageRoomNumber</span></span> | <span data-ttu-id="9df39-139">Şirket içi ilgili odalar ortalama sayısı</span><span class="sxs-lookup"><span data-stu-id="9df39-139">Average number of rooms in house</span></span>
| <span data-ttu-id="9df39-140">7</span><span class="sxs-lookup"><span data-stu-id="9df39-140">7</span></span> | <span data-ttu-id="9df39-141">HomeAge</span><span class="sxs-lookup"><span data-stu-id="9df39-141">HomeAge</span></span> | <span data-ttu-id="9df39-142">Giriş yaşı</span><span class="sxs-lookup"><span data-stu-id="9df39-142">Age of home</span></span>
| <span data-ttu-id="9df39-143">8</span><span class="sxs-lookup"><span data-stu-id="9df39-143">8</span></span> | <span data-ttu-id="9df39-144">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="9df39-144">BusinessCenterDistance</span></span> | <span data-ttu-id="9df39-145">En yakın iş bölge uzaklığı</span><span class="sxs-lookup"><span data-stu-id="9df39-145">Distance to nearest business district</span></span>
| <span data-ttu-id="9df39-146">9</span><span class="sxs-lookup"><span data-stu-id="9df39-146">9</span></span> | <span data-ttu-id="9df39-147">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="9df39-147">HighwayAccess</span></span> | <span data-ttu-id="9df39-148">Otoyollar yakınlığını</span><span class="sxs-lookup"><span data-stu-id="9df39-148">Proximity to highways</span></span>
| <span data-ttu-id="9df39-149">10</span><span class="sxs-lookup"><span data-stu-id="9df39-149">10</span></span> | <span data-ttu-id="9df39-150">TaxRate</span><span class="sxs-lookup"><span data-stu-id="9df39-150">TaxRate</span></span> | <span data-ttu-id="9df39-151">Özellik Vergi oranı</span><span class="sxs-lookup"><span data-stu-id="9df39-151">Property tax rate</span></span>
| <span data-ttu-id="9df39-152">11</span><span class="sxs-lookup"><span data-stu-id="9df39-152">11</span></span> | <span data-ttu-id="9df39-153">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="9df39-153">StudentTeacherRatio</span></span> | <span data-ttu-id="9df39-154">Öğretmenler için Öğrenciler oranı</span><span class="sxs-lookup"><span data-stu-id="9df39-154">Ratio of students to teachers</span></span>
| <span data-ttu-id="9df39-155">12</span><span class="sxs-lookup"><span data-stu-id="9df39-155">12</span></span> | <span data-ttu-id="9df39-156">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="9df39-156">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="9df39-157">Yoksulluğun giderilmesine yaşayan popülasyon yüzdesi</span><span class="sxs-lookup"><span data-stu-id="9df39-157">Percent of population living below poverty</span></span>
| <span data-ttu-id="9df39-158">13</span><span class="sxs-lookup"><span data-stu-id="9df39-158">13</span></span> | <span data-ttu-id="9df39-159">Fiyat</span><span class="sxs-lookup"><span data-stu-id="9df39-159">Price</span></span> | <span data-ttu-id="9df39-160">Giriş fiyatı</span><span class="sxs-lookup"><span data-stu-id="9df39-160">Price of the home</span></span>

<span data-ttu-id="9df39-161">Veri kümesinin bir örnek aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9df39-161">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="9df39-162">Bu örnek verileri gibi bir sınıf tarafından modellenebilir `HousingPriceData`:</span><span class="sxs-lookup"><span data-stu-id="9df39-162">The data in this sample can be modeled by a class like `HousingPriceData`:</span></span>

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

<span data-ttu-id="9df39-163">Verilerin bir [ `IDataView` ](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="9df39-163">Load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

## <a name="train-the-model"></a><span data-ttu-id="9df39-164">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="9df39-164">Train the model</span></span>

<span data-ttu-id="9df39-165">Aşağıdaki kod örneği, ev fiyatlarını tahmin etmek için bir doğrusal regresyon modeli eğitimi işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9df39-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="9df39-166">PERMÜTASYON özellik önem derecesi (PFI) modeli açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="9df39-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="9df39-167">ML.NET kullanımda [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) ilgili göreviniz için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9df39-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="9df39-168">Kullanmanın sonucu [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) eğitim veri kümesi üzerinde bir [ `ImmutableArray` ](xref:System.Collections.Immutable.ImmutableArray) , [ `RegressionMetricsStatistics` ](xref:Microsoft.ML.Data.RegressionMetricsStatistics) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9df39-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="9df39-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) birden çok gözlemleri için Özet istatistikleri gibi ortalama ve standart sapma sağlar [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics) tarafından belirtilen permütasyon sayısını eşit `permutationCount` parametresi.</span><span class="sxs-lookup"><span data-stu-id="9df39-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="9df39-170">Önem derecesi veya bu durumda, R karesi alınmış ölçüm mutlak ortalama azaltma hesaplanan tarafından [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) sonra en önemli en az önemli sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="9df39-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>  

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

<span data-ttu-id="9df39-171">Her özelliklerinin değerlerini yazdırma `featureImportanceMetrics` altında için benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="9df39-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="9df39-172">Bu değerleri farklı olduğundan, farklı sonuçlar verildikleri verilere dayalı görmeyi beklemelisiniz aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9df39-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>  

| <span data-ttu-id="9df39-173">Özellik</span><span class="sxs-lookup"><span data-stu-id="9df39-173">Feature</span></span> | <span data-ttu-id="9df39-174">R kare için değiştirin</span><span class="sxs-lookup"><span data-stu-id="9df39-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="9df39-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="9df39-175">HighwayAccess</span></span>       |   <span data-ttu-id="9df39-176">-0.042731</span><span class="sxs-lookup"><span data-stu-id="9df39-176">-0.042731</span></span>
<span data-ttu-id="9df39-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="9df39-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="9df39-178">-0.012730</span><span class="sxs-lookup"><span data-stu-id="9df39-178">-0.012730</span></span>
<span data-ttu-id="9df39-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="9df39-179">BusinessCenterDistance</span></span>| <span data-ttu-id="9df39-180">-0.010491</span><span class="sxs-lookup"><span data-stu-id="9df39-180">-0.010491</span></span>
<span data-ttu-id="9df39-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="9df39-181">TaxRate</span></span>             |   <span data-ttu-id="9df39-182">-0.008545</span><span class="sxs-lookup"><span data-stu-id="9df39-182">-0.008545</span></span>
<span data-ttu-id="9df39-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="9df39-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="9df39-184">-0.003949</span><span class="sxs-lookup"><span data-stu-id="9df39-184">-0.003949</span></span>
<span data-ttu-id="9df39-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="9df39-185">CrimeRate</span></span>           |   <span data-ttu-id="9df39-186">-0.003665</span><span class="sxs-lookup"><span data-stu-id="9df39-186">-0.003665</span></span>
<span data-ttu-id="9df39-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="9df39-187">CommercialZones</span></span>     |   <span data-ttu-id="9df39-188">0.002749</span><span class="sxs-lookup"><span data-stu-id="9df39-188">0.002749</span></span>
<span data-ttu-id="9df39-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="9df39-189">HomeAge</span></span>             |   <span data-ttu-id="9df39-190">-0.002426</span><span class="sxs-lookup"><span data-stu-id="9df39-190">-0.002426</span></span>
<span data-ttu-id="9df39-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="9df39-191">ResidentialZones</span></span>    |   <span data-ttu-id="9df39-192">-0.002319</span><span class="sxs-lookup"><span data-stu-id="9df39-192">-0.002319</span></span>
<span data-ttu-id="9df39-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="9df39-193">NearWater</span></span>           |   <span data-ttu-id="9df39-194">0.000203</span><span class="sxs-lookup"><span data-stu-id="9df39-194">0.000203</span></span>
<span data-ttu-id="9df39-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="9df39-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="9df39-196">0.000031</span><span class="sxs-lookup"><span data-stu-id="9df39-196">0.000031</span></span>
<span data-ttu-id="9df39-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="9df39-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="9df39-198">-0.000019</span><span class="sxs-lookup"><span data-stu-id="9df39-198">-0.000019</span></span>

<span data-ttu-id="9df39-199">Göz alma bu veri kümesi, bu modeli tarafından tahmin edilen bir ev fiyatı için beş en önemli özellikleri, yakınlık Otoyollar, okullar alanında Öğrenci ve Öğretmen oranı, ana çalışan merkezleri özelliği Vergi oranı yakınlığını etkilenir ve Giriş odalarında ortalama sayısı.</span><span class="sxs-lookup"><span data-stu-id="9df39-199">Taking a look at the the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
