---
title: 'Öğretici: Web sitesi açıklamalarını çözümleme-ikili sınıflandırma'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio 'Da C# kullanır.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: de8ea511b3d421e391b182a6de079b854d3f2390
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281764"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Öğretici: ML.NET 'de ikili sınıflandırmayla Web sitesi açıklamalarını çözümleyin

Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio 2017 ' de C# kullanır.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:
> [!div class="checklist"]
>
> - Konsol uygulaması oluşturma
> - Verileri hazırlama
> - Verileri yükleme
> - Model oluşturma ve eğitme
> - Modeli değerlendirme
> - Tahmin yapmak için modeli kullanma
> - Sonuçları görme

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

- [Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi

- [UCI yaklaşım cümleler veri kümesi](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası) etiketli

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "SentimentAnalysis" adlı bir **.NET Core konsol uygulaması** oluşturun.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.

3. **Microsoft.ml NuGet paketini**yükler:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin ve sonra da **tarayıcı** sekmesini seçin. **Microsoft.ml**için arama yapın, istediğiniz paketi seçin ve sonra da **Install** düğmesini seçin. Kabul etmiş ile yüklemeye, seçtiğiniz paketin lisans koşullarına devam edin.

## <a name="prepare-your-data"></a>Verilerinizi hazırlama

> [!NOTE]
> Bu öğreticinin veri kümeleri, ' Kimden grubundan, derin özellikler kullanılarak tekil etiketlere, Kotzıas et ' e ait. Al,. KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017). UCI Machine Learning deposu [ http://archive.ics.uci.edu/ml ]. Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.

1. [Utiment, cümleler veri KÜMESI ZIP dosyası](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve unzip 'i indirin.

2. `yelp_labelled.txt`Dosyayı oluşturduğunuz *veri* dizinine kopyalayın.

3. Çözüm Gezgini, dosyaya sağ tıklayın `yelp_labeled.txt` ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

1. Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. `Main`Son indirilen veri kümesi dosya yolunu tutacak bir alan oluşturmak için aşağıdaki kodu metodun hemen üstüne ekleyin:

    [!code-csharp[Declare global variables](./snippets/sentiment-analysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. Ardından, giriş verileriniz ve tahminlerinizi için sınıflar oluşturun. Projenize yeni bir sınıf ekleyin:

    - **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.

    - **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

1. *SentimentData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadeyi *SentimentData.cs*öğesinin en üstüne ekleyin:

    [!code-csharp[AddUsings](./snippets/sentiment-analysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. Mevcut sınıf tanımını kaldırın ve iki sınıfa `SentimentData` ve `SentimentPrediction` *SentimentData.cs* dosyasına sahip olan aşağıdaki kodu ekleyin:

    [!code-csharp[DeclareTypes](./snippets/sentiment-analysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Verilerin nasıl hazırlandığını

Giriş veri kümesi sınıfı, `SentimentData` bir `string` for User Comments ( `SentimentText` ) ve bir `bool` ( `Sentiment` ) değeri için 1 (pozitif) ya da 0 (negatif) değerine sahiptir. Her iki alana de eklenen [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri vardır ve bu, her alanın veri dosyası sırasını açıklar.  Ayrıca, `Sentiment` özelliği alanı olarak belirlemek için bir [sütunadı](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) özniteliği vardır `Label` . Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:

|Sentimentmetni                         |Yaklaşım (etiket) |
|--------------------------------------|----------|
|Waitress, hizmette çok yavaş.|    0     |
|Crust iyi değil.                    |    0     |
|Wow... Bu yere iner.              |    1     |
|Hizmet çok soriydi.              |    1     |

`SentimentPrediction`, model eğitiminden sonra kullanılan tahmin sınıfıdır. `SentimentData`Girişin `SentimentText` Çıkış tahminiyle birlikte görüntülenebilmesini sağlayacak şekilde öğesinden devralır. `Prediction`Boole değeri, modelin yeni girişle sağlandığı sırada tahmin edilen değerdir `SentimentText` .

Çıkış sınıfı, `SentimentPrediction` model tarafından hesaplanan iki diğer özellik içerir: `Score` -model tarafından hesaplanan ham puan ve, `Probability` pozitif yaklaşım olan metnin olasılığına ayarlanmış puan.

Bu öğretici için en önemli özellik ' dir `Prediction` .

## <a name="load-the-data"></a>Verileri yükleme

ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.

[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır. Başlatma `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilecek yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal olarak da benzerdir `DBContext` .

Uygulamayı hazırlayın ve sonra verileri yükleyin:

1. `Console.WriteLine("Hello World!")` `Main` Mlcontext değişkenini bildirmek ve başlatmak için yöntemindeki satırı aşağıdaki kodla değiştirin:

    [!code-csharp[CreateMLContext](./snippets/sentiment-analysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. Aşağıdaki kod satırını `Main()` yöntemine ekleyin:

    [!code-csharp[CallLoadData](./snippets/sentiment-analysis/csharp/Program.cs#CallLoadData)]

3. `LoadData()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `Main()` :

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    `LoadData()`Yöntemi aşağıdaki görevleri yürütür:

    - Verileri yükler.
    - Yüklenen veri kümesini tren ve test veri kümelerine böler.
    - Bölünmüş eğitme ve test veri kümelerini döndürür.

4. Aşağıdaki kodu yönteminin ilk satırı olarak ekleyin `LoadData()` :

    [!code-csharp[LoadData](./snippets/sentiment-analysis/csharp/Program.cs#LoadData "loading dataset")]

    [Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) yöntemi, veri şemasını tanımlar ve dosyada okur. Veri yolu değişkenlerini alır ve döndürür `IDataView` .

### <a name="split-the-dataset-for-model-training-and-testing"></a>Model eğitimi ve test için veri kümesini bölme

Bir modeli hazırlarken, modelin doğruluğunu test etmek için veri kümesinin bir kısmını eğitmeniz ve veri kümesinin bir parçası kullanırsınız.

1. Yüklenen verileri gereken veri kümelerine bölmek için, aşağıdaki kodu yöntemine bir sonraki satır olarak ekleyin `LoadData()` :

    [!code-csharp[SplitData](./snippets/sentiment-analysis/csharp/Program.cs#SplitData "Split the Data")]

    Önceki kod, yüklenen veri kümesini eğmek ve test veri kümelerine bölmek ve bunları sınıfında döndürmek için [Traintestsplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) yöntemini kullanır <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> . Parametreli veri test kümesi yüzdesini belirtin `testFraction` . Varsayılan değer %10 ' dur, bu durumda daha fazla veri değerlendirmek için %20 kullanmanız gerekir.

2. `splitDataView`Yönteminin sonuna döndürün `LoadData()` :

    [!code-csharp[ReturnSplitData](./snippets/sentiment-analysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Model oluşturma ve eğitme

1. Yöntemi `BuildAndTrainModel` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin `Main()` :

    [!code-csharp[CallBuildAndTrainModel](./snippets/sentiment-analysis/csharp/Program.cs#CallBuildAndTrainModel)]

    `BuildAndTrainModel()`Yöntemi aşağıdaki görevleri yürütür:

    - Verileri ayıklar ve dönüştürür.
    - Modeli TRAIN.
    - Sınama verilerine göre yaklaşımı tahmin eder.
    - Modeli döndürür.

2. `BuildAndTrainModel()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `Main()` :

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Verileri ayıklama ve dönüştürme

1. `FeaturizeText`Sonraki kod satırı olarak çağır:

    [!code-csharp[FeaturizeText](./snippets/sentiment-analysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    `FeaturizeText()`Önceki koddaki yöntemi, metin sütununu ( `SentimentText` ) `Features` makine öğrenimi algoritması tarafından kullanılan sayısal anahtar türü sütununa dönüştürür ve yeni bir veri kümesi sütunu olarak ekler:

    |Sentimentmetni                         |Yaklaşım |Özellikler              |
    |--------------------------------------|----------|----------------------|
    |Waitress, hizmette çok yavaş.|    0     |[0,76, 0,65, 0,44,...] |
    |Crust iyi değil.                    |    0     |[0,98, 0,43, 0,54,...] |
    |Wow... Bu yere iner.              |    1     |[0,35, 0,73, 0,46,...] |
    |Hizmet çok soriydi.              |    1     |[0,39, 0, 0,75,...]    |

### <a name="add-a-learning-algorithm"></a>Öğrenme algoritması ekleme

Bu uygulama, öğeleri veya veri satırlarını kategorilere ayırır. Uygulama, Web sitesi açıklamalarını pozitif veya negatif olarak kategorilere ayırır, bu nedenle ikili sınıflandırma görevini kullanın.

Aşağıdaki kod satırı olarak aşağıdakini ekleyerek, Machine Learning görevini veri dönüştürme tanımlarına ekleyin `BuildAndTrainModel()` :

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](./snippets/sentiment-analysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) , sınıflandırma eğitim algoritmanız. Bu öğesine eklenir `estimator` ve `SentimentText` `Features` `Label` Geçmiş verilerden bilgi edinmek için uygun () ve giriş parametrelerini kabul eder.

### <a name="train-the-model"></a>Modeli eğitme

`splitTrainSet`Yöntemine bir sonraki kod satırı olarak aşağıdakileri ekleyerek modeli verilere sığdırın ve eğitilen modeli döndürün `BuildAndTrainModel()` :

[!code-csharp[TrainModel](./snippets/sentiment-analysis/csharp/Program.cs#TrainModel "Train the model")]

[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Değerlendirme için kullanılmak üzere eğitilen modeli döndürün

 Metodun sonundaki modeli döndürün `BuildAndTrainModel()` :

[!code-csharp[ReturnModel](./snippets/sentiment-analysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Modelinize eğitim verdikten sonra, test verilerinizi, modelin performansını doğrulamak için kullanın.

1. `Evaluate()`Aşağıdaki kodla hemen sonra yöntemi oluşturun `BuildAndTrainModel()` :

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    `Evaluate()`Yöntemi aşağıdaki görevleri yürütür:

    - Test veri kümesini yükler.
    - BinaryClassification Değerlendiricisi oluşturur.
    - Modeli değerlendirir ve ölçümler oluşturur.
    - Ölçümleri görüntüler.

2. `Main()`Aşağıdaki kodu kullanarak yöntem çağrısının hemen altına, yönteminden yeni yönteme bir çağrı ekleyin `BuildAndTrainModel()` :

    [!code-csharp[CallEvaluate](./snippets/sentiment-analysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. `splitTestSet`Aşağıdaki kodu öğesine ekleyerek verileri dönüştürün `Evaluate()` :

    [!code-csharp[PredictWithTransformer](./snippets/sentiment-analysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    Önceki kod, bir test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapmak üzere [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.

4. Yöntemine aşağıdaki kod satırı olarak aşağıdakini ekleyerek modeli değerlendirin `Evaluate()` :

    [!code-csharp[ComputeMetrics](./snippets/sentiment-analysis/csharp/Program.cs#Evaluate "Compute Metrics")]

Tahmin kümesine () sahip olduktan sonra, tahmini `predictions` değerleri test veri kümesindeki gerçek ile karşılaştıran ve modelin nasıl çalıştığı hakkında bir CalibratedBinaryClassificationMetrics nesnesi döndüren [değerlendir ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi değerlendirir `Labels` . [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics)

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama ölçümlerini görüntüleme

Ölçümleri göstermek için aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](./snippets/sentiment-analysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- `Accuracy`Ölçüm, test kümesindeki doğru tahminlerden oranı olan bir modelin doğruluğunu alır.

- `AreaUnderRocCurve`Ölçüm, modelin pozitif ve negatif sınıfları doğru şekilde sınıflandırarak ne kadar süden emin olduğunu gösterir. `AreaUnderRocCurve`Bunun mümkün olduğunca yakın olmasını istersiniz.

- `F1Score`Ölçüm, [duyarlık](../resources/glossary.md#precision) ve [geri çekme](../resources/glossary.md#recall)arasındaki Bakiyenin ölçüsü olan modelin F1 Puanını alır.  `F1Score`Bunun mümkün olduğunca yakın olmasını istersiniz.

### <a name="predict-the-test-data-outcome"></a>Test verilerinin sonucunu tahmin etme

1. `UseModelWithSingleItem()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `Evaluate()` :

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithSingleItem()`Yöntemi aşağıdaki görevleri yürütür:

    - Test verileri için tek bir açıklama oluşturur.
    - Sınama verilerine göre yaklaşımı tahmin eder.
    - Raporlama için test verilerini ve tahminleri birleştirir.
    - Tahmin edilen sonuçları görüntüler.

2. `Main()`Aşağıdaki kodu kullanarak yöntem çağrısının hemen altına, yönteminden yeni yönteme bir çağrı ekleyin `Evaluate()` :

    [!code-csharp[CallUseModelWithSingleItem](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Yönteminin ilk satırı olarak oluşturmak için aşağıdaki kodu ekleyin `UseModelWithSingleItem()` :

    [!code-csharp[CreatePredictionEngine](./snippets/sentiment-analysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, `PredictionEnginePool` [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uygulamanız genelinde kullanılacak nesneleri oluşturan hizmetini kullanın. [ `PredictionEnginePool` ASP.NET Core Web API 'sinde kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.

    > [!NOTE]
    > `PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.

4. Bir örneği oluşturarak eğitilen modelin, yöntemi içindeki tahminini test etmek için bir açıklama ekleyin `UseModelWithSingleItem()` `SentimentData` :

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)Yöntemine bir sonraki kod satırı olarak aşağıdakileri ekleyerek test açıklama verilerini öğesine geçirin `UseModelWithSingleItem()` :

    [!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    [Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar.

6. `SentimentText`Aşağıdaki kodu kullanarak ve ilgili yaklaşım tahminini görüntüleyin:

    [!code-csharp[OutputPrediction](./snippets/sentiment-analysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Tahmin için modeli kullanın

### <a name="deploy-and-predict-batch-items"></a>Toplu iş öğelerini dağıtma ve tahmin etme

1. `UseModelWithBatchItems()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `UseModelWithSingleItem()` :

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithBatchItems()`Yöntemi aşağıdaki görevleri yürütür:

    - Batch test verileri oluşturur.
    - Sınama verilerine göre yaklaşımı tahmin eder.
    - Raporlama için test verilerini ve tahminleri birleştirir.
    - Tahmin edilen sonuçları görüntüler.

2. `Main`Aşağıdaki kodu kullanarak yöntem çağrısının hemen altına, yönteminden yeni yönteme bir çağrı ekleyin `UseModelWithSingleItem()` :

    [!code-csharp[CallPredictModelBatchItems](./snippets/sentiment-analysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Eğitim modelinin kullanım tahminlerini test etmek için bazı açıklamalar ekleyin `UseModelWithBatchItems()` :

    [!code-csharp[PredictionData](./snippets/sentiment-analysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Açıklama yaklaşımını tahmin etme

[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak açıklama verisi yaklaşımını tahmin etmek için modeli kullanın:

[!code-csharp[Predict](./snippets/sentiment-analysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Tahminleri birleştirin ve görüntüleyin

Aşağıdaki kodu kullanarak tahminler için bir üst bilgi oluşturun:

[!code-csharp[OutputHeaders](./snippets/sentiment-analysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

`SentimentPrediction`Öğesinden devralındığından `SentimentData` , `Transform()` yöntemi tahmin edilen `SentimentText` alanlarla doldurulur. ML.NET işlem işlemleri sırasında her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:

[!code-csharp[DisplayPredictions](./snippets/sentiment-analysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Sonuçlar

Sonuçlarınız aşağıdakine benzer olmalıdır. İşlem sırasında iletiler görüntülenir. Uyarıları görebilir veya iletileri işleme alabilirsiniz. Bunlar, netlik için aşağıdaki sonuçlardan kaldırılmıştır.

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

Tebrikler! İleti yaklaşımını sınıflandırma ve tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz.

Başarılı modellerin oluşturulması, yinelemeli bir işlemdir. Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır. Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı [Hyper-parametreleri](../resources/glossary.md#hyperparameter) ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Konsol uygulaması oluşturma
> - Verileri hazırlama
> - Verileri yükleme
> - Model oluşturma ve eğitme
> - Modeli değerlendirme
> - Tahmin yapmak için modeli kullanma
> - Sonuçları görme

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin
> [!div class="nextstepaction"]
> [Sorun sınıflandırması](github-issue-classification.md)
