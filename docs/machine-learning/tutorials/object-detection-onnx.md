---
title: 'Öğretici: ONNX derin öğrenme modelini kullanarak nesneleri algılama'
description: Bu öğretici, görüntülerdeki nesneleri algılamak için ML.NET önceden eğitilmiş bir ONNX derin öğrenme modelinin nasıl kullanılacağını göstermektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9677c6c9da542123146fc9eef9c311ef30c174e
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608016"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>Öğretici: ML.NET ONNX kullanarak nesneleri algılama

Görüntülerdeki nesneleri algılamak için ML.NET önceden eğitilmiş bir ONNX modelini nasıl kullanacağınızı öğrenin.

Bir nesne algılama modelini sıfırdan eğitmek için milyonlarca parametre, büyük miktarda etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) gerekir. Önceden eğitilmiş bir model kullanmak, eğitim sürecini kısayolla kesmenize olanak tanır.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - ONNX'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin
> - Modeli anlama
> - Önceden eğitilmiş modeli yeniden kullanma
> - Yüklü bir modelle nesneleri algılama

## <a name="pre-requisites"></a>Ön koşullar

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonrası veya Visual Studio 2017 sürümü 15.6 veya daha sonra ".NET Core çapraz platform geliştirme" iş yükü yüklü.
- [Microsoft.ML NuGet Paketi](https://www.nuget.org/packages/Microsoft.ML/)
- [Microsoft.ML.ImageAnalytics NuGet Paketi](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Microsoft.ML.OnnxTransformer NuGet Paketi](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [Tiny YOLOv2 önceden eğitilmiş model](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- [Netron](https://github.com/lutzroeder/netron) (isteğe bağlı)

## <a name="onnx-object-detection-sample-overview"></a>ONNX nesne algılama örneği genel bakış

Bu örnek, önceden eğitilmiş derin öğrenme ONNX modelini kullanarak görüntü içindeki nesneleri algılayan bir .NET çekirdek konsol uygulaması oluşturur. Bu örneğin kodu GitHub'daki [dotnet/machinelearning-samples deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) bulunabilir.

## <a name="what-is-object-detection"></a>Nesne algılama nedir?

Nesne algılama bir bilgisayar görme sorunudur. Görüntü sınıflandırması ile yakından ilişkili olmakla birlikte, nesne algılama daha ayrıntılı bir ölçekte görüntü sınıflandırması gerçekleştirir. Nesne algılama, görüntülerdeki varlıkları hem bulur hem de _kategorilere_ ayırar. Görüntüler farklı türde birden çok nesne içeriyorsa nesne algılamayı kullanın.

![Görüntü Sınıflandırması ile Nesne Sınıflandırması'nı gösteren ekran görüntüleri.](./media/object-detection-onnx/img-classification-obj-detection.png)

Nesne algılama için bazı kullanım örnekleri şunlardır:

- Kendi Kendine Giden Arabalar
- Robotik
- Yüz Algılama
- İşyeri Güvenliği
- Nesne Sayma
- Etkinlik Tanıma

## <a name="select-a-deep-learning-model"></a>Derin öğrenme modeli seçin

Derin öğrenme, makine öğreniminin bir alt kümesidir. Derin öğrenme modellerini eğitmek için büyük miktarlarda veri gereklidir. Verilerdeki desenler bir dizi katmanla temsil edilir. Verilerdeki ilişkiler ağırlıkiçeren katmanlar arasındaki bağlantı olarak kodlanır. Ağırlık ne kadar yüksekse, ilişki o kadar güçlü. Topluca, katmanları ve bağlantıların bu dizi yapay sinir ağları olarak bilinir. Bir ağ da daha fazla katman, "derin" o, derin bir sinir ağı yapma.

Çok Katmanlı Perceptron (MLP), Kvolürtional Nöral Ağ (CNN) ve Tekrarlayan Sinir Ağı (RNN) olmak üzere farklı sinir ağları türleri vardır. En temel işlem kümesini bir biriçe çıkaran MLP' dir. Veriler uzamsal veya zaman bileşeni olmadığında bu sinir ağı iyidir. CNN, verilerde bulunan uzamsal bilgileri işlemek için kıvrımlı katmanları kullanır. CNN'ler için iyi bir kullanım örneği, görüntünün bir bölgesinde bir özelliğin varlığını algılamak için görüntü işlemedir (örneğin, görüntünün ortasında bir burun var mıdır?). Son olarak, RN'ler durum veya belleğin kalıcılığının girdi olarak kullanılmasına izin verir. RN'ler, olayların sıralı sıralama ve bağlamının önemli olduğu zaman serisi çözümlemesi için kullanılır.

### <a name="understand-the-model"></a>Modeli anlama

Nesne algılama bir görüntü işleme görevidir. Bu nedenle, bu sorunu çözmek için eğitilmiş en derin öğrenme modelleri CNNs vardır. Bu öğretici kullanılan model Tiny YOLOv2 modeli, YOLOv2 modeli kağıt açıklanan daha kompakt bir versiyonu: ["YOLO9000: Daha Iyi, Daha Hızlı, Güçlü" Redmon ve Fadhari tarafından](https://arxiv.org/pdf/1612.08242.pdf). Tiny YOLOv2 Pascal VOC veri seti üzerinde eğitilmiştir ve nesnelerin 20 farklı sınıfları tahmin edebilirsiniz 15 katmanları oluşur. Tiny YOLOv2 orijinal YOLOv2 modelinin yoğunlaştırılmış bir versiyonu olduğundan, hız ve doğruluk arasında bir denge yapılır. Modeli oluşturan farklı katmanlar Netron gibi araçlar kullanılarak görselleştirilebilir. Modelin incelenmesi, her bir katmanın ilgili giriş / çıkış boyutlarıyla birlikte katmanın adını içereceği sinir ağını oluşturan tüm katmanlar arasındaki bağlantıların eşlenmesini sağlar. Modelin giriş ve çıkışlarını tanımlamak için kullanılan veri yapıları tensör olarak bilinir. Tentenler, verileri N boyutlu olarak depolayan kapsayıcılar olarak düşünülebilir. Tiny YOLOv2 durumunda, giriş katmanının adı ve `image` boyutları `3 x 416 x 416`bir tensor bekliyor. Çıkış katmanının adı `grid` ve boyutların `125 x 13 x 13`bir çıkış tensörü oluşturur.

![Giriş katmanı gizli katmanlara bölündükten sonra çıktı katmanı](./media/object-detection-onnx/netron-model-map-layers.png)

YOLO modeli bir `3(RGB) x 416px x 416px`görüntü alır. Model bu girişi alır ve bir çıktı üretmek için farklı katmanlar aracılığıyla geçer. Çıktı, giriş görüntüsünü, ızgaradaki `13 x 13` her hücre değerlerden `125` oluşan bir ızgaraya böler.

### <a name="what-is-an-onnx-model"></a>ONNX modeli nedir?

Açık Sinir Ağ Değişimi (ONNX), AI modelleri için açık kaynak biçimidir. ONNX, çerçeveler arasında birlikte çalışabilirliği destekler. Bu, PyTorch gibi birçok popüler makine öğrenme çerçevelerinden birinde bir model eğitebileceğiniz, ONNX formatına dönüştürebileceğiniz ve ONNX modelini ML.NET gibi farklı bir çerçevede kullanabileceğiniz anlamına gelir. Daha fazla bilgi için [ONNX web sitesini](https://onnx.ai/)ziyaret edin.

![ONNX destekli biçimlerin diyagramı kullanılıyor.](./media/object-detection-onnx/onnx-supported-formats.png)

Önceden eğitilmiş Tiny YOLOv2 modeli ONNX formatında depolanır, katmanların seri leştirilmiş bir gösterimi ve bu katmanların öğrenilen desenleri. ML.NET'da ONNX [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) ile birlikte çalışabilirlik [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) ve NuGet paketleri ile sağlanır. Paket, [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) bir görüntüyü alıp bir tahmin veya eğitim ardışık dizisine girdi olarak kullanılabilecek sayısal değerlere kodlayan bir dizi dönüşüm içerir. Paket, [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) onnx modelini yüklemek ve sağlanan girdiye dayalı öngörülerde bulunmak için onnx çalışma süresinden yararlanır.

![ONNX dosyasının ONNX Runtime'a veri akışı.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>.NET Core projesini ayarlama

Şimdi ONNX ne olduğunu ve nasıl Tiny YOLOv2 çalışır genel bir anlayışa sahip, bu uygulama oluşturmak için zamanı.

### <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "ObjectDetection" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.

1. Microsoft.ML **NuGet Paketini**Yükleyin:

    - Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.
    - Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML**arayın.
    - **Yükle** düğmesini seçin.
    - **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.
    - **Microsoft.ML.ImageAnalytics** ve **Microsoft.ML.OnnxTransformer**için bu adımları yineleyin.

### <a name="prepare-your-data-and-pre-trained-model"></a>Verilerinizi ve önceden eğitilmiş modeli hazırlayın

1. [Proje varlıkları dizin zip dosyasını](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) indirin ve zip'i açın.

1. `assets` Dizini *ObjectDetection* proje dizininize kopyalayın. Bu dizin ve alt dizinleri bu öğretici için gerekli olan resim dosyalarını (bir sonraki adımda indirip ekleyeceğiniz Tiny YOLOv2 modeli hariç) içerir.

1. [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2) [Tiny YOLOv2 modeli](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) indirin , ve unzip.

    Komut istemini açın ve aşağıdaki komutu girin:

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. Çıkarılan `model.onnx` dosyayı dizinden yalnızca *ObjectDetection* proje `assets\Model` dizininizin fermuarlı içine `TinyYolo2_model.onnx`kopyalayın ve yeniden adlandırın. Bu dizin, bu öğretici için gerekli modeli içerir.

1. Çözüm Gezgini'nde, varlık dizini ve alt dizinindeki dosyaların her birini sağ tıklatın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıflar oluşturma ve yolları tanımlama

*Program.cs* dosyasını açın ve `using` dosyanın üst üstüne aşağıdaki ek deyimleri ekleyin:

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

Ardından, çeşitli varlıkların yollarını tanımlayın.

1. İlk olarak, `GetAbsolutePath` `Program` sınıfta `Main` yöntemin altına yöntemi ekleyin.

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. Ardından, yöntemin `Main` içinde, varlıklarınızın konumunu depolamak için alanlar oluşturun.

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

Giriş verilerinizi ve tahmin sınıflarınızı depolamak için projenize yeni bir dizin ekleyin.

**Çözüm Gezgini'nde**projeyi sağ tıklatın ve ardından**Yeni Klasör** **Ekle'yi** > seçin. Çözüm Gezgini'nde yeni klasör göründüğünde, "Veri Yapıları" adını verin.

Yeni oluşturulan *DataStructures* dizininde giriş veri sınıfını oluşturun.

1. **Çözüm Gezgini'nde,** *DataStructures* dizinini sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *ImageNetData.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

    *ImageNetData.cs* dosyası kod düzenleyicisinde açılır. ImageNetData.cs üstüne `using` aşağıdaki ifadeyi *ImageNetData.cs*ekleyin:

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    Varolan sınıf tanımını kaldırın ve `ImageNetData` *ImageNetData.cs* dosyasına sınıf için aşağıdaki kodu ekleyin:

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData`giriş görüntü veri sınıfıdır ve <xref:System.String> aşağıdaki alanlara sahiptir:

    - `ImagePath`görüntünün depolandığı yolu içerir.
    - `Label`dosyanın adını içerir.

    Ayrıca, `ImageNetData` belirtilen `ReadFromFile` `imageFolder` yolda depolanan birden çok resim dosyasını yükleyen ve `ImageNetData` bunları nesne koleksiyonu olarak döndüren bir yöntem içerir.

*Veri Yapıları* dizininde tahmin sınıfınızı oluşturun.

1. **Çözüm Gezgini'nde,** *DataStructures* dizinini sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *ImageNetPrediction.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

    *ImageNetPrediction.cs* dosyası kod düzenleyicisinde açılır. ImageNetPrediction.cs üstüne `using` aşağıdaki ifadeyi *ImageNetPrediction.cs*ekleyin:

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    Varolan sınıf tanımını kaldırın ve `ImageNetPrediction` *ImageNetPrediction.cs* dosyasına sınıf için aşağıdaki kodu ekleyin:

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction`tahmin veri sınıfıdır ve `float[]` aşağıdaki alana sahiptir:

    - `PredictedLabel`görüntüde algılanan sınırlayıcı kutuların her biri için boyutlar, nesnelik puanı ve sınıf olasılıkları içerir.

### <a name="initialize-variables-in-main"></a>Main'deki değişkenleri başlatma

[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç `mlContext` noktasıdır ve başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur. Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.

`outputFolder` Alanın altındaki `mlContext` *Program.cs* `Main` yöntemine `MLContext` aşağıdaki satırı ekleyerek değişkeni yeni bir örnekle başolarak adlandırır.

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a>İşlem sonrası model çıktıları için ayrıştırıcı oluşturma

Model, görüntüyü her ızgara `13 x 13` hücresinin olduğu `32px x 32px`bir ızgaraya böler. Her ızgara hücresi 5 potansiyel nesne sınırlayıcı kutu içerir. Sınırlayıcı kutuda 25 öğe vardır:

![Soldaki Kılavuz örneği ve sağdaki Sınırlayıcı Kutu örneği](./media/object-detection-onnx/model-output-description.png)

- `x`ilişkili olduğu ızgara hücresine göre sınırlayıcı kutu merkezinin x konumu.
- `y`ilişkili olduğu ızgara hücresine göre sınırlayıcı kutu merkezinin y konumu.
- `w`sınırlayıcı kutunun genişliği.
- `h`sınırlama kutusunun yüksekliği.
- `o`nesnelik puanı olarak da bilinen sınırlayıcı kutu içinde bir nesnenin bulunduğu güven değeri.
- `p1-p20`model tarafından öngörülen 20 sınıfın her biri için sınıf olasılıkları.

Toplamda, 5 sınırlama kutusunun her birini açıklayan 25 eleman, her bir ızgara hücresinde bulunan 125 öğeyi içerir.

Önceden eğitilmiş ONNX modeli tarafından oluşturulan çıktı, `21125`boyutları `125 x 13 x 13`olan bir tensörün elemanlarını temsil eden bir float uzunluğu dizisidir. Model tarafından oluşturulan öngörüleri bir tentöre dönüştürmek için bazı işlem sonrası çalışmalar gereklidir. Bunu yapmak için, çıktıyı ayrıştırmaya yardımcı olacak bir sınıf kümesi oluşturun.

Ayrıştırıcı sınıfları kümesini düzenlemek için projenize yeni bir dizin ekleyin.

1. **Çözüm Gezgini'nde**projeyi sağ tıklatın ve ardından**Yeni Klasör** **Ekle'yi** > seçin. Çözüm Gezgini'nde yeni klasör göründüğünde, "YoloParser" adını verdi.

### <a name="create-bounding-boxes-and-dimensions"></a>Sınırlayıcı kutular ve boyutlar oluşturma

Model tarafından veri çıktısı, görüntü içindeki nesnelerin sınırlayıcı kutularının koordinatlarını ve boyutlarını içerir. Boyutlar için bir taban sınıf oluşturun.

1. **Çözüm Gezgini'nde,** *YoloParser* dizinine sağ tıklayın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *DimensionsBase.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

    kod düzenleyicisinde *DimensionsBase.cs* dosyası açılır. Tüm `using` deyimleri ve varolan sınıf tanımını kaldırın.

    `DimensionsBase` *DimensionsBase.cs* dosyasına sınıf için aşağıdaki kodu ekleyin:

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase`aşağıdaki `float` özelliklere sahiptir:

    - `X`x ekseni boyunca nesnenin konumunu içerir.
    - `Y`y ekseni boyunca nesnenin konumunu içerir.
    - `Height`nesnenin yüksekliğini içerir.
    - `Width`nesnenin genişliğini içerir.

Ardından, sınırlayıcı kutularınız için bir sınıf oluşturun.

1. **Çözüm Gezgini'nde,** *YoloParser* dizinine sağ tıklayın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *YoloBoundingBox.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

    kod düzenleyicisinde *YoloBoundingBox.cs* dosyası açılır. YoloBoundingBox.cs üstüne `using` aşağıdaki ifadeyi *YoloBoundingBox.cs*ekleyin:

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    Varolan sınıf tanımının hemen üzerinde, `BoundingBoxDimensions` ilgili sınırlayıcı `DimensionsBase` kutunun boyutlarını içerecek şekilde sınıftan devralan yeni bir sınıf tanımı ekleyin.

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    Varolan `YoloBoundingBox` sınıf tanımını kaldırın ve `YoloBoundingBox` *YoloBoundingBox.cs* dosyasına sınıf için aşağıdaki kodu ekleyin:

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    `YoloBoundingBox`aşağıdaki özelliklere sahiptir:

    - `Dimensions`sınırlayıcı kutunun boyutlarını içerir.
    - `Label`sınırlama kutusu içinde algılanan nesnenin sınıfını içerir.
    - `Confidence`sınıfın güvenini içerir.
    - `Rect`sınırlayıcı kutunun boyutlarının dikdörtgen gösterimini içerir.
    - `BoxColor`görüntüüzerinde çizmek için kullanılan ilgili sınıfile ilişkili renk içerir.

### <a name="create-the-parser"></a>Ayrıştırıcıyı oluşturma

Şimdi boyutlar ve sınırlayıcı kutular için sınıflar oluşturulduğuna göre, ayrıştırıcıyı oluşturma nın zamanı geliyor.

1. **Çözüm Gezgini'nde,** *YoloParser* dizinine sağ tıklayın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *YoloOutputParser.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

    kod düzenleyicisinde *YoloOutputParser.cs* dosyası açılır. YoloOutputParser.cs üstüne `using` aşağıdaki ifadeyi *YoloOutputParser.cs*ekleyin:

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    Varolan `YoloOutputParser` sınıf tanımının içinde, görüntüdeki her hücrenin boyutlarını içeren iç içe geçmiş bir sınıf ekleyin. Sınıf tanımının `CellDimensions` en üstündeki `DimensionsBase` sınıftan devralan sınıf için aşağıdaki kodu ekleyin. `YoloOutputParser`

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. Sınıf `YoloOutputParser` tanımının içine aşağıdaki sabitleri ve alanları ekleyin.

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - `ROW_COUNT`görüntünün bölündüğü ızgaradaki satır sayısıdır.
    - `COL_COUNT`görüntünün bölündüğü ızgaradaki sütun sayısıdır.
    - `CHANNEL_COUNT`ızgaranın bir hücresinde bulunan değerlerin toplam sayısıdır.
    - `BOXES_PER_CELL`bir hücredeki sınırlayıcı kutuların sayısıdır,
    - `BOX_INFO_FEATURE_COUNT`kutunun içinde bulunan özellik sayısıdır (x,y,yükseklik,genişlik,güven).
    - `CLASS_COUNT`her sınırlayıcı kutuda bulunan sınıf tahminlerinin sayısıdır.
    - `CELL_WIDTH`görüntü ızgarasındaki bir hücrenin genişliğidir.
    - `CELL_HEIGHT`görüntü ızgarasındaki bir hücrenin yüksekliğidir.
    - `channelStride`ızgaradaki geçerli hücrenin başlangıç konumudur.

    Model puanlama olarak da bilinen bir tahmin yaptığında, `416px x 416px` giriş görüntüsünü `13 x 13`. Her hücre `32px x 32px`içerir . Her hücreiçinde, her biri 5 özellik (x, y, genişlik, yükseklik, güven) içeren 5 sınırlayıcı kutu vardır. Ayrıca, her sınırlayıcı kutu, bu durumda 20 olan sınıfların her birinin olasılığını içerir. Bu nedenle, her hücre 125 bilgi (5 özellik + 20 sınıf olasılıkları) içerir.

5 sınırlayıcı kutunun `channelStride` tümü için aşağıdaki çapaların listesini oluşturun:

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

Çapalar, sınırlayıcı kutuların önceden tanımlanmış yükseklik ve genişlik oranlarıdır. Bir model tarafından algılanan çoğu nesne veya sınıf benzer oranlara sahiptir. Bu sınırlayıcı kutuları oluşturma söz konusu olduğunda değerlidir. Sınırlayıcı kutuları tahmin etmek yerine, önceden tanımlanmış boyutlardan mahsup hesaplanır ve bu nedenle sınırlayıcı kutuyu tahmin etmek için gereken hesaplama azaltılır. Genellikle bu bağlantı oranları kullanılan veri kümesine göre hesaplanır. Bu durumda, veri kümesi bilindiğinden ve değerler önceden hesaplandığı için, çapalar sabit kodlanmış olabilir.

Ardından, modelin tahmin edeceği etiketleri veya sınıfları tanımlayın. Bu model, orijinal YOLOv2 modeli tarafından öngörülen toplam sınıf sayısının bir alt kümesi olan 20 sınıfı tahmin eder.

Etiket listenizi aşağıdaki `anchors`' nin altına ekleyin.

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

Sınıfların her biriyle ilişkili renkler vardır. Sınıf renklerinizi aşağıdaki `labels`lerinizin altına atamak:

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>Yardımcı işlevleri oluşturma

İşlem sonrası aşamada bir dizi adım vardır. Bu yardımcı olmak için, çeşitli yardımcı yöntemler kullanılabilir.

Ayrıştırıcı tarafından kullanılan yardımcı yöntemler şunlardır:

- `Sigmoid`0 ile 1 arasında bir sayı çıkan sigmoid işlevini uygular.
- `Softmax`bir olasılık dağılımına giriş vektörü normalleştirir.
- `GetOffset`tek boyutlu model çıktısındaki öğeleri bir `125 x 13 x 13` tentördeki ilgili konuma eşleştirir.
- `ExtractBoundingBoxes`model çıktısından `GetOffset` yöntemi kullanarak sınırlayıcı kutu boyutlarını ayıklar.
- `GetConfidence`modelin bir nesneyi algıladığını ve `Sigmoid` işlevi bir yüzdeye dönüştürmek için kullandığından ne kadar emin olduğunu belirten güven değerini ayıklar.
- `MapBoundingBoxToCell`sınırlayıcı kutu boyutlarını kullanır ve görüntü içindeki kendi hücresine eşler.
- `ExtractClasses`yöntemi kullanarak model çıktısı sınırlayıcı kutu için sınıf `GetOffset` tahminlerini ayıklar ve yöntemi `Softmax` kullanarak bir olasılık dağılımına dönüştürür.
- `GetTopResult`sınıfı en yüksek olasılıkla tahmin edilen sınıflar listesinden seçer.
- `IntersectionOverUnion`daha düşük olasılıklar ile sınırlayıcı kutuları çakışan filtreler.

Listenizin altındaki tüm yardımcı yöntemleriiçin kodu `classColors`ekleyin.

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

Tüm yardımcı yöntemleri tanımladıktan sonra, bunları model çıktısını işlemek için kullanmanın zamanı gelmiştir.

Yöntemin `IntersectionOverUnion` altında, `ParseOutputs` model tarafından oluşturulan çıktıyı işlemek için yöntem oluşturun.

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

Sınırlayıcı kutularınızı depolamak ve değişkenleri yöntemin `ParseOutputs` içinde tanımlamak için bir liste oluşturun.

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

Her görüntü bir hücre `13 x 13` ızgarasına bölünür. Her hücrede beş sınırlayıcı kutu bulunur. Değişkenin `boxes` altında, hücrelerin her birinde tüm kutuları işlemek için kod ekleyin.

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

En içteki döngüiçinde, geçerli kutunun tek boyutlu model çıkışı içindeki başlangıç konumunu hesaplayın.

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

Hemen altında, geçerli `ExtractBoundingBoxDimensions` sınırlayıcı kutunun boyutlarını almak için yöntemi kullanın.

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

Ardından, geçerli `GetConfidence` sınırlayıcı kutuiçin güven almak için yöntemi kullanın.

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

Bundan sonra, `MapBoundingBoxToCell` geçerli sınırlayıcı kutusunu işlenen geçerli hücreyle eşlemek için yöntemi kullanın.

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

Daha fazla işlem yapmadan önce, güven değerinizin sağlanan eşikten daha büyük olup olmadığını kontrol edin. Değilse, bir sonraki sınırlayıcı kutusunu işleyin.

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

Aksi takdirde, çıktı işlemeye devam edin. Bir sonraki adım, yöntemi kullanarak geçerli sınırlayıcı kutu için öngörülen sınıfların olasılık dağılımını `ExtractClasses` elde etmektir.

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

Ardından, geçerli `GetTopResult` kutu için en yüksek olasılıkla sınıfın değerini ve dizini almak ve puanını hesaplamak için yöntemi kullanın.

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

Yalnızca `topScore` belirtilen eşiğin üzerinde olan sınırlayıcı kutuları bir kez daha tutmak için kullanın.

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

Son olarak, geçerli sınırlayıcı kutu eşiği aşarsa, yeni `BoundingBox` bir `boxes` nesne oluşturun ve listeye ekleyin.

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

Görüntüdeki tüm hücreler işlendikten sonra `boxes` listeyi döndürün. Yöntemdeki dış-en for-for-loop'un `ParseOutputs` altına aşağıdaki dönüş deyimini ekleyin.

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>Çakışan kutuları filtreleme

Şimdi tüm son derece emin sınırlayıcı kutuları model çıktısı ayıklanmış, ek filtreleme örtüşen görüntüleri kaldırmak için yapılması gerekir. Yöntemin `ParseOutputs` altında `FilterBoundingBoxes` çağrılan bir yöntem ekleyin:

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

Yöntemin `FilterBoundingBoxes` içinde, algılanan kutuların boyutuna eşit bir dizi oluşturarak ve tüm yuvaları etkin veya işlemehazır olarak işaretleyerek başlayın.

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

Ardından, sınırlayıcı kutularınızı içeren listeyi güvene göre azalan sırada sıralayın.

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

Bundan sonra, filtre uygulanmış sonuçları tutmak için bir liste oluşturun.

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

Her sınırlayıcı kutuyu, sınırlayıcı kutuların her birinin üzerine yineleyerek işlemeye başlayın.

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

Bu for-loop'un içinde, geçerli sınırlayıcı kutunun işlenip işlenemeyeceğini kontrol edin.

```csharp
if (isActiveBoxes[i])
{

}
```

Bu nedenle, sınırlayıcı kutuyu sonuçlar listesine ekleyin. Sonuçlar çıkarılacak kutuların belirtilen sınırını aşarsa, döngüden çık. if deyiminin içine aşağıdaki kodu ekleyin.

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

Aksi takdirde, bitişik sınırlayıcı kutulara bakın. Kutu limit denetiminin altına aşağıdaki kodu ekleyin.

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

İlk kutu gibi, bitişik kutu etkinse veya işlemeye `IntersectionOverUnion` hazırsa, ilk kutu nun ve ikinci kutunun belirtilen eşiği aşıp aşmadığını denetlemek için yöntemi kullanın. Aşağıdaki kodu en içteki for-loop'unuza ekleyin.

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

Bitişik sınırlayıcı kutuları kontrol eden iç-en for-loop dışında, işlenecek kalan sınırlayıcı kutuları olup olmadığını görün. Değilse, dış for-loop patlak.

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

Son olarak, `FilterBoundingBoxes` yöntemin ilk for-loop dışında, sonuçları döndürün:

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

Harika! Şimdi puanlama için model ile birlikte bu kodu kullanma zamanı.

## <a name="use-the-model-for-scoring"></a>Puanlama için modeli kullanma

İşlem sonrası olduğu gibi, puanlama adımlarında da birkaç adım vardır. Bu soruna yardımcı olmak için, projenize puanlama mantığı nı içeren bir sınıf ekleyin.

1. **Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *OnnxModelScorer.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

    OnnxModelScorer.cs *OnnxModelScorer.cs* dosyası kod düzenleyicisinde açılır. OnnxModelScorer.cs üstüne `using` aşağıdaki ifadeyi *OnnxModelScorer.cs*ekleyin:

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    Sınıf `OnnxModelScorer` tanımının içine aşağıdaki değişkenleri ekleyin.

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    Bunun hemen altında, daha önce `OnnxModelScorer` tanımlanmış değişkenleri başharfleyecek sınıf için bir oluşturucu oluşturun.

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    Oluşturucuyu oluşturduktan sonra, görüntü ve model ayarlarıyla ilgili değişkenler içeren birkaç yapı tanımlayın. Model için giriş `ImageNetSettings` olarak beklenen yükseklik ve genişliği içerecek şekilde çağrılan bir yapı oluşturun.

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    Bundan sonra, modelin giriş `TinyYoloModelSettings` ve çıkış katmanlarının adlarını içeren başka bir yapı oluşturun. Modelin giriş ve çıkış katmanlarının adını görselleştirmek için [Netron](https://github.com/lutzroeder/netron)gibi bir araç kullanabilirsiniz.

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    Ardından, puanlama için kullanılan ilk yöntem kümesini oluşturun. Sınıfınızın `LoadModel` `OnnxModelScorer` içinde yöntemi oluşturun.

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    Yöntemin `LoadModel` içinde, günlüğe kaydetme için aşağıdaki kodu ekleyin.

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    ML.NET boru hatları [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) yöntem çağrıldığında çalışması için veri şemasını bilmek gerekir. Bu durumda, eğitime benzer bir süreç kullanılacaktır. Ancak, gerçek bir eğitim gerçekleşmediği için, boş [`IDataView`](xref:Microsoft.ML.IDataView)bir . Boş bir [`IDataView`](xref:Microsoft.ML.IDataView) listeden ardışık hatlar için yeni bir oluştur.

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    Bunun altında, boru hattını tanımlayın. Boru hattı dört dönüşümden oluşacak.

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*)görüntüyü Bitmap olarak yükler.
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*)görüntüyü belirtilen boyuta yeniden ölçeklendir (bu durumda). `416 x 416`
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*)görüntünün piksel temsilini Bitmap'ten sayısal vektöre değiştirir.
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*)ONNX modelini yükler ve sağlanan veriler üzerinde puan elde etmek için kullanır.

    Değişkenin `LoadModel` altındaki yöntemde `data` ardışık hattınızı tanımlayın.

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    Şimdi puanlama için modeli anında atma zamanı. Ardışık [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) işlem yöntemini arayın ve daha fazla işleme için iade edin.

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

Model yüklendikten sonra, öngörülerde bulunmak için kullanılabilir. Bu işlemi kolaylaştırmak için, `PredictDataUsingModel` yöntemin `LoadModel` altında adı verilen bir yöntem oluşturun.

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

`PredictDataUsingModel`İçinde, günlüğe kaydetme için aşağıdaki kodu ekleyin.

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

Ardından, verileri [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) puanlamak için yöntemi kullanın.

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

Öngörülen olasılıkları ayıklayın ve ek işleme için iade edin.

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

Artık her iki adım da ayarlıştın, bunları tek bir yöntemde birleştirin. Yöntemin `PredictDataUsingModel` altına yeni bir `Score`yöntem ekleyin.

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

Neredeyse orada! Şimdi hepsini kullanma zamanı.

## <a name="detect-objects"></a>Nesneleri algılama

Artık tüm kurulum tamamlandığından, bazı nesneleri algılama nın zamanı geldiğinden. *Program.cs* sınıfınızdaki skorer ve ayrıştırıcıya referanslar ekleyerek başlayın.

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a>Puan ve ayrıştırma modeli çıktıları

Program.cs `Main` sınıfının *Program.cs* yönteminin içinde bir try-catch deyimi ekleyin.

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

`try` Bloğun içinde nesne algılama mantığını uygulamaya başlayın. İlk olarak, verileri [`IDataView`](xref:Microsoft.ML.IDataView)bir .

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

Ardından, bir örnek `OnnxModelScorer` oluşturun ve yüklenen verileri puanlamak için kullanın.

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

Şimdi işlem sonrası adım zamanı. Bir örnek `YoloOutputParser` oluşturun ve model çıktısını işlemek için kullanın.

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

Model çıktısı işlendikten sonra, görüntülere sınırlayıcı kutuları çizme zamanı gelmiştir.

### <a name="visualize-predictions"></a>Tahminleri görselleştir

Model görüntüleri attıktan ve çıktılar işlendikten sonra, sınırlayıcı kutuların görüntüüzerine çizilmesi gerekir. Bunu yapmak için, `DrawBoundingBox` *Program.cs*içinde `GetAbsolutePath` yöntemin altında çağrılan bir yöntem ekleyin.

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

İlk olarak, görüntüyü yükleyin ve `DrawBoundingBox` yöntemde yükseklik ve genişlik boyutlarını alın.

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

Ardından, model tarafından algılanan sınırlayıcı kutuların her biri üzerinde yinelemek için her biri için bir döngü oluşturun.

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

For-each döngü içinde, sınırlayıcı kutunun boyutlarını almak.

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

Sınırlayıcı kutunun boyutları model girişine karşılık geldiği `416 x 416`için, sınırlayıcı kutu boyutlarını görüntünün gerçek boyutuyla eşleşecek şekilde ölçeklendirin.

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

Ardından, her sınırlayıcı kutunun üzerinde görünecek metin için bir şablon tanımlayın. Metin, ilgili sınırlayıcı kutunun içindeki nesnenin sınıfını ve güveni içerir.

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

Görüntüüzerinde çizmek için, bir [`Graphics`](xref:System.Drawing.Graphics) nesneye dönüştürün.

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

Kod `using` bloğunun içinde, grafiğin [`Graphics`](xref:System.Drawing.Graphics) nesne ayarlarını ayarlayın.

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

Bunun altında, metin ve sınırlayıcı kutu için yazı tipi ve renk seçeneklerini ayarlayın.

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

[`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) Yöntemi kullanarak metni içerecek şekilde sınırlayıcı kutunun üzerinde bir dikdörtgen oluşturun ve doldurun. Bu, metnin karşıtlığını ve okunabilirliğini artırmaya yardımcı olur.

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

Ardından, görüntüve yöntemleri kullanarak görüntüüzerindeki metni [`DrawString`](xref:System.Drawing.Graphics.DrawString*) [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) ve sınırlayıcı kutuyu çizin.

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

For-each döngü dışında, görüntüleri kaydetmek için kod `outputDirectory`ekleyin.

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

Uygulamanın çalışma zamanında beklendiği gibi öngörüler yaptığını ek geribildirim `LogDetectedObjects` için, algılanan nesneleri konsola çıktıetmek için `DrawBoundingBox` *Program.cs* dosyasındaki yöntemin altında nağmeler bulunan bir yöntem ekleyin.

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

Artık öngörülerden görsel geri bildirim oluşturmak için yardımcı yöntemlere sahip olduğunuza göre, puanlı görüntülerin her biri üzerinde yinelemek için bir for-loop ekleyin.

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

For-loop'un içinde, görüntü dosyasının adını ve onunla ilişkili sınırlayıcı kutuları alın.

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

Bunun altında, `DrawBoundingBox` görüntü üzerinde sınırlayıcı kutuları çizmek için yöntemi kullanın.

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

Son olarak, `LogDetectedObjects` konsola öngörüler çıktıyöntemini kullanın.

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

Try-catch deyiminden sonra, işlemin çalıştığını belirtmek için ek mantık ekleyin.

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

İşte bu kadar!

## <a name="results"></a>Sonuçlar

Önceki adımları takip ettikten sonra konsol uygulamanızı (Ctrl + F5) çalıştırın. Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır. Uyarılar veya iletileri işleme görebilirsiniz, ancak bu iletiler netlik için aşağıdaki sonuçlardan kaldırılmıştır.

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

Sınırları kutulu görüntüleri görmek için dizine `assets/images/output/` gidin. Aşağıda işlenmiş görüntülerden birinden bir örnek.

![Yemek odasının örnek işlenmiş görüntüsü](./media/object-detection-onnx/dinning-room-table-chairs.png)

Tebrikler! Şimdi, ML.NET önceden eğitilmiş bir modeli yeniden kullanarak nesne algılama `ONNX` için bir makine öğrenme modeli başarıyla oluşturmuşsunuz.

Bu öğreticinin kaynak kodunu [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - ONNX'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin
> - Modeli anlama
> - Önceden eğitilmiş modeli yeniden kullanma
> - Yüklü bir modelle nesneleri algılama

Genişletilmiş bir nesne algılama örneğini keşfetmek için Machine Learning örnekleri GitHub deposuna göz atın.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-örnekleri GitHub deposu](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
