---
title: Machine learning değerlendirilecek ölçümlerini hesapla model kalitesi
description: Değerlendirmek ve makine öğrenimi model kalitesi ML.NET ile doğrulamak için ölçümlerini hesapla öğrenin
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 3e55c329ff12ffdbec41716ca95b4a77d5d082c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655183"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="c3269-103">Machine learning değerlendirilecek ölçümlerini hesapla model kalitesi</span><span class="sxs-lookup"><span data-stu-id="c3269-103">Calculate metrics to evaluate machine learning model quality</span></span> 

> [!NOTE]
> <span data-ttu-id="c3269-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c3269-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="c3269-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c3269-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="c3269-106">Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="c3269-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="c3269-107">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="c3269-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="c3269-108">Nasıl modeli eğitme sonra kalitesini değerlendirmek?</span><span class="sxs-lookup"><span data-stu-id="c3269-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="c3269-109">Machine learning görev kalite değerlendirme için ölçümleri sunar.</span><span class="sxs-lookup"><span data-stu-id="c3269-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="c3269-110">Görevin karşılık gelen 'context', aşağıdaki örnekte olduğu gibi model değerlendirmek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c3269-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```