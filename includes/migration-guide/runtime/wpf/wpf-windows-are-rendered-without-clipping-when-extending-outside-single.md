---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858471"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF pencereler, tek bir monitörün dışına uzatıldığında kırpma olmadan işlenir

|   |   |
|---|---|
|Ayrıntılar|Windows 8 ve üzeri üzerinde çalışan .NET Framework 4.6'da, çoklu monitör senaryosunda tek ekranın dışına uzandığında tüm pencere kırpma olmadan işlenir. Bu, .NET Framework'ün tek bir ekranın ötesine uzanan WPF pencerelerini kesecek önceki sürümlerinden farklıdır.|
|Öneri|Bu davranış (klip le şaşmasın veya <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> kesilmesin), bir uygulamanın yapılandırma <code>&lt;appSettings&gt;</code> <code>EnableMultiMonitorDisplayClipping</code> dosyasındaki öğe kullanılarak veya uygulama başlangıcında özelliği ayarlayarak açıkça ayarlanabilir.|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
