---
ms.openlocfilehash: a133c2ea48df11915f8708029c70549e8a1ccefd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497921"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF pencereleri, tek bir izleyicinin dışında genişledikleri zaman kırpmadan işlenir

#### <a name="details"></a>Ayrıntılar

Windows 8 ve üzeri sürümlerde çalışan .NET Framework 4,6 ' de, tüm pencere, birden çok izleyici senaryosunda tek bir görüntü dışına genişlemediğinde kırpma olmadan işlenir. Bu, tek bir görüntüleme ötesinde Genişletilebilir WPF pencerelerini Clip .NET Framework önceki sürümlerinden farklıdır.

#### <a name="suggestion"></a>Öneri

Bu davranış (klip veya Not) <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> <code>&lt;appSettings&gt;</code> , bir uygulamanın yapılandırma dosyasındaki öğesini kullanarak veya uygulama başlangıcında özelliği ayarlayarak açıkça ayarlanabilir <code>EnableMultiMonitorDisplayClipping</code> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
