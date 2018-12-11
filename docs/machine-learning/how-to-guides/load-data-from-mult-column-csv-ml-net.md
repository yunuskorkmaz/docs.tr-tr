---
title: Machine learning işlem - ML.NET bir CSV dosyasından fazla sayıda sütun ile veri yükleme
description: Çok sütunlu veri verileri makine öğrenimi modeli oluşturma, eğitim ve puanlama ML.NET ile kullanım için bir CSV dosyasından öğrenin
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 3b87231f8e5a4ce39761d1ec71398b5295666d07
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155452"
---
# <a name="load-data-with-many-columns-from-a-csv-file-for-machine-learning-processing---mlnet"></a><span data-ttu-id="e8f29-103">Machine learning işlem - ML.NET bir CSV dosyasından fazla sayıda sütun ile veri yükleme</span><span class="sxs-lookup"><span data-stu-id="e8f29-103">Load data with many columns from a CSV file for machine learning processing - ML.NET</span></span>

<span data-ttu-id="e8f29-104">`TextLoader` metin dosyalarından veri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8f29-104">`TextLoader` is used to load data from text files.</span></span> <span data-ttu-id="e8f29-105">Metin dosyasında veri sütunları, türlerini ve konumlarını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8f29-105">You need to specify the data columns, their types, and their location in the text file.</span></span>

<span data-ttu-id="e8f29-106">Giriş dosyası aynı türden ve her zaman birçok sütunları içerdiğinde birlikte kullanılan olarak okuma bir *vektör sütun*.</span><span class="sxs-lookup"><span data-stu-id="e8f29-106">When the input file contains many columns of the same type and always used together, read them as a *vector column*.</span></span> <span data-ttu-id="e8f29-107">Bu strateji, verileri temizleme şemada sonuçlanır ve aşağıdaki örnekte gösterildiği gibi gereksiz performans maliyetleri ortadan kaldırır:</span><span class="sxs-lookup"><span data-stu-id="e8f29-107">This strategy results in a clean data schema and avoids unnecessary performance costs, as shown in the following example:</span></span>

<span data-ttu-id="e8f29-108">[Örnek dosya](https://github.com/dotnet/machinelearning/tree/master/test/data/generated_regression_dataset.csv):</span><span class="sxs-lookup"><span data-stu-id="e8f29-108">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/generated_regression_dataset.csv):</span></span>

```console
-2.75,0.77,-0.61,0.14,1.39,0.38,-0.53,-0.50,-2.13,-0.39,0.46,140.66
-0.61,-0.37,-0.12,0.55,-1.00,0.84,-0.02,1.30,-0.24,-0.50,-2.12,148.12
-0.85,-0.91,1.81,0.02,-0.78,-1.41,-1.09,-0.65,0.90,-0.37,-0.22,402.20
0.28,1.05,-0.24,0.30,-0.99,0.19,0.32,-0.95,-1.19,-0.63,0.75,443.51
```

<span data-ttu-id="e8f29-109">Kullanarak bu dosyayı okuma `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="e8f29-109">Reading this file using `TextLoader`:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new[] {
        // We read the first 10 values as a single float vector.
        new TextLoader.Column("FeatureVector", DataKind.R4, 0, 9),
        // Separately, read the target variable.
        new TextLoader.Column("Target", DataKind.R4, 10)
    },
    // Default separator is tab, but we need a comma.
    Separator = ",");

// Now read the file (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(dataPath);
```