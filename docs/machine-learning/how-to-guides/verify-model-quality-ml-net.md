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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="8dea2-103">Makine öğrenme modeli kalitesini değerlendirmek için ölçümleri hesaplama</span><span class="sxs-lookup"><span data-stu-id="8dea2-103">Calculate metrics to evaluate machine learning model quality</span></span>

> [!NOTE]
> <span data-ttu-id="8dea2-104">Bu konu, şu anda önizleme aşamasında olan ML.NET 'e başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="8dea2-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="8dea2-105">Daha fazla bilgi için [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) sayfasını ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="8dea2-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="8dea2-106">Bu nasıl yapılır ve ilgili örnek şu anda **ml.NET sürüm 0,10**kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="8dea2-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="8dea2-107">Daha fazla bilgi için [DotNet/Machine-posta GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)depolarındaki sürüm notlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="8dea2-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="8dea2-108">Modeli eğitdikten sonra kaliteyi nasıl değerlendirirsiniz?</span><span class="sxs-lookup"><span data-stu-id="8dea2-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="8dea2-109">Her makine öğrenimi görevi kalite değerlendirmesi için ölçümleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="8dea2-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="8dea2-110">Aşağıdaki örnekte olduğu gibi, modeli değerlendirmek için görevin karşılık gelen ' bağlamını ' kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8dea2-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
