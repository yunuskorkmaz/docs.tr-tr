---
title: Eğitilen bir modelin ile tahminlerde
description: Eğitilen bir modeli kullanarak tahmin yapmayı öğrenin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: dac3b3bfa68776975a2e5e762f46db16e39d61fb
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066177"
---
# <a name="make-predictions-with-a-trained-model"></a>Eğitilen bir modelin ile tahminlerde

Eğitilen bir modelin tahminlerde bulunmak üzere kullanmayı öğrenin

## <a name="create-data-models"></a>Veri modelleri oluşturma

### <a name="input-data"></a>Giriş verileri

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

### <a name="output-data"></a>Çıktı verileri

Gibi `Features` ve `Label` giriş sütun adları, ML.NET modeli tarafından üretilen tahmin edilen değer sütunlar için varsayılan adları vardır. Göreve bağlı olarak, ad farklı olabilir.

Bu örnekte kullanılan algoritmayı doğrusal regresyon algoritması çıkış sütununun varsayılan adı olduğu `Score` tarafından tanımlanan [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliği `PredictedPrice` özelliği.

```csharp
class HousingPrediction : HousingData
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

`HousingPrediction` Veri modeli devraldığı `HousingData` özgün görselleştirmek kolay hale getirmek için veri modeli tarafından oluşturulan çıktı yanı sıra giriş.  

## <a name="set-up-a-prediction-pipeline"></a>Bir öngörü işlem hattı ayarlayın

Olup yapmadan tek veya toplu tahmin, tahmin işlem hattı uygulamasına yüklü olması gerekir. Bu işlem hattı, hem veri ön işleme dönüşümleri, hem de eğitim modeli içerir. Aşağıdaki kod parçacığında tahmin işlem hattı adlı bir dosyadan yükler `model.zip`.

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Tek tahmin

Tek bir tahminde bulunmak için oluşturun bir [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) yüklenen tahmin işlem hattını kullanma.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Ardından, [ `Predict` ](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) yöntemi ve verilerinizi giriş parametresi olarak geçirin. Bu kullanırken olduğunu [ `Predict` ](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) yöntemi giriş olmasını gerekli olmadığı bir [ `IDataView` ](xref:Microsoft.ML.IDataView)). Giriş veri türü bir nesne geçirdiğiniz şekilde bunu rahatça giriş veri türü işleme internalizes olmasıdır. Ayrıca, bu yana `CurrentPrice` hedef veya yeni verileri kullanarak tahmin etmek çalıştığınız etiket şu anda hiçbir değerini olduğu varsayılır.

```csharp
// Input Data
HousingData inputData = new HousingData
{
    Size = 900f,
    HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
};

// Get Prediction
HousingPrediction prediction = predictionEngine.Predict(inputData);
```

Erişirseniz `Score` özelliği `prediction` nesne almanız gerekir bir değer benzer `150079`.

## <a name="batch-prediction"></a>Batch tahmin

Aşağıdaki veriler göz önünde bulundurulduğunda, içine yüklemek bir [ `IDataView` ](xref:Microsoft.ML.IDataView). Çünkü `CurrentPrice` hedef veya yeni verileri kullanarak tahmin etmek çalıştığınız etiket şu anda hiçbir değerini olduğu varsayılır.

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f }
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f }
    }
};
```

Ardından, [ `Transform` ](xref:Microsoft.ML.ITransformer.Transform*) veri dönüşümleri uygulayın ve tahminler üretmek için yöntemi.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Tahmin edilen değerleri kullanarak inceleyin. [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) yöntemi.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Tahmin edilen puan sütundaki değerleri aşağıdaki gibi görünmelidir:

| Gözlem | Tahmin |
|---|---|
| 1. | 144638.2 |
| 2 | 150079.4 |
| 3 | 107789.8 |
