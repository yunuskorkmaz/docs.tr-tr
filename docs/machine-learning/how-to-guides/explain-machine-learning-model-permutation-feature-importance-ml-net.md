---
title: PERMÜTASYON özellik önem kullanarak model tahmin açıklayın
description: Modelleri özellik önemini ML.NET özellik önemi permütasyon ile anlama
ms.date: 05/02/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 1037a1f1c21ef2c9b9a87a070a7d2003c1e76eb4
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307366"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a>PERMÜTASYON özellik önem kullanarak model tahmin açıklayın

ML.NET makine tarafından anlama permütasyon özellik önem derecesi (PFI) kullanarak tahmin için katkı özelliklere sahip model tahminlerini öğrenme açıklayacağınızı öğrenin.

Makine öğrenimi modelleri genellikle kara kutular girişleri almak ve bir çıkış oluşturmak zorlayıcı. Çıkış etkileyen özellikler arasındaki etkileşimleri ve Ara adımları nadiren anlaşılabilir. Machine learning gündelik yaşamla sağlık gibi daha fazla yönünü halinde sunulan gibi neden makine modeli yapar kararları öğrenme yaptığını anlamak için dayanıklılığı olur. Örneğin, tanılama machine learning modeli tarafından yapılan, sağlık uzmanları, tanılama yapmak içine giden Etkenler içine aramak için bir yol gerekir. Doğru tanılama sağlamak veya bir Hasta kurtarma içerip içermediğine üzerinde büyük bir fark hale getirebilir. Bu nedenle daha yüksek düzeyde bir modelde explainability, kabul etme veya reddetme model tarafından alınan kararları daha fazla güvenle sağlık uzmanları sahip.

Çeşitli teknikler PFI biri olan modeller, açıklamak için kullanılır. PFI olan ilham almıştır sınıflandırma ve regresyon modellerini açıklamak için kullanılan bir teknik [Breiman'ın *rastgele ormanları* kağıt](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(10 bölümüne bakın). Yüksek bir düzeyde çalıştığını rastgele tüm veri kümesi için bir kerede veri bir özellik karıştırma ve ilgi ne kadar performans ölçümü azaltır hesaplama yoludur. Büyük değişiklik, daha da önemlisi, özelliğidir. 

Ayrıca, en önemli özelliklere vurgulayarak modeli oluşturucular gürültü ve eğitim süresini azaltmak daha anlamlı özelliklerinin bir alt kümesi ile üzerinde odaklanabilirsiniz.

## <a name="load-the-data"></a>Verileri yükleme

Bu örnek için kullanılan veri kümesindeki sütunları 1-12 özellikleridir. Hedef tahmin etmektir `Price`. 

| Sütun | Özellik | Açıklama 
| --- | --- | --- |
| 1\. | CrimeRate | Gdp suç oranı
| 2 | ResidentialZones | Belediye konut bölgelere
| 3 | CommercialZones | Belediye olmayan konut bölgelere
| 4 | NearWater | Su body yakınlık
| 5 | ToxicWasteLevels | Toxicity düzeyleri (PPM)
| 6 | AverageRoomNumber | Şirket içi ilgili odalar ortalama sayısı
| 7 | HomeAge | Giriş yaşı
| 8 | BusinessCenterDistance | En yakın iş bölge uzaklığı
| 9 | HighwayAccess | Otoyollar yakınlığını
| 10 | TaxRate | Özellik Vergi oranı
| 11 | StudentTeacherRatio | Öğretmenler için Öğrenciler oranı
| 12 | PercentPopulationBelowPoverty | Yoksulluğun giderilmesine yaşayan popülasyon yüzdesi
| 13 | Fiyat | Giriş fiyatı

Veri kümesinin bir örnek aşağıda gösterilmiştir:

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

Bu örnek verileri gibi bir sınıf tarafından modellenebilir `HousingPriceData`:

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

Verilerin bir [ `IDataView` ](xref:Microsoft.ML.IDataView).

## <a name="train-the-model"></a>Modeli eğitme

Aşağıdaki kod örneği, ev fiyatlarını tahmin etmek için bir doğrusal regresyon modeli eğitimi işlemi gösterilmektedir.

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>PERMÜTASYON özellik önem derecesi (PFI) modeli açıklanmaktadır

ML.NET kullanımda [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) ilgili göreviniz için yöntemi.

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

Kullanmanın sonucu [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) eğitim veri kümesi üzerinde bir [ `ImmutableArray` ](xref:System.Collections.Immutable.ImmutableArray) , [ `RegressionMetricsStatistics` ](xref:Microsoft.ML.Data.RegressionMetricsStatistics) nesneleri. [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) birden çok gözlemleri için Özet istatistikleri gibi ortalama ve standart sapma sağlar [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics) tarafından belirtilen permütasyon sayısını eşit `permutationCount` parametresi.

Önem derecesi veya bu durumda, R karesi alınmış ölçüm mutlak ortalama azaltma hesaplanan tarafından [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) sonra en önemli en az önemli sıralanabilir.  

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

Her özelliklerinin değerlerini yazdırma `featureImportanceMetrics` altında için benzer bir çıktı üretir. Bu değerleri farklı olduğundan, farklı sonuçlar verildikleri verilere dayalı görmeyi beklemelisiniz aklınızda bulundurun.  

| Özellik | R kare için değiştirin |
|:--|:--:|
HighwayAccess       |   -0.042731
StudentTeacherRatio |   -0.012730
BusinessCenterDistance| -0.010491
TaxRate             |   -0.008545
AverageRoomNumber   |   -0.003949
CrimeRate           |   -0.003665
CommercialZones     |   0.002749
HomeAge             |   -0.002426
ResidentialZones    |   -0.002319
NearWater           |   0.000203
PercentPopulationLivingBelowPoverty|    0.000031
ToxicWasteLevels    |   -0.000019

Bu veri kümesi için en önemli beş özelliklere göz alma, bu modeli tarafından tahmin edilen bir ev fiyatı etkiler, yakınlık Otoyollar, okullar alanında Öğrenci ve Öğretmen oranı, yakınlık için ana çalışan merkezleri özelliği Vergi oranı ve Giriş odalarında ortalama sayısı.
