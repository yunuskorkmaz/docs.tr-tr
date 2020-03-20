---
ms.openlocfilehash: 9c3eedb7f7d4cd030a12c141b8630876c1ffdb4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859064"
---
### <a name="throttle-concurrent-requests-per-session"></a>Oturum başına eşzamanlı istekleri azaltma

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ve daha önceki ASP.NET, aynı Sessionid ile istekleri sırayla yürütür ve ASP.NET sessionid'i her zaman varsayılan olarak çerezler aracılığıyla yayınlar. Bir sayfanın yanıt vermesi uzun zaman alıyorsa, sadece tarayıcıda F5 tuşuna basarak sunucu performansını önemli ölçüde düşürür. Düzeltmede, sıralı istekleri izlemek ve belirtilen sınırı aştıklarında istekleri sonlandırmak için bir sayaç ekledik. Varsayılan değer 50'dir. Sınıra ulaşılırsa, olay günlüğüne bir uyarı kaydedilir ve IIS günlüğüne bir HTTP 500 yanıtı kaydedilebilir.|
|Öneri|Eski davranışı geri yüklemek için, yeni davranışı devre dışı bırakmak için web.config dosyanıza aşağıdaki ayarı ekleyebilirsiniz.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
