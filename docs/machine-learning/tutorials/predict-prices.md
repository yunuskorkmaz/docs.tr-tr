---
title: 'Öğretici: gerileme kullanarak fiyatları tahmin etme'
description: Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.NET kullanarak bir gerileme modelinin nasıl oluşturulacağı gösterilmektedir.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 27054e28f9a4fa628f0d7348d45528b690d7da83
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281777"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Öğretici: ML.NET ile gerileme kullanarak fiyatları tahmin etme

Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.NET kullanarak bir [gerileme modelinin](../resources/glossary.md#regression) nasıl oluşturulacağı gösterilmektedir.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:
> [!div class="checklist"]
>
> * Verileri hazırlama ve anlama
> * Verileri yükleme ve dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitme
> * Modeli değerlendirme
> * Tahmin için modeli kullanma

## <a name="prerequisites"></a>Ön koşullar

* [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya üzeri ya da visual Studio 2017 sürüm 15,6 veya üzeri, ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "Taxifaretahminini" adlı bir **.NET Core konsol uygulaması** oluşturun.

1. Veri kümesi ve model dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun.

1. **Microsoft.ml** NuGet paketini yükler:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    **Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, **Araştır** sekmesini seçin, **Microsoft.ml**için arama yapın, listeden paketi seçin ve sonra da **Install** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin. **Microsoft. ml. FastTree** NuGet paketi için de aynısını yapın.

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

1. [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri kümelerini indirin ve önceki adımda oluşturduğunuz *veri* klasörüne kaydedin. Machine Learning modelini eğitmek için bu veri kümelerini kullanıyoruz ve sonra modelin ne kadar doğru olduğunu değerlendirin. Bu veri kümeleri başlangıçta [NYC TLC TAXI seyahat veri kümesinden](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)alınır.

1. **Çözüm Gezgini**,. csv dosyalarının her birine sağ tıklayın \* ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

1. **taxi-fare-train.csv** veri kümesini açın ve ilk satırdaki sütun başlıklarına bakın. Her sütuna göz atın. Verileri anlayın ve hangi sütunların **Özellikler** olduğunu ve hangisinin **etiket**olduğunu belirleyin.

`label`Tahmin etmek istediğiniz sütundur. `Features`, Modeli tahmin etmek için size izin verdiğiniz girişlerdir `Label` .

Belirtilen veri kümesi şu sütunları içerir:

* **vendor_id:** Taxı satıcısının KIMLIĞI bir özelliktir.
* **rate_code:** Taxı seyahati 'ın hız türü bir özelliktir.
* **passenger_count:** Seyahat üzerindeki pascuların sayısı bir özelliktir.
* **trip_time_in_secs:** Seyahati için geçen süre. Seyahat tamamlanmadan önce seyahat tarifeli havayolu tahmin etmek istiyorsunuz. Bu sırada, seyahati ne kadar süreyle yapılacağını bilemezsiniz. Bu nedenle, seyahat süresi bir özellik değildir ve bu sütunu modelden dışlayabilirsiniz.
* **trip_distance:** Seyahat uzaklığı bir özelliktir.
* **payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.
* **fare_amount:** Ödenen toplam TAXI tarifeli havayolu etikettir.

## <a name="create-data-classes"></a>Veri sınıfları oluşturma

Giriş verileri ve tahminleri için sınıflar oluşturun:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *TaxiTrip.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.
1. Aşağıdaki `using` yönergeleri yeni dosyaya ekleyin:

   [!code-csharp[AddUsings](./snippets/predict-prices/csharp/TaxiTrip.cs#1 "Add necessary usings")]

Mevcut sınıf tanımını kaldırın ve iki sınıfa `TaxiTrip` ve `TaxiTripFarePrediction` *TaxiTrip.cs* dosyasına sahip olan aşağıdaki kodu ekleyin:

[!code-csharp[DefineTaxiTrip](./snippets/predict-prices/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip`, giriş veri sınıfıdır ve veri kümesi sütunlarının her biri için tanımlar içerir. <xref:Microsoft.ML.Data.LoadColumnAttribute>Veri kümesindeki kaynak sütunlarının dizinlerini belirtmek için özniteliğini kullanın.

`TaxiTripFarePrediction`Sınıfı tahmin edilen sonuçları temsil eder. Özniteliği uygulanmış tek bir float alanı vardır `FareAmount` `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> . Regresyon görevi söz konusu olduğunda, **puan** sütunu tahmin edilen etiket değerlerini içerir.

> [!NOTE]
> `float`Giriş ve tahmin veri sınıflarında kayan nokta değerlerini göstermek için türünü kullanın.

### <a name="define-data-and-model-paths"></a>Veri ve model yollarını tanımlama

Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:

[!code-csharp[AddUsings](./snippets/predict-prices/csharp/Program.cs#1 "Add necessary usings")]

Veri kümelerine sahip dosyaların yollarını tutmak için üç alan oluşturmanız ve modelin kaydedileceği dosyanın olması gerekir:

* `_trainDataPath`modeli eğitmek için kullanılan veri kümesiyle dosyanın yolunu içerir.
* `_testDataPath`modeli değerlendirmek için kullanılan veri kümesiyle dosyanın yolunu içerir.
* `_modelPath`eğitilen modelin depolandığı dosyanın yolunu içerir.

`Main`Bu yolları ve değişkeni belirtmek için yönteminin hemen üstüne aşağıdaki kodu ekleyin `_textLoader` :

[!code-csharp[InitializePaths](./snippets/predict-prices/csharp/Program.cs#2 "Define variables to store the data file paths")]

Tüm ML.NET işlemleri [Mlcontext sınıfında](xref:Microsoft.ML.MLContext)başlar. Başlatma `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilecek yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal olarak da benzerdir `DBContext` .

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

`Console.WriteLine("Hello World!")` `Main` Yöntemi bildirmek ve başlatmak için yöntemindeki satırı aşağıdaki kodla değiştirin `mlContext` :

[!code-csharp[CreateMLContext](./snippets/predict-prices/csharp/Program.cs#3 "Create the ML Context")]

`Main`Yöntemi çağırmak için yöntemi içindeki sonraki kod satırı olarak aşağıdakini ekleyin `Train` :

[!code-csharp[Train](./snippets/predict-prices/csharp/Program.cs#5 "Train your model")]

`Train()`Yöntemi aşağıdaki görevleri yürütür:

* Verileri yükler.
* Verileri ayıklar ve dönüştürür.
* Modeli TRAIN.
* Modeli döndürür.

`Train`Yöntemi modeli TRAIN. Aşağıdaki kodu kullanarak bu yöntemi hemen aşağıda oluşturun `Main` :

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Verileri yükleme ve dönüştürme

ML.NET, sayısal veya metin tablolu verileri tanımlamaya yönelik esnek ve verimli bir yöntem olarak [ıdataview sınıfını](xref:Microsoft.ML.IDataView) kullanır. `IDataView`metin dosyalarını veya gerçek zamanlı olarak yükleyebilirsiniz (örneğin, SQL veritabanı veya günlük dosyaları). Aşağıdaki kodu yönteminin ilk satırı olarak ekleyin `Train()` :

[!code-csharp[LoadTrainData](./snippets/predict-prices/csharp/Program.cs#6 "loading training dataset")]

Taxı seyahat tarifeli havayolu tahmin etmek istediğiniz gibi, `FareAmount` `Label` Bu sütun tahmin ettiğiniz (modelin çıktısı) olur. `CopyColumnsEstimator`Kopyalamak için dönüştürme sınıfını kullanın `FareAmount` ve aşağıdaki kodu ekleyin:

[!code-csharp[CopyColumnsEstimator](./snippets/predict-prices/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

Modeli gösteren algoritma **sayısal** Özellikler gerektirir, bu nedenle kategorik verileri ( `VendorId` , `RateCode` ve `PaymentType` ) değerlerini sayılara ( `VendorIdEncoded` ,, `RateCodeEncoded` ve `PaymentTypeEncoded` ) dönüştürmeniz gerekir. Bunu yapmak için, sütunların her birinde farklı değerlere farklı sayısal anahtar değerleri atayan [Onehotencodingtransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) dönüştürme sınıfını kullanın ve aşağıdaki kodu ekleyin:

[!code-csharp[OneHotEncodingEstimator](./snippets/predict-prices/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

Veri hazırlığının son adımı, tüm özellik sütunlarını, dönüştürme sınıfını kullanarak **Özellikler** sütunuyla birleştirir `mlContext.Transforms.Concatenate` . Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler. Şu kodu ekleyin:

[!code-csharp[ColumnConcatenatingEstimator](./snippets/predict-prices/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Bu sorun, New York şehrinde bir TAXI seyahat tarifeli havayolu tahmin etmeye yönelik olarak tasarlanmıştır. İlk bakışta, yalnızca seyahat mesafesini temel alan görünebilir. Ancak, New York 'taki TAXI satıcıları, ek Pastörler veya nakit yerine kredi kartıyla ödeme yapma gibi diğer faktörlere göre farklılık gösteren ücretler ücretlendirir. Veri kümesindeki diğer faktörlere bağlı olarak gerçek bir değer olan fiyat değerini tahmin etmek istiyorsunuz. Bunu yapmak için bir [gerileme](../resources/glossary.md#regression) makine öğrenimi görevi seçersiniz.

Aşağıdaki kod satırı olarak aşağıdakini ekleyerek [Fasttreeregressiontrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) Machine Learning görevini veri dönüştürme tanımlarına ekleyin `Train()` :

[!code-csharp[FastTreeRegressionTrainer](./snippets/predict-prices/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Modeli eğitme

`dataview`Aşağıdaki kod satırını yönteme ekleyerek modeli eğitimine sığdırın ve eğitilen modeli döndürün `Train()` :

[!code-csharp[TrainModel](./snippets/predict-prices/csharp/Program.cs#11 "Train the model")]

[Fit ()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.

Aşağıdaki kod satırıyla eğitilen modeli döndürün `Train()` :

[!code-csharp[ReturnModel](./snippets/predict-prices/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Daha sonra, kalite güvencesi ve doğrulama için test verilerinize ait model performansınızı değerlendirin. `Evaluate()`Aşağıdaki kodla hemen sonra yöntemi oluşturun `Train()` :

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate`Yöntemi aşağıdaki görevleri yürütür:

* Test veri kümesini yükler.
* Regresyon Değerlendiricisi oluşturur.
* Modeli değerlendirir ve ölçümler oluşturur.
* Ölçümleri görüntüler.

`Main`Aşağıdaki kodu kullanarak yöntem çağrısının hemen altına, yönteminden yeni yönteme bir çağrı ekleyin `Train` :

[!code-csharp[CallEvaluate](./snippets/predict-prices/csharp/Program.cs#14 "Call the Evaluate method")]

[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) yöntemini kullanarak test veri kümesini yükleyin. Yöntemine aşağıdaki kodu ekleyerek bu veri kümesini bir kalite denetimi olarak kullanarak modeli değerlendirin `Evaluate` :

[!code-csharp[LoadTestDataset](./snippets/predict-prices/csharp/Program.cs#15 "Load the test dataset")]

Ardından, `Test` aşağıdaki kodu öğesine ekleyerek verileri dönüştürün `Evaluate()` :

[!code-csharp[PredictWithTransformer](./snippets/predict-prices/csharp/Program.cs#16 "Predict using the Transformer")]

[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesi giriş satırları için tahminleri yapar.

`RegressionContext.Evaluate`Yöntemi, `PredictionModel` belirtilen veri kümesini kullanarak için kalite ölçümlerini hesaplar. <xref:Microsoft.ML.Data.RegressionMetrics>Regresyon değerlendiricileri tarafından hesaplanan genel ölçümleri içeren bir nesne döndürür.

Modelin kalitesini belirlemede bunları göstermek için öncelikle ölçümleri almanız gerekir. Aşağıdaki kodu yönteminin sonraki satırı olarak ekleyin `Evaluate` :

[!code-csharp[ComputeMetrics](./snippets/predict-prices/csharp/Program.cs#17 "Compute Metrics")]

Tahmin kümesine sahip olduktan sonra, tahmin edilen değerleri test veri kümesindeki gerçek ile karşılaştıran ve modelin nasıl çalıştığı hakkında ölçümler döndüren [değerlendir ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) yöntemi, modeli değerlendirir `Labels` .

Modeli değerlendirmek ve değerlendirme ölçümlerini oluşturmak için aşağıdaki kodu ekleyin:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RKARE](../resources/glossary.md#coefficient-of-determination) , regresyon modellerinin başka bir değerlendirme ölçümdür. RKARE 0 ile 1 arasında değerleri alır. Daha yakın değeri 1 ' dir, model daha iyidir. `Evaluate`RKARE değerini göstermek için yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[DisplayRSquared](./snippets/predict-prices/csharp/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) , regresyon modelinin değerlendirme ölçümlerinden biridir. Bunun ne kadar küçük olması, modelin ne kadar iyi olduğu. `Evaluate`RMS değerini göstermek için yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[DisplayRMS](./snippets/predict-prices/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Tahmin için modeli kullanma

`TestSinglePrediction`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `Evaluate` :

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

`TestSinglePrediction`Yöntemi aşağıdaki görevleri yürütür:

* Test verileri için tek bir açıklama oluşturur.
* Sınama verilerine göre tarifeli havayolu miktarını tahmin eder.
* Raporlama için test verilerini ve tahminleri birleştirir.
* Tahmin edilen sonuçları görüntüler.

`Main`Aşağıdaki kodu kullanarak yöntem çağrısının hemen altına, yönteminden yeni yönteme bir çağrı ekleyin `Evaluate` :

[!code-csharp[CallTestSinglePrediction](./snippets/predict-prices/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

`PredictionEngine`Aşağıdaki kodu öğesine ekleyerek tarifeli havayolu tahmin etmek için kullanın `TestSinglePrediction()` :

[!code-csharp[MakePredictionEngine](./snippets/predict-prices/csharp/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, `PredictionEnginePool` [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uygulamanız genelinde kullanılacak nesneleri oluşturan hizmetini kullanın. [ `PredictionEnginePool` ASP.NET Core Web API 'sinde kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.

> [!NOTE]
> `PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.

Bu öğretici, bu sınıf içinde bir test yolculuğu kullanır. Daha sonra, modelle denemeler yapmak için başka senaryolar da ekleyebilirsiniz. Bir örneği oluşturarak eğitilen modelin Maliyet tahminini test etmek için bir seyahat ekleyin `TestSinglePrediction()` `TaxiTrip` :

[!code-csharp[PredictionData](./snippets/predict-prices/csharp/Program.cs#23 "Create test data for single prediction")]

Sonra, tarifeli havayolu öğesini bir taksi seyahat verisinin tek bir örneğine göre tahmin edin ve `PredictionEngine` Aşağıdaki kod satırları yöntemine ekleyerek bunu öğesine geçirin `TestSinglePrediction()` :

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#24 "Create a prediction of taxi fare")]

[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, verilerin tek bir örneğini tahmin eder.

Belirtilen seyahati için öngörülen tarifeli havayolu 'yi göstermek için aşağıdaki kodu `TestSinglePrediction` yöntemine ekleyin:

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#25 "Display the prediction.")]

Test çalışmanıza yönelik tahmini TAXI tarifeli havayolu görmek için programı çalıştırın.

Tebrikler! Artık TAXI seyahat Fares 'yi tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz, doğruluğu değerlendirildi ve tahmine dayalı hale getirmek için kullandınız. Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:

> [!div class="checklist"]
>
> * Verileri hazırlama ve anlama
> * Öğrenme işlem hattı oluşturma
> * Verileri yükleme ve dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitme
> * Modeli değerlendirme
> * Tahmin için modeli kullanma

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Iris kümelemesi](iris-clustering.md)
