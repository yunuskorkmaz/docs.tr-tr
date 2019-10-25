---
title: 'Öğretici: önceden eğitilen bir TensorFlow modelinden ML.NET görüntü sınıflandırma modeli oluşturma'
description: Mevcut bir TensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline bilgi aktarmayı öğrenin. TensorFlow modeli görüntüleri bin kategoride sınıflandırmakta eğitildi. ML.NET modeli görüntüleri daha az daha geniş kategoriler halinde sınıflandırmak için aktarım öğrenimini kullanır.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 399e9ce3288d53049e968688736f5b953d7e5b80
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799082"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="db49b-105">Öğretici: önceden eğitilen bir TensorFlow modelinden ML.NET görüntü sınıflandırma modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="db49b-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="db49b-106">Mevcut bir TensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline bilgi aktarmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="db49b-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="db49b-107">TensorFlow modeli görüntüleri bin kategoride sınıflandırmakta eğitildi.</span><span class="sxs-lookup"><span data-stu-id="db49b-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="db49b-108">ML.NET modeli, görüntüleri 3 kategoride sınıflandırmak üzere bir modeli eğitemak için, ardışık düzeninde TensorFlow modelinin bir parçasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="db49b-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="db49b-109">[Görüntü sınıflandırma](https://en.wikipedia.org/wiki/Outline_of_object_recognition) modelini sıfırdan eğitmek için milyonlarca parametre, bir dizi etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="db49b-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="db49b-110">Özel bir modeli sıfırdan eğitmek kadar uygun olmasa da, aktarım öğrenimi, binlerce görüntüde ve çok hızlı bir şekilde özelleştirilmiş bir model (bir saat içinde, GPU).</span><span class="sxs-lookup"><span data-stu-id="db49b-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="db49b-111">Bu öğreticide, yalnızca bir düzine eğitim görüntüsü kullanılarak bu işlem daha da ayrıntılı şekilde ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="db49b-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="db49b-112">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="db49b-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="db49b-113">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="db49b-113">Understand the problem</span></span>
> * <span data-ttu-id="db49b-114">Önceden eğitilen TensorFlow modelini ML.NET işlem hattına ekleyin</span><span class="sxs-lookup"><span data-stu-id="db49b-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="db49b-115">ML.NET modelini eğitme ve değerlendirme</span><span class="sxs-lookup"><span data-stu-id="db49b-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="db49b-116">Test görüntüsünü sınıflandır</span><span class="sxs-lookup"><span data-stu-id="db49b-116">Classify a test image</span></span>

<span data-ttu-id="db49b-117">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db49b-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="db49b-118">Varsayılan olarak, Bu öğreticinin .NET proje yapılandırmasında .NET Core 2,2 ' i hedeflediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="db49b-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="db49b-119">Aktarım öğrenimi nedir?</span><span class="sxs-lookup"><span data-stu-id="db49b-119">What is transfer learning?</span></span>

<span data-ttu-id="db49b-120">Aktarım öğrenimi, bir sorunu çözerken ve ilgili başka bir soruna uygulanarak bilgi elde edilen bilgileri kullanma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="db49b-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="db49b-121">Bu öğretici için, görüntüleri 3 kategoriye göre sınıflandıran bir ML.NET modelinde resimleri bin kategoride sınıflandırmakta olan bir TensorFlow modelinin bir bölümünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="db49b-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="db49b-122">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="db49b-122">Prerequisites</span></span>

