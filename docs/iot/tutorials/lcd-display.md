---
title: LCD üzerinde metin görüntüleme
description: .NET IoT kitaplıkları ile sıvı kristal ekran üzerinde karakterleri görüntülemeyi öğrenin.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: d4c3e373207e23877903491871f4d09e11000c1a
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96590053"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="display-text-on-an-lcd"></a><span data-ttu-id="0ad45-103">LCD üzerinde metin görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0ad45-103">Display text on an LCD</span></span>

<span data-ttu-id="0ad45-104">LCD karakter görüntüleri, bir dış monitöre gerek olmadan bilgileri görüntülemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ad45-104">LCD character displays are useful for displaying information without the need for an external monitor.</span></span> <span data-ttu-id="0ad45-105">Yaygın LCD karakter görüntüleri, doğrudan GPıO PIN lerine bağlanabilir, ancak böyle bir yaklaşım, en fazla 10 adet GPıO PIN 'i kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0ad45-105">Common LCD character displays can be connected directly to the GPIO pins, but such an approach requires the use of up to 10 GPIO pins.</span></span> <span data-ttu-id="0ad45-106">Bir cihaz birleşimine bağlanmayı gerektiren senaryolar için, GıO üst bilgisinin büyük bir kısmını bir karakter görüntüsüne aktarmak genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="0ad45-106">For scenarios that require connecting to a combination of devices, devoting so much of the GPIO header to a character display is often impractical.</span></span>

<span data-ttu-id="0ad45-107">Birçok üretici, tümleşik bir GPıO genişleticiyle 20x4 LCD karakter görüntüleri satmaya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0ad45-107">Many manufacturers sell 20x4 LCD character displays with an integrated GPIO expander.</span></span> <span data-ttu-id="0ad45-108">Karakter görüntüsü doğrudan GPıO genişleticiye bağlanır ve bu da Inter-Integrated devre (ı2C) seri protokolü aracılığıyla Raspberry Pi 'ye bağlanır.</span><span class="sxs-lookup"><span data-stu-id="0ad45-108">The character display connects directly to the GPIO expander, which then connects to the Raspberry Pi via the Inter-Integrated Circuit (I2C) serial protocol.</span></span>

