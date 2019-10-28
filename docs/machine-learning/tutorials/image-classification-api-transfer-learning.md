---
title: 'Öğretici: aktarım öğrenimi kullanarak otomatikleştirilmiş görsel inceleme'
description: Bu öğreticide, somut yüzeylerin görüntülerini kırçıkarılan veya Kırçıkmıyor olarak sınıflandırmak için görüntü algılama API 'sini kullanarak ML.NET ' deki bir TensorFlow derin öğrenme modelini nasıl eğitecağın nasıl kullanılacağı gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/25/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b8aec80134188811eb80ad1394e5a64d65a3c6f0
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961989"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="97f27-103">Öğretici: ML.NET görüntü sınıflandırma API 'SI ile aktarım öğrenimini kullanarak otomatikleştirilmiş görsel inceleme</span><span class="sxs-lookup"><span data-stu-id="97f27-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="97f27-104">Özel derin öğrenme modelini, aktarım öğrenimi, önceden eğitilen bir TensorFlow modeli ve ML.NET görüntü sınıflandırma API 'sini kullanarak, somut yüzeylerin görüntülerini kırıllanmış veya kırılk olarak sınıflandırmasına nasıl eğeceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="97f27-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

> [!NOTE]
> <span data-ttu-id="97f27-105">Bu öğretici, ML.NET görüntü sınıflandırma API 'sinin önizleme sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="97f27-105">This tutorial uses a preview version of the ML.NET Image Classification API.</span></span>

<span data-ttu-id="97f27-106">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="97f27-106">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="97f27-107">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="97f27-107">Understand the problem</span></span>
> - <span data-ttu-id="97f27-108">ML.NET görüntü sınıflandırma API 'SI hakkında bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="97f27-108">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="97f27-109">Önceden eğitilen modeli anlama</span><span class="sxs-lookup"><span data-stu-id="97f27-109">Understand the pretrained model</span></span>
> - <span data-ttu-id="97f27-110">Özel bir TensorFlow görüntü sınıflandırma modelini eğitme için aktarım öğrenimi kullanma</span><span class="sxs-lookup"><span data-stu-id="97f27-110">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="97f27-111">Özel model ile görüntüleri sınıflandır</span><span class="sxs-lookup"><span data-stu-id="97f27-111">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="97f27-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="97f27-112">Prerequisites</span></span>

- <span data-ttu-id="97f27-113">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="97f27-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="97f27-114">Görüntü sınıflandırma aktarım öğrenme örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="97f27-114">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="97f27-115">Bu örnek, önceden C# eğitilen bir derin öğrenme TensorFlow modeli kullanarak görüntüleri sınıflandırın bir .NET Core konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="97f27-115">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="97f27-116">Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-116">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="97f27-117">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="97f27-117">Understand the problem</span></span>

<span data-ttu-id="97f27-118">Görüntü sınıflandırması bir bilgisayar vizyonu sorunudur.</span><span class="sxs-lookup"><span data-stu-id="97f27-118">Image classification is a computer vision problem.</span></span> <span data-ttu-id="97f27-119">Görüntü sınıflandırması bir görüntüyü giriş olarak alır ve önceden tanımlanmış bir sınıfa kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="97f27-119">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="97f27-120">Görüntü sınıflandırmasının kullanışlı olduğu bazı senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="97f27-120">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="97f27-121">Yüz tanıma</span><span class="sxs-lookup"><span data-stu-id="97f27-121">Facial recognition</span></span>
- <span data-ttu-id="97f27-122">Duygu algılama</span><span class="sxs-lookup"><span data-stu-id="97f27-122">Emotion detection</span></span>
- <span data-ttu-id="97f27-123">Tıp tanısı</span><span class="sxs-lookup"><span data-stu-id="97f27-123">Medical diagnosis</span></span>
- <span data-ttu-id="97f27-124">Yer işareti algılama</span><span class="sxs-lookup"><span data-stu-id="97f27-124">Landmark detection</span></span>

<span data-ttu-id="97f27-125">Bu öğreticide, bir özel görüntü sınıflandırma modeli sunarak, her ne kadar bozuk olan yapıları belirlemek için köprü oluşturma işlemlerini otomatik görsel denetlemesi gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-125">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="97f27-126">ML.NET resim sınıflandırması API 'SI</span><span class="sxs-lookup"><span data-stu-id="97f27-126">ML.NET Image Classification API</span></span>

<span data-ttu-id="97f27-127">ML.NET, görüntü sınıflandırması yapmak için çeşitli yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="97f27-127">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="97f27-128">Bu öğretici, görüntü sınıflandırması API 'sini kullanarak Aktarım öğrenimini uygular.</span><span class="sxs-lookup"><span data-stu-id="97f27-128">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="97f27-129">Görüntü sınıflandırma API 'SI, TensorFlow C# C++ API 'si için bağlamalar sağlayan alt düzey bir kitaplık olan [TensorFlow.net](https://github.com/SciSharp/TensorFlow.NET)kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="97f27-129">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="97f27-130">Aktarım öğrenimi nedir?</span><span class="sxs-lookup"><span data-stu-id="97f27-130">What is transfer learning?</span></span>

