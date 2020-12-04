---
title: LED yanıp sönmesi
description: .NET IoT kitaplıkları ile bir ışığı yakıp söndürme hakkında bilgi edinin.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 07a050c0655f9cae3d7f2b924c0dd07ac1c6c0b9
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96590062"
---
# <a name="blink-an-led"></a>LED yanıp sönmesi

Genel amaçlı g/ç (GıO) PIN 'leri ayrı ayrı denetlenebilir. Bu, LED 'Leri, geçişleri ve diğer durum bilgisi olan cihazları denetlemek için kullanışlıdır. Bu konu başlığında, net ve Raspberry Pi 'nizin GPıO PIN 'lerini kullanarak bir ışığı güçlendirin ve sürekli olarak yanıp söndürirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- 5 mm LED
- 330 Ω dirici
- Enine
- Atlatıcı kabloları
- Raspberry PI GıO ayırıcı pano (isteğe bağlı/önerilen)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a>Donanımı hazırlama

Aşağıdaki diyagramda gösterildiği gibi devre oluşturmak için donanım bileşenlerini kullanın:

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="IŞıĞı ve bir direnleyici ile bir devreni gösteren bir diyagram" lightbox="../media/rpi-led_bb.png":::

Yukarıdaki görüntüde aşağıdaki bağlantılar gösterilmektedir:

- GPıO 18 ila LED anode (uzun, pozitif lider)
- LED katode (kısa, negatif lider) 330 Ω direntor (her iki uçta)
- 330 Ω direntor (diğer uç)

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Uygulama oluşturma

Tercih ettiğiniz geliştirme ortamında aşağıdaki adımları uygulayın:

1. [.Net CLI](../../core/tools/dotnet-new.md) ya da [Visual Studio](../../core/tutorials/with-visual-studio.md)kullanarak yeni bir .NET konsol uygulaması oluşturun. *Blinköğreticisi* olarak adlandırın.

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. *Program.cs* dosyasının içeriğini aşağıdaki kodla değiştirin:

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    Yukarıdaki kodda:

    - [Using bildirimi](../../csharp/whats-new/csharp-8.md#using-declarations) bir örneği oluşturur `GpioController` . `using`Bildirim, nesnenin elden çıkarılmasını ve donanım kaynaklarının düzgün şekilde serbest bırakılacağını sağlar.
    - Çıktı için GPıO pin 18 ' i açıldı
    - `while`Döngü süresiz olarak çalışır. Her yineleme:
        1. GPıO pin 18 ' e bir değer yazar. `ledOn`True ise, `PinValue.High` (üzerine) yazar. Aksi takdirde, yazar `PinValue.Low` .
        1. Uyku 1000 ms.
        1. Değerini değiştirir `ledOn` .

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Dağıtım dizinine geçerek ve yürütülebilir dosyayı çalıştırarak uygulamayı Raspberry Pi üzerinde çalıştırın.

    ```bash
    ./BlinkTutorial
    ```

    Her saniye açık ve kapalı olarak yanıp sönüyor.

1. <kbd>CTRL + C</kbd>tuşlarına basarak Programı sonlandırın.

Tebrikler! Bir ışığı yakıp söndürmek için GıO kullandınız.

## <a name="get-the-source-code"></a>Kaynak kodunu alma

Bu öğreticinin kaynağı [GitHub ' da kullanılabilir](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Bir sensörden ortam koşullarını okumayı öğrenin](../tutorials/temp-sensor.md)
