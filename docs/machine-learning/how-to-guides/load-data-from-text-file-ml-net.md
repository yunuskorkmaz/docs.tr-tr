---
title: Machine learning işlem - ML.NET bir metin dosyasından veri yükleme
description: Machine learning modeli oluşturmaya, eğitim ve puanlama ML.NET ile kullanım için bir metin dosyasından veri yükleme keşfedin
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 70c7ccdeaa27b78a412c2bc82f524d4bf42a740a
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091714"
---
# <a name="load-data-from-a-text-file-for-machine-learning-processing---mlnet"></a>Machine learning işlem - ML.NET bir metin dosyasından veri yükleme

`TextLoader` metin dosyalarından veri yüklemek için kullanılır. Metin dosyasında veri sütunları, türlerini ve konumlarını belirtmeniz gerekir.

Bir dosyanın bazı sütunları okumak veya birden çok kez aynı sütun okuma edilebilir olduğuna dikkat edin.

[Örnek dosya](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):

```console
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse
```

Bir metin dosyasından verileri yüklemek için:

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