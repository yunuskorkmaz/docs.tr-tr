---
title: Genelleştirilmiş Katkı Modelleri ile ML.NET modelleri yorumlayın
description: ML.NET model yorumlanabilirliği için Genelleştirilmiş Katkı Modelleri ve şekil fonksiyonlarını kullanın
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 6df19eff4fec98c5815a9f8f4d8e4e9a80cba6ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092479"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a>ML.NET model yorumlanabilirliği için Genelleştirilmiş Katkı Modelleri ve şekil fonksiyonlarını kullanın

Makine öğrenme modelleri oluştururken, genellikle sadece tahminler yapmak için yeterli değildir. Genellikle, makine öğrenimi geliştiricileri, karar vericiler ve modellerden etkilenenlerin, makine öğrenimi modellerinin nasıl karar lar verdiği ve hangi özelliklerin performanslarına katkıda bulunduğu anlamak gerekir. **Genelleştirilmiş Katkı Modelleri (GAM'ler),** makine öğrenimi geliştiricilerin başkaları tarafından kolayca yorumlanabilecek yüksek kapasiteli modeller oluşturmalarına yardımcı olmak için model yorumlanabilirliği için Microsoft'ta dahili olarak kullanılır.

GAM'lar, terimlerin tek bir değişkenin "şekil işlevleri" olarak adlandırılan doğrusal olmayan işlevler olduğu doğrusal modeller olan **yorumlanabilir modeller** sınıfıdır. Doğrusal modeller olarak kolayca yorumlanırlar, ancak modeller tek bir ağırlık yerine özelliklerin işlevlerini öğrendikleri için, basit bir doğrusal modelden daha karmaşık ilişkiler modelleyebilirler. Elde edilen GAM tahmincisi, eğitim kümesi üzerindeki ortalama tahmini temsil eden bir kesme terimine ve ortalama tahminden sapmayı temsil eden şekil işlevlerine sahiptir. Şekil işlevleri, modelin bir özelliğin farklı değerlerine verdiği yanıtı görmek için gözle incelenebilir ve kod örneğinin sonunda oluşturulan aşağıdaki grafik gibi görselleştirilebilir. ML.NET'daki GAM eğitmeni, parametrik olmayan şekil fonksiyonlarını öğrenmek için sığ degrade artırılmış ağaçlar (örneğin ağaç kütükleri) kullanılarak uygulanır ve Lou, Caruana ve Gehrke tarafından [Sınıflandırma ve Regresyon için Intelligible Modeller'de](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) açıklanan yönteme dayanır.

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

![Jeneralize Katkı Modelleri şekil fonksiyonu grafiği](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

Gam modelini nasıl eğiteceğimiz ve sonuçları nasıl inceleyip yorumlanacağına bir örnek [için, dotnet/machinelearning GitHub deposuna](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs)bakın.
