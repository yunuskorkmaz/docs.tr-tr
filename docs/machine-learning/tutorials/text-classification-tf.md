---
title: 'Öğretici: TensorFlow modelini kullanarak inceleme duyarlılığını analiz edin'
description: Bu öğretici, web sitesi yorumlarında duyguları sınıflandırmak için önceden eğitilmiş tensorflow modelini nasıl kullanacağınızı gösterir. İkili duygu sınıflandırıcı Visual Studio kullanılarak geliştirilen bir C# konsol uygulamasıdır.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241123"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Öğretici: ML.NET önceden eğitilmiş TensorFlow modelini kullanarak film incelemelerinin duyarlılığını analiz edin

Bu öğretici, web sitesi yorumlarında duyguları sınıflandırmak için önceden eğitilmiş tensorflow modelini nasıl kullanacağınızı gösterir. İkili duygu sınıflandırıcı Visual Studio kullanılarak geliştirilen bir C# konsol uygulamasıdır.

Bu eğitimde kullanılan TensorFlow modeli IMDB veritabanından film incelemeleri kullanılarak eğitildi. Uygulamayı geliştirmeyi bitirdikten sonra, film inceleme metni ni sağlayabilirsiniz ve uygulama incelemenin olumlu veya olumsuz bir duyarlılığı olup olmadığını size söyleyecektir.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> * Önceden eğitilmiş tensorFlow modelini yükleyin
> * Web sitesi yorum metnini modele uygun özelliklere dönüştürme
> * Tahminde bulunmak için modeli kullanma

Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.

## <a name="setup"></a>Kurulum

### <a name="create-the-application"></a>Uygulama oluşturma

1. "TextClassificationTF" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *Veri* adlı bir dizin oluşturun.

3. Microsoft.ML **NuGet Paketini**Yükleyin:

    Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin ve ardından **Gözat** sekmesini seçin. **Microsoft.ML**ara, istediğiniz paketi seçin ve sonra **Yükle** düğmesini seçin. Seçtiğiniz paketin lisans koşullarını kabul ederek yüklemeye devam edin. **Microsoft.ML.TensorFlow** ve **SciSharp.TensorFlow.Redist**için bu adımları tekrarlayın.

### <a name="add-the-tensorflow-model-to-the-project"></a>Projeye TensorFlow modelini ekleme

