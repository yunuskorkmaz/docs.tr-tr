---
ms.openlocfilehash: d276e2bbf24c8b2389a0a8078c62c327c3729d50
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621447"
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
