---
title: 'Öğretici: Transfer öğrenmeyi kullanarak otomatik görsel denetim'
description: Bu öğretici, somut yüzeylerin görüntülerini çatlak veya çatlak olarak sınıflandırmak için görüntü algılama API'sini kullanarak ML.NET'da bir TensorFlow derin öğrenme modelini eğitmek için transfer öğreniminin nasıl kullanılacağını göstermektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2dfa3cdab9de47b55f7a3f73f0d6e9460390700c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76920097"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Öğretici: ML.NET Görüntü Sınıflandırma API ile transfer öğrenme kullanarak otomatik görsel denetim

Somut yüzeylerin görüntülerini çatlak veya kırılmamış olarak sınıflandırmak için transfer öğrenimini, önceden eğitilmiş tensorflow modelini ve ML.NET Görüntü Sınıflandırma API'sini kullanarak özel bir derin öğrenme modelini nasıl eğittiğizi öğrenin.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - ML.NET Resim Sınıflandırma API'si hakkında bilgi edinin
> - Önceden eğitilmiş modeli anlama
> - Özel bir TensorFlow görüntü sınıflandırma modelini eğitmek için transfer öğrenimini kullanma
> - Özel modelle görüntüleri sınıflandırma

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.

## <a name="image-classification-transfer-learning-sample-overview"></a>Görüntü sınıflandırma transferi öğrenme örneği genel bakış

Bu örnek, önceden eğitilmiş derin öğrenme TensorFlow modelini kullanarak görüntüleri sınıflandıran bir C# .NET Core konsol uygulamasıdır. Bu örneğin kodu GitHub'daki [dotnet/machinelearning-samples deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) bulunabilir.

## <a name="understand-the-problem"></a>Sorunu anlama

Görüntü sınıflandırması bir bilgisayar görme sorunudur. Görüntü sınıflandırması bir görüntüyü girdi olarak alır ve öngörülen sınıfa kategorilere ayırır. Görüntü sınıflandırmanın yararlı olduğu bazı senaryolar şunlardır:

- Yüz tanıma
- Duygu algılama
- Tıbbi tanı
- Yer işareti algılama

Bu öğretici, çatlaklardan zarar gören yapıları belirlemek için köprü güvertelerinin otomatik görsel denetimini gerçekleştirmek için özel bir görüntü sınıflandırma modeli eğitir.

## <a name="mlnet-image-classification-api"></a>ML.NET Görüntü Sınıflandırma API

ML.NET görüntü sınıflandırması gerçekleştirmenin çeşitli yollarını sağlar. Bu öğretici, Görüntü Sınıflandırma API'sini kullanarak aktarım öğrenimi uygular. Görüntü Sınıflandırma API' si, TensorFlow C++ API için C# bağlamaları sağlayan düşük seviyeli bir kitaplık olan [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET)kullanır.

## <a name="what-is-transfer-learning"></a>Transfer öğrenme nedir?

Transfer öğrenme başka bir ilgili sorun bir problem çözme elde edilen bilgi geçerlidir.

Derin öğrenme modelini sıfırdan eğitmek için çeşitli parametreler, büyük miktarda etiketli eğitim verileri ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) gerekir. Transfer öğrenimi ile birlikte önceden eğitilmiş bir model kullanmak, eğitim sürecini kısayolla kesmenize olanak tanır.

## <a name="training-process"></a>Eğitim süreci

Görüntü Sınıflandırma API önceden eğitilmiş TensorFlow modeli yükleyerek eğitim sürecini başlatır. Eğitim süreci iki adımdan oluşur:

1. Darboğaz fazı
2. Eğitim aşaması

