---
title: 'Öğretici: aktarım öğrenimi kullanarak otomatikleştirilmiş görsel inceleme'
description: Bu öğreticide, somut yüzeylerin görüntülerini kırçıkarılan veya Kırçıkmıyor olarak sınıflandırmak için görüntü algılama API 'sini kullanarak ML.NET ' deki bir TensorFlow derin öğrenme modelini nasıl eğitecağın nasıl kullanılacağı gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/14/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 443f9e9a83ebf31bb6c62323015af4a554323b67
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205049"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="3ab60-103">Öğretici: ML.NET görüntü sınıflandırma API 'SI ile aktarım öğrenimini kullanarak otomatikleştirilmiş görsel inceleme</span><span class="sxs-lookup"><span data-stu-id="3ab60-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="3ab60-104">Özel derin öğrenme modelini, aktarım öğrenimi, önceden eğitilen bir TensorFlow modeli ve ML.NET görüntü sınıflandırma API 'sini kullanarak, somut yüzeylerin görüntülerini kırıllanmış veya kırılk olarak sınıflandırmasına nasıl eğeceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="3ab60-105">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="3ab60-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="3ab60-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="3ab60-106">Understand the problem</span></span>
> - <span data-ttu-id="3ab60-107">ML.NET görüntü sınıflandırma API 'SI hakkında bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="3ab60-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="3ab60-108">Önceden eğitilen modeli anlama</span><span class="sxs-lookup"><span data-stu-id="3ab60-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="3ab60-109">Özel bir TensorFlow görüntü sınıflandırma modelini eğitme için aktarım öğrenimi kullanma</span><span class="sxs-lookup"><span data-stu-id="3ab60-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="3ab60-110">Özel model ile görüntüleri sınıflandır</span><span class="sxs-lookup"><span data-stu-id="3ab60-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3ab60-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3ab60-111">Prerequisites</span></span>

- <span data-ttu-id="3ab60-112">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="3ab60-112">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="3ab60-113">Görüntü sınıflandırma aktarım öğrenme örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="3ab60-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="3ab60-114">Bu örnek, önceden C# eğitilen bir derin öğrenme TensorFlow modeli kullanarak görüntüleri sınıflandırın bir .NET Core konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="3ab60-115">Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="3ab60-116">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="3ab60-116">Understand the problem</span></span>

<span data-ttu-id="3ab60-117">Görüntü sınıflandırması bir bilgisayar vizyonu sorunudur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="3ab60-118">Görüntü sınıflandırması bir görüntüyü giriş olarak alır ve önceden tanımlanmış bir sınıfa kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="3ab60-119">Görüntü sınıflandırmasının kullanışlı olduğu bazı senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3ab60-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="3ab60-120">Yüz tanıma</span><span class="sxs-lookup"><span data-stu-id="3ab60-120">Facial recognition</span></span>
- <span data-ttu-id="3ab60-121">Duygu algılama</span><span class="sxs-lookup"><span data-stu-id="3ab60-121">Emotion detection</span></span>
- <span data-ttu-id="3ab60-122">Tıp tanısı</span><span class="sxs-lookup"><span data-stu-id="3ab60-122">Medical diagnosis</span></span>
- <span data-ttu-id="3ab60-123">Yer işareti algılama</span><span class="sxs-lookup"><span data-stu-id="3ab60-123">Landmark detection</span></span>

<span data-ttu-id="3ab60-124">Bu öğreticide, bir özel görüntü sınıflandırma modeli sunarak, her ne kadar bozuk olan yapıları belirlemek için köprü oluşturma işlemlerini otomatik görsel denetlemesi gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="3ab60-125">ML.NET resim sınıflandırması API 'SI</span><span class="sxs-lookup"><span data-stu-id="3ab60-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="3ab60-126">ML.NET, görüntü sınıflandırması yapmak için çeşitli yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ab60-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="3ab60-127">Bu öğretici, görüntü sınıflandırması API 'sini kullanarak Aktarım öğrenimini uygular.</span><span class="sxs-lookup"><span data-stu-id="3ab60-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="3ab60-128">Görüntü sınıflandırma API 'SI, TensorFlow C# C++ API 'si için bağlamalar sağlayan alt düzey bir kitaplık olan [TensorFlow.net](https://github.com/SciSharp/TensorFlow.NET)kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ab60-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="3ab60-129">Aktarım öğrenimi nedir?</span><span class="sxs-lookup"><span data-stu-id="3ab60-129">What is transfer learning?</span></span>

