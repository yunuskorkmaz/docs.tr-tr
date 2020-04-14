---
title: Genelleştirilmiş Katkı Modelleri ile ML.NET modelleri yorumlayın
description: ML.NET model yorumlanabilirliği için Genelleştirilmiş Katkı Modelleri ve şekil fonksiyonlarını kullanın
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 29eac7a609ada57283a7c5b55b935e30709930dd
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243134"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a><span data-ttu-id="1dac8-103">ML.NET model yorumlanabilirliği için Genelleştirilmiş Katkı Modelleri ve şekil fonksiyonlarını kullanın</span><span class="sxs-lookup"><span data-stu-id="1dac8-103">Use Generalized Additive Models and shape functions for model interpretability in ML.NET</span></span>

<span data-ttu-id="1dac8-104">Makine öğrenme modelleri oluştururken, genellikle sadece tahminler yapmak için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="1dac8-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="1dac8-105">Genellikle, makine öğrenimi geliştiricileri, karar vericiler ve modellerden etkilenenlerin, makine öğrenimi modellerinin nasıl karar lar verdiği ve hangi özelliklerin performanslarına katkıda bulunduğu anlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="1dac8-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="1dac8-106">**Genelleştirilmiş Katkı Modelleri (GAM'ler),** makine öğrenimi geliştiricilerin başkaları tarafından kolayca yorumlanabilecek yüksek kapasiteli modeller oluşturmalarına yardımcı olmak için model yorumlanabilirliği için Microsoft'ta dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1dac8-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model interpretability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="1dac8-107">GAM'lar, terimlerin tek bir değişkenin "şekil işlevleri" olarak adlandırılan doğrusal olmayan işlevler olduğu doğrusal modeller olan **yorumlanabilir modeller** sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="1dac8-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="1dac8-108">Doğrusal modeller olarak kolayca yorumlanırlar, ancak modeller tek bir ağırlık yerine özelliklerin işlevlerini öğrendikleri için, basit bir doğrusal modelden daha karmaşık ilişkiler modelleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="1dac8-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="1dac8-109">Elde edilen GAM tahmincisi, eğitim kümesi üzerindeki ortalama tahmini temsil eden bir kesme terimine ve ortalama tahminden sapmayı temsil eden şekil işlevlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1dac8-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="1dac8-110">Şekil işlevleri, modelin bir özelliğin farklı değerlerine verdiği yanıtı görmek için gözle incelenebilir ve kod örneğinin sonunda oluşturulan aşağıdaki grafik gibi görselleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1dac8-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="1dac8-111">ML.NET'daki GAM eğitmeni, parametrik olmayan şekil fonksiyonlarını öğrenmek için sığ degrade artırılmış ağaçlar (örneğin ağaç kütükleri) kullanılarak uygulanır ve Lou, Caruana ve Gehrke tarafından [Sınıflandırma ve Regresyon için Intelligible Modeller'de](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) açıklanan yönteme dayanır.</span><span class="sxs-lookup"><span data-stu-id="1dac8-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

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

<span data-ttu-id="1dac8-113">Gam modelini nasıl eğitirin ve sonuçları incelemek ve yorumlamak için bir örnek için, [ikili sınıflandırma eğitmeni örneğine](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/Trainers/BinaryClassification/Gam.cs)bakın.</span><span class="sxs-lookup"><span data-stu-id="1dac8-113">For an example of how to train a GAM model and inspect and interpret the results, see the [binary classification trainer sample](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/Trainers/BinaryClassification/Gam.cs).</span></span>
