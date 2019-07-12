---
title: 'Öğretici: Retrain TensorFlow görüntü sınıflandırıcı - aktarımlı öğrenme'
description: Aktarımlı öğrenme ve ML.NET ile bir görüntü sınıflandırma TensorFlow modeli yeniden eğitme hakkında bilgi edinin. Özgün modeli ayrı görüntüleri sınıflandırmak için eğitim. Yeni modeli yeniden eğitme sonra görüntüleri kategoriden düzenler.
ms.date: 07/09/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 65f94fa5e725703d79d0dddae761cbfbc3f89e0e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804753"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a><span data-ttu-id="cc303-105">Öğretici: TensorFlow görüntü sınıflandırıcı ML.NET aktarımlı öğrenme ile yeniden eğitme</span><span class="sxs-lookup"><span data-stu-id="cc303-105">Tutorial: Retrain a TensorFlow image classifier with transfer learning and ML.NET</span></span>

<span data-ttu-id="cc303-106">Aktarımlı öğrenme ve ML.NET ile bir görüntü sınıflandırma TensorFlow modeli yeniden eğitme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="cc303-106">Learn how to retrain an image classification TensorFlow model with transfer learning and ML.NET.</span></span> <span data-ttu-id="cc303-107">Özgün modeli ayrı görüntüleri sınıflandırmak için eğitim.</span><span class="sxs-lookup"><span data-stu-id="cc303-107">The original model was trained to classify individual images.</span></span> <span data-ttu-id="cc303-108">Yeni modeli yeniden eğitme sonra görüntüleri kategoriden düzenler.</span><span class="sxs-lookup"><span data-stu-id="cc303-108">After retraining, the new model organizes the images into broad categories.</span></span> 

