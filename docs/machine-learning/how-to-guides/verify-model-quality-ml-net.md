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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="59024-103">Makine öğrenimi modeli kalitesini değerlendirmek için ölçümleri hesaplama</span><span class="sxs-lookup"><span data-stu-id="59024-103">Calculate metrics to evaluate machine learning model quality</span></span>

> [!NOTE]
> <span data-ttu-id="59024-104">Bu konu, şu anda Önizleme'de olan ML.NET anlamına gelir ve malzeme değişebilir.</span><span class="sxs-lookup"><span data-stu-id="59024-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="59024-105">Daha fazla bilgi için ML.NET sayfasını ziyaret [edin.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="59024-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="59024-106">Bu nasıl yapılır ve ilgili örnek şu anda **sürüm 0,10 ML.NET**kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="59024-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="59024-107">Daha fazla bilgi [için, dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)adresindeki sürüm notlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="59024-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="59024-108">Modeli eğittmeden sonra kaliteyi nasıl değerlendirebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="59024-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="59024-109">Her makine öğrenimi görevi, kalite değerlendirme için ölçümleri ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="59024-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="59024-110">Aşağıdaki örnekte olduğu gibi, modeli değerlendirmek için görevin karşılık gelen 'bağlamını' kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="59024-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
