---
title: Kategorik veri - ML.NET özellik Mühendisliği, eğitim modeli için geçerlidir
description: Özellik Mühendisliği için machine learning modeli eğitimi ML.NET kategorik verilerde uygulanacak hakkında bilgi edinin
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: f0101a3c9398637ece60051257c82eb69ef933d0
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57846070"
---
# <a name="apply-feature-engineering-for-model-training-on-categorical-data---mlnet"></a><span data-ttu-id="f562f-103">Kategorik veri - ML.NET özellik Mühendisliği, eğitim modeli için geçerlidir</span><span class="sxs-lookup"><span data-stu-id="f562f-103">Apply feature engineering for model training on categorical data - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="f562f-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f562f-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="f562f-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f562f-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="f562f-106">Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="f562f-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="f562f-107">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="f562f-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="f562f-108">Herhangi bir float olmayan veri dönüştürmeniz gerekir `float` tüm ML.NET itibaren veri türleri `learners` özellikleri beklediğiniz bir `float vector`.</span><span class="sxs-lookup"><span data-stu-id="f562f-108">You need to convert any non float data to `float` data types since all ML.NET `learners` expect features as a `float vector`.</span></span>

<span data-ttu-id="f562f-109">Veri kümesi içeriyorsa `categorical` verileri (örneğin, ' enum'), ML.NET teklifler özellikleri dönüştürme birkaç yolu:</span><span class="sxs-lookup"><span data-stu-id="f562f-109">If the dataset contains `categorical` data (for example, 'enum'), ML.NET offers several ways of converting it to features:</span></span>

- <span data-ttu-id="f562f-110">Bir kodlama sık erişimli</span><span class="sxs-lookup"><span data-stu-id="f562f-110">One-hot encoding</span></span>
- <span data-ttu-id="f562f-111">Sık erişimli bir karma tabanlı kodlama</span><span class="sxs-lookup"><span data-stu-id="f562f-111">Hash-based one-hot encoding</span></span>
- <span data-ttu-id="f562f-112">İkili kodlama (kategori dizini biraz dizisi ve kullanım BITS özellikler olarak dönüştürme)</span><span class="sxs-lookup"><span data-stu-id="f562f-112">Binary encoding (convert category index into a bit sequence and use bits as features)</span></span>

<span data-ttu-id="f562f-113">A `one-hot encoding` bazı kategorileri çok yüksek kardinalite varsa kısıp olabilir (çok sayıda farklı değerler, küçük bir sık gerçekleşen ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f562f-113">A `one-hot encoding` can be wasteful if some categories are very high-cardinality (lots of different values, with a small set commonly occurring.</span></span> <span data-ttu-id="f562f-114">Bu durumda, sayı tabanlı özellik seçimi ile kodlamak için yuva sayısını azaltın.</span><span class="sxs-lookup"><span data-stu-id="f562f-114">In that case, reduce the number of slots to encode with count-based feature selection.</span></span>

<span data-ttu-id="f562f-115">Kategorik özellik kazandırma sayesinde kategorik dönüşümü emin olmak için doğrudan ML.NET öğrenme hattında şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f562f-115">Include categorical featurization directly in the ML.NET learning pipeline to ensure that the categorical transformation:</span></span>

- <span data-ttu-id="f562f-116">yalnızca 'eğitim verilerini ve test verilerinizde eğitildi',</span><span class="sxs-lookup"><span data-stu-id="f562f-116">is only 'trained' on the training data, and not on your test data,</span></span>
- <span data-ttu-id="f562f-117">doğru şekilde tahmin zaman ek önceden işleme olmadan gelen yeni verilere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f562f-117">is correctly applied to new incoming data, without extra pre-processing at prediction time.</span></span>

<span data-ttu-id="f562f-118">Kategorik işleme için aşağıdaki örnekte [yetişkinlere yönelik görselleştirmenizdeki dataset](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):</span><span class="sxs-lookup"><span data-stu-id="f562f-118">The following example illustrates categorical handling for the [adult census dataset](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):</span></span>

<!-- markdownlint-disable MD010 -->
```console
Label   Workclass   education   marital-status  occupation  relationship    ethnicity   sex native-country-region   age fnlwgt  education-num   capital-gain    capital-loss    hours-per-week
0   Private 11th    Never-married   Machine-op-inspct   Own-child   Black   Male    United-States   25  226802  7   0   0   40
0   Private HS-grad Married-civ-spouse  Farming-fishing Husband White   Male    United-States   38  89814   9   0   0   50
1   Local-gov   Assoc-acdm  Married-civ-spouse  Protective-serv Husband White   Male    United-States   28  336951  12  0   0   40
1   Private Some-college    Married-civ-spouse  Machine-op-inspct   Husband Black   Male    United-States   44  160323  10  7688    0   40
```
<!-- markdownlint-enable MD010 -->

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