<span data-ttu-id="0ad45-109">Bu konu başlığında, bir ı2C GPıO Genişleticisi kullanarak bir LCD karakter görüntüsüne metin göstermek için .NET kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0ad45-109">In this topic, you will use .NET to display text on an LCD character display using an I2C GPIO expander.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0ad45-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0ad45-110">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="0ad45-111">[20x4 LCD karakter gösterimi ve I2C arabirim](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="0ad45-111">[20x4 LCD Character Display with I2C interface](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="0ad45-112">Atlatıcı kabloları</span><span class="sxs-lookup"><span data-stu-id="0ad45-112">Jumper wires</span></span>
- <span data-ttu-id="0ad45-113">Enine (isteğe bağlı/önerilen)</span><span class="sxs-lookup"><span data-stu-id="0ad45-113">Breadboard (optional/recommended)</span></span>
- <span data-ttu-id="0ad45-114">Raspberry PI GıO ayırıcı pano (isteğe bağlı/önerilen)</span><span class="sxs-lookup"><span data-stu-id="0ad45-114">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> <span data-ttu-id="0ad45-115">LCD karakter ekranların birçok üreticisi vardır.</span><span class="sxs-lookup"><span data-stu-id="0ad45-115">There are many manufacturers of LCD character displays.</span></span> <span data-ttu-id="0ad45-116">Çoğu tasarım aynıdır ve üretici, işlevlerle ilgili herhangi bir farklılık yapmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ad45-116">Most designs are identical, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="0ad45-117">Bu öğretici, başvuru için [LCD2004 altında sunkiyle](https://www.sunfounder.com/lcd2004-module.html) geliştirilmiştir <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="0ad45-117">For reference, this tutorial was developed with the [SunFounder LCD2004](https://www.sunfounder.com/lcd2004-module.html) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="0ad45-118">Donanımı hazırlama</span><span class="sxs-lookup"><span data-stu-id="0ad45-118">Prepare the hardware</span></span>

<span data-ttu-id="0ad45-119">I2C GıO genişleticisindeki dört PIN 'i şu şekilde Raspberry Pi 'ye bağlamak için atlatıcı kablolarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="0ad45-119">Use jumper wires to connect the four pins on the I2C GPIO expander to the Raspberry Pi as follows:</span></span>

- <span data-ttu-id="0ad45-120">ARKA plan</span><span class="sxs-lookup"><span data-stu-id="0ad45-120">GND to ground</span></span>
- <span data-ttu-id="0ad45-121">VCC to 5 V</span><span class="sxs-lookup"><span data-stu-id="0ad45-121">VCC to 5V</span></span>
- <span data-ttu-id="0ad45-122">SDA-SDA (GPıO 2)</span><span class="sxs-lookup"><span data-stu-id="0ad45-122">SDA to SDA (GPIO 2)</span></span>
- <span data-ttu-id="0ad45-123">SCL-SCL (GPıO 3)</span><span class="sxs-lookup"><span data-stu-id="0ad45-123">SCL to SCL (GPIO 3)</span></span>

<span data-ttu-id="0ad45-124">Gerektiğinde aşağıdaki rakamları inceleyin:</span><span class="sxs-lookup"><span data-stu-id="0ad45-124">Refer to the following figures as needed:</span></span>

| <span data-ttu-id="0ad45-125">I2C arabirimi (ekran geri)</span><span class="sxs-lookup"><span data-stu-id="0ad45-125">I2C interface (back of display)</span></span> | <span data-ttu-id="0ad45-126">Raspberry PI GıO</span><span class="sxs-lookup"><span data-stu-id="0ad45-126">Raspberry Pi GPIO</span></span> |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="I2C GPıO genişleticiyi gösteren karakter görüntüsünün geri görüntüsünün bir görüntüsü." lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry PI GıO üstbilgisinin aşımını gösteren bir diyagram. Image hitap Raspberry PI Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="0ad45-129">[Image hitap Raspberry PI Foundation](https://www.raspberrypi.org/documentation/usage/gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="0ad45-129">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="0ad45-130">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ad45-130">Create the app</span></span>

<span data-ttu-id="0ad45-131">Tercih ettiğiniz geliştirme ortamında aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="0ad45-131">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="0ad45-132">[.Net CLI](../../core/tools/dotnet-new.md) ya da [Visual Studio](../../core/tutorials/with-visual-studio.md)kullanarak yeni bir .NET konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ad45-132">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="0ad45-133">*Lcdöğreticisi* olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="0ad45-133">Name it *LcdTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="0ad45-134">*Program.cs* dosyasının içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0ad45-134">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    <span data-ttu-id="0ad45-135">Yukarıdaki kodda:</span><span class="sxs-lookup"><span data-stu-id="0ad45-135">In the preceding code:</span></span>

    - <span data-ttu-id="0ad45-136">[Using bildirimi](../../csharp/whats-new/csharp-8.md#using-declarations) `I2cDevice` `I2cDevice.Create` `I2cConnectionSettings` , ve parametreleriyle yeni bir ile çağırarak ve geçirerek bir örneği oluşturur `busId` `deviceAddress` .</span><span class="sxs-lookup"><span data-stu-id="0ad45-136">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in a new `I2cConnectionSettings` with the `busId` and `deviceAddress` parameters.</span></span> <span data-ttu-id="0ad45-137">Bu `I2cDevice` , I2C veri yolunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ad45-137">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="0ad45-138">`using`Bildirim, nesnenin elden çıkarılmasını ve donanım kaynaklarının düzgün şekilde serbest bırakılacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ad45-138">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>

        > [!WARNING]
        > <span data-ttu-id="0ad45-139">GPıO genişleticisindeki cihaz adresi üretici tarafından kullanılan yongaya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ad45-139">The device address for the GPIO expander depends on the chip used by the manufacturer.</span></span> <span data-ttu-id="0ad45-140">PCF8574 ile donatılmış GıO Genişleticileri `0x27` , PCF8574A yongaları kullanan bir adresi kullanır `0x3F` .</span><span class="sxs-lookup"><span data-stu-id="0ad45-140">GPIO expanders equipped with a PCF8574 use the address `0x27`, while those using PCF8574A chips use `0x3F`.</span></span> <span data-ttu-id="0ad45-141">LCD belgelerinize başvurun.</span><span class="sxs-lookup"><span data-stu-id="0ad45-141">Consult your LCD's documentation.</span></span>

    - <span data-ttu-id="0ad45-142">Başka bir `using` bildirim bir örneği oluşturur `Pcf8574` ve oluşturucuya geçirir `I2cDevice` .</span><span class="sxs-lookup"><span data-stu-id="0ad45-142">Another `using` declaration creates an instance of `Pcf8574` and passes the `I2cDevice` into the constructor.</span></span> <span data-ttu-id="0ad45-143">Bu örnek, GPıO genişleticiyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ad45-143">This instance represents the GPIO expander.</span></span>
    - <span data-ttu-id="0ad45-144">Başka bir `using` bildirim `Lcd2004` , görüntüsünü temsil etmek için bir örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ad45-144">Another `using` declaration creates an instance of `Lcd2004` to represent the display.</span></span> <span data-ttu-id="0ad45-145">Çeşitli parametreler, GPıO genişleticiyle iletişim kurmak için kullanılacak ayarları açıklayan oluşturucuya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0ad45-145">Several parameters are passed to the constructor describing the settings to use to communicate with the GPIO expander.</span></span> <span data-ttu-id="0ad45-146">GPıO Genişleticisi parametresi olarak geçirilir `controller` .</span><span class="sxs-lookup"><span data-stu-id="0ad45-146">The GPIO expander is passed as the `controller` parameter.</span></span>
    - <span data-ttu-id="0ad45-147">`while`Döngü süresiz olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="0ad45-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="0ad45-148">Her yineleme:</span><span class="sxs-lookup"><span data-stu-id="0ad45-148">Each iteration:</span></span>
        1. <span data-ttu-id="0ad45-149">Ekranı temizler.</span><span class="sxs-lookup"><span data-stu-id="0ad45-149">Clears the display.</span></span>
        1. <span data-ttu-id="0ad45-150">İmleç konumunu geçerli satırdaki ilk konuma ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0ad45-150">Sets the cursor position to the first position on the current line.</span></span>
        1. <span data-ttu-id="0ad45-151">Geçerli imleç konumundaki görüntülenecek geçerli saati yazar.</span><span class="sxs-lookup"><span data-stu-id="0ad45-151">Writes the current time to the display at the current cursor position.</span></span>
        1. <span data-ttu-id="0ad45-152">Geçerli satır sayacını yineler.</span><span class="sxs-lookup"><span data-stu-id="0ad45-152">Iterates the current line counter.</span></span>
        1. <span data-ttu-id="0ad45-153">Uyku 1000 ms.</span><span class="sxs-lookup"><span data-stu-id="0ad45-153">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="0ad45-154">Dağıtım dizinine geçerek ve yürütülebilir dosyayı çalıştırarak uygulamayı Raspberry Pi üzerinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0ad45-154">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./LcdTutorial
    ```

    <span data-ttu-id="0ad45-155">Her satırda geçerli saatin gösterdiği LCD karakter görüntüsünü gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="0ad45-155">Observe the LCD character display as the current time displays on each line.</span></span>

    > [!TIP]
    > <span data-ttu-id="0ad45-156">Görüntü açık ise, ancak herhangi bir metin görmüyorsanız, ekran arkasında karşıtlık aramasını ayarlamayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="0ad45-156">If the display is lit but you don't see any text, try adjusting the contrast dial on the back of the display.</span></span>

1. <span data-ttu-id="0ad45-157"><kbd>CTRL + C</kbd>tuşlarına basarak Programı sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="0ad45-157">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="0ad45-158">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="0ad45-158">Congratulations!</span></span> <span data-ttu-id="0ad45-159">Bir LCD üzerinde bir ı2C ve GıO Genişleticisi kullanarak metin görüntüdiniz!</span><span class="sxs-lookup"><span data-stu-id="0ad45-159">You've displayed text on an LCD using a I2C and a GPIO expander!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="0ad45-160">Kaynak kodunu alma</span><span class="sxs-lookup"><span data-stu-id="0ad45-160">Get the source code</span></span>

<span data-ttu-id="0ad45-161">Bu öğreticinin kaynağı [GitHub ' da kullanılabilir](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="0ad45-161">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0ad45-162">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0ad45-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0ad45-163">Bir ışığı yakıp söndürmek için Genel Amaçlı giriş/çıkış kullanmayı öğrenin</span><span class="sxs-lookup"><span data-stu-id="0ad45-163">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