<span data-ttu-id="97f27-131">Aktarım öğrenimi, bir problemi bir sorunla ilgili diğer soruna çözüm olarak elde edilen bilgileri uygular.</span><span class="sxs-lookup"><span data-stu-id="97f27-131">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="97f27-132">Derin bir öğrenme modelini sıfırdan eğitmek için birkaç parametre, büyük miktarda etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="97f27-132">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="97f27-133">Aktarım öğrenimi ile önceden eğitilen bir modelin kullanılması, eğitim sürecini kısayollara eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="97f27-133">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span> 

## <a name="training-process"></a><span data-ttu-id="97f27-134">Eğitim süreci</span><span class="sxs-lookup"><span data-stu-id="97f27-134">Training process</span></span>

<span data-ttu-id="97f27-135">Görüntü sınıflandırma API 'SI, önceden eğitilen bir TensorFlow modeli yükleyerek eğitim sürecini başlatır.</span><span class="sxs-lookup"><span data-stu-id="97f27-135">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="97f27-136">Eğitim süreci iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="97f27-136">The training process consists of two steps:</span></span>

1. <span data-ttu-id="97f27-137">Performans sorunu aşaması</span><span class="sxs-lookup"><span data-stu-id="97f27-137">Bottleneck phase</span></span>
2. <span data-ttu-id="97f27-138">Eğitim aşaması</span><span class="sxs-lookup"><span data-stu-id="97f27-138">Training phase</span></span>

