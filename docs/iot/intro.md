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
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a><span data-ttu-id="947dd-103">.NET IoT kitaplıklarıyla IoT cihazları için uygulama geliştirme</span><span class="sxs-lookup"><span data-stu-id="947dd-103">Develop apps for IoT devices with the .NET IoT Libraries</span></span>

<span data-ttu-id="947dd-104">.NET çeşitli platformlar ve mimarilerde çalışır.</span><span class="sxs-lookup"><span data-stu-id="947dd-104">.NET runs on a variety of platforms and architectures.</span></span> <span data-ttu-id="947dd-105">Raspberry PI ve Hummingboard gibi yaygın nesnelerin Interneti (IoT) panoları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="947dd-105">Common Internet of things (IoT) boards, such as Raspberry Pi and Hummingboard, are supported.</span></span> <span data-ttu-id="947dd-106">IoT uygulamaları genellikle sensörler, analog-dijital dönüştürücüler ve LCD cihazlar gibi özel donanımlar ile etkileşime geçin.</span><span class="sxs-lookup"><span data-stu-id="947dd-106">IoT apps typically interact with specialized hardware, such as sensors, analog-to-digital converters, and LCD devices.</span></span> <span data-ttu-id="947dd-107">.NET IoT kitaplıkları bu senaryoları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="947dd-107">The .NET IoT Libraries enable these scenarios.</span></span>

## <a name="video-overview"></a><span data-ttu-id="947dd-108">Genel bakış videosu</span><span class="sxs-lookup"><span data-stu-id="947dd-108">Video overview</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a><span data-ttu-id="947dd-109">Kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="947dd-109">Libraries</span></span>

<span data-ttu-id="947dd-110">.NET IoT kitaplıkları iki NuGet paketini oluşur:</span><span class="sxs-lookup"><span data-stu-id="947dd-110">The .NET IoT Libraries are composed of two NuGet packages:</span></span>

- [<span data-ttu-id="947dd-111">System. Device. GIO</span><span class="sxs-lookup"><span data-stu-id="947dd-111">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio/)
- [<span data-ttu-id="947dd-112">IoT. Device. Bindings</span><span class="sxs-lookup"><span data-stu-id="947dd-112">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings/)

### <a name="systemdevicegpio"></a><span data-ttu-id="947dd-113">System. Device. GIO</span><span class="sxs-lookup"><span data-stu-id="947dd-113">System.Device.Gpio</span></span>

<span data-ttu-id="947dd-114">`System.Device.Gpio` cihazları denetlemek için düşük düzeyli donanım PIN 'leri ile etkileşim kurmak için çeşitli protokolleri destekler.</span><span class="sxs-lookup"><span data-stu-id="947dd-114">`System.Device.Gpio` supports a variety of protocols for interacting with low-level hardware pins to control devices.</span></span> <span data-ttu-id="947dd-115">Bu modüller şunlardır:</span><span class="sxs-lookup"><span data-stu-id="947dd-115">These include:</span></span>

- <span data-ttu-id="947dd-116">Genel amaçlı g/ç (GıO)</span><span class="sxs-lookup"><span data-stu-id="947dd-116">General-purpose I/O (GPIO)</span></span>
- <span data-ttu-id="947dd-117">Inter-Integrated devresi (ı2C)</span><span class="sxs-lookup"><span data-stu-id="947dd-117">Inter-Integrated Circuit (I2C)</span></span>
- <span data-ttu-id="947dd-118">Seri çevre birimi arabirimi (SPI)</span><span class="sxs-lookup"><span data-stu-id="947dd-118">Serial Peripheral Interface (SPI)</span></span>
- <span data-ttu-id="947dd-119">Darbe genişliği modülasyonu (PWM)</span><span class="sxs-lookup"><span data-stu-id="947dd-119">Pulse Width Modulation (PWM)</span></span>
- <span data-ttu-id="947dd-120">Seri bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="947dd-120">Serial port</span></span>

### <a name="iotdevicebindings"></a><span data-ttu-id="947dd-121">IoT. Device. Bindings</span><span class="sxs-lookup"><span data-stu-id="947dd-121">Iot.Device.Bindings</span></span>

<span data-ttu-id="947dd-122">`Iot.Device.Bindings`Paket:</span><span class="sxs-lookup"><span data-stu-id="947dd-122">The `Iot.Device.Bindings` package:</span></span>

