---
title: Bir düşünceleri analiz ikili sınıflandırma senaryosunda ML.NET kullanın
description: ML.NET bir ikili sınıflandırma senaryosunda düşünceleri tahmin uygun eylemi gerçekleştirin için nasıl kullanılacağını anlamak için nasıl kullanılacağını bulur.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 898b4664120b6eeb0ef18aac3acdc94b0ca0bacd
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314844"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Öğretici: Kullanım düşünceleri analiz ikili sınıflandırma senaryosunda ML.NET

> [!NOTE]
> Bu konuda şu anda önizlemede değil, ML.NET başvuruyor ve malzeme değiştirilebilir olabilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu örnek öğretici ML.NET düşünceleri sınıflandırıcı aracılığıyla C# Visual Studio 2017 kullanarak bir .NET Core konsol uygulaması oluşturmak için kullanma gösterilmektedir.

Bu öğreticide, bilgi nasıl yapılır:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenme görevini seçin
> * Verilerinizi hazırlama
> * Öğrenme işlem hattı oluşturma
> * Bir sınıflandırıcı yükleme
> * Modeli eğitmek
> * Farklı bir veri kümesi ile modelini değerlendir
> * Model ile test veri sonuçlarını tahmin etme

## <a name="sentiment-analysis-sample-overview"></a>Düşünceleri analiz örnek genel bakış

Örnek ML.NET sınıflandırır ve düşünceleri olumlu veya olumsuz olarak tahmin modeli eğitmek için kullandığı bir konsol uygulamasıdır. Ayrıca, ikinci bir veri kümesi kalitesini analiz için modeliyle değerlendirir. Düşünceleri veri kümeleri WikiDetox projeden ' dir.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15,6 veya üstü](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core platformlar arası geliştirme" iş yükü ile.

