---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093606"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF windows tek bir izleyici genişletme olduğunda kırpma olmadan işlenir

|   |   |
|---|---|
|Ayrıntılar|Bir çoklu monitör senaryosunda tek ekran dışında genişletir, .NET Framework 4.6 çalışır Windows 8 ve üzeri, kırpma olmadan tüm pencere işlenir. Bu, tek bir görüntü genişletilmiş WPF windows küçük .NET Framework'ün önceki sürümlerden farklıdır.|
|Öneri|Bu davranış (verilip verilmeyeceğini veya küçük) kullanılarak açıkça ayarlanabilir <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> öğesinde <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyasında veya ayarlayarak <code>EnableMultiMonitorDisplayClipping</code> uygulamanın başlangıcında özelliği.|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
