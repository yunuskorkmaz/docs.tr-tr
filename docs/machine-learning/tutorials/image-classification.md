---
title: 'Öğretici: TensorFlow ML.NET görüntü sınıflandırma modeli'
description: Bilgiyi varolan tensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline nasıl aktartırmayı öğrenin. TensorFlow modeli, görüntüleri bin kategoriye sınıflandırmak için eğitildi. ML.NET modeli, görüntüleri daha az geniş kategoriye sınıflandırmak için aktarım öğrenmeyi kullanır.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: be21a94f571a1676d2a4bce2196dec34bf008121
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607577"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="89271-105">Öğretici: Önceden eğitilmiş tensorFlow modelinden ML.NET görüntü sınıflandırma modeli oluşturun</span><span class="sxs-lookup"><span data-stu-id="89271-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="89271-106">Bilgiyi varolan tensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline nasıl aktartırmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="89271-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="89271-107">TensorFlow modeli, görüntüleri bin kategoriye sınıflandırmak için eğitildi.</span><span class="sxs-lookup"><span data-stu-id="89271-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="89271-108">ML.NET modeli, görüntüleri 3 kategoriye ayırmak için bir model eğitmek için ardışık bölümünde TensorFlow modelinin bir kısmını kullanır.</span><span class="sxs-lookup"><span data-stu-id="89271-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="89271-109">Bir [Görüntü Sınıflandırma](https://en.wikipedia.org/wiki/Outline_of_object_recognition) modelini sıfırdan eğitmek için milyonlarca parametre, bir ton etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) gerekir.</span><span class="sxs-lookup"><span data-stu-id="89271-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="89271-110">Sıfırdan özel bir modeli eğitmek kadar etkili olmasa da, transfer öğrenimi binlerce görüntüyle ve milyonlarca etiketli görüntüyle çalışarak bu süreci kısayolla kesmenize ve oldukça hızlı bir şekilde özelleştirilmiş bir model oluşturmanıza olanak tanır (GPU'suz bir makinede bir saat içinde).</span><span class="sxs-lookup"><span data-stu-id="89271-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="89271-111">Bu öğretici, yalnızca bir düzine eğitim görseli kullanarak daha da aşağı doğru işleyen ölçekler.</span><span class="sxs-lookup"><span data-stu-id="89271-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="89271-112">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="89271-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="89271-113">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="89271-113">Understand the problem</span></span>
> * <span data-ttu-id="89271-114">Önceden eğitilmiş TensorFlow modelini ML.NET boru hattına dahil edin</span><span class="sxs-lookup"><span data-stu-id="89271-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="89271-115">ML.NET modelini eğitin ve değerlendirin</span><span class="sxs-lookup"><span data-stu-id="89271-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="89271-116">Test görüntüsünü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="89271-116">Classify a test image</span></span>

<span data-ttu-id="89271-117">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89271-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="89271-118">Varsayılan olarak, bu öğretici hedefler için .NET proje yapılandırması .NET çekirdek 2.2 unutmayın.</span><span class="sxs-lookup"><span data-stu-id="89271-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="89271-119">Transfer öğrenme nedir?</span><span class="sxs-lookup"><span data-stu-id="89271-119">What is transfer learning?</span></span>

<span data-ttu-id="89271-120">Transfer öğrenme, bir problemi çözerken edinilen bilgiyi kullanarak ve farklı ama ilgili bir soruna uygulama sürecidir.</span><span class="sxs-lookup"><span data-stu-id="89271-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="89271-121">Bu öğretici için, görüntüleri 3 kategoriye ayıran ML.NET bir modelde, görüntüleri bin kategoriye ayırmak üzere eğitilmiş tensorflow modelinin bir bölümünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="89271-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89271-122">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="89271-122">Prerequisites</span></span>

* <span data-ttu-id="89271-123">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonrası veya Visual Studio 2017 sürümü 15.6 veya daha sonra ".NET Core çapraz platform geliştirme" iş yükü yüklü.</span><span class="sxs-lookup"><span data-stu-id="89271-123">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="89271-124">Öğretici varlıklar dizini . ZIP dosyası</span><span class="sxs-lookup"><span data-stu-id="89271-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="89271-125">InceptionV1 makine öğrenme modeli</span><span class="sxs-lookup"><span data-stu-id="89271-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="89271-126">Doğru makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="89271-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="89271-127">Derin öğrenme</span><span class="sxs-lookup"><span data-stu-id="89271-127">Deep learning</span></span>

<span data-ttu-id="89271-128">[Derin öğrenme,](https://en.wikipedia.org/wiki/Deep_learning) Bilgisayarlı Görme ve Konuşma Tanıma gibi alanlarda devrim yapan Makine Öğrenimi'nin bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="89271-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="89271-129">Derin öğrenme modelleri, birden çok öğrenme katmanı içeren büyük [etiketli veri](https://en.wikipedia.org/wiki/Labeled_data) kümeleri ve [sinir ağları](https://en.wikipedia.org/wiki/Artificial_neural_network) kullanılarak eğitilir.</span><span class="sxs-lookup"><span data-stu-id="89271-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="89271-130">Derin öğrenme:</span><span class="sxs-lookup"><span data-stu-id="89271-130">Deep learning:</span></span>

* <span data-ttu-id="89271-131">Computer Vision gibi bazı görevlerde daha iyi performans gösterir.</span><span class="sxs-lookup"><span data-stu-id="89271-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="89271-132">Büyük miktarda eğitim verisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="89271-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="89271-133">Resim Sınıflandırması, görüntüleri otomatik olarak şu kategorilere ayırmamıza olanak tanıyan yaygın bir Makine Öğrenimi görevidir:</span><span class="sxs-lookup"><span data-stu-id="89271-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="89271-134">Görüntüde bir insan yüzünü algılamak ya da algılamamak.</span><span class="sxs-lookup"><span data-stu-id="89271-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="89271-135">Kedileri köpeklere karşı tespit etmek.</span><span class="sxs-lookup"><span data-stu-id="89271-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="89271-136">Veya aşağıdaki resimlerde olduğu gibi, bir görüntünün a(n) gıda, oyuncak veya cihaz olup olmadığını belirlemek:</span><span class="sxs-lookup"><span data-stu-id="89271-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="89271-137">![pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![görüntü oyuncak](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![ayı görüntü tost makinesi görüntü](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="89271-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="89271-138">Önceki görüntüler Wikimedia Commons'a aittir ve aşağıdaki gibi atfedilmiştir:</span><span class="sxs-lookup"><span data-stu-id="89271-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="89271-139">"220px-Pepperoni_pizza.jpg" Kamu https://commons.wikimedia.org/w/index.php?curid=79505Malı,</span><span class="sxs-lookup"><span data-stu-id="89271-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="89271-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) by - Kendini fotoğrafladı, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="89271-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="89271-141">"193px-Broodrooster.jpg" [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) by - Kendi iş, CC BY-SA 3.0,https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="89271-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="89271-142">Görüntüleri `Inception model` bin kategoriye sınıflandırmak üzere eğitildi, ancak bu öğretici için görüntüleri daha küçük bir kategori kümesinde ve yalnızca bu kategorilerde sınıflandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89271-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="89271-143">`transfer` bölümünü `transfer learning`girin.</span><span class="sxs-lookup"><span data-stu-id="89271-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="89271-144">`Inception model`'S yeteneğini tanımak ve özel görüntü sınıflandırıcı yeni sınırlı kategorilere görüntüleri sınıflandırmak aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89271-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="89271-145">Gıda</span><span class="sxs-lookup"><span data-stu-id="89271-145">Food</span></span>
* <span data-ttu-id="89271-146">Oyuncak</span><span class="sxs-lookup"><span data-stu-id="89271-146">Toy</span></span>
* <span data-ttu-id="89271-147">Cihaz</span><span class="sxs-lookup"><span data-stu-id="89271-147">Appliance</span></span>

<span data-ttu-id="89271-148">Bu öğretici tensorFlow [inception modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) derin öğrenme modeli, `ImageNet` veri seti üzerinde eğitilmiş popüler bir görüntü tanıma modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="89271-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="89271-149">TensorFlow modeli tüm görüntüleri "Umbrella", "Jersey" ve "Bulaşık Makinesi" gibi bin sınıfa sınıflar.</span><span class="sxs-lookup"><span data-stu-id="89271-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="89271-150">Zaten `Inception model` farklı görüntüler binlerce önceden eğitilmiş olduğundan, içten görüntü tanımlama için gerekli [görüntü özelliklerini](https://en.wikipedia.org/wiki/Feature_(computer_vision)) içerir.</span><span class="sxs-lookup"><span data-stu-id="89271-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="89271-151">Biz çok daha az sınıfları ile yeni bir model eğitmek için modelde bu iç görüntü özellikleri yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="89271-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="89271-152">Aşağıdaki diyagramda gösterildiği gibi, .NET Core veya .NET Framework uygulamalarınızdaki ML.NET NuGet paketlerine bir başvuru eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="89271-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="89271-153">Kapakların altında, ML.NET, varolan bir eğitilmiş `TensorFlow` `TensorFlow` model dosyasını yükleyen kod yazmanıza olanak tanıyan yerel kitaplığı içerir ve başvurur.</span><span class="sxs-lookup"><span data-stu-id="89271-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![TensorFlow transform ML.NET Arch diyagramı](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="89271-155">Çok sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="89271-155">Multiclass classification</span></span>

<span data-ttu-id="89271-156">Klasik bir makine öğrenme algoritması için girdi olarak uygun özellikleri ayıklamak için TensorFlow başlangıç modelini kullandıktan sonra, ML.NET [çok sınıflı bir sınıflandırıcı](../resources/tasks.md#multiclass-classification)ekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="89271-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="89271-157">Bu durumda kullanılan özel eğitmen [multinomial lojistik regresyon algoritmasıdır.](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)</span><span class="sxs-lookup"><span data-stu-id="89271-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="89271-158">Bu eğitmen tarafından uygulanan algoritma, görüntü verileri üzerinde çalışan derin bir öğrenme modeli için geçerli olan çok sayıda özellik ile ilgili sorunlar üzerinde iyi performans gösterir.</span><span class="sxs-lookup"><span data-stu-id="89271-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="89271-159">Veriler</span><span class="sxs-lookup"><span data-stu-id="89271-159">Data</span></span>

<span data-ttu-id="89271-160">İki veri kaynağı vardır: `.tsv` dosya ve görüntü dosyaları.</span><span class="sxs-lookup"><span data-stu-id="89271-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="89271-161">Dosya `tags.tsv` iki sütun içerir: birincisi olarak `ImagePath` tanımlanır ve ikincisi `Label` görüntüye karşılık gelen.</span><span class="sxs-lookup"><span data-stu-id="89271-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="89271-162">Aşağıdaki örnek dosyanın üstbilgi satırı yoktur ve aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="89271-162">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="89271-163">Eğitim ve test görüntüleri, zip dosyasına indireceğiniz varlık klasörlerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="89271-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="89271-164">Bu görüntüler Wikimedia Commons'a aittir.</span><span class="sxs-lookup"><span data-stu-id="89271-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="89271-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), ücretsiz medya deposu.*</span><span class="sxs-lookup"><span data-stu-id="89271-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="89271-166">Erişim tarihi: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster 10:48 Ekim 17, 2018:https://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="89271-166">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="89271-167">Kurulum</span><span class="sxs-lookup"><span data-stu-id="89271-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="89271-168">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="89271-168">Create a project</span></span>

1. <span data-ttu-id="89271-169">"TransferLearningTF" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89271-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="89271-170">Microsoft.ML **NuGet Paketini**Yükleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="89271-171">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="89271-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="89271-172">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML**arayın.</span><span class="sxs-lookup"><span data-stu-id="89271-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="89271-173">**Sürüm** açılır listesine tıklayın, listedeki **1.4.0** paketini seçin ve **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="89271-173">Click on the **Version** drop-down, select the **1.4.0** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="89271-174">**Değişiklikleri Önizleme** iletişim **kutusundatamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="89271-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="89271-175">Listelenen paketlerin lisans koşullarını kabul **ederseniz, Lisans Kabul** iletişim kutusundaki **I Kabul** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="89271-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="89271-176">**Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** ve **Microsoft.ML.TensorFlow v1.4.0**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="89271-176">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** and **Microsoft.ML.TensorFlow v1.4.0**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="89271-177">Varlıkları indirin</span><span class="sxs-lookup"><span data-stu-id="89271-177">Download assets</span></span>

1. <span data-ttu-id="89271-178">[Proje varlıkları dizin zip dosyasını](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)indirin ve zip'i açın.</span><span class="sxs-lookup"><span data-stu-id="89271-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="89271-179">Dizini `assets` *TransferLearningTF* proje dizininize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="89271-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="89271-180">Bu dizin ve alt dizinleri, bu öğretici için gereken verileri ve destek dosyalarını (bir sonraki adımda indirip ekleyeceğiniz Başlangıç modeli hariç) içerir.</span><span class="sxs-lookup"><span data-stu-id="89271-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="89271-181">[Inception modelini](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)indirin ve zip'i indirin.</span><span class="sxs-lookup"><span data-stu-id="89271-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="89271-182">Dizinin `inception5h` *içeriğini, TransferLearningTF* proje `assets/inception` dizininize yenik çıkarArak kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="89271-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="89271-183">Bu dizin, aşağıdaki resimde gösterildiği gibi, bu öğretici için gerekli modeli ve ek destek dosyalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="89271-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Başlangıç dizini içeriği](./media/image-classification/inception-files.png)

1. <span data-ttu-id="89271-185">Çözüm Gezgini'nde, varlık dizini ve alt dizinindeki dosyaların her birini sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="89271-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="89271-186">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="89271-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="89271-187">Sınıflar oluşturma ve yolları tanımlama</span><span class="sxs-lookup"><span data-stu-id="89271-187">Create classes and define paths</span></span>

1. <span data-ttu-id="89271-188">Aşağıdaki ek `using` deyimleri *Program.cs* dosyasının üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. <span data-ttu-id="89271-189">Varlık yollarını belirtmek için yöntemin `Main` hemen üstündeki satıra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="89271-190">Giriş verileriniz ve öngörüleriniz için sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89271-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    <span data-ttu-id="89271-191">`ImageData`giriş görüntü veri sınıfıdır ve <xref:System.String> aşağıdaki alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="89271-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="89271-192">`ImagePath`resim dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="89271-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="89271-193">`Label`görüntü etiketi için bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="89271-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="89271-194">Projenize yeni bir sınıf `ImagePrediction`ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="89271-195">`ImagePrediction`görüntü tahmin sınıfıdır ve aşağıdaki alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="89271-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="89271-196">`Score`belirli bir görüntü sınıflandırması için güven yüzdesini içerir.</span><span class="sxs-lookup"><span data-stu-id="89271-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="89271-197">`PredictedLabelValue`öngörülen görüntü sınıflandırma etiketi için bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="89271-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="89271-198">`ImagePrediction`model eğitildikten sonra tahmin için kullanılan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="89271-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="89271-199">Görüntü yolu `string` `ImagePath`için bir ( ) vardır.</span><span class="sxs-lookup"><span data-stu-id="89271-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="89271-200">Modelyeniden `Label` kullanmak ve eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89271-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="89271-201">Tahmin `PredictedLabelValue` ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89271-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="89271-202">Değerlendirme için, eğitim verileri, öngörülen değerler ve model ile bir giriş kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89271-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="89271-203">Main'deki değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="89271-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="89271-204">Değişkeni `mlContext` yeni bir örnekle `MLContext`başlatma.</span><span class="sxs-lookup"><span data-stu-id="89271-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="89271-205">`Console.WriteLine("Hello World!")` Satırı yöntemde aşağıdaki kodla `Main` değiştirin:</span><span class="sxs-lookup"><span data-stu-id="89271-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    <span data-ttu-id="89271-206">[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç `mlContext` noktasıdır ve başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89271-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="89271-207">Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.</span><span class="sxs-lookup"><span data-stu-id="89271-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="89271-208">Başlangıç modeli parametreleri için bir yapı oluşturma</span><span class="sxs-lookup"><span data-stu-id="89271-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="89271-209">Inception modeli, geçmeniz gereken birkaç parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="89271-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="89271-210">`Main()` Yöntemden hemen sonra, parametre değerlerini aşağıdaki kodla dost adlarla eşlemek için bir yapı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="89271-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="89271-211">Görüntü yardımcı programı yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="89271-211">Create a display utility method</span></span>

<span data-ttu-id="89271-212">Görüntü verilerini ve ilgili tahminleri birden çok kez görüntüleyeceğiniz için, görüntü ve tahmin sonuçlarını görüntülemek için bir görüntü yardımcı programı yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89271-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="89271-213">Aşağıdaki `DisplayResults()` kodu kullanarak, `InceptionSettings` yapıdan hemen sonra yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="89271-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="89271-214">Yöntemin gövdesini `DisplayResults` doldurun:</span><span class="sxs-lookup"><span data-stu-id="89271-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="89271-215">.tsv dosya yardımcı programı yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="89271-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="89271-216">Yöntemden `ReadFromTsv()` `DisplayResults()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="89271-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="89271-217">Yöntemin gövdesini `ReadFromTsv` doldurun:</span><span class="sxs-lookup"><span data-stu-id="89271-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    <span data-ttu-id="89271-218">`tags.tsv` Kod, `ImagePath` dosya yolunu özelliğin görüntü dosyası adına eklemek ve dosyayı ve `Label` nesneye `ImageData` yüklemek için dosyayı parslar.</span><span class="sxs-lookup"><span data-stu-id="89271-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="89271-219">Tahminde bulunmak için bir yöntem oluşturma</span><span class="sxs-lookup"><span data-stu-id="89271-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="89271-220">Yöntemden `ClassifySingleImage()` hemen önce, `DisplayResults()` aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="89271-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="89271-221">Tek `ImagePath` `ImageData` için tam nitelikli yol ve görüntü dosya adı içeren bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89271-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="89271-222">`ClassifySingleImage()` Yöntemde sonraki satırlar olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. <span data-ttu-id="89271-223">Yöntemde bir sonraki satır olarak aşağıdaki kodu ekleyerek `ClassifySingleImage` tek bir tahminde bulunun:</span><span class="sxs-lookup"><span data-stu-id="89271-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    <span data-ttu-id="89271-224">Tahminalmak için [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="89271-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="89271-225">[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir.</span><span class="sxs-lookup"><span data-stu-id="89271-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="89271-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="89271-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="89271-227">Tek dişli veya prototip ortamlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89271-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="89271-228">Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın.</span><span class="sxs-lookup"><span data-stu-id="89271-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="89271-229">ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="89271-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="89271-230">`PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="89271-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="89271-231">Tahmin sonucunu yöntemde bir sonraki kod `ClassifySingleImage()` satırı olarak görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="89271-232">ML.NET modeli boru hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="89271-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="89271-233">ML.NET model boru hattı tahminciler zinciridir.</span><span class="sxs-lookup"><span data-stu-id="89271-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="89271-234">Boru hattı inşaatı sırasında yürütme yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="89271-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="89271-235">Tahminci nesneleri oluşturulur, ancak yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="89271-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="89271-236">Modeli oluşturmak için bir yöntem ekleme</span><span class="sxs-lookup"><span data-stu-id="89271-236">Add a method to generate the model</span></span>

    <span data-ttu-id="89271-237">Bu yöntem öğretici kalbidir.</span><span class="sxs-lookup"><span data-stu-id="89271-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="89271-238">Bu model için bir boru hattı oluşturur ve ML.NET modeli üretmek için boru hattı trenler.</span><span class="sxs-lookup"><span data-stu-id="89271-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="89271-239">Ayrıca modeli daha önce görülmemiş bazı test verilerine göre de değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="89271-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="89271-240">Aşağıdaki `GenerateModel()` kodu kullanarak, `InceptionSettings` yapıdan hemen sonra `DisplayResults()` ve yöntemden hemen önce yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="89271-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="89271-241">Görüntü verilerinden pikselleri yüklemek, yeniden boyutlandırmak ve ayıklamak için tahmincileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    <span data-ttu-id="89271-242">Görüntü verilerinin TensorFlow modelinin beklediği biçimde işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="89271-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="89271-243">Bu durumda, görüntüler belleğe yüklenir, tutarlı bir boyuta küçültüldü ve pikseller sayısal bir vektöre ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="89271-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="89271-244">TensorFlow modelini yüklemek için tahminciyi ekleyin ve puanlayın:</span><span class="sxs-lookup"><span data-stu-id="89271-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="89271-245">Ardışık işlem de bu aşamada tensorFlow modeli belleğe yükler, sonra TensorFlow model ağı üzerinden piksel değerlerinin vektörü işler.</span><span class="sxs-lookup"><span data-stu-id="89271-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="89271-246">Girişleri derin bir öğrenme modeline uygulamak ve modeli kullanarak çıktı üretmek **Puanlama**olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="89271-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="89271-247">Modeli bütünüyle kullanırken, puanlama bir çıkarım veya tahmin yapar.</span><span class="sxs-lookup"><span data-stu-id="89271-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="89271-248">Bu durumda, çıkarımı oluşturan katman olan son katman dışında TensorFlow modelinin tümlerini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="89271-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="89271-249">Sondan bir önceki katmanın `softmax_2_preactivation`çıktısı etiketlenir.</span><span class="sxs-lookup"><span data-stu-id="89271-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="89271-250">Bu katmanın çıktısı, orijinal giriş görüntülerini karakterize eden bir özellik vektörüdür.</span><span class="sxs-lookup"><span data-stu-id="89271-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="89271-251">TensorFlow modeli tarafından oluşturulan bu özellik vektörü, ML.NET bir eğitim algoritmasına giriş olarak kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="89271-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="89271-252">Eğitim verilerindeki dize etiketlerini eşlemek için tahminciyi, toplam anahtar değerlerine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    <span data-ttu-id="89271-253">Sonraki eklenen ML.NET eğitmen, etiketlerinin rasgele `key` dizeleri yerine biçimde olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="89271-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="89271-254">Anahtar, dize değerine bire bir eşleme olan bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="89271-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="89271-255">ML.NET eğitim algoritmasını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. <span data-ttu-id="89271-256">Tahminciyi, öngörülen anahtar değerini bir dize yle eşlemek için ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="89271-257">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="89271-257">Train the model</span></span>

1. <span data-ttu-id="89271-258">[LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) sarıcıyı kullanarak eğitim verilerini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="89271-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="89271-259">`GenerateModel()` Yöntemde sonraki satır olarak aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="89271-260">ML.NET'daki veriler [IDataView sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="89271-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="89271-261">`IDataView`tabular verileri (sayısal ve metin) tanımlamanın esnek ve etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="89271-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="89271-262">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı `IDataView` veya günlük dosyaları) bir nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="89271-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="89271-263">Yukarıdaki yüklenen verilerle modeli eğitin:</span><span class="sxs-lookup"><span data-stu-id="89271-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    <span data-ttu-id="89271-264">Yöntem, `Fit()` eğitim veri kümesini boru hattına uygulayarak modelinizi eğitiyor.</span><span class="sxs-lookup"><span data-stu-id="89271-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="89271-265">Modelin doğruluğunu değerlendirme</span><span class="sxs-lookup"><span data-stu-id="89271-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="89271-266">Yöntemin bir sonraki satırına aşağıdaki kodu ekleyerek test `GenerateModel` verilerini yükleyin ve dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="89271-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="89271-267">Modeli değerlendirmek için kullanabileceğiniz birkaç örnek resim vardır.</span><span class="sxs-lookup"><span data-stu-id="89271-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="89271-268">Eğitim verileri gibi, bunların da model `IDataView`tarafından dönüştürülebilmeleri için bir , içine yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="89271-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="89271-269">Modeli değerlendirmek için `GenerateModel()` yönteme aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    <span data-ttu-id="89271-270">Tahmin kümesini aldıktan sonra, [Değerlendir()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi:</span><span class="sxs-lookup"><span data-stu-id="89271-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="89271-271">Modeli değerlendirir (öngörülen değerleri test veri kümesiyle `labels`karşılaştırır).</span><span class="sxs-lookup"><span data-stu-id="89271-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="89271-272">Model performans ölçümlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="89271-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="89271-273">Model doğruluk ölçümlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="89271-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="89271-274">Ölçümleri görüntülemek, sonuçları paylaşmak ve sonra bunlara göre hareket etmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="89271-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    <span data-ttu-id="89271-275">Aşağıdaki ölçümler görüntü sınıflandırması için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="89271-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="89271-276">`Log-loss`- [bkz.](../resources/glossary.md#log-loss)</span><span class="sxs-lookup"><span data-stu-id="89271-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="89271-277">Log-loss'un mümkün olduğunca sıfıra yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="89271-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="89271-278">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="89271-278">`Per class Log-loss`.</span></span> <span data-ttu-id="89271-279">Sınıf başına Günlük kaybının mümkün olduğunca sıfıra yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="89271-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="89271-280">Eğitilen modeli sonraki satır olarak döndürmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="89271-281">Uygulamayı çalıştırın!</span><span class="sxs-lookup"><span data-stu-id="89271-281">Run the application!</span></span>

1. <span data-ttu-id="89271-282">MLContext sınıfının `GenerateModel` `Main` oluşturulmasından sonra yönteme çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="89271-283">Yöntemde `ClassifySingleImage()` bir sonraki kod satırı olarak yönteme çağrıyı `Main` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89271-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="89271-284">Konsol uygulamanızı çalıştırın (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="89271-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="89271-285">Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89271-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="89271-286">Uyarılar veya iletileri işleme görebilirsiniz, ancak bu iletiler netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="89271-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

<span data-ttu-id="89271-287">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="89271-287">Congratulations!</span></span> <span data-ttu-id="89271-288">Şimdi başarılı bir şekilde ML.NET bir modele transfer öğrenme uygulayarak `TensorFlow` görüntü sınıflandırma için bir makine öğrenme modeli inşa ettik.</span><span class="sxs-lookup"><span data-stu-id="89271-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="89271-289">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89271-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="89271-290">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="89271-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="89271-291">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="89271-291">Understand the problem</span></span>
> * <span data-ttu-id="89271-292">Önceden eğitilmiş TensorFlow modelini ML.NET boru hattına dahil edin</span><span class="sxs-lookup"><span data-stu-id="89271-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="89271-293">ML.NET modelini eğitin ve değerlendirin</span><span class="sxs-lookup"><span data-stu-id="89271-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="89271-294">Test görüntüsünü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="89271-294">Classify a test image</span></span>

<span data-ttu-id="89271-295">Genişletilmiş bir görüntü sınıflandırma örneğini keşfetmek için GitHub deposundaki Machine Learning örneklerine göz atın.</span><span class="sxs-lookup"><span data-stu-id="89271-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="89271-296">dotnet/machinelearning-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="89271-296">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
