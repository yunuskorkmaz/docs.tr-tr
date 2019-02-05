---
title: ML.NET içindeki model explainability için genelleştirilmiş eklenebilir modelleri ve Şekil işlevleri kullanın
description: ML.NET içindeki model explainability için genelleştirilmiş eklenebilir modelleri ve Şekil işlevleri kullanın
ms.date: 02/01/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 7899c0efb80af178ec4fa8623b0712eb9e438e43
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738896"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a><span data-ttu-id="b0ad9-103">ML.NET içindeki model explainability için genelleştirilmiş eklenebilir modelleri ve Şekil işlevleri kullanın</span><span class="sxs-lookup"><span data-stu-id="b0ad9-103">Use Generalized Additive Models and shape functions for model explainability in ML.NET</span></span>

<span data-ttu-id="b0ad9-104">Makine öğrenimi modelleri oluştururken, bunu yalnızca tahminlerde bulunmak için yeterli değil genellikle.</span><span class="sxs-lookup"><span data-stu-id="b0ad9-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="b0ad9-105">Genellikle, makine öğrenimi geliştiriciler, karar verenler ve bu modelleri tarafından etkilenen nasıl makine öğrenme modellerini kararlar ve performanslarını için hangi özelliklerin katkıda anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0ad9-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="b0ad9-106">**Eklenebilir modelleri (GAMs) genelleştirilmiş** dahili olarak model explainability için Microsoft machine learning geliştiriciler başkaları tarafından kolayca yorumlanabilir yüksek kapasiteli modelleri oluşturma yardımcı olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b0ad9-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model explainability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="b0ad9-107">GAMs olan bir sınıfı **yorumlanabilen modelleri** koşulları doğrusal olmayan işlevler, "işlevleri tek bir değişken, Şekil" olarak adlandırılan nerede Doğrusal Model olan.</span><span class="sxs-lookup"><span data-stu-id="b0ad9-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="b0ad9-108">Doğrusal Model kolayca yorumlanır ancak modelleri işlevleri yerine tek bir ağırlık özellikleri öğrenmek için basit bir Doğrusal model değerinden daha karmaşık ilişkileri modelleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0ad9-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="b0ad9-109">Sonuçta elde edilen GAM tahmini Ortalama tahmin Eğitim kümesi ve Ortalama tahmin sapma temsil eden şekle işlevleri temsil eden bir kesme noktası terim sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b0ad9-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="b0ad9-110">Şekil işlevleri farklı bir özellik değerlerini modelinin yanıtı görmek için göz tarafından inceledi ve kod örneği sonunda oluşturulan grafiğin aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="b0ad9-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="b0ad9-111">ML.NET içinde GAM Eğitmeni gradyan artırmalı ağaçlarının sığ nonparametric şekli işlevleri öğrenin (örneğin ağacı stumps) kullanılarak uygulanır ve açıklanan yöntemi dayalı [sınıflandırma ve regresyonanlaşılırmodelleri](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) Lou Caruana ve Gehrke tarafından.</span><span class="sxs-lookup"><span data-stu-id="b0ad9-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

```csharp
// Train the Generalized Additive Model
var fitPipeline = pipeline.Fit(data);
var gamModel = fitPipeline.LastTransformer.Model;

// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
Console.WriteLine($"Average predicted cost: {intercept:0.00}");

// Get the feature names from the training set
var featureNames = data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Get the index of a variable from the training data
var myFeatureIndex = featureNames.ToList().FindIndex(str => str.Equals("MyFeature"));

// The shape functions represent the deviation from the average prediction as a function of the feature value
// It is represented by a discrete set of bins
// First, get the array of bin upper bounds from the model for this feature
var myFeatureBins = gamModel.GetFeatureBinUpperBounds(myFeatureIndex);
// Then get the array of bin weights; these are the effect size for each bin
var myFeatureWeights = gamModel.GetFeatureWeights(myFeatureIndex);

// Write out the shape function for the feature (see the following figure for what this looks like)
for (int i = 0; i < myFeatureBins.Length; i++)
{
    Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
}
```

![Genelleştirilmiş eklenebilir modelleri şekli işlevi grafiği](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

<span data-ttu-id="b0ad9-113">GAM modeli eğitmek ve sonuçları yorumlamanıza incelemek nasıl bir örnek için bkz: [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span><span class="sxs-lookup"><span data-stu-id="b0ad9-113">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>