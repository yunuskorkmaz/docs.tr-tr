---
title: 'Öğretici: Regresyon kullanarak fiyatları tahmin edin'
description: Bu öğretici fiyatları tahmin etmek için ML.NET kullanarak bir regresyon modeli oluşturmak için nasıl göstermektedir, özellikle, New York taksi ücretleri.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 51cef97178c2dbc6a5b572a7045bdad4bc382ba0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78240993"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Öğretici: ML.NET ile regresyon kullanarak fiyatları tahmin

Bu öğretici fiyatları tahmin etmek için ML.NET kullanarak bir [regresyon modeli](../resources/glossary.md#regression) oluşturmak için nasıl göstermektedir, özellikle, New York taksi ücretleri.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> * Verileri hazırlama ve anlama
> * Verileri yükleme ve dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitme
> * Modeli değerlendirme
> * Öngörüler için modeli kullanma

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "TaxiFarePrediction" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.

1. Veri kümesini ve model dosyalarını depolamak için projenizde *Veri* adlı bir dizin oluşturun.

1. **Microsoft.ML** NuGet Paketini yükleyin:

    **Çözüm Gezgini'nde**projeyi sağ tıklatın ve **NuGet Paketlerini Yönet'i**seçin. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, **Gözat** sekmesini seçin, **Microsoft.ML**arayın, listedeki paketi seçin ve **Yükle** düğmesini seçin. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin. **Microsoft.ML.FastTree** NuGet paketi için aynı şeyi yapın.

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

1. [Taksi-ücret-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [taksi-ücret-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri kümelerini indirin ve bunları bir önceki adımda oluşturduğunuz *Veri* klasörüne kaydedin. Bu veri kümelerini makine öğrenimi modelini eğitmek ve modelin ne kadar doğru olduğunu değerlendirmek için kullanırız. Bu veri setleri aslında [NYC TLC Taksi Gezisi veri kümesinden.](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

1. **Çözüm Gezgini'nde** \*,.csv dosyalarının her birini sağ tıklatın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

1. **Taksi-ücret-train.csv** veri kümesini açın ve ilk satırdaki sütun başlıklarına bakın. Sütunların her birine bir göz atın. Verileri anlayın ve hangi sütunların **özellik** olduğuna ve hangilerinin **etiket**olduğuna karar verin.

Tahmin `label` etmek istediğiniz sütundur. Tanımlanan `Features`girdiler, modeli tahmin etmek için `Label`verdiğiniz girdilerdir.

Sağlanan veri kümesi aşağıdaki sütunları içerir:

* **vendor_id:** Taksi satıcısının kimliği bir özelliktir.
* **rate_code:** Taksi gezisinin fiyat türü bir özelliktir.
* **passenger_count:** Yolculuktaki yolcu sayısı bir özelliktir.
* **trip_time_in_secs:** Yolculuğun aldığı süre. Yolculuk tamamlanmadan önce seyahat ücretini tahmin etmek istiyorsunuz. O anda, yolculuğun ne kadar süreceğini bilemezsin. Bu nedenle, yolculuk süresi bir özellik değildir ve bu sütunu modelden dışlarsınız.
* **trip_distance:** Yolculuk mesafesi bir özelliktir.
* **payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.
* **fare_amount:** Ödenen toplam taksi ücreti etikettir.

## <a name="create-data-classes"></a>Veri sınıfları oluşturma

Giriş verileri ve öngörüler için sınıflar oluşturun:

1. **Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.
1. Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *TaxiTrip.cs*olarak değiştirin. Ardından **Ekle** düğmesini seçin.
1. Yeni dosyaya aşağıdaki `using` yönergeleri ekleyin:

   [!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#1 "Add necessary usings")]

Varolan sınıf tanımını kaldırın ve iki sınıfı `TaxiTrip` `TaxiTripFarePrediction`ve TaxiTrip.cs *dosyasına* aşağıdaki kodu ekleyin:

[!code-csharp[DefineTaxiTrip](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip`giriş veri sınıfıdır ve veri kümesi sütunlarının her biri için tanımlar vardır. Veri <xref:Microsoft.ML.Data.LoadColumnAttribute> kümesindeki kaynak sütunların dizinlerini belirtmek için özniteliği kullanın.

Sınıf, `TaxiTripFarePrediction` öngörülen sonuçları temsil eder. Tek bir float alanı `FareAmount`vardır, `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> uygulanan bir öznitelik ile. Regresyon görevi söz konusu olduğunda, **Puan** sütunu tahmin edilmiş etiket değerlerini içerir.

> [!NOTE]
> Giriş `float` ve tahmin veri sınıflarında kayan nokta değerlerini temsil etmek için türü kullanın.

### <a name="define-data-and-model-paths"></a>Veri ve model yollarını tanımlama

Aşağıdaki ek `using` deyimleri *Program.cs* dosyasının üstüne ekleyin:

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#1 "Add necessary usings")]

Verileri kümeleri ve modeli kaydetmek için dosya ile dosyaların yollarını tutmak için üç alan oluşturmanız gerekir:

* `_trainDataPath`modeli eğitmek için kullanılan veri kümesi ile dosyaya giden yolu içerir.
* `_testDataPath`modeli değerlendirmek için kullanılan veri kümesi ile dosyaya giden yolu içerir.
* `_modelPath`ilgili modelin depolandığı dosyaya giden yolu içerir.

Bu yolları belirtmek ve `Main` `_textLoader` değişken için yöntemin hemen üstüne aşağıdaki kodu ekleyin:

[!code-csharp[InitializePaths](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#2 "Define variables to store the data file paths")]

Tüm ML.NET işlemleri [MLContext sınıfında](xref:Microsoft.ML.MLContext)başlar. İlk `mlContext` başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur. Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.

### <a name="initialize-variables-in-main"></a>Main'deki değişkenleri başlatma

Değişkeni `Console.WriteLine("Hello World!")` `Main` bildirmek ve başlatmak için yöntemdeki satırı `mlContext` aşağıdaki kodla değiştirin:

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#3 "Create the ML Context")]

`Main` Yöntemi çağırmak için yöntemde bir sonraki kod satırı olarak aşağıdakileri `Train` ekleyin:

[!code-csharp[Train](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#5 "Train your model")]

Yöntem `Train()` aşağıdaki görevleri yürütür:

* Verileri yükler.
* Verileri ayıklar ve dönüştürür.
* Modeli eğitir.
* Modeli döndürür.

Yöntem `Train` modeli eğitir. Aşağıdaki kodu kullanarak `Main`bu yöntemi hemen aşağıda oluşturun:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Verileri yükleme ve dönüştürme

ML.NET, sayısal veya metin tabular verileri açıklamanın esnek ve verimli bir yolu olarak [IDataView sınıfını](xref:Microsoft.ML.IDataView) kullanır. `IDataView`metin dosyalarını veya gerçek zamanlı olarak yükleyebilir (örneğin, SQL veritabanı veya günlük dosyaları). `Train()` Yöntemin ilk satırı olarak aşağıdaki kodu ekleyin:

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#6 "loading training dataset")]

Taksi yolculuğu ücretini tahmin etmek `FareAmount` istediğinizde, `Label` sütun tahmin edeceğiniz sütundur (modelin çıktısı). Kopyalamak `CopyColumnsEstimator` `FareAmount`ve aşağıdaki kodu eklemek için dönüşüm sınıfını kullanın:

[!code-csharp[CopyColumnsEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

Modeli eğiten algoritma **sayısal** özellikler gerektirir, bu nedenle kategorik verileri`VendorId`( `RateCode`, `PaymentType`ve )`VendorIdEncoded`değerlerini `RateCodeEncoded`sayılara ( , , ve `PaymentTypeEncoded`) dönüştürmeniz gerekir. Bunu yapmak için, sütunların her birinde farklı değerlere farklı sayısal anahtar değerleri atayan [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) dönüşüm sınıfını kullanın ve aşağıdaki kodu ekleyin:

[!code-csharp[OneHotEncodingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

Veri hazırlamadaki son adım, dönüşüm sınıfını **Features** kullanarak tüm `mlContext.Transforms.Concatenate` özellik sütunlarını Özellikler sütununa dönüştürür. Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler. Aşağıdaki kodu ekleyin:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Bu sorun New York'ta bir taksi gezisi ücret tahmin hakkında. İlk bakışta, sadece kat edilen mesafeye bağlı gibi görünebilir. Ancak, New York'taki taksi satıcıları ek yolcular veya nakit yerine kredi kartı ile ödeme gibi diğer faktörler için değişen tutarlar ücret. Veri kümesindeki diğer etkenlere bağlı olarak gerçek bir değer olan fiyat değerini tahmin etmek istiyorsunuz. Bunu yapmak için, bir [regresyon](../resources/glossary.md#regression) makinesi öğrenme görevi seçin.

[FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) makine öğrenme görevini veri dönüştürme tanımlarına aşağıdaki kodu ekleyerek `Train()`ekleyin:

[!code-csharp[FastTreeRegressionTrainer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Modeli eğitme

Modele eğitime `dataview` uygun hale getirin ve yönteme aşağıdaki `Train()` kod satırını ekleyerek eğitilmiş modeli döndürün:

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#11 "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitir.

`Train()` Yöntemde aşağıdaki kod satırı ile eğitilmiş modeli döndürün:

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Ardından, kalite güvencesi ve doğrulama için model performansınızı test verilerinizle değerlendirin. `Evaluate()` Yöntemi aşağıdaki kodla `Train()`hemen sonra oluşturun:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

Yöntem `Evaluate` aşağıdaki görevleri yürütür:

* Test veri kümesini yükler.
* Regresyon değerlendiricioluşturur.
* Modeli değerlendirir ve ölçümler oluşturur.
* Ölçümleri görüntüler.

Aşağıdaki kodu `Main` kullanarak, yöntem çağrısının `Train` hemen altında, yöntemden yeni yönteme çağrı ekleyin:

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#14 "Call the Evaluate method")]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) yöntemini kullanarak test veri kümesini yükleyin. Yönteme aşağıdaki kodu ekleyerek bu veri kümesini kalite `Evaluate` denetimi olarak kullanarak modeli değerlendirin:

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#15 "Load the test dataset")]

Ardından, aşağıdaki `Test` kodu ekleyerek verileri `Evaluate()`dönüştürün:

[!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#16 "Predict using the Transformer")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesi giriş satırları için öngörüler yapar.

Yöntem, `RegressionContext.Evaluate` belirtilen veri kümesini `PredictionModel` kullanarak kalite ölçümlerini hesaplar. Regresyon değerlendiriciler tarafından hesaplanan genel ölçümleri içeren bir <xref:Microsoft.ML.Data.RegressionMetrics> nesne döndürür.

Modelin kalitesini belirlemek için bunları görüntülemek için önce ölçümleri almanız gerekir. `Evaluate` Yöntemde sonraki satır olarak aşağıdaki kodu ekleyin:

[!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#17 "Compute Metrics")]

Tahmin kümesini aldıktan sonra, Tahmin edilen değerleri test veri kümesindeki gerçek `Labels` değerlerle karşılaştıran ve modelin nasıl performans gösterdiğine ilişkin ölçümleri döndüren modeli [değerlendirin.](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A)

Modeli değerlendirmek ve değerlendirme ölçümlerini üretmek için aşağıdaki kodu ekleyin:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) regresyon modellerinin başka bir değerlendirme ölçüsüdür. RSquared 0 ile 1 arasındaki değerleri alır. Değeri 1'e ne kadar yakınsa, model o kadar iyi. RSquared değerini `Evaluate` görüntülemek için yönteme aşağıdaki kodu ekleyin:

[!code-csharp[DisplayRSquared](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#18 "Display the RSquared metric.")]

[RMS,](../resources/glossary.md#root-of-mean-squared-error-rmse) regresyon modelinin değerlendirme ölçümlerinden biridir. Ne kadar düşükse, model o kadar iyi olur. RMS değerini görüntülemek `Evaluate` için yönteme aşağıdaki kodu ekleyin:

[!code-csharp[DisplayRMS](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Öngörüler için modeli kullanma

Yöntemden `TestSinglePrediction` `Evaluate` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

Yöntem `TestSinglePrediction` aşağıdaki görevleri yürütür:

* Test verilerinin tek bir yorumunu oluşturur.
* Test verilerine göre ücret tutarını tahmin eder.
* Raporlama için test verilerini ve öngörüleri birleştirir.
* Öngörülen sonuçları görüntüler.

Aşağıdaki kodu `Main` kullanarak, yöntem çağrısının `Evaluate` hemen altında, yöntemden yeni yönteme çağrı ekleyin:

[!code-csharp[CallTestSinglePrediction](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

Aşağıdaki `PredictionEngine` kodu ekleyerek ücreti tahmin etmek `TestSinglePrediction()`için kullanın:

[!code-csharp[MakePredictionEngine](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir. Tek dişli veya prototip ortamlarda kullanılabilir. Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın. ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.

> [!NOTE]
> `PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.

Bu öğretici, bu sınıf içinde bir test gezisi kullanır. Daha sonra modelle deneme yapmak için başka senaryolar ekleyebilirsiniz. Bir örnek oluşturarak `TestSinglePrediction()` yöntemde maliyet eğitimli modelin tahmin test `TaxiTrip`etmek için bir gezi ekleyin:

[!code-csharp[PredictionData](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#23 "Create test data for single prediction")]

Ardından, taksi yolculuğu verilerinin tek bir örneğine `PredictionEngine` göre ücreti tahmin edin ve yöntemde bir `TestSinglePrediction()` sonraki kod satırları olarak aşağıdakileri ekleyerek bu ücreti iletin:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#24 "Create a prediction of taxi fare")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri örneği üzerinde bir tahminde bulunur.

Belirtilen seyahatin öngörülen ücretini görüntülemek için `TestSinglePrediction` yönteme aşağıdaki kodu ekleyin:

[!code-csharp[Predict](~/samples/snippets/machine-learning/TaxiFarePrediction/csharp/Program.cs#25 "Display the prediction.")]

Test örneğiniz için öngörülen taksi ücretini görmek için programı çalıştırın.

Tebrikler! Şimdi başarılı taksi yolculuk ücretleri tahmin etmek için bir makine öğrenme modeli inşa ettik, doğruluğunu değerlendirdi, ve tahminler yapmak için kullanılır. Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:

> [!div class="checklist"]
>
> * Verileri hazırlama ve anlama
> * Öğrenme ardışık bir yol oluşturma
> * Verileri yükleme ve dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitme
> * Modeli değerlendirme
> * Öngörüler için modeli kullanma

Daha fazla bilgi edinmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Iris kümelemesi](iris-clustering.md)
