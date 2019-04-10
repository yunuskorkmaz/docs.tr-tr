---
ms.openlocfilehash: 0ea8c4843bb0dfb4e4208f2bfad4c416bfae7a1e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234535"
---
### <a name="tls-1x-by-default-passes-the-schsendauxrecord-flag-to-the-underlying-schannel-api"></a>TLS 1.x varsayılan SCH_SEND_AUX_RECORD bayrağı temel alınan SCHANNEL API'sine geçirir

|   |   |
|---|---|
|Ayrıntılar|TLS kullanırken 1.x, .NET Framework, temel alınan Windows SCHANNEL API'sini kullanır. .NET Framework 4.6 ile başlayan [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) bayrağı, SCHANNEL için varsayılan olarak geçirilir. Bu iki ayrı kayıt, ilk olarak bir tek baytlı ve ikinci olarak içinde şifrelenmiş verileri bölme SCHANNEL neden <em>n</em>-1 bayt. Nadiren de olsa, bu istemciler ve verinin tek bir kayıtta bulunduğu varsayılmaktadır mevcut sunucular arasındaki iletişimi keser.|
|Öneri|Bu değişiklik, mevcut bir sunucu ile iletişim keserse, gönderme devre dışı bırakabilirsiniz [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) bayrak ve verileri ayrı kayıtlarını aşağıdaki anahtara ekleyerek bölme değil, önceki davranışı geri yükleme [ \<AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ \<çalışma zamanı >](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) , uygulama yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Bu ayar yalnızca geriye dönük uyumluluk için sağlanır. Aksi takdirde, kullanımı önerilmez.</blockquote> |
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