![Eğitim adımları](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="97f27-140">Performans sorunu aşaması</span><span class="sxs-lookup"><span data-stu-id="97f27-140">Bottleneck phase</span></span>

<span data-ttu-id="97f27-141">Performans sorunu aşamasında, eğitim görüntüleri kümesi yüklenir ve piksel değerleri, önceden eğitilen modelin dondurulmuş katmanları için giriş veya özellikler olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-141">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="97f27-142">Dondurulmuş katmanlar, sinir ağındaki tüm katmanları, tıkanıklık katmanı olarak bilinen Penultimate katmanına kadar içerir.</span><span class="sxs-lookup"><span data-stu-id="97f27-142">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="97f27-143">Bu katmanlarda hiçbir eğitim gerçekleşmediğinden ve işlemler doğrudan geçiş yaptığından, bu katmanlar dondurulmuş olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-143">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="97f27-144">Farklı sınıflar arasında ayrım yapan bir modele yardımcı olan alt düzey desenlerin hesaplandığı, Bu dondurulmuş katmanlarda.</span><span class="sxs-lookup"><span data-stu-id="97f27-144">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="97f27-145">Katman sayısı arttıkça bu adım daha yoğun bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="97f27-145">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="97f27-146">Neyse ki, bu bir kerelik hesaplama olduğundan, sonuçlar önbelleğe alınabilir ve daha sonra farklı parametrelerle denemeler yaparken çalışır.</span><span class="sxs-lookup"><span data-stu-id="97f27-146">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="97f27-147">Eğitim aşaması</span><span class="sxs-lookup"><span data-stu-id="97f27-147">Training phase</span></span>

<span data-ttu-id="97f27-148">Performans sorunlarına neden olan çıkış değerleri hesaplandıktan sonra, modelin son katmanını yeniden eğitmek için giriş olarak kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="97f27-148">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="97f27-149">Bu işlem yinelemeli ve model parametreleri tarafından belirtilen sayıda kez çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-149">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="97f27-150">Her çalıştırma sırasında, kayıp ve doğruluk değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-150">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="97f27-151">Daha sonra, kaybı en aza indirmek ve doğruluğu en üst düzeye çıkarmak için modeli geliştirmek üzere uygun ayarlamalar yapılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-151">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="97f27-152">Eğitim tamamlandığında, iki model biçimi çıkış olur.</span><span class="sxs-lookup"><span data-stu-id="97f27-152">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="97f27-153">Bunlardan biri, modelin `.pb` sürümüdür ve diğeri de modelin `.zip` ML.NET serileştirilmiş sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="97f27-153">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="97f27-154">ML.NET tarafından desteklenen ortamlarda çalışırken, modelin `.zip` sürümünün kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-154">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="97f27-155">Ancak, ML.NET 'in desteklenmediği ortamlarda `.pb` sürümünü kullanma seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="97f27-155">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="97f27-156">Önceden eğitilen modeli anlama</span><span class="sxs-lookup"><span data-stu-id="97f27-156">Understand the pretrained model</span></span>

<span data-ttu-id="97f27-157">Bu öğreticide kullanılan önceden eğitilen model, kalan ağ (ResNet) v2 modelinin 101 katmanlı varyantıdır.</span><span class="sxs-lookup"><span data-stu-id="97f27-157">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="97f27-158">Orijinal model resimleri bin kategoride sınıflandırmakta tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="97f27-158">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="97f27-159">Model, 224 x 224 boyutundaki bir görüntüyü giriş olarak alır ve eğitilen sınıfların her biri için sınıf olasılıkların çıkışını çıkarır.</span><span class="sxs-lookup"><span data-stu-id="97f27-159">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="97f27-160">Bu modelin bir parçası, iki sınıf arasında tahmine dayalı hale getirmek için özel görüntüler kullanarak yeni bir modeli eğitme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-160">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span> 

## <a name="create-console-application"></a><span data-ttu-id="97f27-161">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="97f27-161">Create console application</span></span>

<span data-ttu-id="97f27-162">Aktarım öğrenimine ve görüntü sınıflandırma API 'sine ilişkin genel bir bilgiye sahip olduğunuza göre, uygulamayı derlemek zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-162">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="97f27-163">"DeepLearning_ImageClassification_Binary" adlı bir  **C# .NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97f27-163">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="97f27-164">**Microsoft.ml 1.4.0-preview2** NuGet paketini yüklerken:</span><span class="sxs-lookup"><span data-stu-id="97f27-164">Install the **Microsoft.ML 1.4.0-preview2** NuGet Package:</span></span>
    1. <span data-ttu-id="97f27-165">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="97f27-165">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="97f27-166">Paket kaynağı olarak "nuget.org" öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="97f27-166">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="97f27-167">**Tarayıcı** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="97f27-167">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="97f27-168">**Ön sürümü dahil et** onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="97f27-168">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="97f27-169">**Microsoft.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="97f27-169">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="97f27-170">**Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="97f27-170">Select the **Install** button.</span></span>
    1. <span data-ttu-id="97f27-171">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="97f27-171">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="97f27-172">**Microsoft. ml. DNN 0.16.0-preview2** ve **Microsoft. ml. ımageanalytics 1.4.0-preview2**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="97f27-172">Repeat these steps for **Microsoft.ML.Dnn 0.16.0-preview2** and **Microsoft.ML.ImageAnalytics 1.4.0-preview2**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="97f27-173">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="97f27-173">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="97f27-174">Bu öğreticinin veri kümeleri Maguire, Marc; adresinden Dorafshan, Sattar; ve Thomas, Robert J., "SDNET2018: Machine Learning uygulamaları için somut bir görüntü veri kümesi" (2018).</span><span class="sxs-lookup"><span data-stu-id="97f27-174">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="97f27-175">Tüm veri kümelerine gözatamazsınız.</span><span class="sxs-lookup"><span data-stu-id="97f27-175">Browse all Datasets.</span></span> <span data-ttu-id="97f27-176">Kağıt 48.</span><span class="sxs-lookup"><span data-stu-id="97f27-176">Paper 48.</span></span> <span data-ttu-id="97f27-177">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="97f27-177">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="97f27-178">SDNET2018, kırılmamış ve kırılamayan somut yapılar (köprü kümeleri, duvarlar ve Payalar) için ek açıklamalar içeren bir görüntü veri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="97f27-178">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span> 

![SDNET2018 veri kümesi Köprüsü destesi örnekleri](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="97f27-180">Veriler üç alt dizine göre düzenlenir:</span><span class="sxs-lookup"><span data-stu-id="97f27-180">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="97f27-181">D köprü destesi görüntülerini içerir</span><span class="sxs-lookup"><span data-stu-id="97f27-181">D contains bridge deck images</span></span>
- <span data-ttu-id="97f27-182">P paizni görüntülerini içerir</span><span class="sxs-lookup"><span data-stu-id="97f27-182">P contains pavement images</span></span>
- <span data-ttu-id="97f27-183">W duvar görüntülerini içerir</span><span class="sxs-lookup"><span data-stu-id="97f27-183">W contains wall images</span></span>

<span data-ttu-id="97f27-184">Bu alt dizinlerin her biri, iki ek ön eki içerir:</span><span class="sxs-lookup"><span data-stu-id="97f27-184">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="97f27-185">C, kırçıkarılan yüzeyler için kullanılan önekidir</span><span class="sxs-lookup"><span data-stu-id="97f27-185">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="97f27-186">U, kırçıkarılan yüzeyler için kullanılan önekidir</span><span class="sxs-lookup"><span data-stu-id="97f27-186">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="97f27-187">Bu öğreticide, yalnızca köprü destesi görüntüleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-187">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="97f27-188">[Veri kümesini](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) indirin ve sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="97f27-188">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="97f27-189">Veri kümesi dosyalarınızı kaydetmek için projenizde "varlıklar" adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97f27-189">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="97f27-190">Son daraltılmış dizinden *CD* ve *ud* alt dizinlerini *varlıklar* dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="97f27-190">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="97f27-191">Giriş ve çıkış sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="97f27-191">Create input and output classes</span></span>

1. <span data-ttu-id="97f27-192">*Program.cs* dosyasını açın ve dosyanın en üstündeki mevcut `using` deyimlerini aşağıdaki şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="97f27-192">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="97f27-193">*Program.cs*içinde `Program` sınıfının altında `ImageData`adlı bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97f27-193">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="97f27-194">Bu sınıf başlangıçta yüklenen verileri temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-194">This class is used to represent the initially loaded data.</span></span> 

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L135-L140)]

    <span data-ttu-id="97f27-195">`ImageData` aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="97f27-195">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="97f27-196">`ImagePath`, görüntünün depolandığı tam yoldur.</span><span class="sxs-lookup"><span data-stu-id="97f27-196">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="97f27-197">`Label` görüntünün ait olduğu kategorisidir.</span><span class="sxs-lookup"><span data-stu-id="97f27-197">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="97f27-198">Tahmin edilecek değer budur.</span><span class="sxs-lookup"><span data-stu-id="97f27-198">This is the value to predict.</span></span>

