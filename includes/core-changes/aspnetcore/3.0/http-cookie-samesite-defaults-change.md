---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74282520"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP: bazı tanımlama bilgisi SameSite Varsayılanları None olarak değiştirildi

`SameSite`, bazı siteler arası Istek sahteciliği (CSRF) saldırılarını azaltmaya yardımcı olabilecek tanımlama bilgileri için bir seçenektir. Bu seçenek başlangıçta tanıtıldığında, çeşitli ASP.NET Core API 'lerde tutarsız varsayılanlar kullanılmıştır. Tutarsızlık, sonuçları kafa karıştırıcı olarak yönlendirdi. ASP.NET Core 3,0 itibariyle, Bu varsayılanlar daha iyi hizalanmıştır. Bu özelliği bileşen başına temelinde kabul etmeniz gerekir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Benzer ASP.NET Core API 'Leri, farklı varsayılan <xref:Microsoft.AspNetCore.Http.SameSiteMode> değerlerini kullandı. `HttpResponse.Cookies.Append(String, String)` ve `HttpResponse.Cookies.Append(String, String, CookieOptions)`, sırasıyla `SameSiteMode.None` ve `SameSiteMode.Lax`için varsayılan olarak görülen tutarsızlığa bir örnektir.

#### <a name="new-behavior"></a>Yeni davranış

Etkilenen tüm API 'Ler `SameSiteMode.None`varsayılan.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Varsayılan değer `SameSite` bir kabul etme özelliği yapmak için değiştirilmiştir.

#### <a name="recommended-action"></a>Önerilen eylem

Tanımlama bilgilerini gösteren her bileşeni, `SameSite` senaryolarına uygun olup olmadığına karar vermeniz gerekir. Etkilenen API 'lerin kullanımını gözden geçirin ve `SameSite` gerektiği şekilde yeniden yapılandırın.

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
