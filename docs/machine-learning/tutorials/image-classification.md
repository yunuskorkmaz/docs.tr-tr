---
title: 'Öğretici: Önceden eğitilen bir TensorFlow modelinden ML.NET görüntü sınıflandırma modeli oluşturma'
description: Mevcut bir TensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline bilgi aktarmayı öğrenin. TensorFlow modeli görüntüleri bin kategoride sınıflandırmakta eğitildi. ML.NET modeli görüntüleri daha az daha geniş kategoriler halinde sınıflandırmak için aktarım öğrenimini kullanır.
ms.date: 09/26/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 28d8c18721bd353e961284935758a87679c8c8e0
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353687"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Öğretici: Önceden eğitilen bir TensorFlow modelinden ML.NET görüntü sınıflandırma modeli oluşturma

Mevcut bir TensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline bilgi aktarmayı öğrenin.

TensorFlow modeli görüntüleri bin kategoride sınıflandırmakta eğitildi. ML.NET modeli, görüntüleri 3 kategoride sınıflandırmak üzere bir modeli eğitemak için, ardışık düzeninde TensorFlow modelinin bir parçasını kullanır.

[Görüntü sınıflandırma](https://en.wikipedia.org/wiki/Outline_of_object_recognition) modelini sıfırdan eğitmek için milyonlarca parametre, bir dizi etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir. Özel bir modeli sıfırdan eğitmek kadar uygun olmasa da, aktarım öğrenimi, binlerce görüntüde ve çok hızlı bir şekilde özelleştirilmiş bir model (bir saat içinde, GPU). Bu öğreticide, yalnızca bir düzine eğitim görüntüsü kullanılarak bu işlem daha da ayrıntılı şekilde ölçeklendirilir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
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

* [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

* Microsoft.ML 1.3.1 NuGet paketi
* Microsoft. ML. ımageanalytics 1.3.1 NuGet paketi
* Microsoft. ML. TensorFlow 1.3.1 NuGet paketi

* [Öğretici varlıkları dizini. ZIP dosyası](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

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

![Pizza Image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![oyuncak](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
ayı![görüntüsü Toaster görüntüsü](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Önceki görüntüler Wikimedia Commons ' a aittir ve aşağıdaki gibi verilmiştir:
>
> * "220px-Pepperoni_pizza. jpg" genel etki alanı, https://commons.wikimedia.org/w/index.php?curid=79505,
> * [Jonık](https://commons.wikimedia.org/wiki/User:Jonik) -Self-Photo, CC BY-SA 2,0 https://commons.wikimedia.org/w/index.php?curid=48166 ile "119px-Nalle_-_a_small_brown_teddy_bear. jpg".
> * "193px-Broodrooster. jpg"- [k. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) -kendi ÇALıŞMASı, CC BY-SA 3,0, https://commons.wikimedia.org/w/index.php?curid=27403

@No__t-0, görüntüleri bin kategoride sınıflandırmakta, ancak bu öğreticide, görüntüleri daha küçük bir kategori kümesinde ve yalnızca bu kategorilerden sınıflandırmanız gerekir. `transfer` Parçasını`transfer learning`girin. Özel görüntü sınıflandırıcınızın yeni sınırlı kategorilerine görüntü tanıma ve sınıflandırma özelliğini aktarabilirsiniz `Inception model`.

* Yiyecek
* Cağı
* Elektrikli

Bu öğretici, `ImageNet` veri kümesi üzerinde eğitilen popüler bir görüntü tanıma modeli olan TensorFlow [Inception modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) derin öğrenme modelini kullanır. TensorFlow modeli, tüm görüntüleri "şemsiye", "Jersey" ve "Dishronı" gibi binlik bir sınıfa göre sınıflandırır.

@No__t-0, binlerce farklı görüntüde önceden eğitildiğinden, dahili olarak görüntü tanımlama için gereken [görüntü özelliklerini](https://en.wikipedia.org/wiki/Feature_(computer_vision)) içerir. En az sınıfa sahip yeni bir modeli eğitebilmeniz için modelde bu iç görüntü özelliklerinden yararlanabilirsiniz.

Aşağıdaki diyagramda gösterildiği gibi, .NET Core veya .NET Framework uygulamalarında ML.NET NuGet paketlerine bir başvuru eklersiniz. ML.NET ' nin altında, var olan eğitilen bir `TensorFlow` model dosyasını yükleyen kodu yazmanıza olanak tanıyan yerel `TensorFlow` kitaplığına ekler ve başvurur.

![TensorFlow Transform ML.NET yay diyagramı](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Birden çok Lass sınıflandırması

Klasik makine öğrenimi algoritması için giriş olarak uygun özellikleri ayıklamak üzere TensorFlow kullanım modelini kullandıktan sonra, ML.NET [çok sınıflı bir sınıflandırıcı](../resources/tasks.md#multiclass-classification)ekleyeceğiz.

Bu durumda kullanılan belirli bir eğitmen, [ÇOKTERİMLİ lojistik regresyon algoritmasıdır](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

Bu eğitimci tarafından uygulanan algoritma, görüntü verilerinde çalışan derin bir öğrenme modelinin durumu olan çok sayıda özellik ile ilgili sorunları iyi gerçekleştirir.

### <a name="data"></a>Data

İki veri kaynağı vardır: `.tsv` dosya ve resim dosyaları.  Dosya iki sütun içerir: ilki olarak `ImagePath` tanımlanır ve ikinci tane `Label` görüntüye karşılık gelir. `tags.tsv` Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:

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
    * **Sürüm** açılır listesine tıklayın, listeden **1.3.1** paketini seçin ve ardından **Kaldır düğmesini seçin** .
    * **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin.
    * Listelenen paketlerin lisans koşullarını kabul ediyorsanız, **Lisans kabulü** Iletişim kutusunda **kabul ediyorum** düğmesini seçin.
    * **Microsoft. ml. ımageanalytics v 1.3.1** ve **Microsoft. ml. TensorFlow v 1.3.1**için bu adımları tekrarlayın.

### <a name="download-assets"></a>Varlıkları indir

1. [Proje Varlıkları Dizin ZIP dosyasını](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)indirin ve sıkıştırmayı açın.

1. Dizini transferlearningtf proje dizininize kopyalayın. `assets` Bu dizin ve alt dizinleri, bu öğretici için gerekli olan veri ve destek dosyalarını (bir sonraki adımda indirecek ve ekleyeceğiniz bir model hariç) içerir.

1. [Inception modelini](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)indirin ve sıkıştırmayı açın.

1. `inception5h` Dizinin içeriğini *transferlearningtf* proje `assets/inputs-train/inception` dizininize kopyalamanız yeterlidir. Bu dizin, aşağıdaki görüntüde gösterildiği gibi, bu öğretici için gereken modeli ve ek destek dosyalarını içerir:

   ![Dizin içeriğini geçersiz kılma](./media/image-classification/inception-files.png)

1. Çözüm Gezgini, varlık dizinindeki ve alt dizinlerde bulunan dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

1. Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. Varlık yollarını belirtmek için, aşağıdaki kodu `Main` yönteminin üstüne doğru satıra ekleyin:

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. Giriş verileriniz ve tahminler için sınıflar oluşturun.

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    `ImageData`, giriş resmi veri sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:

    * `ImagePath`görüntü dosyası adını içerir.
    * `Label`resim etiketi için bir değer içerir.

1. Projenize yeni bir sınıf ekleyin `ImagePrediction`:

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    `ImagePrediction`, görüntü tahmin sınıfıdır ve aşağıdaki alanlara sahiptir:

    * `Score`belirli bir görüntü sınıflandırması için güven yüzdesini içerir.
    * `PredictedLabelValue`tahmin edilen görüntü sınıflandırma etiketi için bir değer içerir.

    `ImagePrediction`, model eğitilen bir tahmin için kullanılan sınıftır. Görüntü yolu için `string` bir`ImagePath`() içerir. @No__t-0, modeli yeniden kullanmak ve geliştirmek için kullanılır. , `PredictedLabelValue` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme için eğitim verileri olan bir giriş, tahmin edilen değerler ve model kullanılır.

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

1. Değişkeni yeni bir `MLContext`örneğiyle başlatın. `mlContext`  Satırı, `Main` yöntemindeki aşağıdaki kodla değiştirin: `Console.WriteLine("Hello World!")`

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    [Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal `DBContext` olarak da benzerdir.

### <a name="create-a-struct-for-inception-model-parameters"></a>Inception model parametreleri için bir struct oluşturun

1. Inception modelinde, geçirmeniz gereken birkaç parametre vardır. Parametre değerlerini, `Main()` yönteminden hemen sonra aşağıdaki kodla kolay adlarla eşlemek için bir struct oluşturun:

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Görüntüleme yardımcı programı yöntemi oluşturma

Görüntü verilerini ve ilgili tahminleri birden çok kez görüntüleyenden sonra, görüntüyü ve tahmin sonuçlarını görüntülemeyi işlemek için bir görüntüleme yardımcı programı yöntemi oluşturun.

1. Aşağıdaki kodu kullanarak, `InceptionSettings` yapının hemen ardından yöntemioluşturun:`DisplayResults()`

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. @No__t-0 yönteminin gövdesini doldur:

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>. Tsv dosya yardımcı programı yöntemi oluşturma

1. Aşağıdaki kodu kullanarak yönteminden hemen `DisplayResults()` sonra yönteminioluşturun:`ReadFromTsv()`

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. @No__t-0 yönteminin gövdesini doldur:

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    Kod, `ImagePath` özelliği için görüntü dosyası adına dosya yolunu eklemek ve onu ve `Label` ' i bir @no__t 3 nesnesine yüklemek için `tags.tsv` dosyası aracılığıyla ayrıştırır.

### <a name="create-a-method-to-make-a-prediction"></a>Tahmin yapmak için bir yöntem oluşturma

1. Aşağıdaki kodu kullanarak, `DisplayResults()` yönteminden hemen önce `ClassifySingleImage()` yöntemini oluşturun:

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Tek `ImagePath` için tam yolu ve resim dosyası adını içeren `ImageData` nesnesi oluşturun. Aşağıdaki kodu `ClassifySingleImage()` yöntemine bir sonraki satır olarak ekleyin:

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. @No__t-0 yönteminde sonraki satır olarak aşağıdaki kodu ekleyerek tek bir tahmin yapın:

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    [PredictionEngine sınıfı](xref:Microsoft.ML.PredictionEngine%602) sınıfı, tek bir veri örneğinde tahmin gerçekleştiren KULLANıŞLı bir API 'dir. Tahmin sağlamak için, [tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) yöntemini kullanın.

1. `ClassifySingleImage()` Yöntem içindeki bir sonraki kod satırı olarak tahmin sonucunu görüntüleyin:

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>ML.NET model işlem hattını oluşturma

Bir ML.NET model işlem hattı, bir tahmin zinciri zinciridir. İşlem hattı oluşturma sırasında yürütmenin gerçekleşmediğini unutmayın. Tahmin aracı nesneleri oluşturulur ancak yürütülmez.

1. Modeli oluşturmak için bir yöntem ekleyin

    Bu yöntem, öğreticinin kalbidir. Model için bir işlem hattı oluşturur ve ML.NET modelini oluşturmak için işlem hattını trafelar. Ayrıca, modeli daha önce görülmeyen test verilerine karşı değerlendirir.

    Aşağıdaki kodu kullanarak, `InceptionSettings` `DisplayResults()` yapının hemen ardından ve yönteminden hemen önce yönteminioluşturun:`GenerateModel()`

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Görüntü verilerinden pikselleri yüklemek, yeniden boyutlandırmak ve çıkarmak için tahmini ekleyin:

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    Görüntü verilerinin, TensorFlow modelinin beklediği biçimde işlenmesi gerekir. Bu durumda, görüntüler belleğe yüklenir, tutarlı bir boyuta yeniden boyutlandırılır ve pikseller sayısal bir vektörde ayıklanır.

1. TensorFlow modelini yüklemek için tahmin Aracı ' ı ekleyin ve puan edin:

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    İşlem hattındaki bu aşamada, TensorFlow modeli belleğe yüklenir ve ardından, Masorflow model ağı aracılığıyla piksel değerleri vektörü işlenir. Ayrıntılı bir öğrenme modeline giriş uygulama ve modeli kullanarak bir çıktı oluşturma, **Puanlama**olarak adlandırılır. Model tamamen kullanılırken, Puanlama bir çıkarım veya tahmin yapar. 

    Bu durumda, çıkarım yapan katman olan son katman dışındaki tüm TensorFlow modelini kullanırsınız. Penultimate katmanının çıktısı `softmax_2_preactivation` olarak etiketlenir. Bu katmanın çıktısı, orijinal giriş görüntülerini niteleyen özelliklerin bir vektörüdür.

    TensorFlow modeli tarafından oluşturulan bu özellik vektörü, bir ML.NET eğitim algoritmasına giriş olarak kullanılacaktır.

1. Eğitim verilerinde dize etiketlerini tamsayı anahtar değerleriyle eşlemek için tahmin aracı 'ı ekleyin:

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    Sonraki eklenen ml.net eğitmen, etiketlerin rastgele dizeler yerine `key` biçiminde olmasını gerektirir. Anahtar, bir dize değerine bire bir eşleme içeren bir sayıdır.

1. ML.NET eğitim algoritmasını ekleyin:

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. Tahmin edilen anahtar değerini bir dizeye geri eşlemek için tahmin aracı ekleyin:

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Modeli eğitme

1. [Loadfromtextfile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) sarmalayıcısı kullanarak eğitim verilerini yükleyin. Aşağıdaki kodu `GenerateModel()` yönteminin sonraki satırı olarak ekleyin:

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.

1. Modeli yukarıda yüklenen verilerle eğitme:

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    @No__t-0 yöntemi, eğitim veri kümesini işlem hattına uygulayarak modelinizi adım adım sağlar.

## <a name="evaluate-the-accuracy-of-the-model"></a>Modelin doğruluğunu değerlendirin

1. @No__t-0 yönteminin bir sonraki satırına aşağıdaki kodu ekleyerek test verilerini yükleyin ve dönüştürün:

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Modeli değerlendirmek için kullanabileceğiniz birkaç örnek görüntü vardır. Eğitim verileri gibi, bunların model tarafından dönüştürülebilmeleri için `IDataView` ' a yüklenmesi gerekir.
   
1. Modeli değerlendirmek için `GenerateModel()` yöntemine aşağıdaki kodu ekleyin:

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    Tahmin kümesinden sonra, [değerlendir ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi:

    * Model değerlendirir (tahmin edilen değerleri `labels`) test veri kümesiyle karşılaştırır.
    * Model performans ölçümlerini döndürür.

1. Model doğruluk ölçümlerini görüntüleme

    Ölçümleri göstermek, sonuçları paylaşmak ve sonra bunlar üzerinde işlem yapmak için aşağıdaki kodu kullanın:

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    Aşağıdaki ölçümler görüntü sınıflandırması için değerlendirilir:

    * `Log-loss`- [günlük kaybını](../resources/glossary.md#log-loss)görüntüleyin. Günlük kaybını mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.
    * `Per class Log-loss`. Her sınıf günlük kaybını, mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.

1. Eğitilen modeli sonraki satır olarak döndürmek için aşağıdaki kodu ekleyin:

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Uygulamayı çalıştırın!

1. MLContext sınıfının oluşturulmasından sonra `Main` yönteminde `GenerateModel` ' a çağrı ekleyin:

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. @No__t-0 yöntemine `Main` yönteminde sonraki kod satırı olarak çağrı ekleyin:

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. Konsol uygulamanızı çalıştırın (CTRL + F5). Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.  Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.

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
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9625379

    C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
    Press any key to close this window . . .
    ```

Tebrikler! Artık ML.NET ' deki bir `TensorFlow` modeline aktarma öğrenimini uygulayarak görüntü sınıflandırması için bir makine öğrenimi modeli oluşturdunuz.

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
