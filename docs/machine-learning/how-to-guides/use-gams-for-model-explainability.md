---
title: Model explainability için genelleştirilmiş ekleme modellerini ve şekil işlevlerini kullanma
description: ML.NET içinde model explainability için genelleştirilmiş ekleme modellerini ve şekil işlevlerini kullanma
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: c58cf823007196c35da093fab7423c1e40ba1158
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855609"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a>ML.NET içinde model explainability için genelleştirilmiş ekleme modellerini ve şekil işlevlerini kullanma

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET 'e başvurur ve malzemeler değişebilir. Daha fazla bilgi için [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) sayfasını ziyaret edin.

Bu nasıl yapılır ve ilgili örnek şu anda **ml.NET sürüm 0,10**kullanıyor. Daha fazla bilgi için [DotNet/Machine-posta GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)depolarındaki sürüm notlarına bakın.

Makine öğrenimi modelleri oluştururken, genellikle tahmin yapmak için yeterli değildir. Genellikle, makine öğrenimi geliştiricilerinin, karar mekanizmalarının ve modellerden etkilenen kullanıcıların, makine öğrenimi modellerinin kararlar vermesini ve hangi özelliklerin performansına katkıda bulunduğunu anlaması gerekir. Machine Learning geliştiricilerinin, başkaları tarafından kolayca yorumlanabilecek yüksek kapasiteli modeller oluşturmalarına yardımcı olmak üzere, Microsoft model explainability için dahili olarak Microsoft 'ta **Genelleştirilmiş ek modeller (GAMs)** kullanılır.

GAMs, koşulların tek bir değişkenin "şekil işlevleri" olarak adlandırılan doğrusal olmayan işlevler olduğu doğrusal modeller olan bir **yorumlı modellerden** oluşan bir sınıftır. Doğrusal modeller olarak kolayca yorumlanır, ancak modeller tek bir ağırlığa değil özelliklerin işlevlerini öğrendiklerinden basit bir doğrusal modelden daha karmaşık ilişkiler modelleyebilir. Elde edilen GAM tahmini, eğitim kümesi üzerinden ortalama tahminleri ve ortalama tahmine ait sapmayı temsil eden şekil işlevlerini temsil eden bir kesme dönemi içerir. Şekil işlevleri, bir özelliğin farklı değerlerine modelin yanıtını görmek için göz önünde görünebilir ve kod örneği sonunda oluşturulan aşağıdaki grafik gibi görselleştirilir. ML.net ' deki gam eğitmen, basit olmayan şekil işlevlerini öğrenmek için (örneğin Tree Stumps) ve Lou tarafından [sınıflandırma ve gerileme için anlaşılır modellerle](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) tanımlanan yöntemi temel alarak, Caruana ve Gehrke.

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
