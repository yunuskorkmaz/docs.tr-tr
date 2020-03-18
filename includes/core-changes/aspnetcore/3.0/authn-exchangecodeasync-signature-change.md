---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394239"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Kimlik doğrulama: OAuthHandler ExchangeCodeAsync imza değiştirildi

core 3.0ASP.NETde imzası `OAuthHandler.ExchangeCodeAsync` aşağıdakilerden değiştirilmiştir:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

Hedef:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

`code` Ve `redirectUri` dizeleri ayrı bağımsız değişkenler olarak geçirildi.

#### <a name="new-behavior"></a>Yeni davranış

`Code`ve `RedirectUri` `OAuthCodeExchangeContext` `OAuthCodeExchangeContext` konstrüktör aracılığıyla ayarlanabilen özelliklerdir. Yeni `OAuthCodeExchangeContext` tür, `OAuthHandler.ExchangeCodeAsync`''ye geçirilen tek bağımsız değişkendir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, ek parametrelerin kırılmaz bir şekilde sağlanmasına olanak tanır. Yeni `ExchangeCodeAsync` aşırı yüklemeler yaratmaya gerek yok.

#### <a name="recommended-action"></a>Önerilen eylem

Uygun `OAuthCodeExchangeContext` `code` ve `redirectUri` değerlerle bir yapı inşa edin. Bir <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> örnek sağlanmalıdır. Bu `OAuthCodeExchangeContext` tek örnek, `OAuthHandler.ExchangeCodeAsync` birden çok bağımsız değişken yerine geçirilebilir.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
