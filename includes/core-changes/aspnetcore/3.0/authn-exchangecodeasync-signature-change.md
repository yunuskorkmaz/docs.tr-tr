---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394239"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Kimlik doğrulaması: OAuthHandler ExchangeCodeAsync imzası değişti

ASP.NET Core 3,0 ' de, `OAuthHandler.ExchangeCodeAsync` imzası şu şekilde değiştirildi:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

Bitiş:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`code` ve `redirectUri` dizeleri ayrı bağımsız değişkenler olarak geçirildi.

#### <a name="new-behavior"></a>Yeni davranış

`Code` ve `RedirectUri`, `OAuthCodeExchangeContext` `OAuthCodeExchangeContext` Oluşturucusu aracılığıyla ayarlayabileceği özelliklerdir. Yeni `OAuthCodeExchangeContext` türü `OAuthHandler.ExchangeCodeAsync`geçirilen tek bağımsız değişkendir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, ek parametrelerin kırılmamış bir şekilde sağlanmasını sağlar. Yeni `ExchangeCodeAsync` aşırı yüklemeleri oluşturmanız gerekmez.

#### <a name="recommended-action"></a>Önerilen eylem

Uygun `code` ve `redirectUri` değerleriyle bir `OAuthCodeExchangeContext` oluşturun. <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> bir örnek sağlanmalıdır. Bu tek `OAuthCodeExchangeContext` örneği, birden çok bağımsız değişken yerine `OAuthHandler.ExchangeCodeAsync` geçirilebilir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
