---
title: Modeli yeniden eğitme
description: ML.NET'da bir modeli nasıl yeniden eğitin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 735782a4a0877a917b6e1885f009aa49d834170f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976959"
---
# <a name="re-train-a-model"></a>Modeli yeniden eğitme

ML.NET'da bir makine öğrenimi modelini nasıl yeniden eğitin.

Dünya ve etrafındaki veriler sabit bir hızla değişir. Bu nedenle, modellerin de değişmesi ve güncellendirilmesi gerekir. ML.NET, öğrenilen model parametrelerini kullanarak modelleri her seferinde sıfırdan başlamak yerine sürekli olarak önceki deneyimleri temel almak için bir başlangıç noktası olarak yeniden eğitme işlevleri sağlar.

Aşağıdaki algoritmalar ML.NET yeniden eğitilebilir:

- [OrtalamaPerceptronEğitmen](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [LbfgsLojistikRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [LbfgsMaximumEntropyMulticlassTrainer](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [LbfgsPoissonRegressionEğitmen](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [LinearSvmTrainer](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [SgdCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [SgdNonCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [SembolikSgdLojistikRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a>Önceden eğitilmiş modeli yükleyin

İlk olarak, önceden eğitilmiş modeli uygulamanıza yükleyin. Eğitim boru hatlarını ve modellerini yükleme hakkında daha fazla bilgi edinmek [için, eğitilen bir modeli kaydet ve yükleyin'](save-load-machine-learning-models-ml-net.md)e bakın.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a>Önceden eğitilmiş model parametrelerini ayıklayın

Model yüklendikten sonra, önceden eğitilmiş modelin [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) özelliğine erişerek öğrenilen model parametrelerini ayıklayın. Önceden eğitilmiş model bir [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) [`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) oluşturur doğrusal regresyon modeli kullanılarak [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters)eğitildi. Bu doğrusal regresyon modeli parametreleri, modelin öğrenilen önyargıve ağırlıklarını veya katsayıları içerir. Bu değerler, yeni yeniden eğitilmiş model için bir başlangıç noktası olarak kullanılacaktır.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Yeniden eğitim modeli

Bir modeli yeniden eğitme süreci, bir modeli eğitmekten farklı değildir. Tek fark, veri [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) ek olarak yöntem de giriş orijinal öğrenilen model parametreleri olarak alır ve yeniden eğitim sürecinde bir başlangıç noktası olarak kullanır.

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

## <a name="compare-model-parameters"></a>Model parametrelerini karşılaştırın

Yeniden eğitimin gerçekten olup olmadığını nasıl anlarsın? Yeniden eğitilen modelin parametrelerinin orijinal modelden farklı olup olmadığını karşılaştırmanın bir yolu da bu olabilir. Aşağıdaki kod örneği orijinali yeniden eğitilmiş model ağırlıklarıyla karşılaştırır ve bunları konsola çıkar.

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

Aşağıdaki tablo, çıktının nasıl görünebileceğini gösterir.

|Özgün | Yeniden eğitildi | Fark |
|---|---|---|
| 33039.86 | 56293.76 | -23253.9 |
| 29099.14 | 49586.03 | -20486.89 |
| 28938.38 | 48609.23 | -19670.85 |
| 30484.02 | 53745.43 | -23261.41 |
