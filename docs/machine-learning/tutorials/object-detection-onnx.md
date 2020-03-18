---
title: 'Öğretici: ONNX derin öğrenme modelini kullanarak nesneleri algılama'
description: Bu öğretici, görüntülerdeki nesneleri algılamak için ML.NET önceden eğitilmiş bir ONNX derin öğrenme modelinin nasıl kullanılacağını göstermektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ff9986c09e39f5c4d24f52c351db6455ff63e77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092726"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="72838-103">Öğretici: ML.NET ONNX kullanarak nesneleri algılama</span><span class="sxs-lookup"><span data-stu-id="72838-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="72838-104">Görüntülerdeki nesneleri algılamak için ML.NET önceden eğitilmiş bir ONNX modelini nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="72838-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="72838-105">Bir nesne algılama modelini sıfırdan eğitmek için milyonlarca parametre, büyük miktarda etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) gerekir.</span><span class="sxs-lookup"><span data-stu-id="72838-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="72838-106">Önceden eğitilmiş bir model kullanmak, eğitim sürecini kısayolla kesmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="72838-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="72838-107">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72838-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="72838-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="72838-108">Understand the problem</span></span>
> - <span data-ttu-id="72838-109">ONNX'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin</span><span class="sxs-lookup"><span data-stu-id="72838-109">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="72838-110">Modeli anlama</span><span class="sxs-lookup"><span data-stu-id="72838-110">Understand the model</span></span>
> - <span data-ttu-id="72838-111">Önceden eğitilmiş modeli yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="72838-111">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="72838-112">Yüklü bir modelle nesneleri algılama</span><span class="sxs-lookup"><span data-stu-id="72838-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="72838-113">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="72838-113">Pre-requisites</span></span>

