---
title: Eğitme ve değerlendirme çapraz doğrulama kullanarak makine öğrenme modeli
description: Eğitme ve değerlendirme çapraz doğrulama kullanarak makine öğrenme modeli hakkında bilgi edinin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: a15dfbfcd563cf9df9c25779a5854a9f556523d1
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066165"
---
# <a name="train-and-evaluate-a-machine-learning-model-using-cross-validation"></a>Eğitme ve değerlendirme çapraz doğrulama kullanarak makine öğrenme modeli

Çapraz doğrulama ML.NET daha güçlü makine öğrenimi modelleri oluşturmak için kullanmayı öğrenin. 

Çapraz doğrulama, eğitim ve veriler çeşitli bölümlere ayırır ve bu bölümler birden çok algoritmalarına eğitir model değerlendirme teknik ' dir. Bu teknik, eğitim işlem verileri tutarak modelinin sağlamlık artırır. Görünmeyen gözlemler performans iyileştirme yanı sıra veri kısıtlı ortamlarında, daha küçük bir veri kümesiyle eğitim modelleri için etkili bir aracı olabilir.

## <a name="the-data-and-data-model"></a>Veri ve veri modeli

Belirtilen bir dosyadan veri, aşağıdaki biçime sahiptir:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Verileri gibi bir sınıf tarafından modellenebilir `HousingData`:

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

İçinde verilerin bir [ `IDataView` ](xref:Microsoft.ML.IDataView).

## <a name="prepare-the-data"></a>Verileri hazırlama

Veri machine learning modeli oluşturmak üzere kullanmadan önce önceden işler. Bu örnekte `Size` ve `HistoricalPrices` sütunları adlı yeni bir sütun için çıkış tek özellik vektör içine birleştirilir `Features` kullanarak [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) yöntemi. ML.NET algoritmalarda beklenen biçime veri alma yanı sıra sütunlarını ardışık düzende sonraki işlemleri her ayrı sütun yerine birleştirilmiş sütun için bir kez işlemi uygulayarak en iyi duruma getirir. 

Sütunları tek bir vektörü birleştirilir sonra [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) uygulanan `Features` almak için sütun `Size` ve `HistoricalPrices` aynı 0-1 aralığında. 

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

## <a name="train-model-with-cross-validation"></a>Çapraz doğrulama modeli eğitme

Önceden işlenmiş hesaplandıktan sonra modeli eğitmek için zaman gelir. İlk olarak, en yakın olan makine öğrenme gerçekleştirilecek görevi uygun algoritmayı seçin. Tahmin edilen değer sayısal sürekli bir değeri olduğundan, regresyon görevdir. ML.NET tarafından uygulanan regresyon algoritmalarından biri olan [ `StochasticDualCoordinateAscentCoordinator` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algoritması. Çapraz doğrulama kullanımı modeli eğitmek için [ `CrossValidate` ](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) yöntemi. 

> [!NOTE]
> Bu örnek bir doğrusal regresyon modeli kullansa da, CrossValidate Anomali algılama hariç ML.NET görevlerinde öğrenme tüm makine için geçerlidir.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) aşağıdaki işlemleri gerçekleştirir:

1. Belirli bölümleri içinde belirtilen değere eşit sayıda veriyi bölümler `numberOfFolds` parametresi. Her bölüm sonucu bir [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) nesne.
1. Belirtilen makine öğrenimi algoritma estimator eğitim veri kümesi üzerinde kullanarak bölümlerin her bir modeli eğitilir.
1. Her modelin performans kullanarak değerlendirilir [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) sınama veri kümesi üzerinde yöntemi. 
1. Model, ölçümlerle birlikte modellerinin her biri için döndürülür.

Sonuç depolanan `cvResults` koleksiyonudur [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1) nesneleri. Bu nesne eğitilen model yanı sıra erişilebilir her iki formu olan ölçümler içerir [ `Model` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Model) ve [ `Metrics` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Metrics) özellikleri sırasıyla. Bu örnekte `Model` özelliği türüdür [ `ITransformer` ](xref:Microsoft.ML.ITransformer) ve `Metrics` özelliği türüdür [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics). 

## <a name="extract-metrics"></a>Ölçümleri ayıklayın

Ölçümleri farklı eğitilen modelleri için üzerinden erişilebilir `Metrics` kişinin özelliği [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesne. Bu durumda, [R karesi alınmış ölçüm](https://en.wikipedia.org/wiki/Coefficient_of_determination) erişilen ve değişkeninde depolanan `rSquared`. 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

İçeriğini incelemek, `rSquared` değişken çıktısı beş değerleri 0-1'den daha yakın yerlerde 1 arasında en iyi anlamına gelir olmalıdır.

## <a name="select-the-best-performing-model"></a>En iyi performansa sahip model seçin

R kare seçme gibi ölçümleri kötü gerçekleştirmek için en iyi modellerinden kullanma. Ardından, tahminlerde veya ile ek işlemleri gerçekleştirmek için en iyi modeli seçin.

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
