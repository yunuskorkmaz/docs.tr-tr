---
title: Bir metin dosyasına - ML.NET olmayan veriler ile machine learning modeli eğitme
description: ML.NET machine learning modeli eğitimi tahmin işlem hattının parçası olarak dosya olmayan eğitim verilerini yüklemek için nasıl kullanılacağını keşfedin.
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4ffbc69629aa9dc6cea5d33c704bc9c57a4a612c
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092026"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a>Bir metin dosyasına - ML.NET olmayan veriler ile machine learning modeli eğitme

ML.NET kanıtlanabilir yaygın olarak kullanıldığı yerler kullanılmasıdır `TextLoader` eğitim verilerini bir dosyadan okuma için.
Ancak, gerçek zamanlı eğitim senaryolarda veri başka bir yerde, aşağıdaki gibi olabilir:

* SQL tablolarında
* günlük dosyalarından ayıklanan
* çalışma sırasında oluşturulan

Kullanım [şema kavramayı](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) varolan getirmek için C# `IEnumerable` ML.NET içine bir `DataView`.

Bu örnekte, müşteri karmaşıklığı tahmin modeli ve aşağıdaki özellikleri ayıklama üretim sisteminizde oluşturacaksınız:

* Müşteri Kimliği (model tarafından göz ardı)
* Müşteri (hedef 'etiketi') çoğaltılmaları olup olmadığı
* 'Demografik kategori' ('genç yetişkin' gibi bir dize vs.)
* Son 5 gün ziyaret sayısı.

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

Bu veri yükleme `DataView` ve aşağıdaki kodu kullanarak bir model eğitip:

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
