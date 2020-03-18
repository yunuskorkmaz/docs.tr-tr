---
title: 'Öğretici: Destek sorunlarını kategorilere ayırın - çok sınıflı sınıflandırma'
description: ML.NET,ML.NET belirli bir alana atamak üzere GitHub sorunlarını sınıflandırmak için çok sınıflı bir sınıflandırma senaryosunda nasıl kullanacağını keşfedin.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 50980cd933054825bf21f955b0341dd8e66f3e62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78239943"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a>Öğretici: ML.NET ile çok sınıflı sınıflandırma kullanarak destek sorunlarını kategorilere ayırın

Bu örnek öğretici, Visual Studio'da C# kullanarak bir .NET Core konsol uygulaması aracılığıyla GitHub sorunu için Alan etiketini sınıflandıran ve tahmin eden bir modeli eğitmek için bir GitHub sorun sınıflandırıcısı oluşturmak için ML.NET kullanılmasını göstermektedir.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> * Verilerinizi hazırlama
> * Verileri dönüştürme
> * Modeli eğitme
> * Modeli değerlendirme
> * Eğitimli model ile tahmin edin
> * Yüklü bir modelle Dağıtma ve Tahmin Etme

Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.

* [Github sorunları sekmesi ayrılmış dosya (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Github sorunları test sekmesi ayrılmış dosya (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

### <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 2017'yi açın. Menü çubuğundan**Yeni** > **Proje** **Dosyası'nı** > seçin. Yeni **Proje** iletişim kutusunda, **.NET Core** düğümünü izleyen **Visual C#** düğümünü seçin. Ardından **Konsol Uygulaması (.NET Core)** proje şablonu'nu seçin. **Ad** metin kutusunda "GitHubIssueClassification" yazın ve **ardından Tamam** düğmesini seçin.

2. Veri seti dosyalarınızı kaydetmek için projenizde *Veri* adlı bir dizin oluşturun:

    **Çözüm Gezgini'nde,** projenize sağ tıklayın ve**Yeni Klasör** **Ekle'yi** > seçin. "Veri" yazın ve Enter tuşuna basın.

3. Modelinizi kaydetmek için projenizde *Modeller* adlı bir dizin oluşturun:

    **Çözüm Gezgini'nde,** projenize sağ tıklayın ve**Yeni Klasör** **Ekle'yi** > seçin. "Modeller" yazın ve Enter tuşuna basın.

4. Microsoft.ML **NuGet Paketini**Yükleyin:

    Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML** arayın ve **Yükle** düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.

### <a name="prepare-your-data"></a>Verilerinizi hazırlama

1. [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri kümelerini indirin ve bunları daha önce oluşturulmuş *Veri* klasörüne kaydedin. İlk veri seti makine öğrenme modelini eğitir ve ikincisi modelinizin ne kadar doğru olduğunu değerlendirmek için kullanılabilir.

2. Çözüm Gezgini'nde \*,tsv dosyalarının her birini sağ tıklatın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıflar oluşturma ve yolları tanımlama

Aşağıdaki ek `using` deyimleri *Program.cs* dosyasının üstüne ekleyin:

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

En son indirilen dosyalara giden yolları tutmak için üç genel `MLContext`alan`DataView`ve `PredictionEngine`aşağıdakiler için genel değişkenler oluşturun:

* `_trainDataPath`modeli eğitmek için kullanılan veri kümesine giden yola sahiptir.
* `_testDataPath`modeli değerlendirmek için kullanılan veri kümesine giden yolu vardır.
* `_modelPath`eğitilmiş modelin kaydedildiği yola sahiptir.
* `_mlContext`işleme <xref:Microsoft.ML.MLContext> bağlamını sağlayan dır.
* `_trainingDataView`eğitim <xref:Microsoft.ML.IDataView> veri kümesini işlemek için kullanılır.
* `_predEngine`tek <xref:Microsoft.ML.PredictionEngine%602> tahminler için kullanılır.

Bu yolları ve diğer değişkenleri `Main` belirtmek için yöntemin hemen üstündeki satıra aşağıdaki kodu ekleyin:

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

Giriş verileriniz ve öngörüleriniz için bazı sınıflar oluşturun. Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.

1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *GitHubIssueData.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.

    kod düzenleyicisinde *GitHubIssueData.cs* dosya açılır. GitHubIssueData.cs üstüne `using` aşağıdaki ifadeyi *GitHubIssueData.cs*ekleyin:

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

Varolan sınıf tanımını kaldırın ve iki sınıfı `GitHubIssue` `IssuePrediction`ve *GitHubIssueData.cs* dosyasına aşağıdaki kodu ekleyin:

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

Tahmin `label` etmek istediğiniz sütundur. Tanımlanan, `Features` Etiketi tahmin etmek için modele verdiğiniz girdilerdir.

Veri kümesindeki kaynak sütunların dizinlerini belirtmek için [LoadColumnAtöz'ü](xref:Microsoft.ML.Data.LoadColumnAttribute) kullanın.

`GitHubIssue`giriş veri kümesi sınıfıdır ve <xref:System.String> aşağıdaki alanlara sahiptir:

* ilk sütun `ID` (GitHub Sorun Kimliği)
* ikinci sütun `Area` (eğitim için tahmin)
* üçüncü sütun `Title` (GitHub sorun başlığı) `feature` ilk tahmin etmek için kullanılan`Area`
* dördüncü sütun, `Description` `feature``Area`

`IssuePrediction`model eğitildikten sonra tahmin için kullanılan sınıftır. Tek `string` bir (`Area`) `PredictedLabel` `ColumnName` ve bir özniteliği vardır.  Tahmin `PredictedLabel` ve değerlendirme sırasında kullanılır. Değerlendirme için, eğitim verileri, öngörülen değerler ve model ile bir giriş kullanılır.

Tüm ML.NET işlemleri [MLContext](xref:Microsoft.ML.MLContext) sınıfında başlar. İlk `mlContext` başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur. Kavramsal olarak `DBContext` `Entity Framework`benzer.

### <a name="initialize-variables-in-main"></a>Main'deki değişkenleri başlatma

`_mlContext` Birden çok eğitim arasında tekrarlanabilir/deterministik sonuçlar için rasgele bir tohum () `MLContext` `seed: 0`ile yeni bir örnek ile küresel değişkeni başlangıç.  `Console.WriteLine("Hello World!")` Satırı yöntemde aşağıdaki kodla `Main` değiştirin:

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Verileri yükleme

ML.NET, sayısal veya metin tabular verileri açıklamanın esnek ve verimli bir yolu olarak [IDataView sınıfını](xref:Microsoft.ML.IDataView) kullanır. `IDataView`metin dosyalarını veya gerçek zamanlı olarak yükleyebilir (örneğin, SQL veritabanı veya günlük dosyaları).

Ardışık `_trainingDataView` düzen için kullanmak için global değişkeni başlatmave yüklemek için, `mlContext` başlatmadan sonra aşağıdaki kodu ekleyin:

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyada okur. Veri yolu değişkenlerini alır ve `IDataView`bir .

`Main` Yöntemde bir sonraki kod satırı olarak aşağıdakileri ekleyin:

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

Yöntem `ProcessData` aşağıdaki görevleri yürütür:

* Verileri ayıklar ve dönüştürür.
* İşleme ardışık hattını döndürür.

Yöntemden `ProcessData` `Main` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Özellikleri Ayıklayın ve verileri dönüştürün

Bir için Alan GitHub etiketini `GitHubIssue`tahmin etmek istediğinizde, `Area` sütunu sayısal anahtar türü `Label` sütununa (sınıflandırma algoritmaları tarafından kabul edilen bir biçim) dönüştürmek ve yeni bir veri kümesi sütunu olarak eklemek için [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanın:

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

Ardından, `mlContext.Transforms.Text.FeaturizeText` metin (`Title` ve `Description`) sütunlarını çağrılan `TitleFeaturized` her biri için `DescriptionFeaturized`sayısal bir vektöre dönüştüren çağrı ve . Her iki sütun için de aşağıdaki kodla ardışık ardışıklaştırmayı tamamlayın:

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

Veri hazırlamadaki son adım, Tüm özellik sütunlarını [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) yöntemini kullanarak **Özellikler** sütununa birleştirir. Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler. Bu dönüşümü aşağıdaki kodla ardışık ardışık olarak tamamlayın:

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 Ardından, önbelleği kullanarak verileri birden çok kez yinelediğinizde aşağıdaki kodda olduğu gibi daha iyi performans elde edilebilsin diye DataView'ı önbelleğe almak için bir <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> ekleyin:

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> Eğitim süresini düşürmek için küçük/orta veri kümeleri için AppendCacheCheckpoint'i kullanın. KULLANMAYIN (kaldırın. Çok büyük veri kümelerini işlerken AppendCacheCheckpoint())

Yöntemin sonunda boru hattını `ProcessData` döndürün.

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

Bu adım, ön işleme/featurization işler. ML.NET'da bulunan ek bileşenleri kullanmak, modelinizde daha iyi sonuçlar elde etmenizi sağlayabilir.

## <a name="build-and-train-the-model"></a>Modeli oluşturma ve eğitme

Yöntemde `BuildAndTrainModel`bir sonraki kod satırı olarak yönteme `Main` aşağıdaki çağrıyı ekleyin:

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

Yöntem `BuildAndTrainModel` aşağıdaki görevleri yürütür:

* Eğitim algoritması sınıfını oluşturur.
* Modeli eğitir.
* Eğitim verilerine göre alanı tahmin eder.
* Modeli döndürür.

Yöntemden `BuildAndTrainModel` `Main` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>Sınıflandırma görevi hakkında

Sınıflandırma, bir öğenin veya veri satırının kategorisini, türünü veya sınıfını **belirlemek** için verileri kullanan ve sık sık aşağıdaki türlerden biri olan bir makine öğrenimi görevidir:

* İkili: A veya B.
* Çok sınıflı: Tek bir model kullanılarak tahmin edilebilen birden çok kategori.

Sorun kategorisi tahmini yalnızca iki (ikili) yerine birden çok kategoriden (çok sınıflı) biri olabileceğinden, bu tür bir sorun için çok sınıflı sınıflandırma öğrenme algoritması kullanın.

Makine öğrenme algoritmasını veri dönüştürme tanımlarına ilk kod satırı olarak ekleyerek `BuildAndTrainModel()`ekle:

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) sizin çok sınıflı sınıflandırma eğitim algoritmanızdır. Bu, geçmiş `pipeline` verilerden öğrenmek için featurized`Features` `Label` `Title` ve `Description` ( ) ve giriş parametrelerini kabul eder.

### <a name="train-the-model"></a>Modeli eğitme

Modeli `splitTrainSet` verilere sığdırın ve yöntemde bir sonraki kod satırı olarak `BuildAndTrainModel()` aşağıdakileri ekleyerek eğitilmiş modeli döndürün:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

Yöntem, `Fit()`veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitiyor.

[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde bir tahmin gerçekleştirmenize ve geçiş yapmanızı sağlayan kolaylık api'sidir. `BuildAndTrainModel()` Yöntemde bir sonraki satır olarak bunu ekleyin:

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Eğitimli model ile tahmin edin

Bir örnek oluşturarak `Predict` yöntemde eğitimli modelin tahmin test etmek `GitHubIssue`için bir GitHub sorunu ekleyin:

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevini kullanma, tek bir veri satırı nda öngörüyapar:

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Modeli kullanma: tahmin sonuçları

Sonuçları `GitHubIssue` paylaşmak `Area` ve buna göre hareket etmek için etiket tahminini görüntüleyin.  Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu kullanarak sonuçlar için bir ekran oluşturun:

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Değerlendirme için kullanılmak üzere eğitilmiş modeli döndürme

Yöntemin sonunda modeli döndürün. `BuildAndTrainModel`

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Modeli oluşturduğunuz ve eğittiğinize göre, modeli kalite güvencesi ve doğrulama için farklı bir veri kümesiyle değerlendirmeniz gerekir. `Evaluate` Yöntemde, oluşturulan model `BuildAndTrainModel` değerlendirilmek üzere geçirilir. Aşağıdaki `Evaluate` kodda olduğu `BuildAndTrainModel`gibi, hemen sonra yöntemi oluşturun:

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

Yöntem `Evaluate` aşağıdaki görevleri yürütür:

* Test veri kümesini yükler.
* Çok sınıflı değerlendirici oluşturur.
* Modeli değerlendirir ve ölçümleri oluşturur.
* Ölçümleri görüntüler.

Aşağıdaki kodu `Main` kullanarak, yöntem çağrısının `BuildAndTrainModel` hemen altında, yöntemden yeni yönteme çağrı ekleyin:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

Daha önce eğitim veri setinde yaptığınız gibi, yönteme aşağıdaki kodu ekleyerek `Evaluate` test veri kümesini yükleyin:

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

[Değerlendirme()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) yöntemi, belirtilen veri kümesini kullanarak modelin kalite ölçümlerini hesaplar. Çok sınıflı sınıflandırma değerlendiriciler tarafından hesaplanan genel ölçümleri içeren bir <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> nesne döndürür.
Modelin kalitesini belirlemek için ölçümleri görüntülemek için önce bunları almanız gerekir.
Özellikleri ve dönüş tahminlerini girdi etmek `_trainedModel` için makine öğrenme global değişkeninin (bir [ITransformer)](xref:Microsoft.ML.ITransformer) [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yönteminin kullanımına dikkat edin. `Evaluate` Yönteme sonraki satır olarak aşağıdaki kodu ekleyin:

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

Aşağıdaki ölçümler çok sınıflı sınıflandırma için değerlendirilir:

* Mikro Doğruluk - Her örnek sınıfı çifti doğruluk ölçümüne eşit katkıda bulunur.  Micro Accuracy'in mümkün olduğunca yakın olmasını istiyorsunuz.

* Makro Doğruluğu - Her sınıf doğruluk ölçümüne eşit katkıda bulunur. Azınlık sınıfları daha büyük sınıflar olarak eşit ağırlık verilir. Makro Doğruluğu'nun mümkün olduğunca yakın olmasını istiyorsunuz.

* Günlük kaybı - [bkz.](../resources/glossary.md#log-loss) Log-loss'un mümkün olduğunca sıfıra yakın olmasını istiyorsunuz.

* Günlük kaybı azaltma - 1.00'In mükemmel tahminleri olduğu ve 0'ın ortalama tahminleri gösterdiği [-inf, 1.00]'den aralıklar. Günlük kaybı azaltmanın mümkün olduğunca yakın olmasını istiyorsunuz.

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama için ölçümlerin görüntülenmesi

Ölçümleri görüntülemek, sonuçları paylaşmak ve sonra bunlara göre hareket etmek için aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>Modeli bir dosyaya kaydetme

Modelinizden memnun kaldıktan sonra, daha sonra veya başka bir uygulamada öngörülerde bulunmak için dosyayı bir dosyaya kaydedin. `Evaluate` yöntemine aşağıdaki kodu ekleyin.

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

Yönteminizin `SaveModelAsFile` `Evaluate` altındaki yöntemi oluşturun.

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Yönteminize `SaveModelAsFile` aşağıdaki kodu ekleyin. Bu kod, [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) eğitilen modeli zip dosyası olarak seri hale getirmek ve depolamak için yöntemi kullanır.

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>Bir modelle Dağıtma ve Tahmin Etme

Aşağıdaki kodu `Main` kullanarak, yöntem çağrısının `Evaluate` hemen altında, yöntemden yeni yönteme çağrı ekleyin:

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

Yöntemden `PredictIssue` `Evaluate` hemen sonra (ve yöntemden `SaveModelAsFile` hemen önce) aşağıdaki kodu kullanarak yöntemi oluşturun:

```csharp
private static void PredictIssue()
{

}
```

Yöntem `PredictIssue` aşağıdaki görevleri yürütür:

* Kaydedilen modeli yükler
* Tek bir test verisi sorunu oluşturur.
* Test verilerine göre Alanı tahmin eder.
* Raporlama için test verilerini ve öngörüleri birleştirir.
* Öngörülen sonuçları görüntüler.

Yönteme aşağıdaki kodu ekleyerek kaydedilen modeli uygulamanıza yükleyin: `PredictIssue`

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

Bir örnek oluşturarak `Predict` yöntemde eğitimli modelin tahmin test etmek `GitHubIssue`için bir GitHub sorunu ekleyin:

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

Daha önce yaptığınız gibi, `PredictionEngine` aşağıdaki kodu içeren bir örnek oluşturun:

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir. Tek dişli veya prototip ortamlarda kullanılabilir. Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın. ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.

> [!NOTE]
> `PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.

Tahmin `PredictionEngine` `PredictIssue` yöntemine aşağıdaki kodu ekleyerek Area GitHub etiketini tahmin etmek için kullanın:

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Tahmin için yüklenen modeli kullanma

Sorunu `Area` kategorilere ayırmak ve buna göre hareket etmek için görüntüleyin. Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodu kullanarak sonuçlar için bir ekran oluşturun:

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a>Sonuçlar

Sonuçlarınız aşağıdakilere benzer olmalıdır. Ardışık işlem olarak, iletileri görüntüler. Uyarılar veya iletileri işleme görebilirsiniz. Bu iletiler netlik için aşağıdaki sonuçlardan kaldırıldı.

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

Tebrikler! Şimdi başarılı bir şekilde sınıflandırmak ve bir GitHub sorunu için bir Alan etiketi tahmin için bir makine öğrenme modeli inşa ettik. Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Verilerinizi hazırlama
> * Verileri dönüştürme
> * Modeli eğitme
> * Modeli değerlendirme
> * Eğitimli model ile tahmin edin
> * Yüklü bir modelle Dağıtma ve Tahmin Etme

Daha fazla bilgi edinmek için bir sonraki öğreticiye ilerleyin
> [!div class="nextstepaction"]
> [Taksi Ücreti Tahmincisi](predict-prices.md)
