---
title: Eğitilen makine öğrenme uygulamaları - ML.NET modeli kullanıma hazır hale getirme
description: ML.NET eğitilen ve değerlendirilen makine öğrenme modeli uygulamalarında kullanmak için nasıl kullanılacağını keşfedin
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: be6906c939b82d00067babaeebe809dae3de413a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675140"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a><span data-ttu-id="e9531-103">Eğitilen makine öğrenme uygulamaları - ML.NET modeli kullanıma hazır hale getirme</span><span class="sxs-lookup"><span data-stu-id="e9531-103">Operationalize a trained machine learning model in apps - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="e9531-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="e9531-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="e9531-105">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e9531-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="e9531-106">Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="e9531-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="e9531-107">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning github deposu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="e9531-107">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="e9531-108">Model ölçümler için iyi baktığınızda, zaman 'modeli hazır hale getirmek için ' dir.</span><span class="sxs-lookup"><span data-stu-id="e9531-108">When the model metrics look good to you, it's time to 'operationalize' the model.</span></span> <span data-ttu-id="e9531-109">`model` Oluşturulan nesne kullanılabilir, kalıcı ve onu 'öğrenilen' eğitim sırasında aynı adımları uygulayarak farklı ortamlarda yeniden kullanılan.</span><span class="sxs-lookup"><span data-stu-id="e9531-109">The `model` object you built can be consumed, persisted, and reused in different environments, applying the same steps that it 'learned' during training.</span></span>

<span data-ttu-id="e9531-110">Model bir dosyaya kaydedin ve (büyük olasılıkla farklı bir bağlamda) yeniden yüklemek için aşağıdaki örneği kullanın:</span><span class="sxs-lookup"><span data-stu-id="e9531-110">To save the model to a file, and reload it (potentially in a different context), use the following example:</span></span>

```csharp
using (var stream = File.Create(modelPath))
{
    // Saving and loading happens to 'dynamic' models.
    mlContext.Model.Save(model, stream);
}

// Potentially, the lines below can be in a different process altogether.

// When you load the model, it's a transformer.
ITransformer loadedModel;
using (var stream = File.OpenRead(modelPath))
    loadedModel = mlContext.Model.Load(stream);
```
