---
title: Çapraz doğrulama - ML.NET kullanarak makine öğrenme modeli eğitme
description: Bir machine learning modelinin tahminler elde etmek için doğruluğu büyük bir düzeyde olmasını ML.NET ile çapraz doğrulama kullanarak modeli eğitmek nasıl keşfedin
ms.date: 02/01/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 9ed139aacb41e8f8529f30747486ab1b13183df0
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739338"
---
# <a name="train-a-machine-learning-model-using-cross-validation---mlnet"></a><span data-ttu-id="84f3d-103">Çapraz doğrulama - ML.NET kullanarak makine öğrenme modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="84f3d-103">Train a machine learning model using cross-validation - ML.NET</span></span>

<span data-ttu-id="84f3d-104">[Çapraz doğrulama](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) ML uygulamalar için kullanışlı bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="84f3d-104">[Cross-validation](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) is a useful technique for ML applications.</span></span> <span data-ttu-id="84f3d-105">Bir çalışma alanından diğerine model kalitesi varyansını tahmin etmenize yardımcı olur ve ayrıca değerlendirme için ayarlanmış ayrı bir test ayıklanacak ihtiyacını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="84f3d-105">It helps estimate the variance of the model quality from one run to another and also eliminates the need to extract a separate test set for evaluation.</span></span>

<span data-ttu-id="84f3d-106">ML.NET otomatik olarak (tüm ön işleme bulunduğu sürece bir öğrenme işlem hattında) özellik kazandırma sayesinde doğru geçerlidir sonra 'stratification sütun' kavramı ilgili örnekler ayrılmış yoksa emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="84f3d-106">ML.NET automatically applies featurization correctly (as long as all of the preprocessing resides in one learning pipeline) then use the 'stratification column' concept to make sure that related examples don't get separated.</span></span>

<span data-ttu-id="84f3d-107">Rastgele 90/10 train-test bölme ve bir 5-fold çapraz doğrulama kullanarak Iris veri kümesinde bir eğitim örnek aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="84f3d-107">Here's a training example on an Iris dataset using randomized 90/10 train-test split, and a 5-fold cross-validation:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextReader(
    columns: new TextLoader.Column[]
    {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("SepalLength",DataKind.R4,0),
        new TextLoader.Column("SepalWidth",DataKind.R4,1),
        new TextLoader.Column("PetalLength",DataKind.R4,2),
        new TextLoader.Column("PetalWidth",DataKind.R4,3),
        // Label: kind of iris.
        new TextLoader.Column("Label",DataKind.TX,4)
    },
    // Default separator is tab, but the dataset has semicolon.
    separatorChar: ',',
    // First line of the file is a header, not a data row.
    hasHeader: true
);


// Read the data.
var data = reader.Read(dataPath);

// Build the training pipeline.
var dynamicPipeline =
    // Concatenate all the features together into one column 'Features'.
    mlContext.Transforms.Concatenate("Features", "SepalLength", "SepalWidth", "PetalLength", "PetalWidth")
    // Note that the label is text, so it needs to be converted to key.
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Label"), TransformerScope.TrainTest)
    // Use the multi-class SDCA model to predict the label using features.
    .Append(mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent());

// Split the data 90:10 into train and test sets, train and evaluate.
var (trainData, testData) = mlContext.MulticlassClassification.TrainTestSplit(data, testFraction: 0.1);

// Train the model.
var model = dynamicPipeline.Fit(trainData);
// Compute quality metrics on the test set.
var metrics = mlContext.MulticlassClassification.Evaluate(model.Transform(testData));
Console.WriteLine(metrics.AccuracyMicro);

// Now run the 5-fold cross-validation experiment, using the same pipeline.
var cvResults = mlContext.MulticlassClassification.CrossValidate(data, dynamicPipeline, numFolds: 5);

// The results object is an array of 5 elements. For each of the 5 folds, we have metrics, model and scored test data.
// Let's compute the average micro-accuracy.
var microAccuracies = cvResults.Select(r => r.metrics.AccuracyMicro);
Console.WriteLine(microAccuracies.Average());
```
