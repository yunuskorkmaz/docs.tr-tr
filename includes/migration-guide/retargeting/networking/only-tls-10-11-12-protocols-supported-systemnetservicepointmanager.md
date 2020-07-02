---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615763"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>System .net. ServicePointManager ve System .net. Security. SslStream içinde yalnızca TLS 1,0, 1,1 ve 1,2 protokolleri desteklenir

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' den başlayarak, <xref:System.Net.ServicePointManager> ve <xref:System.Net.Security.SslStream> sınıflarının yalnızca şu üç protokolden birini kullanmasına izin verilir: TLS 1.0, TLS 1.1 veya TLS 1.2. SSL 3.0 protokol ve RC4 şifresi desteklenmez.

#### <a name="suggestion"></a>Öneri

Önerilen risk azaltma, sunucu tarafı uygulamayı TLS 1.0, TLS 1.1 veya TLS 1.2 sürümüne yükseltmek için önerilir. Bu uygun değilse veya istemci uygulamaları bozulur, <xref:System.AppContext?displayProperty=fullName> sınıfı iki şekilde bu özelliği devre dışı bırakmak için kullanılabilir:

- <xref:System.AppContext?displayProperty=fullName> [Burada](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)açıklandığı gibi, üzerinde uyumluluk anahtarlarını programlı olarak ayarlayarak.
- `<runtime>`app.config dosyanın bölümüne aşağıdaki satırı ekleyerek:

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>
