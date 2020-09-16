---
title: Eğitilen bir modelle tahminlere sahip olun
description: Eğitilen bir model kullanarak tahminleri yapmayı öğrenin
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2e8263db289bed50e7437b695134458b8c07e0e5
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679579"
---
# <a name="make-predictions-with-a-trained-model"></a>Eğitilen bir modelle tahminlere sahip olun

Öngörüler yapmak için eğitilen bir model kullanmayı öğrenin

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

`Features`Ve `Label` giriş sütunu adları gibi ml.net, bir model tarafından üretilen tahmin edilen değer sütunlarının varsayılan adlarına sahiptir. Göreve bağlı olarak, ad farklı olabilir.

Bu örnekte kullanılan algoritma bir doğrusal regresyon algoritması olduğundan, çıkış sütununun varsayılan adı, `Score` [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özelliğindeki özniteliği tarafından tanımlanır `PredictedPrice` .

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a>Tahmin işlem hattı ayarlama

Tek veya toplu bir tahmin yapılıp yapılmayacağını belirtir, tahmin işlem hattının uygulamaya yüklenmesi gerekir. Bu işlem hattı hem veri ön işleme dönüştürmelerini hem de eğitilen modeli içerir. Aşağıdaki kod parçacığı, adlı bir dosyadan tahmin işlem hattını yükler `model.zip` .

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Tek tahmin

Tek bir tahmin yapmak için, yüklenmiş tahmin işlem hattını kullanarak bir oluşturun [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) .

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Ardından, yöntemini kullanın [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A) ve giriş verilerinizi parametre olarak geçirin. [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A)Yöntemini kullanmanın girişin bir olması gerekmez [`IDataView`](xref:Microsoft.ML.IDataView) ). Bunun nedeni, girdi veri türünün bir nesnesini geçirebilmeniz için giriş veri türü işlemesini uygun bir şekilde iletmektir. Ayrıca, `CurrentPrice` yeni verileri kullanarak tahmin etmeye çalıştığınız hedef veya etiket olduğundan, bu, şu anda bunun için bir değer olmadığı varsayılır.

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

`Score`Nesnenin özelliğine eriştiğinizde `prediction` Şuna benzer bir değer almalısınız `150079` .

## <a name="multiple-predictions"></a>Birden çok tahmin

Aşağıdaki veriler verildiğinde, ' a yükleyin [`IDataView`](xref:Microsoft.ML.IDataView) . Bu durumda, öğesinin adı [`IDataView`](xref:Microsoft.ML.IDataView) `inputData` . `CurrentPrice`Yeni verileri kullanarak tahmin etmeye çalıştığınız hedef veya etiket olduğundan, bu, şu anda bunun için bir değer olmadığı varsayılır.

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f, 175000f, 210000f }
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

Ardından, [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) veri dönüşümlerini uygulamak ve tahmin oluşturmak için yöntemini kullanın.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Yöntemini kullanarak tahmin edilen değerleri inceleyin [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) .

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Puan sütunundaki tahmin edilen değerler aşağıdaki gibi görünmelidir:

| Kümesinin | Tahmin |
|---|---|
| 1 | 144638,2 |
| 2 | 150079,4 |
| 3 | 107789,8 |
