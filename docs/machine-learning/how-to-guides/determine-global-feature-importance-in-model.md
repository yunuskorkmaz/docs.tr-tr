---
title: Modelleri özellik önemini ML.NET özellik önemi permütasyon ile belirleme
description: Modelleri özellik önemini ML.NET özellik önemi permütasyon ile anlama
ms.date: 12/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ebad89aaee1155d7c116b8536307756227dced31
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307116"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a><span data-ttu-id="4faa6-103">Modelleri özellik önemini ML.NET özellik önemi permütasyon ile belirleme</span><span class="sxs-lookup"><span data-stu-id="4faa6-103">Determine the feature importance of models with Permutation Feature Importance in ML.NET</span></span>

<span data-ttu-id="4faa6-104">Makine öğrenimi modelleri oluştururken, bunu yalnızca tahminlerde bulunmak için yeterli değil genellikle.</span><span class="sxs-lookup"><span data-stu-id="4faa6-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="4faa6-105">Genellikle, makine öğrenimi geliştiriciler, karar verenler ve bu modelleri tarafından etkilenen nasıl makine öğrenme modellerini kararlar ve performanslarını için hangi özelliklerin katkıda anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4faa6-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="4faa6-106">`Permutation Feature Importance` (PFI) Microsoft'ta makine öğrenme geliştiricilerin modelleri özellik önemini daha iyi anlamanıza yardımcı olmak için dahili olarak kullanılan bir model explainability aracıdır.</span><span class="sxs-lookup"><span data-stu-id="4faa6-106">`Permutation Feature Importance` (PFI) is a model explainability tool that is used internally at Microsoft to help machine learning developers better understand the feature importance of models.</span></span>

<span data-ttu-id="4faa6-107">PFI olduğunu belirlemek için bir teknik **genel özellik önem** eğitilen makine öğrenimi modelinde motive içinde Breiman tarafından ["Rasgele ormanları" kağıt, Bölüm 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span><span class="sxs-lookup"><span data-stu-id="4faa6-107">PFI is a technique to determine **global feature importance** in a trained machine learning model, motivated by Breiman in the ["Random Forests" paper, section 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span></span> <span data-ttu-id="4faa6-108">PFI soru sorarak özellik önem ölçer "bir özellik değerlerini bir rastgele ayarlanıp modeli üzerindeki etkisi ne olacağını \* değeri?".</span><span class="sxs-lookup"><span data-stu-id="4faa6-108">PFI measures feature importance by asking the question, "What would the effect on the model be if the values for a feature were set to a random\* value?".</span></span> <span data-ttu-id="4faa6-109">PFI yöntemin avantajı modeli belirsiz olduğundan emin olup — verebilen herhangi bir model ile çalıştığını — ve bunu herhangi bir veri kümesi, yalnızca Eğitim kümesi özelliği önem hesaplamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4faa6-109">The advantage of the PFI method is that it is model agnostic — it works with any model that can be evaluated — and it can use any dataset, not just the training set, to compute feature importance.</span></span> <span data-ttu-id="4faa6-110">Bu sayede özellik importances gibi bu grafiği oluşturmak için PFI gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4faa6-110">You can use PFI like so to produce feature importances like this graph:</span></span>

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

<span data-ttu-id="4faa6-112">Bir model özellik önemini çözümlemek için PFI kullanarak bir örnek için bkz. [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance).</span><span class="sxs-lookup"><span data-stu-id="4faa6-112">For a sample using PFI to analyze the feature importance of a model, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance).</span></span>

<span data-ttu-id="4faa6-113">/ \*, Tam olarak, ancak örnekler dizi derlenemiyor rastgele yanı sıra değil.</span><span class="sxs-lookup"><span data-stu-id="4faa6-113">/\* Well, not random exactly, but permuted across the set of examples.</span></span>
