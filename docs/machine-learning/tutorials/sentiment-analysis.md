---
title: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu
description: ML.NET ikili sınıflandırma senaryoda yaklaşım tahmin uygun eylemde için nasıl kullanılacağını anlamak için nasıl kullanılacağını keşfedin.
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7d2935fafe9dbad28205c8a896d97d80474a686f
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028085"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Öğretici: Kullanımı bir yaklaşım analizi ikili sınıflandırma senaryosunda ML.NET

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu örnek öğretici, C# kullanarak Visual Studio 2017'de .NET Core konsol uygulaması aracılığıyla bir yaklaşım sınıflandırıcı oluşturma ML.NET kullanılması gösterilmektedir.

Bu öğreticide, şunların nasıl yapılır:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenimi görevini seçin
> * Verilerinizi hazırlama
> * Öğrenme işlem hattınızı oluşturun
> * Sınıflandırıcı yükleme
> * Modeli eğitme
> * Farklı bir veri kümesiyle modeli değerlendirme
> * Modeli ile test veri sonuçlarını tahmin edin

## <a name="sentiment-analysis-sample-overview"></a>Yaklaşım analizi örneğine genel bakış

Örnek ML.NET sınıflandırır ve yaklaşım artı veya eksi olarak tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır. Ayrıca, kalite analizi için ikinci bir veri kümesi modeliyle değerlendirir. Yaklaşım veri kümeleri WikiDetox projeden ' dir.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

