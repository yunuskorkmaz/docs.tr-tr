---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901635"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Yetkilendirme: IAllowAnonymous YetkilendirmeFilterContext.Filters kaldırıldı

Core 3.0ASP.NET itibariyle MVC, denetleyiciler ve eylem yöntemleri üzerinde keşfedilen [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) öznitelikleri için [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) eklemez. Bu değişiklik <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>türevleri için yerel olarak ele alınmıştır, ancak <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> bu ve uygulamalar için bir kırılma değişiklik' s. [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) özelliğine sarılmış bu tür uygulamalar, hem yapılandırma hem de bağımlılık enjeksiyonu gerektiğinde güçlü bir şekilde yazılmış, öznitelik tabanlı yetkilendirme elde etmenin [popüler](https://stackoverflow.com/a/41348219/608220) ve desteklenen bir yoludur.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>[AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) koleksiyonunda yer aldı. Arabirimin varlığını sınamak, filtreyi tek tek denetleyici yöntemlerini geçersiz kılmak veya devre dışı etmek için geçerli bir yaklaşımdı.

#### <a name="new-behavior"></a>Yeni davranış

`IAllowAnonymous``AuthorizationFilterContext.Filters` koleksiyonda artık görünmez. `IAsyncAuthorizationFilter`eski davranışa bağlı olan uygulamalar genellikle aralıklı HTTP 401 Yetkisiz veya HTTP 403 Yasak yanıtlarına neden olur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Core 3.0'ASP.NET yeni bir uç nokta yönlendirme stratejisi tanıtıldı.

#### <a name="recommended-action"></a>Önerilen eylem

Uç nokta meta verilerini `IAllowAnonymous`arama . Örnek:

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

Bu tekniğin bir örneği [bu HasAllowAnonymous yönteminde](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)görülmektedir.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!--

#### Affected APIs

Not detectable via API analysis

-->
