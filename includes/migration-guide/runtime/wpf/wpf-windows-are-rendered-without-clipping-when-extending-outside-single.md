---
ms.openlocfilehash: 2e974d277d6659aaada321b2a7e7a604df78a7bd
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761416"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF windows tek bir izleyici genişletme olduğunda kırpma olmadan işlenir

|   |   |
|---|---|
|Ayrıntılar|Bir çoklu monitör senaryosunda tek ekran dışında genişletir, .NET Framework 4.6 çalışır Windows 8 ve üzeri, kırpma olmadan tüm pencere işlenir. Bu, tek bir görüntü genişletilmiş WPF windows küçük .NET Framework'ün önceki sürümlerden farklıdır.|
|Öneri|Bu davranış (verilip verilmeyeceğini veya küçük) kullanılarak açıkça ayarlanabilir <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> öğesinde <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyasında veya ayarlayarak <code>EnableMultiMonitorDisplayClipping</code> uygulamanın başlangıcında özelliği.|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma zamanı|