1. <span data-ttu-id="97f27-199">Giriş ve çıkış verileriniz için sınıflar oluşturma</span><span class="sxs-lookup"><span data-stu-id="97f27-199">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="97f27-200">`ImageData` sınıfının altında, giriş verilerinizin şemasını `ModelInput`adlı yeni bir sınıfta tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="97f27-200">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L142-L151)]

        <span data-ttu-id="97f27-201">`ModelInput` aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="97f27-201">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="97f27-202">`ImagePath`, görüntünün depolandığı tam yoldur.</span><span class="sxs-lookup"><span data-stu-id="97f27-202">`ImagePath` is the fully qualified path where the image is stored.</span></span> 
        - <span data-ttu-id="97f27-203">`Label` görüntünün ait olduğu kategorisidir.</span><span class="sxs-lookup"><span data-stu-id="97f27-203">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="97f27-204">Tahmin edilecek değer budur.</span><span class="sxs-lookup"><span data-stu-id="97f27-204">This is the value to predict.</span></span>
        - <span data-ttu-id="97f27-205">`Image` görüntünün `byte[]` gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="97f27-205">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="97f27-206">Model, yansıma verilerinin eğitim için bu türden olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="97f27-206">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="97f27-207">`LabelAsKey`, `Label`sayısal gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="97f27-207">`LabelAsKey` is the numerical representation of the `Label`.</span></span> 

        <span data-ttu-id="97f27-208">Modeli eğitme ve tahmin yapmak için yalnızca `Image` ve `LabelAsKey` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-208">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="97f27-209">`ImagePath` ve `Label` özellikleri özgün görüntü dosyası adına ve kategorisine erişmek için kolaylık sağlamak üzere tutulur.</span><span class="sxs-lookup"><span data-stu-id="97f27-209">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="97f27-210">Daha sonra, `ModelInput` sınıfının altında, çıkış verilerinizin şemasını `ModelOutput`adlı yeni bir sınıfta tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="97f27-210">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span> 

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L153-L160)]

        <span data-ttu-id="97f27-211">`ModelOutput` aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="97f27-211">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="97f27-212">`ImagePath`, görüntünün depolandığı tam yoldur.</span><span class="sxs-lookup"><span data-stu-id="97f27-212">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="97f27-213">`Label` görüntünün ait olduğu özgün kategorisidir.</span><span class="sxs-lookup"><span data-stu-id="97f27-213">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="97f27-214">Tahmin edilecek değer budur.</span><span class="sxs-lookup"><span data-stu-id="97f27-214">This is the value to predict.</span></span> 
        - <span data-ttu-id="97f27-215">`PredictedLabel`, model tarafından tahmin edilen değerdir.</span><span class="sxs-lookup"><span data-stu-id="97f27-215">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="97f27-216">`ModelInput`benzer şekilde, yalnızca `PredictedLabel` model tarafından yapılan tahminleri içerdiğinden tahmine dayalı hale getirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="97f27-216">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="97f27-217">`ImagePath` ve `Label` özellikleri özgün görüntü dosyası adına ve kategorisine erişmek için kolaylık sağlamak amacıyla tutulur.</span><span class="sxs-lookup"><span data-stu-id="97f27-217">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="97f27-218">Yolları tanımlama ve değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="97f27-218">Define paths and initialize variables</span></span>

1. <span data-ttu-id="97f27-219">`Main` yöntemi içinde varlıklarınızın konumunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="97f27-219">Inside the `Main` method, define the location of your assets.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L16)]

1. <span data-ttu-id="97f27-220">Sonra, `mlContext` değişkenini yeni bir [Mlcontext](xref:Microsoft.ML.MLContext)örneğiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="97f27-220">Then, initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L18)]

<span data-ttu-id="97f27-221">[Mlcontext](xref:Microsoft.ML.MLContext) sınıfı tüm ml.NET işlemleri için bir başlangıç noktasıdır ve mlcontext 'i başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97f27-221">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="97f27-222">Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="97f27-222">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="97f27-223">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="97f27-223">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="97f27-224">Veri yükleme yardımcı programı yöntemi oluştur</span><span class="sxs-lookup"><span data-stu-id="97f27-224">Create data loading utility method</span></span>

<span data-ttu-id="97f27-225">Görüntüler iki alt dizine depolanır.</span><span class="sxs-lookup"><span data-stu-id="97f27-225">The images are stored in two subdirectories.</span></span> <span data-ttu-id="97f27-226">Verileri yüklemeden önce, `ImageData` nesnelerinin bir listesi halinde biçimlendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="97f27-226">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="97f27-227">Bunu yapmak için, `Main` yönteminin altında `LoadImagesFromDirectory` yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97f27-227">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="97f27-228">`LoadImagesDirectory` iç dizinlerindeki tüm dosya yollarını almak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="97f27-228">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L102-L103)]

1. <span data-ttu-id="97f27-229">Ardından, bir `foreach` bildiri kullanarak her bir dosyanın üzerinde yineleyin.</span><span class="sxs-lookup"><span data-stu-id="97f27-229">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="97f27-230">`foreach` ifadesinin içinde, dosya uzantılarının desteklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="97f27-230">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="97f27-231">Resim sınıflandırma API 'SI JPEG ve PNG biçimlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="97f27-231">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L107-L108)]

