---
title: 'Öğretici: Regresyon kullanarak fiyatlarını tahmin etme'
description: Bu öğreticide, özellikle fiyatlarını tahmin etmek için New York City taksi fares ML.NET kullanarak bir regresyon modeli derler gösterilmektedir.
author: jralexander
ms.author: johalex
ms.date: 05/09/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 40f70b6d89bf19ae0b20cb00d56e9f7dceb48f61
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377788"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Öğretici: ML.NET ile regresyon kullanarak fiyatlarını tahmin etme

Bu öğreticide nasıl oluşturulacağını gösterir. bir [regresyon modeli](../resources/glossary.md#regression) Fiyatlar, özellikle tahmin etmek için New York City taksi fares ML.NET kullanma.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * Hazırlama ve verileri anlama
> * Yükleme ve dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitme
> * Modeli değerlendirme
> * Kullanım modeli tahminler elde etmek için

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Oluşturma bir **.NET Core konsol uygulaması** "TaxiFarePrediction" denir.

1. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi ve model dosyaları depolamak için.

1. Yükleme **Microsoft.ML** NuGet paketi:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**. Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listeden bir paket seçin ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz. İçin de aynısını yapın **Microsoft.ML.FastTree** Nuget paketi.

## <a name="prepare-and-understand-the-data"></a>Hazırlama ve verileri anlama

1. İndirme [taksi taksi train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [taksi taksi test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri ayarlar ve bunları kaydetmek *veri* önceki adımda oluşturduğunuz klasör. Machine learning modeli eğitmek ve modelin nasıl doğru olup'ı değerlendirmek için bu veri kümesi kullanıyoruz. Bu veri kümesi başlangıçta arasındadır [NYC TLC taksi seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. İçinde **Çözüm Gezgini**, her birini sağ tıklayın \*.csv dosyalarını ve select **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

1. Açık **taksi taksi train.csv** veri kümesi ve ilk satırında sütun üst bilgilerini bakın. Her sütun bir göz atın. Verileri anlamak ve hangi sütunların karar **özellikleri** hangisinin **etiket**.

`label` Tahmin etmek istediğiniz sütun. Tanımlanan `Features`modeli tahmin etmek için size girişleri `Label`.

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

### <a name="define-data-and-model-paths"></a>Veri ve model tanımlar

Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Veri kümeleri dosyalarına ve modeli kaydedin ve dosyaya yolları tutmak için üç alanı oluşturmanız gerekir:

* `_trainDataPath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.
* `_testDataPath` model değerlendirmek için kullanılan veri kümesiyle dosyasının yolunu içerir.
* `_modelPath` eğitilen modelin depolandığı dosya yolu içerir.

Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için ve `_textLoader` değişkeni:

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Tüm ML.NET işlemleri başlangıç süresi [MLContext sınıfı](xref:Microsoft.ML.MLContext). Başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur. Bu, kavramsal olarak, benzer `DBContext` Entity Framework.

### <a name="initialize-variables-in-main"></a>Ana değişkenleri başlatma

Değiştirin `Console.WriteLine("Hello World!")` satırına `Main` bildirmek ve başlatmak için aşağıdaki kod ile yöntemi `mlContext` değişkeni:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

Sonraki kod satırı olarak ekleyin `Main` çağrılacak yöntem `Train` yöntemi:

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train()` Yöntemi aşağıdaki görevleri yürütür:

* Verileri yükler.
* Ayıklar ve verileri dönüştürür.
* Modeli eğitir.
* Model döndürür.

`Train` Yöntemi modeli eğitir. Bu yöntem oluşturma hemen altına `Main`, aşağıdaki kodu kullanarak:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Veri yükleme ve dönüştürme

ML.NET kullanan [IDataView sınıfı](xref:Microsoft.ML.IDataView) sayısal ya da metin tablosal verileri açıklamak esnek ve verimli bir yolu olarak. `IDataView` iki metin dosyalarını yükleyebilir veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları). İlk satırı olarak aşağıdaki kodu ekleyin `Train()` yöntemi:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

Taksi seyahat taksi tahmin etmek istediğiniz gibi `FareAmount` sütun `Label` (modelin çıkış) tahmin kullanım `CopyColumnsEstimator` kopyalamak için dönüştürme sınıfına `FareAmount`ve aşağıdaki kodu ekleyin: 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

Modeli eğitir algoritması **sayısal** kategorik verileri dönüştürmek zorunda özellikleri (`VendorId`, `RateCode`, ve `PaymentType`) içine numaraları değerleri (`VendorIdEncoded`, `RateCodeEncoded`, ve `PaymentTypeEncoded`). Bunu yapmak için kullanın [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) atayan farklı sayısal dönüştürme sınıfına anahtar sütunları farklı değerlerle değerlerini ve aşağıdaki kodu ekleyin:

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak `mlContext.Transforms.Concatenate` dönüştürme sınıfı. Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun. Aşağıdaki kodu ekleyin:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Bu sorun, taksi seyahat taksi da oturan tahmin etme hakkında olmasıdır. İlk bakışta takip edilerek özgün uzaklık üzerinde yalnızca bağımlı görünüyor olabilir. Ancak, New York taksi satıcıları ek Yolcuların veya nakit yerine bir kredi kartıyla ödeme gibi diğer faktörlere için değişken miktarda ücret alınır. Veri kümesindeki diğer etkenlere göre bir gerçek değer için fiyat değerini tahmin etmek istersiniz. Bunu yapmak için seçtiğiniz bir [regresyon](../resources/glossary.md#regression) machine learning görev.

Append [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) sonraki kod satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarını için machine learning görev `Train()`:

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Modeli eğitme

Eğitim modeline uygun `dataview` ve eğitim modeli, kod aşağıdaki satırı ekleyerek dönüş `Train()` yöntemi:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.

Aşağıdaki kod satırı ile eğitilmiş modelin dönüş `Train()` yöntemi:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Ardından, kalite güvencesi ve doğrulama test verilerinizle, model performansını değerlendirme. Oluşturma `Evaluate()` yöntemi hemen sonrasına `Train()`, aşağıdaki kod ile:

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

Test veri kümesini kullanarak yük [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) yöntemi. Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirin aşağıdaki kodu ekleyerek `Evaluate` yöntemi:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

Ardından, dönüştürme `Test` aşağıdakileri ekleyerek veri kod için `EvaluateModel()`:

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi giriş veri kümesi satırlarında test için Öngörüler sağlar.

`RegressionContext.Evaluate` Yöntemi hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma. Döndürür bir <xref:Microsoft.ML.Data.RegressionMetrics> regresyon değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne. 

Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir. Sonraki satırda olarak aşağıdaki kodu ekleyin `Evaluate` yöntemi:

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

Ayarlanırsa, tahmin sonra [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) yöntemi değerlendirir gerçek tahmin edilen değerlerle karşılaştırır modeli `Labels` modelin nasıl performans gösterdiğini üzerinde test veri kümesini ve döndürür ölçümleri de.

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

Oluşturma `TestSinglePrediction` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
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

Kullanım `PredictionEngine` taksi aşağıdaki kodu ekleyerek tahmin etmek için `TestSinglePrediction()`:

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine sınıfı](xref:Microsoft.ML.PredictionEngine%602) verileri tek bir örneğini geçirin ve sonra bir öngörü üzerinde gerçekleştirmek izin veren bir kolaylık API.

Bu öğretici, bu sınıf içinde bir test seyahat kullanır. Daha sonra modeli denemek için diğer senaryolar ekleyebilirsiniz. Eğitilen modelin Maliyet tahminini test etmek için bir seyahat ekleme `TestSinglePrediction()` bir örneğini oluşturarak yöntemi `TaxiTrip`:

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

Ardından, taksi seyahat verilerini tek bir örneği temel taksi tahmin edin ve geçirin `PredictionEngine` aşağıdaki kodda bir sonraki satırı olarak ekleyerek `TestSinglePrediction()` yöntemi:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi verileri tek bir örneği üzerinde bir tahmin sağlar.

Belirtilen seyahat, tahmin edilen taksi görüntülemek için aşağıdaki kodu ekleyin. `TestSinglePrediction` yöntemi:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

Test durumunuz için tahmin edilen taksi taksi görmek için programı çalıştırın.

Tebrikler! Başarıyla taksi seyahat fares tahmin etmeye yönelik bir machine learning modeli, doğruluğunun değerlendirilir, derleyip tahminlerde bulunmak için kullanılır. Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposu.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:

> [!div class="checklist"]
> * Hazırlama ve verileri anlama
> * Öğrenme işlem hattı oluşturma
> * Yükleme ve dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitme
> * Modeli değerlendirme
> * Kullanım modeli tahminler elde etmek için

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Iris kümelemesi](iris-clustering.md)
