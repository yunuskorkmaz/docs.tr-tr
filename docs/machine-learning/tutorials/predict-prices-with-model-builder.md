---
title: 'Öğretici: Model Oluşturucu ile gerileme kullanarak fiyatları tahmin'
description: Bu öğretici fiyatları tahmin etmek için ML.NET Model Builder kullanarak bir regresyon modeli oluşturmak için nasıl göstermektedir, özellikle, New York Taksi ücretleri.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: 750738f8e3c65363e9996667feeccd1b84391f9f
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438240"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a>Öğretici: Model Oluşturucu ile gerileme kullanarak fiyatları tahmin

Fiyatları tahmin etmek için bir regresyon modeli oluşturmak için ML.NET Model Builder'ı nasıl kullanacağınızı öğrenin.  Bu eğitimde geliştirdiğiniz .NET konsol uygulaması, tarihsel New York taksi ücreti verilerine göre taksi ücretlerini tahmin eder.

Model Oluşturucu fiyat tahmin şablonu, sayısal tahmin değeri gerektiren herhangi bir senaryo için kullanılabilir. Örnek senaryolar şunlardır: ev fiyat tahmini, talep tahmini ve satış tahmini.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> - Verileri hazırlama ve anlama
> - Bir senaryo seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Öngörüler için modeli kullanma

> [!NOTE]
> Model Oluşturucu şu anda Önizleme'de.

## <a name="pre-requisites"></a>Ön koşullar

Ön koşul ve yükleme yönergelerinin listesi için [Model Oluşturucu yükleme kılavuzunu ziyaret edin.](../how-to-guides/install-model-builder.md)

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "TaxiFarePrediction" adlı **bir C# .NET Çekirdek Konsol Uygulaması** oluşturun. Çözüm **ve projeyi aynı dizindeki yerleştir** çözümve proje **işaretsiz** olduğundan emin olun (VS 2019) veya **çözüm için create directory** (VS 2017) **işaretlenir.**

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

1. Veri kümesi dosyalarını depolamak için projenizde *Veri* adlı bir dizin oluşturun.

1. Makine öğrenimi modelini eğitmek ve değerlendirmek için kullanılan veri seti aslında NYC TLC Taksi Gezisi veri kümesindendir.

    1. Veri kümesini indirmek için [taksi-ücret-train.csv indirme linkine](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv)gidin.

    1. Sayfa yüklendiğinde, sayfanın herhangi bir yerine sağ tıklayın ve **Olarak Kaydet'i**seçin.

    1. Önceki adımda oluşturduğunuz *Veri* klasörüne dosyayı kaydetmek için **Kaydet İletişim** kutusunu kullanın.

1. **Çözüm Gezgini'nde,** *taksi-ücret-train.csv* dosyasına sağ tıklayın ve **Özellikler'i**seçin. **Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.

Veri kümesindeki `taxi-fare-train.csv` her satır, bir taksi tarafından yapılan seyahatlerin ayrıntılarını içerir.

1. **Taksi-ücret-train.csv** veri setini açın

    Sağlanan veri kümesi aşağıdaki sütunları içerir:

    - **vendor_id:** Taksi satıcısının kimliği bir özelliktir.
    - **rate_code:** Taksi gezisinin fiyat türü bir özelliktir.
    - **passenger_count:** Yolculuktaki yolcu sayısı bir özelliktir.
    - **trip_time_in_secs:** Yolculuğun aldığı süre. Yolculuk tamamlanmadan önce seyahat ücretini tahmin etmek istiyorsunuz. O anda yolculuğun ne kadar süreceğini bilemezsin. Bu nedenle, yolculuk süresi bir özellik değildir ve bu sütunu modelden dışlarsınız.
    - **trip_distance:** Yolculuk mesafesi bir özelliktir.
    - **payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.
    - **fare_amount:** Ödenen toplam taksi ücreti etikettir.

Tahmin `label` etmek istediğiniz sütundur. Bir regresyon görevi gerçekleştirirken, amaç sayısal bir değeri tahmin etmektir. Bu fiyat tahmini senaryosunda, bir taksi yolculuğu maliyeti tahmin ediliyor. Bu nedenle, **fare_amount** etikettir. Tanımlanan `features` girdiler, modeli tahmin etmek için `label`verdiğiniz girdilerdir. Bu durumda, **trip_time_in_secs** hariç sütunların geri kalanı, ücret tutarını tahmin etmek için özellik veya girdi olarak kullanılır.

## <a name="choose-a-scenario"></a>Bir senaryo seçin

Modelinizi eğitmek için Model Builder tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir. Bu durumda, `Price Prediction`senaryo.

1. **Solution Explorer'da** *TaxiFarePrediction* projesine sağ tıklayın ve**Machine Learning** **Ekle'yi** > seçin.
1. Model Oluşturucu aracının senaryo adımında *Fiyat Tahmini* senaryosunu seçin.

## <a name="load-the-data"></a>Verileri yükleme

Model Builder iki kaynaktan, bir SQL Server veritabanından veya yerel bir dosyadan csv veya tsv formatında veri kabul eder.

