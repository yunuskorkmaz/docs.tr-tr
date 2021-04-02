---
title: LED yanıp sönmesi
description: .NET IoT kitaplıkları ile bir ışığı yakıp söndürme hakkında bilgi edinin.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 0d5db19faac0293b9982731f26dfd85d6ce07b3a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259040"
---
# <a name="blink-an-led"></a><span data-ttu-id="82e60-103">LED yanıp sönmesi</span><span class="sxs-lookup"><span data-stu-id="82e60-103">Blink an LED</span></span>

<span data-ttu-id="82e60-104">Genel amaçlı g/ç (GıO) PIN 'leri ayrı ayrı denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="82e60-104">General-purpose I/O (GPIO) pins can be controlled individually.</span></span> <span data-ttu-id="82e60-105">Bu, LED 'Leri, geçişleri ve diğer durum bilgisi olan cihazları denetlemek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="82e60-105">This is useful for controlling LEDs, relays, and other stateful devices.</span></span> <span data-ttu-id="82e60-106">Bu konu başlığında, net ve Raspberry Pi 'nizin GPıO PIN 'lerini kullanarak bir ışığı güçlendirin ve sürekli olarak yanıp söndürirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82e60-106">In this topic, you will use .NET and your Raspberry Pi's GPIO pins to power an LED and blink it repeatedly.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="82e60-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="82e60-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="82e60-108">5 mm LED</span><span class="sxs-lookup"><span data-stu-id="82e60-108">5 mm LED</span></span>
- <span data-ttu-id="82e60-109">330 Ω dirici</span><span class="sxs-lookup"><span data-stu-id="82e60-109">330 Ω resistor</span></span>
- <span data-ttu-id="82e60-110">Enine</span><span class="sxs-lookup"><span data-stu-id="82e60-110">Breadboard</span></span>
- <span data-ttu-id="82e60-111">Atlatıcı kabloları</span><span class="sxs-lookup"><span data-stu-id="82e60-111">Jumper wires</span></span>
- <span data-ttu-id="82e60-112">Raspberry PI GıO ayırıcı pano (isteğe bağlı/önerilen)</span><span class="sxs-lookup"><span data-stu-id="82e60-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="82e60-113">Donanımı hazırlama</span><span class="sxs-lookup"><span data-stu-id="82e60-113">Prepare the hardware</span></span>

<span data-ttu-id="82e60-114">Aşağıdaki diyagramda gösterildiği gibi devre oluşturmak için donanım bileşenlerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="82e60-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="IŞıĞı ve bir direnleyici ile bir devreni gösteren bir diyagram" lightbox="../media/rpi-led_bb.png":::

<span data-ttu-id="82e60-116">Yukarıdaki görüntüde aşağıdaki bağlantılar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="82e60-116">The image above depicts the following connections:</span></span>

- <span data-ttu-id="82e60-117">GPıO 18 ila LED anode (uzun, pozitif lider)</span><span class="sxs-lookup"><span data-stu-id="82e60-117">GPIO 18 to LED anode (longer, positive lead)</span></span>
- <span data-ttu-id="82e60-118">LED katode (kısa, negatif lider) 330 Ω direntor (her iki uçta)</span><span class="sxs-lookup"><span data-stu-id="82e60-118">LED cathode (shorter, negative lead) to 330 Ω resistor (either end)</span></span>
- <span data-ttu-id="82e60-119">330 Ω direntor (diğer uç)</span><span class="sxs-lookup"><span data-stu-id="82e60-119">330 Ω resistor (other end) to ground</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="82e60-120">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="82e60-120">Create the app</span></span>

