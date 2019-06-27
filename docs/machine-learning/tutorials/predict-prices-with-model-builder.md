---
title: Regresyon modeli Oluşturucu ile kullanarak fiyatlarını tahmin etme
description: Bu öğreticide ML.NET Model Fiyatlar, özellikle tahmin etmek için oluşturucu oturan taksi fares kullanarak bir regresyon modeli derler gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: db9788e3065a0f2f21d712b2d4826efea2d8a829
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410655"
---
# <a name="predict-prices-using-regression-with-model-builder"></a>Regresyon modeli Oluşturucu ile kullanarak fiyatlarını tahmin etme

ML.NET Model Oluşturucu oluşturmak için kullanmayı öğrenin bir [regresyon modeli](../resources/glossary.md#regression) fiyatlarını tahmin etmek için.  Bu öğreticide geliştirdiğiniz .NET konsol uygulaması taksi fares geçmiş New York taksi taksi verilerini temel alarak tahmin eder.

Model Oluşturucu fiyatı tahmin şablon sayısal tahmin değeri gerektiren her senaryo için kullanılabilir. Örnek senaryoları şunları içerir: barındırmak fiyat tahmini, Talep tahmini ve satış tahmini.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * Hazırlama ve verileri anlama
> * Senaryo seçin
> * Verileri yükleme
> * Modeli eğitme
> * Modeli değerlendirme
> * Kullanım modeli tahminler elde etmek için

> [!NOTE]
> Model Oluşturucu şu anda Önizleme aşamasındadır.

## <a name="pre-requisites"></a>Ön koşullar

Önkoşullar ve yükleme yönergeleri bir listesi için ziyaret edin [Model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md).

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Oluşturma bir **.NET Core konsol uygulaması** "TaxiFarePrediction" denir.

1. Yükleme **Microsoft.ML** NuGet paketi:

    İçinde **Çözüm Gezgini**, sağ *TaxiFarePrediction* seçin ve proje **NuGet paketlerini Yönet**. Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listeden bir paket seçin ve seçin **yükleme** düğmesi. Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.

## <a name="prepare-and-understand-the-data"></a>Hazırlama ve verileri anlama

1. Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi dosyaları depolamak için.

1. İndirme [taksi taksi train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) veri kümesi ve kaydetmesi *veri* önceki adımda oluşturduğunuz klasör. Bu veri kümesi, eğitmek ve machine learning modeli değerlendirmek için kullanılır. Bu veri kümesi başlangıçta dandır [NYC TLC taksi seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. İçinde **Çözüm Gezgini**, sağ *taksi taksi train.csv* seçin ve dosya **özellikleri**. Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.

Her satırda `taxi-fare-train.csv` veri kümesi bir taksi tarafından yapılan gelişlerin ayrıntılarını içerir. 

1. Açık **taksi taksi train.csv** veri kümesi

    Sağlanan veri kümesi şu sütunları içerir:

    * **vendor_id:** Taksi satıcı kimliği bir özelliktir.
    * **rate_code:** Taksi dönüş oranı türünü bir özelliktir.
    * **passenger_count:** Bir özellik Yolcuların seyahat üzerinde sayısıdır.
    * **trip_time_in_secs:** Seyahat geçen süre miktarı. Seyahat, taksi seyahat tamamlanmadan önce tahmin etmek istersiniz. Bu ne kadar seyahat bilmiyorum dakikamızı ayıralım. Bu nedenle, seyahat süresi, bir özellik değildir ve bu sütunu modelden dışında bırakacağız.
    * **trip_distance:** Seyahat mesafesini bir özelliktir.
    * **payment_type:** Ödeme yöntemini (nakit veya kredi kartı) bir özelliktir.
    * **fare_amount:** Ücretli toplam taksi taksi etiketi olur.

`label` Tahmin etmek istediğiniz sütun. Bir regresyon görevi gerçekleştirirken, sayısal bir değer tahmin hedeftir. Bu fiyat tahmini senaryoda taksi kılma maliyetini tahmin edildiğinde. Bu nedenle, **fare_amount** etiketidir. Tanımlanan `features` modeli tahmin etmek için size girişleri `label`. Bu durumda, geri kalan sütunların özellikleri veya girişleri olarak taksi miktarı tahmin etmek için kullanılır.

## <a name="choose-a-scenario"></a>Senaryo seçin

Modelinizi eğitmek için kullanılabilir makine öğrenme modeli oluşturucusu tarafından sağlanan senaryolar listesinden seçmeniz gerekir. Bu durumda, senaryodur `Price Prediction`. Daha kapsamlı bir liste için ziyaret edin [Model Oluşturucu genel bakış makalesi](../automate-training-with-model-builder.md#scenarios).

1. İçinde **Çözüm Gezgini**, sağ *TaxiFarePrediction* proje ve seçin **Ekle** > **Machine Learning**.
1. Model Oluşturucu aracı senaryo adımda seçin *fiyat tahmini* senaryo.

## <a name="load-the-data"></a>Verileri yükleme

Model Oluşturucu verileri iki kaynağı, bir SQL Server veritabanı veya bir yerel dosya csv veya tsv dosyasını kabul eder. Aşağıdaki veri biçimi gereksinimleri hakkında daha fazla bilgi için ziyaret [bağlantı](../how-to-guides/install-model-builder.md#limitations).

1. Model Oluşturucu aracı verileri adımda seçin *dosya* veri kaynağı açılır listeden.
1. Düğmeyi seçin *bir dosya seçin* metin kutusu ve kullanım ve seçmek için dosya Gezgini'ni *taksi taksi test.csv* içinde *veri* dizini
1. Seçin *fare_amount* içinde *etiket veya Predıct sütun* açılır ve Model Oluşturucu aracı train adımına gidin.

## <a name="train-the-model"></a>Modeli eğitme

Bu öğreticide fiyatı tahmin modeli eğitmek için kullanılan görev öğrenme regresyon makinedir. Model eğitimi işlemi sırasında en iyi performansa sahip veri kümeniz için model bulmak için farklı bir regresyon algoritmaları ve ayarları'nı kullanarak ayrı modeller Model Oluşturucu eğitir.

Modeli eğitmek gereken süreyi veri miktarı için uygun. Bu grafik için yeterli bir değer seçmek için kılavuz kullanın. `Time to train (seconds)` alan:

\* Veri kümesi boyutu  | Veri kümesi türü       | Ort. Eğitimi * süresi
------------- | ------------------ | --------------
0 - 10 mb     | Sayısal ve metin   | 10 saniye
10 - 100 mb   | Sayısal ve metin   | 10 dakikalık
100 - 500 mb  | Sayısal ve metin   | 30 dakika
500 - 1 Gb    | Sayısal ve metin   | 60 dk önce
1 Gb+         | Sayısal ve metin   | 3 saat +

1. Eğitim verileri dosyası 10 MB'tan fazla olduğundan, 600 saniye (10 dakika) değeri olarak kullanın *süresi (saniye) eğitmek için*.
2. Seçin *eğitim Başlat*.

Eğitim işlem boyunca ilerleme veri görüntülenen `Progress` eğitimi adım bölümü.

- Durum eğitim işleminin tamamlanma durumunu görüntüler.
- En yüksek doğruluğa en iyi performansa sahip Model Oluşturucu bulundu modelinin doğruluğunu görüntüler. Daha yüksek doğruluk testi veri daha doğru bir şekilde tahmin modeli anlamına gelir. 
- En iyi algoritmayı bulundu modelinin oluşturucusu tarafından gerçekleştirilen en iyi performansa algoritma adını görüntüler.
- Son algoritması, en son Model Oluşturucu, modeli eğitmek için kullanılan algoritma adını görüntüler.

Alıştırma tamamlandıktan sonra değerlendir adımına gidin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

En iyi performansı sahip bir model eğitimi adım olacaktır. Model Oluşturucu aracı değerlendir adımda çıkış bölümüne en iyi performansa sahip modeli tarafından kullanılan algoritmayı içerecek *en iyi modeli* ölçümlerde yanı sıra giriş *en iyi Model kalitesi (RSquared)* . İlk beş modelleri ve bunların ölçümleri içeren ek olarak, bir Özet Tablosu. Hakkında daha fazla bilgi edinmek için aşağıdaki bağlantıyı ziyaret edin [model ölçümlerini değerlendirme](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).

Doğruluk ölçümlerinizi memnun değilseniz, deneyin ve doğruluğu artırmak için bazı kolay veya daha fazla veri modeli eğitme süre miktarını artırmak için yöntemlerdir.

## <a name="use-the-model-for-predictions"></a>Kullanım modeli tahminler elde etmek için

İki proje eğitim işleminin sonucu olarak oluşturulacak.

- TaxiFarePredictionML.ConsoleApp: Model eğitimi ve tüketim kodu içeren bir .NET konsol uygulaması.
- TaxiFarePredictionML.Model: Giriş şemasını tanımlayan ve en iyi performansa sahip sırasında eğitim modeli kalıcı sürümünü yanı sıra model verileri çıkış veri modelleri içeren .NET Standard sınıf kitaplığı.

1. Kod Model Oluşturucu aracının bölümünde **eklenen projeleri** projeleri çözüme eklemek için.
1. Çözüm Gezgini'nde sağ *TaxiFarePrediction* proje. Ardından, **Ekle > var olan öğe**. İçin dosya türü açılan listesinde seçin `All Files`, gitmek *TaxiFarePredictionML.Model* dizin ve select projeyi `MLModel.zip` dosya. Son eklenen'ı sağ `MLModel.zip` seçin ve dosya *özellikleri*. Çıkış dizini seçeneğini Kopyala için *yeniyse Kopyala* açılır listeden.
1. Sağ *TaxiFarePrediction* proje. Ardından, **Ekle > başvuru**. Seçin **projeleri > Çözüm** düğüm ve listeden *TaxiFarePredictionML.Model* proje ve Tamam'ı seçin.

4. Açık *Program.cs* dosyası *TaxiFarePrediction* proje.
5. Aşağıdaki using deyimlerini:

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. Ekleme `ConsumeModel` yönteme `Program` sınıfı. `ConsumeModel` Oluşturacak bir `PredictionEngine` yeni veri tahminlerde bulunabilir ve konsola yazdırmanız için Model Oluşturucu tarafından oluşturulan model göre.

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

7. Aşağıdaki kodu ekleyin `Main` yöntemi ve uygulamayı çalıştırın.

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    Program tarafından oluşturulan çıktı kod parçacığını aşağıdaki gibi görünmelidir:

    ```bash
    Predicted Fare: 16.82245
    ```

Daha sonra başka bir çözüm içinde oluşturulan projeleri başvurmanız gerekiyorsa, içinde bulabilirsiniz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizin.

## <a name="next-steps"></a>Sonraki Adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> * Hazırlama ve verileri anlama
> * Senaryo seçin
> * Verileri yükleme
> * Modeli eğitme
> * Modeli değerlendirme
> * Kullanım modeli tahminler elde etmek için

Modelinizi dağıtma hakkında bilgi edinmek için aşağıdaki nasıl yapılır makaleleri birini ilerleyin.

> [!div class="nextstepaction"]
> [Azure işlevleri için model dağıtma](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [Bir Web API'si için model dağıtma](../how-to-guides/serve-model-web-api-ml-net.md)
