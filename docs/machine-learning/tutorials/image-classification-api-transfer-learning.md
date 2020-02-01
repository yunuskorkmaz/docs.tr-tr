---
title: 'Öğretici: aktarım öğrenimi kullanarak otomatikleştirilmiş görsel inceleme'
description: Bu öğreticide, somut yüzeylerin görüntülerini kırçıkarılan veya Kırçıkmıyor olarak sınıflandırmak için görüntü algılama API 'sini kullanarak ML.NET ' deki bir TensorFlow derin öğrenme modelini nasıl eğitecağın nasıl kullanılacağı gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2dfa3cdab9de47b55f7a3f73f0d6e9460390700c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920097"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>Öğretici: ML.NET görüntü sınıflandırma API 'SI ile aktarım öğrenimini kullanarak otomatikleştirilmiş görsel inceleme

Özel derin öğrenme modelini, aktarım öğrenimi, önceden eğitilen bir TensorFlow modeli ve ML.NET görüntü sınıflandırma API 'sini kullanarak, somut yüzeylerin görüntülerini kırıllanmış veya kırılk olarak sınıflandırmasına nasıl eğeceğinizi öğrenin.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - ML.NET görüntü sınıflandırma API 'SI hakkında bilgi edinin
> - Önceden eğitilen modeli anlama
> - Özel bir TensorFlow görüntü sınıflandırma modelini eğitme için aktarım öğrenimi kullanma
> - Özel model ile görüntüleri sınıflandır

## <a name="prerequisites"></a>Prerequisites