* <span data-ttu-id="db49b-123">[Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="db49b-123">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="db49b-124">Microsoft.ML 1.3.1 NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="db49b-124">Microsoft.ML 1.3.1 Nuget package</span></span>
* <span data-ttu-id="db49b-125">Microsoft. ML. ımageanalytics 1.3.1 NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="db49b-125">Microsoft.ML.ImageAnalytics 1.3.1 Nuget package</span></span>
* <span data-ttu-id="db49b-126">Microsoft. ML. TensorFlow 1.3.1 NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="db49b-126">Microsoft.ML.TensorFlow 1.3.1 Nuget package</span></span>

* [<span data-ttu-id="db49b-127">Öğretici varlıkları dizini. ZIP dosyası</span><span class="sxs-lookup"><span data-stu-id="db49b-127">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)

* [<span data-ttu-id="db49b-128">InceptionV1 Machine Learning modeli</span><span class="sxs-lookup"><span data-stu-id="db49b-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="db49b-129">Doğru makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="db49b-129">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="db49b-130">Derin öğrenme</span><span class="sxs-lookup"><span data-stu-id="db49b-130">Deep learning</span></span>

<span data-ttu-id="db49b-131">[Derin öğrenme](https://en.wikipedia.org/wiki/Deep_learning) , görüntü işleme ve konuşma tanıma gibi revolutionizing alan Machine Learning bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="db49b-131">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="db49b-132">Derin öğrenme modelleri, birden fazla öğrenme katmanı içeren büyük ölçekli [veri](https://en.wikipedia.org/wiki/Labeled_data) ve [sinir Networks](https://en.wikipedia.org/wiki/Artificial_neural_network) kümeleri kullanılarak eğitilir.</span><span class="sxs-lookup"><span data-stu-id="db49b-132">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="db49b-133">Derin öğrenme:</span><span class="sxs-lookup"><span data-stu-id="db49b-133">Deep learning:</span></span>

* <span data-ttu-id="db49b-134">Görüntü İşleme gibi bazı görevlerde daha iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="db49b-134">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="db49b-135">Çok büyük miktarlarda eğitim verisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="db49b-135">Requires huge amounts of training data.</span></span>

<span data-ttu-id="db49b-136">Görüntü sınıflandırması, görüntüleri otomatik olarak kategoriler halinde sınıflandırmamızı sağlayan ortak bir Machine Learning görevdir:</span><span class="sxs-lookup"><span data-stu-id="db49b-136">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="db49b-137">Görüntüde insan yüzü algılanıyor.</span><span class="sxs-lookup"><span data-stu-id="db49b-137">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="db49b-138">Kediler ve köpekler algılanıyor.</span><span class="sxs-lookup"><span data-stu-id="db49b-138">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="db49b-139">Aşağıdaki görüntülerde olduğu gibi, bir resmin (n) yiyecek, oyunı veya gereç olduğunu belirleme:</span><span class="sxs-lookup"><span data-stu-id="db49b-139">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="db49b-140">![pizza Image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![oyuncak ayı görüntü](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![Toaster Image](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="db49b-140">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="db49b-141">Önceki görüntüler Wikimedia Commons ' a aittir ve aşağıdaki gibi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="db49b-141">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="db49b-142">"220px-Pepperoni_pizza. jpg" genel etki alanı, https://commons.wikimedia.org/w/index.php?curid=79505 ,</span><span class="sxs-lookup"><span data-stu-id="db49b-142">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="db49b-143">[Jonık](https://commons.wikimedia.org/wiki/User:Jonik) -Self-Photo, CC BY-SA 2,0 https://commons.wikimedia.org/w/index.php?curid=48166 tarafından "119px-Nalle_-_a_small_brown_teddy_bear. jpg".</span><span class="sxs-lookup"><span data-stu-id="db49b-143">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="db49b-144">"193px-Broodrooster. jpg"- [k. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) -kendi ÇALıŞMASı, CC BY-SA 3,0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="db49b-144">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="db49b-145">`Inception model` görüntüleri bin kategoride sınıflandırıp, ancak bu öğreticide, görüntüleri daha küçük bir kategori kümesinde ve yalnızca bu kategorilerden sınıflandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="db49b-145">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="db49b-146">`transfer learning``transfer` bölümünü girin.</span><span class="sxs-lookup"><span data-stu-id="db49b-146">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="db49b-147">`Inception model`, resimleri tanıma ve sınıflandırıp özel görüntü sınıflandırıcınızın yeni sınırlı kategorilerine aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db49b-147">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="db49b-148">Yemek</span><span class="sxs-lookup"><span data-stu-id="db49b-148">Food</span></span>
* <span data-ttu-id="db49b-149">Cağı</span><span class="sxs-lookup"><span data-stu-id="db49b-149">Toy</span></span>
* <span data-ttu-id="db49b-150">Elektrikli</span><span class="sxs-lookup"><span data-stu-id="db49b-150">Appliance</span></span>

<span data-ttu-id="db49b-151">Bu öğretici, `ImageNet` veri kümesi üzerinde eğitilen popüler bir görüntü tanıma modeli olan TensorFlow [Inception modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) derin öğrenme modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="db49b-151">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="db49b-152">TensorFlow modeli, tüm görüntüleri "şemsiye", "Jersey" ve "Dishronı" gibi binlik bir sınıfa göre sınıflandırır.</span><span class="sxs-lookup"><span data-stu-id="db49b-152">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="db49b-153">`Inception model`, binlerce farklı görüntüde önceden eğitildiğinden, dahili olarak görüntü tanımlama için gereken [görüntü özelliklerini](https://en.wikipedia.org/wiki/Feature_(computer_vision)) içerir.</span><span class="sxs-lookup"><span data-stu-id="db49b-153">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="db49b-154">En az sınıfa sahip yeni bir modeli eğitebilmeniz için modelde bu iç görüntü özelliklerinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db49b-154">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="db49b-155">Aşağıdaki diyagramda gösterildiği gibi, .NET Core veya .NET Framework uygulamalarında ML.NET NuGet paketlerine bir başvuru eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="db49b-155">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="db49b-156">ML.NET dahil olmak üzere, var olan eğitilen bir `TensorFlow` modeli dosyasını yükleyen kodu yazmanıza izin veren yerel `TensorFlow` kitaplığına başvurur.</span><span class="sxs-lookup"><span data-stu-id="db49b-156">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![TensorFlow Transform ML.NET yay diyagramı](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="db49b-158">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="db49b-158">Multiclass classification</span></span>

<span data-ttu-id="db49b-159">Klasik makine öğrenimi algoritması için giriş olarak uygun özellikleri ayıklamak üzere TensorFlow kullanım modelini kullandıktan sonra, ML.NET [çok sınıflı bir sınıflandırıcı](../resources/tasks.md#multiclass-classification)ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="db49b-159">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="db49b-160">Bu durumda kullanılan belirli bir eğitmen, [ÇOKTERİMLİ lojistik regresyon algoritmasıdır](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="db49b-160">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="db49b-161">Bu eğitimci tarafından uygulanan algoritma, görüntü verilerinde çalışan derin bir öğrenme modelinin durumu olan çok sayıda özellik ile ilgili sorunları iyi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="db49b-161">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="db49b-162">Veri</span><span class="sxs-lookup"><span data-stu-id="db49b-162">Data</span></span>

<span data-ttu-id="db49b-163">İki veri kaynağı vardır: `.tsv` dosyası ve görüntü dosyaları.</span><span class="sxs-lookup"><span data-stu-id="db49b-163">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="db49b-164">`tags.tsv` dosyası iki sütun içerir: Birincisi, `ImagePath` olarak tanımlanır ve ikinci tane görüntüye karşılık gelen `Label`.</span><span class="sxs-lookup"><span data-stu-id="db49b-164">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="db49b-165">Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="db49b-165">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="db49b-166">Eğitim ve test görüntüleri, bir ZIP dosyasında indirileceği varlıklar klasörlerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="db49b-166">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="db49b-167">Bu görüntüler Wikimedia Commons ' a aittir.</span><span class="sxs-lookup"><span data-stu-id="db49b-167">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="db49b-168">*[Wkımedıa Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), ücretsiz medya deposu.*</span><span class="sxs-lookup"><span data-stu-id="db49b-168">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="db49b-169">10:48 Ekim, 2018: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear alındı</span><span class="sxs-lookup"><span data-stu-id="db49b-169">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="db49b-170">Kurulum</span><span class="sxs-lookup"><span data-stu-id="db49b-170">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="db49b-171">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="db49b-171">Create a project</span></span>

1. <span data-ttu-id="db49b-172">"TransferLearningTF" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="db49b-172">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="db49b-173">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="db49b-173">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="db49b-174">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="db49b-174">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="db49b-175">Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="db49b-175">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="db49b-176">**Sürüm** açılır listesine tıklayın, listeden **1.3.1** paketini seçin ve ardından **Kaldır düğmesini seçin** .</span><span class="sxs-lookup"><span data-stu-id="db49b-176">Click on the **Version** drop-down, select the **1.3.1** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="db49b-177">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="db49b-177">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="db49b-178">Listelenen paketlerin lisans koşullarını kabul ediyorsanız, **Lisans kabulü** Iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="db49b-178">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="db49b-179">**Microsoft. ml. ımageanalytics v 1.3.1** ve **Microsoft. ml. TensorFlow v 1.3.1**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="db49b-179">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.3.1** and **Microsoft.ML.TensorFlow v1.3.1**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="db49b-180">Varlıkları indir</span><span class="sxs-lookup"><span data-stu-id="db49b-180">Download assets</span></span>

1. <span data-ttu-id="db49b-181">[Proje Varlıkları Dizin ZIP dosyasını](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)indirin ve sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="db49b-181">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="db49b-182">`assets` dizinini *Transferlearningtf* proje dizininize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="db49b-182">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="db49b-183">Bu dizin ve alt dizinleri, bu öğretici için gerekli olan veri ve destek dosyalarını (bir sonraki adımda indirecek ve ekleyeceğiniz bir model hariç) içerir.</span><span class="sxs-lookup"><span data-stu-id="db49b-183">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="db49b-184">[Inception modelini](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)indirin ve sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="db49b-184">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="db49b-185">`inception5h` dizininin içeriğini, *Transferlearningtf* Project `assets/inputs-train/inception` dizininize kopyalamanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="db49b-185">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inputs-train/inception` directory.</span></span> <span data-ttu-id="db49b-186">Bu dizin, aşağıdaki görüntüde gösterildiği gibi, bu öğretici için gereken modeli ve ek destek dosyalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="db49b-186">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Dizin içeriğini geçersiz kılma](./media/image-classification/inception-files.png)

1. <span data-ttu-id="db49b-188">Çözüm Gezgini, varlık dizinindeki ve alt dizinlerde bulunan dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="db49b-188">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="db49b-189">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="db49b-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="db49b-190">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="db49b-190">Create classes and define paths</span></span>

1. <span data-ttu-id="db49b-191">*Program.cs* dosyasının en üstüne aşağıdaki ek `using` deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-191">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. <span data-ttu-id="db49b-192">Varlık yollarını belirtmek için, `Main` yönteminin hemen üstüne aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-192">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="db49b-193">Giriş verileriniz ve tahminler için sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="db49b-193">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    <span data-ttu-id="db49b-194">`ImageData`, giriş resmi veri sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="db49b-194">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="db49b-195">`ImagePath` resim dosyası adını içerir.</span><span class="sxs-lookup"><span data-stu-id="db49b-195">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="db49b-196">`Label` resim etiketi için bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="db49b-196">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="db49b-197">`ImagePrediction`için projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-197">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="db49b-198">`ImagePrediction`, görüntü tahmin sınıfıdır ve aşağıdaki alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="db49b-198">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="db49b-199">`Score`, belirli bir görüntü sınıflandırması için güvenirlik yüzdesini içerir.</span><span class="sxs-lookup"><span data-stu-id="db49b-199">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="db49b-200">`PredictedLabelValue`, tahmin edilen görüntü sınıflandırma etiketi için bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="db49b-200">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="db49b-201">`ImagePrediction`, model eğitilen bir tahmin için kullanılan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="db49b-201">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="db49b-202">Görüntü yolu için bir `string` (`ImagePath`) vardır.</span><span class="sxs-lookup"><span data-stu-id="db49b-202">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="db49b-203">`Label` modeli yeniden kullanmak ve geliştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db49b-203">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="db49b-204">`PredictedLabelValue`, tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db49b-204">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="db49b-205">Değerlendirme için eğitim verileri olan bir giriş, tahmin edilen değerler ve model kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db49b-205">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="db49b-206">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="db49b-206">Initialize variables in Main</span></span>

1. <span data-ttu-id="db49b-207">`mlContext` değişkenini yeni bir `MLContext`örneğiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="db49b-207">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="db49b-208">@No__t_0 satırını `Main` yönteminde aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="db49b-208">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    <span data-ttu-id="db49b-209">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve `mlContext` başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db49b-209">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="db49b-210">Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="db49b-210">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="db49b-211">Inception model parametreleri için bir struct oluşturun</span><span class="sxs-lookup"><span data-stu-id="db49b-211">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="db49b-212">Inception modelinde, geçirmeniz gereken birkaç parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="db49b-212">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="db49b-213">Parametre değerlerini, `Main()` yönteminden hemen sonra aşağıdaki kodla kolay adlarla eşlemek için bir struct oluşturun:</span><span class="sxs-lookup"><span data-stu-id="db49b-213">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="db49b-214">Görüntüleme yardımcı programı yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="db49b-214">Create a display utility method</span></span>

<span data-ttu-id="db49b-215">Görüntü verilerini ve ilgili tahminleri birden çok kez görüntüleyenden sonra, görüntüyü ve tahmin sonuçlarını görüntülemeyi işlemek için bir görüntüleme yardımcı programı yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="db49b-215">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="db49b-216">Aşağıdaki kodu kullanarak, `InceptionSettings` yapısı hemen sonrasında `DisplayResults()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="db49b-216">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="db49b-217">`DisplayResults` yönteminin gövdesini doldur:</span><span class="sxs-lookup"><span data-stu-id="db49b-217">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="db49b-218">. Tsv dosya yardımcı programı yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="db49b-218">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="db49b-219">Aşağıdaki kodu kullanarak, `DisplayResults()` yönteminden hemen sonra `ReadFromTsv()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="db49b-219">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="db49b-220">`ReadFromTsv` yönteminin gövdesini doldur:</span><span class="sxs-lookup"><span data-stu-id="db49b-220">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    <span data-ttu-id="db49b-221">Kod, `ImagePath` özelliğinin görüntü dosyası adına dosya yolunu eklemek ve onu ve `Label` bir `ImageData` nesnesine yüklemek için `tags.tsv` dosyası aracılığıyla ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="db49b-221">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="db49b-222">Tahmin yapmak için bir yöntem oluşturma</span><span class="sxs-lookup"><span data-stu-id="db49b-222">Create a method to make a prediction</span></span>

1. <span data-ttu-id="db49b-223">Aşağıdaki kodu kullanarak, `DisplayResults()` yönteminden hemen önce `ClassifySingleImage()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="db49b-223">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="db49b-224">Tek `ImagePath`tam yolunu ve resim dosyası adını içeren bir `ImageData` nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="db49b-224">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="db49b-225">Aşağıdaki kodu `ClassifySingleImage()` yönteminin sonraki satırları olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-225">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. <span data-ttu-id="db49b-226">Aşağıdaki kodu `ClassifySingleImage` yöntemine bir sonraki satır olarak ekleyerek tek bir tahmin yapın:</span><span class="sxs-lookup"><span data-stu-id="db49b-226">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    <span data-ttu-id="db49b-227">Tahmin sağlamak için, [tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="db49b-227">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="db49b-228">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="db49b-228">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="db49b-229">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="db49b-229">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="db49b-230">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="db49b-230">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="db49b-231">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="db49b-231">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="db49b-232">[ASP.NET Core Web API 'sindeki `PredictionEnginePool` kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="db49b-232">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="db49b-233">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="db49b-233">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="db49b-234">Tahmin sonucunu `ClassifySingleImage()` yönteminde sonraki kod satırı olarak görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-234">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="db49b-235">ML.NET model işlem hattını oluşturma</span><span class="sxs-lookup"><span data-stu-id="db49b-235">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="db49b-236">Bir ML.NET model işlem hattı, bir tahmin zinciri zinciridir.</span><span class="sxs-lookup"><span data-stu-id="db49b-236">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="db49b-237">İşlem hattı oluşturma sırasında yürütmenin gerçekleşmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="db49b-237">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="db49b-238">Tahmin aracı nesneleri oluşturulur ancak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="db49b-238">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="db49b-239">Modeli oluşturmak için bir yöntem ekleyin</span><span class="sxs-lookup"><span data-stu-id="db49b-239">Add a method to generate the model</span></span>

    <span data-ttu-id="db49b-240">Bu yöntem, öğreticinin kalbidir.</span><span class="sxs-lookup"><span data-stu-id="db49b-240">This method is the heart of the tutorial.</span></span> <span data-ttu-id="db49b-241">Model için bir işlem hattı oluşturur ve ML.NET modelini oluşturmak için işlem hattını trafelar.</span><span class="sxs-lookup"><span data-stu-id="db49b-241">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="db49b-242">Ayrıca, modeli daha önce görülmeyen test verilerine karşı değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="db49b-242">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="db49b-243">Aşağıdaki kodu kullanarak, `InceptionSettings` yapısı ve `DisplayResults()` yönteminden hemen önce olmak üzere `GenerateModel()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="db49b-243">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="db49b-244">Görüntü verilerinden pikselleri yüklemek, yeniden boyutlandırmak ve çıkarmak için tahmini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-244">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    <span data-ttu-id="db49b-245">Görüntü verilerinin, TensorFlow modelinin beklediği biçimde işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db49b-245">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="db49b-246">Bu durumda, görüntüler belleğe yüklenir, tutarlı bir boyuta yeniden boyutlandırılır ve pikseller sayısal bir vektörde ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="db49b-246">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="db49b-247">TensorFlow modelini yüklemek için tahmin Aracı ' ı ekleyin ve puan edin:</span><span class="sxs-lookup"><span data-stu-id="db49b-247">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="db49b-248">İşlem hattındaki bu aşamada, TensorFlow modeli belleğe yüklenir ve ardından, Masorflow model ağı aracılığıyla piksel değerleri vektörü işlenir.</span><span class="sxs-lookup"><span data-stu-id="db49b-248">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="db49b-249">Ayrıntılı bir öğrenme modeline giriş uygulama ve modeli kullanarak bir çıktı oluşturma, **Puanlama**olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="db49b-249">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="db49b-250">Model tamamen kullanılırken, Puanlama bir çıkarım veya tahmin yapar.</span><span class="sxs-lookup"><span data-stu-id="db49b-250">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="db49b-251">Bu durumda, çıkarım yapan katman olan son katman dışındaki tüm TensorFlow modelini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="db49b-251">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="db49b-252">Penultimate katmanının çıkışı `softmax_2_preactivation`etiketlidir.</span><span class="sxs-lookup"><span data-stu-id="db49b-252">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="db49b-253">Bu katmanın çıktısı, orijinal giriş görüntülerini niteleyen özelliklerin bir vektörüdür.</span><span class="sxs-lookup"><span data-stu-id="db49b-253">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="db49b-254">TensorFlow modeli tarafından oluşturulan bu özellik vektörü, bir ML.NET eğitim algoritmasına giriş olarak kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="db49b-254">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="db49b-255">Eğitim verilerinde dize etiketlerini tamsayı anahtar değerleriyle eşlemek için tahmin aracı 'ı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-255">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    <span data-ttu-id="db49b-256">Sonraki eklenen ml.net eğitmen, etiketlerinin rastgele dizeler yerine `key` biçimde olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="db49b-256">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="db49b-257">Anahtar, bir dize değerine bire bir eşleme içeren bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="db49b-257">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="db49b-258">ML.NET eğitim algoritmasını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-258">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. <span data-ttu-id="db49b-259">Tahmin edilen anahtar değerini bir dizeye geri eşlemek için tahmin aracı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-259">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="db49b-260">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="db49b-260">Train the model</span></span>

1. <span data-ttu-id="db49b-261">[Loadfromtextfile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) sarmalayıcısı kullanarak eğitim verilerini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="db49b-261">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="db49b-262">Aşağıdaki kodu `GenerateModel()` yönteminin sonraki satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-262">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="db49b-263">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="db49b-263">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="db49b-264">`IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="db49b-264">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="db49b-265">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) `IDataView` nesnesine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="db49b-265">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="db49b-266">Modeli yukarıda yüklenen verilerle eğitme:</span><span class="sxs-lookup"><span data-stu-id="db49b-266">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    <span data-ttu-id="db49b-267">`Fit()` yöntemi, eğitim veri kümesini işlem hattına uygulayarak modelinizi ister.</span><span class="sxs-lookup"><span data-stu-id="db49b-267">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="db49b-268">Modelin doğruluğunu değerlendirin</span><span class="sxs-lookup"><span data-stu-id="db49b-268">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="db49b-269">Aşağıdaki kodu `GenerateModel` yönteminin bir sonraki satırına ekleyerek test verilerini yükleyin ve dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="db49b-269">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="db49b-270">Modeli değerlendirmek için kullanabileceğiniz birkaç örnek görüntü vardır.</span><span class="sxs-lookup"><span data-stu-id="db49b-270">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="db49b-271">Eğitim verileri gibi, bunların model tarafından dönüştürülebilmeleri için bir `IDataView`yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db49b-271">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="db49b-272">Modeli değerlendirmek için `GenerateModel()` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-272">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    <span data-ttu-id="db49b-273">Tahmin kümesinden sonra, [değerlendir ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi:</span><span class="sxs-lookup"><span data-stu-id="db49b-273">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="db49b-274">Model değerlendirir (tahmin edilen değerleri `labels`test veri kümesiyle karşılaştırır).</span><span class="sxs-lookup"><span data-stu-id="db49b-274">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="db49b-275">Model performans ölçümlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="db49b-275">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="db49b-276">Model doğruluk ölçümlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="db49b-276">Display the model accuracy metrics</span></span>

    <span data-ttu-id="db49b-277">Ölçümleri göstermek, sonuçları paylaşmak ve sonra bunlar üzerinde işlem yapmak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="db49b-277">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    <span data-ttu-id="db49b-278">Aşağıdaki ölçümler görüntü sınıflandırması için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="db49b-278">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="db49b-279">`Log-loss`- [günlük kaybını](../resources/glossary.md#log-loss)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="db49b-279">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="db49b-280">Günlük kaybını mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="db49b-280">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="db49b-281">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="db49b-281">`Per class Log-loss`.</span></span> <span data-ttu-id="db49b-282">Her sınıf günlük kaybını, mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="db49b-282">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="db49b-283">Eğitilen modeli sonraki satır olarak döndürmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-283">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="db49b-284">Uygulamayı çalıştırın!</span><span class="sxs-lookup"><span data-stu-id="db49b-284">Run the application!</span></span>

1. <span data-ttu-id="db49b-285">MLContext sınıfının oluşturulmasından sonra `Main` yönteminde `GenerateModel` çağrısı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-285">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="db49b-286">`ClassifySingleImage()` yöntemine çağrıyı, `Main` yönteminde sonraki kod satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db49b-286">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="db49b-287">Konsol uygulamanızı çalıştırın (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="db49b-287">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="db49b-288">Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db49b-288">Your results should be similar to the following output.</span></span>  <span data-ttu-id="db49b-289">Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="db49b-289">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli.jpg predicted as: food with score: 0.976743
    Image: pizza.jpg predicted as: food with score: 0.9751652
    Image: pizza2.jpg predicted as: food with score: 0.9660203
    Image: teddy2.jpg predicted as: toy with score: 0.9748783
    Image: teddy3.jpg predicted as: toy with score: 0.9829691
    Image: teddy4.jpg predicted as: toy with score: 0.9868168
    Image: toaster.jpg predicted as: appliance with score: 0.9769174
    Image: toaster2.png predicted as: appliance with score: 0.9800823
    =============== Classification metrics ===============
    LogLoss is: 0.0228266745633507
    PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9625379

    C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
    Press any key to close this window . . .
    ```

<span data-ttu-id="db49b-290">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="db49b-290">Congratulations!</span></span> <span data-ttu-id="db49b-291">Artık ML.NET ' deki bir `TensorFlow` modeline aktarım öğrenimi uygulayarak görüntü sınıflandırması için bir makine öğrenimi modeli oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="db49b-291">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="db49b-292">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db49b-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="db49b-293">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="db49b-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="db49b-294">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="db49b-294">Understand the problem</span></span>
> * <span data-ttu-id="db49b-295">Önceden eğitilen TensorFlow modelini ML.NET işlem hattına ekleyin</span><span class="sxs-lookup"><span data-stu-id="db49b-295">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="db49b-296">ML.NET modelini eğitme ve değerlendirme</span><span class="sxs-lookup"><span data-stu-id="db49b-296">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="db49b-297">Test görüntüsünü sınıflandır</span><span class="sxs-lookup"><span data-stu-id="db49b-297">Classify a test image</span></span>

<span data-ttu-id="db49b-298">Genişletilmiş bir görüntü sınıflandırma örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="db49b-298">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="db49b-299">DotNet/machinöğrenim-Samples GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="db49b-299">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
