---
title: 'Öğretici: model Oluşturucu ile görüntülerde nesneleri algılama'
description: Bu öğreticide, görüntülerde durma işaretlerini algılamak için ML.NET model Oluşturucu ve Azure ML kullanarak bir nesne algılama modelinin nasıl oluşturulacağı gösterilmektedir.
author: briacht
ms.author: brachtma
ms.date: 03/12/2021
ms.topic: tutorial
ms.custom: mlnet-tooling
ms.openlocfilehash: 21b672b84c7f55578a76459fa9f02aca3455d719
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104657917"
---
# <a name="tutorial-detect-stop-signs-in-images-with-model-builder"></a><span data-ttu-id="ece8b-103">Öğretici: model Oluşturucu ile görüntülerde durma işaretlerini Algıla</span><span class="sxs-lookup"><span data-stu-id="ece8b-103">Tutorial: Detect stop signs in images with Model Builder</span></span>

<span data-ttu-id="ece8b-104">Görüntülerde durma işaretlerini algılayıp bulmak için ML.NET model Oluşturucu ve Azure ML kullanarak bir nesne algılama modeli oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-104">Learn how to build an object detection model using ML.NET Model Builder and Azure ML to detect and locate stop signs in images.</span></span>

<span data-ttu-id="ece8b-105">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="ece8b-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="ece8b-106">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="ece8b-106">Prepare and understand the data</span></span>
> - <span data-ttu-id="ece8b-107">Senaryoyu seçin</span><span class="sxs-lookup"><span data-stu-id="ece8b-107">Choose the scenario</span></span>
> - <span data-ttu-id="ece8b-108">Eğitim ortamını seçin</span><span class="sxs-lookup"><span data-stu-id="ece8b-108">Choose the training environment</span></span>
> - <span data-ttu-id="ece8b-109">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="ece8b-109">Load the data</span></span>
> - <span data-ttu-id="ece8b-110">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="ece8b-110">Train the model</span></span>
> - <span data-ttu-id="ece8b-111">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ece8b-111">Evaluate the model</span></span>
> - <span data-ttu-id="ece8b-112">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="ece8b-112">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="ece8b-113">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="ece8b-113">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ece8b-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ece8b-114">Prerequisites</span></span>

<span data-ttu-id="ece8b-115">Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-115">For a list of prerequisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="model-builder-object-detection-overview"></a><span data-ttu-id="ece8b-116">Model Oluşturucu nesne algılamaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="ece8b-116">Model Builder object detection overview</span></span>

<span data-ttu-id="ece8b-117">Nesne algılama bir bilgisayar vizyonu sorunudur.</span><span class="sxs-lookup"><span data-stu-id="ece8b-117">Object detection is a computer vision problem.</span></span> <span data-ttu-id="ece8b-118">Görüntü sınıflandırmasıyla yakından ilgili olarak, nesne algılama görüntü sınıflandırmasını daha ayrıntılı bir ölçekte gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-118">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="ece8b-119">Nesne algılama hem görüntüler içindeki varlıkları bulur _hem_ de kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="ece8b-119">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="ece8b-120">Görüntüler farklı türlerde birden çok nesne içerdiğinde nesne algılamayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-120">Use object detection when images contain multiple objects of different types.</span></span>

![Resim sınıflandırmasına karşı nesne sınıflandırmasına karşı ekran görüntüleri.](./media/object-detection-onnx/img-classification-obj-detection.PNG)

<span data-ttu-id="ece8b-122">Nesne algılama için bazı kullanım örnekleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="ece8b-122">Some use cases for object detection include:</span></span>

- <span data-ttu-id="ece8b-123">Self-Driving otomobiller</span><span class="sxs-lookup"><span data-stu-id="ece8b-123">Self-Driving Cars</span></span>
- <span data-ttu-id="ece8b-124">Robotics</span><span class="sxs-lookup"><span data-stu-id="ece8b-124">Robotics</span></span>
- <span data-ttu-id="ece8b-125">Yüz Algılama</span><span class="sxs-lookup"><span data-stu-id="ece8b-125">Face Detection</span></span>
- <span data-ttu-id="ece8b-126">Çalışma alanı güvenliği</span><span class="sxs-lookup"><span data-stu-id="ece8b-126">Workplace Safety</span></span>
- <span data-ttu-id="ece8b-127">Nesne sayımı</span><span class="sxs-lookup"><span data-stu-id="ece8b-127">Object Counting</span></span>
- <span data-ttu-id="ece8b-128">Etkinlik tanıma</span><span class="sxs-lookup"><span data-stu-id="ece8b-128">Activity Recognition</span></span>

