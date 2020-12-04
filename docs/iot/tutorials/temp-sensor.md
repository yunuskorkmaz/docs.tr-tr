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
# <a name="read-environmental-conditions-from-a-sensor"></a><span data-ttu-id="9c292-103">Sensörden ortam koşullarını okuma</span><span class="sxs-lookup"><span data-stu-id="9c292-103">Read environmental conditions from a sensor</span></span>

<span data-ttu-id="9c292-104">IoT cihazlarının en yaygın senaryolarından biri çevresel koşulların algılanması.</span><span class="sxs-lookup"><span data-stu-id="9c292-104">One of the most common scenarios for IoT devices is detection of environmental conditions.</span></span> <span data-ttu-id="9c292-105">Sıcaklık, nem, Barometrik basıncı ve daha fazlasını izlemek için çeşitli sensör mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="9c292-105">A variety of sensors are available to monitor temperature, humidity, barometric pressure, and more.</span></span>

<span data-ttu-id="9c292-106">Bu konu başlığında, bir sensörden ortam koşullarını okumak için .NET kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="9c292-106">In this topic, you will use .NET to read environmental conditions from a sensor.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9c292-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="9c292-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="9c292-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> nem/barometrik basınç/sıcaklık algılayıcısı</span><span class="sxs-lookup"><span data-stu-id="9c292-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> humidity/barometric pressure/temperature sensor breakout</span></span>
- <span data-ttu-id="9c292-109">Atlatıcı kabloları</span><span class="sxs-lookup"><span data-stu-id="9c292-109">Jumper wires</span></span>
- <span data-ttu-id="9c292-110">Enine (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="9c292-110">Breadboard (optional)</span></span>
- <span data-ttu-id="9c292-111">Raspberry PI GıO ayırıcı panosu (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="9c292-111">Raspberry Pi GPIO breakout board (optional)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> <span data-ttu-id="9c292-112">BME280 ayırıcıların birçok üreticisi vardır.</span><span class="sxs-lookup"><span data-stu-id="9c292-112">There are many manufacturers of BME280 breakouts.</span></span> <span data-ttu-id="9c292-113">Çoğu tasarım benzerdir ve üretici, işlevselliğe herhangi bir farklılık yapmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c292-113">Most designs are similar, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="9c292-114">Bu öğreticide, Çeşitlemeler hesaba deniyor.</span><span class="sxs-lookup"><span data-stu-id="9c292-114">This tutorial attempts to account for variations.</span></span> <span data-ttu-id="9c292-115">BME280 ayırıcılarınızın Inter-Integrated devre (ı2C) arabirimi içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9c292-115">Ensure your BME280 breakout includes an Inter-Integrated Circuit (I2C) interface.</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="9c292-116">Donanımı hazırlama</span><span class="sxs-lookup"><span data-stu-id="9c292-116">Prepare the hardware</span></span>

<span data-ttu-id="9c292-117">Aşağıdaki diyagramda gösterildiği gibi devre oluşturmak için donanım bileşenlerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="9c292-117">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Raspberry Pi ile BME280 breakbir tahtaya bağlantıyı gösteren eğime diyagramı" lightbox="../media/rpi-bmp280_i2c.png":::

<span data-ttu-id="9c292-119">Aşağıda, Raspberry Pi 'den BME280 ayırıcıya olan bağlantılar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9c292-119">The following are the connections from the Raspberry Pi to the BME280 breakout:</span></span>

- <span data-ttu-id="9c292-120">3.3 */VIN veya* 3v3 (kırmızı renkte gösterilir)</span><span class="sxs-lookup"><span data-stu-id="9c292-120">3.3V to VIN *OR* 3V3 (shown in red)</span></span>
- <span data-ttu-id="9c292-121">Zemin-plan (siyah)</span><span class="sxs-lookup"><span data-stu-id="9c292-121">Ground to GND (black)</span></span>
- <span data-ttu-id="9c292-122">SDA (GPıO 2)-SDI *veya* sda (mavi)</span><span class="sxs-lookup"><span data-stu-id="9c292-122">SDA (GPIO 2) to SDI *OR* SDA (blue)</span></span>
- <span data-ttu-id="9c292-123">SCL (GPıO 3)-SCK *veya* SCL (turuncu)</span><span class="sxs-lookup"><span data-stu-id="9c292-123">SCL (GPIO 3) to SCK *OR* SCL (orange)</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="9c292-124">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c292-124">Create the app</span></span>

<span data-ttu-id="9c292-125">Tercih ettiğiniz geliştirme ortamında aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="9c292-125">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="9c292-126">[.Net CLI](../../core/tools/dotnet-new.md) ya da [Visual Studio](../../core/tutorials/with-visual-studio.md)kullanarak yeni bir .NET konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9c292-126">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="9c292-127">*Sensoröğreticisi* olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="9c292-127">Name it *SensorTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="9c292-128">*Program.cs* dosyasının içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9c292-128">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    <span data-ttu-id="9c292-129">Yukarıdaki kodda:</span><span class="sxs-lookup"><span data-stu-id="9c292-129">In the preceding code:</span></span>

    - <span data-ttu-id="9c292-130">`i2cSettings` Yeni bir örneğine ayarlanır `I2cConnectionSettings` .</span><span class="sxs-lookup"><span data-stu-id="9c292-130">`i2cSettings` is set to a new instance of `I2cConnectionSettings`.</span></span> <span data-ttu-id="9c292-131">Oluşturucu `busId` parametresini 1 olarak ve `deviceAddress` parametresini olarak ayarlar `Bme280.DefaultI2cAddress` .</span><span class="sxs-lookup"><span data-stu-id="9c292-131">The constructor sets the `busId` parameter to 1 and the `deviceAddress` parameter to `Bme280.DefaultI2cAddress`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="9c292-132">Bazı BME280 breaküreticileri ikincil adres değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c292-132">Some BME280 breakout manufacturers use the secondary address value.</span></span> <span data-ttu-id="9c292-133">Bu cihazlar için kullanın `Bme280.SecondaryI2cAddress` .</span><span class="sxs-lookup"><span data-stu-id="9c292-133">For those devices, use `Bme280.SecondaryI2cAddress`.</span></span>

    - <span data-ttu-id="9c292-134">[Using bildirimi](../../csharp/whats-new/csharp-8.md#using-declarations) , `I2cDevice` çağırarak ve geçirerek bir örneği oluşturur `I2cDevice.Create` `i2cSettings` .</span><span class="sxs-lookup"><span data-stu-id="9c292-134">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in `i2cSettings`.</span></span> <span data-ttu-id="9c292-135">Bu `I2cDevice` , I2C veri yolunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9c292-135">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="9c292-136">`using`Bildirim, nesnenin elden çıkarılmasını ve donanım kaynaklarının düzgün şekilde serbest bırakılacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c292-136">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="9c292-137">Başka bir `using` bildirim `Bme280` , algılayıcısı temsil etmek için bir örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c292-137">Another `using` declaration creates an instance of `Bme280` to represent the sensor.</span></span> <span data-ttu-id="9c292-138">, `I2cDevice` Oluşturucuya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="9c292-138">The `I2cDevice` is passed in the constructor.</span></span>
    - <span data-ttu-id="9c292-139">Yongasının, yongasının geçerli (varsayılan) ayarlarıyla ölçümleri yapması için gereken süre, çağırarak alınır `GetMeasurementDuration` .</span><span class="sxs-lookup"><span data-stu-id="9c292-139">The time required for the chip to take measurements with the chip's current (default) settings is retrieved by calling `GetMeasurementDuration`.</span></span>
    - <span data-ttu-id="9c292-140">`while`Döngü süresiz olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="9c292-140">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="9c292-141">Her yineleme:</span><span class="sxs-lookup"><span data-stu-id="9c292-141">Each iteration:</span></span>
        1. <span data-ttu-id="9c292-142">Konsolunu temizler.</span><span class="sxs-lookup"><span data-stu-id="9c292-142">Clears the console.</span></span>
        1. <span data-ttu-id="9c292-143">Güç modunu olarak ayarlar `Bmx280PowerMode.Forced` .</span><span class="sxs-lookup"><span data-stu-id="9c292-143">Sets the power mode to `Bmx280PowerMode.Forced`.</span></span> <span data-ttu-id="9c292-144">Bu, yonganın tek bir ölçüm gerçekleştirmesini, sonuçları depolamasını ve sonra uykuya geçmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="9c292-144">This forces the chip to perform one measurement, store the results, and then sleep.</span></span>
        1. <span data-ttu-id="9c292-145">Sıcaklık, basınç, nem ve yükseklik değerlerini okur.</span><span class="sxs-lookup"><span data-stu-id="9c292-145">Reads the values for temperature, pressure, humidity, and altitude.</span></span>

            > [!NOTE]
            > <span data-ttu-id="9c292-146">Yükseklik, cihaz bağlama tarafından hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="9c292-146">Altitude is calculated by the device binding.</span></span> <span data-ttu-id="9c292-147">' Nin bu aşırı yüklemesi, `TryReadAltitude` bir tahmin oluşturmak için ortalama deniz düzeyinde basınç kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c292-147">This overload of `TryReadAltitude` uses mean sea level pressure to generate an estimate.</span></span>

        1. <span data-ttu-id="9c292-148">Geçerli ortam koşullarını konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="9c292-148">Writes the current environmental conditions to the console.</span></span>
        1. <span data-ttu-id="9c292-149">Uyku 1000 ms.</span><span class="sxs-lookup"><span data-stu-id="9c292-149">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="9c292-150">Dağıtım dizinine geçerek ve yürütülebilir dosyayı çalıştırarak uygulamayı Raspberry Pi üzerinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9c292-150">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./SensorTutorial
    ```

    <span data-ttu-id="9c292-151">Konsolundaki algılayıcı çıkışını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="9c292-151">Observe the sensor output in the console.</span></span>

1. <span data-ttu-id="9c292-152"><kbd>CTRL + C</kbd>tuşlarına basarak Programı sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="9c292-152">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="9c292-153">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="9c292-153">Congratulations!</span></span> <span data-ttu-id="9c292-154">Sıcaklık/nem/barometrik basınç algılayıcısındaki değerleri okumak için ı2C 'yi kullandınız!</span><span class="sxs-lookup"><span data-stu-id="9c292-154">You've used I2C to read values from a temperature/humidity/barometric pressure sensor!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="9c292-155">Kaynak kodunu alma</span><span class="sxs-lookup"><span data-stu-id="9c292-155">Get the source code</span></span>

<span data-ttu-id="9c292-156">Bu öğreticinin kaynağı [GitHub ' da kullanılabilir](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="9c292-156">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9c292-157">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9c292-157">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9c292-158">Bir LCD üzerinde metin görüntülemeyi öğrenin</span><span class="sxs-lookup"><span data-stu-id="9c292-158">Learn how to display text on an LCD</span></span>](../tutorials/lcd-display.md)
