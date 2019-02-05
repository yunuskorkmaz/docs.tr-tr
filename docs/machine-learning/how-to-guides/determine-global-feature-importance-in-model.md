---
title: Modelleri özellik önemini ML.NET özellik önemi permütasyon ile belirleme
description: Modelleri özellik önemini ML.NET özellik önemi permütasyon ile anlama
ms.date: 02/01/2019
ms.custom: mvc,how-to
ms.openlocfilehash: a61e5dbbd544aa7df56291db9207343cb6f03e6e
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738818"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a>Modelleri özellik önemini ML.NET özellik önemi permütasyon ile belirleme

Makine öğrenimi modelleri oluştururken, bunu yalnızca tahminlerde bulunmak için yeterli değil genellikle. Genellikle, makine öğrenimi geliştiriciler, karar verenler ve bu modelleri tarafından etkilenen nasıl makine öğrenme modellerini kararlar ve performanslarını için hangi özelliklerin katkıda anlamanız gerekir. `Permutation Feature Importance` (PFI) Microsoft'ta makine öğrenme geliştiricilerin modelleri özellik önemini daha iyi anlamanıza yardımcı olmak için dahili olarak kullanılan bir model explainability aracıdır.

PFI olduğunu belirlemek için bir teknik **genel özellik önem** eğitilen makine öğrenimi modelinde motive içinde Breiman tarafından ["Rasgele ormanları" kağıt, Bölüm 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf). PFI soru sorarak özellik önem ölçer "bir özellik değerlerini bir rastgele ayarlanıp modeli üzerindeki etkisi ne olacağını * değeri?". PFI yöntemin avantajı modeli belirsiz olduğundan emin olup — verebilen herhangi bir model ile çalıştığını — ve bunu herhangi bir veri kümesi, yalnızca Eğitim kümesi özelliği önem hesaplamak için kullanabilirsiniz. Bu sayede özellik importances gibi bu grafiği oluşturmak için PFI gibi kullanabilirsiniz:

![PERMÜTASYON özellik önem grafiği](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model.LastTransformer, model.Transform(data), "MedianHomeValue");

// Get the feature names from the training set
var featureNames =
    data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Write out the feature names and their importance to the model's Mean R-squared value
for (int i = 0; i < featureNames.Length;i++)
{
    Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].RSquared.Mean:G4}");
}
```

Bir model özellik önemini çözümlemek için PFI kullanarak bir örnek için bkz. [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance).

/ *, Tam olarak, ancak örnekler dizi derlenemiyor rastgele yanı sıra değil.