- [Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="image-classification-transfer-learning-sample-overview"></a>Görüntü sınıflandırma aktarım öğrenme örneğine genel bakış

Bu örnek, önceden C# eğitilen bir derin öğrenme TensorFlow modeli kullanarak görüntüleri sınıflandırın bir .NET Core konsol uygulamasıdır. Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri deposunda](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) bulunabilir.

## <a name="understand-the-problem"></a>Sorunu anlama

Görüntü sınıflandırması bir bilgisayar vizyonu sorunudur. Görüntü sınıflandırması bir görüntüyü giriş olarak alır ve önceden tanımlanmış bir sınıfa kategorilere ayırır. Görüntü sınıflandırmasının kullanışlı olduğu bazı senaryolar şunlardır:

- Yüz tanıma
- Duygu algılama
- Tıp tanısı
- Yer işareti algılama

Bu öğreticide, bir özel görüntü sınıflandırma modeli sunarak, her ne kadar bozuk olan yapıları belirlemek için köprü oluşturma işlemlerini otomatik görsel denetlemesi gerçekleştirebilir.

## <a name="mlnet-image-classification-api"></a>ML.NET resim sınıflandırması API 'SI

ML.NET, görüntü sınıflandırması yapmak için çeşitli yollar sağlar. Bu öğretici, görüntü sınıflandırması API 'sini kullanarak Aktarım öğrenimini uygular. Görüntü sınıflandırma API 'SI, TensorFlow C# C++ API 'si için bağlamalar sağlayan alt düzey bir kitaplık olan [TensorFlow.net](https://github.com/SciSharp/TensorFlow.NET)kullanımını sağlar.

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

Performans sorunlarına neden olan çıkış değerleri hesaplandıktan sonra, modelin son katmanını yeniden eğitmek için giriş olarak kullanılırlar. Bu işlem yinelemeli ve model parametreleri tarafından belirtilen sayıda kez çalıştırılır. Her çalıştırma sırasında, kayıp ve doğruluk değerlendirilir. Daha sonra, kaybı en aza indirmek ve doğruluğu en üst düzeye çıkarmak için modeli geliştirmek üzere uygun ayarlamalar yapılır. Eğitim tamamlandığında, iki model biçimi çıkış olur. Bunlardan biri, modelin `.pb` sürümüdür ve diğeri de modelin `.zip` ML.NET serileştirilmiş sürümüdür. ML.NET tarafından desteklenen ortamlarda çalışırken, modelin `.zip` sürümünün kullanılması önerilir. Ancak, ML.NET 'in desteklenmediği ortamlarda `.pb` sürümünü kullanma seçeneğiniz vardır.

## <a name="understand-the-pretrained-model"></a>Önceden eğitilen modeli anlama

Bu öğreticide kullanılan önceden eğitilen model, kalan ağ (ResNet) v2 modelinin 101 katmanlı varyantıdır. Orijinal model resimleri bin kategoride sınıflandırmakta tasarlanmıştır. Model, 224 x 224 boyutundaki bir görüntüyü giriş olarak alır ve eğitilen sınıfların her biri için sınıf olasılıkların çıkışını çıkarır. Bu modelin bir parçası, iki sınıf arasında tahmine dayalı hale getirmek için özel görüntüler kullanarak yeni bir modeli eğitme için kullanılır.

## <a name="create-console-application"></a>Konsol uygulaması oluşturma

Aktarım öğrenimine ve görüntü sınıflandırma API 'sine ilişkin genel bir bilgiye sahip olduğunuza göre, uygulamayı derlemek zaman alabilir.

1. "DeepLearning_ImageClassification_Binary" adlı bir  **C# .NET Core konsol uygulaması** oluşturun.
1. **Microsoft.ml** Version **1.4.0** NuGet paketini yükler:
    1. Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.
    1. Paket kaynağı olarak "nuget.org" öğesini seçin.
    1. **Tarayıcı** sekmesini seçin.
    1. **Ön sürümü dahil et** onay kutusunu işaretleyin.
    1. **Microsoft.ml**için arama yapın.
    1. **Install** düğmesini seçin.
    1. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.
    1. Bu adımları **Microsoft. ml. Vision** sürümü **1.4.0**, **SciSharp. TensorFlow. Redist** sürüm **1.15.0**ve **Microsoft. ml. ımageanalytics** sürümü **1.4.0** NuGet paketleri için yineleyin.

### <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

> [!NOTE]
> Bu öğreticinin veri kümeleri Maguire, Marc; adresinden Dorafshan, Sattar; ve Thomas, Robert J., "SDNET2018: Machine Learning uygulamaları için somut bir görüntü veri kümesi" (2018). Tüm veri kümelerine gözatamazsınız. Kağıt 48. https://digitalcommons.usu.edu/all_datasets/48

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

1. *Program.cs* dosyasını açın ve dosyanın en üstündeki mevcut `using` deyimlerini aşağıdaki şekilde değiştirin:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. *Program.cs*içinde `Program` sınıfının altında `ImageData`adlı bir sınıf oluşturun. Bu sınıf başlangıçta yüklenen verileri temsil etmek için kullanılır.

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData` aşağıdaki özellikleri içerir:

    - `ImagePath`, görüntünün depolandığı tam yoldur.
    - `Label` görüntünün ait olduğu kategorisidir. Tahmin edilecek değer budur.

1. Giriş ve çıkış verileriniz için sınıflar oluşturma

    1. `ImageData` sınıfının altında, giriş verilerinizin şemasını `ModelInput`adlı yeni bir sınıfta tanımlayın.

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput` aşağıdaki özellikleri içerir:

        - `Image` görüntünün `byte[]` gösterimidir. Model, yansıma verilerinin eğitim için bu türden olmasını bekler.
        - `LabelAsKey`, `Label`sayısal gösterimidir.
        - `ImagePath`, görüntünün depolandığı tam yoldur.
        - `Label` görüntünün ait olduğu kategorisidir. Tahmin edilecek değer budur.

        Modeli eğitme ve tahmin yapmak için yalnızca `Image` ve `LabelAsKey` kullanılır. `ImagePath` ve `Label` özellikleri özgün görüntü dosyası adına ve kategorisine erişmek için kolaylık sağlamak üzere tutulur.

    1. Daha sonra, `ModelInput` sınıfının altında, çıkış verilerinizin şemasını `ModelOutput`adlı yeni bir sınıfta tanımlayın.

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput` aşağıdaki özellikleri içerir:

        - `ImagePath`, görüntünün depolandığı tam yoldur.
        - `Label` görüntünün ait olduğu özgün kategorisidir. Tahmin edilecek değer budur.
        - `PredictedLabel`, model tarafından tahmin edilen değerdir.

        `ModelInput`benzer şekilde, yalnızca `PredictedLabel` model tarafından yapılan tahminleri içerdiğinden tahmine dayalı hale getirilmeleri gerekir. `ImagePath` ve `Label` özellikleri özgün görüntü dosyası adına ve kategorisine erişmek için kolaylık sağlamak amacıyla tutulur.

### <a name="create-workspace-directory"></a>Çalışma alanı dizini oluştur

Eğitim ve doğrulama verileri sıklıkla değişmediğinde, daha fazla çalıştırma için hesaplanan darboğazal değerlerini önbelleğe almak iyi bir uygulamadır.

1. Projenizde, hesaplanan performans sorunu değerlerini ve modelin `.pb` sürümünü depolamak için *çalışma alanı* adlı yeni bir dizin oluşturun.

### <a name="define-paths-and-initialize-variables"></a>Yolları tanımlama ve değişkenleri başlatma

1. `Main` yönteminin içinde, varlıklarınızın konumunu, hesaplanan tıkanıklık değerlerini ve modelin `.pb` sürümünü tanımlayın.

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. `mlContext` değişkenini yeni bir [Mlcontext](xref:Microsoft.ML.MLContext)örneğiyle başlatın.

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    [Mlcontext](xref:Microsoft.ML.MLContext) sınıfı tüm ml.NET işlemleri için bir başlangıç noktasıdır ve mlcontext 'i başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Benzer, kavramsal olarak, Entity Framework `DBContext`.

## <a name="load-the-data"></a>Verileri yükleme

### <a name="create-data-loading-utility-method"></a>Veri yükleme yardımcı programı yöntemi oluştur

Görüntüler iki alt dizine depolanır. Verileri yüklemeden önce, `ImageData` nesnelerinin bir listesi halinde biçimlendirilmesi gerekir. Bunu yapmak için, `Main` yönteminin altında `LoadImagesFromDirectory` yöntemi oluşturun.

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. `LoadImagesDirectory` iç dizinlerindeki tüm dosya yollarını almak için aşağıdaki kodu ekleyin:

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. Ardından, bir `foreach` bildiri kullanarak her bir dosyanın üzerinde yineleyin.

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. `foreach` ifadesinin içinde, dosya uzantılarının desteklendiğinden emin olun. Resim sınıflandırma API 'SI JPEG ve PNG biçimlerini destekler.

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. Ardından, dosyanın etiketini alın. `useFolderNameAsLabel` parametresi `true`olarak ayarlanırsa, dosyanın kaydedildiği üst dizin etiket olarak kullanılır. Aksi takdirde, etiketin dosya adının veya dosya adının ön eki olmasını bekler.

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. Son olarak, `ModelInput`yeni bir örneğini oluşturun.

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>Verileri hazırlama

1. `Main` yöntemine geri döndüğünüzde, eğitim için kullanılan görüntülerin listesini almak için `LoadFromDirectory` yardımcı program yöntemini kullanın.

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. Sonra, [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) yöntemini kullanarak görüntüleri bir [`IDataView`](xref:Microsoft.ML.IDataView) içine yükleyin.

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. Veriler, dizinlerden okunan sıraya göre yüklenir. Verileri dengelemek için [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) yöntemi kullanarak karıştırın.

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. Makine öğrenimi modelleri, girişin sayısal biçimde olmasını bekler. Bu nedenle, eğitimin öncesinde bazı ön işleme verilerin yapılması gerekir. [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) ve `LoadRawImageBytes` dönüştürmelerini [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) oluşturun. `MapValueToKey` Transform, `Label` sütununda kategorik değeri alır, sayısal bir `KeyType` değere dönüştürür ve `LabelAsKey`adlı yeni bir sütunda depolar. `LoadImages`, eğitim için görüntüleri yüklemek üzere `imageFolder` parametresiyle birlikte `ImagePath` sütunundaki değerleri alır.

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) yöntemini kullanarak verileri `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ve ardından önceden işlenmiş verileri içeren bir [`IDataView`](xref:Microsoft.ML.IDataView) döndüren [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) yöntemi ile uygulayın.

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. Bir modeli eğmek için bir eğitim veri kümesinin yanı sıra bir doğrulama veri kümesi de olması önemlidir. Model, eğitim kümesi üzerinde eğitilir. Görülmeyen veriler üzerinde tahminleri ne kadar iyi yapar doğrulama kümesine göre performans ile ölçülür. Model, bu performansın sonuçlarına bağlı olarak, geliştirme çabasında ne kadar öğrenildiği konusunda ayarlamalar yapar. Doğrulama kümesi, özgün veri kümenizi veya bu amaçla zaten ayrılmış olan başka bir kaynağı bölerek gelebilir. Bu durumda, önceden işlenmiş veri kümesi eğitim, doğrulama ve test kümelerine bölünür.

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    Yukarıdaki kod örneği iki bölme gerçekleştirir. İlk olarak, önceden işlenmiş veriler bölünür ve %70, doğrulama için kalan %30 ' u kullanıldığında eğitim için kullanılır. Daha sonra, %30 doğrulama kümesi daha fazla doğrulama ve test kümelerine bölünür; burada %90 doğrulama için kullanılır ve test için %10 kullanılır.

    Bu veri bölümlerinin amacını düşünmek için bir yol, bir sınavın. Bir sınava göre çalışırken, sınavlarda bulunan kavramlara bir attık almak için notlarınızı, kitapları veya diğer kaynaklarınızı gözden geçirin. Bu, eğitim kümesinin için olduğu şeydir. Daha sonra, bilginizi doğrulamak için bir sahte sınava sahip olabilirsiniz. Bu, doğrulama kümesinin yararlı olduğu yerdir. Gerçek sınava girmeden önce kavramların iyi bir yermi olduğunu kontrol etmek istiyorsunuz. Bu sonuçlara dayanarak, ne kadar yanlış olduğunu veya iyi anladığınızı ve gerçek sınava göre gözden geçirdiğinize ilişkin değişikliklerinizi dahil etmediğinizi göz önünde bulmalısınız. Son olarak, sınava sahip olursunuz. Bu, için test kümesinin kullanıldığı şeydir. Sınavdaki soruları hiç gördüğdiniz ve şimdi eğitim ve doğrulamadan öğrendiklerinizi kullanarak bilgilerinizi el ile görev için nasıl uygulayacaksınız.

1. Eğitim, doğrulama ve test verileri için bölümleri ilgili değerleri atayın.

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>Eğitim işlem hattını tanımlama

Model eğitimi birkaç adımdan oluşur. İlk olarak, modeli eğitmek için görüntü sınıflandırma API 'SI kullanılır. Daha sonra, `PredictedLabel` sütunundaki kodlanmış Etiketler, `MapKeyToValue` dönüşümü kullanılarak özgün kategorik değerlerine geri dönüştürülür.

1. Bir `ImageClassificationTrainer`için gerekli ve isteğe bağlı parametrelerin bir kümesini depolamak üzere yeni bir değişken oluşturun.

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    `ImageClassificationTrainer` birkaç isteğe bağlı parametre alır:

    - `FeatureColumnName`, model için girdi olarak kullanılan sütundur.
    - `LabelColumnName`, tahmin edilecek değerin sütundeğeridir.
    - `ValidationSet`, doğrulama verilerini içeren [`IDataView`](xref:Microsoft.ML.IDataView) .
    - `Arch`, önceden eğitilen model mimarilerinden hangisinin kullanılacağını tanımlar. Bu öğretici ResNetv2 modelinin 101 katman türevini kullanır.
    - `MetricsCallback` eğitim sırasında ilerlemeyi izlemek için bir işlevi bağlar.
    - `TestOnTrainSet`, bir doğrulama kümesi mevcut olmadığında modelin eğitim kümesine karşı performansını ölçmesini söyler.
    - `ReuseTrainSetBottleneckCachedValues`, sonraki çalışmalarda performans sorunlarına neden olan önbelleğe alınmış değerleri kullanıp kullanmayacağınızı modele söyler. Performans sorunu, ilk çalıştırıldığında yoğun bir şekilde yoğun bir geçiş hesaplasıdır. Eğitim verileri değişmezse ve farklı sayıda dönemler veya toplu iş boyutu kullanmayı denemek istiyorsanız, önbelleğe alınmış değerleri kullanmak bir modeli eğmek için gereken süreyi önemli ölçüde azaltır.
    - `ReuseValidationSetBottleneckCachedValues`, yalnızca bu örnekte doğrulama veri kümesi için olan `ReuseTrainSetBottleneckCachedValues` benzerdir.
    - `WorkspacePath`, hesaplanan performans sorunu değerlerinin ve modelin `.pb` sürümünün depolanacağı dizini tanımlar.

1. Hem `mapLabelEstimator` hem de `ImageClassificationTrainer`oluşan [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) eğitim işlem hattını tanımlayın.

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. Modelinize eğitebilmeniz için [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) yöntemini kullanın.

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>Modeli kullanma

Modelinize eğitim sahibi olduğunuza göre, görüntüleri sınıflandırmak için kullanmanın zamanı.

`Main` yönteminin altında, konsolunda tahmin bilgilerini göstermek için `OutputPrediction` adlı yeni bir yardımcı program yöntemi oluşturun.

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>Tek bir görüntüyü sınıflandır

1. Tek bir görüntü tahminini yapmak ve çıkarmak için `Main` yönteminin altına `ClassifySingleImage` adlı yeni bir yöntem ekleyin.

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. `ClassifySingleImage` yöntemi içinde [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) oluşturun. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneği üzerinde bir tahmin etmenizi ve daha sonra bir tahmin gerçekleştirmenizi sağlayan KULLANıŞLı bir API 'dir.

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. Tek bir `ModelInput` örneğine erişmek için, [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemini kullanarak `data` [`IDataView`](xref:Microsoft.ML.IDataView) bir [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dönüştürün ve ardından ilk gözlemyi alın.

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. Görüntüyü sınıflandırmak için [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) yöntemini kullanın.

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. `OutputPrediction` yöntemiyle, tahmine konsola çıkış yapın.

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. `Main` yönteminin içinde, görüntü sınama kümesini kullanarak `ClassifySingleImage` çağırın.

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>Birden çok görüntüyü sınıflandırma

1. Birden çok görüntü Tahminleri yapmak ve çıkarmak için `ClassifySingleImage` yönteminin altına `ClassifyImages` adlı yeni bir yöntem ekleyin.

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodunu kullanarak tahminleri içeren bir [`IDataView`](xref:Microsoft.ML.IDataView) oluşturun. `ClassifyImages` yönteminin içine aşağıdaki kodu ekleyin.

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. Tahmine dayalı olarak yinelemek için, `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) yöntemini kullanarak [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) dönüştürün ve ardından ilk 10 gözlemleme elde edin.

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. Tahmine dayalı olarak orijinal ve tahmin edilen etiketleri yineleyin ve çıktı.

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. Son olarak, `Main` yönteminin içinde, görüntü sınama kümesini kullanarak `ClassifyImages` çağırın.

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>Uygulamayı çalıştırın

Konsol uygulamanızı çalıştırın. Çıktının aşağıdakine benzer olması gerekir. Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır. Breçekimi için çıkış yoğunlaştırılmış.

**Performans sorunu aşaması**

Görüntüler `byte[]` olarak yüklendiği için görüntü adı için hiçbir değer yazdırılamaz, bu nedenle görüntülenecek görüntü adı yok.

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

*7001 -220. jpg* görüntüsünü incelemeden, aslında bunun kırdığını görebilirsiniz.

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
