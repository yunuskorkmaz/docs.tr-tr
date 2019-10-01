---
title: 'Öğretici: önceden eğitilen bir TensorFlow modeli kullanarak film incelemelerinin yaklaşımını çözümleyin'
description: Bu öğreticide, Web sitesi açıklamalarında yaklaşımı sınıflandırmak için önceden eğitilen bir TensorFlow modelinin nasıl kullanılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio kullanılarak C# geliştirilen bir konsol uygulamasıdır.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: e25e884769ad62d3d888986b1475000b543b24b1
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700933"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Öğretici: ML.NET 'de önceden eğitilen bir TensorFlow modeli kullanarak film incelemelerinin yaklaşımını çözümleyin

Bu öğreticide, Web sitesi açıklamalarında yaklaşımı sınıflandırmak için önceden eğitilen bir TensorFlow modelinin nasıl kullanılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio kullanılarak C# geliştirilen bir konsol uygulamasıdır.

Bu öğreticide kullanılan TensorFlow modeli, ıMDB veritabanından Film İncelemeleri kullanılarak eğitildi. Uygulamayı geliştirmeyi bitirdikten sonra, film gözden geçirme metni sağlayabileceksiniz ve uygulama Gözden geçirmedeki pozitif veya negatif bir yaklaşım olup olmadığını söyleyecektir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Önceden eğitilen bir TensorFlow modeli yükleme
> * Web sitesi açıklama metnini model için uygun özelliklere Dönüştür
> * Tahmin yapmak için modeli kullanma

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Prerequisites

