---
title: Kategorik veri - ML.NET özellik Mühendisliği, eğitim modeli için geçerlidir
description: Özellik Mühendisliği için machine learning modeli eğitimi ML.NET kategorik verilerde uygulanacak hakkında bilgi edinin
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: eedbe0499784e7a99b0101c42892652daef3a114
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968419"
---
# <a name="apply-feature-engineering-for-model-training-on-categorical-data---mlnet"></a>Kategorik veri - ML.NET özellik Mühendisliği, eğitim modeli için geçerlidir

Herhangi bir float olmayan veri dönüştürmeniz gerekir `float` tüm ML.NET itibaren veri türleri `learners` özellikleri beklediğiniz bir `float vector`.

Veri kümesi içeriyorsa `categorical` verileri (örneğin, ' enum'), ML.NET teklifler özellikleri dönüştürme birkaç yolu:

- Bir kodlama sık erişimli
- Sık erişimli bir karma tabanlı kodlama
- İkili kodlama (kategori dizini biraz dizisi ve kullanım BITS özellikler olarak dönüştürme)

A `one-hot encoding` bazı kategorileri çok yüksek kardinalite varsa kısıp olabilir (çok sayıda farklı değerler, küçük bir sık gerçekleşen ayarlayın. Bu durumda, sayı tabanlı özellik seçimi ile kodlamak için yuva sayısını azaltın.

Kategorik özellik kazandırma sayesinde kategorik dönüşümü emin olmak için doğrudan ML.NET öğrenme hattında şunlardır:

- yalnızca 'eğitim verilerini ve test verilerinizde eğitildi',
- doğru şekilde tahmin zaman ek önceden işleme olmadan gelen yeni verilere uygulanır.

Kategorik işleme için aşağıdaki örnekte [yetişkinlere yönelik görselleştirmenizdeki dataset](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):

```console
Label   Workclass   education   marital-status  occupation  relationship    ethnicity   sex native-country-region   age fnlwgt  education-num   capital-gain    capital-loss    hours-per-week
0   Private 11th    Never-married   Machine-op-inspct   Own-child   Black   Male    United-States   25  226802  7   0   0   40
0   Private HS-grad Married-civ-spouse  Farming-fishing Husband White   Male    United-States   38  89814   9   0   0   50
1   Local-gov   Assoc-acdm  Married-civ-spouse  Protective-serv Husband White   Male    United-States   28  336951  12  0   0   40
1   Private Some-college    Married-civ-spouse  Machine-op-inspct   Husband Black   Male    United-States   44  160323  10  7688    0   40
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(new[] 
    {
        new TextLoader.Column("Label", DataKind.BL, 0),
        // We will load all the categorical features into one vector column of size 8.
        new TextLoader.Column("CategoricalFeatures", DataKind.TX, 1, 8),
        // Similarly, load all numerical features into one vector of size 6.
        new TextLoader.Column("NumericalFeatures", DataKind.R4, 9, 14),
        // Let's also separately load the 'Workclass' column.
        new TextLoader.Column("Workclass", DataKind.TX, 1),
    },
    hasHeader: true
);

// Read the data.
var data = reader.Read(dataPath);

// Inspect the first 10 records of the categorical columns to check that they are correctly read.
var catColumns = data.GetColumn<string[]>(mlContext, "CategoricalFeatures").Take(10).ToArray();

// Build several alternative featurization pipelines.
var pipeline =
    // Convert each categorical feature into one-hot encoding independently.
    mlContext.Transforms.Categorical.OneHotEncoding("CategoricalFeatures", "CategoricalOneHot")
        // Convert all categorical features into indices, and build a 'word bag' of these.
        .Append(mlContext.Transforms.Categorical.OneHotEncoding("CategoricalFeatures", "CategoricalBag",OneHotEncodingTransformer.OutputKind.Bag))
        // One-hot encode the workclass column, then drop all the categories that have fewer than 10 instances in the train set.
        .Append(mlContext.Transforms.Categorical.OneHotEncoding("Workclass", "WorkclassOneHot"))
        .Append(mlContext.Transforms.FeatureSelection.SelectFeaturesBasedOnCount("WorkclassOneHot", "WorkclassOneHotTrimmed", count: 10));

// Let's train our pipeline, and then apply it to the same data.
var transformedData = pipeline.Fit(data).Transform(data);

// Inspect some columns of the resulting dataset.
var categoricalBags = transformedData.GetColumn<float[]>(mlContext, "CategoricalBag").Take(10).ToArray();
var workclasses = transformedData.GetColumn<float[]>(mlContext, "WorkclassOneHotTrimmed").Take(10).ToArray();

// Of course, if we want to train the model, we will need to compose a single float vector of all the features.
// Here's how we could do this:

var fullLearningPipeline = pipeline
    // Concatenate two of the 3 categorical pipelines, and the numeric features.
    .Append(mlContext.Transforms.Concatenate("Features", "NumericalFeatures", "CategoricalBag", "WorkclassOneHotTrimmed"))
    // Cache data in memory so that the following trainer will be able to access training examples without
    // reading them from disk multiple times.
    .AppendCacheCheckpoint(mlContext)
    // Now we're ready to train. We chose our FastTree trainer for this classification task.
    .Append(mlContext.BinaryClassification.Trainers.FastTree(numTrees: 50));

// Train the model.
var model = fullLearningPipeline.Fit(data);
```
