---
title: Bir GitHub sorunu sınıflı sınıflandırma senaryosunda ML.NET kullanın
description: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları için belirli bir alanla atamak sınıflandırmak için nasıl kullanılacağını keşfedin.
ms.date: 01/22/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3983fe1dae98deb485585cb3b3868bdbb68c8c39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746684"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a>Öğretici: ML.NET bir çok sınıflı sınıflandırma senaryosunda GitHub sorunları sınıflandırmak için kullanın.

Bu örnek öğretici ML.NET kullanarak bir .NET Core konsol uygulaması kullanarak aracılığıyla bir GitHub sorunu sınıflandırıcı oluşturma gösterilmektedir C# Visual Studio 2017'de.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenimi görevini seçin
> * Verilerinizi hazırlama
> * Öğrenme işlem hattınızı oluşturun
> * Sınıflandırıcı yükleme
> * Modeli eğitme
> * Farklı bir veri kümesiyle modeli değerlendirme
> * Test verileri sonucu modeli ile tek bir örneğini tahmin edin
> * Yüklenen modeli test veri sonuçlarını tahmin edin

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

## <a name="github-issue-sample-overview"></a>GitHub sorunu örneğine genel bakış

Örnek ML.NET sınıflandırır ve bir GitHub sorunu alan etiketini tahmin eden bir model eğitip için kullanan bir konsol uygulamasıdır. Ayrıca, kalite analizi için ikinci bir veri kümesi modeliyle değerlendirir. Çıkış veri kümeleri dotnet/corefx'te GitHub deposundan ' dir.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

* [Github sorunlar sekmeyle dosyası (issues_train.tsv)](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).
* [Github sorunları sekmeyle dosyası (issues_test.tsv) test](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).

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
4. **Çalıştır**
   * **Model tüketim**

### <a name="understand-the-problem"></a>Sorunu anlama

Öncelikle, oluşturmak ve modeli eğitmek destekleyebileceği bölümleri aşağı kesmek için sorunu anlamak gerekir. Problemi parçalamak, tahmin edin ve sonuçları değerlendirin olanak tanır.

Sorun Bu öğretici için hangi alan gelen GitHub sorunları bunları öncelik belirleme ve planlama için doğru etiket için ait öğrenmektir.

Aşağıdaki problemi bölünebilir:

* sorun başlık metni
* Sorun açıklaması metni
* model eğitim verileri için bir alan değeri
* bir tahmin edilen alan değeri değerlendirmek ve işletimsel olarak kullanın

Ardından gerek **belirlemek** alanı Görev Seçimi öğrenme makineyle yardımcı olur.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Bu sorun aşağıdaki gerçekleri bildirin:

Eğitim verileri:

GitHub sorunları birçok alanda etiketli (**alan**) aşağıdaki örneklerde gösterildiği gibi:

* alan System.Numerics
* System.Xml alanı
* alan altyapı
* alan System.Linq
* alan System.IO

Tahmin **alan** yeni GitHub sorunu aşağıdaki örneklerde olduğu gibi böyle:

* Debug.Assert Contract.Assert vs
* System.Xml içinde alanları salt okunur yapın

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

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

### <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "SentimentAnalysis" yazın ve ardından **Tamam** düğmesi.

2. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyalarınızı kaydetmek için:

    İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**. "Veri" yazın ve Enter tuşuna basın.

3. Yükleme **Microsoft.ML NuGet paketini**:

    Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

### <a name="prepare-your-data"></a>Verilerinizi hazırlama

