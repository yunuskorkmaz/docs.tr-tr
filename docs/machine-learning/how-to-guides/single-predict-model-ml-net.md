---
title: Bir zaman - ML.NET bir tahminde bulunmak için PredictionFunction kullanın
description: ML.NET PredictionFunction aynı anda bir tahminde bulunmak için kullanmayı öğrenin
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 9e34c1357e5ac241abd628289cd694bcd6b9cbb1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131587"
---
# <a name="use-the-predictionfunction-to-make-one-prediction-at-a-time---mlnet"></a><span data-ttu-id="738f7-103">Bir zaman - ML.NET bir tahminde bulunmak için PredictionFunction kullanın</span><span class="sxs-lookup"><span data-stu-id="738f7-103">Use the PredictionFunction to make one prediction at a time - ML.NET</span></span> 

<span data-ttu-id="738f7-104">Herhangi bir ML.NET modeli bir dönüştürücü olduğundan, kullandığınız `model.Transform` modele uygulamak `DataView` tahminler gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="738f7-104">Since any ML.NET model is a transformer, you use `model.Transform` to apply the model to the `DataView` to make predictions.</span></span> 

<span data-ttu-id="738f7-105">'Üzerinde tahmin etmek istediğiniz, ancak bunun yerine bir örnek aynı anda almaya herhangi bir veri kümesi' olduğunda daha tipik bir durumda, yine de olur.</span><span class="sxs-lookup"><span data-stu-id="738f7-105">A more typical case, though, is when there is no 'dataset' that you want to predict on, but instead you receive one example at a time.</span></span> <span data-ttu-id="738f7-106">Örneğin, model ASP.NET Web sitenizi bir parçası olarak çalıştırmak ve gelen HTTP isteği için bir tahminde bulunmak ihtiyacınız.</span><span class="sxs-lookup"><span data-stu-id="738f7-106">For instance, you run the model as part of your ASP.NET website, and need to make a prediction for an incoming HTTP request.</span></span>

<span data-ttu-id="738f7-107">`PredictionFunction` Tahmin işlem hattı üzerinden bir seferde bir örnek çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="738f7-107">The `PredictionFunction` runs one example at a time through the prediction pipeline.</span></span>

<span data-ttu-id="738f7-108">Önceden oluşturulmuş bir süsen tahmin veri kümesi modelini kullanarak tam bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="738f7-108">Here is the full example using a prebuilt Iris prediction dataset model:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        new TextLoader.Column("SepalLength", DataKind.R4, 0),
        new TextLoader.Column("SepalWidth", DataKind.R4, 1),
        new TextLoader.Column("PetalLength", DataKind.R4, 2),
        new TextLoader.Column("PetalWidth", DataKind.R4, 3),
        // Label: kind of iris.
        new TextLoader.Column("Label", DataKind.TX, 4),
    },
    // Default separator is tab, but the dataset has comma.
    Separator = ","
});

// Retrieve the training data.
var trainData = reader.Read(irisDataPath);

// Build the training pipeline.
var pipeline =
    // Concatenate all the features together into one column 'Features'.
    mlContext.Transforms.Concatenate("Features", "SepalLength", "SepalWidth", "PetalLength", "PetalWidth")
    // Note that the label is text, so it needs to be converted to key.
    .Append(mlContext.Transforms.Categorical.MapValueToKey("Label"), TransformerScope.TrainTest)
    // Use the multi-class SDCA model to predict the label using features.
    .Append(mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent())
    // Apply the inverse conversion from 'PredictedLabel' column back to string value.
    .Append(mlContext.Transforms.Conversion.MapKeyToValue(("PredictedLabel", "Data")));

// Train the model.
var model = pipeline.Fit(trainData);
```

<span data-ttu-id="738f7-109">Kullanılacak [şema kavramayı](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md) tahmin için bir çift sınıflar aşağıdaki gibi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="738f7-109">To use [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md) for prediction, define a pair of classes like the following:</span></span>

```csharp
private class IrisInput
{
    // Unfortunately, we still need the dummy 'Label' column to be present.
    [ColumnName("Label")]
    public string IgnoredLabel { get; set; }
    public float SepalLength { get; set; }
    public float SepalWidth { get; set; }
    public float PetalLength { get; set; }
    public float PetalWidth { get; set; }
}

private class IrisPrediction
{
    [ColumnName("Data")]
    public string PredictedClass { get; set; }
}
```

<span data-ttu-id="738f7-110">Tahmin kod artık şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="738f7-110">The prediction code now looks as follows:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Use the model for one-time prediction.
// Make the prediction function object. Note that, on average, this call takes around 200x longer
// than one prediction, so you might want to cache and reuse the prediction function, instead of
// creating one per prediction.
var predictionFunc = model.MakePredictionFunction<IrisInput, IrisPrediction>(mlContext);

// Obtain the prediction. Remember that 'Predict' is not reentrant. If you want to use multiple threads
// for simultaneous prediction, make sure each thread is using its own PredictionFunction.
var prediction = predictionFunc.Predict(new IrisInput
{
    SepalLength = 4.1f,
    SepalWidth = 0.1f,
    PetalLength = 3.2f,
    PetalWidth = 1.4f
});
```
