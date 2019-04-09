---
title: ML.NET ile bir regresyon learner kullanarak fiyatlarını tahmin etme
description: ML.NET ile bir regresyon learner kullanarak fiyatlarını tahmin etme.
author: aditidugar
ms.author: johalex
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: b97ea433b36aa52682e5e86ab493cfabf8f86193
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122089"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a>Öğretici: ML.NET ile bir regresyon learner kullanarak fiyatlarını tahmin etme

Bu öğretici ML.NET oluşturmak için nasıl kullanılacağını gösterir. bir [regresyon modeli](../resources/glossary.md#regression) Fiyatlar, özellikle tahmin etmede, New York City taksi fares.

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu öğretici ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.11**. Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenimi görevini seçin
> * Hazırlama ve verileri anlama
> * Öğrenme işlem hattı oluşturma
> * Yükleme ve dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitme
> * Modeli değerlendirme
> * Kullanım modeli tahminler elde etmek için

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

## <a name="understand-the-problem"></a>Sorunu anlama

Bu da oturan bir taksi seyahat, taksi tahmin etme hakkında bir sorundur. İlk bakışta takip edilerek özgün uzaklık üzerinde yalnızca bağımlı görünüyor olabilir. Ancak, New York taksi satıcıları ek Yolcuların veya nakit yerine bir kredi kartıyla ödeme gibi diğer faktörlere için değişken miktarda ücret alınır.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenimi görevini seçin

Veri kümesindeki diğer etkenlere göre bir gerçek değer için fiyat değerini tahmin etmek istersiniz. Seçtiğiniz yapmak için bir [regresyon](../resources/glossary.md#regression) machine learning görev.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Visual Studio 2017'yi açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "TaxiFarePrediction" yazın ve ardından **Tamam** düğmesi.

1. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi ve model dosyaları depolamak için:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**. "Veri" yazın ve Enter tuşuna basın.

1. Yükleme **Microsoft.ML** NuGet paketi:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**. Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

## <a name="prepare-and-understand-the-data"></a>Hazırlama ve verileri anlama

1. İndirme [taksi taksi train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [taksi taksi test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri ayarlar ve bunları kaydetmek *veri* önceki adımda oluşturduğunuz klasör. Machine learning modeli eğitmek ve modelin nasıl doğru olup'ı değerlendirmek için bu veri kümesi kullanıyoruz. Bu veri kümesi başlangıçta arasındadır [NYC TLC taksi seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. İçinde **Çözüm Gezgini**, her birini sağ tıklayın \*.csv dosyalarını ve select **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

1. Açık **taksi taksi train.csv** veri kümesi ve ilk satırında sütun üst bilgilerini bakın. Her sütun bir göz atın. Verileri anlamak ve hangi sütunların karar **özellikleri** hangisinin **etiket**.

**Etiket** tahmin etmek istediğiniz sütunu tanımlayıcısıdır. Tanımlanan **özellikleri** etiketi tahmin etmek için kullanılır.

Sağlanan veri kümesi şu sütunları içerir:

* **vendor_id:** Taksi satıcı kimliği bir özelliktir.
* **rate_code:** Taksi dönüş oranı türünü bir özelliktir.
* **passenger_count:** Bir özellik Yolcuların seyahat üzerinde sayısıdır.
* **trip_time_in_secs:** Seyahat geçen süre miktarı. Seyahat, taksi seyahat tamamlanmadan önce tahmin etmek istersiniz. Bu ne kadar seyahat bilmiyorum dakikamızı ayıralım. Bu nedenle, seyahat süresi, bir özellik değildir ve bu sütunu modelden dışında bırakacağız.
* **trip_distance:** Seyahat mesafesini bir özelliktir.
* **payment_type:** Ödeme yöntemini (nakit veya kredi kartı) bir özelliktir.
* **fare_amount:** Ücretli toplam taksi taksi etiketi olur.

## <a name="create-data-classes"></a>Veri sınıfları oluşturma

Girdi verilerini ve Öngörüler için sınıflar oluşturun:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TaxiTrip.cs*. Ardından, **Ekle** düğmesi.
1. Aşağıdaki `using` yeni dosya için yönergeler:

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `TaxiTrip` ve `TaxiTripFarePrediction`, *TaxiTrip.cs* dosyası:

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` giriş verisi sınıfıdır ve her bir veri kümesi sütunları tanımlarına sahip. Kullanım <xref:Microsoft.ML.Data.LoadColumnAttribute> veri kümesinde kaynak sütunları dizin belirtmek için özniteliği.

`TaxiTripFarePrediction` Sınıfı, tahmini sonuçlar'ı temsil eder. Tek bir kayan noktalı sayı alana sahip `FareAmount`, ile bir `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> özniteliği uygulandı. Regresyon görev durumunda **puanı** sütun tahmin edilen etiket değerlerini içerir.

> [!NOTE]
> Kullanım `float` giriş ve tahmin verilerini sınıflardaki kayan nokta değerlerini temsil eden tür.

## <a name="define-data-and-model-paths"></a>Veri ve model tanımlar

Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Veri kümeleri dosyalarına ve modeli kaydedin ve dosyaya yolları tutmak için üç alanı oluşturmanız gerekir:

* `_trainDataPath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.
* `_testDataPath` model değerlendirmek için kullanılan veri kümesiyle dosyasının yolunu içerir.
* `_modelPath` eğitilen modelin depolandığı dosya yolu içerir.

Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için ve `_textLoader` değişkeni:

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

ML.NET modeliyle oluştururken ML bağlam oluşturarak başlayın. Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework. Ortam, özel durum izleme ve günlüğe kaydetme için kullanılabilmesi için machine learning işiniz için bir bağlam sağlar.

### <a name="initialize-variables-in-main"></a>Ana değişkenleri başlatma

Adlı bir değişken oluşturma `mlContext` ve yeni bir örneğini ile başlatma `MLContext`.  Değiştirin `Console.WriteLine("Hello World!")` aşağıdaki kod satırıyla `Main` yöntemi:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

Sonraki kod satırı olarak ekleyin `Main` çağrılacak yöntem `Train` yöntemi:

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train` Yöntemi aşağıdaki görevleri yürütür:

* Verileri yükler.
* Ayıklar ve verileri dönüştürür.
* Modeli eğitir.
* Model .zip dosyası olarak kaydeder.
* Model döndürür.

`Train` Yöntemi modeli eğitir. Bu yöntem oluşturma hemen altına `Main`, aşağıdaki kodu kullanarak:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

İki parametre olarak geçiriyoruz `Train` yöntemi; bir `MLContext` bağlamının (`mlContext`) ve veri kümesi yolu için bir dize (`dataPath`). Veri kümelerini yüklemek için bu yöntem yeniden oluşturacağız.

## <a name="load-and-transform-data"></a>Veri yükleme ve dönüştürme

Kullanarak verileri yüklemek `MLContext.Data.LoadFromTextFile` için sarmalayıcı [LoadFromTextFile yöntemi](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29). Döndürür bir <xref:Microsoft.Data.DataView.IDataView>. 

Giriş ve çıkış olarak `Transforms`, `DataView` için karşılaştırılabilir temel veri işlem hattı türü `IEnumerable` için `LINQ`.

ML.NET veriler SQL görünümüne benzer. Bu, gevşek değerlendirilen, şema ve heterojen olur. Nesne, işlem hattını ilk kısmı ve verileri yükler. Bu öğreticide, bir veri kümesi ile taksi seyahat fiyatlandırma bilgileri yükler. Bu model oluşturmayı ve bunu eğitmek için kullanılır.

İlk satırı olarak aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

Sonraki adımlarda sütunlara adlarıyla tanımlanan diyoruz `TaxiTrip` sınıfı.

Model eğitim ve diğer değerleri varsayılan olarak, hesaplanan zaman **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir. Taksi seyahat taksi tahmin etmek istediğimiz gibi kopyalayın `FareAmount` sütuna **etiket** sütun. Bunu yapmak için kullanın `CopyColumnsEstimator` dönüştürme sınıfı ve aşağıdaki kodu ekleyin:

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

Modeli eğitir algoritması **sayısal** kategorik verileri dönüştürmek zorunda özellikleri (`VendorId`, `RateCode`, ve `PaymentType`) içine numaraları değerleri (`VendorIdEncoded`, `RateCodeEncoded`, ve `PaymentTypeEncoded`). Bunu yapmak için Microsoft.ML.Transforms.OneHotEncodingTransformer kullanmak > atayan farklı sayısal dönüştürme sınıfına anahtar sütunları farklı değerlerle değerlerini ve aşağıdaki kodu ekleyin:

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak `mlContext.Transforms.Concatenate` dönüştürme sınıfı. Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun. Aşağıdaki kodu ekleyin:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Veri ardışık düzenine eklemek ve giriş doğru biçime dönüştürme sonra bir öğrenme algoritması seçiyoruz (**learner**). Learner modeli eğitir. Seçtik bir **regresyon** görev kullanacağız Bu sorun için bir `FastTreeRegressionTrainer` ML.NET tarafından sağlanan regresyon öğrencileriyle biri olan learner.

`FastTreeRegressionTrainer` Eğitim algoritması kullanan gradyan artırma. Gradyan artırma bir machine learning teknik regresyon sorunları var. Bu, her regresyon ağaç tarafınızdaki bir biçimde oluşturur. Her adımda hata oluştu ölçmenizi ve sonraki düzeltmek için önceden tanımlanmış kaybı işlevi kullanır. Aslında bir topluluğu, tahmin modellerini daha zayıf bir tahmin modeli sonucudur. Gradyan artırma hakkında daha fazla bilgi için bkz. [artırılmış karar ağacı regresyonu](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Aşağıdaki kodu ekleyin `Train` ekleme yöntemi `FastTreeRegressionTrainer` önceki adımda eklenen veri işleme kodu:

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Modeli eğitme

Modeli eğitmek için son adımdır bakın. Biz modeli eğitmek <xref:Microsoft.ML.Data.TransformerChain>bağlı olarak yüklenen ve dönüştürülen bir veri kümesi. Tahmin tanımlandıktan sonra kullanarak modeli eğitme <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> zaten yüklenmiş eğitim verilerini sağlayarak. Bu tahminler elde etmek için kullanılacak bir modelini döndürür. `pipeline.Fit()` işlem hattı eğitir ve döndürür bir `Transformer` göre `DataView` geçirildi. Denemeyi böyle kadar yürütülmez.

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

### <a name="save-the-model"></a>Modeli kaydedin

Bu noktada, türünde bir modeli kullandığınız <xref:Microsoft.ML.Data.TransformerChain> , tümleştirilebilir, mevcut veya yeni .NET uygulamalarınızın hiçbirine. Model bir .zip dosyası olarak kaydetmek için aşağıdaki kodu ekleyin sonunda `Train` yöntemi:

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a>Bir .zip dosyası olarak modeli kaydedin

Oluşturma `SaveModelAsFile` yöntemi hemen sonrasına `Train` yöntemi, aşağıdaki kodu kullanarak:

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` Yöntemi aşağıdaki görevleri yürütür:

* Model bir .zip dosyası olarak kaydeder.

Modeli yeniden ve diğer uygulamalarda kullanılan üzere kaydetmek için bir yöntem için oluşturmamız gerekir. `ITransformer` Sahip bir <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> alır yöntemi `_modelPath` genel alan ve <xref:System.IO.Stream>. Bu zip dosyası olarak kaydetmek istediğimiz beri oluşturacağız `FileStream` çağırmadan önce hemen `SaveTo` yöntemi. Aşağıdaki kodu ekleyin `SaveModelAsFile` yöntemi sonraki satır olarak:

[!code-csharp[SaveToMethod](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

Biz burada dosyanın bir konsol iletisi ile yazarak yazılmıştır görüntüleyebilir `_modelPath`, aşağıdaki kodu kullanarak:

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Değerlendirme model etiket değerlerini ne kadar iyi tahmin denetleme işlemidir. Model modeli eğitmek için kullanılmayan verileri iyi tahminler yapar önemlidir. Bu öğreticide işlendiğinden bunu yapmanın bir yolu, verileri eğitim ve test veri kümesi bölme sağlamaktır. Eğitim verileri modeli eğittiğimize göre test verileri ne kadar iyi gerçekleştirdiği görebilirsiniz.

`Evaluate` Yöntemi modeli değerlendirir. Bu yöntem oluşturmak için aşağıdaki kodu ekleyin. `Train` yöntemi:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```
`Evaluate` Yöntemi aşağıdaki görevleri yürütür:

* Test veri kümesini yükler.
* Regresyon değerlendirici oluşturur.
* Model değerlendirir ve ölçüm oluşturur.
* Ölçümleri görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

Test veri kümesini kullanarak yük `MLContext.Data.LoadFromTextFile` sarmalayıcı. Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirebilir. Aşağıdaki kodu ekleyin `Evaluate` yöntemi:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

Ardından, makine öğrenimi kullanın `model` özellikleri giriş ve tahmin döndürmek için parametre (dönüştürücü). Aşağıdaki kodu ekleyin `Evaluate` yöntemi sonraki satır olarak:

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

`RegressionContext.Evaluate` Yöntemi hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma. Döndürür bir <xref:Microsoft.ML.Data.RegressionMetrics> regresyon değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne. Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir. Sonraki satırda olarak aşağıdaki kodu ekleyin `Evaluate` yöntemi:

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

Modeli değerlendirme ve değerlendirme ölçümleri üretmek için aşağıdaki kodu ekleyin:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) regresyon modelleri, başka bir değerlendirme unsurdur. RSquared 0 ile 1 arasındaki değerleri alır. Daha değerini 1 olarak daha iyi modelidir yakınız. Aşağıdaki kodu ekleyin `Evaluate` yöntemi RSquared değerini görüntülemek için:

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) gerileme modelini değerlendirme ölçümlerini biridir. Daha düşük olan, daha iyi modelidir. Aşağıdaki kodu ekleyin `Evaluate` yöntemi RMS değerini görüntülemek için:

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Kullanım modeli tahminler elde etmek için

## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a>Model ve tek bir yorum ile test veri sonucu tahmin edin

Oluşturma `TestSinglePrediction` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

`TestSinglePrediction` Yöntemi aşağıdaki görevleri yürütür:

* Test verilerini tek bir yorum oluşturur.
* Test verilerini temel alarak taksi miktarı tahmin eder.
* Bir araya getirir, verileri ve raporlama için Öngörüler test edin.
* Tahmin edilen sonuçları görüntüler.

Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

Modeli zip dosyasından yükleme istiyoruz beri kaydettik, oluşturacağız `FileStream` çağırmadan önce hemen `Load` yöntemi. Aşağıdaki kodu ekleyin `TestSinglePrediction` yöntemi sonraki satır olarak:

[!code-csharp[LoadTheModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

Sırada `model` olduğu bir `transformer` gereksinimi, tek tek örnekleri tahminler elde etmek için çok yaygın bir üretim senaryosu, çok sayıda veri satırı üzerinde çalışır. <xref:Microsoft.ML.PredictionEngine%602> Öğesinden döndürülen bir sarmalayıcı olan `CreatePredictionEngine` yöntemi. Oluşturmak için aşağıdaki kodu ekleyelim `PredictionEngine` sonraki satırı olarak `TestSinglePrediction` yöntemi:

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
Bu öğretici, bu sınıf içinde bir test seyahat kullanır. Daha sonra modeli denemek için diğer senaryolar ekleyebilirsiniz. Eğitilen modelin Maliyet tahminini test etmek için bir seyahat ekleme `TestSinglePrediction` bir örneğini oluşturarak yöntemi `TaxiTrip`:

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 Biz taksi seyahat verilerini tek bir örneği temel taksi tahmin etmek için kullanabilirsiniz. Bir öngörü almak için kullanın <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> verileri. Giriş verilerini bir dizedir ve modeli içeren özellik kazandırma sayesinde unutmayın. İşlem hattınızı, eğitim ve tahmin sırasında eşitlenmiş. Özellikle tahminler elde etmek için ön işleme/özellik kazandırma sayesinde kod yazmak zorunda olmadığı ve aynı API batch ve tek seferlik Öngörüler üstlenir.

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

Belirtilen seyahat, tahmin edilen taksi görüntülemek için aşağıdaki kodu ekleyin. `TestSinglePrediction` yöntemi:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

Test durumunuz için tahmin edilen taksi taksi görmek için programı çalıştırın.

Tebrikler! Başarıyla taksi seyahat fares tahmin etmeye yönelik bir machine learning modeli, doğruluğunun değerlendirilir, derleyip tahminlerde bulunmak için kullanılır. Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposu.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenimi görevini seçin
> * Hazırlama ve verileri anlama
> * Öğrenme işlem hattı oluşturma
> * Yükleme ve dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitme
> * Modeli değerlendirme
> * Kullanım modeli tahminler elde etmek için

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Iris kümeleme](iris-clustering.md)
