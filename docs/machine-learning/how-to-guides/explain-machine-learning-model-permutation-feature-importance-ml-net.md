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
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a>Permütasyon Özelliği Önemi kullanarak model tahminlerini yorumlama

Permütasyon Özelliği Önemi 'ni (PFI) kullanarak, makine öğrenimi modeli tahminlerini nasıl yorumladığınızı öğrenin ML.NET. PFI, her özelliğin bir tahmine yaptığı göreli katkıyı verir.

Makine öğrenimi modelleri genellikle girdileri almak ve bir çıkış oluşturmak kara kutular olarak düşünülmektedir. Çıktıyı etkileyen özellikler arasındaki ara adımlar veya etkileşimler nadiren anlaşılır. Makine öğrenimi sağlık gibi günlük yaşamın daha fazla yönlerine tanıtıldığı için, bir makine öğrenme modelinin neden karar verebettiğini anlamak son derece önemlidir. Örneğin, tanılar bir makine öğrenme modeli tarafından yapılıyorsa, sağlık profesyonelleri bu tanıları yapmak için gitti faktörleri içine bakmak için bir yol gerekir. Doğru tanının sağlanması, hastanın hızlı bir şekilde iyileşip iyileşmemesi konusunda büyük bir fark yaratabilir. Bu nedenle, bir modeldeki açıklanabilirlik düzeyi ne kadar yüksekse, sağlık profesyonellerinin model tarafından alınan kararları kabul etmesi veya reddetmesi gerekir.

Biri PFI olan modelleri açıklamak için çeşitli teknikler kullanılır. PFI, [Breiman'ın *Rastgele Ormanlar* makalesine](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) göre sınıflandırma ve regresyon modellerini açıklamak için kullanılan bir tekniktir (bkz. bölüm 10). Yüksek düzeyde, çalışma şekli, tüm veri kümesi için verileri rasgele bir özelliği rasgele karıştırmak ve ilgi performans ölçütü nün ne kadar azaldığını hesaplamaktır. Değişiklik ne kadar büyükse, bu özellik o kadar önemlidir.

Ayrıca, en önemli özellikleri vurgulayarak, model oluşturucular gürültü ve eğitim süresini potansiyel olarak azaltabilecek daha anlamlı özelliklerden oluşan bir alt küme kullanmaya odaklanabilirler.

## <a name="load-the-data"></a>Verileri yükleme

Bu örnek için kullanılan veri kümesindeki özellikler 1-12 sütunlarında dır. Amaç tahmin `Price`etmektir.

| Sütun | Özellik | Açıklama
| --- | --- | --- |
| 1 | Suç Oranı | Kişi başına suç oranı
| 2 | Yerleşim Bölgeleri | Şehirdeki yerleşim bölgeleri
| 3 | Ticari Bölgeler | Kasabadaki yerleşim dışı bölgeler
| 4 | Yakın Su | Su gövdesine yakınlık
| 5 | Toksik Atık Seviyeleri | Toksisite düzeyleri (PPM)
| 6 | Ortalama Oda Sayısı | Evdeki ortalama oda sayısı
| 7 | HomeAge | Ev yaşı
| 8 | İşMerkeziMesafesi | En yakın iş bölgesine uzaklık
| 9 | OtoyolErişim | Otoyollara yakınlık
| 10 | Vergi Oranı | Emlak vergisi oranı
| 11 | ÖğrenciÖğretmen Oranı | Öğrencilerin öğretmenlere oranı
| 12 | Nüfusun YüzdeLeriYoksulluk | Yoksulluğun altında yaşayan nüfusun yüzdesi
| 13 | Fiyat | Ev fiyatı

Veri kümesinin bir örneği aşağıda gösterilmiştir:

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

Bu örnekteki veriler gibi `HousingPriceData` bir sınıf tarafından modellenebilir [`IDataView`](xref:Microsoft.ML.IDataView)ve bir .

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

## <a name="train-the-model"></a>Modeli eğitme

Aşağıdaki kod örneği, ev fiyatlarını tahmin etmek için doğrusal bir regresyon modelinin eğitilmesi sürecini göstermektedir.

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>Permütasyon Özelliği Önemi (PFI) olan modeli açıklayın

ML.NET ilgili [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) görev için yöntemi kullanın.

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

Eğitim veri [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) kümesini kullanmanın sonucu [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) nesnelerin bir sonucudur. [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)parametre tarafından belirtilen permütasyon sayısına [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) eşit birden fazla gözlem için ortalama ve standart sapma gibi özet istatistikleri sağlar. `permutationCount`

Önemi, ya da bu durumda, r-kare metrik mutlak [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) ortalama düşüş tarafından hesaplanan sonra en önemli en önemli den en önemli sıralanabilir.

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

Her bir özelliğin değerlerini `featureImportanceMetrics` yazdırmak, aşağıdakine benzer çıktı lar oluşturur. Bu değerler verilen verilere göre değiştiğinden, farklı sonuçlar görmeyi beklemeniz gerektiğini unutmayın.

| Özellik | R-Squared olarak değiştirin |
|:--|:--:|
OtoyolErişim       |   -0.042731
ÖğrenciÖğretmen Oranı |   -0.012730
İşMerkeziMesafesi| -0.010491
Vergi Oranı             |   -0.008545
Ortalama Oda Sayısı   |   -0.003949
Suç Oranı           |   -0.003665
Ticari Bölgeler     |   0.002749
HomeAge             |   -0.002426
Yerleşim Bölgeleri    |   -0.002319
Yakın Su           |   0.000203
Nüfusun YüzdesiYoksulluk Altında Yaşayanlar|    0.000031
Toksik Atık Seviyeleri    |   -0.000019

Bu veri seti için en önemli beş özelliği göz önünde bulundurarak, bu model tarafından öngörülen bir evin fiyatı karayollarına yakınlığı, bölgedeki okulların öğrenci öğretmen oranı, büyük istihdam merkezlerine yakınlığı, emlak vergisi oranı ve evde oda ortalama sayısı.
