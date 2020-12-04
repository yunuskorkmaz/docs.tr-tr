---
title: Sensörden ortam koşullarını okuma
description: .NET IoT kitaplıkları ile termpsilinebilir, Barometrik basıncı ve nem oranını nasıl okuyacağınızı öğrenin.
author: camsoper
ms.author: casoper
ms.date: 11/14/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 1270e7629e9afc12b1d76d260d4b8b51428f1040
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96590065"
---
# <a name="read-environmental-conditions-from-a-sensor"></a>Sensörden ortam koşullarını okuma

IoT cihazlarının en yaygın senaryolarından biri çevresel koşulların algılanması. Sıcaklık, nem, Barometrik basıncı ve daha fazlasını izlemek için çeşitli sensör mevcuttur.

Bu konu başlığında, bir sensörden ortam koşullarını okumak için .NET kullanacaksınız.

## <a name="prerequisites"></a>Önkoşullar

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> nem/barometrik basınç/sıcaklık algılayıcısı
- Atlatıcı kabloları
- Enine (isteğe bağlı)
- Raspberry PI GıO ayırıcı panosu (isteğe bağlı)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> BME280 ayırıcıların birçok üreticisi vardır. Çoğu tasarım benzerdir ve üretici, işlevselliğe herhangi bir farklılık yapmamalıdır. Bu öğreticide, Çeşitlemeler hesaba deniyor. BME280 ayırıcılarınızın Inter-Integrated devre (ı2C) arabirimi içerdiğinden emin olun.

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>Donanımı hazırlama

Aşağıdaki diyagramda gösterildiği gibi devre oluşturmak için donanım bileşenlerini kullanın:

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Raspberry Pi ile BME280 breakbir tahtaya bağlantıyı gösteren eğime diyagramı" lightbox="../media/rpi-bmp280_i2c.png":::

Aşağıda, Raspberry Pi 'den BME280 ayırıcıya olan bağlantılar verilmiştir:

- 3.3 */VIN veya* 3v3 (kırmızı renkte gösterilir)
- Zemin-plan (siyah)
- SDA (GPıO 2)-SDI *veya* sda (mavi)
- SCL (GPıO 3)-SCK *veya* SCL (turuncu)

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Uygulama oluşturma

Tercih ettiğiniz geliştirme ortamında aşağıdaki adımları uygulayın:

1. [.Net CLI](../../core/tools/dotnet-new.md) ya da [Visual Studio](../../core/tutorials/with-visual-studio.md)kullanarak yeni bir .NET konsol uygulaması oluşturun. *Sensoröğreticisi* olarak adlandırın.

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* dosyasının içeriğini aşağıdaki kodla değiştirin:

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    Yukarıdaki kodda:

    - `i2cSettings` Yeni bir örneğine ayarlanır `I2cConnectionSettings` . Oluşturucu `busId` parametresini 1 olarak ve `deviceAddress` parametresini olarak ayarlar `Bme280.DefaultI2cAddress` .

        > [!IMPORTANT]
        > Bazı BME280 breaküreticileri ikincil adres değerini kullanır. Bu cihazlar için kullanın `Bme280.SecondaryI2cAddress` .

    - [Using bildirimi](../../csharp/whats-new/csharp-8.md#using-declarations) , `I2cDevice` çağırarak ve geçirerek bir örneği oluşturur `I2cDevice.Create` `i2cSettings` . Bu `I2cDevice` , I2C veri yolunu temsil eder. `using`Bildirim, nesnenin elden çıkarılmasını ve donanım kaynaklarının düzgün şekilde serbest bırakılacağını sağlar.
    - Başka bir `using` bildirim `Bme280` , algılayıcısı temsil etmek için bir örneği oluşturur. , `I2cDevice` Oluşturucuya geçirilir.
    - Yongasının, yongasının geçerli (varsayılan) ayarlarıyla ölçümleri yapması için gereken süre, çağırarak alınır `GetMeasurementDuration` .
    - `while`Döngü süresiz olarak çalışır. Her yineleme:
        1. Konsolunu temizler.
        1. Güç modunu olarak ayarlar `Bmx280PowerMode.Forced` . Bu, yonganın tek bir ölçüm gerçekleştirmesini, sonuçları depolamasını ve sonra uykuya geçmesini zorlar.
        1. Sıcaklık, basınç, nem ve yükseklik değerlerini okur.

            > [!NOTE]
            > Yükseklik, cihaz bağlama tarafından hesaplanır. ' Nin bu aşırı yüklemesi, `TryReadAltitude` bir tahmin oluşturmak için ortalama deniz düzeyinde basınç kullanır.

        1. Geçerli ortam koşullarını konsola yazar.
        1. Uyku 1000 ms.

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Dağıtım dizinine geçerek ve yürütülebilir dosyayı çalıştırarak uygulamayı Raspberry Pi üzerinde çalıştırın.

    ```bash
    ./SensorTutorial
    ```

    Konsolundaki algılayıcı çıkışını gözlemleyin.

1. <kbd>CTRL + C</kbd>tuşlarına basarak Programı sonlandırın.

Tebrikler! Sıcaklık/nem/barometrik basınç algılayıcısındaki değerleri okumak için ı2C 'yi kullandınız!

## <a name="get-the-source-code"></a>Kaynak kodunu alma

Bu öğreticinin kaynağı [GitHub ' da kullanılabilir](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Bir LCD üzerinde metin görüntülemeyi öğrenin](../tutorials/lcd-display.md)
