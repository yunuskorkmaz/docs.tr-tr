---
title: Makine öğrenme modeli kalitesini değerlendirmek için ölçümleri hesaplama
description: Makine öğrenimi modeli kalitesini ML.NET ile değerlendirmek ve doğrulamak için ölçümleri hesaplamayı öğrenin
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 529003913b166c966e131b006800f944096605b7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855568"
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
