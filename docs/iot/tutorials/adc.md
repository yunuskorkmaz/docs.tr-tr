---
title: Analogdan dijitale dönüştürücüdeki değerleri okuma
description: Bir analog-dijital dönüştürücü kullanarak değişken voltaj değerlerini okumayı öğrenin.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 509616e3423fbb83b74bfbb8ecec1a7df49f0a20
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259752"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="read-values-from-an-analog-to-digital-converter"></a><span data-ttu-id="0ed85-103">Analogdan dijitale dönüştürücüdeki değerleri okuma</span><span class="sxs-lookup"><span data-stu-id="0ed85-103">Read values from an analog-to-digital converter</span></span>

<span data-ttu-id="0ed85-104">Örneksel-dijital Dönüştürücüsü (ADC), bir analog giriş gerilimi değerini okuyabilen ve bunu dijital bir değere dönüştürebileceğiniz bir cihazdır.</span><span class="sxs-lookup"><span data-stu-id="0ed85-104">An analog-to-digital converter (ADC) is a device that can read an analog input voltage value and convert it into a digital value.</span></span> <span data-ttu-id="0ed85-105">ADCs, Potentiometers ve belirli koşullara göre direnci değiştiren diğer cihazlardan değerleri okumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ed85-105">ADCs are used for reading values from thermistors, potentiometers, and other devices that change resistance based on certain conditions.</span></span>

<span data-ttu-id="0ed85-106">Bu konu başlığında, bir potentiometer ile giriş gerilimi 'ı modüle olduğunuz için bir ADC 'nin değerlerini okumak üzere .NET kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0ed85-106">In this topic, you will use .NET to read values from an ADC as you modulate the input voltage with a potentiometer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0ed85-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0ed85-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="0ed85-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) analog-dijital Dönüştürücüsü</span><span class="sxs-lookup"><span data-stu-id="0ed85-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) analog-to-digital converter</span></span>
- <span data-ttu-id="0ed85-109">Üç pin potentiometer</span><span class="sxs-lookup"><span data-stu-id="0ed85-109">Three-pin potentiometer</span></span>
- <span data-ttu-id="0ed85-110">Enine</span><span class="sxs-lookup"><span data-stu-id="0ed85-110">Breadboard</span></span>
- <span data-ttu-id="0ed85-111">Atlatıcı kabloları</span><span class="sxs-lookup"><span data-stu-id="0ed85-111">Jumper wires</span></span>
- <span data-ttu-id="0ed85-112">Raspberry PI GıO ayırıcı pano (isteğe bağlı/önerilen)</span><span class="sxs-lookup"><span data-stu-id="0ed85-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="0ed85-113">Donanımı hazırlama</span><span class="sxs-lookup"><span data-stu-id="0ed85-113">Prepare the hardware</span></span>

<span data-ttu-id="0ed85-114">Aşağıdaki diyagramda gösterildiği gibi devre oluşturmak için donanım bileşenlerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="0ed85-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="MCP3008 ADC ve potentiometer ile bir bağlantı hattını gösteren eğiz diyagramı" lightbox="../media/rpi-trimpot_spi.png":::

<span data-ttu-id="0ed85-116">MCP3008, iletişim kurmak için seri çevre birimi arabirimini (SPI) kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ed85-116">The MCP3008 uses Serial Peripheral Interface (SPI) to communicate.</span></span> <span data-ttu-id="0ed85-117">MCP3008, Raspberry Pi ve potentiometer arasındaki bağlantılar aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0ed85-117">The following are the connections from the MCP3008 to the Raspberry Pi and potentiometer:</span></span>

