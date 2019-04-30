---
title: Eğitilen makine öğrenme uygulamaları - ML.NET modeli kullanıma hazır hale getirme
description: ML.NET eğitilen ve değerlendirilen makine öğrenme modeli uygulamalarında kullanmak için nasıl kullanılacağını keşfedin
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: be6906c939b82d00067babaeebe809dae3de413a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650433"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a>Eğitilen makine öğrenme uygulamaları - ML.NET modeli kullanıma hazır hale getirme

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**. Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning github deposu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)

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
