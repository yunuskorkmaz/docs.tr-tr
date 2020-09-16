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
# <a name="train-a-machine-learning-model-using-cross-validation"></a>Çapraz doğrulama kullanarak makine öğrenimi modelini eğitme

ML.NET içinde daha güçlü makine öğrenimi modelleri eğitmek için çapraz doğrulamayı nasıl kullanacağınızı öğrenin.

Çapraz doğrulama, verileri birkaç bölüme ayıran ve bu bölümlerde birden çok algoritmaya yönelik bir eğitim ve model değerlendirme tekniğidir. Bu teknik eğitim sürecinde veri tutarak modelin sağlamlığını geliştirir. Veri kısıtlı ortamlarda, görünmeyen gözlemlerdeki performansı iyileştirmeye ek olarak, daha küçük bir veri kümesiyle eğitim modelleri için etkili bir araç olabilir.

## <a name="the-data-and-data-model"></a>Veri ve veri modeli

Aşağıdaki biçime sahip bir dosyadan verilen veriler:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Veriler, gibi bir sınıfa göre modellenebilir `HousingData` ve ' a yüklenir [`IDataView`](xref:Microsoft.ML.IDataView) .

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

Machine Learning modelini derlemek için kullanmadan önce verileri önceden işleyin. Bu örnekte, `Size` ve sütunları, `HistoricalPrices` yöntemi kullanılarak adlı yeni bir sütuna çıktı olan tek bir özellik vektörü içinde birleştirilir `Features` [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) . ML.NET algoritmaları tarafından beklenen biçimde verileri almaya ek olarak sütunları bitiştirme, her ayrı sütun yerine birleştirilmiş sütun için işlemi bir kez uygulayarak işlem hattındaki sonraki işlemleri iyileştirir.

Sütunlar tek bir vektörde birleştirildikten sonra, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) `Features` almak için sütuna, `Size` `HistoricalPrices` 0-1 arasındaki aynı aralığa uygulanır.

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

## <a name="train-model-with-cross-validation"></a>Çapraz doğrulama ile modeli eğitme

Veriler önceden işlendikten sonra modeli eğitmeniz zaman alabilir. İlk olarak, gerçekleştirilecek makine öğrenimi göreviyle en yakından hizalanan algoritmayı seçin. Tahmin edilen değer sayısal bir sürekli değer olduğundan, görev gerileme olur. ML.NET tarafından uygulanan regresyon algoritmalarından biri [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algoritmadır. Çapraz doğrulama ile modeli eğitme [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate%2A) yöntemini kullanın.

> [!NOTE]
> Bu örnek, bir doğrusal regresyon modeli kullansa da, çapraz doğrulama, ML.NET içinde anomali algılama hariç diğer tüm makine öğrenimi görevleri için geçerlidir.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate%2A) Aşağıdaki işlemleri gerçekleştirir:

1. Verileri, parametresinde belirtilen değere eşit sayıda bölüm için bölümler `numberOfFolds` . Her bölümün sonucu bir [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) nesnedir.
1. Bir model, eğitim veri kümesindeki belirtilen makine öğrenimi algoritması tahmin aracı 'ı kullanılarak bölümlerin her birinde eğitilir.
1. Her modelin performansı, [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) test veri kümesindeki yöntemi kullanılarak değerlendirilir.
1. Modeller, modellerin her biri için, ölçümleriyle birlikte döndürülür.

İçinde depolanan sonuç `cvResults` bir [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesne koleksiyonudur. Bu nesne, hem eğitilen modeli hem de her ikisi de sırasıyla erişilebilir olan ölçümleri [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) ve [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) özellikleri içerir. Bu örnekte, `Model` özelliği türündedir [`ITransformer`](xref:Microsoft.ML.ITransformer) ve `Metrics` özelliği türündedir [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) .

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Farklı eğitilen modellere yönelik ölçümlere `Metrics` tekil nesnenin özelliği aracılığıyla erişilebilir [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) . Bu durumda, [R-kare ölçüsüne](https://en.wikipedia.org/wiki/Coefficient_of_determination) erişilir ve değişkenine depolanır `rSquared` .

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

`rSquared`Değişkenin içeriğini inceleyebileceğiniz çıktının en iyi şekilde 1 ' e yakın olduğu 0-1 arasında beş değer olmalıdır. R-kare gibi ölçümleri kullanarak en iyi performansa sahip modelleri seçin. Daha sonra, tahmine dayalı hale getirmek veya ek işlemleri gerçekleştirmek için en iyi modeli seçin.

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
