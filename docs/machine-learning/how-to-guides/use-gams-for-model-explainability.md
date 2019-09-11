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
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a><span data-ttu-id="ddc6b-103">ML.NET içinde model explainability için genelleştirilmiş ekleme modellerini ve şekil işlevlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="ddc6b-103">Use Generalized Additive Models and shape functions for model explainability in ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="ddc6b-104">Bu konu, şu anda önizleme aşamasında olan ML.NET 'e başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="ddc6b-105">Daha fazla bilgi için [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) sayfasını ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="ddc6b-106">Bu nasıl yapılır ve ilgili örnek şu anda **ml.NET sürüm 0,10**kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="ddc6b-107">Daha fazla bilgi için [DotNet/Machine-posta GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)depolarındaki sürüm notlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="ddc6b-108">Makine öğrenimi modelleri oluştururken, genellikle tahmin yapmak için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-108">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="ddc6b-109">Genellikle, makine öğrenimi geliştiricilerinin, karar mekanizmalarının ve modellerden etkilenen kullanıcıların, makine öğrenimi modellerinin kararlar vermesini ve hangi özelliklerin performansına katkıda bulunduğunu anlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-109">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="ddc6b-110">Machine Learning geliştiricilerinin, başkaları tarafından kolayca yorumlanabilecek yüksek kapasiteli modeller oluşturmalarına yardımcı olmak üzere, Microsoft model explainability için dahili olarak Microsoft 'ta **Genelleştirilmiş ek modeller (GAMs)** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-110">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model explainability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="ddc6b-111">GAMs, koşulların tek bir değişkenin "şekil işlevleri" olarak adlandırılan doğrusal olmayan işlevler olduğu doğrusal modeller olan bir **yorumlı modellerden** oluşan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-111">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="ddc6b-112">Doğrusal modeller olarak kolayca yorumlanır, ancak modeller tek bir ağırlığa değil özelliklerin işlevlerini öğrendiklerinden basit bir doğrusal modelden daha karmaşık ilişkiler modelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-112">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="ddc6b-113">Elde edilen GAM tahmini, eğitim kümesi üzerinden ortalama tahminleri ve ortalama tahmine ait sapmayı temsil eden şekil işlevlerini temsil eden bir kesme dönemi içerir.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-113">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="ddc6b-114">Şekil işlevleri, bir özelliğin farklı değerlerine modelin yanıtını görmek için göz önünde görünebilir ve kod örneği sonunda oluşturulan aşağıdaki grafik gibi görselleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-114">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="ddc6b-115">ML.net ' deki gam eğitmen, basit olmayan şekil işlevlerini öğrenmek için (örneğin Tree Stumps) ve Lou tarafından [sınıflandırma ve gerileme için anlaşılır modellerle](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) tanımlanan yöntemi temel alarak, Caruana ve Gehrke.</span><span class="sxs-lookup"><span data-stu-id="ddc6b-115">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

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

<span data-ttu-id="ddc6b-117">GAM modelini eğitme ve sonuçları İnceleme ve yorumlama hakkında bir örnek için bkz. [DotNet/machinöğrenim GitHub deposu](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span><span class="sxs-lookup"><span data-stu-id="ddc6b-117">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>
