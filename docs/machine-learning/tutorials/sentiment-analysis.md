---
title: 'Öğretici: Web sitesi açıklamalarını çözümleme-ikili sınıflandırma'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio C# 'da kullanır.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: c6b9d51a8ab91b4365c909993211f11ab3436808
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700852"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Öğretici: ML.NET 'de ikili sınıflandırmayla Web sitesi açıklamalarını çözümleyin

Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio C# 2017 ' de kullanılır.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Konsol uygulaması oluşturma
> - Verileri hazırlama
> - Verileri yükleme
> - Model oluşturma ve eğitme
> - Modeli değerlendirme
> - Tahmin yapmak için modeli kullanma
> - Sonuçlara bakın

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Prerequisites

- ".NET Core platformlar arası geliştirme" iş yükü yüklüyken [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

- [UCI yaklaşım cümleler veri kümesi](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası) etiketli

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "SentimentAnalysis" adlı bir **.NET Core konsol uygulaması** oluşturun.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.

3. **Microsoft.ml NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin ve sonra da **tarayıcı** sekmesini seçin. **Microsoft.ml**için arama yapın, istediğiniz paketi seçin ve sonra da **Install** düğmesini seçin. Kabul etmiş ile yüklemeye, seçtiğiniz paketin lisans koşullarına devam edin. **Microsoft. ml. FastTree** NuGet paketi için de aynısını yapın.

## <a name="prepare-your-data"></a>Verilerinizi hazırlayın

> [!NOTE]
> Bu öğreticinin veri kümeleri, ' Kimden grubundan, derin özellikler kullanılarak tekil etiketlere, Kotzıas et ' e ait. Al,. KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017). UCI Machine Learning deposu [http://archive.ics.uci.edu/ml ]. Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.

1. [Utiment, cümleler veri KÜMESI ZIP dosyası](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve unzip 'i indirin.

2. @No__t-0 dosyasını, oluşturduğunuz *veri* dizinine kopyalayın.

3. Çözüm Gezgini, `yelp_labeled.txt` dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

1. *Program.cs* dosyasının en üstüne aşağıdaki ek `using` deyimlerini ekleyin:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. Son indirilen veri kümesi dosya yolunu ve kaydedilen model dosyası yolunu tutmak için iki genel alan oluşturun:

    - `_dataPath`, modeli eğitmek için kullanılan veri kümesinin yoluna sahiptir.
    - `_modelPath`, eğitilen modelin kaydedildiği yolu içerir.

3. Yolları belirtmek için, aşağıdaki kodu `Main` yönteminin üstüne doğru satıra ekleyin:

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. Ardından, giriş verileriniz ve tahminlerinizi için sınıflar oluşturun. Projenize yeni bir sınıf ekleyin:

    - **Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.

    - **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

5. *SentimentData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. Mevcut sınıf tanımını kaldırın ve *SentimentData.cs* dosyasına `SentimentData` ve `SentimentPrediction` olmak üzere iki sınıfa sahip aşağıdaki kodu ekleyin:

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Verilerin nasıl hazırlandığını
@No__t-0 giriş veri kümesi sınıfının kullanıcı açıklamaları için bir `string` (`SentimentText`) ve yaklaşım için 1 (pozitif) ya da 0 (negatif) bir `bool` (`Sentiment`) değeri vardır. Her iki alana de eklenen [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri vardır ve bu, her alanın veri dosyası sırasını açıklar.  Ayrıca, `Sentiment` özelliğinin, `Label` alanı olarak belirlemek için [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) özniteliği vardır. Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:

|Sentimentmetni                         |Yaklaşım (etiket) |
|--------------------------------------|----------|
|Waitress, hizmette çok yavaş.|    0     |
|Crust iyi değil.                    |    0     |
|Wow... Bu yere iner.              |    1\.     |
|Hizmet çok soriydi.              |    1\.     |

`SentimentPrediction`, model eğitimi sonrasında kullanılan tahmin sınıfıdır. @No__t-0 ' dan devraldığından, giriş `SentimentText` ' in çıkış tahminiyle birlikte görüntülenmesini sağlayabilirsiniz. @No__t-0 Boole değeri, modelin yeni giriş `SentimentText` ile birlikte sağlandığı zaman tahmin edilen değerdir.

@No__t-0 çıkış sınıfı, model tarafından hesaplanan iki diğer özellik içerir: `Score`-model tarafından hesaplanan ham puan ve `Probability`-pozitif yaklaşım olan metnin olasılığına ayarlanmış puan.

Bu öğretici için en önemli özellik `Prediction` ' dır.

## <a name="load-the-data"></a>Verileri yükleme
ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) `IDataView` nesnesine yüklenebilir.

[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır. @No__t başlatılıyor-0, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur. Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.

Uygulamayı hazırlayın ve sonra verileri yükleyin:

1. @No__t-1 yöntemindeki `Console.WriteLine("Hello World!")` satırını, mlContext değişkenini bildirmek ve başlatmak için aşağıdaki kodla değiştirin:

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. @No__t-0 yöntemine sonraki kod satırı olarak aşağıdakileri ekleyin:

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. Aşağıdaki kodu kullanarak, `Main()` yönteminden hemen sonra `LoadData()` yöntemini oluşturun:

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    @No__t-0 yöntemi aşağıdaki görevleri yürütür:

    - Verileri yükler.
    - Yüklenen veri kümesini tren ve test veri kümelerine böler.
    - Bölünmüş eğitme ve test veri kümelerini döndürür.

4. @No__t-0 yönteminin ilk satırı olarak aşağıdaki kodu ekleyin:

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    [Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar. Veri yolu değişkenlerini alır ve `IDataView` döndürür.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Model eğitimi ve test için veri kümesini bölme

Bir modeli hazırlarken, modelin doğruluğunu test etmek için veri kümesinin bir kısmını eğitmeniz ve veri kümesinin bir parçası kullanırsınız.

1. Yüklenen verileri gereken veri kümelerine bölmek için, `LoadData()` yönteminde sonraki satır olarak aşağıdaki kodu ekleyin:

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    Önceki kod, yüklenen veri kümesini eğmek ve test veri kümelerine bölmek için [Traintestsplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) yöntemini kullanır ve onları [Traintestdata](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) sınıfında döndürür. @No__t-0parametresiyle verilerin test kümesi yüzdesini belirtin. Varsayılan değer% 10 ' dur, bu durumda daha fazla veri değerlendirmek için% 20 kullanmanız gerekir.

2. @No__t-1 yönteminin sonundaki `splitDataView` döndürün:

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Model oluşturma ve eğitme

1. @No__t-0yöntemine `Main()` yönteminde sonraki kod satırı olarak aşağıdaki çağrıyı ekleyin:

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    @No__t-0 yöntemi aşağıdaki görevleri yürütür:

    - Verileri ayıklar ve dönüştürür.
    - Modeli TRAIN.
    - Sınama verilerine göre yaklaşımı tahmin eder.
    - Modeli döndürür.

2. Aşağıdaki kodu kullanarak, `Main()` yönteminden hemen sonra `BuildAndTrainModel()` yöntemini oluşturun:

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Verileri ayıklama ve dönüştürme

1. Sonraki kod satırı olarak `FeaturizeText` öğesini çağırın:

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    Önceki koddaki `FeaturizeText()` yöntemi, metin sütununu (`SentimentText`) makine öğrenimi algoritması tarafından kullanılan sayısal anahtar türü `Features` sütununa dönüştürür ve yeni bir veri kümesi sütunu olarak ekler:

    |Sentimentmetni                         |Yaklaşım |Özellikler              |
    |--------------------------------------|----------|----------------------|
    |Waitress, hizmette çok yavaş.|    0     |[0,76, 0,65, 0,44,...] |
    |Crust iyi değil.                    |    0     |[0,98, 0,43, 0,54,...] |
    |Wow... Bu yere iner.              |    1\.     |[0,35, 0,73, 0,46,...] |
    |Hizmet çok soriydi.              |    1\.     |[0,39, 0, 0,75,...]    |

### <a name="add-a-learning-algorithm"></a>Öğrenme algoritması ekleme

Bu uygulama, öğeleri veya veri satırlarını kategorilere ayırır. Uygulama, Web sitesi açıklamalarını pozitif veya negatif olarak kategorilere ayırır, bu nedenle ikili sınıflandırma görevini kullanın.

@No__t-0 ' a bir sonraki kod satırı olarak aşağıdakini ekleyerek makine öğrenimi görevini veri dönüştürme tanımlarına ekleyin:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) , sınıflandırma eğitim algoritmanız. Bu, `estimator` ' a eklenir ve geçmiş verilerden öğrenme `SentimentText` (`Features`) ve `Label` giriş parametrelerini kabul eder.

### <a name="train-the-model"></a>Modeli eğitme

Modeli `splitTrainSet` verilerine sığdırın ve `BuildAndTrainModel()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen modeli döndürün:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Değerlendirme için kullanılmak üzere eğitilen modeli döndürün

 @No__t-0 yönteminin sonundaki modeli döndürün:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Modelinize eğitim verdikten sonra, test verilerinizi, modelin performansını doğrulamak için kullanın.

1. @No__t-0 yöntemini aşağıdaki kodla `BuildAndTrainModel()` ' den sonra oluşturun:

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    @No__t-0 yöntemi aşağıdaki görevleri yürütür:

    - Test veri kümesini yükler.
    - BinaryClassification Değerlendiricisi oluşturur.
    - Modeli değerlendirir ve ölçümler oluşturur.
    - Ölçümleri görüntüler.

2. Aşağıdaki kodu kullanarak, `Main()` yönteminden yeni yönteme bir çağrı ekleyin, `BuildAndTrainModel()` yöntem çağrısının altına ekleyin:

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Aşağıdaki kodu `Evaluate()` ' e ekleyerek `splitTestSet` verisini dönüştürün:

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    Önceki kod, bir test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapmak üzere [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.

4. @No__t-0 yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirin:

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

Tahmin kümesine (`predictions`) sahip olduktan sonra, tahmine dayalı değerleri test veri kümesindeki gerçek `Labels` ile karşılaştıran ve şu şekilde bir [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) nesnesi döndüren [değerlendirme ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi değerlendirir. Model gerçekleştiriliyor.

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama ölçümlerini görüntüleme

Ölçümleri göstermek için aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- @No__t-0 ölçümü, test kümesindeki doğru tahminlerden oranı olan bir modelin doğruluğunu alır.

- @No__t-0 ölçümü, modelin ne kadar duyarlı olduğunu pozitif ve negatif sınıfların doğru sınıflandırdığını gösterir. @No__t-0 ' nın mümkün olduğunca yakın olmasını istiyorsunuz.

- @No__t-0 ölçümü, [duyarlık](../resources/glossary.md#precision) ve [geri çekme](../resources/glossary.md#recall)arasındaki Bakiyenin ölçüsü olan modelin F1 Puanını alır.  @No__t-0 ' nın mümkün olduğunca yakın olmasını istiyorsunuz.

### <a name="predict-the-test-data-outcome"></a>Test verilerinin sonucunu tahmin etme

1. Aşağıdaki kodu kullanarak, `Evaluate()` yönteminden hemen sonra `UseModelWithSingleItem()` yöntemini oluşturun:

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    @No__t-0 yöntemi aşağıdaki görevleri yürütür:

    - Test verileri için tek bir açıklama oluşturur.
    - Sınama verilerine göre yaklaşımı tahmin eder.
    - Raporlama için test verilerini ve tahminleri birleştirir.
    - Tahmin edilen sonuçları görüntüler.

2. Aşağıdaki kodu kullanarak, `Main()` yönteminden yeni yönteme bir çağrı ekleyin, `Evaluate()` yöntem çağrısının altına ekleyin:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. @No__t-0 yönteminde ilk satır olarak oluşturmak için aşağıdaki kodu ekleyin:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın. [ASP.NET Core Web API 'sinde `PredictionEnginePool` ' i nasıl kullanacağınızı](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) öğrenmek için bu kılavuza bakın

    > [!NOTE]
    > `PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.
    
4. @No__t-1 ' in bir örneğini oluşturarak eğitilen modelin tahminini `UseModelWithSingleItem()` yönteminde test etmek için bir açıklama ekleyin:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. @No__t-2 yöntemine sonraki kod satırları olarak aşağıdakini ekleyerek test açıklama verilerini [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) ' e geçirin:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    [Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar.

6. Aşağıdaki kodu kullanarak `SentimentText` ve karşılık gelen yaklaşım tahminini görüntüleyin:

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Tahmin için modeli kullanın

### <a name="deploy-and-predict-batch-items"></a>Toplu iş öğelerini dağıtma ve tahmin etme

1. Aşağıdaki kodu kullanarak, `UseModelWithSingleItem()` yönteminden hemen sonra `UseModelWithBatchItems()` yöntemini oluşturun:

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    @No__t-0 yöntemi aşağıdaki görevleri yürütür:

    - Batch test verileri oluşturur.
    - Sınama verilerine göre yaklaşımı tahmin eder.
    - Raporlama için test verilerini ve tahminleri birleştirir.
    - Tahmin edilen sonuçları görüntüler.

2. Aşağıdaki kodu kullanarak, `Main` yönteminden yeni yönteme bir çağrı ekleyin, `UseModelWithSingleItem()` yöntem çağrısının altına ekleyin:

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. @No__t-0 yönteminde eğitilen modelin tahminlerini test etmek için bazı açıklamalar ekleyin:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Açıklama yaklaşımını tahmin etme

[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak açıklama verisi yaklaşımını tahmin etmek için modeli kullanın:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Tahminleri birleştirin ve görüntüleyin

Aşağıdaki kodu kullanarak tahminler için bir üst bilgi oluşturun:

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

@No__t-0 `SentimentData` ' den devralındığından, `SentimentText` ' i tahmin edilen alanlarla doldurulmuş `Transform()` yöntemi. ML.NET işlem işlemleri sırasında her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

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

Mühendisi! İleti yaklaşımını sınıflandırma ve tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz.

Başarılı modellerin oluşturulması, yinelemeli bir işlemdir. Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır. Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı [Hyper-parametreleri](../resources/glossary.md##hyperparameter) ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, nasıl yapılacağını öğrendiniz:
> [!div class="checklist"]
>
> - Konsol uygulaması oluşturma
> - Verileri hazırlama
> - Verileri yükleme
> - Model oluşturma ve eğitme
> - Modeli değerlendirme
> - Tahmin yapmak için modeli kullanma
> - Sonuçlara bakın

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin
> [!div class="nextstepaction"]
> [Sorun sınıflandırması](github-issue-classification.md)
