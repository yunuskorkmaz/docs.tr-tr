---
title: Genelleştirilmiş eklenebilir modellerle ML.NET modellerini yorumlama
description: ML.NET içinde model yorumlenebilirliği için genelleştirilmiş ek modeller ve şekil işlevlerini kullanın
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 6df19eff4fec98c5815a9f8f4d8e4e9a80cba6ed
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092479"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a>ML.NET içinde model yorumlenebilirliği için genelleştirilmiş ek modeller ve şekil işlevlerini kullanın

Makine öğrenimi modelleri oluştururken, genellikle tahmin yapmak için yeterli değildir. Genellikle, makine öğrenimi geliştiricilerinin, karar mekanizmalarının ve modellerden etkilenen kullanıcıların, makine öğrenimi modellerinin kararlar vermesini ve hangi özelliklerin performansına katkıda bulunduğunu anlaması gerekir. **Genelleştirilmiş ek modeller (GAMs)** , makine öğrenimi geliştiricilerin başkaları tarafından kolayca yorumlanabilecek yüksek kapasiteli modeller oluşturmalarına yardımcı olmak üzere model yorumlanabilir için dahili olarak Microsoft 'ta kullanılır.

GAMs, koşulların tek bir değişkenin "şekil işlevleri" olarak adlandırılan doğrusal olmayan işlevler olduğu doğrusal modeller olan bir **yorumlı modellerden** oluşan bir sınıftır. Doğrusal modeller olarak kolayca yorumlanır, ancak modeller tek bir ağırlığa değil özelliklerin işlevlerini öğrendiklerinden basit bir doğrusal modelden daha karmaşık ilişkiler modelleyebilir. Elde edilen GAM tahmini, eğitim kümesi üzerinden ortalama tahminleri ve ortalama tahmine ait sapmayı temsil eden şekil işlevlerini temsil eden bir kesme dönemi içerir. Şekil işlevleri, bir özelliğin farklı değerlerine modelin yanıtını görmek için göz önünde görünebilir ve kod örneği sonunda oluşturulan aşağıdaki grafik gibi görselleştirilir. ML.net ' deki gam eğitmen, basit olmayan şekil işlevlerini öğrenmek için (örneğin Tree Stumps) ve Lou, Caruana ve Gehrke tarafından [sınıflandırma ve gerileme için okunaklı modellerle](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) tanımlanan yöntemi temel alır.

```csharp
// Train the Generalized Additive Model
var fitPipeline = pipeline.Fit(data);
var gamModel = fitPipeline.LastTransformer.Model;

// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
Console.WriteLine($"Average predicted cost: {intercept:0.00}");

// Get the column names from the training set
var columnNames = data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Get the index of a variable from the training data
var myFeatureIndex = columnNames.ToList().FindIndex(str => str.Equals("MyFeature"));

// The shape functions represent the deviation from the average prediction as a function of the feature value
// It is represented by a discrete set of bins
// First, get the array of bin upper bounds from the model for this feature
var myFeatureBins = gamModel.GetBinUpperBounds(myFeatureIndex);
// Then get the array of bin weights; these are the effect size for each bin
var myFeatureWeights = gamModel.GetBinEffects(myFeatureIndex);

// Write out the shape function for the feature (see the following figure for what this looks like)
for (int i = 0; i < myFeatureBins.Length; i++)
{
    Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
}
```

![Genelleştirilmiş eklenebilir modeller şekil işlevi grafiği](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

GAM modelini eğitme ve sonuçları İnceleme ve yorumlama hakkında bir örnek için bkz. [DotNet/machinöğrenim GitHub deposu](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).