<span data-ttu-id="ece8b-129">Bu örnek, model Oluşturucu ile oluşturulmuş bir makine öğrenimi modeli kullanarak görüntülerde durma işaretlerini algılayan bir C# .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ece8b-129">This sample creates a C# .NET Core console application that detects stop signs in images using a machine learning model built with Model Builder.</span></span> <span data-ttu-id="ece8b-130">Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/ObjectDetection_StopSigns) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ece8b-130">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/ObjectDetection_StopSigns) GitHub repository.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="ece8b-131">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="ece8b-131">Prepare and understand the data</span></span>

<span data-ttu-id="ece8b-132">Dur Işareti veri kümesi, her biri en az bir Dur işareti içeren [50 görüntüden indirilen](https://unsplash.com/)görüntüden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ece8b-132">The Stop Sign dataset consists of 50 images downloaded from [Unsplash](https://unsplash.com/), each of which contain at least one stop sign.</span></span>

<span data-ttu-id="ece8b-133">Yapmanız gereken ilk şey, resimlerinize not ekleme veya her görüntüde durdurma işaretlerinin etrafında sınırlayıcı kutular çizmektir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-133">The first thing you need to do is annotate your images, or draw bounding boxes around the stop signs in each image.</span></span> <span data-ttu-id="ece8b-134">Bu öğreticide, resimlerinize [Vott](https://github.com/microsoft/VoTT)adlı bir araçla açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-134">In this tutorial, you will annotate your images with a tool called [VoTT](https://github.com/microsoft/VoTT).</span></span>

> <span data-ttu-id="ece8b-135">Aşağıdaki veri etiketleme adımlarını atlamak istiyorsanız, veri [kümesinin bu sürümünü indirebilir](https://aka.ms/mlnet-object-detection-tutorial-assets) ve [bir konsol uygulaması oluşturmak](object-detection-model-builder.md#create-a-console-application)için atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ece8b-135">If you want to skip the data labeling steps below, you can [download this version of the dataset](https://aka.ms/mlnet-object-detection-tutorial-assets) and skip to [Create a console application](object-detection-model-builder.md#create-a-console-application).</span></span>

### <a name="create-a-new-vott-project"></a><span data-ttu-id="ece8b-136">Yeni bir VoTT projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ece8b-136">Create a new VoTT project</span></span>

1. <span data-ttu-id="ece8b-137">50 [veri kümesini indirin](https://aka.ms/mlnet-object-detection-tutorial-dataset) ve görüntüleri imzalayın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-137">[Download the dataset](https://aka.ms/mlnet-object-detection-tutorial-dataset) of 50 stop sign images and unzip.</span></span>
1. <span data-ttu-id="ece8b-138">[VoTT 'Yi indirin](https://github.com/Microsoft/VoTT/releases) (görsel nesne etiketleme aracı).</span><span class="sxs-lookup"><span data-stu-id="ece8b-138">[Download VoTT](https://github.com/Microsoft/VoTT/releases) (Visual Object Tagging Tool).</span></span>
1. <span data-ttu-id="ece8b-139">VoTT 'yi açın ve **Yeni proje**'yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-139">Open VoTT and select **New Project**.</span></span>

    ![VoTT giriş ekranı](./media/object-detection-model-builder/vott.png)

1. <span data-ttu-id="ece8b-141">**Proje ayarları**' nda, **görünen adı** "StopSignObjDetection" olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-141">In **Project Settings**, change the **Display Name** to "StopSignObjDetection".</span></span>
1. <span data-ttu-id="ece8b-142">**Güvenlik belirtecini** *yeni güvenlik belirteci oluşturacak* şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-142">Change the **Security Token** to *Generate New Security Token*.</span></span>
1. <span data-ttu-id="ece8b-143">**Kaynak bağlantısı**' nın yanındaki **bağlantı ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-143">Next to **Source Connection**, select **Add Connection**.</span></span>
1. <span data-ttu-id="ece8b-144">**Bağlantı ayarları**' nda, kaynak **bağlantının görünen adını** "stopsignımages" olarak değiştirin ve **sağlayıcı** olarak *yerel dosya sistemi* ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-144">In **Connection Settings**, change the **Display Name** for the source connection to "StopSignImages", and select *Local File System* as the **Provider**.</span></span> <span data-ttu-id="ece8b-145">**Klasör yolu** için 50 eğitim görüntülerini Içeren *durdurma işaretleri* klasörünü seçin ve ardından **Bağlantıyı Kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-145">For the **Folder Path**, select the *Stop-Signs* folder which contains the 50 training images, and then select **Save Connection**.</span></span>

    ![VoTT yeni bağlantı Iletişim kutusu](./media/object-detection-model-builder/vott-new-connection.png)

1. <span data-ttu-id="ece8b-147">**Proje ayarları**' nda, **kaynak bağlantısını** *stopsignımages* (yeni oluşturduğunuz bağlantı) olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-147">In **Project Settings**, change the **Source Connection** to *StopSignImages* (the connection you just created).</span></span>
1. <span data-ttu-id="ece8b-148">**Hedef bağlantıyı** Ayrıca *stopsignımages* ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-148">Change the **Target Connection** to *StopSignImages* as well.</span></span> <span data-ttu-id="ece8b-149">**Proje ayarlarınız** şu ekran görüntüsüne benzer şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ece8b-149">Your **Project Settings** should now look similar to this screenshot:</span></span>

    ![VoTT proje ayarları Iletişim kutusu](./media/object-detection-model-builder/vott-new-project.png)

1. <span data-ttu-id="ece8b-151">**Projeyi kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-151">Select **Save Project**.</span></span>

### <a name="add-tag-and-label-images"></a><span data-ttu-id="ece8b-152">Etiket ve etiket görüntüleri ekleme</span><span class="sxs-lookup"><span data-stu-id="ece8b-152">Add tag and label images</span></span>

<span data-ttu-id="ece8b-153">Şimdi, sol taraftaki tüm eğitim görüntülerinin önizlemesi, ortadaki seçili görüntünün önizlemesi ve sağ taraftaki **Etiketler** sütunu ile bir pencere görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-153">You should now see a window with preview images of all the training images on the left, a preview of the selected image in the middle, and a **Tags** column on the right.</span></span> <span data-ttu-id="ece8b-154">Bu ekran **Etiketler düzenleyicisidir**.</span><span class="sxs-lookup"><span data-stu-id="ece8b-154">This screen is the **Tags editor**.</span></span>

1. <span data-ttu-id="ece8b-155">Yeni bir etiket eklemek için **Etiketler** araç çubuğunda ilk (artı-şekillendirilmiş) simgesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-155">Select the first (plus-shaped) icon in the **Tags** toolbar to add a new tag.</span></span>

    ![VoTT yeni etiket simgesi](./media/object-detection-model-builder/vott-new-tag-icon.png)

1. <span data-ttu-id="ece8b-157">"Durdur-Imzala" etiketini adlandırın ve klavyenizde <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-157">Name the tag "Stop-Sign" and hit <kbd>Enter</kbd> on your keyboard.</span></span>

    ![VoTT yeni etiketi](./media/object-detection-model-builder/vott-new-tag.png)

1. <span data-ttu-id="ece8b-159">Görüntüde her bir durdurma işaretini çevreleyen bir dikdörtgen çizmek için tıklayın ve sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-159">Click and drag to draw a rectangle around each stop sign in the image.</span></span> <span data-ttu-id="ece8b-160">İmleç bir dikdörtgen çizmenize izin vermezse, üstteki araç çubuğundan **dikdörtgen çiz** aracını seçmeyi veya <kbd>R</kbd>klavye kısayolunu kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-160">If the cursor does not let you draw a rectangle, try selecting the **Draw Rectangle** tool from the toolbar on the top, or use the keyboard shortcut <kbd>R</kbd>.</span></span>
1. <span data-ttu-id="ece8b-161">Dikdörtgeninizi çizdikten sonra, etiketi sınırlayıcı kutuya eklemek için önceki adımlarda oluşturduğunuz **Durdur-imzala** etiketini seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-161">After drawing your rectangle, select the **Stop-Sign** tag that you created in the previous steps to add the tag to the bounding box.</span></span>
1. <span data-ttu-id="ece8b-162">Veri kümesindeki bir sonraki görüntünün önizleme görüntüsüne tıklayın ve bu işlemi tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-162">Click on the preview image for the next image in the dataset and repeat this process.</span></span>
1. <span data-ttu-id="ece8b-163">Her görüntüde her durdurma oturumu için 3-4 adıma devam edin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-163">Continue steps 3-4 for every stop sign in every image.</span></span>

    ![VoTT resimleri açıklama ekleme](./media/object-detection-model-builder/vott-annotating.gif)

### <a name="export-your-vott-json"></a><span data-ttu-id="ece8b-165">VoTT JSON 'nizi dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="ece8b-165">Export your VoTT JSON</span></span>

<span data-ttu-id="ece8b-166">Tüm eğitim görüntülerinizi etiketledikten sonra, eğitim için model Oluşturucu tarafından kullanılacak dosyayı dışarı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ece8b-166">Once you have labeled all of your training images, you can export the file that will be used by Model Builder for training.</span></span>

1. <span data-ttu-id="ece8b-167">**Dışa aktarma ayarlarına** gitmek için sol araç çubuğundaki dördüncü simgeyi (bir kutudaki çapraz oka sahip olan) seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-167">Select the fourth icon in the left toolbar (the one with the diagonal arrow in a box) to go to the **Export Settings**.</span></span>
1. <span data-ttu-id="ece8b-168">**Sağlayıcıyı** *vott JSON* olarak bırakın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-168">Leave the **Provider** as *VoTT JSON*.</span></span>
1. <span data-ttu-id="ece8b-169">**Varlık durumunu** *yalnızca etiketli varlıklar* olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-169">Change the **Asset State** to *Only tagged Assets*.</span></span>
1. <span data-ttu-id="ece8b-170">**Görüntüleri içer** işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-170">Uncheck **Include Images**.</span></span> <span data-ttu-id="ece8b-171">Görüntüleri eklerseniz, eğitim görüntüleri oluşturulan dışarı aktarma klasörüne kopyalanır ve bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-171">If you include the images, then the training images will be copied to the export folder that is generated, which is not necessary.</span></span>
1. <span data-ttu-id="ece8b-172">**Dışarı aktarma ayarlarını kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-172">Select **Save Export Settings**.</span></span>

    ![VoTT dışarı aktarma ayarları](./media/object-detection-model-builder/vott-export.png)

1. <span data-ttu-id="ece8b-174">**Etiketler düzenleyiciye** geri dönün (sol araç çubuğundaki ikinci simge bir şerit gibi).</span><span class="sxs-lookup"><span data-stu-id="ece8b-174">Go back to the **Tags editor** (the second icon in the left toolbar shaped like a ribbon).</span></span> <span data-ttu-id="ece8b-175">Üstteki araç çubuğunda **projeyi dışarı aktar** simgesini (bir kutudaki ok gibi) seçin veya <kbd>CTRL</kbd> + <kbd>E</kbd>klavye kısayolunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-175">In the top toolbar, select the **Export Project** icon (the last icon shaped like an arrow in a box), or use the keyboard shortcut <kbd>Ctrl</kbd>+<kbd>E</kbd>.</span></span>

    ![VoTT dışarı aktarma düğmesi](./media/object-detection-model-builder/vott-export-button.png)

<span data-ttu-id="ece8b-177">Bu dışarı aktarma işlemi, *Dur-imzala* klasörünüzde *vott-JSON-Export* adlı yeni bir klasör oluşturur ve bu yeni klasörde *STOPSIGNOBJDETECTION-Export* adlı bir JSON dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ece8b-177">This export will create a new folder called *vott-json-export* in your *Stop-Sign-Images* folder and will generate a JSON file named *StopSignObjDetection-export* in that new folder.</span></span> <span data-ttu-id="ece8b-178">Bu JSON dosyasını, model Oluşturucu 'da bir nesne algılama modelini eğitmek için sonraki adımlarda kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ece8b-178">You will use this JSON file in the next steps for training an object detection model in Model Builder.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="ece8b-179">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ece8b-179">Create a console application</span></span>

1. <span data-ttu-id="ece8b-180">Visual Studio 'da, *Stopsigndetection* adlı bir **C# .NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ece8b-180">In Visual Studio, create a **C# .NET Core console application** called *StopSignDetection*.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="ece8b-181">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="ece8b-181">Choose a scenario</span></span>

1. <span data-ttu-id="ece8b-182">**Çözüm Gezgini**, *stopsigndetection* projesine sağ tıklayın ve   >  model Oluşturucu kullanıcı arabirimini açmak için **Machine Learning** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-182">In **Solution Explorer**, right-click the *StopSignDetection* project, and select **Add** > **Machine Learning** to open the Model Builder UI.</span></span>
1. <span data-ttu-id="ece8b-183">Bu örnek için, senaryo nesne algılamasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="ece8b-183">For this sample, the scenario is object detection.</span></span> <span data-ttu-id="ece8b-184">Model oluşturucunun **senaryo** adımında, **nesne algılama** senaryosunu seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-184">In the **Scenario** step of Model Builder, select the **Object Detection** scenario.</span></span>

![Visual Studio 'da model Oluşturucu Sihirbazı](./media/object-detection-model-builder/obj-det-scenario.png)

> <span data-ttu-id="ece8b-186">Senaryolar listesinde *nesne algılamayı* görmüyorsanız, [model Oluşturucu sürümünüzü güncelleştirmeniz](https://marketplace.visualstudio.com/items?itemName=MLNET.07)gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-186">If you don't see *Object Detection* in the list of scenarios, you may need to [update your version of Model Builder](https://marketplace.visualstudio.com/items?itemName=MLNET.07).</span></span>

## <a name="choose-the-training-environment"></a><span data-ttu-id="ece8b-187">Eğitim ortamını seçin</span><span class="sxs-lookup"><span data-stu-id="ece8b-187">Choose the training environment</span></span>

<span data-ttu-id="ece8b-188">Şu anda, model Oluşturucu yalnızca Azure Machine Learning olan eğitim nesne algılama modellerini destekler, bu nedenle Azure eğitim ortamı varsayılan olarak seçilidir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-188">Currently, Model Builder supports training object detection models with Azure Machine Learning only, so the Azure training environment is selected by default.</span></span>

![Azure eğitim ortamı seçimi](./media/object-detection-model-builder/obj-det-environment.png)

<span data-ttu-id="ece8b-190">Azure ML 'yi kullanarak bir modeli eğmek için model Oluşturucu 'dan bir Azure ML denemesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-190">To train a model using Azure ML, you must create an Azure ML experiment from Model Builder.</span></span>

<span data-ttu-id="ece8b-191">**Azure ML** denemesi, bir veya daha fazla makine öğrenimi eğitiminin çalıştığı yapılandırmayı ve sonuçları kapsülleyen bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="ece8b-191">An **Azure ML experiment** is a resource that encapsulates the configuration and results for one or more machine learning training runs.</span></span>

<span data-ttu-id="ece8b-192">Azure ML denemesi oluşturmak için öncelikle ortamınızı Azure 'da yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-192">To create an Azure ML experiment, you first need to configure your environment in Azure.</span></span> <span data-ttu-id="ece8b-193">Bir deneme çalışması için aşağıdakiler gerekir:</span><span class="sxs-lookup"><span data-stu-id="ece8b-193">An experiment needs the following to run:</span></span>

- <span data-ttu-id="ece8b-194">Bir Azure aboneliği</span><span class="sxs-lookup"><span data-stu-id="ece8b-194">An Azure subscription</span></span>
- <span data-ttu-id="ece8b-195">**Çalışma alanı**: eğitim çalıştırmasının bir parçası olarak oluşturulan tüm Azure ML kaynakları ve yapıtları için merkezi bir yer sağlayan BIR Azure ML kaynağı.</span><span class="sxs-lookup"><span data-stu-id="ece8b-195">A **workspace**: an Azure ML resource that provides a central place for all Azure ML resources and artifacts created as part of a training run.</span></span>
- <span data-ttu-id="ece8b-196">**İşlem**: Azure Machine Learning işlem, eğitim için kullanılan bulut tabanlı BIR Linux VM 'dir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-196">A **compute**: an Azure Machine Learning compute is a cloud-based Linux VM used for training.</span></span> <span data-ttu-id="ece8b-197">[Model Oluşturucu tarafından desteklenen işlem türleri](../resources/azure-training-concepts-model-builder.md#what-is-an-azure-machine-learning-compute)hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-197">Learn more about [compute types supported by Model Builder](../resources/azure-training-concepts-model-builder.md#what-is-an-azure-machine-learning-compute).</span></span>

### <a name="set-up-an-azure-ml-workspace"></a><span data-ttu-id="ece8b-198">Azure ML çalışma alanı ayarlama</span><span class="sxs-lookup"><span data-stu-id="ece8b-198">Set up an Azure ML workspace</span></span>

<span data-ttu-id="ece8b-199">Ortamınızı yapılandırmak için:</span><span class="sxs-lookup"><span data-stu-id="ece8b-199">To configure your environment:</span></span>

1. <span data-ttu-id="ece8b-200">**Çalışma alanını ayarla** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-200">Select the **Set up workspace** button.</span></span>
1. <span data-ttu-id="ece8b-201">**Yeni deneme oluştur** Iletişim kutusunda Azure aboneliğinizi seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-201">In the **Create new experiment** dialog, select your Azure subscription.</span></span>
1. <span data-ttu-id="ece8b-202">Mevcut bir çalışma alanını seçin veya yeni bir Azure ML çalışma alanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ece8b-202">Select an existing workspace or create a new Azure ML workspace.</span></span>

    <span data-ttu-id="ece8b-203">Yeni bir çalışma alanı oluşturduğunuzda, aşağıdaki kaynaklar sağlanır:</span><span class="sxs-lookup"><span data-stu-id="ece8b-203">When you create a new workspace, the following resources are provisioned:</span></span>

    - <span data-ttu-id="ece8b-204">Azure Machine Learning çalışma alanı</span><span class="sxs-lookup"><span data-stu-id="ece8b-204">Azure Machine Learning workspace</span></span>
    - <span data-ttu-id="ece8b-205">Azure Storage</span><span class="sxs-lookup"><span data-stu-id="ece8b-205">Azure Storage</span></span>
    - <span data-ttu-id="ece8b-206">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="ece8b-206">Azure Application Insights</span></span>
    - <span data-ttu-id="ece8b-207">Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="ece8b-207">Azure Container Registry</span></span>
    - <span data-ttu-id="ece8b-208">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="ece8b-208">Azure Key Vault</span></span>

    <span data-ttu-id="ece8b-209">Sonuç olarak, bu işlem birkaç dakika sürebilir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-209">As a result, this process may take a few minutes.</span></span>

1. <span data-ttu-id="ece8b-210">Mevcut bir işlem seçin veya yeni bir Azure ML işlemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ece8b-210">Select an existing compute or create a new Azure ML compute.</span></span> <span data-ttu-id="ece8b-211">Bu işlem birkaç dakika sürebilir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-211">This process may take a few minutes.</span></span>
1. <span data-ttu-id="ece8b-212">Varsayılan deneme adını bırakıp **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-212">Leave the default experiment name and select **Create**.</span></span>

    ![Azure çalışma alanı kurulum Iletişim kutusu](./media/object-detection-model-builder/azure-dialog.png)

<span data-ttu-id="ece8b-214">İlk deneme oluşturulur ve deneme adı çalışma alanına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-214">The first experiment is created, and the experiment name is registered in the workspace.</span></span> <span data-ttu-id="ece8b-215">Sonraki tüm çalıştırmalar (aynı deneme adı kullanılırsa) aynı denemenin bir parçası olarak günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-215">Any subsequent runs (if the same experiment name is used ) are logged as part of the same experiment.</span></span> <span data-ttu-id="ece8b-216">Aksi takdirde, yeni bir deneme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ece8b-216">Otherwise, a new experiment is created.</span></span>

<span data-ttu-id="ece8b-217">Yapılandırmanızla memnun kaldıysanız, **veri** adımına geçmek Için model Oluşturucu 'daki **sonraki adım** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-217">If you’re satisfied with your configuration, select the **Next step** button in Model Builder to move to the **Data** step.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="ece8b-218">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="ece8b-218">Load the data</span></span>

<span data-ttu-id="ece8b-219">Model oluşturucunun **veri** adımında eğitim veri kümenizi seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="ece8b-219">In the **Data** step of Model Builder, you will select your training dataset.</span></span>

><span data-ttu-id="ece8b-220">Model Oluşturucu Şu anda yalnızca VoTT tarafından oluşturulan JSON biçimini kabul eder, ancak takım daha sonra daha fazla biçim desteği eklemeyi planlıyor.</span><span class="sxs-lookup"><span data-stu-id="ece8b-220">Model Builder currently only accepts the format of JSON generated by VoTT, but the team plans to add support for more formats in the future.</span></span> <span data-ttu-id="ece8b-221">Model Oluşturucu 'da desteklendiğini görmek istediğiniz nesne algılama için bir veri kümesi biçimi varsa, geri bildiriminizi [GitHub](https://github.com/dotnet/machinelearning-modelbuilder/issues/new?assignees=&labels=&template=data_suggestion.md&title=)' da bırakın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-221">If there is a dataset format for object detection that you’d like to see supported in Model Builder, leave your feedback on [GitHub](https://github.com/dotnet/machinelearning-modelbuilder/issues/new?assignees=&labels=&template=data_suggestion.md&title=).</span></span>

1. <span data-ttu-id="ece8b-222">**Klasör Seç** metin kutusunun yanındaki düğmeyi seçin ve `StopSignObjDetection-export.json` *Durdur-imzalar/vott-JSON-Export* dizininde bulunması gereken öğesini bulmak için dosya Gezgini 'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-222">Select the button next to the **Select a folder** text box and use the File Explorer to find the `StopSignObjDetection-export.json` which should be located in the *Stop-Signs/vott-json-export* directory.</span></span>

    ![Model Oluşturucu verileri adımı](./media/object-detection-model-builder/obj-det-data.png)

1. <span data-ttu-id="ece8b-224">Verileriniz **veri önizlemesinde** doğru görünüyorsa, **eğitme** adımına geçmek için **İleri adım** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-224">If your data looks correct in the **Data Preview**, select **Next step** to move on to the **Train** step.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="ece8b-225">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="ece8b-225">Train the model</span></span>

<span data-ttu-id="ece8b-226">Sonraki adım modelinize eğitedir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-226">The next step is to train your model.</span></span>

<span data-ttu-id="ece8b-227">Model Oluşturucu **eğitme** ekranında **eğitime başla** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-227">In the Model Builder **Train** screen, select the **Start training** button.</span></span>

<span data-ttu-id="ece8b-228">Bu noktada Verileriniz Azure Storage 'a yüklenir ve eğitim süreci Azure ML 'de başlar.</span><span class="sxs-lookup"><span data-stu-id="ece8b-228">At this point, your data is uploaded to Azure Storage and the training process begins in Azure ML.</span></span>

><span data-ttu-id="ece8b-229">Eğitim süreci bir süre sürer ve bu süre, seçilen işlem boyutuna ve veri miktarına bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-229">The training process takes some time, and the amount of time may vary depending on the size of compute selected as well as the amount of data.</span></span> <span data-ttu-id="ece8b-230">Bir modelin Azure 'da eğitildiği ilk sefer, kaynakların sağlanması gerektiğinden biraz daha uzun bir eğitim süresi bekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-230">The first time a model is trained in Azure, you can expect a slightly longer training time because resources have to be provisioned.</span></span> <span data-ttu-id="ece8b-231">Bu 50 görüntü örneği için eğitim yaklaşık 16 dakika sürdü.</span><span class="sxs-lookup"><span data-stu-id="ece8b-231">For this sample of 50 images, training took about 16 minutes.</span></span>

<span data-ttu-id="ece8b-232">Azure Machine Learning portalında çalıştırmaların ilerlemesini, Visual Studio 'da **geçerli çalışmayı izle Azure Portal** bağlantısını seçerek izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ece8b-232">You can track the progress of your runs in the Azure Machine Learning portal by selecting the **Monitor current run in Azure portal** link in Visual Studio.</span></span>

<span data-ttu-id="ece8b-233">Eğitim tamamlandıktan sonra, **değerlendir** adımına geçmek için **sonraki adım** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-233">Once training is complete, select the **Next step** button to move on to the **Evaluate** step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="ece8b-234">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="ece8b-234">Evaluate the model</span></span>

<span data-ttu-id="ece8b-235">Değerlendirme ekranında, model doğruluğu dahil olmak üzere eğitim sürecinin sonuçlarına ilişkin bir genel bakış elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="ece8b-235">In the Evaluate screen, you get an overview of the results from the training process, including the model accuracy.</span></span>

![Model Oluşturucu adımı değerlendir](./media/object-detection-model-builder/obj-det-evaluate.png)

<span data-ttu-id="ece8b-237">Bu durumda, doğruluk %100 diyor ve bu da modelin veri kümesindeki çok az sayıda görüntü nedeniyle büyük *olasılıkla büyük* olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-237">In this case, the accuracy says 100%, which means that the model is more than likely *overfit* due to too few images in the dataset.</span></span>

<span data-ttu-id="ece8b-238">Modelinizin beklendiği gibi çalışıp çalışmadığını hızlı bir şekilde denetlemek için **modelinize deneme** deneyimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ece8b-238">You can use the **Try your model** experience to quickly check whether your model is performing as expected.</span></span>

<span data-ttu-id="ece8b-239">**Bir görüntüye gözatıp** , tercihen modelin eğitim kapsamında kullanmadığından bir test görüntüsü belirtin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-239">Select **Browse an image** and provide a test image, preferably one that the model did not use as part of training.</span></span>

![Model Oluşturucu modelinizi deneyin](./media/object-detection-model-builder/obj-det-try-model.png)

<span data-ttu-id="ece8b-241">Algılanan her bir sınırlayıcı kutusunda gösterilen puan, algılanan nesnenin **güvenilirlikli** olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-241">The score shown on each detected bounding box indicates the **confidence** of the detected object.</span></span> <span data-ttu-id="ece8b-242">Örneğin, yukarıdaki ekran görüntüsünde, durdurma işareti etrafındaki sınırlayıcı kutudaki puan, modelin %99 olduğunu ve algılanan nesnenin bir Dur işareti olduğundan emin olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-242">For instance, in the screenshot above, the score on the bounding box around the stop sign indicates that the model is 99% sure that the detected object is a stop sign.</span></span>

<span data-ttu-id="ece8b-243">Eşik kaydırıcıyla arttırılabilen veya azaltılan **puan eşiği**, puanlarına göre algılanan nesneleri ekler ve kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ece8b-243">The **Score threshold**, which can be increased or decreased with the threshold slider, will add and remove detected objects based on their scores.</span></span> <span data-ttu-id="ece8b-244">Örneğin, eşik. 51 ise, model yalnızca Güvenirlik puanı. 51 veya üzeri olan nesneleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece8b-244">For instance, if the threshold is .51, then the model will only show objects that have a confidence score of .51 or above.</span></span> <span data-ttu-id="ece8b-245">Eşiği artırdıkça, daha az algılanan nesneler görürsünüz ve eşiği azaltdıkça, algılanan daha fazla nesne görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ece8b-245">As you increase the threshold, you will see less detected objects, and as you decrease the threshold, you will see more detected objects.</span></span>

<span data-ttu-id="ece8b-246">Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu artırmanın kolay bir yolu daha fazla veri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="ece8b-246">If you're not satisfied with your accuracy metrics, one easy way to try to improve model accuracy is to use more data.</span></span> <span data-ttu-id="ece8b-247">Aksi takdirde, model Oluşturucu 'daki **kod** adımına geçmek için **sonraki adım** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-247">Otherwise, select the **Next step** link to move on to the **Code** step in Model Builder.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="ece8b-248">Tahminleri yapmak için kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="ece8b-248">Add the code to make predictions</span></span>

<span data-ttu-id="ece8b-249">Eğitim sürecinin bir sonucu olarak iki proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ece8b-249">Two projects are created as a result of the training process.</span></span>

- <span data-ttu-id="ece8b-250">*StopSignDetectionML. ConsoleApp*: model eğitim kodunu ve örnek tüketim kodunu içeren bir C# .NET Core konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="ece8b-250">*StopSignDetectionML.ConsoleApp*: A C# .NET Core Console application that contains the model training code and sample consumption code.</span></span>
- <span data-ttu-id="ece8b-251">*StopSignDetectionML. model*: giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini, eğitim sırasında en iyi gerçekleştirme modelinin kaydedilmiş sürümünü ve tahmin yapmak için çağrılan bir yardımcı sınıfı içeren .NET Standard bir sınıf kitaplığı `ConsumeModel` .</span><span class="sxs-lookup"><span data-stu-id="ece8b-251">*StopSignDetectionML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training, and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="ece8b-252">Model oluşturucunun kod adımında, otomatik olarak oluşturulan projeleri çözüme eklemek için **Proje Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-252">In the code step of Model Builder, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="ece8b-253">*Stopsigndetection* projesinde *program. cs* dosyasını açın ve *StopSignDetectionML. model* projesine başvurmak için dosyanın en üstüne aşağıdaki using ifadesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ece8b-253">Open the *Program.cs* file in the *StopSignDetection* project, and add the following using statement at the top of the file to reference the *StopSignDetectionML.Model* project:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L2)]

1. <span data-ttu-id="ece8b-254">Aşağıdaki [Test görüntüsünü](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/test-image1.jpeg)indirin.</span><span class="sxs-lookup"><span data-stu-id="ece8b-254">Download the following [test image](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/test-image1.jpeg).</span></span>
1. <span data-ttu-id="ece8b-255">`ModelInput` `ImageSource` Uygulamanızın yöntemi içindeki test görüntünüzün FilePath öğesine ayarlanmış özelliği ile sınıfının yeni bir örneğini oluşturun `Main` .</span><span class="sxs-lookup"><span data-stu-id="ece8b-255">Create a new instance of the `ModelInput` class with the `ImageSource` property set to the filepath of your test image inside the `Main` method of your application.</span></span> <span data-ttu-id="ece8b-256">"Merhaba Dünya" ifadesini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ece8b-256">Replace the "Hello World" statement with the following code:</span></span>

    [!code-csharp [InputData](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L10-L15)]

1. <span data-ttu-id="ece8b-257">`Predict` `ConsumeModel` Eğitilen modeli yüklemek, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) model için bir oluşturmak ve yeni verilerde tahmine dayalı hale getirmek için sınıfından yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-257">Use the `Predict` method from the `ConsumeModel` class to load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model, and make predictions on new data.</span></span> <span data-ttu-id="ece8b-258">Aşağıdaki kodu deyimin altına ekleyin `ModelInput` :</span><span class="sxs-lookup"><span data-stu-id="ece8b-258">Add the following code below the `ModelInput` statement:</span></span>

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L15)]

1. <span data-ttu-id="ece8b-259">Aşağıdaki kodu ekleyerek tahmine ait çıktıyı, etiket, koordinat ve skor dahil olmak üzere Yazdır:</span><span class="sxs-lookup"><span data-stu-id="ece8b-259">Print out the Prediction's output, including the label, coordinates, and score by adding the following code:</span></span>

    [!code-csharp [PrintResults](~/machinelearning-samples/samples/modelbuilder/ObjectDetection_StopSigns/StopSignDetection/Program.cs#L17-L18)]

1. <span data-ttu-id="ece8b-260">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ece8b-260">Run the application.</span></span>

    <span data-ttu-id="ece8b-261">Program tarafından oluşturulan çıkış aşağıdaki kod parçacığına benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="ece8b-261">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Boxes:
    
    Top: 89.453415, Left: 481.95343, Right: 724.8073, Bottom: 388.32385, Label: Stop-Sign, Score: 0.99539465
    ```

<span data-ttu-id="ece8b-262">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="ece8b-262">Congratulations!</span></span> <span data-ttu-id="ece8b-263">Model Oluşturucu 'Yu kullanarak görüntülerde durma işaretlerini algılamaya yönelik bir makine öğrenimi modeli oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="ece8b-263">You've successfully built a machine learning model to detect stop signs in images using Model Builder.</span></span> <span data-ttu-id="ece8b-264">Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/ObjectDetection_StopSigns) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ece8b-264">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/ObjectDetection_StopSigns) GitHub repository.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ece8b-265">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ece8b-265">Additional resources</span></span>

<span data-ttu-id="ece8b-266">Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:</span><span class="sxs-lookup"><span data-stu-id="ece8b-266">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="ece8b-267">Model Oluşturucu senaryoları</span><span class="sxs-lookup"><span data-stu-id="ece8b-267">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="ece8b-268">ML.NET içinde ONNX kullanarak nesne algılama</span><span class="sxs-lookup"><span data-stu-id="ece8b-268">Object Detection using ONNX in ML.NET</span></span>](object-detection-onnx.md)
