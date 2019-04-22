---
title: TensorFlow ile bir ML.NET özel görüntü sınıflandırıcı oluşturma
description: Önceden eğitilmiş bir TensorFlow modeli yeniden kullanarak görüntüleri sınıflandırmak için senaryo bir TensorFlow aktarımlı ML.NET özel görüntü sınıflandırıcıda oluşturma keşfedin.
ms.date: 04/05/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9b9ac1f1f15b4003a19a3d30d6cadf3e86946376
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517973"
---
# <a name="tutorial-build-an-mlnet-custom-image-classifier-with-tensorflow"></a>Öğretici: TensorFlow ile bir ML.NET özel görüntü sınıflandırıcı oluşturma

Bu örnek öğretici, önceden eğitilen bir görüntü sınıflandırıcı nasıl kullanabileceğinizi gösteren `TensorFlow` görüntüleri birkaç kategoride sınıflandırmak için yeni özel modeli oluşturmak için model.

Ne öncesi zaten bir model kullanabilirsiniz ya da tümünün veya bazılarının, sorununuzu çözmenize yardımcı olmak için bu modelinin katmanlarını yeniden eğitme ve benzer bir sorunu çözmek eğitilen? Bu teknik yeniden yeni bir model oluşturmak üzere önceden eğitilen bir modelin parçası olarak da bilinen [aktarım öğrenme](https://en.wikipedia.org/wiki/Transfer_learning).

Eğitim bir [görüntü sınıflandırması](https://en.wikipedia.org/wiki/Outline_of_object_recognition) sıfırdan modeli, Parametreler, bir sürü etiketli eğitim verilerini ve işlem kaynakları (GPU saat yüzlerce) çok büyük miktarda milyonlarca ayarlama gerektirir. Aktarımlı öğrenme kadar etkili olarak sıfırdan özel bir model eğitim olsa da görüntüleri etiketlenmiş resimlerinizi milyonlarca karşılaştırması binlerce birlikte çalışarak bu işlem için kısayol sağlar ve oldukça hızlı bir şekilde özelleştirilmiş model derleme (bir makinede bir saat içinde bir GPU).

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * Sorunu anlama
> * Yeniden kullanmak ve önceden eğitilmiş bir modeli ayarlama
> * Resimleri sınıflandırma

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu öğretici ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.10**. Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) GitHub deposu.

## <a name="image-classification-sample-overview"></a>Görüntü sınıflandırma örneğine genel bakış

Örnek görüntüleri küçük bir eğitim veri miktarı ile sınıflandırmak için önceden eğitilmiş bir modeli yeniden kullanarak bir görüntü sınıflandırıcı oluşturma için ML.NET kullanan bir konsol uygulamasıdır.

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) depo.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

* Microsoft.ML 0.10.0 Nuget paketi
* Microsoft.ML.ImageAnalytics 0.10.0 Nuget paketi
* Microsoft.ML.TensorFlow 0.10.0 Nuget paketi

