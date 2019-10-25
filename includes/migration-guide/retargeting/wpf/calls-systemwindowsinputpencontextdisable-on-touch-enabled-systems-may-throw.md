---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887852"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Dokunmatik özellikli sistemlerde System. Windows. Input. PenContext. Disable için çağrılar bir ArgumentException oluşturabilir

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, dokunmatik özellikli sistemlerde iç **System. Windows. Int32. PenContext. Disable** yöntemine yapılan çağrılar, yeniden giriş nedeniyle işlenmemiş bir <code>T:System.ArgumentException</code> oluşturabilir.|
|Öneri|Bu sorun 4,7 .NET Framework giderilmiştir. Özel durumu engellemek için, .NET Framework .NET Framework 4,7 ' den başlayarak bir sürümüne yükseltin.|
|Kapsam|Kenar|
|Version|4.6.1|
|Tür|Yeniden Hedefleme|
