---
title: 'Öğretici: TensorFlow görüntü sınıflandırıcısını yeniden eğitme-aktarım öğrenimi'
description: Transfer Learning ve ML.NET ile görüntü sınıflandırması TensorFlow modelini yeniden eğitme hakkında bilgi edinin. Özgün model tek tek resimleri sınıflandırmak için eğitildi. Yeniden öğreticduktan sonra, yeni model görüntüleri geniş kategoriler halinde düzenler.
ms.date: 07/09/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: eb6e3d3f3a33aa7360802ce1bc6c16532539c828
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929234"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a><span data-ttu-id="7767a-105">Öğretici: Transfer Learning ve ML.NET ile bir TensorFlow görüntü sınıflandırıcısını yeniden eğitme</span><span class="sxs-lookup"><span data-stu-id="7767a-105">Tutorial: Retrain a TensorFlow image classifier with transfer learning and ML.NET</span></span>

<span data-ttu-id="7767a-106">Transfer Learning ve ML.NET ile görüntü sınıflandırması TensorFlow modelini yeniden eğitme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="7767a-106">Learn how to retrain an image classification TensorFlow model with transfer learning and ML.NET.</span></span> <span data-ttu-id="7767a-107">Özgün model tek tek resimleri sınıflandırmak için eğitildi.</span><span class="sxs-lookup"><span data-stu-id="7767a-107">The original model was trained to classify individual images.</span></span> <span data-ttu-id="7767a-108">Yeniden öğreticduktan sonra, yeni model görüntüleri geniş kategoriler halinde düzenler.</span><span class="sxs-lookup"><span data-stu-id="7767a-108">After retraining, the new model organizes the images into broad categories.</span></span> 

