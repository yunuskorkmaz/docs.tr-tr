---
title: 'Öğretici: bir TensorFlow modeli kullanarak İnceleme yaklaşımını çözümleme'
description: Bu öğreticide, Web sitesi açıklamalarında yaklaşımı sınıflandırmak için önceden eğitilen bir TensorFlow modelinin nasıl kullanılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio kullanılarak geliştirilen bir C# konsol uygulamasıdır.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9c1e45f183bd5edc488e4f37bea648566d124c65
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803267"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Öğretici: ML.NET 'de önceden eğitilen bir TensorFlow modeli kullanarak film incelemelerinin yaklaşımını çözümleyin

Bu öğreticide, Web sitesi açıklamalarında yaklaşımı sınıflandırmak için önceden eğitilen bir TensorFlow modelinin nasıl kullanılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio kullanılarak geliştirilen bir C# konsol uygulamasıdır.

Bu öğreticide kullanılan TensorFlow modeli, ıMDB veritabanından Film İncelemeleri kullanılarak eğitildi. Uygulamayı geliştirmeyi bitirdikten sonra, film gözden geçirme metni sağlayabileceksiniz ve uygulama Gözden geçirmedeki pozitif veya negatif bir yaklaşım olup olmadığını söyleyecektir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Önceden eğitilen bir TensorFlow modeli yükleme
> * Web sitesi açıklama metnini model için uygun özelliklere Dönüştür
> * Tahmin yapmak için modeli kullanma

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

