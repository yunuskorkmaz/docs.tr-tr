---
title: Makine öğrenme modeli kalitesini değerlendirmek için ölçümleri hesaplama
description: Makine öğrenimi modeli kalitesini ML.NET ile değerlendirmek ve doğrulamak için ölçümleri hesaplamayı öğrenin
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d6409307cd283ae67d7546c4dc6e19e6089a0766
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975835"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Makine öğrenme modeli kalitesini değerlendirmek için ölçümleri hesaplama

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET 'e başvurur ve malzemeler değişebilir. Daha fazla bilgi için [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) sayfasını ziyaret edin.

Bu nasıl yapılır ve ilgili örnek şu anda **ml.NET sürüm 0,10**kullanıyor. Daha fazla bilgi için [DotNet/Machine-posta GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)depolarındaki sürüm notlarına bakın.

Modeli eğitdikten sonra kaliteyi nasıl değerlendirirsiniz? Her makine öğrenimi görevi kalite değerlendirmesi için ölçümleri kullanıma sunar.

Aşağıdaki örnekte olduğu gibi, modeli değerlendirmek için görevin karşılık gelen ' bağlamını ' kullanabilirsiniz:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
