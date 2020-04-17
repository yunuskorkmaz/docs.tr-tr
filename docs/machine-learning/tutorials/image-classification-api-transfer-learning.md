---
title: 'Öğretici: Transfer öğrenmeyi kullanarak otomatik görsel denetim'
description: Bu öğretici, somut yüzeylerin görüntülerini çatlak veya çatlak olarak sınıflandırmak için görüntü algılama API'sini kullanarak ML.NET'da bir TensorFlow derin öğrenme modelini eğitmek için transfer öğreniminin nasıl kullanılacağını göstermektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a050d7673f7ef00cf11d959d04e709222cb2be8f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607564"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="a4702-103">Öğretici: ML.NET Görüntü Sınıflandırma API ile transfer öğrenme kullanarak otomatik görsel denetim</span><span class="sxs-lookup"><span data-stu-id="a4702-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="a4702-104">Somut yüzeylerin görüntülerini çatlak veya kırılmamış olarak sınıflandırmak için transfer öğrenimini, önceden eğitilmiş tensorflow modelini ve ML.NET Görüntü Sınıflandırma API'sini kullanarak özel bir derin öğrenme modelini nasıl eğittiğizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="a4702-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="a4702-105">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="a4702-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a4702-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="a4702-106">Understand the problem</span></span>
> - <span data-ttu-id="a4702-107">ML.NET Resim Sınıflandırma API'si hakkında bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="a4702-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="a4702-108">Önceden eğitilmiş modeli anlama</span><span class="sxs-lookup"><span data-stu-id="a4702-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="a4702-109">Özel bir TensorFlow görüntü sınıflandırma modelini eğitmek için transfer öğrenimini kullanma</span><span class="sxs-lookup"><span data-stu-id="a4702-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="a4702-110">Özel modelle görüntüleri sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="a4702-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a4702-111">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="a4702-111">Prerequisites</span></span>

- <span data-ttu-id="a4702-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonrası veya Visual Studio 2017 sürümü 15.6 veya daha sonra ".NET Core çapraz platform geliştirme" iş yükü yüklü.</span><span class="sxs-lookup"><span data-stu-id="a4702-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="a4702-113">Görüntü sınıflandırma transferi öğrenme örneği genel bakış</span><span class="sxs-lookup"><span data-stu-id="a4702-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="a4702-114">Bu örnek, önceden eğitilmiş derin öğrenme TensorFlow modelini kullanarak görüntüleri sınıflandıran bir C# .NET Core konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a4702-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="a4702-115">Bu örneğin kodu GitHub'daki [dotnet/machinelearning-samples deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="a4702-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="a4702-116">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="a4702-116">Understand the problem</span></span>

<span data-ttu-id="a4702-117">Görüntü sınıflandırması bir bilgisayar görme sorunudur.</span><span class="sxs-lookup"><span data-stu-id="a4702-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="a4702-118">Görüntü sınıflandırması bir görüntüyü girdi olarak alır ve öngörülen sınıfa kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="a4702-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="a4702-119">Görüntü sınıflandırmanın yararlı olduğu bazı senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a4702-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="a4702-120">Yüz tanıma</span><span class="sxs-lookup"><span data-stu-id="a4702-120">Facial recognition</span></span>
- <span data-ttu-id="a4702-121">Duygu algılama</span><span class="sxs-lookup"><span data-stu-id="a4702-121">Emotion detection</span></span>
- <span data-ttu-id="a4702-122">Tıbbi tanı</span><span class="sxs-lookup"><span data-stu-id="a4702-122">Medical diagnosis</span></span>
- <span data-ttu-id="a4702-123">Yer işareti algılama</span><span class="sxs-lookup"><span data-stu-id="a4702-123">Landmark detection</span></span>

<span data-ttu-id="a4702-124">Bu öğretici, çatlaklardan zarar gören yapıları belirlemek için köprü güvertelerinin otomatik görsel denetimini gerçekleştirmek için özel bir görüntü sınıflandırma modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="a4702-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="a4702-125">ML.NET Görüntü Sınıflandırma API</span><span class="sxs-lookup"><span data-stu-id="a4702-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="a4702-126">ML.NET görüntü sınıflandırması gerçekleştirmenin çeşitli yollarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4702-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="a4702-127">Bu öğretici, Görüntü Sınıflandırma API'sini kullanarak aktarım öğrenimi uygular.</span><span class="sxs-lookup"><span data-stu-id="a4702-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="a4702-128">Görüntü Sınıflandırma API' si, TensorFlow C++ API için C# bağlamaları sağlayan düşük seviyeli bir kitaplık olan [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET)kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4702-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="a4702-129">Transfer öğrenme nedir?</span><span class="sxs-lookup"><span data-stu-id="a4702-129">What is transfer learning?</span></span>

