---
title: Modelleri özellik önemini ML.NET özellik önemi permütasyon ile belirleme
description: Modelleri özellik önemini ML.NET özellik önemi permütasyon ile anlama
ms.date: 12/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 4b93e085dbb99e7f6f5a0a839b863aad1c69c7ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155461"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a>Modelleri özellik önemini ML.NET özellik önemi permütasyon ile belirleme

Makine öğrenimi modelleri oluştururken, bunu yalnızca tahminlerde bulunmak için yeterli değil genellikle. Genellikle, makine öğrenimi geliştiriciler, karar verenler ve bu modelleri tarafından etkilenen nasıl makine öğrenme modellerini kararlar ve performanslarını için hangi özelliklerin katkıda anlamanız gerekir. `Permutation Feature Importance` (PFI) Microsoft'ta makine öğrenme geliştiricilerin modelleri özellik önemini daha iyi anlamanıza yardımcı olmak için dahili olarak kullanılan bir model explainability aracıdır.

PFI olduğunu belirlemek için bir teknik **genel özellik önem** eğitilen makine öğrenimi modelinde motive içinde Breiman tarafından ["Rasgele ormanları" kağıt, Bölüm 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf). PFI soru sorarak özellik önem ölçer "bir özellik değerlerini bir rastgele ayarlanıp modeli üzerindeki etkisi ne olacağını * değeri?". PFI yöntemin avantajı modeli belirsiz olduğundan emin olup — verebilen herhangi bir model ile çalıştığını — ve bunu herhangi bir veri kümesi, yalnızca Eğitim kümesi özelliği önem hesaplamak için kullanabilirsiniz. Bu sayede özellik importances gibi bu grafiği oluşturmak için PFI gibi kullanabilirsiniz:

![PERMÜTASYON özellik önem grafiği](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model, data);
 
// Get the feature names from the training set
var featureNames = data.Schema.GetColumns()
                .Select(tuple => tuple.column.Name) // Get the column names
                .Where(name => name != labelName) // Drop the Label
                .ToArray();
 
// Write out the feature names and their importance to the model's R-squared value
for (int i = 0; i < featureNames.Length; i++)
  Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].rSquared:G4}");
```

Bir model özellik önemini çözümlemek için PFI kullanarak bir örnek için bkz. [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance.cs).

/ *, Tam olarak, ancak örnekler dizi derlenemiyor rastgele yanı sıra değil.
