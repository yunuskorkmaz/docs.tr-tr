---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804559"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>ETW olay adları yalnızca "Başlat" veya "Durdur" sonekiile göre farklı olamaz

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ve 4.6.1'de, çalışma zamanı, Windows için iki Olay İzleme (ETW)&quot; &quot;olay&quot; adının yalnızca Başlangıç &quot;veya Durdur <code>LogUser</code> sonekiyle (bir olay adlandırılmış ve diğerinin adı geçtiğinde) <code>LogUserStart</code>farklı olduğunda bir <xref:System.ArgumentException> zaman atar. Bu durumda, çalışma zamanı, herhangi bir günlüğe kaydetme yemeyen olay kaynağını oluşturamaz.|
|Öneri|Özel durumu önlemek için, iki olay adı &quot;yalnızca&quot; &quot;Başlat&quot; veya Durdur sonekiyle farklılık olmadığından emin olun. Bu gereksinim .NET Framework 4.6.2 ile başlayarak kaldırılır; çalışma süresi, yalnızca &quot;Başlat&quot; ve &quot;Durdur&quot; sonekine göre farklılık gösteren olay adlarını ayrıştırabilir.|
|Kapsam|Edge|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