* [Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="setup"></a>Kurulum

### <a name="create-the-application"></a>Uygulama oluşturma

1. "TextClassificationTF" adlı bir **.NET Core konsol uygulaması** oluşturun.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.

3. **Microsoft.ml NuGet paketini**yükler:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin ve sonra da **tarayıcı** sekmesini seçin. **Microsoft.ml**için arama yapın, istediğiniz paketi seçin ve sonra da **Install** düğmesini seçin. Kabul etmiş ile yüklemeye, seçtiğiniz paketin lisans koşullarına devam edin. **Microsoft. ml. TensorFlow**, **Microsoft. ml. Sampleutils** ve **SciSharp. TensorFlow. Redist**için bu adımları tekrarlayın.

### <a name="add-the-tensorflow-model-to-the-project"></a>TensorFlow modelini projeye ekleme

> [!NOTE]
> Bu öğreticinin modeli [DotNet/machinöğrenim-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub deposundan. Model, TensorFlow SavedModel biçimindedir.

1. [Sentiment_model ZIP dosyasını](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)indirin ve sıkıştırmayı açın.

    ZIP dosyası şunları içerir:

    * `saved_model.pb`: TensorFlow modelinin kendisi. Model, bir ıMDB İnceleme dizesindeki metni temsil eden özelliklerin sabit uzunlukta (boyut 600) tamsayı dizisini alır ve 1 ' e kadar olan iki olasılıkların çıkışını verir: giriş incelemesinin pozitif yaklaşım olduğu ve giriş incelemesinin olumsuz yaklaşım olduğu olasılık.
    * `imdb_word_index.csv`: tek sözcüklerden bir tamsayı değere eşleme. Eşleme, TensorFlow modelinin giriş özelliklerini oluşturmak için kullanılır.

2. En içteki `sentiment_model` dizinin Içeriğini *TextClassificationTF* proje `sentiment_model` dizininize kopyalayın. Bu dizin, aşağıdaki görüntüde gösterildiği gibi, bu öğretici için gereken modeli ve ek destek dosyalarını içerir:

   ![Dizin içeriğini sentiment_model](./media/text-classification-tf/sentiment-model-files.png)

3. Çözüm Gezgini, dizin ve alt dizindeki dosyaların her birine sağ tıklayın `sentiment_model` ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

### <a name="add-using-statements-and-global-variables"></a>Using deyimleri ve genel değişkenler ekleme

1. Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. `Main`Kaydedilen model dosyası yolunu ve özellik vektörü uzunluğunu tutmak için yönteminin üzerinde doğrudan iki genel değişken oluşturun.

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`, eğitilen modelin dosya yoludur.
    * `FeatureLength`, modelin beklediği tamsayı özelliği dizisinin uzunluğudur.

### <a name="model-the-data"></a>Verileri modelleme

Film İncelemeleri, ücretsiz form metinlerdir. Uygulamanız, metni bir dizi farklı aşamada model tarafından beklenen giriş biçimine dönüştürür.

Birincisi, metni ayrı sözcüklere bölmek ve her bir sözcüğü bir tamsayı kodlamasıyla eşlemek için belirtilen eşleme dosyasını kullanmaktır. Bu dönüştürmenin sonucu, tümcedeki sözcüklerin sayısına karşılık gelen uzunluğa sahip bir değişken uzunluklu tamsayı dizisidir.

|Özellik| Değer|Tür|
|-------------|-----------------------|------|
|Belgemetinmetni|Bu film gerçekten iyi|string|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|

Değişken uzunluğu özellik dizisi daha sonra sabit 600 uzunluğuna yeniden boyutlandırılır. Bu, TensorFlow modelinin beklediği uzunluktadır.

|Özellik| Değer|Tür|
|-------------|-----------------------|------|
|Belgemetinmetni|Bu film gerçekten iyi|string|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|
|Özellikler|14, 22, 9, 66, 78,... |Tamsayı [600]|

1. Yönteminden sonra giriş verileriniz için bir sınıf oluşturun `Main` :

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    Giriş veri sınıfı `MovieReview` `string` için bir for User Comments ( `ReviewText` ) vardır.

1. Yöntemden sonra değişken uzunluklu özellikler için bir sınıf oluşturun `Main` :

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    `VariableLengthFeatures`Özelliğin bir vektör olarak belirlemek için bir [Vectortype](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) özniteliği vardır.  Tüm vektör öğeleri aynı türde olmalıdır. Çok sayıda sütun içeren veri kümelerinde, birden fazla sütunu tek bir vektör olarak yüklemek, veri dönüştürmeleri uyguladığınızda veri geçişlerinin sayısını azaltır.

    Bu sınıf, `ResizeFeatures` eylemde kullanılır. Özelliklerinin adları (Bu durumda yalnızca bir tane), DataView içindeki hangi sütunların özel eşleme eylemine _giriş_ olarak kullanılabileceğini göstermek için kullanılır.

1. Yönteminden sonra sabit uzunluklu özellikler için bir sınıf oluşturun `Main` :

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    Bu sınıf, `ResizeFeatures` eylemde kullanılır. Özelliklerinin adları (Bu durumda yalnızca bir tane), DataView içindeki hangi sütunların özel eşleme eyleminin _çıktısı_ olarak kullanılabileceğini göstermek için kullanılır.

    Özelliğin adının `Features` TensorFlow modeliyle belirlendiğini unutmayın. Bu özellik adını değiştiremezsiniz.

1. Yöntemi sonrasında tahmin için bir sınıf oluşturun `Main` :

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction`, model eğitiminden sonra kullanılan tahmin sınıfıdır. `MovieReviewSentimentPrediction`tek bir `float` Array ( `Prediction` ) ve bir `VectorType` özniteliğe sahiptir.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Özellikleri yeniden boyutlandırmak için MLContext, arama sözlüğü ve eylemi oluşturma

[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır. Başlatma `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilecek yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal olarak da benzerdir `DBContext` .

1. `Console.WriteLine("Hello World!")` `Main` Mlcontext değişkenini bildirmek ve başlatmak için yöntemindeki satırı aşağıdaki kodla değiştirin:

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A)Aşağıdaki tabloda görüldüğü gibi, bir dosyadan eşleme verilerini yüklemek için yöntemini kullanarak sözcükleri tamsayı olarak kodlamak için bir sözlük oluşturun:

    |Word     |Dizin oluşturma    |
    |---------|---------|
    |öğre     |  362    |
    |istiyorum     |  181    |
    |yanlış    |  355    |
    |effects  |  302    |
    |rahatsızlık  |  547    |

    Arama eşlemesini oluşturmak için aşağıdaki kodu ekleyin:

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. `Action`Değişken uzunluğu sözcük tamsayı dizisini, sonraki kod satırları ile sabit boyutlu bir tamsayı dizisine yeniden boyutlandırmak için bir ekleyin:

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Önceden eğitilen TensorFlow modelini yükleme

1. TensorFlow modelini yüklemek için kod ekleyin:

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    Model yüklendikten sonra, giriş ve çıkış şemasını ayıklayabilirsiniz. Şemalar yalnızca ilgi ve öğrenme için görüntülenir. Son uygulamanın çalışması için bu koda ihtiyacınız yoktur:

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    Giriş şeması, tamsayı kodlamalı sözcüklerin sabit uzunluklu dizisidir. Çıktı şeması, bir gözden geçirme yaklaşımını negatif mi yoksa pozitif mi olduğunu gösteren bir dizi olasılıkların dizisidir. Bu değerler, pozitif olma olasılığı olarak 1 ' e kadar toplamdır.

## <a name="create-the-mlnet-pipeline"></a>ML.NET işlem hattını oluşturma

1. Bir sonraki kod satırı olarak sözcükleri sözcüklere eklemek için, işlem hattını oluşturun ve giriş metnini [Tokenizeıntowords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) dönüşümünü kullanarak sözcüklere bölün:

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   [Tokenizeıntowords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) dönüşümü, metni/dizeyi sözcüklere ayrıştırmak için boşluk kullanır. Yeni bir sütun oluşturur ve her giriş dizesini Kullanıcı tanımlı ayırıcıya göre alt dizelerin vektörüne böler.

1. Yukarıda bildirdiğiniz arama tablosunu kullanarak kelimeleri tamsayı kodlamasıyla eşleyin:

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. Değişken uzunluğu tamsayı kodlamalarını modelin gerektirdiği sabit uzunluğa göre yeniden boyutlandırın:

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. Girişi yüklenen TensorFlow modeliyle sınıflandırın:

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    TensorFlow model çıkışı çağrılır `Prediction/Softmax` . Adın `Prediction/Softmax` TensorFlow modeliyle belirlendiğini unutmayın. Bu adı değiştiremezsiniz.

1. Çıkış tahmini için yeni bir sütun oluşturun:

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    `Prediction/Softmax`Bir C# sınıfında bir özellik olarak kullanılabilecek bir ada sahip bir sütunu içine kopyalamanız gerekir: `Prediction` . `/`C# özellik adında karaktere izin verilmez.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>İşlem hattından ML.NET modeli oluşturma

1. Ardışık düzen aracılığıyla model oluşturmak için kodu ekleyin:

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    Yöntemi çağırarak, işlem hattındaki tahmini zincirinden bir ml.net modeli oluşturulur `Fit` . Bu durumda, TensorFlow modeli önceden eğitilen için, modeli oluşturmak üzere herhangi bir veri vermedik. Yöntemin gereksinimlerini karşılamak için boş bir veri görünümü nesnesi sağlıyoruz `Fit` .

## <a name="use-the-model-to-make-a-prediction"></a>Tahmin yapmak için modeli kullanma

1. Yönteminin `PredictSentiment` altına aşağıdaki yöntemi ekleyin `Main` :

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. `PredictionEngine`Yönteminin ilk satırı olarak oluşturmak için aşağıdaki kodu ekleyin `PredictSentiment()` :

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, `PredictionEnginePool` [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uygulamanız genelinde kullanılacak nesneleri oluşturan hizmetini kullanın. [ `PredictionEnginePool` ASP.NET Core Web API 'sinde kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.

    > [!NOTE]
    > `PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.

1. Bir örneği oluşturarak eğitilen modelin, yöntemi içindeki tahminini test etmek için bir açıklama ekleyin `Predict()` `MovieReview` :

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. `Prediction Engine`Yöntemine sonraki kod satırlarını ekleyerek test açıklama verilerini öğesine geçirin `PredictSentiment()` :

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. [Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar:

    |Özellik| Değer|Tür|
    |-------------|-----------------------|------|
    |Prediction (Tahmin)|[0,5459937, 0,454006255]|float []|

1. Aşağıdaki kodu kullanarak yaklaşım tahminini görüntüleyin:

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. Yönteminin sonuna bir çağrısı ekleyin `PredictSentiment` `Main` :

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Sonuçlar

Uygulamanızı derleyin ve çalıştırın.

Sonuçlarınız aşağıdakine benzer olmalıdır. İşlem sırasında iletiler görüntülenir. Uyarıları görebilir veya iletileri işleme alabilirsiniz. Bu iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Tebrikler! Artık ML.NET ' de önceden eğitilen bir modeli yeniden kullandığınızda, iletilerin sınıflandırılmasına ve tahmine yönelik bir makine öğrenimi modelini başarıyla oluşturdunuz `TensorFlow` .

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Önceden eğitilen bir TensorFlow modeli yükleme
> * Web sitesi açıklama metnini model için uygun özelliklere Dönüştür
> * Tahmin yapmak için modeli kullanma
