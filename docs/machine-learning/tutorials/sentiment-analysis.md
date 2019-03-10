---
title: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu
description: ML.NET ikili sınıflandırma senaryoda yaklaşım tahmin uygun eylemde için nasıl kullanılacağını anlamak için nasıl kullanılacağını keşfedin.
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: d7e46b489506f4adad843ba5315afde4c7689b4e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723328"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Öğretici: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu

Bu örnek öğretici ML.NET kullanarak bir .NET Core konsol uygulaması kullanarak aracılığıyla pozitif veya negatif yaklaşım tahmin etmek için bir yaklaşım sınıflandırıcı oluşturma gösterilmektedir C# Visual Studio 2017'de. Machine learning dünyasında, bu tür bir tahmin ikili sınıflandırma bilinir.

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu öğretici ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.11**. Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenimi algoritması seçin
> * Verilerinizi hazırlama
> * Verileri dönüştürme
> * Modeli eğitme
> * Modeli değerlendirme
> * Eğitilen modeli tahmin edin
> * Dağıtma ve yüklenen modeliyle tahmin edin

## <a name="sentiment-analysis-sample-overview"></a>Yaklaşım analizi örneğine genel bakış

Örnek ML.NET sınıflandırır ve yaklaşım artı veya eksi olarak tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır. California Üniversitesi, Irvine (hangi train veri kümesi ve bir test veri kümesini halinde bölme UCI), Yelp yaklaşım dataset arasındadır. Örnek kalite analizi için test veri modeliyle değerlendirir. 

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

