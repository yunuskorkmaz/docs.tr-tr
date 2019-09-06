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
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>Öğretici: ML.NET içinde ONNX kullanarak nesneleri Algıla

Görüntülerdeki nesneleri saptamak için ML.NET ' de önceden eğitilen bir ONNX modeli kullanmayı öğrenin.

Bir nesne algılama modelini sıfırdan eğitmek için milyonlarca parametre, büyük miktarda etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir. Önceden eğitilen bir modelin kullanılması, eğitim sürecini kısayola etmenizi sağlar.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> - Sorunu anlama
> - ONNX 'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin
> - Modeli anlama
> - Önceden eğitilen modeli yeniden kullanma
> - Yüklü bir modelle nesneleri Algıla

## <a name="pre-requisites"></a>Ön koşullar

- [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.
- [Microsoft.ML NuGet paketi](https://www.nuget.org/packages/Microsoft.ML/)
- [Microsoft. ML. ımageanalytics NuGet paketi](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Microsoft. ML. OnnxTransformer NuGet paketi](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [Küçük YOLOv2 önceden eğitilen model](https://github.com/onnx/models/tree/master/tiny_yolov2)
- [Netron](https://github.com/lutzroeder/netron) seçim

## <a name="onnx-object-detection-sample-overview"></a>ONNX nesne algılama örneğine genel bakış

Bu örnek, önceden eğitilen derinlemesine öğrenme ONNX modelini kullanarak bir görüntüdeki nesneleri algılayan bir .NET Core konsol uygulaması oluşturur. Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) bulunabilir.

## <a name="what-is-object-detection"></a>Nesne algılama nedir?

Nesne algılama bir bilgisayar vizyonu sorunudur. Görüntü sınıflandırmasıyla yakından ilgili olarak, nesne algılama görüntü sınıflandırmasını daha ayrıntılı bir ölçekte gerçekleştirir. Nesne algılama hem görüntüler içindeki varlıkları bulur _hem_ de kategorilere ayırır. Görüntüler farklı türlerde birden çok nesne içerdiğinde nesne algılamayı kullanın.

![](./media/object-detection-onnx/img-classification-obj-detection.PNG)

Nesne algılama için bazı kullanım örnekleri şunları içerir:

- Kendi kendine yönlendiren otomobiller
- Robotics
- Yüz Algılama
- Çalışma alanı güvenliği
- Nesne sayımı
- Etkinlik tanıma

## <a name="select-a-deep-learning-model"></a>Derin öğrenme modeli seçin

Derin öğrenme, Machine Learning 'in bir alt kümesidir. Derin öğrenme modellerini eğmek için, büyük miktarlarda veri gerekir. Verilerdeki desenler, bir dizi katman tarafından temsil edilir. Verilerdeki ilişkiler, ağırlık içeren katmanlar arasında bağlantı olarak kodlanır. Ağırlığa göre daha güçlü olan ilişki. Toplu olarak, bu katman ve bağlantı serisi yapay sinir Networks olarak bilinir. Bir ağdaki daha fazla katman, "daha derin" ve bunu derin bir sinir ağı yapıyor.

Farklı türlerde sinir Networks, en yaygın çok katmanlı Perceptron (MLP), evsel sinir ağı (CNN) ve yinelenen sinir ağı (RNN). En temel, bir giriş kümesini bir çıktı kümesine eşleyen MLP 'dir. Bu sinir ağı, verilerin bir uzamsal veya zaman bileşeni olmadığında iyidir. CNN, veride bulunan uzamsal bilgileri işlemek için evsel katmanların kullanımını sağlar. CNNs için iyi bir kullanım örneği, bir görüntünün bölgesindeki bir özelliğin varlığını algılamak için görüntü işleme 'dir (örneğin, bir görüntünün merkezinde bir burun mu var?). Son olarak, RNNs durum veya belleğin girdi olarak kullanılmasına izin verir. RNNs, sıralı sıralama ve olayların bağlamı önemli olduğu zaman serisi analizi için kullanılır.

### <a name="understand-the-model"></a>Modeli anlama

Nesne algılama bir görüntü işleme görevidir. Bu nedenle, bu sorunu çözmek için eğitilen çoğu derin öğrenme modeli CNNs ' dir. Bu öğreticide kullanılan model, YOLOv2 modelinin kağıda açıklanan daha kompakt bir sürümü olan küçük YOLOv2 modelidir: ["YOLO9000: RedMon ve Fadhari](https://arxiv.org/pdf/1612.08242.pdf)tarafından daha Iyi, daha hızlı, daha güçlü. Küçük YOLOv2, Pascal VOC veri kümesi üzerinde eğitilir ve 20 farklı nesne sınıfı tahmin edebilen 15 katmandan oluşur. Küçük YOLOv2 özgün YOLOv2 modelinin sıkıştırılmış bir sürümü olduğundan, hız ve doğruluk arasında bir zorunluluğunu getirir yapılır. Modeli oluşturan farklı katmanlar netron gibi araçlar kullanılarak görselleştirilir. Modelin araştırılama, her katmanın, ilgili giriş/çıkış boyutlarıyla birlikte katman adını içerdiği sinir ağını oluşturan tüm katmanlar arasında bağlantı eşlemesini elde edecektir. Modelin girişlerini ve çıkışlarını tanımlamakta kullanılan veri yapıları, teniler olarak bilinir. Teniler, verileri N boyutlu bir şekilde depolayan kapsayıcılar olarak düşünülebilir. Küçük YOLOv2 durumunda, giriş katmanının adı olur `image` ve bir boyut `3 x 416 x 416`gerektirir. Çıktı katmanının adı olur `grid` ve boyutların `125 x 13 x 13`bir çıkış eğilimi oluşturur.

![](./media/object-detection-onnx/netron-model-map.png)

YOLO modeli bir görüntü `3(RGB) x 416px x 416px`alır. Model bu girişi alır ve bir çıktı üretmek için farklı katmanlardan geçirir. Çıktı, giriş görüntüsünü kılavuzdaki her hücreyle `13 x 13` `125` değerleri içeren bir kılavuza böler.

### <a name="what-is-an-onnx-model"></a>ONNX modeli nedir?

Open sinir Network Exchange (ONNX), AI modelleri için açık kaynak biçimidir. ONNX çerçeveler arasında birlikte çalışabilirliği destekler. Bu, bir modeli PyTorch gibi birçok popüler makine öğrenimi çerçevelerinden birinde eğitebileceğiniz anlamına gelir, ONNX biçimine dönüştürebilir ve ML.NET gibi farklı bir çerçevede ONNX modelini kullanabilirsiniz. Daha fazla bilgi edinmek için [Onnx Web sitesini](https://onnx.ai/)ziyaret edin.

![](./media/object-detection-onnx/onnx-frameworks.png)

Önceden eğitilen küçük YOLOv2 modeli, katmanların serileştirilmiş bir gösterimi ve bu katmanların öğrenilen desenleri ile ONNX biçiminde depolanır. ML.net ' de, onnx ile birlikte çalışabilirlik, [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) ve [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet paketleriyle birlikte sağlanır. Paket [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) , bir görüntüyü alan ve bir tahmin veya eğitim işlem hattına giriş olarak kullanılabilecek sayısal değerlere kodlayan bir dizi dönüştürme içerir. [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) Paket onnx çalışma zamanından yararlanır ve belirtilen girişe göre tahmine dayalı hale getirmek için bu modeli kullanır.

![](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>.NET Core projesini ayarlama

Artık ONNX 'in ne olduğuna ve küçük YOLOv2 nasıl çalıştığına ilişkin genel bir bilgiye sahip olduğunuza göre, uygulamanın derlenmesi zaman vardır.

### <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "ObjectDetection" adlı bir **.NET Core konsol uygulaması** oluşturun.

1. **Microsoft.ml NuGet paketini**yükler:

    - Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.
    - Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml**için arama yapın.
    - **Install** düğmesini seçin.
    - **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.
    - **Microsoft. ml. ımageanalytics** ve **Microsoft. ml. OnnxTransformer**için bu adımları tekrarlayın.

### <a name="prepare-your-data-and-pre-trained-model"></a>Verilerinizi hazırlayın ve önceden eğitilen modeli

1. [Proje Varlıkları Dizin ZIP dosyasını](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) indirin ve sıkıştırmayı açın.

1. Dizini objectdetection proje dizininize kopyalayın. `assets` Bu dizin ve alt dizinleri, bu öğretici için gerekli olan resim dosyalarını (küçük YOLOv2 modeli dışında, indirecek ve sonraki adımda ekleyeceğiniz) içerir.

1. [Onnx model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)ve unzip 'Ten [küçük YOLOv2 modelini](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) indirin.

    Komut istemi ' ni açın ve şu komutu girin:

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. Ayıklanan `model.onnx` dosyayı Dizin içinden *objectdetection* proje `assets\Model` dizininize kopyalayın ve olarak `TinyYolo2_model.onnx`yeniden adlandırın. Bu dizin, bu öğretici için gereken modeli içerir.

1. Çözüm Gezgini, varlık dizinindeki ve alt dizinlerde bulunan dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

*Program.cs* dosyasını açın ve aşağıdaki ek `using` deyimlerini dosyanın en üstüne ekleyin:

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

Ardından, çeşitli varlıkların yollarını tanımlayın.

1. İlk olarak, yöntemi `GetAbsolutePath` `Program` sınıfındaki yönteminin `Main` altına ekleyin.

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. Ardından, `Main` yöntemi içinde varlıklarınızın konumunu depolamak için alanlar oluşturun.

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

Giriş verilerinizi ve tahmin sınıflarınızı depolamak için projenize yeni bir dizin ekleyin.

**Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni klasör** **Ekle** > ' yi seçin. Yeni klasör Çözüm Gezgini göründüğünde, "Datayapýlarý" olarak adlandırın.

Yeni oluşturulan *Datayapýlarý* dizininde giriş veri sınıfınızı oluşturun.

1. **Çözüm Gezgini**, *datayapýlarý* dizinine sağ tıklayıp**Yeni öğe** **Ekle** > ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ImageNetData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *ImageNetData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadeyi *ImageNetData.cs*öğesinin en üstüne ekleyin:

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    Mevcut sınıf tanımını kaldırın ve `ImageNetData` sınıf için aşağıdaki kodu *ImageNetData.cs* dosyasına ekleyin:

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData`, giriş resmi veri sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:

    - `ImagePath`görüntünün depolandığı yolu içerir.
    - `Label`dosyanın adını içerir.

    Ayrıca, `ImageNetData` `ReadFromFile` belirtilenyolda`imageFolder` depolanan birden çok görüntü dosyasını yükleyen ve bunları bir nesnekoleksiyonuolarakdöndürenbiryöntemiiçerir.`ImageNetData`

*Veri yapıları* dizininde tahmin sınıfınızı oluşturun.

1. **Çözüm Gezgini**, *datayapýlarý* dizinine sağ tıklayıp**Yeni öğe** **Ekle** > ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ImageNetPrediction.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *ImageNetPrediction.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadeyi *ImageNetPrediction.cs*öğesinin en üstüne ekleyin:

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    Mevcut sınıf tanımını kaldırın ve `ImageNetPrediction` sınıf için aşağıdaki kodu *ImageNetPrediction.cs* dosyasına ekleyin:

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction`, tahmin verileri sınıfıdır ve şu `float[]` alana sahiptir:

    - `PredictedLabel`görüntüde algılanan her bir sınırlayıcı kutu için boyutları, objectlik Puanını ve sınıf olasılıkları içerir.

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal `DBContext` olarak da benzerdir.

`MLContext` `mlContext` Aşağıdaki satırı alanınaltındaki`outputFolder` program.cs yöntemine ekleyerek değişkeni yeni bir örneğiyle başlatın. `Main`

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a>İşlem sonrası model çıkışları için bir Ayrıştırıcı oluşturun

Model, her kılavuz `13 x 13` `32px x 32px`hücresinin bulunduğu bir görüntüyü kılavuza böler. Her kılavuz hücresi, 5 olası nesne sınırlayıcı kutusu içerir. Bir sınırlayıcı kutusunda 25 öğe vardır:

![](./media/object-detection-onnx/model-output-description.png)

- `x`sınırlama kutusu merkezinin ilişkilendirildiği kılavuz hücresine göre x konumu.
- `y`sınırlama kutusu merkezinin ilişkilendirildiği kılavuz hücresine göre y konumu.
- `w`sınırlayıcı kutunun genişliği.
- `h`sınırlayıcı kutunun yüksekliği.
- `o`bir nesnenin, sınırlayıcı kutusunda bulunduğu güven değeri, aynı zamanda objectlik puanı olarak da bilinir.
- `p1-p20`model tarafından tahmin edilen 20 sınıfın her biri için sınıf olasılıkların.

Toplamda, 5 sınırlayıcı kutulardan her birini tanımlayan 25 öğe, her kılavuz hücresinde bulunan 125 öğelerini yapar.

Önceden eğitilen onnx modeli tarafından oluşturulan çıkış, boyutlarla `21125` `125 x 13 x 13`birlikte bir ön sor öğelerinin öğelerini temsil eden bir float dizisidir. Model tarafından oluşturulan tahminleri bir tencursor 'a dönüştürmek için bazı işleme sonrası işler gereklidir. Bunu yapmak için, çıktıyı ayrıştırmaya yardımcı olmak üzere bir sınıf kümesi oluşturun.

Ayrıştırıcı sınıfları kümesini düzenlemek için projenize yeni bir dizin ekleyin.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni klasör** **Ekle** > ' yi seçin. Yeni klasör Çözüm Gezgini göründüğünde, "YoloParser" olarak adlandırın.

### <a name="create-bounding-boxes-and-dimensions"></a>Sınırlayıcı kutular ve boyutlar oluşturma

Modelin veri çıktısı, görüntü içindeki nesnelerin sınırlayıcı kutularının koordinatlarını ve boyutlarını içerir. Boyutlar için bir temel sınıf oluşturun.

1. **Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra**Yeni öğe** **Ekle** > ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *DimensionsBase.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *DimensionsBase.cs* dosyası kod düzenleyicisinde açılır. Tüm `using` deyimlerini ve varolan sınıf tanımını kaldırın.

    `DimensionsBase` Sınıfı için aşağıdaki kodu *DimensionsBase.cs* dosyasına ekleyin:

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase`Aşağıdaki `float` alanlara sahiptir:

    - `X`nesnenin x ekseni üzerindeki konumunu içerir.
    - `Y`nesnenin y ekseni üzerinde konumunu içerir.
    - `Height`nesnenin yüksekliğini içerir.
    - `Width`nesnenin genişliğini içerir.

Ardından, sınırlayıcı kutularınız için bir sınıf oluşturun.

1. **Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra**Yeni öğe** **Ekle** > ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *YoloBoundingBox.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *YoloBoundingBox.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadeyi *YoloBoundingBox.cs*öğesinin en üstüne ekleyin:

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    Mevcut sınıf tanımının hemen üzerinde, ilgili sınırlayıcı kutusunun boyutlarını içerecek şekilde `BoundingBoxDimensions` `DimensionsBase` sınıfından devralan adlı yeni bir sınıf tanımı ekleyin.

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    Mevcut `YoloBoundingBox` sınıf tanımını kaldırın ve `YoloBoundingBox` sınıf için aşağıdaki kodu *YoloBoundingBox.cs* dosyasına ekleyin:

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    `YoloBoundingBox`aşağıdaki alanlara sahiptir:

    - `Dimensions`sınırlayıcı kutunun boyutlarını içerir.
    - `Label`sınırlayıcı kutusunda algılanan nesne sınıfını içerir.
    - `Confidence`sınıfının güvenini içerir.
    - `Rect`sınırlayıcı kutunun boyutlarının dikdörtgen gösterimini içerir.
    - `BoxColor`görüntüde çizim yapmak için kullanılan ilgili sınıfla ilişkili rengi içerir.

### <a name="create-the-parser"></a>Ayrıştırıcı oluşturma

Artık boyut ve sınırlama kutuları için sınıflar oluşturuldığına göre, ayrıştırıcısı oluşturma zamanı.

1. **Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra**Yeni öğe** **Ekle** > ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *YoloOutputParser.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *YoloOutputParser.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadeyi *YoloOutputParser.cs*öğesinin en üstüne ekleyin:

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    Varolan `YoloOutputParser` sınıf tanımının içinde, görüntüdeki her bir hücrenin boyutlarını içeren bir iç içe sınıf ekleyin. Sınıf tanımının en üstündeki `CellDimensions` `DimensionsBase` `YoloOutputParser` sınıftan devralan sınıf için aşağıdaki kodu ekleyin.

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. `YoloOutputParser` Sınıf tanımı içinde aşağıdaki sabiti ve alanları ekleyin.

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - `ROW_COUNT`, görüntüdeki görüntünün bölüneceğini, ızgaradaki satır sayısıdır.
    - `COL_COUNT`, görüntüde bölünen, kılavuzdaki sütun sayısıdır.
    - `CHANNEL_COUNT`kılavuzun tek bir hücresinde bulunan toplam değer sayısıdır.
    - `BOXES_PER_CELL`, bir hücredeki sınırlayıcı kutuların sayısıdır,
    - `BOX_INFO_FEATURE_COUNT`, bir kutu içinde (x, y, Height, Width, güvenirlik) bulunan özelliklerin sayısıdır.
    - `CLASS_COUNT`, her bir sınırlayıcı kutusunda bulunan sınıf tahminleri sayısıdır.
    - `CELL_WIDTH`, görüntü kılavuzundaki bir hücrenin genişliğidir.
    - `CELL_HEIGHT`, görüntü kılavuzundaki bir hücrenin yüksekliğidir.
    - `channelStride`Kılavuzdaki geçerli hücrenin başlangıç konumudur.

    Model, Puanlama olarak da bilinen bir tahmin yaptığında, `416px x 416px` giriş görüntüsünü `13 x 13`boyutunun bir hücre kılavuzuna böler. Her hücre içerir `32px x 32px`. Her hücrede, 5 Özellik (x, y, Width, Height, güvenirlik) içeren 5 sınırlayıcı kutu vardır. Ayrıca, her sınırlayıcı kutu, bu örnekte 20 olan her bir sınıf olasılığını içerir. Bu nedenle, her hücre 125 bilgi parçasını içerir (5 özellik + 20 sınıf olasılıkların).

Tüm 5 sınırlayıcı kutular için aşağıdan `channelStride` bir çıpası listesi oluşturun:

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

Bağlayıcıların sınırlayıcı kutuların önceden tanımlanmış yükseklik ve genişlik oranları vardır. Bir model tarafından algılanan çoğu nesne veya sınıfın benzer oranları vardır. Bu, sınırlayıcı kutular oluşturmak için kullanışlıdır. Sınırlayıcı kutuları tahmin etmek yerine, önceden tanımlanmış boyutlardan olan fark, bu nedenle, sınırlayıcı kutuyu tahmin etmek için gereken hesaplamayı azaltmak için hesaplanır. Genellikle bu bağlantı oranları, kullanılan veri kümesi temel alınarak hesaplanır. Bu durumda, veri kümesi bilindiği ve değerler önceden hesaplandığından, bağlantılar sabit kodlanmış olabilir.

Ardından, modelin tahmin edecek etiketleri veya sınıfları tanımlayın. Bu model, özgün YOLOv2 modeli tarafından tahmin edilen toplam sınıf sayısının bir alt kümesi olan 20 sınıfı tahmin eder.

Altına etiket listenizi ekleyin `anchors`.

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

Sınıfların her biriyle ilişkili renkler vardır. Sınıf renklerinizi aşağıdaki `labels`gibi atayın:

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>Yardımcı işlevler oluşturma

İşleme sonrası aşamasında yer alan bir dizi adım vardır. Bu konuda yardımcı olmak için birkaç yardımcı yöntem kullanılabilir.

Ayrıştırıcı tarafından kullanılan yardımcı yöntemler şunlardır:

- `Sigmoid`0 ile 1 arasında bir sayı çıkışı yapan sigmoıd işlevini uygular.
- `Softmax`bir giriş vektörünü bir olasılık dağıtımına normalleştirir.
- `GetOffset`tek boyutlu model çıkışındaki öğeleri bir `125 x 13 x 13` tencursor içindeki ilgili konuma eşler.
- `ExtractBoundingBoxes`Model çıktısından `GetOffset` yöntemi kullanarak sınırlama kutusu boyutlarını ayıklar.
- `GetConfidence`modelin bir nesne algıladığını ve bir yüzdeyi dönüştürmek için `Sigmoid` işlevi kullandığını belirten güvenirlik değerini ayıklar.
- `MapBoundingBoxToCell`, sınırlayıcı kutu boyutlarını kullanır ve bunları görüntünün içindeki ilgili hücresiyle eşler.
- `ExtractClasses``GetOffset` yöntemi kullanarak model çıktısından sınırlama kutusu için sınıf tahminlerini ayıklar ve `Softmax` yöntemi kullanarak bunları bir olasılık dağıtımına dönüştürür.
- `GetTopResult`en yüksek olasılığa sahip tahmin edilen sınıflar listesinden sınıfı seçer.
- `IntersectionOverUnion`daha düşük olasılıklara sahip sınırlayıcı kutuları filtreler.

Listenizin altındaki tüm yardımcı yöntemleri için kodu ekleyin `classColors`.

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

Tüm yardımcı yöntemlerini tanımladıktan sonra, model çıkışını işlemek için bunları kullanma zamanı da vardır.

Yönteminin altında, model tarafından oluşturulan `ParseOutputs` çıktıyı işlemek için yöntemi oluşturun. `IntersectionOverUnion`

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

Sınırlayıcı kutularınızı depolamak ve `ParseOutputs` yöntemin içinde değişkenleri tanımlamak için bir liste oluşturun.

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

Her resim bir `13 x 13` hücre kılavuzuna bölünmüştür. Her hücrede beş sınırlayıcı kutu bulunur. `boxes` Değişkenin altında, her hücrenin içindeki tüm kutuları işlemek için kod ekleyin.

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

En içteki döngünün içinde, tek boyutlu model çıkışı içindeki geçerli kutunun başlangıç konumunu hesaplayın.

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

Doğrudan altında, geçerli sınırlayıcı kutusunun `ExtractBoundingBoxDimensions` boyutlarını almak için yöntemini kullanın.

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

Ardından, geçerli sınırlayıcı `GetConfidence` kutusunun güvenini almak için yöntemini kullanın.

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

Bundan sonra, geçerli sınırlayıcı `MapBoundingBoxToCell` kutuyu işlenmekte olan geçerli hücreyle eşlemek için yöntemini kullanın.

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

Daha fazla işlem yapmadan önce, güven değerinin sağlanan eşikten büyük olup olmadığını kontrol edin. Aksi takdirde, sonraki sınırlayıcı kutuyu işleyin.

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

Aksi takdirde, çıktıyı işlemeye devam edin. Sonraki adımda, `ExtractClasses` yöntemi kullanılarak geçerli sınırlayıcı kutu için öngörülen sınıfların olasılık dağılımı alınır.

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

Daha sonra, geçerli `GetTopResult` kutu için en yüksek olasılığa sahip sınıfın değerini ve dizinini almak ve Puanını hesaplamak için yöntemini kullanın.

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

`topScore` ' İ bir kez daha kullanarak yalnızca belirtilen eşiğin üzerinde olan sınırlayıcı kutuları saklayın.

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

Son olarak, geçerli sınırlayıcı kutusu eşiği aşarsa, yeni `BoundingBox` bir nesne oluşturun ve `boxes` listeye ekleyin.

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

Görüntüdeki tüm hücreler işlendikten sonra `boxes` listeyi geri döndürün. Aşağıdaki return ifadesini `ParseOutputs` yöntemine en dıştaki for-Loop altına ekleyin.

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>Çakışan kutuları filtrele

Artık yüksek oranda uygun sınırlama kutularının tümü model çıktısından ayıklandığına göre, çakışan görüntüleri kaldırmak için ek filtrelemenin yapılması gerekir. Yönteminin altına adlı `FilterBoundingBoxes` bir yöntem ekleyin: `ParseOutputs`

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

`FilterBoundingBoxes` Yöntemi içinde, algılanan kutuların boyutuna eşit bir dizi oluşturarak ve tüm yuvaları etkin veya işleme hazırmış olarak işaretleyerek devre dışı bırakın.

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

Ardından, sınırlayıcı kutularınızı içeren listeyi güvenle azalan sırada sıralayın.

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

Bundan sonra filtrelenmiş sonuçları tutacak bir liste oluşturun.

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

Her bir sınırlayıcı kutunun her biri üzerinde yinelenerek her bir sınırlayıcı kutuyu işlemeye başlayın.

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

Bu for-döngüsünün içinde, geçerli sınırlayıcı kutusunun işlenip işlenemeyeceğini kontrol edin.

```csharp
if (isActiveBoxes[i])
{

}
```

Bu durumda, sınırlama kutusunu sonuçlar listesine ekleyin. Sonuçlar Ayıklanacak belirlenen kutu sınırını aşarsa döngüyü sonlandırın. Aşağıdaki kodu if-deyimin içine ekleyin.

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

Aksi takdirde, bitişik sınırlayıcı kutulara bakın. Aşağıdaki kodu Box limit denetiminin altına ekleyin.

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

İlk kutu gibi, bitişik kutu etkin veya işlenmek üzere hazırsanız, ilk kutunun ve ikinci kutunun belirtilen eşiği `IntersectionOverUnion` aşıp aşmadığını denetlemek için yöntemini kullanın. Aşağıdaki kodu, en son for-loop ' a ekleyin.

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

Bitişik sınırlayıcı kutuları denetleyen en büyük for-Loop dışında, işlenmek üzere kalan herhangi bir sınırlama kutusu olup olmadığına bakın. Aksi takdirde, için dış döngüden çıkar.

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

Son olarak, `FilterBoundingBoxes` yöntemin ilk döngüsü dışında, sonuçları döndürün:

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

Harika! Artık bu kodu Puanlama modeliyle birlikte kullanmanın zamanı.

## <a name="use-the-model-for-scoring"></a>Puanlama için modeli kullanma

İşlem sonrasında olduğu gibi, Puanlama adımlarında birkaç adım vardır. Bu konuda yardım almak için, projenize Puanlama mantığını içerecek bir sınıf ekleyin.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *OnnxModelScorer.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *OnnxModelScorer.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadeyi *OnnxModelScorer.cs*öğesinin en üstüne ekleyin:

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    `OnnxModelScorer` Sınıf tanımı içinde aşağıdaki değişkenleri ekleyin.

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    Doğrudan altında, daha önce tanımlanmış değişkenleri başlatacak `OnnxModelScorer` sınıf için bir Oluşturucu oluşturun.

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    Oluşturucuyu oluşturduktan sonra, görüntü ve model ayarlarıyla ilgili değişkenleri içeren birkaç yapı tanımlayın. Model için girdi olarak `ImageNetSettings` beklenen yüksekliği ve genişliği içeren bir struct oluşturun.

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    Bundan sonra, modelin giriş ve çıkış `TinyYoloModelSettings` katmanlarının adlarını içeren adlı başka bir struct oluşturun. Modelin giriş ve çıkış katmanlarının adını görselleştirmek için, [netron](https://github.com/lutzroeder/netron)gibi bir araç kullanabilirsiniz.

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    Ardından, Puanlama için kullanılan ilk yöntem kümesini oluşturun. Sınıfınızıniçindeki`OnnxModelScorer`yöntemioluşturun. `LoadModel`

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    `LoadModel` Yöntemi içinde günlüğe kaydetmek için aşağıdaki kodu ekleyin.

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    ML.NET işlem hatları, [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) yöntemi çağrıldığında üzerinde çalışılacak veri şemasını bilmelidir. Bu durumda, eğitimle benzer bir süreç kullanılacaktır. Ancak, hiçbir gerçek eğitim gerçekleşmediğinden boş [`IDataView`](xref:Microsoft.ML.IDataView)kullanılması kabul edilebilir. Boş bir listeden [`IDataView`](xref:Microsoft.ML.IDataView) işlem hattı için yeni bir oluştur.

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    Bunun altında, işlem hattını tanımlayın. İşlem hattı dört dönüşümden oluşur.

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)görüntüyü bir bit eşlem olarak yükler.
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)görüntüyü belirtilen boyuta ölçeklendirin (Bu durumda, `416 x 416`).
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)görüntünün piksel temsilini bir bit eşlemden sayısal bir Vector öğesine değiştirir.
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)ONNX modelini yükler ve belirtilen verileri öğrenmek için onu kullanır.

    İşlem hattınızı `LoadModel` `data` değişkenin altındaki yöntemde tanımlayın.

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    Şimdi Puanlama için model oluşturma zamanı. İşlem hattında [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) yöntemi çağırın ve daha fazla işleme için döndürün.

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

Model yüklendikten sonra tahmin yapmak için kullanılabilir. Bu işlemi kolaylaştırmak için `PredictDataUsingModel` `LoadModel` yönteminin altında adlı bir yöntem oluşturun.

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

`PredictDataUsingModel`İçinde, günlüğe kaydetmek için aşağıdaki kodu ekleyin.

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

Ardından, verileri öğrenmek [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) için yöntemini kullanın.

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

Tahmin edilen olasılıkların ayıklanmasını ayıklayın ve bunları ek işleme için geri döndürün.

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

Her iki adım de ayarlandığına göre, bunları tek bir yöntemde birleştirin. Yönteminin altında adlı `Score`yeni bir yöntem ekleyin. `PredictDataUsingModel`

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

Neredeyse bitti! Şimdi bunu tüm kullanıma yerleştirme zamanı.

## <a name="detect-objects"></a>Nesneleri Algıla

Tüm kurulumun tamamlandığına göre, bazı nesneleri algılamaya zaman atalım. *Program.cs* sınıfınıza scorer ve ayrıştırıcıya başvurular ekleyerek başlayın.

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a>Model çıkışlarını puan ve ayrıştırma

`Main` *Program.cs* sınıfınızın yöntemi içinde, bir try-catch ifadesini ekleyin.

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

`try` Bloğun içinde, nesne algılama mantığını uygulamaya başlayın. İlk olarak, verileri bir [`IDataView`](xref:Microsoft.ML.IDataView)öğesine yükleyin.

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

Ardından, bir örneği `OnnxModelScorer` oluşturun ve yüklenen verileri almak için onu kullanın.

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

Şimdi işleme sonrası adımının zamanı. Bir örneği `YoloOutputParser` oluşturun ve model çıkışını işlemek için onu kullanın.

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

Model çıkışı işlendikten sonra, görüntülerde sınırlayıcı kutuları çizmeniz zaman alır.

### <a name="visualize-predictions"></a>Tahminleri görselleştirin

Model, görüntüleri puanladıktan ve çıktılar işlendikten sonra, görüntü üzerinde sınırlayıcı kutular çizmelidir. Bunu yapmak için `DrawBoundingBox` *program.cs*içindeki `GetAbsolutePath` yönteminin altına adlı bir yöntem ekleyin.

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

İlk olarak, görüntüyü yükleyin ve `DrawBoundingBox` yöntemdeki yükseklik ve genişlik boyutlarını alın.

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

Ardından, model tarafından algılanan her bir sınırlayıcı kutu üzerinde yinelemek için her bir For-Each döngüsü oluşturun.

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

For-each döngüsünün içinde, sınırlayıcı kutunun boyutlarını alın.

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

Sınırlayıcı kutunun boyutları model girişine `416 x 416`karşılık geldiğinden, sınırlayıcı kutu boyutlarını görüntünün gerçek boyutuyla eşleşecek şekilde ölçeklendirin.

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

Ardından, her bir sınırlayıcı kutusunun üzerinde görünecek metin için bir şablon tanımlayın. Metin, ilgili sınırlayıcı kutusunun içindeki nesnenin sınıfını ve güveni içerir.

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

Görüntüde çizim yapmak için bir [`Graphics`](xref:System.Drawing.Graphics) nesneye dönüştürün.

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

Kod bloğunun içinde, [`Graphics`](xref:System.Drawing.Graphics) grafiğin nesne ayarlarını ayarlayın. `using`

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

Bunun altında metin ve sınırlayıcı kutusu için yazı tipi ve renk seçeneklerini ayarlayın.

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

[`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) Yöntemi kullanarak metni içermesi için sınırlayıcı kutunun üzerindeki bir dikdörtgeni oluşturun ve girin. Bu, metnin karşıtlığına ve okunabilirliği iyileştirmenize yardımcı olur.

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

Ardından, [`DrawString`](xref:System.Drawing.Graphics.DrawString*) ve [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) yöntemlerini kullanarak görüntüye metin ve sınırlayıcı kutusunu çizin.

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

For-each döngüsünün dışında, içindeki `outputDirectory`görüntüleri kaydetmek için kod ekleyin.

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

Uygulamanın çalışma zamanında beklendiği gibi tahmine dayalı hale getiren ek geri bildirimde bulunmak için, algılanan nesneleri konsola çıkarmak `LogDetectedObjects` üzere program.cs `DrawBoundingBox` dosyasındaki yönteminin altına adlı bir yöntem ekleyin.

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

Tahmine dayalı olarak görsel geri bildirim oluşturmaya yönelik yardımcı yöntemlere sahip olduğunuza göre, her bir puanlanmış görüntünün üzerinde yinelemek için bir for döngüsü ekleyin.

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

For döngüsü içinde, görüntü dosyasının adını ve onunla ilişkili sınırlayıcı kutuları alın.

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

Bunun altında, görüntüdeki sınırlayıcı `DrawBoundingBox` kutuları çizmek için yöntemini kullanın.

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

Son olarak,, `LogDetectedObjects` tahmine dayalı olarak konsola çıkış yapmak için yöntemini kullanın.

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

Try-catch ifadesinden sonra, işlemin çalıştığını göstermek için ek mantık ekleyin.

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

İşte bu kadar!

## <a name="results"></a>Sonuçlar

Önceki adımları uyguladıktan sonra konsol uygulamanızı çalıştırın (CTRL + F5). Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır. Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.

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

Sınırlayıcı kutuları olan görüntüleri görmek için `assets/images/output/` dizine gidin. Aşağıda, işlenen görüntülerden birindeki bir örnek verilmiştir.

![](./media/object-detection-onnx/image3.jpg)

Tebrikler! Artık ml.net ' de önceden eğitilen `ONNX` bir modeli yeniden çalıştırarak nesne algılama için bir makine öğrenimi modelini başarıyla oluşturdunuz.

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> - Sorunu anlama
> - ONNX 'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin
> - Modeli anlama
> - Önceden eğitilen modeli yeniden kullanma
> - Yüklü bir modelle nesneleri Algıla

Genişletilmiş bir nesne algılama örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/machinöğrenim-Samples GitHub deposu](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/DeepLearning_ObjectDetection_Onnx)
