---
title: Permütasyon Özelliği Önemi olan ML.NET modelleri yorumlayın
description: Permütasyon Özelliği Önemi olan modellerin ML.NET
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c1163a41cd2feb0e8785ae9d4c6a71dfbedf3f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092622"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="d7b8e-103">Permütasyon Özelliği Önemi kullanarak model tahminlerini yorumlama</span><span class="sxs-lookup"><span data-stu-id="d7b8e-103">Interpret model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="d7b8e-104">Permütasyon Özelliği Önemi 'ni (PFI) kullanarak, makine öğrenimi modeli tahminlerini nasıl yorumladığınızı öğrenin ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-104">Using Permutation Feature Importance (PFI), learn how to interpret ML.NET machine learning model predictions.</span></span> <span data-ttu-id="d7b8e-105">PFI, her özelliğin bir tahmine yaptığı göreli katkıyı verir.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-105">PFI gives the relative contribution each feature makes to a prediction.</span></span>

<span data-ttu-id="d7b8e-106">Makine öğrenimi modelleri genellikle girdileri almak ve bir çıkış oluşturmak kara kutular olarak düşünülmektedir.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-106">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="d7b8e-107">Çıktıyı etkileyen özellikler arasındaki ara adımlar veya etkileşimler nadiren anlaşılır.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-107">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="d7b8e-108">Makine öğrenimi sağlık gibi günlük yaşamın daha fazla yönlerine tanıtıldığı için, bir makine öğrenme modelinin neden karar verebettiğini anlamak son derece önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-108">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="d7b8e-109">Örneğin, tanılar bir makine öğrenme modeli tarafından yapılıyorsa, sağlık profesyonelleri bu tanıları yapmak için gitti faktörleri içine bakmak için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-109">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="d7b8e-110">Doğru tanının sağlanması, hastanın hızlı bir şekilde iyileşip iyileşmemesi konusunda büyük bir fark yaratabilir.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-110">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="d7b8e-111">Bu nedenle, bir modeldeki açıklanabilirlik düzeyi ne kadar yüksekse, sağlık profesyonellerinin model tarafından alınan kararları kabul etmesi veya reddetmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-111">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="d7b8e-112">Biri PFI olan modelleri açıklamak için çeşitli teknikler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-112">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="d7b8e-113">PFI, [Breiman'ın *Rastgele Ormanlar* makalesine](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) göre sınıflandırma ve regresyon modellerini açıklamak için kullanılan bir tekniktir (bkz. bölüm 10).</span><span class="sxs-lookup"><span data-stu-id="d7b8e-113">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="d7b8e-114">Yüksek düzeyde, çalışma şekli, tüm veri kümesi için verileri rasgele bir özelliği rasgele karıştırmak ve ilgi performans ölçütü nün ne kadar azaldığını hesaplamaktır.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-114">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="d7b8e-115">Değişiklik ne kadar büyükse, bu özellik o kadar önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-115">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="d7b8e-116">Ayrıca, en önemli özellikleri vurgulayarak, model oluşturucular gürültü ve eğitim süresini potansiyel olarak azaltabilecek daha anlamlı özelliklerden oluşan bir alt küme kullanmaya odaklanabilirler.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-116">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="d7b8e-117">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="d7b8e-117">Load the data</span></span>

