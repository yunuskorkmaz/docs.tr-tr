---
title: 'Öğretici: destek sorunlarını kategorilere ayırma-birden çok Lass sınıflandırması'
description: Birden çok Lass sınıflandırma senaryosunda ML.NET kullanarak bunları belirli bir alana atamaya yönelik GitHub sorunlarını sınıflandırın.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 7507463cfc5504182f028ab2ced9a03733c61f6d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774494"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a>Öğretici: ML .NET ile birden çok Lass sınıflandırması kullanarak destek sorunlarını kategorilere ayırma

Bu örnek öğreticide, Visual Studio 'da kullanılan C# bir .NET Core konsol uygulaması aracılığıyla bir GitHub sorununun alan etiketini sınıflandırdığı ve tahmin eden bir modeli eğiten bir GitHub sorunu Sınıflandırıcısı oluşturmak için ml.NET kullanımı gösterilmektedir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Verilerinizi hazırlayın
> * Verileri dönüştürme
> * Modeli eğitme
> * Modeli değerlendirme
> * Eğitilen modelle birlikte tahmin edin
> * Yüklü bir modelle dağıtım ve tahmin etme

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.

## <a name="prerequisites"></a>Prerequisites

* [Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

* [GitHub sorunları sekmeyle ayrılmış dosya (issues_train. TSV)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [GitHub, test sekmeyle ayrılmış dosyası (issues_test. TSV) ile karşılaşır](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

### <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 2017 ' i açın. Menü çubuğundan **dosya** > **Yeni** > **Proje** ' yi seçin. **Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin. Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna "Githubıssueclassıflıve" yazın ve **Tamam** düğmesini seçin.

2. Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun:

    **Çözüm Gezgini**, projenize sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin. "Data" yazın ve ENTER tuşuna basın.

3. Modelinize kaydetmek için projenizde *modeller* adlı bir dizin oluşturun:

    **Çözüm Gezgini**, projenize sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin. "Modeller" yazın ve ENTER tuşuna basın.

4. **Microsoft.ml NuGet paketini**yükler:

    Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden **v 1.0.0** paketini seçin ve sonra da **Install** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.

### <a name="prepare-your-data"></a>Verilerinizi hazırlayın

1. [İssues_train. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test. tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri kümelerini indirin ve daha önce oluşturulan *veri* klasörüne kaydedin. Makine öğrenimi modelini ve ikincisini gösteren ilk veri kümesi, modelinizin ne kadar doğru olduğunu değerlendirmek için kullanılabilir.

2. Çözüm Gezgini, \*. tsv dosyalarının her birine sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

*Program.cs* dosyasının en üstüne aşağıdaki ek `using` deyimlerini ekleyin:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Son indirilen dosyaların yollarını ve `MLContext`, `DataView` ve `PredictionEngine` için genel değişkenleri tutmak üzere üç genel alan oluşturun:

* `_trainDataPath`, modeli eğitmek için kullanılan veri kümesinin yoludur.
* `_testDataPath`, modeli değerlendirmek için kullanılan veri kümesinin yoludur.
* `_modelPath`, eğitilen modelin kaydedildiği yolu içerir.
* `_mlContext`, işleme bağlamı sağlayan <xref:Microsoft.ML.MLContext>.
* eğitim veri kümesini işlemek için kullanılan <xref:Microsoft.ML.IDataView> `_trainingDataView`.
* `_predEngine`, tek tahminlerde kullanılan <xref:Microsoft.ML.PredictionEngine%602>.

Aşağıdaki kodu, bu yolları ve diğer değişkenleri belirtmek için `Main` yönteminin hemen üstüne ekleyin:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturun. Projenize yeni bir sınıf ekleyin:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.

1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *GitHubIssueData.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *GitHubIssueData.cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` ifadesini *GitHubIssueData.cs*öğesinin en üstüne ekleyin:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Mevcut sınıf tanımını kaldırın ve *GitHubIssueData.cs* dosyasına `GitHubIssue` ve `IssuePrediction` iki sınıfa sahip aşağıdaki kodu ekleyin:

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

@No__t_0, tahmin etmek istediğiniz sütundur. Tanımlanan `Features`, modele bir etiketi tahmin etmek için verdiğiniz girişlerdir.

Veri kümesindeki kaynak sütunlarının dizinlerini belirtmek için [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) kullanın.

`GitHubIssue`, giriş veri kümesi sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:

* `ID` ilk sütun (GitHub sorun KIMLIĞI)
* ikinci sütun `Area` (eğitim tahmini)
* üçüncü sütun `Title` (GitHub sorun başlığı), `Area` tahmin etmek için kullanılan ilk `feature`.
* dördüncü sütun `Description`, `Area` tahmin etmek için kullanılan ikinci `feature`

`IssuePrediction`, model eğitilen bir tahmin için kullanılan sınıftır. Tek bir `string` (`Area`) ve bir `PredictedLabel` `ColumnName` özniteliği vardır.  @No__t_0, tahmin ve değerlendirme sırasında kullanılır. Değerlendirme için eğitim verileri olan bir giriş, tahmin edilen değerler ve model kullanılır.

Tüm ML.NET işlemleri [Mlcontext](xref:Microsoft.ML.MLContext) sınıfında başlar. @No__t_0 başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur. Benzer, kavramsal olarak, `Entity Framework` `DBContext`.

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

Birden çok harekette tekrarlanabilir/belirleyici sonuçlar için rastgele çekirdek (`seed: 0`) ile `_mlContext` genel değişkenini yeni bir `MLContext` örneğiyle başlatın.  @No__t_0 satırını `Main` yönteminde aşağıdaki kodla değiştirin:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Verileri yükleme

ML.NET, sayısal veya metin tablolu verileri tanımlamaya yönelik esnek ve verimli bir yöntem olarak [ıdataview sınıfını](xref:Microsoft.ML.IDataView) kullanır. `IDataView` metin dosyalarını veya gerçek zamanlı olarak yükleyebilirsiniz (örneğin, SQL veritabanı veya günlük dosyaları).

@No__t_0 genel değişkenini, işlem hattı için kullanmak üzere başlatmak ve yüklemek için, `mlContext` başlatmadan sonra aşağıdaki kodu ekleyin:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar. Veri yolu değişkenlerini alır ve `IDataView` döndürür.

@No__t_0 yöntemine sonraki kod satırı olarak aşağıdakileri ekleyin:

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

@No__t_0 yöntemi aşağıdaki görevleri yürütür:

* Verileri ayıklar ve dönüştürür.
* İşlem ardışık düzenini döndürür.

Aşağıdaki kodu kullanarak, `Main` yönteminden hemen sonra `ProcessData` yöntemini oluşturun:

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>Özellikleri Ayıkla ve verileri Dönüştür

@No__t_0 için GitHub etiketini tahmin etmek istediğiniz için [Mapvaluetokey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanarak `Area` sütununu bir sayısal anahtar türü `Label` sütununa (sınıflandırma algoritmaları tarafından kabul edilen bir biçim) dönüştürün ve yeni bir veri kümesi sütunu olarak ekleyin :

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

Sonra, metin (`Title` ve `Description`) sütunlarını her bir `TitleFeaturized` ve `DescriptionFeaturized` için sayısal bir vektöre dönüştüren `mlContext.Transforms.Text.FeaturizeText` çağırın. Aşağıdaki kodla, her iki sütun için de işlem hattına bir şekilde ekleyin:

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

Veri hazırlığında son adım, [Birleştir ()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) yöntemini kullanarak tüm özellik sütunlarını **Özellikler** sütunuyla birleştirir. Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler. Aşağıdaki kodla bu dönüşümü işlem hattına ekleyin:

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 Daha sonra, verileri birden çok kez yinelemek için bir <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> ekleyin. bu nedenle, aşağıdaki kodda olduğu gibi, önbelleği kullanmak daha iyi bir performans alabilir:

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> Eğitim süresini azaltmak için küçük/orta veri kümeleri için AppendCacheCheckpoint kullanın. Bunu kullanmayın (kaldırın. Çok büyük veri kümelerini işlerken AppendCacheCheckpoint ()).

@No__t_0 yönteminin sonundaki işlem hattını döndürün.

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

Bu adım ön işleme/korleştirme gerçekleştirir. ML.NET ' de kullanılabilen ek bileşenleri kullanmak modelinize daha iyi sonuçlar verebilir.

## <a name="build-and-train-the-model"></a>Model oluşturma ve eğitme

Aşağıdaki çağrıyı, `Main` yönteminde sonraki kod satırı olarak `BuildAndTrainModel`method ekleyin:

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

@No__t_0 yöntemi aşağıdaki görevleri yürütür:

* Eğitim algoritması sınıfını oluşturur.
* Modeli TRAIN.
* Eğitim verilerine göre alanı tahmin eder.
* Modeli döndürür.

Aşağıdaki kodu kullanarak, `Main` yönteminden hemen sonra `BuildAndTrainModel` yöntemini oluşturun:

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>Sınıflandırma görevi hakkında

Sınıflandırma, bir öğe veya veri satırının kategorisini, türünü veya sınıfını **tespit** etmek için verileri kullanan bir makine öğrenimi görevi ve genellikle aşağıdaki türlerden biridir:

* İkili: A veya B.
* Birden çok sınıf: tek bir model kullanılarak tahmin edilebilir birden fazla kategori.

Bu tür bir sorun için, tek bir Lass sınıflandırma öğrenme algoritması kullanın, çünkü sorun kategorisi tahmininizde yalnızca iki (ikili) yerine birden çok kategori (birden çok Lass) olabilir.

@No__t_0 ' deki ilk kod satırı olarak aşağıdakini ekleyerek, makine öğrenimi algoritmasını veri dönüştürme tanımlarına ekleyin:

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

[Sdcamaximumentropi](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) , birden çok Lass sınıflandırma eğitim algoritmadır. Bu, `pipeline` eklenir ve geçmiş verilerden öğrenme `Title` ve `Description` (`Features`) ve `Label` giriş parametrelerini kabul eder.

### <a name="train-the-model"></a>Modeli eğitme

Modeli `splitTrainSet` verilerine sığdırın ve `BuildAndTrainModel()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen modeli döndürün:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

@No__t_0method, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi ister.

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneği üzerinde bir tahmin gerçekleştirmenizi ve daha sonra bir tahmin gerçekleştirmenizi sağlayan KULLANıŞLı bir API 'dir. @No__t_0 yönteminin sonraki satırı olarak bunu ekleyin:

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>Eğitilen modelle birlikte tahmin edin

Bir `GitHubIssue` örneği oluşturarak eğitilen modelin `Predict` yönteminde tahminini test etmek için bir GitHub sorunu ekleyin:

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevini kullanın, tek bir veri satırında tahmin yapar:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>Modeli kullanma: tahmin sonuçları

Sonuçları paylaşmak ve bunlara göre işlem yapmak için `GitHubIssue` ve karşılık gelen `Area` etiket tahminini görüntüleyin.  Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodunu kullanarak sonuçlar için bir görüntü oluşturun:

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Değerlendirme için kullanılmak üzere eğitilen modeli döndürün

@No__t_0 yönteminin sonundaki modeli döndürün.

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Modeli oluşturup eğitildiniz, artık kalite güvencesi ve doğrulama için farklı bir veri kümesiyle değerlendirmeniz gerekir. @No__t_0 yönteminde, `BuildAndTrainModel` oluşturulan model değerlendirilmek üzere geçirilir. Aşağıdaki kodda olduğu gibi, `BuildAndTrainModel` hemen sonra `Evaluate` yöntemini oluşturun:

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

@No__t_0 yöntemi aşağıdaki görevleri yürütür:

* Test veri kümesini yükler.
* Birden çok Lass değerlendirici oluşturur.
* Modeli değerlendirir ve ölçüm oluşturur.
* Ölçümleri görüntüler.

Aşağıdaki kodu kullanarak, `BuildAndTrainModel` yöntemi çağrısının altına sağ `Main` yönteminden yeni yönteme bir çağrı ekleyin:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

Daha önce eğitim veri kümesiyle yaptığınız gibi, `Evaluate` yöntemine aşağıdaki kodu ekleyerek test veri kümesini yükleyin:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

[Değerlendir ()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) yöntemi, belirtilen veri kümesini kullanarak model için kalite ölçümlerini hesaplar. Birden çok Lass Classification değerlendiricileri tarafından hesaplanan genel ölçümleri içeren bir <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> nesnesi döndürür.
Modelin kalitesini belirleme ölçümlerini göstermek için önce bunları almanız gerekir.
Özellikleri girmek ve tahmin getirmeleri için Machine Learning `_trainedModel` genel değişkeninin (bir [ıranseski](xref:Microsoft.ML.ITransformer)) [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yönteminin kullanımına dikkat edin. Aşağıdaki kodu `Evaluate` yöntemine sonraki satır olarak ekleyin:

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

Aşağıdaki ölçümler birden çok Lass sınıflandırması için değerlendirilir:

* Mikro doğruluk-her örnek sınıf çifti, doğruluk ölçüsüne eşit olarak katkıda bulunur.  Mikro doğruluk ' ın olabildiğince 1 ' e yakın olmasını istiyorsunuz.

* Makro doğruluğu-her sınıf, doğruluk ölçüsüne eşit olarak katkıda bulunur. Minınlık sınıflarına daha büyük sınıflar olarak eşit ağırlık verilir. Makro doğruluğunu mümkün olduğunca 1 ' e yakın olacak şekilde istiyorsunuz.

* Günlük-kayıp- [günlük kaybını](../resources/glossary.md#log-loss)görüntüleyin. Günlük kaybını mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.

* Günlük kaybı azaltma-[-inf, 100] aralığından, 100 ' nin kusursuz tahminlerden ve 0 ' ın, ortalama tahmine dayalı olduğunu gösterir. Günlük kaybını azaltmanın mümkün olduğunca sıfıra yakın olmasını istiyorsunuz.

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama ölçümlerini görüntüleme

Ölçümleri göstermek, sonuçları paylaşmak ve sonra bunlar üzerinde işlem yapmak için aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>Modeli bir dosyaya kaydet

Modelinize her memnun olduktan sonra, daha sonra veya başka bir uygulamada tahmine dayalı hale getirmek için dosyayı bir dosyaya kaydedin. @No__t_0 yöntemine aşağıdaki kodu ekleyin.

[!code-csharp[SnippetCallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetCallSaveModel)]

@No__t_1 yönteminizin altında `SaveModelAsFile` yöntemi oluşturun.

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

Aşağıdaki kodu `SaveModelAsFile` yöntemine ekleyin. Bu kod, eğitilen modeli seri hale getirmek ve bir ZIP dosyası olarak depolamak için [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) yöntemini kullanır.

[!code-csharp[SnippetSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>Bir modelle dağıtım ve tahmin etme

Aşağıdaki kodu kullanarak, `Evaluate` yöntemi çağrısının altına sağ `Main` yönteminden yeni yönteme bir çağrı ekleyin:

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

Aşağıdaki kodu kullanarak, `Evaluate` yönteminden hemen sonra (ve `SaveModelAsFile` yönteminden hemen önce) `PredictIssue` yöntemini oluşturun:

```csharp
private static void PredictIssue()
{

}
```

@No__t_0 yöntemi aşağıdaki görevleri yürütür:

* Kaydedilen modeli yükler
* Test verileri için tek bir sorun oluşturur.
* Test verilerine göre alanı tahmin eder.
* Raporlama için test verilerini ve tahminleri birleştirir.
* Tahmin edilen sonuçları görüntüler.

@No__t_0 yöntemine aşağıdaki kodu ekleyerek kayıtlı modeli uygulamanıza yükleyin:

[!code-csharp[SnippetLoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetLoadModel)]

Bir `GitHubIssue` örneği oluşturarak eğitilen modelin `Predict` yönteminde tahminini test etmek için bir GitHub sorunu ekleyin:

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

Daha önce yaptığınız gibi, aşağıdaki kodla bir `PredictionEngine` örneği oluşturun:

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın. [ASP.NET Core Web API 'sinde `PredictionEnginePool` ' i nasıl kullanacağınızı](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application) öğrenmek için bu kılavuza bakın

> [!NOTE]
> `PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.

Aşağıdaki kodu tahmin için `PredictIssue` yöntemine ekleyerek GitHub etiketini tahmin etmek için `PredictionEngine` kullanın:

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>Yüklü modeli tahmin için kullanma

Sorunu kategorilere ayırarak ve buna uygun şekilde hareket edebilmek için `Area` görüntüleyin. Aşağıdaki <xref:System.Console.WriteLine?displayProperty=nameWithType> kodunu kullanarak sonuçlar için bir görüntü oluşturun:

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>Sonuçlar

Sonuçlarınız aşağıdakine benzer olmalıdır. İşlem hattı sırasında iletileri görüntüler. Uyarıları görebilir veya iletileri işleme alabilirsiniz. Bu iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.

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

Mühendisi! Artık bir GitHub sorunu için bir alan etiketini sınıflandırmak ve tahmin etmek üzere bir makine öğrenimi modeli oluşturdunuz. Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, nasıl yapılacağını öğrendiniz:
> [!div class="checklist"]
>
> * Verilerinizi hazırlayın
> * Verileri dönüştürme
> * Modeli eğitme
> * Modeli değerlendirme
> * Eğitilen modelle birlikte tahmin edin
> * Yüklü bir modelle dağıtım ve tahmin etme

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin
> [!div class="nextstepaction"]
> [Taxı tarifeli havayolu Predictor](taxi-fare.md)
