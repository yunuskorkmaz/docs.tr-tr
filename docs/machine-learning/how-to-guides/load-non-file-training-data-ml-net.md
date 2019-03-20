---
title: Bir metin dosyasına - ML.NET olmayan veriler ile machine learning modeli eğitme
description: ML.NET machine learning modeli eğitimi tahmin işlem hattının parçası olarak dosya olmayan eğitim verilerini yüklemek için nasıl kullanılacağını keşfedin.
ms.date: 03/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 32de37e45b9e19669ea06d74c7f252ec885fe004
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186097"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="d9c67-103">Bir metin dosyasına - ML.NET olmayan veriler ile machine learning modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="d9c67-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="d9c67-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d9c67-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="d9c67-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d9c67-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="d9c67-106">Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.11**.</span><span class="sxs-lookup"><span data-stu-id="d9c67-106">This how-to and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="d9c67-107">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="d9c67-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="d9c67-108">ML.NET kanıtlanabilir yaygın olarak kullanıldığı yerler kullanılmasıdır `TextLoader` eğitim verilerini bir dosyadan okuma için.</span><span class="sxs-lookup"><span data-stu-id="d9c67-108">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="d9c67-109">Ancak, gerçek zamanlı eğitim senaryolarda veri başka bir yerde, aşağıdaki gibi olabilir:</span><span class="sxs-lookup"><span data-stu-id="d9c67-109">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="d9c67-110">SQL tablolarında</span><span class="sxs-lookup"><span data-stu-id="d9c67-110">in SQL tables</span></span>
* <span data-ttu-id="d9c67-111">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="d9c67-111">JSON/XML</span></span>
* <span data-ttu-id="d9c67-112">günlük dosyalarından ayıklanan</span><span class="sxs-lookup"><span data-stu-id="d9c67-112">extracted from log files</span></span>
* <span data-ttu-id="d9c67-113">çalışma sırasında oluşturulan</span><span class="sxs-lookup"><span data-stu-id="d9c67-113">generated on the fly</span></span>

<span data-ttu-id="d9c67-114">Kullanım [şema kavramayı](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) varolan getirmek için C# `IEnumerable` ML.NET içine bir `DataView`.</span><span class="sxs-lookup"><span data-stu-id="d9c67-114">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="d9c67-115">Bu örnekte, müşteri karmaşıklığı tahmin modeli ve aşağıdaki özellikleri ayıklama üretim sisteminizde oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="d9c67-115">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="d9c67-116">Müşteri Kimliği (model tarafından göz ardı)</span><span class="sxs-lookup"><span data-stu-id="d9c67-116">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="d9c67-117">Müşteri (hedef 'etiketi') çoğaltılmaları olup olmadığı</span><span class="sxs-lookup"><span data-stu-id="d9c67-117">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="d9c67-118">'Demografik kategori' ('genç yetişkin' gibi bir dize vs.)</span><span class="sxs-lookup"><span data-stu-id="d9c67-118">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="d9c67-119">Son 5 gün ziyaret sayısı.</span><span class="sxs-lookup"><span data-stu-id="d9c67-119">The number of visits from the last 5 days.</span></span>

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

<span data-ttu-id="d9c67-120">Bu veri yükleme `DataView` ve aşağıdaki kodu kullanarak bir model eğitip:</span><span class="sxs-lookup"><span data-stu-id="d9c67-120">Load this data into the `DataView` and train the model, using the following code:</span></span>

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
var trainData = mlContext.Data.LoadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
