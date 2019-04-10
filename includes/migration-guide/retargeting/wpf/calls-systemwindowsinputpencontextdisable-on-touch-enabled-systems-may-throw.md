---
ms.openlocfilehash: 3cd5052dffcb059c240a310e0b89384f28409264
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234548"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Dokunmatik özellikli sistemlerde System.Windows.Input.PenContext.Disable çağrıları ArgumentException atabilir.

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, iç ağa çağırır <strong>System.Windows.Intput.PenContext.Disable</strong> Dokunmatik özellikli sistemlerinde yöntemi işlenmeyen bir throw <code>T:System.ArgumentException</code> yeniden giriş nedeniyle.|
|Öneri|.NET Framework 4.7 bu sorun giderilmiştir. Özel durum önlemek için .NET Framework 4.7 ile başlayan .NET Framework'ün bir sürüme yükseltin.|
|Kapsam|Kenar|
|Sürüm|4.6.1|
|Tür|Yeniden Hedefleme|
