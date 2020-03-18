---
title: 'Öğretici: TensorFlow ML.NET görüntü sınıflandırma modeli'
description: Bilgiyi varolan tensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline nasıl aktartırmayı öğrenin. TensorFlow modeli, görüntüleri bin kategoriye sınıflandırmak için eğitildi. ML.NET modeli, görüntüleri daha az geniş kategoriye sınıflandırmak için aktarım öğrenmeyi kullanır.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 1e5478f53c82f36ddafe19e3659e2234ff9687b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241032"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Öğretici: Önceden eğitilmiş tensorFlow modelinden ML.NET görüntü sınıflandırma modeli oluşturun

Bilgiyi varolan tensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline nasıl aktartırmayı öğrenin.

TensorFlow modeli, görüntüleri bin kategoriye sınıflandırmak için eğitildi. ML.NET modeli, görüntüleri 3 kategoriye ayırmak için bir model eğitmek için ardışık bölümünde TensorFlow modelinin bir kısmını kullanır.

Bir [Görüntü Sınıflandırma](https://en.wikipedia.org/wiki/Outline_of_object_recognition) modelini sıfırdan eğitmek için milyonlarca parametre, bir ton etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) gerekir. Sıfırdan özel bir modeli eğitmek kadar etkili olmasa da, transfer öğrenimi binlerce görüntüyle ve milyonlarca etiketli görüntüyle çalışarak bu süreci kısayolla kesmenize ve oldukça hızlı bir şekilde özelleştirilmiş bir model oluşturmanıza olanak sağlar (bir makinede bir saat içinde GPU). Bu öğretici, yalnızca bir düzine eğitim görseli kullanarak daha da aşağı doğru işleyen ölçekler.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> * Sorunu anlama
> * Önceden eğitilmiş TensorFlow modelini ML.NET boru hattına dahil edin
> * ML.NET modelini eğitin ve değerlendirin
> * Test görüntüsünü sınıflandırma

Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz. Varsayılan olarak, bu öğretici hedefler için .NET proje yapılandırması .NET çekirdek 2.2 unutmayın.

## <a name="what-is-transfer-learning"></a>Transfer öğrenme nedir?

Transfer öğrenme, bir problemi çözerken edinilen bilgiyi kullanarak ve farklı ama ilgili bir soruna uygulama sürecidir.

Bu öğretici için, görüntüleri 3 kategoriye ayıran ML.NET bir modelde, görüntüleri bin kategoriye ayırmak üzere eğitilmiş tensorflow modelinin bir bölümünü kullanırsınız.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.
* [Öğretici varlıklar dizini . ZIP dosyası](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [InceptionV1 makine öğrenme modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Doğru makine öğrenimi görevini seçin

### <a name="deep-learning"></a>Derin öğrenme

[Derin öğrenme,](https://en.wikipedia.org/wiki/Deep_learning) Bilgisayarlı Görme ve Konuşma Tanıma gibi alanlarda devrim yapan Makine Öğrenimi'nin bir alt kümesidir.

Derin öğrenme modelleri, birden çok öğrenme katmanı içeren büyük [etiketli veri](https://en.wikipedia.org/wiki/Labeled_data) kümeleri ve [sinir ağları](https://en.wikipedia.org/wiki/Artificial_neural_network) kullanılarak eğitilir. Derin öğrenme:

* Computer Vision gibi bazı görevlerde daha iyi performans gösterir.
* Büyük miktarda eğitim verisi gerektirir.

Resim Sınıflandırması, görüntüleri otomatik olarak şu kategorilere ayırmamıza olanak tanıyan yaygın bir Makine Öğrenimi görevidir:

* Görüntüde bir insan yüzünü algılamak ya da algılamamak.
* Kedileri köpeklere karşı tespit etmek.

 Veya aşağıdaki resimlerde olduğu gibi, bir görüntünün a(n) gıda, oyuncak veya cihaz olup olmadığını belirlemek:

![pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![görüntü oyuncak](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![ayı görüntü tost makinesi görüntü](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Önceki görüntüler Wikimedia Commons'a aittir ve aşağıdaki gibi atfedilmiştir:
>
> * "220px-Pepperoni_pizza.jpg" Kamu https://commons.wikimedia.org/w/index.php?curid=79505Malı,
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) by - Kendini fotoğrafladı, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.
> * "193px-Broodrooster.jpg" [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) by - Kendi iş, CC BY-SA 3.0,https://commons.wikimedia.org/w/index.php?curid=27403

Görüntüleri `Inception model` bin kategoriye sınıflandırmak üzere eğitildi, ancak bu öğretici için görüntüleri daha küçük bir kategori kümesinde ve yalnızca bu kategorilerde sınıflandırmanız gerekir. `transfer` bölümünü `transfer learning`girin. `Inception model`'S yeteneğini tanımak ve özel görüntü sınıflandırıcı yeni sınırlı kategorilere görüntüleri sınıflandırmak aktarabilirsiniz.

* Gıda
* Oyuncak
* Cihaz

Bu öğretici tensorFlow [inception modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) derin öğrenme modeli, `ImageNet` veri seti üzerinde eğitilmiş popüler bir görüntü tanıma modeli kullanır. TensorFlow modeli tüm görüntüleri "Umbrella", "Jersey" ve "Bulaşık Makinesi" gibi bin sınıfa sınıflar.

Zaten `Inception model` farklı görüntüler binlerce önceden eğitilmiş olduğundan, içten görüntü tanımlama için gerekli [görüntü özelliklerini](https://en.wikipedia.org/wiki/Feature_(computer_vision)) içerir. Biz çok daha az sınıfları ile yeni bir model eğitmek için modelde bu iç görüntü özellikleri yararlanabilir.

Aşağıdaki diyagramda gösterildiği gibi, .NET Core veya .NET Framework uygulamalarınızdaki ML.NET NuGet paketlerine bir başvuru eklersiniz. Kapakların altında, ML.NET, varolan bir eğitilmiş `TensorFlow` `TensorFlow` model dosyasını yükleyen kod yazmanıza olanak tanıyan yerel kitaplığı içerir ve başvurur.

![TensorFlow transform ML.NET Arch diyagramı](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Çok sınıflı sınıflandırma

Klasik bir makine öğrenme algoritması için girdi olarak uygun özellikleri ayıklamak için TensorFlow başlangıç modelini kullandıktan sonra, ML.NET [çok sınıflı bir sınıflandırıcı](../resources/tasks.md#multiclass-classification)ekliyoruz.

Bu durumda kullanılan özel eğitmen [multinomial lojistik regresyon algoritmasıdır.](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)

Bu eğitmen tarafından uygulanan algoritma, görüntü verileri üzerinde çalışan derin bir öğrenme modeli için geçerli olan çok sayıda özellik ile ilgili sorunlar üzerinde iyi performans gösterir.

### <a name="data"></a>Veriler

İki veri kaynağı vardır: `.tsv` dosya ve görüntü dosyaları.  Dosya `tags.tsv` iki sütun içerir: birincisi olarak `ImagePath` tanımlanır ve ikincisi `Label` görüntüye karşılık gelen. Aşağıdaki örnek dosyanın üstbilgi satırı yoktur ve aşağıdaki gibi görünür:

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

Eğitim ve test görüntüleri, zip dosyasına indireceğiniz varlık klasörlerinde bulunur. Bu görüntüler Wikimedia Commons'a aittir.
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), ücretsiz medya deposu.* Erişim tarihi: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster 10:48 Ekim 17, 2018:https://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>Kurulum

### <a name="create-a-project"></a>Proje oluşturma

1. "TransferLearningTF" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.

1. Microsoft.ML **NuGet Paketini**Yükleyin:

    * Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.
    * Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML**arayın.
    * **Sürüm** açılır listesine tıklayın, listedeki **1.4.0** paketini seçin ve **Yükle** düğmesini seçin.
    * **Değişiklikleri Önizleme** iletişim **kutusundatamam** düğmesini seçin.
    * Listelenen paketlerin lisans koşullarını kabul **ederseniz, Lisans Kabul** iletişim kutusundaki **I Kabul** düğmesini seçin.
    * **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** ve **Microsoft.ML.TensorFlow v1.4.0**için bu adımları tekrarlayın.

### <a name="download-assets"></a>Varlıkları indirin

1. [Proje varlıkları dizin zip dosyasını](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)indirin ve zip'i açın.

1. Dizini `assets` *TransferLearningTF* proje dizininize kopyalayın. Bu dizin ve alt dizinleri, bu öğretici için gereken verileri ve destek dosyalarını (bir sonraki adımda indirip ekleyeceğiniz Başlangıç modeli hariç) içerir.

1. [Inception modelini](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)indirin ve zip'i indirin.

1. Dizinin `inception5h` *içeriğini, TransferLearningTF* proje `assets/inception` dizininize yenik çıkarArak kopyalayın. Bu dizin, aşağıdaki resimde gösterildiği gibi, bu öğretici için gerekli modeli ve ek destek dosyalarını içerir:

   ![Başlangıç dizini içeriği](./media/image-classification/inception-files.png)

1. Çözüm Gezgini'nde, varlık dizini ve alt dizinindeki dosyaların her birini sağ tıklatın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıflar oluşturma ve yolları tanımlama

1. Aşağıdaki ek `using` deyimleri *Program.cs* dosyasının üstüne ekleyin:

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. Varlık yollarını belirtmek için yöntemin `Main` hemen üstündeki satıra aşağıdaki kodu ekleyin:

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. Giriş verileriniz ve öngörüleriniz için sınıflar oluşturun.

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    `ImageData`giriş görüntü veri sınıfıdır ve <xref:System.String> aşağıdaki alanlara sahiptir:

    * `ImagePath`resim dosya adını içerir.
    * `Label`görüntü etiketi için bir değer içerir.

1. Projenize yeni bir sınıf `ImagePrediction`ekleyin:

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    `ImagePrediction`görüntü tahmin sınıfıdır ve aşağıdaki alanlara sahiptir:

    * `Score`belirli bir görüntü sınıflandırması için güven yüzdesini içerir.
    * `PredictedLabelValue`öngörülen görüntü sınıflandırma etiketi için bir değer içerir.

    `ImagePrediction`model eğitildikten sonra tahmin için kullanılan sınıftır. Görüntü yolu `string` `ImagePath`için bir ( ) vardır. Modelyeniden `Label` kullanmak ve eğitmek için kullanılır. Tahmin `PredictedLabelValue` ve değerlendirme sırasında kullanılır. Değerlendirme için, eğitim verileri, öngörülen değerler ve model ile bir giriş kullanılır.

### <a name="initialize-variables-in-main"></a>Main'deki değişkenleri başlatma

1. Değişkeni `mlContext` yeni bir örnekle `MLContext`başlatma.  `Console.WriteLine("Hello World!")` Satırı yöntemde aşağıdaki kodla `Main` değiştirin:

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    [MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç `mlContext` noktasıdır ve başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur. Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.

### <a name="create-a-struct-for-inception-model-parameters"></a>Başlangıç modeli parametreleri için bir yapı oluşturma

1. Inception modeli, geçmeniz gereken birkaç parametreye sahiptir. `Main()` Yöntemden hemen sonra, parametre değerlerini aşağıdaki kodla dost adlarla eşlemek için bir yapı oluşturun:

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Görüntü yardımcı programı yöntemi oluşturma

Görüntü verilerini ve ilgili tahminleri birden çok kez görüntüleyeceğiniz için, görüntü ve tahmin sonuçlarını görüntülemek için bir görüntü yardımcı programı yöntemi oluşturun.

1. Aşağıdaki `DisplayResults()` kodu kullanarak, `InceptionSettings` yapıdan hemen sonra yöntemi oluşturun:

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Yöntemin gövdesini `DisplayResults` doldurun:

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>.tsv dosya yardımcı programı yöntemi oluşturma

1. Yöntemden `ReadFromTsv()` `DisplayResults()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Yöntemin gövdesini `ReadFromTsv` doldurun:

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    `tags.tsv` Kod, `ImagePath` dosya yolunu özelliğin görüntü dosyası adına eklemek ve dosyayı ve `Label` nesneye `ImageData` yüklemek için dosyayı parslar.

### <a name="create-a-method-to-make-a-prediction"></a>Tahminde bulunmak için bir yöntem oluşturma

1. Yöntemden `ClassifySingleImage()` hemen önce, `DisplayResults()` aşağıdaki kodu kullanarak yöntemi oluşturun:

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Tek `ImagePath` `ImageData` için tam nitelikli yol ve görüntü dosya adı içeren bir nesne oluşturun. `ClassifySingleImage()` Yöntemde sonraki satırlar olarak aşağıdaki kodu ekleyin:

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. Yöntemde bir sonraki satır olarak aşağıdaki kodu ekleyerek `ClassifySingleImage` tek bir tahminde bulunun:

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    Tahminalmak için [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) yöntemini kullanın. [PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir. Tek dişli veya prototip ortamlarda kullanılabilir. Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın. ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.

    > [!NOTE]
    > `PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.

1. Tahmin sonucunu yöntemde bir sonraki kod `ClassifySingleImage()` satırı olarak görüntüleyin:

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>ML.NET modeli boru hattı oluşturma

ML.NET model boru hattı tahminciler zinciridir. Boru hattı inşaatı sırasında yürütme yapılamaz. Tahminci nesneleri oluşturulur, ancak yürütülmez.

1. Modeli oluşturmak için bir yöntem ekleme

    Bu yöntem öğretici kalbidir. Bu model için bir boru hattı oluşturur ve ML.NET modeli üretmek için boru hattı trenler. Ayrıca modeli daha önce görülmemiş bazı test verilerine göre de değerlendirir.

    Aşağıdaki `GenerateModel()` kodu kullanarak, `InceptionSettings` yapıdan hemen sonra `DisplayResults()` ve yöntemden hemen önce yöntemi oluşturun:

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Görüntü verilerinden pikselleri yüklemek, yeniden boyutlandırmak ve ayıklamak için tahmincileri ekleyin:

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    Görüntü verilerinin TensorFlow modelinin beklediği biçimde işlenmesi gerekir. Bu durumda, görüntüler belleğe yüklenir, tutarlı bir boyuta küçültüldü ve pikseller sayısal bir vektöre ayıklanır.

1. TensorFlow modelini yüklemek için tahminciyi ekleyin ve puanlayın:

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    Ardışık işlem de bu aşamada tensorFlow modeli belleğe yükler, sonra TensorFlow model ağı üzerinden piksel değerlerinin vektörü işler. Girişleri derin bir öğrenme modeline uygulamak ve modeli kullanarak çıktı üretmek **Puanlama**olarak adlandırılır. Modeli bütünüyle kullanırken, puanlama bir çıkarım veya tahmin yapar.

    Bu durumda, çıkarımı oluşturan katman olan son katman dışında TensorFlow modelinin tümlerini kullanırsınız. Sondan bir önceki katmanın `softmax_2_preactivation`çıktısı etiketlenir. Bu katmanın çıktısı, orijinal giriş görüntülerini karakterize eden bir özellik vektörüdür.

    TensorFlow modeli tarafından oluşturulan bu özellik vektörü, ML.NET bir eğitim algoritmasına giriş olarak kullanılacaktır.

1. Eğitim verilerindeki dize etiketlerini eşlemek için tahminciyi, toplam anahtar değerlerine ekleyin:

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    Sonraki eklenen ML.NET eğitmen, etiketlerinin rasgele `key` dizeleri yerine biçimde olmasını gerektirir. Anahtar, dize değerine bire bir eşleme olan bir sayıdır.

1. ML.NET eğitim algoritmasını ekleyin:

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. Tahminciyi, öngörülen anahtar değerini bir dize yle eşlemek için ekleyin:

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Modeli eğitme

1. [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) sarıcıyı kullanarak eğitim verilerini yükleyin. `GenerateModel()` Yöntemde sonraki satır olarak aşağıdaki kodu ekleyin:

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    ML.NET'daki veriler [IDataView sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`tabular verileri (sayısal ve metin) tanımlamanın esnek ve etkili bir yoludur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı `IDataView` veya günlük dosyaları) bir nesneye yüklenebilir.

1. Yukarıdaki yüklenen verilerle modeli eğitin:

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    Yöntem, `Fit()` eğitim veri kümesini boru hattına uygulayarak modelinizi eğitiyor.

## <a name="evaluate-the-accuracy-of-the-model"></a>Modelin doğruluğunu değerlendirme

1. Yöntemin bir sonraki satırına aşağıdaki kodu ekleyerek test `GenerateModel` verilerini yükleyin ve dönüştürün:

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Modeli değerlendirmek için kullanabileceğiniz birkaç örnek resim vardır. Eğitim verileri gibi, bunların da model `IDataView`tarafından dönüştürülebilmeleri için bir , içine yüklenmesi gerekir.

1. Modeli değerlendirmek için `GenerateModel()` yönteme aşağıdaki kodu ekleyin:

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    Tahmin kümesini aldıktan sonra, [Değerlendir()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi:

    * Modeli değerlendirir (öngörülen değerleri test veri kümesiyle `labels`karşılaştırır).
    * Model performans ölçümlerini döndürür.

1. Model doğruluk ölçümlerini görüntüleme

    Ölçümleri görüntülemek, sonuçları paylaşmak ve sonra bunlara göre hareket etmek için aşağıdaki kodu kullanın:

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    Aşağıdaki ölçümler görüntü sınıflandırması için değerlendirilir:

    * `Log-loss`- [bkz.](../resources/glossary.md#log-loss) Log-loss'un mümkün olduğunca sıfıra yakın olmasını istiyorsunuz.
    * `Per class Log-loss`. Sınıf başına Günlük kaybının mümkün olduğunca sıfıra yakın olmasını istiyorsunuz.

1. Eğitilen modeli sonraki satır olarak döndürmek için aşağıdaki kodu ekleyin:

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Uygulamayı çalıştırın!

1. MLContext sınıfının `GenerateModel` `Main` oluşturulmasından sonra yönteme çağrı ekleyin:

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. Yöntemde `ClassifySingleImage()` bir sonraki kod satırı olarak yönteme çağrıyı `Main` ekleyin:

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. Konsol uygulamanızı çalıştırın (Ctrl + F5). Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.  Uyarılar veya iletileri işleme görebilirsiniz, ancak bu iletiler netlik için aşağıdaki sonuçlardan kaldırılmıştır.

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

Tebrikler! Şimdi başarılı bir şekilde ML.NET bir modele transfer öğrenme uygulayarak `TensorFlow` görüntü sınıflandırma için bir makine öğrenme modeli inşa ettik.

Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Sorunu anlama
> * Önceden eğitilmiş TensorFlow modelini ML.NET boru hattına dahil edin
> * ML.NET modelini eğitin ve değerlendirin
> * Test görüntüsünü sınıflandırma

Genişletilmiş bir görüntü sınıflandırma örneğini keşfetmek için GitHub deposundaki Machine Learning örneklerine göz atın.
> [!div class="nextstepaction"]
> [dotnet/machinelearning-örnekleri GitHub deposu](https://github.com/dotnet/machinelearning-samples/)
