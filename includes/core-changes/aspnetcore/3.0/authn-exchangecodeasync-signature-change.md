---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032707"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Kimlik doğrulaması: OAuthHandler ExchangeCodeAsync imzası değişti

ASP.NET Core 3,0 ' de, imzası şu şekilde `OAuthHandler.ExchangeCodeAsync` değiştirildi:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

Hedef:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`code`Ve `redirectUri` dizeleri ayrı bağımsız değişkenler olarak geçildi.

#### <a name="new-behavior"></a>Yeni davranış

`Code` ve `RedirectUri` `OAuthCodeExchangeContext` , Oluşturucu aracılığıyla ayarlanabilir özellikler vardır `OAuthCodeExchangeContext` . Yeni `OAuthCodeExchangeContext` tür, geçirilen tek bağımsız değişkendir `OAuthHandler.ExchangeCodeAsync` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, ek parametrelerin kırılmamış bir şekilde sağlanmasını sağlar. Yeni aşırı yükleme oluşturmaya gerek yoktur `ExchangeCodeAsync` .

#### <a name="recommended-action"></a>Önerilen eylem

`OAuthCodeExchangeContext`Uygun ve değerleri ile oluşturun `code` `redirectUri` . <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties>Örnek sağlanmalıdır. Bu tek `OAuthCodeExchangeContext` örnek `OAuthHandler.ExchangeCodeAsync` , birden çok bağımsız değişken yerine öğesine geçirilebilir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
