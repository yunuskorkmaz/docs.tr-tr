---
ms.openlocfilehash: 8438341d6fcc5cf0415a2cae059bc76477a5c5e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234556"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Yalnızca System.Net.ServicePointManager ve System.Net.Security.SslStream desteklenen Tls 1.0, 1.1 ve 1.2 protokolleri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ile başlayan <xref:System.Net.ServicePointManager> ve <xref:System.Net.Security.SslStream> sınıfları yalnızca izin verilecek aşağıdaki üç protokolden birini kullanın: Tls1.0, Tls1.1 veya Tls1.2. SSL3.0 protokolünün ve RC4 şifreleme desteklenmez.|
|Öneri|Önerilen risk azaltma, sunucu tarafı uygulamayı Tls1.0, Tls1.1 veya Tls1.2 yükseltme sağlamaktır. Bu uygun değilse veya istemci uygulamaları kopmuş <xref:System.AppContext?displayProperty=name> sınıfı, bu özellik iki yöntemden biriyle dışında kabul etmek için kullanılabilir:<ol><li>/ Compat anahtarlarını programlı olarak ayarlayarak <xref:System.AppContext?displayProperty=name>açıklandığı gibi [burada](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)</li><li>Aşağıdaki satırı ekleyerek <code>&lt;runtime&gt;</code> app.config dosyasının: <code>&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;</code>;</li></ol>|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|
