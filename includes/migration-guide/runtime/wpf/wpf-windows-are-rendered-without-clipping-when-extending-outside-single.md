---
ms.openlocfilehash: 2e974d277d6659aaada321b2a7e7a604df78a7bd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858471"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF windows tek bir izleyici genişletme olduğunda kırpma olmadan işlenir

|   |   |
|---|---|
|Ayrıntılar|Bir çoklu monitör senaryosunda tek ekran dışında genişletir, .NET Framework 4.6 çalışır Windows 8 ve üzeri, kırpma olmadan tüm pencere işlenir. Bu, tek bir görüntü genişletilmiş WPF windows küçük .NET Framework'ün önceki sürümlerden farklıdır.|
|Öneri|Bu davranış (verilip verilmeyeceğini veya küçük) kullanılarak açıkça ayarlanabilir <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> öğesinde <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyasında veya ayarlayarak <code>EnableMultiMonitorDisplayClipping</code> uygulamanın başlangıcında özelliği.|
|`Scope`|Küçük|
|Version|4.6|
|Type|Çalışma zamanı|