> [!NOTE]
> Bu öğretici için model [dotnet / machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo olduğunu. Model TensorFlow SavedModel biçimindedir.

1. zip [sentiment_model dosyasını](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)indirin ve zip'i açın.

    Zip dosyası şunları içerir:

    * `saved_model.pb`: TensorFlow modelinin kendisi. Model, IMDB gözden geçirme dizesinde metni temsil eden sabit bir uzunluk (boyut 600) tamsayı dizisini alır ve 1'e kadar toplamı iki olasılık çıkarır: giriş incelemesinin olumlu bir duyarlılığa sahip olma olasılığı ve girdi incelemesinin sahip olma olasılığı olumsuz duygular.
    * `imdb_word_index.csv`: tek tek sözcüklerden tamsayı değerine eşleme. Eşleme TensorFlow modeli için giriş özellikleri oluşturmak için kullanılır.

2. En içteki `sentiment_model` dizinin içeriğini *TextClassificationTF* proje `sentiment_model` dizininize kopyalayın. Bu dizin, aşağıdaki resimde gösterildiği gibi, bu öğretici için gerekli modeli ve ek destek dosyalarını içerir:

   ![sentiment_model dizin içeriği](./media/text-classification-tf/sentiment-model-files.png)

3. Çözüm Gezgini'nde, `sentiment_model` dizin ve alt dizindeki dosyaların her birini sağ tıklatın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

### <a name="add-using-statements-and-global-variables"></a>Deyimleri ve genel değişkenleri kullanarak ekleme

1. Aşağıdaki ek `using` deyimleri *Program.cs* dosyasının üstüne ekleyin:

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Kaydedilen model dosya yolunu `Main` ve özellik vektör uzunluğunu tutmak için yöntemin hemen üzerinde iki genel değişken oluşturun.

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`eğitilmiş modelin dosya yoludur.
    * `FeatureLength`modelin beklediği toplam özellik dizisinin uzunluğudur.

### <a name="model-the-data"></a>Verileri modelleme

Film eleştirileri ücretsiz form metindir. Uygulamanız, metni, modeltarafından birkaç ayrı aşamada beklenen giriş biçimine dönüştürür.

İlki, metni ayrı sözcüklere bölmek ve her sözcüğü bir sonda kodlamasına eşlemek için sağlanan eşleme dosyasını kullanmaktır. Bu dönüşümün sonucu, cümledeki sözcük sayısına karşılık gelen uzunlukta bir değişken uzunlukta tamsayı dizisidir.

|Özellik| Değer|Tür|
|-------------|-----------------------|------|
|İnceleme Metni|bu film gerçekten çok iyi|string|
|Değişken UzunlukÖzellikleri|14,22,9,66,78,... |int[]|

Değişken uzunluk özelliği dizisi daha sonra 600 sabit bir uzunluğa yeniden boyutlandırılır. Bu, TensorFlow modelinin beklediği uzunluktur.

|Özellik| Değer|Tür|
|-------------|-----------------------|------|
|İnceleme Metni|bu film gerçekten çok iyi|string|
|Değişken UzunlukÖzellikleri|14,22,9,66,78,... |int[]|
|Özellikler|14,22,9,66,78,... |int[600]|

1. Yöntemden `Main` sonra giriş verileriniz için bir sınıf oluşturun:

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    Giriş veri sınıfı, `MovieReview`kullanıcı `string` yorumları için`ReviewText`bir var ( ).

1. `Main` Yöntemden sonra değişken uzunluk özellikleri için bir sınıf oluşturun:

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    Özellik `VariableLengthFeatures` vektör olarak belirlemek için bir [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) özniteliği vardır.  Tüm vektör elemanları aynı türde olmalıdır. Çok sayıda sütuna sahip veri kümelerinde, birden çok sütunu tek bir vektör olarak yüklemek, veri dönüşümlerini uyguladığınızda veri geçişlerinin sayısını azaltır.

    Bu sınıf `ResizeFeatures` eylemde kullanılır. Özelliklerinin adları (bu durumda yalnızca bir) DataView'daki hangi sütunların özel eşleme eylemine _giriş_ olarak kullanılabileceğini belirtmek için kullanılır.

1. `Main` Yöntemden sonra sabit uzunluk özellikleri için bir sınıf oluşturun:

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    Bu sınıf `ResizeFeatures` eylemde kullanılır. Özelliklerinin adları (bu durumda yalnızca bir tane) DataView'daki hangi sütunların özel eşleme eyleminin _çıktısı_ olarak kullanılabileceğini belirtmek için kullanılır.

    Özelliğin `Features` adının TensorFlow modeli tarafından belirlendiğini unutmayın. Bu özellik adını değiştiremezsiniz.

1. `Main` Yöntemden sonra tahmin için bir sınıf oluşturun:

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction`model eğitiminden sonra kullanılan tahmin sınıfıdır. `MovieReviewSentimentPrediction`tek `float` bir dizi`Prediction`( `VectorType` ) ve bir özniteliği vardır.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Özellikleri yeniden boyutlandırmak için MLContext, arama sözlüğü ve eylem oluşturun

[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç noktasıdır. İlk `mlContext` başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur. Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.

1. MlContext `Console.WriteLine("Hello World!")` değişkenini `Main` bildirmek ve başlatmak için yöntemdeki satırı aşağıdaki kodla değiştirin:

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. Aşağıdaki tabloda görüldüğü gibi, bir dosyadan [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) eşleme verilerini yüklemek için yöntemi kullanarak sözcükleri tamsayı olarak kodlamak için bir sözlük oluşturun:

    |Word     |Dizin oluşturma    |
    |---------|---------|
    |Çocuklar     |  362    |
    |Istiyor     |  181    |
    |Yanlış    |  355    |
    |effects  |  302    |
    |Duygu  |  547    |

    Arama eşlemi oluşturmak için aşağıdaki kodu ekleyin:

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. Bir `Action` sonraki kod satırları ile sabit boyutlu bir toplam dizi değişken uzunlukta sözcük ortasayı dizisini yeniden boyutlandırmak için bir ekleyin:

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Önceden eğitilmiş TensorFlow modelini yükleyin

1. TensorFlow modelini yüklemek için kod ekleyin:

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    Model yüklendikten sonra, giriş ve çıkış şema ayıklayabilirsiniz. Şemalar sadece ilgi ve öğrenme için görüntülenir. Son uygulamanın çalışması için bu koda ihtiyacınız yoktur:

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    Giriş şeması, tamsayı kodlanmış sözcüklerin sabit uzunluktaki dizisidir. Çıktı şeması, bir incelemenin duyarlılığının olumsuz mu yoksa olumlu mu olduğunu gösteren bir sürüolasılık dizisidir. Bu değerler 1'e kadar toplam, pozitif olma olasılığı, duyarlılığın negatif olma olasılığının tamamlayıcısı olduğu için.

## <a name="create-the-mlnet-pipeline"></a>ML.NET ardışık oluşturma

1. Satır kuralını oluşturun ve bir sonraki kod satırı olarak metni sözcüklere bölmek için [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) dönüştürmeyi kullanarak giriş metnini sözcüklere bölün:

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) dönüştürme, metin/dizeyi sözcüklere ayrıştırmak için boşlukları kullanır. Yeni bir sütun oluşturur ve her giriş dizesini kullanıcı tanımlı ayırıcıya dayalı bir alt dizeleri vektörüne böler.

1. Yukarıda beyan ettiğiniz arama tablosunu kullanarak sözcükleri, kendi enstabazı kodlamalarına eşle:

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. Değişken uzunluk lı ortalık kodlayıcı kodlamalarını modelin gerektirdiği sabit uzunlukta olana yeniden boyutlandırın:

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. Yüklenen TensorFlow modeliyle girişi sınıflandırın:

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    TensorFlow modeli çıktısı `Prediction/Softmax`denir. Adın `Prediction/Softmax` TensorFlow modeli tarafından belirlendiğini unutmayın. Bu adı değiştiremezsiniz.

1. Çıktı tahmini için yeni bir sütun oluşturun:

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    Sütunu `Prediction/Softmax` C# sınıfında özellik olarak kullanılabilecek bir adla kopyalamanız gerekir: `Prediction`. `/` C# özellik adında karaktere izin verilmez.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Boru hattından ML.NET modeli oluşturma

1. Modeli ardışık kaynaktan oluşturmak için kodu ekleyin:

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    ML.NET modeli, `Fit` yöntem çağırılarak ardışık ardışık alan tahminciler zincirinden oluşturulur. Bu durumda, TensorFlow modeli daha önce eğitilmiş olduğundan, modeli oluşturmak için herhangi bir veri sığdırmiyoruz. Yöntemin gereksinimlerini karşılamak için boş bir `Fit` veri görünümü nesnesi sağlıyoruz.

## <a name="use-the-model-to-make-a-prediction"></a>Tahminde bulunmak için modeli kullanma

1. `PredictSentiment` Yöntemi aşağıdaki yöntemin `Main` altına ekleyin:

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Yöntemde ilk satır `PredictionEngine` olarak oluşturmak için aşağıdaki kodu ekleyin: `PredictSentiment()`

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    [PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir. Tek dişli veya prototip ortamlarda kullanılabilir. Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın. ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.

    > [!NOTE]
    > `PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.

1. Bir örnek oluşturarak `Predict()` yöntemde eğitimli modelin tahminsına test `MovieReview`etmek için bir açıklama ekleyin:

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. Yöntemde sonraki kod `Prediction Engine` satırlarını ekleyerek test yorum `PredictSentiment()` verilerini geçirin:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahminyapar:

    |Özellik| Değer|Tür|
    |-------------|-----------------------|------|
    |Prediction (Tahmin)|[0.5459937, 0.454006255]|float[]|

1. Aşağıdaki kodu kullanarak duyarlılık tahminini görüntüleyin:

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. Yöntemin sonunda `PredictSentiment` bir çağrı ekleyin: `Main`

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Sonuçlar

Uygulamanızı oluşturun ve çalıştırın.

Sonuçlarınız aşağıdakilere benzer olmalıdır. İşlem sırasında iletiler görüntülenir. Uyarılar veya iletileri işleme görebilirsiniz. Bu iletiler netlik için aşağıdaki sonuçlardan kaldırıldı.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Tebrikler! Şimdi, ML.NET önceden eğitilmiş bir modeli yeniden kullanarak iletilerin duyarlılığını sınıflandırmak ve `TensorFlow` tahmin etmek için başarılı bir şekilde bir makine öğrenme modeli oluşturmuşsunuz.

Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Önceden eğitilmiş tensorFlow modelini yükleyin
> * Web sitesi yorum metnini modele uygun özelliklere dönüştürme
> * Tahminde bulunmak için modeli kullanma
