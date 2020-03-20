---
ms.openlocfilehash: fc17efbad63ee43ddcdfd14e2fbd1557d2b3d31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72424798"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>TLS 1.x varsayılan olarak SCH_SEND_AUX_RECORD bayrağını temel SCHANNEL API'sine geçirir

|   |   |
|---|---|
|Ayrıntılar|TLS 1.x kullanırken,.NET Framework temel Windows SCHANNEL API'sine dayanır. .NET Framework 4.6 ile [başlayarak, SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) bayrağı varsayılan olarak SCHANNEL'a geçirilir. Bu, SCHANNEL'ın verileri tek bayt, ikincisi <em>n</em>-1 bayt olarak olmak üzere iki ayrı kayda bölmesine neden olur. Nadir durumlarda, bu, verilerin tek bir kayıtta bulunduğu varsayımını yapan istemciler ve varolan sunucular arasındaki iletişimi bozar.|
|Öneri|Bu değişiklik varolan bir sunucuyla iletişimi keserlerse, [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) bayrağı göndermeyi devre dışı bırakıp, uygulama yapılandırma dosyanızın [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) öğesine aşağıdaki anahtarı ekleyerek verileri ayrı kayıtlara bölmeme davranışını geri yükleyebilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Bu ayar yalnızca geriye dönük uyumluluk için sağlanır. Kullanımı aksi takdirde tavsiye edilmez.</blockquote> |
|Kapsam|Edge|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
