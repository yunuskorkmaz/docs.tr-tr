---
title: Makine öğrenimi modeli kalitesini değerlendirmek için ölçümleri hesaplama
description: Makine öğrenimi modeli kalitesini ML.NET ile değerlendirmek ve doğrulamak için ölçümleri nasıl hesaplayabilirsiniz öğrenin
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d6409307cd283ae67d7546c4dc6e19e6089a0766
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73975835"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Makine öğrenimi modeli kalitesini değerlendirmek için ölçümleri hesaplama

> [!NOTE]
> Bu konu, şu anda Önizleme'de olan ML.NET anlamına gelir ve malzeme değişebilir. Daha fazla bilgi için ML.NET sayfasını ziyaret [edin.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)

Bu nasıl yapılır ve ilgili örnek şu anda **sürüm 0,10 ML.NET**kullanıyor. Daha fazla bilgi [için, dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)adresindeki sürüm notlarına bakın.

Modeli eğittmeden sonra kaliteyi nasıl değerlendirebilirsiniz? Her makine öğrenimi görevi, kalite değerlendirme için ölçümleri ortaya çıkarır.

Aşağıdaki örnekte olduğu gibi, modeli değerlendirmek için görevin karşılık gelen 'bağlamını' kullanabilirsiniz:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
