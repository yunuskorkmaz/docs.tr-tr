---
title: Modeli yeniden eğitme
description: ML.NET içinde bir modeli yeniden eğitme hakkında bilgi edinin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 1c891ad1d5b4c1160ca41c43eff6eea444f7224f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545005"
---
# <a name="re-train-a-model"></a>Modeli yeniden eğitme

ML.NET ' de makine öğrenimi modelini yeniden eğitme hakkında bilgi edinin.

Dünya ve çevresindeki veriler sabit bir hızda değişir. Bu nedenle, modellerin de değiştirilmesi ve güncelleştirilmesi gerekir. ML.NET, bir başlangıç noktası olarak öğrenilmiş model parametrelerini kullanan yeniden eğitim modellerine, her seferinde sıfırdan başlamak yerine, bir önceki deneyime sürekli olarak derleme yapmak için işlevsellik sağlar.

Aşağıdaki algoritmalar ML.NET içinde yeniden eğitiliyor:

- [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [LbfgsLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [Lbfgsmaximumentropybirden çok Lasstrainer](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [Lbfgspoissongerilesiontrainer](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [Doğrsvmtrainer](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [Onlinegradientharfin Ttrainer](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [Sgddtu Oytedtrainer](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [Sgdnondtu ırtedtrainer](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [SymbolicSgdLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a>Önceden eğitilen modeli yükle

İlk olarak, önceden eğitilen modeli uygulamanıza yükleyin. Eğitim işlem hatlarını ve modellerini yükleme hakkında daha fazla bilgi edinmek için bkz. [eğitilen modeli kaydetme ve yükleme](save-load-machine-learning-models-ml-net.md).

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

## <a name="extract-pre-trained-model-parameters"></a>Önceden eğitilen model parametrelerini Ayıkla

Model yüklendikten sonra, [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) önceden eğitilen modelin özelliğine erişerek öğrenilen model parametrelerini ayıklayın. Önceden eğitilen model, [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) Bu çıktıları oluşturan doğrusal regresyon modeli kullanılarak eğitildi [`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) . Bu doğrusal regresyon modeli parametreleri, modelin öğrenilen sapma ve ağırlıklarını veya katsayılarını içerir. Bu değerler, yeni yeniden eğitilen model için bir başlangıç noktası olarak kullanılacaktır.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Modeli yeniden eğitme

Modeli yeniden eğitime işlemi, bir modelin eğitiminden farklı değildir. Tek fark, [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) verilerin yanı sıra özgün öğrenilen model parametrelerini giriş olarak da alır ve bunları yeniden eğitim sürecinde bir başlangıç noktası olarak kullanır.

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

## <a name="compare-model-parameters"></a>Model parametrelerini Karşılaştır

Yeniden eğitimin gerçekten gerçekleştiğini nasıl anlarsınız? Bir yol, yeniden eğitilen model parametrelerinin orijinal modelden farklı olup olmadığını karşılaştırmak olacaktır. Aşağıdaki kod örneği, orijinali yeniden eğitilen model ağırlıklarına karşı karşılaştırır ve bunları konsola çıkarır.

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

Aşağıdaki tabloda çıktının nasıl görünebileceğini gösterilmektedir.

|Özgün | Eğitilebileceği | Fark |
|---|---|---|
| 33039,86 | 56293,76 | -23253,9 |
| 29099,14 | 49586,03 | -20486,89 |
| 28938,38 | 48609,23 | -19670,85 |
| 30484,02 | 53745,43 | -23261,41 |