- <span data-ttu-id="0ed85-118">V<sub>dd</sub> -3.3 $ (kırmızı renkte gösterilir)</span><span class="sxs-lookup"><span data-stu-id="0ed85-118">V<sub>DD</sub> to 3.3V (shown in red)</span></span>
- <span data-ttu-id="0ed85-119">V<sub>ref</sub> -3.3 v (kırmızı)</span><span class="sxs-lookup"><span data-stu-id="0ed85-119">V<sub>REF</sub> to 3.3V (red)</span></span>
- <span data-ttu-id="0ed85-120">AGND-zemin (siyah)</span><span class="sxs-lookup"><span data-stu-id="0ed85-120">AGND to ground (black)</span></span>
- <span data-ttu-id="0ed85-121">CLK-SCLK (turuncu)</span><span class="sxs-lookup"><span data-stu-id="0ed85-121">CLK to SCLK (orange)</span></span>
- <span data-ttu-id="0ed85-122">D<sub>/</sub> miso (turuncu)</span><span class="sxs-lookup"><span data-stu-id="0ed85-122">D<sub>OUT</sub> to MISO (orange)</span></span>
- <span data-ttu-id="0ed85-123">D<sub>-</sub> Mosi (turuncu)</span><span class="sxs-lookup"><span data-stu-id="0ed85-123">D<sub>IN</sub> to MOSI (orange)</span></span>
- <span data-ttu-id="0ed85-124">CS/SHDN to CE0 (yeşil)</span><span class="sxs-lookup"><span data-stu-id="0ed85-124">CS/SHDN to CE0 (green)</span></span>
- <span data-ttu-id="0ed85-125">DZEDEN zemin (siyah)</span><span class="sxs-lookup"><span data-stu-id="0ed85-125">DGND to ground (black)</span></span>
- <span data-ttu-id="0ed85-126">Potentiometer (sarı) CH0 to Variable (ortadaki) sabitleme</span><span class="sxs-lookup"><span data-stu-id="0ed85-126">CH0 to variable (middle) pin on potentiometer (yellow)</span></span>

<span data-ttu-id="0ed85-127">3.3 ve potentiometer üzerindeki dış PIN 'leri belirtin.</span><span class="sxs-lookup"><span data-stu-id="0ed85-127">Supply 3.3V and ground to the outer pins on the potentiometer.</span></span> <span data-ttu-id="0ed85-128">Sıra önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="0ed85-128">Order is unimportant.</span></span>

<span data-ttu-id="0ed85-129">Gerektiğinde aşağıdaki çıkış diyagramlarına başvurun:</span><span class="sxs-lookup"><span data-stu-id="0ed85-129">Refer to the following pinout diagrams as needed:</span></span>

