---
title: Eğitilen makine öğrenme uygulamaları - ML.NET modeli kullanıma hazır hale getirme
description: ML.NET eğitilen ve değerlendirilen makine öğrenme modeli uygulamalarında kullanmak için nasıl kullanılacağını keşfedin
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ff3f0a8856382d020129693bcf722f572fd87606
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131572"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a><span data-ttu-id="ec1ed-103">Eğitilen makine öğrenme uygulamaları - ML.NET modeli kullanıma hazır hale getirme</span><span class="sxs-lookup"><span data-stu-id="ec1ed-103">Operationalize a trained machine learning model in apps - ML.NET</span></span>

<span data-ttu-id="ec1ed-104">Model ölçümler için iyi baktığınızda, zaman 'modeli hazır hale getirmek için ' dir.</span><span class="sxs-lookup"><span data-stu-id="ec1ed-104">When the model metrics look good to you, it's time to 'operationalize' the model.</span></span> <span data-ttu-id="ec1ed-105">`model` Oluşturulan nesne kullanılabilir, kalıcı ve onu 'öğrenilen' eğitim sırasında aynı adımları uygulayarak farklı ortamlarda yeniden kullanılan.</span><span class="sxs-lookup"><span data-stu-id="ec1ed-105">The `model` object you built can be consumed, persisted, and reused in different environments, applying the same steps that it 'learned' during training.</span></span>

<span data-ttu-id="ec1ed-106">Model bir dosyaya kaydedin ve (büyük olasılıkla farklı bir bağlamda) yeniden yüklemek için aşağıdaki örneği kullanın:</span><span class="sxs-lookup"><span data-stu-id="ec1ed-106">To save the model to a file, and reload it (potentially in a different context), use the following example:</span></span>

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
