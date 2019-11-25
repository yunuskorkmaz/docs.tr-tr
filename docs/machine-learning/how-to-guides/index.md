---
title: ML.NET nasıl yapılır kılavuzlarını
description: Özel AI çözümleri oluşturma ve .NET uygulamalarınıza tümleştirme Machine Learning konusunda yardımcı olmak üzere belirli görevleri nasıl gerçekleştireceğinizi öğrenin.
ms.custom: seodec18
ms.date: 03/01/2019
ms.openlocfilehash: e2b4ff77c7f76282d70c06b5ef534306fe4e93a6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977105"
---
# <a name="net-machine-learning-how-to-guides"></a><span data-ttu-id="d200c-103">.NET Machine Learning nasıl yapılır kılavuzlarından</span><span class="sxs-lookup"><span data-stu-id="d200c-103">.NET Machine learning how-to guides</span></span>

<span data-ttu-id="d200c-104">ML.NET kılavuzunun nasıl yapılır bölümünde yaygın soruların hızlı yanıtlarını bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d200c-104">In the How to section of the ML.NET Guide, you can find quick answers to common questions.</span></span> <span data-ttu-id="d200c-105">Bazı durumlarda, makaleleri bulmayı kolaylaştırmak için birden çok bölümde listelenebilir.</span><span class="sxs-lookup"><span data-stu-id="d200c-105">In some cases, articles may be listed in multiple sections to make them easy to find.</span></span>

## <a name="load-data"></a><span data-ttu-id="d200c-106">Veri yükleme</span><span class="sxs-lookup"><span data-stu-id="d200c-106">Load data</span></span>

* [<span data-ttu-id="d200c-107">Dosyaları ve SQL veritabanlarından verileri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d200c-107">Load data from files and SQL databases.</span></span>](load-data-ml-net.md)

### <a name="prepare-the-data"></a><span data-ttu-id="d200c-108">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="d200c-108">Prepare the data</span></span>

* [<span data-ttu-id="d200c-109">Veri işlemede kullanılacak normalde eğitim verilerini önceden işleyin.</span><span class="sxs-lookup"><span data-stu-id="d200c-109">Preprocess training data with normalizers to use in data processing.</span></span>](normalizers-preprocess-data-ml-net.md)

## <a name="train-the-model"></a><span data-ttu-id="d200c-110">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="d200c-110">Train the model</span></span>

* [<span data-ttu-id="d200c-111">Çapraz doğrulama kullanarak makine öğrenimi modelini eğitme.</span><span class="sxs-lookup"><span data-stu-id="d200c-111">Train a machine learning model using cross-validation.</span></span>](train-machine-learning-model-cross-validation-ml-net.md)

* [<span data-ttu-id="d200c-112">ML.NET kullanarak bir değer tahmin etmek için regresyon modeli eğitme.</span><span class="sxs-lookup"><span data-stu-id="d200c-112">Train a regression model to predict a value using ML.NET.</span></span>](train-machine-learning-model-ml-net.md)

### <a name="evaluate-the-model-quality"></a><span data-ttu-id="d200c-113">Model kalitesini değerlendirin</span><span class="sxs-lookup"><span data-stu-id="d200c-113">Evaluate the model quality</span></span>

* [<span data-ttu-id="d200c-114">Model kalitesini değerlendirmek için ölçümleri hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="d200c-114">Calculate metrics to evaluate model quality.</span></span>](verify-model-quality-ml-net.md)

### <a name="model-explainability"></a><span data-ttu-id="d200c-115">Model explainability</span><span class="sxs-lookup"><span data-stu-id="d200c-115">Model explainability</span></span>

* [<span data-ttu-id="d200c-116">Permütasyon özelliği önem derecesine sahip modellerin Özellik önemini saptayın.</span><span class="sxs-lookup"><span data-stu-id="d200c-116">Determine the feature importance of models with Permutation Feature Importance.</span></span>](explain-machine-learning-model-permutation-feature-importance-ml-net.md)

* [<span data-ttu-id="d200c-117">Explainability modeli için genelleştirilmiş ekleme modellerini ve şekil işlevlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d200c-117">Use Generalized Additive Models and shape functions for model explainability.</span></span>](use-gams-for-model-explainability.md)

## <a name="run"></a><span data-ttu-id="d200c-118">Çalıştır</span><span class="sxs-lookup"><span data-stu-id="d200c-118">Run</span></span>

* [<span data-ttu-id="d200c-119">ML.NET işlem hattı işleme sırasında Ara veri değerlerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="d200c-119">Inspect intermediate data values during ML.NET pipeline processing.</span></span>](inspect-intermediate-data-ml-net.md)

* [<span data-ttu-id="d200c-120">Eğitilen bir makine öğrenme modeli yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d200c-120">Load a trained machine learning model.</span></span>](save-load-machine-learning-models-ml-net.md)

* [<span data-ttu-id="d200c-121">Eğitilen bir modelle tahminlere sahip olun.</span><span class="sxs-lookup"><span data-stu-id="d200c-121">Make predictions with a trained model.</span></span>](machine-learning-model-predictions-ml-net.md)

## <a name="probabilistic-infernet"></a><span data-ttu-id="d200c-122">Dayalı (Infer.NET)</span><span class="sxs-lookup"><span data-stu-id="d200c-122">Probabilistic (Infer.NET)</span></span>

* [<span data-ttu-id="d200c-123">Infer.NET ve dayalı programlamasında bir oyun eşleşmesi liste uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d200c-123">Create a game match up list app with Infer.NET and probabilistic programming.</span></span>](matchup-app-infer-net.md)
