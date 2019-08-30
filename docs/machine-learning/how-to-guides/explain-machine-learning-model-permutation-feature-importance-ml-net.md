---
title: Permütasyon özelliği önem derecesi kullanarak model tahminlerini açıklayın
description: ML.NET içinde permütasyon özelliği önem derecesine sahip modellerin Özellik önemini anlayın
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 9617582c79b2278e3a68e7acf84568247b81eca1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167653"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a>Permütasyon özelliği önem derecesi kullanarak model tahminlerini açıklayın

ML.NET makine öğrenme modeli tahminlerini, katkı özelliklerinin permütasyon özelliğinin önem derecesini (PFı) kullanarak tahmin etmek zorunda olduğunu anlayarak nasıl açıklacağınızı öğrenin.

Makine öğrenimi modelleri genellikle giriş ve çıkış oluşturan siyah kutular olarak düşünülebilir. Çıktıyı etkileyen özellikler arasındaki ara adımlar veya etkileşimler nadiren anlaşılmıştır. Makine öğrenimi, sağlık hizmetleri gibi günlük hayatın daha belirgin yönlerine tanıtıldığında, Machine Learning modelinin neden yaptığı kararları nasıl yaptığını anlamak en önemli öneme sahiptir. Örneğin, bir makine öğrenimi modeliyle tanılar yapılırsa, sağlık uzmanlarının, bu, bu, tanılar haline gelen faktörleri bulmak için bir yol gerekir. Doğru tanısı sağlamak, hasta 'ın hızlı bir şekilde kurtarma yapıp yapmayacağı konusunda harika bir farklılık yapabilir. Bu nedenle, bir modeldeki explainability düzeyi arttıkça, daha yüksek güvenilirlikli sağlık uzmanlarının model tarafından yapılan kararları kabul etmesi veya reddetmesi gerekir.

Farklı teknikler, bunlardan biri PFI olan modelleri açıklamak için kullanılır. PFı, [Breiman 'Nın *rastgele orman* kağıdı](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)tarafından ilham olan sınıflandırma ve regresyon modellerini açıklamak için kullanılan bir tekniktir (bkz. Bölüm 10). Yüksek düzeyde, çalışma şekli, veri kümesinin tamamı için bir seferde bir özelliği rastgele karıştırarak ve ilgi çekici performans ölçüsünün ne kadarının azaldığından hesaplama. Değişiklik ne kadar büyükse, bu özellik o kadar önemli olur. 

Ayrıca, en önemli özellikleri vurgulayarak model oluşturucular, gürültü ve eğitim süresini azaltan daha anlamlı özelliklerin bir alt kümesini kullanmaya odaklanabilir.

## <a name="load-the-data"></a>Verileri yükleme

Bu örnek için kullanılan veri kümesindeki Özellikler 1-12 sütunlarında bulunur. Amaç tahmin `Price`etmek için tasarlanmıştır. 

| Sütun | Özellik | Açıklama 
| --- | --- | --- |
| 1\. | Crimerde | GDP suta hızı başına
| 2 | ResidentialZones | Kasadaki mesken bölgeleri
| 3 | Ticari bölgeler | Kasadaki yöresel olmayan bölgeler
| 4 | Yaklaştığında su | Su gövdesine yakınlık
| 5 | ToxicWasteLevels | Toxicity düzeyleri (PPM)
| 6 | AverageRoomNumber | Evin ortalama oda sayısı
| 7 | HomeAge | Evin yaşı
| 8 | BusinessCenterDistance | En yakın iş bölgesi uzaklığı
| 9 | HighwayAccess | Üst yöntemlere yakınlık
| 10 | Vergilenrate | Özellik vergi oranı
| 11 | StudentTeacherRatio | Öğrencilerin öğretmenler için oranı
| 12 | PercentPopulationBelowPoverty | Poverty 'in altında yaşayan popülasyon yüzdesi
| 13 | Fiyat | Giriş fiyatı

Veri kümesinin bir örneği aşağıda gösterilmiştir:

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

Bu örnekteki veriler, gibi `HousingPriceData` bir sınıf tarafından modellenebilir ve ' [`IDataView`](xref:Microsoft.ML.IDataView)a yüklenmiş olabilir.

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

Aşağıdaki kod örneği, ev fiyatlarını tahmin etmek için bir doğrusal regresyon modeli eğitimi sürecini gösterir.

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>Modeli permütasyon özelliği önem derecesi (PFı) ile açıklayın

ML.NET içinde ilgili göreviniz [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) için yöntemini kullanın.

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

Eğitim veri kümesinde kullanmanın [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) sonucu [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) bir [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) nesnedir. [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)parametresi tarafından belirtilen permütasyon sayısına eşit olan [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) birden çok gözlemde için Ortalama ve standart sapma gibi özet istatistikler sağlar. `permutationCount`

Önem derecesi veya bu durumda, tarafından [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) hesaplanan R-kare ölçümünde mutlak ortalama azalma, daha sonra en önemli olan en az önemli olarak sıralanır.  

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

İçindeki `featureImportanceMetrics` her bir özelliğin değerlerini yazdırmak, aşağıdakine benzer bir çıktı üretir. Bu değerler verilen verilere göre farklılık gösterdiğinden, farklı sonuçlar görmeyi beklemeniz gerektiğini aklınızda bulundurun.  

| Özellik | R-kare olarak değiştir |
|:--|:--:|
HighwayAccess       |   -0,042731
StudentTeacherRatio |   -0,012730
BusinessCenterDistance| -0,010491
Vergilenrate             |   -0,008545
AverageRoomNumber   |   -0,003949
Crimerde           |   -0,003665
Ticari bölgeler     |   0,002749
HomeAge             |   -0,002426
ResidentialZones    |   -0,002319
Yaklaştığında su           |   0,000203
PercentPopulationLivingBelowPoverty|    0,000031
ToxicWasteLevels    |   -0,000019

Bu veri kümesi için en önemli beş özelliğe göz atmak için, bu model tarafından tahmin edilen bir evin fiyatı, bir yakınlık, alanda okulların öğrencisi oranı, önemli iş merkezlerine yakınlık, özellik vergi oranı ve giriş alanındaki ortalama oda sayısı.
