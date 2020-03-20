---
ms.openlocfilehash: 5b531dc23feb311a797823dfa2a4d853859f9e18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235502"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>System.Net.ServicePointManager ve System.Net.Security.SslStream'de desteklenen 1.0, 1.1 ve 1.2 protokolleri sadece TL'dir.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ile <xref:System.Net.ServicePointManager> başlayarak, <xref:System.Net.Security.SslStream> ve sınıfların yalnızca aşağıdaki üç protokolden birini kullanmasına izin verilir: Tls1.0, Tls1.1 veya Tls1.2. SSL3.0 protokolü ve RC4 şifresi desteklenmez.|
|Öneri|Önerilen azaltma, kesme tarafındaki uygulamayı Tls1.0, Tls1.1 veya Tls1.2'ye yükseltmektir. Bu mümkün değilse veya istemci uygulamaları bozulursa, <xref:System.AppContext?displayProperty=name> sınıf bu özelliğin dışında iki şekilde devre dışı bırakmak için kullanılabilir:<ol><li>Programlı olarak compat anahtarları ayarlayarak <xref:System.AppContext?displayProperty=name>, [burada](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)açıklandığı gibi .</li><li>app.config dosyasının <code>&lt;runtime&gt;</code> bölümüne aşağıdaki satırı ekleyerek:</li></ol><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|
