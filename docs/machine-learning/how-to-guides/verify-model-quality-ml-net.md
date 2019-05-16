---
title: Machine learning değerlendirilecek ölçümlerini hesapla model kalitesi
description: Değerlendirmek ve makine öğrenimi model kalitesi ML.NET ile doğrulamak için ölçümlerini hesapla öğrenin
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 2c7749205b862a42f42b857972057c441ab84364
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641103"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Machine learning değerlendirilecek ölçümlerini hesapla model kalitesi 

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**. Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Nasıl modeli eğitme sonra kalitesini değerlendirmek? Machine learning görev kalite değerlendirme için ölçümleri sunar.

Görevin karşılık gelen 'context', aşağıdaki örnekte olduğu gibi model değerlendirmek için kullanabilirsiniz:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