* [Wikipedia detox satır veri sekmeyle ayrılmış dosya (wikiPedia-detox-250-satır-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).
* [Wikipedia detox satırı test sekmeyle ayrılmış dosya (wikipedia-detox-250-satır-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).

## <a name="machine-learning-workflow"></a>Machine learning iş akışı

Bu öğretici bir machine learning düzenli bir şekilde taşımak işlem tanır iş akışı izler.

İş akışı aşamaları aşağıdaki gibidir:

1. **Sorunu anlamak**
2. **Veri alma**
3. **Veri önişle ve mühendislik özellik**
4. **Eğitmek ve modeli tahmin etme**
5. **Modeli değerlendirin**
6. **Model operationalization**

### <a name="understand-the-problem"></a>Sorunu anlama

İlk oluşturma ve eğitim modeli destekleyebilir bölümleri aşağıya doğru bölün şekilde sorun anlamanız gerekir. Tahmin etmek ve sonuçları değerlendirin problemi kesiliyor.

Sorun Bu öğretici için uygun eylemi gerçekleştirin için gelen Web sitesi yorum düşünceleri anlamaktır.

Problemi düşünceleri metin ve düşünceleri değer ile modeli eğitmek için istediğiniz veriler için ve değerlendirmek ve işletimsel kullanmak bir tahmin edilen düşünceleri değer bozulabilir.

Ardından gerek **belirlemek** Görev Seçimi öğrenme makineyle yardımcı düşünceleri.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenme görevini seçin

Bu sorun aşağıdaki gerçekleri bildirin:

Verileri eğitim: Web sitesi açıklamaları olumlu veya olumsuz olabilir (**düşünceleri**).
Tahmin **düşünceleri** açıklamasının bir yeni Web sitesi, pozitif veya negatif gibi aşağıdaki örneklerde:

* Wikipedia için anlamsız ekleme kullanmamalıdır.
* Kendisine en iyi olduğu ve makale, yazması gerekir.

Sınıflandırma machine learning görevi bu senaryo için uygundur.

### <a name="about-the-classification-task"></a>Sınıflandırma görev hakkında

Sınıflandırma olan verileri kullanan bir machine learning görevi **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı. Örneğin, sınıflandırma için kullanabilirsiniz:

* Düşünceleri olumlu veya olumsuz olarak belirleyin.
* E-posta istenmeyen posta olarak Önemsiz veya iyi sınıflandırır.
* Hasta'nın lab örnek cancerous olup olmadığını belirler.
* Müşterilerin bir satış kampanyası yanıtlamak için kendi propensity göre kategorilere ayır.

Sınıflandırma görevleri sık aşağıdaki türleri şunlardır:

* İkili: ya da A veya b
* Veya çoklu sınıflar: tek bir model kullanarak tahmin birden çok kategori.

## <a name="create-a-console-application"></a>Bir konsol uygulaması oluşturun

1. Visual Studio 2017'ni açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde *yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusu, "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.

2. Adlı bir dizin oluşturun *veri* projenize veri kümesi dosyalarınızı kaydetmek için:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve seçin **Ekle** > **yeni klasör**. "Data" yazın ve Enter tuşuna basın.

3. Yükleme **Microsoft.ML NuGet paketi**:

    Çözüm Gezgini'nde projenizi ve select üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulünü** iletişim varsa, listelenen paketler için lisans koşullarını kabul etmiş olursunuz.

### <a name="prepare-your-data"></a>Verilerinizi hazırlama

1. Karşıdan [WikiPedia detox-250-satır-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) ve [wikipedia-detox-250-satır-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör. İlk veri kümesini makine öğrenimi modeline eğitir ve ikinci nasıl modelinizi doğrudur değerlendirmek için kullanılabilir.

2. Çözüm Gezgini'nde, her biri sağ \*.tsv dosyaları ve select **özellikleri**. Altında **Gelişmiş**, değerini değiştirme **çıktı dizinine Kopyala** için **her zaman**.

### <a name="create-classes-and-define-paths"></a>Sınıflar oluşturma ve yolları tanımla

Aşağıdaki ek ekleyin `using` deyimleri üstüne *Program.cs* dosyası:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

Yolun son indirilen dosyaları tutmak için üç genel değişkenler oluşturmanız gerekir:

* `_dataPath` modeli eğitmek için kullanılan veri kümesi yolu.
* `_testDataPath` model değerlendirmek için kullanılan veri kümesi yolu.
* `_modelPath` Eğitim modeli kaydedildiği yolu vardır.

Satırının sağındaki aşağıdaki kodu ekleyin `Main` yöntemi en son indirilen dosyaları belirtmek için:

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

Giriş verisi ve tahminleri için bazı sınıfları oluşturmanız gerekir. Yeni bir sınıf projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*. Ardından, seçin **Ekle** düğmesi.

    *SentimentData.cs* dosyasını Kod Düzenleyicisi'nde açar. Aşağıdakileri ekleyin `using` deyimi üstüne *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Varolan sınıf tanımına kaldırmak ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` girdi veri kümesi sınıfı ve sahip bir `float` (`Sentiment`) düşünceleri pozitif veya negatif bir değer ve açıklama için bir dize olan (`SentimentText`). Her iki alana sahip `Column` öznitelikleri kendisine bağlı. Bu öznitelik veri dosyası ve olduğu her bir alan sıralamasını açıklar `Label` alan. `SentimentPrediction` model eğitilmiş sonra sınıf tahmin için kullanılır. Tek bir Boole değeri vardır (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği. `Label` Oluşturabilir ve ayrıca sahip ikinci bir veri kümesi model değerlendirmek için kullanılan model ve onun eğitmek için kullanılır. `PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme için bir giriş eğitim verilerini, tahmin edilen değerler ve modeli ile kullanılır.

İçinde *Program.cs* dosya, değişiklik `Main` değiştirerek yöntem imzası `void` ile `async Task`, aşağıdaki örnekte olduğu gibi:

```csharp
static async Task Main(string[] args) 
{

}
```

Eklediğiniz `async` için `Main` ile bir <xref:System.Threading.Tasks.Task> daha sonra bir zip dosyasına model kaydediyorsanız ve program dış görev tamamlanana dek bekleyin gerekir çünkü dönüş türü.

> [!NOTE]
> Bir *zaman uyumsuz ana* yöntemi kullanmanıza olanak sağlayan `await` içinde `Main` yöntemi. Daha fazla bilgi için bkz: [zaman uyumsuz ana](../../../docs/csharp/programming-guide/main-and-command-args/index.md) konusu C# programlama kılavuzu.

Değiştir `Console.WriteLine("Hello World!")` aşağıdaki kodda satırıyla `Main` yöntemi:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

`Train` Yöntemi aşağıdaki görevleri yürütür:

* Yükler veya verileri alır.
* Preprocesses ve featurizes verileri.
* Model eğitir.
* Test verilerine dayalı düşünceleri tahmin eder.

Oluşturma `Train` yöntemi, hemen sonra `Main` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a>Veri alma

Yeni bir örneğini başlatır <xref:Microsoft.ML.LearningPipeline> veri yükleme, veri işleme/featurization ve modeli içerecektir. İlk satırı olarak aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<xref:Microsoft.ML.Data.TextLoader> Nesne Ardışık düzenin ilk bir parçasıdır ve eğitim dosya verileri yükler.

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a>Veri önişle ve mühendislik özellik

Ön işleme ve veri temizleme bir veri kümesi etkili bir şekilde machine learning için kullanılmadan önce gerçekleşen önemli görevlerdir. Ham verileri gürültülü ve güvenilmeyen görülür ve değerleri eksik olabilir. Bu model görevleri olmadan verileri kullanarak yanıltıcı sonuçlara yol açabilir. ML. NET'in dönüşüm işlem hatlarını, eğitim veya test önce verilerinizi uygulanan Dönüşümlerin özel kümesi oluşturmak izin verir. Dönüşümler birincil amacı için veri featurization ' dir. Bir dönüştürme ardışık düzen avantajı, test verileri uygulamak için ardışık düzen kaydetme dönüştürme ardışık düzen tanımı sonra olmasıdır.

Geçerli bir <xref:Microsoft.ML.Transforms.TextFeaturizer> dönüştürmek için `SentimentText` sütununa bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector) adlı `Features` makine öğrenimi algoritması tarafından kullanılan. Bu ön işleme featurization adımdır. ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz. Ekleme `TextFeaturizer` ardışık düzenine kodun sonraki satırında, olarak:

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Nesnesidir bir karar ağacı öğrenen bu ardışık düzeninde kullanmanız. Farklı öğrencileriyle ML.NET ve bunların parametrelerini müşteri adayları farklı sonuçlar değiştirme kullanılabilir çıkışı çalışırken featurization adıma benzer. Ayarlayabileceğiniz ayarlamak için [hyperparameters](../resources/glossary.md#hyperparameter) gibi <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, ve <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>. Bu hyperparameters herhangi bir şey model etkiler önce ayarlanır ve modeline özgüdür. Performans için karar ağacı büyük değerler performansı olumsuz yönde etkileyebilir şekilde ayarlamak için kullanılırlar.

Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a>Modeli eğitmek

Modeli eğitmek <xref:Microsoft.ML.PredictionModel%602>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi. `pipeline.Train<SentimentData, SentimentPrediction>()` (verileri trenler featurizer ve öğrenen yükler) ardışık düzen eğitir. Bu işlem yapılana kadar deneme yürütülmedi.

Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Kaydet ve değerlendirme amacıyla kullanmak model eğitilmiş dön

Bu noktada, mevcut veya yeni .NET uygulamalarınızın hiçbirine tümleşik bir modeline sahiptir. Modelinizi döndürmeden önce bir .zip dosyasına kaydetmek için bir sonraki satırda aşağıdaki kodu ekleyin `Train`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

Modelin sonunda dönmek `Train` yöntemi.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirin

Oluşturulan ve model eğitilmiş göre kalite ve doğrulama için farklı bir veri kümesi ile değerlendirmeniz gerekir. İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `Train` değerlendirilecek geçirildi. Oluşturma `Evaluate` yöntemi, hemen sonra `Train`, aşağıdaki kod gibi:

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Evaluate` Yöntemi aşağıdaki görevleri yürütür:

* Test veri yükler.
* İkili değerlendirici oluşturur.
* Model değerlendirir ve ölçümleri oluşturun.
* Ölçümleri görüntüler.

Yeni yönteminden bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntem çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<xref:Microsoft.ML.Data.TextLoader> Sınıfı aynı şema yeni test veri yükler. Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilirsiniz. Aşağıdaki kodu ekleyin `Evaluate` yöntemi:

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Nesne hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma. Bu ölçümler görmek için bir sonraki satırda olarak değerlendirici eklemek `Evaluate` aşağıdaki kod ile yöntemi:

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<xref:Microsoft.ML.Models.BinaryClassificationMetrics> İkili sınıflandırma değerlendiricisi tarafından hesaplanan genel ölçümleri içerir. Bu model kalitesini belirlemek için görüntü için ölçümleri ilk almanız gerekir. Aşağıdaki kodu ekleyin:

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama için ölçümler görüntüleme

Bunlar üzerinde işlem ölçümleri görüntülemek ve sonuçları paylaşmak için aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a>Model ile test veri sonuçlarını tahmin etme

Oluşturma `Predict` yöntemi, hemen sonra `Evaluate` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Predict` Yöntemi aşağıdaki görevleri yürütür:

* Test verileri oluşturur.
* Test verilerine dayalı düşünceleri tahmin eder.
* Test veri ve raporlama için tahminleri birleştirir.
* Tahmin edilen sonuçları görüntüler.

Yeni yönteminden bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntem çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

Eğitilmiş modelinin tahminleri test etmek için bazı açıklamalar ekleme `Predict` yöntemi:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

Bir model sahip olduğunuza göre yorum veri kullanmanın olumlu veya olumsuz düşünceleri tahmin etmek için kullanabileceğiniz <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> yöntemi. Tahmin almak için `Predict` yeni verileri. Giriş verisi dize ve model olduğuna dikkat edin featurization içerir. İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş. Özellikle tahminleri için ön işleme featurization kod yazmak zorunda kaydetmedi ve aynı API batch ve tek seferlik tahminleri mvc'deki.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a>Model operationalization: tahmin

Görüntü `SentimentText` ve sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için karşılık gelen düşünceleri tahmin. Bu işlem ilkeleri bir parçası olarak döndürülen verileri kullanarak operationalization çağrılır. Aşağıdaki kullanarak sonuçları için bir başlık oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

Tahmin edilen sonuçları görüntülemeden önce düşünceleri ve özgün yorum tahmin edilen düşünceleri ile birlikte görmek için tahmini birleştirin. Aşağıdaki kod <xref:System.Linq.Enumerable.Zip%2A> yöntemini gerçekleşen, sağlamak için bu nedenle bu kodu ekleyin sonraki:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

Birleştirilmiş göre `SentimentText` ve `Sentiment` bir sınıfına kullanarak sonuçları görüntüleyebilirsiniz <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemi:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

C# 7.0 C# 7.1 ve projeyi varsayılan dil sürümü yeni bir özellik olan tanımlama grubu öğe adları olan olayla olduğundan, C# 7.1 veya üzeri dil sürümü değiştirmeniz gerekir.
Bunu yapmak için proje düğümüne sağ tıklayın **Çözüm Gezgini** seçip **özellikleri**. Seçin **yapı** sekmesinde ve seçin **Gelişmiş** düğmesi. Açılır listede seçin **C# 7.1** (veya daha yüksek bir sürüm). Seçin **Tamam** düğmesi.

## <a name="results"></a>Sonuçları

Sonuçlar aşağıdakine benzer olmalıdır. Ardışık Düzen işleme gibi iletileri görüntüler. Uyarı veya işlem iletileri görebilirsiniz. Bunlar daha anlaşılır olması için aşağıdaki sonuçları kaldırılmıştır.

```

PredictionModel quality metrics evaluation
------------------------------------------
Accuracy: 66.67%
Auc: 94.44%
F1Score: 75.00%

Sentiment Predictions
---------------------
Sentiment: Please refrain from adding nonsense to Wikipedia. | Prediction: Negative
Sentiment: He is the best, and the article should say that. | Prediction: Positive

```

Tebrikler! Sınıflandırma ve iletileri düşünceleri tahmin için makine öğrenimi modeli şimdi başarıyla oluşturuncaya. Bu öğreticinin için kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) deposu.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, öğrenilen nasıl yapılır:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenme görevini seçin
> * Verilerinizi hazırlama
> * Öğrenme işlem hattı oluşturma
> * Bir sınıflandırıcı yükleme
> * Modeli eğitmek
> * Farklı bir veri kümesi ile modelini değerlendir
> * Model ile test veri sonuçlarını tahmin etme

Daha fazla bilgi için sonraki öğretici ilerleyin
> [!div class="nextstepaction"]
> [Ücreti bir göstergesi olduğu ücreti](taxi-fare.md)
