---
title: Machine learning işlem - ML.NET bir metin dosyasından veri yükleme
description: Machine learning modeli oluşturmaya, eğitim ve puanlama ML.NET ile kullanım için bir metin dosyasından veri yükleme keşfedin
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 14b1f8c99da6f1b8da436d9afef5b2ac8d36ecae
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843375"
---
# <a name="load-data-from-a-text-file-for-machine-learning-processing---mlnet"></a><span data-ttu-id="4c23d-103">Machine learning işlem - ML.NET bir metin dosyasından veri yükleme</span><span class="sxs-lookup"><span data-stu-id="4c23d-103">Load data from a text file for machine learning processing - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="4c23d-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="4c23d-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="4c23d-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="4c23d-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="4c23d-106">Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="4c23d-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="4c23d-107">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="4c23d-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="4c23d-108">`TextLoader` metin dosyalarından veri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c23d-108">`TextLoader` is used to load data from text files.</span></span> <span data-ttu-id="4c23d-109">Metin dosyasında veri sütunları, türlerini ve konumlarını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c23d-109">You need to specify the data columns, their types, and their location in the text file.</span></span>

<span data-ttu-id="4c23d-110">Bir dosyanın bazı sütunları okumak veya birden çok kez aynı sütun okuma edilebilir olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4c23d-110">Note that it's perfectly acceptable to read some columns of a file, or read the same column multiple times.</span></span>

<span data-ttu-id="4c23d-111">[Örnek dosya](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):</span><span class="sxs-lookup"><span data-stu-id="4c23d-111">[Example file](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):</span></span>

<!-- markdownlint-disable MD010 -->
```console
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="4c23d-112">Bir metin dosyasından verileri yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="4c23d-112">To load the data from a text file:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
        // A boolean column depicting the 'target label'.
        new TextLoader.Column("IsOver50k",DataKind.BL,0),
        // Three text columns.
        new TextLoader.Column("WorkClass",DataKind.TX,1),
        new TextLoader.Column("Education",DataKind.TX,2),
        new TextLoader.Column("MaritalStatus",DataKind.TX,3)
    },
    hasHeader: true
);

// Now read the file (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(dataPath);
```
