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
# <a name="train-a-machine-learning-model-using-cross-validation"></a>Çapraz doğrulama yı kullanarak bir makine öğrenme modeli eğitin

ML.NET daha sağlam makine öğrenimi modellerini eğitmek için çapraz doğrulamayı nasıl kullanacağınızı öğrenin.

Çapraz doğrulama, verileri birkaç bölüme bölen ve bu bölümlerde birden çok algoritma eğiten bir eğitim ve model değerlendirme tekniğidir. Bu teknik, eğitim sürecinden verileri tutarak modelin sağlamlığını artırır. Görünmeyen gözlemlerde performansı artırmanın yanı sıra, veri kısıtlamalı ortamlarda daha küçük bir veri kümesine sahip modelleri eğitmek için etkili bir araç olabilir.

## <a name="the-data-and-data-model"></a>Veri ve veri modeli

Aşağıdaki biçime sahip bir dosyadan alınan veriler verilir:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Veriler gibi `HousingData` bir sınıf tarafından modellenebilir ve [`IDataView`](xref:Microsoft.ML.IDataView)bir .

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

## <a name="prepare-the-data"></a>Verileri hazırlama

Makine öğrenme modelini oluşturmak için kullanmadan önce verileri önceden işleme. Bu örnekte, `Size` `HistoricalPrices` ve sütunlar tek bir özellik vektörü içinde birleştirilir [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) ve bu da yöntem kullanılarak adlandırılan `Features` yeni bir sütuna çıkarılır. ML.NET algoritmaları tarafından beklenen biçime veri almanın yanı sıra, sütunları birleştirme, ayrı sütunların her biri yerine bir kez işlem uygulayarak ardışık ardışık sonraki işlemleri en iyi duruma getirmektedir.

Sütunlar tek bir vektörde [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) birleştirildiğinde, `Features` 0-1 `Size` `HistoricalPrices` arasında ve aynı aralıkta almak için sütuna uygulanır.

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

## <a name="train-model-with-cross-validation"></a>Çapraz doğrulamalı tren modeli

Veriler önceden işlendikten sonra, modeli eğitmenin zamanı gelmiştir. İlk olarak, gerçekleştirilecek makine öğrenme göreviyle en yakın hizalayan algoritmayı seçin. Öngörülen değer sayısal olarak sürekli bir değer olduğundan, görev gerilemedir. ML.NET tarafından uygulanan regresyon algoritmalarından [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) biri de algoritmadır. Çapraz doğrulama ile modeli eğitmek için [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) yöntemi kullanın.

> [!NOTE]
> Bu örnek doğrusal bir regresyon modeli kullansa da, CrossValidate Anomaly Detection hariç ML.NET diğer tüm makine öğrenimi görevleri için geçerlidir.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*)aşağıdaki işlemleri gerçekleştirir:

1. Verileri `numberOfFolds` parametrede belirtilen değere eşit bir dizi bölüme ayırır. Her bölümün sonucu bir [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) nesnedir.
1. Bir model, eğitim veri kümesinde belirtilen makine öğrenme algoritması tahmincisi kullanılarak bölümlerin her biri üzerinde eğitilir.
1. Her modelin performansı test veri [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) kümesindeki yöntem kullanılarak değerlendirilir.
1. Model, ölçümleri ile birlikte her model için döndürülür.

Depolanan sonuç `cvResults` [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesnelerin bir koleksiyondur. Bu nesne, hem erişilebilir form [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) hem [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) de özellikleri sırasıyla, eğitimli modeli yanı sıra ölçümleri içerir. Bu örnekte, `Model` özellik türünde [`ITransformer`](xref:Microsoft.ML.ITransformer) `Metrics` ve özellik [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics)türündedir.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Farklı eğitilmiş modeller için ölçümlertek bir `Metrics` [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesnenin özelliği üzerinden erişilebilir. Bu durumda, [R-Squared metrik](https://en.wikipedia.org/wiki/Coefficient_of_determination) erişilir ve değişkende `rSquared`saklanır.

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

`rSquared` Değişkenin içeriğini incelerseniz, çıktı 0-1 arasında değişen beş değer olmalıdır ve 1'e yakın olmak en iyi anlamına gelir. R-Squared gibi ölçümleri kullanarak, modelleri en iyiden en kötü performansa doğru seçin. Ardından, öngörülerde bulunmak veya ek işlemler gerçekleştirmek için en üst modeli seçin.

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