* [Öğretici varlıklar dizin. ZIP dosyası](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [InceptionV3 machine learning modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

[Derin öğrenme](https://en.wikipedia.org/wiki/Deep_learning) , görüntü işleme ve konuşma tanıma gibi alanları revolutionizing Machine Learning, bir alt kümesidir.

Modelleri, büyük kümelerini kullanarak eğitilir derin öğrenme [veri etiketli](https://en.wikipedia.org/wiki/Labeled_data) ve [sinir ağları](https://en.wikipedia.org/wiki/Artificial_neural_network) birden çok öğrenim katmanlarını içerir. Derin öğrenme:

* Görüntü işleme gibi bazı görevler üzerinde daha iyi gerçekleştirir.

* İyi büyük verileri tutarlarını gerçekleştirir.

Görüntü sınıflandırması otomatik olarak gibi birden fazla kategoriye görüntüleri sınıflandırmak olanak sağlayan ortak bir Machine Learning görevidir:

* İnsan yüz veya bir görüntüde algılanıyor.
* Köpek Kedilere algılanıyor.

 Veya belirlenmesinde aşağıdaki resimlerde gösterildiği gibi bir görüntü bir yiyecek, çocuğunun veya Gereci:

![pizza görüntü](./media/image-classification/220px-Pepperoni_pizza.jpg)
![Oyuncak Ayı ayı görüntü](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster görüntüsü](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Önceki görüntüler için Wikimedia Commons ait ve şu şekilde atanmıştır:
>
> * "220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" tarafından [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) -, CC BY-SA 2.0, kendi kendine fotoğrafı https://commons.wikimedia.org/w/index.php?curid=48166.
> * "193px-Broodrooster.jpg" tarafından [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) -kendi iş, CC BY SA 3.0 https://commons.wikimedia.org/w/index.php?curid=27403

Aktarımlı öğrenme içeren birkaç stratejileri gibi *tüm katmanlar yeniden eğitme* ve *sondan katman*. Bu öğreticide açıklamak ve nasıl kullanabileceğinizi gösteren *sondan katman stratejisi*. *Sondan katman stratejisi* zaten belirli bir sorunu çözmek için önceden eğitildi bir model kullanır. Strateji, ardından yeni bir sorunu çözmeye sağlamak için bu modelin son katmanı retrains. Önceden eğitilmiş modelin yeni modelinizin bir parçası olarak yeniden önemli zamandan ve kaynaklardan tasarruf.

Görüntü sınıflandırma modelinizi yeniden [başlangıcı modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), üzerinde bir popüler görüntü tanıma modeli eğitilir `ImageNet` TensorFlow modeli nerede çalışırsa tüm sınıflandırmak için veri kümesi, binlerce sınıflara gibi görüntüleri " Genel","Jersey"ve"Dishwasher".

`Inception v3 model` Olarak sınıflandırılan bir [derin konvolüsyonel sinir ağını](https://en.wikipedia.org/wiki/Convolutional_neural_network) ve eşleşen veya bazı etki alanlarına İnsan performansa aşan sabit visual tanıma görevleri, makul performans elde edebilirsiniz. Model/algoritması birden çok Araştırmacıları tarafından geliştirilmiş ve özgün kağıda tabanlı: ["Yeni mimarisi için görüntü işleme tarafından Szegedy yeniden değerlendirme", et. Al.](https://arxiv.org/abs/1512.00567)

Çünkü `Inception model` öncesi zaten içerdiği farklı görüntüleri binlerce üzerinde geliştirilen, [görüntü özellikleri](https://en.wikipedia.org/wiki/Feature_(computer_vision)) resim tanımlama için gerekli. Basit özellikleri (örneğin, kenarlar) alt görüntü özelliği katmanlarının tanır ve daha yüksek katmanları (şekiller gibi) daha karmaşık özelliklerden tanı. Son katmanı, zaten nasıl sınıflandırılacağıyla görüntüleri anlayan önceden eğitilen bir modelin ile başlatıyorsanız çünkü çok daha küçük veri kümesi karşı çalıştırılır. Modelinizi ikiden fazla kategorileri sınıflandırmak verdiğinden, bu örneği yer almaktadır. bir [çok sınıflı sınıflandırıcı](../resources/tasks.md#multiclass-classification). 

`TensorFlow` popüler derin öğrenme ve eğitim derin sinir ağı (ve genel sayısal hesaplamalar) etkinleştirir ve halinde uygulanır makine öğrenimi araç seti bir `transformer` ML.NET içinde. Bu öğretici için yeniden kullanıldığı `Inception model`.

Aşağıdaki diyagramda gösterildiği gibi .NET Core veya .NET Framework uygulamalarınızı ML.NET NuGet paketlerini bir başvuru ekleyin. ML.NET kapsar altında içerir ve yerel başvuruyor `TensorFlow` yükler mevcut bir kod yazmanızı sağlayan kitaplığı eğitilmiş `TensorFlow` Puanlama için model dosyası.  

![TensorFlow dönüştürme ML.NET mimarisi diyagramı](./media/image-classification/tensorflow-mlnet.png)

`Inception model` Binlerce kategoriler halinde görüntüleri sınıflandırmak için eğitilen ancak daha küçük bir kategori kümesini ve bu kategorilerin görüntülerde sınıflandırmak gerekir. Girin `transfer` parçası `transfer learning`. Aktarabilirsiniz `Inception model`'s tanıması ve özel görüntü sınıflandırıcınızı yeni sınırlı kategorilerini görüntülere sınıflandırma özelliği.  

 Son üç kategorileri kümesi kullanarak bu modeli katmanı yeniden eğitme oluşturacağız:

* Yiyecek
* Çocuğunun
* Gereç

Katman kullanan bir [ÇOKTERİMLİ Lojistik regresyon algoritması](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) kategoriyi mümkün olan en kısa sürede bulunacak. Bu algoritma, yanıt bir değer ölçeklendirerek kategoriyi ve diğerleri için sıfır değeri belirlemek için olasılıkları kullanma sınıflandırır.  

### <a name="dataset"></a>DataSet

İki veri kaynağı vardır: `.tsv` dosyası ve görüntü dosyaları.  `tags.tsv` Dosyada iki sütun: ilk olarak tanımlanan `ImagePath` ve ikincisi `Label` görüntüsüne karşılık gelen. Aşağıdaki örnek dosyası, bir başlık satırı yok ve şöyle görünür:

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

Eğitim ve test görüntüleri bir ZIP dosyası indireceksiniz varlıklar klasörlerinde yer alır. Bu görüntüler için Wikimedia Commons ait.
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), serbest medya depo.* Alınan 10:48, 17 Ekim 2018 tarihinden sonra:  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

### <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "TransferLearningTF" yazın ve ardından **Tamam** düğmesi.

2. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**. Tıklayarak **sürüm** açılan listesinde, select **0.10.0** paketini listede bulun ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz. Bu adımı yineleyin **Microsoft.ML.ImageAnalytics v0.10.0** ve **Microsoft.ML.TensorFlow v0.10.0**.

  > [!NOTE]
  > Bu öğreticide **Microsoft.ML v0.10.0**, **Microsoft.ML.ImageAnalytics v0.10.0**, ve **Microsoft.ML.TensorFlow v0.10.0**.

### <a name="prepare-your-data"></a>Verilerinizi hazırlama

1. İndirme [proje varlıklar dizin zip dosyasını](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)ve sıkıştırmasını açın.

2. Kopyalama `assets` içine dizin, *TransferLearningTF* proje dizini. Bu dizin ve alt dizinlerinde (dışında indirme ve bir sonraki adımda ekleme yeni model) verileri ve destek dosyaları içeren Bu öğretici için gerekli.

3. İndirme [başlangıcı modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)ve sıkıştırmasını açın.

4. İçeriğini kopyalayın `inception5h` dizin yalnızca sıkıştırması açılan içine, *TransferLearningTF* proje `assets\inputs-train\inception` dizin. Bu dizin, aşağıdaki görüntüde gösterildiği gibi model ve Bu öğretici için gerekli ek destek dosyalarını içerir:

   ![Yeni dizin içeriği](./media/image-classification/inception-files.png)

5. Her varlık dizin ve alt dizinleri seçip dosya Çözüm Gezgini'nde sağ **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

### <a name="create-classes-and-define-paths"></a>Yollarını tanımlamak ve sınıfları oluşturma

Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

Yolları çeşitli varlıklar ve genel değişkenleri tutmak için genel alanlar oluşturmak `LabelTokey`,`ImageReal`, ve `PredictedLabelValue`:

* `_assetsPath` varlıkları yolu vardır.
* `_trainTagsTsv` yolu için eğitim görüntü veri etiketleri tsv dosyası vardır.
* `_predictTagsTsv` yolu için tahmin görüntü veri etiketleri tsv dosyası vardır.
* `_trainImagesFolder` modeli eğitmek için kullanılan görüntülerin yolunu sahiptir.
* `_predictImagesFolder` eğitilen modelin sınıflandırılmaya görüntü sahiptir.
* `_inceptionPb` Yolun modelinizi yeniden kullanılabilmeleri için önceden eğitilmiş başlangıcı modeline sahiptir.
* `_inputImageClassifierZip` eğitilen model öğesinden yüklendiği yolu vardır.
* `_outputImageClassifierZip` eğitilen modelin kaydedildiği yolu vardır.
* `LabelTokey` olan `Label` bir anahtar ile eşlenen değeri.
* `ImageReal`  Tahmin edilen görüntü değeri içeren sütun.
* `PredictedLabelValue` Tahmin edilen etiket değeri içeren sütun.

Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollar ve diğer değişkenlerini belirtmek için:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturun. Yeni bir sınıf, projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *ImageData.cs*. Ardından, **Ekle** düğmesi.

    *ImageData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *ImageData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

Varolan sınıf tanımına kaldırın ve aşağıdaki kodu ekleyin `ImageData` sınıfının *ImageData.cs* dosyası:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

`ImageData` girdi görüntüsünün veri sınıfı ve aşağıdaki <xref:System.String> alanlar:

* `ImagePath` görüntü dosya adı içeriyor.
* `Label` görüntü etiketi için bir değer içeriyor.

Projeniz için yeni bir sınıf eklemek `ImagePrediction`:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *ImagePrediction.cs*. Ardından, **Ekle** düğmesi.

    *ImagePrediction.cs* dosyası Kod Düzenleyicisi'nde açılır. Hem de kaldırma `System.Collections.Generic` ve `System.Text` `using` deyimleri en üstündeki *ImagePrediction.cs*:

Varolan sınıf tanımına kaldırın ve olan aşağıdaki kodu ekleyin `ImagePrediction` çok sınıf *ImagePrediction.cs* dosyası:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

`ImagePrediction` Görüntü tahmin sınıftır ve aşağıdaki alanlar vardır:

* `Score` güvenle yüzdesi verilen görüntü sınıflandırması içerir.
* `PredictedLabelValue` Tahmin edilen görüntü sınıflandırma etiketi için bir değer içeriyor.

`ImagePrediction` eğitilen modelin sonra sınıf tahmin için kullanılır. Bunun bir `string` (`ImagePath`) görüntü yolu için. `Label` Modeli yeniden eğitme ve yeniden kullanmak için kullanılır. `PredictedLabelValue` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.

[MLContext sınıfı](xref:Microsoft.ML.MLContext) bir tüm ML.NET işlemleri için başlangıç noktası ve başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur. Bu, kavramsal olarak, benzer `DBContext` Entity Framework.

### <a name="initialize-variables-in-main"></a>Ana değişkenleri başlatma

Başlatma `mlContext` değişken ile yeni bir örneğini `MLContext`.  Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a>Varsayılan parametreleri için bir yapı oluşturma

Yeni modelde birkaç varsayılan parametre olarak geçirmenize gerek yok. Aşağıdaki kod ile kolay adlar için varsayılan parametre değerlerini hemen sonra eşlemek için bir yapı oluşturmak `Main()` yöntemi:

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Görüntü yardımcı programı yöntemi oluşturma

Daha fazla kez ve görüntü verileri ve ilgili Öngörüler yinelenen kodu istemiyorsanız eşleştirme ve görüntü. Eşleştirme ve görüntü ve tahmin sonuçlarını görüntüleyen işlemek için bir görüntü yardımcı programı yöntemi oluşturun.

`PairAndDisplayResults()` Yöntemi aşağıdaki görevleri yürütür:

* Veri ve raporlama için Öngörüler birleştirir.
* Tahmin edilen sonuçları görüntüler.

Oluşturma `PairAndDisplayResults()` yöntemi hemen sonrasına `InceptionSettings` yapısı, aşağıdaki kodu kullanarak:

```csharp
private static void PairAndDisplayResults(IEnumerable<ImageNetData> imageData, IEnumerable<ImageNetPrediction> imagePredictionData)
{

}
```

Tahmin edilen sonuçlarını görüntülemeden önce birleştirme `imageData` ve `imagePrediction` özgün birlikte görmek için `Image Path` tahmin edilen kategori ile. Aşağıdaki kod <xref:System.Linq.Enumerable.Zip%2A?displayProperty=nameWithType> yöntemini gerçekleşen, sağlamak için bu nedenle ilk satırı olarak bu ekleyin `PairAndDisplayResults()` yöntemi:

[!code-csharp[BuildImagePredictionPairs](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#BuildImagePredictionPairs)]

Birleştirilmiş göre `imageData` ve `imageData` bir sınıf kullanarak sonuçları görüntüleyebilirsiniz <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemi:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

Sizi ararız `PairAndDisplayResults()` sonraki iki yöntemle yöntemi.

### <a name="create-a-tsv-file-utility-method"></a>.Tsv dosya yardımcı program metodu oluştur

`ReadFromTsv()` Yöntemi aşağıdaki görevleri yürütür:

* Görüntü verisini okur `tags.tsv` dosya.
* Dosya yolu görüntü dosya adına ekler.
* Dosya verilerini bir IEnumerable yükler`ImageData` nesne.

Oluşturma `ReadFromTsv()` yöntemi hemen sonrasına `PairAndDisplayResults()` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

Aşağıdaki kod aracılığıyla ayrıştırır `tags.tsv` dosya yolu için resim dosya adı eklemek için dosya `ImagePath` özelliği ve yükler ve `Label` içine bir `ImageData` nesne. İlk satırı olarak ekleyin `ReadFromTsv()` yöntemi.  Tahmin sonuçlarını görüntülemek için tam dosya yolunu ihtiyacınız vardır.

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
ML.NET içinde üç ana kavramı vardır: [Veri](../basic-concepts-model-training-in-mldotnet.md#data), [dönüştürücüler](../basic-concepts-model-training-in-mldotnet.md#transformer), ve [Estimators](../basic-concepts-model-training-in-mldotnet.md#estimator).

## <a name="reuse-and-tune-pre-trained-model"></a>Yeniden kullanmak ve önceden eğitilmiş bir modeli ayarlama

Aşağıdaki çağrısı ekleyin `ReuseAndTuneInceptionModel()`yöntemi sonraki kod satırı olarak `Main()` yöntemi:

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

`ReuseAndTuneInceptionModel()` Yöntemi aşağıdaki görevleri yürütür:

* Verileri yükler
* Ayıklar ve verileri dönüştürür.
* TensorFlow modelini puanlar.
* (Çağırma sayısı) tabanlarını modeli.
* Model sonuçlarını görüntüler.
* Model değerlendirir.
* Model kaydeder.

Oluşturma `ReuseAndTuneInceptionModel()` yöntemi hemen sonrasına `InceptionSettings` yapısı ve hemen önce `PairAndDisplayResults()` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a>Verileri yükleme

ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.Data.DataView.IDataView). `IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur. Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne.

Kullanarak verileri yüklemek `MLContext.Data.ReadFromTextFile` sarmalayıcı. Sonraki satırda olarak aşağıdaki kodu ekleyin `ReuseAndTuneInceptionModel()` yöntemi:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a>Özellikleri ayıklayın ve verileri dönüştürme

Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir.  Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.

Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) verileri ve ne zaman, derin sinir ağları ile ilgilenen gerekir uyarlayabilirsiniz ağ tarafından beklenen biçimde görüntüleri. Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).

Eğitim ve değerlendirme sonra ile tahmin **etiket** sütun değerleri. Önceden eğitilmiş bir modeli kullandığınız gibi alanları yeni modeliyle eşlemek [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemi. Bu yöntem dönüştüren `Label` sayısal bir anahtar türü (`LabelTokey`) sütunu ve yeni veri kümesi sütun olarak ekleyin:  Bu ad `estimator` gibi de Eğitmeni kendisine eklemeniz. Sonraki kod satırı ekleyin:

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

Resim estimator kullanan önceden eğitilmiş işleme [derin sinir Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers özelliği ayıklama için. Derin sinir ağları ile ilgilenirken, beklenen ağ biçimi görüntülerin uyarlayın. Modelin beklenen biçime görüntü verilerini almak için kullandığınız görüntü dönüşümlerden nedeni budur:

1. `LoadImages`Dönüştürme görüntü bit eşlem türü olarak belleğe yüklenir.
2. `Resize` Dönüştürme olarak önceden eğitilmiş model tanımlı girdi görüntüsü genişliği ve yüksekliği görüntüleri yeniden boyutlandırır.
3. `ImagePixelExtractingEstimator` Dönüştürme giriş görüntülerden piksel ayıklar ve bunları sayısal vektörü dönüştürür.

Bu görüntü dönüşümler sonraki kod satırı ekleyin:

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

`TensorFlowTransform` Ayıklar belirtilen çıkış ( `Inception model`ait görüntü özellikleri `softmax2_pre_activation`) ve önceden eğitilmiş kullanarak bir veri kümesi puanlar `TensorFlow` modeli.

`softmax2_pre_activation` model, görüntüleri sınıfı belirleyen ile ait olduğu yardımcı olur. `softmax2_pre_activation` Görüntü kategorilerin her birine ve tüm bu olasılıklar olasılığını döndürür, en fazla 1 eklemeniz gerekir. Bu görüntü tek bir kategoriye ait olacak aşağıdaki örnekte gösterildiği gibi varsayılır:

| örneği         | Olasılık   |
| ------------- | ------------- |
| `Food`        |  0.001        |
| `Toy`         |  0.95         |
| `Appliance`   |  0,06         |

Append `TensorFlowTransform` için `estimator` aşağıdaki kod satırını ile:

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a>Eğitim algoritması seçin

Eğitim algoritması eklemek için çağrı `mlContext.MulticlassClassification.Trainers.LogisticRegression()` sarmalayıcı yöntemi.  `LogisticRegression` Eklenir `estimator` ve yeni görüntü özelliklerini kabul eder (`softmax2_pre_activation`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.  Eğitmeni ile aşağıdaki kodu ekleyin:

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

Harita gerekir `predictedlabel` için `predictedlabelvalue`:

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

`Fit()` Yöntemine sağlanan bir eğitim veri kümesi modelinizi eğitir. Yürütülmeden `Estimator` verileri dönüştürme ve eğitim ve uygulama tanımlarını döndürür geri olan eğitilen model bir `Transformer`. Modele uygun `Train` veri ve sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen model dönüş `ReuseAndTuneInceptionModel()` yöntemi:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, birden çok test veri kümesini girdi satırları sağlanan için Öngörüler sağlar.  Dönüştürme `Training` aşağıdakileri ekleyerek veri kod için `ReuseAndTuneInceptionModel()`:

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

Görüntü veri ve öngörü dönüştürme `DataViews` içine kesin türü belirtilmiş `IEnumerables` çiftine daha kolay görüntüleme için. Kullanım `MLContext.CreateEnumerable()` yöntemi, aşağıdaki kodu kullanarak yapmak için:

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

Çağrı `PairAndDisplayResults()` eşleştirin ve verilerinizi ve Öngörüler sonraki satırı olarak görüntülemek için yöntem `ReuseAndTuneInceptionModel()` yöntemi:

[!code-csharp[CallPairAndDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallPairAndDisplayResults1)]

Ayarlanırsa, tahmin sonra [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi:

* Model değerlendirir (tahmin edilen değeri ile gerçek veri kümesini karşılaştırır `Labels`).

* Model performansı ölçümlerini döndürür. 

Aşağıdaki kodu ekleyin `ReuseAndTuneInceptionModel()` yöntemi sonraki satır olarak:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

Aşağıdaki ölçümler için görüntü sınıflandırması değerlendirilir:

* `Log-loss` -bkz [günlük kaybı](../resources/glossary.md#log-loss). Sıfır olarak mümkün olduğunca yakın olmasını günlük zarar kullanmanız gerekir.

* `Per class Log-loss`. Sınıf günlük kaybı sıfır olarak mümkün olduğunca yakın olmasını istediğiniz.

Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

`mlContext.Model.Save` eğitilen model diğer .NET uygulamalarında tahminlerde bulunmak için kullanılabilecek bir .zip dosyası olarak ("varlıklar/çıkışları" klasöründe farklı olarak) kaydeder. Aşağıdaki kodu ekleyin `ReuseAndTuneInceptionModel()` yöntemi sonraki satır olarak:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#SaveModel)]

## <a name="classify-images-with-a-loaded-model"></a>Yüklenen bir model ile görüntü sınıflandırma

Aşağıdaki çağrısı ekleyin `ClassifyImages()` yöntemi sonraki kod satırı olarak `Main` yöntemi:

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

`ClassifyImages()` Yöntemi aşağıdaki görevleri yürütür:

* Modeli yükler.
* Okur. TSV dosyasına `IEnumerable`.
* Test verileri temel alan görüntü sınıflandırmaları tahmin eder.

Oluşturma `ClassifyImages()` yöntemi hemen sonrasına `ReuseAndTuneInceptionModel()` yöntemi ve hemen önce `PairAndDisplayResults()` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation)
{

}
```

İlk olarak, aşağıdaki kod ile daha önce kaydettiğiniz model yüklenemiyor:

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadModel)]

Çağrı `ReadFromTsv()` yöntemi oluşturmak için bir `IEnumerable<ImageData>` her biri için tam yolu içeren sınıf `ImagePath`. Bu dosya yolu, veri ve öngörü sonuçlarınızı eşleştirmeye ihtiyacınız vardır. Dönüştürmeniz gerekir `IEnumerable<ImageData>` sınıfının bir `IDataView` tahmin etmek için kullanacağınız. Sonraki iki satırlar halinde aşağıdaki kodu ekleyin `ClassifyImages()` yöntemi:

[!code-csharp[ReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTSV)]

Eğitim resmi verilerle daha önce yaptığınız gibi test görüntü kullanarak verileri kategori tahmin [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi. Aşağıdaki kodu ekleyin `ClassifyImages()` yöntemi tahminler elde etmek için ve dönüştürmek için `predictions` `IDataView` içine bir `IEnumerable` eşleştirme ve görüntüleme için:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

Eşleştirebilir ve Öngörüler ve test görüntü verilerini görüntülemek için çağırmak için aşağıdaki kodu ekleyin. `PairAndDisplayResults()` sonraki satırı olarak daha önce oluşturduğunuz yöntemi `ClassifyImages()` yöntemi:

[!code-csharp[CallPairAndDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallPairAndDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a>Yüklenen bir model ile tek bir görüntü sınıflandırma

Aşağıdaki çağrısı ekleyin `ClassifySingleImage()` yöntemi sonraki kod satırı olarak `Main` yöntemi:

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

`ClassifyImages()` Yöntemi aşağıdaki görevleri yürütür:

* Modeli yükler.
* Yükleri bir `ImageData` örneği.
* Test verileri temel alan görüntü sınıflandırması tahmin eder.

Oluşturma `ClassifySingleImage()` yöntemi hemen sonrasına `ClassifyImages()` yöntemi ve hemen önce `PairAndDisplayResults()` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation)
{

}
```

İlk olarak, aşağıdaki kod ile daha önce kaydettiğiniz model yüklenemiyor:

[!code-csharp[LoadModel2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadModel2)]

Oluşturma bir `ImageData` tek tam yol ve görüntü dosya adı içeren sınıf `ImagePath`. Sonraki satırları olarak aşağıdaki kodu ekleyin `ClassifySingleImage()` yöntemi:

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

[PredictionEngine sınıfı](xref:Microsoft.ML.PredictionEngine%602) tahmin verilerini tek bir örneğini gerçekleştirdiği API kolaylığıdır. [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütununu tahmin sağlar. Geçirmek `imageData` için `PredictionEngine` resim kategorisi aşağıdaki kodu ekleyerek tahmin etmek için `ClassifySingleImage()`:

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

Sonraki kod satırı olarak tahmin sonucu görüntülemek `ClassifySingleImage()` yöntemi:

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a>Sonuçlar

Önceki adımları tamamladıktan sonra Konsol uygulamanızı (Ctrl + F5) çalıştırın. Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.  Uyarı veya işlem iletileri görebilirsiniz, ancak bu iletiler anlaşılması için aşağıdaki sonuçları kaldırılmış olan.

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
=============== Save model to local file ===============
Model saved: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Loading model ===============
Model loaded: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Loading model ===============
Model loaded: C:\Tutorials\TransferLearningTF\bin\Debug\netcoreapp2.2\assets\outputs\imageClassifier.zip
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379
Press any key to continue . . .
```

Tebrikler! Şimdi başarıyla bir makine öğrenme modelinin görüntü sınıflandırması için önceden eğitilmiş yeniden kullanarak derlediğiniz `TensorFlow` ML.NET içindeki model.

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) depo.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> * Sorunu anlama
> * Yeniden kullanmak ve önceden eğitilmiş bir modeli ayarlama
> * Yüklenen bir model ile görüntü sınıflandırma

Bir genişletilmiş görüntü sınıflandırma örnek keşfetmek için Machine Learning örnekleri GitHub havuzuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/machinelearning-samples GitHub deposu](https://github.com/dotnet/machinelearning-samples/)
