---
title: 'Öğretici: ONNX ve ML.NET ile derin öğrenme kullanarak nesneleri Algıla'
description: Bu öğreticide, görüntülerdeki nesneleri algılamak için ML.NET ' de önceden eğitilen ONNX derin öğrenme modelinin nasıl kullanılacağı gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 08/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a5a11bc49fa834ebd6945e47767deb559244b459
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374509"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="cd0f3-103">Öğretici: ML.NET içinde ONNX kullanarak nesneleri Algıla</span><span class="sxs-lookup"><span data-stu-id="cd0f3-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="cd0f3-104">Görüntülerdeki nesneleri saptamak için ML.NET ' de önceden eğitilen bir ONNX modeli kullanmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="cd0f3-105">Bir nesne algılama modelini sıfırdan eğitmek için milyonlarca parametre, büyük miktarda etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="cd0f3-106">Önceden eğitilen bir modelin kullanılması, eğitim sürecini kısayola etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="cd0f3-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="cd0f3-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="cd0f3-108">Understand the problem</span></span>
> - <span data-ttu-id="cd0f3-109">ONNX 'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin</span><span class="sxs-lookup"><span data-stu-id="cd0f3-109">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="cd0f3-110">Modeli anlama</span><span class="sxs-lookup"><span data-stu-id="cd0f3-110">Understand the model</span></span>
> - <span data-ttu-id="cd0f3-111">Önceden eğitilen modeli yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="cd0f3-111">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="cd0f3-112">Yüklü bir modelle nesneleri Algıla</span><span class="sxs-lookup"><span data-stu-id="cd0f3-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="cd0f3-113">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="cd0f3-113">Pre-requisites</span></span>