1. Model Oluşturucu aracının veri adımında, veri kaynağı açılır tarafından *Dosya'yı* seçin.
1. Dosya metin kutusunu *seç'in* yanındaki düğmeyi seçin ve *Veri* dizinindeki *taksi-fare-test.csv'ye* göz atmak ve seçmek için Dosya Gezgini'ni kullanın
1. Sütundaki *fare_amount* 'yi seçin *(Label) açılır düşüşünü tahmin edin.*
1. Giriş *Sütunları (Özellikler)* açılır bırak'ı genişletin ve eğitim sırasında özellik olarak hariç tutmak için *trip_time_in_secs* sütunun denetimini kaldırın.  Model Oluşturucu aracının tren adımına gidin.

## <a name="train-the-model"></a>Modeli eğitme

Bu öğretici fiyat tahmin modeli eğitmek için kullanılan makine öğrenme görevi gerileme olduğunu. Model eğitim süreci sırasında Model Builder, veri setiniz için en iyi performans gösteren modeli bulmak için farklı regresyon algoritmaları ve ayarları kullanarak ayrı modeller eğitir.

Modelin eğitilmesi için gereken süre veri miktarıyla orantılıdır. Model Oluşturucu, veri kaynağınızın boyutuna bağlı **olarak, eğitme Süresi (saniye)** için varsayılan bir değer seçer.

1. Daha uzun süre antrenman yapmayı tercih etmedikçe, varsayılan değeri, *eğitme süresi (saniye)* olduğu gibi bırakın.
2. *Start Training'i*seçin.

Eğitim süreci boyunca, ilerleme verileri tren `Progress` adımı bölümünde görüntülenir.

- Durum, eğitim sürecinin tamamlanma durumunu görüntüler.
- En iyi doğruluk, Model Builder tarafından şimdiye kadar bulunan en iyi performans gösteren modelin doğruluğunu görüntüler. Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin ettiği anlamına gelir.
- En iyi algoritma, Model Builder tarafından şimdiye kadar bulunan en iyi performans gösteren algoritmanın adını görüntüler.
- Son algoritma, modeli eğitmek için Model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.

Eğitim tamamlandıktan sonra değerlendirme adımına gidin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Eğitim adımının sonucu en iyi performansa sahip bir model olacaktır. Model Oluşturucu aracının değerlendirme adımında, çıkış bölümü, *Best Model* Girişinde en iyi performans gösteren model tarafından kullanılan algoritmayı içerecek ve En İyi Model *Kalitesi (RSquared)* ölçütleri ile birlikte. Ayrıca, en iyi beş modeli ve bunların ölçümlerini içeren bir özet tablo.

Doğruluk ölçümlerinizden memnun değilseniz, model doğruluğunu geliştirmeyi denemenin ve geliştirmenin bazı kolay yolları, modeli eğitmek veya daha fazla veri kullanmak için gereken süreyi artırmakiçindir. Aksi takdirde, kod adımına gidin.

## <a name="add-the-code-to-make-predictions"></a>Tahminlerde bulunmak için kodu ekleme

Eğitim süreci sonucunda iki proje oluşturulacaktır.

- TaxiFarePredictionML.ConsoleApp: Model eğitimi ve örnek tüketim kodunu içeren bir .NET Core Console uygulaması.
- TaxiFarePredictionML.Model: Giriş ve çıktı modeli verilerinin şemasını tanımlayan veri modellerini, eğitim sırasında en iyi performans gösteren modelin kaydedilmiş `ConsumeModel` sürümünü ve tahminde bulunmak için çağrılan yardımcı sınıfı içeren bir .NET Standart sınıf kitaplığı.

1. Model Oluşturucu aracının kod adımında, çözüme otomatik oluşturulan projeleri eklemek için **Projeler Ekle'yi** seçin.
1. *TaxiFarePrediction* projesinde *Program.cs* dosyasını açın.
1. *TaxiFarePredictionML.Model* projesine başvurmak için aşağıdaki ifadeyi ekleyin:

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. Modeli kullanarak yeni veriler üzerinde bir tahminde bulunmak `ModelInput` için, `Main` uygulama yöntemi içinde sınıfın yeni bir örneğini oluşturun. Ücret tutarının girişin bir parçası olmadığını unutmayın. Bunun nedeni, modelin bunun için tahmin oluşturacağıdır.

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. Sınıftaki `Predict` `ConsumeModel` yöntemi kullanın. Yöntem, `Predict` eğitilen modeli [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) yükler, model için bir model oluşturur ve yeni veriler üzerinde öngörülerde bulunmak için kullanır.

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. Uygulamayı çalıştırın.

    Program tarafından oluşturulan çıktı aşağıdaki snippet benzer görünmelidir:

    ```bash
    Predicted Fare: 14.96086
    ```

Oluşturulan projeleri başka bir çözüm içinde daha sonra göndermeniz gerekiyorsa, bunları `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizinin içinde bulabilirsiniz.

## <a name="next-steps"></a>Sonraki Adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Verileri hazırlama ve anlama
> - Bir senaryo seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Öngörüler için modeli kullanma

### <a name="additional-resources"></a>Ek Kaynaklar

Bu eğitimde bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:

- [Model Oluşturucu Senaryolar](../automate-training-with-model-builder.md#scenario)
- [Regresyon](../resources/glossary.md#regression)
- [Regresyon Model Ölçümleri](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [NYC TLC Taksi Gezisi veri seti](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
