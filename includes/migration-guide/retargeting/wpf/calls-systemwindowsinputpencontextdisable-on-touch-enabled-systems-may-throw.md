---
ms.openlocfilehash: 3cd5052dffcb059c240a310e0b89384f28409264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757789"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Dokunmatik özellikli sistemlerde System.Windows.Input.PenContext.Disable çağrıları ArgumentException atabilir.

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, iç ağa çağırır <strong>System.Windows.Intput.PenContext.Disable</strong> Dokunmatik özellikli sistemlerinde yöntemi işlenmeyen bir throw <code>T:System.ArgumentException</code> yeniden giriş nedeniyle.|
|Öneri|.NET Framework 4.7 bu sorun giderilmiştir. Özel durum önlemek için .NET Framework 4.7 ile başlayan .NET Framework'ün bir sürüme yükseltin.|
|Kapsam|Kenar|
|Sürüm|4.6.1|
|Tür|Yeniden Hedefleme|
