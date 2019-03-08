---
title: Bir metin dosyasına - ML.NET olmayan veriler ile machine learning modeli eğitme
description: ML.NET machine learning modeli eğitimi tahmin işlem hattının parçası olarak dosya olmayan eğitim verilerini yüklemek için nasıl kullanılacağını keşfedin.
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 27b327a63cb55b7fce0f4ff7facd3ee7c4a1c85c
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678633"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="c0371-103">Bir metin dosyasına - ML.NET olmayan veriler ile machine learning modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c0371-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="c0371-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c0371-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="c0371-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c0371-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="c0371-106">Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="c0371-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="c0371-107">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="c0371-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="c0371-108">ML.NET kanıtlanabilir yaygın olarak kullanıldığı yerler kullanılmasıdır `TextLoader` eğitim verilerini bir dosyadan okuma için.</span><span class="sxs-lookup"><span data-stu-id="c0371-108">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="c0371-109">Ancak, gerçek zamanlı eğitim senaryolarda veri başka bir yerde, aşağıdaki gibi olabilir:</span><span class="sxs-lookup"><span data-stu-id="c0371-109">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="c0371-110">SQL tablolarında</span><span class="sxs-lookup"><span data-stu-id="c0371-110">in SQL tables</span></span>
* <span data-ttu-id="c0371-111">günlük dosyalarından ayıklanan</span><span class="sxs-lookup"><span data-stu-id="c0371-111">extracted from log files</span></span>
* <span data-ttu-id="c0371-112">çalışma sırasında oluşturulan</span><span class="sxs-lookup"><span data-stu-id="c0371-112">generated on the fly</span></span>

<span data-ttu-id="c0371-113">Kullanım [şema kavramayı](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) varolan getirmek için C# `IEnumerable` ML.NET içine bir `DataView`.</span><span class="sxs-lookup"><span data-stu-id="c0371-113">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="c0371-114">Bu örnekte, müşteri karmaşıklığı tahmin modeli ve aşağıdaki özellikleri ayıklama üretim sisteminizde oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="c0371-114">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="c0371-115">Müşteri Kimliği (model tarafından göz ardı)</span><span class="sxs-lookup"><span data-stu-id="c0371-115">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="c0371-116">Müşteri (hedef 'etiketi') çoğaltılmaları olup olmadığı</span><span class="sxs-lookup"><span data-stu-id="c0371-116">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="c0371-117">'Demografik kategori' ('genç yetişkin' gibi bir dize vs.)</span><span class="sxs-lookup"><span data-stu-id="c0371-117">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="c0371-118">Son 5 gün ziyaret sayısı.</span><span class="sxs-lookup"><span data-stu-id="c0371-118">The number of visits from the last 5 days.</span></span>

```csharp
private class CustomerChurnInfo
{
    public string CustomerID { get; set; }
    public bool HasChurned { get; set; }
    public string DemographicCategory { get; set; }
    // Visits during last 5 days, latest to newest.
    [VectorType(5)]
    public float[] LastVisits { get; set; }
}
```

<span data-ttu-id="c0371-119">Bu veri yükleme `DataView` ve aşağıdaki kodu kullanarak bir model eğitip:</span><span class="sxs-lookup"><span data-stu-id="c0371-119">Load this data into the `DataView` and train the model, using the following code:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// Let's assume that 'GetChurnData()' fetches and returns the training data from somewhere.
IEnumerable<CustomerChurnInfo> churnData = GetChurnInfo();

// Turn the data into the ML.NET data view.
// We can use CreateDataView or CreateStreamingDataView, depending on whether 'churnData' is an IList,
// or merely an IEnumerable.
var trainData = mlContext.Data.ReadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
