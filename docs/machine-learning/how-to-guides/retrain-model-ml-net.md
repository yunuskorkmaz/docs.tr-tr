---
title: Modeli yeniden eğitme
description: Bilgi ML.NET modelinde nasıl yeniden eğitme
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2f8f8c035166612aabede8a512485bdf296c5655
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557912"
---
# <a name="re-train-a-model"></a>Modeli yeniden eğitme

Bir machine learning modeli ML.NET olarak yeniden eğitme hakkında bilgi edinin.

Dünya ve verileri çevresinde sabit bir hızda değiştirin. Bu nedenle, modelleri değiştirmek ve güncelleştirmeniz gerekir. ML.NET işlevselliğini kullanarak yeniden eğitim modelleri için sürekli olarak önceki deneyime yerine her zaman sıfırdan oluşturmak için bir başlangıç noktası olarak model parametreleri öğrendiniz sağlar.  

Aşağıdaki algoritmaları ML.NET içinde yeniden trainable şunlardır:

- [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [LbfgsLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [LbfgsMaximumEntropyMulticlassTrainer](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [LbfgsPoissonRegressionTrainer](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [LinearSvmTrainer](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [SgdCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [SgdNonCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [SymbolicSgdLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a>Önceden eğitilmiş model yükle

İlk olarak, önceden eğitilmiş modelin uygulamanıza yükleyin. Yükleme eğitim işlem hatlarını ve modelleri hakkında daha fazla bilgi için bkz ilgili [nasıl yapılır makalesi](./consuming-model-ml-net.md).

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data prepration pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a>Önceden eğitilmiş model parametreleri Ayıkla

Modele yüklendiğinde erişerek öğrenilen model parametreleri Ayıkla [ `Model` ](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) önceden eğitilmiş modelin özelliği. Önceden eğitilmiş model doğrusal regresyon modeli kullanılarak eğitilmiş [ `OnlineGradientDescentTrainer` ](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) oluşturan bir[ `RegressionPredictionTransformer` ](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) , çıkarır [ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters). Bu doğrusal regresyon modeli parametreleri öğrenilen sapması ve ağırlıklarını veya modelin katsayılarını içerir. Bu değerler, yeni yeniden eğitim modeli için bir başlangıç noktası olarak kullanılır.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters = 
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Modeli yeniden eğitme

Bir modeli yeniden eğitme işlemi farklı bir model Eğitimi, değildir. Tek fark, [ `Fit` ](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) verilerin yanı sıra yöntemi de alır giriş özgün öğrenilen model parametreleri ve yeniden eğitim işlemde olarak başlangıç noktası kullanır.  

```csharp
// New Data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};

//Load New Data
IDataView newData = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Preprocess Data
IDataView transformedNewData = dataPrepPipeline.Transform(newData);

// Retrain model
RegressionPredictionTransformer<LinearRegressionModelParameters> retrainedModel = 
    mlContext.Regression.Trainers.OnlineGradientDescent()
        .Fit(transformedNewData, originalModelParameters);
```

## <a name="compare-model-parameters"></a>Model parametreleri karşılaştırın

Eğitim yeniden gerçekten oldu, nasıl bilebilirsiniz? Bir yolu, yeniden eğitilen modelin parametreleri özgün modeli farklı olup olmadığını Karşılaştırılacak olacaktır. Aşağıdaki kod örneği, orijinal yeniden eğitilen model ağırlıkları karşı karşılaştırır ve bunları konsola çıkarır.

```csharp
// Extract Model Parameters of re-trained model
LinearRegressionModelParameters retrainedModelParameters = retrainedModel.Model as LinearRegressionModelParameters;

// Inspect Change in Weights
var weightDiffs = 
    originalModelParameters.Weights.Zip(
        retrainedModelParameters.Weights, (original, retrained) => original - retrained).ToArray();

Console.WriteLine("Original | Retrained | Difference");
for(int i=0;i < weightDiffs.Count();i++)
{
    Console.WriteLine($"{originalModelParameters.Weights[i]} | {retrainedModelParameters.Weights[i]} | {weightDiffs[i]}");
}
```

Aşağıdaki tabloda, çıktı aşağıdaki gibi görünmelidir gösterir. 

|Özgün | Retrained | Fark |
|---|---|---|
| 33039.86 | 56293.76 | -23253.9 |
| 29099.14 | 49586.03 | -20486.89 |
| 28938.38 | 48609.23 | -19670.85 |
| 30484.02 | 53745.43 | -23261.41 |
