---
title: 'Öğretici: Analiz web sitesi yorumları - ikili sınıflandırma'
description: 'Bu öğretici, web sitesi yorumlarından duyguları sınıflandıran ve uygun eylemi yapan bir .NET Core konsol uygulamasının nasıl oluşturulabileceğinizi gösterir. İkili duygu sınıflandırıcı Visual Studio C # kullanır.'
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 47b9a9fe37cbcacab3797ed7fb1398b0c524d746
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241136"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Öğretici: ML.NET ikili sınıflandırma ile web sitesi yorumlarının duyarlılığını analiz edin

Bu öğretici, web sitesi yorumlarından duyguları sınıflandıran ve uygun eylemi yapan bir .NET Core konsol uygulamasının nasıl oluşturulabileceğinizi gösterir. İkili duygu sınıflandırıcısı Visual Studio 2017'de C# kullanır.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> - Konsol uygulaması oluşturma
> - Verileri hazırlama
> - Verileri yükleme
> - Modeli oluşturma ve eğitme
> - Modeli değerlendirme
> - Tahminde bulunmak için modeli kullanma
> - Sonuçları görme

Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core çapraz platform geliştirme" iş yükü yüklü

- [UCI Sentiment Etiketli Cümleler dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası)

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "SentimentAnalysis" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *Veri* adlı bir dizin oluşturun.

3. Microsoft.ML **NuGet Paketini**Yükleyin:

    Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin ve ardından **Gözat** sekmesini seçin. **Microsoft.ML**ara, istediğiniz paketi seçin ve sonra **Yükle** düğmesini seçin. Seçtiğiniz paketin lisans koşullarını kabul ederek yüklemeye devam edin. **Microsoft.ML.FastTree** NuGet paketi için aynı şeyi yapın.

## <a name="prepare-your-data"></a>Verilerinizi hazırlama

> [!NOTE]
> Bu öğretici için veri kümeleri 'Derin Özellikleri Kullanarak Gruptan Bireysel Etiketlere', Kotzias et. al,. KDD 2015 ve UCI Machine Learning Deposu - Dua, D. ve Karra Taniskidou, E. (2017) ev sahipliği yaptı. UCI Makine Öğrenme Deposuhttp://archive.ics.uci.edu/ml[ ]. Irvine, CA: Kaliforniya Üniversitesi, Bilgi ve Bilgisayar Bilimleri Fakültesi.

