---
title: Hızlı başlangıç-.NET kullanarak Raspberry PI Sense HAT oluşturma
description: Raspberry PI için bir eklenti panosu olan bir algılama HAT kullanarak .NET IoT kitaplıklarını 5 dakika içinde kullanmaya başlayın.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 09e0c46a08e08a2021a9dffe214d3d62d6fb8ec5
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "96589981"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a>Hızlı başlangıç-.NET kullanarak Raspberry PI Sense HAT oluşturma

Raspberry PI [Sense hat](https://www.raspberrypi.org/products/sense-hat/) , <span class="docon docon-navigate-external x-hidden-focus"></span> Raspberry Pi için bir eklenti panosuyla bulunur. Algılama HAT, 5 × 8 RGB LED matrisini, beş düğmeli bir oyun çubuğunu ve aşağıdaki algılayıcıları içerir:

- Jiroskop
- İvme Ölçer
- Manyetometre
- Sıcaklık
- Barometrik basıncı
- Nem oranı

Bu hızlı başlangıç, algılama HAT ' ten algılayıcı değerlerini almak, oyun çubuğu girişine yanıt vermek ve LED matrisini yeniden yönlendirmek için .NET kullanır.

## <a name="prerequisites"></a>Önkoşullar

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- Algılama HAT

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a>Hızlı başlangıcı Çalıştır

Raspberry PI 'nize Sense HAT ekleyin. Raspberry Pi (yerel veya uzak) üzerindeki bir bash isteminde aşağıdaki komutu çalıştırın:

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

Komut bir betiği indirir ve çalıştırır. Betik şunları yapar:

- .NET SDK 'Yı kurar.
- Algılama HAT hızlı başlangıç projesini içeren bir GitHub deposunu klonlar.
- Projeyi oluşturur.
- Projeyi çalıştırır.

Algılayıcı verileri görüntülenirken konsol çıkışını gözlemleyin. LED matrisi, mavi bir alanda sarı bir piksel görüntüler. Oyun çubuğunu herhangi bir yönde tutmak, sarı pikseli o yönde taşır. Orta oyun çubuğu düğmesine tıklamak arka planın mavi ve Red arasında değişmesine neden olur.

## <a name="get-the-source-code"></a>Kaynak kodunu alma

Bu hızlı başlangıç kaynağı [GitHub ' da kullanılabilir](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart). <span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Bir ışığı yakıp söndürmek için Genel Amaçlı giriş/çıkış kullanmayı öğrenin](../tutorials/blink-led.md)
