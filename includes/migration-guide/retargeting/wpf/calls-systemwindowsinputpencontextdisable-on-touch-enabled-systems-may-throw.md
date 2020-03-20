---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887852"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>System.Windows.Input.PenContext.Disable touch-enabled sistemlere aramalar bir ArgumentException atabilir

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, dokunma özellikli sistemlerde dahili **System.Windows.Intput.PenContext.Disable** yöntemi ne <code>T:System.ArgumentException</code> çağrıları reentrancy nedeniyle işlenmemiş atabilir.|
|Öneri|Bu sorun .NET Framework 4.7'de ele alınmıştır. İstisnayı önlemek için .NET Framework 4.7 ile başlayan bir .NET Framework sürümüne yükseltin.|
|Kapsam|Edge|
|Sürüm|4.6.1|
|Tür|Yeniden Hedefleme|