<span data-ttu-id="d7b8e-118">Bu örnek için kullanılan veri kümesindeki özellikler 1-12 sütunlarında dır.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-118">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="d7b8e-119">Amaç tahmin `Price`etmektir.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-119">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="d7b8e-120">Sütun</span><span class="sxs-lookup"><span data-stu-id="d7b8e-120">Column</span></span> | <span data-ttu-id="d7b8e-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="d7b8e-121">Feature</span></span> | <span data-ttu-id="d7b8e-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7b8e-122">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="d7b8e-123">1</span><span class="sxs-lookup"><span data-stu-id="d7b8e-123">1</span></span> | <span data-ttu-id="d7b8e-124">Suç Oranı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-124">CrimeRate</span></span> | <span data-ttu-id="d7b8e-125">Kişi başına suç oranı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-125">Per capita crime rate</span></span>
| <span data-ttu-id="d7b8e-126">2</span><span class="sxs-lookup"><span data-stu-id="d7b8e-126">2</span></span> | <span data-ttu-id="d7b8e-127">Yerleşim Bölgeleri</span><span class="sxs-lookup"><span data-stu-id="d7b8e-127">ResidentialZones</span></span> | <span data-ttu-id="d7b8e-128">Şehirdeki yerleşim bölgeleri</span><span class="sxs-lookup"><span data-stu-id="d7b8e-128">Residential zones in town</span></span>
| <span data-ttu-id="d7b8e-129">3</span><span class="sxs-lookup"><span data-stu-id="d7b8e-129">3</span></span> | <span data-ttu-id="d7b8e-130">Ticari Bölgeler</span><span class="sxs-lookup"><span data-stu-id="d7b8e-130">CommercialZones</span></span> | <span data-ttu-id="d7b8e-131">Kasabadaki yerleşim dışı bölgeler</span><span class="sxs-lookup"><span data-stu-id="d7b8e-131">Non-residential zones in town</span></span>
| <span data-ttu-id="d7b8e-132">4</span><span class="sxs-lookup"><span data-stu-id="d7b8e-132">4</span></span> | <span data-ttu-id="d7b8e-133">Yakın Su</span><span class="sxs-lookup"><span data-stu-id="d7b8e-133">NearWater</span></span> | <span data-ttu-id="d7b8e-134">Su gövdesine yakınlık</span><span class="sxs-lookup"><span data-stu-id="d7b8e-134">Proximity to body of water</span></span>
| <span data-ttu-id="d7b8e-135">5</span><span class="sxs-lookup"><span data-stu-id="d7b8e-135">5</span></span> | <span data-ttu-id="d7b8e-136">Toksik Atık Seviyeleri</span><span class="sxs-lookup"><span data-stu-id="d7b8e-136">ToxicWasteLevels</span></span> | <span data-ttu-id="d7b8e-137">Toksisite düzeyleri (PPM)</span><span class="sxs-lookup"><span data-stu-id="d7b8e-137">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="d7b8e-138">6</span><span class="sxs-lookup"><span data-stu-id="d7b8e-138">6</span></span> | <span data-ttu-id="d7b8e-139">Ortalama Oda Sayısı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-139">AverageRoomNumber</span></span> | <span data-ttu-id="d7b8e-140">Evdeki ortalama oda sayısı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-140">Average number of rooms in house</span></span>
| <span data-ttu-id="d7b8e-141">7</span><span class="sxs-lookup"><span data-stu-id="d7b8e-141">7</span></span> | <span data-ttu-id="d7b8e-142">HomeAge</span><span class="sxs-lookup"><span data-stu-id="d7b8e-142">HomeAge</span></span> | <span data-ttu-id="d7b8e-143">Ev yaşı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-143">Age of home</span></span>
| <span data-ttu-id="d7b8e-144">8</span><span class="sxs-lookup"><span data-stu-id="d7b8e-144">8</span></span> | <span data-ttu-id="d7b8e-145">İşMerkeziMesafesi</span><span class="sxs-lookup"><span data-stu-id="d7b8e-145">BusinessCenterDistance</span></span> | <span data-ttu-id="d7b8e-146">En yakın iş bölgesine uzaklık</span><span class="sxs-lookup"><span data-stu-id="d7b8e-146">Distance to nearest business district</span></span>
| <span data-ttu-id="d7b8e-147">9</span><span class="sxs-lookup"><span data-stu-id="d7b8e-147">9</span></span> | <span data-ttu-id="d7b8e-148">OtoyolErişim</span><span class="sxs-lookup"><span data-stu-id="d7b8e-148">HighwayAccess</span></span> | <span data-ttu-id="d7b8e-149">Otoyollara yakınlık</span><span class="sxs-lookup"><span data-stu-id="d7b8e-149">Proximity to highways</span></span>
| <span data-ttu-id="d7b8e-150">10</span><span class="sxs-lookup"><span data-stu-id="d7b8e-150">10</span></span> | <span data-ttu-id="d7b8e-151">Vergi Oranı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-151">TaxRate</span></span> | <span data-ttu-id="d7b8e-152">Emlak vergisi oranı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-152">Property tax rate</span></span>
| <span data-ttu-id="d7b8e-153">11</span><span class="sxs-lookup"><span data-stu-id="d7b8e-153">11</span></span> | <span data-ttu-id="d7b8e-154">ÖğrenciÖğretmen Oranı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-154">StudentTeacherRatio</span></span> | <span data-ttu-id="d7b8e-155">Öğrencilerin öğretmenlere oranı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-155">Ratio of students to teachers</span></span>
| <span data-ttu-id="d7b8e-156">12</span><span class="sxs-lookup"><span data-stu-id="d7b8e-156">12</span></span> | <span data-ttu-id="d7b8e-157">Nüfusun YüzdeLeriYoksulluk</span><span class="sxs-lookup"><span data-stu-id="d7b8e-157">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="d7b8e-158">Yoksulluğun altında yaşayan nüfusun yüzdesi</span><span class="sxs-lookup"><span data-stu-id="d7b8e-158">Percent of population living below poverty</span></span>
| <span data-ttu-id="d7b8e-159">13</span><span class="sxs-lookup"><span data-stu-id="d7b8e-159">13</span></span> | <span data-ttu-id="d7b8e-160">Fiyat</span><span class="sxs-lookup"><span data-stu-id="d7b8e-160">Price</span></span> | <span data-ttu-id="d7b8e-161">Ev fiyatı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-161">Price of the home</span></span>

