---
title: ML.NET Content Guide
description: Özel yapay ZEKA çözümleri oluşturmanıza ve bunları ML.NET kullanarak .NET uygulamalarınızla tümleştirin öğrenin.
ms.date: 01/18/2019
ms.custom: seodec18
ms.openlocfilehash: d80ba8ec2d563960242765f1ffbedec3e8882954
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550467"
---
# <a name="mlnet-content-guide"></a><span data-ttu-id="42092-103">ML.NET Content Guide</span><span class="sxs-lookup"><span data-stu-id="42092-103">ML.NET Content Guide</span></span>

<span data-ttu-id="42092-104">Bu kılavuzu temel kavramları açıklar ve öğreticileri ve API Başvurusu ML.NET ile çalışmak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="42092-104">This guide explains basic concepts and provides tutorials and an API reference for working with ML.NET.</span></span>

> [!NOTE]
> <span data-ttu-id="42092-105">Bu belge, şu anda Önizleme aşamasında olan ML.NET ifade eder.</span><span class="sxs-lookup"><span data-stu-id="42092-105">This documentation refers to ML.NET, which is currently in Preview.</span></span> <span data-ttu-id="42092-106">Malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="42092-106">Material may be subject to change.</span></span> <span data-ttu-id="42092-107">Daha fazla bilgi için [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="42092-107">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="get-started"></a><span data-ttu-id="42092-108">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="42092-108">Get started</span></span>

<span data-ttu-id="42092-109">Yükleme ve içinde ML.NET oluşturmaya başlamak için izleyin [başlangıç Öğreticisi](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span><span class="sxs-lookup"><span data-stu-id="42092-109">To install and start building in ML.NET, follow the [Get started tutorial](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span></span>

<span data-ttu-id="42092-110">ML.NET hakkında bilgi edinmek için [ML.NET nedir?](what-is-mldotnet.md)</span><span class="sxs-lookup"><span data-stu-id="42092-110">To learn about ML.NET, see [What is ML.NET?](what-is-mldotnet.md)</span></span>

<span data-ttu-id="42092-111">Temel bilgileri anlamak için bkz: [ML.NET eğitim modeli için temel kavramlar](basic-concepts-model-training-in-mldotnet.md).</span><span class="sxs-lookup"><span data-stu-id="42092-111">To understand basics, see [Basic concepts for model training in ML.NET](basic-concepts-model-training-in-mldotnet.md).</span></span>

## <a name="tutorials"></a><span data-ttu-id="42092-112">Öğreticiler</span><span class="sxs-lookup"><span data-stu-id="42092-112">Tutorials</span></span>

<span data-ttu-id="42092-113">[İkili sınıflandırma modelinde düşüncelerini çözümleme](tutorials/sentiment-analysis.md) yaklaşım pozitif veya negatif olup olmadığını belirleyen bir uygulamayı nasıl oluşturacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="42092-113">[Analyze sentiment using a binary classification model](tutorials/sentiment-analysis.md) shows you how to build an app that determines whether sentiment is positive or negative.</span></span>

<span data-ttu-id="42092-114">[Sınıflandırma bir çok sınıflı sınıflandırma modeli kullanarak GitHub sorunları](tutorials/github-issue-classification.md) bir GitHub sorunu alan etiketini belirleyen bir uygulamayı nasıl oluşturacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="42092-114">[Classify GitHub issues using a multiclass classification model](tutorials/github-issue-classification.md) shows you how to build an app that determines the Area label for a GitHub issue.</span></span>

<span data-ttu-id="42092-115">[Taksi taksi bir regresyon modeli kullanarak tahmin](tutorials/taxi-fare.md) faktörlerden geçmiş verilerden yanıt belirlemek için kullandığı Tahmine dayalı bir uygulamayı nasıl oluşturacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="42092-115">[Predict taxi fare using a regression model](tutorials/taxi-fare.md) shows you how to build a predictive app that uses many factors from historical data to determine the answer.</span></span>

<span data-ttu-id="42092-116">[Iris çiçek sınıflandırma özellikleri tarafından](tutorials/iris-clustering.md) kullanarak Iris veri kümesini analiz etmek için bir kümeleme modeli kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="42092-116">[Classify iris flowers by features](tutorials/iris-clustering.md) shows you how to use a clustering model to analyze the iris data set.</span></span> 

## <a name="how-to-guide"></a><span data-ttu-id="42092-117">Nasıl Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="42092-117">How to guide</span></span>

<span data-ttu-id="42092-118">[Infer.NET ve olasılığa dayalı programlama ile bir oyun eşleşme yukarı listesi uygulaması derleme](how-to-guides/matchup-app-infer-net.md) bir Xbox oyun göreceğiniz gibi bir eşleşme yukarı uygulaması basitleştirilmiş bir sürümünü oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="42092-118">[Build a game match-up list app with Infer.NET and probabilistic programming](how-to-guides/matchup-app-infer-net.md) shows you how to build a simplified version of a match-up app like you'd see in an Xbox game.</span></span>

## <a name="resources"></a><span data-ttu-id="42092-119">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="42092-119">Resources</span></span>

<span data-ttu-id="42092-120">[Machine learning sözlüğü](resources/glossary.md) önemli terimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="42092-120">[Machine learning glossary](resources/glossary.md) defines key terminology.</span></span>

<span data-ttu-id="42092-121">[Makine öğrenimi görevlerini](resources/tasks.md) sınıflandırma ve anomali algılama gibi görevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="42092-121">[Machine learning tasks](resources/tasks.md) describes tasks, such as classification and anomaly detection.</span></span> 

<span data-ttu-id="42092-122">[Veri Dönüşümleri](resources/transforms.md) ML.NET veri hazırlama özelliklerinde açıklar.</span><span class="sxs-lookup"><span data-stu-id="42092-122">[Data transforms](resources/transforms.md) describes data preparation capabilities in ML.NET.</span></span>


## <a name="api-reference"></a><span data-ttu-id="42092-123">API başvurusu</span><span class="sxs-lookup"><span data-stu-id="42092-123">API reference</span></span>

<span data-ttu-id="42092-124">[ML.NET API Başvurusu](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) mevcut API'lere derecesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="42092-124">[ML.NET API Reference](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) describes the breadth of APIs available.</span></span>