<span data-ttu-id="a4702-130">Transfer öğrenme başka bir ilgili sorun bir problem çözme elde edilen bilgi geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4702-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="a4702-131">Derin öğrenme modelini sıfırdan eğitmek için çeşitli parametreler, büyük miktarda etiketli eğitim verileri ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4702-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="a4702-132">Transfer öğrenimi ile birlikte önceden eğitilmiş bir model kullanmak, eğitim sürecini kısayolla kesmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a4702-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="a4702-133">Eğitim süreci</span><span class="sxs-lookup"><span data-stu-id="a4702-133">Training process</span></span>

<span data-ttu-id="a4702-134">Görüntü Sınıflandırma API önceden eğitilmiş TensorFlow modeli yükleyerek eğitim sürecini başlatır.</span><span class="sxs-lookup"><span data-stu-id="a4702-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="a4702-135">Eğitim süreci iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="a4702-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="a4702-136">Darboğaz fazı</span><span class="sxs-lookup"><span data-stu-id="a4702-136">Bottleneck phase</span></span>
2. <span data-ttu-id="a4702-137">Eğitim aşaması</span><span class="sxs-lookup"><span data-stu-id="a4702-137">Training phase</span></span>

![Eğitim Adımları](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="a4702-139">Darboğaz fazı</span><span class="sxs-lookup"><span data-stu-id="a4702-139">Bottleneck phase</span></span>

<span data-ttu-id="a4702-140">Darboğaz aşamasında, eğitim görüntüleri kümesi yüklenir ve piksel değerleri önceden eğitilmiş modelin dondurulmuş katmanları için giriş veya özellik olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="a4702-141">Dondurulmuş katmanlar, altboğaz katmanı olarak gayri resmi olarak bilinen sondan bir önceki katmana kadar sinir ağındaki tüm katmanları içerir.</span><span class="sxs-lookup"><span data-stu-id="a4702-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="a4702-142">Bu katmanlar üzerinde eğitim oluşmayacağı ve işlemler geçiş olduğundan bu katmanlara dondurulmuş olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="a4702-143">Bir modelin farklı sınıflar arasında ayrım lar yaptığı alt düzey desenlerin hesaplandığı bu donmuş katmanlarda.</span><span class="sxs-lookup"><span data-stu-id="a4702-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="a4702-144">Katman sayısı ne kadar büyükse, bu adım hesaplama açısından o kadar yoğundur.</span><span class="sxs-lookup"><span data-stu-id="a4702-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="a4702-145">Neyse ki, bu tek seferlik bir hesaplama olduğundan, sonuçlar önbelleğe alınabilir ve farklı parametrelerle deneme yaparken daha sonraki çalıştırmalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4702-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="a4702-146">Eğitim aşaması</span><span class="sxs-lookup"><span data-stu-id="a4702-146">Training phase</span></span>

<span data-ttu-id="a4702-147">Darboğaz aşamasından çıkış değerleri hesaplandıktan sonra, modelin son katmanını yeniden eğitmek için giriş olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="a4702-148">Bu işlem yinelemelidir ve model parametreleri tarafından belirtilen kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="a4702-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="a4702-149">Her çalıştırma sırasında, kayıp ve doğruluk değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a4702-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="a4702-150">Daha sonra, kaybı en aza indirmek ve doğruluğu en üst düzeye çıkarmak amacıyla modeli geliştirmek için uygun ayarlamalar yapılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="a4702-151">Eğitim tamamlandıktan sonra, iki model biçimi çıktı.</span><span class="sxs-lookup"><span data-stu-id="a4702-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="a4702-152">Bunlardan biri modelin `.pb` sürümü ve diğer modelin `.zip` ML.NET seri leştirilmiş sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="a4702-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="a4702-153">ML.NET tarafından desteklenen ortamlarda çalışırken, modelin `.zip` sürümünün kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="a4702-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="a4702-154">Ancak, ML.NET desteklenmiyor ortamlarda `.pb` sürümü kullanma seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="a4702-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="a4702-155">Önceden eğitilmiş modeli anlama</span><span class="sxs-lookup"><span data-stu-id="a4702-155">Understand the pretrained model</span></span>

<span data-ttu-id="a4702-156">Bu öğreticide kullanılan önceden eğitilmiş model, Bakiye Ağı (ResNet) v2 modelinin 101 katmanlı varyantıdır.</span><span class="sxs-lookup"><span data-stu-id="a4702-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="a4702-157">Orijinal model, görüntüleri bin kategoriye sınıflandırmak için eğitildi.</span><span class="sxs-lookup"><span data-stu-id="a4702-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="a4702-158">Model, 224 x 224 boyutundaki bir görüntüyü girdi olarak alır ve eğitildiği sınıfların her biri için sınıf olasılıklarını çıkarır.</span><span class="sxs-lookup"><span data-stu-id="a4702-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="a4702-159">Bu modelin bir parçası iki sınıf arasında öngörüler yapmak için özel görüntüler kullanarak yeni bir model eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="a4702-160">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4702-160">Create console application</span></span>

<span data-ttu-id="a4702-161">Artık transfer öğrenimi ve Görüntü Sınıflandırma API'si hakkında genel bir anlayışa sahip olduğunuza göre, uygulamayı oluşturmanın zamanı gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="a4702-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="a4702-162">"DeepLearning_ImageClassification_Binary" adlı bir **C# .NET Core Konsol Uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4702-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="a4702-163">**1.4.0** NuGet Paketini **Microsoft.ML** yükleyin:</span><span class="sxs-lookup"><span data-stu-id="a4702-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="a4702-164">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="a4702-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="a4702-165">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="a4702-166">**Gözat** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a4702-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="a4702-167">Yayın **aet'i ekle** onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="a4702-168">**Microsoft.ML**arayın.</span><span class="sxs-lookup"><span data-stu-id="a4702-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="a4702-169">**Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a4702-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="a4702-170">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a4702-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="a4702-171">**Microsoft.ML.Vision** sürüm **1.4.0**, **SciSharp.TensorFlow.Redist** sürüm **1.15.0**ve **Microsoft.ML.ImageAnalytics** sürüm **1.4.0** NuGet paketleri için bu adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="a4702-172">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="a4702-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="a4702-173">Bu öğretici için veri setleri Maguire, Marc vardır; Dorafshan, Sattar; ve Thomas, Robert J., "SDNET2018: Makine öğrenimi uygulamaları için somut bir çatlak görüntü veri seti" (2018).</span><span class="sxs-lookup"><span data-stu-id="a4702-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="a4702-174">Tüm Datasets göz atın.</span><span class="sxs-lookup"><span data-stu-id="a4702-174">Browse all Datasets.</span></span> <span data-ttu-id="a4702-175">Kağıt 48.</span><span class="sxs-lookup"><span data-stu-id="a4702-175">Paper 48.</span></span> <span data-ttu-id="a4702-176">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="a4702-176">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="a4702-177">SDNET2018, çatlak ve çatlamış olmayan beton yapılar (köprü güverteleri, duvarlar ve kaldırım) için ek açıklamalar içeren bir görüntü veri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="a4702-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![SDNET2018 dataset köprü güverte örnekleri](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="a4702-179">Veriler üç alt dizin halinde düzenlenir:</span><span class="sxs-lookup"><span data-stu-id="a4702-179">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="a4702-180">D köprü güverte görüntüleri içerir</span><span class="sxs-lookup"><span data-stu-id="a4702-180">D contains bridge deck images</span></span>
- <span data-ttu-id="a4702-181">P kaldırım görüntüleri içerir</span><span class="sxs-lookup"><span data-stu-id="a4702-181">P contains pavement images</span></span>
- <span data-ttu-id="a4702-182">W duvar görüntüleri içerir</span><span class="sxs-lookup"><span data-stu-id="a4702-182">W contains wall images</span></span>

<span data-ttu-id="a4702-183">Bu alt dizinlerin her biri iki ek önceden belirlenmiş alt dizin içerir:</span><span class="sxs-lookup"><span data-stu-id="a4702-183">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="a4702-184">C, çatlak yüzeyler için kullanılan önektir.</span><span class="sxs-lookup"><span data-stu-id="a4702-184">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="a4702-185">U, kırılmamış yüzeyler için kullanılan önektir</span><span class="sxs-lookup"><span data-stu-id="a4702-185">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="a4702-186">Bu eğitimde, yalnızca köprü güverte görüntüleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-186">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="a4702-187">Veri [kümesini](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) indirin ve zip'i indirin.</span><span class="sxs-lookup"><span data-stu-id="a4702-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="a4702-188">Veri kümesi dosyalarınızı kaydetmek için projenizde "varlıklar" adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4702-188">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="a4702-189">*CD* ve *UD* alt dizilişlerini son zamanlarda fermuarsız dizinden *varlıklar* dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a4702-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="a4702-190">Giriş ve çıktı sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4702-190">Create input and output classes</span></span>

1. <span data-ttu-id="a4702-191">*Program.cs* dosyasını açın ve `using` dosyanın üst kısmındaki varolan ifadeleri aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a4702-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="a4702-192">`Program` *Program.cs'daki*sınıfın altında , `ImageData`adı verilen bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4702-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="a4702-193">Bu sınıf, başlangıçta yüklenen verileri temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-193">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="a4702-194">`ImageData`aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="a4702-194">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="a4702-195">`ImagePath`görüntünün depolandığı tam nitelikli yoldur.</span><span class="sxs-lookup"><span data-stu-id="a4702-195">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="a4702-196">`Label`görüntünün ait olduğu kategoridir.</span><span class="sxs-lookup"><span data-stu-id="a4702-196">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="a4702-197">Bu tahmin değeridir.</span><span class="sxs-lookup"><span data-stu-id="a4702-197">This is the value to predict.</span></span>

1. <span data-ttu-id="a4702-198">Giriş ve çıktı verileriniz için sınıflar oluşturun</span><span class="sxs-lookup"><span data-stu-id="a4702-198">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="a4702-199">`ImageData` Sınıfın altında, giriş verilerinizin şemasını yeni bir sınıfta `ModelInput`tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a4702-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="a4702-200">`ModelInput`aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="a4702-200">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="a4702-201">`Image`resmin `byte[]` temsilidir.</span><span class="sxs-lookup"><span data-stu-id="a4702-201">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="a4702-202">Model, görüntü verilerinin eğitim için bu tür olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="a4702-202">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="a4702-203">`LabelAsKey`'nin `Label`sayısal temsilidir.</span><span class="sxs-lookup"><span data-stu-id="a4702-203">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="a4702-204">`ImagePath`görüntünün depolandığı tam nitelikli yoldur.</span><span class="sxs-lookup"><span data-stu-id="a4702-204">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="a4702-205">`Label`görüntünün ait olduğu kategoridir.</span><span class="sxs-lookup"><span data-stu-id="a4702-205">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="a4702-206">Bu tahmin değeridir.</span><span class="sxs-lookup"><span data-stu-id="a4702-206">This is the value to predict.</span></span>

        <span data-ttu-id="a4702-207">Sadece `Image` `LabelAsKey` ve modeli eğitmek ve tahminler yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="a4702-208">`ImagePath` Ve `Label` özellikleri, özgün resim dosya adı ve kategorisine erişmek için kolaylık sağlamak için tutulur.</span><span class="sxs-lookup"><span data-stu-id="a4702-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="a4702-209">Daha sonra, `ModelInput` sınıfın altında, çıktı verilerinizin şemasını yeni `ModelOutput`bir sınıfta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a4702-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="a4702-210">`ModelOutput`aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="a4702-210">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="a4702-211">`ImagePath`görüntünün depolandığı tam nitelikli yoldur.</span><span class="sxs-lookup"><span data-stu-id="a4702-211">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="a4702-212">`Label`görüntünün ait olduğu orijinal kategoridir.</span><span class="sxs-lookup"><span data-stu-id="a4702-212">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="a4702-213">Bu tahmin değeridir.</span><span class="sxs-lookup"><span data-stu-id="a4702-213">This is the value to predict.</span></span>
        - <span data-ttu-id="a4702-214">`PredictedLabel`model tarafından öngörülen değerdir.</span><span class="sxs-lookup"><span data-stu-id="a4702-214">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="a4702-215">Benzer `ModelInput`, model `PredictedLabel` tarafından yapılan tahmin içerdiğinden sadece öngörüler yapmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a4702-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="a4702-216">Ve `ImagePath` `Label` özellikleri, özgün resim dosyası adı ve kategorisine erişmek için kolaylık sağlamak için korunur.</span><span class="sxs-lookup"><span data-stu-id="a4702-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="a4702-217">Çalışma alanı dizini oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4702-217">Create workspace directory</span></span>

<span data-ttu-id="a4702-218">Eğitim ve doğrulama verileri sık sık değişmediğinde, daha fazla çalıştırma için hesaplanan darboğaz değerlerini önbelleğe almak iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="a4702-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="a4702-219">Projenizde, hesaplanan darboğaz *workspace* değerlerini ve `.pb` modelin sürümünü depolamak için çalışma alanı adı verilen yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4702-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="a4702-220">Yolları tanımlayın ve değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="a4702-220">Define paths and initialize variables</span></span>

1. <span data-ttu-id="a4702-221">Yöntemin `Main` içinde, varlıklarınızın konumunu, hesaplanmış darboğaz `.pb` değerlerini ve modelin sürümünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a4702-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="a4702-222">`mlContext` [MlContext](xref:Microsoft.ML.MLContext)yeni bir örnek ile değişkeni başlatma.</span><span class="sxs-lookup"><span data-stu-id="a4702-222">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="a4702-223">[MLContext](xref:Microsoft.ML.MLContext) sınıfı tüm ML.NET işlemleri için bir başlangıç noktasıdır ve mlContext'ı başlatmak, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a4702-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="a4702-224">Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.</span><span class="sxs-lookup"><span data-stu-id="a4702-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="a4702-225">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="a4702-225">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="a4702-226">Veri yükleme yardımcı programı yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4702-226">Create data loading utility method</span></span>

<span data-ttu-id="a4702-227">Görüntüler iki alt diziniçinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="a4702-227">The images are stored in two subdirectories.</span></span> <span data-ttu-id="a4702-228">Verileri yüklemeden önce, `ImageData` nesnelerin listesine biçimlendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4702-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="a4702-229">Bunu yapmak için, `LoadImagesFromDirectory` yöntemin `Main` altında yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4702-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="a4702-230">Alt `LoadImagesDirectory` dizinlerden tüm dosya yollarını almak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a4702-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="a4702-231">Ardından, bir `foreach` deyim kullanarak dosyaların her birini yineleyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-231">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="a4702-232">İfadenin `foreach` içinde, dosya uzantılarının destekleniyi denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-232">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="a4702-233">Görüntü Sınıflandırma API JPEG ve PNG biçimlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a4702-233">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="a4702-234">Sonra, dosya için etiket alın.</span><span class="sxs-lookup"><span data-stu-id="a4702-234">Then, get the label for the file.</span></span> <span data-ttu-id="a4702-235">`useFolderNameAsLabel` Parametre `true`ayarlanmışsa, dosyanın kaydedildiği ana dizini etiket olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="a4702-236">Aksi takdirde, etiketin dosya adının veya dosya adının öneki olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="a4702-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="a4702-237">Son olarak, yeni `ModelInput`bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4702-237">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="a4702-238">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="a4702-238">Prepare the data</span></span>

1. <span data-ttu-id="a4702-239">Yöntemde, `Main` eğitim için `LoadFromDirectory` kullanılan görüntülerin listesini almak için yardımcı program yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4702-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="a4702-240">Ardından, görüntüleri yöntemi [`IDataView`](xref:Microsoft.ML.IDataView) kullanarak [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="a4702-241">Veriler dizinlerden okunduğu sırada yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a4702-241">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="a4702-242">Verileri dengelemek için [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) yöntemi kullanarak karıştırın.</span><span class="sxs-lookup"><span data-stu-id="a4702-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="a4702-243">Makine öğrenimi modelleri girdinin sayısal formatta olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="a4702-243">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="a4702-244">Bu nedenle, bazı ön işleme eğitim den önce veri üzerinde yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4702-244">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="a4702-245">Oluşan [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) bir oluşturun [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) ve `LoadRawImageBytes` dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a4702-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="a4702-246">Dönüştürme `MapValueToKey` `Label` sütundaki kategorik değeri alır, sayısal `KeyType` bir değere dönüştürür ve yeni bir `LabelAsKey`sütunda depolar.</span><span class="sxs-lookup"><span data-stu-id="a4702-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="a4702-247">Eğitim `LoadImages` için görüntüleri `ImagePath` yüklemek için `imageFolder` parametre ile birlikte sütundaki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="a4702-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="a4702-248">Verileri, [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) önceden işlenmiş verileri `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) içeren bir [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) [`IDataView`](xref:Microsoft.ML.IDataView) yöntemi döndüren yönteme uygulamak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4702-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="a4702-249">Bir modeli eğitmek için, bir eğitim veri kümesinin yanı sıra doğrulama veri kümesine sahip olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a4702-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="a4702-250">Model eğitim seti üzerinde eğitilir.</span><span class="sxs-lookup"><span data-stu-id="a4702-250">The model is trained on the training set.</span></span> <span data-ttu-id="a4702-251">Görünmeyen veriler üzerinde ne kadar iyi öngörüler yapar doğrulama kümesine karşı performans ile ölçülür.</span><span class="sxs-lookup"><span data-stu-id="a4702-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="a4702-252">Bu performansın sonuçlarına bağlı olarak, model geliştirmek için öğrendiklerine ayarlamalar yapar.</span><span class="sxs-lookup"><span data-stu-id="a4702-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="a4702-253">Doğrulama kümesi, özgün veri kümenizi bölmekten veya bu amaç için ayrılmış başka bir kaynaktan gelebilir.</span><span class="sxs-lookup"><span data-stu-id="a4702-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="a4702-254">Bu durumda, önceden işlenmiş veri kümesi eğitim, doğrulama ve test kümelerine ayrılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="a4702-255">Yukarıdaki kod örneği iki bölme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a4702-255">The code sample above performs two splits.</span></span> <span data-ttu-id="a4702-256">İlk olarak, önceden işlenmiş veriler bölünür ve %70'i eğitim için kullanılırken, geri kalan %30'u doğrulama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="a4702-257">Daha sonra, %30 doğrulama kümesi doğrulama için %90 ve test için %10'un kullanıldığı doğrulama ve test kümelerine ayrılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="a4702-258">Bu veri bölümlerinin amacı hakkında düşünmenin bir yolu bir sınav almaktır.</span><span class="sxs-lookup"><span data-stu-id="a4702-258">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="a4702-259">Sınava çalışırken, sınavdaki kavramları kavramak için notlarınızı, kitaplarınızı veya diğer kaynaklarınızı gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="a4702-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="a4702-260">Tren seti bunun için var.</span><span class="sxs-lookup"><span data-stu-id="a4702-260">This is what the train set is for.</span></span> <span data-ttu-id="a4702-261">Daha sonra, bilginizi doğrulamak için sahte bir sınava girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4702-261">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="a4702-262">Doğrulama kümesi nin kullanışlı olduğu yer burasıdır.</span><span class="sxs-lookup"><span data-stu-id="a4702-262">This is where the validation set comes in handy.</span></span> <span data-ttu-id="a4702-263">Gerçek sınava girmeden önce kavramları iyi kavrayıp kavrayamadığınızı kontrol etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a4702-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="a4702-264">Bu sonuçlara dayanarak, neyi yanlış anladığınızı veya iyi anlamadığınızı not alır ve gerçek sınav için gözden geçirirken değişikliklerinizi dahil eleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4702-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="a4702-265">Sonunda sınava gireceksin.</span><span class="sxs-lookup"><span data-stu-id="a4702-265">Finally, you take the exam.</span></span> <span data-ttu-id="a4702-266">Bu, test kümesinin ne için kullanıldığıdır.</span><span class="sxs-lookup"><span data-stu-id="a4702-266">This is what the test set is used for.</span></span> <span data-ttu-id="a4702-267">Sınavda yer alan soruları hiç görmediniz ve şimdi eğitim ve doğrulamadan öğrendiklerinizi elinizdeki göreve uygulamak için kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a4702-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="a4702-268">Bölümleri tren, doğrulama ve test verileri için kendi değerlerini atayın.</span><span class="sxs-lookup"><span data-stu-id="a4702-268">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="a4702-269">Eğitim boru hattını tanımlayın</span><span class="sxs-lookup"><span data-stu-id="a4702-269">Define the training pipeline</span></span>

<span data-ttu-id="a4702-270">Model eğitimi birkaç adımdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="a4702-270">Model training consists of a couple of steps.</span></span> <span data-ttu-id="a4702-271">İlk olarak, Görüntü Sınıflandırma API modeli eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4702-271">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="a4702-272">Daha sonra, `PredictedLabel` sütundaki kodlanmış etiketler `MapKeyToValue` dönüştürme kullanılarak özgün kategorik değerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a4702-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="a4702-273">Bir `ImageClassificationTrainer`.</span><span class="sxs-lookup"><span data-stu-id="a4702-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="a4702-274">Bir `ImageClassificationTrainer` birkaç isteğe bağlı parametre alır:</span><span class="sxs-lookup"><span data-stu-id="a4702-274">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="a4702-275">`FeatureColumnName`model için giriş olarak kullanılan sütundur.</span><span class="sxs-lookup"><span data-stu-id="a4702-275">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="a4702-276">`LabelColumnName`tahmin değeri için sütundur.</span><span class="sxs-lookup"><span data-stu-id="a4702-276">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="a4702-277">`ValidationSet`doğrulama [`IDataView`](xref:Microsoft.ML.IDataView) verilerini içerendir.</span><span class="sxs-lookup"><span data-stu-id="a4702-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="a4702-278">`Arch`önceden eğitilmiş model mimarilerinden hangilerinin kullanılacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a4702-278">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="a4702-279">Bu öğretici, ResNetv2 modelinin 101 katmanlı varyantını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4702-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="a4702-280">`MetricsCallback`eğitim sırasında ilerlemeyi izlemek için bir işlev bağlar.</span><span class="sxs-lookup"><span data-stu-id="a4702-280">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="a4702-281">`TestOnTrainSet`doğrulama kümesi olmadığında performansı eğitim kümesine göre ölçmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="a4702-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="a4702-282">`ReuseTrainSetBottleneckCachedValues`sonraki çalıştırmalarda önbelleğe alınan değerleri darboğaz aşamasından kullanıp kullanmayacağını modele bildirir.</span><span class="sxs-lookup"><span data-stu-id="a4702-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="a4702-283">Darboğaz aşaması, ilk kez gerçekleştirilinin hesaplama aşamasında olan tek seferlik bir geçiş hesaplamasIdır.</span><span class="sxs-lookup"><span data-stu-id="a4702-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="a4702-284">Eğitim verileri değişmezse ve farklı sayıda çağ veya toplu iş boyutu kullanarak deneme yapmak istiyorsanız, önbelleğe alınan değerleri kullanmak bir modeli eğitmek için gereken süreyi önemli ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="a4702-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="a4702-285">`ReuseValidationSetBottleneckCachedValues``ReuseTrainSetBottleneckCachedValues` yalnızca bu durumda doğrulama veri kümesi için benzer.</span><span class="sxs-lookup"><span data-stu-id="a4702-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="a4702-286">`WorkspacePath`açılan darboğaz değerlerinin ve `.pb` modelin sürümünün depolanacağı dizin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a4702-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="a4702-287">[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) Hem ve `mapLabelEstimator` `ImageClassificationTrainer`.</span><span class="sxs-lookup"><span data-stu-id="a4702-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="a4702-288">Modelinizi [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) eğitmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4702-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="a4702-289">Modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="a4702-289">Use the model</span></span>

<span data-ttu-id="a4702-290">Artık modelinizi eğittiğinize göre, görüntüleri sınıflandırmak için onu kullanma nın zamanı gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="a4702-290">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="a4702-291">Yöntemin `Main` altında, konsolda tahmin `OutputPrediction` bilgilerini görüntülemek için çağrılan yeni bir yardımcı program yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4702-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="a4702-292">Tek bir görüntüyü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="a4702-292">Classify a single image</span></span>

1. <span data-ttu-id="a4702-293">Tek bir görüntü `ClassifySingleImage` tahmini `Main` yapmak ve çıktı vermek için yöntemin altına çağrılan yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="a4702-294">Yöntemin [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) içini `ClassifySingleImage` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4702-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="a4702-295">Bu, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde bir tahmin gerçekleştirmenize ve geçiş yapmanızı sağlayan bir kolaylık API'sidir.</span><span class="sxs-lookup"><span data-stu-id="a4702-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="a4702-296">`ModelInput` Tek bir örne erişmek `data` [`IDataView`](xref:Microsoft.ML.IDataView) için, yöntemi [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) kullanarak dönüştürün [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) ve ardından ilk gözlemi alın.</span><span class="sxs-lookup"><span data-stu-id="a4702-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="a4702-297">Görüntüyü [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) sınıflandırmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4702-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="a4702-298">Yöntemle konsola tahmin `OutputPrediction` çıktı.</span><span class="sxs-lookup"><span data-stu-id="a4702-298">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="a4702-299">Yöntemin `Main` içinde, `ClassifySingleImage` test görüntüleri kümesini kullanarak arayın.</span><span class="sxs-lookup"><span data-stu-id="a4702-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="a4702-300">Birden çok görüntüyü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="a4702-300">Classify multiple images</span></span>

1. <span data-ttu-id="a4702-301">Birden çok görüntü `ClassifyImages` öngörüsü yapmak ve çıktı vermek için yöntemin `ClassifySingleImage` altına çağrılan yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="a4702-302">Yöntemi [`IDataView`](xref:Microsoft.ML.IDataView) kullanarak öngörüleri içeren [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="a4702-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="a4702-303">`ClassifyImages` Yöntemin içine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-303">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="a4702-304">Öngörüler üzerinde tekrarlamak için, `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntem kullanarak dönüştürmek ve daha sonra ilk 10 gözlemler olsun.</span><span class="sxs-lookup"><span data-stu-id="a4702-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="a4702-305">Tahminler için orijinal ve öngörülen etiketleri yineleyin ve çıktıedin.</span><span class="sxs-lookup"><span data-stu-id="a4702-305">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="a4702-306">Son olarak, `Main` yöntemin `ClassifyImages` içinde, görüntülerin test kümesini kullanarak arayın.</span><span class="sxs-lookup"><span data-stu-id="a4702-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="a4702-307">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a4702-307">Run the application</span></span>

<span data-ttu-id="a4702-308">Konsol uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a4702-308">Run your console app.</span></span> <span data-ttu-id="a4702-309">Çıktı aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4702-309">The output should be similar to that below.</span></span> <span data-ttu-id="a4702-310">Uyarılar veya iletileri işleme görebilirsiniz, ancak bu iletiler netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a4702-310">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="a4702-311">Kısalık için, çıkış yoğunlaştırılmış tır.</span><span class="sxs-lookup"><span data-stu-id="a4702-311">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="a4702-312">**Darboğaz fazı**</span><span class="sxs-lookup"><span data-stu-id="a4702-312">**Bottleneck phase**</span></span>

<span data-ttu-id="a4702-313">Görüntüler görüntü adı olarak yüklendiğinden, görüntü adı `byte[]` için hiçbir değer yazdırılmaz, bu nedenle görüntü adı görüntülenecek bir ad yoktur.</span><span class="sxs-lookup"><span data-stu-id="a4702-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="a4702-314">**Eğitim aşaması**</span><span class="sxs-lookup"><span data-stu-id="a4702-314">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="a4702-315">**Görüntü çıktısını sınıflandırma**</span><span class="sxs-lookup"><span data-stu-id="a4702-315">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="a4702-316">*7001-220.jpg* görüntü nün incelenmesi üzerine, aslında kırık olmadığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4702-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Tahmin için kullanılan SDNET2018 dataset görüntüsü](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="a4702-318">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="a4702-318">Congratulations!</span></span> <span data-ttu-id="a4702-319">Şimdi başarılı görüntüleri sınıflandırmak için derin bir öğrenme modeli inşa ettik.</span><span class="sxs-lookup"><span data-stu-id="a4702-319">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="a4702-320">Modeli geliştirin</span><span class="sxs-lookup"><span data-stu-id="a4702-320">Improve the model</span></span>

<span data-ttu-id="a4702-321">Modelinizin sonuçlarından memnun değilseniz, aşağıdaki yaklaşımlardan bazılarını deneyerek performansını artırmayı deneyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a4702-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="a4702-322">**Daha Fazla Veri**: Bir model ne kadar çok örnekten öğrenirse, o kadar iyi performans gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4702-322">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="a4702-323">[SDNET2018 veri setinin](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) tamamını indirin ve eğitmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4702-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="a4702-324">**Verileri artırmak**: Verilere çeşitlilik katmak için yaygın bir teknik, görüntü alarak ve farklı dönüşümler (döndürme, çevirme, kaydırma, kırpma) uygulayarak verileri artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="a4702-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="a4702-325">Bu, modelden öğrenilen daha çeşitli örnekler ekler.</span><span class="sxs-lookup"><span data-stu-id="a4702-325">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="a4702-326">**Daha uzun süre tren**: Ne kadar uzun süre antrenman yaptığınızda, model o kadar ayarlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4702-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="a4702-327">Dönem sayısını artırmak modelinizin performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="a4702-327">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="a4702-328">**Hiper parametrelerle denemeler**: Bu eğitimde kullanılan parametrelere ek olarak, diğer parametreler performansı artırmak için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a4702-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="a4702-329">Her çağdan sonra modelde yapılan güncelleştirmelerin büyüklüğünü belirleyen öğrenme oranının değiştirilmesi performansı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="a4702-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="a4702-330">**Farklı bir model mimarisi kullanın**: Verilerinizin nasıl göründüğüne bağlı olarak, özelliklerini en iyi şekilde öğrenebilecek model farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4702-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="a4702-331">Modelinizin performansından memnun değilseniz, mimariyi değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-331">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a4702-332">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a4702-332">Additional Resources</span></span>

- <span data-ttu-id="a4702-333">[Derin Öğrenme vs Makine Öğrenme](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="a4702-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a4702-334">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a4702-334">Next steps</span></span>

<span data-ttu-id="a4702-335">Bu eğitimde, transfer öğrenimi, önceden eğitilmiş görüntü sınıflandırma TensorFlow modeli ve ML.NET Görüntü Sınıflandırma API'sini kullanarak beton yüzeylerin görüntülerini çatlak veya kırılmamış olarak sınıflandırmak için özel bir derin öğrenme modeli oluşturmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="a4702-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="a4702-336">Daha fazla bilgi edinmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="a4702-336">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4702-337">Nesne Algılama</span><span class="sxs-lookup"><span data-stu-id="a4702-337">Object Detection</span></span>](object-detection-onnx.md)
