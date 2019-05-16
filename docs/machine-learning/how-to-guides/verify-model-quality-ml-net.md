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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="02693-103">Machine learning değerlendirilecek ölçümlerini hesapla model kalitesi</span><span class="sxs-lookup"><span data-stu-id="02693-103">Calculate metrics to evaluate machine learning model quality</span></span> 

> [!NOTE]
> <span data-ttu-id="02693-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="02693-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="02693-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="02693-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="02693-106">Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="02693-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="02693-107">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="02693-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="02693-108">Nasıl modeli eğitme sonra kalitesini değerlendirmek?</span><span class="sxs-lookup"><span data-stu-id="02693-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="02693-109">Machine learning görev kalite değerlendirme için ölçümleri sunar.</span><span class="sxs-lookup"><span data-stu-id="02693-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="02693-110">Görevin karşılık gelen 'context', aşağıdaki örnekte olduğu gibi model değerlendirmek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="02693-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