* [Wikipedia detox satır veri sekmeyle ayrılmış dosya (wikiPedia-detox-250-satırı-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).
* [Wikipedia detox satır test sekmeyle ayrılmış dosya (wikipedia-detox-250-satırı-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).

## <a name="machine-learning-workflow"></a>Machine learning iş akışı

Bu öğreticide, bir makine öğrenimi düzenli bir şekilde taşımak işlem sağlayan bir iş akışı izler.

İş akışı aşamalar aşağıdaki gibidir:

1. **Sorunu anlama**
2. **Veri alma**
3. **Verileri önceden işleme ve özellik Mühendisliği**
4. **Eğitme ve modeli tahmin edin**
5. **Modeli değerlendirme**
6. **Modeli kullanıma hazır hale getirme**

### <a name="understand-the-problem"></a>Sorunu anlama

Öncelikle, oluşturmak ve modeli eğitmek destekleyebileceği bölümleri aşağı kesmek için sorunu anlamak gerekir. Sorun bozucu, tahmin edin ve sonuçları değerlendirin olanak tanır.

Sorun Bu öğretici için uygun eylemi gerçekleştirin gelen Web sitesi açıklama yaklaşım öğrenmektir.

Problemi yaklaşım metin ve duyarlılık değeri ile modeli eğitmek için istediğiniz verileri için ve tahmin edilen duyarlılık değeri değerlendirmek ve işletimsel olarak kullanmak dökümünü alabilirsiniz.

Ardından gerek **belirlemek** yaklaşımı, Görev Seçimi öğrenme makineyle yardımcı olur.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Bu sorun aşağıdaki gerçekleri bildirin:

Eğitim verileri: Web sitesi açıklamaları pozitif veya negatif olabilir (**yaklaşım**).
Tahmin **yaklaşım** açıklamasının bir yeni Web sitesi, pozitif veya negatif gibi aşağıdaki örnekte:

* Lütfen anlamsız Wikipedia için makalelerinizde.
* Kendisi için en iyi yöntemdir ve makale, yazması gerekir.

Sınıflandırma machine learning görevi bu senaryo için idealdir.

### <a name="about-the-classification-task"></a>Sınıflandırma görevi hakkında

Sınıflandırma olan verileri kullanan bir makine öğrenimi görev **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı. Örneğin, sınıflandırma için kullanabilirsiniz:

* Artı veya eksi olarak duyguları tanımlayın.
* E-posta klasörünüzü veya iyi istenmeyen sınıflandırın.
* Bir hastanın Laboratuvar örnek cancerous olup olmadığını belirler.
* Müşteriler, kendi eğilimini yanıt satış kampanyaya göre kategorilere ayırın.

Sınıflandırma görevleri sık aşağıdaki türlerden biri şunlardır:

* İkili: ya da A veya b
* Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.

## <a name="create-a-console-application"></a>Bir konsol uygulaması oluşturun

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.

2. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:

    İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**. "Veri" yazın ve Enter tuşuna basın.

3. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

### <a name="prepare-your-data"></a>Verilerinizi hazırlama

1. İndirme [WikiPedia detox-250-satırı-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) ve [wikipedia-detox-250-satırı-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör. İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.

2. Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

### <a name="create-classes-and-define-paths"></a>Yollarını tanımlamak ve sınıfları oluşturma

Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

Yolları için kısa bir süre önce indirilen dosyaları tutmak için üç genel alanlar oluşturmak ihtiyacınız vardır:

* `_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.
* `_testDataPath` Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.
* `_modelPath` eğitilen modelin kaydedildiği yolu vardır.

Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollarını belirtmek için:

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir. Yeni bir sınıf, projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*. Ardından, **Ekle** düğmesi.

    *SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` Giriş veri kümesi sınıfı ve bir `float` (`Sentiment`) pozitif veya negatif yaklaşım için bir değer ve bir dize yorumu için olan (`SentimentText`). Her iki alanınız `Column` öznitelikleri kendisine bağlı. Bu öznitelik her bir alanın veri dosyası ve olduğu siparişi açıklayan `Label` alan. `SentimentPrediction` eğitilen modelin sonra sınıf tahmin için kullanılır. Tek bir Boole değeri vardır (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği. `Label` Oluşturup modeli ya da onun da model değerlendirmek için ikinci bir veri kümesi ile kullanılan eğitmek için kullanılır. `PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.

İçinde *Program.cs* dosya, değişiklik `Main` değiştirerek yöntem imzası `void` ile `async Task`, aşağıdaki örnekte olduğu gibi:

```csharp
static async Task Main(string[] args) 
{

}
```

Eklediğiniz `async` için `Main` ile bir <xref:System.Threading.Tasks.Task> dönüş türü bir zip dosyasına daha sonra modeli kaydediyorsanız ve program, dış görev tamamlanana kadar beklemesi gerekir.

> [!NOTE]
> Bir *async main* yöntemi kullanmanıza olanak sağlar `await` içinde `Main` yöntemi. Daha fazla bilgi için [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) konusu C# programlama kılavuzu.

Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

`Train` Yöntemi aşağıdaki görevleri yürütür:

* Yükler veya verilerini alır.
* Önceden işler ve featurizes verileri.
* Modeli eğitir.
* Test verilerine dayalı yaklaşım tahmin eder.

Oluşturma `Train` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a>Veri alma

Yeni bir örneğini başlatır <xref:Microsoft.ML.LearningPipeline> veri yükleme, veri işleme/özellik kazandırma sayesinde ve model içerecektir. İlk satırı olarak aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<xref:Microsoft.ML.Data.TextLoader> Nesne ilk işlem hattı parçasıdır ve eğitim dosya verileri yükler.

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a>Verileri önceden işleme ve özellik Mühendisliği

Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir. Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir. Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir. ML. NET dönüştürme işlem hatları, eğitim veya test etmeden önce verilerinizi uygulanan dönüştürmeler özel bir dizi oluşturmak izin verin. Dönüşümler birincil amacı veri özellik kazandırma sayesinde için ' dir. Bir dönüştürme ardışık düzen avantajı, test verileri uygulamak için işlem hattı kaydetme dönüştürme işlem hattı tanımını sonra olmasıdır.

Geçerli bir <xref:Microsoft.ML.Transforms.TextFeaturizer> dönüştürülecek `SentimentText` sütununa bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector) adlı `Features` makine öğrenimi algoritması tarafından kullanılan. Bu ön işleme/özellik kazandırma sayesinde adımdır. ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz. Ekleme `TextFeaturizer` ardışık düzenine sonraki kod satırına olarak:

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> Bu işlem hattında kullanacağınız karar ağacı learner nesnedir. ML.NET ve kendi parametrelerini müşteri adayları için farklı sonuçlar değiştirerek mevcut farklı öğrencileriyle denemeye özellik kazandırma sayesinde adıma benzer. Ayarlayabileceğiniz ayarlama için [hiperparametreleri](../resources/glossary.md#hyperparameter) gibi <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, ve <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>. Bu hiperparametreleri herhangi bir şey model etkiler önce ayarlanır ve model özgüdür. Karar ağacı performans için daha büyük bir değer performansı olumsuz yönde etkileyebilir şekilde ayarlamak için kullanılırlar.

Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a>Modeli eğitme

Modeli eğitme <xref:Microsoft.ML.PredictionModel%602>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi. `pipeline.Train<SentimentData, SentimentPrediction>()` (veri trenler özelliği oluşturucu ve learner yükler) işlem hattı eğitir. Denemeyi böyle kadar yürütülmez.

Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Kaydet ve değerlendirme için kullanılacak modeli eğitilir dön

Bu noktada, tüm mevcut veya yeni .NET uygulamalarınızı tümleşik bir model var. Modelinizi döndürmeden önce bir .zip dosyası olarak kaydetmek için sonraki satıra aşağıdaki kodu ekleyin `Train`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

Model sonunda dönüş `Train` yöntemi.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir. İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `Train` değerlendirilecek geçirilir. Oluşturma `Evaluate` yöntemi hemen sonrasına `Train`, aşağıdaki kod gibi:

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Evaluate` Yöntemi aşağıdaki görevleri yürütür:

* Test veri kümesini yükler.
* İkili değerlendirici oluşturur.
* Model değerlendirir ve metrikleri oluşturma.
* Ölçümleri görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<xref:Microsoft.ML.Data.TextLoader> Sınıfı aynı şemaya sahip yeni test veri kümesini yükler. Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir. Aşağıdaki kodu ekleyin `Evaluate` yöntemi:

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<xref:Microsoft.ML.Models.BinaryClassificationEvaluator> Nesne hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma. Bu ölçümler görmek için bir sonraki satırda olarak değerlendirici ekleyin `Evaluate` yöntemi, aşağıdaki kod ile:

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<xref:Microsoft.ML.Models.BinaryClassificationMetrics> İkili sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içerir. Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir. Aşağıdaki kodu ekleyin:

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama için ölçümleri görüntüleme

Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a>Modeli ile test veri sonuçlarını tahmin edin

Oluşturma `Predict` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Predict` Yöntemi aşağıdaki görevleri yürütür:

* Test verileri oluşturur.
* Test verilerine dayalı yaklaşım tahmin eder.
* Bir araya getirir, verileri ve raporlama için Öngörüler test edin.
* Tahmin edilen sonuçları görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `Predict` yöntemi:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

Bir modeliniz olduğuna göre pozitif veya negatif yaklaşım açıklama verileri kullanarak tahmin etmek için kullanabileceğiniz <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> yöntemi. Bir öngörü almak için kullanın `Predict` yeni veriler. Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın. İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş. Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a>Modeli kullanıma hazır hale getirme: tahmin

Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için. Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır. Aşağıdakileri kullanarak sonuçları için bir başlık oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

Tahmin edilen sonuçlarını görüntülemeden önce yaklaşımını ve özgün açıklamayı, tahmin edilen yaklaşım ile birlikte görmek için tahmini birleştirin. Aşağıdaki kod <xref:System.Linq.Enumerable.Zip%2A> gerçekleşen, yapmanız gereken yöntemini bu nedenle bu kodunu ekleyin sonraki:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

Birleştirilmiş göre `SentimentText` ve `Sentiment` bir sınıf kullanarak sonuçları görüntüleyebilirsiniz <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemi:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

C# 7.0 C# 7.1 ve projenin varsayılan dil sürümü yeni bir özellik olan demet öğesi adları olan olayla olduğundan, C# 7.1 veya üzeri dil sürümünü değiştirmek gerekir.
Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**. Seçin **derleme** sekmenize **Gelişmiş** düğmesi. Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm). Seçin **Tamam** düğmesi.

## <a name="results"></a>Sonuçları

Sonuçlar aşağıdakine benzer olmalıdır. İşlem hattı işlediği gibi iletileri görüntüler. Uyarıları ve iletileri işlemeyi görebilirsiniz. Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.

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

Tebrikler! Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz. Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide şunları öğrendiniz: nasıl yapılır:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenimi görevini seçin
> * Verilerinizi hazırlama
> * Öğrenme işlem hattınızı oluşturun
> * Sınıflandırıcı yükleme
> * Modeli eğitme
> * Farklı bir veri kümesiyle modeli değerlendirme
> * Modeli ile test veri sonuçlarını tahmin edin

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Taksi taksi göstergesi](taxi-fare.md)
