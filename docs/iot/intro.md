---
title: .NET IoT kitaplıklarıyla IoT cihazları için uygulama geliştirme
description: .NET 'in IoT cihazlarına ve senaryolarına yönelik uygulamalar oluşturmak için nasıl kullanılabileceğini öğrenin.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: overview
ms.prod: dotnet
ms.openlocfilehash: 13460fdafbfd7ef4e047cb7537e832ae4039c614
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255437"
---
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a>.NET IoT kitaplıklarıyla IoT cihazları için uygulama geliştirme

.NET çeşitli platformlar ve mimarilerde çalışır. Raspberry PI ve Hummingboard gibi yaygın nesnelerin Interneti (IoT) panoları desteklenir. IoT uygulamaları genellikle sensörler, analog-dijital dönüştürücüler ve LCD cihazlar gibi özel donanımlar ile etkileşime geçin. .NET IoT kitaplıkları bu senaryoları etkinleştirir.

## <a name="video-overview"></a>Genel bakış videosu

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a>Kitaplıklar

.NET IoT kitaplıkları iki NuGet paketini oluşur:

- [System. Device. GIO](https://www.nuget.org/packages/System.Device.Gpio/)
- [IoT. Device. Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/)

### <a name="systemdevicegpio"></a>System. Device. GIO

`System.Device.Gpio` cihazları denetlemek için düşük düzeyli donanım PIN 'leri ile etkileşim kurmak için çeşitli protokolleri destekler. Bu modüller şunlardır:

- Genel amaçlı g/ç (GıO)
- Inter-Integrated devresi (ı2C)
- Seri çevre birimi arabirimi (SPI)
- Darbe genişliği modülasyonu (PWM)
- Seri bağlantı noktası

### <a name="iotdevicebindings"></a>IoT. Device. Bindings

`Iot.Device.Bindings`Paket:

* System. Device. GIO sarmalayarak uygulama geliştirmeyi kolaylaştırmak için [cihaz bağlamaları](https://github.com/dotnet/iot/blob/master/src/devices/README.md) içerir.
* Topluluk tarafından desteklenir ve sürekli olarak ek bağlamalar eklenir.

Yaygın olarak kullanılan cihaz bağlamaları şunları içerir:

- [Karakter LCD-LCD karakter gösterimi](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)
- [SN74HC595-8 bit kaydırma kaydı](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)
- [BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)
- [MAX7219-LED matris sürücüsü](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)
- [RGBLedMatrix-RGB LED matrisi](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)

## <a name="supported-operating-systems"></a>Desteklenen işletim sistemleri

`System.Device.Gpio` , ARM/ARM64 ve Windows 10 IoT Core 'u destekleyen çoğu Linux sürümünde desteklenir.

> [!TIP]
> Raspberry PI için, [Raspberry PI OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  (eski adıyla Raspbian) önerilir.

## <a name="supported-hardware-platforms"></a>Desteklenen donanım platformları

`System.Device.Gpio` , tek tahta platformlarıyla uyumludur. Önerilen platformlar Raspberry Pi (2 ve üzeri) ve Hummingboard ' dir. Uyumlu oldukları bilinen diğer platformlar, Beagteboard ve ODROıD ' dir.

BILGISAYAR platformları, USB-ZPE/ı2C Köprüsü kullanılarak desteklenir.

> [!IMPORTANT]
> .NET, Raspberry Pi 2 ' den önceki Raspberry Pi sıfır ve Raspberry PI cihazları dahil olmak üzere ARMv6 Architecture cihazlarında desteklenmez.

## <a name="resources"></a>Kaynaklar

- [GitHub 'da .NET IoT kitaplıkları](https://github.com/dotnet/iot)
