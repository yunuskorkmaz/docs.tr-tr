---
title: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu
description: ML.NET ikili sınıflandırma senaryoda yaklaşım tahmin uygun eylemde için nasıl kullanılacağını anlamak için nasıl kullanılacağını keşfedin.
ms.date: 03/01/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 854330614713a6e05a47b3833634907027bda267
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368330"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>Öğretici: ML.NET kullanımda bir yaklaşım analizi ikili sınıflandırma senaryosu

Bu örnek öğretici, C# kullanarak Visual Studio 2017'de .NET Core konsol uygulaması aracılığıyla bir yaklaşım sınıflandırıcı oluşturma ML.NET kullanılması gösterilmektedir.

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu öğretici ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.10**. Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning github deposu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)

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

Örnek ML.NET sınıflandırır ve yaklaşım artı veya eksi olarak tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır. Ayrıca, kalite analizi için ikinci bir veri kümesi modeliyle değerlendirir. Yaklaşım veri kümeleri WikiDetox projeden ' dir.

Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

* [Wikipedia detox satır veri sekmeyle ayrılmış dosya (wikiPedia-detox-250-satırı-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).
* [Wikipedia detox satır test sekmeyle ayrılmış dosya (wikipedia-detox-250-satırı-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).

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

Eğitim verileri: Web sitesi açıklamaları toxic olabilir (1) olmadığını (0) toxic (**yaklaşım**).
Tahmin **yaklaşım** açıklamasının bir yeni Web sitesi, toxic veya değil toxic, gibi aşağıdaki örnekte:

* Lütfen anlamsız Wikipedia için makalelerinizde.
* Kendisi için en iyi yöntemdir ve makale, yazması gerekir.

Sınıflandırma makine öğrenimi algoritmasının bu senaryo için idealdir.

### <a name="about-the-classification-task"></a>Sınıflandırma görevi hakkında

Sınıflandırma olan verileri kullanan bir machine learning algoritmasını **belirlemek** kategori, tür veya bir öğe veya veri satırı sınıfı. Örneğin, sınıflandırma için kullanabilirsiniz:

* Artı veya eksi olarak duyguları tanımlayın.
* E-posta klasörünüzü veya iyi istenmeyen sınıflandırın.
* Bir hastanın Laboratuvar örnek cancerous olup olmadığını belirler.
* Müşteriler, kendi eğilimini yanıt satış kampanyaya göre kategorilere ayırın.

Sınıflandırma algoritmaları sık aşağıdaki türlerden biri şunlardır:

* İkili: ya da A veya b
* Veya çoklu sınıflar: tek bir model kullanarak tahmin edilebilmesi birden çok kategori.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.

2. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:

    İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**. "Veri" yazın ve Enter tuşuna basın.

3. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

### <a name="prepare-your-data"></a>Verilerinizi hazırlama

1. İndirme [Wikipedia detox-250-satırı-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) ve [wikipedia-detox-250-satırı-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör. İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.

2. Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

### <a name="create-classes-and-define-paths"></a>Yollarını tanımlamak ve sınıfları oluşturma

Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

Kısa bir süre önce indirilen dosyaları ve bir genel değişken için yollar tutmak için üç genel alanlar oluşturmak için ihtiyacınız `TextLoader`:

* `_trainDataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.
* `_testDataPath` Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.
* `_modelPath` eğitilen modelin kaydedildiği yolu vardır.
* `_textLoader` olan <xref:Microsoft.ML.Data.TextLoader> yüklemek ve veri kümeleri dönüştürmek için kullanılır.

Satır sağ aşağıdaki kodu ekleyin `Main` bu yollarını belirtmek için yöntemi ve `_textLoader` değişkeni:

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir. Yeni bir sınıf, projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*. Ardından, **Ekle** düğmesi.

    *SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *SentimentData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `SentimentData` ve `SentimentPrediction`, *SentimentData.cs* dosyası:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` Giriş veri kümesi sınıfı ve bir `float` (`Sentiment`) pozitif veya negatif yaklaşım için bir değer ve bir dize yorumu için olan (`SentimentText`). Her iki alanınız `Column` öznitelikleri kendisine bağlı. Bu öznitelik her bir alanın veri dosyası ve olduğu siparişi açıklayan `Label` alan. `SentimentPrediction` eğitilen modelin sonra sınıf tahmin için kullanılır. Tek bir Boole değeri vardır (`Sentiment`) ve bir `PredictedLabel` `ColumnName` özniteliği. `Label` Oluşturup modeli ya da onun da model değerlendirmek için ikinci bir veri kümesi ile kullanılan eğitmek için kullanılır. `PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.

ML.NET modeliyle oluştururken oluşturarak başlayın bir `MLContext`. Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework. Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilecek ML işiniz için bir bağlam sağlar.

### <a name="initialize-variables-in-main"></a>Ana değişkenleri başlatma

Adlı bir değişken oluşturma `mlContext` ve yeni bir örneğini ile başlatma `MLContext`.  Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

Sonra Kurulum başlatma veri yükleme için `_textLoader` yeniden kullanmak için genel değişkeni.  Oluşturduğunuzda, bir `TextLoader` kullanarak `MLContext.Data.CreateTextLoader`, gerekli bağlamı geçirdiğiniz ve <xref:Microsoft.ML.Data.TextLoader.Arguments> özelleştirme sağlayan sınıf.

 Bir dizi geçirerek veri şemasını belirtin <xref:Microsoft.ML.Data.TextLoader.Column> tüm sütun adlarını ve türlerini içeren yükleyicisi nesneleri. Oluşturduğunuz zaman veri şemasını önceden tanımlanmış bizim `SentimentData` sınıfı. İlk sütun (etiketi) bizim şema için olan bir <xref:System.Boolean> (tahmin) ve ikinci sütun (SentimentText) türü metin/dizesi yaklaşımını tahminde için kullanılan bir özelliktir.
`TextLoader` Sınıf tam olarak başlatılmış döndürür <xref:Microsoft.ML.Data.TextLoader>  

Başlatmak için `_textLoader` gerekli veri kümeleri için yeniden kullanmak için genel değişkeni sonra aşağıdaki kodu ekleyin `mlContext` başlatma:

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextLoader")]

Sonraki kod satırı olarak ekleyin `Main` yöntemi:

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

`Train` Yöntemi aşağıdaki görevleri yürütür:

* Verileri yükler.
* Ayıklar ve verileri dönüştürür.
* Modeli eğitir.
* Test verilerine dayalı yaklaşım tahmin eder.
* Model döndürür.

Oluşturma `Train` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

İki parametre Train yönteme geçirilen dikkat edin; bir `MLContext` bağlamının (`mlContext`) ve <xref:System.String> veri kümesi yolu için (`dataPath`). Eğitim ve test için bu yöntemi birden çok kez kullanın dağıtacağız.

## <a name="load-the-data"></a>Verileri yükleme

Kullanarak verileri yüklemek `_textLoader` genel değişkenin `dataPath` parametresi. Döndürür bir <xref:Microsoft.Data.DataView.IDataView>. Giriş ve çıkış olarak `Transforms`, `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.

ML.NET veriler SQL görünümüne benzer. Bu, gevşek değerlendirilen, şema ve heterojen olur. Nesne, işlem hattını ilk kısmı ve verileri yükler. Bu öğreticide, açıklama ve karşılık gelen toxic veya olmayan toxic yaklaşım bir veri kümesine yükler. Bu model oluşturmayı ve bunu eğitmek için kullanılır.

 İlk satırı olarak aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a>Verileri dönüştürme ve ayıklama

Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir. Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir. Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.

ML. NET dönüştürme işlem hatları, verilerinizi, eğitim veya test etmeden önce uygulanan dönüştürmeler özel bir dizi oluşturun. Veri Dönüşümleri birincil amacı olan [özellik kazandırma sayesinde](../resources/glossary.md#feature-engineering). Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) metinsel verilerimizi ML algoritmalarınızı tanıyacak bir biçime dönüştürmek için sonraki adım, bu nedenle veri. Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).

Ardından, arama `mlContext.Transforms.Text.FeaturizeText` hangi featurizes metin sütununu (`SentimentText`) adı verilen sayısal bir vektör sütununa `Features` makine öğrenimi algoritması tarafından kullanılan. Bu döndüren bir sarmalayıcı çağrısı, bir <xref:Microsoft.ML.Data.EstimatorChain%601> bir işlem hattı etkin olacak. Bu ad `pipeline` eğitmen için ardından ekleyeceği şekilde `EstimatorChain`. Bu, sonraki kod satırı ekleyin:

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

>[!WARNING]
> ML.NET sürüm 0.10 dönüştürme parametreleri sırası değişti. Bu, kullanıma alma hatası kadar uygulamayı çalıştırın ve model derleme. Dönüşümlerin parametre adları, önceki kod parçacığında gösterildiği gibi kullanın.

Bu ön işleme/özellik kazandırma sayesinde adımdır. ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Eğitmen eklemek için çağrı `mlContext.Transforms.Text.FeaturizeText` döndüren sarmalayıcı yöntemini bir <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> nesne. Bu işlem hattında kullanacağınız karar ağacı learner budur. `FastTreeBinaryClassificationTrainer` Eklenir `pipeline` ve özellikleri tespit `SentimentText` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.

Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>Modeli eğitme

Modeli eğitme <xref:Microsoft.ML.Data.TransformerChain%601>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi. Tahmin tanımlandıktan sonra kullanarak modelinize eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> zaten yüklenmiş eğitim verilerini sağlayarak. Bu tahminler elde etmek için kullanılacak bir modelini döndürür. `pipeline.Fit()` işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi. Denemeyi böyle kadar yürütülmez.

Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Kaydet ve değerlendirme için kullanılacak modeli eğitilir dön

Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain%601> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine. Model sonunda dönüş `Train` yöntemi.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Oluşturduğunuz ve eğitilen modele göre kalite güvencesi ve doğrulama için farklı bir veri kümesi değerlendirilecek gerekir. İçinde `Evaluate` yöntemi, oluşturduğunuz modeli `Train` değerlendirilecek geçirilir. Oluşturma `Evaluate` yöntemi hemen sonrasına `Train`, aşağıdaki kod gibi:

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate` Yöntemi aşağıdaki görevleri yürütür:

* Test veri kümesini yükler.
* İkili değerlendirici oluşturur.
* Model değerlendirir ve metrikleri oluşturma.
* Ölçümleri görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

Daha önce başlatılmış kullanarak test veri kümesini yük `_textLoader` genel değişkenin `_testDataPath` genel alan. Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir. Aşağıdaki kodu ekleyin `Evaluate` yöntemi:

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

Ardından, makine öğrenimi kullanacağınız `model` özellikleri giriş ve tahmin döndürmek için parametre (dönüştürücü). Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

`BinaryClassificationContext.Evaluate` Yöntemi hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma. Döndürür bir `BinaryClassificationEvaluator.CalibratedResult` nesne ikili sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içerir. Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir. Sonraki satırda olarak aşağıdaki kodu ekleyin `Evaluate` yöntemi:

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama için ölçümleri görüntüleme

Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

Modelinizi dönmeden önce bir .zip dosyası olarak kaydetmek için çağırmak için aşağıdaki kodu ekleyin. `SaveModelAsFile` yöntemi olarak bir sonraki satırda `Evaluate`:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

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

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]
Dağıtma ve tahmin da görüntü bir konsol iletisi ile yazarak dosyasının nerede yazılmıştır yüklenen modeliyle `_modelPath`, aşağıdaki kodu kullanarak:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>Kaydedilen modeli ile test veri sonucu tahmin edin

Oluşturma `Predict` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

`Predict` Yöntemi aşağıdaki görevleri yürütür:

* Test verilerini tek bir yorum oluşturur.
* Test verilerine dayalı yaklaşım tahmin eder.
* Bir araya getirir, verileri ve raporlama için Öngörüler test edin.
* Tahmin edilen sonuçları görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

Sırada `model` olduğu bir `transformer` gereksinimi, tek tek örnekleri tahminler elde etmek için çok yaygın bir üretim senaryosu, çok sayıda veri satırı üzerinde çalışır. <xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi. Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` ilk satırı olarak `Predict` yöntemi:

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionEngine")]
  
Eğitilen modelin tahmine test etmek için bir açıklama ekleyin `Predict` bir örneğini oluşturarak yöntemi `SentimentData`:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]

 Bu açıklama verilerini tek bir örneğini Toxic veya olmayan Toxic duyarlılığını tahmin etmek için kullanabilirsiniz. Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri. Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın. İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş. Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="using-the-model-prediction"></a>Modeli kullanılarak: tahmin

Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için. Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır. Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>Dağıtma ve yüklenen modeliyle tahmin edin

Oluşturma `PredictWithModelLoadedFromFile` yöntemi hemen önce `SaveModelAsFile` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

`PredictWithModelLoadedFromFile` Yöntemi aşağıdaki görevleri yürütür:

* Toplu test verilerini oluşturur.
* Test verilerine dayalı yaklaşım tahmin eder.
* Bir araya getirir, verileri ve raporlama için Öngörüler test edin.
* Tahmin edilen sonuçları görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Predict` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

Eğitilen modelin Öngörüler, test etmek için bazı açıklamalar ekleme `PredictWithModelLoadedFromFile` yöntemi:

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

Model yüklenemiyor

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]

Bir modeliniz olduğuna göre yorum kullanarak veri Toxic veya olmayan Toxic yaklaşım tahmin etmek için kullanabileceğiniz <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> yöntemi. Bir öngörü almak için kullanın `Predict` yeni veriler. Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın. İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş. Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir. Aşağıdaki kodu ekleyin `PredictWithModelLoadedFromFile` yöntemi tahminler elde etmek için:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="using-the-loaded-model-for-prediction"></a>Tahmin için yüklenen modeli kullanma

Görüntü `SentimentText` ve ilgili yaklaşım tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için. Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır. Aşağıdakileri kullanarak sonuçları için bir başlık oluşturma <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

Tahmin edilen sonuçlarını görüntülemeden önce yaklaşımını ve özgün açıklamayı, tahmin edilen yaklaşım ile birlikte görmek için tahmini birleştirin. Aşağıdaki kod <xref:System.Linq.Enumerable.Zip%2A> gerçekleşen, yapmanız gereken yöntemini bu nedenle bu kodunu ekleyin sonraki:

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

Birleştirilmiş göre `SentimentText` ve `Sentiment` bir sınıf kullanarak sonuçları görüntüleyebilirsiniz <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemi:

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

C# 7.0 C# 7.1 ve projenin varsayılan dil sürümü yeni bir özellik olan demet öğesi adları olan olayla olduğundan, C# 7.1 veya üzeri dil sürümünü değiştirmek gerekir.
Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**. Seçin **derleme** sekmenize **Gelişmiş** düğmesi. Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm). **Tamam** düğmesini seçin.

## <a name="results"></a>Sonuçlar

Sonuçlar aşağıdakine benzer olmalıdır. İşlem hattı işlediği gibi iletileri görüntüler. Uyarıları ve iletileri işlemeyi görebilirsiniz. Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 94.44%
Auc: 98.77%
F1Score: 94.74%
=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.5297049
=============== End of Predictions ===============

=============== New iteration of Model ===============
=============== Create and Train the Model ===============
=============== End of training ===============


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of loaded model with a multiple sample ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: I love this article. | Prediction: Not Toxic | Probability: 0.09454837

```

Tebrikler! Sınıflandırma ve iletileri yaklaşımını tahminde için makine öğrenme modeli artık başarıyla oluşturdunuz. Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) depo.

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