| <span data-ttu-id="0ed85-130">MCP3008</span><span class="sxs-lookup"><span data-stu-id="0ed85-130">MCP3008</span></span>  | <span data-ttu-id="0ed85-131">Raspberry PI GıO</span><span class="sxs-lookup"><span data-stu-id="0ed85-131">Raspberry Pi GPIO</span></span> |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="MCP3008 'ın Pinsiz gösteren bir diyagram" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Raspberry PI GıO üstbilgisinin aşımını gösteren bir diyagram. Image hitap Raspberry PI Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="0ed85-134">[Image hitap Raspberry PI Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span><span class="sxs-lookup"><span data-stu-id="0ed85-134">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="0ed85-135">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ed85-135">Create the app</span></span>

<span data-ttu-id="0ed85-136">Tercih ettiğiniz geliştirme ortamında aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="0ed85-136">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="0ed85-137">[.Net CLI](../../core/tools/dotnet-new.md) ya da [Visual Studio](../../core/tutorials/with-visual-studio.md)kullanarak yeni bir .NET konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ed85-137">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="0ed85-138">*Adcöğreticisi* olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="0ed85-138">Name it *AdcTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="0ed85-139">*Program.cs* dosyasının içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0ed85-139">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    <span data-ttu-id="0ed85-140">Yukarıdaki kodda:</span><span class="sxs-lookup"><span data-stu-id="0ed85-140">In the preceding code:</span></span>

    - <span data-ttu-id="0ed85-141">`hardwareSpiSettings` Yeni bir örneğine ayarlanır `SpiConnectionSettings` .</span><span class="sxs-lookup"><span data-stu-id="0ed85-141">`hardwareSpiSettings` is set to a new instance of `SpiConnectionSettings`.</span></span> <span data-ttu-id="0ed85-142">Oluşturucu `busId` parametresini 0 ve `chipSelectLine` parametresini 0 olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0ed85-142">The constructor sets the `busId` parameter to 0 and the `chipSelectLine` parameter to 0.</span></span>
    - <span data-ttu-id="0ed85-143">[Using bildirimi](../../csharp/whats-new/csharp-8.md#using-declarations) , `SpiDevice` çağırarak ve geçirerek bir örneği oluşturur `SpiDevice.Create` `hardwareSpiSettings` .</span><span class="sxs-lookup"><span data-stu-id="0ed85-143">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `SpiDevice` by calling `SpiDevice.Create` and passing in `hardwareSpiSettings`.</span></span> <span data-ttu-id="0ed85-144">Bu `SpiDevice` , SPI veri yolunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ed85-144">This `SpiDevice` represents the SPI bus.</span></span> <span data-ttu-id="0ed85-145">`using`Bildirim, nesnenin elden çıkarılmasını ve donanım kaynaklarının düzgün şekilde serbest bırakılacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ed85-145">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="0ed85-146">Başka bir `using` bildirim bir örneği oluşturur `Mcp3008` ve oluşturucuya geçirir `SpiDevice` .</span><span class="sxs-lookup"><span data-stu-id="0ed85-146">Another `using` declaration creates an instance of `Mcp3008` and passes the `SpiDevice` into the constructor.</span></span>
    - <span data-ttu-id="0ed85-147">`while`Döngü süresiz olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="0ed85-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="0ed85-148">Her yineleme:</span><span class="sxs-lookup"><span data-stu-id="0ed85-148">Each iteration:</span></span>
        1. <span data-ttu-id="0ed85-149">Çağırarak CH0 değerini ADC üzerinde okur `mcp.Read(0)` .</span><span class="sxs-lookup"><span data-stu-id="0ed85-149">Reads the value of CH0 on the ADC by calling `mcp.Read(0)`.</span></span>
        1. <span data-ttu-id="0ed85-150">Değeri 10,24 olarak böler.</span><span class="sxs-lookup"><span data-stu-id="0ed85-150">Divides the value by 10.24.</span></span> <span data-ttu-id="0ed85-151">MCP3008 10 bit bir ADC olduğundan, bu, 1024 arası olası 0-1023 değerleri döndürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0ed85-151">The MCP3008 is a 10-bit ADC, which means it returns 1024 possible values ranging 0-1023.</span></span> <span data-ttu-id="0ed85-152">Değerin 10,24 olarak bölünerek değeri yüzde olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ed85-152">Dividing the value by 10.24 represents the value as a percentage.</span></span>
        1. <span data-ttu-id="0ed85-153">Değeri en yakın tamsayıya yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="0ed85-153">Rounds the value to the nearest integer.</span></span>
        1. <span data-ttu-id="0ed85-154">Değeri yüzde olarak biçimlendirilen konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="0ed85-154">Writes the value to the console formatted as a percentage.</span></span>
        1. <span data-ttu-id="0ed85-155">Uyku 500 MS.</span><span class="sxs-lookup"><span data-stu-id="0ed85-155">Sleeps 500 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="0ed85-156">Dağıtım dizinine geçerek ve yürütülebilir dosyayı çalıştırarak uygulamayı Raspberry Pi üzerinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0ed85-156">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./AdcTutorial
    ```

    <span data-ttu-id="0ed85-157">Potentiometer aramasını döndürürken çıktıyı gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="0ed85-157">Observe the output as you rotate the potentiometer dial.</span></span> <span data-ttu-id="0ed85-158">Bunun nedeni, potentiometer tarafından sağlanan gerilimi 'ın ADC üzerinde CH0.</span><span class="sxs-lookup"><span data-stu-id="0ed85-158">This is due to the potentiometer varying the voltage supplied to CH0 on the ADC.</span></span> <span data-ttu-id="0ed85-159">ADC, CH0 üzerindeki giriş gerilimi değerini V<sub>başvurusuna</sub> sağlanan başvuru gerilimi ile karşılaştırarak bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ed85-159">The ADC compares the input voltage on CH0 to the reference voltage supplied to V<sub>REF</sub> to generate a value.</span></span>

1. <span data-ttu-id="0ed85-160"><kbd>CTRL + C</kbd>tuşlarına basarak Programı sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="0ed85-160">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="0ed85-161">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="0ed85-161">Congratulations!</span></span> <span data-ttu-id="0ed85-162">Verileri bir analog-dijital dönüştürücüden okumak için SPI kullandınız.</span><span class="sxs-lookup"><span data-stu-id="0ed85-162">You've used SPI to read values from an analog-to-digital converter.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="0ed85-163">Kaynak kodunu alma</span><span class="sxs-lookup"><span data-stu-id="0ed85-163">Get the source code</span></span>

<span data-ttu-id="0ed85-164">Bu öğreticinin kaynağı [GitHub ' da kullanılabilir](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial).</span><span class="sxs-lookup"><span data-stu-id="0ed85-164">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0ed85-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0ed85-165">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0ed85-166">Bir ışığı yakıp söndürmek için Genel Amaçlı giriş/çıkış kullanmayı öğrenin</span><span class="sxs-lookup"><span data-stu-id="0ed85-166">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