<span data-ttu-id="3ab60-130">Aktarım öğrenimi, bir problemi bir sorunla ilgili diğer soruna çözüm olarak elde edilen bilgileri uygular.</span><span class="sxs-lookup"><span data-stu-id="3ab60-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="3ab60-131">Derin bir öğrenme modelini sıfırdan eğitmek için birkaç parametre, büyük miktarda etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="3ab60-132">Aktarım öğrenimi ile önceden eğitilen bir modelin kullanılması, eğitim sürecini kısayollara eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="3ab60-133">Eğitim süreci</span><span class="sxs-lookup"><span data-stu-id="3ab60-133">Training process</span></span>

<span data-ttu-id="3ab60-134">Görüntü sınıflandırma API 'SI, önceden eğitilen bir TensorFlow modeli yükleyerek eğitim sürecini başlatır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="3ab60-135">Eğitim süreci iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="3ab60-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="3ab60-136">Performans sorunu aşaması</span><span class="sxs-lookup"><span data-stu-id="3ab60-136">Bottleneck phase</span></span>
2. <span data-ttu-id="3ab60-137">Eğitim aşaması</span><span class="sxs-lookup"><span data-stu-id="3ab60-137">Training phase</span></span>

![Eğitim adımları](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="3ab60-139">Performans sorunu aşaması</span><span class="sxs-lookup"><span data-stu-id="3ab60-139">Bottleneck phase</span></span>

<span data-ttu-id="3ab60-140">Performans sorunu aşamasında, eğitim görüntüleri kümesi yüklenir ve piksel değerleri, önceden eğitilen modelin dondurulmuş katmanları için giriş veya özellikler olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="3ab60-141">Dondurulmuş katmanlar, sinir ağındaki tüm katmanları, tıkanıklık katmanı olarak bilinen Penultimate katmanına kadar içerir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="3ab60-142">Bu katmanlarda hiçbir eğitim gerçekleşmediğinden ve işlemler doğrudan geçiş yaptığından, bu katmanlar dondurulmuş olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="3ab60-143">Farklı sınıflar arasında ayrım yapan bir modele yardımcı olan alt düzey desenlerin hesaplandığı, Bu dondurulmuş katmanlarda.</span><span class="sxs-lookup"><span data-stu-id="3ab60-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="3ab60-144">Katman sayısı arttıkça bu adım daha yoğun bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="3ab60-145">Neyse ki, bu bir kerelik hesaplama olduğundan, sonuçlar önbelleğe alınabilir ve daha sonra farklı parametrelerle denemeler yaparken çalışır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="3ab60-146">Eğitim aşaması</span><span class="sxs-lookup"><span data-stu-id="3ab60-146">Training phase</span></span>

<span data-ttu-id="3ab60-147">Performans sorunlarına neden olan çıkış değerleri hesaplandıktan sonra, modelin son katmanını yeniden eğitmek için giriş olarak kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="3ab60-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="3ab60-148">Bu işlem yinelemeli ve model parametreleri tarafından belirtilen sayıda kez çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="3ab60-149">Her çalıştırma sırasında, kayıp ve doğruluk değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="3ab60-150">Daha sonra, kaybı en aza indirmek ve doğruluğu en üst düzeye çıkarmak için modeli geliştirmek üzere uygun ayarlamalar yapılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="3ab60-151">Eğitim tamamlandığında, iki model biçimi çıkış olur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="3ab60-152">Bunlardan biri, modelin `.pb` sürümüdür ve diğeri de modelin `.zip` ML.NET serileştirilmiş sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="3ab60-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="3ab60-153">ML.NET tarafından desteklenen ortamlarda çalışırken, modelin `.zip` sürümünün kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="3ab60-154">Ancak, ML.NET 'in desteklenmediği ortamlarda `.pb` sürümünü kullanma seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="3ab60-155">Önceden eğitilen modeli anlama</span><span class="sxs-lookup"><span data-stu-id="3ab60-155">Understand the pretrained model</span></span>

<span data-ttu-id="3ab60-156">Bu öğreticide kullanılan önceden eğitilen model, kalan ağ (ResNet) v2 modelinin 101 katmanlı varyantıdır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="3ab60-157">Orijinal model resimleri bin kategoride sınıflandırmakta tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="3ab60-158">Model, 224 x 224 boyutundaki bir görüntüyü giriş olarak alır ve eğitilen sınıfların her biri için sınıf olasılıkların çıkışını çıkarır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="3ab60-159">Bu modelin bir parçası, iki sınıf arasında tahmine dayalı hale getirmek için özel görüntüler kullanarak yeni bir modeli eğitme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="3ab60-160">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ab60-160">Create console application</span></span>

<span data-ttu-id="3ab60-161">Aktarım öğrenimine ve görüntü sınıflandırma API 'sine ilişkin genel bir bilgiye sahip olduğunuza göre, uygulamayı derlemek zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="3ab60-162">"DeepLearning_ImageClassification_Binary" adlı bir  **C# .NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="3ab60-163">**Microsoft.ml** Version **1.4.0** NuGet paketini yükler:</span><span class="sxs-lookup"><span data-stu-id="3ab60-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="3ab60-164">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="3ab60-165">Paket kaynağı olarak "nuget.org" öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="3ab60-166">**Tarayıcı** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="3ab60-167">**Ön sürümü dahil et** onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="3ab60-168">**Microsoft.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="3ab60-169">**Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="3ab60-170">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="3ab60-171">Bu adımları **Microsoft. ml. Vision** sürümü **1.4.0**, **SciSharp. TensorFlow. Redist** sürüm **1.15.0**ve **Microsoft. ml. ımageanalytics** sürümü **1.4.0** NuGet paketleri için yineleyin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="3ab60-172">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="3ab60-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="3ab60-173">Bu öğreticinin veri kümeleri Maguire, Marc; adresinden Dorafshan, Sattar; ve Thomas, Robert J., "SDNET2018: Machine Learning uygulamaları için somut bir görüntü veri kümesi" (2018).</span><span class="sxs-lookup"><span data-stu-id="3ab60-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="3ab60-174">Tüm veri kümelerine gözatamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3ab60-174">Browse all Datasets.</span></span> <span data-ttu-id="3ab60-175">Kağıt 48.</span><span class="sxs-lookup"><span data-stu-id="3ab60-175">Paper 48.</span></span> <span data-ttu-id="3ab60-176">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="3ab60-176">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="3ab60-177">SDNET2018, kırılmamış ve kırılamayan somut yapılar (köprü kümeleri, duvarlar ve Payalar) için ek açıklamalar içeren bir görüntü veri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![SDNET2018 veri kümesi Köprüsü destesi örnekleri](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="3ab60-179">Veriler üç alt dizine göre düzenlenir:</span><span class="sxs-lookup"><span data-stu-id="3ab60-179">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="3ab60-180">D köprü destesi görüntülerini içerir</span><span class="sxs-lookup"><span data-stu-id="3ab60-180">D contains bridge deck images</span></span>
- <span data-ttu-id="3ab60-181">P paizni görüntülerini içerir</span><span class="sxs-lookup"><span data-stu-id="3ab60-181">P contains pavement images</span></span>
- <span data-ttu-id="3ab60-182">W duvar görüntülerini içerir</span><span class="sxs-lookup"><span data-stu-id="3ab60-182">W contains wall images</span></span>

<span data-ttu-id="3ab60-183">Bu alt dizinlerin her biri, iki ek ön eki içerir:</span><span class="sxs-lookup"><span data-stu-id="3ab60-183">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="3ab60-184">C, kırçıkarılan yüzeyler için kullanılan önekidir</span><span class="sxs-lookup"><span data-stu-id="3ab60-184">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="3ab60-185">U, kırçıkarılan yüzeyler için kullanılan önekidir</span><span class="sxs-lookup"><span data-stu-id="3ab60-185">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="3ab60-186">Bu öğreticide, yalnızca köprü destesi görüntüleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-186">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="3ab60-187">[Veri kümesini](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) indirin ve sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="3ab60-188">Veri kümesi dosyalarınızı kaydetmek için projenizde "varlıklar" adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-188">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="3ab60-189">Son daraltılmış dizinden *CD* ve *ud* alt dizinlerini *varlıklar* dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="3ab60-190">Giriş ve çıkış sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ab60-190">Create input and output classes</span></span>

1. <span data-ttu-id="3ab60-191">*Program.cs* dosyasını açın ve dosyanın en üstündeki mevcut `using` deyimlerini aşağıdaki şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="3ab60-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="3ab60-192">*Program.cs*içinde `Program` sınıfının altında `ImageData`adlı bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="3ab60-193">Bu sınıf başlangıçta yüklenen verileri temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-193">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="3ab60-194">`ImageData` aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3ab60-194">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="3ab60-195">`ImagePath`, görüntünün depolandığı tam yoldur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-195">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="3ab60-196">`Label` görüntünün ait olduğu kategorisidir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-196">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="3ab60-197">Tahmin edilecek değer budur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-197">This is the value to predict.</span></span>

1. <span data-ttu-id="3ab60-198">Giriş ve çıkış verileriniz için sınıflar oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ab60-198">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="3ab60-199">`ImageData` sınıfının altında, giriş verilerinizin şemasını `ModelInput`adlı yeni bir sınıfta tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="3ab60-200">`ModelInput` aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3ab60-200">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="3ab60-201">`ImagePath`, görüntünün depolandığı tam yoldur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-201">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="3ab60-202">`Label` görüntünün ait olduğu kategorisidir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-202">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="3ab60-203">Tahmin edilecek değer budur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-203">This is the value to predict.</span></span>
        - <span data-ttu-id="3ab60-204">`Image` görüntünün `byte[]` gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-204">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="3ab60-205">Model, yansıma verilerinin eğitim için bu türden olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="3ab60-205">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="3ab60-206">`LabelAsKey`, `Label`sayısal gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-206">`LabelAsKey` is the numerical representation of the `Label`.</span></span>

        <span data-ttu-id="3ab60-207">Modeli eğitme ve tahmin yapmak için yalnızca `Image` ve `LabelAsKey` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="3ab60-208">`ImagePath` ve `Label` özellikleri özgün görüntü dosyası adına ve kategorisine erişmek için kolaylık sağlamak üzere tutulur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="3ab60-209">Daha sonra, `ModelInput` sınıfının altında, çıkış verilerinizin şemasını `ModelOutput`adlı yeni bir sınıfta tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="3ab60-210">`ModelOutput` aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3ab60-210">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="3ab60-211">`ImagePath`, görüntünün depolandığı tam yoldur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-211">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="3ab60-212">`Label` görüntünün ait olduğu özgün kategorisidir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-212">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="3ab60-213">Tahmin edilecek değer budur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-213">This is the value to predict.</span></span>
        - <span data-ttu-id="3ab60-214">`PredictedLabel`, model tarafından tahmin edilen değerdir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-214">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="3ab60-215">`ModelInput`benzer şekilde, yalnızca `PredictedLabel` model tarafından yapılan tahminleri içerdiğinden tahmine dayalı hale getirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="3ab60-216">`ImagePath` ve `Label` özellikleri özgün görüntü dosyası adına ve kategorisine erişmek için kolaylık sağlamak amacıyla tutulur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="3ab60-217">Çalışma alanı dizini oluştur</span><span class="sxs-lookup"><span data-stu-id="3ab60-217">Create workspace directory</span></span>

<span data-ttu-id="3ab60-218">Eğitim ve doğrulama verileri sıklıkla değişmediğinde, daha fazla çalıştırma için hesaplanan darboğazal değerlerini önbelleğe almak iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="3ab60-219">Projenizde, hesaplanan performans sorunu değerlerini ve modelin `.pb` sürümünü depolamak için *çalışma alanı* adlı yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="3ab60-220">Yolları tanımlama ve değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="3ab60-220">Define paths and initialize variables</span></span>

1. <span data-ttu-id="3ab60-221">`Main` yönteminin içinde, varlıklarınızın konumunu, hesaplanan tıkanıklık değerlerini ve modelin `.pb` sürümünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="3ab60-222">Sonra, `mlContext` değişkenini yeni bir [Mlcontext](xref:Microsoft.ML.MLContext)örneğiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-222">Then, initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="3ab60-223">[Mlcontext](xref:Microsoft.ML.MLContext) sınıfı tüm ml.NET işlemleri için bir başlangıç noktasıdır ve mlcontext 'i başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="3ab60-224">Benzer, kavramsal olarak, Entity Framework `DBContext`.</span><span class="sxs-lookup"><span data-stu-id="3ab60-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="3ab60-225">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="3ab60-225">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="3ab60-226">Veri yükleme yardımcı programı yöntemi oluştur</span><span class="sxs-lookup"><span data-stu-id="3ab60-226">Create data loading utility method</span></span>

<span data-ttu-id="3ab60-227">Görüntüler iki alt dizine depolanır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-227">The images are stored in two subdirectories.</span></span> <span data-ttu-id="3ab60-228">Verileri yüklemeden önce, `ImageData` nesnelerinin bir listesi halinde biçimlendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="3ab60-229">Bunu yapmak için, `Main` yönteminin altında `LoadImagesFromDirectory` yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="3ab60-230">`LoadImagesDirectory` iç dizinlerindeki tüm dosya yollarını almak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3ab60-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="3ab60-231">Ardından, bir `foreach` bildiri kullanarak her bir dosyanın üzerinde yineleyin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-231">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="3ab60-232">`foreach` ifadesinin içinde, dosya uzantılarının desteklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-232">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="3ab60-233">Resim sınıflandırma API 'SI JPEG ve PNG biçimlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="3ab60-233">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="3ab60-234">Ardından, dosyanın etiketini alın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-234">Then, get the label for the file.</span></span> <span data-ttu-id="3ab60-235">`useFolderNameAsLabel` parametresi `true`olarak ayarlanırsa, dosyanın kaydedildiği üst dizin etiket olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="3ab60-236">Aksi takdirde, etiketin dosya adının veya dosya adının ön eki olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="3ab60-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="3ab60-237">Son olarak, `ModelInput`yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-237">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="3ab60-238">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="3ab60-238">Prepare the data</span></span>

1. <span data-ttu-id="3ab60-239">`Main` yöntemine geri döndüğünüzde, eğitim için kullanılan görüntülerin listesini almak için `LoadFromDirectory` yardımcı program yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="3ab60-240">Sonra, [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yöntemini kullanarak görüntüleri bir [`IDataView`](xref:Microsoft.ML.IDataView) içine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="3ab60-241">Veriler, dizinlerden okunan sıraya göre yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-241">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="3ab60-242">Verileri dengelemek için [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) yöntemi kullanarak karıştırın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="3ab60-243">Makine öğrenimi modelleri, girişin sayısal biçimde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="3ab60-243">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="3ab60-244">Bu nedenle, eğitimin öncesinde bazı ön işleme verilerin yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-244">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="3ab60-245">[`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) ve `LoadRawImageBytes` dönüştürmelerini [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="3ab60-246">`MapValueToKey` Transform, `Label` sütununda kategorik değeri alır, sayısal bir `KeyType` değere dönüştürür ve `LabelAsKey`adlı yeni bir sütunda depolar.</span><span class="sxs-lookup"><span data-stu-id="3ab60-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="3ab60-247">`LoadImages`, eğitim için görüntüleri yüklemek üzere `imageFolder` parametresiyle birlikte `ImagePath` sütunundaki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="3ab60-248">[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) yöntemini kullanarak verileri `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ve ardından önceden işlenmiş verileri içeren bir [`IDataView`](xref:Microsoft.ML.IDataView) döndüren [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) yöntemi ile uygulayın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="3ab60-249">Bir modeli eğmek için bir eğitim veri kümesinin yanı sıra bir doğrulama veri kümesi de olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="3ab60-250">Model, eğitim kümesi üzerinde eğitilir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-250">The model is trained on the training set.</span></span> <span data-ttu-id="3ab60-251">Görülmeyen veriler üzerinde tahminleri ne kadar iyi yapar doğrulama kümesine göre performans ile ölçülür.</span><span class="sxs-lookup"><span data-stu-id="3ab60-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="3ab60-252">Model, bu performansın sonuçlarına bağlı olarak, geliştirme çabasında ne kadar öğrenildiği konusunda ayarlamalar yapar.</span><span class="sxs-lookup"><span data-stu-id="3ab60-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="3ab60-253">Doğrulama kümesi, özgün veri kümenizi veya bu amaçla zaten ayrılmış olan başka bir kaynağı bölerek gelebilir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="3ab60-254">Bu durumda, önceden işlenmiş veri kümesi eğitim, doğrulama ve test kümelerine bölünür.</span><span class="sxs-lookup"><span data-stu-id="3ab60-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="3ab60-255">Yukarıdaki kod örneği iki bölme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-255">The code sample above performs two splits.</span></span> <span data-ttu-id="3ab60-256">İlk olarak, önceden işlenmiş veriler bölünür ve %70, doğrulama için kalan %30 ' u kullanıldığında eğitim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="3ab60-257">Daha sonra, %30 doğrulama kümesi daha fazla doğrulama ve test kümelerine bölünür; burada %90 doğrulama için kullanılır ve test için %10 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="3ab60-258">Bu veri bölümlerinin amacını düşünmek için bir yol, bir sınavın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-258">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="3ab60-259">Bir sınava göre çalışırken, sınavlarda bulunan kavramlara bir attık almak için notlarınızı, kitapları veya diğer kaynaklarınızı gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="3ab60-260">Bu, eğitim kümesinin için olduğu şeydir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-260">This is what the train set is for.</span></span> <span data-ttu-id="3ab60-261">Daha sonra, bilginizi doğrulamak için bir sahte sınava sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ab60-261">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="3ab60-262">Bu, doğrulama kümesinin yararlı olduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-262">This is where the validation set comes in handy.</span></span> <span data-ttu-id="3ab60-263">Gerçek sınava girmeden önce kavramların iyi bir yermi olduğunu kontrol etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="3ab60-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="3ab60-264">Bu sonuçlara dayanarak, ne kadar yanlış olduğunu veya iyi anladığınızı ve gerçek sınava göre gözden geçirdiğinize ilişkin değişikliklerinizi dahil etmediğinizi göz önünde bulmalısınız.</span><span class="sxs-lookup"><span data-stu-id="3ab60-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="3ab60-265">Son olarak, sınava sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="3ab60-265">Finally, you take the exam.</span></span> <span data-ttu-id="3ab60-266">Bu, için test kümesinin kullanıldığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-266">This is what the test set is used for.</span></span> <span data-ttu-id="3ab60-267">Sınavdaki soruları hiç gördüğdiniz ve şimdi eğitim ve doğrulamadan öğrendiklerinizi kullanarak bilgilerinizi el ile görev için nasıl uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3ab60-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="3ab60-268">Eğitim, doğrulama ve test verileri için bölümleri ilgili değerleri atayın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-268">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="3ab60-269">Eğitim işlem hattını tanımlama</span><span class="sxs-lookup"><span data-stu-id="3ab60-269">Define the training pipeline</span></span>

<span data-ttu-id="3ab60-270">Model eğitimi birkaç adımdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-270">Model training consists of a couple of steps.</span></span> <span data-ttu-id="3ab60-271">İlk olarak, modeli eğitmek için görüntü sınıflandırma API 'SI kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-271">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="3ab60-272">Daha sonra, `PredictedLabel` sütunundaki kodlanmış Etiketler, `MapKeyToValue` dönüşümü kullanılarak özgün kategorik değerlerine geri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="3ab60-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="3ab60-273">Bir `ImageClassificationTrainer`için gerekli ve isteğe bağlı parametrelerin bir kümesini depolamak üzere yeni bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span> 

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="3ab60-274">`ImageClassificationTrainer` birkaç isteğe bağlı parametre alır:</span><span class="sxs-lookup"><span data-stu-id="3ab60-274">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="3ab60-275">`FeatureColumnName`, model için girdi olarak kullanılan sütundur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-275">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="3ab60-276">`LabelColumnName`, tahmin edilecek değerin sütundeğeridir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-276">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="3ab60-277">`ValidationSet`, doğrulama verilerini içeren [`IDataView`](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="3ab60-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="3ab60-278">`Arch`, önceden eğitilen model mimarilerinden hangisinin kullanılacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3ab60-278">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="3ab60-279">Bu öğretici ResNetv2 modelinin 101 katman türevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="3ab60-280">`MetricsCallback` eğitim sırasında ilerlemeyi izlemek için bir işlevi bağlar.</span><span class="sxs-lookup"><span data-stu-id="3ab60-280">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="3ab60-281">`TestOnTrainSet`, bir doğrulama kümesi mevcut olmadığında modelin eğitim kümesine karşı performansını ölçmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="3ab60-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="3ab60-282">`ReuseTrainSetBottleneckCachedValues`, sonraki çalışmalarda performans sorunlarına neden olan önbelleğe alınmış değerleri kullanıp kullanmayacağınızı modele söyler.</span><span class="sxs-lookup"><span data-stu-id="3ab60-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="3ab60-283">Performans sorunu, ilk çalıştırıldığında yoğun bir şekilde yoğun bir geçiş hesaplasıdır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="3ab60-284">Eğitim verileri değişmezse ve farklı sayıda dönemler veya toplu iş boyutu kullanmayı denemek istiyorsanız, önbelleğe alınmış değerleri kullanmak bir modeli eğmek için gereken süreyi önemli ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="3ab60-285">`ReuseValidationSetBottleneckCachedValues`, yalnızca bu örnekte doğrulama veri kümesi için olan `ReuseTrainSetBottleneckCachedValues` benzerdir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="3ab60-286">`WorkspacePath`, hesaplanan performans sorunu değerlerinin ve modelin `.pb` sürümünün depolanacağı dizini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3ab60-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="3ab60-287">Hem `mapLabelEstimator` hem de `ImageClassificationTrainer`oluşan [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) eğitim işlem hattını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="3ab60-288">Modelinize eğitebilmeniz için [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="3ab60-289">Modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="3ab60-289">Use the model</span></span>

<span data-ttu-id="3ab60-290">Modelinize eğitim sahibi olduğunuza göre, görüntüleri sınıflandırmak için kullanmanın zamanı.</span><span class="sxs-lookup"><span data-stu-id="3ab60-290">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="3ab60-291">`Main` yönteminin altında, konsolunda tahmin bilgilerini göstermek için `OutputPrediction` adlı yeni bir yardımcı program yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="3ab60-292">Tek bir görüntüyü sınıflandır</span><span class="sxs-lookup"><span data-stu-id="3ab60-292">Classify a single image</span></span>

1. <span data-ttu-id="3ab60-293">Tek bir görüntü tahminini yapmak ve çıkarmak için `Main` yönteminin altına `ClassifySingleImage` adlı yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="3ab60-294">`ClassifySingleImage` yöntemi içinde [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="3ab60-295">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneği üzerinde bir tahmin etmenizi ve daha sonra bir tahmin gerçekleştirmenizi sağlayan KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="3ab60-296">Tek bir `ModelInput` örneğine erişmek için, [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemini kullanarak `data` [`IDataView`](xref:Microsoft.ML.IDataView) bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dönüştürün ve ardından ilk gözlemyi alın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="3ab60-297">Görüntüyü sınıflandırmak için [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="3ab60-298">`OutputPrediction` yöntemiyle, tahmine konsola çıkış yapın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-298">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="3ab60-299">`Main` yönteminin içinde, görüntü sınama kümesini kullanarak `ClassifySingleImage` çağırın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="3ab60-300">Birden çok görüntüyü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="3ab60-300">Classify multiple images</span></span>

1. <span data-ttu-id="3ab60-301">Birden çok görüntü Tahminleri yapmak ve çıkarmak için `ClassifySingleImage` yönteminin altına `ClassifyImages` adlı yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="3ab60-302">[`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodunu kullanarak tahminleri içeren bir [`IDataView`](xref:Microsoft.ML.IDataView) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ab60-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="3ab60-303">`ClassifyImages` yönteminin içine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-303">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="3ab60-304">Tahmine dayalı olarak yinelemek için, `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemini kullanarak [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dönüştürün ve ardından ilk 10 gözlemleme elde edin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="3ab60-305">Tahmine dayalı olarak orijinal ve tahmin edilen etiketleri yineleyin ve çıktı.</span><span class="sxs-lookup"><span data-stu-id="3ab60-305">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="3ab60-306">Son olarak, `Main` yönteminin içinde, görüntü sınama kümesini kullanarak `ClassifyImages` çağırın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="3ab60-307">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3ab60-307">Run the application</span></span>

<span data-ttu-id="3ab60-308">Konsol uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-308">Run your console app.</span></span> <span data-ttu-id="3ab60-309">Çıktının aşağıdakine benzer olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-309">The output should be similar to that below.</span></span> <span data-ttu-id="3ab60-310">Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-310">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="3ab60-311">Breçekimi için çıkış yoğunlaştırılmış.</span><span class="sxs-lookup"><span data-stu-id="3ab60-311">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="3ab60-312">**Performans sorunu aşaması**</span><span class="sxs-lookup"><span data-stu-id="3ab60-312">**Bottleneck phase**</span></span>

<span data-ttu-id="3ab60-313">Görüntüler `byte[]` olarak yüklendiği için görüntü adı için hiçbir değer yazdırılamaz, bu nedenle görüntülenecek görüntü adı yok.</span><span class="sxs-lookup"><span data-stu-id="3ab60-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="3ab60-314">**Eğitim aşaması**</span><span class="sxs-lookup"><span data-stu-id="3ab60-314">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="3ab60-315">**Görüntüleri sınıflandırın çıktısı**</span><span class="sxs-lookup"><span data-stu-id="3ab60-315">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="3ab60-316">*7001 -220. jpg* görüntüsünü incelemeden, aslında bunun kırdığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ab60-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Tahmin için kullanılan SDNET2018 veri kümesi görüntüsü](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="3ab60-318">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="3ab60-318">Congratulations!</span></span> <span data-ttu-id="3ab60-319">Artık görüntülerin sınıflandırılmasına yönelik derin bir öğrenme modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="3ab60-319">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="3ab60-320">Modeli geliştirme</span><span class="sxs-lookup"><span data-stu-id="3ab60-320">Improve the model</span></span>

<span data-ttu-id="3ab60-321">Modelinizin sonuçlarını tatmin ediyorsanız, aşağıdaki yaklaşımlardan bazılarını deneyerek performansını geliştirmeyi deneyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3ab60-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="3ab60-322">**Daha fazla veri**: bir modelin öğreni daha fazla örnek, ne kadar iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="3ab60-322">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="3ab60-323">Tam [SDNET2018 veri kümesini](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) indirip eğmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ab60-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="3ab60-324">**Verileri artırmak**: verileri bir görüntü alarak ve farklı dönüşümler uygulayarak (Döndür, çevir, Shift, Kırp) veri eklemek için sık kullanılan bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="3ab60-325">Bu, modelin öğreni için daha fazla değişken örnek ekler.</span><span class="sxs-lookup"><span data-stu-id="3ab60-325">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="3ab60-326">Daha **uzun bir süre eğitin**: daha fazla eğitede, model daha fazla ayarlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="3ab60-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="3ab60-327">Dönemler sayısının artırılması, modelinizin performansını iyileştirebilecek.</span><span class="sxs-lookup"><span data-stu-id="3ab60-327">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="3ab60-328">**Hyper-Parameters Ile denemeler yapın**: Bu öğreticide kullanılan parametrelere ek olarak, diğer parametreler potansiyel olarak performansı iyileştirecek şekilde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="3ab60-329">Her dönem performansı iyileştirebilmek için modele yapılan güncelleştirmelerin büyüklüğünü belirleyen öğrenme oranını değiştirme.</span><span class="sxs-lookup"><span data-stu-id="3ab60-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="3ab60-330">**Farklı bir model mimarisi kullanın**: verilerinizin neye benzer olduğuna bağlı olarak, özelliklerini en iyi şekilde öğrenen en iyi şekilde bir model farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3ab60-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="3ab60-331">Modelinizin performansını karşılıyoruz, mimariyi değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-331">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3ab60-332">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3ab60-332">Additional Resources</span></span>

- <span data-ttu-id="3ab60-333">[Derin öğrenme vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="3ab60-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3ab60-334">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3ab60-334">Next steps</span></span>

<span data-ttu-id="3ab60-335">Bu öğreticide, aktarım öğrenimi, önceden eğitilen bir görüntü sınıflandırması TensorFlow modeli ve ML.NET görüntü sınıflandırma API 'sini kullanarak, somut yüzeyleri kırıllanmış veya kırılk olarak sınıflandırmakta olan özel bir derin öğrenme modeli oluşturmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="3ab60-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="3ab60-336">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="3ab60-336">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3ab60-337">Nesne algılama</span><span class="sxs-lookup"><span data-stu-id="3ab60-337">Object Detection</span></span>](object-detection-onnx.md)