1. <span data-ttu-id="97f27-232">Ardından, dosyanın etiketini alın.</span><span class="sxs-lookup"><span data-stu-id="97f27-232">Then, get the label for the file.</span></span> <span data-ttu-id="97f27-233">`useFolderNameAsLabel` parametresi `true`olarak ayarlanırsa, dosyanın kaydedildiği üst dizin etiket olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-233">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="97f27-234">Aksi takdirde, etiketin dosya adının veya dosya adının ön eki olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="97f27-234">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L110-L124)]

1. <span data-ttu-id="97f27-235">Son olarak, `ModelInput`yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97f27-235">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L126-L130)]

### <a name="prepare-the-data"></a><span data-ttu-id="97f27-236">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="97f27-236">Prepare the data</span></span>

1. <span data-ttu-id="97f27-237">`Main` yöntemine geri döndüğünüzde, eğitim için kullanılan görüntülerin listesini almak için `LoadFromDirectory` yardımcı program yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="97f27-237">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L20)]

1. <span data-ttu-id="97f27-238">Sonra, [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yöntemini kullanarak görüntüleri bir [`IDataView`](xref:Microsoft.ML.IDataView) içine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="97f27-238">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L22)]    

1. <span data-ttu-id="97f27-239">Veriler, dizinlerden okunan sıraya göre yüklenir.</span><span class="sxs-lookup"><span data-stu-id="97f27-239">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="97f27-240">Verileri dengelemek için [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) yöntemi kullanarak karıştırın.</span><span class="sxs-lookup"><span data-stu-id="97f27-240">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L24)]

