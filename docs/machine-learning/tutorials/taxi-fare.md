---
title: New York ücreti fares (regresyon) tahmin etmek için ML.NET kullanın
description: Regresyon senaryoda ML.NET kullanmayı öğrenin.
author: aditidugar
ms.author: johalex
ms.date: 06/05/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 048ed1d38408c1ba4901c554cae33d5552c9e303
ms.sourcegitcommit: 5b0802832fb9ad684d34e69b8644a16a5b7c4810
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "35017308"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>Öğretici: Kullanım ML.NET New York ücreti fares (regresyon) tahmin etmek için

> [!NOTE]
> Bu konuda şu anda önizlemede değil, ML.NET başvuruyor ve malzeme değiştirilebilir olabilir. Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu öğretici ML.NET oluşturmak için nasıl kullanılacağı gösterilmektedir bir [regresyon modeli](../resources/glossary.md#regression) New York şehrinde ücreti fares tahmin etmeye yönelik.

Bu öğreticide, bilgi nasıl yapılır:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenme görevini seçin
> * Hazırlama ve verilerinizi anlama
> * Öğrenme işlem hattı oluşturma
> * Yük ve verilerinizi dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitmek
> * Modeli değerlendirin
> * Model için tahminde kullanın

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15,6 veya üstü](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core platformlar arası geliştirme" iş yükü ile.

## <a name="understand-the-problem"></a>Sorunu anlama

Bu sorunu kalmaz **bir ücreti ücreti tahmin etmeye seyahat New York şehirde**. İlk bakışta, seyahat uzaklığı üzerinde yalnızca bağımlı görünebilir. Ancak, New York'taki ücreti satıcıları ek yolcu veya nakit yerine bir kredi kartıyla ödeme gibi diğer faktörlere değişen tutarlarının gider.

## <a name="select-the-appropriate-machine-learning-task"></a>Uygun makine öğrenme görevini seçin

Ücreti ücreti tahmin etmek için önce uygun makine öğrenme görevi seçin. Gerçek değer (Fiyat gösteren bir double) kümesindeki diğer faktörleri temel tahmin etmek için aramaktadır. Seçtiğiniz bir [ **regresyon** ](../resources/glossary.md#regression) görev.

Modeli eğitmek işleminin hangi kümesindeki son ücreti fiyatını tahmin etmeye durumlarda en etkili faktörlerdir tanımlar.

## <a name="create-a-console-application"></a>Bir konsol uygulaması oluşturun

1. Visual Studio 2017'ni açın. Seçin **dosya** > **yeni** > **proje** menü çubuğundan. İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü. Ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusu, "TaxiFarePrediction" yazın ve ardından **Tamam** düğmesi.

2. Adlı bir dizin oluşturun *veri* projenize veri kümesi dosyalarınızı kaydetmek için:

    İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve seçin **Ekle** > **yeni klasör**. "Data" yazın ve Enter tuşuna basın.

3. Yükleme **Microsoft.ML NuGet paketi**:

    Çözüm Gezgini'nde projenizi ve select üzerinde sağ **NuGet paketlerini Yönet**. Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulünü** iletişim varsa, listelenen paketler için lisans koşullarını kabul etmiş olursunuz.

### <a name="prepare-and-understand-your-data"></a>Hazırlama ve verilerinizi anlama

1. Karşıdan [ücreti ücreti train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [ücreti ücreti test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri ayarlar ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör. Ücreti seyahat veri kümesi makine öğrenimi modeline eğitir ve nasıl modelinizi doğrudur değerlendirmek için kullanılır. Bu veri kümeleri başlangıçta arasındadır [NYC TLC ücreti seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

2. Çözüm Gezgini'nde, her biri sağ \*.csv dosyaları ve select **özellikleri**. Altında **Gelişmiş**, değerini değiştirme **çıktı dizinine Kopyala** için **her zaman**.

3. Açık **ücreti ücreti train.csv** veri Kod düzenleyicisinde ayarlama ve sütun üst bilgileri ilk satırda bakın. Her sütun göz atın. İçin verileri anlamak ve hangi sütunların olduğuna karar **özellikleri** ve olduğu **etiket**.

**Etiket** tahmin etmek için çalıştığınız sütun tanımlayıcısıdır. Tanımlanan **özellikleri** etiketi tahmin etmek için kullanılır.

* **vendor_id:** ücreti satıcı kimliği bir özelliktir.
* **rate_code:** ücreti seyahat hızı türünü bir özelliktir.
* **passenger_count:** seyahat üzerinde yolcu sayısı bir özelliktir.
* **trip_time_in_secs:** süreyi seyahat sürdü. Bu tamamlandıktan sonra seyahat kadar gereken süreyi bilemezsiniz. Bu sütunu modelden hariç.
* **trip_distance:** seyahat mesafesini bir özelliktir.
* **payment_type:** ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.
* **fare_amount:** Ücretli toplam ücreti ücreti etiketidir.

### <a name="create-classes-and-define-paths"></a>Sınıflar oluşturma ve yolları tanımla

Aşağıdaki ek ekleyin `using` deyimleri üstüne *Program.cs* dosyası:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

En son indirilen dosyaları yolları tutun ve model kaydetmek için üç genel değişkenler oluşturmanız gerekir:

* `_datapath` veri modeli eğitmek için kullanılan yolu vardır.
* `_testdatapath` veri modeli değerlendirmek için kullanılan yolu vardır.
* `_modelpath` Eğitim modeli depolandığı yolu vardır.

Satırının sağındaki aşağıdaki kodu ekleyin `Main` en son indirilen dosyaları belirtmek için:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Ardından, girdi verileri ve tahminleri için sınıflar oluşturun:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TaxiTrip.cs*. Ardından, seçin **Ekle** düğmesi.
1. Aşağıdakileri ekleyin `using` deyimleri yeni dosya için:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Varolan sınıf tanımına kaldırmak ve iki sınıf olan aşağıdaki kodu ekleyin `TaxiTrip` ve `TaxiTripFarePrediction`, *TaxiTrip.cs* dosyası:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` Giriş veri kümesi sınıfı olup veri kümesi sütunların her biri için tanımları içerir. `TaxiTripFarePrediction` Model eğitilmiş sonra sınıfı tahmin için kullanılır. Tek bir kayan nokta vardır (`FareAmount`) ve bir `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) özniteliği uygulanmıştır.

Şimdi geri dönerek **Program.cs** dosya. İçinde `Main`, yerine `Console.WriteLine("Hello World!")` aşağıdaki kod ile:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` Yöntemi eğitir modelinizi. Bu işlev oluşturmak yalnızca aşağıda `Main`, aşağıdaki kodu kullanarak:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a>Öğrenme işlem hattı oluşturma

Öğrenme ardışık düzen tüm veri ve algoritma modeli eğitmek için gerekli yükler. Aşağıdaki kodu ekleyin `Train()` yöntemi:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a>Yük ve verilerinizi dönüştürme

Ardından, verilerinizi ardışık düzenine yükleyin. İşaret `_datapath` başlangıçta oluşturulması ve .csv dosyasını (,) sınırlayıcıyı belirtin. Aşağıdaki kodu ekleyin `Train()` son adımı yöntemini:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

Alt çizgi, oluşturmakta olduğunuz kod olmadan sütunları başvuracağınız. Kopya `FareAmount` yeni bir sütun sütununa adında "kullanarak etiket" `ColumnCopier()` işlevi. Bu sütun **etiket**.

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

Bazı gerçekleştir **özellik Mühendisliği** böylece machine learning için etkili bir şekilde kullanılabilir verileri dönüştürmek için. Model eğitir algoritması **sayısal** özellikleri kategorik veri dönüştürme (`VendorId`, `RateCode`, ve `PaymentType`) numaraları içine. `CategoricalOneHotVectorizer()` İşlevi değerleri bu sütunların her biri için sayısal anahtar atar. Bu kod ekleyerek, verilerinizi dönüştürmek:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

Veri hazırlama son adımda tüm birleştirir, **özellikleri** bir vektör kullanarak `ColumnConcatenator()` işlevi. Bu gerekli bir adım kolayca özelliklerinizi işlem algoritması yardımcı olur. Aşağıdaki kodu ekleyin:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Dikkat `trip_time_in_secs` sütun dahil değil. Zaten bir yararlı tahmin özelliği değil belirledi.

> [!NOTE]
> Bu adımları başarılı yürütme için yukarıda belirtilen sırada ardışık düzene eklenmelidir.

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Veri ardışık düzenine eklemek ve doğru giriş biçimine dönüştürme sonra bir öğrenme algoritması seçin (**öğrenen**). Öğrenme algoritmasını model eğitir. Seçtiğiniz bir **regresyon görev** Bu sorun için bu nedenle eklediğiniz adlı bir öğrenen `FastTreeRegressor()` yararlanan ardışık düzene **gradyan artırmanın**.

Gradyan artırmanın regresyon sorunları için tekniği öğrenme bir makinedir. Her regresyon ağaç step-wise bir şekilde oluşturur. Her adım hata ölçmek ve sonraki düzeltmek için önceden tanımlanmış kaybı işlevi kullanır. Gerçekte bir ensemble zayıf tahmin modellerin olduğu bir tahmin modeli sonucudur. Gradyan artırma hakkında daha fazla bilgi için bkz: [Boosted karar ağacı regresyon](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Aşağıdaki kodu ekleyin `Train()` son adımda eklediğiniz veri işleme koddan yöntemi:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Yukarıdaki adımların tümünü tek tek deyimleri ardışık düzenine eklenen ancak C# oluşturma ve ardışık düzeni başlatan basitleştiren bir kullanışlı koleksiyonu başlatma sözdizimine sahip. Şimdiye kadar eklediğiniz kod değiştirin `Train()` aşağıdaki kod ile yöntemi:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Modeli eğitmek

Modeli eğitmek için son adımdır bakın. Bu noktaya kadar ardışık düzeninde bir şey çalıştırıldı. `pipeline.Train<T_Input, T_Output>()` İşlev alır önceden tanımlanmış `TaxiTrip` sınıf türü ve çıkış bir `TaxiTripFarePrediction` türü. Bu son parçası, koda ekleme `Train()` işlevi:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

Ve bu kadar! Başarıyla bir makine ücreti fares NYC, tahmin modeli öğrenme eğitilmiş. Şimdi ne kadar doğru modelinizi anlamak ve bunu kullanma konusunda bilgi almak için göz atın.

## <a name="save-the-model"></a>Modeli kaydedin

Sonraki adıma geçmeden önce modelinizi bir .zip dosyasına sonuna aşağıdaki kodu ekleyerek kaydetmek, `Train()` işlevi:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Ekleme `await` ifadesine `model.WriteAsync()` çağrı anlamına `Train()` döndüren bir zaman uyumsuz yöntem yöntemi değiştirilmiş bir `Task`. İmzasını değiştirmek `Train` aşağıdaki kodda gösterildiği gibi:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Dönüş türünü değiştirme `Train` yöntemi anlamına gelir eklemek zorunda bir `await` çağıran kodu için `Train` içinde `Main` yöntemini aşağıdaki kodda gösterildiği gibi değiştirin:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Ekleme bir `await` içinde `Main` yöntemi anlamına gelir `Main` yöntemi olmalıdır `async` değiştiricisini ve return bir `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Ayrıca aşağıdaki eklemeniz gerekir deyimini dosyanın üst kısmında kullanarak:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Çünkü `async Main` yöntemdir C# 7.1 yeni bir özelliktir ve C# 7.0 projesinin varsayılan dil sürümünü ise, C# 7.1 veya üzeri dil sürümü değiştirmeniz gerekir.
Bunu yapmak için proje düğümüne sağ tıklayın **Çözüm Gezgini** seçip **özellikleri**. Seçin **yapı** sekmesinde ve seçin **Gelişmiş** düğmesi. Açılır listede seçin **C# 7.1** (veya daha yüksek bir sürüm). Seçin **Tamam** düğmesi.

## <a name="evaluate-the-model"></a>Modeli değerlendirin

Değerlendirme modeli ne kadar iyi çalıştığı denetleme işlemidir. Modelinizi eğitilmiş zaman, onu kullanmadı veriler üzerinde iyi tahminleri yapar önemlidir. Yapmanın bir yolu tren veri bölerek budur ve Bu öğreticide yaptığınız gibi veri kümeleri, test. Tren veri modeli eğittiğimize göre ne kadar iyi test verileri üzerindeki işlevini görebilirsiniz.

Geri dönerek, `Main` işlev ve çağrının altına aşağıdaki kodu ekleyin `Train()`yöntemi:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate()` İşlevi modelinizi değerlendirir. Bu işlev oluşturma `Train()`. Aşağıdaki kodu ekleyin:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Test verileri kullanarak yük `TextLoader()` işlevi. Aşağıdaki kodu ekleyin `Evaluate()` yöntemi:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Modeli değerlendirin ve ölçümler için üretmek için aşağıdaki kodu ekleyin:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

RMS regresyon sorunları değerlendirmek için bir ölçümüdür. Bu daha düşükse, daha iyi modelinizi. Aşağıdaki kodu ekleyin `Evaluate()` modeliniz için RMS yazdırmak için işlevi.

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

RSquared regresyon sorunları değerlendirmek için başka bir ölçümüdür. RSquared 0 ile 1 arasında bir değer olacaktır. 1, daha iyi olduğunuz yakınsa modelinizi. Aşağıdaki kodu ekleyin `Evaluate()` modeliniz için RSquared değeri yazdırmak için işlevi.

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Model için tahminde kullanın

Ardından, modelinizin doğru şekilde çalıştığından emin olmak için kullanabileceğiniz merkezi test senaryoları için bir sınıf oluşturun:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestTrips.cs*. Ardından, seçin **Ekle** düğmesi.
1. Sınıfı aşağıdaki örnekte gibi statik olarak değiştirin:

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

Bu öğretici, bu sınıf içinde bir test seyahat kullanır. Daha sonra bu örnekle denemek için diğer senaryolar ekleyebilirsiniz. Aşağıdaki kodu ekleyin `TestTrips` sınıfı:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

Bu seyahat 's gerçek ücreti, 29.5 olmakla birlikte bir yer tutucu olarak 0'ı kullanın. Makine öğrenme algoritmasını ücreti tahmin.

Aşağıdaki kodu ekleyin, `Main` işlevi. Modeli kullanarak test `TestTrip` verileri:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Test çalışması için tahmin edilen ücreti ücreti görmek için programı çalıştırın.

Tebrikler! Şimdi başarıyla ücreti fares tahmin etmeye yönelik bir machine learning modelini yerleşik, doğruluğunu değerlendirilir ve test. Bu öğreticinin için kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) deposu.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, öğrenilen nasıl yapılır:
> [!div class="checklist"]
> * Sorunu anlama
> * Uygun makine öğrenme görevini seçin
> * Hazırlama ve verilerinizi anlama
> * Öğrenme işlem hattı oluşturma
> * Yük ve verilerinizi dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitmek
> * Modeli değerlendirin
> * Model için tahminde kullanın

Bilgi almaya devam etmek ve daha fazla örneklerini bulmak için GitHub depomuzda denetleyin.
> [!div class="nextstepaction"]
> [DotNet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/)
