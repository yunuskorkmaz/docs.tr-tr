---
title: 'Öğretici: Web sitesi açıklamaları - ikili sınıflandırma analiz edin'
description: Bu öğreticide, elde edilen Web sitesi açıklamaları duyarlılığı sınıflandırır ve uygun tedbiri alır bir .NET Core konsol uygulaması oluşturma işlemini gösterir. İkili yaklaşım sınıflandırıcı kullanan C# Visual Studio 2017'de.
ms.date: 04/18/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 1989a11a2f06ce4d713d6c3ecc70de0da606604e
ms.sourcegitcommit: 438824ff21f77c4301c6ba8a89a106114aa27bc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65462226"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Öğretici: ML.NET ikili sınıflandırma ile Web sitesi yorumların düşüncelerini çözümleme

Bu öğreticide, elde edilen Web sitesi açıklamaları duyarlılığı sınıflandırır ve uygun tedbiri alır bir .NET Core konsol uygulaması oluşturma işlemini gösterir. İkili yaklaşım sınıflandırıcı kullanan C# Visual Studio 2017'de. 

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * Konsol uygulaması oluşturma
> * Verileri hazırlama
> * Verileri yükleme
> * Derleme ve modeli eğitme
> * Modeli değerlendirme
> * Model bir tahminde kullanmak
> * Sonuçları göster

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır

* [UCI yaklaşım cümleler etiketli veri kümesini](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası)

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Oluşturma bir **.NET Core konsol uygulaması** "SentimentAnalysis" denir.

2. Adlı bir dizin oluşturmak *veri* , projenizdeki veri kümesi dosyalarınızı kaydeder.

3. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin ve ardından **Gözat** sekmesi. Arama **Microsoft.ML**, seçin ve ardından paketi **yükleme** düğmesi. Kuruluma devam etmek için kabul ederek, seçtiğiniz paket için lisans koşulları. İçin de aynısını yapın **Microsoft.ML.FastTree** NuGet paketi.

## <a name="prepare-your-data"></a>Verilerinizi hazırlama