<span data-ttu-id="82e60-121">Tercih ettiğiniz geliştirme ortamında aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="82e60-121">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="82e60-122">[.Net CLI](../../core/tools/dotnet-new.md) ya da [Visual Studio](../../core/tutorials/with-visual-studio.md)kullanarak yeni bir .NET konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82e60-122">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="82e60-123">*Blinköğreticisi* olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="82e60-123">Name it *BlinkTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="82e60-124">*Program.cs* dosyasının içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="82e60-124">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    <span data-ttu-id="82e60-125">Yukarıdaki kodda:</span><span class="sxs-lookup"><span data-stu-id="82e60-125">In the preceding code:</span></span>

    - <span data-ttu-id="82e60-126">[Using bildirimi](../../csharp/whats-new/csharp-8.md#using-declarations) bir örneği oluşturur `GpioController` .</span><span class="sxs-lookup"><span data-stu-id="82e60-126">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `GpioController`.</span></span> <span data-ttu-id="82e60-127">`using`Bildirim, nesnenin elden çıkarılmasını ve donanım kaynaklarının düzgün şekilde serbest bırakılacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="82e60-127">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="82e60-128">Çıktı için GPıO pin 18 ' i açıldı</span><span class="sxs-lookup"><span data-stu-id="82e60-128">GPIO pin 18 is opened for output</span></span>
    - <span data-ttu-id="82e60-129">`while`Döngü süresiz olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="82e60-129">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="82e60-130">Her yineleme:</span><span class="sxs-lookup"><span data-stu-id="82e60-130">Each iteration:</span></span>
        1. <span data-ttu-id="82e60-131">GPıO pin 18 ' e bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="82e60-131">Writes a value to GPIO pin 18.</span></span> <span data-ttu-id="82e60-132">`ledOn`True ise, `PinValue.High` (üzerine) yazar.</span><span class="sxs-lookup"><span data-stu-id="82e60-132">If `ledOn` is true, it writes `PinValue.High` (on).</span></span> <span data-ttu-id="82e60-133">Aksi takdirde, yazar `PinValue.Low` .</span><span class="sxs-lookup"><span data-stu-id="82e60-133">Otherwise, it writes `PinValue.Low`.</span></span>
        1. <span data-ttu-id="82e60-134">Uyku 1000 ms.</span><span class="sxs-lookup"><span data-stu-id="82e60-134">Sleeps 1000 ms.</span></span>
        1. <span data-ttu-id="82e60-135">Değerini değiştirir `ledOn` .</span><span class="sxs-lookup"><span data-stu-id="82e60-135">Toggles the value of `ledOn`.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="82e60-136">Dağıtım dizinine geçerek ve yürütülebilir dosyayı çalıştırarak uygulamayı Raspberry Pi üzerinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="82e60-136">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./BlinkTutorial
    ```

    <span data-ttu-id="82e60-137">Her saniye açık ve kapalı olarak yanıp sönüyor.</span><span class="sxs-lookup"><span data-stu-id="82e60-137">The LED blinks off and on every second.</span></span>

1. <span data-ttu-id="82e60-138"><kbd>CTRL + C</kbd>tuşlarına basarak Programı sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="82e60-138">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="82e60-139">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="82e60-139">Congratulations!</span></span> <span data-ttu-id="82e60-140">Bir ışığı yakıp söndürmek için GıO kullandınız.</span><span class="sxs-lookup"><span data-stu-id="82e60-140">You've used GPIO to blink an LED.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="82e60-141">Kaynak kodunu alma</span><span class="sxs-lookup"><span data-stu-id="82e60-141">Get the source code</span></span>

<span data-ttu-id="82e60-142">Bu öğreticinin kaynağı [GitHub ' da kullanılabilir](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial).</span><span class="sxs-lookup"><span data-stu-id="82e60-142">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial).</span></span>

## <a name="next-steps"></a><span data-ttu-id="82e60-143">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="82e60-143">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="82e60-144">Bir sensörden ortam koşullarını okumayı öğrenin</span><span class="sxs-lookup"><span data-stu-id="82e60-144">Learn how to read environmental conditions from a sensor</span></span>](../tutorials/temp-sensor.md)
