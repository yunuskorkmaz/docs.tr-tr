---
title: LCD üzerinde metin görüntüleme
description: .NET IoT kitaplıkları ile sıvı kristal ekran üzerinde karakterleri görüntülemeyi öğrenin.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 005b40a7d9f46b84fcd90541248f5f4fd243e612
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255561"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="display-text-on-an-lcd"></a>LCD üzerinde metin görüntüleme

LCD karakter görüntüleri, bir dış monitöre gerek olmadan bilgileri görüntülemek için yararlıdır. Yaygın LCD karakter görüntüleri, doğrudan GPıO PIN lerine bağlanabilir, ancak böyle bir yaklaşım, en fazla 10 adet GPıO PIN 'i kullanılmasını gerektirir. Bir cihaz birleşimine bağlanmayı gerektiren senaryolar için, GıO üst bilgisinin büyük bir kısmını bir karakter görüntüsüne aktarmak genellikle pratik değildir.

Birçok üretici, tümleşik bir GPıO genişleticiyle 20x4 LCD karakter görüntüleri satmaya sahiptir. Karakter görüntüsü doğrudan GPıO genişleticiye bağlanır ve bu da Inter-Integrated devre (ı2C) seri protokolü aracılığıyla Raspberry Pi 'ye bağlanır.

Bu konu başlığında, bir ı2C GPıO Genişleticisi kullanarak bir LCD karakter görüntüsüne metin göstermek için .NET kullanacaksınız.

## <a name="prerequisites"></a>Önkoşullar

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [20x4 LCD karakter gösterimi ve ı2C arabirim](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)
- Atlatıcı kabloları
- Enine (isteğe bağlı/önerilen)
- Raspberry PI GıO ayırıcı pano (isteğe bağlı/önerilen)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> LCD karakter ekranların birçok üreticisi vardır. Çoğu tasarım aynıdır ve üretici, işlevlerle ilgili herhangi bir farklılık yapmamalıdır. Bu öğretici, başvuru için [LCD2004 altında sunkiyle](https://www.sunfounder.com/lcd2004-module.html)geliştirilmiştir.

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>Donanımı hazırlama

I2C GıO genişleticisindeki dört PIN 'i şu şekilde Raspberry Pi 'ye bağlamak için atlatıcı kablolarını kullanın:

- ARKA plan
- VCC to 5 V
- SDA-SDA (GPıO 2)
- SCL-SCL (GPıO 3)

Gerektiğinde aşağıdaki rakamları inceleyin:

| I2C arabirimi (ekran geri) | Raspberry PI GıO |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="I2C GPıO genişleticiyi gösteren karakter görüntüsünün geri görüntüsünün bir görüntüsü." lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry PI GıO üstbilgisinin aşımını gösteren bir diyagram. Image hitap Raspberry PI Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br />[Image hitap Raspberry PI Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Uygulama oluşturma

Tercih ettiğiniz geliştirme ortamında aşağıdaki adımları uygulayın:

1. [.Net CLI](../../core/tools/dotnet-new.md) ya da [Visual Studio](../../core/tutorials/with-visual-studio.md)kullanarak yeni bir .NET konsol uygulaması oluşturun. *Lcdöğreticisi* olarak adlandırın.

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* dosyasının içeriğini aşağıdaki kodla değiştirin:

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    Yukarıdaki kodda:

    - [Using bildirimi](../../csharp/whats-new/csharp-8.md#using-declarations) `I2cDevice` `I2cDevice.Create` `I2cConnectionSettings` , ve parametreleriyle yeni bir ile çağırarak ve geçirerek bir örneği oluşturur `busId` `deviceAddress` . Bu `I2cDevice` , I2C veri yolunu temsil eder. `using`Bildirim, nesnenin elden çıkarılmasını ve donanım kaynaklarının düzgün şekilde serbest bırakılacağını sağlar.

        > [!WARNING]
        > GPıO genişleticisindeki cihaz adresi üretici tarafından kullanılan yongaya bağlıdır. PCF8574 ile donatılmış GıO Genişleticileri `0x27` , PCF8574A yongaları kullanan bir adresi kullanır `0x3F` . LCD belgelerinize başvurun.

    - Başka bir `using` bildirim bir örneği oluşturur `Pcf8574` ve oluşturucuya geçirir `I2cDevice` . Bu örnek, GPıO genişleticiyi temsil eder.
    - Başka bir `using` bildirim `Lcd2004` , görüntüsünü temsil etmek için bir örneği oluşturur. Çeşitli parametreler, GPıO genişleticiyle iletişim kurmak için kullanılacak ayarları açıklayan oluşturucuya geçirilir. GPıO Genişleticisi parametresi olarak geçirilir `controller` .
    - `while`Döngü süresiz olarak çalışır. Her yineleme:
        1. Ekranı temizler.
        1. İmleç konumunu geçerli satırdaki ilk konuma ayarlar.
        1. Geçerli imleç konumundaki görüntülenecek geçerli saati yazar.
        1. Geçerli satır sayacını yineler.
        1. Uyku 1000 ms.

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Dağıtım dizinine geçerek ve yürütülebilir dosyayı çalıştırarak uygulamayı Raspberry Pi üzerinde çalıştırın.

    ```bash
    ./LcdTutorial
    ```

    Her satırda geçerli saatin gösterdiği LCD karakter görüntüsünü gözlemleyin.

    > [!TIP]
    > Görüntü açık ise, ancak herhangi bir metin görmüyorsanız, ekran arkasında karşıtlık aramasını ayarlamayı deneyin.

1. <kbd>CTRL + C</kbd>tuşlarına basarak Programı sonlandırın.

Tebrikler! Bir LCD üzerinde bir ı2C ve GıO Genişleticisi kullanarak metin görüntüdiniz!

## <a name="get-the-source-code"></a>Kaynak kodunu alma

Bu öğreticinin kaynağı [GitHub ' da kullanılabilir](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial).

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Bir ışığı yakıp söndürmek için Genel Amaçlı giriş/çıkış kullanmayı öğrenin](../tutorials/blink-led.md)