1. İndirme [issues_train.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) ve [issues_test.tsv](https://github.com/dotnet/samples/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör. İlk veri kümesini makine öğrenme modeli eğitir ve ikinci modelinizi nasıl doğru olup olmadığını değerlendirmek için kullanılabilir.

2. Her bir Çözüm Gezgini'nde sağ \*.tsv dosyaları ve select **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

### <a name="create-classes-and-define-paths"></a>Yollarını tanımlamak ve sınıfları oluşturma

Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

Kısa bir süre önce indirilen dosyaları ve bir genel değişken için yollar tutmak için üç genel alanlar oluşturmak için ihtiyacınız `TextLoader`:

* `_trainDataPath` Yolun modeli eğitmek için kullanılan veri kümesine sahiptir.
* `_testDataPath` Yolun model değerlendirmek için kullanılan veri kümesine sahiptir.
* `_modelPath` eğitilen modelin kaydedildiği yolu vardır.
* `_mlContext` olan <xref:Microsoft.ML.MLContext> , işlem bağlamı sağlar.
* `_trainingDataView` olan <xref:Microsoft.ML.Data.IDataView> eğitim veri kümesi işlemek için kullanılır.
* `_predEngine` olan <xref:Microsoft.ML.PredictionEngine%602> tek Tahminler elde etmek için kullanılır.
* `_reader` olan <xref:Microsoft.ML.Data.TextLoader> yüklemek ve veri kümeleri dönüştürmek için kullanılır.

Aşağıdaki kod satırı hemen üstündeki ekleyin `Main` yöntemi bu yollar ve diğer değişkenlerini belirtmek için:

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir. Yeni bir sınıf, projenize ekleyin:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *GitHubIssueData.cs*. Ardından, **Ekle** düğmesi.

    *GitHubIssueData.cs* dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki `using` üstüne deyimi *GitHubIssueData.cs*:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `GitHubIssue` ve `IssuePrediction`, *GitHubIssueData.cs* dosyası:

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`GitHubIssue` Giriş veri kümesi sınıfı ve aşağıdaki <xref:System.String> alanlar:

* `ID` GitHub sorun kimliği için bir değer içeriyor
* `Area` için bir değer içeren `Area` etiketi
* `Title` GitHub sorunu başlık içerir
* `Description` GitHub sorun açıklaması içerir

`IssuePrediction` eğitilen modelin sonra sınıf tahmin için kullanılır. Tek bir sahip `string` (`Area`) ve bir `PredictedLabel` `ColumnName` özniteliği. `Label` Oluşturup modeli ya da onun da model değerlendirmek için ikinci bir veri kümesi ile kullanılan eğitmek için kullanılır. `PredictedLabel` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme, bir giriş eğitim verileri, tahmin edilen değerleri ve modeli ile kullanılır.

ML.NET modeliyle oluştururken oluşturarak başlayın bir <xref:Microsoft.ML.MLContext>. Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework. Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilecek ML işiniz için bir bağlam sağlar.

### <a name="initialize-variables-in-main"></a>Ana değişkenleri başlatma

Başlatma `_mlContext` yeni bir örneğini genel değişkenin `MLContext` ile rastgele bir tohum (`seed: 0`) arasında birden çok eğitimleri/deterministic tekrarlanabilir sonuçlar.  Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>Verileri yükleme

Ardından, başlatma `_trainingDataView` <xref:Microsoft.ML.Data.IDataView> genel değişken ve ile veri yükleme `_trainDataPath` parametresi.

 Giriş ve çıkış olarak `Transforms`, `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.

ML.NET içinde veri benzer bir `SQL view`. Bu, gevşek değerlendirilen, şema ve heterojen olur. Nesne, işlem hattını ilk kısmı ve verileri yükler. Bu öğreticide, bir veri kümesi sorunu başlıklarını, açıklamaları ve karşılık gelen alan GitHub etiketi ile yükler. `DataView` Oluşturup modeli eğitmek için kullanılır.

Önceden oluşturduğunuz beri `GitHubIssue` veri modeli türüyle eşleşen veri kümesi şeması, başlatma, eşleme ve veri kümesi bir kod satırının içine yükleniyor birleştirebilirsiniz.

Satırın ilk bölümü (`CreateTextReader<GitHubIssue>(hasHeader: true)`) oluşturur bir <xref:Microsoft.ML.Data.TextLoader> çıkarım veri kümesi şeması tarafından gelen `GitHubIssue` veri türü ve veri kümesi üst bilgisini kullanarak model.

Oluşturduğunuz zaman veri şemasını önceden tanımlanmış `GitHubIssue` sınıfı. Şemanızı için:

* İlk sütun `ID` (GitHub sorunu kimliği)
* ikinci sütunda `Area` (eğitim tahmin)
* üçüncü sütunda `Title` (GitHub sorun başlığı) sanal makinede ilk [özellik](../resources/glossary.md##feature) tahmin etmek için kullanılan `Area`
* Dördüncü sütun `Description` tahmin etmek için kullanılan ikinci özelliğidir `Area`

Satırın ikinci bölümü (`.Read(_trainDataPath)`) kullanan <xref:Microsoft.ML.Data.TextLoader.Read%2A> eğitim metni yüklemek için gereken yöntemini kullanarak dosya `_trainDataPath` içine `IDataView` (`_trainingDataView`) genel değişkeni.  

Başlatma ve yüklemek için `_trainingDataView` ardışık düzeni için kullanmak için genel değişkeni sonra aşağıdaki kodu ekleyin `mlContext` başlatma:

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]


Sonraki kod satırı olarak ekleyin `Main` yöntemi:

[!code-csharp[CallProcessData](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

`ProcessData` Yöntemi aşağıdaki görevleri yürütür:

* Ayıklar ve verileri dönüştürür.
* İşleme işlem hattı döndürür.

Oluşturma `ProcessData` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static EstimatorChain<ITransformer> ProcessData()
{

}
```

## <a name="extract-and-transform-the-data"></a>Verileri dönüştürme ve ayıklama

Ön işleme ve verileri temizleme bir veri kümesi, machine learning için etkili bir şekilde kullanılmadan önce gerçekleşen önemli görevlerdir. Ham veriler genellikle gürültülü ve güvenilmeyen ve değerleri eksik olabilir. Veri modelleme görevleri olmadan kullanarak yanıltıcı sonuçlara neden olabilir.

ML. NET dönüştürme işlem hatları, verilerinizi, eğitim veya test etmeden önce uygulanan dönüştürmeler özel bir dizi oluşturun. Veri Dönüşümleri birincil amacı olan [özellik kazandırma sayesinde](../resources/glossary.md#feature-engineering). Makine öğrenimi algoritmaları anlamak [özellikleri tespit](../resources/glossary.md#feature) metinsel verilerimizi ML algoritmalarınızı tanıyacak bir biçime dönüştürmek için sonraki adım, bu nedenle veri. Bu biçim bir [sayısal vektör](../resources/glossary.md#numerical-feature-vector).

Sonraki adımlarda sütunlara adlarıyla tanımlanan diyoruz `GitHubIssue` sınıfı.

Model eğitim ve diğer değerleri varsayılan olarak, hesaplanan zaman **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir. Alan GitHub etiketi tahmin etmek istediğimiz bir `GitHubIssue`, kopyalama `Area` sütuna **etiket** sütun. Bunu yapmak için kullanın `MLContext.Transforms.Conversion.MapValueToKey`, bu değer için bir sarmalayıcı <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> dönüştürme sınıfı.  `MapValueToKey` Döndürür bir <xref:Microsoft.ML.Data.EstimatorChain%601> bir işlem hattı etkin olacak. Bu ad `pipeline` eğitmen için ardından ekleyeceği şekilde `EstimatorChain`. Bu, sonraki kod satırı ekleyin:

[!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

Modeli eğitir algoritması **sayısal** yanında, böylece özellikleri çağrı `mlContext.Transforms.Text.FeaturizeText` hangi featurizes metni (`Title` ve `Description`) sayısal bir vektör her adlı sütuna `TitleFeaturized` ve `DescriptionFeaturized`. Featurizing farklı değerler her sütun için farklı sayısal anahtar değerleri atar ve makine öğrenme algoritmasına tarafından kullanılır.
Aşağıdaki kod ile işlem hattı her iki sütun için özellik kazandırma sayesinde ekleyin:

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak `Concatenate` dönüştürme sınıfı. Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun. Aşağıdaki kod ile işlem hattı için bu dönüşümü ekleyin:

[!code-csharp[Concatenate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 Ardından, ekleme bir <xref:Microsoft.ML.Data.EstimatorChain`1.AppendCacheCheckpoint%2A> üzerinden yineleme yapma, verileri birden çok kez önbellek kullanarak daha iyi performans için şu kod gibi alabilirsiniz şekilde DataView önbelleğe almak için

[!code-csharp[AppendCache](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

Ardışık Düzen sonunda dönüş `ProcessData` yöntemi.

[!code-csharp[ReturnPipeline](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

Bu adımda, ön işleme/özellik kazandırma sayesinde işler. ML.NET içinde kullanılabilir ek bileşenler kullanarak modelinizi ile daha iyi sonuçlar etkinleştirebilirsiniz.

## <a name="build-and-train-the-model"></a>Derleme ve modeli eğitme

Aşağıdaki çağrısı ekleyin `BuildAndTrainModel`yöntemi sonraki kod satırı olarak `Main` yöntemi:

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` Yöntemi aşağıdaki görevleri yürütür:

* Eğitim algoritması sınıfı oluşturur.
* Modeli eğitir.
* Eğitim verilerini temel alarak alan tahmin eder.
* Modele kaydeder bir `.zip` dosya.
* Model döndürür.

Oluşturma `BuildAndTrainModel` yöntemi hemen sonrasına `Main` yöntemi, aşağıdaki kodu kullanarak:

```csharp
public static void BuildAndTrainModel()
{

}
```

İki parametre BuildAndTrainModel yönteme geçirilen dikkat edin; bir `IDataView` eğitim veri kümesi için (`trainingDataView`) ve <xref:Microsoft.ML.Data.EstimatorChain%601> ProcessData içinde oluşturulan işleme işlem hattının (`pipeline`).

 İlk satırı olarak aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:

### <a name="choose-a-trainer-algorithm"></a>Eğitmen algoritma seçme

Eğitmen algoritması eklemek için çağrı `mlContext.Transforms.Text.FeaturizeText` döndüren sarmalayıcı yöntemini bir <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> nesne. Bu işlem hattında kullanacağınız karar ağacı learner budur. `SdcaMultiClassTrainer` Eklenir `pipeline` ve özellikleri tespit `Title` ve `Description` (`Features`) ve `Label` giriş geçmiş verilerden bilgi edinmek için parametreleri.

Aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:

[!code-csharp[SdcaMultiClassTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SdcaMultiClassTrainer)]

Eğitmen algoritması oluşturduğunuza göre eklenecek `pipeline`. Ayrıca okunabilir özgün durumuna döndürülecek değer etiketi eşlemek gerekir. Aşağıdaki kod ile bu eylemlerin her ikisini birden yapın:

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a>Modeli eğitme

Modeli eğitme <xref:Microsoft.ML.Data.TransformerChain%601>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi. Tahmin tanımlandıktan sonra kullanarak modelinize eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> zaten yüklenmiş eğitim verilerini sağlayarak. Bu tahminler elde etmek için kullanılacak bir modelini döndürür. `trainingPipeline.Fit()` işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi. Denemeyi böyle kadar yürütülmez.

Aşağıdaki kodu ekleyin `BuildAndTrainModel` yöntemi:

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

Sırada `model` olduğu bir `transformer` gereksinimi, tek tek örnekleri tahminler elde etmek için çok yaygın bir üretim senaryosu, çok sayıda veri satırı üzerinde çalışır. <xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi. Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` sonraki satırı olarak `BuildAndTrainModel` yöntemi:

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:

[!code-csharp[CreateTestIssue1](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

Bu tahmin etmek için kullanabileceğiniz `Area` sorun verileri tek bir örneğini etiketi. Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri. Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın. İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş. Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="model-operationalization-prediction"></a>Modeli kullanıma hazır hale getirme: tahmin

Görüntü `GitHubIssue` ve karşılık gelen `Area` tahmin sonuçları paylaşmak ve bunlar üzerinde buna göre hareket için etiket. Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır. Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>Kaydet ve değerlendirme için kullanılacak modeli eğitilir dön

Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain%601> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine. Eğitilen model bir .zip dosyası olarak kaydetmek için çağırmak için aşağıdaki kodu ekleyin. `SaveModelAsFile` yöntemi olarak bir sonraki satırda `BuildAndTrainModel`:

[!code-csharp[CallSaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

Model sonunda dönüş `BuildAndTrainModel` yöntemi.

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="save-the-model-as-azip-file"></a>Modeli a.zip dosyası olarak kaydedin.

Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `BuildAndTrainModel` yöntemi, aşağıdaki kodu kullanarak:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:

* Model bir .zip dosyası olarak kaydeder.

Ardından, yeniden kullanılabilir ve diğer uygulamalarda kullanılan model kaydetmek için bir yöntem oluşturun. `ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>. Bu zip dosyası olarak kaydetmek için oluşturacağınız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi. Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

Bir konsol iletisi ile yazarak dosyasının nerede yazılmıştır görüntüleyebilir `_modelPath`, aşağıdaki kodu kullanarak:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

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

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

Eğitim veri kümesi ile daha önce yaptığınız gibi eşleme başlatma birleştirin ve sınama veri kümesi bir kod satırının içine yükleniyor. Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir. Aşağıdaki kodu ekleyin `Evaluate` yöntemi:

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

`MulticlassClassificationContext.Evaluate` İçin bir sarmalayıcı olan <xref:Microsoft.ML.MulticlassClassificationContext.Evaluate%2A> belirtilen veri kümesi kullanan model için Kalite Ölçümleri hesaplar yöntemi. Döndürür bir <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> sınıflı sınıflandırma değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne.
Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir.
Kullanımına dikkat edin `Transform` machine Learning yöntemi `_trainedModel` özellikleri giriş ve tahmin döndürmek için genel değişkeni (dönüştürücü). Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

Aşağıdaki ölçümler sınıflı sınıflandırma için değerlendirilir:

* Mikro doğruluğu - her örnek sınıfı çifti eşit doğruluğu ölçüme katkıda bulunur.  Mikro doğruluğu, 1 olarak mümkün olduğunca yakın olmasını istediğiniz.

* Makro doğruluğu - her sınıf eşit doğruluğu ölçüme katkıda bulunur. Azınlık sınıfları daha büyük bir sınıf olarak eşit ağırlık verilir. Makrosu 1 olarak mümkün olduğunca yakın olmasını doğruluğu kullanmanız gerekir.

* Günlük zarar - bkz [günlük kaybı](../resources/glossary.md#log-loss). Sıfır olarak mümkün olduğunca yakın olmasını günlük zarar kullanmanız gerekir.

* Günlük kaybı azaltma - aralıkları gelen [-INF, 100], burada 100 mükemmel Öngörüler ve 0, ortalama Öngörüler gösterir. Günlük kaybı azaltma sıfır olarak mümkün olduğunca yakın olmasını istediğiniz.

### <a name="displaying-the-metrics-for-model-validation"></a>Model doğrulama için ölçümleri görüntüleme

Ölçümleri görüntülemek için sonuçları paylaşıp bunlar üzerinde harekete aşağıdaki kodu kullanın:

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>Kaydedilen modeli ile test veri sonucu tahmin edin

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallPredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

Oluşturma `PredictIssue` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:

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

İlk olarak, aşağıdaki kod ile daha önce kaydettiğiniz model yüklenemiyor:

[!code-csharp[LoadModel](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

Eğitilen modelin tahmine test etmek için bir GitHub sorunu Ekle `Predict` bir örneğini oluşturarak yöntemi `GitHubIssue`:

[!code-csharp[AddTestIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
Bir modeliniz olduğuna göre tek bir GitHub sorunu veri örneğini alan GitHub etiketini tahmin etmek için kullanabilirsiniz. Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri. Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın. İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş. Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir. Aşağıdaki kodu ekleyin `PredictIssue` yöntemi tahminler elde etmek için:

[!code-csharp[PredictIssue](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

### <a name="model-operationalization-prediction"></a>Modeli kullanıma hazır hale getirme: tahmin

Görüntü `Area` sorunu kategorilere ayırmak ve buna göre hareket üzerinde için. Bu, kullanıma hazır hale getirme, operasyonel ilke bir parçası olarak döndürülen veriler kullanılarak çağrılır. Aşağıdakileri kullanarak sonuçları için bir görüntü oluşturmak <xref:System.Console.WriteLine?displayProperty=nameWithType> kod:

[!code-csharp[DisplayResults](../../../samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>Sonuçlar

Sonuçlar aşağıdakine benzer olmalıdır. İşlem hattı işlediği gibi iletileri görüntüler. Uyarıları ve iletileri işlemeyi görebilirsiniz. Bunlar aşağıdaki sonuçlarından anlaşılması için kaldırılmıştır.

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
The model is saved to C:\Users\johalex\dotnet-samples\samples\machine-learning\tutorials\GitHubIssueClassification\bin\Debug\netcoreapp2.0\..\..\..\Models\model.zip
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.74
*       MacroAccuracy:    0.687
*       LogLoss:          .932
*       LogLossReduction: 63.852
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

Tebrikler! Bir machine learning modeli sınıflandırmak ve bir alan etiketini bir GitHub sorunu için tahmin etmek için şimdi başarıyla oluşturdunuz. Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) depo.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
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