* [UCI yaklaşım cümleler etiketli veri kümesini zip dosyası](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="machine-learning-workflow"></a>Machine learning iş akışı

Bu öğreticide, bir makine öğrenimi düzenli bir şekilde taşımak işlem sağlayan bir iş akışı izler.

İş akışı aşamalar aşağıdaki gibidir:

1. **Sorunu anlama**
2. **Verilerinizi hazırlama**
   * **Verileri yükleme**
   * **Özellikler (verilerinizi dönüştürmek) ayıklayın**
3. **Derleme ve eğitme** 
   * **Modeli eğitme**
   * **Modeli değerlendirme**
4. **Model dağıtma**
   * **Tahmin modelini kullanın**

### <a name="understand-the-problem"></a>Sorunu anlama

Öncelikle, oluşturmak ve modeli eğitmek destekleyebileceği bölümleri aşağı kesmek için sorunu anlamak gerekir. Sorun bozucu, tahmin edin ve sonuçları değerlendirin olanak tanır.

Sorun Bu öğretici için uygun eylemi gerçekleştirin gelen Web sitesi açıklama yaklaşım öğrenmektir.

Problemi yaklaşım metin ve duyarlılık değeri ile modeli eğitmek için istediğiniz verileri için ve tahmin edilen duyarlılık değeri değerlendirmek ve işletimsel olarak kullanmak dökümünü alabilirsiniz.

Ardından gerek **belirlemek** yaklaşımı, Görev Seçimi öğrenme makineyle yardımcı olur.

## <a name="select-the-appropriate-machine-learning-algorithm"></a>Uygun makine öğrenimi algoritması seçin

Bu sorun aşağıdaki gerçekleri bildirin:

Eğitim verileri: Web sitesi açıklamaları pozitif olabilir (1) veya negatif (0) (**yaklaşım**).

Tahmin **yaklaşım** açıklamasının bir yeni Web sitesi, pozitif veya negatif gibi aşağıdaki örnekte:

* Burada bekleme Hastanenin seviyorum. Bunlar Kaya.
* Burası, en kötü A'dan sahiptir.

Sınıflandırma makine öğrenimi algoritmasının bu senaryo için idealdir.

### <a name="about-the-classification-algorithm"></a>Sınıflandırma algoritmasıdır hakkında

Sınıflandırma olan verileri kullanan bir machine learning algoritmasını **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı. Örneğin, sınıflandırma için kullanabilirsiniz:

* Artı veya eksi olarak duyguları tanımlayın.
* E-posta klasörünüzü veya iyi istenmeyen sınıflandırın.
* Bir hastanın Laboratuvar örnek cancerous olup olmadığını belirler.
* Müşteriler, kendi eğilimini yanıt satış kampanyaya göre kategorilere ayırın.

Sınıflandırma algoritmaları sık aşağıdaki türlerden biri şunlardır:

* İkili: ya da A veya b
* Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.

Web sitesi açıklamaları pozitif veya negatif olarak sınıflandırılması gerektiğinden, ikili sınıflandırma algoritmasını kullanın. 

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.

2. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:

    İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**. "Veri" yazın ve Enter tuşuna basın.

3. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

### <a name="prepare-your-data"></a>Verilerinizi hazırlama

1. İndirme [UCI yaklaşım cümleler etiketli veri kümesini zip dosyası (alıntıları aşağıdaki nota bakın)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)ve sıkıştırmasını açın.

2. Kopyalama `yelp_labelled.txt` doyasını *veri* oluşturduğunuz dizin.

> [!NOTE]
> Bu öğreticide veri kümeleri Kotzias 'kaynak grubundan ayrıntılı özelliklerini kullanarak her bir etiketi için' olan et. Al. 2015 ve barındırılan KDD UCI Machine Learning deposu - Dua, d ve Karra Taniskidou, e (2017). UCI Makine deposu [http://archive.ics.uci.edu/ml]. Irvine, CA: California Üniversitesi, okul bilgi ve bilgisayar Bilimine.

3. Çözüm Gezgini'nde sağ `yelp_labeled.txt` seçin ve dosya **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

### <a name="create-classes-and-define-paths"></a>Yollarını tanımlamak ve sınıfları oluşturma

Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

En son indirilen veri kümesi dosyası yolu ve kayıtlı modeli dosya yolu tutmak için iki genel alanlar oluşturmak ihtiyacınız vardır:

* `_dataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.
* `_modelPath` eğitilen modelin kaydedildiği yolu vardır.

Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollarını belirtmek için:

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir. Yeni bir sınıf, projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*. Ardından, **Ekle** düğmesi.

    *SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

Giriş veri kümesi sınıfı `SentimentData`, sahip bir `string` Açıklama (`SentimentText`) ve bir `bool` (`Sentiment`) pozitif veya negatif yaklaşım için bir değer olan. Her iki alanınız <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> öznitelikleri kendisine bağlı. Bu öznitelik veri dosyasındaki her bir alanın sırasını anlatır.  Ayrıca, `Sentiment` özelliğine sahip bir <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> olarak belirlemek için `Label` alan. `SentimentPrediction` eğitilen modelin sonra sınıf tahmin için kullanılır. Tek bir Boole değeri vardır (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği. `Label` Oluşturabilir ve ayrıca bölünmüş test veri kümesini kullanıma ile model değerlendirmek için kullanılan model ya da onun eğitmek için kullanılır. `PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.

ML.NET modeliyle oluştururken oluşturarak başlayın bir <xref:Microsoft.ML.MLContext>. `MLContext` kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework. Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilecek ML işiniz için bir bağlam sağlar.

### <a name="initialize-variables-in-main"></a>Ana değişkenleri başlatma

Adlı bir değişken oluşturma `mlContext` ve yeni bir örneğini ile başlatma `MLContext`.  Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

Sonraki kod satırı olarak ekleyin `Main` yöntemi:

[!code-csharp[CallLoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

`LoadData` Yöntemi aşağıdaki görevleri yürütür:

* Verileri yükler.
* Yüklenen veri kümesi train böler ve test edin, veri kümeleri.
* Bölme döndürür eğitme ve test etme, veri kümeleri.

Oluşturma `LoadData` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static (IDataView trainSet, IDataView testSet) LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a>Verileri yükleme

Önceden oluşturduğunuz beri `SentimentData` veri modeli türüyle eşleşen veri kümesi şeması, başlatma, eşleme ve veri kümesi bir satır kod kullanarak yüklerken Birleştir `MLContext.Data.ReadFromTextFile` için sarmalayıcı <xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29>. Döndürür bir <xref:Microsoft.Data.DataView.IDataView>. 

 Giriş ve çıkış olarak `Transforms`, `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.

ML.NET veriler SQL görünümüne benzer. Bu, gevşek değerlendirilen, şema ve heterojen olur. Nesne, işlem hattını ilk kısmı ve verileri yükler. Bu öğreticide, açıklama ve karşılık gelen toxic veya olmayan toxic yaklaşım bir veri kümesine yükler. Bu model oluşturmayı ve bunu eğitmek için kullanılır.

 İlk satırı olarak aşağıdaki kodu ekleyin `LoadData` yöntemi:

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a>Eğitim ve test modeli için veri kümesi bölünemiyor

Ardından, hem bir eğitim veri kümesi modeli eğitmek için hem de model değerlendirmek için test veri kümesini gerekir. Kullanım `MLContext.BinaryClassification.TrainTestSplit` sarmalayan <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> train yüklenen veri kümesi bölün ve veri kümeleri sınayabilir ve bunları içine bir <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>. Test kümesi için kısa bir veri belirtebilirsiniz `testFraction`parametresi. Varsayılan % 10'dur ancak, % 20 Bu durumda daha fazla veri Değerlendirme amacıyla kullanmak için kullanın.  

Yüklenen verilere gerekli veri kümelerine ayırmak için bir sonraki satırda olarak aşağıdaki kodu ekleyin `LoadData` yöntemi:

[!code-csharp[SplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

Dönüş `splitDataView` sonunda `LoadData` yöntemi:

[!code-csharp[ReturnSplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Derleme ve modeli eğitme

Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main` yöntemi:

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` Yöntemi aşağıdaki görevleri yürütür:

* Ayıklar ve verileri dönüştürür.
* Modeli eğitir.
* Test verilerine dayalı yaklaşım tahmin eder.
* Model döndürür.

Oluşturma `Train` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

İki parametre Train yönteme geçirilen dikkat edin; bir `MLContext` bağlamının (`mlContext`) ve bir `IDataView`eğitim veri kümesi için (`splitTrainSet`). 

## <a name="extract-and-transform-the-data"></a>Verileri dönüştürme ve ayıklama

Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir. Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir. Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.

ML. NET dönüştürme işlem hatları, verilerinizi, eğitim veya test etmeden önce uygulanan dönüştürmeler özel bir dizi oluşturun. Veri Dönüşümleri birincil amacı olan [özellik kazandırma sayesinde](../resources/glossary.md#feature-engineering). Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) metinsel verilerimizi ML algoritmalarınızı tanıyacak bir biçime dönüştürmek için sonraki adım, bu nedenle veri. Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).

Ardından, arama `mlContext.Transforms.Text.FeaturizeText` hangi featurizes metin sütununu (`SentimentText`) adı verilen sayısal bir vektör sütununa `Features` makine öğrenimi algoritması tarafından kullanılan. Bu döndüren bir sarmalayıcı çağrısı, bir <xref:Microsoft.ML.Data.EstimatorChain%601> bir işlem hattı etkin olacak. Bu ad `pipeline` eğitmen için ardından ekleyeceği şekilde `EstimatorChain`. Bu, sonraki kod satırı ekleyin:

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> ML.NET sürüm 0.10 dönüştürme parametrelerinin sırasını değiştirildi. Bu, kullanıma alma hatası kadar uygulamayı çalıştırın ve model derleme. Dönüşümlerin parametre adları, önceki kod parçacığında gösterildiği gibi kullanın.

Bu ön işleme/özellik kazandırma sayesinde adımdır. ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Eğitmen eklemek için çağrı `mlContext.BinaryClassification.Trainers.FastTree` döndüren sarmalayıcı yöntemini bir <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> nesne. Bu işlem hattında kullanacağınız karar ağacı learner budur. `FastTreeBinaryClassificationTrainer` Eklenir `pipeline` ve özellikleri tespit `SentimentText` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.

Aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>Modeli eğitme

Modeli eğitme <xref:Microsoft.ML.Data.TransformerChain%601>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi. Tahmin tanımlandıktan sonra kullanarak modelinize eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> zaten yüklenmiş eğitim verilerini sağlayarak yöntemi. Bu tahminler elde etmek için kullanılacak bir modelini döndürür. `pipeline.Fit()` işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi. Denemeyi kadar yürütülmez `.Fit()` yöntemi çalışır.

Aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Kaydet ve değerlendirme için kullanılacak modeli eğitilir dön

Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain%601> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine. Model sonunda dönüş `BuildAndTrainModel` yöntemi.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir. İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `BuildAndTrainModel` değerlendirilecek geçirilir. Oluşturma `Evaluate` yöntemi hemen sonrasına `BuildAndTrainModel`, aşağıdaki kod gibi:

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

`Evaluate` Yöntemi aşağıdaki görevleri yürütür:

* Test veri kümesini yükler.
* Binaryclassification değerlendirici oluşturur.
* Model değerlendirir ve ölçüm oluşturur.
* Ölçümleri görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

Ardından, makine öğrenimi kullanacağınız `model` parametre (dönüştürücü) ve `splitTestSet` özellikleri giriş ve tahmin döndürmek için parametre. Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

`mlContext.BinaryClassification.Evaluate` Yöntemi hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma. Döndürür bir <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> ikili sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne. Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir. Sonraki satırda olarak aşağıdaki kodu ekleyin `Evaluate` yöntemi:

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama için ölçümleri görüntüleme

Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

Modelinizi dönmeden önce bir .zip dosyası olarak kaydetmek için çağırmak için aşağıdaki kodu ekleyin. `SaveModelAsFile` yöntemi olarak bir sonraki satırda `Evaluate`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a>Modeli a.zip dosyası olarak kaydedin.

Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:

* Model bir .zip dosyası olarak kaydeder.

Ardından, yeniden kullanılabilir ve diğer uygulamalarda kullanılan model kaydetmek için bir yöntem oluşturun. `ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>. Bu zip dosyası olarak kaydetmek için oluşturacağınız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi. Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>Dağıtma ve yüklenen modeliyle tahmin edin

Bir konsol iletisi ile yazarak dosyasının nerede yazılmıştır görüntüleyebilir `_modelPath`, aşağıdaki kodu kullanarak:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>Kaydedilen modeli ile test veri sonucu tahmin edin

Oluşturma `UseModelWithSingleItem` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

`UseModelWithSingleItem` Yöntemi aşağıdaki görevleri yürütür:

* Test verilerini tek bir yorum oluşturur.
* Test verilerine dayalı yaklaşım tahmin eder.
* Bir araya getirir, verileri ve raporlama için Öngörüler test edin.
* Tahmin edilen sonuçları görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallUseModelWithSingleItem](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

Sırada `model` olduğu bir `transformer` gereksinimi, tek tek örnekleri tahminler elde etmek için çok yaygın bir üretim senaryosu, çok sayıda veri satırı üzerinde çalışır. <xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi. Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` ilk satırı olarak `Predict` yöntemi:

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
Eğitilen modelin tahmine test etmek için bir açıklama ekleyin `Predict` bir örneğini oluşturarak yöntemi `SentimentData`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 Bu açıklama verilerini tek bir örneğini pozitif veya negatif duyarlılığını tahmin etmek için kullanabilirsiniz. Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri. Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın. İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş. Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a>Model kullanmak: tahmin

Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için. Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır. Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>Dağıtma ve yüklenen modeliyle tahmin edin

Oluşturma `UseLoadedModelWithBatchItems` yöntemi hemen önce `SaveModelAsFile` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

`UseLoadedModelWithBatchItems` Yöntemi aşağıdaki görevleri yürütür:

* Toplu test verilerini oluşturur.
* Test verilerine dayalı yaklaşım tahmin eder.
* Bir araya getirir, verileri ve raporlama için Öngörüler test edin.
* Tahmin edilen sonuçları görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `UseModelWithSingleItem` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `UseLoadedModelWithBatchItems` yöntemi:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

Model yüklenemiyor

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

Bir modeliniz olduğuna göre yorum kullanarak veri Toxic veya olmayan Toxic yaklaşım tahmin etmek için kullanabileceğiniz <xref:Microsoft.ML.ITransformer.Transform%2A> yöntemi. Bir öngörü almak için kullanın `Predict` yeni veriler. Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın. İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş. Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir. Aşağıdaki kodu ekleyin `UseLoadedModelWithBatchItems` yöntemi tahminler elde etmek için:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a>Tahmin için yüklenen modeli kullanın

Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için. Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır. Aşağıdakileri kullanarak sonuçları için bir başlık oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

Tahmin edilen sonuçlarını görüntülemeden önce yaklaşımını ve özgün açıklamayı, tahmin edilen yaklaşım ile birlikte görmek için tahmini birleştirin. Aşağıdaki kod <xref:System.Linq.Enumerable.Zip%2A> gerçekleşen, yapmanız gereken yöntemini bu nedenle bu kodunu ekleyin sonraki:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

Birleştirilmiş göre `SentimentText` ve `Sentiment` bir sınıf kullanarak sonuçları görüntüleyebilirsiniz <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemi:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

C# 7.0 C# 7.1 ve projenin varsayılan dil sürümü yeni bir özellik olan demet öğesi adları olan olayla olduğundan, C# 7.1 veya üzeri dil sürümünü değiştirmek gerekir.
Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**. Seçin **derleme** sekmenize **Gelişmiş** düğmesi. Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm). **Tamam** düğmesini seçin.

## <a name="results"></a>Sonuçlar

Sonuçlar aşağıdakine benzer olmalıdır. İşlem hattı işlediği gibi iletileri görüntüler. Uyarıları ve iletileri işlemeyi görebilirsiniz. Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

Tebrikler! Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz. 

Başarılı modeller oluşturma yinelemeli bir işlemdir. Bu model düşük ilk kalite hızlı modeli eğitimi sağlamak için öğretici kullanan küçük veri kümeleri sahiptir. Model kalitesi memnun değilseniz daha büyük bir eğitim veri kümeleri sağlama veya farklı hyper-parametreleriyle her bir algoritmanın için farklı eğitim algoritmalarıyla seçerek geliştirmek deneyebilirsiniz.

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenimi algoritması seçin
> * Verilerinizi hazırlama
> * Verileri dönüştürme
> * Modeli eğitme
> * Modeli değerlendirme
> * Eğitilen modeli tahmin edin
> * Dağıtma ve yüklenen modeliyle tahmin edin

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Sorun sınıflandırması](github-issue-classification.md)
