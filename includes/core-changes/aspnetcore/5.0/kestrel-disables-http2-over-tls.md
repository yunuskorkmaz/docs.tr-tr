---
ms.openlocfilehash: 92210f6becb5a5a43893ee0fd51ef51e2ddd7f8d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325236"
---
### <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a>Kestrel: HTTP/2 uyumsuz Windows sürümlerinde TLS üzerinden devre dışı bırakıldı

Windows üzerinde Aktarım Katmanı Güvenliği (TLS) üzerinden HTTP/2 ' yi etkinleştirmek için iki gereksinimin karşılanması gerekir:

- Windows 8.1 ve Windows Server 2012 R2 ile başlayarak kullanılabilen uygulama katmanı protokol anlaşması (ALPN) desteği.
- Windows 10 ve Windows Server 2016 ile başlayarak kullanılabilen, HTTP/2 ile uyumlu olan bir şifre kümesi.

Bu nedenle, TLS üzerinden HTTP/2 yapılandırıldığında Kestrel davranışı şu şekilde değişir:

- `Http1` `Information` [Listenoptions. httpprotocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) olarak ayarlandığında bir iletiyi alçaltma ve bu düzeyde günlüğe kaydetme `Http1AndHttp2` . `Http1AndHttp2` , için varsayılan değerdir `ListenOptions.HttpProtocols` .
- `NotSupportedException` `ListenOptions.HttpProtocols` Olarak ayarlandığında bir oluşturun `Http2` .

Tartışma için bkz. sorun [DotNet/aspnetcore # 23068](https://github.com/dotnet/aspnetcore/issues/23068).

#### <a name="version-introduced"></a>Sunulan sürüm

ASP.NET Core 5,0 Preview 7

#### <a name="old-behavior"></a>Eski davranış

Aşağıdaki tabloda, TLS üzerinden HTTP/2 yapılandırıldığında davranış özetlenmektedir.

| Protokoller | Windows 7,<br />Windows Server 2008 R2,<br />veya daha önceki bir sürümü | Windows 8,<br />Windows Server 2012 | Windows 8.1<br />Windows Server 2012 R2 | Windows 10,<br />Windows Server 2016,<br />veya daha yeni |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | Yaratır `NotSupportedException`                   | TLS el sıkışması sırasında hata     | TLS el sıkışması sırasında hata &ast;     | Hata yok |
| `Http1AndHttp2` | Düşürme `Http1`                    | Düşürme `Http1`     | TLS el sıkışması sırasında hata &ast;     | Hata yok |

&ast; Bu senaryoları etkinleştirmek için uyumlu şifre paketlerini yapılandırın.

#### <a name="new-behavior"></a>Yeni davranış

Aşağıdaki tabloda, TLS üzerinden HTTP/2 yapılandırıldığında davranış özetlenmektedir.

| Protokoller | Windows 7,<br />Windows Server 2008 R2,<br />veya daha önceki bir sürümü | Windows 8,<br />Windows Server 2012 | Windows 8.1<br />Windows Server 2012 R2 | Windows 10,<br />Windows Server 2016,<br />veya daha yeni |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | Yaratır `NotSupportedException`                   | Yaratır `NotSupportedException`     | Throw `NotSupportedException`&ast;&ast;     | Hata yok |
| `Http1AndHttp2` | Düşürme `Http1`                    | Düşürme `Http1`     | `Http1`Düşürme&ast;&ast;     | Hata yok |

&ast;&ast; Uyumlu şifre paketlerini yapılandırın ve `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` `true` Bu senaryoları etkinleştirmek için uygulama bağlam anahtarını olarak ayarlayın.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, eski Windows sürümlerindeki TLS üzerinden HTTP/2 uyumluluk hatalarının erken ve mümkün olduğunca net bir şekilde ortaya geçmesini sağlar.

#### <a name="recommended-action"></a>Önerilen eylem

Uyumsuz Windows sürümlerinde TLS üzerinden HTTP/2 devre dışı bırakıldığından emin olun. Windows 8.1 ve Windows Server 2012 R2, varsayılan olarak gerekli şifrelemeleri olmadığından uyumsuzdur. Ancak, bilgisayar yapılandırma ayarlarını HTTP/2 ile uyumlu şifrelemeleri kullanacak şekilde güncelleştirmek mümkündür. Daha fazla bilgi için bkz. [Windows 8.1 'de TLS şifre paketleri](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1). Yapılandırıldıktan sonra Kestrel üzerinde TLS üzerinden HTTP/2, uygulama bağlamı anahtarı ayarlanarak etkinleştirilmelidir `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` . Örnek:

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

Temel alınan destek değiştirilmedi. Örneğin, TLS üzerinden HTTP/2, Windows 8 veya Windows Server 2012 ' de hiç çalışmadı. Bu değişiklik, bu desteklenmeyen senaryolardaki hataların sunulma şeklini değiştirir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

#### Affected APIs

Not detectable via API analysis

-->
