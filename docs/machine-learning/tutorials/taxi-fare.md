---
title: New York ücreti fares (regresyon) tahmin etmek için ML.NET kullanın
description: Regresyon senaryoda ML.NET kullanmayı öğrenin.
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 690e39dcbd02d81b8d4afe918a74795aa02f7fc6
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314971"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>Öğretici: Kullanım ML.NET New York ücreti fares (regresyon) tahmin etmek için

> [!NOTE]
> Bu konuda şu anda önizlemede değil, ML.NET başvuruyor ve malzeme değiştirilebilir olabilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu öğretici ML.NET oluşturmak için nasıl kullanılacağı gösterilmektedir bir [regresyon modeli](../resources/glossary.md#regression) New York şehrinde ücreti fares tahmin etmeye yönelik.

Bu öğreticide, bilgi nasıl yapılır:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenme görevini seçin
> * Hazırlama ve verileri anlamak
> * Öğrenme işlem hattı oluşturma
> * Yük ve veri dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitmek
> * Modeli değerlendirin
> * Model için tahminde kullanın

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15,6 veya üstü](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core platformlar arası geliştirme" iş yükü ile.

## <a name="understand-the-problem"></a>Sorunu anlama

Bu sorunu kalmaz **bir ücreti ücreti tahmin etmeye seyahat New York şehirde**. İlk bakışta, seyahat uzaklığı üzerinde yalnızca bağımlı görünebilir. Ancak, New York'taki ücreti satıcıları ek yolcu veya nakit yerine bir kredi kartıyla ödeme gibi diğer faktörlere değişen tutarlarının gider.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenme görevini seçin

Ücreti ücreti tahmin etmek için önce uygun makine öğrenme görevi seçin. Gerçek değer (Fiyat gösteren bir double) kümesindeki diğer faktörleri temel tahmin etmek için aramaktadır. Seçtiğiniz bir [ **regresyon** ](../resources/glossary.md#regression) görev.

## <a name="create-a-console-application"></a>Bir konsol uygulaması oluşturun

1. Visual Studio 2017'ni açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusu, "TaxiFarePrediction" yazın ve ardından **Tamam** düğmesi.

2. Adlı bir dizin oluşturun *veri* projenize veri kümesi dosyaları kaydetmek için:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve seçin **Ekle** > **yeni klasör**. "Data" yazın ve Enter tuşuna basın.

3. Yükleme **Microsoft.ML NuGet paketi**:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve seçin **NuGet paketlerini Yönet**. Paket, kaynak olarak seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulünü** iletişim varsa, listelenen paketler için lisans koşullarını kabul etmiş olursunuz.

## <a name="prepare-and-understand-the-data"></a>Hazırlama ve verileri anlamak

1. Karşıdan [ücreti ücreti train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [ücreti ücreti test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri ayarlar ve bunları kaydetmek *veri* önceki adımda oluşturduğunuz klasör. Machine learning modelini eğitmek ve ne kadar doğru modeldir değerlendirmek için bu veri kümeleri kullanırız. Bu veri kümeleri başlangıçta arasındadır [NYC TLC ücreti seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

2. İçinde **Çözüm Gezgini**, her biri sağ \*.csv dosyaları ve seçin **özellikleri**. Altında **Gelişmiş**, değerini değiştirme **çıktı dizinine Kopyala** için **her zaman**.

3. Açık **ücreti ücreti train.csv** veri kümesi ve sütun üst bilgileri ilk satırda bakın. Her sütun göz atın. İçin verileri anlamak ve hangi sütunların olduğuna karar **özellikleri** ve hangisinin **etiket**.

**Etiket** tahmin etmek istediğiniz sütun tanımlayıcısıdır. Tanımlanan **özellikleri** etiketi tahmin etmek için kullanılır.

Sağlanan veri kümesi şu sütunları içerir:

* **vendor_id:** ücreti satıcı kimliği bir özelliktir.
* **rate_code:** ücreti seyahat hızı türünü bir özelliktir.
* **passenger_count:** seyahat üzerinde yolcu sayısı bir özelliktir.
* **trip_time_in_secs:** süreyi seyahat sürdü. Seyahat tamamlanmadan önce Seyahat Ücreti tahmin etmek istediğiniz. Bu ne kadar süreyle seyahat tanımadığınız dakika sürer. Bu nedenle, dönüş süresi bir özellik değildir ve bu sütunu modelden hariç.
* **trip_distance:** seyahat mesafesini bir özelliktir.
* **payment_type:** ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.
* **fare_amount:** Ücretli toplam ücreti ücreti etiketidir.

## <a name="create-data-classes"></a>Veri sınıfları oluşturma

Giriş verilerini ve tahminleri için sınıflar oluşturun:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TaxiTrip.cs*. Ardından, seçin **Ekle** düğmesi.
1. Aşağıdakileri ekleyin `using` deyimleri yeni dosya için:

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Varolan sınıf tanımına kaldırmak ve iki sınıf olan aşağıdaki kodu ekleyin `TaxiTrip` ve `TaxiTripFarePrediction`, *TaxiTrip.cs* dosyası:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` giriş verisi sınıfı olup veri kümesi sütunların her biri için tanımları içerir. Kullanım [sütun](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) veri kümesinde kaynak sütunların dizinlerini belirtmek için özniteliği.

`TaxiTripFarePrediction` Sınıfı, tahmin edilen sonuçları göstermek için kullanılır. Tek bir kayan nokta vardır (`FareAmount`) ile alan bir `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) özniteliği uygulanmıştır. **Puan** ML.NET özel sütununda bir sütundur. Model tahmin edilen değerler bu sütuna çıkarır.

## <a name="define-data-and-model-paths"></a>Veriler ve model yolları tanımla

Geri dönerek *Program.cs* dosya ve veri kümeleri ile dosyalara yolları tutun ve model kaydetmek için üç genel sabitler oluşturun:

* `_datapath` veri modeli eğitmek için kullanılan yolu vardır.
* `_testdatapath` veri modeli değerlendirmek için kullanılan yolu vardır.
* `_modelpath` Eğitim modeli depolandığı yolu vardır.

Satırının sağındaki aşağıdaki kodu ekleyin `Main` yöntemi bu yollarını belirtin:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

## <a name="create-a-learning-pipeline"></a>Öğrenme işlem hattı oluşturma

Aşağıdaki ek ekleyin `using` deyimleri üstüne *Program.cs* dosyası:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

İçinde `Main`, yerine `Console.WriteLine("Hello World!")` aşağıdaki kod ile:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` Yöntemi eğitir modeli. Bu yöntem oluşturma yalnızca aşağıda `Main`, aşağıdaki kodu kullanarak:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

Öğrenme ardışık düzen tüm veri ve algoritma modeli eğitmek için gerekli yükler. Aşağıdaki kodu ekleyin `Train` yöntemi:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a>Yükleme ve dönüştürme verileri

Öğrenme ardışık düzen gerçekleştirir ilk adımı verileri eğitim veri kümesinden yüklüyor. Örneğimizde, eğitim veri kümesi metin dosyasında tarafından tanımlanan bir yol ile depolanan `_datapath` sabit. Bu dosyayı sütun adları üstbilgiyle içerdiğinden, verileri yüklenirken ilk satırın yoksayılacak. Dosyadaki sütunları virgülle ayrılmış (","). Aşağıdaki kodu ekleyin `Train` yöntemi:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

Sonraki adımlarda size sütunlara tanımlanan adlarıyla başvurmak `TaxiTrip` sınıfı.

Ne zaman model eğitilmiş ve hesaplanan değerler **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir. Ücreti Seyahat Ücreti tahmin etmek istiyoruz gibi kopyalamak `FareAmount` sütununa **etiket** sütun. Bunu yapmak için kullanmak <xref:Microsoft.ML.Transforms.ColumnCopier> ve aşağıdaki kodu ekleyin:

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

Model eğitir algoritması **sayısal** kategorik veri dönüştürme böylece özellikleri (`VendorId`, `RateCode`, ve `PaymentType`) numaraları değerlere. Bunu yapmak için kullanmak <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, hangi farklı sayısal atar anahtar sütunların her biri farklı değerler değerlerini ve aşağıdaki kodu ekleyin:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak <xref:Microsoft.ML.Transforms.ColumnConcatenator> dönüştürme sınıfı. Bu adım bir öğrenen yalnızca özelliklerinden işlerken gereklidir **özellikleri** sütun. Aşağıdaki kodu ekleyin:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Dikkat `TripTime` karşılık gelen sütun `trip_time_in_secs` veri kümesi dosyasındaki sütun dahil değildir. Zaten bir yararlı tahmin özelliği değil belirledi.

> [!NOTE]
> Bu adımları başarılı yürütme için yukarıda belirtilen sırada ardışık düzene eklenmelidir.

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Veri ardışık düzenine eklemek ve doğru giriş biçimine dönüştürme sonra bir öğrenme algoritması seçin (**öğrenen**). Öğrenen model eğitir. Seçtiğiniz bir **regresyon görev** Bu sorun için bu nedenle eklediğiniz bir <xref:Microsoft.ML.Trainers.FastTreeRegressor> ML.NET tarafından sağlanan regresyon öğrencileriyle biri öğrenen.

<xref:Microsoft.ML.Trainers.FastTreeRegressor> Gradyan artırmanın öğrenen kullanır. Gradyan artırmanın regresyon sorunları için tekniği öğrenme bir makinedir. Her regresyon ağaç step-wise bir şekilde oluşturur. Her adım hata ölçmek ve sonraki düzeltmek için önceden tanımlanmış kaybı işlevi kullanır. Gerçekte bir ensemble zayıf tahmin modellerin olduğu bir tahmin modeli sonucudur. Gradyan artırma hakkında daha fazla bilgi için bkz: [Boosted karar ağacı regresyon](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Aşağıdaki kodu ekleyin `Train` önceki adımda eklenen veri işleme koddan yöntemi:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Yukarıdaki adımların tümünü tek tek deyimleri ardışık düzenine eklenen ancak C# oluşturma ve ardışık düzeni başlatan basitleştiren bir kullanışlı koleksiyonu başlatma sözdizimine sahip. Şimdiye kadar eklediğiniz kod değiştirin `Train` aşağıdaki kod ile yöntemi:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Modeli eğitmek

Modeli eğitmek için son adımdır bakın. Bu noktaya kadar ardışık düzeninde bir şey çalıştırıldı. `pipeline.Train<TInput, TOutput>` Yöntemi üreten bir örnekte geçen modeli `TInput` yazın ve bir örneğini çıkaran `TOutput` türü. Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

Ve bu kadar! Başarıyla bir makine ücreti fares NYC, tahmin modeli öğrenme eğitilmiş. Şimdi şimdi ne kadar doğru modeli olduğunu anlamak için göz atın ve ücreti ücreti değerleri tahmin etmek için kullanmayı öğrenin.

### <a name="save-the-model"></a>Modeli kaydedin

Sonraki adıma geçmeden önce modeli bir .zip dosyasına aşağıdaki kodu sonunda ekleyerek kaydedin `Train` yöntemi:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Ekleme `await` ifadesine `model.WriteAsync` çağrı anlamına `Train` yöntemi bir görev döndüren bir zaman uyumsuz yöntem değiştirilmesi gerekir. İmzasını değiştirmek `Train` aşağıdaki kodda gösterildiği gibi:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Dönüş türünü değiştirme `Train` yöntemi anlamına gelir eklemek zorunda bir `await` çağıran kodu için `Train` içinde `Main` yöntemini aşağıdaki kodda gösterildiği gibi değiştirin:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Kullanarak `await` içinde `Main` yöntemi anlamına gelir `Main` yöntemi olmalıdır `async` değiştiricisini ve return bir `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Ayrıca aşağıdaki eklemeniz gerekir `using` deyimini dosyanın üst:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Çünkü `async Main` yöntemi, C# 7.1 eklenen özelliğidir ve C# 7.0 projesinin varsayılan dil sürümünü ise, C# 7.1 veya üzeri dil sürümü değiştirmeniz gerekir. Bunu yapmak için proje düğümüne sağ tıklayın **Çözüm Gezgini** seçip **özellikleri**. Seçin **yapı** sekmesinde ve seçin **Gelişmiş** düğmesi. Açılır listede seçin **C# 7.1** (veya daha yüksek bir sürüm). Seçin **Tamam** düğmesi.

## <a name="evaluate-the-model"></a>Modeli değerlendirin

Değerlendirme ne kadar iyi etiket değerlerini modeli tahmin denetleme işlemidir. Model, modeli eğitmek için kullanılmamış veriler üzerinde iyi tahminleri yapar önemlidir. Bu öğreticide yapılır bunu yapmanın bir yolu tren verileri bölün ve veri kümelerini, test için aynıdır. Tren veri modeli eğittiğimize göre ne kadar iyi test verileri üzerindeki işlevini görebilirsiniz.

Geri dönerek `Main` yöntemi çağrısı altına aşağıdaki kodu ekleyin `Train`yöntemi:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate` Yöntemi modeli değerlendirir. Bu yöntem oluşturmak için aşağıdaki aşağıdaki kodu ekleyin `Train` yöntemi:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Aşağıdaki kodu ekleyin `Evaluate` test verilerinin Kurulum yükleme yöntemi:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Modeli değerlendirin ve değerlendirme ölçümleri üretmek için aşağıdaki kodu ekleyin:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) regresyon modeli değerlendirme ölçümlerini biridir. Daha az olduğundan, daha iyi modelidir. Aşağıdaki kodu ekleyin `Evaluate` yöntemi RMS değerini görüntülemek için:

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

[RSquared](../resources/glossary.md#coefficient-of-determination) bir regresyon modelini başka bir değerlendirme ölçümüdür. RSquared değer 0 ile 1 arasında bir değer alır. Yakınsa değeri 1'e daha iyi modeldir olduğu. Aşağıdaki kodu ekleyin `Evaluate` yöntemi RSquared değerini görüntülemek için:

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Model için tahminde kullanın

Ardından, model düzgün çalıştığından emin olmak için kullanabileceğiniz merkezi test senaryoları için bir sınıf oluşturun:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestTrips.cs*. Ardından, seçin **Ekle** düğmesi.
1. Sınıfı aşağıdaki örnekte gibi statik olarak değiştirin:

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

Bu öğretici, bu sınıf içinde bir test seyahat kullanır. Daha sonra modelle denemek için diğer senaryolar ekleyebilirsiniz. Aşağıdaki kodu ekleyin `TestTrips` sınıfı:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

Bu seyahat 's gerçek ücreti 29.5 ' dir. Model ücreti tahmin etmek gibi bir yer tutucu olarak 0'ı kullanın.

Belirtilen Seyahat Ücreti tahmin etmek için geri dönüp *Program.cs* dosya ve aşağıdaki kodu ekleyin `Main` yöntemi:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Test çalışması için tahmin edilen ücreti ücreti görmek için programı çalıştırın.

Tebrikler! Şimdi başarıyla ücreti seyahat fares tahmin etmeye yönelik bir machine learning modelini yerleşik, doğruluğunu değerlendirilir ve tahminleri yapmak için kullanılır. Bu öğreticinin için kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) deposu.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, öğrenilen nasıl yapılır:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenme görevini seçin
> * Hazırlama ve verileri anlamak
> * Öğrenme işlem hattı oluşturma
> * Yük ve veri dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitmek
> * Modeli değerlendirin
> * Model için tahminde kullanın

Bilgi almaya devam etmek ve daha fazla örneklerini bulmak için GitHub depomuzda denetleyin.
> [!div class="nextstepaction"]
> [DotNet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/)
