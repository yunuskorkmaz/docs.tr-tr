---
title: Machine learning değerlendirilecek ölçümlerini hesapla kalite - ML.NET modeli
description: Değerlendirmek ve makine öğrenimi model kalitesi ML.NET ile doğrulamak için ölçümlerini hesapla öğrenin
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 6fd4dfab6104b4398918e42ed70584b04169a8c1
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297676"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a><span data-ttu-id="823fe-103">Machine learning değerlendirilecek ölçümlerini hesapla kalite - ML.NET modeli</span><span class="sxs-lookup"><span data-stu-id="823fe-103">Calculate metrics to evaluate machine learning model quality - ML.NET</span></span>

<span data-ttu-id="823fe-104">Nasıl modeli eğitme sonra kalitesini değerlendirmek?</span><span class="sxs-lookup"><span data-stu-id="823fe-104">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="823fe-105">Machine learning görev kalite değerlendirme için ölçümleri sunar.</span><span class="sxs-lookup"><span data-stu-id="823fe-105">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="823fe-106">Görevin karşılık gelen 'context', aşağıdaki örnekte olduğu gibi model değerlendirmek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="823fe-106">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```