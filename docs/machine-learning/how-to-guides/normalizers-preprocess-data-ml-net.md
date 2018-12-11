---
title: Veri işleme - ML.NET kullanılacak normalizers ile eğitim verileri ön işleme
description: Machine learning modeli oluşturmaya, eğitim ve puanlama ML.NET ile kullanım için eğitim verileri ön işleme için normalizers kullanmayı öğrenin
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: c8b959904705e996c97bdcd8b3444e754d14d046
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148840"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a><span data-ttu-id="8cf60-103">Veri işleme - ML.NET kullanılacak normalizers ile eğitim verileri ön işleme</span><span class="sxs-lookup"><span data-stu-id="8cf60-103">Preprocess training data with normalizers to use in data processing - ML.NET</span></span>

<span data-ttu-id="8cf60-104">ML.NET sunan bir dizi [parametrik ve parametreli olmayan algoritmaları](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span><span class="sxs-lookup"><span data-stu-id="8cf60-104">ML.NET exposes a number of [parametric and non-parametric algorithms](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span></span>

<span data-ttu-id="8cf60-105">Sahip **değil** olarak seçtiğiniz hangi normalizer önemli olduğu **kullanın** bir normalizer doğrusal veya diğer parametrik modellerin eğitimi.</span><span class="sxs-lookup"><span data-stu-id="8cf60-105">It's **not** as important which normalizer you choose as it is to **use** a normalizer when training linear or other parametric models.</span></span>

<span data-ttu-id="8cf60-106">Her zaman normalizer doğrudan ML.NET öğrenme işlem hattında, bu nedenle dahil bu:</span><span class="sxs-lookup"><span data-stu-id="8cf60-106">Always include the normalizer directly in the ML.NET learning pipeline, so it:</span></span>

- <span data-ttu-id="8cf60-107">Eğitim verilerini ve test verilerini değil, yalnızca eğitildi,</span><span class="sxs-lookup"><span data-stu-id="8cf60-107">is only trained on the training data, and not on your test data,</span></span>
- <span data-ttu-id="8cf60-108">Yeni gelen verilerin tamamı, tahmin zaman ek ön işleme gerek kalmadan için doğru şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8cf60-108">is correctly applied to all the new incoming data, without the need for extra pre-processing at prediction time.</span></span>

<span data-ttu-id="8cf60-109">Bir işlem hatları öğrenme içinde normalleştirme gösteren kod parçacığı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8cf60-109">Here's a snippet of code that demonstrates normalization in learning pipelines.</span></span> <span data-ttu-id="8cf60-110">Bunu kullanarak Iris veri kümesini varsayılır:</span><span class="sxs-lookup"><span data-stu-id="8cf60-110">It assumes the Iris dataset:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("Features", DataKind.R4, 0, 3),
        // Label: kind of iris.
        new TextLoader.Column("Label", DataKind.TX, 4),
    },
    // Default separator is tab, but the dataset has comma.
    Separator = ","
});

// Read the training data.
var trainData = reader.Read(dataPath);

// Apply all kinds of standard ML.NET normalization to the raw features.
var pipeline =
    mlContext.Transforms.Normalize(
        new NormalizingEstimator.MinMaxColumn("Features", "MinMaxNormalized", fixZero: true),
        new NormalizingEstimator.MeanVarColumn("Features", "MeanVarNormalized", fixZero: true),
        new NormalizingEstimator.BinningColumn("Features", "BinNormalized", numBins: 256));

// Let's train our pipeline of normalizers, and then apply it to the same data.
var normalizedData = pipeline.Fit(trainData).Transform(trainData);

// Inspect one column of the resulting dataset.
var meanVarValues = normalizedData.GetColumn<float[]>(mlContext, "MeanVarNormalized").ToArray();
```
