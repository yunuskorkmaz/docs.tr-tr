---
title: ML.NET nasıl yapılacağını kılavuzları
description: Özel Yapay AI çözümleri oluşturma ve Machine Learning entegrasyonuile .NET uygulamalarınıza yardımcı olmak için belirli görevleri nasıl yapacağınızı öğrenin.
ms.date: 03/01/2019
ms.openlocfilehash: 4ce2de77c35062aa19449e3ba6bb3d5abd003d60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715663"
---
# <a name="net-machine-learning-how-to-guides"></a><span data-ttu-id="3015e-103">.NET Machine öğrenme nasıl yapılacağını kılavuzları</span><span class="sxs-lookup"><span data-stu-id="3015e-103">.NET Machine learning how-to guides</span></span>

<span data-ttu-id="3015e-104">ML.NET Kılavuzu'nun nasıl yapılacağını bölümünde, sık sorulan sorulara hızlı yanıtlar bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3015e-104">In the How to section of the ML.NET Guide, you can find quick answers to common questions.</span></span> <span data-ttu-id="3015e-105">Bazı durumlarda, makalelerin bulunmasını kolaylaştırmak için birden çok bölümde listelenebilir.</span><span class="sxs-lookup"><span data-stu-id="3015e-105">In some cases, articles may be listed in multiple sections to make them easy to find.</span></span>

## <a name="load-data"></a><span data-ttu-id="3015e-106">Veri yükleme</span><span class="sxs-lookup"><span data-stu-id="3015e-106">Load data</span></span>

* [<span data-ttu-id="3015e-107">Dosyalardan ve SQL veritabanlarından veri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="3015e-107">Load data from files and SQL databases.</span></span>](load-data-ml-net.md)

### <a name="prepare-the-data"></a><span data-ttu-id="3015e-108">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="3015e-108">Prepare the data</span></span>

* [<span data-ttu-id="3015e-109">Veri işlemede kullanılacak normalleştiricilerle önişlem eğitim verileri.</span><span class="sxs-lookup"><span data-stu-id="3015e-109">Preprocess training data with normalizers to use in data processing.</span></span>](normalizers-preprocess-data-ml-net.md)

## <a name="train-the-model"></a><span data-ttu-id="3015e-110">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="3015e-110">Train the model</span></span>

* [<span data-ttu-id="3015e-111">Çapraz doğrulama kullanarak bir makine öğrenme modeli eğitin.</span><span class="sxs-lookup"><span data-stu-id="3015e-111">Train a machine learning model using cross-validation.</span></span>](train-machine-learning-model-cross-validation-ml-net.md)

* [<span data-ttu-id="3015e-112">ML.NET kullanarak bir değeri tahmin etmek için bir regresyon modeli eğitin.</span><span class="sxs-lookup"><span data-stu-id="3015e-112">Train a regression model to predict a value using ML.NET.</span></span>](train-machine-learning-model-ml-net.md)

### <a name="evaluate-the-model-quality"></a><span data-ttu-id="3015e-113">Model kalitesini değerlendirme</span><span class="sxs-lookup"><span data-stu-id="3015e-113">Evaluate the model quality</span></span>

* [<span data-ttu-id="3015e-114">Model kalitesini değerlendirmek için ölçümleri hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="3015e-114">Calculate metrics to evaluate model quality.</span></span>](verify-model-quality-ml-net.md)

### <a name="model-explainability"></a><span data-ttu-id="3015e-115">Model açıklanabilirliği</span><span class="sxs-lookup"><span data-stu-id="3015e-115">Model explainability</span></span>

* [<span data-ttu-id="3015e-116">Permütasyon Özelliği Önemi olan modellerin özelliğinin önemini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="3015e-116">Determine the feature importance of models with Permutation Feature Importance.</span></span>](explain-machine-learning-model-permutation-feature-importance-ml-net.md)

* [<span data-ttu-id="3015e-117">Model açıklanabilirliği için Genelleştirilmiş Katkı Modelleri ve şekil işlevlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3015e-117">Use Generalized Additive Models and shape functions for model explainability.</span></span>](use-gams-for-model-explainability.md)

## <a name="run"></a><span data-ttu-id="3015e-118">Çalıştırın</span><span class="sxs-lookup"><span data-stu-id="3015e-118">Run</span></span>

* [<span data-ttu-id="3015e-119">ML.NET boru hattı işleme sırasında ara veri değerlerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="3015e-119">Inspect intermediate data values during ML.NET pipeline processing.</span></span>](inspect-intermediate-data-ml-net.md)

* [<span data-ttu-id="3015e-120">Eğitimli bir makine öğrenme modeli yükleyin.</span><span class="sxs-lookup"><span data-stu-id="3015e-120">Load a trained machine learning model.</span></span>](save-load-machine-learning-models-ml-net.md)

* [<span data-ttu-id="3015e-121">Eğitimli bir modelle tahminlerde bulunun.</span><span class="sxs-lookup"><span data-stu-id="3015e-121">Make predictions with a trained model.</span></span>](machine-learning-model-predictions-ml-net.md)

## <a name="probabilistic-infernet"></a><span data-ttu-id="3015e-122">Olasılıksal (Infer.NET)</span><span class="sxs-lookup"><span data-stu-id="3015e-122">Probabilistic (Infer.NET)</span></span>

* [<span data-ttu-id="3015e-123">Infer.NET ve olasılıksal programlama ile bir oyun maç listesi uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3015e-123">Create a game match up list app with Infer.NET and probabilistic programming.</span></span>](matchup-app-infer-net.md)
