---
title: ML.NET ardışık düzen işleme sırasında ara veri değerlerini İnceleme
description: Ardışık Düzen işleme öğrenme ML.NET makine sırasında gerçek ara veri değerlerini incelemek hakkında bilgi edinin
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 362cb9351c3cb77b6aa67d59154854e882869ad9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968720"
---
# <a name="inspect-intermediate-data-values-during-mlnet-pipeline-processing"></a><span data-ttu-id="2e766-103">ML.NET ardışık düzen işleme sırasında ara veri değerlerini İnceleme</span><span class="sxs-lookup"><span data-stu-id="2e766-103">Inspect intermediate data values during ML.NET pipeline processing</span></span>

> [!NOTE]
> <span data-ttu-id="2e766-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2e766-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="2e766-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="2e766-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="2e766-106">Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="2e766-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="2e766-107">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="2e766-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="2e766-108">Deneme sırasında inceleyin ve belirli bir noktada veri işleme sonuçları doğrulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e766-108">During the experiment, you may want to observe and validate the data processing results at a given point.</span></span> <span data-ttu-id="2e766-109">ML.NET işlemleri oluşturma veri ' gösterir' olan nesneleri yavaş olduğundan, bu kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="2e766-109">This isn't easy since ML.NET operations are lazy, constructing objects that are 'promises' of data.</span></span>

<span data-ttu-id="2e766-110">`GetColumn<T>` Genişletme yöntemi, Ara verileri incelemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e766-110">The `GetColumn<T>` extension method lets you inspect the intermediate data.</span></span> <span data-ttu-id="2e766-111">Bir veri sütunu olarak içeriğini döndürür bir `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="2e766-111">It returns the contents of one data column as an `IEnumerable`.</span></span>

<span data-ttu-id="2e766-112">Aşağıdaki örnek nasıl kullanılacağını gösterir `GetColumn<T>` genişletme yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2e766-112">The following example shows how to use the `GetColumn<T>` extension method:</span></span>

<span data-ttu-id="2e766-113">[Örnek dosya](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span><span class="sxs-lookup"><span data-stu-id="2e766-113">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span></span>

<!-- markdownlint-disable MD010 -->
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse

```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="2e766-114">Bizim sınıfı şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="2e766-114">Our class is defined as follows:</span></span>

```csharp
public class InspectedRow
{
    [LoadColumn(0)]
    public bool IsOver50K { get; set; }
    [LoadColumn(1)]
    public string WorkClass { get; set; }
    [LoadColumn(2)]
    public string Education { get; set; }
    [LoadColumn(3)]
    public string MaritalStatus { get; set; }
}
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Read the data into a data view.
var data = mlContext.Data.ReadFromTextFile<InspectedRow>(dataPath, hasHeader: true);

// Start creating our processing pipeline. For now, let's just concatenate all the text columns
// together into one.
var pipeline = mlContext.Transforms.Concatenate("AllFeatures", "WorkClass", "Education", "MaritalStatus");

// Fit our data pipeline and transform data with it.
var transformedData = pipeline.Fit(data).Transform(data);

// Extract the 'AllFeatures' column.
// This will give the entire dataset: make sure to only take several row
// in case the dataset is huge. The is similar to the static API, except
// you have to specify the column name and type.
var featureColumns =
    transformedData
        .GetColumn<string[]>(mlContext, "AllFeatures")
        .Take(20)
        .ToArray();
```
