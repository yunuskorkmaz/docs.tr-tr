---
title: 'Öğretici: ONNX ve ML.NET ile derin öğrenme kullanarak nesneleri Algıla'
description: Bu öğreticide, görüntülerdeki nesneleri algılamak için ML.NET ' de önceden eğitilen ONNX derin öğrenme modelinin nasıl kullanılacağı gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 08/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 1364b6a1cf6d424975828185a50175b2763c6516
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420052"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="14c30-103">Öğretici: ML.NET 'de ONNX kullanarak nesneleri algılama</span><span class="sxs-lookup"><span data-stu-id="14c30-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="14c30-104">Görüntülerdeki nesneleri saptamak için ML.NET ' de önceden eğitilen bir ONNX modeli kullanmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="14c30-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="14c30-105">Bir nesne algılama modelini sıfırdan eğitmek için milyonlarca parametre, büyük miktarda etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="14c30-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="14c30-106">Önceden eğitilen bir modelin kullanılması, eğitim sürecini kısayola etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="14c30-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="14c30-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="14c30-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="14c30-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="14c30-108">Understand the problem</span></span>
> - <span data-ttu-id="14c30-109">ONNX 'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin</span><span class="sxs-lookup"><span data-stu-id="14c30-109">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="14c30-110">Modeli anlama</span><span class="sxs-lookup"><span data-stu-id="14c30-110">Understand the model</span></span>
> - <span data-ttu-id="14c30-111">Önceden eğitilen modeli yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="14c30-111">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="14c30-112">Yüklü bir modelle nesneleri Algıla</span><span class="sxs-lookup"><span data-stu-id="14c30-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="14c30-113">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="14c30-113">Pre-requisites</span></span>

