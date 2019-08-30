---
title: Çapraz doğrulama kullanarak makine öğrenimi modelini eğitme
description: ML.NET içinde daha güçlü makine öğrenimi modelleri oluşturmak için çapraz doğrulamayı nasıl kullanacağınızı öğrenin. Çapraz doğrulama, verileri birkaç bölüme ayıran ve bu bölümlerde birden çok algoritmaya yönelik bir eğitim ve model değerlendirme tekniğidir.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: f29103d0cf59cdec10a641b05ce359bf95c01ccd
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169052"
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

Veriler, gibi `HousingData` bir sınıfa göre modellenebilir ve ' [`IDataView`](xref:Microsoft.ML.IDataView)a yüklenir.

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

Machine Learning modelini derlemek için kullanmadan önce verileri önceden işleyin. Bu örnekte, `Size` ve `HistoricalPrices` sütunları, [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) yöntemi kullanılarak adlı `Features` yeni bir sütuna çıktı olan tek bir özellik vektörü içinde birleştirilir. ML.NET algoritmaları tarafından beklenen biçimde verileri almaya ek olarak sütunları bitiştirme, her ayrı sütun yerine birleştirilmiş sütun için işlemi bir kez uygulayarak işlem hattındaki sonraki işlemleri iyileştirir. 

[`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) Sütunlar tek bir vektörde birleştirildikten sonra, almak `Features` `Size` `HistoricalPrices` için sütuna, 0-1 arasındaki aynı aralığa uygulanır. 

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

Veriler önceden işlendikten sonra modeli eğitmeniz zaman alabilir. İlk olarak, gerçekleştirilecek makine öğrenimi göreviyle en yakından hizalanan algoritmayı seçin. Tahmin edilen değer sayısal bir sürekli değer olduğundan, görev gerileme olur. ML.NET tarafından uygulanan regresyon algoritmalarından biri [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algoritmadır. Çapraz doğrulama ile modeli eğitme [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) yöntemini kullanın. 

> [!NOTE]
> Bu örnek, bir doğrusal regresyon modeli kullansa da, çapraz doğrulama, ML.NET içinde anomali algılama hariç diğer tüm makine öğrenimi görevleri için geçerlidir.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*)Aşağıdaki işlemleri gerçekleştirir:

1. Verileri, `numberOfFolds` parametresinde belirtilen değere eşit sayıda bölüm için bölümler. Her bölümün sonucu bir [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) nesnedir.
1. Bir model, eğitim veri kümesindeki belirtilen makine öğrenimi algoritması tahmin aracı 'ı kullanılarak bölümlerin her birinde eğitilir.
1. Her modelin performansı, test veri kümesindeki [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) yöntemi kullanılarak değerlendirilir. 
1. Modeller, modellerin her biri için, ölçümleriyle birlikte döndürülür.

İçinde `cvResults` depolanan sonuç bir [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesne koleksiyonudur. Bu nesne, hem eğitilen modeli hem de her ikisi de sırasıyla erişilebilir [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) olan ölçümleri ve [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) özellikleri içerir. Bu örnekte, `Model` özelliği türündedir [`ITransformer`](xref:Microsoft.ML.ITransformer) ve `Metrics` özelliği türündedir [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics). 

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Farklı eğitilen modellere yönelik ölçümlere tekil `Metrics` [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) nesnenin özelliği aracılığıyla erişilebilir. Bu durumda, [R-kare ölçüsüne](https://en.wikipedia.org/wiki/Coefficient_of_determination) erişilir ve değişkenine `rSquared`depolanır. 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

`rSquared` Değişkenin içeriğini inceleyebileceğiniz çıktının en iyi şekilde 1 ' e yakın olduğu 0-1 arasında beş değer olmalıdır. R-kare gibi ölçümleri kullanarak en iyi performansa sahip modelleri seçin. Daha sonra, tahmine dayalı hale getirmek veya ek işlemleri gerçekleştirmek için en iyi modeli seçin.

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