- <span data-ttu-id="cd0f3-114">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="cd0f3-115">Microsoft.ML NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="cd0f3-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="cd0f3-116">Microsoft. ML. ımageanalytics NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="cd0f3-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="cd0f3-117">Microsoft. ML. OnnxTransformer NuGet paketi</span><span class="sxs-lookup"><span data-stu-id="cd0f3-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="cd0f3-118">Küçük YOLOv2 önceden eğitilen model</span><span class="sxs-lookup"><span data-stu-id="cd0f3-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/tiny_yolov2)
- <span data-ttu-id="cd0f3-119">[Netron](https://github.com/lutzroeder/netron) seçim</span><span class="sxs-lookup"><span data-stu-id="cd0f3-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="cd0f3-120">ONNX nesne algılama örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="cd0f3-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="cd0f3-121">Bu örnek, önceden eğitilen derinlemesine öğrenme ONNX modelini kullanarak bir görüntüdeki nesneleri algılayan bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="cd0f3-122">Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="cd0f3-123">Nesne algılama nedir?</span><span class="sxs-lookup"><span data-stu-id="cd0f3-123">What is object detection?</span></span>

<span data-ttu-id="cd0f3-124">Nesne algılama bir bilgisayar vizyonu sorunudur.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="cd0f3-125">Görüntü sınıflandırmasıyla yakından ilgili olarak, nesne algılama görüntü sınıflandırmasını daha ayrıntılı bir ölçekte gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="cd0f3-126">Nesne algılama hem görüntüler içindeki varlıkları bulur _hem_ de kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="cd0f3-127">Görüntüler farklı türlerde birden çok nesne içerdiğinde nesne algılamayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-127">Use object detection when images contain multiple objects of different types.</span></span>

![](./media/object-detection-onnx/img-classification-obj-detection.PNG)

<span data-ttu-id="cd0f3-128">Nesne algılama için bazı kullanım örnekleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-128">Some use cases for object detection include:</span></span>

- <span data-ttu-id="cd0f3-129">Kendi kendine yönlendiren otomobiller</span><span class="sxs-lookup"><span data-stu-id="cd0f3-129">Self-Driving Cars</span></span>
- <span data-ttu-id="cd0f3-130">Robotics</span><span class="sxs-lookup"><span data-stu-id="cd0f3-130">Robotics</span></span>
- <span data-ttu-id="cd0f3-131">Yüz Algılama</span><span class="sxs-lookup"><span data-stu-id="cd0f3-131">Face Detection</span></span>
- <span data-ttu-id="cd0f3-132">Çalışma alanı güvenliği</span><span class="sxs-lookup"><span data-stu-id="cd0f3-132">Workplace Safety</span></span>
- <span data-ttu-id="cd0f3-133">Nesne sayımı</span><span class="sxs-lookup"><span data-stu-id="cd0f3-133">Object Counting</span></span>
- <span data-ttu-id="cd0f3-134">Etkinlik tanıma</span><span class="sxs-lookup"><span data-stu-id="cd0f3-134">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="cd0f3-135">Derin öğrenme modeli seçin</span><span class="sxs-lookup"><span data-stu-id="cd0f3-135">Select a deep learning model</span></span>

<span data-ttu-id="cd0f3-136">Derin öğrenme, Machine Learning 'in bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-136">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="cd0f3-137">Derin öğrenme modellerini eğmek için, büyük miktarlarda veri gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-137">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="cd0f3-138">Verilerdeki desenler, bir dizi katman tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-138">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="cd0f3-139">Verilerdeki ilişkiler, ağırlık içeren katmanlar arasında bağlantı olarak kodlanır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-139">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="cd0f3-140">Ağırlığa göre daha güçlü olan ilişki.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-140">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="cd0f3-141">Toplu olarak, bu katman ve bağlantı serisi yapay sinir Networks olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-141">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="cd0f3-142">Bir ağdaki daha fazla katman, "daha derin" ve bunu derin bir sinir ağı yapıyor.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-142">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span>

<span data-ttu-id="cd0f3-143">Farklı türlerde sinir Networks, en yaygın çok katmanlı Perceptron (MLP), evsel sinir ağı (CNN) ve yinelenen sinir ağı (RNN).</span><span class="sxs-lookup"><span data-stu-id="cd0f3-143">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="cd0f3-144">En temel, bir giriş kümesini bir çıktı kümesine eşleyen MLP 'dir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-144">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="cd0f3-145">Bu sinir ağı, verilerin bir uzamsal veya zaman bileşeni olmadığında iyidir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-145">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="cd0f3-146">CNN, veride bulunan uzamsal bilgileri işlemek için evsel katmanların kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-146">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="cd0f3-147">CNNs için iyi bir kullanım örneği, bir görüntünün bölgesindeki bir özelliğin varlığını algılamak için görüntü işleme 'dir (örneğin, bir görüntünün merkezinde bir burun mu var?).</span><span class="sxs-lookup"><span data-stu-id="cd0f3-147">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="cd0f3-148">Son olarak, RNNs durum veya belleğin girdi olarak kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-148">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="cd0f3-149">RNNs, sıralı sıralama ve olayların bağlamı önemli olduğu zaman serisi analizi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-149">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span>

### <a name="understand-the-model"></a><span data-ttu-id="cd0f3-150">Modeli anlama</span><span class="sxs-lookup"><span data-stu-id="cd0f3-150">Understand the model</span></span>

<span data-ttu-id="cd0f3-151">Nesne algılama bir görüntü işleme görevidir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-151">Object detection is an image processing task.</span></span> <span data-ttu-id="cd0f3-152">Bu nedenle, bu sorunu çözmek için eğitilen çoğu derin öğrenme modeli CNNs ' dir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-152">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="cd0f3-153">Bu öğreticide kullanılan model, YOLOv2 modelinin kağıda açıklanan daha kompakt bir sürümü olan küçük YOLOv2 modelidir: ["YOLO9000: RedMon ve Fadhari](https://arxiv.org/pdf/1612.08242.pdf)tarafından daha Iyi, daha hızlı, daha güçlü.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-153">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="cd0f3-154">Küçük YOLOv2, Pascal VOC veri kümesi üzerinde eğitilir ve 20 farklı nesne sınıfı tahmin edebilen 15 katmandan oluşur.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-154">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="cd0f3-155">Küçük YOLOv2 özgün YOLOv2 modelinin sıkıştırılmış bir sürümü olduğundan, hız ve doğruluk arasında bir zorunluluğunu getirir yapılır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-155">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="cd0f3-156">Modeli oluşturan farklı katmanlar netron gibi araçlar kullanılarak görselleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-156">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="cd0f3-157">Modelin araştırılama, her katmanın, ilgili giriş/çıkış boyutlarıyla birlikte katman adını içerdiği sinir ağını oluşturan tüm katmanlar arasında bağlantı eşlemesini elde edecektir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-157">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="cd0f3-158">Modelin girişlerini ve çıkışlarını tanımlamakta kullanılan veri yapıları, teniler olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-158">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="cd0f3-159">Teniler, verileri N boyutlu bir şekilde depolayan kapsayıcılar olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-159">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="cd0f3-160">Küçük YOLOv2 durumunda, giriş katmanının adı olur `image` ve bir boyut `3 x 416 x 416`gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-160">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="cd0f3-161">Çıktı katmanının adı olur `grid` ve boyutların `125 x 13 x 13`bir çıkış eğilimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-161">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>

![](./media/object-detection-onnx/netron-model-map.png)

<span data-ttu-id="cd0f3-162">YOLO modeli bir görüntü `3(RGB) x 416px x 416px`alır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-162">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="cd0f3-163">Model bu girişi alır ve bir çıktı üretmek için farklı katmanlardan geçirir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-163">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="cd0f3-164">Çıktı, giriş görüntüsünü kılavuzdaki her hücreyle `13 x 13` `125` değerleri içeren bir kılavuza böler.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-164">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span>

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="cd0f3-165">ONNX modeli nedir?</span><span class="sxs-lookup"><span data-stu-id="cd0f3-165">What is an ONNX model?</span></span>

<span data-ttu-id="cd0f3-166">Open sinir Network Exchange (ONNX), AI modelleri için açık kaynak biçimidir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-166">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="cd0f3-167">ONNX çerçeveler arasında birlikte çalışabilirliği destekler.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-167">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="cd0f3-168">Bu, bir modeli PyTorch gibi birçok popüler makine öğrenimi çerçevelerinden birinde eğitebileceğiniz anlamına gelir, ONNX biçimine dönüştürebilir ve ML.NET gibi farklı bir çerçevede ONNX modelini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-168">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="cd0f3-169">Daha fazla bilgi edinmek için [Onnx Web sitesini](https://onnx.ai/)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-169">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span>

![](./media/object-detection-onnx/onnx-frameworks.png)

<span data-ttu-id="cd0f3-170">Önceden eğitilen küçük YOLOv2 modeli, katmanların serileştirilmiş bir gösterimi ve bu katmanların öğrenilen desenleri ile ONNX biçiminde depolanır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-170">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="cd0f3-171">ML.net ' de, onnx ile birlikte çalışabilirlik, [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) ve [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet paketleriyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-171">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="cd0f3-172">Paket [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) , bir görüntüyü alan ve bir tahmin veya eğitim işlem hattına giriş olarak kullanılabilecek sayısal değerlere kodlayan bir dizi dönüştürme içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-172">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="cd0f3-173">[`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) Paket onnx çalışma zamanından yararlanır ve belirtilen girişe göre tahmine dayalı hale getirmek için bu modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-173">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span>

![](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="cd0f3-174">.NET Core projesini ayarlama</span><span class="sxs-lookup"><span data-stu-id="cd0f3-174">Set up the .NET Core project</span></span>

<span data-ttu-id="cd0f3-175">Artık ONNX 'in ne olduğuna ve küçük YOLOv2 nasıl çalıştığına ilişkin genel bir bilgiye sahip olduğunuza göre, uygulamanın derlenmesi zaman vardır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-175">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="cd0f3-176">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd0f3-176">Create a console application</span></span>

1. <span data-ttu-id="cd0f3-177">"ObjectDetection" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-177">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="cd0f3-178">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-178">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="cd0f3-179">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-179">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    - <span data-ttu-id="cd0f3-180">Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml**için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-180">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    - <span data-ttu-id="cd0f3-181">**Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-181">Select the **Install** button.</span></span>
    - <span data-ttu-id="cd0f3-182">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-182">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    - <span data-ttu-id="cd0f3-183">**Microsoft. ml. ımageanalytics** ve **Microsoft. ml. OnnxTransformer**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-183">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="cd0f3-184">Verilerinizi hazırlayın ve önceden eğitilen modeli</span><span class="sxs-lookup"><span data-stu-id="cd0f3-184">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="cd0f3-185">[Proje Varlıkları Dizin ZIP dosyasını](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) indirin ve sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-185">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="cd0f3-186">Dizini objectdetection proje dizininize kopyalayın. `assets`</span><span class="sxs-lookup"><span data-stu-id="cd0f3-186">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="cd0f3-187">Bu dizin ve alt dizinleri, bu öğretici için gerekli olan resim dosyalarını (küçük YOLOv2 modeli dışında, indirecek ve sonraki adımda ekleyeceğiniz) içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-187">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="cd0f3-188">[Onnx model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)ve unzip 'Ten [küçük YOLOv2 modelini](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) indirin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-188">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="cd0f3-189">Komut istemi ' ni açın ve şu komutu girin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-189">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. <span data-ttu-id="cd0f3-190">Ayıklanan `model.onnx` dosyayı Dizin içinden *objectdetection* proje `assets\Model` dizininize kopyalayın ve olarak `TinyYolo2_model.onnx`yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-190">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="cd0f3-191">Bu dizin, bu öğretici için gereken modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-191">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="cd0f3-192">Çözüm Gezgini, varlık dizinindeki ve alt dizinlerde bulunan dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-192">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="cd0f3-193">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-193">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="cd0f3-194">Sınıf oluşturma ve yollar tanımlama</span><span class="sxs-lookup"><span data-stu-id="cd0f3-194">Create classes and define paths</span></span>

<span data-ttu-id="cd0f3-195">*Program.cs* dosyasını açın ve aşağıdaki ek `using` deyimlerini dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-195">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

<span data-ttu-id="cd0f3-196">Ardından, çeşitli varlıkların yollarını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-196">Next, define the paths of the various assets.</span></span>

1. <span data-ttu-id="cd0f3-197">İlk olarak, yöntemi `GetAbsolutePath` `Program` sınıfındaki yönteminin `Main` altına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-197">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span>

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="cd0f3-198">Ardından, `Main` yöntemi içinde varlıklarınızın konumunu depolamak için alanlar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-198">Then, inside the `Main` method, create fields to store the location of your assets.</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="cd0f3-199">Giriş verilerinizi ve tahmin sınıflarınızı depolamak için projenize yeni bir dizin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-199">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="cd0f3-200">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni klasör** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="cd0f3-201">Yeni klasör Çözüm Gezgini göründüğünde, "Datayapýlarý" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-201">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="cd0f3-202">Yeni oluşturulan *Datayapýlarý* dizininde giriş veri sınıfınızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-202">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="cd0f3-203">**Çözüm Gezgini**, *datayapýlarý* dizinine sağ tıklayıp**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-203">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="cd0f3-204">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ImageNetData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-204">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="cd0f3-205">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-205">Then, select the **Add** button.</span></span>

    <span data-ttu-id="cd0f3-206">*ImageNetData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-206">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="cd0f3-207">Aşağıdaki `using` ifadeyi *ImageNetData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-207">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="cd0f3-208">Mevcut sınıf tanımını kaldırın ve `ImageNetData` sınıf için aşağıdaki kodu *ImageNetData.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-208">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="cd0f3-209">`ImageNetData`, giriş resmi veri sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-209">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="cd0f3-210">`ImagePath`görüntünün depolandığı yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-210">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="cd0f3-211">`Label`dosyanın adını içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-211">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="cd0f3-212">Ayrıca, `ImageNetData` `ReadFromFile` belirtilenyolda`imageFolder` depolanan birden çok görüntü dosyasını yükleyen ve bunları bir nesnekoleksiyonuolarakdöndürenbiryöntemiiçerir.`ImageNetData`</span><span class="sxs-lookup"><span data-stu-id="cd0f3-212">Additionally, `ImageNetData` contains a method `ReadFromFile` which loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="cd0f3-213">*Veri yapıları* dizininde tahmin sınıfınızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-213">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="cd0f3-214">**Çözüm Gezgini**, *datayapýlarý* dizinine sağ tıklayıp**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-214">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="cd0f3-215">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ImageNetPrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="cd0f3-216">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="cd0f3-217">*ImageNetPrediction.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-217">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="cd0f3-218">Aşağıdaki `using` ifadeyi *ImageNetPrediction.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-218">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="cd0f3-219">Mevcut sınıf tanımını kaldırın ve `ImageNetPrediction` sınıf için aşağıdaki kodu *ImageNetPrediction.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-219">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="cd0f3-220">`ImageNetPrediction`, tahmin verileri sınıfıdır ve şu `float[]` alana sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-220">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="cd0f3-221">`PredictedLabel`görüntüde algılanan her bir sınırlayıcı kutu için boyutları, objectlik Puanını ve sınıf olasılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-221">`PredictedLabel` contains the dimensions, objectness score and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="cd0f3-222">Değişkenleri ana olarak Başlat</span><span class="sxs-lookup"><span data-stu-id="cd0f3-222">Initialize variables in Main</span></span>

<span data-ttu-id="cd0f3-223">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-223">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="cd0f3-224">Entity Framework, kavramsal `DBContext` olarak da benzerdir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="cd0f3-225">`MLContext` `mlContext` Aşağıdaki satırı alanınaltındaki`outputFolder` program.cs yöntemine ekleyerek değişkeni yeni bir örneğiyle başlatın. `Main`</span><span class="sxs-lookup"><span data-stu-id="cd0f3-225">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="cd0f3-226">İşlem sonrası model çıkışları için bir Ayrıştırıcı oluşturun</span><span class="sxs-lookup"><span data-stu-id="cd0f3-226">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="cd0f3-227">Model, her kılavuz `13 x 13` `32px x 32px`hücresinin bulunduğu bir görüntüyü kılavuza böler.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-227">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="cd0f3-228">Her kılavuz hücresi, 5 olası nesne sınırlayıcı kutusu içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-228">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="cd0f3-229">Bir sınırlayıcı kutusunda 25 öğe vardır:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-229">A bounding box has  25 elements:</span></span>

![](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="cd0f3-230">`x`sınırlama kutusu merkezinin ilişkilendirildiği kılavuz hücresine göre x konumu.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-230">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="cd0f3-231">`y`sınırlama kutusu merkezinin ilişkilendirildiği kılavuz hücresine göre y konumu.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-231">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="cd0f3-232">`w`sınırlayıcı kutunun genişliği.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-232">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="cd0f3-233">`h`sınırlayıcı kutunun yüksekliği.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-233">`h` the height of the bounding box.</span></span>
- <span data-ttu-id="cd0f3-234">`o`bir nesnenin, sınırlayıcı kutusunda bulunduğu güven değeri, aynı zamanda objectlik puanı olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-234">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="cd0f3-235">`p1-p20`model tarafından tahmin edilen 20 sınıfın her biri için sınıf olasılıkların.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-235">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="cd0f3-236">Toplamda, 5 sınırlayıcı kutulardan her birini tanımlayan 25 öğe, her kılavuz hücresinde bulunan 125 öğelerini yapar.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-236">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="cd0f3-237">Önceden eğitilen onnx modeli tarafından oluşturulan çıkış, boyutlarla `21125` `125 x 13 x 13`birlikte bir ön sor öğelerinin öğelerini temsil eden bir float dizisidir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-237">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="cd0f3-238">Model tarafından oluşturulan tahminleri bir tencursor 'a dönüştürmek için bazı işleme sonrası işler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-238">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="cd0f3-239">Bunu yapmak için, çıktıyı ayrıştırmaya yardımcı olmak üzere bir sınıf kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-239">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="cd0f3-240">Ayrıştırıcı sınıfları kümesini düzenlemek için projenize yeni bir dizin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-240">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="cd0f3-241">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni klasör** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-241">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="cd0f3-242">Yeni klasör Çözüm Gezgini göründüğünde, "YoloParser" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-242">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="cd0f3-243">Sınırlayıcı kutular ve boyutlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd0f3-243">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="cd0f3-244">Modelin veri çıktısı, görüntü içindeki nesnelerin sınırlayıcı kutularının koordinatlarını ve boyutlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-244">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="cd0f3-245">Boyutlar için bir temel sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-245">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="cd0f3-246">**Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-246">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="cd0f3-247">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *DimensionsBase.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-247">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="cd0f3-248">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-248">Then, select the **Add** button.</span></span>

    <span data-ttu-id="cd0f3-249">*DimensionsBase.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-249">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="cd0f3-250">Tüm `using` deyimlerini ve varolan sınıf tanımını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-250">Remove all `using` statements and existing class definition.</span></span>

    <span data-ttu-id="cd0f3-251">`DimensionsBase` Sınıfı için aşağıdaki kodu *DimensionsBase.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-251">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="cd0f3-252">`DimensionsBase`Aşağıdaki `float` alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-252">`DimensionsBase` has the following `float` fields:</span></span>

    - <span data-ttu-id="cd0f3-253">`X`nesnenin x ekseni üzerindeki konumunu içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-253">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="cd0f3-254">`Y`nesnenin y ekseni üzerinde konumunu içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-254">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="cd0f3-255">`Height`nesnenin yüksekliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-255">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="cd0f3-256">`Width`nesnenin genişliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-256">`Width` contains the width of the object.</span></span>

<span data-ttu-id="cd0f3-257">Ardından, sınırlayıcı kutularınız için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-257">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="cd0f3-258">**Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-258">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="cd0f3-259">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *YoloBoundingBox.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-259">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="cd0f3-260">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-260">Then, select the **Add** button.</span></span>

    <span data-ttu-id="cd0f3-261">*YoloBoundingBox.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-261">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="cd0f3-262">Aşağıdaki `using` ifadeyi *YoloBoundingBox.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-262">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="cd0f3-263">Mevcut sınıf tanımının hemen üzerinde, ilgili sınırlayıcı kutusunun boyutlarını içerecek şekilde `BoundingBoxDimensions` `DimensionsBase` sınıfından devralan adlı yeni bir sınıf tanımı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-263">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` which inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="cd0f3-264">Mevcut `YoloBoundingBox` sınıf tanımını kaldırın ve `YoloBoundingBox` sınıf için aşağıdaki kodu *YoloBoundingBox.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-264">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    <span data-ttu-id="cd0f3-265">`YoloBoundingBox`aşağıdaki alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-265">`YoloBoundingBox` has the following fields:</span></span>

    - <span data-ttu-id="cd0f3-266">`Dimensions`sınırlayıcı kutunun boyutlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-266">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="cd0f3-267">`Label`sınırlayıcı kutusunda algılanan nesne sınıfını içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-267">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="cd0f3-268">`Confidence`sınıfının güvenini içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-268">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="cd0f3-269">`Rect`sınırlayıcı kutunun boyutlarının dikdörtgen gösterimini içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-269">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="cd0f3-270">`BoxColor`görüntüde çizim yapmak için kullanılan ilgili sınıfla ilişkili rengi içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-270">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="cd0f3-271">Ayrıştırıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd0f3-271">Create the parser</span></span>

<span data-ttu-id="cd0f3-272">Artık boyut ve sınırlama kutuları için sınıflar oluşturuldığına göre, ayrıştırıcısı oluşturma zamanı.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-272">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="cd0f3-273">**Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-273">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="cd0f3-274">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *YoloOutputParser.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-274">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="cd0f3-275">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-275">Then, select the **Add** button.</span></span>

    <span data-ttu-id="cd0f3-276">*YoloOutputParser.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-276">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="cd0f3-277">Aşağıdaki `using` ifadeyi *YoloOutputParser.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-277">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="cd0f3-278">Varolan `YoloOutputParser` sınıf tanımının içinde, görüntüdeki her bir hücrenin boyutlarını içeren bir iç içe sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-278">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="cd0f3-279">Sınıf tanımının en üstündeki `CellDimensions` `DimensionsBase` `YoloOutputParser` sınıftan devralan sınıf için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-279">Add the following code for the `CellDimensions` class which inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="cd0f3-280">`YoloOutputParser` Sınıf tanımı içinde aşağıdaki sabiti ve alanları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-280">Inside the `YoloOutputParser` class definition, add the following constant and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - <span data-ttu-id="cd0f3-281">`ROW_COUNT`, görüntüdeki görüntünün bölüneceğini, ızgaradaki satır sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-281">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="cd0f3-282">`COL_COUNT`, görüntüde bölünen, kılavuzdaki sütun sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-282">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="cd0f3-283">`CHANNEL_COUNT`kılavuzun tek bir hücresinde bulunan toplam değer sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-283">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="cd0f3-284">`BOXES_PER_CELL`, bir hücredeki sınırlayıcı kutuların sayısıdır,</span><span class="sxs-lookup"><span data-stu-id="cd0f3-284">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="cd0f3-285">`BOX_INFO_FEATURE_COUNT`, bir kutu içinde (x, y, Height, Width, güvenirlik) bulunan özelliklerin sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-285">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="cd0f3-286">`CLASS_COUNT`, her bir sınırlayıcı kutusunda bulunan sınıf tahminleri sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-286">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="cd0f3-287">`CELL_WIDTH`, görüntü kılavuzundaki bir hücrenin genişliğidir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-287">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="cd0f3-288">`CELL_HEIGHT`, görüntü kılavuzundaki bir hücrenin yüksekliğidir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-288">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="cd0f3-289">`channelStride`Kılavuzdaki geçerli hücrenin başlangıç konumudur.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-289">`channelStride` is the starting position of the current cell in the grid.</span></span>

    <span data-ttu-id="cd0f3-290">Model, Puanlama olarak da bilinen bir tahmin yaptığında, `416px x 416px` giriş görüntüsünü `13 x 13`boyutunun bir hücre kılavuzuna böler.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-290">When the model makes a prediction, also known as scoring, it divides the `416px x 416px` input image into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="cd0f3-291">Her hücre içerir `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-291">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="cd0f3-292">Her hücrede, 5 Özellik (x, y, Width, Height, güvenirlik) içeren 5 sınırlayıcı kutu vardır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-292">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="cd0f3-293">Ayrıca, her sınırlayıcı kutu, bu örnekte 20 olan her bir sınıf olasılığını içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-293">In addition, each bounding box contains the probability of each of the classes which in this case is 20.</span></span> <span data-ttu-id="cd0f3-294">Bu nedenle, her hücre 125 bilgi parçasını içerir (5 özellik + 20 sınıf olasılıkların).</span><span class="sxs-lookup"><span data-stu-id="cd0f3-294">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span>

<span data-ttu-id="cd0f3-295">Tüm 5 sınırlayıcı kutular için aşağıdan `channelStride` bir çıpası listesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-295">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

<span data-ttu-id="cd0f3-296">Bağlayıcıların sınırlayıcı kutuların önceden tanımlanmış yükseklik ve genişlik oranları vardır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-296">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="cd0f3-297">Bir model tarafından algılanan çoğu nesne veya sınıfın benzer oranları vardır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-297">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="cd0f3-298">Bu, sınırlayıcı kutular oluşturmak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-298">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="cd0f3-299">Sınırlayıcı kutuları tahmin etmek yerine, önceden tanımlanmış boyutlardan olan fark, bu nedenle, sınırlayıcı kutuyu tahmin etmek için gereken hesaplamayı azaltmak için hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-299">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="cd0f3-300">Genellikle bu bağlantı oranları, kullanılan veri kümesi temel alınarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-300">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="cd0f3-301">Bu durumda, veri kümesi bilindiği ve değerler önceden hesaplandığından, bağlantılar sabit kodlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-301">In this case because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="cd0f3-302">Ardından, modelin tahmin edecek etiketleri veya sınıfları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-302">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="cd0f3-303">Bu model, özgün YOLOv2 modeli tarafından tahmin edilen toplam sınıf sayısının bir alt kümesi olan 20 sınıfı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-303">This model predicts 20 classes which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="cd0f3-304">Altına etiket listenizi ekleyin `anchors`.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-304">Add your list of labels below the `anchors`.</span></span>

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="cd0f3-305">Sınıfların her biriyle ilişkili renkler vardır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-305">There are colors associated with each of the classes.</span></span> <span data-ttu-id="cd0f3-306">Sınıf renklerinizi aşağıdaki `labels`gibi atayın:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-306">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="cd0f3-307">Yardımcı işlevler oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd0f3-307">Create helper functions</span></span>

<span data-ttu-id="cd0f3-308">İşleme sonrası aşamasında yer alan bir dizi adım vardır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-308">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="cd0f3-309">Bu konuda yardımcı olmak için birkaç yardımcı yöntem kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-309">To help with that, several helper methods can be employed.</span></span>

<span data-ttu-id="cd0f3-310">Ayrıştırıcı tarafından kullanılan yardımcı yöntemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-310">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="cd0f3-311">`Sigmoid`0 ile 1 arasında bir sayı çıkışı yapan sigmoıd işlevini uygular.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-311">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="cd0f3-312">`Softmax`bir giriş vektörünü bir olasılık dağıtımına normalleştirir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-312">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="cd0f3-313">`GetOffset`tek boyutlu model çıkışındaki öğeleri bir `125 x 13 x 13` tencursor içindeki ilgili konuma eşler.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-313">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="cd0f3-314">`ExtractBoundingBoxes`Model çıktısından `GetOffset` yöntemi kullanarak sınırlama kutusu boyutlarını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-314">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="cd0f3-315">`GetConfidence`modelin bir nesne algıladığını ve bir yüzdeyi dönüştürmek için `Sigmoid` işlevi kullandığını belirten güvenirlik değerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-315">`GetConfidence` extracts the confidence value which states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="cd0f3-316">`MapBoundingBoxToCell`, sınırlayıcı kutu boyutlarını kullanır ve bunları görüntünün içindeki ilgili hücresiyle eşler.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-316">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="cd0f3-317">`ExtractClasses``GetOffset` yöntemi kullanarak model çıktısından sınırlama kutusu için sınıf tahminlerini ayıklar ve `Softmax` yöntemi kullanarak bunları bir olasılık dağıtımına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-317">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="cd0f3-318">`GetTopResult`en yüksek olasılığa sahip tahmin edilen sınıflar listesinden sınıfı seçer.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-318">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="cd0f3-319">`IntersectionOverUnion`daha düşük olasılıklara sahip sınırlayıcı kutuları filtreler.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-319">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="cd0f3-320">Listenizin altındaki tüm yardımcı yöntemleri için kodu ekleyin `classColors`.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-320">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="cd0f3-321">Tüm yardımcı yöntemlerini tanımladıktan sonra, model çıkışını işlemek için bunları kullanma zamanı da vardır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-321">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="cd0f3-322">Yönteminin altında, model tarafından oluşturulan `ParseOutputs` çıktıyı işlemek için yöntemi oluşturun. `IntersectionOverUnion`</span><span class="sxs-lookup"><span data-stu-id="cd0f3-322">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

<span data-ttu-id="cd0f3-323">Sınırlayıcı kutularınızı depolamak ve `ParseOutputs` yöntemin içinde değişkenleri tanımlamak için bir liste oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-323">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="cd0f3-324">Her resim bir `13 x 13` hücre kılavuzuna bölünmüştür.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-324">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="cd0f3-325">Her hücrede beş sınırlayıcı kutu bulunur.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-325">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="cd0f3-326">`boxes` Değişkenin altında, her hücrenin içindeki tüm kutuları işlemek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-326">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

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

<span data-ttu-id="cd0f3-327">En içteki döngünün içinde, tek boyutlu model çıkışı içindeki geçerli kutunun başlangıç konumunu hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-327">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="cd0f3-328">Doğrudan altında, geçerli sınırlayıcı kutusunun `ExtractBoundingBoxDimensions` boyutlarını almak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-328">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="cd0f3-329">Ardından, geçerli sınırlayıcı `GetConfidence` kutusunun güvenini almak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-329">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="cd0f3-330">Bundan sonra, geçerli sınırlayıcı `MapBoundingBoxToCell` kutuyu işlenmekte olan geçerli hücreyle eşlemek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-330">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="cd0f3-331">Daha fazla işlem yapmadan önce, güven değerinin sağlanan eşikten büyük olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-331">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="cd0f3-332">Aksi takdirde, sonraki sınırlayıcı kutuyu işleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-332">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="cd0f3-333">Aksi takdirde, çıktıyı işlemeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-333">Otherwise, continue processing the output.</span></span> <span data-ttu-id="cd0f3-334">Sonraki adımda, `ExtractClasses` yöntemi kullanılarak geçerli sınırlayıcı kutu için öngörülen sınıfların olasılık dağılımı alınır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-334">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="cd0f3-335">Daha sonra, geçerli `GetTopResult` kutu için en yüksek olasılığa sahip sınıfın değerini ve dizinini almak ve Puanını hesaplamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-335">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="cd0f3-336">`topScore` ' İ bir kez daha kullanarak yalnızca belirtilen eşiğin üzerinde olan sınırlayıcı kutuları saklayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-336">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="cd0f3-337">Son olarak, geçerli sınırlayıcı kutusu eşiği aşarsa, yeni `BoundingBox` bir nesne oluşturun ve `boxes` listeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-337">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="cd0f3-338">Görüntüdeki tüm hücreler işlendikten sonra `boxes` listeyi geri döndürün.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-338">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="cd0f3-339">Aşağıdaki return ifadesini `ParseOutputs` yöntemine en dıştaki for-Loop altına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-339">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="cd0f3-340">Çakışan kutuları filtrele</span><span class="sxs-lookup"><span data-stu-id="cd0f3-340">Filter overlapping boxes</span></span>

<span data-ttu-id="cd0f3-341">Artık yüksek oranda uygun sınırlama kutularının tümü model çıktısından ayıklandığına göre, çakışan görüntüleri kaldırmak için ek filtrelemenin yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-341">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="cd0f3-342">Yönteminin altına adlı `FilterBoundingBoxes` bir yöntem ekleyin: `ParseOutputs`</span><span class="sxs-lookup"><span data-stu-id="cd0f3-342">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="cd0f3-343">`FilterBoundingBoxes` Yöntemi içinde, algılanan kutuların boyutuna eşit bir dizi oluşturarak ve tüm yuvaları etkin veya işleme hazırmış olarak işaretleyerek devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-343">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="cd0f3-344">Ardından, sınırlayıcı kutularınızı içeren listeyi güvenle azalan sırada sıralayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-344">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="cd0f3-345">Bundan sonra filtrelenmiş sonuçları tutacak bir liste oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-345">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="cd0f3-346">Her bir sınırlayıcı kutunun her biri üzerinde yinelenerek her bir sınırlayıcı kutuyu işlemeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-346">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="cd0f3-347">Bu for-döngüsünün içinde, geçerli sınırlayıcı kutusunun işlenip işlenemeyeceğini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-347">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{

}
```

<span data-ttu-id="cd0f3-348">Bu durumda, sınırlama kutusunu sonuçlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-348">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="cd0f3-349">Sonuçlar Ayıklanacak belirlenen kutu sınırını aşarsa döngüyü sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-349">If the results exceeds the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="cd0f3-350">Aşağıdaki kodu if-deyimin içine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-350">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="cd0f3-351">Aksi takdirde, bitişik sınırlayıcı kutulara bakın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-351">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="cd0f3-352">Aşağıdaki kodu Box limit denetiminin altına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-352">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="cd0f3-353">İlk kutu gibi, bitişik kutu etkin veya işlenmek üzere hazırsanız, ilk kutunun ve ikinci kutunun belirtilen eşiği `IntersectionOverUnion` aşıp aşmadığını denetlemek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-353">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="cd0f3-354">Aşağıdaki kodu, en son for-loop ' a ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-354">Add the following code to your inner-most for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="cd0f3-355">Bitişik sınırlayıcı kutuları denetleyen en büyük for-Loop dışında, işlenmek üzere kalan herhangi bir sınırlama kutusu olup olmadığına bakın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-355">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="cd0f3-356">Aksi takdirde, için dış döngüden çıkar.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-356">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="cd0f3-357">Son olarak, `FilterBoundingBoxes` yöntemin ilk döngüsü dışında, sonuçları döndürün:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-357">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="cd0f3-358">Harika!</span><span class="sxs-lookup"><span data-stu-id="cd0f3-358">Great!</span></span> <span data-ttu-id="cd0f3-359">Artık bu kodu Puanlama modeliyle birlikte kullanmanın zamanı.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-359">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="cd0f3-360">Puanlama için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="cd0f3-360">Use the model for scoring</span></span>

<span data-ttu-id="cd0f3-361">İşlem sonrasında olduğu gibi, Puanlama adımlarında birkaç adım vardır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-361">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="cd0f3-362">Bu konuda yardım almak için, projenize Puanlama mantığını içerecek bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-362">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="cd0f3-363">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-363">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="cd0f3-364">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *OnnxModelScorer.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-364">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="cd0f3-365">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-365">Then, select the **Add** button.</span></span>

    <span data-ttu-id="cd0f3-366">*OnnxModelScorer.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-366">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="cd0f3-367">Aşağıdaki `using` ifadeyi *OnnxModelScorer.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-367">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="cd0f3-368">`OnnxModelScorer` Sınıf tanımı içinde aşağıdaki değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-368">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="cd0f3-369">Doğrudan altında, daha önce tanımlanmış değişkenleri başlatacak `OnnxModelScorer` sınıf için bir Oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-369">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="cd0f3-370">Oluşturucuyu oluşturduktan sonra, görüntü ve model ayarlarıyla ilgili değişkenleri içeren birkaç yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-370">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="cd0f3-371">Model için girdi olarak `ImageNetSettings` beklenen yüksekliği ve genişliği içeren bir struct oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-371">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="cd0f3-372">Bundan sonra, modelin giriş ve çıkış `TinyYoloModelSettings` katmanlarının adlarını içeren adlı başka bir struct oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-372">After that, create another struct called `TinyYoloModelSettings` which contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="cd0f3-373">Modelin giriş ve çıkış katmanlarının adını görselleştirmek için, [netron](https://github.com/lutzroeder/netron)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-373">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="cd0f3-374">Ardından, Puanlama için kullanılan ilk yöntem kümesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-374">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="cd0f3-375">Sınıfınızıniçindeki`OnnxModelScorer`yöntemioluşturun. `LoadModel`</span><span class="sxs-lookup"><span data-stu-id="cd0f3-375">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="cd0f3-376">`LoadModel` Yöntemi içinde günlüğe kaydetmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-376">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="cd0f3-377">ML.NET işlem hatları, [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) yöntemi çağrıldığında üzerinde çalışılacak veri şemasını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-377">ML.NET pipelines need to know the data schema to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="cd0f3-378">Bu durumda, eğitimle benzer bir süreç kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-378">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="cd0f3-379">Ancak, hiçbir gerçek eğitim gerçekleşmediğinden boş [`IDataView`](xref:Microsoft.ML.IDataView)kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-379">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="cd0f3-380">Boş bir listeden [`IDataView`](xref:Microsoft.ML.IDataView) işlem hattı için yeni bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-380">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    <span data-ttu-id="cd0f3-381">Bunun altında, işlem hattını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-381">Below that, define the pipeline.</span></span> <span data-ttu-id="cd0f3-382">İşlem hattı dört dönüşümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-382">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="cd0f3-383">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)görüntüyü bir bit eşlem olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-383">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="cd0f3-384">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)görüntüyü belirtilen boyuta ölçeklendirin (Bu durumda, `416 x 416`).</span><span class="sxs-lookup"><span data-stu-id="cd0f3-384">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="cd0f3-385">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)görüntünün piksel temsilini bir bit eşlemden sayısal bir Vector öğesine değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-385">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="cd0f3-386">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)ONNX modelini yükler ve belirtilen verileri öğrenmek için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-386">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="cd0f3-387">İşlem hattınızı `LoadModel` `data` değişkenin altındaki yöntemde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-387">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="cd0f3-388">Şimdi Puanlama için model oluşturma zamanı.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-388">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="cd0f3-389">İşlem hattında [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) yöntemi çağırın ve daha fazla işleme için döndürün.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-389">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="cd0f3-390">Model yüklendikten sonra tahmin yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-390">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="cd0f3-391">Bu işlemi kolaylaştırmak için `PredictDataUsingModel` `LoadModel` yönteminin altında adlı bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-391">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="cd0f3-392">`PredictDataUsingModel`İçinde, günlüğe kaydetmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-392">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="cd0f3-393">Ardından, verileri öğrenmek [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-393">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="cd0f3-394">Tahmin edilen olasılıkların ayıklanmasını ayıklayın ve bunları ek işleme için geri döndürün.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-394">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="cd0f3-395">Her iki adım de ayarlandığına göre, bunları tek bir yöntemde birleştirin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-395">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="cd0f3-396">Yönteminin altında adlı `Score`yeni bir yöntem ekleyin. `PredictDataUsingModel`</span><span class="sxs-lookup"><span data-stu-id="cd0f3-396">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="cd0f3-397">Neredeyse bitti!</span><span class="sxs-lookup"><span data-stu-id="cd0f3-397">Almost there!</span></span> <span data-ttu-id="cd0f3-398">Şimdi bunu tüm kullanıma yerleştirme zamanı.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-398">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="cd0f3-399">Nesneleri Algıla</span><span class="sxs-lookup"><span data-stu-id="cd0f3-399">Detect objects</span></span>

<span data-ttu-id="cd0f3-400">Tüm kurulumun tamamlandığına göre, bazı nesneleri algılamaya zaman atalım.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-400">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="cd0f3-401">*Program.cs* sınıfınıza scorer ve ayrıştırıcıya başvurular ekleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-401">Start off by adding references to the scorer and parser in your *Program.cs* class.</span></span>

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a><span data-ttu-id="cd0f3-402">Model çıkışlarını puan ve ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="cd0f3-402">Score and parse model outputs</span></span>

<span data-ttu-id="cd0f3-403">`Main` *Program.cs* sınıfınızın yöntemi içinde, bir try-catch ifadesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-403">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="cd0f3-404">`try` Bloğun içinde, nesne algılama mantığını uygulamaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-404">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="cd0f3-405">İlk olarak, verileri bir [`IDataView`](xref:Microsoft.ML.IDataView)öğesine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-405">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="cd0f3-406">Ardından, bir örneği `OnnxModelScorer` oluşturun ve yüklenen verileri almak için onu kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-406">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="cd0f3-407">Şimdi işleme sonrası adımının zamanı.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-407">Now it's time for the post-processing step.</span></span> <span data-ttu-id="cd0f3-408">Bir örneği `YoloOutputParser` oluşturun ve model çıkışını işlemek için onu kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-408">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="cd0f3-409">Model çıkışı işlendikten sonra, görüntülerde sınırlayıcı kutuları çizmeniz zaman alır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-409">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span>

### <a name="visualize-predictions"></a><span data-ttu-id="cd0f3-410">Tahminleri görselleştirin</span><span class="sxs-lookup"><span data-stu-id="cd0f3-410">Visualize predictions</span></span>

<span data-ttu-id="cd0f3-411">Model, görüntüleri puanladıktan ve çıktılar işlendikten sonra, görüntü üzerinde sınırlayıcı kutular çizmelidir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-411">After the model has scored the images and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="cd0f3-412">Bunu yapmak için `DrawBoundingBox` *program.cs*içindeki `GetAbsolutePath` yönteminin altına adlı bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-412">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method inside of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="cd0f3-413">İlk olarak, görüntüyü yükleyin ve `DrawBoundingBox` yöntemdeki yükseklik ve genişlik boyutlarını alın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-413">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="cd0f3-414">Ardından, model tarafından algılanan her bir sınırlayıcı kutu üzerinde yinelemek için her bir For-Each döngüsü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-414">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="cd0f3-415">For-each döngüsünün içinde, sınırlayıcı kutunun boyutlarını alın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-415">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="cd0f3-416">Sınırlayıcı kutunun boyutları model girişine `416 x 416`karşılık geldiğinden, sınırlayıcı kutu boyutlarını görüntünün gerçek boyutuyla eşleşecek şekilde ölçeklendirin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-416">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="cd0f3-417">Ardından, her bir sınırlayıcı kutusunun üzerinde görünecek metin için bir şablon tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-417">Then, define a template for text that will appear above each bounding box.</span></span> <span data-ttu-id="cd0f3-418">Metin, ilgili sınırlayıcı kutusunun içindeki nesnenin sınıfını ve güveni içerir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-418">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="cd0f3-419">Görüntüde çizim yapmak için bir [`Graphics`](xref:System.Drawing.Graphics) nesneye dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-419">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

<span data-ttu-id="cd0f3-420">Kod bloğunun içinde, [`Graphics`](xref:System.Drawing.Graphics) grafiğin nesne ayarlarını ayarlayın. `using`</span><span class="sxs-lookup"><span data-stu-id="cd0f3-420">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="cd0f3-421">Bunun altında metin ve sınırlayıcı kutusu için yazı tipi ve renk seçeneklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-421">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="cd0f3-422">[`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) Yöntemi kullanarak metni içermesi için sınırlayıcı kutunun üzerindeki bir dikdörtgeni oluşturun ve girin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-422">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="cd0f3-423">Bu, metnin karşıtlığına ve okunabilirliği iyileştirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-423">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="cd0f3-424">Ardından, [`DrawString`](xref:System.Drawing.Graphics.DrawString*) ve [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) yöntemlerini kullanarak görüntüye metin ve sınırlayıcı kutusunu çizin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-424">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="cd0f3-425">For-each döngüsünün dışında, içindeki `outputDirectory`görüntüleri kaydetmek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-425">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="cd0f3-426">Uygulamanın çalışma zamanında beklendiği gibi tahmine dayalı hale getiren ek geri bildirimde bulunmak için, algılanan nesneleri konsola çıkarmak `LogDetectedObjects` üzere program.cs `DrawBoundingBox` dosyasındaki yönteminin altına adlı bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-426">For additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="cd0f3-427">Tahmine dayalı olarak görsel geri bildirim oluşturmaya yönelik yardımcı yöntemlere sahip olduğunuza göre, her bir puanlanmış görüntünün üzerinde yinelemek için bir for döngüsü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-427">Now that you have helper methods to create visual feedback from the predictions, add a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="cd0f3-428">For döngüsü içinde, görüntü dosyasının adını ve onunla ilişkili sınırlayıcı kutuları alın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-428">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="cd0f3-429">Bunun altında, görüntüdeki sınırlayıcı `DrawBoundingBox` kutuları çizmek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-429">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="cd0f3-430">Son olarak,, `LogDetectedObjects` tahmine dayalı olarak konsola çıkış yapmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-430">Lastly, use the `LogDetectedObjects` method to output predictions to the console.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

<span data-ttu-id="cd0f3-431">Try-catch ifadesinden sonra, işlemin çalıştığını göstermek için ek mantık ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-431">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="cd0f3-432">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="cd0f3-432">That's it!</span></span>

## <a name="results"></a><span data-ttu-id="cd0f3-433">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="cd0f3-433">Results</span></span>

<span data-ttu-id="cd0f3-434">Önceki adımları uyguladıktan sonra konsol uygulamanızı çalıştırın (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="cd0f3-434">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="cd0f3-435">Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-435">Your results should be similar to the following output.</span></span> <span data-ttu-id="cd0f3-436">Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-436">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="cd0f3-437">Sınırlayıcı kutuları olan görüntüleri görmek için `assets/images/output/` dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-437">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="cd0f3-438">Aşağıda, işlenen görüntülerden birindeki bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-438">Below is a sample from one of the processed images.</span></span>

![](./media/object-detection-onnx/image3.jpg)

<span data-ttu-id="cd0f3-439">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="cd0f3-439">Congratulations!</span></span> <span data-ttu-id="cd0f3-440">Artık ml.net ' de önceden eğitilen `ONNX` bir modeli yeniden çalıştırarak nesne algılama için bir makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-440">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="cd0f3-441">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-441">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="cd0f3-442">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="cd0f3-442">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="cd0f3-443">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="cd0f3-443">Understand the problem</span></span>
> - <span data-ttu-id="cd0f3-444">ONNX 'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin</span><span class="sxs-lookup"><span data-stu-id="cd0f3-444">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="cd0f3-445">Modeli anlama</span><span class="sxs-lookup"><span data-stu-id="cd0f3-445">Understand the model</span></span>
> - <span data-ttu-id="cd0f3-446">Önceden eğitilen modeli yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="cd0f3-446">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="cd0f3-447">Yüklü bir modelle nesneleri Algıla</span><span class="sxs-lookup"><span data-stu-id="cd0f3-447">Detect objects with a loaded model</span></span>

<span data-ttu-id="cd0f3-448">Genişletilmiş bir nesne algılama örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="cd0f3-448">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="cd0f3-449">DotNet/machinöğrenim-Samples GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="cd0f3-449">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/DeepLearning_ObjectDetection_Onnx)