- <span data-ttu-id="72838-114">[Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="72838-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="72838-115">Microsoft.ML NuGet Paketi</span><span class="sxs-lookup"><span data-stu-id="72838-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="72838-116">Microsoft.ML.ImageAnalytics NuGet Paketi</span><span class="sxs-lookup"><span data-stu-id="72838-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="72838-117">Microsoft.ML.OnnxTransformer NuGet Paketi</span><span class="sxs-lookup"><span data-stu-id="72838-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="72838-118">Tiny YOLOv2 önceden eğitilmiş model</span><span class="sxs-lookup"><span data-stu-id="72838-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- <span data-ttu-id="72838-119">[Netron](https://github.com/lutzroeder/netron) (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="72838-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="72838-120">ONNX nesne algılama örneği genel bakış</span><span class="sxs-lookup"><span data-stu-id="72838-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="72838-121">Bu örnek, önceden eğitilmiş derin öğrenme ONNX modelini kullanarak görüntü içindeki nesneleri algılayan bir .NET çekirdek konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72838-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="72838-122">Bu örneğin kodu GitHub'daki [dotnet/machinelearning-samples deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="72838-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="72838-123">Nesne algılama nedir?</span><span class="sxs-lookup"><span data-stu-id="72838-123">What is object detection?</span></span>

<span data-ttu-id="72838-124">Nesne algılama bir bilgisayar görme sorunudur.</span><span class="sxs-lookup"><span data-stu-id="72838-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="72838-125">Görüntü sınıflandırması ile yakından ilişkili olmakla birlikte, nesne algılama daha ayrıntılı bir ölçekte görüntü sınıflandırması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="72838-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="72838-126">Nesne algılama, görüntülerdeki varlıkları hem bulur hem de _kategorilere_ ayırar.</span><span class="sxs-lookup"><span data-stu-id="72838-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="72838-127">Görüntüler farklı türde birden çok nesne içeriyorsa nesne algılamayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-127">Use object detection when images contain multiple objects of different types.</span></span>

![Görüntü Sınıflandırması ile Nesne Sınıflandırması'nı gösteren ekran görüntüleri.](./media/object-detection-onnx/img-classification-obj-detection.png)

<span data-ttu-id="72838-129">Nesne algılama için bazı kullanım örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="72838-129">Some use cases for object detection include:</span></span>

- <span data-ttu-id="72838-130">Kendi Kendine Giden Arabalar</span><span class="sxs-lookup"><span data-stu-id="72838-130">Self-Driving Cars</span></span>
- <span data-ttu-id="72838-131">Robotik</span><span class="sxs-lookup"><span data-stu-id="72838-131">Robotics</span></span>
- <span data-ttu-id="72838-132">Yüz Algılama</span><span class="sxs-lookup"><span data-stu-id="72838-132">Face Detection</span></span>
- <span data-ttu-id="72838-133">İşyeri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="72838-133">Workplace Safety</span></span>
- <span data-ttu-id="72838-134">Nesne Sayma</span><span class="sxs-lookup"><span data-stu-id="72838-134">Object Counting</span></span>
- <span data-ttu-id="72838-135">Etkinlik Tanıma</span><span class="sxs-lookup"><span data-stu-id="72838-135">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="72838-136">Derin öğrenme modeli seçin</span><span class="sxs-lookup"><span data-stu-id="72838-136">Select a deep learning model</span></span>

<span data-ttu-id="72838-137">Derin öğrenme, makine öğreniminin bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="72838-137">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="72838-138">Derin öğrenme modellerini eğitmek için büyük miktarlarda veri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="72838-138">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="72838-139">Verilerdeki desenler bir dizi katmanla temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="72838-139">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="72838-140">Verilerdeki ilişkiler ağırlıkiçeren katmanlar arasındaki bağlantı olarak kodlanır.</span><span class="sxs-lookup"><span data-stu-id="72838-140">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="72838-141">Ağırlık ne kadar yüksekse, ilişki o kadar güçlü.</span><span class="sxs-lookup"><span data-stu-id="72838-141">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="72838-142">Topluca, katmanları ve bağlantıların bu dizi yapay sinir ağları olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="72838-142">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="72838-143">Bir ağ da daha fazla katman, "derin" o, derin bir sinir ağı yapma.</span><span class="sxs-lookup"><span data-stu-id="72838-143">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span>

<span data-ttu-id="72838-144">Çok Katmanlı Perceptron (MLP), Kvolürtional Nöral Ağ (CNN) ve Tekrarlayan Sinir Ağı (RNN) olmak üzere farklı sinir ağları türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="72838-144">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="72838-145">En temel işlem kümesini bir biriçe çıkaran MLP' dir.</span><span class="sxs-lookup"><span data-stu-id="72838-145">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="72838-146">Veriler uzamsal veya zaman bileşeni olmadığında bu sinir ağı iyidir.</span><span class="sxs-lookup"><span data-stu-id="72838-146">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="72838-147">CNN, verilerde bulunan uzamsal bilgileri işlemek için kıvrımlı katmanları kullanır.</span><span class="sxs-lookup"><span data-stu-id="72838-147">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="72838-148">CNN'ler için iyi bir kullanım örneği, görüntünün bir bölgesinde bir özelliğin varlığını algılamak için görüntü işlemedir (örneğin, görüntünün ortasında bir burun var mıdır?).</span><span class="sxs-lookup"><span data-stu-id="72838-148">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="72838-149">Son olarak, RN'ler durum veya belleğin kalıcılığının girdi olarak kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="72838-149">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="72838-150">RN'ler, olayların sıralı sıralama ve bağlamının önemli olduğu zaman serisi çözümlemesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72838-150">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span>

### <a name="understand-the-model"></a><span data-ttu-id="72838-151">Modeli anlama</span><span class="sxs-lookup"><span data-stu-id="72838-151">Understand the model</span></span>

<span data-ttu-id="72838-152">Nesne algılama bir görüntü işleme görevidir.</span><span class="sxs-lookup"><span data-stu-id="72838-152">Object detection is an image-processing task.</span></span> <span data-ttu-id="72838-153">Bu nedenle, bu sorunu çözmek için eğitilmiş en derin öğrenme modelleri CNNs vardır.</span><span class="sxs-lookup"><span data-stu-id="72838-153">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="72838-154">Bu öğretici kullanılan model Tiny YOLOv2 modeli, YOLOv2 modeli kağıt açıklanan daha kompakt bir versiyonu: ["YOLO9000: Daha Iyi, Daha Hızlı, Güçlü" Redmon ve Fadhari tarafından](https://arxiv.org/pdf/1612.08242.pdf).</span><span class="sxs-lookup"><span data-stu-id="72838-154">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="72838-155">Tiny YOLOv2 Pascal VOC veri seti üzerinde eğitilmiştir ve nesnelerin 20 farklı sınıfları tahmin edebilirsiniz 15 katmanları oluşur.</span><span class="sxs-lookup"><span data-stu-id="72838-155">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="72838-156">Tiny YOLOv2 orijinal YOLOv2 modelinin yoğunlaştırılmış bir versiyonu olduğundan, hız ve doğruluk arasında bir denge yapılır.</span><span class="sxs-lookup"><span data-stu-id="72838-156">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="72838-157">Modeli oluşturan farklı katmanlar Netron gibi araçlar kullanılarak görselleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="72838-157">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="72838-158">Modelin incelenmesi, her bir katmanın ilgili giriş / çıkış boyutlarıyla birlikte katmanın adını içereceği sinir ağını oluşturan tüm katmanlar arasındaki bağlantıların eşlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="72838-158">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="72838-159">Modelin giriş ve çıkışlarını tanımlamak için kullanılan veri yapıları tensör olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="72838-159">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="72838-160">Tentenler, verileri N boyutlu olarak depolayan kapsayıcılar olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="72838-160">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="72838-161">Tiny YOLOv2 durumunda, giriş katmanının adı ve `image` boyutları `3 x 416 x 416`bir tensor bekliyor.</span><span class="sxs-lookup"><span data-stu-id="72838-161">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="72838-162">Çıkış katmanının adı `grid` ve boyutların `125 x 13 x 13`bir çıkış tensörü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72838-162">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>

![Giriş katmanı gizli katmanlara bölündükten sonra çıktı katmanı](./media/object-detection-onnx/netron-model-map-layers.png)

<span data-ttu-id="72838-164">YOLO modeli bir `3(RGB) x 416px x 416px`görüntü alır.</span><span class="sxs-lookup"><span data-stu-id="72838-164">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="72838-165">Model bu girişi alır ve bir çıktı üretmek için farklı katmanlar aracılığıyla geçer.</span><span class="sxs-lookup"><span data-stu-id="72838-165">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="72838-166">Çıktı, giriş görüntüsünü, ızgaradaki `13 x 13` her hücre değerlerden `125` oluşan bir ızgaraya böler.</span><span class="sxs-lookup"><span data-stu-id="72838-166">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span>

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="72838-167">ONNX modeli nedir?</span><span class="sxs-lookup"><span data-stu-id="72838-167">What is an ONNX model?</span></span>

<span data-ttu-id="72838-168">Açık Sinir Ağ Değişimi (ONNX), AI modelleri için açık kaynak biçimidir.</span><span class="sxs-lookup"><span data-stu-id="72838-168">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="72838-169">ONNX, çerçeveler arasında birlikte çalışabilirliği destekler.</span><span class="sxs-lookup"><span data-stu-id="72838-169">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="72838-170">Bu, PyTorch gibi birçok popüler makine öğrenme çerçevelerinden birinde bir model eğitebileceğiniz, ONNX formatına dönüştürebileceğiniz ve ONNX modelini ML.NET gibi farklı bir çerçevede kullanabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="72838-170">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="72838-171">Daha fazla bilgi için [ONNX web sitesini](https://onnx.ai/)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="72838-171">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span>

![ONNX destekli biçimlerin diyagramı kullanılıyor.](./media/object-detection-onnx/onnx-supported-formats.png)

<span data-ttu-id="72838-173">Önceden eğitilmiş Tiny YOLOv2 modeli ONNX formatında depolanır, katmanların seri leştirilmiş bir gösterimi ve bu katmanların öğrenilen desenleri.</span><span class="sxs-lookup"><span data-stu-id="72838-173">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="72838-174">ML.NET'da ONNX [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) ile birlikte çalışabilirlik [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) ve NuGet paketleri ile sağlanır.</span><span class="sxs-lookup"><span data-stu-id="72838-174">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="72838-175">Paket, [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) bir görüntüyü alıp bir tahmin veya eğitim ardışık dizisine girdi olarak kullanılabilecek sayısal değerlere kodlayan bir dizi dönüşüm içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-175">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="72838-176">Paket, [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) onnx modelini yüklemek ve sağlanan girdiye dayalı öngörülerde bulunmak için onnx çalışma süresinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="72838-176">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span>

![ONNX dosyasının ONNX Runtime'a veri akışı.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="72838-178">.NET Core projesini ayarlama</span><span class="sxs-lookup"><span data-stu-id="72838-178">Set up the .NET Core project</span></span>

<span data-ttu-id="72838-179">Şimdi ONNX ne olduğunu ve nasıl Tiny YOLOv2 çalışır genel bir anlayışa sahip, bu uygulama oluşturmak için zamanı.</span><span class="sxs-lookup"><span data-stu-id="72838-179">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="72838-180">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="72838-180">Create a console application</span></span>

1. <span data-ttu-id="72838-181">"ObjectDetection" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-181">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="72838-182">Microsoft.ML **NuGet Paketini**Yükleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-182">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="72838-183">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-183">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    - <span data-ttu-id="72838-184">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML**arayın.</span><span class="sxs-lookup"><span data-stu-id="72838-184">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    - <span data-ttu-id="72838-185">**Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-185">Select the **Install** button.</span></span>
    - <span data-ttu-id="72838-186">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-186">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    - <span data-ttu-id="72838-187">**Microsoft.ML.ImageAnalytics** ve **Microsoft.ML.OnnxTransformer**için bu adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-187">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="72838-188">Verilerinizi ve önceden eğitilmiş modeli hazırlayın</span><span class="sxs-lookup"><span data-stu-id="72838-188">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="72838-189">[Proje varlıkları dizin zip dosyasını](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) indirin ve zip'i açın.</span><span class="sxs-lookup"><span data-stu-id="72838-189">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="72838-190">`assets` Dizini *ObjectDetection* proje dizininize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="72838-190">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="72838-191">Bu dizin ve alt dizinleri bu öğretici için gerekli olan resim dosyalarını (bir sonraki adımda indirip ekleyeceğiniz Tiny YOLOv2 modeli hariç) içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-191">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="72838-192">[ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2) [Tiny YOLOv2 modeli](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) indirin , ve unzip.</span><span class="sxs-lookup"><span data-stu-id="72838-192">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="72838-193">Komut istemini açın ve aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="72838-193">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. <span data-ttu-id="72838-194">Çıkarılan `model.onnx` dosyayı dizinden yalnızca *ObjectDetection* proje `assets\Model` dizininizin fermuarlı içine `TinyYolo2_model.onnx`kopyalayın ve yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="72838-194">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="72838-195">Bu dizin, bu öğretici için gerekli modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-195">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="72838-196">Çözüm Gezgini'nde, varlık dizini ve alt dizinindeki dosyaların her birini sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-196">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="72838-197">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72838-197">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="72838-198">Sınıflar oluşturma ve yolları tanımlama</span><span class="sxs-lookup"><span data-stu-id="72838-198">Create classes and define paths</span></span>

<span data-ttu-id="72838-199">*Program.cs* dosyasını açın ve `using` dosyanın üst üstüne aşağıdaki ek deyimleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-199">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

<span data-ttu-id="72838-200">Ardından, çeşitli varlıkların yollarını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-200">Next, define the paths of the various assets.</span></span>

1. <span data-ttu-id="72838-201">İlk olarak, `GetAbsolutePath` `Program` sınıfta `Main` yöntemin altına yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-201">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span>

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="72838-202">Ardından, yöntemin `Main` içinde, varlıklarınızın konumunu depolamak için alanlar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-202">Then, inside the `Main` method, create fields to store the location of your assets.</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="72838-203">Giriş verilerinizi ve tahmin sınıflarınızı depolamak için projenize yeni bir dizin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-203">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="72838-204">**Çözüm Gezgini'nde**projeyi sağ tıklatın ve ardından**Yeni Klasör** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-204">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="72838-205">Çözüm Gezgini'nde yeni klasör göründüğünde, "Veri Yapıları" adını verin.</span><span class="sxs-lookup"><span data-stu-id="72838-205">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="72838-206">Yeni oluşturulan *DataStructures* dizininde giriş veri sınıfını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-206">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="72838-207">**Çözüm Gezgini'nde,** *DataStructures* dizinini sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-207">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="72838-208">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *ImageNetData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72838-208">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="72838-209">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-209">Then, select the **Add** button.</span></span>

    <span data-ttu-id="72838-210">*ImageNetData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="72838-210">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="72838-211">ImageNetData.cs üstüne `using` aşağıdaki ifadeyi *ImageNetData.cs*ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-211">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="72838-212">Varolan sınıf tanımını kaldırın ve `ImageNetData` *ImageNetData.cs* dosyasına sınıf için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-212">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="72838-213">`ImageNetData`giriş görüntü veri sınıfıdır ve <xref:System.String> aşağıdaki alanlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="72838-213">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="72838-214">`ImagePath`görüntünün depolandığı yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-214">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="72838-215">`Label`dosyanın adını içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-215">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="72838-216">Ayrıca, `ImageNetData` belirtilen `ReadFromFile` `imageFolder` yolda depolanan birden çok resim dosyasını yükleyen ve `ImageNetData` bunları nesne koleksiyonu olarak döndüren bir yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-216">Additionally, `ImageNetData` contains a method `ReadFromFile` that loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="72838-217">*Veri Yapıları* dizininde tahmin sınıfınızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-217">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="72838-218">**Çözüm Gezgini'nde,** *DataStructures* dizinini sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-218">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="72838-219">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *ImageNetPrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72838-219">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="72838-220">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-220">Then, select the **Add** button.</span></span>

    <span data-ttu-id="72838-221">*ImageNetPrediction.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="72838-221">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="72838-222">ImageNetPrediction.cs üstüne `using` aşağıdaki ifadeyi *ImageNetPrediction.cs*ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-222">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="72838-223">Varolan sınıf tanımını kaldırın ve `ImageNetPrediction` *ImageNetPrediction.cs* dosyasına sınıf için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-223">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="72838-224">`ImageNetPrediction`tahmin veri sınıfıdır ve `float[]` aşağıdaki alana sahiptir:</span><span class="sxs-lookup"><span data-stu-id="72838-224">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="72838-225">`PredictedLabel`görüntüde algılanan sınırlayıcı kutuların her biri için boyutlar, nesnelik puanı ve sınıf olasılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-225">`PredictedLabel` contains the dimensions, objectness score, and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="72838-226">Main'deki değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="72838-226">Initialize variables in Main</span></span>

<span data-ttu-id="72838-227">[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç `mlContext` noktasıdır ve başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72838-227">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="72838-228">Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.</span><span class="sxs-lookup"><span data-stu-id="72838-228">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="72838-229">`outputFolder` Alanın altındaki `mlContext` *Program.cs* `Main` yöntemine `MLContext` aşağıdaki satırı ekleyerek değişkeni yeni bir örnekle başolarak adlandırır.</span><span class="sxs-lookup"><span data-stu-id="72838-229">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="72838-230">İşlem sonrası model çıktıları için ayrıştırıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="72838-230">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="72838-231">Model, görüntüyü her ızgara `13 x 13` hücresinin olduğu `32px x 32px`bir ızgaraya böler.</span><span class="sxs-lookup"><span data-stu-id="72838-231">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="72838-232">Her ızgara hücresi 5 potansiyel nesne sınırlayıcı kutu içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-232">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="72838-233">Sınırlayıcı kutuda 25 öğe vardır:</span><span class="sxs-lookup"><span data-stu-id="72838-233">A bounding box has  25 elements:</span></span>

![Soldaki Kılavuz örneği ve sağdaki Sınırlayıcı Kutu örneği](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="72838-235">`x`ilişkili olduğu ızgara hücresine göre sınırlayıcı kutu merkezinin x konumu.</span><span class="sxs-lookup"><span data-stu-id="72838-235">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="72838-236">`y`ilişkili olduğu ızgara hücresine göre sınırlayıcı kutu merkezinin y konumu.</span><span class="sxs-lookup"><span data-stu-id="72838-236">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="72838-237">`w`sınırlayıcı kutunun genişliği.</span><span class="sxs-lookup"><span data-stu-id="72838-237">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="72838-238">`h`sınırlama kutusunun yüksekliği.</span><span class="sxs-lookup"><span data-stu-id="72838-238">`h` the height of the bounding box.</span></span>
- <span data-ttu-id="72838-239">`o`nesnelik puanı olarak da bilinen sınırlayıcı kutu içinde bir nesnenin bulunduğu güven değeri.</span><span class="sxs-lookup"><span data-stu-id="72838-239">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="72838-240">`p1-p20`model tarafından öngörülen 20 sınıfın her biri için sınıf olasılıkları.</span><span class="sxs-lookup"><span data-stu-id="72838-240">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="72838-241">Toplamda, 5 sınırlama kutusunun her birini açıklayan 25 eleman, her bir ızgara hücresinde bulunan 125 öğeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-241">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="72838-242">Önceden eğitilmiş ONNX modeli tarafından oluşturulan çıktı, `21125`boyutları `125 x 13 x 13`olan bir tensörün elemanlarını temsil eden bir float uzunluğu dizisidir.</span><span class="sxs-lookup"><span data-stu-id="72838-242">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="72838-243">Model tarafından oluşturulan öngörüleri bir tentöre dönüştürmek için bazı işlem sonrası çalışmalar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="72838-243">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="72838-244">Bunu yapmak için, çıktıyı ayrıştırmaya yardımcı olacak bir sınıf kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-244">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="72838-245">Ayrıştırıcı sınıfları kümesini düzenlemek için projenize yeni bir dizin ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-245">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="72838-246">**Çözüm Gezgini'nde**projeyi sağ tıklatın ve ardından**Yeni Klasör** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-246">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="72838-247">Çözüm Gezgini'nde yeni klasör göründüğünde, "YoloParser" adını verdi.</span><span class="sxs-lookup"><span data-stu-id="72838-247">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="72838-248">Sınırlayıcı kutular ve boyutlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="72838-248">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="72838-249">Model tarafından veri çıktısı, görüntü içindeki nesnelerin sınırlayıcı kutularının koordinatlarını ve boyutlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-249">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="72838-250">Boyutlar için bir taban sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-250">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="72838-251">**Çözüm Gezgini'nde,** *YoloParser* dizinine sağ tıklayın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-251">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="72838-252">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *DimensionsBase.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72838-252">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="72838-253">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-253">Then, select the **Add** button.</span></span>

    <span data-ttu-id="72838-254">kod düzenleyicisinde *DimensionsBase.cs* dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="72838-254">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="72838-255">Tüm `using` deyimleri ve varolan sınıf tanımını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="72838-255">Remove all `using` statements and existing class definition.</span></span>

    <span data-ttu-id="72838-256">`DimensionsBase` *DimensionsBase.cs* dosyasına sınıf için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-256">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="72838-257">`DimensionsBase`aşağıdaki `float` özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="72838-257">`DimensionsBase` has the following `float` properties:</span></span>

    - <span data-ttu-id="72838-258">`X`x ekseni boyunca nesnenin konumunu içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-258">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="72838-259">`Y`y ekseni boyunca nesnenin konumunu içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-259">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="72838-260">`Height`nesnenin yüksekliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-260">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="72838-261">`Width`nesnenin genişliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-261">`Width` contains the width of the object.</span></span>

<span data-ttu-id="72838-262">Ardından, sınırlayıcı kutularınız için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-262">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="72838-263">**Çözüm Gezgini'nde,** *YoloParser* dizinine sağ tıklayın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-263">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="72838-264">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *YoloBoundingBox.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72838-264">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="72838-265">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-265">Then, select the **Add** button.</span></span>

    <span data-ttu-id="72838-266">kod düzenleyicisinde *YoloBoundingBox.cs* dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="72838-266">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="72838-267">YoloBoundingBox.cs üstüne `using` aşağıdaki ifadeyi *YoloBoundingBox.cs*ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-267">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="72838-268">Varolan sınıf tanımının hemen üzerinde, `BoundingBoxDimensions` ilgili sınırlayıcı `DimensionsBase` kutunun boyutlarını içerecek şekilde sınıftan devralan yeni bir sınıf tanımı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-268">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` that inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="72838-269">Varolan `YoloBoundingBox` sınıf tanımını kaldırın ve `YoloBoundingBox` *YoloBoundingBox.cs* dosyasına sınıf için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-269">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    <span data-ttu-id="72838-270">`YoloBoundingBox`aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="72838-270">`YoloBoundingBox` has the following properties:</span></span>

    - <span data-ttu-id="72838-271">`Dimensions`sınırlayıcı kutunun boyutlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-271">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="72838-272">`Label`sınırlama kutusu içinde algılanan nesnenin sınıfını içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-272">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="72838-273">`Confidence`sınıfın güvenini içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-273">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="72838-274">`Rect`sınırlayıcı kutunun boyutlarının dikdörtgen gösterimini içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-274">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="72838-275">`BoxColor`görüntüüzerinde çizmek için kullanılan ilgili sınıfile ilişkili renk içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-275">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="72838-276">Ayrıştırıcıyı oluşturma</span><span class="sxs-lookup"><span data-stu-id="72838-276">Create the parser</span></span>

<span data-ttu-id="72838-277">Şimdi boyutlar ve sınırlayıcı kutular için sınıflar oluşturulduğuna göre, ayrıştırıcıyı oluşturma nın zamanı geliyor.</span><span class="sxs-lookup"><span data-stu-id="72838-277">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="72838-278">**Çözüm Gezgini'nde,** *YoloParser* dizinine sağ tıklayın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-278">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="72838-279">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *YoloOutputParser.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72838-279">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="72838-280">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-280">Then, select the **Add** button.</span></span>

    <span data-ttu-id="72838-281">kod düzenleyicisinde *YoloOutputParser.cs* dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="72838-281">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="72838-282">YoloOutputParser.cs üstüne `using` aşağıdaki ifadeyi *YoloOutputParser.cs*ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-282">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="72838-283">Varolan `YoloOutputParser` sınıf tanımının içinde, görüntüdeki her hücrenin boyutlarını içeren iç içe geçmiş bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-283">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="72838-284">Sınıf tanımının `CellDimensions` en üstündeki `DimensionsBase` sınıftan devralan sınıf için aşağıdaki kodu ekleyin. `YoloOutputParser`</span><span class="sxs-lookup"><span data-stu-id="72838-284">Add the following code for the `CellDimensions` class that inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="72838-285">Sınıf `YoloOutputParser` tanımının içine aşağıdaki sabitleri ve alanları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-285">Inside the `YoloOutputParser` class definition, add the following constants and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - <span data-ttu-id="72838-286">`ROW_COUNT`görüntünün bölündüğü ızgaradaki satır sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="72838-286">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="72838-287">`COL_COUNT`görüntünün bölündüğü ızgaradaki sütun sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="72838-287">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="72838-288">`CHANNEL_COUNT`ızgaranın bir hücresinde bulunan değerlerin toplam sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="72838-288">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="72838-289">`BOXES_PER_CELL`bir hücredeki sınırlayıcı kutuların sayısıdır,</span><span class="sxs-lookup"><span data-stu-id="72838-289">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="72838-290">`BOX_INFO_FEATURE_COUNT`kutunun içinde bulunan özellik sayısıdır (x,y,yükseklik,genişlik,güven).</span><span class="sxs-lookup"><span data-stu-id="72838-290">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="72838-291">`CLASS_COUNT`her sınırlayıcı kutuda bulunan sınıf tahminlerinin sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="72838-291">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="72838-292">`CELL_WIDTH`görüntü ızgarasındaki bir hücrenin genişliğidir.</span><span class="sxs-lookup"><span data-stu-id="72838-292">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="72838-293">`CELL_HEIGHT`görüntü ızgarasındaki bir hücrenin yüksekliğidir.</span><span class="sxs-lookup"><span data-stu-id="72838-293">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="72838-294">`channelStride`ızgaradaki geçerli hücrenin başlangıç konumudur.</span><span class="sxs-lookup"><span data-stu-id="72838-294">`channelStride` is the starting position of the current cell in the grid.</span></span>

    <span data-ttu-id="72838-295">Model puanlama olarak da bilinen bir tahmin yaptığında, `416px x 416px` giriş görüntüsünü `13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="72838-295">When the model makes a prediction, also known as scoring, it divides the `416px x 416px` input image into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="72838-296">Her hücre `32px x 32px`içerir .</span><span class="sxs-lookup"><span data-stu-id="72838-296">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="72838-297">Her hücreiçinde, her biri 5 özellik (x, y, genişlik, yükseklik, güven) içeren 5 sınırlayıcı kutu vardır.</span><span class="sxs-lookup"><span data-stu-id="72838-297">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="72838-298">Ayrıca, her sınırlayıcı kutu, bu durumda 20 olan sınıfların her birinin olasılığını içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-298">In addition, each bounding box contains the probability of each of the classes, which in this case is 20.</span></span> <span data-ttu-id="72838-299">Bu nedenle, her hücre 125 bilgi (5 özellik + 20 sınıf olasılıkları) içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-299">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span>

<span data-ttu-id="72838-300">5 sınırlayıcı kutunun `channelStride` tümü için aşağıdaki çapaların listesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="72838-300">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

<span data-ttu-id="72838-301">Çapalar, sınırlayıcı kutuların önceden tanımlanmış yükseklik ve genişlik oranlarıdır.</span><span class="sxs-lookup"><span data-stu-id="72838-301">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="72838-302">Bir model tarafından algılanan çoğu nesne veya sınıf benzer oranlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="72838-302">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="72838-303">Bu sınırlayıcı kutuları oluşturma söz konusu olduğunda değerlidir.</span><span class="sxs-lookup"><span data-stu-id="72838-303">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="72838-304">Sınırlayıcı kutuları tahmin etmek yerine, önceden tanımlanmış boyutlardan mahsup hesaplanır ve bu nedenle sınırlayıcı kutuyu tahmin etmek için gereken hesaplama azaltılır.</span><span class="sxs-lookup"><span data-stu-id="72838-304">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="72838-305">Genellikle bu bağlantı oranları kullanılan veri kümesine göre hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="72838-305">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="72838-306">Bu durumda, veri kümesi bilindiğinden ve değerler önceden hesaplandığı için, çapalar sabit kodlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="72838-306">In this case, because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="72838-307">Ardından, modelin tahmin edeceği etiketleri veya sınıfları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-307">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="72838-308">Bu model, orijinal YOLOv2 modeli tarafından öngörülen toplam sınıf sayısının bir alt kümesi olan 20 sınıfı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="72838-308">This model predicts 20 classes, which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="72838-309">Etiket listenizi aşağıdaki `anchors`' nin altına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-309">Add your list of labels below the `anchors`.</span></span>

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="72838-310">Sınıfların her biriyle ilişkili renkler vardır.</span><span class="sxs-lookup"><span data-stu-id="72838-310">There are colors associated with each of the classes.</span></span> <span data-ttu-id="72838-311">Sınıf renklerinizi aşağıdaki `labels`lerinizin altına atamak:</span><span class="sxs-lookup"><span data-stu-id="72838-311">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="72838-312">Yardımcı işlevleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="72838-312">Create helper functions</span></span>

<span data-ttu-id="72838-313">İşlem sonrası aşamada bir dizi adım vardır.</span><span class="sxs-lookup"><span data-stu-id="72838-313">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="72838-314">Bu yardımcı olmak için, çeşitli yardımcı yöntemler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72838-314">To help with that, several helper methods can be employed.</span></span>

<span data-ttu-id="72838-315">Ayrıştırıcı tarafından kullanılan yardımcı yöntemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="72838-315">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="72838-316">`Sigmoid`0 ile 1 arasında bir sayı çıkan sigmoid işlevini uygular.</span><span class="sxs-lookup"><span data-stu-id="72838-316">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="72838-317">`Softmax`bir olasılık dağılımına giriş vektörü normalleştirir.</span><span class="sxs-lookup"><span data-stu-id="72838-317">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="72838-318">`GetOffset`tek boyutlu model çıktısındaki öğeleri bir `125 x 13 x 13` tentördeki ilgili konuma eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="72838-318">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="72838-319">`ExtractBoundingBoxes`model çıktısından `GetOffset` yöntemi kullanarak sınırlayıcı kutu boyutlarını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="72838-319">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="72838-320">`GetConfidence`modelin bir nesneyi algıladığını ve `Sigmoid` işlevi bir yüzdeye dönüştürmek için kullandığından ne kadar emin olduğunu belirten güven değerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="72838-320">`GetConfidence` extracts the confidence value that states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="72838-321">`MapBoundingBoxToCell`sınırlayıcı kutu boyutlarını kullanır ve görüntü içindeki kendi hücresine eşler.</span><span class="sxs-lookup"><span data-stu-id="72838-321">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="72838-322">`ExtractClasses`yöntemi kullanarak model çıktısı sınırlayıcı kutu için sınıf `GetOffset` tahminlerini ayıklar ve yöntemi `Softmax` kullanarak bir olasılık dağılımına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="72838-322">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="72838-323">`GetTopResult`sınıfı en yüksek olasılıkla tahmin edilen sınıflar listesinden seçer.</span><span class="sxs-lookup"><span data-stu-id="72838-323">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="72838-324">`IntersectionOverUnion`daha düşük olasılıklar ile sınırlayıcı kutuları çakışan filtreler.</span><span class="sxs-lookup"><span data-stu-id="72838-324">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="72838-325">Listenizin altındaki tüm yardımcı yöntemleriiçin kodu `classColors`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-325">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="72838-326">Tüm yardımcı yöntemleri tanımladıktan sonra, bunları model çıktısını işlemek için kullanmanın zamanı gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="72838-326">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="72838-327">Yöntemin `IntersectionOverUnion` altında, `ParseOutputs` model tarafından oluşturulan çıktıyı işlemek için yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-327">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

<span data-ttu-id="72838-328">Sınırlayıcı kutularınızı depolamak ve değişkenleri yöntemin `ParseOutputs` içinde tanımlamak için bir liste oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-328">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="72838-329">Her görüntü bir hücre `13 x 13` ızgarasına bölünür.</span><span class="sxs-lookup"><span data-stu-id="72838-329">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="72838-330">Her hücrede beş sınırlayıcı kutu bulunur.</span><span class="sxs-lookup"><span data-stu-id="72838-330">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="72838-331">Değişkenin `boxes` altında, hücrelerin her birinde tüm kutuları işlemek için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-331">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

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

<span data-ttu-id="72838-332">En içteki döngüiçinde, geçerli kutunun tek boyutlu model çıkışı içindeki başlangıç konumunu hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="72838-332">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="72838-333">Hemen altında, geçerli `ExtractBoundingBoxDimensions` sınırlayıcı kutunun boyutlarını almak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-333">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="72838-334">Ardından, geçerli `GetConfidence` sınırlayıcı kutuiçin güven almak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-334">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="72838-335">Bundan sonra, `MapBoundingBoxToCell` geçerli sınırlayıcı kutusunu işlenen geçerli hücreyle eşlemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-335">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="72838-336">Daha fazla işlem yapmadan önce, güven değerinizin sağlanan eşikten daha büyük olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="72838-336">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="72838-337">Değilse, bir sonraki sınırlayıcı kutusunu işleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-337">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="72838-338">Aksi takdirde, çıktı işlemeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="72838-338">Otherwise, continue processing the output.</span></span> <span data-ttu-id="72838-339">Bir sonraki adım, yöntemi kullanarak geçerli sınırlayıcı kutu için öngörülen sınıfların olasılık dağılımını `ExtractClasses` elde etmektir.</span><span class="sxs-lookup"><span data-stu-id="72838-339">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="72838-340">Ardından, geçerli `GetTopResult` kutu için en yüksek olasılıkla sınıfın değerini ve dizini almak ve puanını hesaplamak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-340">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="72838-341">Yalnızca `topScore` belirtilen eşiğin üzerinde olan sınırlayıcı kutuları bir kez daha tutmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-341">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="72838-342">Son olarak, geçerli sınırlayıcı kutu eşiği aşarsa, yeni `BoundingBox` bir `boxes` nesne oluşturun ve listeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-342">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="72838-343">Görüntüdeki tüm hücreler işlendikten sonra `boxes` listeyi döndürün.</span><span class="sxs-lookup"><span data-stu-id="72838-343">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="72838-344">Yöntemdeki dış-en for-for-loop'un `ParseOutputs` altına aşağıdaki dönüş deyimini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-344">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="72838-345">Çakışan kutuları filtreleme</span><span class="sxs-lookup"><span data-stu-id="72838-345">Filter overlapping boxes</span></span>

<span data-ttu-id="72838-346">Şimdi tüm son derece emin sınırlayıcı kutuları model çıktısı ayıklanmış, ek filtreleme örtüşen görüntüleri kaldırmak için yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="72838-346">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="72838-347">Yöntemin `ParseOutputs` altında `FilterBoundingBoxes` çağrılan bir yöntem ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-347">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="72838-348">Yöntemin `FilterBoundingBoxes` içinde, algılanan kutuların boyutuna eşit bir dizi oluşturarak ve tüm yuvaları etkin veya işlemehazır olarak işaretleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-348">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="72838-349">Ardından, sınırlayıcı kutularınızı içeren listeyi güvene göre azalan sırada sıralayın.</span><span class="sxs-lookup"><span data-stu-id="72838-349">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="72838-350">Bundan sonra, filtre uygulanmış sonuçları tutmak için bir liste oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-350">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="72838-351">Her sınırlayıcı kutuyu, sınırlayıcı kutuların her birinin üzerine yineleyerek işlemeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-351">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="72838-352">Bu for-loop'un içinde, geçerli sınırlayıcı kutunun işlenip işlenemeyeceğini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="72838-352">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{

}
```

<span data-ttu-id="72838-353">Bu nedenle, sınırlayıcı kutuyu sonuçlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-353">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="72838-354">Sonuçlar çıkarılacak kutuların belirtilen sınırını aşarsa, döngüden çık.</span><span class="sxs-lookup"><span data-stu-id="72838-354">If the results exceed the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="72838-355">if deyiminin içine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-355">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="72838-356">Aksi takdirde, bitişik sınırlayıcı kutulara bakın.</span><span class="sxs-lookup"><span data-stu-id="72838-356">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="72838-357">Kutu limit denetiminin altına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-357">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="72838-358">İlk kutu gibi, bitişik kutu etkinse veya işlemeye `IntersectionOverUnion` hazırsa, ilk kutu nun ve ikinci kutunun belirtilen eşiği aşıp aşmadığını denetlemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-358">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="72838-359">Aşağıdaki kodu en içteki for-loop'unuza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-359">Add the following code to your innermost for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="72838-360">Bitişik sınırlayıcı kutuları kontrol eden iç-en for-loop dışında, işlenecek kalan sınırlayıcı kutuları olup olmadığını görün.</span><span class="sxs-lookup"><span data-stu-id="72838-360">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="72838-361">Değilse, dış for-loop patlak.</span><span class="sxs-lookup"><span data-stu-id="72838-361">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="72838-362">Son olarak, `FilterBoundingBoxes` yöntemin ilk for-loop dışında, sonuçları döndürün:</span><span class="sxs-lookup"><span data-stu-id="72838-362">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="72838-363">Harika!</span><span class="sxs-lookup"><span data-stu-id="72838-363">Great!</span></span> <span data-ttu-id="72838-364">Şimdi puanlama için model ile birlikte bu kodu kullanma zamanı.</span><span class="sxs-lookup"><span data-stu-id="72838-364">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="72838-365">Puanlama için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="72838-365">Use the model for scoring</span></span>

<span data-ttu-id="72838-366">İşlem sonrası olduğu gibi, puanlama adımlarında da birkaç adım vardır.</span><span class="sxs-lookup"><span data-stu-id="72838-366">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="72838-367">Bu soruna yardımcı olmak için, projenize puanlama mantığı nı içeren bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-367">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="72838-368">**Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-368">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="72838-369">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *OnnxModelScorer.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72838-369">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="72838-370">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="72838-370">Then, select the **Add** button.</span></span>

    <span data-ttu-id="72838-371">OnnxModelScorer.cs *OnnxModelScorer.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="72838-371">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="72838-372">OnnxModelScorer.cs üstüne `using` aşağıdaki ifadeyi *OnnxModelScorer.cs*ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72838-372">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="72838-373">Sınıf `OnnxModelScorer` tanımının içine aşağıdaki değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-373">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="72838-374">Bunun hemen altında, daha önce `OnnxModelScorer` tanımlanmış değişkenleri başharfleyecek sınıf için bir oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-374">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="72838-375">Oluşturucuyu oluşturduktan sonra, görüntü ve model ayarlarıyla ilgili değişkenler içeren birkaç yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-375">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="72838-376">Model için giriş `ImageNetSettings` olarak beklenen yükseklik ve genişliği içerecek şekilde çağrılan bir yapı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-376">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="72838-377">Bundan sonra, modelin giriş `TinyYoloModelSettings` ve çıkış katmanlarının adlarını içeren başka bir yapı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-377">After that, create another struct called `TinyYoloModelSettings` that contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="72838-378">Modelin giriş ve çıkış katmanlarının adını görselleştirmek için [Netron](https://github.com/lutzroeder/netron)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72838-378">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="72838-379">Ardından, puanlama için kullanılan ilk yöntem kümesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-379">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="72838-380">Sınıfınızın `LoadModel` `OnnxModelScorer` içinde yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-380">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="72838-381">Yöntemin `LoadModel` içinde, günlüğe kaydetme için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-381">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="72838-382">ML.NET boru hatları [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) yöntem çağrıldığında çalışması için veri şemasını bilmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="72838-382">ML.NET pipelines need to know the data schema to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="72838-383">Bu durumda, eğitime benzer bir süreç kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="72838-383">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="72838-384">Ancak, gerçek bir eğitim gerçekleşmediği için, boş [`IDataView`](xref:Microsoft.ML.IDataView)bir .</span><span class="sxs-lookup"><span data-stu-id="72838-384">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="72838-385">Boş bir [`IDataView`](xref:Microsoft.ML.IDataView) listeden ardışık hatlar için yeni bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="72838-385">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    <span data-ttu-id="72838-386">Bunun altında, boru hattını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-386">Below that, define the pipeline.</span></span> <span data-ttu-id="72838-387">Boru hattı dört dönüşümden oluşacak.</span><span class="sxs-lookup"><span data-stu-id="72838-387">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="72838-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)görüntüyü Bitmap olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="72838-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="72838-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)görüntüyü belirtilen boyuta yeniden ölçeklendir (bu durumda). `416 x 416`</span><span class="sxs-lookup"><span data-stu-id="72838-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="72838-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)görüntünün piksel temsilini Bitmap'ten sayısal vektöre değiştirir.</span><span class="sxs-lookup"><span data-stu-id="72838-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="72838-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)ONNX modelini yükler ve sağlanan veriler üzerinde puan elde etmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="72838-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="72838-392">Değişkenin `LoadModel` altındaki yöntemde `data` ardışık hattınızı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-392">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="72838-393">Şimdi puanlama için modeli anında atma zamanı.</span><span class="sxs-lookup"><span data-stu-id="72838-393">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="72838-394">Ardışık [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) işlem yöntemini arayın ve daha fazla işleme için iade edin.</span><span class="sxs-lookup"><span data-stu-id="72838-394">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="72838-395">Model yüklendikten sonra, öngörülerde bulunmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72838-395">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="72838-396">Bu işlemi kolaylaştırmak için, `PredictDataUsingModel` yöntemin `LoadModel` altında adı verilen bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-396">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="72838-397">`PredictDataUsingModel`İçinde, günlüğe kaydetme için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-397">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="72838-398">Ardından, verileri [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) puanlamak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-398">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="72838-399">Öngörülen olasılıkları ayıklayın ve ek işleme için iade edin.</span><span class="sxs-lookup"><span data-stu-id="72838-399">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="72838-400">Artık her iki adım da ayarlıştın, bunları tek bir yöntemde birleştirin.</span><span class="sxs-lookup"><span data-stu-id="72838-400">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="72838-401">Yöntemin `PredictDataUsingModel` altına yeni bir `Score`yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-401">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="72838-402">Neredeyse orada!</span><span class="sxs-lookup"><span data-stu-id="72838-402">Almost there!</span></span> <span data-ttu-id="72838-403">Şimdi hepsini kullanma zamanı.</span><span class="sxs-lookup"><span data-stu-id="72838-403">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="72838-404">Nesneleri algılama</span><span class="sxs-lookup"><span data-stu-id="72838-404">Detect objects</span></span>

<span data-ttu-id="72838-405">Artık tüm kurulum tamamlandığından, bazı nesneleri algılama nın zamanı geldiğinden.</span><span class="sxs-lookup"><span data-stu-id="72838-405">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="72838-406">*Program.cs* sınıfınızdaki skorer ve ayrıştırıcıya referanslar ekleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-406">Start off by adding references to the scorer and parser in your *Program.cs* class.</span></span>

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a><span data-ttu-id="72838-407">Puan ve ayrıştırma modeli çıktıları</span><span class="sxs-lookup"><span data-stu-id="72838-407">Score and parse model outputs</span></span>

<span data-ttu-id="72838-408">Program.cs `Main` sınıfının *Program.cs* yönteminin içinde bir try-catch deyimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-408">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="72838-409">`try` Bloğun içinde nesne algılama mantığını uygulamaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-409">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="72838-410">İlk olarak, verileri [`IDataView`](xref:Microsoft.ML.IDataView)bir .</span><span class="sxs-lookup"><span data-stu-id="72838-410">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="72838-411">Ardından, bir örnek `OnnxModelScorer` oluşturun ve yüklenen verileri puanlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-411">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="72838-412">Şimdi işlem sonrası adım zamanı.</span><span class="sxs-lookup"><span data-stu-id="72838-412">Now it's time for the post-processing step.</span></span> <span data-ttu-id="72838-413">Bir örnek `YoloOutputParser` oluşturun ve model çıktısını işlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-413">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="72838-414">Model çıktısı işlendikten sonra, görüntülere sınırlayıcı kutuları çizme zamanı gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="72838-414">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span>

### <a name="visualize-predictions"></a><span data-ttu-id="72838-415">Tahminleri görselleştir</span><span class="sxs-lookup"><span data-stu-id="72838-415">Visualize predictions</span></span>

<span data-ttu-id="72838-416">Model görüntüleri attıktan ve çıktılar işlendikten sonra, sınırlayıcı kutuların görüntüüzerine çizilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="72838-416">After the model has scored the images and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="72838-417">Bunu yapmak için, `DrawBoundingBox` *Program.cs*içinde `GetAbsolutePath` yöntemin altında çağrılan bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-417">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method inside of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="72838-418">İlk olarak, görüntüyü yükleyin ve `DrawBoundingBox` yöntemde yükseklik ve genişlik boyutlarını alın.</span><span class="sxs-lookup"><span data-stu-id="72838-418">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="72838-419">Ardından, model tarafından algılanan sınırlayıcı kutuların her biri üzerinde yinelemek için her biri için bir döngü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72838-419">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="72838-420">For-each döngü içinde, sınırlayıcı kutunun boyutlarını almak.</span><span class="sxs-lookup"><span data-stu-id="72838-420">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="72838-421">Sınırlayıcı kutunun boyutları model girişine karşılık geldiği `416 x 416`için, sınırlayıcı kutu boyutlarını görüntünün gerçek boyutuyla eşleşecek şekilde ölçeklendirin.</span><span class="sxs-lookup"><span data-stu-id="72838-421">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="72838-422">Ardından, her sınırlayıcı kutunun üzerinde görünecek metin için bir şablon tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-422">Then, define a template for text that will appear above each bounding box.</span></span> <span data-ttu-id="72838-423">Metin, ilgili sınırlayıcı kutunun içindeki nesnenin sınıfını ve güveni içerir.</span><span class="sxs-lookup"><span data-stu-id="72838-423">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="72838-424">Görüntüüzerinde çizmek için, bir [`Graphics`](xref:System.Drawing.Graphics) nesneye dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="72838-424">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

<span data-ttu-id="72838-425">Kod `using` bloğunun içinde, grafiğin [`Graphics`](xref:System.Drawing.Graphics) nesne ayarlarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-425">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="72838-426">Bunun altında, metin ve sınırlayıcı kutu için yazı tipi ve renk seçeneklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="72838-426">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="72838-427">[`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) Yöntemi kullanarak metni içerecek şekilde sınırlayıcı kutunun üzerinde bir dikdörtgen oluşturun ve doldurun.</span><span class="sxs-lookup"><span data-stu-id="72838-427">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="72838-428">Bu, metnin karşıtlığını ve okunabilirliğini artırmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="72838-428">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="72838-429">Ardından, görüntüve yöntemleri kullanarak görüntüüzerindeki metni [`DrawString`](xref:System.Drawing.Graphics.DrawString*) [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) ve sınırlayıcı kutuyu çizin.</span><span class="sxs-lookup"><span data-stu-id="72838-429">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="72838-430">For-each döngü dışında, görüntüleri kaydetmek için kod `outputDirectory`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-430">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="72838-431">Uygulamanın çalışma zamanında beklendiği gibi öngörüler yaptığını ek geribildirim `LogDetectedObjects` için, algılanan nesneleri konsola çıktıetmek için `DrawBoundingBox` *Program.cs* dosyasındaki yöntemin altında nağmeler bulunan bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-431">For additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="72838-432">Artık öngörülerden görsel geri bildirim oluşturmak için yardımcı yöntemlere sahip olduğunuza göre, puanlı görüntülerin her biri üzerinde yinelemek için bir for-loop ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-432">Now that you have helper methods to create visual feedback from the predictions, add a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="72838-433">For-loop'un içinde, görüntü dosyasının adını ve onunla ilişkili sınırlayıcı kutuları alın.</span><span class="sxs-lookup"><span data-stu-id="72838-433">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="72838-434">Bunun altında, `DrawBoundingBox` görüntü üzerinde sınırlayıcı kutuları çizmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-434">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="72838-435">Son olarak, `LogDetectedObjects` konsola öngörüler çıktıyöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="72838-435">Lastly, use the `LogDetectedObjects` method to output predictions to the console.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

<span data-ttu-id="72838-436">Try-catch deyiminden sonra, işlemin çalıştığını belirtmek için ek mantık ekleyin.</span><span class="sxs-lookup"><span data-stu-id="72838-436">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="72838-437">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="72838-437">That's it!</span></span>

## <a name="results"></a><span data-ttu-id="72838-438">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="72838-438">Results</span></span>

<span data-ttu-id="72838-439">Önceki adımları takip ettikten sonra konsol uygulamanızı (Ctrl + F5) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="72838-439">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="72838-440">Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="72838-440">Your results should be similar to the following output.</span></span> <span data-ttu-id="72838-441">Uyarılar veya iletileri işleme görebilirsiniz, ancak bu iletiler netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="72838-441">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="72838-442">Sınırları kutulu görüntüleri görmek için dizine `assets/images/output/` gidin.</span><span class="sxs-lookup"><span data-stu-id="72838-442">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="72838-443">Aşağıda işlenmiş görüntülerden birinden bir örnek.</span><span class="sxs-lookup"><span data-stu-id="72838-443">Below is a sample from one of the processed images.</span></span>

![Yemek odasının örnek işlenmiş görüntüsü](./media/object-detection-onnx/dinning-room-table-chairs.png)

<span data-ttu-id="72838-445">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="72838-445">Congratulations!</span></span> <span data-ttu-id="72838-446">Şimdi, ML.NET önceden eğitilmiş bir modeli yeniden kullanarak nesne algılama `ONNX` için bir makine öğrenme modeli başarıyla oluşturmuşsunuz.</span><span class="sxs-lookup"><span data-stu-id="72838-446">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="72838-447">Bu öğreticinin kaynak kodunu [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72838-447">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="72838-448">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="72838-448">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="72838-449">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="72838-449">Understand the problem</span></span>
> - <span data-ttu-id="72838-450">ONNX'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin</span><span class="sxs-lookup"><span data-stu-id="72838-450">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="72838-451">Modeli anlama</span><span class="sxs-lookup"><span data-stu-id="72838-451">Understand the model</span></span>
> - <span data-ttu-id="72838-452">Önceden eğitilmiş modeli yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="72838-452">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="72838-453">Yüklü bir modelle nesneleri algılama</span><span class="sxs-lookup"><span data-stu-id="72838-453">Detect objects with a loaded model</span></span>

<span data-ttu-id="72838-454">Genişletilmiş bir nesne algılama örneğini keşfetmek için Machine Learning örnekleri GitHub deposuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="72838-454">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="72838-455">dotnet/machinelearning-örnekleri GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="72838-455">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
