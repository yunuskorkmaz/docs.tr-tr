---
title: Eğitimli bir modelle tahminlerde bulunun
description: Eğitimli bir modeli kullanarak öngörülerde bulunmayı öğrenin
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 182350cc5143155133385c6fd77986b271f6db91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977039"
---
# <a name="make-predictions-with-a-trained-model"></a>Eğitimli bir modelle tahminlerde bulunun

Öngörülerde bulunmak için eğitilmiş bir modeli nasıl kullanacağınızı öğrenin

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

`Features` Ve `Label` giriş sütun adları gibi, ML.NET bir model tarafından üretilen öngörülen değer sütunları için varsayılan adlara sahiptir. Göreve bağlı olarak ad farklı olabilir.

Bu örnekte kullanılan algoritma doğrusal bir regresyon algoritması olduğundan, çıkış sütununun `Score` varsayılan adı [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) `PredictedPrice` özellikteki öznitelik tarafından tanımlanır.

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a>Tahmin ardışık bir dizi ayar

İster tek bir ister toplu tahmin de bulunun, tahmin ardışık alanının uygulamaya yüklenmesi gerekir. Bu ardışık işlem, hem veri ön işleme dönüşümlerini hem de eğitilmiş modeli içerir. Aşağıdaki kod parçacığı, tahmin ardışık hattını . `model.zip`adlı bir dosyadan yükler.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Tek tahmin

Tek bir tahmin yapmak [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için yüklenen tahmin ardışık hattını kullanarak bir tahmin oluşturun.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Ardından, [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) yöntemi kullanın ve giriş verilerinizi parametre olarak geçirin. [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) Yöntemi kullanarak giriş bir [`IDataView`](xref:Microsoft.ML.IDataView)olması gerekmez dikkat edin). Bunun nedeni, giriş veri türünden bir nesneye geçebilmeniz için giriş veri türü işlemesini uygun şekilde içselleştiren olmasıdır. Ayrıca, `CurrentPrice` yeni veriler kullanarak tahmin etmeye çalıştığınız hedef veya etiket olduğundan, şu anda bunun için bir değer olmadığı varsayılır.

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

Nesnenin özelliğine `Score` `prediction` erişiyorsanız, ''ye `150079`benzer bir değer almalısınız.

## <a name="multiple-predictions"></a>Birden çok tahmin

Aşağıdaki veriler göz önüne alındığında, bir [`IDataView`](xref:Microsoft.ML.IDataView). Bu durumda, adı [`IDataView`](xref:Microsoft.ML.IDataView) . `inputData` Yeni `CurrentPrice` veriler kullanarak tahmin etmeye çalıştığınız hedef veya etiket olduğundan, şu anda bunun bir değeri olmadığı varsayılır.

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

Ardından, veri [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) dönüşümlerini uygulamak ve öngörüler oluşturmak için yöntemi kullanın.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) Yöntemi kullanarak öngörülen değerleri inceleyin.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Puan sütununda öngörülen değerler aşağıdaki gibi görünmelidir:

| Gözlem | Prediction (Tahmin) |
|---|---|
| 1 | 144638.2 |
| 2 | 150079.4 |
| 3 | 107789.8 |
