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
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a>Öğretici: Transfer Learning ve ML.NET ile bir TensorFlow görüntü sınıflandırıcısını yeniden eğitme

Transfer Learning ve ML.NET ile görüntü sınıflandırması TensorFlow modelini yeniden eğitme hakkında bilgi edinin. Özgün model tek tek resimleri sınıflandırmak için eğitildi. Yeniden öğreticduktan sonra, yeni model görüntüleri geniş kategoriler halinde düzenler. 

[Görüntü sınıflandırma](https://en.wikipedia.org/wiki/Outline_of_object_recognition) modelini sıfırdan eğitmek için milyonlarca parametre, bir dizi etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir. Özel bir modeli sıfırdan eğitmek kadar uygun olmasa da, aktarım öğrenimi, binlerce görüntüde ve çok hızlı bir şekilde özelleştirilmiş bir model (bir saat içinde, GPU).

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Sorunu anlama
> * Önceden eğitilen modeli yeniden kullanma ve ayarlama
> * Görüntüleri sınıflandır

## <a name="what-is-transfer-learning"></a>Aktarım öğrenimi nedir?

Zaten benzer bir sorunu çözmek için eğitilen bir modeli yeniden kullanabilmeniz ve bu modelin tamamını ya da bir kısmını yeniden eğitmeniz durumunda ne olur? Yeni bir model oluşturmak için zaten eğitilen bir modelin bir kısmını yeniden kullanma tekniği, [Aktarım öğrenimi](https://en.wikipedia.org/wiki/Transfer_learning)olarak bilinir.

## <a name="image-classification-sample-overview"></a>Görüntü sınıflandırması örneğine genel bakış

Örnek, görüntüleri az miktarda eğitim verileriyle sınıflandırmak için önceden eğitilen bir modeli yeniden kullanarak bir görüntü Sınıflandırıcısı oluşturmak için ML.NET kullanan bir konsol uygulamasıdır.

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz. Varsayılan olarak, Bu öğreticinin .NET proje yapılandırmasında .NET Core 2,2 ' i hedeflediğini unutmayın.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi. 

* Microsoft.ML 1.0.0 NuGet paketi
* Microsoft. ML. ımageanalytics 1.0.0 NuGet paketi
* Microsoft. ML. TensorFlow 0.12.0 NuGet paketi

* [Öğretici varlıkları dizini. ZIP dosyası](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [InceptionV1 Machine Learning modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

[Derin öğrenme](https://en.wikipedia.org/wiki/Deep_learning) , görüntü işleme ve konuşma tanıma gibi revolutionizing alan Machine Learning bir alt kümesidir.

Derin öğrenme modelleri, birden fazla öğrenme katmanı içeren büyük ölçekli [veri](https://en.wikipedia.org/wiki/Labeled_data) ve [sinir Networks](https://en.wikipedia.org/wiki/Artificial_neural_network) kümeleri kullanılarak eğitilir. Derin öğrenme:

* Görüntü İşleme gibi bazı görevlerde daha iyi çalışır.

* Büyük veri miktarları üzerinde iyi sonuç verir.

Görüntü sınıflandırması, görüntüleri otomatik olarak birden çok kategoride sınıflandırmamızı sağlayan ortak bir Machine Learning görevdir:

* Görüntüde insan yüzü algılanıyor.
* Kediler ve köpekler algılanıyor.

 Ya da bir görüntünün (n) yiyecek, oyunı veya gereç olduğunu belirleyen aşağıdaki görüntülerde olduğu gibi:

![Pizza Image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![oyuncak](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
ayı![görüntüsü Toaster görüntüsü](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Önceki görüntüler Wikimedia Commons ' a aittir ve aşağıdaki gibi verilmiştir:
>
> * "220px-Pepperoni_pizza. jpg" genel etki alanı https://commons.wikimedia.org/w/index.php?curid=79505 ,,
> * [Jonık](https://commons.wikimedia.org/wiki/User:Jonik) -Self-Photo, CC BY-SA 2,0, https://commons.wikimedia.org/w/index.php?curid=48166 ile "119px-Nalle_-_a_small_brown_teddy_bear. jpg".
> * "193px-Broodrooster. jpg"- [k. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) -kendi ÇALıŞMASı, CC BY-SA 3,0, https://commons.wikimedia.org/w/index.php?curid=27403

Aktarım öğrenimi, tüm katmanları ve *Penultimate katmanını* *yeniden eğitme* gibi birkaç strateji içerir. Bu öğretici, *Penultimate katman stratejisinin*nasıl kullanılacağını açıklayacak ve gösterecektir. *Penultimate katman stratejisi* , belirli bir sorunu çözmek için önceden eğitilen bir modeli yeniden kullanır. Strateji daha sonra yeni bir sorunu çözmeleri için bu modelin son katmanını geri çeker. Yeni modelinizin bir parçası olarak önceden eğitilen modeli yeniden kullanmak önemli zaman ve kaynakları kaydeder.

Görüntü sınıflandırma modeliniz, popüler bir [](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)görüntü tanıma modeli olan `ImageNet` veri kümesi üzerinde eğitilen modeli, popüler bir görüntü tanıma modelini yeniden kullanır, bu da TensorFlow modelinin tüm görüntülerini "şemsiye", "Jersey" ve "gibi binlik bir sınıfa sınıflandırmaya çalıştığı Dishroni ".

, `Inception v1 model` [Derin bir evsel sinir ağı](https://en.wikipedia.org/wiki/Convolutional_neural_network) olarak sınıflandırılabilir ve sabit görsel tanıma görevlerinde, bazı etki alanlarında insan performansını eşleştirerek veya aşarak makul bir performans elde edebilir. Model/algoritma birden çok araştırmacılar tarafından geliştirilmiştir ve özgün kağıda dayalıdır: ["Szegedy, et tarafından Görüntü İşleme" için bir değerlendirme mimarisini yeniden düşünüyorsunuz. Eşkenar.](https://arxiv.org/abs/1512.00567)

, `Inception model` Binlerce farklı görüntüde önceden eğitilen için görüntü tanımlama için gereken [görüntü özelliklerini](https://en.wikipedia.org/wiki/Feature_(computer_vision)) içerir. Küçük görüntü özelliği katmanları basit özellikleri (kenarlar gibi) tanır ve daha yüksek katmanlar daha karmaşık özellikleri (örneğin şekiller) tanır. Görüntülerin sınıflandırılacağı önceden eğitilen bir model ile başladığınız için son katman çok daha küçük bir veri kümesine göre eğitilir. Modeliniz ikiden fazla kategori sınıflandırmanıza izin verdiğinden, bu [çok sınıf sınıflandırıcının](../resources/tasks.md#multiclass-classification)bir örneğidir. 

`TensorFlow`, eğitim derin sinir ağlarını (ve genel sayısal hesaplamalar) sağlayan ve ml.NET içinde bir `transformer` olarak uygulanan popüler bir derin öğrenme ve makine öğrenimi araç setidir. Bu öğreticide, yeniden kullanmak `Inception model`için kullanılır.

Aşağıdaki diyagramda gösterildiği gibi, .NET Core veya .NET Framework uygulamalarında ML.NET NuGet paketlerine bir başvuru eklersiniz. ML.net, kapsar ve var olan bir eğitilen `TensorFlow` `TensorFlow` model dosyasını Puanlama için yükleyen kodu yazmanızı sağlayan yerel kitaplığı içerir.  

![TensorFlow Transform ML.NET yay diyagramı](./media/image-classification/tensorflow-mlnet.png)

`Inception model` Görüntüleri bin kategoride sınıflandırıp, ancak daha küçük bir kategori kümesindeki görüntüleri ve yalnızca bu kategorileri sınıflandırmanız gerekir. `transfer` Parçasını`transfer learning`girin. Özel görüntü sınıflandırıcınızın yeni sınırlı kategorilerine görüntü tanıma ve sınıflandırma özelliğini aktarabilirsiniz `Inception model`.  

 Bu modelin son katmanını, üç kategori kümesini kullanarak yeniden eğitecağız:

* Yiyecek
* Cağı
* Elektrikli

Katmanınız, doğru kategoriyi olabildiğince çabuk bulmak için [ÇOKTERİMLİ lojistik regresyon algoritmasını](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) kullanır. Bu algoritma, yanıtı tespit etmek için olasılıkların kullanımını sınıflandırarak, doğru kategoriye bir değer ve diğerlerine sıfır değer verir.  

### <a name="dataset"></a>DataSet

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
> *[Wkımedıa Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), ücretsiz medya deposu.* 10:48 Ekim, 2018:  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

### <a name="create-a-project"></a>Proje oluşturma

1. "TransferLearningTF" adlı bir **.NET Core konsol uygulaması** oluşturun.

2. **Microsoft.ml NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml**için arama yapın. **Sürüm** açılır listesine tıklayın, listeden **1.0.0** paketini seçin ve ardından **Kaldır düğmesini seçin** . **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin. **Microsoft. ml. ımageanalytics v 1.0.0** ve **Microsoft. ml. TensorFlow v 0.12.0**için bu adımları tekrarlayın.

### <a name="prepare-your-data"></a>Verilerinizi hazırlayın

1. [Proje Varlıkları Dizin ZIP dosyasını](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)indirin ve sıkıştırmayı açın.

2. Dizini transferlearningtf proje dizininize kopyalayın. `assets` Bu dizin ve alt dizinleri, bu öğretici için gerekli olan veri ve destek dosyalarını (bir sonraki adımda indirecek ve ekleyeceğiniz bir model hariç) içerir.

3. [Inception modelini](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)indirin ve sıkıştırmayı açın.

4. `inception5h` Dizinin içeriğini *transferlearningtf* proje `assets\inputs-train\inception` dizininize kopyalamanız yeterlidir. Bu dizin, aşağıdaki görüntüde gösterildiği gibi, bu öğretici için gereken modeli ve ek destek dosyalarını içerir:

   ![Dizin içeriğini geçersiz kılma](./media/image-classification/inception-files.png)

5. Çözüm Gezgini, varlık dizinindeki ve alt dizinlerde bulunan dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

Çeşitli varlıkların yollarını tutmak için genel alanlar,, ve `LabelTokey` `PredictedLabelValue`için`ImageReal`genel değişkenler oluşturun:

* `_assetsPath`, varlıkların yolunu içerir.
* `_trainTagsTsv`Eğitim resmi veri etiketleri TSV dosyasının yolunu içerir.
* `_predictTagsTsv`tahmin görüntüsü veri etiketleri TSV dosyasının yolunu içerir.
* `_trainImagesFolder`modeli eğitmek için kullanılan görüntülerin yolunu içerir.
* `_predictImagesFolder`eğitilen model tarafından sınıflandırılacak görüntülerin yolunu içerir.
* `_inceptionPb`, modelinize yeniden eğmek için önceden eğitilen modelin yolunu içerir.
* `_inputImageClassifierZip`eğitilen modelin yüklendiği yolu içerir.
* `_outputImageClassifierZip`Eğitim modelinin kaydedildiği yolu içerir.
* `LabelTokey`, bir anahtarla eşleştirilmiş değerdir.`Label`
* `ImageReal`tahmin edilen görüntü değerini içeren sütundur.
* `PredictedLabelValue`tahmin edilen etiket değerini içeren sütundur.

Aşağıdaki kodu, bu yolları ve diğer değişkenleri belirtmek için `Main` yönteminin hemen üstüne ekleyin:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

Giriş verileriniz için bazı sınıflar ve tahminler oluşturun. Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.

1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ImageData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *ImageData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadeyi *ImageData.cs*öğesinin en üstüne ekleyin:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

Mevcut sınıf tanımını kaldırın ve `ImageData` sınıf için aşağıdaki kodu *ImageData.cs* dosyasına ekleyin:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

`ImageData`, giriş resmi veri sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:

* `ImagePath`görüntü dosyası adını içerir.
* `Label`resim etiketi için bir değer içerir.

Projenize yeni bir sınıf ekleyin `ImagePrediction`:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.

1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ImagePrediction.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *ImagePrediction.cs* dosyası kod düzenleyicisinde açılır. *ImagePrediction.cs 'in*en üstündeki `System.Text` `System.Collections.Generic` `using` ve deyimlerini kaldırın:

Mevcut sınıf tanımını kaldırın ve `ImagePrediction` *ImagePrediction.cs* dosyasına sınıfına sahip olan aşağıdaki kodu ekleyin:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

`ImagePrediction`, görüntü tahmin sınıfıdır ve aşağıdaki alanlara sahiptir:

* `Score`belirli bir görüntü sınıflandırması için güven yüzdesini içerir.
* `PredictedLabelValue`tahmin edilen görüntü sınıflandırma etiketi için bir değer içerir.

`ImagePrediction`, model eğitilen bir tahmin için kullanılan sınıftır. Görüntü yolu için `string` bir`ImagePath`() içerir. , `Label` Modeli yeniden kullanmak ve yeniden geliştirmek için kullanılır. , `PredictedLabelValue` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme için eğitim verileri olan bir giriş, tahmin edilen değerler ve model kullanılır.

[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal `DBContext` olarak da benzerdir.

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

Değişkeni yeni bir `MLContext`örneğiyle başlatın. `mlContext`  Satırı, `Main` yöntemindeki aşağıdaki kodla değiştirin: `Console.WriteLine("Hello World!")`

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a>Varsayılan parametreler için bir struct oluşturun

Inception modelinde, geçirmeniz gereken birkaç varsayılan parametre vardır. Aşağıdaki kodla, varsayılan parametre değerlerini kolay adlarla eşlemek için bir struct oluşturun, yalnızca `Main()` yönteminden sonra:

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Görüntüleme yardımcı programı yöntemi oluşturma

Görüntü verilerini ve ilgili tahminleri birden çok kez görüntüleyenden sonra, görüntüyü ve tahmin sonuçlarını görüntülemeyi işlemek için bir görüntüleme yardımcı programı yöntemi oluşturun.

`DisplayResults()` Yöntemi aşağıdaki görevleri yürütür:

* Tahmin edilen sonuçları görüntüler.

Aşağıdaki kodu kullanarak, `InceptionSettings` yapının hemen ardından yöntemioluşturun:`DisplayResults()`

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

Yöntemi tahmin edilen alanlarla `ImagePrediction` birlikte doldurulur `ImagePath`. `Transform()` ML.NET işlemi ilerledikçe, her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

`DisplayResults()` Yöntemi iki görüntü sınıflandırma yöntemlerinde çağıracaksınız.

### <a name="create-a-tsv-file-utility-method"></a>. Tsv dosya yardımcı programı yöntemi oluşturma

`ReadFromTsv()` Yöntemi aşağıdaki görevleri yürütür:

* Resim veri `tags.tsv` dosyasını okur.
* Dosya yolunu görüntü dosyası adına ekler.
* Dosya verilerini IEnumerable`ImageData` nesnesine yükler.

Aşağıdaki kodu kullanarak yönteminden hemen `PairAndDisplayResults()` sonra yönteminioluşturun:`ReadFromTsv()`

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

Aşağıdaki `tags.tsv` kod, dosya yolunu `ImagePath` özellik için görüntü dosyası adına eklemek `Label` ve bir `ImageData` nesnesine yüklemek için dosyasını ayrıştırır. `ReadFromTsv()` Metodun ilk satırı olarak ekleyin.  Tahmin sonuçlarını göstermek için tam dosya yolu gereklidir.

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
ML.NET ' de üç ana kavram vardır: [Veri](../resources/glossary.md#data), [dönüştürücüler](../resources/glossary.md#transformer)ve [estimators](../resources/glossary.md#estimator).

## <a name="reuse-and-tune-pre-trained-model"></a>Önceden eğitilen modeli yeniden kullanma ve ayarlama

`ReuseAndTuneInceptionModel()` Yöntemi`Main()` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin:

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

`ReuseAndTuneInceptionModel()` Yöntemi aşağıdaki görevleri yürütür:

* Verileri yükler
* Verileri ayıklar ve dönüştürür.
* TensorFlow modeline puan alır.
* Model (geri çekme).
* Model sonuçlarını görüntüler.
* Modeli değerlendirir.
* Modeli döndürür.

Aşağıdaki kodu kullanarak, `InceptionSettings` `DisplayResults()` yapının hemen ardından ve yönteminden hemen önce yönteminioluşturun:`ReuseAndTuneInceptionModel()`

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a>Verileri yükleme

ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.

`MLContext.Data.LoadFromTextFile` Sarmalayıcı kullanarak verileri yükleyin. Aşağıdaki kodu `ReuseAndTuneInceptionModel()` yönteminin sonraki satırı olarak ekleyin:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a>Özellikleri Ayıkla ve verileri Dönüştür

Önceden işleme ve temizleme verileri, makine öğrenimi için bir veri kümesi etkin bir şekilde kullanılmadan önce oluşan önemli görevlerdir.  Bu modelleme görevleri olmadan veri kullanımı, yanıltıcı sonuçlar üretebilir.

Makine öğrenimi algoritmaları [, verileri ve](../resources/glossary.md#feature) derin sinir ağlarla ilgilenirken görüntüleri ağ tarafından beklenen biçime uyarlamanız gerekir. Bu biçim sayısal bir [vektördür](../resources/glossary.md#numerical-feature-vector).

Eğitim ve değerlendirmeden sonra **etiket** sütun değerleriyle birlikte tahmin edin. Önceden eğitilen bir model kullanırken, alanları [Mapvaluetokey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemiyle yeni modelle eşleyin. Bu yöntem, `Label` bir sayısal anahtar türü (`LabelTokey`) sütununu dönüştürür ve bunu yeni veri kümesi sütunu olarak ekler:  Bunu, `estimator` aynı zamanda da bu şekilde adlandırın. Sonraki kod satırını ekleyin:

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

Görüntü işleme tahmin aracı, özellik ayıklama için önceden eğitilen [derin sinir ağı (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) özelliklerini kullanır. Derin sinir ağlarla ilgilenirken, görüntüleri beklenen ağ biçimine uyarlayın. Bu, görüntü verilerini modelin beklenen biçiminde almak için birkaç görüntü dönüştürme işlemi kullanmanız nedenidir:

1. Dönüşüm `LoadImages`görüntüleri, bir bit eşlem türü olarak belleğe yüklenir.
2. `ResizeImages` Dönüştürme, önceden eğitilen modelin tanımlı bir giriş resmi genişliği ve yüksekliği olduğundan, görüntüleri yeniden boyutlandırır.
3. `ExtractPixels` Dönüştürme, giriş görüntülerinden pikselleri ayıklar ve bunları sayısal bir Vector öğesine dönüştürür.

Bu görüntü dönüşümlerini sonraki kod satırları olarak ekle:

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

, `LoadTensorFlowModel` `TensorFlow` `ScoreTensorFlowModel` Modelin`TensorFlowEstimator` bir kez yüklenmesine izin veren ve ardından kullanılarak oluşturulan kullanımı kolay bir yöntemdir. Belirtilen çıktıları `Inception model`ayıklar (görüntü özellikleri `softmax2_pre_activation`) ve önceden eğitilen `TensorFlow` modeli kullanarak bir veri kümesine puan verir. `ScoreTensorFlowModel`

`softmax2_pre_activation`görüntülerin hangi sınıfa ait olduğunu belirlemek için modele yardımcı olur. `softmax2_pre_activation`bir görüntü için kategorilerin her biri için bir olasılık döndürür ve bu olasılıkların hepsi 1 ' e kadar olmalıdır. Aşağıdaki örnekte gösterildiği gibi bir görüntünün yalnızca bir kategoriye ait olacağını varsayar:

| örneği         | Olasılıktır   |
| ------------- | ------------- |
| `Food`        |  0,001        |
| `Toy`         |  0,95         |
| `Appliance`   |  0,06         |

Aşağıdaki kod satırıyla öğesini `estimator` öğesineekleyin:`TensorFlowTransform`

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a>Eğitim algoritması seçin

Eğitim algoritmasını eklemek için `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` sarmalayıcı yöntemini çağırın.  [Lbfgsmaximumentropi](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) öğesine `estimator` eklenir ve geçmiş verilerden bilgi almak için Inception görüntü özelliklerini `Label` (`softmax2_pre_activation`) ve giriş parametrelerini kabul eder.  Aşağıdaki kodla birlikte bir sorun ekleyin:

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

Ayrıca, `predictedlabel` `predictedlabelvalue`ile arasında eşleme yapmanız gerekir:

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

`Fit()` Yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi trakla. Modeli eğitim veri kümesine sığdırın `ReuseAndTuneInceptionModel()` ve aşağıdaki kod satırını yöntemine ekleyerek eğitilen modeli döndürün:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapar.  Aşağıdaki kodu öğesine `ReuseAndTuneInceptionModel()`ekleyerek verileridönüştürün:`Training`

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

Daha kolay görüntülenmesi için görüntü verilerinizi `DataViews` ve tahminini kesin olarak `IEnumerables` belirlenmiş şekilde eşleştirin. Aşağıdaki kodu kullanarak bunu yapmak için yönteminikullanın:`MLContext.CreateEnumerable()`

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

Veri ve tahmine dayalı olarak yöntemi bir sonraki satır `ReuseAndTuneInceptionModel()` olarak göstermek için yönteminiçağırın:`DisplayResults()`

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

Tahmin kümesinden sonra, [değerlendir ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi:

* Model değerlendirir (tahmin edilen değerleri gerçek veri kümesiyle `Labels`karşılaştırır).

* Model performans ölçümlerini döndürür.

Aşağıdaki kodu `ReuseAndTuneInceptionModel()` yöntemine sonraki satır olarak ekleyin:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

Aşağıdaki ölçümler görüntü sınıflandırması için değerlendirilir:

* `Log-loss`- [günlük kaybını](../resources/glossary.md#log-loss)görüntüleyin. Günlük kaybını mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.

* `Per class Log-loss`. Her sınıf günlük kaybını, mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.

Ölçümleri göstermek, sonuçları paylaşmak ve sonra bunlar üzerinde işlem yapmak için aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 Eğitilen modeli sonraki satır olarak döndürmek için aşağıdaki kodu ekleyin:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a>Görüntüleri yüklü bir modelle sınıflandır

`ClassifyImages()` Yöntemi`Main` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin:

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

`ClassifyImages()` Yöntemi aşağıdaki görevleri yürütür:

* Okuma. TSV dosyasını içine `IEnumerable`.
* Sınama verilerine göre görüntü sınıflandırmalarını tahmin eder.

Yöntemi, aşağıdaki kodu kullanarak yönteminden hemen `ReuseAndTuneInceptionModel()` sonra ve `PairAndDisplayResults()` yönteminden hemen önce oluşturun: `ClassifyImages()`

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

İlk olarak, her `ReadFromTsv()` biri `ImagePath`için tam yolu `IEnumerable<ImageData>` içeren bir sınıf oluşturmak için yöntemini çağırın. Verilerinizi ve tahmin sonuçlarınızı eşleştirmek için bu dosya yolunun olması gerekir. Ayrıca, `IEnumerable<ImageData>` öğesini tahmin etmek için kullanacağınız sınıfı bir `IDataView` öğesine dönüştürmeniz gerekir. Aşağıdaki kodu, `ClassifyImages()` yönteminin sonraki iki satırı olarak ekleyin:

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

Daha önce eğitim görüntü verilerinde yaptığınız gibi, geçirilen modelin [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak test görüntüsü verilerinin kategorisini tahmin edin. Aşağıdaki kodu `ClassifyImages()` tahmine meler için yöntemine ekleyin ve öğesini eşleştirme ve görüntüleme `IEnumerable` için `IDataView` öğesine `predictions` dönüştürün:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

Test görüntüsü verilerinizi ve tahminleri eşleştirmek ve göstermek için aşağıdaki kodu, daha önce `DisplayResults()` `ClassifyImages()` yönteminde bir sonraki satır olarak oluşturulan yöntemi çağırmak için ekleyin:

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a>Yüklü bir modelle tek bir görüntüyü sınıflandırma

`ClassifySingleImage()` Yöntemi`Main` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin:

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

`ClassifySingleImage()` Yöntemi aşağıdaki görevleri yürütür:

* Bir `ImageData` örnek yükler.
* Test verilerine göre görüntü sınıflandırmasını tahmin eder.

Yöntemi, aşağıdaki kodu kullanarak yönteminden hemen `ClassifyImages()` sonra ve `PairAndDisplayResults()` yönteminden hemen önce oluşturun: `ClassifySingleImage()`

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

İlk olarak, tek `ImageData` `ImagePath`için tam yolu ve resim dosyası adını içeren bir sınıf oluşturun. Aşağıdaki kodu `ClassifySingleImage()` yöntemine bir sonraki satır olarak ekleyin:

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

[PredictionEngine sınıfı](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştiren KULLANıŞLı bir API 'dir. PREDICT [()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütunu üzerinde bir tahmin yapar. Aşağıdaki `imageData` kodu öğesine `PredictionEngine` ekleyerekgörüntükategorisinitahminetmek`ClassifySingleImage()`için öğesine geçirin:

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

`ClassifySingleImage()` Yöntem içindeki bir sonraki kod satırı olarak tahmin sonucunu görüntüleyin:

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a>Sonuçlar

Önceki adımları uyguladıktan sonra konsol uygulamanızı çalıştırın (CTRL + F5). Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.  Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.

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

Tebrikler! Artık ml.net ' de önceden eğitilen `TensorFlow` bir modeli yeniden çalıştırarak görüntü sınıflandırması için bir makine öğrenimi modelini başarıyla oluşturdunuz.

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Sorunu anlama
> * Önceden eğitilen modeli yeniden kullanma ve ayarlama
> * Görüntüleri yüklü bir modelle sınıflandır

Genişletilmiş bir görüntü sınıflandırma örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/machinöğrenim-Samples GitHub deposu](https://github.com/dotnet/machinelearning-samples/)
