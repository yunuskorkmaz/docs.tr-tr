---
title: Analogdan dijitale dönüştürücüdeki değerleri okuma
description: Bir analog-dijital dönüştürücü kullanarak değişken voltaj değerlerini okumayı öğrenin.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 7cf25f181997ed66639842727be57e7824ef5466
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739993"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="read-values-from-an-analog-to-digital-converter"></a>Analogdan dijitale dönüştürücüdeki değerleri okuma

Örneksel-dijital Dönüştürücüsü (ADC), bir analog giriş gerilimi değerini okuyabilen ve bunu dijital bir değere dönüştürebileceğiniz bir cihazdır. ADCs, Potentiometers ve belirli koşullara göre direnci değiştiren diğer cihazlardan değerleri okumak için kullanılır.

Bu konu başlığında, bir potentiometer ile giriş gerilimi 'ı modüle olduğunuz için bir ADC 'nin değerlerini okumak üzere .NET kullanacaksınız.

## <a name="prerequisites"></a>Önkoşullar

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [MCP3008](https://www.microchip.com/wwwproducts/MCP3008) <span class="docon docon-navigate-external x-hidden-focus"></span> Analog-Dijital dönüştürücüsü
- Üç pin potentiometer
- Enine
- Atlatıcı kabloları
- Raspberry PI GıO ayırıcı pano (isteğe bağlı/önerilen)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a>Donanımı hazırlama

Aşağıdaki diyagramda gösterildiği gibi devre oluşturmak için donanım bileşenlerini kullanın:

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="MCP3008 ADC ve potentiometer ile bir bağlantı hattını gösteren eğiz diyagramı" lightbox="../media/rpi-trimpot_spi.png":::

MCP3008, iletişim kurmak için seri çevre birimi arabirimini (SPI) kullanır. MCP3008, Raspberry Pi ve potentiometer arasındaki bağlantılar aşağıda verilmiştir:

- V<sub>dd</sub> -3.3 $ (kırmızı renkte gösterilir)
- V<sub>ref</sub> -3.3 v (kırmızı)
- AGND-zemin (siyah)
- CLK-SCLK (turuncu)
- D<sub>/</sub> miso (turuncu)
- D<sub>-</sub> Mosi (turuncu)
- CS/SHDN to CE0 (yeşil)
- DZEDEN zemin (siyah)
- Potentiometer (sarı) CH0 to Variable (ortadaki) sabitleme

3.3 ve potentiometer üzerindeki dış PIN 'leri belirtin. Sıra önemli değildir.

Gerektiğinde aşağıdaki çıkış diyagramlarına başvurun:

| MCP3008  | Raspberry PI GıO |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="MCP3008 'ın Pinsiz gösteren bir diyagram" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry PI GıO üstbilgisinin aşımını gösteren bir diyagram. Image hitap Raspberry PI Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br />[Image hitap Raspberry PI Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Uygulama oluşturma

Tercih ettiğiniz geliştirme ortamında aşağıdaki adımları uygulayın:

1. [.Net CLI](../../core/tools/dotnet-new.md) ya da [Visual Studio](../../core/tutorials/with-visual-studio.md)kullanarak yeni bir .NET konsol uygulaması oluşturun. *Adcöğreticisi* olarak adlandırın.

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* dosyasının içeriğini aşağıdaki kodla değiştirin:

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    Yukarıdaki kodda:

    - `hardwareSpiSettings` Yeni bir örneğine ayarlanır `SpiConnectionSettings` . Oluşturucu `busId` parametresini 0 ve `chipSelectLine` parametresini 0 olarak ayarlar.
    - [Using bildirimi](../../csharp/whats-new/csharp-8.md#using-declarations) , `SpiDevice` çağırarak ve geçirerek bir örneği oluşturur `SpiDevice.Create` `hardwareSpiSettings` . Bu `SpiDevice` , SPI veri yolunu temsil eder. `using`Bildirim, nesnenin elden çıkarılmasını ve donanım kaynaklarının düzgün şekilde serbest bırakılacağını sağlar.
    - Başka bir `using` bildirim bir örneği oluşturur `Mcp3008` ve oluşturucuya geçirir `SpiDevice` .
    - `while`Döngü süresiz olarak çalışır. Her yineleme:
        1. Çağırarak CH0 değerini ADC üzerinde okur `mcp.Read(0)` .
        1. Değeri 10,24 olarak böler. MCP3008 10 bit bir ADC olduğundan, bu, 1024 arası olası 0-1023 değerleri döndürdüğü anlamına gelir. Değerin 10,24 olarak bölünerek değeri yüzde olarak temsil eder.
        1. Değeri en yakın tamsayıya yuvarlar.
        1. Değeri yüzde olarak biçimlendirilen konsola yazar.
        1. Uyku 500 MS.

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Dağıtım dizinine geçerek ve yürütülebilir dosyayı çalıştırarak uygulamayı Raspberry Pi üzerinde çalıştırın.

    ```bash
    ./AdcTutorial
    ```

    Potentiometer aramasını döndürürken çıktıyı gözlemleyin. Bunun nedeni, potentiometer tarafından sağlanan gerilimi 'ın ADC üzerinde CH0. ADC, CH0 üzerindeki giriş gerilimi değerini V<sub>başvurusuna</sub> sağlanan başvuru gerilimi ile karşılaştırarak bir değer oluşturur.

1. <kbd>CTRL + C</kbd>tuşlarına basarak Programı sonlandırın.

Tebrikler! Verileri bir analog-dijital dönüştürücüden okumak için SPI kullandınız.

## <a name="get-the-source-code"></a>Kaynak kodunu alma

Bu öğreticinin kaynağı [GitHub ' da kullanılabilir](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Bir ışığı yakıp söndürmek için Genel Amaçlı giriş/çıkış kullanmayı öğrenin](../tutorials/blink-led.md)
