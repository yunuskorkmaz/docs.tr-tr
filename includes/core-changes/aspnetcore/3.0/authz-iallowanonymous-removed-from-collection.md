---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032715"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Yetkilendirme: ıallowanonymous, AuthorizationFilterContext. Filters öğesinden kaldırıldı

ASP.NET Core 3,0 itibariyle, MVC, denetleyiciler ve eylem yöntemlerinde bulunan [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) öznitelikleri Için [allowanonymousfilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) eklemez. Bu değişiklik, türevleri için yerel olarak adreslenir <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute> , ancak ve uygulamaları için önemli bir değişiklik <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> . Bir [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) özniteliğinde Sarmalanan uygulamalar, hem yapılandırma hem de bağımlılık ekleme gerektiğinde kesin olarak belirlenmiş, öznitelik tabanlı yetkilendirme elde etmenin [popüler](https://stackoverflow.com/a/41348219/608220) ve desteklenen bir yoludur.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>[Authorizationfiltercontext. Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) koleksiyonunda göründü. Arabirim varlığına yönelik test, tek tek denetleyici yöntemlerinde filtreyi geçersiz kılmak veya devre dışı bırakmak için geçerli bir yaklaşımdır.

#### <a name="new-behavior"></a>Yeni davranış

`IAllowAnonymous` Artık `AuthorizationFilterContext.Filters` koleksiyonda görünmez. `IAsyncAuthorizationFilter` Eski davranışa bağımlı olan uygulamalar genellikle aralıklı HTTP 401 Yetkisiz veya HTTP 403 Yasak yanıtlara neden olur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 3,0 ' de yeni bir uç nokta yönlendirme stratejisi sunuldu.

#### <a name="recommended-action"></a>Önerilen eylem

Uç nokta meta verilerinde arama yapın `IAllowAnonymous` . Örnek:

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

Bu [HasAllowAnonymous yönteminde](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)bu tekniğin bir örneği görülür.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

#### Affected APIs

Not detectable via API analysis

-->
