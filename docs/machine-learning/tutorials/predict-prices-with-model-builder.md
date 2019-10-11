---
title: 'Öğretici: model Oluşturucu ile gerileme kullanarak fiyatları tahmin etme'
description: Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.net model Oluşturucu kullanarak bir gerileme modeli oluşturma gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/08/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a851bf3c405d15243bc1457b8c3dff815d072ebe
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180279"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a>Öğretici: model Oluşturucu ile gerileme kullanarak fiyatları tahmin etme

Fiyatları tahmin etmek için bir gerileme modeli oluşturmak üzere ML.NET model Oluşturucu 'Yu nasıl kullanacağınızı öğrenin.  Bu öğreticide geliştirdiğiniz .NET konsol uygulaması, geçmiş New York taksi tarifeli havayolu verilerine dayalı olarak taksi Fares 'yi tahmin eder.

Model Oluşturucu fiyat tahmin şablonu, sayısal tahmin değeri gerektiren herhangi bir senaryo için kullanılabilir. Örnek senaryolar şunlardır: ev fiyat tahmini, talep tahmini ve satış tahmini.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
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

## <a name="pre-requisites"></a>Önkoşullar

Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "Taxifaretahminini" adlı bir **.NET Core konsol uygulaması** oluşturun.

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

1. Veri kümesi dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun.

1. Machine Learning modelini eğmekte ve değerlendirmek için kullanılan veri kümesi, ilk olarak NYC TLC TAXI seyahat veri kümesinden.

    1. Veri kümesini indirmek için [Taxi-fare-train. csv indirme bağlantısına](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv)gidin.

    1. Sayfa yüklendiğinde, sayfada herhangi bir yere sağ tıklayın ve **farklı kaydet**' i seçin.

    1. Dosyayı önceki adımda oluşturduğunuz *veri* klasörüne kaydetmek Için **Farklı Kaydet iletişim kutusunu** kullanın.

1. **Çözüm Gezgini**, *Taxi-fare-train. csv* dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

@No__t-0 veri kümesindeki her satır, bir TAXI tarafından yapılan gelişlerin ayrıntılarını içerir.

1. **Taxi-fare-train. csv** veri kümesini açın

    Belirtilen veri kümesi şu sütunları içerir:

    - **vendor_id:** Taxı satıcısının KIMLIĞI bir özelliktir.
    - **rate_code:** Taxı seyahati 'ın hız türü bir özelliktir.
    - **passenger_count:** Seyahat üzerindeki pascuların sayısı bir özelliktir.
    - **trip_time_in_secs:** Seyahati için geçen süre. Seyahat tamamlanmadan önce seyahat tarifeli havayolu tahmin etmek istiyorsunuz. Bu anda seyahati ne kadar süreyle yapılacağını bilemezsiniz. Bu nedenle, seyahat süresi bir özellik değildir ve bu sütunu modelden dışlayabilirsiniz.
    - **trip_distance:** Seyahat uzaklığı bir özelliktir.
    - **payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.
    - **fare_amount:** Ödenen toplam TAXI tarifeli havayolu etikettir.

@No__t-0, tahmin etmek istediğiniz sütundur. Regresyon görevi gerçekleştirirken, amaç sayısal bir değeri tahmin etmek için kullanılır. Bu fiyat tahmin senaryosunda, bir TAXI arttırıldığında 'nın maliyeti tahmin ediliyor. Bu nedenle, **fare_amount** etikettir. Tanımlanan `features`, modele `label` tahmin etmek için verdiğiniz girişlerdir. Bu durumda, **trip_time_in_secs** özel durumu ile sütunların geri kalanı, tarifeli havayolu tutarını tahmin etmek için özellik veya giriş olarak kullanılır.

## <a name="choose-a-scenario"></a>Senaryo seçin

Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir. Bu durumda, senaryo `Price Prediction` ' dır.

1. **Çözüm Gezgini**, *taxifaretahmine* projesine sağ tıklayın ve **Ekle** > **Machine Learning**' yı seçin.
1. Model Oluşturucu aracının senaryo adımında *fiyat tahmini* senaryosu ' nı seçin.

## <a name="load-the-data"></a>Verileri yükleme

Model Oluşturucu, bir SQL Server veritabanı veya CSV ya da TSV biçimindeki yerel bir dosya olan iki kaynaktan verileri kabul eder.