* [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="setup"></a>Kurulum

### <a name="create-the-application"></a>Uygulamayı oluşturma

1. "TextClassificationTF" adlı bir **.NET Core konsol uygulaması** oluşturun.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.

3. **Microsoft.ml NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin ve sonra da **tarayıcı** sekmesini seçin. **Microsoft.ml**için arama yapın, istediğiniz paketi seçin ve sonra da **Install** düğmesini seçin. Kabul etmiş ile yüklemeye, seçtiğiniz paketin lisans koşullarına devam edin. **Microsoft. ml. TensorFlow**için bu adımları tekrarlayın.

### <a name="add-the-tensorflow-model-to-the-project"></a>TensorFlow modelini projeye ekleme

> [!NOTE]
> Bu öğreticinin modeli [DotNet/machinöğrenim-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub deposundan. Model, TensorFlow SavedModel biçimindedir.

1. [Sentiment_model ZIP dosyasını](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)indirin ve sıkıştırmayı açın.

    ZIP dosyası şunları içerir:

    * `saved_model.pb`: TensorFlow modelinin kendisi. Model, bir ıMDB İnceleme dizesindeki metni temsil eden özelliklerin sabit bir uzunluğunu (boyut 600) tamsayı dizisini alır ve 1 ' e kadar olan iki olasılıkların çıkışını verir: giriş incelemesinin pozitif yaklaşım olduğu ve giriş incelemesinin sahip olduğu olasılık negatif yaklaşım.
    * `imdb_word_index.csv`: tek sözcüklerden bir tamsayı değere eşleme. Eşleme, TensorFlow modelinin giriş özelliklerini oluşturmak için kullanılır.

2. En içteki `sentiment_model` dizininin içeriğini *TextClassificationTF* projenizin `sentiment_model` dizinine kopyalayın. Bu dizin, aşağıdaki görüntüde gösterildiği gibi, bu öğretici için gereken modeli ve ek destek dosyalarını içerir:

   ![sentiment_model Dizin içeriği](./media/text-classification-tf/sentiment-model-files.png)

3. Çözüm Gezgini, `sentiment_model` Dizin ve alt dizinindeki dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

### <a name="add-using-statements-and-global-variables"></a>Using deyimleri ve genel değişkenler ekleme

1. *Program.cs* dosyasının en üstüne aşağıdaki ek `using` deyimlerini ekleyin:

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. Kaydedilen model dosyası yolunu ve özellik vektörü uzunluğunu tutmak için `Main` yönteminin üzerinde doğrudan iki genel değişken oluşturun.

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`, eğitilen modelin dosya yoludur.
    * `FeatureLength`, modelin beklediği tamsayı özelliği dizisinin uzunluğudur.

### <a name="model-the-data"></a>Verileri modelleyin

Film İncelemeleri, ücretsiz form metinlerdir. Uygulamanız, metni bir dizi farklı aşamada model tarafından beklenen giriş biçimine dönüştürür.

Birincisi, metni ayrı sözcüklere bölmek ve her bir sözcüğü bir tamsayı kodlamasıyla eşlemek için belirtilen eşleme dosyasını kullanmaktır. Bu dönüştürmenin sonucu, tümcedeki sözcüklerin sayısına karşılık gelen uzunluğa sahip bir değişken uzunluklu tamsayı dizisidir.

|Özellik| Değer|Tür|
|-------------|-----------------------|------|
|Belgemetinmetni|Bu film gerçekten iyi|dize|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|

Değişken uzunluğu özellik dizisi daha sonra sabit 600 uzunluğuna yeniden boyutlandırılır. Bu, TensorFlow modelinin beklediği uzunluktadır.

|Özellik| Değer|Tür|
|-------------|-----------------------|------|
|Belgemetinmetni|Bu film gerçekten iyi|dize|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|
|Özellikler|14, 22, 9, 66, 78,... |Tamsayı [600]|

1. @No__t-0 yönteminden sonra giriş verileriniz için bir sınıf oluşturun:

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    @No__t-0 olan giriş veri sınıfında kullanıcı açıklamaları için bir `string` (`ReviewText`) vardır.

1. @No__t-0 yönteminden sonra değişken uzunluklu özellikler için bir sınıf oluşturun:

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    @No__t-0 özelliğinin vektör olarak belirlemek için bir [Vectortype](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) özniteliği vardır.  Tüm vektör öğeleri aynı türde olmalıdır. Çok sayıda sütun içeren veri kümelerinde, birden fazla sütunu tek bir vektör olarak yüklemek, veri dönüştürmeleri uyguladığınızda veri geçişlerinin sayısını azaltır.

    Bu sınıf `ResizeFeatures` eyleminde kullanılır. Özelliklerinin adları (Bu durumda yalnızca bir tane), DataView içindeki hangi sütunların özel eşleme eylemine _giriş_ olarak kullanılabileceğini göstermek için kullanılır.

1. @No__t-0 yönteminden sonra sabit uzunluklu özellikler için bir sınıf oluşturun:

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    Bu sınıf `ResizeFeatures` eyleminde kullanılır. Özelliklerinin adları (Bu durumda yalnızca bir tane), DataView içindeki hangi sütunların özel eşleme eyleminin _çıktısı_ olarak kullanılabileceğini göstermek için kullanılır.

    @No__t-0 özelliğinin adının TensorFlow modeliyle belirlendiğini unutmayın. Bu özellik adını değiştiremezsiniz.

1. @No__t-0 yönteminden sonra tahmin için bir sınıf oluşturun:

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction`, model eğitiminden sonra kullanılan tahmin sınıfıdır. `MovieReviewSentimentPrediction` tek bir `float` dizisine (`Prediction`) ve `VectorType` özniteliğine sahiptir.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Özellikleri yeniden boyutlandırmak için MLContext, arama sözlüğü ve eylemi oluşturma

[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır. @No__t başlatılıyor-0, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur. Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.

1. @No__t-1 yöntemindeki `Console.WriteLine("Hello World!")` satırını, mlContext değişkenini bildirmek ve başlatmak için aşağıdaki kodla değiştirin:

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. Aşağıdaki tabloda görüldüğü gibi, bir dosyadan eşleme verilerini yüklemek için [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) metodunu kullanarak sözcükleri tamsayı olarak kodlamak için bir sözlük oluşturun:

    |Word     |Dizin    |
    |---------|---------|
    |öğre     |  362    |
    |istiyorum     |  181    |
    |yanlış    |  355    |
    |efektler  |  302    |
    |rahatsızlık  |  547    |

    Arama eşlemesini oluşturmak için aşağıdaki kodu ekleyin:

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. Değişken uzunluklu kelime tamsayı dizisinin bir sonraki kod satırı ile sabit boyutlu bir tamsayı dizisine yeniden boyutlandırılması için bir `Action` ekleyin:

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Önceden eğitilen TensorFlow modelini yükleme

1. TensorFlow modelini yüklemek için kod ekleyin:

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    Model yüklendikten sonra, giriş ve çıkış şemasını ayıklayabilirsiniz. Şemalar yalnızca ilgi ve öğrenme için görüntülenir. Son uygulamanın çalışması için bu koda ihtiyacınız yoktur:

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    Giriş şeması, tamsayı kodlamalı sözcüklerin sabit uzunluklu dizisidir. Çıktı şeması, bir gözden geçirme yaklaşımını negatif mi yoksa pozitif mi olduğunu gösteren bir dizi olasılıkların dizisidir. Bu değerler, pozitif olma olasılığı olarak 1 ' e kadar toplamdır.

## <a name="create-the-mlnet-pipeline"></a>ML.NET işlem hattını oluşturma

1. Bir sonraki kod satırı olarak sözcükleri sözcüklere eklemek için, işlem hattını oluşturun ve giriş metnini [Tokenizeıntowords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) dönüşümünü kullanarak sözcüklere bölün:

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   [Tokenizeıntowords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) dönüşümü, metni/dizeyi sözcüklere ayrıştırmak için boşluk kullanır. Yeni bir sütun oluşturur ve her giriş dizesini Kullanıcı tanımlı ayırıcıya göre alt dizelerin vektörüne böler.

1. Yukarıda bildirdiğiniz arama tablosunu kullanarak kelimeleri tamsayı kodlamasıyla eşleyin:

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. Değişken uzunluğu tamsayı kodlamalarını modelin gerektirdiği sabit uzunluğa göre yeniden boyutlandırın:

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. Girişi yüklenen TensorFlow modeliyle sınıflandırın:

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    TensorFlow model çıkışı `Prediction/Softmax` olarak adlandırılır. @No__t-0 adının TensorFlow modeliyle belirlendiğini unutmayın. Bu adı değiştiremezsiniz.

1. Çıkış tahmini için yeni bir sütun oluşturun:

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    @No__t-0 sütununu bir C# sınıfta özellik olarak kullanılabilecek bir adla birine kopyalamanız gerekir: `Prediction`. C# Özellik adında `/` karakterine izin verilmez.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>İşlem hattından ML.NET modeli oluşturma

1. Ardışık düzen aracılığıyla model oluşturmak için kodu ekleyin:

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    @No__t-0 yöntemini çağırarak, işlem hattındaki tahmini zincirinden bir ml.net modeli oluşturulur. Bu durumda, TensorFlow modeli önceden eğitilen için, modeli oluşturmak üzere herhangi bir veri vermedik. @No__t-0 yönteminin gereksinimlerini karşılamak için boş bir veri görünümü nesnesi sağlıyoruz.

## <a name="use-the-model-to-make-a-prediction"></a>Tahmin yapmak için modeli kullanma

1. @No__t-1 yönteminin altına `PredictSentiment` yöntemini ekleyin:

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. @No__t-1 yönteminde ilk satır olarak `PredictionEngine` oluşturmak için aşağıdaki kodu ekleyin:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın. [ASP.NET Core Web API 'sinde `PredictionEnginePool` ' i nasıl kullanacağınızı](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) öğrenmek için bu kılavuza bakın

    > [!NOTE]
    > `PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.

1. @No__t-1 ' in bir örneğini oluşturarak eğitilen modelin tahminini `Predict()` yönteminde test etmek için bir açıklama ekleyin:

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. @No__t-1 yöntemine sonraki kod satırlarını ekleyerek test açıklama verilerini `Prediction Engine` ' a geçirin:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. [Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar:

    |Özellik| Değer|Tür|
    |-------------|-----------------------|------|
    |hızlı|[0,5459937, 0,454006255]|float []|

1. Aşağıdaki kodu kullanarak yaklaşım tahminini görüntüleyin:

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. @No__t-1 yönteminin sonundaki `PredictSentiment` ' a bir çağrı ekleyin:

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Sonuçlar

Uygulamanızı derleyin ve çalıştırın.

Sonuçlarınız aşağıdakine benzer olmalıdır. İşlem sırasında iletiler görüntülenir. Uyarıları görebilir veya iletileri işleme alabilirsiniz. Bu iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Mühendisi! ML.NET ' de önceden eğitilen bir `TensorFlow` modelini yeniden çalıştırarak, ileti yaklaşımını sınıflandırma ve tahmin etme için bir makine öğrenimi modelini başarıyla oluşturdunuz.

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) deposunda bulabilirsiniz.

Bu öğreticide, nasıl yapılacağını öğrendiniz:
> [!div class="checklist"]
>
> * Önceden eğitilen bir TensorFlow modeli yükleme
> * Web sitesi açıklama metnini model için uygun özelliklere Dönüştür
> * Tahmin yapmak için modeli kullanma
