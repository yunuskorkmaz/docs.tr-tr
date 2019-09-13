---
title: Model Oluşturucu ile gerileme kullanarak fiyatları tahmin etme
description: Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.net model Oluşturucu kullanarak bir gerileme modeli oluşturma gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 07/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bc1dacdad436cc5384bca4bbce224acc18d69201
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929438"
---
# <a name="predict-prices-using-regression-with-model-builder"></a>Model Oluşturucu ile gerileme kullanarak fiyatları tahmin etme

Fiyatları tahmin etmek için bir gerileme modeli () oluşturmak üzere ML.NET model Oluşturucu 'Yu nasıl kullanacağınızı öğrenin.  Bu öğreticide geliştirdiğiniz .NET konsol uygulaması, geçmiş New York taksi tarifeli havayolu verilerine dayalı olarak taksi Fares 'yi tahmin eder.

Model Oluşturucu fiyat tahmin şablonu, sayısal tahmin değeri gerektiren herhangi bir senaryo için kullanılabilir. Örnek senaryolar şunlardır: ev fiyat tahmini, talep tahmini ve satış tahmini.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Verileri hazırlama ve anlama
> - Senaryo seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Tahmin için modeli kullanma

> [!NOTE]
> Model Oluşturucu Şu anda önizleme aşamasındadır.

## <a name="pre-requisites"></a>Ön koşullar

Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "Taxifaretahminini" adlı bir **.NET Core konsol uygulaması** oluşturun.

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

1. Veri kümesi dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun.

1. Machine Learning modelini eğmekte ve değerlendirmek için kullanılan veri kümesi, ilk olarak NYC TLC TAXI seyahat veri kümesinden.

    Veri kümesini indirmek için [Taxi-fare-train. csv indirme bağlantısına](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv)gidin.

    Sayfa yüklendiğinde, sayfada herhangi bir yere sağ tıklayın ve **farklı kaydet**' i seçin.

    Dosyayı önceki adımda oluşturduğunuz *veri* klasörüne kaydetmek Için **Farklı Kaydet iletişim kutusunu** kullanın.

1. **Çözüm Gezgini**, *Taxi-fare-train. csv* dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

`taxi-fare-train.csv` Veri kümesindeki her satır bir TAXI tarafından yapılan gelişlerin ayrıntılarını içerir.

1. **Taxi-fare-train. csv** veri kümesini açın

    Belirtilen veri kümesi şu sütunları içerir:

    - **vendor_id:** Taxı satıcısının KIMLIĞI bir özelliktir.
    - **rate_code:** Taxı seyahati 'ın hız türü bir özelliktir.
    - **passenger_count:** Seyahat üzerindeki pascuların sayısı bir özelliktir.
    - **trip_time_in_secs:** Seyahati için geçen süre.
    - **trip_distance:** Seyahat uzaklığı bir özelliktir.
    - **payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.
    - **fare_amount:** Ödenen toplam TAXI tarifeli havayolu etikettir.

`label` Tahmin etmek istediğiniz sütundur. Regresyon görevi gerçekleştirirken, amaç sayısal bir değeri tahmin etmek için kullanılır. Bu fiyat tahmin senaryosunda, bir TAXI arttırıldığında 'nın maliyeti tahmin ediliyor. Bu nedenle, **fare_amount** etikettir. `features` ,`label`Modeli tahmin etmek için size izin verdiğiniz girişlerdir. Bu durumda, sütunların geri kalanı tarifeli havayolu tutarını tahmin etmek için özellik veya giriş olarak kullanılır.

## <a name="choose-a-scenario"></a>Senaryo seçin

Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir. Bu durumda senaryo `Price Prediction`.

1. **Çözüm Gezgini**, *taxifaretahmin* projesine sağ tıklayın ve**Machine Learning** **Ekle** > ' yi seçin.
1. Model Oluşturucu aracının senaryo adımında *fiyat tahmini* senaryosu ' nı seçin.

## <a name="load-the-data"></a>Verileri yükleme

Model Oluşturucu, bir SQL Server veritabanı veya CSV ya da TSV biçimindeki yerel bir dosya olan iki kaynaktan verileri kabul eder.

1. Model Oluşturucu aracının veri adımında, veri kaynağı açılır listesinden *Dosya* ' yı seçin.
1. *Dosya Seç* metin kutusunun yanındaki düğmeyi seçin ve *veri* dizinindeki *Taxi-fare-test. csv* dosyasına gidip seçmek için dosya Gezgini 'ni kullanın
1. Açılan menüyü *tahmin etmek Için etiket veya sütunda* *fare_amount* öğesini seçin ve model Oluşturucu aracının eğitme adımına gidin.

## <a name="train-the-model"></a>Modeli eğitme

