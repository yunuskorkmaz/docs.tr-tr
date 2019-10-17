---
ms.openlocfilehash: fc17efbad63ee43ddcdfd14e2fbd1557d2b3d31c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72424798"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>TLS 1. x varsayılan olarak temel SCHANNEL API 'sine SCH_SEND_AUX_RECORD bayrağını geçirir

|   |   |
|---|---|
|Ayrıntılar|TLS 1. x kullanırken, .NET Framework temeldeki Windows SCHANNEL API 'sine dayanır. .NET Framework 4,6 ' den başlayarak, [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) bayrağı varsayılan olarak SChannel ' a geçirilir. Bu, SCHANNEL 'ın verileri iki ayrı kayıt halinde, ilki tek bir bayt ve ikinciden <em>n</em>-1 bayt olarak şifrelemesine neden olur. Nadir durumlarda, bu durum istemciler ve mevcut sunucular arasındaki iletişimi, verilerin tek bir kayıtta bulunduğu varsayımını yapan bir şekilde keser.|
|Öneri|Bu değişiklik var olan bir sunucuyla iletişimi kopararsa, [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) bayrağını göndermeyi devre dışı bırakabilir ve [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ' ye aşağıdaki anahtarı ekleyerek, verileri ayrı kayıtlara bölmemek için önceki davranışı geri yükleyebilirsiniz. öğesini uygulama yapılandırma dosyanızın [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümünde:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Bu ayar yalnızca geriye dönük uyumluluk için sağlanır. Aksi takdirde kullanılması önerilmez.</blockquote> |
|Kapsam|Kenar|
|Version|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