<span data-ttu-id="7767a-109">[Görüntü sınıflandırma](https://en.wikipedia.org/wiki/Outline_of_object_recognition) modelini sıfırdan eğitmek için milyonlarca parametre, bir dizi etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7767a-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="7767a-110">Özel bir modeli sıfırdan eğitmek kadar uygun olmasa da, aktarım öğrenimi, binlerce görüntüde ve çok hızlı bir şekilde özelleştirilmiş bir model (bir saat içinde, GPU).</span><span class="sxs-lookup"><span data-stu-id="7767a-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="7767a-111">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="7767a-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="7767a-112">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="7767a-112">Understand the problem</span></span>
> * <span data-ttu-id="7767a-113">Önceden eğitilen modeli yeniden kullanma ve ayarlama</span><span class="sxs-lookup"><span data-stu-id="7767a-113">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="7767a-114">Görüntüleri sınıflandır</span><span class="sxs-lookup"><span data-stu-id="7767a-114">Classify Images</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="7767a-115">Aktarım öğrenimi nedir?</span><span class="sxs-lookup"><span data-stu-id="7767a-115">What is transfer learning?</span></span>

<span data-ttu-id="7767a-116">Zaten benzer bir sorunu çözmek için eğitilen bir modeli yeniden kullanabilmeniz ve bu modelin tamamını ya da bir kısmını yeniden eğitmeniz durumunda ne olur?</span><span class="sxs-lookup"><span data-stu-id="7767a-116">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="7767a-117">Yeni bir model oluşturmak için zaten eğitilen bir modelin bir kısmını yeniden kullanma tekniği, [Aktarım öğrenimi](https://en.wikipedia.org/wiki/Transfer_learning)olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="7767a-117">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="7767a-118">Görüntü sınıflandırması örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="7767a-118">Image classification sample overview</span></span>

<span data-ttu-id="7767a-119">Örnek, görüntüleri az miktarda eğitim verileriyle sınıflandırmak için önceden eğitilen bir modeli yeniden kullanarak bir görüntü Sınıflandırıcısı oluşturmak için ML.NET kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="7767a-119">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="7767a-120">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7767a-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="7767a-121">Varsayılan olarak, Bu öğreticinin .NET proje yapılandırmasında .NET Core 2,2 ' i hedeflediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7767a-121">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7767a-122">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7767a-122">Prerequisites</span></span>

* <span data-ttu-id="7767a-123">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="7767a-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span> 

* <span data-ttu-id="7767a-124">Microsoft.ML 1.0.0 NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="7767a-124">Microsoft.ML 1.0.0 Nuget package</span></span>
* <span data-ttu-id="7767a-125">Microsoft. ML. ımageanalytics 1.0.0 NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="7767a-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget package</span></span>
* <span data-ttu-id="7767a-126">Microsoft. ML. TensorFlow 0.12.0 NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="7767a-126">Microsoft.ML.TensorFlow 0.12.0 Nuget package</span></span>

* [<span data-ttu-id="7767a-127">Öğretici varlıkları dizini. ZIP dosyası</span><span class="sxs-lookup"><span data-stu-id="7767a-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="7767a-128">InceptionV1 Machine Learning modeli</span><span class="sxs-lookup"><span data-stu-id="7767a-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="7767a-129">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="7767a-129">Select the appropriate machine learning task</span></span>

<span data-ttu-id="7767a-130">[Derin öğrenme](https://en.wikipedia.org/wiki/Deep_learning) , görüntü işleme ve konuşma tanıma gibi revolutionizing alan Machine Learning bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="7767a-130">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="7767a-131">Derin öğrenme modelleri, birden fazla öğrenme katmanı içeren büyük ölçekli [veri](https://en.wikipedia.org/wiki/Labeled_data) ve [sinir Networks](https://en.wikipedia.org/wiki/Artificial_neural_network) kümeleri kullanılarak eğitilir.</span><span class="sxs-lookup"><span data-stu-id="7767a-131">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="7767a-132">Derin öğrenme:</span><span class="sxs-lookup"><span data-stu-id="7767a-132">Deep learning:</span></span>

* <span data-ttu-id="7767a-133">Görüntü İşleme gibi bazı görevlerde daha iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="7767a-133">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="7767a-134">Büyük veri miktarları üzerinde iyi sonuç verir.</span><span class="sxs-lookup"><span data-stu-id="7767a-134">Performs well on huge data amounts.</span></span>

<span data-ttu-id="7767a-135">Görüntü sınıflandırması, görüntüleri otomatik olarak birden çok kategoride sınıflandırmamızı sağlayan ortak bir Machine Learning görevdir:</span><span class="sxs-lookup"><span data-stu-id="7767a-135">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="7767a-136">Görüntüde insan yüzü algılanıyor.</span><span class="sxs-lookup"><span data-stu-id="7767a-136">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="7767a-137">Kediler ve köpekler algılanıyor.</span><span class="sxs-lookup"><span data-stu-id="7767a-137">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="7767a-138">Ya da bir görüntünün (n) yiyecek, oyunı veya gereç olduğunu belirleyen aşağıdaki görüntülerde olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="7767a-138">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="7767a-139">![Pizza Image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![oyuncak](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
ayı![görüntüsü Toaster görüntüsü](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="7767a-139">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="7767a-140">Önceki görüntüler Wikimedia Commons ' a aittir ve aşağıdaki gibi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7767a-140">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="7767a-141">"220px-Pepperoni_pizza. jpg" genel etki alanı https://commons.wikimedia.org/w/index.php?curid=79505 ,,</span><span class="sxs-lookup"><span data-stu-id="7767a-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="7767a-142">[Jonık](https://commons.wikimedia.org/wiki/User:Jonik) -Self-Photo, CC BY-SA 2,0, https://commons.wikimedia.org/w/index.php?curid=48166 ile "119px-Nalle_-_a_small_brown_teddy_bear. jpg".</span><span class="sxs-lookup"><span data-stu-id="7767a-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="7767a-143">"193px-Broodrooster. jpg"- [k. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) -kendi ÇALıŞMASı, CC BY-SA 3,0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="7767a-143">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="7767a-144">Aktarım öğrenimi, tüm katmanları ve *Penultimate katmanını* *yeniden eğitme* gibi birkaç strateji içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-144">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="7767a-145">Bu öğretici, *Penultimate katman stratejisinin*nasıl kullanılacağını açıklayacak ve gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="7767a-145">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="7767a-146">*Penultimate katman stratejisi* , belirli bir sorunu çözmek için önceden eğitilen bir modeli yeniden kullanır.</span><span class="sxs-lookup"><span data-stu-id="7767a-146">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="7767a-147">Strateji daha sonra yeni bir sorunu çözmeleri için bu modelin son katmanını geri çeker.</span><span class="sxs-lookup"><span data-stu-id="7767a-147">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="7767a-148">Yeni modelinizin bir parçası olarak önceden eğitilen modeli yeniden kullanmak önemli zaman ve kaynakları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7767a-148">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="7767a-149">Görüntü sınıflandırma modeliniz, popüler bir [](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)görüntü tanıma modeli olan `ImageNet` veri kümesi üzerinde eğitilen modeli, popüler bir görüntü tanıma modelini yeniden kullanır, bu da TensorFlow modelinin tüm görüntülerini "şemsiye", "Jersey" ve "gibi binlik bir sınıfa sınıflandırmaya çalıştığı Dishroni ".</span><span class="sxs-lookup"><span data-stu-id="7767a-149">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="7767a-150">, `Inception v1 model` [Derin bir evsel sinir ağı](https://en.wikipedia.org/wiki/Convolutional_neural_network) olarak sınıflandırılabilir ve sabit görsel tanıma görevlerinde, bazı etki alanlarında insan performansını eşleştirerek veya aşarak makul bir performans elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="7767a-150">The `Inception v1 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="7767a-151">Model/algoritma birden çok araştırmacılar tarafından geliştirilmiştir ve özgün kağıda dayalıdır: ["Szegedy, et tarafından Görüntü İşleme" için bir değerlendirme mimarisini yeniden düşünüyorsunuz. Eşkenar.](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="7767a-151">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="7767a-152">, `Inception model` Binlerce farklı görüntüde önceden eğitilen için görüntü tanımlama için gereken [görüntü özelliklerini](https://en.wikipedia.org/wiki/Feature_(computer_vision)) içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-152">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="7767a-153">Küçük görüntü özelliği katmanları basit özellikleri (kenarlar gibi) tanır ve daha yüksek katmanlar daha karmaşık özellikleri (örneğin şekiller) tanır.</span><span class="sxs-lookup"><span data-stu-id="7767a-153">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="7767a-154">Görüntülerin sınıflandırılacağı önceden eğitilen bir model ile başladığınız için son katman çok daha küçük bir veri kümesine göre eğitilir.</span><span class="sxs-lookup"><span data-stu-id="7767a-154">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="7767a-155">Modeliniz ikiden fazla kategori sınıflandırmanıza izin verdiğinden, bu [çok sınıf sınıflandırıcının](../resources/tasks.md#multiclass-classification)bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="7767a-155">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="7767a-156">`TensorFlow`, eğitim derin sinir ağlarını (ve genel sayısal hesaplamalar) sağlayan ve ml.NET içinde bir `transformer` olarak uygulanan popüler bir derin öğrenme ve makine öğrenimi araç setidir.</span><span class="sxs-lookup"><span data-stu-id="7767a-156">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="7767a-157">Bu öğreticide, yeniden kullanmak `Inception model`için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7767a-157">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="7767a-158">Aşağıdaki diyagramda gösterildiği gibi, .NET Core veya .NET Framework uygulamalarında ML.NET NuGet paketlerine bir başvuru eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="7767a-158">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="7767a-159">ML.net, kapsar ve var olan bir eğitilen `TensorFlow` `TensorFlow` model dosyasını Puanlama için yükleyen kodu yazmanızı sağlayan yerel kitaplığı içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-159">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![TensorFlow Transform ML.NET yay diyagramı](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="7767a-161">`Inception model` Görüntüleri bin kategoride sınıflandırıp, ancak daha küçük bir kategori kümesindeki görüntüleri ve yalnızca bu kategorileri sınıflandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7767a-161">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="7767a-162">`transfer` Parçasını`transfer learning`girin.</span><span class="sxs-lookup"><span data-stu-id="7767a-162">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="7767a-163">Özel görüntü sınıflandırıcınızın yeni sınırlı kategorilerine görüntü tanıma ve sınıflandırma özelliğini aktarabilirsiniz `Inception model`.</span><span class="sxs-lookup"><span data-stu-id="7767a-163">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="7767a-164">Bu modelin son katmanını, üç kategori kümesini kullanarak yeniden eğitecağız:</span><span class="sxs-lookup"><span data-stu-id="7767a-164">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="7767a-165">Yiyecek</span><span class="sxs-lookup"><span data-stu-id="7767a-165">Food</span></span>
* <span data-ttu-id="7767a-166">Cağı</span><span class="sxs-lookup"><span data-stu-id="7767a-166">Toy</span></span>
* <span data-ttu-id="7767a-167">Elektrikli</span><span class="sxs-lookup"><span data-stu-id="7767a-167">Appliance</span></span>

<span data-ttu-id="7767a-168">Katmanınız, doğru kategoriyi olabildiğince çabuk bulmak için [ÇOKTERİMLİ lojistik regresyon algoritmasını](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) kullanır.</span><span class="sxs-lookup"><span data-stu-id="7767a-168">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="7767a-169">Bu algoritma, yanıtı tespit etmek için olasılıkların kullanımını sınıflandırarak, doğru kategoriye bir değer ve diğerlerine sıfır değer verir.</span><span class="sxs-lookup"><span data-stu-id="7767a-169">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="7767a-170">DataSet</span><span class="sxs-lookup"><span data-stu-id="7767a-170">DataSet</span></span>

<span data-ttu-id="7767a-171">İki veri kaynağı vardır: `.tsv` dosya ve resim dosyaları.</span><span class="sxs-lookup"><span data-stu-id="7767a-171">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="7767a-172">Dosya iki sütun içerir: ilki olarak `ImagePath` tanımlanır ve ikinci tane `Label` görüntüye karşılık gelir. `tags.tsv`</span><span class="sxs-lookup"><span data-stu-id="7767a-172">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="7767a-173">Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="7767a-173">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="7767a-174">Eğitim ve test görüntüleri, bir ZIP dosyasında indirileceği varlıklar klasörlerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7767a-174">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="7767a-175">Bu görüntüler Wikimedia Commons ' a aittir.</span><span class="sxs-lookup"><span data-stu-id="7767a-175">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="7767a-176">*[Wkımedıa Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), ücretsiz medya deposu.*</span><span class="sxs-lookup"><span data-stu-id="7767a-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="7767a-177">10:48 Ekim, 2018:</span><span class="sxs-lookup"><span data-stu-id="7767a-177">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="7767a-178">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="7767a-178">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="7767a-179">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="7767a-179">Create a project</span></span>

1. <span data-ttu-id="7767a-180">"TransferLearningTF" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7767a-180">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

2. <span data-ttu-id="7767a-181">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="7767a-181">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="7767a-182">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7767a-182">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="7767a-183">Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="7767a-183">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="7767a-184">**Sürüm** açılır listesine tıklayın, listeden **1.0.0** paketini seçin ve ardından **Kaldır düğmesini seçin** .</span><span class="sxs-lookup"><span data-stu-id="7767a-184">Click on the **Version** drop-down, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="7767a-185">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7767a-185">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="7767a-186">**Microsoft. ml. ımageanalytics v 1.0.0** ve **Microsoft. ml. TensorFlow v 0.12.0**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="7767a-186">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.0.0** and **Microsoft.ML.TensorFlow v0.12.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="7767a-187">Verilerinizi hazırlayın</span><span class="sxs-lookup"><span data-stu-id="7767a-187">Prepare your data</span></span>

1. <span data-ttu-id="7767a-188">[Proje Varlıkları Dizin ZIP dosyasını](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)indirin ve sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="7767a-188">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="7767a-189">Dizini transferlearningtf proje dizininize kopyalayın. `assets`</span><span class="sxs-lookup"><span data-stu-id="7767a-189">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="7767a-190">Bu dizin ve alt dizinleri, bu öğretici için gerekli olan veri ve destek dosyalarını (bir sonraki adımda indirecek ve ekleyeceğiniz bir model hariç) içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-190">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="7767a-191">[Inception modelini](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)indirin ve sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="7767a-191">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="7767a-192">`inception5h` Dizinin içeriğini *transferlearningtf* proje `assets\inputs-train\inception` dizininize kopyalamanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="7767a-192">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="7767a-193">Bu dizin, aşağıdaki görüntüde gösterildiği gibi, bu öğretici için gereken modeli ve ek destek dosyalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="7767a-193">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Dizin içeriğini geçersiz kılma](./media/image-classification/inception-files.png)

5. <span data-ttu-id="7767a-195">Çözüm Gezgini, varlık dizinindeki ve alt dizinlerde bulunan dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7767a-195">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="7767a-196">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7767a-196">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="7767a-197">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="7767a-197">Create classes and define paths</span></span>

<span data-ttu-id="7767a-198">Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-198">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="7767a-199">Çeşitli varlıkların yollarını tutmak için genel alanlar,, ve `LabelTokey` `PredictedLabelValue`için`ImageReal`genel değişkenler oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7767a-199">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="7767a-200">`_assetsPath`, varlıkların yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-200">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="7767a-201">`_trainTagsTsv`Eğitim resmi veri etiketleri TSV dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-201">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="7767a-202">`_predictTagsTsv`tahmin görüntüsü veri etiketleri TSV dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-202">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="7767a-203">`_trainImagesFolder`modeli eğitmek için kullanılan görüntülerin yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-203">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="7767a-204">`_predictImagesFolder`eğitilen model tarafından sınıflandırılacak görüntülerin yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-204">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="7767a-205">`_inceptionPb`, modelinize yeniden eğmek için önceden eğitilen modelin yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-205">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="7767a-206">`_inputImageClassifierZip`eğitilen modelin yüklendiği yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-206">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="7767a-207">`_outputImageClassifierZip`Eğitim modelinin kaydedildiği yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-207">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="7767a-208">`LabelTokey`, bir anahtarla eşleştirilmiş değerdir.`Label`</span><span class="sxs-lookup"><span data-stu-id="7767a-208">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="7767a-209">`ImageReal`tahmin edilen görüntü değerini içeren sütundur.</span><span class="sxs-lookup"><span data-stu-id="7767a-209">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="7767a-210">`PredictedLabelValue`tahmin edilen etiket değerini içeren sütundur.</span><span class="sxs-lookup"><span data-stu-id="7767a-210">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="7767a-211">Aşağıdaki kodu, bu yolları ve diğer değişkenleri belirtmek için `Main` yönteminin hemen üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-211">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="7767a-212">Giriş verileriniz için bazı sınıflar ve tahminler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7767a-212">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="7767a-213">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-213">Add a new class to your project:</span></span>

1. <span data-ttu-id="7767a-214">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7767a-214">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="7767a-215">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ImageData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7767a-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="7767a-216">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7767a-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="7767a-217">*ImageData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="7767a-217">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="7767a-218">Aşağıdaki `using` ifadeyi *ImageData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-218">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="7767a-219">Mevcut sınıf tanımını kaldırın ve `ImageData` sınıf için aşağıdaki kodu *ImageData.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-219">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="7767a-220">`ImageData`, giriş resmi veri sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7767a-220">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="7767a-221">`ImagePath`görüntü dosyası adını içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-221">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="7767a-222">`Label`resim etiketi için bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-222">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="7767a-223">Projenize yeni bir sınıf ekleyin `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="7767a-223">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="7767a-224">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7767a-224">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="7767a-225">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ImagePrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7767a-225">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="7767a-226">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7767a-226">Then, select the **Add** button.</span></span>

    <span data-ttu-id="7767a-227">*ImagePrediction.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="7767a-227">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="7767a-228">*ImagePrediction.cs 'in*en üstündeki `System.Text` `System.Collections.Generic` `using` ve deyimlerini kaldırın:</span><span class="sxs-lookup"><span data-stu-id="7767a-228">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="7767a-229">Mevcut sınıf tanımını kaldırın ve `ImagePrediction` *ImagePrediction.cs* dosyasına sınıfına sahip olan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-229">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="7767a-230">`ImagePrediction`, görüntü tahmin sınıfıdır ve aşağıdaki alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7767a-230">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="7767a-231">`Score`belirli bir görüntü sınıflandırması için güven yüzdesini içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-231">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="7767a-232">`PredictedLabelValue`tahmin edilen görüntü sınıflandırma etiketi için bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-232">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="7767a-233">`ImagePrediction`, model eğitilen bir tahmin için kullanılan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="7767a-233">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="7767a-234">Görüntü yolu için `string` bir`ImagePath`() içerir.</span><span class="sxs-lookup"><span data-stu-id="7767a-234">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="7767a-235">, `Label` Modeli yeniden kullanmak ve yeniden geliştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7767a-235">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="7767a-236">, `PredictedLabelValue` Tahmin ve değerlendirme sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7767a-236">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="7767a-237">Değerlendirme için eğitim verileri olan bir giriş, tahmin edilen değerler ve model kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7767a-237">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="7767a-238">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7767a-238">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="7767a-239">Entity Framework, kavramsal `DBContext` olarak da benzerdir.</span><span class="sxs-lookup"><span data-stu-id="7767a-239">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="7767a-240">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="7767a-240">Initialize variables in Main</span></span>

<span data-ttu-id="7767a-241">Değişkeni yeni bir `MLContext`örneğiyle başlatın. `mlContext`</span><span class="sxs-lookup"><span data-stu-id="7767a-241">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="7767a-242">Satırı, `Main` yöntemindeki aşağıdaki kodla değiştirin: `Console.WriteLine("Hello World!")`</span><span class="sxs-lookup"><span data-stu-id="7767a-242">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="7767a-243">Varsayılan parametreler için bir struct oluşturun</span><span class="sxs-lookup"><span data-stu-id="7767a-243">Create a struct for default parameters</span></span>

<span data-ttu-id="7767a-244">Inception modelinde, geçirmeniz gereken birkaç varsayılan parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="7767a-244">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="7767a-245">Aşağıdaki kodla, varsayılan parametre değerlerini kolay adlarla eşlemek için bir struct oluşturun, yalnızca `Main()` yönteminden sonra:</span><span class="sxs-lookup"><span data-stu-id="7767a-245">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="7767a-246">Görüntüleme yardımcı programı yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7767a-246">Create a display utility method</span></span>

<span data-ttu-id="7767a-247">Görüntü verilerini ve ilgili tahminleri birden çok kez görüntüleyenden sonra, görüntüyü ve tahmin sonuçlarını görüntülemeyi işlemek için bir görüntüleme yardımcı programı yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7767a-247">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

<span data-ttu-id="7767a-248">`DisplayResults()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="7767a-248">The `DisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="7767a-249">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7767a-249">Displays the predicted results.</span></span>

<span data-ttu-id="7767a-250">Aşağıdaki kodu kullanarak, `InceptionSettings` yapının hemen ardından yöntemioluşturun:`DisplayResults()`</span><span class="sxs-lookup"><span data-stu-id="7767a-250">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

<span data-ttu-id="7767a-251">Yöntemi tahmin edilen alanlarla `ImagePrediction` birlikte doldurulur `ImagePath`. `Transform()`</span><span class="sxs-lookup"><span data-stu-id="7767a-251">The `Transform()` method populated `ImagePath` in `ImagePrediction` along with the predicted fields.</span></span> <span data-ttu-id="7767a-252">ML.NET işlemi ilerledikçe, her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:</span><span class="sxs-lookup"><span data-stu-id="7767a-252">As the ML.NET process progresses, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="7767a-253">`DisplayResults()` Yöntemi iki görüntü sınıflandırma yöntemlerinde çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="7767a-253">You'll call the `DisplayResults()` method in the two image classification methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="7767a-254">. Tsv dosya yardımcı programı yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7767a-254">Create a .tsv file utility method</span></span>

<span data-ttu-id="7767a-255">`ReadFromTsv()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="7767a-255">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="7767a-256">Resim veri `tags.tsv` dosyasını okur.</span><span class="sxs-lookup"><span data-stu-id="7767a-256">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="7767a-257">Dosya yolunu görüntü dosyası adına ekler.</span><span class="sxs-lookup"><span data-stu-id="7767a-257">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="7767a-258">Dosya verilerini IEnumerable`ImageData` nesnesine yükler.</span><span class="sxs-lookup"><span data-stu-id="7767a-258">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="7767a-259">Aşağıdaki kodu kullanarak yönteminden hemen `PairAndDisplayResults()` sonra yönteminioluşturun:`ReadFromTsv()`</span><span class="sxs-lookup"><span data-stu-id="7767a-259">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="7767a-260">Aşağıdaki `tags.tsv` kod, dosya yolunu `ImagePath` özellik için görüntü dosyası adına eklemek `Label` ve bir `ImageData` nesnesine yüklemek için dosyasını ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="7767a-260">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="7767a-261">`ReadFromTsv()` Metodun ilk satırı olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7767a-261">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="7767a-262">Tahmin sonuçlarını göstermek için tam dosya yolu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7767a-262">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="7767a-263">ML.NET ' de üç ana kavram vardır: [Veri](../resources/glossary.md#data), [dönüştürücüler](../resources/glossary.md#transformer)ve [estimators](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="7767a-263">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="7767a-264">Önceden eğitilen modeli yeniden kullanma ve ayarlama</span><span class="sxs-lookup"><span data-stu-id="7767a-264">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="7767a-265">`ReuseAndTuneInceptionModel()` Yöntemi`Main()` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-265">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="7767a-266">`ReuseAndTuneInceptionModel()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="7767a-266">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="7767a-267">Verileri yükler</span><span class="sxs-lookup"><span data-stu-id="7767a-267">Loads the data</span></span>
* <span data-ttu-id="7767a-268">Verileri ayıklar ve dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="7767a-268">Extracts and transforms the data.</span></span>
* <span data-ttu-id="7767a-269">TensorFlow modeline puan alır.</span><span class="sxs-lookup"><span data-stu-id="7767a-269">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="7767a-270">Model (geri çekme).</span><span class="sxs-lookup"><span data-stu-id="7767a-270">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="7767a-271">Model sonuçlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7767a-271">Displays model results.</span></span>
* <span data-ttu-id="7767a-272">Modeli değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="7767a-272">Evaluates the model.</span></span>
* <span data-ttu-id="7767a-273">Modeli döndürür.</span><span class="sxs-lookup"><span data-stu-id="7767a-273">Returns the model.</span></span>

<span data-ttu-id="7767a-274">Aşağıdaki kodu kullanarak, `InceptionSettings` `DisplayResults()` yapının hemen ardından ve yönteminden hemen önce yönteminioluşturun:`ReuseAndTuneInceptionModel()`</span><span class="sxs-lookup"><span data-stu-id="7767a-274">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="7767a-275">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="7767a-275">Load the data</span></span>

<span data-ttu-id="7767a-276">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="7767a-276">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="7767a-277">`IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="7767a-277">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="7767a-278">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7767a-278">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="7767a-279">`MLContext.Data.LoadFromTextFile` Sarmalayıcı kullanarak verileri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7767a-279">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="7767a-280">Aşağıdaki kodu `ReuseAndTuneInceptionModel()` yönteminin sonraki satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-280">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="7767a-281">Özellikleri Ayıkla ve verileri Dönüştür</span><span class="sxs-lookup"><span data-stu-id="7767a-281">Extract Features and transform the data</span></span>

<span data-ttu-id="7767a-282">Önceden işleme ve temizleme verileri, makine öğrenimi için bir veri kümesi etkin bir şekilde kullanılmadan önce oluşan önemli görevlerdir.</span><span class="sxs-lookup"><span data-stu-id="7767a-282">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="7767a-283">Bu modelleme görevleri olmadan veri kullanımı, yanıltıcı sonuçlar üretebilir.</span><span class="sxs-lookup"><span data-stu-id="7767a-283">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="7767a-284">Makine öğrenimi algoritmaları [, verileri ve](../resources/glossary.md#feature) derin sinir ağlarla ilgilenirken görüntüleri ağ tarafından beklenen biçime uyarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7767a-284">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="7767a-285">Bu biçim sayısal bir [vektördür](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="7767a-285">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="7767a-286">Eğitim ve değerlendirmeden sonra **etiket** sütun değerleriyle birlikte tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="7767a-286">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="7767a-287">Önceden eğitilen bir model kullanırken, alanları [Mapvaluetokey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemiyle yeni modelle eşleyin.</span><span class="sxs-lookup"><span data-stu-id="7767a-287">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="7767a-288">Bu yöntem, `Label` bir sayısal anahtar türü (`LabelTokey`) sütununu dönüştürür ve bunu yeni veri kümesi sütunu olarak ekler:  Bunu, `estimator` aynı zamanda da bu şekilde adlandırın.</span><span class="sxs-lookup"><span data-stu-id="7767a-288">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="7767a-289">Sonraki kod satırını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-289">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="7767a-290">Görüntü işleme tahmin aracı, özellik ayıklama için önceden eğitilen [derin sinir ağı (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7767a-290">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="7767a-291">Derin sinir ağlarla ilgilenirken, görüntüleri beklenen ağ biçimine uyarlayın.</span><span class="sxs-lookup"><span data-stu-id="7767a-291">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="7767a-292">Bu, görüntü verilerini modelin beklenen biçiminde almak için birkaç görüntü dönüştürme işlemi kullanmanız nedenidir:</span><span class="sxs-lookup"><span data-stu-id="7767a-292">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="7767a-293">Dönüşüm `LoadImages`görüntüleri, bir bit eşlem türü olarak belleğe yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7767a-293">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="7767a-294">`ResizeImages` Dönüştürme, önceden eğitilen modelin tanımlı bir giriş resmi genişliği ve yüksekliği olduğundan, görüntüleri yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="7767a-294">The `ResizeImages` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="7767a-295">`ExtractPixels` Dönüştürme, giriş görüntülerinden pikselleri ayıklar ve bunları sayısal bir Vector öğesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="7767a-295">The `ExtractPixels` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="7767a-296">Bu görüntü dönüşümlerini sonraki kod satırları olarak ekle:</span><span class="sxs-lookup"><span data-stu-id="7767a-296">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="7767a-297">, `LoadTensorFlowModel` `TensorFlow` `ScoreTensorFlowModel` Modelin`TensorFlowEstimator` bir kez yüklenmesine izin veren ve ardından kullanılarak oluşturulan kullanımı kolay bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="7767a-297">The `LoadTensorFlowModel` is a convenience method that allows the `TensorFlow` model to be loaded once and then creates the `TensorFlowEstimator` using `ScoreTensorFlowModel`.</span></span> <span data-ttu-id="7767a-298">Belirtilen çıktıları `Inception model`ayıklar (görüntü özellikleri `softmax2_pre_activation`) ve önceden eğitilen `TensorFlow` modeli kullanarak bir veri kümesine puan verir. `ScoreTensorFlowModel`</span><span class="sxs-lookup"><span data-stu-id="7767a-298">The `ScoreTensorFlowModel` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="7767a-299">`softmax2_pre_activation`görüntülerin hangi sınıfa ait olduğunu belirlemek için modele yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7767a-299">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="7767a-300">`softmax2_pre_activation`bir görüntü için kategorilerin her biri için bir olasılık döndürür ve bu olasılıkların hepsi 1 ' e kadar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7767a-300">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="7767a-301">Aşağıdaki örnekte gösterildiği gibi bir görüntünün yalnızca bir kategoriye ait olacağını varsayar:</span><span class="sxs-lookup"><span data-stu-id="7767a-301">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="7767a-302">örneği</span><span class="sxs-lookup"><span data-stu-id="7767a-302">Class</span></span>         | <span data-ttu-id="7767a-303">Olasılıktır</span><span class="sxs-lookup"><span data-stu-id="7767a-303">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="7767a-304">0,001</span><span class="sxs-lookup"><span data-stu-id="7767a-304">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="7767a-305">0,95</span><span class="sxs-lookup"><span data-stu-id="7767a-305">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="7767a-306">0,06</span><span class="sxs-lookup"><span data-stu-id="7767a-306">0.06</span></span>         |

<span data-ttu-id="7767a-307">Aşağıdaki kod satırıyla öğesini `estimator` öğesineekleyin:`TensorFlowTransform`</span><span class="sxs-lookup"><span data-stu-id="7767a-307">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="7767a-308">Eğitim algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="7767a-308">Choose a training algorithm</span></span>

<span data-ttu-id="7767a-309">Eğitim algoritmasını eklemek için `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` sarmalayıcı yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="7767a-309">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` wrapper method.</span></span>  <span data-ttu-id="7767a-310">[Lbfgsmaximumentropi](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) öğesine `estimator` eklenir ve geçmiş verilerden bilgi almak için Inception görüntü özelliklerini `Label` (`softmax2_pre_activation`) ve giriş parametrelerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="7767a-310">The [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="7767a-311">Aşağıdaki kodla birlikte bir sorun ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-311">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="7767a-312">Ayrıca, `predictedlabel` `predictedlabelvalue`ile arasında eşleme yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="7767a-312">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="7767a-313">`Fit()` Yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi trakla.</span><span class="sxs-lookup"><span data-stu-id="7767a-313">The `Fit()` method trains your model by transforming the dataset and applying the training.</span></span> <span data-ttu-id="7767a-314">Modeli eğitim veri kümesine sığdırın `ReuseAndTuneInceptionModel()` ve aşağıdaki kod satırını yöntemine ekleyerek eğitilen modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="7767a-314">Fit the model to the training dataset and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="7767a-315">[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapar.</span><span class="sxs-lookup"><span data-stu-id="7767a-315">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="7767a-316">Aşağıdaki kodu öğesine `ReuseAndTuneInceptionModel()`ekleyerek verileridönüştürün:`Training`</span><span class="sxs-lookup"><span data-stu-id="7767a-316">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="7767a-317">Daha kolay görüntülenmesi için görüntü verilerinizi `DataViews` ve tahminini kesin olarak `IEnumerables` belirlenmiş şekilde eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="7767a-317">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="7767a-318">Aşağıdaki kodu kullanarak bunu yapmak için yönteminikullanın:`MLContext.CreateEnumerable()`</span><span class="sxs-lookup"><span data-stu-id="7767a-318">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="7767a-319">Veri ve tahmine dayalı olarak yöntemi bir sonraki satır `ReuseAndTuneInceptionModel()` olarak göstermek için yönteminiçağırın:`DisplayResults()`</span><span class="sxs-lookup"><span data-stu-id="7767a-319">Call the `DisplayResults()` method to display your data and predictions as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

<span data-ttu-id="7767a-320">Tahmin kümesinden sonra, [değerlendir ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7767a-320">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="7767a-321">Model değerlendirir (tahmin edilen değerleri gerçek veri kümesiyle `Labels`karşılaştırır).</span><span class="sxs-lookup"><span data-stu-id="7767a-321">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="7767a-322">Model performans ölçümlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7767a-322">Returns the model performance metrics.</span></span>

<span data-ttu-id="7767a-323">Aşağıdaki kodu `ReuseAndTuneInceptionModel()` yöntemine sonraki satır olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-323">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="7767a-324">Aşağıdaki ölçümler görüntü sınıflandırması için değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="7767a-324">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="7767a-325">`Log-loss`- [günlük kaybını](../resources/glossary.md#log-loss)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="7767a-325">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="7767a-326">Günlük kaybını mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="7767a-326">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="7767a-327">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="7767a-327">`Per class Log-loss`.</span></span> <span data-ttu-id="7767a-328">Her sınıf günlük kaybını, mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="7767a-328">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="7767a-329">Ölçümleri göstermek, sonuçları paylaşmak ve sonra bunlar üzerinde işlem yapmak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="7767a-329">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 <span data-ttu-id="7767a-330">Eğitilen modeli sonraki satır olarak döndürmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-330">Add the following code to return the trained model as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="7767a-331">Görüntüleri yüklü bir modelle sınıflandır</span><span class="sxs-lookup"><span data-stu-id="7767a-331">Classify images with a loaded model</span></span>

<span data-ttu-id="7767a-332">`ClassifyImages()` Yöntemi`Main` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-332">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="7767a-333">`ClassifyImages()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="7767a-333">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="7767a-334">Okuma. TSV dosyasını içine `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="7767a-334">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="7767a-335">Sınama verilerine göre görüntü sınıflandırmalarını tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="7767a-335">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="7767a-336">Yöntemi, aşağıdaki kodu kullanarak yönteminden hemen `ReuseAndTuneInceptionModel()` sonra ve `PairAndDisplayResults()` yönteminden hemen önce oluşturun: `ClassifyImages()`</span><span class="sxs-lookup"><span data-stu-id="7767a-336">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="7767a-337">İlk olarak, her `ReadFromTsv()` biri `ImagePath`için tam yolu `IEnumerable<ImageData>` içeren bir sınıf oluşturmak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="7767a-337">First, call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="7767a-338">Verilerinizi ve tahmin sonuçlarınızı eşleştirmek için bu dosya yolunun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7767a-338">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="7767a-339">Ayrıca, `IEnumerable<ImageData>` öğesini tahmin etmek için kullanacağınız sınıfı bir `IDataView` öğesine dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7767a-339">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="7767a-340">Aşağıdaki kodu, `ClassifyImages()` yönteminin sonraki iki satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-340">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

<span data-ttu-id="7767a-341">Daha önce eğitim görüntü verilerinde yaptığınız gibi, geçirilen modelin [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak test görüntüsü verilerinin kategorisini tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="7767a-341">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the model passed in.</span></span> <span data-ttu-id="7767a-342">Aşağıdaki kodu `ClassifyImages()` tahmine meler için yöntemine ekleyin ve öğesini eşleştirme ve görüntüleme `IEnumerable` için `IDataView` öğesine `predictions` dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="7767a-342">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="7767a-343">Test görüntüsü verilerinizi ve tahminleri eşleştirmek ve göstermek için aşağıdaki kodu, daha önce `DisplayResults()` `ClassifyImages()` yönteminde bir sonraki satır olarak oluşturulan yöntemi çağırmak için ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-343">To pair and display your test image data and predictions, add the following code to call the `DisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="7767a-344">Yüklü bir modelle tek bir görüntüyü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7767a-344">Classify a single image with a loaded model</span></span>

<span data-ttu-id="7767a-345">`ClassifySingleImage()` Yöntemi`Main` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-345">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="7767a-346">`ClassifySingleImage()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="7767a-346">The `ClassifySingleImage()` method executes the following tasks:</span></span>

* <span data-ttu-id="7767a-347">Bir `ImageData` örnek yükler.</span><span class="sxs-lookup"><span data-stu-id="7767a-347">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="7767a-348">Test verilerine göre görüntü sınıflandırmasını tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="7767a-348">Predicts image classification based on test data.</span></span>

<span data-ttu-id="7767a-349">Yöntemi, aşağıdaki kodu kullanarak yönteminden hemen `ClassifyImages()` sonra ve `PairAndDisplayResults()` yönteminden hemen önce oluşturun: `ClassifySingleImage()`</span><span class="sxs-lookup"><span data-stu-id="7767a-349">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="7767a-350">İlk olarak, tek `ImageData` `ImagePath`için tam yolu ve resim dosyası adını içeren bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7767a-350">First, create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="7767a-351">Aşağıdaki kodu `ClassifySingleImage()` yöntemine bir sonraki satır olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-351">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="7767a-352">[PredictionEngine sınıfı](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştiren KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="7767a-352">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="7767a-353">PREDICT [()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütunu üzerinde bir tahmin yapar.</span><span class="sxs-lookup"><span data-stu-id="7767a-353">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="7767a-354">Aşağıdaki `imageData` kodu öğesine `PredictionEngine` ekleyerekgörüntükategorisinitahminetmek`ClassifySingleImage()`için öğesine geçirin:</span><span class="sxs-lookup"><span data-stu-id="7767a-354">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="7767a-355">`ClassifySingleImage()` Yöntem içindeki bir sonraki kod satırı olarak tahmin sonucunu görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="7767a-355">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="7767a-356">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="7767a-356">Results</span></span>

<span data-ttu-id="7767a-357">Önceki adımları uyguladıktan sonra konsol uygulamanızı çalıştırın (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="7767a-357">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="7767a-358">Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7767a-358">Your results should be similar to the following output.</span></span>  <span data-ttu-id="7767a-359">Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7767a-359">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="7767a-360">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="7767a-360">Congratulations!</span></span> <span data-ttu-id="7767a-361">Artık ml.net ' de önceden eğitilen `TensorFlow` bir modeli yeniden çalıştırarak görüntü sınıflandırması için bir makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="7767a-361">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="7767a-362">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7767a-362">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="7767a-363">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="7767a-363">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="7767a-364">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="7767a-364">Understand the problem</span></span>
> * <span data-ttu-id="7767a-365">Önceden eğitilen modeli yeniden kullanma ve ayarlama</span><span class="sxs-lookup"><span data-stu-id="7767a-365">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="7767a-366">Görüntüleri yüklü bir modelle sınıflandır</span><span class="sxs-lookup"><span data-stu-id="7767a-366">Classify images with a loaded model</span></span>

<span data-ttu-id="7767a-367">Genişletilmiş bir görüntü sınıflandırma örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="7767a-367">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7767a-368">DotNet/machinöğrenim-Samples GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="7767a-368">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
