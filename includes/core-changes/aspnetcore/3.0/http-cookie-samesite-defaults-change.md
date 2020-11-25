---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032763"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP: bazı tanımlama bilgisi SameSite Varsayılanları None olarak değiştirildi

`SameSite` , bazı siteler arası Istek sahteciliği (CSRF) saldırılarını azaltmaya yardımcı olabilecek tanımlama bilgilerine yönelik bir seçenektir. Bu seçenek başlangıçta tanıtıldığında, çeşitli ASP.NET Core API 'lerde tutarsız varsayılanlar kullanılmıştır. Tutarsızlık, sonuçları kafa karıştırıcı olarak yönlendirdi. ASP.NET Core 3,0 itibariyle, Bu varsayılanlar daha iyi hizalanmıştır. Bu özelliği bileşen başına temelinde kabul etmeniz gerekir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Benzer ASP.NET Core API 'Leri farklı varsayılan <xref:Microsoft.AspNetCore.Http.SameSiteMode> değerler kullandı. Ve ' de `HttpResponse.Cookies.Append(String, String)` `HttpResponse.Cookies.Append(String, String, CookieOptions)` Varsayılan olarak `SameSiteMode.None` `SameSiteMode.Lax` , ve sırasıyla olarak görülen tutarsızlığa bir örnektir.

#### <a name="new-behavior"></a>Yeni davranış

Etkilenen tüm API 'Ler varsayılan olarak `SameSiteMode.None` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Varsayılan değer, `SameSite` bir katılım özelliği oluşturmak için değiştirilmiştir.

#### <a name="recommended-action"></a>Önerilen eylem

Tanımlama bilgilerini gösteren her bileşen, senaryoları için uygun olup olmadığına karar vermeniz gerekir `SameSite` . Etkilenen API 'lerin kullanımını gözden geçirin ve `SameSite` gerektiği şekilde yeniden yapılandırın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