<span data-ttu-id="d7b8e-162">Veri kümesinin bir örneği aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d7b8e-162">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="d7b8e-163">Bu örnekteki veriler gibi `HousingPriceData` bir sınıf tarafından modellenebilir [`IDataView`](xref:Microsoft.ML.IDataView)ve bir .</span><span class="sxs-lookup"><span data-stu-id="d7b8e-163">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="train-the-model"></a><span data-ttu-id="d7b8e-164">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="d7b8e-164">Train the model</span></span>

<span data-ttu-id="d7b8e-165">Aşağıdaki kod örneği, ev fiyatlarını tahmin etmek için doğrusal bir regresyon modelinin eğitilmesi sürecini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="d7b8e-166">Permütasyon Özelliği Önemi (PFI) olan modeli açıklayın</span><span class="sxs-lookup"><span data-stu-id="d7b8e-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="d7b8e-167">ML.NET ilgili [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) görev için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="d7b8e-168">Eğitim veri [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) kümesini kullanmanın sonucu [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) nesnelerin bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="d7b8e-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)parametre tarafından belirtilen permütasyon sayısına [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) eşit birden fazla gözlem için ortalama ve standart sapma gibi özet istatistikleri sağlar. `permutationCount`</span><span class="sxs-lookup"><span data-stu-id="d7b8e-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="d7b8e-170">Önemi, ya da bu durumda, r-kare metrik mutlak [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) ortalama düşüş tarafından hesaplanan sonra en önemli en önemli den en önemli sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

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

