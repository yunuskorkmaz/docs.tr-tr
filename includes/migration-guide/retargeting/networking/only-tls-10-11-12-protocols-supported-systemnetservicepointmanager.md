---
ms.openlocfilehash: 5b531dc23feb311a797823dfa2a4d853859f9e18
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235502"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Yalnızca System.Net.ServicePointManager ve System.Net.Security.SslStream desteklenen Tls 1.0, 1.1 ve 1.2 protokolleri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ile başlayan <xref:System.Net.ServicePointManager> ve <xref:System.Net.Security.SslStream> sınıfları yalnızca izin verilecek aşağıdaki üç protokolden birini kullanın: Tls1.0, Tls1.1 veya Tls1.2. SSL3.0 protokolünün ve RC4 şifreleme desteklenmez.|
|Öneri|Önerilen risk azaltma, sunucu tarafı uygulamayı Tls1.0, Tls1.1 veya Tls1.2 yükseltme sağlamaktır. Bu uygun değilse veya istemci uygulamaları kopmuş <xref:System.AppContext?displayProperty=name> sınıfı, bu özellik iki yöntemden biriyle dışında kabul etmek için kullanılabilir:<ol><li>/ Compat anahtarlarını programlı olarak ayarlayarak <xref:System.AppContext?displayProperty=name>açıklandığı gibi [burada](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Aşağıdaki satırı ekleyerek <code>&lt;runtime&gt;</code> app.config dosyasının:</li></ol><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|
