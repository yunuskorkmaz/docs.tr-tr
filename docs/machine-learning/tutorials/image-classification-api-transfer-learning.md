---
title: 'Öğretici: aktarım öğrenimi kullanarak otomatikleştirilmiş görsel inceleme'
description: Bu öğreticide, somut yüzeylerin görüntülerini kırçıkarılan veya Kırçıkmıyor olarak sınıflandırmak için görüntü algılama API 'sini kullanarak ML.NET ' deki bir TensorFlow derin öğrenme modelini nasıl eğitecağın nasıl kullanılacağı gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 17fbb8c6714f3af47c0b554aec2c53c8046021bb
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803748"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Öğretici: ML.NET görüntü sınıflandırma API 'SI ile aktarım öğrenimini kullanarak otomatikleştirilmiş görsel inceleme

Özel derin öğrenme modelini, aktarım öğrenimi, önceden eğitilen bir TensorFlow modeli ve ML.NET görüntü sınıflandırma API 'sini kullanarak, somut yüzeylerin görüntülerini kırıllanmış veya kırılk olarak sınıflandırmasına nasıl eğeceğinizi öğrenin.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - ML.NET görüntü sınıflandırma API 'SI hakkında bilgi edinin
> - Önceden eğitilen modeli anlama
> - Özel bir TensorFlow görüntü sınıflandırma modelini eğitme için aktarım öğrenimi kullanma
> - Özel model ile görüntüleri sınıflandır

## <a name="prerequisites"></a>Ön koşullar