<span data-ttu-id="cc303-109">Eğitim bir [görüntü sınıflandırması](https://en.wikipedia.org/wiki/Outline_of_object_recognition) sıfırdan modeli, Parametreler, bir sürü etiketli eğitim verilerini ve işlem kaynakları (GPU saat yüzlerce) çok büyük miktarda milyonlarca ayarlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cc303-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="cc303-110">Aktarımlı öğrenme kadar etkili olarak sıfırdan özel bir model eğitim olsa da görüntüleri etiketlenmiş resimlerinizi milyonlarca karşılaştırması binlerce birlikte çalışarak bu işlem için kısayol sağlar ve oldukça hızlı bir şekilde özelleştirilmiş model derleme (bir makinede bir saat içinde bir GPU).</span><span class="sxs-lookup"><span data-stu-id="cc303-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="cc303-111">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="cc303-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="cc303-112">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="cc303-112">Understand the problem</span></span>
> * <span data-ttu-id="cc303-113">Yeniden kullanmak ve önceden eğitilmiş bir modeli ayarlama</span><span class="sxs-lookup"><span data-stu-id="cc303-113">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="cc303-114">Resimleri sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="cc303-114">Classify Images</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="cc303-115">Hangi aktarım öğrenmeye devam ettiği?</span><span class="sxs-lookup"><span data-stu-id="cc303-115">What is transfer learning?</span></span>

<span data-ttu-id="cc303-116">Ne öncesi zaten bir model kullanabilirsiniz ya da tümünün veya bazılarının, sorununuzu çözmenize yardımcı olmak için bu modelinin katmanlarını yeniden eğitme ve benzer bir sorunu çözmek eğitilen?</span><span class="sxs-lookup"><span data-stu-id="cc303-116">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="cc303-117">Bu teknik yeniden yeni bir model oluşturmak üzere önceden eğitilen bir modelin parçası olarak da bilinen [aktarım öğrenme](https://en.wikipedia.org/wiki/Transfer_learning).</span><span class="sxs-lookup"><span data-stu-id="cc303-117">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="cc303-118">Görüntü sınıflandırma örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="cc303-118">Image classification sample overview</span></span>

<span data-ttu-id="cc303-119">Örnek görüntüleri küçük bir eğitim veri miktarı ile sınıflandırmak için önceden eğitilmiş bir modeli yeniden kullanarak bir görüntü sınıflandırıcı oluşturma için ML.NET kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="cc303-119">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="cc303-120">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) depo.</span><span class="sxs-lookup"><span data-stu-id="cc303-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="cc303-121">Varsayılan olarak, .NET proje yapılandırması Bu öğretici için .NET core 2.2 hedefleyen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cc303-121">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc303-122">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="cc303-122">Prerequisites</span></span>

* <span data-ttu-id="cc303-123">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="cc303-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span> 

* <span data-ttu-id="cc303-124">Microsoft.ML 1.0.0 Nuget paketi</span><span class="sxs-lookup"><span data-stu-id="cc303-124">Microsoft.ML 1.0.0 Nuget package</span></span>
* <span data-ttu-id="cc303-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget paketi</span><span class="sxs-lookup"><span data-stu-id="cc303-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget package</span></span>
* <span data-ttu-id="cc303-126">Microsoft.ML.TensorFlow 0.12.0 Nuget paketi</span><span class="sxs-lookup"><span data-stu-id="cc303-126">Microsoft.ML.TensorFlow 0.12.0 Nuget package</span></span>

* [<span data-ttu-id="cc303-127">Öğretici varlıklar dizin. ZIP dosyası</span><span class="sxs-lookup"><span data-stu-id="cc303-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="cc303-128">InceptionV1 machine learning modeli</span><span class="sxs-lookup"><span data-stu-id="cc303-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="cc303-129">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="cc303-129">Select the appropriate machine learning task</span></span>

<span data-ttu-id="cc303-130">[Derin öğrenme](https://en.wikipedia.org/wiki/Deep_learning) , görüntü işleme ve konuşma tanıma gibi alanları revolutionizing Machine Learning, bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="cc303-130">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="cc303-131">Modelleri, büyük kümelerini kullanarak eğitilir derin öğrenme [veri etiketli](https://en.wikipedia.org/wiki/Labeled_data) ve [sinir ağları](https://en.wikipedia.org/wiki/Artificial_neural_network) birden çok öğrenim katmanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cc303-131">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="cc303-132">Derin öğrenme:</span><span class="sxs-lookup"><span data-stu-id="cc303-132">Deep learning:</span></span>

* <span data-ttu-id="cc303-133">Görüntü işleme gibi bazı görevler üzerinde daha iyi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="cc303-133">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="cc303-134">İyi büyük verileri tutarlarını gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="cc303-134">Performs well on huge data amounts.</span></span>

<span data-ttu-id="cc303-135">Görüntü sınıflandırması otomatik olarak gibi birden fazla kategoriye görüntüleri sınıflandırmak olanak sağlayan ortak bir Machine Learning görevidir:</span><span class="sxs-lookup"><span data-stu-id="cc303-135">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="cc303-136">İnsan yüz veya bir görüntüde algılanıyor.</span><span class="sxs-lookup"><span data-stu-id="cc303-136">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="cc303-137">Köpek Kedilere algılanıyor.</span><span class="sxs-lookup"><span data-stu-id="cc303-137">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="cc303-138">Veya belirlenmesinde aşağıdaki resimlerde gösterildiği gibi bir görüntü bir yiyecek, çocuğunun veya Gereci:</span><span class="sxs-lookup"><span data-stu-id="cc303-138">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="cc303-139">![pizza görüntü](./media/image-classification/220px-Pepperoni_pizza.jpg)
![Oyuncak Ayı ayı görüntü](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster görüntüsü](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc303-139">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="cc303-140">Önceki görüntüler için Wikimedia Commons ait ve şu şekilde atanmıştır:</span><span class="sxs-lookup"><span data-stu-id="cc303-140">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="cc303-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span><span class="sxs-lookup"><span data-stu-id="cc303-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="cc303-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" tarafından [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) -, CC BY-SA 2.0, kendi kendine fotoğrafı https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="cc303-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="cc303-143">"193px-Broodrooster.jpg" tarafından [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) -kendi iş, CC BY SA 3.0 https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="cc303-143">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="cc303-144">Aktarımlı öğrenme içeren birkaç stratejileri gibi *tüm katmanlar yeniden eğitme* ve *sondan katman*.</span><span class="sxs-lookup"><span data-stu-id="cc303-144">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="cc303-145">Bu öğreticide açıklamak ve nasıl kullanabileceğinizi gösteren *sondan katman stratejisi*.</span><span class="sxs-lookup"><span data-stu-id="cc303-145">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="cc303-146">*Sondan katman stratejisi* zaten belirli bir sorunu çözmek için önceden eğitildi bir model kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc303-146">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="cc303-147">Strateji, ardından yeni bir sorunu çözmeye sağlamak için bu modelin son katmanı retrains.</span><span class="sxs-lookup"><span data-stu-id="cc303-147">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="cc303-148">Önceden eğitilmiş modelin yeni modelinizin bir parçası olarak yeniden önemli zamandan ve kaynaklardan tasarruf.</span><span class="sxs-lookup"><span data-stu-id="cc303-148">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="cc303-149">Görüntü sınıflandırma modelinizi yeniden [başlangıcı modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), üzerinde bir popüler görüntü tanıma modeli eğitilir `ImageNet` TensorFlow modeli nerede çalışırsa tüm sınıflandırmak için veri kümesi, binlerce sınıflara gibi görüntüleri " Genel","Jersey"ve"Dishwasher".</span><span class="sxs-lookup"><span data-stu-id="cc303-149">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="cc303-150">`Inception v1 model` Olarak sınıflandırılan bir [derin konvolüsyonel sinir ağını](https://en.wikipedia.org/wiki/Convolutional_neural_network) ve eşleşen veya bazı etki alanlarına İnsan performansa aşan sabit visual tanıma görevleri, makul performans elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc303-150">The `Inception v1 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="cc303-151">Model/algoritması birden çok Araştırmacıları tarafından geliştirilmiş ve özgün kağıda tabanlı: ["Yeni mimarisi için görüntü işleme tarafından Szegedy yeniden değerlendirme", et. Al.](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="cc303-151">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="cc303-152">Çünkü `Inception model` öncesi zaten içerdiği farklı görüntüleri binlerce üzerinde geliştirilen, [görüntü özellikleri](https://en.wikipedia.org/wiki/Feature_(computer_vision)) resim tanımlama için gerekli.</span><span class="sxs-lookup"><span data-stu-id="cc303-152">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="cc303-153">Basit özellikleri (örneğin, kenarlar) alt görüntü özelliği katmanlarının tanır ve daha yüksek katmanları (şekiller gibi) daha karmaşık özelliklerden tanı.</span><span class="sxs-lookup"><span data-stu-id="cc303-153">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="cc303-154">Son katmanı, zaten nasıl sınıflandırılacağıyla görüntüleri anlayan önceden eğitilen bir modelin ile başlatıyorsanız çünkü çok daha küçük veri kümesi karşı çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="cc303-154">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="cc303-155">Modelinizi ikiden fazla kategorileri sınıflandırmak verdiğinden, bu örneği yer almaktadır. bir [çok sınıflı sınıflandırıcı](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="cc303-155">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="cc303-156">`TensorFlow` popüler derin öğrenme ve eğitim derin sinir ağı (ve genel sayısal hesaplamalar) etkinleştirir ve halinde uygulanır makine öğrenimi araç seti bir `transformer` ML.NET içinde.</span><span class="sxs-lookup"><span data-stu-id="cc303-156">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="cc303-157">Bu öğretici için yeniden kullanıldığı `Inception model`.</span><span class="sxs-lookup"><span data-stu-id="cc303-157">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="cc303-158">Aşağıdaki diyagramda gösterildiği gibi .NET Core veya .NET Framework uygulamalarınızı ML.NET NuGet paketlerini bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc303-158">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="cc303-159">ML.NET kapsar altında içerir ve yerel başvuruyor `TensorFlow` yükler mevcut bir kod yazmanızı sağlayan kitaplığı eğitilmiş `TensorFlow` Puanlama için model dosyası.</span><span class="sxs-lookup"><span data-stu-id="cc303-159">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![TensorFlow dönüştürme ML.NET mimarisi diyagramı](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="cc303-161">`Inception model` Binlerce kategoriler halinde görüntüleri sınıflandırmak için eğitilen ancak daha küçük bir kategori kümesini ve bu kategorilerin görüntülerde sınıflandırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc303-161">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="cc303-162">Girin `transfer` parçası `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="cc303-162">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="cc303-163">Aktarabilirsiniz `Inception model`'s tanıması ve özel görüntü sınıflandırıcınızı yeni sınırlı kategorilerini görüntülere sınıflandırma özelliği.</span><span class="sxs-lookup"><span data-stu-id="cc303-163">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="cc303-164">Son üç kategorileri kümesi kullanarak bu modeli katmanı yeniden eğitme oluşturacağız:</span><span class="sxs-lookup"><span data-stu-id="cc303-164">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="cc303-165">Yiyecek</span><span class="sxs-lookup"><span data-stu-id="cc303-165">Food</span></span>
* <span data-ttu-id="cc303-166">Çocuğunun</span><span class="sxs-lookup"><span data-stu-id="cc303-166">Toy</span></span>
* <span data-ttu-id="cc303-167">Gereç</span><span class="sxs-lookup"><span data-stu-id="cc303-167">Appliance</span></span>

<span data-ttu-id="cc303-168">Katman kullanan bir [ÇOKTERİMLİ Lojistik regresyon algoritması](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) kategoriyi mümkün olan en kısa sürede bulunacak.</span><span class="sxs-lookup"><span data-stu-id="cc303-168">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="cc303-169">Bu algoritma, yanıt bir değer ölçeklendirerek kategoriyi ve diğerleri için sıfır değeri belirlemek için olasılıkları kullanma sınıflandırır.</span><span class="sxs-lookup"><span data-stu-id="cc303-169">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="cc303-170">DataSet</span><span class="sxs-lookup"><span data-stu-id="cc303-170">DataSet</span></span>

<span data-ttu-id="cc303-171">İki veri kaynağı vardır: `.tsv` dosyası ve görüntü dosyaları.</span><span class="sxs-lookup"><span data-stu-id="cc303-171">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="cc303-172">`tags.tsv` Dosyada iki sütun: ilk olarak tanımlanan `ImagePath` ve ikincisi `Label` görüntüsüne karşılık gelen.</span><span class="sxs-lookup"><span data-stu-id="cc303-172">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="cc303-173">Aşağıdaki örnek dosyası, bir başlık satırı yok ve şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="cc303-173">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="cc303-174">Eğitim ve test görüntüleri bir ZIP dosyası indireceksiniz varlıklar klasörlerinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="cc303-174">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="cc303-175">Bu görüntüler için Wikimedia Commons ait.</span><span class="sxs-lookup"><span data-stu-id="cc303-175">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="cc303-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), serbest medya depo.*</span><span class="sxs-lookup"><span data-stu-id="cc303-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="cc303-177">Alınan 10:48, 17 Ekim 2018 tarihinden sonra:</span><span class="sxs-lookup"><span data-stu-id="cc303-177">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="cc303-178">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc303-178">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="cc303-179">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc303-179">Create a project</span></span>

1. <span data-ttu-id="cc303-180">Oluşturma bir **.NET Core konsol uygulaması** "TransferLearningTF" denir.</span><span class="sxs-lookup"><span data-stu-id="cc303-180">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

2. <span data-ttu-id="cc303-181">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="cc303-181">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="cc303-182">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="cc303-182">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="cc303-183">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="cc303-183">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="cc303-184">Tıklayarak **sürüm** açılan listesinde, select **1.0.0** paketini listede bulun ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="cc303-184">Click on the **Version** drop-down, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="cc303-185">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="cc303-185">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="cc303-186">Bu adımı yineleyin **Microsoft.ML.ImageAnalytics v1.0.0** ve **Microsoft.ML.TensorFlow v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="cc303-186">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.0.0** and **Microsoft.ML.TensorFlow v0.12.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="cc303-187">Verilerinizi hazırlama</span><span class="sxs-lookup"><span data-stu-id="cc303-187">Prepare your data</span></span>

1. <span data-ttu-id="cc303-188">İndirme [proje varlıklar dizin zip dosyasını](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)ve sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="cc303-188">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="cc303-189">Kopyalama `assets` içine dizin, *TransferLearningTF* proje dizini.</span><span class="sxs-lookup"><span data-stu-id="cc303-189">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="cc303-190">Bu dizin ve alt dizinlerinde (dışında indirme ve bir sonraki adımda ekleme yeni model) verileri ve destek dosyaları içeren Bu öğretici için gerekli.</span><span class="sxs-lookup"><span data-stu-id="cc303-190">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="cc303-191">İndirme [başlangıcı modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)ve sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="cc303-191">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="cc303-192">İçeriğini kopyalayın `inception5h` dizin yalnızca sıkıştırması açılan içine, *TransferLearningTF* proje `assets\inputs-train\inception` dizin.</span><span class="sxs-lookup"><span data-stu-id="cc303-192">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="cc303-193">Bu dizin, aşağıdaki görüntüde gösterildiği gibi model ve Bu öğretici için gerekli ek destek dosyalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="cc303-193">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Yeni dizin içeriği](./media/image-classification/inception-files.png)

5. <span data-ttu-id="cc303-195">Her varlık dizin ve alt dizinleri seçip dosya Çözüm Gezgini'nde sağ **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="cc303-195">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="cc303-196">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="cc303-196">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="cc303-197">Yollarını tanımlamak ve sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc303-197">Create classes and define paths</span></span>

<span data-ttu-id="cc303-198">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="cc303-198">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="cc303-199">Yolları çeşitli varlıklar ve genel değişkenleri tutmak için genel alanlar oluşturmak `LabelTokey`,`ImageReal`, ve `PredictedLabelValue`:</span><span class="sxs-lookup"><span data-stu-id="cc303-199">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="cc303-200">`_assetsPath` varlıkları yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="cc303-200">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="cc303-201">`_trainTagsTsv` yolu için eğitim görüntü veri etiketleri tsv dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="cc303-201">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="cc303-202">`_predictTagsTsv` yolu için tahmin görüntü veri etiketleri tsv dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="cc303-202">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="cc303-203">`_trainImagesFolder` modeli eğitmek için kullanılan görüntülerin yolunu sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cc303-203">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="cc303-204">`_predictImagesFolder` eğitilen modelin sınıflandırılmaya görüntü sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cc303-204">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="cc303-205">`_inceptionPb` Yolun modelinizi yeniden kullanılabilmeleri için önceden eğitilmiş başlangıcı modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cc303-205">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="cc303-206">`_inputImageClassifierZip` eğitilen model öğesinden yüklendiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="cc303-206">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="cc303-207">`_outputImageClassifierZip` eğitilen modelin kaydedildiği yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="cc303-207">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="cc303-208">`LabelTokey` olan `Label` bir anahtar ile eşlenen değeri.</span><span class="sxs-lookup"><span data-stu-id="cc303-208">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="cc303-209">`ImageReal`  Tahmin edilen görüntü değeri içeren sütun.</span><span class="sxs-lookup"><span data-stu-id="cc303-209">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="cc303-210">`PredictedLabelValue` Tahmin edilen etiket değeri içeren sütun.</span><span class="sxs-lookup"><span data-stu-id="cc303-210">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="cc303-211">Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollar ve diğer değişkenlerini belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="cc303-211">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="cc303-212">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cc303-212">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="cc303-213">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cc303-213">Add a new class to your project:</span></span>

1. <span data-ttu-id="cc303-214">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="cc303-214">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="cc303-215">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *ImageData.cs*.</span><span class="sxs-lookup"><span data-stu-id="cc303-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="cc303-216">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="cc303-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="cc303-217">*ImageData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="cc303-217">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="cc303-218">Aşağıdaki `using` üstüne deyimi *ImageData.cs*:</span><span class="sxs-lookup"><span data-stu-id="cc303-218">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="cc303-219">Varolan sınıf tanımına kaldırın ve aşağıdaki kodu ekleyin `ImageData` sınıfının *ImageData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="cc303-219">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="cc303-220">`ImageData` girdi görüntüsünün veri sınıfı ve aşağıdaki <xref:System.String> alanlar:</span><span class="sxs-lookup"><span data-stu-id="cc303-220">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="cc303-221">`ImagePath` görüntü dosya adı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cc303-221">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="cc303-222">`Label` görüntü etiketi için bir değer içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cc303-222">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="cc303-223">Projeniz için yeni bir sınıf eklemek `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="cc303-223">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="cc303-224">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="cc303-224">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="cc303-225">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *ImagePrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="cc303-225">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="cc303-226">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="cc303-226">Then, select the **Add** button.</span></span>

    <span data-ttu-id="cc303-227">*ImagePrediction.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="cc303-227">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="cc303-228">Hem de kaldırma `System.Collections.Generic` ve `System.Text` `using` deyimleri en üstündeki *ImagePrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="cc303-228">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="cc303-229">Varolan sınıf tanımına kaldırın ve olan aşağıdaki kodu ekleyin `ImagePrediction` çok sınıf *ImagePrediction.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="cc303-229">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="cc303-230">`ImagePrediction` Görüntü tahmin sınıftır ve aşağıdaki alanlar vardır:</span><span class="sxs-lookup"><span data-stu-id="cc303-230">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="cc303-231">`Score` güvenle yüzdesi verilen görüntü sınıflandırması içerir.</span><span class="sxs-lookup"><span data-stu-id="cc303-231">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="cc303-232">`PredictedLabelValue` Tahmin edilen görüntü sınıflandırma etiketi için bir değer içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cc303-232">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="cc303-233">`ImagePrediction` eğitilen modelin sonra sınıf tahmin için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc303-233">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="cc303-234">Bunun bir `string` (`ImagePath`) görüntü yolu için.</span><span class="sxs-lookup"><span data-stu-id="cc303-234">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="cc303-235">`Label` Modeli yeniden eğitme ve yeniden kullanmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc303-235">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="cc303-236">`PredictedLabelValue` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc303-236">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="cc303-237">Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc303-237">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="cc303-238">[MLContext sınıfı](xref:Microsoft.ML.MLContext) bir tüm ML.NET işlemleri için başlangıç noktası ve başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc303-238">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="cc303-239">Bu, kavramsal olarak, benzer `DBContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="cc303-239">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="cc303-240">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="cc303-240">Initialize variables in Main</span></span>

<span data-ttu-id="cc303-241">Başlatma `mlContext` değişken ile yeni bir örneğini `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="cc303-241">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="cc303-242">Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-242">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="cc303-243">Varsayılan parametreleri için bir yapı oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc303-243">Create a struct for default parameters</span></span>

<span data-ttu-id="cc303-244">Yeni modelde birkaç varsayılan parametre olarak geçirmenize gerek yok.</span><span class="sxs-lookup"><span data-stu-id="cc303-244">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="cc303-245">Aşağıdaki kod ile kolay adlar için varsayılan parametre değerlerini hemen sonra eşlemek için bir yapı oluşturmak `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-245">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="cc303-246">Görüntü yardımcı programı yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc303-246">Create a display utility method</span></span>

<span data-ttu-id="cc303-247">Görüntü verilerini ve ilgili Öngörüler birden çok kez görüntüleyeceksiniz olduğundan, görüntü ve tahmin sonuçlarını görüntüleyen işlemek için bir görüntü yardımcı programı yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cc303-247">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

<span data-ttu-id="cc303-248">`DisplayResults()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="cc303-248">The `DisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="cc303-249">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cc303-249">Displays the predicted results.</span></span>

<span data-ttu-id="cc303-250">Oluşturma `DisplayResults()` yöntemi hemen sonrasına `InceptionSettings` yapısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="cc303-250">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

<span data-ttu-id="cc303-251">`Transform()` Doldurulmuş yöntemi `ImagePath` içinde `ImagePrediction` tahmin edilen alanların yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="cc303-251">The `Transform()` method populated `ImagePath` in `ImagePrediction` along with the predicted fields.</span></span> <span data-ttu-id="cc303-252">ML.NET işlem ilerledikçe, her bileşen sütunları ekler ve bu sonuçları görüntülemek üzere kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="cc303-252">As the ML.NET process progresses, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="cc303-253">Sizi ararız `DisplayResults()` iki görüntü sınıflandırma yöntemleri yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc303-253">You'll call the `DisplayResults()` method in the two image classification methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="cc303-254">.Tsv dosya yardımcı program metodu oluştur</span><span class="sxs-lookup"><span data-stu-id="cc303-254">Create a .tsv file utility method</span></span>

<span data-ttu-id="cc303-255">`ReadFromTsv()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="cc303-255">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="cc303-256">Görüntü verisini okur `tags.tsv` dosya.</span><span class="sxs-lookup"><span data-stu-id="cc303-256">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="cc303-257">Dosya yolu görüntü dosya adına ekler.</span><span class="sxs-lookup"><span data-stu-id="cc303-257">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="cc303-258">Dosya verilerini bir IEnumerable yükler`ImageData` nesne.</span><span class="sxs-lookup"><span data-stu-id="cc303-258">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="cc303-259">Oluşturma `ReadFromTsv()` yöntemi hemen sonrasına `PairAndDisplayResults()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="cc303-259">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="cc303-260">Aşağıdaki kod aracılığıyla ayrıştırır `tags.tsv` dosya yolu için resim dosya adı eklemek için dosya `ImagePath` özelliği ve yükler ve `Label` içine bir `ImageData` nesne.</span><span class="sxs-lookup"><span data-stu-id="cc303-260">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="cc303-261">İlk satırı olarak ekleyin `ReadFromTsv()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc303-261">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="cc303-262">Tahmin sonuçlarını görüntülemek için tam dosya yolunu ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="cc303-262">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="cc303-263">ML.NET içinde üç ana kavramı vardır: [Veri](../resources/glossary.md#data), [dönüştürücüler](../resources/glossary.md#transformer), ve [Estimators](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="cc303-263">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="cc303-264">Yeniden kullanmak ve önceden eğitilmiş bir modeli ayarlama</span><span class="sxs-lookup"><span data-stu-id="cc303-264">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="cc303-265">Aşağıdaki çağrısı ekleyin `ReuseAndTuneInceptionModel()`yöntemi sonraki kod satırı olarak `Main()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-265">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="cc303-266">`ReuseAndTuneInceptionModel()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="cc303-266">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="cc303-267">Verileri yükler</span><span class="sxs-lookup"><span data-stu-id="cc303-267">Loads the data</span></span>
* <span data-ttu-id="cc303-268">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="cc303-268">Extracts and transforms the data.</span></span>
* <span data-ttu-id="cc303-269">TensorFlow modelini puanlar.</span><span class="sxs-lookup"><span data-stu-id="cc303-269">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="cc303-270">(Çağırma sayısı) tabanlarını modeli.</span><span class="sxs-lookup"><span data-stu-id="cc303-270">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="cc303-271">Model sonuçlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cc303-271">Displays model results.</span></span>
* <span data-ttu-id="cc303-272">Model değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="cc303-272">Evaluates the model.</span></span>
* <span data-ttu-id="cc303-273">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc303-273">Returns the model.</span></span>

<span data-ttu-id="cc303-274">Oluşturma `ReuseAndTuneInceptionModel()` yöntemi hemen sonrasına `InceptionSettings` yapısı ve hemen önce `DisplayResults()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="cc303-274">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="cc303-275">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="cc303-275">Load the data</span></span>

<span data-ttu-id="cc303-276">ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="cc303-276">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="cc303-277">`IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur.</span><span class="sxs-lookup"><span data-stu-id="cc303-277">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="cc303-278">Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne.</span><span class="sxs-lookup"><span data-stu-id="cc303-278">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="cc303-279">Kullanarak verileri yüklemek `MLContext.Data.LoadFromTextFile` sarmalayıcı.</span><span class="sxs-lookup"><span data-stu-id="cc303-279">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="cc303-280">Sonraki satırda olarak aşağıdaki kodu ekleyin `ReuseAndTuneInceptionModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-280">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="cc303-281">Özellikleri ayıklayın ve verileri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cc303-281">Extract Features and transform the data</span></span>

<span data-ttu-id="cc303-282">Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="cc303-282">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="cc303-283">Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc303-283">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="cc303-284">Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) verileri ve ne zaman, derin sinir ağları ile ilgilenen gerekir uyarlayabilirsiniz ağ tarafından beklenen biçimde görüntüleri.</span><span class="sxs-lookup"><span data-stu-id="cc303-284">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="cc303-285">Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="cc303-285">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="cc303-286">Eğitim ve değerlendirme sonra ile tahmin **etiket** sütun değerleri.</span><span class="sxs-lookup"><span data-stu-id="cc303-286">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="cc303-287">Önceden eğitilmiş bir modeli kullandığınız gibi alanları yeni modeliyle eşlemek [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc303-287">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="cc303-288">Bu yöntem dönüştüren `Label` sayısal bir anahtar türü (`LabelTokey`) sütunu ve yeni veri kümesi sütun olarak ekleyin:  Bu ad `estimator` gibi de Eğitmeni kendisine eklemeniz.</span><span class="sxs-lookup"><span data-stu-id="cc303-288">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="cc303-289">Sonraki kod satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cc303-289">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="cc303-290">Resim estimator kullanan önceden eğitilmiş işleme [derin sinir Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers özelliği ayıklama için.</span><span class="sxs-lookup"><span data-stu-id="cc303-290">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="cc303-291">Derin sinir ağları ile ilgilenirken, beklenen ağ biçimi görüntülerin uyarlayın.</span><span class="sxs-lookup"><span data-stu-id="cc303-291">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="cc303-292">Modelin beklenen biçime görüntü verilerini almak için kullandığınız görüntü dönüşümlerden nedeni budur:</span><span class="sxs-lookup"><span data-stu-id="cc303-292">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="cc303-293">`LoadImages`Dönüştürme görüntü bit eşlem türü olarak belleğe yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cc303-293">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="cc303-294">`ResizeImages` Dönüştürme olarak önceden eğitilmiş model tanımlı girdi görüntüsü genişliği ve yüksekliği görüntüleri yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="cc303-294">The `ResizeImages` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="cc303-295">`ExtractPixels` Dönüştürme giriş görüntülerden piksel ayıklar ve bunları sayısal vektörü dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="cc303-295">The `ExtractPixels` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="cc303-296">Bu görüntü dönüşümler sonraki kod satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cc303-296">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="cc303-297">`LoadTensorFlowModel` İzin veren bir kolaylık yöntemi `TensorFlow` kez yüklenmesi için model ve ardından oluşturan `TensorFlowEstimator` kullanarak `ScoreTensorFlowModel`.</span><span class="sxs-lookup"><span data-stu-id="cc303-297">The `LoadTensorFlowModel` is a convenience method that allows the `TensorFlow` model to be loaded once and then creates the `TensorFlowEstimator` using `ScoreTensorFlowModel`.</span></span> <span data-ttu-id="cc303-298">`ScoreTensorFlowModel` Ayıklar belirtilen çıkış ( `Inception model`ait görüntü özellikleri `softmax2_pre_activation`) ve önceden eğitilmiş kullanarak bir veri kümesi puanlar `TensorFlow` modeli.</span><span class="sxs-lookup"><span data-stu-id="cc303-298">The `ScoreTensorFlowModel` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="cc303-299">`softmax2_pre_activation` model, görüntüleri sınıfı belirleyen ile ait olduğu yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="cc303-299">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="cc303-300">`softmax2_pre_activation` Görüntü kategorilerin her birine ve tüm bu olasılıklar olasılığını döndürür, en fazla 1 eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc303-300">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="cc303-301">Bu görüntü tek bir kategoriye ait olacak aşağıdaki örnekte gösterildiği gibi varsayılır:</span><span class="sxs-lookup"><span data-stu-id="cc303-301">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="cc303-302">örneği</span><span class="sxs-lookup"><span data-stu-id="cc303-302">Class</span></span>         | <span data-ttu-id="cc303-303">Olasılık</span><span class="sxs-lookup"><span data-stu-id="cc303-303">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="cc303-304">0.001</span><span class="sxs-lookup"><span data-stu-id="cc303-304">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="cc303-305">0.95</span><span class="sxs-lookup"><span data-stu-id="cc303-305">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="cc303-306">0,06</span><span class="sxs-lookup"><span data-stu-id="cc303-306">0.06</span></span>         |

<span data-ttu-id="cc303-307">Append `TensorFlowTransform` için `estimator` aşağıdaki kod satırını ile:</span><span class="sxs-lookup"><span data-stu-id="cc303-307">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="cc303-308">Eğitim algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="cc303-308">Choose a training algorithm</span></span>

<span data-ttu-id="cc303-309">Eğitim algoritması eklemek için çağrı `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` sarmalayıcı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc303-309">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` wrapper method.</span></span>  <span data-ttu-id="cc303-310">[LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) eklenir `estimator` ve yeni görüntü özelliklerini kabul eder (`softmax2_pre_activation`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="cc303-310">The [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="cc303-311">Eğitmeni ile aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cc303-311">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="cc303-312">Harita gerekir `predictedlabel` için `predictedlabelvalue`:</span><span class="sxs-lookup"><span data-stu-id="cc303-312">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="cc303-313">`Fit()` Yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="cc303-313">The `Fit()` method trains your model by transforming the dataset and applying the training.</span></span> <span data-ttu-id="cc303-314">Eğitim veri kümesi modeline uygun ve sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen model dönüş `ReuseAndTuneInceptionModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-314">Fit the model to the training dataset and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="cc303-315">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, birden çok test veri kümesini girdi satırları sağlanan için Öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc303-315">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="cc303-316">Dönüştürme `Training` aşağıdakileri ekleyerek veri kod için `ReuseAndTuneInceptionModel()`:</span><span class="sxs-lookup"><span data-stu-id="cc303-316">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="cc303-317">Görüntü veri ve öngörü dönüştürme `DataViews` içine kesin türü belirtilmiş `IEnumerables` çiftine daha kolay görüntüleme için.</span><span class="sxs-lookup"><span data-stu-id="cc303-317">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="cc303-318">Kullanım `MLContext.CreateEnumerable()` yöntemi, aşağıdaki kodu kullanarak yapmak için:</span><span class="sxs-lookup"><span data-stu-id="cc303-318">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="cc303-319">Çağrı `DisplayResults()` veriler ve Öngörüler sonraki satırda görüntülenecek yöntemi `ReuseAndTuneInceptionModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-319">Call the `DisplayResults()` method to display your data and predictions as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

<span data-ttu-id="cc303-320">Ayarlanırsa, tahmin sonra [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-320">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="cc303-321">Model değerlendirir (tahmin edilen değeri ile gerçek veri kümesini karşılaştırır `Labels`).</span><span class="sxs-lookup"><span data-stu-id="cc303-321">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="cc303-322">Model performansı ölçümlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc303-322">Returns the model performance metrics.</span></span>

<span data-ttu-id="cc303-323">Aşağıdaki kodu ekleyin `ReuseAndTuneInceptionModel()` yöntemi sonraki satır olarak:</span><span class="sxs-lookup"><span data-stu-id="cc303-323">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="cc303-324">Aşağıdaki ölçümler için görüntü sınıflandırması değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="cc303-324">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="cc303-325">`Log-loss` -bkz [günlük kaybı](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="cc303-325">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="cc303-326">Sıfır olarak mümkün olduğunca yakın olmasını günlük zarar kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc303-326">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="cc303-327">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="cc303-327">`Per class Log-loss`.</span></span> <span data-ttu-id="cc303-328">Sınıf günlük kaybı sıfır olarak mümkün olduğunca yakın olmasını istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="cc303-328">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="cc303-329">Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="cc303-329">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 <span data-ttu-id="cc303-330">Sonraki satır olarak eğitilen model döndürmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cc303-330">Add the following code to return the trained model as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="cc303-331">Yüklenen bir model ile görüntü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="cc303-331">Classify images with a loaded model</span></span>

<span data-ttu-id="cc303-332">Aşağıdaki çağrısı ekleyin `ClassifyImages()` yöntemi sonraki kod satırı olarak `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-332">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="cc303-333">`ClassifyImages()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="cc303-333">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="cc303-334">Okur. TSV dosyasına `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="cc303-334">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="cc303-335">Test verileri temel alan görüntü sınıflandırmaları tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="cc303-335">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="cc303-336">Oluşturma `ClassifyImages()` yöntemi hemen sonrasına `ReuseAndTuneInceptionModel()` yöntemi ve hemen önce `PairAndDisplayResults()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="cc303-336">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="cc303-337">İlk olarak, çağrı `ReadFromTsv()` yöntemi oluşturmak için bir `IEnumerable<ImageData>` her biri için tam yolu içeren sınıf `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="cc303-337">First, call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="cc303-338">Bu dosya yolu, veri ve öngörü sonuçlarınızı eşleştirmeye ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="cc303-338">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="cc303-339">Dönüştürmeniz gerekir `IEnumerable<ImageData>` sınıfının bir `IDataView` tahmin etmek için kullanacağınız.</span><span class="sxs-lookup"><span data-stu-id="cc303-339">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="cc303-340">Sonraki iki satırlar halinde aşağıdaki kodu ekleyin `ClassifyImages()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-340">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

<span data-ttu-id="cc303-341">Eğitim resmi verilerle daha önce yaptığınız gibi test görüntü kullanarak verileri kategori tahmin [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) modelin yönteme içinde.</span><span class="sxs-lookup"><span data-stu-id="cc303-341">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the model passed in.</span></span> <span data-ttu-id="cc303-342">Aşağıdaki kodu ekleyin `ClassifyImages()` yöntemi tahminler elde etmek için ve dönüştürmek için `predictions` `IDataView` içine bir `IEnumerable` eşleştirme ve görüntüleme için:</span><span class="sxs-lookup"><span data-stu-id="cc303-342">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="cc303-343">Eşleştirebilir ve Öngörüler ve test görüntü verilerini görüntülemek için çağırmak için aşağıdaki kodu ekleyin. `DisplayResults()` sonraki satırı olarak daha önce oluşturduğunuz yöntemi `ClassifyImages()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-343">To pair and display your test image data and predictions, add the following code to call the `DisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="cc303-344">Yüklenen bir model ile tek bir görüntü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="cc303-344">Classify a single image with a loaded model</span></span>

<span data-ttu-id="cc303-345">Aşağıdaki çağrısı ekleyin `ClassifySingleImage()` yöntemi sonraki kod satırı olarak `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-345">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="cc303-346">`ClassifySingleImage()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="cc303-346">The `ClassifySingleImage()` method executes the following tasks:</span></span>

* <span data-ttu-id="cc303-347">Yükleri bir `ImageData` örneği.</span><span class="sxs-lookup"><span data-stu-id="cc303-347">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="cc303-348">Test verileri temel alan görüntü sınıflandırması tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="cc303-348">Predicts image classification based on test data.</span></span>

<span data-ttu-id="cc303-349">Oluşturma `ClassifySingleImage()` yöntemi hemen sonrasına `ClassifyImages()` yöntemi ve hemen önce `PairAndDisplayResults()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="cc303-349">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="cc303-350">İlk olarak, oluşturun bir `ImageData` tek tam yol ve görüntü dosya adı içeren sınıf `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="cc303-350">First, create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="cc303-351">Sonraki satırları olarak aşağıdaki kodu ekleyin `ClassifySingleImage()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-351">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="cc303-352">[PredictionEngine sınıfı](xref:Microsoft.ML.PredictionEngine%602) tahmin verilerini tek bir örneğini gerçekleştirdiği API kolaylığıdır.</span><span class="sxs-lookup"><span data-stu-id="cc303-352">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="cc303-353">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütununu tahmin sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc303-353">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="cc303-354">Geçirmek `imageData` için `PredictionEngine` resim kategorisi aşağıdaki kodu ekleyerek tahmin etmek için `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="cc303-354">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="cc303-355">Sonraki kod satırı olarak tahmin sonucu görüntülemek `ClassifySingleImage()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cc303-355">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="cc303-356">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="cc303-356">Results</span></span>

<span data-ttu-id="cc303-357">Önceki adımları tamamladıktan sonra Konsol uygulamanızı (Ctrl + F5) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cc303-357">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="cc303-358">Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cc303-358">Your results should be similar to the following output.</span></span>  <span data-ttu-id="cc303-359">Uyarı veya işlem iletileri görebilirsiniz, ancak bu iletiler anlaşılması için aşağıdaki sonuçları kaldırılmış olan.</span><span class="sxs-lookup"><span data-stu-id="cc303-359">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="cc303-360">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="cc303-360">Congratulations!</span></span> <span data-ttu-id="cc303-361">Şimdi başarıyla bir makine öğrenme modelinin görüntü sınıflandırması için önceden eğitilmiş yeniden kullanarak derlediğiniz `TensorFlow` ML.NET içindeki model.</span><span class="sxs-lookup"><span data-stu-id="cc303-361">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="cc303-362">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) depo.</span><span class="sxs-lookup"><span data-stu-id="cc303-362">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="cc303-363">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="cc303-363">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="cc303-364">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="cc303-364">Understand the problem</span></span>
> * <span data-ttu-id="cc303-365">Yeniden kullanmak ve önceden eğitilmiş bir modeli ayarlama</span><span class="sxs-lookup"><span data-stu-id="cc303-365">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="cc303-366">Yüklenen bir model ile görüntü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="cc303-366">Classify images with a loaded model</span></span>

<span data-ttu-id="cc303-367">Bir genişletilmiş görüntü sınıflandırma örnek keşfetmek için Machine Learning örnekleri GitHub havuzuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="cc303-367">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="cc303-368">DotNet/machinelearning-samples GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="cc303-368">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