* <span data-ttu-id="947dd-123">System. Device. GIO sarmalayarak uygulama geliştirmeyi kolaylaştırmak için [cihaz bağlamaları](https://github.com/dotnet/iot/blob/master/src/devices/README.md) içerir.</span><span class="sxs-lookup"><span data-stu-id="947dd-123">Contains [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) to streamline app development by wrapping System.Device.Gpio.</span></span>
* <span data-ttu-id="947dd-124">Topluluk tarafından desteklenir ve sürekli olarak ek bağlamalar eklenir.</span><span class="sxs-lookup"><span data-stu-id="947dd-124">Is community-supported, and additional bindings are added continually.</span></span>

<span data-ttu-id="947dd-125">Yaygın olarak kullanılan cihaz bağlamaları şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="947dd-125">Commonly used device bindings include:</span></span>

- [<span data-ttu-id="947dd-126">Karakter LCD-LCD karakter gösterimi</span><span class="sxs-lookup"><span data-stu-id="947dd-126">CharacterLcd - LCD character display</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)
- [<span data-ttu-id="947dd-127">SN74HC595-8 bit kaydırma kaydı</span><span class="sxs-lookup"><span data-stu-id="947dd-127">SN74HC595 - 8-bit shift register</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)
- [<span data-ttu-id="947dd-128">BrickPi3</span><span class="sxs-lookup"><span data-stu-id="947dd-128">BrickPi3</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)
- [<span data-ttu-id="947dd-129">MAX7219-LED matris sürücüsü</span><span class="sxs-lookup"><span data-stu-id="947dd-129">Max7219 - LED Matrix driver</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)
- [<span data-ttu-id="947dd-130">RGBLedMatrix-RGB LED matrisi</span><span class="sxs-lookup"><span data-stu-id="947dd-130">RGBLedMatrix - RGB LED Matrix</span></span>](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)

## <a name="supported-operating-systems"></a><span data-ttu-id="947dd-131">Desteklenen işletim sistemleri</span><span class="sxs-lookup"><span data-stu-id="947dd-131">Supported operating systems</span></span>

<span data-ttu-id="947dd-132">`System.Device.Gpio` , ARM/ARM64 ve Windows 10 IoT Core 'u destekleyen çoğu Linux sürümünde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="947dd-132">`System.Device.Gpio` is supported on most versions of Linux that support ARM/ARM64 and Windows 10 IoT Core.</span></span>

> [!TIP]
> <span data-ttu-id="947dd-133">Raspberry PI için, [Raspberry PI OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  (eski adıyla Raspbian) önerilir.</span><span class="sxs-lookup"><span data-stu-id="947dd-133">For Raspberry Pi, [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  (formerly Raspbian) is recommended.</span></span>

## <a name="supported-hardware-platforms"></a><span data-ttu-id="947dd-134">Desteklenen donanım platformları</span><span class="sxs-lookup"><span data-stu-id="947dd-134">Supported hardware platforms</span></span>

<span data-ttu-id="947dd-135">`System.Device.Gpio` , tek tahta platformlarıyla uyumludur.</span><span class="sxs-lookup"><span data-stu-id="947dd-135">`System.Device.Gpio` is compatible with most single-board platforms.</span></span> <span data-ttu-id="947dd-136">Önerilen platformlar Raspberry Pi (2 ve üzeri) ve Hummingboard ' dir.</span><span class="sxs-lookup"><span data-stu-id="947dd-136">Recommended platforms are Raspberry Pi (2 and greater) and Hummingboard.</span></span> <span data-ttu-id="947dd-137">Uyumlu oldukları bilinen diğer platformlar, Beagteboard ve ODROıD ' dir.</span><span class="sxs-lookup"><span data-stu-id="947dd-137">Other platforms known to be compatible are BeagleBoard and ODROID.</span></span>

<span data-ttu-id="947dd-138">BILGISAYAR platformları, USB-ZPE/ı2C Köprüsü kullanılarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="947dd-138">PC platforms are supported via the use of a USB to SPI/I2C bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="947dd-139">.NET, Raspberry Pi 2 ' den önceki Raspberry Pi sıfır ve Raspberry PI cihazları dahil olmak üzere ARMv6 Architecture cihazlarında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="947dd-139">.NET is not supported on ARMv6 architecture devices, including Raspberry Pi Zero and Raspberry Pi devices prior to Raspberry Pi 2.</span></span>

## <a name="resources"></a><span data-ttu-id="947dd-140">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="947dd-140">Resources</span></span>

- [<span data-ttu-id="947dd-141">GitHub 'da .NET IoT kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="947dd-141">.NET IoT Libraries on Github</span></span>](https://github.com/dotnet/iot)