- [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya üzeri ya da visual Studio 2017 sürüm 15,6 veya üzeri, ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="image-classification-transfer-learning-sample-overview"></a>Görüntü sınıflandırma aktarım öğrenme örneğine genel bakış

Bu örnek, görüntüleri önceden eğitilen bir öğrenme TensorFlow modeli kullanarak sınıflandırın bir C# .NET Core konsol uygulamasıdır. Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) bulunabilir.

## <a name="understand-the-problem"></a>Sorunu anlama

Görüntü sınıflandırması bir bilgisayar vizyonu sorunudur. Görüntü sınıflandırması bir görüntüyü giriş olarak alır ve önceden tanımlanmış bir sınıfa kategorilere ayırır. Görüntü sınıflandırmasının kullanışlı olduğu bazı senaryolar şunlardır:

- Yüz tanıma
- Duygu algılama
- Tıp tanısı
- Yer işareti algılama

Bu öğreticide, bir özel görüntü sınıflandırma modeli sunarak, her ne kadar bozuk olan yapıları belirlemek için köprü oluşturma işlemlerini otomatik görsel denetlemesi gerçekleştirebilir.

## <a name="mlnet-image-classification-api"></a>ML.NET resim sınıflandırması API 'SI

ML.NET, görüntü sınıflandırması yapmak için çeşitli yollar sağlar. Bu öğretici, görüntü sınıflandırması API 'sini kullanarak Aktarım öğrenimini uygular. Görüntü sınıflandırma API 'si, TensorFlow C++ API 'SI için C# bağlamaları sağlayan alt düzey bir kitaplık olan [TensorFlow.net](https://github.com/SciSharp/TensorFlow.NET)kullanımını sağlar.

## <a name="what-is-transfer-learning"></a>Aktarım öğrenimi nedir?

Aktarım öğrenimi, bir problemi bir sorunla ilgili diğer soruna çözüm olarak elde edilen bilgileri uygular.

Derin bir öğrenme modelini sıfırdan eğitmek için birkaç parametre, büyük miktarda etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir. Aktarım öğrenimi ile önceden eğitilen bir modelin kullanılması, eğitim sürecini kısayollara eklemenize olanak tanır.

## <a name="training-process"></a>Eğitim süreci

Görüntü sınıflandırma API 'SI, önceden eğitilen bir TensorFlow modeli yükleyerek eğitim sürecini başlatır. Eğitim süreci iki adımdan oluşur:

1. Performans sorunu aşaması
2. Eğitim aşaması

![Eğitim adımları](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>Performans sorunu aşaması

Performans sorunu aşamasında, eğitim görüntüleri kümesi yüklenir ve piksel değerleri, önceden eğitilen modelin dondurulmuş katmanları için giriş veya özellikler olarak kullanılır. Dondurulmuş katmanlar, sinir ağındaki tüm katmanları, tıkanıklık katmanı olarak bilinen Penultimate katmanına kadar içerir. Bu katmanlarda hiçbir eğitim gerçekleşmediğinden ve işlemler doğrudan geçiş yaptığından, bu katmanlar dondurulmuş olarak adlandırılır. Farklı sınıflar arasında ayrım yapan bir modele yardımcı olan alt düzey desenlerin hesaplandığı, Bu dondurulmuş katmanlarda. Katman sayısı arttıkça bu adım daha yoğun bir işlemdir. Neyse ki, bu bir kerelik hesaplama olduğundan, sonuçlar önbelleğe alınabilir ve daha sonra farklı parametrelerle denemeler yaparken çalışır.

### <a name="training-phase"></a>Eğitim aşaması

Performans sorunlarına neden olan çıkış değerleri hesaplandıktan sonra, modelin son katmanını yeniden eğitmek için giriş olarak kullanılırlar. Bu işlem yinelemeli ve model parametreleri tarafından belirtilen sayıda kez çalıştırılır. Her çalıştırma sırasında, kayıp ve doğruluk değerlendirilir. Daha sonra, kaybı en aza indirmek ve doğruluğu en üst düzeye çıkarmak için modeli geliştirmek üzere uygun ayarlamalar yapılır. Eğitim tamamlandığında, iki model biçimi çıkış olur. Bunlardan biri `.pb` modelin sürümüdür ve diğeri ise `.zip` modelin ml.net serileştirilmiş sürümüdür. ML.NET tarafından desteklenen ortamlarda çalışırken, `.zip` modelin sürümünün kullanılması önerilir. Ancak, ML.NET 'in desteklenmediği ortamlarda sürümü kullanma seçeneğiniz vardır `.pb` .

## <a name="understand-the-pretrained-model"></a>Önceden eğitilen modeli anlama

Bu öğreticide kullanılan önceden eğitilen model, kalan ağ (ResNet) v2 modelinin 101 katmanlı varyantıdır. Orijinal model resimleri bin kategoride sınıflandırmakta tasarlanmıştır. Model, 224 x 224 boyutundaki bir görüntüyü giriş olarak alır ve eğitilen sınıfların her biri için sınıf olasılıkların çıkışını çıkarır. Bu modelin bir parçası, iki sınıf arasında tahmine dayalı hale getirmek için özel görüntüler kullanarak yeni bir modeli eğitme için kullanılır.

## <a name="create-console-application"></a>Konsol uygulaması oluşturma

Aktarım öğrenimine ve görüntü sınıflandırma API 'sine ilişkin genel bir bilgiye sahip olduğunuza göre, uygulamayı derlemek zaman alabilir.

1. "DeepLearning_ImageClassification_Binary" adlı bir **C# .NET Core konsol uygulaması** oluşturun.
1. **Microsoft.ml** NuGet paketini yükler:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.
    1. Paket kaynağı olarak "nuget.org" öğesini seçin.
    1. **Gözat** sekmesini seçin.
    1. **Ön sürümü dahil et** onay kutusunu işaretleyin.
    1. **Microsoft.ml**için arama yapın.
    1. **Install** düğmesini seçin.
    1. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.
    1. **Microsoft. ml. Vision**, **SciSharp. TensorFlow. Redist**ve **Microsoft. ml. ımageanalytics** NuGet paketleri için bu adımları yineleyin.

### <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

> [!NOTE]
> Bu öğreticinin veri kümeleri Maguire, Marc; adresinden Dorafshan, Sattar; ve Thomas, Robert J., "SDNET2018: Machine Learning uygulamaları için somut bir görüntü veri kümesi" (2018). Tüm veri kümelerine gözatamazsınız. Kağıt 48. <https://digitalcommons.usu.edu/all_datasets/48>

SDNET2018, kırılmamış ve kırılamayan somut yapılar (köprü kümeleri, duvarlar ve Payalar) için ek açıklamalar içeren bir görüntü veri kümesidir.

![SDNET2018 veri kümesi Köprüsü destesi örnekleri](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

Veriler üç alt dizine göre düzenlenir:

- D köprü destesi görüntülerini içerir
- P paizni görüntülerini içerir
- W duvar görüntülerini içerir

Bu alt dizinlerin her biri, iki ek ön eki içerir:

- C, kırçıkarılan yüzeyler için kullanılan önekidir
- U, kırçıkarılan yüzeyler için kullanılan önekidir

Bu öğreticide, yalnızca köprü destesi görüntüleri kullanılır.

1. [Veri kümesini](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) indirin ve sıkıştırmayı açın.
1. Veri kümesi dosyalarınızı kaydetmek için projenizde "varlıklar" adlı bir dizin oluşturun.
1. Son daraltılmış dizinden *CD* ve *ud* alt dizinlerini *varlıklar* dizinine kopyalayın.

### <a name="create-input-and-output-classes"></a>Giriş ve çıkış sınıfları oluşturma

1. *Program.cs* dosyasını açın ve `using` dosyanın en üstündeki mevcut deyimlerini aşağıdaki gibi değiştirin:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. `Program` *Program.cs*içindeki sınıfının altında adlı bir sınıf oluşturun `ImageData` . Bu sınıf başlangıçta yüklenen verileri temsil etmek için kullanılır.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData`aşağıdaki özellikleri içerir:

    - `ImagePath`, görüntünün depolandığı tam yoldur.
    - `Label`, görüntünün ait olduğu kategorisidir. Tahmin edilecek değer budur.

1. Giriş ve çıkış verileriniz için sınıflar oluşturma

    1. Sınıfının altında `ImageData` , giriş verilerinizin şemasını adlı yeni bir sınıfta tanımlayın `ModelInput` .

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput`aşağıdaki özellikleri içerir:

        - `Image``byte[]`görüntünün gösterimidir. Model, yansıma verilerinin eğitim için bu türden olmasını bekler.
        - `LabelAsKey`, öğesinin sayısal gösterimidir `Label` .
        - `ImagePath`, görüntünün depolandığı tam yoldur.
        - `Label`, görüntünün ait olduğu kategorisidir. Tahmin edilecek değer budur.

        Yalnızca `Image` ve `LabelAsKey` modeli eğitmek ve tahmin yapmak için kullanılır. `ImagePath`Ve `Label` özellikleri özgün görüntü dosyası adına ve kategorisine erişmek için kolaylık sağlamak üzere tutulur.

    1. Ardından, sınıfının altında `ModelInput` , çıkış verilerinizin şemasını adlı yeni bir sınıfta tanımlayın `ModelOutput` .

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput`aşağıdaki özellikleri içerir:

        - `ImagePath`, görüntünün depolandığı tam yoldur.
        - `Label`görüntünün ait olduğu özgün kategorisidir. Tahmin edilecek değer budur.
        - `PredictedLabel`, model tarafından tahmin edilen değerdir.

        Benzer şekilde `ModelInput` , yalnızca, `PredictedLabel` model tarafından yapılan tahminleri içerdiğinden tahmin yapmak için gereklidir. `ImagePath`Ve `Label` özellikleri özgün görüntü dosyası adına ve kategorisine erişmek için kolaylık sağlamak üzere tutulur.

### <a name="create-workspace-directory"></a>Çalışma alanı dizini oluştur

Eğitim ve doğrulama verileri sıklıkla değişmediğinde, daha fazla çalıştırma için hesaplanan darboğazal değerlerini önbelleğe almak iyi bir uygulamadır.

1. Projenizde, hesaplanan performans sorunu değerlerini ve modelin sürümünü depolamak için *çalışma alanı* adlı yeni bir dizin oluşturun `.pb` .

### <a name="define-paths-and-initialize-variables"></a>Yolları tanımlama ve değişkenleri başlatma

1. Yöntemi içinde `Main` varlıklarınızın konumunu, hesaplanan performans sorunu değerlerini ve `.pb` modelin sürümünü tanımlayın.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. `mlContext`Değişkeni yeni bir [mlcontext](xref:Microsoft.ML.MLContext)örneğiyle başlatın.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    [Mlcontext](xref:Microsoft.ML.MLContext) sınıfı tüm ml.NET işlemleri için bir başlangıç noktasıdır ve mlcontext 'i başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal olarak da benzerdir `DBContext` .

## <a name="load-the-data"></a>Verileri yükleme

### <a name="create-data-loading-utility-method"></a>Veri yükleme yardımcı programı yöntemi oluştur

Görüntüler iki alt dizine depolanır. Verileri yüklemeden önce, bir nesne listesine biçimlendirilmesi gerekir `ImageData` . Bunu yapmak için yönteminin `LoadImagesFromDirectory` altında yöntemi oluşturun `Main` .

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. İçinde, `LoadImagesDirectory` alt dizinlerden tüm dosya yollarını almak için aşağıdaki kodu ekleyin:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Ardından, bir deyimleri kullanarak her bir dosya için yineleme yapın `foreach` .

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. İfadesinin içinde `foreach` , dosya uzantılarının desteklendiğinden emin olun. Resim sınıflandırma API 'SI JPEG ve PNG biçimlerini destekler.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Ardından, dosyanın etiketini alın. Parametresi olarak `useFolderNameAsLabel` ayarlandıysa `true` , dosyanın kaydedildiği üst dizin etiket olarak kullanılır. Aksi takdirde, etiketin dosya adının veya dosya adının ön eki olmasını bekler.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Son olarak, yeni bir örneğini oluşturun `ModelInput` .

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Verileri hazırlama

1. Yöntemine geri döndüğünüzde `Main` , `LoadFromDirectory` eğitim için kullanılan görüntülerin listesini almak için yardımcı program yöntemini kullanın.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Ardından, yöntemini kullanarak görüntüleri içine yükleyin [`IDataView`](xref:Microsoft.ML.IDataView) [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) .

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Veriler, dizinlerden okunan sıraya göre yüklenir. Verileri dengelemek için yöntemini kullanarak karıştırın [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) .

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Makine öğrenimi modelleri, girişin sayısal biçimde olmasını bekler. Bu nedenle, eğitimin öncesinde bazı ön işleme verilerin yapılması gerekir. [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) Ve `LoadRawImageBytes` dönüştürmelerini oluşturun. `MapValueToKey`Dönüştür sütundaki kategorik değeri alır `Label` , sayısal bir `KeyType` değere dönüştürür ve adlı yeni bir sütunda depolar `LabelAsKey` . , Bir `LoadImages` sütundaki değerleri, `ImagePath` `imageFolder` eğitimle ilgili görüntüleri yüklemek için parametresiyle birlikte alır.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. Verileri, [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) daha önce işlenmiş verileri içeren bir öğesini döndüren yöntemine göre uygulamak için yöntemini kullanın [`IDataView`](xref:Microsoft.ML.IDataView) .

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Bir modeli eğmek için bir eğitim veri kümesinin yanı sıra bir doğrulama veri kümesi de olması önemlidir. Model, eğitim kümesi üzerinde eğitilir. Görülmeyen veriler üzerinde tahminleri ne kadar iyi yapar doğrulama kümesine göre performans ile ölçülür. Model, bu performansın sonuçlarına bağlı olarak, geliştirme çabasında ne kadar öğrenildiği konusunda ayarlamalar yapar. Doğrulama kümesi, özgün veri kümenizi veya bu amaçla zaten ayrılmış olan başka bir kaynağı bölerek gelebilir. Bu durumda, önceden işlenmiş veri kümesi eğitim, doğrulama ve test kümelerine bölünür.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    Yukarıdaki kod örneği iki bölme gerçekleştirir. İlk olarak, önceden işlenmiş veriler bölünür ve %70, doğrulama için kalan %30 ' u kullanıldığında eğitim için kullanılır. Daha sonra, %30 doğrulama kümesi daha fazla doğrulama ve test kümelerine bölünür; burada %90 doğrulama için kullanılır ve test için %10 kullanılır.

    Bu veri bölümlerinin amacını düşünmek için bir yol, bir sınavın. Bir sınava göre çalışırken, sınavlarda bulunan kavramlara bir attık almak için notlarınızı, kitapları veya diğer kaynaklarınızı gözden geçirin. Bu, eğitim kümesinin için olduğu şeydir. Daha sonra, bilginizi doğrulamak için bir sahte sınava sahip olabilirsiniz. Bu, doğrulama kümesinin yararlı olduğu yerdir. Gerçek sınava girmeden önce kavramların iyi bir yermi olduğunu kontrol etmek istiyorsunuz. Bu sonuçlara dayanarak, ne kadar yanlış olduğunu veya iyi anladığınızı ve gerçek sınava göre gözden geçirdiğinize ilişkin değişikliklerinizi dahil etmediğinizi göz önünde bulmalısınız. Son olarak, sınava sahip olursunuz. Bu, için test kümesinin kullanıldığı şeydir. Sınavdaki soruları hiç gördüğdiniz ve şimdi eğitim ve doğrulamadan öğrendiklerinizi kullanarak bilgilerinizi el ile görev için nasıl uygulayacaksınız.

1. Eğitim, doğrulama ve test verileri için bölümleri ilgili değerleri atayın.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Eğitim işlem hattını tanımlama

Model eğitimi birkaç adımdan oluşur. İlk olarak, modeli eğitmek için görüntü sınıflandırma API 'SI kullanılır. Daha sonra, sütundaki kodlanmış Etiketler, `PredictedLabel` dönüştürme kullanılarak özgün kategorik değerlerine geri dönüştürülür `MapKeyToValue` .

1. Bir için gerekli ve isteğe bağlı parametrelerin bir kümesini depolamak için yeni bir değişken oluşturun `ImageClassificationTrainer` .

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    , `ImageClassificationTrainer` İsteğe bağlı birkaç parametre alır:

    - `FeatureColumnName`, model için girdi olarak kullanılan sütundur.
    - `LabelColumnName`tahmin edilecek değerin sütundeğeridir.
    - `ValidationSet`, [`IDataView`](xref:Microsoft.ML.IDataView) doğrulama verilerini içeriyor.
    - `Arch`önceden eğitilen model mimarilerinden hangisinin kullanılacağını tanımlar. Bu öğretici ResNetv2 modelinin 101 katman türevini kullanır.
    - `MetricsCallback`Eğitim sırasında ilerlemeyi izlemek için bir işlevi bağlar.
    - `TestOnTrainSet`bir doğrulama kümesi mevcut olmadığında, modele eğitim kümesine karşı performansı ölçmesini söyler.
    - `ReuseTrainSetBottleneckCachedValues`modele, sonraki çalışmalarda performans sorunlarına neden olan önbelleğe alınmış değerleri kullanıp kullanmayacağınızı söyler. Performans sorunu, ilk çalıştırıldığında yoğun bir şekilde yoğun bir geçiş hesaplasıdır. Eğitim verileri değişmezse ve farklı sayıda dönemler veya toplu iş boyutu kullanmayı denemek istiyorsanız, önbelleğe alınmış değerleri kullanmak bir modeli eğmek için gereken süreyi önemli ölçüde azaltır.
    - `ReuseValidationSetBottleneckCachedValues``ReuseTrainSetBottleneckCachedValues`yalnızca bu durumda, doğrulama veri kümesi için olduğu gibidir.
    - `WorkspacePath`hesaplanan performans sorunu değerlerinin ve model sürümünün depolanacağı dizini tanımlar `.pb` .

1. [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)Ve ' den oluşan eğitim işlem hattını tanımlayın `mapLabelEstimator` `ImageClassificationTrainer` .

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*)Modelinizi eğitebilmeniz için yöntemini kullanın.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Modeli kullanma

Modelinize eğitim sahibi olduğunuza göre, görüntüleri sınıflandırmak için kullanmanın zamanı.

Yönteminin altında `Main` , `OutputPrediction` konsolunda tahmin bilgilerini göstermek için adlı yeni bir yardımcı program yöntemi oluşturun.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Tek bir görüntüyü sınıflandır

1. `ClassifySingleImage` `Main` Tek bir görüntü tahminini oluşturmak ve çıktısını almak için yönteminin altına adlı yeni bir yöntem ekleyin.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)Yöntemi içinde oluşturun `ClassifySingleImage` . , [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) Tek bir veri örneği üzerinde bir tahmin etmenizi ve daha sonra bir tahmin gerçekleştirmenizi sağlayan kullanışlı BIR API 'dir.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Tek bir örneğe erişmek için, `ModelInput` `data` [`IDataView`](xref:Microsoft.ML.IDataView) yöntemini kullanarak öğesine dönüştürün [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) ve sonra ilk gözlemyi alın.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*)Görüntüyü sınıflandırmak için yöntemini kullanın.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. Yöntemi ile tahmine göre tahmine çıkış yapın `OutputPrediction` .

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. Yöntemi içinde `Main` , `ClassifySingleImage` Test görüntü kümesini kullanarak çağırın.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Birden çok görüntüyü sınıflandırma

1. `ClassifyImages` `ClassifySingleImage` Birden çok görüntü tahmini yapmak ve çıkarmak için yönteminin altında adlı yeni bir yöntem ekleyin.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. [`IDataView`](xref:Microsoft.ML.IDataView)Yöntemini kullanarak tahminleri içeren bir oluşturma oluşturun [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) . Aşağıdaki kodu yönteminin içine ekleyin `ClassifyImages` .

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. Tahmine dayalı olarak yinelemek için `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) yöntemini kullanarak öğesine dönüştürün [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) ve ardından ilk 10 gözlemyi alın.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Tahmine dayalı olarak orijinal ve tahmin edilen etiketleri yineleyin ve çıktı.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Son olarak, `Main` yöntemi içinde, `ClassifyImages` görüntü sınama kümesini kullanarak çağırın.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Konsol uygulamanızı çalıştırın. Çıktının aşağıdakine benzer olması gerekir. Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır. Breçekimi için çıkış yoğunlaştırılmış.

**Performans sorunu aşaması**

Görüntü adı için hiçbir değer yazdırılmaz, `byte[]` Bu nedenle görüntülenecek görüntü adı yok.

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

**Görüntüleri sınıflandırın çıktısı**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

*7001-220.jpg* görüntüsünü incelemeden, aslında bunun kırdığını görebilirsiniz.

![Tahmin için kullanılan SDNET2018 veri kümesi görüntüsü](./media/image-classification-api-transfer-learning/predictedimage.jpg)

Tebrikler! Artık görüntülerin sınıflandırılmasına yönelik derin bir öğrenme modelini başarıyla oluşturdunuz.

### <a name="improve-the-model"></a>Modeli geliştirme

Modelinizin sonuçlarını tatmin ediyorsanız, aşağıdaki yaklaşımlardan bazılarını deneyerek performansını geliştirmeyi deneyebilirsiniz:

- **Daha fazla veri**: bir modelin öğreni daha fazla örnek, ne kadar iyi çalışır. Tam [SDNET2018 veri kümesini](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) indirip eğmek için kullanın.
- **Verileri artırmak**: verileri bir görüntü alarak ve farklı dönüşümler uygulayarak (Döndür, çevir, Shift, Kırp) veri eklemek için sık kullanılan bir tekniktir. Bu, modelin öğreni için daha fazla değişken örnek ekler.
- Daha **uzun bir süre eğitin**: daha fazla eğitede, model daha fazla ayarlanmış olur. Dönemler sayısının artırılması, modelinizin performansını iyileştirebilecek.
- **Hyper-Parameters Ile denemeler yapın**: Bu öğreticide kullanılan parametrelere ek olarak, diğer parametreler potansiyel olarak performansı iyileştirecek şekilde ayarlanabilir. Her dönem performansı iyileştirebilmek için modele yapılan güncelleştirmelerin büyüklüğünü belirleyen öğrenme oranını değiştirme.
- **Farklı bir model mimarisi kullanın**: verilerinizin neye benzer olduğuna bağlı olarak, özelliklerini en iyi şekilde öğrenen en iyi şekilde bir model farklı olabilir. Modelinizin performansını karşılıyoruz, mimariyi değiştirmeyi deneyin.

### <a name="additional-resources"></a>Ek Kaynaklar

- [Derin öğrenme vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, aktarım öğrenimi, önceden eğitilen bir görüntü sınıflandırması TensorFlow modeli ve ML.NET görüntü sınıflandırma API 'sini kullanarak, somut yüzeyleri kırıllanmış veya kırılk olarak sınıflandırmakta olan özel bir derin öğrenme modeli oluşturmayı öğrendiniz.

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Nesne algılama](object-detection-onnx.md)
