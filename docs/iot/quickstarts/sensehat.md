---
title: Hızlı başlangıç-.NET kullanarak Raspberry PI Sense HAT oluşturma
description: Raspberry PI için bir eklenti panosu olan bir algılama HAT kullanarak .NET IoT kitaplıklarını 5 dakika içinde kullanmaya başlayın.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 28d6650187bbf7b9ce91516f4da4d09b114c904a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "102259711"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a><span data-ttu-id="063ed-103">Hızlı başlangıç-.NET kullanarak Raspberry PI Sense HAT oluşturma</span><span class="sxs-lookup"><span data-stu-id="063ed-103">Quickstart - Use .NET to drive a Raspberry Pi Sense HAT</span></span>

<span data-ttu-id="063ed-104">Raspberry PI [Sense hat](https://www.raspberrypi.org/products/sense-hat/) (T **bir a** vware a Ile **VIT**), Raspberry PI için bir eklenti panosuyla bulunur.</span><span class="sxs-lookup"><span data-stu-id="063ed-104">The Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) (**H** ardware **A** ttached on **T** op) is an add-on board for Raspberry Pi.</span></span> <span data-ttu-id="063ed-105">Algılama HAT, 5 × 8 RGB LED matrisini, beş düğmeli bir oyun çubuğunu ve aşağıdaki algılayıcıları içerir:</span><span class="sxs-lookup"><span data-stu-id="063ed-105">The Sense HAT is equipped with an 8×8 RGB LED matrix, a five-button joystick, and includes the following sensors:</span></span>

- <span data-ttu-id="063ed-106">Jiroskop</span><span class="sxs-lookup"><span data-stu-id="063ed-106">Gyroscope</span></span>
- <span data-ttu-id="063ed-107">İvme Ölçer</span><span class="sxs-lookup"><span data-stu-id="063ed-107">Accelerometer</span></span>
- <span data-ttu-id="063ed-108">Manyetometre</span><span class="sxs-lookup"><span data-stu-id="063ed-108">Magnetometer</span></span>
- <span data-ttu-id="063ed-109">Sıcaklık</span><span class="sxs-lookup"><span data-stu-id="063ed-109">Temperature</span></span>
- <span data-ttu-id="063ed-110">Barometrik basıncı</span><span class="sxs-lookup"><span data-stu-id="063ed-110">Barometric pressure</span></span>
- <span data-ttu-id="063ed-111">Nem oranı</span><span class="sxs-lookup"><span data-stu-id="063ed-111">Humidity</span></span>

<span data-ttu-id="063ed-112">Bu hızlı başlangıç, algılama HAT ' ten algılayıcı değerlerini almak, oyun çubuğu girişine yanıt vermek ve LED matrisini yeniden yönlendirmek için .NET kullanır.</span><span class="sxs-lookup"><span data-stu-id="063ed-112">This quickstart uses .NET to retrieve sensor values from the Sense HAT, respond to joystick input, and drive the LED matrix.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="063ed-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="063ed-113">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="063ed-114">Algılama HAT</span><span class="sxs-lookup"><span data-stu-id="063ed-114">Sense HAT</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a><span data-ttu-id="063ed-115">Hızlı başlangıcı Çalıştır</span><span class="sxs-lookup"><span data-stu-id="063ed-115">Run the quickstart</span></span>

<span data-ttu-id="063ed-116">Raspberry PI 'nize Sense HAT ekleyin.</span><span class="sxs-lookup"><span data-stu-id="063ed-116">Attach the Sense HAT to your Raspberry Pi.</span></span> <span data-ttu-id="063ed-117">Raspberry Pi (yerel veya uzak) üzerindeki bir bash isteminde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="063ed-117">From a Bash prompt on the Raspberry Pi (local or remote), run the following command:</span></span>

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

<span data-ttu-id="063ed-118">Komut bir betiği indirir ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="063ed-118">The command downloads and runs a script.</span></span> <span data-ttu-id="063ed-119">Betik şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="063ed-119">The script:</span></span>

- <span data-ttu-id="063ed-120">.NET SDK 'Yı kurar.</span><span class="sxs-lookup"><span data-stu-id="063ed-120">Installs the .NET SDK.</span></span>
- <span data-ttu-id="063ed-121">Algılama HAT hızlı başlangıç projesini içeren bir GitHub deposunu klonlar.</span><span class="sxs-lookup"><span data-stu-id="063ed-121">Clones a GitHub repository that includes the Sense HAT quickstart project.</span></span>
- <span data-ttu-id="063ed-122">Projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="063ed-122">Builds the project.</span></span>
- <span data-ttu-id="063ed-123">Projeyi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="063ed-123">Runs the project.</span></span>

<span data-ttu-id="063ed-124">Algılayıcı verileri görüntülenirken konsol çıkışını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="063ed-124">Observe the console output as sensor data is displayed.</span></span> <span data-ttu-id="063ed-125">LED matrisi, mavi bir alanda sarı bir piksel görüntüler.</span><span class="sxs-lookup"><span data-stu-id="063ed-125">The LED matrix displays a yellow pixel on a field of blue.</span></span> <span data-ttu-id="063ed-126">Oyun çubuğunu herhangi bir yönde tutmak, sarı pikseli o yönde taşır.</span><span class="sxs-lookup"><span data-stu-id="063ed-126">Holding the joystick in any direction moves the yellow pixel in that direction.</span></span> <span data-ttu-id="063ed-127">Orta oyun çubuğu düğmesine tıklamak arka planın mavi ve Red arasında değişmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="063ed-127">Clicking the center joystick button causes the background to switch from blue to red.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="063ed-128">Kaynak kodunu alma</span><span class="sxs-lookup"><span data-stu-id="063ed-128">Get the source code</span></span>

<span data-ttu-id="063ed-129">Bu hızlı başlangıç kaynağı [GitHub ' da kullanılabilir](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart).</span><span class="sxs-lookup"><span data-stu-id="063ed-129">The source for this quickstart is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart).</span></span>

## <a name="next-steps"></a><span data-ttu-id="063ed-130">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="063ed-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="063ed-131">Bir ışığı yakıp söndürmek için Genel Amaçlı giriş/çıkış kullanmayı öğrenin</span><span class="sxs-lookup"><span data-stu-id="063ed-131">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
