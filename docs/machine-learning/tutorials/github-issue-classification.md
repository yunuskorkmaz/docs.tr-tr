---
title: GitHub sorunları - sınıflı sınıflandırma sınıflandırma
description: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları için belirli bir alanla atamak sınıflandırmak için nasıl kullanılacağını keşfedin.
ms.date: 05/02/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a4122d0cdfe6531275fabf94743882a82f2a13c1
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063532"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a>Öğretici: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları sınıflandırmak için kullanın.

Bu örnek öğretici ML.NET sınıflandırır ve bir .NET Core konsol uygulaması kullanarak aracılığıyla bir GitHub sorunu alan etiketini tahmin modeli eğitmek için bir GitHub sorunu sınıflandırıcı oluşturma kullanmayı göstermektedir C# Visual Studio'da.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * Verilerinizi hazırlama
> * Verileri dönüştürme
> * Modeli eğitme
> * Modeli değerlendirme
> * Eğitilen modeli tahmin edin
> * Dağıtma ve yüklenen modeliyle tahmin edin

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) depo.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

* [Github sorunlar sekmeyle dosyası (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Github sorunları sekmeyle dosyası (issues_test.tsv) test](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

### <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "GitHubIssueClassification" yazın ve ardından **Tamam** düğmesi.

2. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:

    İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**. "Veri" yazın ve Enter tuşuna basın.

3. Adlı bir dizin oluşturmak *modelleri* modelinizi kaydetmek için projenizde:

    İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**. "Modeli" yazın ve Enter tuşuna basın.

4. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**seçin **v 1.0.0** paketini listede bulun ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

### <a name="prepare-your-data"></a>Verilerinizi hazırlama

1. İndirme [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör. İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.

2. Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

### <a name="create-classes-and-define-paths"></a>Yollarını tanımlamak ve sınıfları oluşturma

Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Yolları kısa bir süre önce indirilen dosyaları ve genel değişkenleri tutmak için üç genel alanlar oluşturmak `MLContext`,`DataView`, ve `PredictionEngine`:

* `_trainDataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.
* `_testDataPath` Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.
* `_modelPath` eğitilen modelin kaydedildiği yolu vardır.
* `_mlContext` olan <xref:Microsoft.ML.MLContext> , işlem bağlamı sağlar.
* `_trainingDataView` olan <xref:Microsoft.ML.IDataView> eğitim veri kümesi işlemek için kullanılır.
* `_predEngine` olan <xref:Microsoft.ML.PredictionEngine%602> tek Tahminler elde etmek için kullanılır.

Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollar ve diğer değişkenlerini belirtmek için:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturun. Yeni bir sınıf, projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *GitHubIssueData.cs*. Ardından, **Ekle** düğmesi.

    *GitHubIssueData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *GitHubIssueData.cs*:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `GitHubIssue` ve `IssuePrediction`, *GitHubIssueData.cs* dosyası:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`label` Tahmin etmek istediğiniz sütun. Tanımlanan `Features` etiketi tahmin modelini size girişleri.

Kullanım [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) veri kümesinde kaynak sütunları dizin belirtmek için.

`GitHubIssue` Giriş veri kümesi sınıfı ve aşağıdaki <xref:System.String> alanlar:

* İlk sütun `ID` (GitHub sorunu kimliği)
* ikinci sütunda `Area` (eğitim tahmin)
* üçüncü sütunda `Title` (GitHub sorun başlığı) sanal makinede ilk `feature` tahmin etmek için kullanılan `Area`
* Dördüncü sütun `Description` ikinci `feature` tahmin etmek için kullanılan `Area`

`IssuePrediction` eğitilen modelin sonra sınıf tahmin için kullanılır. Tek bir sahip `string` (`Area`) ve bir `PredictedLabel` `ColumnName` özniteliği.  `PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.

Tüm ML.NET işlemleri başlangıç süresi [MLContext](xref:Microsoft.ML.MLContext) sınıfı. Başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur. Bu, kavramsal olarak, benzer `DBContext` içinde `Entity Framework`.

### <a name="initialize-variables-in-main"></a>Ana değişkenleri başlatma

Başlatma `_mlContext` yeni bir örneğini genel değişkenin `MLContext` ile rastgele bir tohum (`seed: 0`) arasında birden çok eğitimleri/deterministic tekrarlanabilir sonuçlar.  Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Verileri yükleme

ML.NET kullanan [IDataView sınıfı](xref:Microsoft.ML.IDataView) sayısal ya da metin tablosal verileri açıklamak esnek ve verimli bir yolu olarak. `IDataView` iki metin dosyalarını yükleyebilir veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları).

Başlatma ve yüklemek için `_trainingDataView` ardışık düzeni için kullanmak için genel değişkeni sonra aşağıdaki kodu ekleyin `mlContext` başlatma:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur. Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`.

Sonraki kod satırı olarak ekleyin `Main` yöntemi:

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

`ProcessData` Yöntemi aşağıdaki görevleri yürütür:

* Ayıklar ve verileri dönüştürür.
* İşleme işlem hattı döndürür.

Oluşturma `ProcessData` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Özellikleri ayıklayın ve verileri dönüştürme

Alan GitHub etiketi tahmin etmek istediğiniz gibi bir `GitHubIssue`, kullanın [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) dönüştürmek için yöntemi `Area` sayısal bir anahtar türü sütununa `Label` sütun (sınıflandırma algoritmalarda kabul bir biçimi ) ve yeni veri kümesi bir sütun olarak ekleyin:

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

Ardından, arama `mlContext.Transforms.Text.FeaturizeText` metin dönüştürür (`Title` ve `Description`) sayısal bir vektör her adlı sütuna `TitleFeaturized` ve `DescriptionFeaturized`. Aşağıdaki kod ile işlem hattı her iki sütun için özellik kazandırma sayesinde ekleyin:

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) yöntemi. Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun. Aşağıdaki kod ile işlem hattı için bu dönüşümü ekleyin:

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 Ardından, ekleme bir <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> üzerinden yineleme yapma, verileri birden çok kez önbellek kullanarak daha iyi performans için şu kod gibi alabilirsiniz şekilde DataView önbelleğe almak için:

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> Eğitim süresini azaltmak için AppendCacheCheckpoint küçük/Orta veri kümeleri için kullanın. (Kaldırın. bunu kullanmayın Çok büyük veri kümelerinde işlerken AppendCacheCheckpoint()).

Ardışık Düzen sonunda dönüş `ProcessData` yöntemi.

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

Bu adımda, ön işleme/özellik kazandırma sayesinde işler. ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.

## <a name="build-and-train-the-model"></a>Derleme ve modeli eğitme

Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main` yöntemi:

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` Yöntemi aşağıdaki görevleri yürütür:

* Eğitim algoritması sınıfı oluşturur.
* Modeli eğitir.
* Eğitim verilerini temel alarak alan tahmin eder.
* Model döndürür.

Oluşturma `BuildAndTrainModel` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>Sınıflandırma görevi hakkında

Sınıflandırma olan verileri kullanan bir makine öğrenimi görev **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı ve sık sık aşağıdaki türlerden biridir:

* İkili: ya da A veya b
* Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.

Bu sorun türü için birden çok kategoriden (veya çoklu sınıflar) sorun kategorisi tahmininizde olabileceği algoritması, öğrenme veya çoklu sınıflar sınıflandırması yalnızca iki yerine kullanın (ikili).

Machine learning algoritmasını kod ilk satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarını ekleme `BuildAndTrainModel()`:

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) sınıflı sınıflandırma eğitim algoritmasıdır. Bu eklenen `pipeline` ve özellikleri tespit `Title` ve `Description` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.

### <a name="train-the-model"></a>Modeli eğitme

Modele uygun `splitTrainSet` veri ve sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen model dönüş `BuildAndTrainModel()` yöntemi:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

`Fit()`Yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) geçirin ve ardından verileri tek bir örneğini tahmin gerçekleştirin izin veren bir kolaylık API, bir özelliktir. Bu sonraki satırı olarak ekleyin `BuildAndTrainModel()` yöntemi:

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Eğitilen modeli tahmin edin

Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

Kullanım [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi tahmin verilerinin tek bir satırda yapar:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Modeli kullanılarak: tahmin sonuçlarını

Görüntü `GitHubIssue` ve karşılık gelen `Area` tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için etiket.  Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Değerlendirme için kullanılacak modeli eğitilir döndürür

Model sonunda dönüş `BuildAndTrainModel` yöntemi.

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir. İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `BuildAndTrainModel` değerlendirilecek geçirilir. Oluşturma `Evaluate` yöntemi hemen sonrasına `BuildAndTrainModel`, aşağıdaki kod gibi:

```csharp
public static void Evaluate()
{

}
```

`Evaluate` Yöntemi aşağıdaki görevleri yürütür:

* Test veri kümesini yükler.
* Çok sınıflı değerlendirici oluşturur.
* Model değerlendirir ve metrikleri oluşturma.
* Ölçümleri görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `BuildAndTrainModel` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

Aşağıdaki kodu ekleyerek eğitim veri kümesi ile daha önce yaptığınız gibi test veri kümesini yüklemek `Evaluate` yöntemi:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

[Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) yöntemi, belirtilen veri kümesi kullanan model için Kalite Ölçümleri hesaplar. Döndürür bir <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> sınıflı sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne.
Model kalitesini belirlemek için ölçümleri görüntülemek için bunları ilk almanız gerekir.
Kullanımına dikkat edin [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) machine Learning yöntemi `_trainedModel` genel değişkeni (bir [ITransformer](xref:Microsoft.ML.ITransformer)) özellikleri giriş ve tahmin döndürmek için. Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

Aşağıdaki ölçümler sınıflı sınıflandırma için değerlendirilir:

* Mikro doğruluğu - her örnek sınıfı çifti eşit doğruluğu ölçüme katkıda bulunur.  Mikro doğruluğu, 1 olarak mümkün olduğunca yakın olmasını istediğiniz.

* Makro doğruluğu - her sınıf eşit doğruluğu ölçüme katkıda bulunur. Azınlık sınıfları daha büyük bir sınıf olarak eşit ağırlık verilir. Makrosu 1 olarak mümkün olduğunca yakın olmasını doğruluğu kullanmanız gerekir.

* Günlük zarar - bkz [günlük kaybı](../resources/glossary.md#log-loss). Sıfır olarak mümkün olduğunca yakın olmasını günlük zarar kullanmanız gerekir.

* Günlük kaybı azaltma - aralıkları gelen [-INF, 100], burada 100 mükemmel Öngörüler ve 0, ortalama Öngörüler gösterir. Günlük kaybı azaltma sıfır olarak mümkün olduğunca yakın olmasını istediğiniz.

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama için ölçümleri görüntüleme

Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="deploy-and-predict-with-a-model"></a>Dağıtma ve bir modeli tahmin edin

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

Oluşturma `PredictIssue` yöntemi hemen sonrasına `Evaluate` yöntemi (ve hemen önce `SaveModelAsFile` yöntemi), aşağıdaki kodu kullanarak:

```csharp
private static void PredictIssue()
{

}
```

`PredictIssue` Yöntemi aşağıdaki görevleri yürütür:

* Test verilerini tek bir konu oluşturur.
* Test verilerini temel alarak alan tahmin eder.
* Bir araya getirir, verileri ve raporlama için Öngörüler test edin.
* Tahmin edilen sonuçları görüntüler.

Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

Daha önce yaptığınız gibi oluşturun bir `PredictionEngine` aşağıdaki kod örneği:

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
Kullanım `PredictionEngine` alan GitHub etiketi için aşağıdaki kodu ekleyerek tahmin etmek için `PredictIssue` yöntemi tahmin için:

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Tahmin için yüklenen modeli kullanma

Görüntü `Area` sorunu kategorilere ayırmak ve buna göre hareket üzerinde için. Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>Sonuçlar

Sonuçlar aşağıdakine benzer olmalıdır. İşlem hattı işlediği gibi iletileri görüntüler. Uyarıları ve iletileri işlemeyi görebilirsiniz. Bu iletiler, anlaşılması için aşağıdaki sonuçlarından kaldırıldı.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Tebrikler! Bir machine learning modeli sınıflandırmak ve bir alan etiketini bir GitHub sorunu için tahmin etmek için şimdi başarıyla oluşturdunuz. Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) depo.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> * Verilerinizi hazırlama
> * Verileri dönüştürme
> * Modeli eğitme
> * Modeli değerlendirme
> * Eğitilen modeli tahmin edin
> * Dağıtma ve yüklenen modeliyle tahmin edin

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Taksi taksi göstergesi](taxi-fare.md)