> [!NOTE]
> Bu öğretici için veri kümeleri Kotzias 'kaynak grubundan ayrıntılı özelliklerini kullanarak her bir etiketi için' olan et. Al. 2015 ve barındırılan KDD UCI Machine Learning deposu - Dua, d ve Karra Taniskidou, e (2017). UCI Makine deposu [http://archive.ics.uci.edu/ml]. Irvine, CA: California Üniversitesi, okul bilgi ve bilgisayar Bilimine.

1. İndirme [UCI yaklaşım cümleler etiketli veri kümesini ZIP dosyası](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve sıkıştırmasını açın.

2. Kopyalama `yelp_labelled.txt` doyasını *veri* oluşturduğunuz dizin.

3. Çözüm Gezgini'nde sağ `yelp_labeled.txt` seçin ve dosya **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

### <a name="create-classes-and-define-paths"></a>Yollarını tanımlamak ve sınıfları oluşturma

1. Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. En son indirilen veri kümesi dosyası yolu ve kayıtlı modeli dosya yolu tutmak için iki genel alanlar oluşturun:

    * `_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.
    * `_modelPath` eğitilen modelin kaydedildiği yolu vardır.

3. Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi yollarını belirtmek için:

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. Ardından, girdi verilerini ve Öngörüler için sınıflar oluşturun. Yeni bir sınıf, projenize ekleyin:

    - İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

    - İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*. Ardından, **Ekle** düğmesi.

    
5. *SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Verilerin nasıl hazırlanmıştır
Giriş veri kümesi sınıfı `SentimentData`, sahip bir `string` kullanıcı yorumları için (`SentimentText`) ve bir `bool` (`Sentiment`) değeri 1 (pozitif) veya yaklaşım için 0 (negatif). Her iki alanınız [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri bağlı, her bir alanın veri dosyası siparişi açıklar.  Ayrıca, `Sentiment` özelliğine sahip bir [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) olarak belirtmek için özniteliği `Label` alan. Aşağıdaki örnek dosyası, bir başlık satırı yok ve şöyle görünür:

|SentimentText                         |Yaklaşım (etiketi) |
|--------------------------------------|----------|
|Waitress hizmetinde biraz yavaş.|    0     |
|Kabuk iyi değil.                    |    0     |
|WOW... Burası sevdiği.              |    1.     |
|Hizmet çok sor.              |    1.     |

`SentimentPrediction` Tahmin sınıf, model eğitiminin sonra kullanılır. Devraldığı `SentimentData` görüntülemek için `SentimentText` Öngörüler ile. `SentimentPrediction` sahip tek bir Boole değeri (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği. `Label` Oluşturabilir ve ayrıca bölünmüş test veri kümesini kullanıma ile model değerlendirmek için kullanılan model ya da onun eğitmek için kullanılır. `PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme, eğitim verileri, tahmin edilen değerleri ve modeli kullanılır.

[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç noktasıdır. Başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur. Bu, kavramsal olarak, benzer `DBContext` Entity Framework.

## <a name="load-the-data"></a>Verileri yükleme
ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.ML.IDataView). `IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur. Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne.

Uygulamayı hazırlama ve ardından veri yükleyebilirsiniz:

1. Değiştirin `Console.WriteLine("Hello World!")` satırına `Main` mlContext değişkeni bildirmek ve başlatmak için aşağıdaki kod ile yöntemi:

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. Sonraki kod satırı olarak ekleyin `Main()` yöntemi:

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. Oluşturma `LoadData()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    `LoadData()` Yöntemi aşağıdaki görevleri yürütür:

    * Verileri yükler.
    *  Yüklenen veri kümesi train böler ve test edin, veri kümeleri.
    * Bölme döndürür eğitme ve test etme, veri kümeleri.

4. İlk satırı olarak aşağıdaki kodu ekleyin `LoadData()` yöntemi:

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur. Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Eğitim ve test modeli için veri kümesi bölünemiyor

Bir model hazırlarken ve modelin doğruluğunu test etmek için veri kümesinin parçası eğitmek için veri kümesinin parçası kullanın.  

1. Yüklenen verilere gerekli veri kümelerine ayırmak için bir sonraki satırda olarak aşağıdaki kodu ekleyin `LoadData()` yöntemi:

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    Önceki kod [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) train yüklenen veri kümesi bölün ve veri kümeleri sınayabilir ve bunları yöntemi [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) sınıfı. Test verileri ile yüzdesi belirlemek `testFraction`parametresi. Varsayılan % 10, bu durumda, % 20 daha fazla veri değerlendirmek için kullanın.  

2. Dönüş `splitDataView` sonunda `LoadData()` yöntemi:

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Derleme ve modeli eğitme

1. Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main()` yöntemi:

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    `BuildAndTrainModel()` Yöntemi aşağıdaki görevleri yürütür:

    * Ayıklar ve verileri dönüştürür.
    * Modeli eğitir.
    * Test verilerine dayalı yaklaşım tahmin eder.
    * Model döndürür.

2. Oluşturma `BuildAndTrainModel()` yöntemi hemen sonrasına `Main()` yöntemi, aşağıdaki kodu kullanarak:
    
    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Verileri dönüştürme ve ayıklama

1. Çağrı `FeaturizeText` sonraki kod satırına olarak:

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    `FeaturizeText()` Yöntemi önceki kodda, metin sütununu dönüştürür (`SentimentText`) sayısal bir anahtar türü `Features` sütun makine öğrenimi algoritması tarafından kullanılan ve yeni veri kümesi bir sütun olarak ekler:

    |SentimentText                         |Yaklaşım |Özellikler              |
    |--------------------------------------|----------|----------------------|
    |Waitress hizmetinde biraz yavaş.|    0     |[0.76, 0.65, 0.44, …] |
    |Kabuk iyi değil.                    |    0     |[0.98, 0.43, 0.54, …] |
    |WOW... Burası sevdiği.              |    1.     |[0.35, 0.73, 0.46, …] |
    |Hizmet çok sor.              |    1.     |[0.39, 0, 0.75, …]    |

### <a name="add-a-learning-algorithm"></a>Bir öğrenme algoritması Ekle

Bu uygulama, öğeleri veya veri satırı kategorilere ayıran bir sınıflandırma algoritmasıdır kullanır. Uygulama Web sitesi açıklamaları artı veya eksi olarak kategorilere ayırır, ikili sınıflandırma görevi kullanın.

Machine learning görev sonraki kod satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarını ekleme `BuildAndTrainModel()`:

    
[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

    
[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) sınıflandırma eğitim algoritmasıdır. Bu eklenen `estimator` ve özellikleri tespit `SentimentText` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.

### <a name="train-the-model"></a>Modeli eğitme

Modele uygun `splitTrainSet` veri ve sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen model dönüş `BuildAndTrainModel()` yöntemi:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Değerlendirme için kullanılacak modeli eğitilir döndürür

 Model sonunda dönüş `BuildAndTrainModel()` yöntemi:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Modelinizi eğitildi sonra testinizi kullanın veri modelinin performans doğrulayın. 

1. Oluşturma `Evaluate()` yöntemi hemen sonrasına `BuildAndTrainModel()`, aşağıdaki kod ile:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    `Evaluate()` Yöntemi aşağıdaki görevleri yürütür:

    * Test veri kümesini yükler.
    * BinaryClassification değerlendirici oluşturur.
    * Model değerlendirir ve ölçüm oluşturur.
    * Ölçümleri görüntüler.

2. Yeni yönteme bir çağrı ekleyin `Main()` yöntemi, sağda altında `BuildAndTrainModel()` yöntemi çağrısı, aşağıdaki kodu kullanarak:

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Dönüştürme `splitTestSet` aşağıdakileri ekleyerek veri kod için `Evaluate()`:

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    Önceki kod [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) birden çok test veri kümesini girdi satırları sağlanan için tahminde bulunmak için yöntemi.

4. Sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirme `Evaluate()` yöntemi:

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

Ayarlama tahmin aldıktan sonra (`predictions`), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi değerlendirir gerçek tahmin edilen değerlerle karşılaştırır modeli `Labels` test veri kümesini ve döndürür bir [ CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) modelin nasıl performans gösterdiğini üzerinde nesne.

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama için ölçümleri görüntüleme

Ölçümleri görüntülemek için aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* `Accuracy` Ölçüm doğru tahminler elde etmek test kümesindeki oranı olan bir model doğruluğunu alır.

* `AreaUnderRocCurve` Ölçüm nasıl başarılara model doğru pozitif ve negatif sınıfları sınıflandırma olduğunu gösterir. İstediğiniz `AreaUnderRocCurve` biri olarak mümkün olduğunca yakın olmasını.

* `F1Score` Ölçüm Bakiye ölçüsüdür modelin F1 puanı alır arasında [duyarlık](../resources/glossary.md#precision) ve [geri çağırma](../resources/glossary.md#recall).  İstediğiniz `F1Score` biri olarak mümkün olduğunca yakın olmasını.

### <a name="predict-the-test-data-outcome"></a>Test verileri sonucu tahmin edin

1. Oluşturma `UseModelWithSingleItem()` yöntemi hemen sonrasına `Evaluate()` yöntemi, aşağıdaki kodu kullanarak:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithSingleItem()` Yöntemi aşağıdaki görevleri yürütür:

    * Test verilerini tek bir yorum oluşturur.
    * Test verilerine dayalı yaklaşım tahmin eder.
    * Bir araya getirir, verileri ve raporlama için Öngörüler test edin.
    * Tahmin edilen sonuçları görüntüler.

2. Yeni yönteme bir çağrı ekleyin `Main()` yöntemi, sağda altında `Evaluate()` yöntemi çağrısı, aşağıdaki kodu kullanarak:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. ilk satırı olarak oluşturmak için aşağıdaki kodu ekleyin `Predict()` yöntemi:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) geçirin ve ardından verileri tek bir örneğini tahmin gerçekleştirin izin veren bir kolaylık API, bir özelliktir.
  
4. Eğitilen modelin tahmine test etmek için bir açıklama ekleyin `Predict()` bir örneğini oluşturarak yöntemi `SentimentData`:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Test açıklaması verileri geçirmek `Prediction Engine` aşağıdaki kodda bir sonraki satırı olarak ekleyerek `UseModelWithSingleItem()` yöntemi:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi verilerin tek bir satırda bir tahmin sağlar.

6. Görüntü `SentimentText` ve aşağıdaki kodu kullanarak ilgili yaklaşım tahmin:

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Model için tahmin kullanın

### <a name="deploy-and-predict-batch-items"></a>Toplu iş öğeleri tahmin edin ve dağıtın

1. Oluşturma `UseModelWithBatchItems()` yöntemi hemen sonrasına `UseModelWithSingleItem()` yöntemi, aşağıdaki kodu kullanarak:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext)
    {

    }
    ```

    `UseModelWithBatchItems()` Yöntemi aşağıdaki görevleri yürütür:

    * Toplu test verilerini oluşturur.
    * Test verilerine dayalı yaklaşım tahmin eder.
    * Bir araya getirir, verileri ve raporlama için Öngörüler test edin.
    * Tahmin edilen sonuçları görüntüler.

2. Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `UseModelWithSingleItem()` yöntemi çağrısı, aşağıdaki kodu kullanarak:

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `UseModelWithBatchItems()` yöntemi:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Açıklama yaklaşım tahmin edin

Açıklama veri yaklaşım kullanarak tahmin modelini kullanan [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Birleştirme ve Öngörüler görüntüleme

Aşağıdaki kodu kullanarak tahminler elde etmek için bir başlık oluşturun:

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Çünkü `SentimentPrediction` devralındı `SentimentData`, `Transform()` doldurulmuş yöntemi `SentimentText` tahmin edilen alanlara sahip. ML.NET işlemi işlerken, her bileşen sütunları ekler ve bu sonuçları görüntülemek kolaylaştırır:

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Sonuçlar

Sonuçlar aşağıdakine benzer olmalıdır. İşleme sırasında iletileri görüntülenir. Uyarıları ve iletileri işlemeyi görebilirsiniz. Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

Tebrikler! Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz.

Başarılı modeller oluşturma yinelemeli bir işlemdir. Bu model düşük ilk kalite hızlı modeli eğitimi sağlamak için öğretici kullanan küçük veri kümeleri sahiptir. Model kalitesi memnun değilseniz farklı farklı eğitim algoritmalarıyla seçerek ya da daha büyük bir eğitim veri kümeleri sağlayarak geliştirmek deneyebilirsiniz [hyper-parametreleriyle](../resources/glossary.md##hyperparameter) her bir algoritmanın için.

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> * Konsol uygulaması oluşturma
> * Verileri hazırlama
> * Verileri yükleme
> * Derleme ve modeli eğitme
> * Modeli değerlendirme
> * Model bir tahminde kullanmak
> * Sonuçları göster

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Sorun sınıflandırması](github-issue-classification.md)