1. <span data-ttu-id="97f27-241">Makine öğrenimi modelleri, girişin sayısal biçimde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="97f27-241">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="97f27-242">Bu nedenle, eğitimin öncesinde bazı ön işleme verilerin yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="97f27-242">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="97f27-243">[`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) ve [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) dönüştürmelerini [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97f27-243">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) transforms.</span></span> <span data-ttu-id="97f27-244">`MapValueToKey` Transform, `Label` sütununda kategorik değeri alır, sayısal bir `KeyType` değere dönüştürür ve `LabelAsKey`adlı yeni bir sütunda depolar.</span><span class="sxs-lookup"><span data-stu-id="97f27-244">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="97f27-245">`LoadImages`, eğitim için görüntüleri yüklemek üzere `imageFolder` parametresiyle birlikte `ImagePath` sütunundaki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="97f27-245">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span> <span data-ttu-id="97f27-246">`useImageType` `false` olarak ayarlamak, görüntüleri bir `byte[]`dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="97f27-246">Setting the `useImageType` to `false` converts the images into a `byte[]`.</span></span> 

    [!code-csharp [DefinePreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L26-L33)]

1. <span data-ttu-id="97f27-247">[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) yöntemini kullanarak verileri `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ve ardından önceden işlenmiş verileri içeren bir [`IDataView`](xref:Microsoft.ML.IDataView) döndüren [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) yöntemi ile uygulayın.</span><span class="sxs-lookup"><span data-stu-id="97f27-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="97f27-248">Bir modeli eğmek için bir eğitim veri kümesinin yanı sıra bir doğrulama veri kümesi de olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="97f27-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="97f27-249">Model, eğitim kümesi üzerinde eğitilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-249">The model is trained on the training set.</span></span> <span data-ttu-id="97f27-250">Görülmeyen veriler üzerinde tahminleri ne kadar iyi yapar doğrulama kümesine göre performans ile ölçülür.</span><span class="sxs-lookup"><span data-stu-id="97f27-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="97f27-251">Model, bu performansın sonuçlarına bağlı olarak, geliştirme çabasında ne kadar öğrenildiği konusunda ayarlamalar yapar.</span><span class="sxs-lookup"><span data-stu-id="97f27-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="97f27-252">Doğrulama kümesi, özgün veri kümenizi veya bu amaçla zaten ayrılmış olan başka bir kaynağı bölerek gelebilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="97f27-253">Bu durumda, önceden işlenmiş veri kümesi eğitim, doğrulama ve test kümelerine bölünür.</span><span class="sxs-lookup"><span data-stu-id="97f27-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="97f27-254">Yukarıdaki kod örneği iki bölme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="97f27-254">The code sample above performs two splits.</span></span> <span data-ttu-id="97f27-255">İlk olarak, önceden işlenmiş veriler bölünür ve %70, doğrulama için kalan %30 ' u kullanıldığında eğitim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="97f27-256">Daha sonra, %30 doğrulama kümesi daha fazla doğrulama ve test kümelerine bölünür; burada %90 doğrulama için kullanılır ve test için %10 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span> 

    <span data-ttu-id="97f27-257">Bu veri bölümlerinin amacını düşünmek için bir yol, bir sınavın.</span><span class="sxs-lookup"><span data-stu-id="97f27-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="97f27-258">Bir sınava göre çalışırken, sınavlarda bulunan kavramlara bir attık almak için notlarınızı, kitapları veya diğer kaynaklarınızı gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="97f27-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="97f27-259">Bu, eğitim kümesinin için olduğu şeydir.</span><span class="sxs-lookup"><span data-stu-id="97f27-259">This is what the train set is for.</span></span> <span data-ttu-id="97f27-260">Daha sonra, bilginizi doğrulamak için bir sahte sınava sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97f27-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="97f27-261">Bu, doğrulama kümesinin yararlı olduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="97f27-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="97f27-262">Gerçek sınava girmeden önce kavramların iyi bir yermi olduğunu kontrol etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="97f27-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="97f27-263">Bu sonuçlara dayanarak, ne kadar yanlış olduğunu veya iyi anladığınızı ve gerçek sınava göre gözden geçirdiğinize ilişkin değişikliklerinizi dahil etmediğinizi göz önünde bulmalısınız.</span><span class="sxs-lookup"><span data-stu-id="97f27-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="97f27-264">Son olarak, sınava sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="97f27-264">Finally, you take the exam.</span></span> <span data-ttu-id="97f27-265">Bu, için test kümesinin kullanıldığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="97f27-265">This is what the test set is used for.</span></span> <span data-ttu-id="97f27-266">Sınavdaki soruları hiç gördüğdiniz ve şimdi eğitim ve doğrulamadan öğrendiklerinizi kullanarak bilgilerinizi el ile görev için nasıl uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="97f27-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span> 

1. <span data-ttu-id="97f27-267">Eğitim, doğrulama ve test verileri için bölümleri ilgili değerleri atayın.</span><span class="sxs-lookup"><span data-stu-id="97f27-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="97f27-268">Eğitim işlem hattını tanımlama</span><span class="sxs-lookup"><span data-stu-id="97f27-268">Define the training pipeline</span></span>

<span data-ttu-id="97f27-269">Model eğitimi birkaç adımdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="97f27-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="97f27-270">İlk olarak, modeli eğitmek için görüntü sınıflandırma API 'SI kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="97f27-271">Daha sonra, `PredictedLabel` sütunundaki kodlanmış Etiketler, `MapKeyToValue` dönüşümü kullanılarak özgün kategorik değerlerine geri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="97f27-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span> 

1. <span data-ttu-id="97f27-272">Hem `mapLabelEstimator` hem de `ImageClassification` dönüşümlerinden oluşan eğitim [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) işlem hattını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="97f27-272">Define the training [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pipeline that consists of both the `mapLabelEstimator` and the `ImageClassification` transforms.</span></span>

    [!code-csharp [DefineTrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L58)]    

    <span data-ttu-id="97f27-273">`ImageClassification` tahmin aracı birkaç parametre alır:</span><span class="sxs-lookup"><span data-stu-id="97f27-273">The `ImageClassification` estimator takes in several parameters:</span></span>

    - <span data-ttu-id="97f27-274">`featuresColumnName`, model için girdi olarak kullanılan sütundur.</span><span class="sxs-lookup"><span data-stu-id="97f27-274">`featuresColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="97f27-275">`labelColumnName`, tahmin edilecek değerin sütundeğeridir.</span><span class="sxs-lookup"><span data-stu-id="97f27-275">`labelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="97f27-276">`arch`, önceden eğitilen model mimarilerinden hangisinin kullanılacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97f27-276">`arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="97f27-277">Bu öğretici ResNetv2 modelinin 101 katman türevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="97f27-277">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="97f27-278">`epoch`, eğitim işlemi boyunca tüm veri kümesi üzerinde en fazla yineleme sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="97f27-278">`epoch` specifies the maximum number of iterations over the entire dataset throughout the training process.</span></span> <span data-ttu-id="97f27-279">Sayı arttıkça, model ne kadar uzun bir süre ve üretilen daha iyi bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="97f27-279">The higher the number, the longer the model trains for and potentially the better model that is produced.</span></span>
    - <span data-ttu-id="97f27-280">`batchSize`, eğitim için bir seferde kullanılacak örnek sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="97f27-280">`batchSize` is the number of samples to use at a time for training.</span></span> <span data-ttu-id="97f27-281">Bir dönem sırasında, modeli eğitmek ve güncellemek için batchSize eşit birden çok yığın kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97f27-281">During one epoch, multiple batches equal to the batchSize are used to train and update the model.</span></span> <span data-ttu-id="97f27-282">Sayı ne kadar düşükse, her toplu işlem işlendiğinde daha az bellek gerekir.</span><span class="sxs-lookup"><span data-stu-id="97f27-282">The lower the number, the less memory required when each batch is processed.</span></span>
    - <span data-ttu-id="97f27-283">`testOnTrainSet`, bir doğrulama kümesi mevcut olmadığında modelin eğitim kümesine karşı performansını ölçmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="97f27-283">`testOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="97f27-284">`metricsCallback` eğitim sırasında ilerlemeyi izlemek için bir işlevi bağlar.</span><span class="sxs-lookup"><span data-stu-id="97f27-284">`metricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="97f27-285">`validationSet`, doğrulama verilerini içeren [`IDataView`](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="97f27-285">`validationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="97f27-286">`reuseTrainSetBottleneckCachedValues`, sonraki çalışmalarda performans sorunlarına neden olan önbelleğe alınmış değerleri kullanıp kullanmayacağınızı modele söyler.</span><span class="sxs-lookup"><span data-stu-id="97f27-286">`reuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="97f27-287">Performans sorunu, ilk çalıştırıldığında yoğun bir şekilde yoğun bir geçiş hesaplasıdır.</span><span class="sxs-lookup"><span data-stu-id="97f27-287">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="97f27-288">Eğitim verileri değişmezse ve farklı sayıda dönemler veya toplu iş boyutu kullanmayı denemek istiyorsanız, önbelleğe alınmış değerleri kullanmak bir modeli eğmek için gereken süreyi önemli ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="97f27-288">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="97f27-289">`reuseValidationSetBottleneckCachedValues`, yalnızca bu örnekte doğrulama veri kümesi için olan `reuseTrainSetBottleneckCachedValues` benzerdir.</span><span class="sxs-lookup"><span data-stu-id="97f27-289">`reuseValidationSetBottleneckCachedValues` is similar to `reuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="97f27-290">`disableEarlyStopping`, ımageclassıflıya erken bir durdurma stratejisi kullanıp kullanmayacağınızı söyler.</span><span class="sxs-lookup"><span data-stu-id="97f27-290">`disableEarlyStopping` tells the ImageClassification estimator whether to employ an early stopping strategy.</span></span> <span data-ttu-id="97f27-291">Model, eğitim sırasında doğru öngörülere sahip olmaya yardımcı olacak en iyi değerleri aradığında, performans artabilir veya azalabilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-291">As the model searches for the optimal values that will help it make accurate predictions during training, performance may increase or decrease.</span></span> <span data-ttu-id="97f27-292">Sonuç olarak, model son dönemi ulaşırsa, eğitiminden öğrendiği desenlerin en küçük bir hal olması durumunda olabilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-292">Ultimately, if the model reaches the last epoch, it may be the case that the patterns it learned from training are suboptimal.</span></span> <span data-ttu-id="97f27-293">Erken durdurma, bu performans için eğitimin performansını izler ve modelin en iyi sürümünü koruma çabasında eğitim sürecini keser.</span><span class="sxs-lookup"><span data-stu-id="97f27-293">Early stopping monitors training for these drops in performance and stops the training process in an effort to preserve an optimal version of the model.</span></span>

1. <span data-ttu-id="97f27-294">Modelinize eğitebilmeniz için [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="97f27-294">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L60)]

## <a name="use-the-model"></a><span data-ttu-id="97f27-295">Modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="97f27-295">Use the model</span></span>

<span data-ttu-id="97f27-296">Modelinize eğitim sahibi olduğunuza göre, görüntüleri sınıflandırmak için kullanmanın zamanı.</span><span class="sxs-lookup"><span data-stu-id="97f27-296">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="97f27-297">`Main` yönteminin altında, konsolunda tahmin bilgilerini göstermek için `OutputPrediction` adlı yeni bir yardımcı program yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97f27-297">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L94-L98)]

### <a name="classify-a-single-image"></a><span data-ttu-id="97f27-298">Tek bir görüntüyü sınıflandır</span><span class="sxs-lookup"><span data-stu-id="97f27-298">Classify a single image</span></span>

1. <span data-ttu-id="97f27-299">Tek bir görüntü tahminini yapmak ve çıkarmak için `Main` yönteminin altına `ClassifySingleImage` adlı yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="97f27-299">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="97f27-300">`ClassifySingleImage` yöntemi içinde [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97f27-300">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="97f27-301">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneği üzerinde bir tahmin etmenizi ve daha sonra bir tahmin gerçekleştirmenizi sağlayan KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="97f27-301">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L71)]    

1. <span data-ttu-id="97f27-302">Tek bir `ModelInput` örneğine erişmek için, [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemini kullanarak `data` [`IDataView`](xref:Microsoft.ML.IDataView) bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dönüştürün ve ardından ilk gözlemyi alın.</span><span class="sxs-lookup"><span data-stu-id="97f27-302">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span> 

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="97f27-303">Görüntüyü sınıflandırmak için [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="97f27-303">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="97f27-304">`OutputPrediction` yöntemiyle, tahmine konsola çıkış yapın.</span><span class="sxs-lookup"><span data-stu-id="97f27-304">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77-L78)]

1. <span data-ttu-id="97f27-305">`Main` yönteminin içinde, görüntü sınama kümesini kullanarak `ClassifySingleImage` çağırın.</span><span class="sxs-lookup"><span data-stu-id="97f27-305">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

### <a name="classify-multiple-images"></a><span data-ttu-id="97f27-306">Birden çok görüntüyü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="97f27-306">Classify multiple images</span></span>

1. <span data-ttu-id="97f27-307">Birden çok görüntü Tahminleri yapmak ve çıkarmak için `ClassifySingleImage` yönteminin altına `ClassifyImages` adlı yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="97f27-307">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="97f27-308">[`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodunu kullanarak tahminleri içeren bir [`IDataView`](xref:Microsoft.ML.IDataView) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97f27-308">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="97f27-309">`ClassifyImages` yönteminin içine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="97f27-309">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L83)]

1. <span data-ttu-id="97f27-310">Tahmine dayalı olarak yinelemek için, `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemini kullanarak [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dönüştürün ve ardından ilk 10 gözlemleme elde edin.</span><span class="sxs-lookup"><span data-stu-id="97f27-310">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="97f27-311">Tahmine dayalı olarak orijinal ve tahmin edilen etiketleri yineleyin ve çıktı.</span><span class="sxs-lookup"><span data-stu-id="97f27-311">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87-L91)]

1. <span data-ttu-id="97f27-312">Son olarak, `Main` yönteminin içinde, görüntü sınama kümesini kullanarak `ClassifyImages` çağırın.</span><span class="sxs-lookup"><span data-stu-id="97f27-312">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

## <a name="run-the-application"></a><span data-ttu-id="97f27-313">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="97f27-313">Run the application</span></span>

<span data-ttu-id="97f27-314">Konsol uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="97f27-314">Run your console app.</span></span> <span data-ttu-id="97f27-315">Çıktının aşağıdakine benzer olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="97f27-315">The output should be similar to that below.</span></span> <span data-ttu-id="97f27-316">Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="97f27-316">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="97f27-317">Breçekimi için çıkış yoğunlaştırılmış.</span><span class="sxs-lookup"><span data-stu-id="97f27-317">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="97f27-318">**Performans sorunu aşaması**</span><span class="sxs-lookup"><span data-stu-id="97f27-318">**Bottleneck phase**</span></span>

<span data-ttu-id="97f27-319">Görüntüler `byte[]` olarak yüklendiği için görüntü adı için hiçbir değer yazdırılamaz, bu nedenle görüntülenecek görüntü adı yok.</span><span class="sxs-lookup"><span data-stu-id="97f27-319">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279, Image Name:
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2, Image Name:
```

<span data-ttu-id="97f27-320">**Eğitim aşaması**</span><span class="sxs-lookup"><span data-stu-id="97f27-320">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="97f27-321">**Görüntüleri sınıflandırın çıktısı**</span><span class="sxs-lookup"><span data-stu-id="97f27-321">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="97f27-322">*7001 -220. jpg* görüntüsünü incelemeden, aslında bunun kırdığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97f27-322">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span> 

![Tahmin için kullanılan SDNET2018 veri kümesi görüntüsü](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="97f27-324">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="97f27-324">Congratulations!</span></span> <span data-ttu-id="97f27-325">Artık görüntülerin sınıflandırılmasına yönelik derin bir öğrenme modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="97f27-325">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="97f27-326">Modeli geliştirme</span><span class="sxs-lookup"><span data-stu-id="97f27-326">Improve the model</span></span>

<span data-ttu-id="97f27-327">Modelinizin sonuçlarını tatmin ediyorsanız, aşağıdaki yaklaşımlardan bazılarını deneyerek performansını geliştirmeyi deneyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="97f27-327">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="97f27-328">**Daha fazla veri**: bir modelin öğreni daha fazla örnek, ne kadar iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="97f27-328">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="97f27-329">Tam [SDNET2018 veri kümesini](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) indirip eğmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="97f27-329">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span> 
- <span data-ttu-id="97f27-330">**Verileri artırmak**: verileri bir görüntü alarak ve farklı dönüşümler uygulayarak (Döndür, çevir, Shift, Kırp) veri eklemek için sık kullanılan bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="97f27-330">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="97f27-331">Bu, modelin öğreni için daha fazla değişken örnek ekler.</span><span class="sxs-lookup"><span data-stu-id="97f27-331">This adds more varied examples for the model to learn from.</span></span> 
- <span data-ttu-id="97f27-332">Daha **uzun bir süre eğitin**: daha fazla eğitede, model daha fazla ayarlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="97f27-332">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="97f27-333">Dönemler sayısının artırılması, modelinizin performansını iyileştirebilecek.</span><span class="sxs-lookup"><span data-stu-id="97f27-333">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="97f27-334">**Hyper-Parameters Ile denemeler yapın**: Bu öğreticide kullanılan parametrelere ek olarak, diğer parametreler potansiyel olarak performansı iyileştirecek şekilde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-334">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="97f27-335">Her dönem performansı iyileştirebilmek için modele yapılan güncelleştirmelerin büyüklüğünü belirleyen öğrenme oranını değiştirme.</span><span class="sxs-lookup"><span data-stu-id="97f27-335">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="97f27-336">**Farklı bir model mimarisi kullanın**: verilerinizin neye benzer olduğuna bağlı olarak, özelliklerini en iyi şekilde öğrenen en iyi şekilde bir model farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="97f27-336">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="97f27-337">Modelinizin performansını karşılıyoruz, mimariyi değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="97f27-337">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="97f27-338">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="97f27-338">Additional Resources</span></span>

- <span data-ttu-id="97f27-339">[Derin öğrenme vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="97f27-339">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="97f27-340">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="97f27-340">Next steps</span></span>

<span data-ttu-id="97f27-341">Bu öğreticide, aktarım öğrenimi, önceden eğitilen bir görüntü sınıflandırması TensorFlow modeli ve ML.NET görüntü sınıflandırma API 'sini kullanarak, somut yüzeyleri kırıllanmış veya kırılk olarak sınıflandırmakta olan özel bir derin öğrenme modeli oluşturmayı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="97f27-341">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="97f27-342">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="97f27-342">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="97f27-343">Nesne algılama</span><span class="sxs-lookup"><span data-stu-id="97f27-343">Object Detection</span></span>](object-detection-onnx.md)
