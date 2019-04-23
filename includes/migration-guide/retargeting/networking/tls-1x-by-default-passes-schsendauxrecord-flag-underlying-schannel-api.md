---
ms.openlocfilehash: 5850d55023849fdc797ec0cb5464495179dcbb61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982150"
---
### <a name="tls-1x-by-default-passes-the-schsendauxrecord-flag-to-the-underlying-schannel-api"></a>TLS 1.x varsayılan SCH_SEND_AUX_RECORD bayrağı temel alınan SCHANNEL API'sine geçirir

|   |   |
|---|---|
|Ayrıntılar|TLS kullanırken 1.x, .NET Framework, temel alınan Windows SCHANNEL API'sini kullanır. .NET Framework 4.6 ile başlayan [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) bayrağı, SCHANNEL için varsayılan olarak geçirilir. Bu iki ayrı kayıt, ilk olarak bir tek baytlı ve ikinci olarak içinde şifrelenmiş verileri bölme SCHANNEL neden <em>n</em>-1 bayt. Nadiren de olsa, bu istemciler ve verinin tek bir kayıtta bulunduğu varsayılmaktadır mevcut sunucular arasındaki iletişimi keser.|
|Öneri|Bu değişiklik, mevcut bir sunucu ile iletişim keserse, gönderme devre dışı bırakabilirsiniz [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) bayrak ve verileri ayrı kayıtlarını aşağıdaki anahtara ekleyerek bölme değil, önceki davranışı geri yükleme [ < ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ < ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) , uygulama yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Bu ayar yalnızca geriye dönük uyumluluk için sağlanır. Aksi takdirde, kullanımı önerilmez.</blockquote> |
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