![Eğitim Adımları](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Darboğaz fazı

Darboğaz aşamasında, eğitim görüntüleri kümesi yüklenir ve piksel değerleri önceden eğitilmiş modelin dondurulmuş katmanları için giriş veya özellik olarak kullanılır. Dondurulmuş katmanlar, altboğaz katmanı olarak gayri resmi olarak bilinen sondan bir önceki katmana kadar sinir ağındaki tüm katmanları içerir. Bu katmanlar üzerinde eğitim oluşmayacağı ve işlemler geçiş olduğundan bu katmanlara dondurulmuş olarak adlandırılır. Bir modelin farklı sınıflar arasında ayrım lar yaptığı alt düzey desenlerin hesaplandığı bu donmuş katmanlarda. Katman sayısı ne kadar büyükse, bu adım hesaplama açısından o kadar yoğundur. Neyse ki, bu tek seferlik bir hesaplama olduğundan, sonuçlar önbelleğe alınabilir ve farklı parametrelerle deneme yaparken daha sonraki çalıştırmalarda kullanılabilir.

### <a name="training-phase"></a>Eğitim aşaması

Darboğaz aşamasından çıkış değerleri hesaplandıktan sonra, modelin son katmanını yeniden eğitmek için giriş olarak kullanılır. Bu işlem yinelemelidir ve model parametreleri tarafından belirtilen kez çalışır. Her çalıştırma sırasında, kayıp ve doğruluk değerlendirilir. Daha sonra, kaybı en aza indirmek ve doğruluğu en üst düzeye çıkarmak amacıyla modeli geliştirmek için uygun ayarlamalar yapılır. Eğitim tamamlandıktan sonra, iki model biçimi çıktı. Bunlardan biri modelin `.pb` sürümü ve diğer modelin `.zip` ML.NET seri leştirilmiş sürümüdür. ML.NET tarafından desteklenen ortamlarda çalışırken, modelin `.zip` sürümünün kullanılması önerilir. Ancak, ML.NET desteklenmiyor ortamlarda `.pb` sürümü kullanma seçeneğiniz vardır.

## <a name="understand-the-pretrained-model"></a>Önceden eğitilmiş modeli anlama

Bu öğreticide kullanılan önceden eğitilmiş model, Bakiye Ağı (ResNet) v2 modelinin 101 katmanlı varyantıdır. Orijinal model, görüntüleri bin kategoriye sınıflandırmak için eğitildi. Model, 224 x 224 boyutundaki bir görüntüyü girdi olarak alır ve eğitildiği sınıfların her biri için sınıf olasılıklarını çıkarır. Bu modelin bir parçası iki sınıf arasında öngörüler yapmak için özel görüntüler kullanarak yeni bir model eğitmek için kullanılır.

## <a name="create-console-application"></a>Konsol uygulaması oluşturma

Artık transfer öğrenimi ve Görüntü Sınıflandırma API'si hakkında genel bir anlayışa sahip olduğunuza göre, uygulamayı oluşturmanın zamanı gelmiştir.

1. "DeepLearning_ImageClassification_Binary" adlı bir **C# .NET Core Konsol Uygulaması** oluşturun.
1. **1.4.0** NuGet Paketini **Microsoft.ML** yükleyin:
    1. Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.
    1. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin.
    1. **Gözat** sekmesini seçin.
    1. Yayın **aet'i ekle** onay kutusunu işaretleyin.
    1. **Microsoft.ML**arayın.
    1. **Yükle** düğmesini seçin.
    1. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.
    1. **Microsoft.ML.Vision** sürüm **1.4.0**, **SciSharp.TensorFlow.Redist** sürüm **1.15.0**ve **Microsoft.ML.ImageAnalytics** sürüm **1.4.0** NuGet paketleri için bu adımları yineleyin.

### <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

> [!NOTE]
> Bu öğretici için veri setleri Maguire, Marc vardır; Dorafshan, Sattar; ve Thomas, Robert J., "SDNET2018: Makine öğrenimi uygulamaları için somut bir çatlak görüntü veri seti" (2018). Tüm Datasets göz atın. Kağıt 48. https://digitalcommons.usu.edu/all_datasets/48

SDNET2018, çatlak ve çatlamış olmayan beton yapılar (köprü güverteleri, duvarlar ve kaldırım) için ek açıklamalar içeren bir görüntü veri kümesidir.

![SDNET2018 dataset köprü güverte örnekleri](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Veriler üç alt dizin halinde düzenlenir:

- D köprü güverte görüntüleri içerir
- P kaldırım görüntüleri içerir
- W duvar görüntüleri içerir

Bu alt dizinlerin her biri iki ek önceden belirlenmiş alt dizin içerir:

- C, çatlak yüzeyler için kullanılan önektir.
- U, kırılmamış yüzeyler için kullanılan önektir

Bu eğitimde, yalnızca köprü güverte görüntüleri kullanılır.

1. Veri [kümesini](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) indirin ve zip'i indirin.
1. Veri kümesi dosyalarınızı kaydetmek için projenizde "varlıklar" adlı bir dizin oluşturun.
1. *CD* ve *UD* alt dizilişlerini son zamanlarda fermuarsız dizinden *varlıklar* dizinine kopyalayın.

### <a name="create-input-and-output-classes"></a>Giriş ve çıktı sınıfları oluşturma

1. *Program.cs* dosyasını açın ve `using` dosyanın üst kısmındaki varolan ifadeleri aşağıdakilerle değiştirin:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. `Program` *Program.cs'daki*sınıfın altında , `ImageData`adı verilen bir sınıf oluşturun. Bu sınıf, başlangıçta yüklenen verileri temsil etmek için kullanılır.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData`aşağıdaki özellikleri içerir:

    - `ImagePath`görüntünün depolandığı tam nitelikli yoldur.
    - `Label`görüntünün ait olduğu kategoridir. Bu tahmin değeridir.

1. Giriş ve çıktı verileriniz için sınıflar oluşturun

    1. `ImageData` Sınıfın altında, giriş verilerinizin şemasını yeni bir sınıfta `ModelInput`tanımlayın.

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput`aşağıdaki özellikleri içerir:

        - `Image`resmin `byte[]` temsilidir. Model, görüntü verilerinin eğitim için bu tür olmasını bekler.
        - `LabelAsKey`'nin `Label`sayısal temsilidir.
        - `ImagePath`görüntünün depolandığı tam nitelikli yoldur.
        - `Label`görüntünün ait olduğu kategoridir. Bu tahmin değeridir.

        Sadece `Image` `LabelAsKey` ve modeli eğitmek ve tahminler yapmak için kullanılır. `ImagePath` Ve `Label` özellikleri, özgün resim dosya adı ve kategorisine erişmek için kolaylık sağlamak için tutulur.

    1. Daha sonra, `ModelInput` sınıfın altında, çıktı verilerinizin şemasını yeni `ModelOutput`bir sınıfta tanımlar.

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput`aşağıdaki özellikleri içerir:

        - `ImagePath`görüntünün depolandığı tam nitelikli yoldur.
        - `Label`görüntünün ait olduğu orijinal kategoridir. Bu tahmin değeridir.
        - `PredictedLabel`model tarafından öngörülen değerdir.

        Benzer `ModelInput`, model `PredictedLabel` tarafından yapılan tahmin içerdiğinden sadece öngörüler yapmak için gereklidir. Ve `ImagePath` `Label` özellikleri, özgün resim dosyası adı ve kategorisine erişmek için kolaylık sağlamak için korunur.

### <a name="create-workspace-directory"></a>Çalışma alanı dizini oluşturma

Eğitim ve doğrulama verileri sık sık değişmediğinde, daha fazla çalıştırma için hesaplanan darboğaz değerlerini önbelleğe almak iyi bir uygulamadır.

1. Projenizde, hesaplanan darboğaz *workspace* değerlerini ve `.pb` modelin sürümünü depolamak için çalışma alanı adı verilen yeni bir dizin oluşturun.

### <a name="define-paths-and-initialize-variables"></a>Yolları tanımlayın ve değişkenleri başlatma

1. Yöntemin `Main` içinde, varlıklarınızın konumunu, hesaplanmış darboğaz `.pb` değerlerini ve modelin sürümünü tanımlayın.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. `mlContext` [MlContext](xref:Microsoft.ML.MLContext)yeni bir örnek ile değişkeni başlatma.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    [MLContext](xref:Microsoft.ML.MLContext) sınıfı tüm ML.NET işlemleri için bir başlangıç noktasıdır ve mlContext'ı başlatmak, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur. Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.

## <a name="load-the-data"></a>Verileri yükleme

### <a name="create-data-loading-utility-method"></a>Veri yükleme yardımcı programı yöntemi oluşturma

Görüntüler iki alt diziniçinde depolanır. Verileri yüklemeden önce, `ImageData` nesnelerin listesine biçimlendirilmesi gerekir. Bunu yapmak için, `LoadImagesFromDirectory` yöntemin `Main` altında yöntem oluşturun.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. Alt `LoadImagesDirectory` dizinlerden tüm dosya yollarını almak için aşağıdaki kodu ekleyin:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Ardından, bir `foreach` deyim kullanarak dosyaların her birini yineleyin.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. İfadenin `foreach` içinde, dosya uzantılarının destekleniyi denetleyin. Görüntü Sınıflandırma API JPEG ve PNG biçimlerini destekler.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Sonra, dosya için etiket alın. `useFolderNameAsLabel` Parametre `true`ayarlanmışsa, dosyanın kaydedildiği ana dizini etiket olarak kullanılır. Aksi takdirde, etiketin dosya adının veya dosya adının öneki olmasını bekler.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Son olarak, yeni `ModelInput`bir örnek oluşturun.

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Verileri hazırlama

1. Yöntemde, `Main` eğitim için `LoadFromDirectory` kullanılan görüntülerin listesini almak için yardımcı program yöntemini kullanın.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Ardından, görüntüleri yöntemi [`IDataView`](xref:Microsoft.ML.IDataView) kullanarak [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yükleyin.

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Veriler dizinlerden okunduğu sırada yüklenir. Verileri dengelemek için [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) yöntemi kullanarak karıştırın.

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Makine öğrenimi modelleri girdinin sayısal formatta olmasını bekler. Bu nedenle, bazı ön işleme eğitim den önce veri üzerinde yapılması gerekir. Oluşan [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) bir oluşturun [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) ve `LoadRawImageBytes` dönüştürür. Dönüştürme `MapValueToKey` `Label` sütundaki kategorik değeri alır, sayısal `KeyType` bir değere dönüştürür ve yeni bir `LabelAsKey`sütunda depolar. Eğitim `LoadImages` için görüntüleri `ImagePath` yüklemek için `imageFolder` parametre ile birlikte sütundaki değerleri alır.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. Verileri, [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) önceden işlenmiş verileri `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) içeren bir [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) [`IDataView`](xref:Microsoft.ML.IDataView) yöntemi döndüren yönteme uygulamak için yöntemi kullanın.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Bir modeli eğitmek için, bir eğitim veri kümesinin yanı sıra doğrulama veri kümesine sahip olmak önemlidir. Model eğitim seti üzerinde eğitilir. Görünmeyen veriler üzerinde ne kadar iyi öngörüler yapar doğrulama kümesine karşı performans ile ölçülür. Bu performansın sonuçlarına bağlı olarak, model geliştirmek için öğrendiklerine ayarlamalar yapar. Doğrulama kümesi, özgün veri kümenizi bölmekten veya bu amaç için ayrılmış başka bir kaynaktan gelebilir. Bu durumda, önceden işlenmiş veri kümesi eğitim, doğrulama ve test kümelerine ayrılır.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    Yukarıdaki kod örneği iki bölme gerçekleştirir. İlk olarak, önceden işlenmiş veriler bölünür ve %70'i eğitim için kullanılırken, geri kalan %30'u doğrulama için kullanılır. Daha sonra, %30 doğrulama kümesi doğrulama için %90 ve test için %10'un kullanıldığı doğrulama ve test kümelerine ayrılır.

    Bu veri bölümlerinin amacı hakkında düşünmenin bir yolu bir sınav almaktır. Sınava çalışırken, sınavdaki kavramları kavramak için notlarınızı, kitaplarınızı veya diğer kaynaklarınızı gözden geçirin. Tren seti bunun için var. Daha sonra, bilginizi doğrulamak için sahte bir sınava girebilirsiniz. Doğrulama kümesi nin kullanışlı olduğu yer burasıdır. Gerçek sınava girmeden önce kavramları iyi kavrayıp kavrayamadığınızı kontrol etmek istiyorsunuz. Bu sonuçlara dayanarak, neyi yanlış anladığınızı veya iyi anlamadığınızı not alır ve gerçek sınav için gözden geçirirken değişikliklerinizi dahil eleştirirsiniz. Sonunda sınava gireceksin. Bu, test kümesinin ne için kullanıldığıdır. Sınavda yer alan soruları hiç görmediniz ve şimdi eğitim ve doğrulamadan öğrendiklerinizi elinizdeki göreve uygulamak için kullanıyorsunuz.

1. Bölümleri tren, doğrulama ve test verileri için kendi değerlerini atayın.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Eğitim boru hattını tanımlayın

Model eğitimi birkaç adımdan oluşur. İlk olarak, Görüntü Sınıflandırma API modeli eğitmek için kullanılır. Daha sonra, `PredictedLabel` sütundaki kodlanmış etiketler `MapKeyToValue` dönüştürme kullanılarak özgün kategorik değerine dönüştürülür.

1. Bir `ImageClassificationTrainer`.

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    Bir `ImageClassificationTrainer` birkaç isteğe bağlı parametre alır:

    - `FeatureColumnName`model için giriş olarak kullanılan sütundur.
    - `LabelColumnName`tahmin değeri için sütundur.
    - `ValidationSet`doğrulama [`IDataView`](xref:Microsoft.ML.IDataView) verilerini içerendir.
    - `Arch`önceden eğitilmiş model mimarilerinden hangilerinin kullanılacağını tanımlar. Bu öğretici, ResNetv2 modelinin 101 katmanlı varyantını kullanır.
    - `MetricsCallback`eğitim sırasında ilerlemeyi izlemek için bir işlev bağlar.
    - `TestOnTrainSet`doğrulama kümesi olmadığında performansı eğitim kümesine göre ölçmesini söyler.
    - `ReuseTrainSetBottleneckCachedValues`sonraki çalıştırmalarda önbelleğe alınan değerleri darboğaz aşamasından kullanıp kullanmayacağını modele bildirir. Darboğaz aşaması, ilk kez gerçekleştirilinin hesaplama aşamasında olan tek seferlik bir geçiş hesaplamasIdır. Eğitim verileri değişmezse ve farklı sayıda çağ veya toplu iş boyutu kullanarak deneme yapmak istiyorsanız, önbelleğe alınan değerleri kullanmak bir modeli eğitmek için gereken süreyi önemli ölçüde azaltır.
    - `ReuseValidationSetBottleneckCachedValues``ReuseTrainSetBottleneckCachedValues` yalnızca bu durumda doğrulama veri kümesi için benzer.
    - `WorkspacePath`açılan darboğaz değerlerinin ve `.pb` modelin sürümünün depolanacağı dizin tanımlar.

1. [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) Hem ve `mapLabelEstimator` `ImageClassificationTrainer`.

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. Modelinizi [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) eğitmek için yöntemi kullanın.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Modeli kullanma

Artık modelinizi eğittiğinize göre, görüntüleri sınıflandırmak için onu kullanma nın zamanı gelmiştir.

Yöntemin `Main` altında, konsolda tahmin `OutputPrediction` bilgilerini görüntülemek için çağrılan yeni bir yardımcı program yöntemi oluşturun.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Tek bir görüntüyü sınıflandırma

1. Tek bir görüntü `ClassifySingleImage` tahmini `Main` yapmak ve çıktı vermek için yöntemin altına çağrılan yeni bir yöntem ekleyin.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Yöntemin [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) içini `ClassifySingleImage` oluşturun. Bu, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde bir tahmin gerçekleştirmenize ve geçiş yapmanızı sağlayan bir kolaylık API'sidir.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. `ModelInput` Tek bir örne erişmek `data` [`IDataView`](xref:Microsoft.ML.IDataView) için, yöntemi [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) kullanarak dönüştürün [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) ve ardından ilk gözlemi alın.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. Görüntüyü [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) sınıflandırmak için yöntemi kullanın.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. Yöntemle konsola tahmin `OutputPrediction` çıktı.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. Yöntemin `Main` içinde, `ClassifySingleImage` test görüntüleri kümesini kullanarak arayın.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Birden çok görüntüyü sınıflandırma

1. Birden çok görüntü `ClassifyImages` öngörüsü yapmak ve çıktı vermek için yöntemin `ClassifySingleImage` altına çağrılan yeni bir yöntem ekleyin.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. Yöntemi [`IDataView`](xref:Microsoft.ML.IDataView) kullanarak öngörüleri içeren [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) bir oluştur. `ClassifyImages` Yöntemin içine aşağıdaki kodu ekleyin.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. Öngörüler üzerinde tekrarlamak için, `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntem kullanarak dönüştürmek ve daha sonra ilk 10 gözlemler olsun.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Tahminler için orijinal ve öngörülen etiketleri yineleyin ve çıktıedin.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Son olarak, `Main` yöntemin `ClassifyImages` içinde, görüntülerin test kümesini kullanarak arayın.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Konsol uygulamanızı çalıştırın. Çıktı aşağıdakine benzer olmalıdır. Uyarılar veya iletileri işleme görebilirsiniz, ancak bu iletiler netlik için aşağıdaki sonuçlardan kaldırılmıştır. Kısalık için, çıkış yoğunlaştırılmış tır.

**Darboğaz fazı**

Görüntüler görüntü adı olarak yüklendiğinden, görüntü adı `byte[]` için hiçbir değer yazdırılmaz, bu nedenle görüntü adı görüntülenecek bir ad yoktur.

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

**Eğitim aşaması**

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

**Görüntü çıktısını sınıflandırma**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

*7001-220.jpg* görüntü nün incelenmesi üzerine, aslında kırık olmadığını görebilirsiniz.

![Tahmin için kullanılan SDNET2018 dataset görüntüsü](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Tebrikler! Şimdi başarılı görüntüleri sınıflandırmak için derin bir öğrenme modeli inşa ettik.

### <a name="improve-the-model"></a>Modeli geliştirin

Modelinizin sonuçlarından memnun değilseniz, aşağıdaki yaklaşımlardan bazılarını deneyerek performansını artırmayı deneyebilirsiniz:

- **Daha Fazla Veri**: Bir model ne kadar çok örnekten öğrenirse, o kadar iyi performans gösterir. [SDNET2018 veri setinin](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) tamamını indirin ve eğitmek için kullanın.
- **Verileri artırmak**: Verilere çeşitlilik katmak için yaygın bir teknik, görüntü alarak ve farklı dönüşümler (döndürme, çevirme, kaydırma, kırpma) uygulayarak verileri artırmaktır. Bu, modelden öğrenilen daha çeşitli örnekler ekler.
- **Daha uzun süre tren**: Ne kadar uzun süre antrenman yaptığınızda, model o kadar ayarlı olacaktır. Dönem sayısını artırmak modelinizin performansını artırabilir.
- **Hiper parametrelerle denemeler**: Bu eğitimde kullanılan parametrelere ek olarak, diğer parametreler performansı artırmak için ayarlanabilir. Her çağdan sonra modelde yapılan güncelleştirmelerin büyüklüğünü belirleyen öğrenme oranının değiştirilmesi performansı artırabilir.
- **Farklı bir model mimarisi kullanın**: Verilerinizin nasıl göründüğüne bağlı olarak, özelliklerini en iyi şekilde öğrenebilecek model farklı olabilir. Modelinizin performansından memnun değilseniz, mimariyi değiştirmeyi deneyin.

### <a name="additional-resources"></a>Ek Kaynaklar

- [Derin Öğrenme vs Makine Öğrenme](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, transfer öğrenimi, önceden eğitilmiş görüntü sınıflandırma TensorFlow modeli ve ML.NET Görüntü Sınıflandırma API'sini kullanarak beton yüzeylerin görüntülerini çatlak veya kırılmamış olarak sınıflandırmak için özel bir derin öğrenme modeli oluşturmayı öğrendiniz.

Daha fazla bilgi edinmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Nesne Algılama](object-detection-onnx.md)
