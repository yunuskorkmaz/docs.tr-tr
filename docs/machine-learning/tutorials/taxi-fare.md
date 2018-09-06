---
title: ML.NET New York taksi fares (gerileme) tahmin etmek için kullanın
description: ML.NET bir regresyon senaryosunda kullanmayı öğrenin.
author: aditidugar
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 133b7ad17a98e4eea510f1704555b690b98e9091
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801066"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>Öğretici: Kullanımı ML.NET New York taksi fares (gerileme) tahmin etmek için

> [!NOTE]
> Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir. Daha fazla bilgi için [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Bu öğretici ML.NET oluşturmak için nasıl kullanılacağını gösterir. bir [regresyon modeli](../resources/glossary.md#regression) oturan taksi fares tahmin etmeye yönelik.

Bu öğreticide, şunların nasıl yapılır:
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

## <a name="create-a-console-application"></a>Bir konsol uygulaması oluşturun

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

* **vendor_id:** taksi satıcı kimliği bir özelliktir.
* **rate_code:** taksi dönüş oranı türünü bir özelliktir.
* **passenger_count:** Yolcuların seyahat üzerinde sayısı bir özelliktir.
* **trip_time_in_secs:** seyahat süresini sürdü. Seyahat, taksi seyahat tamamlanmadan önce tahmin etmek istersiniz. Bu ne kadar seyahat bilmiyorum dakikamızı ayıralım. Bu nedenle, seyahat süresi, bir özellik değildir ve bu sütunu modelden dışında bırakacağız.
* **trip_distance:** seyahat mesafesini bir özelliktir.
* **payment_type:** (nakit veya kredi kartı) ödeme yöntemini bir özelliktir.
* **fare_amount:** ödenen toplam taksi taksi etiketidir.

## <a name="create-data-classes"></a>Veri sınıfları oluşturma

Girdi verilerini ve Öngörüler için sınıflar oluşturun:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TaxiTrip.cs*. Ardından, **Ekle** düğmesi.
1. Aşağıdaki `using` yeni dosya için yönergeler:

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `TaxiTrip` ve `TaxiTripFarePrediction`, *TaxiTrip.cs* dosyası:

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` giriş verisi sınıfıdır ve her bir veri kümesi sütunları tanımlarına sahip. Kullanım [sütun](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) veri kümesinde kaynak sütunları dizin belirtmek için özniteliği.

`TaxiTripFarePrediction` Sınıfı, tahmini sonuçlar'ı temsil eder. Tek bir kayan noktalı sayı alana sahip `FareAmount`, ile bir `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) özniteliği uygulandı. Regresyon görev durumunda **puanı** sütun tahmin edilen etiket değerlerini içerir.

> [!NOTE]
> Kullanım `float` giriş ve tahmin verilerini sınıflardaki kayan nokta değerlerini temsil eden tür.

## <a name="define-data-and-model-paths"></a>Veri ve model tanımlar

Geri Git *Program.cs* dosya ve veri kümeleri dosyalarına ve modeli kaydedin ve dosyaya yolları tutmak için üç alanları ekleyin:

* `_datapath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.
* `_testdatapath` model değerlendirmek için kullanılan veri kümesiyle dosyasının yolunu içerir.
* `_modelpath` eğitilen modelin depolandığı dosya yolu içerir.

Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için:

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Derleme, aşağıdaki ekleyin önceki kodun `using` üst kısmındaki yönergeleri *Program.cs* dosyası:

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a>Öğrenme işlem hattı oluşturma

Aşağıdaki ek ekleyin `using` yönergeleri üstüne *Program.cs* dosyası:

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

İçinde `Main` yöntemi Değiştir `Console.WriteLine("Hello World!")` aşağıdaki kod ile:

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` Yöntemi modeli eğitir. Bu yöntem oluşturma hemen altına `Main`, aşağıdaki kodu kullanarak:

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

Öğrenme işlem hattınızı tüm veri ve algoritmaları modeli eğitmek gerekli yükler. Aşağıdaki kodu ekleyin `Train` yöntemi:

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a>Veri yükleme ve dönüştürme

İlk adımı gerçekleştirmek için eğitim veri kümesinden veri yüklenmesidir. Bu örnekte, tarafından tanımlanan bir yol ile metin dosyasında eğitim veri kümesi depolanır `_datapath` alan. İlk satır verileri yüklenirken yoksayılmalıdır. Bu nedenle bu dosyayı sütun adları üstbilgiyle sahiptir. Bir dosyadaki sütunları virgülle ayrılmış (","). Aşağıdaki kodu ekleyin `Train` yöntemi:

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

Sonraki adımlarda sütunlara adlarıyla tanımlanan diyoruz `TaxiTrip` sınıfı.

Model eğitim ve diğer değerleri varsayılan olarak, hesaplanan zaman **etiket** sütun tahmin için doğru değerleri olarak değerlendirilir. Taksi seyahat taksi tahmin etmek istediğimiz gibi kopyalayın `FareAmount` sütuna **etiket** sütun. Bunu yapmak için kullanın <xref:Microsoft.ML.Transforms.ColumnCopier> ve aşağıdaki kodu ekleyin:

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

Modeli eğitir algoritması **sayısal** kategorik verileri dönüştürmek zorunda özellikleri (`VendorId`, `RateCode`, ve `PaymentType`) içine numaraları değerleri. Bunu yapmak için kullanın <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, anahtar değerlerini farklı değerlerle her sütun, farklı sayısal atar ve aşağıdaki kodu ekleyin:

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak <xref:Microsoft.ML.Transforms.ColumnConcatenator> dönüştürme sınıfı. Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun. Aşağıdaki kodu ekleyin:

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

Dikkat `TripTime` karşılık gelen sütun `trip_time_in_secs` sütunu veri kümesi dosyası içindeki dahil değildir. Zaten bir kullanışlı tahmin özelliği değil belirledi.

> [!NOTE]
> Aşağıdaki adımları başarılı yürütme için yukarıda belirtilen sırada ardışık düzene eklenmelidir.

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Veri ardışık düzenine eklemek ve giriş doğru biçime dönüştürme sonra bir öğrenme algoritması seçin (**learner**). Learner modeli eğitir. Seçtiğiniz bir **regresyon** görev kullandığınız için bu sorun için bir <xref:Microsoft.ML.Trainers.FastTreeRegressor> ML.NET tarafından sağlanan regresyon öğrencileriyle biri olan learner.

<xref:Microsoft.ML.Trainers.FastTreeRegressor> Gradyan artırma learner kullanır. Gradyan artırma bir machine learning teknik regresyon sorunları var. Bu, her regresyon ağaç tarafınızdaki bir biçimde oluşturur. Her adımda hata oluştu ölçmenizi ve sonraki düzeltmek için önceden tanımlanmış kaybı işlevi kullanır. Aslında bir topluluğu, tahmin modellerini daha zayıf bir tahmin modeli sonucudur. Gradyan artırma hakkında daha fazla bilgi için bkz. [artırılmış karar ağacı regresyonu](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).

Aşağıdaki kodu ekleyin `Train` önceki adımda eklenen koddan veri işleme yöntemi:

```csharp
pipeline.Add(new FastTreeRegressor());
```

Yukarıdaki adımların tümünü ayrı deyimler ardışık düzenine eklenen, ancak C# oluşturma ve başlatma işlem hattını basitleştirir bir kullanışlı toplama başlatma söz dizimine sahiptir. Şimdiye kadar eklediğiniz kodu değiştirin `Train` yöntemini aşağıdaki kod ile:

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>Modeli eğitme

Modeli eğitmek için son adımdır bakın. Bu noktaya kadar hiçbir işlem hattı çalıştırıldı. `pipeline.Train<TInput, TOutput>` Yöntemi üreten bir örneğini alan modeli `TInput` türü ve örneği çıkaran `TOutput` türü. Aşağıdaki kodu ekleyin `Train` yöntemi:

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

Ve İşte bu kadar! Başarıyla bir makine öğrenimi taksi fares NYC içinde tahmin edebilen bir model eğitim. Şimdi şimdi modelin nasıl doğru olup olmadığını anlamak için göz atın ve taksi taksi değerleri tahmin etmek için kullanmayı öğrenin.

### <a name="save-the-model"></a>Modeli kaydedin

Bu noktada, tüm mevcut veya yeni .NET uygulamalarınızı tümleşik bir model var. Model bir .zip dosyası olarak kaydetmek için aşağıdaki kodu ekleyin sonunda `Train` yöntemi:

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

Ekleme `await` ifadesine `model.WriteAsync` çağrı anlamına `Train` yöntemi bir görev döndüren zaman uyumsuz yöntemi için değiştirilmesi gerekir. Değişiklik imzası `Train` aşağıdaki kodda gösterildiği gibi:

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

Dönüş türünün değiştirilmesi `Train` yöntemi eklemek sahip olduğunuz anlamına gelir; bir `await` çağıran koda `Train` içinde `Main` aşağıdaki kodda gösterildiği gibi yöntemi:

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

Kullanarak `await` içinde `Main` yöntemi anlamına gelir `Main` yöntemi olmalıdır `async` değiştiricisi ve dönüş bir `Task`:

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

Ayrıca aşağıdakileri eklemeniz gerekir `using` dosyasının en üstüne yönergenizi:

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

Çünkü `async Main` yöntemi, C# 7.1 eklenen özelliğidir ve C# 7.0 projesi varsayılan dil sürümü değil, C# 7.1 veya üzeri dil sürümünü değiştirmeniz gerekir. Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**. Seçin **derleme** sekmenize **Gelişmiş** düğmesi. Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm). Seçin **Tamam** düğmesi.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Değerlendirme model etiket değerlerini ne kadar iyi tahmin denetleme işlemidir. Model modeli eğitmek için kullanılmayan verileri iyi tahminler yapar önemlidir. Bu öğreticide işlendiğinden bunu yapmanın bir yolu, verileri eğitim ve test veri kümesi bölme sağlamaktır. Eğitim verileri modeli eğittiğimize göre test verileri ne kadar iyi gerçekleştirdiği görebilirsiniz.

Geri Git `Main` yöntemi çağrısı altına aşağıdaki kodu ekleyin `Train`yöntemi:

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate` Yöntemi modeli değerlendirir. Bu yöntem oluşturmak için aşağıdaki kodu ekleyin. `Train` yöntemi:

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

Aşağıdaki kodu ekleyin `Evaluate` test verilerini Kurulum yüklemeyi yöntemi:

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

Modeli değerlendirme ve değerlendirme ölçümleri üretmek için aşağıdaki kodu ekleyin:

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) gerileme modelini değerlendirme ölçümlerini biridir. Daha düşük olan, daha iyi modelidir. Aşağıdaki kodu ekleyin `Evaluate` yöntemi RMS değerini görüntülemek için:

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

[RSquared](../resources/glossary.md#coefficient-of-determination) regresyon modelleri, başka bir değerlendirme unsurdur. RSquared 0 ile 1 arasındaki değerleri alır. Daha değerini 1 olarak daha iyi modelidir yakınız. Aşağıdaki kodu ekleyin `Evaluate` yöntemi RSquared değerini görüntülemek için:

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>Kullanım modeli tahminler elde etmek için

Ev test veri örnekleri için bir sınıf oluşturun:

1. İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.
1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestTrips.cs*. Ardından, **Ekle** düğmesi.
1. Sınıfı gibi aşağıdaki örnekte de statik olarak değiştirin:

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

Bu öğretici, bu sınıf içinde bir test seyahat kullanır. Daha sonra modeli denemek için diğer senaryolar ekleyebilirsiniz. Aşağıdaki kodu ekleyin `TestTrips` sınıfı:

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

Bu yolculuğu'nın gerçek taksi 29.5 ' dir. Model taksi tahmin etme gibi yer tutucu olarak 0'ı kullanın.

Belirtilen seyahat, taksi tahmin etmek için geri gidin *Program.cs* dosya ve içine aşağıdaki kodu ekleyin `Main` yöntemi:

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

Test durumunuz için tahmin edilen taksi taksi görmek için programı çalıştırın.

Tebrikler! Başarıyla taksi seyahat fares tahmin etmeye yönelik bir machine learning modeli, doğruluğunun değerlendirilir, derleyip tahminlerde bulunmak için kullanılır. Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposu.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide şunları öğrendiniz: nasıl yapılır:
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
> [Iris kümelemesi](iris-clustering.md)