- <span data-ttu-id="14c30-114">[Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="14c30-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="14c30-115">Microsoft.ML NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="14c30-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="14c30-116">Microsoft. ML. ımageanalytics NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="14c30-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="14c30-117">Microsoft. ML. OnnxTransformer NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="14c30-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="14c30-118">Küçük YOLOv2 önceden eğitilen model</span><span class="sxs-lookup"><span data-stu-id="14c30-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- <span data-ttu-id="14c30-119">[Netron](https://github.com/lutzroeder/netron) (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="14c30-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="14c30-120">ONNX nesne algılama örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="14c30-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="14c30-121">Bu örnek, önceden eğitilen derinlemesine öğrenme ONNX modelini kullanarak bir görüntüdeki nesneleri algılayan bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14c30-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="14c30-122">Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="14c30-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="14c30-123">Nesne algılama nedir?</span><span class="sxs-lookup"><span data-stu-id="14c30-123">What is object detection?</span></span>

<span data-ttu-id="14c30-124">Nesne algılama bir bilgisayar vizyonu sorunudur.</span><span class="sxs-lookup"><span data-stu-id="14c30-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="14c30-125">Görüntü sınıflandırmasıyla yakından ilgili olarak, nesne algılama görüntü sınıflandırmasını daha ayrıntılı bir ölçekte gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="14c30-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="14c30-126">Nesne algılama hem görüntüler içindeki varlıkları bulur _hem_ de kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="14c30-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="14c30-127">Görüntüler farklı türlerde birden çok nesne içerdiğinde nesne algılamayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-127">Use object detection when images contain multiple objects of different types.</span></span>

![Resim sınıflandırmasına karşı nesne sınıflandırmasına karşı ekran görüntüleri.](./media/object-detection-onnx/img-classification-obj-detection.png)

<span data-ttu-id="14c30-129">Nesne algılama için bazı kullanım örnekleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="14c30-129">Some use cases for object detection include:</span></span>

- <span data-ttu-id="14c30-130">Kendi kendine yönlendiren otomobiller</span><span class="sxs-lookup"><span data-stu-id="14c30-130">Self-Driving Cars</span></span>
- <span data-ttu-id="14c30-131">Robotics</span><span class="sxs-lookup"><span data-stu-id="14c30-131">Robotics</span></span>
- <span data-ttu-id="14c30-132">Yüz Algılama</span><span class="sxs-lookup"><span data-stu-id="14c30-132">Face Detection</span></span>
- <span data-ttu-id="14c30-133">Çalışma alanı güvenliği</span><span class="sxs-lookup"><span data-stu-id="14c30-133">Workplace Safety</span></span>
- <span data-ttu-id="14c30-134">Nesne sayımı</span><span class="sxs-lookup"><span data-stu-id="14c30-134">Object Counting</span></span>
- <span data-ttu-id="14c30-135">Etkinlik tanıma</span><span class="sxs-lookup"><span data-stu-id="14c30-135">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="14c30-136">Derin öğrenme modeli seçin</span><span class="sxs-lookup"><span data-stu-id="14c30-136">Select a deep learning model</span></span>

<span data-ttu-id="14c30-137">Derin öğrenme, Machine Learning 'in bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="14c30-137">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="14c30-138">Derin öğrenme modellerini eğmek için, büyük miktarlarda veri gerekir.</span><span class="sxs-lookup"><span data-stu-id="14c30-138">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="14c30-139">Verilerdeki desenler, bir dizi katman tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="14c30-139">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="14c30-140">Verilerdeki ilişkiler, ağırlık içeren katmanlar arasında bağlantı olarak kodlanır.</span><span class="sxs-lookup"><span data-stu-id="14c30-140">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="14c30-141">Ağırlığa göre daha güçlü olan ilişki.</span><span class="sxs-lookup"><span data-stu-id="14c30-141">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="14c30-142">Toplu olarak, bu katman ve bağlantı serisi yapay sinir Networks olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="14c30-142">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="14c30-143">Bir ağdaki daha fazla katman, "daha derin" ve bunu derin bir sinir ağı yapıyor.</span><span class="sxs-lookup"><span data-stu-id="14c30-143">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span>

<span data-ttu-id="14c30-144">Farklı türlerde sinir Networks, en yaygın çok katmanlı Perceptron (MLP), evsel sinir ağı (CNN) ve yinelenen sinir ağı (RNN).</span><span class="sxs-lookup"><span data-stu-id="14c30-144">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="14c30-145">En temel, bir giriş kümesini bir çıktı kümesine eşleyen MLP 'dir.</span><span class="sxs-lookup"><span data-stu-id="14c30-145">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="14c30-146">Bu sinir ağı, verilerin bir uzamsal veya zaman bileşeni olmadığında iyidir.</span><span class="sxs-lookup"><span data-stu-id="14c30-146">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="14c30-147">CNN, veride bulunan uzamsal bilgileri işlemek için evsel katmanların kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="14c30-147">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="14c30-148">CNNs için iyi bir kullanım örneği, bir görüntünün bölgesindeki bir özelliğin varlığını algılamak için görüntü işleme 'dir (örneğin, bir görüntünün merkezinde bir burun mu var?).</span><span class="sxs-lookup"><span data-stu-id="14c30-148">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="14c30-149">Son olarak, RNNs durum veya belleğin girdi olarak kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="14c30-149">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="14c30-150">RNNs, sıralı sıralama ve olayların bağlamı önemli olduğu zaman serisi analizi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14c30-150">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span>

### <a name="understand-the-model"></a><span data-ttu-id="14c30-151">Modeli anlama</span><span class="sxs-lookup"><span data-stu-id="14c30-151">Understand the model</span></span>

<span data-ttu-id="14c30-152">Nesne algılama bir görüntü işleme görevidir.</span><span class="sxs-lookup"><span data-stu-id="14c30-152">Object detection is an image processing task.</span></span> <span data-ttu-id="14c30-153">Bu nedenle, bu sorunu çözmek için eğitilen çoğu derin öğrenme modeli CNNs ' dir.</span><span class="sxs-lookup"><span data-stu-id="14c30-153">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="14c30-154">Bu öğreticide kullanılan model, YOLOv2 modelinin ["YOLO9000: daha iyi, daha hızlı, daha güçlü" ve Redmon ve Fadhari tarafından](https://arxiv.org/pdf/1612.08242.pdf)tanımlanan daha küçük bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="14c30-154">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="14c30-155">Küçük YOLOv2, Pascal VOC veri kümesi üzerinde eğitilir ve 20 farklı nesne sınıfı tahmin edebilen 15 katmandan oluşur.</span><span class="sxs-lookup"><span data-stu-id="14c30-155">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="14c30-156">Küçük YOLOv2 özgün YOLOv2 modelinin sıkıştırılmış bir sürümü olduğundan, hız ve doğruluk arasında bir zorunluluğunu getirir yapılır.</span><span class="sxs-lookup"><span data-stu-id="14c30-156">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="14c30-157">Modeli oluşturan farklı katmanlar netron gibi araçlar kullanılarak görselleştirilir.</span><span class="sxs-lookup"><span data-stu-id="14c30-157">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="14c30-158">Modelin araştırılama, her katmanın, ilgili giriş/çıkış boyutlarıyla birlikte katman adını içerdiği sinir ağını oluşturan tüm katmanlar arasında bağlantı eşlemesini elde edecektir.</span><span class="sxs-lookup"><span data-stu-id="14c30-158">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="14c30-159">Modelin girişlerini ve çıkışlarını tanımlamakta kullanılan veri yapıları, teniler olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="14c30-159">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="14c30-160">Teniler, verileri N boyutlu bir şekilde depolayan kapsayıcılar olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="14c30-160">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="14c30-161">Küçük YOLOv2 durumunda, giriş katmanının adı `image` ' dır ve `3 x 416 x 416` ' de bir boyut kullanımını bekler.</span><span class="sxs-lookup"><span data-stu-id="14c30-161">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="14c30-162">Çıkış katmanının adı `grid` ' dır ve `125 x 13 x 13` boyutları için bir çıktı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14c30-162">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>

![Gizli katmanlara bölünmekte olan giriş katmanı, çıkış katmanı](./media/object-detection-onnx/netron-model-map-layers.png)

<span data-ttu-id="14c30-164">YOLO modeli bir görüntü `3(RGB) x 416px x 416px` alır.</span><span class="sxs-lookup"><span data-stu-id="14c30-164">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="14c30-165">Model bu girişi alır ve bir çıktı üretmek için farklı katmanlardan geçirir.</span><span class="sxs-lookup"><span data-stu-id="14c30-165">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="14c30-166">Çıktı, giriş görüntüsünü, kılavuzda `125` değerlerinden oluşan her hücreyle birlikte `13 x 13` kılavuzuna böler.</span><span class="sxs-lookup"><span data-stu-id="14c30-166">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span>

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="14c30-167">ONNX modeli nedir?</span><span class="sxs-lookup"><span data-stu-id="14c30-167">What is an ONNX model?</span></span>

<span data-ttu-id="14c30-168">Open sinir Network Exchange (ONNX), AI modelleri için açık kaynak biçimidir.</span><span class="sxs-lookup"><span data-stu-id="14c30-168">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="14c30-169">ONNX çerçeveler arasında birlikte çalışabilirliği destekler.</span><span class="sxs-lookup"><span data-stu-id="14c30-169">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="14c30-170">Bu, bir modeli PyTorch gibi birçok popüler makine öğrenimi çerçevelerinden birinde eğitebileceğiniz anlamına gelir, ONNX biçimine dönüştürebilir ve ML.NET gibi farklı bir çerçevede ONNX modelini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14c30-170">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="14c30-171">Daha fazla bilgi edinmek için [Onnx Web sitesini](https://onnx.ai/)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="14c30-171">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span>

![Kullanılan ONNX desteklenen biçimlerin diyagramı.](./media/object-detection-onnx/onyx-supported-formats.png)

<span data-ttu-id="14c30-173">Önceden eğitilen küçük YOLOv2 modeli, katmanların serileştirilmiş bir gösterimi ve bu katmanların öğrenilen desenleri ile ONNX biçiminde depolanır.</span><span class="sxs-lookup"><span data-stu-id="14c30-173">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="14c30-174">ML.NET ' de, ONNX ile birlikte çalışabilirlik [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) ve [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet paketleriyle elde edilir.</span><span class="sxs-lookup"><span data-stu-id="14c30-174">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="14c30-175">[`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) paketi bir görüntü alıp bir tahmin veya eğitim işlem hattına giriş olarak kullanılabilecek sayısal değerlere kodlayan bir dizi dönüştürme içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-175">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="14c30-176">[`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) paketi Onnx çalışma zamanından yararlanır ve belirtilen girişe göre tahmine dayalı hale getirmek için bu modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="14c30-176">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span>

![ONNX dosyasının ONNX çalışma zamanına veri akışı.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="14c30-178">.NET Core projesini ayarlama</span><span class="sxs-lookup"><span data-stu-id="14c30-178">Set up the .NET Core project</span></span>

<span data-ttu-id="14c30-179">Artık ONNX 'in ne olduğuna ve küçük YOLOv2 nasıl çalıştığına ilişkin genel bir bilgiye sahip olduğunuza göre, uygulamanın derlenmesi zaman vardır.</span><span class="sxs-lookup"><span data-stu-id="14c30-179">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="14c30-180">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="14c30-180">Create a console application</span></span>

1. <span data-ttu-id="14c30-181">"ObjectDetection" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-181">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="14c30-182">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="14c30-182">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="14c30-183">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-183">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    - <span data-ttu-id="14c30-184">Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="14c30-184">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    - <span data-ttu-id="14c30-185">**Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-185">Select the **Install** button.</span></span>
    - <span data-ttu-id="14c30-186">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-186">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    - <span data-ttu-id="14c30-187">**Microsoft. ml. ımageanalytics** ve **Microsoft. ml. OnnxTransformer**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-187">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="14c30-188">Verilerinizi hazırlayın ve önceden eğitilen modeli</span><span class="sxs-lookup"><span data-stu-id="14c30-188">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="14c30-189">[Proje Varlıkları Dizin ZIP dosyasını](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) indirin ve sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="14c30-189">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="14c30-190">`assets` dizinini *Objectdetection* proje dizininize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-190">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="14c30-191">Bu dizin ve alt dizinleri, bu öğretici için gerekli olan resim dosyalarını (küçük YOLOv2 modeli dışında, indirecek ve sonraki adımda ekleyeceğiniz) içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-191">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="14c30-192">[Onnx model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)ve unzip 'Ten [küçük YOLOv2 modelini](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) indirin.</span><span class="sxs-lookup"><span data-stu-id="14c30-192">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="14c30-193">Komut istemi ' ni açın ve şu komutu girin:</span><span class="sxs-lookup"><span data-stu-id="14c30-193">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. <span data-ttu-id="14c30-194">Ayıklanan `model.onnx` dosyasını Dizin içinden *Objectdetection* proje `assets\Model` dizinine kopyalayın ve `TinyYolo2_model.onnx`olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="14c30-194">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="14c30-195">Bu dizin, bu öğretici için gereken modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-195">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="14c30-196">Çözüm Gezgini, varlık dizinindeki ve alt dizinlerde bulunan dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-196">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="14c30-197">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="14c30-197">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="14c30-198">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="14c30-198">Create classes and define paths</span></span>

<span data-ttu-id="14c30-199">*Program.cs* dosyasını açın ve aşağıdaki ek `using` deyimlerini dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-199">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

<span data-ttu-id="14c30-200">Ardından, çeşitli varlıkların yollarını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-200">Next, define the paths of the various assets.</span></span>

1. <span data-ttu-id="14c30-201">İlk olarak, `Program` sınıfındaki `Main` yönteminin altına `GetAbsolutePath` yöntemini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-201">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span>

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="14c30-202">Ardından, `Main` yönteminin içinde, varlıklarınızın konumunu depolamak için alanlar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-202">Then, inside the `Main` method, create fields to store the location of your assets.</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="14c30-203">Giriş verilerinizi ve tahmin sınıflarınızı depolamak için projenize yeni bir dizin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-203">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="14c30-204">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-204">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="14c30-205">Yeni klasör Çözüm Gezgini göründüğünde, "Datayapýlarý" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="14c30-205">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="14c30-206">Yeni oluşturulan *Datayapýlarý* dizininde giriş veri sınıfınızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-206">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="14c30-207">**Çözüm Gezgini**, *datayapýlarý* dizinine sağ tıklayın ve sonra **Ekle** > **Yeni öğe**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-207">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="14c30-208">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ImageNetData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="14c30-208">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="14c30-209">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-209">Then, select the **Add** button.</span></span>

    <span data-ttu-id="14c30-210">*ImageNetData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="14c30-210">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="14c30-211">Aşağıdaki `using` ifadesini *ImageNetData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-211">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="14c30-212">Mevcut sınıf tanımını kaldırın ve `ImageNetData` sınıfı için aşağıdaki kodu *ImageNetData.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-212">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="14c30-213">`ImageNetData`, giriş resmi veri sınıfıdır ve aşağıdaki <xref:System.String> alanlarına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="14c30-213">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="14c30-214">`ImagePath`, görüntünün depolandığı yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-214">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="14c30-215">`Label` dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-215">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="14c30-216">Ayrıca, `ImageNetData`, belirtilen `imageFolder` yolunda depolanan birden çok görüntü dosyasını yükleyen ve bunları `ImageNetData` nesnelerinin bir koleksiyonu olarak döndüren bir yöntem `ReadFromFile` ' i içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-216">Additionally, `ImageNetData` contains a method `ReadFromFile` which loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="14c30-217">*Veri yapıları* dizininde tahmin sınıfınızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-217">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="14c30-218">**Çözüm Gezgini**, *datayapýlarý* dizinine sağ tıklayın ve sonra **Ekle** > **Yeni öğe**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-218">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="14c30-219">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ImageNetPrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="14c30-219">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="14c30-220">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-220">Then, select the **Add** button.</span></span>

    <span data-ttu-id="14c30-221">*ImageNetPrediction.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="14c30-221">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="14c30-222">Aşağıdaki `using` ifadesini *ImageNetPrediction.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-222">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="14c30-223">Mevcut sınıf tanımını kaldırın ve `ImageNetPrediction` sınıfı için aşağıdaki kodu *ImageNetPrediction.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-223">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="14c30-224">`ImageNetPrediction`, tahmin verileri sınıfıdır ve aşağıdaki `float[]` alanına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="14c30-224">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="14c30-225">`PredictedLabel`, görüntüde algılanan her bir sınırlayıcı kutu için boyut, objectlik puanı ve sınıf olasılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-225">`PredictedLabel` contains the dimensions, objectness score and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="14c30-226">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="14c30-226">Initialize variables in Main</span></span>

<span data-ttu-id="14c30-227">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve `mlContext` başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14c30-227">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="14c30-228">Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="14c30-228">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="14c30-229">`outputFolder` alanının altındaki *Program.cs* `Main` yöntemine aşağıdaki satırı ekleyerek `mlContext` değişkenini yeni bir `MLContext` örneğiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="14c30-229">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="14c30-230">İşlem sonrası model çıkışları için bir Ayrıştırıcı oluşturun</span><span class="sxs-lookup"><span data-stu-id="14c30-230">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="14c30-231">Model, her kılavuz hücresinin `32px x 32px` olduğu bir görüntüyü `13 x 13` kılavuzuna böler.</span><span class="sxs-lookup"><span data-stu-id="14c30-231">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="14c30-232">Her kılavuz hücresi, 5 olası nesne sınırlayıcı kutusu içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-232">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="14c30-233">Bir sınırlayıcı kutusunda 25 öğe vardır:</span><span class="sxs-lookup"><span data-stu-id="14c30-233">A bounding box has  25 elements:</span></span>

![Sol taraftaki kılavuz örneği ve sağ taraftaki sınırlayıcı kutu örneği](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="14c30-235">`x`, sınırlama kutusu merkezinin ilişkilendirildiği kılavuz hücresine göre x konumudur.</span><span class="sxs-lookup"><span data-stu-id="14c30-235">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="14c30-236">`y` sınırlayıcı kutu merkezinin ilişkilendirildiği kılavuz hücresine göre y konumu.</span><span class="sxs-lookup"><span data-stu-id="14c30-236">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="14c30-237">`w` sınırlayıcı kutunun genişliği.</span><span class="sxs-lookup"><span data-stu-id="14c30-237">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="14c30-238">`h` sınırlayıcı kutunun yüksekliği.</span><span class="sxs-lookup"><span data-stu-id="14c30-238">`h` the height of the bounding box.</span></span>
- <span data-ttu-id="14c30-239">`o` bir nesnenin sınırlayıcı kutu içinde var olduğu, aynı zamanda objectlık puanı olarak da bilinen güvenirlik değeri.</span><span class="sxs-lookup"><span data-stu-id="14c30-239">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="14c30-240">model tarafından tahmin edilen 20 sınıfın her biri için `p1-p20` sınıfı olasılıkların.</span><span class="sxs-lookup"><span data-stu-id="14c30-240">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="14c30-241">Toplamda, 5 sınırlayıcı kutulardan her birini tanımlayan 25 öğe, her kılavuz hücresinde bulunan 125 öğelerini yapar.</span><span class="sxs-lookup"><span data-stu-id="14c30-241">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="14c30-242">Önceden eğitilen ONNX modeli tarafından oluşturulan çıkış, `21125` uzunluğunda bir float dizisidir ve `125 x 13 x 13` boyutları ile bir ön sor öğelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="14c30-242">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="14c30-243">Model tarafından oluşturulan tahminleri bir tencursor 'a dönüştürmek için bazı işleme sonrası işler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="14c30-243">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="14c30-244">Bunu yapmak için, çıktıyı ayrıştırmaya yardımcı olmak üzere bir sınıf kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-244">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="14c30-245">Ayrıştırıcı sınıfları kümesini düzenlemek için projenize yeni bir dizin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-245">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="14c30-246">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-246">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="14c30-247">Yeni klasör Çözüm Gezgini göründüğünde, "YoloParser" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="14c30-247">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="14c30-248">Sınırlayıcı kutular ve boyutlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="14c30-248">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="14c30-249">Modelin veri çıktısı, görüntü içindeki nesnelerin sınırlayıcı kutularının koordinatlarını ve boyutlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-249">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="14c30-250">Boyutlar için bir temel sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-250">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="14c30-251">**Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra  > **Yeni öğe** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-251">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="14c30-252">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *DimensionsBase.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="14c30-252">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="14c30-253">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-253">Then, select the **Add** button.</span></span>

    <span data-ttu-id="14c30-254">*DimensionsBase.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="14c30-254">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="14c30-255">Tüm `using` deyimlerini ve var olan sınıf tanımını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="14c30-255">Remove all `using` statements and existing class definition.</span></span>

    <span data-ttu-id="14c30-256">`DimensionsBase` sınıfı için aşağıdaki kodu *DimensionsBase.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-256">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="14c30-257">`DimensionsBase` aşağıdaki `float` alanlarına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="14c30-257">`DimensionsBase` has the following `float` fields:</span></span>

    - <span data-ttu-id="14c30-258">`X`, nesnenin konumunu x ekseni üzerinde içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-258">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="14c30-259">`Y`, nesnenin y ekseni üzerinde konumunu içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-259">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="14c30-260">`Height` nesnenin yüksekliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-260">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="14c30-261">`Width` nesnenin genişliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-261">`Width` contains the width of the object.</span></span>

<span data-ttu-id="14c30-262">Ardından, sınırlayıcı kutularınız için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-262">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="14c30-263">**Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra  > **Yeni öğe** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-263">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="14c30-264">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *YoloBoundingBox.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="14c30-264">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="14c30-265">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-265">Then, select the **Add** button.</span></span>

    <span data-ttu-id="14c30-266">*YoloBoundingBox.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="14c30-266">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="14c30-267">Aşağıdaki `using` ifadesini *YoloBoundingBox.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-267">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="14c30-268">Mevcut sınıf tanımının hemen üstünde, ilgili sınırlayıcı kutunun boyutlarını içermesi için `DimensionsBase` sınıfından devralan `BoundingBoxDimensions` adlı yeni bir sınıf tanımı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-268">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` which inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="14c30-269">Var olan `YoloBoundingBox` sınıf tanımını kaldırın ve *YoloBoundingBox.cs* dosyasına `YoloBoundingBox` sınıfı için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-269">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    <span data-ttu-id="14c30-270">`YoloBoundingBox` aşağıdaki alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="14c30-270">`YoloBoundingBox` has the following fields:</span></span>

    - <span data-ttu-id="14c30-271">`Dimensions`, sınırlayıcı kutunun boyutlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-271">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="14c30-272">`Label` ' ın sınırlayıcı kutusunda algılanan nesne sınıfını içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-272">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="14c30-273">`Confidence` sınıfının güvenini içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-273">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="14c30-274">`Rect`, sınırlayıcı kutunun boyutlarının dikdörtgen gösterimini içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-274">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="14c30-275">`BoxColor`, görüntüde çizmek için kullanılan ilgili sınıfla ilişkili rengi içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-275">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="14c30-276">Ayrıştırıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="14c30-276">Create the parser</span></span>

<span data-ttu-id="14c30-277">Artık boyut ve sınırlama kutuları için sınıflar oluşturuldığına göre, ayrıştırıcısı oluşturma zamanı.</span><span class="sxs-lookup"><span data-stu-id="14c30-277">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="14c30-278">**Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra  > **Yeni öğe** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-278">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="14c30-279">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *YoloOutputParser.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="14c30-279">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="14c30-280">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-280">Then, select the **Add** button.</span></span>

    <span data-ttu-id="14c30-281">*YoloOutputParser.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="14c30-281">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="14c30-282">Aşağıdaki `using` ifadesini *YoloOutputParser.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-282">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="14c30-283">Var olan `YoloOutputParser` sınıf tanımının içinde, görüntüdeki her bir hücrenin boyutlarını içeren bir iç içe sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-283">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="14c30-284">`YoloOutputParser` sınıf tanımının en üstündeki `DimensionsBase` sınıfından devralan `CellDimensions` sınıfı için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-284">Add the following code for the `CellDimensions` class which inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="14c30-285">`YoloOutputParser` sınıf tanımı içinde aşağıdaki sabiti ve alanları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-285">Inside the `YoloOutputParser` class definition, add the following constant and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - <span data-ttu-id="14c30-286">`ROW_COUNT`, görüntüde bölünen, kılavuzdaki satır sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="14c30-286">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="14c30-287">`COL_COUNT`, görüntünün bölüneceğini belirten Izgaradaki sütun sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="14c30-287">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="14c30-288">`CHANNEL_COUNT`, kılavuzun tek bir hücresinde bulunan toplam değer sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="14c30-288">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="14c30-289">`BOXES_PER_CELL`, bir hücredeki sınırlayıcı kutuların sayısıdır,</span><span class="sxs-lookup"><span data-stu-id="14c30-289">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="14c30-290">`BOX_INFO_FEATURE_COUNT`, bir kutu içinde (x, y, Height, Width, güvenirlik) bulunan özelliklerin sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="14c30-290">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="14c30-291">`CLASS_COUNT`, her bir sınırlayıcı kutusunda bulunan sınıf tahminleri sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="14c30-291">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="14c30-292">`CELL_WIDTH`, görüntü kılavuzundaki bir hücrenin genişliğidir.</span><span class="sxs-lookup"><span data-stu-id="14c30-292">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="14c30-293">`CELL_HEIGHT`, görüntü kılavuzundaki bir hücrenin yüksekliğidir.</span><span class="sxs-lookup"><span data-stu-id="14c30-293">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="14c30-294">`channelStride`, kılavuzdaki geçerli hücrenin başlangıç konumudur.</span><span class="sxs-lookup"><span data-stu-id="14c30-294">`channelStride` is the starting position of the current cell in the grid.</span></span>

    <span data-ttu-id="14c30-295">Model, Puanlama olarak da bilinen bir tahmin yaptığında, `416px x 416px` giriş görüntüsünü `13 x 13` boyutundaki bir hücre kılavuzuna böler.</span><span class="sxs-lookup"><span data-stu-id="14c30-295">When the model makes a prediction, also known as scoring, it divides the `416px x 416px` input image into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="14c30-296">Her hücre içeren `32px x 32px` ' dır.</span><span class="sxs-lookup"><span data-stu-id="14c30-296">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="14c30-297">Her hücrede, 5 Özellik (x, y, Width, Height, güvenirlik) içeren 5 sınırlayıcı kutu vardır.</span><span class="sxs-lookup"><span data-stu-id="14c30-297">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="14c30-298">Ayrıca, her sınırlayıcı kutu, bu örnekte 20 olan her bir sınıf olasılığını içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-298">In addition, each bounding box contains the probability of each of the classes which in this case is 20.</span></span> <span data-ttu-id="14c30-299">Bu nedenle, her hücre 125 bilgi parçasını içerir (5 özellik + 20 sınıf olasılıkların).</span><span class="sxs-lookup"><span data-stu-id="14c30-299">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span>

<span data-ttu-id="14c30-300">Tüm 5 sınırlayıcı kutular için `channelStride` ' ın altına bir çıpası listesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="14c30-300">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

<span data-ttu-id="14c30-301">Bağlayıcıların sınırlayıcı kutuların önceden tanımlanmış yükseklik ve genişlik oranları vardır.</span><span class="sxs-lookup"><span data-stu-id="14c30-301">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="14c30-302">Bir model tarafından algılanan çoğu nesne veya sınıfın benzer oranları vardır.</span><span class="sxs-lookup"><span data-stu-id="14c30-302">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="14c30-303">Bu, sınırlayıcı kutular oluşturmak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="14c30-303">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="14c30-304">Sınırlayıcı kutuları tahmin etmek yerine, önceden tanımlanmış boyutlardan olan fark, bu nedenle, sınırlayıcı kutuyu tahmin etmek için gereken hesaplamayı azaltmak için hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="14c30-304">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="14c30-305">Genellikle bu bağlantı oranları, kullanılan veri kümesi temel alınarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="14c30-305">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="14c30-306">Bu durumda, veri kümesi bilindiği ve değerler önceden hesaplandığından, bağlantılar sabit kodlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="14c30-306">In this case because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="14c30-307">Ardından, modelin tahmin edecek etiketleri veya sınıfları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-307">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="14c30-308">Bu model, özgün YOLOv2 modeli tarafından tahmin edilen toplam sınıf sayısının bir alt kümesi olan 20 sınıfı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="14c30-308">This model predicts 20 classes which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="14c30-309">`anchors`altına etiket listenizi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-309">Add your list of labels below the `anchors`.</span></span>

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="14c30-310">Sınıfların her biriyle ilişkili renkler vardır.</span><span class="sxs-lookup"><span data-stu-id="14c30-310">There are colors associated with each of the classes.</span></span> <span data-ttu-id="14c30-311">Sınıf renklerinizi `labels` altına atayın:</span><span class="sxs-lookup"><span data-stu-id="14c30-311">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="14c30-312">Yardımcı işlevler oluşturma</span><span class="sxs-lookup"><span data-stu-id="14c30-312">Create helper functions</span></span>

<span data-ttu-id="14c30-313">İşleme sonrası aşamasında yer alan bir dizi adım vardır.</span><span class="sxs-lookup"><span data-stu-id="14c30-313">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="14c30-314">Bu konuda yardımcı olmak için birkaç yardımcı yöntem kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="14c30-314">To help with that, several helper methods can be employed.</span></span>

<span data-ttu-id="14c30-315">Ayrıştırıcı tarafından kullanılan yardımcı yöntemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="14c30-315">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="14c30-316">`Sigmoid`, 0 ile 1 arasında bir sayı çıkışı yapan sigmoıd işlevini uygular.</span><span class="sxs-lookup"><span data-stu-id="14c30-316">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="14c30-317">`Softmax`, bir giriş vektörünü bir olasılık dağıtımına normalleştirir.</span><span class="sxs-lookup"><span data-stu-id="14c30-317">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="14c30-318">`GetOffset`, tek boyutlu model çıkışındaki öğeleri bir `125 x 13 x 13` önplanda karşılık gelen konuma eşler.</span><span class="sxs-lookup"><span data-stu-id="14c30-318">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="14c30-319">`ExtractBoundingBoxes`, model çıktısından `GetOffset` yöntemini kullanarak sınırlayıcı kutu boyutlarını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="14c30-319">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="14c30-320">`GetConfidence`, modelin bir nesne algıladığı ve bir yüzdeye dönüştürmek için `Sigmoid` işlevini kullandığından emin olan güvenirlik değerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="14c30-320">`GetConfidence` extracts the confidence value which states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="14c30-321">`MapBoundingBoxToCell` sınırlayıcı kutu boyutlarını kullanır ve bunları görüntünün içindeki ilgili hücresiyle eşler.</span><span class="sxs-lookup"><span data-stu-id="14c30-321">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="14c30-322">`ExtractClasses`, `GetOffset` yöntemini kullanarak model çıktısından sınırlama kutusu için sınıf tahminlerini ayıklar ve `Softmax` yöntemini kullanarak bunları bir olasılık dağıtımına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="14c30-322">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="14c30-323">`GetTopResult`, en yüksek olasılığa sahip tahmin edilen sınıflar listesinden sınıfı seçer.</span><span class="sxs-lookup"><span data-stu-id="14c30-323">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="14c30-324">`IntersectionOverUnion`, daha düşük olasılıklara sahip sınırlayıcı kutularla çakışarak filtreler.</span><span class="sxs-lookup"><span data-stu-id="14c30-324">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="14c30-325">`classColors`listenizin altındaki tüm yardımcı yöntemleri için kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-325">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="14c30-326">Tüm yardımcı yöntemlerini tanımladıktan sonra, model çıkışını işlemek için bunları kullanma zamanı da vardır.</span><span class="sxs-lookup"><span data-stu-id="14c30-326">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="14c30-327">`IntersectionOverUnion` yönteminin altında, model tarafından oluşturulan çıktıyı işlemek için `ParseOutputs` metodunu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-327">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

<span data-ttu-id="14c30-328">Sınırlayıcı kutularınızı depolamak ve `ParseOutputs` yöntemi içinde değişkenleri tanımlamak için bir liste oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-328">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="14c30-329">Her görüntü, `13 x 13` hücrelerinin bir kılavuza bölünmüştür.</span><span class="sxs-lookup"><span data-stu-id="14c30-329">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="14c30-330">Her hücrede beş sınırlayıcı kutu bulunur.</span><span class="sxs-lookup"><span data-stu-id="14c30-330">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="14c30-331">`boxes` değişkeninin altında, her hücrenin içindeki tüm kutuları işlemek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-331">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

<span data-ttu-id="14c30-332">En içteki döngünün içinde, tek boyutlu model çıkışı içindeki geçerli kutunun başlangıç konumunu hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-332">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="14c30-333">Bundan hemen sonra, geçerli sınırlayıcı kutusunun boyutlarını almak için `ExtractBoundingBoxDimensions` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-333">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="14c30-334">Ardından, geçerli sınırlayıcı kutusunun güvenini almak için `GetConfidence` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-334">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="14c30-335">Bundan sonra, geçerli sınırlayıcı kutuyu işlenmekte olan geçerli hücreyle eşlemek için `MapBoundingBoxToCell` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-335">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="14c30-336">Daha fazla işlem yapmadan önce, güven değerinin sağlanan eşikten büyük olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="14c30-336">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="14c30-337">Aksi takdirde, sonraki sınırlayıcı kutuyu işleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-337">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="14c30-338">Aksi takdirde, çıktıyı işlemeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="14c30-338">Otherwise, continue processing the output.</span></span> <span data-ttu-id="14c30-339">Sonraki adım, `ExtractClasses` yöntemi kullanılarak geçerli sınırlayıcı kutu için tahmin edilen sınıfların olasılık dağılımını almaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="14c30-339">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="14c30-340">Ardından, geçerli kutu için en yüksek olasılığa sahip sınıfın değerini ve dizinini almak için `GetTopResult` yöntemini kullanın ve Puanını hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-340">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="14c30-341">`topScore` yalnızca belirtilen eşiğin üzerinde olan sınırlayıcı kutuları bir kez daha bırakmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-341">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="14c30-342">Son olarak, geçerli sınırlayıcı kutusu eşiği aşarsa, yeni bir `BoundingBox` nesnesi oluşturun ve `boxes` listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-342">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="14c30-343">Görüntüdeki tüm hücreler işlendikten sonra `boxes` listesini döndürün.</span><span class="sxs-lookup"><span data-stu-id="14c30-343">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="14c30-344">Aşağıdaki return ifadesini `ParseOutputs` metoduna en dıştaki for-Loop altına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-344">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="14c30-345">Çakışan kutuları filtrele</span><span class="sxs-lookup"><span data-stu-id="14c30-345">Filter overlapping boxes</span></span>

<span data-ttu-id="14c30-346">Artık yüksek oranda uygun sınırlama kutularının tümü model çıktısından ayıklandığına göre, çakışan görüntüleri kaldırmak için ek filtrelemenin yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="14c30-346">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="14c30-347">`ParseOutputs` yönteminin altına `FilterBoundingBoxes` adlı bir yöntem ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-347">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="14c30-348">`FilterBoundingBoxes` yöntemi içinde, algılanan kutuların boyutuna eşit bir dizi oluşturarak ve tüm yuvaları etkin veya işleme için hazırlanma olarak işaretleyerek devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="14c30-348">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="14c30-349">Ardından, sınırlayıcı kutularınızı içeren listeyi güvenle azalan sırada sıralayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-349">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="14c30-350">Bundan sonra filtrelenmiş sonuçları tutacak bir liste oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-350">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="14c30-351">Her bir sınırlayıcı kutunun her biri üzerinde yinelenerek her bir sınırlayıcı kutuyu işlemeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-351">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="14c30-352">Bu for-döngüsünün içinde, geçerli sınırlayıcı kutusunun işlenip işlenemeyeceğini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="14c30-352">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{

}
```

<span data-ttu-id="14c30-353">Bu durumda, sınırlama kutusunu sonuçlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-353">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="14c30-354">Sonuçlar Ayıklanacak belirlenen kutu sınırını aşarsa döngüyü sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="14c30-354">If the results exceeds the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="14c30-355">Aşağıdaki kodu if-deyimin içine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-355">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="14c30-356">Aksi takdirde, bitişik sınırlayıcı kutulara bakın.</span><span class="sxs-lookup"><span data-stu-id="14c30-356">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="14c30-357">Aşağıdaki kodu Box limit denetiminin altına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-357">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="14c30-358">İlk kutu gibi, bitişik kutu etkin veya işlenmek üzere hazırsanız, ilk kutunun ve ikinci kutunun belirtilen eşiği aşıp aşmadığını denetlemek için `IntersectionOverUnion` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-358">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="14c30-359">Aşağıdaki kodu, en son for-loop ' a ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-359">Add the following code to your inner-most for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="14c30-360">Bitişik sınırlayıcı kutuları denetleyen en büyük for-Loop dışında, işlenmek üzere kalan herhangi bir sınırlama kutusu olup olmadığına bakın.</span><span class="sxs-lookup"><span data-stu-id="14c30-360">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="14c30-361">Aksi takdirde, için dış döngüden çıkar.</span><span class="sxs-lookup"><span data-stu-id="14c30-361">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="14c30-362">Son olarak, `FilterBoundingBoxes` yönteminin ilk döngüsü dışında, sonuçları döndürür:</span><span class="sxs-lookup"><span data-stu-id="14c30-362">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="14c30-363">Alanları!</span><span class="sxs-lookup"><span data-stu-id="14c30-363">Great!</span></span> <span data-ttu-id="14c30-364">Artık bu kodu Puanlama modeliyle birlikte kullanmanın zamanı.</span><span class="sxs-lookup"><span data-stu-id="14c30-364">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="14c30-365">Puanlama için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="14c30-365">Use the model for scoring</span></span>

<span data-ttu-id="14c30-366">İşlem sonrasında olduğu gibi, Puanlama adımlarında birkaç adım vardır.</span><span class="sxs-lookup"><span data-stu-id="14c30-366">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="14c30-367">Bu konuda yardım almak için, projenize Puanlama mantığını içerecek bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-367">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="14c30-368">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-368">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="14c30-369">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *OnnxModelScorer.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="14c30-369">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="14c30-370">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="14c30-370">Then, select the **Add** button.</span></span>

    <span data-ttu-id="14c30-371">*OnnxModelScorer.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="14c30-371">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="14c30-372">Aşağıdaki `using` ifadesini *OnnxModelScorer.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="14c30-372">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="14c30-373">`OnnxModelScorer` sınıf tanımı içinde aşağıdaki değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-373">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="14c30-374">Bundan sonra, daha önce tanımlanmış değişkenleri başlatacak `OnnxModelScorer` sınıfı için bir Oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-374">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="14c30-375">Oluşturucuyu oluşturduktan sonra, görüntü ve model ayarlarıyla ilgili değişkenleri içeren birkaç yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-375">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="14c30-376">Model için girdi olarak beklenen yüksekliği ve genişliği içeren `ImageNetSettings` adlı bir yapı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-376">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="14c30-377">Bundan sonra, modelin giriş ve çıkış katmanlarının adlarını içeren `TinyYoloModelSettings` adlı başka bir yapı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-377">After that, create another struct called `TinyYoloModelSettings` which contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="14c30-378">Modelin giriş ve çıkış katmanlarının adını görselleştirmek için, [netron](https://github.com/lutzroeder/netron)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14c30-378">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="14c30-379">Ardından, Puanlama için kullanılan ilk yöntem kümesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-379">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="14c30-380">`OnnxModelScorer` sınıfınızın içinde `LoadModel` yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-380">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="14c30-381">`LoadModel` yönteminin içinde günlüğe kaydetmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-381">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="14c30-382">ML.NET işlem hatları [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) yöntemi çağrıldığında üzerinde çalışılacak veri şemasını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="14c30-382">ML.NET pipelines need to know the data schema to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="14c30-383">Bu durumda, eğitimle benzer bir süreç kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="14c30-383">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="14c30-384">Ancak, hiçbir gerçek eğitim gerçekleşmediğinden boş bir [`IDataView`](xref:Microsoft.ML.IDataView)kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="14c30-384">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="14c30-385">Boş bir listeden işlem hattı için yeni bir [`IDataView`](xref:Microsoft.ML.IDataView) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-385">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    <span data-ttu-id="14c30-386">Bunun altında, işlem hattını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-386">Below that, define the pipeline.</span></span> <span data-ttu-id="14c30-387">İşlem hattı dört dönüşümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="14c30-387">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="14c30-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) görüntüyü bir bit eşlem olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="14c30-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="14c30-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) görüntüyü belirtilen boyuta ölçeklendirin (Bu durumda, `416 x 416`).</span><span class="sxs-lookup"><span data-stu-id="14c30-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="14c30-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) görüntünün piksel gösterimini bir bit eşlemden sayısal bir Vector öğesine değiştirir.</span><span class="sxs-lookup"><span data-stu-id="14c30-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="14c30-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) onnx modelini yükler ve belirtilen verileri öğrenmek için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="14c30-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="14c30-392">`data` değişkeninin altındaki `LoadModel` yönteminde işlem hattınızı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-392">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="14c30-393">Şimdi Puanlama için model oluşturma zamanı.</span><span class="sxs-lookup"><span data-stu-id="14c30-393">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="14c30-394">İşlem hattında [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) metodunu çağırın ve daha fazla işleme için döndürün.</span><span class="sxs-lookup"><span data-stu-id="14c30-394">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="14c30-395">Model yüklendikten sonra tahmin yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="14c30-395">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="14c30-396">Bu işlemi kolaylaştırmak için `LoadModel` yönteminin altında `PredictDataUsingModel` adlı bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-396">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="14c30-397">`PredictDataUsingModel`içinde günlüğe kaydetmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-397">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="14c30-398">Ardından, verileri öğrenmek için [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-398">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="14c30-399">Tahmin edilen olasılıkların ayıklanmasını ayıklayın ve bunları ek işleme için geri döndürün.</span><span class="sxs-lookup"><span data-stu-id="14c30-399">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="14c30-400">Her iki adım de ayarlandığına göre, bunları tek bir yöntemde birleştirin.</span><span class="sxs-lookup"><span data-stu-id="14c30-400">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="14c30-401">`PredictDataUsingModel` yönteminin altında `Score`adlı yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-401">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="14c30-402">Neredeyse bitti!</span><span class="sxs-lookup"><span data-stu-id="14c30-402">Almost there!</span></span> <span data-ttu-id="14c30-403">Şimdi bunu tüm kullanıma yerleştirme zamanı.</span><span class="sxs-lookup"><span data-stu-id="14c30-403">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="14c30-404">Nesneleri Algıla</span><span class="sxs-lookup"><span data-stu-id="14c30-404">Detect objects</span></span>

<span data-ttu-id="14c30-405">Tüm kurulumun tamamlandığına göre, bazı nesneleri algılamaya zaman atalım.</span><span class="sxs-lookup"><span data-stu-id="14c30-405">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="14c30-406">*Program.cs* sınıfınıza scorer ve ayrıştırıcıya başvurular ekleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-406">Start off by adding references to the scorer and parser in your *Program.cs* class.</span></span>

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a><span data-ttu-id="14c30-407">Model çıkışlarını puan ve ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="14c30-407">Score and parse model outputs</span></span>

<span data-ttu-id="14c30-408">*Program.cs* sınıfınızın `Main` yönteminde, try-catch ifadesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-408">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="14c30-409">`try` bloğunun içinde, nesne algılama mantığını uygulamaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-409">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="14c30-410">İlk olarak, verileri [`IDataView`](xref:Microsoft.ML.IDataView)' e yükleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-410">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="14c30-411">Ardından, `OnnxModelScorer` ' ın bir örneğini oluşturun ve yüklenen verileri almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-411">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="14c30-412">Şimdi işleme sonrası adımının zamanı.</span><span class="sxs-lookup"><span data-stu-id="14c30-412">Now it's time for the post-processing step.</span></span> <span data-ttu-id="14c30-413">Bir `YoloOutputParser` örneği oluşturun ve model çıkışını işlemek için onu kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-413">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="14c30-414">Model çıkışı işlendikten sonra, görüntülerde sınırlayıcı kutuları çizmeniz zaman alır.</span><span class="sxs-lookup"><span data-stu-id="14c30-414">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span>

### <a name="visualize-predictions"></a><span data-ttu-id="14c30-415">Tahminleri görselleştirin</span><span class="sxs-lookup"><span data-stu-id="14c30-415">Visualize predictions</span></span>

<span data-ttu-id="14c30-416">Model, görüntüleri puanladıktan ve çıktılar işlendikten sonra, görüntü üzerinde sınırlayıcı kutular çizmelidir.</span><span class="sxs-lookup"><span data-stu-id="14c30-416">After the model has scored the images and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="14c30-417">Bunu yapmak için *program.cs*içindeki `GetAbsolutePath` yönteminin altına `DrawBoundingBox` adlı bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-417">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method inside of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="14c30-418">İlk olarak, görüntüyü yükleyin ve `DrawBoundingBox` yönteminde yükseklik ve genişlik boyutlarını alın.</span><span class="sxs-lookup"><span data-stu-id="14c30-418">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="14c30-419">Ardından, model tarafından algılanan her bir sınırlayıcı kutu üzerinde yinelemek için her bir For-Each döngüsü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14c30-419">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="14c30-420">For-each döngüsünün içinde, sınırlayıcı kutunun boyutlarını alın.</span><span class="sxs-lookup"><span data-stu-id="14c30-420">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="14c30-421">Sınırlayıcı kutunun boyutları `416 x 416` ' ın model girişine karşılık geldiğinden, sınırlayıcı kutu boyutlarını görüntünün gerçek boyutuyla eşleşecek şekilde ölçeklendirin.</span><span class="sxs-lookup"><span data-stu-id="14c30-421">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="14c30-422">Ardından, her bir sınırlayıcı kutusunun üzerinde görünecek metin için bir şablon tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-422">Then, define a template for text that will appear above each bounding box.</span></span> <span data-ttu-id="14c30-423">Metin, ilgili sınırlayıcı kutusunun içindeki nesnenin sınıfını ve güveni içerir.</span><span class="sxs-lookup"><span data-stu-id="14c30-423">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="14c30-424">Görüntüde çizim yapmak için [`Graphics`](xref:System.Drawing.Graphics) nesnesine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="14c30-424">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

<span data-ttu-id="14c30-425">`using` kod bloğunun içinde, grafiğin [`Graphics`](xref:System.Drawing.Graphics) nesne ayarlarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-425">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="14c30-426">Bunun altında metin ve sınırlayıcı kutusu için yazı tipi ve renk seçeneklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="14c30-426">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="14c30-427">[`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) yöntemi kullanılarak metni içermesi için sınırlayıcı kutunun üzerinde bir dikdörtgen oluşturun ve girin.</span><span class="sxs-lookup"><span data-stu-id="14c30-427">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="14c30-428">Bu, metnin karşıtlığına ve okunabilirliği iyileştirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="14c30-428">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="14c30-429">Sonra, [`DrawString`](xref:System.Drawing.Graphics.DrawString*) ve [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) yöntemlerini kullanarak görüntüde metin ve sınırlayıcı kutusunu çizin.</span><span class="sxs-lookup"><span data-stu-id="14c30-429">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="14c30-430">For-each döngüsünün dışında, görüntüleri `outputDirectory` ' a kaydetmek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-430">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="14c30-431">Uygulamanın çalışma zamanında beklendiği gibi tahmine dayalı hale getirdiğine ek geri bildirimde bulunmak için, algılanan nesneleri konsola çıkarmak için *program.cs* dosyasındaki `DrawBoundingBox` yönteminin altına `LogDetectedObjects` adlı bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-431">For additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="14c30-432">Tahmine dayalı olarak görsel geri bildirim oluşturmaya yönelik yardımcı yöntemlere sahip olduğunuza göre, her bir puanlanmış görüntünün üzerinde yinelemek için bir for döngüsü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-432">Now that you have helper methods to create visual feedback from the predictions, add a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="14c30-433">For döngüsü içinde, görüntü dosyasının adını ve onunla ilişkili sınırlayıcı kutuları alın.</span><span class="sxs-lookup"><span data-stu-id="14c30-433">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="14c30-434">Bunun altında, görüntüde sınırlayıcı kutuları çizmek için `DrawBoundingBox` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-434">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="14c30-435">Son olarak, tahmine dayalı olarak konsola çıkarmak için `LogDetectedObjects` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="14c30-435">Lastly, use the `LogDetectedObjects` method to output predictions to the console.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

<span data-ttu-id="14c30-436">Try-catch ifadesinden sonra, işlemin çalıştığını göstermek için ek mantık ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14c30-436">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="14c30-437">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="14c30-437">That's it!</span></span>

## <a name="results"></a><span data-ttu-id="14c30-438">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="14c30-438">Results</span></span>

<span data-ttu-id="14c30-439">Önceki adımları uyguladıktan sonra konsol uygulamanızı çalıştırın (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="14c30-439">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="14c30-440">Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="14c30-440">Your results should be similar to the following output.</span></span> <span data-ttu-id="14c30-441">Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="14c30-441">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

<span data-ttu-id="14c30-442">Sınırlayıcı kutuları olan görüntüleri görmek için `assets/images/output/` dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="14c30-442">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="14c30-443">Aşağıda, işlenen görüntülerden birindeki bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="14c30-443">Below is a sample from one of the processed images.</span></span>

![Bir atma odasının örnek işlenmiş görüntüsü](./media/object-detection-onnx/dinning-room-table-chairs.png)

<span data-ttu-id="14c30-445">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="14c30-445">Congratulations!</span></span> <span data-ttu-id="14c30-446">ML.NET ' de önceden eğitilen `ONNX` modelini yeniden çalıştırarak nesne algılama için bir makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="14c30-446">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="14c30-447">Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14c30-447">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="14c30-448">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="14c30-448">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="14c30-449">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="14c30-449">Understand the problem</span></span>
> - <span data-ttu-id="14c30-450">ONNX 'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin</span><span class="sxs-lookup"><span data-stu-id="14c30-450">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="14c30-451">Modeli anlama</span><span class="sxs-lookup"><span data-stu-id="14c30-451">Understand the model</span></span>
> - <span data-ttu-id="14c30-452">Önceden eğitilen modeli yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="14c30-452">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="14c30-453">Yüklü bir modelle nesneleri Algıla</span><span class="sxs-lookup"><span data-stu-id="14c30-453">Detect objects with a loaded model</span></span>

<span data-ttu-id="14c30-454">Genişletilmiş bir nesne algılama örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="14c30-454">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="14c30-455">DotNet/machinöğrenim-Samples GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="14c30-455">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