1. Model Oluşturucu aracının veri adımında, veri kaynağı açılır listesinden *Dosya* ' yı seçin.
1. *Dosya Seç* metin kutusunun yanındaki düğmeyi seçin ve *veri* dizinindeki *Taxi-fare-test. csv* dosyasına gidip seçmek için dosya Gezgini 'ni kullanın
1. *Tahmin edilecek (etiket) açılan sütununda* *fare_amount* öğesini seçin ve model Oluşturucu aracının eğitme adımına gidin.
1. *Giriş sütunları (Özellikler)* açılan listesini genişletin ve eğitim sırasında bunu bir özellik olarak dışlamak için *trip_time_in_secs* sütununun işaretini kaldırın.

## <a name="train-the-model"></a>Modeli eğitme

Bu öğreticide fiyat tahmin modelini eğitmek için kullanılan makine öğrenimi görevi gerileme. Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı gerileme algoritmaları ve ayarları kullanarak modelleri ayrı ayrı işler.

Modelin eğitilmesi için gereken süre, veri miktarına müşterinizin istekleriyle orantılı. Model Oluşturucu, veri kaynağınızın boyutuna bağlı olarak, **tren süresi (saniye)** için varsayılan bir değer seçer.

1. Daha uzun bir süre eğmemeyi tercih etmediğiniz sürece varsayılan değeri *eğitme süresi (saniye)* olarak bırakın.
2. *Eğitimi Başlat*' ı seçin.

Eğitim süreci boyunca, ilerleme verileri eğitme adımının `Progress` bölümünde görüntülenir.

- Durum, eğitim sürecinin tamamlanma durumunu görüntüler.
- En iyi doğruluk, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde oluşan modelin doğruluğunu gösterir. Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.
- En iyi algoritma, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde gerçekleştirilen algoritmanın adını görüntüler.
- Son algoritma modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.

Eğitim tamamlandıktan sonra değerlendir adımına gidin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Eğitim adımının sonucu, en iyi performansa sahip bir model olacaktır. Model Oluşturucu aracının değerlendir adımında, çıkış *bölümü en iyi model girişinde en* iyi işlem modeli tarafından kullanılan algoritmayı *(RKARE)* içerir. Ayrıca, ilk beş modeli ve bunların ölçümlerini içeren bir Özet tablosu.

Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu denemeye yönelik bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır. Aksi takdirde, kod adımına gidin.

## <a name="add-the-code-to-make-predictions"></a>Tahminleri yapmak için kodu ekleyin

Eğitim sürecinin bir sonucu olarak iki proje oluşturulacaktır.

- TaxiFarePredictionML. ConsoleApp: model eğitimi ve örnek tüketim kodu içeren bir .NET Core konsol uygulaması.
- TaxiFarePredictionML. Model: giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini, eğitim sırasında en iyi gerçekleştirme modelinin kaydedilmiş sürümünü ve tahmine dayalı hale getirmek için `ConsumeModel` adlı bir yardımcı sınıfı içeren .NET Standard bir sınıf kitaplığı.

1. Model Oluşturucu aracının kod adımında, otomatik olarak oluşturulan projeleri çözüme eklemek için **Proje Ekle** ' yi seçin.
1. *Program.cs* dosyasını *Taxifaretahmin* projesinde açın.
1. *TaxiFarePredictionML. model* projesine başvurmak için aşağıdaki using ifadesini ekleyin:

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. Modeli kullanarak yeni verileri tahmin etmek için, uygulamanızın `Main` yöntemi içinde `ModelInput` sınıfının yeni bir örneğini oluşturun. Tarifeli havayolu tutarının girişin bir parçası olmadığına dikkat edin. Bunun nedeni, modelin tahmin oluşturması olacaktır. 

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

1. @No__t-1 sınıfından `Predict` yöntemini kullanın. @No__t-0 yöntemi, eğitilen modeli yükler, model için bir [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) oluşturur ve yeni verilerde tahmine dayalı hale getirmek için onu kullanır. 

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. Uygulamayı çalıştırın.

    Program tarafından oluşturulan çıkış aşağıdaki kod parçacığına benzemelidir:

    ```bash
    Predicted Fare: 14.96086
    ```

Oluşturulan projelere başka bir çözümün içinde daha sonraki bir zamanda başvurmanız gerekirse, bunları `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` dizininde bulabilirsiniz.

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
