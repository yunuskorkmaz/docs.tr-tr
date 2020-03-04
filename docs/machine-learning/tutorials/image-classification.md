---
title: "Öğretici: TensorFlow 'dan ML.NET görüntü sınıflandırma modeli"
description: Mevcut bir TensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline bilgi aktarmayı öğrenin. TensorFlow modeli görüntüleri bin kategoride sınıflandırmakta eğitildi. ML.NET modeli görüntüleri daha az daha geniş kategoriler halinde sınıflandırmak için aktarım öğrenimini kullanır.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 1e5478f53c82f36ddafe19e3659e2234ff9687b4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241032"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Öğretici: önceden eğitilen bir TensorFlow modelinden ML.NET görüntü sınıflandırma modeli oluşturma

Mevcut bir TensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline bilgi aktarmayı öğrenin.

TensorFlow modeli görüntüleri bin kategoride sınıflandırmakta eğitildi. ML.NET modeli, görüntüleri 3 kategoride sınıflandırmak üzere bir modeli eğitemak için, ardışık düzeninde TensorFlow modelinin bir parçasını kullanır.

[Görüntü sınıflandırma](https://en.wikipedia.org/wiki/Outline_of_object_recognition) modelini sıfırdan eğitmek için milyonlarca parametre, bir dizi etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir. Özel bir modeli sıfırdan eğitmek kadar uygun olmasa da, aktarım öğrenimi, binlerce görüntüde ve çok hızlı bir şekilde özelleştirilmiş bir model (bir saat içinde, GPU). Bu öğreticide, yalnızca bir düzine eğitim görüntüsü kullanılarak bu işlem daha da ayrıntılı şekilde ölçeklendirilir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Sorunu anlama
> * Önceden eğitilen TensorFlow modelini ML.NET işlem hattına ekleyin
> * ML.NET modelini eğitme ve değerlendirme
> * Test görüntüsünü sınıflandır

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz. Varsayılan olarak, Bu öğreticinin .NET proje yapılandırmasında .NET Core 2,2 ' i hedeflediğini unutmayın.

## <a name="what-is-transfer-learning"></a>Aktarım öğrenimi nedir?

Aktarım öğrenimi, bir sorunu çözerken ve ilgili başka bir soruna uygulanarak bilgi elde edilen bilgileri kullanma işlemidir.

Bu öğretici için, görüntüleri 3 kategoriye göre sınıflandıran bir ML.NET modelinde resimleri bin kategoride sınıflandırmakta olan bir TensorFlow modelinin bir bölümünü kullanırsınız.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.
* [Öğretici varlıkları dizini. ZIP dosyası](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [InceptionV1 Machine Learning modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Doğru makine öğrenimi görevini seçin

### <a name="deep-learning"></a>Derin öğrenme

[Derin öğrenme](https://en.wikipedia.org/wiki/Deep_learning) , görüntü işleme ve konuşma tanıma gibi revolutionizing alan Machine Learning bir alt kümesidir.

Derin öğrenme modelleri, birden fazla öğrenme katmanı içeren büyük ölçekli [veri](https://en.wikipedia.org/wiki/Labeled_data) ve [sinir Networks](https://en.wikipedia.org/wiki/Artificial_neural_network) kümeleri kullanılarak eğitilir. Derin öğrenme:

* Görüntü İşleme gibi bazı görevlerde daha iyi çalışır.
* Çok büyük miktarlarda eğitim verisi gerektirir.

Görüntü sınıflandırması, görüntüleri otomatik olarak kategoriler halinde sınıflandırmamızı sağlayan ortak bir Machine Learning görevdir:

* Görüntüde insan yüzü algılanıyor.
* Kediler ve köpekler algılanıyor.

 Aşağıdaki görüntülerde olduğu gibi, bir resmin (n) yiyecek, oyunı veya gereç olduğunu belirleme:

![pizza Image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![oyuncak ayı görüntü](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![Toaster Image](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Önceki görüntüler Wikimedia Commons ' a aittir ve aşağıdaki gibi verilmiştir:
>
> * "220px-Pepperoni_pizza. jpg" genel etki alanı, https://commons.wikimedia.org/w/index.php?curid=79505,
> * [Jonık](https://commons.wikimedia.org/wiki/User:Jonik) -Self-Photo, CC BY-SA 2,0, https://commons.wikimedia.org/w/index.php?curid=48166tarafından "119px-Nalle_-_a_small_brown_teddy_bear. jpg".
> * "193px-Broodrooster. jpg"- [k. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) -kendi ÇALıŞMASı, CC BY-SA 3,0, https://commons.wikimedia.org/w/index.php?curid=27403

`Inception model` görüntüleri bin kategoride sınıflandırıp, ancak bu öğreticide, görüntüleri daha küçük bir kategori kümesinde ve yalnızca bu kategorilerden sınıflandırmanız gerekir. `transfer learning``transfer` bölümünü girin. `Inception model`, resimleri tanıma ve sınıflandırıp özel görüntü sınıflandırıcınızın yeni sınırlı kategorilerine aktarabilirsiniz.

* Yiyecek
* Cağı
* Elektrikli

Bu öğretici, `ImageNet` veri kümesi üzerinde eğitilen popüler bir görüntü tanıma modeli olan TensorFlow [Inception modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) derin öğrenme modelini kullanır. TensorFlow modeli, tüm görüntüleri "şemsiye", "Jersey" ve "Dishronı" gibi binlik bir sınıfa göre sınıflandırır.

`Inception model`, binlerce farklı görüntüde önceden eğitildiğinden, dahili olarak görüntü tanımlama için gereken [görüntü özelliklerini](https://en.wikipedia.org/wiki/Feature_(computer_vision)) içerir. En az sınıfa sahip yeni bir modeli eğitebilmeniz için modelde bu iç görüntü özelliklerinden yararlanabilirsiniz.

Aşağıdaki diyagramda gösterildiği gibi, .NET Core veya .NET Framework uygulamalarında ML.NET NuGet paketlerine bir başvuru eklersiniz. ML.NET dahil olmak üzere, var olan eğitilen bir `TensorFlow` modeli dosyasını yükleyen kodu yazmanıza izin veren yerel `TensorFlow` kitaplığına başvurur.

![TensorFlow Transform ML.NET yay diyagramı](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Birden çok Lass sınıflandırması

Klasik makine öğrenimi algoritması için giriş olarak uygun özellikleri ayıklamak üzere TensorFlow kullanım modelini kullandıktan sonra, ML.NET [çok sınıflı bir sınıflandırıcı](../resources/tasks.md#multiclass-classification)ekleyeceğiz.

Bu durumda kullanılan belirli bir eğitmen, [ÇOKTERİMLİ lojistik regresyon algoritmasıdır](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

Bu eğitimci tarafından uygulanan algoritma, görüntü verilerinde çalışan derin bir öğrenme modelinin durumu olan çok sayıda özellik ile ilgili sorunları iyi gerçekleştirir.

### <a name="data"></a>Veri

İki veri kaynağı vardır: `.tsv` dosyası ve görüntü dosyaları.  `tags.tsv` dosyası iki sütun içerir: Birincisi, `ImagePath` olarak tanımlanır ve ikinci tane görüntüye karşılık gelen `Label`. Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:

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

Eğitim ve test görüntüleri, bir ZIP dosyasında indirileceği varlıklar klasörlerinde bulunur. Bu görüntüler Wikimedia Commons ' a aittir.
> *[Wkımedıa Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), ücretsiz medya deposu.* 10:48 Ekim, 2018: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear alındı

## <a name="setup"></a>Kurulum

### <a name="create-a-project"></a>Proje oluşturma

1. "TransferLearningTF" adlı bir **.NET Core konsol uygulaması** oluşturun.

1. **Microsoft.ml NuGet paketini**yükler:

    * Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.
    * Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml**için arama yapın.
    * **Sürüm** açılır listesine tıklayın, listeden **1.4.0** paketini seçin ve ardından **Kaldır düğmesini seçin** .
    * **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin.
    * Listelenen paketlerin lisans koşullarını kabul ediyorsanız, **Lisans kabulü** Iletişim kutusunda **kabul ediyorum** düğmesini seçin.
    * **Microsoft. ml. ımageanalytics v 1.4.0**, **SciSharp. TensorFlow. Redist v 1.15.0** ve **Microsoft. ml. TensorFlow v 1.4.0**için bu adımları yineleyin.

### <a name="download-assets"></a>Varlıkları indir

1. [Proje Varlıkları Dizin ZIP dosyasını](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)indirin ve sıkıştırmayı açın.

1. `assets` dizinini *Transferlearningtf* proje dizininize kopyalayın. Bu dizin ve alt dizinleri, bu öğretici için gerekli olan veri ve destek dosyalarını (bir sonraki adımda indirecek ve ekleyeceğiniz bir model hariç) içerir.

1. [Inception modelini](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)indirin ve sıkıştırmayı açın.

1. `inception5h` dizininin içeriğini, *Transferlearningtf* Project `assets/inception` dizininize kopyalamanız yeterlidir. Bu dizin, aşağıdaki görüntüde gösterildiği gibi, bu öğretici için gereken modeli ve ek destek dosyalarını içerir:

   ![Dizin içeriğini geçersiz kılma](./media/image-classification/inception-files.png)

1. Çözüm Gezgini, varlık dizinindeki ve alt dizinlerde bulunan dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

1. Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. Varlık yollarını belirtmek için, `Main` yönteminin hemen üstüne aşağıdaki kodu ekleyin:

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. Giriş verileriniz ve tahminler için sınıflar oluşturun.

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    `ImageData`, giriş resmi veri sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:

    * `ImagePath` resim dosyası adını içerir.
    * `Label` resim etiketi için bir değer içerir.

1. `ImagePrediction`için projenize yeni bir sınıf ekleyin:

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    `ImagePrediction`, görüntü tahmin sınıfıdır ve aşağıdaki alanlara sahiptir:

    * `Score`, belirli bir görüntü sınıflandırması için güvenirlik yüzdesini içerir.
    * `PredictedLabelValue`, tahmin edilen görüntü sınıflandırma etiketi için bir değer içerir.

    `ImagePrediction`, model eğitilen bir tahmin için kullanılan sınıftır. Görüntü yolu için bir `string` (`ImagePath`) vardır. `Label` modeli yeniden kullanmak ve geliştirmek için kullanılır. `PredictedLabelValue`, tahmin ve değerlendirme sırasında kullanılır. Değerlendirme için eğitim verileri olan bir giriş, tahmin edilen değerler ve model kullanılır.

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

1. `mlContext` değişkenini yeni bir `MLContext`örneğiyle başlatın.  `Console.WriteLine("Hello World!")` satırını `Main` yönteminde aşağıdaki kodla değiştirin:

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    [Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve `mlContext` başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Benzer, kavramsal olarak, Entity Framework `DBContext`.

### <a name="create-a-struct-for-inception-model-parameters"></a>Inception model parametreleri için bir struct oluşturun

1. Inception modelinde, geçirmeniz gereken birkaç parametre vardır. Parametre değerlerini, `Main()` yönteminden hemen sonra aşağıdaki kodla kolay adlarla eşlemek için bir struct oluşturun:

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Görüntüleme yardımcı programı yöntemi oluşturma

Görüntü verilerini ve ilgili tahminleri birden çok kez görüntüleyenden sonra, görüntüyü ve tahmin sonuçlarını görüntülemeyi işlemek için bir görüntüleme yardımcı programı yöntemi oluşturun.

1. Aşağıdaki kodu kullanarak, `InceptionSettings` yapısı hemen sonrasında `DisplayResults()` yöntemini oluşturun:

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. `DisplayResults` yönteminin gövdesini doldur:

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>. Tsv dosya yardımcı programı yöntemi oluşturma

1. Aşağıdaki kodu kullanarak, `DisplayResults()` yönteminden hemen sonra `ReadFromTsv()` yöntemini oluşturun:

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. `ReadFromTsv` yönteminin gövdesini doldur:

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    Kod, `ImagePath` özelliğinin görüntü dosyası adına dosya yolunu eklemek ve onu ve `Label` bir `ImageData` nesnesine yüklemek için `tags.tsv` dosyası aracılığıyla ayrıştırır.

### <a name="create-a-method-to-make-a-prediction"></a>Tahmin yapmak için bir yöntem oluşturma

1. Aşağıdaki kodu kullanarak, `DisplayResults()` yönteminden hemen önce `ClassifySingleImage()` yöntemini oluşturun:

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Tek `ImagePath`tam yolunu ve resim dosyası adını içeren bir `ImageData` nesnesi oluşturun. Aşağıdaki kodu `ClassifySingleImage()` yönteminin sonraki satırları olarak ekleyin:

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. Aşağıdaki kodu `ClassifySingleImage` yöntemine bir sonraki satır olarak ekleyerek tek bir tahmin yapın:

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    Tahmin sağlamak için, [tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) yöntemini kullanın. [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanız genelinde kullanılmak üzere [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnelerinin bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) oluşturan `PredictionEnginePool` hizmetini kullanın. [ASP.NET Core Web API 'sindeki `PredictionEnginePool` kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.

    > [!NOTE]
    > `PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.

1. Tahmin sonucunu `ClassifySingleImage()` yönteminde sonraki kod satırı olarak görüntüleyin:

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>ML.NET model işlem hattını oluşturma

Bir ML.NET model işlem hattı, bir tahmin zinciri zinciridir. İşlem hattı oluşturma sırasında yürütmenin gerçekleşmediğini unutmayın. Tahmin aracı nesneleri oluşturulur ancak yürütülmez.

1. Modeli oluşturmak için bir yöntem ekleyin

    Bu yöntem, öğreticinin kalbidir. Model için bir işlem hattı oluşturur ve ML.NET modelini oluşturmak için işlem hattını trafelar. Ayrıca, modeli daha önce görülmeyen test verilerine karşı değerlendirir.

    Aşağıdaki kodu kullanarak, `InceptionSettings` yapısı ve `DisplayResults()` yönteminden hemen önce olmak üzere `GenerateModel()` yöntemini oluşturun:

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Görüntü verilerinden pikselleri yüklemek, yeniden boyutlandırmak ve çıkarmak için tahmini ekleyin:

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    Görüntü verilerinin, TensorFlow modelinin beklediği biçimde işlenmesi gerekir. Bu durumda, görüntüler belleğe yüklenir, tutarlı bir boyuta yeniden boyutlandırılır ve pikseller sayısal bir vektörde ayıklanır.

1. TensorFlow modelini yüklemek için tahmin Aracı ' ı ekleyin ve puan edin:

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    İşlem hattındaki bu aşamada, TensorFlow modeli belleğe yüklenir ve ardından, Masorflow model ağı aracılığıyla piksel değerleri vektörü işlenir. Ayrıntılı bir öğrenme modeline giriş uygulama ve modeli kullanarak bir çıktı oluşturma, **Puanlama**olarak adlandırılır. Model tamamen kullanılırken, Puanlama bir çıkarım veya tahmin yapar.

    Bu durumda, çıkarım yapan katman olan son katman dışındaki tüm TensorFlow modelini kullanırsınız. Penultimate katmanının çıkışı `softmax_2_preactivation`etiketlidir. Bu katmanın çıktısı, orijinal giriş görüntülerini niteleyen özelliklerin bir vektörüdür.

    TensorFlow modeli tarafından oluşturulan bu özellik vektörü, bir ML.NET eğitim algoritmasına giriş olarak kullanılacaktır.

1. Eğitim verilerinde dize etiketlerini tamsayı anahtar değerleriyle eşlemek için tahmin aracı 'ı ekleyin:

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    Sonraki eklenen ml.net eğitmen, etiketlerinin rastgele dizeler yerine `key` biçimde olmasını gerektirir. Anahtar, bir dize değerine bire bir eşleme içeren bir sayıdır.

1. ML.NET eğitim algoritmasını ekleyin:

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. Tahmin edilen anahtar değerini bir dizeye geri eşlemek için tahmin aracı ekleyin:

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Modeli eğitme

1. [Loadfromtextfile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) sarmalayıcısı kullanarak eğitim verilerini yükleyin. Aşağıdaki kodu `GenerateModel()` yönteminin sonraki satırı olarak ekleyin:

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesnesine yüklenebilir.

1. Modeli yukarıda yüklenen verilerle eğitme:

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    `Fit()` yöntemi, eğitim veri kümesini işlem hattına uygulayarak modelinizi ister.

## <a name="evaluate-the-accuracy-of-the-model"></a>Modelin doğruluğunu değerlendirin

1. Aşağıdaki kodu `GenerateModel` yönteminin bir sonraki satırına ekleyerek test verilerini yükleyin ve dönüştürün:

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Modeli değerlendirmek için kullanabileceğiniz birkaç örnek görüntü vardır. Eğitim verileri gibi, bunların model tarafından dönüştürülebilmeleri için bir `IDataView`yüklenmesi gerekir.

1. Modeli değerlendirmek için `GenerateModel()` yöntemine aşağıdaki kodu ekleyin:

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    Tahmin kümesinden sonra, [değerlendir ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi:

    * Model değerlendirir (tahmin edilen değerleri `labels`test veri kümesiyle karşılaştırır).
    * Model performans ölçümlerini döndürür.

1. Model doğruluk ölçümlerini görüntüleme

    Ölçümleri göstermek, sonuçları paylaşmak ve sonra bunlar üzerinde işlem yapmak için aşağıdaki kodu kullanın:

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    Aşağıdaki ölçümler görüntü sınıflandırması için değerlendirilir:

    * `Log-loss`- [günlük kaybını](../resources/glossary.md#log-loss)görüntüleyin. Günlük kaybını mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.
    * `Per class Log-loss`. Her sınıf günlük kaybını, mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.

1. Eğitilen modeli sonraki satır olarak döndürmek için aşağıdaki kodu ekleyin:

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Uygulamayı çalıştırın!

1. MLContext sınıfının oluşturulmasından sonra `Main` yönteminde `GenerateModel` çağrısı ekleyin:

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. `ClassifySingleImage()` yöntemine çağrıyı, `Main` yönteminde sonraki kod satırı olarak ekleyin:

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. Konsol uygulamanızı çalıştırın (CTRL + F5). Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.  Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.

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

Tebrikler! Artık ML.NET ' deki bir `TensorFlow` modeline aktarım öğrenimi uygulayarak görüntü sınıflandırması için bir makine öğrenimi modeli oluşturdunuz.

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Sorunu anlama
> * Önceden eğitilen TensorFlow modelini ML.NET işlem hattına ekleyin
> * ML.NET modelini eğitme ve değerlendirme
> * Test görüntüsünü sınıflandır

Genişletilmiş bir görüntü sınıflandırma örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/machinöğrenim-Samples GitHub deposu](https://github.com/dotnet/machinelearning-samples/)
