---
title: Machine learning hizmetinin işlem - ML.NET için birden fazla dosyalardan veri yükleme
description: Bilgi nasıl makine öğrenme modeli oluşturma, eğitim ve puanlama ML.NET ile kullanım için birden çok dosyadan veri yükleme
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: c9b34bd6bcbac62e9f9c33226f5d0feb41168392
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52672368"
---
# <a name="load-data-from-multiple-files-for-machine-learning-processing---mlnet"></a><span data-ttu-id="95f58-103">Machine learning hizmetinin işlem - ML.NET için birden fazla dosyalardan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="95f58-103">Load data from multiple files for machine learning processing - ML.NET</span></span>

<span data-ttu-id="95f58-104">Kullanım `TextLoader`ve bir dizi dosyaları belirtin `Read` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95f58-104">Use the `TextLoader`, and specify an array of files to the `Read` method.</span></span> <span data-ttu-id="95f58-105">Dosyaları aynı olmalıdır (aynı sayıda ve türde sütun) şema:</span><span class="sxs-lookup"><span data-stu-id="95f58-105">The files must have the same schema (same number and type of columns):</span></span>

* [<span data-ttu-id="95f58-106">Örnek fıle1'de</span><span class="sxs-lookup"><span data-stu-id="95f58-106">Example file1</span></span>](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.train)
* [<span data-ttu-id="95f58-107">Örnek dosya2</span><span class="sxs-lookup"><span data-stu-id="95f58-107">Example file2</span></span>](https://github.com/dotnet/machinelearning/blob/e3a34ae6ae1b25ac96faa0317308703ce943ff95/test/data/adult.test)

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // A boolean column depicting the 'label'.
        new TextLoader.Column("IsOver50k", DataKind.BL, 0),
        // Three text columns.
        new TextLoader.Column("Workclass", DataKind.TX, 1),
        new TextLoader.Column("Education", DataKind.TX, 2),
        new TextLoader.Column("MaritalStatus", DataKind.TX, 3)
    },
    // First line of the file is a header, not a data row.
    HasHeader = true
});

var data = reader.Read(exampleFile1, exampleFile2);
```