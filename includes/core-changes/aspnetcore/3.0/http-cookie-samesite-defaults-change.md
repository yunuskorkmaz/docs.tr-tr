---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282520"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP: Bazı çerez SameSite varsayılanları Hiçbiri olarak değiştirildi

`SameSite`bazı Çapraz Site İsteği (CSRF) saldırılarını azaltmaya yardımcı olabilecek tanımlama bilgileri için bir seçenektir. Bu seçenek başlangıçta sunulduğunda, çeşitli ASP.NET Core API'lerinde tutarsız varsayılanlar kullanılmıştır. Tutarsızlık kafa karıştırıcı sonuçlara yol açmıştır. Core 3.0ASP.NET itibariyle, bu varsayılanlar daha iyi hizalanır. Bu özelliği bileşen başına olarak kabul etmeniz gerekir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Benzer ASP.NET Core API'leri farklı varsayılan <xref:Microsoft.AspNetCore.Http.SameSiteMode> değerler kullansın. Tutarsızlık bir örnek görülür `HttpResponse.Cookies.Append(String, String)` ve `HttpResponse.Cookies.Append(String, String, CookieOptions)`, hangi varsayılan `SameSiteMode.None` `SameSiteMode.Lax`ve , sırasıyla.

#### <a name="new-behavior"></a>Yeni davranış

Tüm etkilenen API'ler varsayılan `SameSiteMode.None`.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Varsayılan değer, bir `SameSite` kabul özelliği yapmak için değiştirildi.

#### <a name="recommended-action"></a>Önerilen eylem

Tanımlama bilgileri yayıp yasanan `SameSite` her bileşenin senaryolarına uygun olup olmadığına karar vermesi gerekir. Etkilenen API'lerin kullanımını gözden geçirin ve gerektiğinde yeniden yapılandırın. `SameSite`

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