<span data-ttu-id="d7b8e-171">Her bir özelliğin değerlerini `featureImportanceMetrics` yazdırmak, aşağıdakine benzer çıktı lar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="d7b8e-172">Bu değerler verilen verilere göre değiştiğinden, farklı sonuçlar görmeyi beklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="d7b8e-173">Özellik</span><span class="sxs-lookup"><span data-stu-id="d7b8e-173">Feature</span></span> | <span data-ttu-id="d7b8e-174">R-Squared olarak değiştirin</span><span class="sxs-lookup"><span data-stu-id="d7b8e-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="d7b8e-175">OtoyolErişim</span><span class="sxs-lookup"><span data-stu-id="d7b8e-175">HighwayAccess</span></span>       |   <span data-ttu-id="d7b8e-176">-0.042731</span><span class="sxs-lookup"><span data-stu-id="d7b8e-176">-0.042731</span></span>
<span data-ttu-id="d7b8e-177">ÖğrenciÖğretmen Oranı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="d7b8e-178">-0.012730</span><span class="sxs-lookup"><span data-stu-id="d7b8e-178">-0.012730</span></span>
<span data-ttu-id="d7b8e-179">İşMerkeziMesafesi</span><span class="sxs-lookup"><span data-stu-id="d7b8e-179">BusinessCenterDistance</span></span>| <span data-ttu-id="d7b8e-180">-0.010491</span><span class="sxs-lookup"><span data-stu-id="d7b8e-180">-0.010491</span></span>
<span data-ttu-id="d7b8e-181">Vergi Oranı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-181">TaxRate</span></span>             |   <span data-ttu-id="d7b8e-182">-0.008545</span><span class="sxs-lookup"><span data-stu-id="d7b8e-182">-0.008545</span></span>
<span data-ttu-id="d7b8e-183">Ortalama Oda Sayısı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="d7b8e-184">-0.003949</span><span class="sxs-lookup"><span data-stu-id="d7b8e-184">-0.003949</span></span>
<span data-ttu-id="d7b8e-185">Suç Oranı</span><span class="sxs-lookup"><span data-stu-id="d7b8e-185">CrimeRate</span></span>           |   <span data-ttu-id="d7b8e-186">-0.003665</span><span class="sxs-lookup"><span data-stu-id="d7b8e-186">-0.003665</span></span>
<span data-ttu-id="d7b8e-187">Ticari Bölgeler</span><span class="sxs-lookup"><span data-stu-id="d7b8e-187">CommercialZones</span></span>     |   <span data-ttu-id="d7b8e-188">0.002749</span><span class="sxs-lookup"><span data-stu-id="d7b8e-188">0.002749</span></span>
<span data-ttu-id="d7b8e-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="d7b8e-189">HomeAge</span></span>             |   <span data-ttu-id="d7b8e-190">-0.002426</span><span class="sxs-lookup"><span data-stu-id="d7b8e-190">-0.002426</span></span>
<span data-ttu-id="d7b8e-191">Yerleşim Bölgeleri</span><span class="sxs-lookup"><span data-stu-id="d7b8e-191">ResidentialZones</span></span>    |   <span data-ttu-id="d7b8e-192">-0.002319</span><span class="sxs-lookup"><span data-stu-id="d7b8e-192">-0.002319</span></span>
<span data-ttu-id="d7b8e-193">Yakın Su</span><span class="sxs-lookup"><span data-stu-id="d7b8e-193">NearWater</span></span>           |   <span data-ttu-id="d7b8e-194">0.000203</span><span class="sxs-lookup"><span data-stu-id="d7b8e-194">0.000203</span></span>
<span data-ttu-id="d7b8e-195">Nüfusun YüzdesiYoksulluk Altında Yaşayanlar</span><span class="sxs-lookup"><span data-stu-id="d7b8e-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="d7b8e-196">0.000031</span><span class="sxs-lookup"><span data-stu-id="d7b8e-196">0.000031</span></span>
<span data-ttu-id="d7b8e-197">Toksik Atık Seviyeleri</span><span class="sxs-lookup"><span data-stu-id="d7b8e-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="d7b8e-198">-0.000019</span><span class="sxs-lookup"><span data-stu-id="d7b8e-198">-0.000019</span></span>

<span data-ttu-id="d7b8e-199">Bu veri seti için en önemli beş özelliği göz önünde bulundurarak, bu model tarafından öngörülen bir evin fiyatı karayollarına yakınlığı, bölgedeki okulların öğrenci öğretmen oranı, büyük istihdam merkezlerine yakınlığı, emlak vergisi oranı ve evde oda ortalama sayısı.</span><span class="sxs-lookup"><span data-stu-id="d7b8e-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
