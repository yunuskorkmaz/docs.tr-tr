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
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a>Eğitilen makine öğrenme uygulamaları - ML.NET modeli kullanıma hazır hale getirme

Model ölçümler için iyi baktığınızda, zaman 'modeli hazır hale getirmek için ' dir. `model` Oluşturulan nesne kullanılabilir, kalıcı ve onu 'öğrenilen' eğitim sırasında aynı adımları uygulayarak farklı ortamlarda yeniden kullanılan.

Model bir dosyaya kaydedin ve (büyük olasılıkla farklı bir bağlamda) yeniden yüklemek için aşağıdaki örneği kullanın:

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