Bu öğreticide fiyat tahmin modelini eğitmek için kullanılan makine öğrenimi görevi gerileme. Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı gerileme algoritmaları ve ayarları kullanarak modelleri ayrı ayrı işler.

Modelin eğitilmesi için gereken süre, veri miktarına müşterinizin istekleriyle orantılı. `Time to train (seconds)` Alan için uygun bir değer seçmek üzere bu grafiği kılavuz olarak kullanın:

\* Veri kümesi boyutu  | Veri kümesi türü       | Ort. Tren süresi *
------------- | ------------------ | --------------
0-10 MB     | Sayısal ve metin   | 10 sn
10-100 MB   | Sayısal ve metin   | 10 dakika
100-500 MB  | Sayısal ve metin   | 30 dakika
500-1 GB    | Sayısal ve metin   | 60 dk
1 GB +         | Sayısal ve metin   | 3 saat +

1. Eğitim veri dosyası 10 MB 'tan fazla olduğundan, *tren süresi (saniye)* değeri olarak 600 saniye (10 dakika) kullanın.
2. *Eğitimi Başlat*' ı seçin.

Eğitim süreci boyunca, ilerleme verileri eğitme adımının `Progress` bölümünde görüntülenir.

- Durum, eğitim sürecinin tamamlanma durumunu görüntüler.
- En iyi doğruluk, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde oluşan modelin doğruluğunu gösterir. Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.
- En iyi algoritma, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde gerçekleştirilen algoritmanın adını görüntüler.
- Son algoritma modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.

Eğitim tamamlandıktan sonra değerlendir adımına gidin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Eğitim adımının sonucu, en iyi performansa sahip bir model olacaktır. Model Oluşturucu aracının değerlendir adımında, çıkış bölümü en iyi *model girişinde en* iyi işlem modeli tarafından kullanılan algoritmayı *(RKARE)* içerir. Ayrıca, ilk beş modeli ve bunların ölçümlerini içeren bir Özet tablosu.

Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu denemeye yönelik bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır. Aksi takdirde, kod adımına gidin.

## <a name="add-the-code-to-make-predictions"></a>Tahminleri yapmak için kodu ekleyin

Eğitim sürecinin bir sonucu olarak iki proje oluşturulacaktır.

- TaxiFarePredictionML. ConsoleApp: Model eğitimi ve tüketim kodu içeren bir .NET Core konsol uygulaması.
- TaxiFarePredictionML. Model: Eğitim sırasında en iyi gerçekleştirme modelinin kalıcı sürümü ve giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini içeren .NET Standard sınıf kitaplığı.

1. Model Oluşturucu aracının kod adımında, otomatik olarak oluşturulan projeleri çözüme eklemek için **Proje Ekle** ' yi seçin.
1. *Taxifaretahmin* projesi öğesine sağ tıklayın. Ardından **> başvuru ekleyin**. **Projeler > çözüm** düğümünü seçin ve listeden *TaxiFarePredictionML. model* projesini denetleyip Tamam ' ı seçin.
1. *Program.cs* dosyasını *Taxifaretahmin* projesinde açın.
1. *Microsoft.ml* NuGet paketini ve *TaxiFarePredictionML. model* projesine başvurmak için aşağıdaki using deyimlerini ekleyin:

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. `ConsumeModel` Yöntemini`Program` sınıfına ekleyin.

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

    Eğitilen modeli yükler, model için bir [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) oluşturun ve yeni verilerde tahmine dayalı hale getirmek için onu kullanın. `ConsumeModel`

1. Modeli kullanarak yeni verileri tahmin etmek için, `ModelInput` sınıfın yeni bir örneğini oluşturun ve `ConsumeModel` yöntemini kullanın. Tarifeli havayolu tutarının girişin bir parçası olmadığına dikkat edin. Bunun nedeni, modelin tahmin oluşturması olacaktır. `Main` Yöntemine aşağıdaki kodu ekleyin ve uygulamayı çalıştırın

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

    Program tarafından oluşturulan çıkış aşağıdaki kod parçacığına benzemelidir:

    ```bash
    Predicted Fare: 16.82245
    ```

Oluşturulan projelere başka bir çözümün içinde daha sonraki bir zamanda başvurmanız gerekirse, bunları `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizin içinde bulabilirsiniz.

## <a name="next-steps"></a>Sonraki Adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Verileri hazırlama ve anlama
> - Senaryo seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Tahmin için modeli kullanma

### <a name="additional-resources"></a>Ek Kaynaklar

Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:

- [Model Oluşturucu senaryoları](../automate-training-with-model-builder.md#scenarios)
- [Regresyon](../resources/glossary.md#regression)
- [Regresyon modeli ölçümleri](../resources/metrics.md#metrics-for-regression)
- [NYC TLC TAXI seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
