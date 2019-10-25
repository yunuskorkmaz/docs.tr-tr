---
title: Eğitilen bir modelle tahminlere sahip olun
description: Eğitilen bir model kullanarak tahminleri yapmayı öğrenin
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: f764d2147ec56f8dcc38f96d566ac746cf205650
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799127"
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

### <a name="output-data"></a>Çıkış verileri

`Features` ve `Label` giriş sütunu adları gibi, ML.NET bir model tarafından üretilen tahmin edilen değer sütunlarının varsayılan adlarına sahiptir. Göreve bağlı olarak, ad farklı olabilir.

Bu örnekte kullanılan algoritma bir doğrusal regresyon algoritması olduğundan, çıkış sütununun varsayılan adı, `PredictedPrice` özelliğindeki [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliği tarafından tanımlanan `Score`.

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a>Tahmin işlem hattı ayarlama

Tek veya toplu bir tahmin yapılıp yapılmayacağını belirtir, tahmin işlem hattının uygulamaya yüklenmesi gerekir. Bu işlem hattı hem veri ön işleme dönüştürmelerini hem de eğitilen modeli içerir. Aşağıdaki kod parçacığı, `model.zip`adlı bir dosyadan tahmin ardışık düzenini yükler.

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Tek tahmin

Tek bir tahmin yapmak için, yüklenen tahmin işlem hattını kullanarak bir [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) oluşturun.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Ardından [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) yöntemini kullanın ve giriş verilerinizi parametre olarak geçirin. [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) yönteminin kullanılması, girişin bir [`IDataView`](xref:Microsoft.ML.IDataView)olmasını gerektirmediğine dikkat edin. Bunun nedeni, girdi veri türünün bir nesnesini geçirebilmeniz için giriş veri türü işlemesini uygun bir şekilde iletmektir. Ayrıca, yeni verileri kullanarak tahmin etmeye çalıştığınız hedef veya etiket `CurrentPrice`, bu, şu anda bunun için bir değer olmadığı varsayılır.

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

`prediction` nesnesinin `Score` özelliğine eriştiğinizde `150079`benzer bir değer almalısınız.

## <a name="multiple-predictions"></a>Birden çok tahmin

Aşağıdaki veriler verildiğinde bir [`IDataView`](xref:Microsoft.ML.IDataView)yükleyin. Bu durumda, [`IDataView`](xref:Microsoft.ML.IDataView) adı `inputData`. Yeni verileri kullanarak tahmin etmeye çalıştığınız hedef veya etiket `CurrentPrice`, şu anda bunun için bir değer olmadığı varsayılır.

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

Ardından, veri dönüştürmelerini uygulamak ve tahmin oluşturmak için [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) yöntemini kullanın.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) yöntemi kullanarak tahmin edilen değerleri inceleyin.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Puan sütunundaki tahmin edilen değerler aşağıdaki gibi görünmelidir:

| Kümesinin | Hızlı |
|---|---|
| 1\. | 144638,2 |
| 2 | 150079,4 |
| 3 | 107789,8 |
