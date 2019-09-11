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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="c9728-103">Makine öğrenme modeli kalitesini değerlendirmek için ölçümleri hesaplama</span><span class="sxs-lookup"><span data-stu-id="c9728-103">Calculate metrics to evaluate machine learning model quality</span></span> 

> [!NOTE]
> <span data-ttu-id="c9728-104">Bu konu, şu anda önizleme aşamasında olan ML.NET 'e başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="c9728-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="c9728-105">Daha fazla bilgi için [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) sayfasını ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="c9728-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="c9728-106">Bu nasıl yapılır ve ilgili örnek şu anda **ml.NET sürüm 0,10**kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="c9728-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="c9728-107">Daha fazla bilgi için [DotNet/Machine-posta GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)depolarındaki sürüm notlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="c9728-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="c9728-108">Modeli eğitdikten sonra kaliteyi nasıl değerlendirirsiniz?</span><span class="sxs-lookup"><span data-stu-id="c9728-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="c9728-109">Her makine öğrenimi görevi kalite değerlendirmesi için ölçümleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="c9728-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="c9728-110">Aşağıdaki örnekte olduğu gibi, modeli değerlendirmek için görevin karşılık gelen ' bağlamını ' kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c9728-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