1. [INDIR UCI Sentiment Etiketli Cümleler dataset ZIP dosyası](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve unzip.

2. Dosyayı `yelp_labelled.txt` oluşturduğunuz *Veri* dizinine kopyalayın.

3. Çözüm Gezgini'nde dosyayı `yelp_labeled.txt` sağ tıklatın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıflar oluşturma ve yolları tanımlama

1. Aşağıdaki ek `using` deyimleri *Program.cs* dosyasının üstüne ekleyin:

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. En son indirilen dataset dosya `Main` yolunu tutmak için bir alan oluşturmak için yöntemin hemen üstündeki satıra aşağıdaki kodu ekleyin:

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. Ardından, giriş verileriniz ve öngörüleriniz için sınıflar oluşturun. Projenize yeni bir sınıf ekleyin:

    - **Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.

    - Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *SentimentData.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

1. *SentimentData.cs* dosyası kod düzenleyicisinde açılır. SentimentData.cs üstüne `using` aşağıdaki ifadeyi *SentimentData.cs*ekleyin:

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. Varolan sınıf tanımını kaldırın ve iki sınıfı `SentimentData` `SentimentPrediction`ve SentimentData.cs *dosyasına* aşağıdaki kodu ekleyin:

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Veriler nasıl hazırlandı?

Giriş `SentimentData`veri kümesi sınıfı, kullanıcı `string` yorumları için`SentimentText`bir `bool` (`Sentiment`) ve ( ) değeri 1 (pozitif) veya 0 (negatif) duyarlılık için vardır. Her iki alanda da, her alanın veri dosyası sırasını açıklayan [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri bunlara eklenir.  Buna ek `Sentiment` olarak, özellik `Label` alan olarak belirlemek için bir [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) özniteliği vardır. Aşağıdaki örnek dosyanın üstbilgi satırı yoktur ve aşağıdaki gibi görünür:

|SentimentText                         |Duygusallık (Etiket) |
|--------------------------------------|----------|
|Garson biraz yavaş hizmet etti.|    0     |
|Kabuk iyi değil.                    |    0     |
|Wow... Burayı çok severdim.              |    1     |
|Servis çok hızlı oldu.              |    1     |

`SentimentPrediction`model eğitiminden sonra kullanılan tahmin sınıfıdır. Girişin çıktı `SentimentData` tahminiyle birlikte `SentimentText` görüntülenebilmeleri için bu gelirden devralır. Boolean, `Prediction` modelin yeni girdiyle `SentimentText`birlikte verildiğinde öngördüğü değerdir.

Çıktı sınıfı `SentimentPrediction` model tarafından hesaplanan iki `Score` başka özellik içerir: - model `Probability` tarafından hesaplanan ham puan ve - pozitif duyarlılığa sahip metnin olasılığına kalibre edilen puan.

Bu öğretici için, en `Prediction`önemli özelliği .

## <a name="load-the-data"></a>Verileri yükleme

ML.NET'daki veriler [IDataView sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`tabular verileri (sayısal ve metin) tanımlamanın esnek ve etkili bir yoludur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı `IDataView` veya günlük dosyaları) bir nesneye yüklenebilir.

[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç noktasıdır. İlk `mlContext` başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur. Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.

Uygulamayı hazırlarsınız ve verileri yüklersiniz:

1. MlContext `Console.WriteLine("Hello World!")` değişkenini `Main` bildirmek ve başlatmak için yöntemdeki satırı aşağıdaki kodla değiştirin:

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. `Main()` Yöntemde bir sonraki kod satırı olarak aşağıdakileri ekleyin:

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. Yöntemden `LoadData()` `Main()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    Yöntem `LoadData()` aşağıdaki görevleri yürütür:

    - Verileri yükler.
    - Yüklenen veri kümesini tren ve test veri kümelerine böler.
    - Bölünmüş tren ve test veri kümelerini döndürür.

4. `LoadData()` Yöntemin ilk satırı olarak aşağıdaki kodu ekleyin:

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyada okur. Veri yolu değişkenlerini alır ve `IDataView`bir .

### <a name="split-the-dataset-for-model-training-and-testing"></a>Model eğitimi ve testi için veri kümesini bölme

Bir model hazırlarken, onu eğitmek için veri kümesinin bir kısmını ve modelin doğruluğunu test etmek için veri kümesinin bir kısmını kullanırsınız.

1. Yüklenen verileri gerekli veri kümelerine bölmek için `LoadData()` yöntemde bir sonraki satır olarak aşağıdaki kodu ekleyin:

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    Önceki kod, yüklenen veri kümesini tren ve test veri kümelerine bölmek ve [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) sınıfında döndürmek için [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) yöntemini kullanır. Parametreile verilerin test kümesi `testFraction`yüzdesini belirtin. Varsayılan değer %10'dur, bu durumda daha fazla veriyi değerlendirmek için %20'dir.

2. Yöntemin sonunda ki döndürme: `splitDataView` `LoadData()`

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Modeli oluşturma ve eğitme

1. Yöntemde `BuildAndTrainModel`bir sonraki kod satırı olarak yönteme `Main()` aşağıdaki çağrıyı ekleyin:

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    Yöntem `BuildAndTrainModel()` aşağıdaki görevleri yürütür:

    - Verileri ayıklar ve dönüştürür.
    - Modeli eğitir.
    - Test verilerine dayalı duyarlılığı tahmin eder.
    - Modeli döndürür.

2. Yöntemden `BuildAndTrainModel()` `Main()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Verileri ayıklayın ve dönüştürün

1. Bir `FeaturizeText` sonraki kod satırı olarak arayın:

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    Önceki `FeaturizeText()` koddaki yöntem metin sütununa`SentimentText`( ) makine öğrenme `Features` algoritması tarafından kullanılan sayısal anahtar türü sütununa dönüştürür ve yeni bir veri kümesi sütunu olarak ekler:

    |SentimentText                         |Yaklaşım |Özellikler              |
    |--------------------------------------|----------|----------------------|
    |Garson biraz yavaş hizmet etti.|    0     |[0.76, 0.65, 0.44, ...] |
    |Kabuk iyi değil.                    |    0     |[0.98, 0.43, 0.54, ...] |
    |Wow... Burayı çok severdim.              |    1     |[0.35, 0.73, 0.46, ...] |
    |Servis çok hızlı oldu.              |    1     |[0.39, 0, 0.75, ...]    |

### <a name="add-a-learning-algorithm"></a>Öğrenme algoritması ekleme

Bu uygulama, öğeleri veya veri satırlarını kategorilere ayıran bir sınıflandırma algoritması kullanır. Uygulama web sitesi yorumlarını olumlu veya olumsuz olarak kategorilere ayırır, bu nedenle ikili sınıflandırma görevini kullanın.

Bir sonraki kod satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarına makine `BuildAndTrainModel()`öğrenimi görevini ekleme:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) sınıflandırma eğitim algoritmasıdır. Bu, `estimator` geçmiş verilerden öğrenmek için featurized `SentimentText` ( `Label` `Features`) ve giriş parametrelerini kabul eder.

### <a name="train-the-model"></a>Modeli eğitme

Modeli `splitTrainSet` verilere sığdırın ve yöntemde bir sonraki kod satırı olarak `BuildAndTrainModel()` aşağıdakileri ekleyerek eğitilmiş modeli döndürün:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitir.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Değerlendirme için kullanılmak üzere eğitilmiş modeli döndürme

 Yöntemin sonunda modeli döndürün: `BuildAndTrainModel()`

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Modeliniz eğitildikten sonra, test verilerinizi modelin performansını doğrulayın.

1. `Evaluate()` Yöntemi aşağıdaki kodla `BuildAndTrainModel()`hemen sonra oluşturun:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    Yöntem `Evaluate()` aşağıdaki görevleri yürütür:

    - Test veri kümesini yükler.
    - İkili Sınıflandırma değerlendiricisi oluşturur.
    - Modeli değerlendirir ve ölçümler oluşturur.
    - Ölçümleri görüntüler.

2. Aşağıdaki kodu `Main()` kullanarak, yöntem çağrısının `BuildAndTrainModel()` hemen altında, yöntemden yeni yönteme çağrı ekleyin:

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Aşağıdaki `splitTestSet` kodu ekleyerek verileri dönüştürün: `Evaluate()`

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    Önceki kod, bir test veri kümesinin birden çok sağlanan giriş satırları için öngörüler yapmak için [Dönüştür()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.

4. Yöntemde bir sonraki kod satırı olarak aşağıdakileri `Evaluate()` ekleyerek modeli değerlendirin:

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

Tahmin kümesine sahip`predictions`olduktan sonra (), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi, öngörülen değerleri test veri `Labels` kümesindeki gerçek değerlerle karşılaştıran ve modelin nasıl performans gösterdiğine ilişkin [kalibreli BirLeştirilmişBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) nesnesini döndüren modeli değerlendirir.

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama için ölçümlerin görüntülenmesi

Ölçümleri görüntülemek için aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- `Accuracy` Metrik, test kümesindeki doğru tahminlerin oranı olan bir modelin doğruluğunu alır.

- Metrik, `AreaUnderRocCurve` modelin pozitif ve negatif sınıfları doğru bir şekilde sınıflandıracağından ne kadar emin olduğunu gösterir. Mümkün olduğunca `AreaUnderRocCurve` birine yakın olmasını istiyorsun.

- `F1Score` Metrik, [modelin](../resources/glossary.md#precision) F1 puanını alır, bu da hassasiyet ve [geri çağırma](../resources/glossary.md#recall)arasındaki dengenin bir ölçüsüdür.  Mümkün olduğunca `F1Score` birine yakın olmasını istiyorsun.

### <a name="predict-the-test-data-outcome"></a>Test verisi sonucunu tahmin etme

1. Yöntemden `UseModelWithSingleItem()` `Evaluate()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Yöntem `UseModelWithSingleItem()` aşağıdaki görevleri yürütür:

    - Test verilerinin tek bir yorumunu oluşturur.
    - Test verilerine dayalı duyarlılığı tahmin eder.
    - Raporlama için test verilerini ve öngörüleri birleştirir.
    - Öngörülen sonuçları görüntüler.

2. Aşağıdaki kodu `Main()` kullanarak, yöntem çağrısının `Evaluate()` hemen altında, yöntemden yeni yönteme çağrı ekleyin:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. `UseModelWithSingleItem()` Yöntem'de ilk satır olarak oluşturmak için aşağıdaki kodu ekleyin:

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir. Tek dişli veya prototip ortamlarda kullanılabilir. Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın. ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.

    > [!NOTE]
    > `PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.

4. Bir örnek oluşturarak `UseModelWithSingleItem()` yöntemde eğitimli modelin tahminsına test `SentimentData`etmek için bir açıklama ekleyin:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Yöntemde bir sonraki [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) kod satırı olarak aşağıdakileri ekleyerek test `UseModelWithSingleItem()` yorum verilerini geçirin:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar.

6. Aşağıdaki `SentimentText` kodu kullanarak görüntülenmesi ve buna karşılık gelen duyarlılık tahmini:

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Tahmin için modeli kullanma

### <a name="deploy-and-predict-batch-items"></a>Toplu iş öğelerini dağıtma ve tahmin etme

1. Yöntemden `UseModelWithBatchItems()` `UseModelWithSingleItem()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    Yöntem `UseModelWithBatchItems()` aşağıdaki görevleri yürütür:

    - Toplu test verileri oluşturur.
    - Test verilerine dayalı duyarlılığı tahmin eder.
    - Raporlama için test verilerini ve öngörüleri birleştirir.
    - Öngörülen sonuçları görüntüler.

2. Aşağıdaki kodu `Main` kullanarak, yöntem çağrısının `UseModelWithSingleItem()` hemen altında, yöntemden yeni yönteme çağrı ekleyin:

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. `UseModelWithBatchItems()` Yöntemde eğitimli modelin öngörülerini sınamak için bazı açıklamalar ekleyin:

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Yorum duyarlılığını tahmin edin

[Dönüştür()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak yorum veri duyarlılığını tahmin etmek için modeli kullanın:

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Tahminleri birleştirin ve görüntüleyin

Aşağıdaki kodu kullanarak öngörüler için bir üstbilgi oluşturun:

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

Çünkü, `SentimentPrediction` `SentimentData` `Transform()` tahmin edilen alanları ile `SentimentText` doldurulan yöntem devralır. ML.NET işlem işlendikçe, her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Sonuçlar

Sonuçlarınız aşağıdakilere benzer olmalıdır. İşlem sırasında iletiler görüntülenir. Uyarılar veya iletileri işleme görebilirsiniz. Bunlar netlik için aşağıdaki sonuçlardan kaldırılmıştır.

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

Tebrikler! İletilerin duyarlılığını sınıflandırmak ve tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturmuşsunuz.

Başarılı modeller oluşturmak yinelemeli bir işlemdir. Öğretici hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu model in ilk düşük kaliteye sahiptir. Model kalitesinden memnun değilseniz, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı [hiper parametrelere](../resources/glossary.md#hyperparameter) sahip farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.

Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Konsol uygulaması oluşturma
> - Verileri hazırlama
> - Verileri yükleme
> - Modeli oluşturma ve eğitme
> - Modeli değerlendirme
> - Tahminde bulunmak için modeli kullanma
> - Sonuçları görme

Daha fazla bilgi edinmek için bir sonraki öğreticiye ilerleyin
> [!div class="nextstepaction"]
> [Konu Sınıflandırması](github-issue-classification.md)
