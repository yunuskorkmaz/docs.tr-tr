---
title: 'Öğretici: Web sitesi açıklamalarını çözümle-ikili sınıflandırma'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio C# 'da kullanır.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 4daa7734f12c57a177fab3c62fdd96bda22838af
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107173"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Öğretici: ML.NET içinde ikili sınıflandırmayla Web sitesi açıklamalarının yaklaşımını çözümleyin

Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir .NET Core konsol uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio C# 2017 ' de kullanılır.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> - Konsol uygulaması oluşturma
> - Verileri hazırlama
> - Verileri yükleme
> - Model oluşturma ve eğitme
> - Modeli değerlendirme
> - Tahmin yapmak için modeli kullanma
> - Sonuçlara bakın

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- ".NET Core platformlar arası geliştirme" iş yükü yüklüyken [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

- [Ustaklama tümce veri kümesi etiketli](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP dosyası)

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "SentimentAnalysis" adlı bir **.NET Core konsol uygulaması** oluşturun.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.

3. **Microsoft.ml NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin ve sonra da **tarayıcı** sekmesini seçin. **Microsoft.ml**için arama yapın, istediğiniz paketi seçin ve ardından **Install** düğmesini seçin. Kabul etmiş ile yüklemeye, seçtiğiniz paketin lisans koşullarına devam edin. **Microsoft. ml. FastTree** NuGet paketi için de aynısını yapın.

## <a name="prepare-your-data"></a>Verilerinizi hazırlayın

> [!NOTE]
> Bu öğreticinin veri kümeleri, ' Kimden grubundan, derin özellikler kullanılarak tekil etiketlere, Kotzıas et ' e ait. Al,. KDD 2015 ve UCI Machine Learning Repository-dua, D. ve karra Taniskidou, E. (2017). UCI Machine Learning deposu [http://archive.ics.uci.edu/ml ]. Irvine, CA: California Üniversitesi, bilgi Okulu ve bilgisayar bilimi.

1. [Utiment, cümleler veri KÜMESI ZIP dosyası](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve unzip 'i indirin.

2. Dosyayı oluşturduğunuz veri dizinine kopyalayın. `yelp_labelled.txt`

3. Çözüm Gezgini, `yelp_labeled.txt` dosyaya sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

1. Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. Son indirilen veri kümesi dosya yolunu ve kaydedilen model dosyası yolunu tutmak için iki genel alan oluşturun:

    - `_dataPath`, modeli eğitmek için kullanılan veri kümesinin yolunu içerir.
    - `_modelPath`Eğitim modelinin kaydedildiği yolu içerir.

3. Yolları belirtmek için aşağıdaki kodu `Main` metodun hemen üstüne ekleyin:

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. Ardından, giriş verileriniz ve tahminlerinizi için sınıflar oluşturun. Projenize yeni bir sınıf ekleyin:

    - **Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.

    - **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

5. *SentimentData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadeyi *SentimentData.cs*öğesinin en üstüne ekleyin:

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. Mevcut sınıf tanımını kaldırın ve iki sınıfa `SentimentData` ve `SentimentPrediction`SentimentData.cs dosyasına sahip olan aşağıdaki kodu ekleyin:

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Verilerin nasıl hazırlandığını
`SentimentData`Giriş veri kümesi sınıfı, bir `string` for User Comments (`SentimentText`) ve bir `bool` (`Sentiment`) değeri için 1 (pozitif) ya da 0 (negatif) değerine sahiptir. Her iki alana de eklenen [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) öznitelikleri vardır ve bu, her alanın veri dosyası sırasını açıklar.  Ayrıca, `Sentiment` özelliği `Label` alanı olarak belirlemek için bir [sütunadı](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) özniteliği vardır. Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:

|Sentimentmetni                         |Yaklaşım (etiket) |
|--------------------------------------|----------|
|Waitress, hizmette çok yavaş.|    0     |
|Crust iyi değil.                    |    0     |
|Wow... Bu yere iner.              |    1\.     |
|Hizmet çok soriydi.              |    1\.     |

`SentimentPrediction`, model eğitiminden sonra kullanılan tahmin sınıfıdır. `SentimentData` Girişin`SentimentText` çıkış tahminiyle birlikte görüntülenebilmesini sağlayacak şekilde öğesinden devralır. Boole değeri, modelin yeni girişle `SentimentText`sağlandığı sırada tahmin edilen değerdir. `Prediction`

Çıkış sınıfı `SentimentPrediction` , model tarafından hesaplanan iki diğer özellik içerir: `Score` -model tarafından hesaplanan ham puan ve `Probability` , pozitif yaklaşım olan metnin olasılığına ayarlanmış puan.

Bu öğretici için en önemli özellik ' dir `Prediction`.

## <a name="load-the-data"></a>Verileri yükleme
ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.

[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır. Başlatma `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilecek yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal `DBContext` olarak da benzerdir.

Uygulamayı hazırlayın ve sonra verileri yükleyin:

1. Mlcontext değişkenini bildirmek ve `Main` başlatmak için yöntemindeki satırıaşağıdakikodladeğiştirin:`Console.WriteLine("Hello World!")`

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. Aşağıdaki kod `Main()` satırını yöntemine ekleyin:

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. Aşağıdaki kodu kullanarak yönteminden hemen `Main()` sonra yönteminioluşturun:`LoadData()`

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    `LoadData()` Yöntemi aşağıdaki görevleri yürütür:

    - Verileri yükler.
    - Yüklenen veri kümesini tren ve test veri kümelerine böler.
    - Bölünmüş eğitme ve test veri kümelerini döndürür.

4. Aşağıdaki kodu `LoadData()` yönteminin ilk satırı olarak ekleyin:

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    [Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar. Veri yolu değişkenlerini alır ve döndürür `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Model eğitimi ve test için veri kümesini bölme

Bir modeli hazırlarken, modelin doğruluğunu test etmek için veri kümesinin bir kısmını eğitmeniz ve veri kümesinin bir parçası kullanırsınız.

1. Yüklenen verileri gereken veri kümelerine bölmek için, aşağıdaki kodu `LoadData()` yöntemine bir sonraki satır olarak ekleyin:

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    Önceki kod, yüklenen veri kümesini eğmek ve test veri kümelerine bölmek için [Traintestsplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) yöntemini kullanır ve onları [Traintestdata](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) sınıfında döndürür. `testFraction`Parametreli veri test kümesi yüzdesini belirtin. Varsayılan değer% 10 ' dur, bu durumda daha fazla veri değerlendirmek için% 20 kullanmanız gerekir.

2. Yöntemininsonuna`LoadData()`döndürün: `splitDataView`

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Model oluşturma ve eğitme

1. `BuildAndTrainModel` Yöntemi`Main()` içindeki sonraki kod satırı olarak yöntemine aşağıdaki çağrıyı ekleyin:

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    `BuildAndTrainModel()` Yöntemi aşağıdaki görevleri yürütür:

    - Verileri ayıklar ve dönüştürür.
    - Modeli TRAIN.
    - Sınama verilerine göre yaklaşımı tahmin eder.
    - Modeli döndürür.

2. Aşağıdaki kodu kullanarak yönteminden hemen `Main()` sonra yönteminioluşturun:`BuildAndTrainModel()`

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Verileri ayıklama ve dönüştürme

1. Sonraki `FeaturizeText` kod satırı olarak çağır:

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    Önceki koddaki`SentimentText` `Features`yöntemi, metin sütununu () makine öğrenimi algoritması tarafından kullanılan sayısal anahtar türü sütununa dönüştürür ve yeni bir veri kümesi sütunu olarak ekler: `FeaturizeText()`

    |Sentimentmetni                         |Yaklaşım |Özellikler              |
    |--------------------------------------|----------|----------------------|
    |Waitress, hizmette çok yavaş.|    0     |[0,76, 0,65, 0,44,...] |
    |Crust iyi değil.                    |    0     |[0,98, 0,43, 0,54,...] |
    |Wow... Bu yere iner.              |    1\.     |[0,35, 0,73, 0,46,...] |
    |Hizmet çok soriydi.              |    1\.     |[0,39, 0, 0,75,...]    |

### <a name="add-a-learning-algorithm"></a>Öğrenme algoritması ekleme

Bu uygulama, öğeleri veya veri satırlarını kategorilere ayırır. Uygulama, Web sitesi açıklamalarını pozitif veya negatif olarak kategorilere ayırır, bu nedenle ikili sınıflandırma görevini kullanın.

Aşağıdaki kod `BuildAndTrainModel()`satırı olarak aşağıdakini ekleyerek, Machine Learning görevini veri dönüştürme tanımlarına ekleyin:

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) , sınıflandırma eğitim algoritmanız. Bu öğesine `estimator` eklenir ve geçmiş verilerden bilgi edinmek için uygun `SentimentText` (`Features`) ve `Label` giriş parametrelerini kabul eder.

### <a name="train-the-model"></a>Modeli eğitme

Yöntemine bir sonraki kod satırı `splitTrainSet` olarak aşağıdakileri ekleyerek modeli verilere sığdırın ve eğitilen modeli döndürün: `BuildAndTrainModel()`

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Değerlendirme için kullanılmak üzere eğitilen modeli döndürün

 `BuildAndTrainModel()` Metodun sonundaki modeli döndürün:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Modelinize eğitim verdikten sonra, test verilerinizi, modelin performansını doğrulamak için kullanın.

1. Aşağıdaki kodla hemen sonra `BuildAndTrainModel()` yöntemioluşturun:`Evaluate()`

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    `Evaluate()` Yöntemi aşağıdaki görevleri yürütür:

    - Test veri kümesini yükler.
    - BinaryClassification Değerlendiricisi oluşturur.
    - Modeli değerlendirir ve ölçümler oluşturur.
    - Ölçümleri görüntüler.

2. Aşağıdaki kodu kullanarak yöntem çağrısının hemen `Main()` `BuildAndTrainModel()` altına, yönteminden yeni yönteme bir çağrı ekleyin:

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Aşağıdaki kodu öğesine `Evaluate()`ekleyerek verileridönüştürün:`splitTestSet`

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    Önceki kod, bir test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapmak üzere [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanır.

4. `Evaluate()` Yöntemine aşağıdaki kod satırı olarak aşağıdakini ekleyerek modeli değerlendirin:

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

Tahmin kümesine (`predictions`) sahip olduktan sonra, tahmini değerleri test veri kümesindeki `Labels` gerçek ile karşılaştıran ve bir [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) döndüren [değerlendir ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) yöntemi, modeli değerlendirir. modelin nasıl çalıştığı hakkında nesne.

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama ölçümlerini görüntüleme

Ölçümleri göstermek için aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- `Accuracy` Ölçüm, test kümesindeki doğru tahminlerden oranı olan bir modelin doğruluğunu alır.

- `AreaUnderRocCurve` Ölçüm, modelin pozitif ve negatif sınıfları doğru şekilde sınıflandırarak ne kadar süden emin olduğunu gösterir. Bunun mümkün olduğunca `AreaUnderRocCurve` yakın olmasını istersiniz.

- Ölçüm, duyarlık ve [geri çekme](../resources/glossary.md#recall)arasındaki Bakiyenin ölçüsü olan modelin F1 Puanını alır. [](../resources/glossary.md#precision) `F1Score`  Bunun mümkün olduğunca `F1Score` yakın olmasını istersiniz.

### <a name="predict-the-test-data-outcome"></a>Test verilerinin sonucunu tahmin etme

1. Aşağıdaki kodu kullanarak yönteminden hemen `Evaluate()` sonra yönteminioluşturun:`UseModelWithSingleItem()`

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithSingleItem()` Yöntemi aşağıdaki görevleri yürütür:

    - Test verileri için tek bir açıklama oluşturur.
    - Sınama verilerine göre yaklaşımı tahmin eder.
    - Raporlama için test verilerini ve tahminleri birleştirir.
    - Tahmin edilen sonuçları görüntüler.

2. Aşağıdaki kodu kullanarak yöntem çağrısının hemen `Main()` `Evaluate()` altına, yönteminden yeni yönteme bir çağrı ekleyin:

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. `UseModelWithSingleItem()` Yönteminin ilk satırı olarak oluşturmak için aşağıdaki kodu ekleyin:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneği üzerinde bir tahmin gerçekleştirmenizi ve daha sonra bir tahmin gerçekleştirmenizi sağlayan KULLANıŞLı bir API 'dir.

4. `UseModelWithSingleItem()` Bir`SentimentData`örneği oluşturarak eğitilen modelin, yöntemi içindeki tahminini test etmek için bir açıklama ekleyin:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. `UseModelWithSingleItem()` Yöntemine bir sonraki kod satırı olarak aşağıdakileri `Prediction Engine` ekleyerek test açıklama verilerini öğesine geçirin:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    [Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar.

6. Aşağıdaki `SentimentText` kodu kullanarak ve ilgili yaklaşım tahminini görüntüleyin:

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Tahmin için modeli kullanın

### <a name="deploy-and-predict-batch-items"></a>Toplu iş öğelerini dağıtma ve tahmin etme

1. Aşağıdaki kodu kullanarak yönteminden hemen `UseModelWithSingleItem()` sonra yönteminioluşturun:`UseModelWithBatchItems()`

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithBatchItems()` Yöntemi aşağıdaki görevleri yürütür:

    - Batch test verileri oluşturur.
    - Sınama verilerine göre yaklaşımı tahmin eder.
    - Raporlama için test verilerini ve tahminleri birleştirir.
    - Tahmin edilen sonuçları görüntüler.

2. Aşağıdaki kodu kullanarak yöntem çağrısının hemen `Main` `UseModelWithSingleItem()` altına, yönteminden yeni yönteme bir çağrı ekleyin:

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Eğitim modelinin kullanım tahminlerini `UseModelWithBatchItems()` test etmek için bazı açıklamalar ekleyin:

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Açıklama yaklaşımını tahmin etme

[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemini kullanarak açıklama verisi yaklaşımını tahmin etmek için modeli kullanın:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Tahminleri birleştirin ve görüntüleyin

Aşağıdaki kodu kullanarak tahminler için bir üst bilgi oluşturun:

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Öğesinden devralındığından ,`Transform()` yöntemi tahmin edilen alanlarla `SentimentText`doldurulur. `SentimentPrediction` `SentimentData` ML.NET işlem işlemleri sırasında her bileşen sütun ekler ve bu da sonuçları görüntülemeyi kolaylaştırır:

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

Tebrikler! İleti yaklaşımını sınıflandırma ve tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz.

Başarılı modellerin oluşturulması, yinelemeli bir işlemdir. Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır. Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı [Hyper-parametreleri](../resources/glossary.md##hyperparameter) ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
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
