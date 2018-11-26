---
title: Veri işleme - ML.NET kullanılacak normalizers ile eğitim verileri ön işleme
description: Machine learning modeli oluşturmaya, eğitim ve puanlama ML.NET ile kullanım için eğitim verileri ön işleme için normalizers kullanmayı öğrenin
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: c8b959904705e996c97bdcd8b3444e754d14d046
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297691"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a>Veri işleme - ML.NET kullanılacak normalizers ile eğitim verileri ön işleme

ML.NET sunan bir dizi [parametrik ve parametreli olmayan algoritmaları](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).

Sahip **değil** olarak seçtiğiniz hangi normalizer önemli olduğu **kullanın** bir normalizer doğrusal veya diğer parametrik modellerin eğitimi.

Her zaman normalizer doğrudan ML.NET öğrenme işlem hattında, bu nedenle dahil bu:

- Eğitim verilerini ve test verilerini değil, yalnızca eğitildi,
- Yeni gelen verilerin tamamı, tahmin zaman ek ön işleme gerek kalmadan için doğru şekilde uygulanır.

Bir işlem hatları öğrenme içinde normalleştirme gösteren kod parçacığı aşağıda verilmiştir. Bunu kullanarak Iris veri kümesini varsayılır:

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
